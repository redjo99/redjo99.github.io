---
title: "[Brute Force] 외판원 순회"
excerpt: "CS 분야에서 널리 쓰이는 외판원 순회(TSP) 문제를 풀어봅시다."

categories:
  - bruteforce
tags:
  - [algorithm, bruteforce, TSP]

permalink: /bruteforce/2025-06-21-brute-force-TSP/

toc: true
toc_sticky: true

date: 2025-06-21
last_modified_at: 2025-06-22
---

## 🦥 본문

Brute Force의 두 번째 문제로는,
외판원 순회(TSP) 문제를 가져왔습니다.

TSP는 computer science 분야에서 아주 중요하게 취급되므로,  
오늘 처음 들어보셨다면 이번 기회를 통해 접해보시길 바랍니다.  
  
사실 TSP 문제는 구성과 조건에 따라 어떤 알고리즘으로 풀어야 하는지가 달라집니다.  
제가 들고 온 TSP 문제는 Brute Force로 풀 수 있는 것이니, 함께 문제를 보시죠!  
  
[외판원 순회 2 - 백준](https://www.acmicpc.net/problem/10971)  
  
예제의 지도를 그려보자면, 아래와 같이 되겠네요.  
  
![tsp2 map](/assets/images/posts_img/TSP2_baekjoon.png)
  
이 문제는 우리가 답을 찾을 때도 머릿속에서 모든 경우의 경로 합을 계산하며,  
그 중 가장 작은 값을 답으로 정한다는 것을 알 수 있습니다.  
따라서 고민없이 Brute Force를 적용하면 된다는 건데요,  
혹시 모르니 시간복잡도 계산부터 해 봅시다!  
  
  도시의 수가 N일 때, 출발점을 정하는 경우는 N 입니다.  
이후 하나의 출발점에서 다음 지점으로 갈 수 있는 경우의 수는 N - 1 입니다.  
마찬가지로 다음 지점은 N - 2, 그 다음은 N - 3, ... 이므로,  
총 경로의 수는 N! 이라 할 수 있겠네요.  
매번 최솟값을 갱신해야 하지만, 비교 연산 하나면 해결되므로 이는 O(1) 입니다.  
따라서 시간복잡도는 O(N! * 1) = O(N!) 이 되고,  
최악의 경우 N = 10일 때이므로 10! 회의 연산이 필요하네요.  
지난 포스팅에서 10^8 이하면 1초 안에 해결이 가능하다고 했죠?  
10!은 10^8보다 현저히 작은 값이고, 시간 제한도 2초이므로 Brute Force로 풀면 되겠습니다.  

  그럼 이번에도 자유롭게 풀어 보시고, 아래의 제 코드를 참고하시죠!  
  
  
그럼 다음 포스팅에서 새로운 Brute Force 예제와 함께 만나요!
