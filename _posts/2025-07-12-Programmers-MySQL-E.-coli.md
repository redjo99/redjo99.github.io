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
  
  
그럼 다음 포스팅에서 LeetCode 3번 문제와 함께 만나뵙겠습니다!
