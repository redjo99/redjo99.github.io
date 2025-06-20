---
title: "[Brute Force] 소개 및 기초예제"
excerpt: "모든 알고리즘의 기초가 되는 브루트 포스와 완전탐색을 소개합니다."

categories:
  - bruteforce
tags:
  - [algorithm, bruteforce]

permalink: /bruteforce/2025-06-20-brute_force/

toc: true
toc_sticky: true

date: 2025-06-20
last_modified_at: 2025-06-20
---

## 🦥 본문

알고리즘 공부의 시작으로 Brute Force(브루트 포스)를 소개드리는 이유는,  
모든 알고리즘의 기초가 되는 방식이기 때문입니다.  
  
그런데 여러분은 '완전탐색'이라는 알고리즘 또한 들어보셨을 수도 있습니다.  
차례대로 설명드리면서 차이를 알려드리겠습니다.  
  
먼저 Brute Force 알고리즘은, 문제해결을 위해 모든 경우를 탐색하여 해답을 얻습니다.  
완전탐색 알고리즘은, 모든 경우를 탐색하는 방식 자체를 말합니다.  
따라서 둘의 차이는, 탐색에 중점을 두느냐 해답 찾기에 중점을 두느냐에 있습니다.  
저는 알고리즘 문제풀이에 중점을 두므로, 앞으로는 Brute Force라는 용어만 사용하겠습니다.  
  
Brute Force는 모든 경우를 탐색하므로, 해답 찾기에 실패할 걱정은 없습니다.  
코드 작성 또한 별도의 번뜩이는 아이디어가 필요하지 않으므로, 다른 알고리즘에 비해 편하죠.
다만, 모든 경우를 탐색하기 때문에, 시간 복잡도가 높습니다.  
실제로 앞으로 배울 다른 알고리즘들은 시간 단축을 위해 만들어졌기 때문에,  
어떻게 보면 완전탐색을 피하기 위해 만들어졌다고 볼 수도 있습니다.  
  
따라서 여러분이 앞으로 복잡한 문제를 만나신다면,  
1. 이거 완전탐색으로 시간 내에 풀 수 있을까..?
2. (안 된다고 판단한 후) 그럼 무슨 알고리즘을 적용해야 할까..?  
순서로 생각하셔도 무방합니다.  
  
자, 그럼 이번에도 간단한 예제를 만나보겠습니다.

[]()

  
<script src="https://gist.github.com/redjo99/40edc140b362b1efc1f1f68fd3b507f4.js"></script>  
  
![hello world](/assets/images/posts_img/readme/hello_world.png)  
  
위는 c++에서 hello world를 출력하는 코드인데,  
 
  
<script src="https://gist.github.com/redjo99/f56d4c5a5fd4e973ad3704365e2c7e71.js"></script>  
  
따라서 개인적으로는 std를 먼저 선언한 후 시작하는 것을 추천합니다.  

  
![std error](/assets/images/posts_img/readme/std.png)  
  
빨간 줄에서 친절하게 std가 필요하지 않냐고 물어보고 있죠?  
 
  
<script src="https://gist.github.com/redjo99/feffe391cbe77675c1345264817216a0.js"></script>  
  
![cin](/assets/images/posts_img/cin.png)  
  
마지막으로 위 코드와 함께 입력을 설명하겠습니다.  

  
그럼 다음 포스팅에서 c++ 강의 이어가겠습니다!
