
```python
import boto3 # aws 서비스 제어용 파이썬 라이브러리(ec2,sns,Lambda등 aws 리소스를 다룰 수 있음)


def lambda_handler(event, context):
    ec2 = boto3.client('ec2') # EC2 서비스와 통신하기 위한 boto3 클라이언트 생성

    instance_id = event.get('instance_id') # LambdaA에서 LabdaB를 invoke()(호출)할 떄 보낸 JSON 형식 데이터에서 instance_id를 꺼냄

    if not instance_id: # 에러 체크
        return {
            'statusCode': 400,
            'message': 'instance_id가 전달되지 않았습니다.'
        }

    try:
        response = ec2.start_instances(InstanceIds=[instance_id]) # 전달받은 Instance_Id를 리스트에 넣어서 EC2 인스턴스 시작 요청을 보냄
        print(f"EC2 인스턴스 {instance_id} 시작 요청 완료")
        
        return { # 성공시 해당 내용 반환
            'statusCode': 200,
            'message': f'EC2 인스턴스 {instance_id}를 시작했습니다.',
            'response': response
        }

    except Exception as e: # 실패시 해당 내용 반환
        print(f"EC2 인스턴스 {instance_id} 시작 요청 완료")
        return {
            'statusCode': 500,
            'message': f'인스턴스 시작 중 오류 발생: {str(e)}'
        }
