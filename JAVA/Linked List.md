## Linked List

###  Linked List?

컴퓨터에서 자료를 저장하는 구조의 한 종류로 일렬로 연결된 데이터를 저장할 때 사용.

![image-20200616205101467](C:\Users\KGHK\AppData\Roaming\Typora\typora-user-images\image-20200616205101467.png)

컴퓨터에 자료를 저장하는 구조의 한 종류.

일렬로 연결된 데이터를 저장할 때 사용.

데이터를 저장할 수 있는 공간이 있으면 다음 데이터의 주소를 가지고 있는 구조.

배열하고 비교를 안할 수가 없다. 배열 방들은 물리적으로 한군데 모여 있고 대신 한번 만들면 크기 조절 불가

근데 Linked List는 그냥 하나 끼워 넣으면 됨.

이렇게 주소를 일일이 찾아다녀야 되기 때문에 붙어있는 배열보다 속도가 느릴 수 있음.

근데 삽입하고 삭제하고 그런거를 노드 추가 삭제 그럴 때 배열 다 복사하고 지랄할 때 시간 존나 오래걸림.

= 길이가 정해지지 않은 데이터를 핸들링 할 때는 Linked List가 좋다.



Linked List의 단/양방향

길이가 정해져 있지 않당.

데이터를 저장한 노드에 다음 데이터의 주소를 가지고 있는 구조. 위의 그림은 한쪽 방향으로만 간다. 따라서 검색을 할 때는 맨 앞엣놈부터 한개씩 노드를 이동하면서 검색을 해야함. 한 방향으로만 이동이 가능한 것 : 단방향

양방향은 앞에놈이 어딨는지 주소를 추가로 가지고 있는 것이다.

단방향 : header 주소 하나만 포인터를 저장하고 있음. 근데 양방향은 양 쪽 끝에 포인터를 저장하고 있어서 맨 끝에 노드를 삽입할 때 일부러 끝까지 찾아가는 번거로움을 줄일 수 있을 것. 그러나 공간의 효율성을 중요하게 여기기 때문에 굳이 양쪽으로 댕길 필요가 없는걸 양방향으로 다닐 필욘 없다.