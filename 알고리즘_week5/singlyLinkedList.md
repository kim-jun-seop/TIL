# 리스트 만들기

```dart
class SList:
    class Node:
        def __init__(self, item, link):  #Node의 생성자
            self.item = item
            self.next = link

    def delete_front(self): #노드에서 맨앞에 삭제
        if self.isEmpty():
            print("리스트가 텅비어서 삭제 불가")
            return None
        else:
            t = self.head
            self.head = self.head.next
            del t
            self.size -= 1

    def __init__(self): #SList의 생성자, 자바에서 this역할=self(생성자에는 반드시) 
        print("난 SList의 생성자") 
        self.head = None
        self.size = 0
    
    def isEmpty(self): 
        return self.size == 0

    def insert_front(self, item): #노드에서 맨앞에 추가
        if self.isEmpty():
            self.head = self.Node(item, None)
        else:
            self.head = self.Node(item, self.head)
        self.size += 1

    def insert_after(self, item, p): #노드에서 맨뒤에 추가
        p.next = self.Node(item, p.next)
        self.size += 1

    def search(self, target): #노드에서 조회
        p = self.head
        #k = 0, 1, 2, 3
        for k in range(self.size):
            if target == p.item:
                return k
            p = p.next

    def delete_after(self, p): #p가 참조하는 노드의 다음 노드를 삭제
        if self.isEmpty():
            print("리스트가 텅 비어있어서 삭제불가")
            return None
        else:
            t = p.next
            p.next = t.next
            del t
            self.size -= 1 

    def insert_index(self, index, item): #사용자가 원하는 인덱스에 새로운 노드 삽입
         if index < 0  or index >= self.size:
            print("인덱스 오류로 인해 삽입이 불가합니다.")
            return
         else:
            p = self.head
            for i in range(index-1):
                p = p.next
            self.insert_after(item,p)

    def delete_index(self, index): #사용자가 원하는 인덱스에 있는 노드를 삭제
        if index < 0 or index >= self.size:
            print("인덱스 오류로 인해 삭제가 불가합니다.")
            return
        else: 
            p = self.head
            for i in range(index-1):
                p = p.next
            self.delete_after(p)

    def delete_final(self):   #연결리스트의 맨 마지막 노드를 삭제하는 함수
        if self.isEmpty():
           print("리스트가 텅 비어있어서 삭제 불가")
           return None
        if self.head.next is None:  # 노드가 하나뿐일 때
           self.delete_front()
        else:
            p = self.head
            while p.next.next is not None:  # 마지막 노드의 직전까지 이동
                p = p.next
            t = p.next
            p.next = None
            del t
            self.size -= 1
             
    def printList(self):
        p = self.head
        while p:
            if p.next is not None:
                print(p.item , "=>", end="")
            else:
                print(p.item)
            p = p.next

def globalFunc():
    pass

if __name__ =="__main__":
    s = SList() #SList()의 생성자 호출
    s.insert_front("apple")
    s.insert_front("orange")
    s.insert_front("grape")
    s.insert_front("watermelon")
    s.insert_front("orange")
    s.printList()
    s.insert_after("cherry", s.head.next)
    s.printList()
    s.insert_front('pear')
    s.printList()
    print("cherry는 %d번째 노드에 있다" % 
            (s.search("cherry")+1))
    s.delete_after(s.head)
    s.printList()
    s.delete_front()
    print("첫 번째 노드 삭제후 \t\t")
    s.printList()

    #실습 과제 함수 작성
    s.insert_index(2,"melon")
    print("index=2에 melon 삽입후 \t\t")
    s.printList()
    s.delete_index(3)
    print("index=3에 있는 노드 삭제후 \t\t")
    s.printList()
    s.delete_final()
    print("마지막에있는 노드 삭제후 \t\t")
    s.printList()
