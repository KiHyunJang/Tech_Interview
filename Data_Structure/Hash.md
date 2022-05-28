# Hash
  
## 해시 테이블 (Hash Table)
헤시 테이블이란 key,value형태로 데이터를 저장하는 자료구조이다.  
해시 함수에 key를 적용해 나온 결과를 배열의 인덱스로 하고, 그자리에 value를 저장한다.  
해시 충돌이 없을 경우, 해시 테이블의 시간복잡도는 O(1)  
Swift에서도 dictionary를 Hash Table라고 생각하면 쉽다.  
  
## 해시 함수 (Hash Function)
key를 해시로 바꿔주는 역할을 한다.  
다양한 길이를 가지고 있는 key를 일정한 길이의 hash로 바꿔서 공간을 효율적으로 관리한다.  
해시 충돌을 최소화 하는 해시 함수를 만드는 것이 중요하다.  
  
## 해시 (Hash)
해시 함수의 결과 값  
저장소에서 value와 매칭되어 저장됨  
  
## 해시 충돌
서로 다른 키가 같은 해시 값을 가지는 경우  
  
## 해시 충돌 해결법
##### **Open Address 방식 (개방주소법)**  
해시 충돌이 발생하면, (즉 삽입하려는 해시 버킷이 이미 사용 중인 경우) **다른 해시 버킷에 해당 자료를 삽입하는 방식** 이다. 버킷이란 바구니와 같은 개념으로 데이터를 저장하기 위한 공간이라고 생각하면 된다. 다른 해시 버킷이란 어떤 해시 버킷을 말하는 것인가?  
공개 주소 방식이라고도 불리는 이 알고리즘은 Collision 이 발생하면 데이터를 저장할 장소를 찾아 헤맨다. Worst Case 의 경우 비어있는 버킷을 찾지 못하고 탐색을 시작한 위치까지 되돌아 올 수 있다. 이 과정에서도 여러 방법들이 존재하는데, 다음 세 가지에 대해 알아보자.  
  
Linear Probing 순차적으로 탐색하며 비어있는 버킷을 찾을 때까지 계속 진행된다.  
Quadratic probing 2 차 함수를 이용해 탐색할 위치를 찾는다.  
Double hashing probing 하나의 해쉬 함수에서 충돌이 발생하면 2 차 해쉬 함수를 이용해 새로운 주소를 할당한다. 위 두 가지 방법에 비해 많은 연산량을 요구하게 된다.  
​  
##### **Separate Chaining 방식 (분리 연결법)**  
일반적으로 Open Addressing 은 Separate Chaining 보다 느리다. Open Addressing 의 경우 해시 버킷을 채운 밀도가 높아질수록 Worst Case 발생 빈도가 더 높아지기 때문이다. 반면 Separate Chaining 방식의 경우 해시 충돌이 잘 발생하지 않도록 보조 해시 함수를 통해 조정할 수 있다면 Worst Case 에 가까워 지는 빈도를 줄일 수 있다. Java 7 에서는 Separate Chaining 방식을 사용하여 HashMap 을 구현하고 있다. Separate Chaining 방식으로는 두 가지 구현 방식이 존재한다.  
  
**연결 리스트를 사용하는 방식(Linked List)**  
각각의 버킷(bucket)들을 연결리스트(Linked List)로 만들어 Collision 이 발생하면 해당 bucket 의 list 에 추가하는 방식이다. 연결 리스트의 특징을 그대로 이어받아 삭제 또는 삽입이 간단하다. 하지만 단점도 그대로 물려받아 작은 데이터들을 저장할 때 연결 리스트 자체의 오버헤드가 부담이 된다. 또 다른 특징으로는, 버킷을 계속해서 사용하는 Open Address 방식에 비해 테이블의 확장을 늦출 수 있다. 
   
**Tree 를 사용하는 방식 (Red-Black Tree)**  
기본적인 알고리즘은 Separate Chaining 방식과 동일하며 연결 리스트 대신 트리를 사용하는 방식이다. 연결 리스트를 사용할 것인가와 트리를 사용할 것인가에 대한 기준은 하나의 해시 버킷에 할당된 key-value 쌍의 개수이다. 데이터의 개수가 적다면 링크드 리스트를 사용하는 것이 맞다. 트리는 기본적으로 메모리 사용량이 많기 때문이다. 데이터 개수가 적을 때 Worst Case 를 살펴보면 트리와 링크드 리스트의 성능 상 차이가 거의 없다. 따라서 메모리 측면을 봤을 때 데이터 개수가 적을 때는 링크드 리스트를 사용한다.  
  
## 해시 충돌의 문제가 있음에도 쓰는 이유
많은 양의 데이터를 해시 충돌만 없다면 빠르게 탐색 가능하다.  
적은 자원으로 많은 양의 데이터를 효율적으로 관리할 수 있다.  
하드디스크나 클라우드에 존재하는 무한한 데이터들을 유한한 개수의 해시값으로 매핑하면 작은 메모리로도 프로세스 관리가 가능하다.  
  
## Swift에서 Hash
체이닝은 해시 저장 공간을 연결리스트로 구성해 해시 충돌이 일어난 경우, 해당 인덱스의 연결리스트에 데이터를 추가하는 방법이고, open addressing은 추가 저장 공간을 이용하지 않고 빈 공간을 찾아 저장소의 다른 주소에 저장하는 방법이다.  
  
swift에선 open addressing with linear probing.