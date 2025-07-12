---
title: "[프로그래머스] MySQL LV1. 특정 형질을 가지는 대장균 찾기"
excerpt: "프로그래머스의 MySQL LV1 대장균 문제를 풀어봅시다."

categories:
  - programmers
tags:
  - [mysql, programmers]

permalink: /programmers/2025-07-12-Programmers-MySQL-E.-coli/

toc: true
toc_sticky: true

date: 2025-07-12
last_modified_at: 2025-07-12
---

## 🦥 본문

안녕하세요, 오늘은 Programmers에서 MySQL 문제를 풀어볼 예정입니다.  
전공자들을 포함한 많은 분들이 코딩테스트를 준비하실 때 대부분 알고리즘을 대비하지만,  
일부 기업, 특히 데이터를 다루는 쪽에선 MySQL이나 Oracle로도 응시를 한답니다.  
(보통 MySQL이나 Oracle 중 편한 걸 선택하는 방식입니다.)  
저는 학부생 때 배웠기에 익숙한 MySQL을 선택해 풀어보겠습니다.  
데이터 관련 분야에 관심있으신 분들은 함께하시면 도움될 겁니다!  
  
그럼 LV1 문제부터 만나보시죠!  
  
[특정 형질을 가진 대장균 찾기 - Programmers](https://school.programmers.co.kr/learn/courses/30/lessons/301646)  
  
첫 문제기에 MySQL 풀이 방식에 대해 잠깐 설명드리자면,  
주어진 데이터(표)들에서 내가 원하는 값들을 원하는 형식으로 뽑아내야 합니다.  
그래서 문제 조건을 보고, 필터링, 변환, 새로운 값 산출, 병합 등 수많은 방식 중  
무엇이 필요한지를 생각해 그에 맞는 커맨드를 입력하면 됩니다.  
  
그리고, 대부분의 MySQL 문제는 SELECT (A) FROM (B) WHERE (C) 형태의 풀이를 가집니다.  
'B 데이터에서 A 특성들을 C 조건에 맞는 것들만 뽑아온다.'라고 보시면 되겠습니다.  
때문에 c++ 문제를 풀 때 #include<iostream>, int main()을 적고 시작하는 것처럼,  
MySQL에서는 아래 세 줄을 먼저 적고 시작하시면 편합니다.  
  
SELECT  
FROM  
WHERE  
  
이렇게 말이죠.  
  
그럼 이제, 문제를 살펴보겠습니다.  
  

  
<script src="https://gist.github.com/redjo99/02cf0c3877020e7d70f4db95f31aa541.js"></script>  
  
문제 그림처럼, 방향을 바꿔가며 택배 상자를 하나하나 쌓았습니다.  
시간복잡도를 생각해보면, 
  
1)  
ListNode* node2 = new ListNode();   // 값이 0인 노드 node2 생성.  
ListNode* node3 = new ListNode(3);   // 값이 3인 노드 node3 생성.  
ListNode* node1 = new ListNode(5, &node2);   // 값이 5인 node1을 생성하고, node2 앞에 붙임.  
node2->next = node3;   // node2 뒤에 node3를 붙임.
  
2)  
ListNode* node1 = new ListNode(5);  
node1->next = new ListNode(0);   // 5 뒤에 0 붙임.   
node1->next->next = new ListNode(3);   // 5 뒤의 뒤에 3 붙임.  
  
이런 식으로 여러 가지 방법이 있습니다.  
  
참고로, 지금은 함수 내부 작업이라 언급하지 않았지만  
new는 동적 메모리 할당입니다.  
따라서 함수 외부 코드까지 작업하실 때는 메모리 해제가 필요하며,  
linked list의 맨 뒤에서부터 역순으로 delete를 실행하면 됩니다.  
바로 위의 예시에선,  
delete node1->next->next;  
delete node1->next;  
delete node1;  
순서로 실행하시면 됩니다.  
  
2. 중간에 삽입  
5 -> 0 -> 3 리스트가 생성된 상태에서,  
4를 중간에 삽입해 5 -> 4 -> 0 -> 3으로 만들어봅시다.  
1 - 1)의 코드가 존재하는 상태에서 네 번째 노드를 추가해볼게요.  
  
ListNode* node4 = new ListNode(4);   // 새 노드(4) 추가.  
node4->next = node2;   // 4 뒤에 0 붙임.  
node1->next = node4;   // 5 뒤에 4 붙임.  
  
요약하자면, 5 - 0 연결을 끊고, 5 - 4 연결과 4 - 0 연결을 만드는 겁니다.  
새 연결을 만들 때 기존 5 - 0 연결은 끊어지니 따로 끊을 필요는 없는 거죠.  
  
그럼 중간 삽입이 아니라 처음 위치에 삽입하려면 어떻게 할까요?  
이번에는 5 -> 0 -> 3 리스트를 4 -> 5 -> 0 -> 3으로 만들어봅시다.  
아까처럼 1 - 1) 상황에서 진행해보겠습니다.  
  
ListNode* node4 = new ListNode(4);  
node4->next = node1;   // 4 뒤에 5 붙임.  
node1 = node4;   // 노드 시작점을 5에서 4로 변경.
  
과정은 중간 삽입과 비슷하지만,  
노드 시작점을 변경하는 코드가 필요하다는 걸 기억하세요!  
  
3. 리스트 출력  
앞에서 만든 4 -> 5 -> 0 -> 3 리스트를 출력해봅시다.
  
ListNode* current = node1;   // 첫 번째 노드부터 시작.  
while (current != nullptr) {   // 다음 노드 없을 때까지 반복.  
  cout << current->val << endl;  
  current = current->next;   // 노드 하나씩 넘어감.
}
  
  
자 그럼 이제, 문제를 풀 준비가 되었습니다. 알고리즘을 생각해 볼까요?  
  

  
코드 확인해 보시죠!  
  
<script src="https://gist.github.com/redjo99/d7a3a9ceec3058ef872554a48e37f1d3.js"></script>  
  
  
  
실제로 채점 결과 정답이었고, 아래의 결과를 얻었습니다.  
  
|  | Runtime | Memory |
| --- | --- | --- |
| **Result** | 1ms | 14.76MB |
| **Beats** | 80.14% | 51.13% |
   
예상했던 대로 시간에서 우수한 성능, 메모리에선 평균적인 성능이 나왔습니다.  
  
코드 길이는 짧았지만, 많은 요소를 생각해야 하는 좋은 문제였네요.  
  
그럼 다음 포스팅에서 LeetCode 3번 문제와 함께 만나뵙겠습니다!
