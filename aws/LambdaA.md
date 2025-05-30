
```python
import boto3 # aws 서비스 제어용 파이썬 라이브러리(ec2,sns,Lambda등 aws 리소스를 다룰 수 있음)
import json # json변환용


Instance_Id = 'i-035ef86ba73a65d9a' # ec2인스턴스 고유 ID
SNS_ARN = 'arn:aws:sns:ap-northeast-2:443370697536:sgu-202574-cpu-alarm' # 알림을 보낼 SNS ARN
LambdaB_Name = 'sgu-202574-LambdaB' # ec2를 시작시킬 LambdaB 함수 이름

def lambda_handler(event, context): # Lambda 함수의 시작점
    ec2 = boto3.client('ec2') # ec2에 접근하기 위한 클라이언트 객체
    sns = boto3.client('sns') # sns에 접근하기 위한 클라이언트 객체
    lambda_client = boto3.client('lambda') # lambda에 접근하기 위한 클라이언트 객체

    #ec2 상태 확인
    response = ec2.describe_instance_status( # ec2인스턴스의 실행 상태, 상태 검사 결과 등을 조회하는 함수
        InstanceIds = [Instance_Id], # 확인하고 싶은 인스턴스 id를 리스트로 전달 , aws api가 리스트 형식을 요구함(리스트가 아니면 에러)
        IncludeAllInstances = True  # true로 설정하면 "stopped"같은 중지된 인스턴스도 포함해서 조회 
    )

    statuses = response['InstanceStatuses'] # ec2 상태 정보를 담은 리스를 반환

    if not response['InstanceStatuses'] : # 인스턴스 정보가 없으면 -> 중지된게 아니라 삭제 or 없는것이니 에러 반환
        return {'status' : 'error', 'message' : '인스턴스 상태 정보를 가져오지 못함.'}

    state = statuses[0]['InstanceState']['Name'] # 첫 번째 인스턴스 상태를 가져와 'Name'을 꺼내기 , "InstanceState" {"Code : 80, "Name" : "Stopped"}
    print(f'현재 EC2 상태: {state}')

    if state.lower() == 'stopped': # EC2 인스턴스의 상태가 대소문자 상관없이 stopped이면 실행
        # sns 알림 전송
        message = (
            f"EC2 instance {Instance_Id} is stopped.\n"
        )
        sns.publish( # sns에 보내는 메시지
            TopicArn = SNS_ARN, # 보내는 대상의 고유 식별자
            Subject = 'EC2 status alert', # 이메일 제목
            Message = message # 이메일 본문
        )
        print("SNS 알림 발송 완료") # 알림이 발송됐다는걸 CloudWatch 로그로 확인 가능

        # LambdaB 호출 (비동기 호출 -> 어떤 작업을 요청만 하고, 그 작업이 끝날 때까지 기다리지 않고 다음 코드로 넘어가는 방식)
        lambda_client.invoke( # 다른 람다 함수 실행
            FunctionName = LambdaB_Name, # 호출할 람다 함수 이름
            InvocationType = 'Event',  # 비동기 호출
            Payload = json.dumps({ # JSON 문자열로 변환하는 함수(LambdaB로 넘겨줄 JSON형태의 데이터를 만듬)
                'instance_id': Instance_Id
            }).encode('utf-8') # 만든 문자열을 바이트 형태로 바꿔주기(invoke()는 payload에 바이트 타입만 받기 떄문에 꼭 필요!)
        )
        print("LambdaB 호출 완료")

    elif state in ['running' , 'pending']: # state가 running(켜진상태) 또는 pending(켜지는중)인 경우 실행
        print(f"EC2상태는 '{state}' -> 이미 실행 중이거나 부팅 중이므로 호출하지 않음.")
    else:
        print(f"EC2 상태가 '{state}' -> 처리 로직 없음.")
    return {'message' : f'EC2 상태 : {state}'}
