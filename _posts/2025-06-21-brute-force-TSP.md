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
last_modified_at: 2025-06-21
---

## 🦥 본문

Brute Force의 두 번째 예제로는,
외판원 순회(TSP) 문제를 가져왔습니다.

TSP는 computer science 분야에서 아주 중요하게 취급되므로,  
오늘 처음 들어보셨다면 이번 기회를 통해 접해보시길 바랍니다.  
  
사실 TSP 문제는 구성과 조건에 따라 어떤 알고리즘으로 풀어야 하는지가 달라집니다.  
제가 들고 온 TSP 문제는 Brute Force로 풀 수 있는 것이니, 함께 문제를 보시죠!  
  
[외판원 순회 2 - 백준](https://www.acmicpc.net/problem/10971)  
  

  
요약하자면 숫자야구 문답이 입력으로 주어지고, 가능한 답의 개수를 출력해야 합니다.  
링크에 있는 예시 입출력을 살펴보죠.  
  
먼저 2 스트라이크 0 볼을 기록한 327부터 보겠습니다.  
셋 중 하나겠죠.  
1. 32X (X != 7)
2. 3X7 (X != 2)
3. X27 (X != 3)
  
그리고 1 스트라이크 0 볼을 기록한 356도 동시에 보겠습니다.  
이것도 셋 중 하나겠죠.  
1. 3XY (X != 5 && Y != 6)
2. X5Y (X != 3 && Y != 6)
3. XY6 (X != 3 && Y != 5)
  
32X, 3X7, X27 중 하나를 만족하면서, 동시에 3XX, X5X, XX6 중 하나도 만족해야 하네요.  
이건 32X, 3X7 두 가지로 볼 수 있습니다.  
(X5X와 XX6은 각각 3X7, 32X에 포함되므로 따로 세지 않았습니다.)  
  
이제 1 스트라이크 1 볼을 기록한 123을 보겠습니다.  
32X, 3X7 중 해당 조건을 만족하는 건 무엇일까요?  
32X (X != 7 && X != 1) 밖에 없겠습니다.  
(321이라면 1 스트라이크 2 볼이 되므로 X가 1이 아니라는 조건이 추가됐으며,  
3X7이 불가능한 이유는 X가 2가 아니라는 조건이 있었기에 0 스트라이크 1 볼이 되기 때문입니다.)  
  
자, 그럼 마지막 0 스트라이크 1 볼을 기록한 489를 봅시다.  
32X가 해당 조건을 만족하려면, X가 4 또는 X가 9이면 되겠습니다.  
  
따라서, 가능한 답은 324와 328 두 가지이므로, 2를 출력하면 됩니다!  


  자 좋습니다. 이제 문제는 이해했는데, 어떤 알고리즘으로 풀면 될까요?  
제가 예시를 풀었던 대로 하면 될까요?  
2 스트라이크인 경우를 찾아서 세 가지 경우로 나누고,  
아 그전에 2 스트라이크인 경우가 없다면 1 스트라이크부터 세 가지 경우로 나누고,  
아 그런데 3 스트라이크가 있었다면 3 스트라이크 그대로 답이니까 1을 출력하고,  
....  
  
입력이 다양할 수 있기 때문에 복잡하죠?  
우리가 앞에서 얘기한 순서대로 생각해봅시다!  
바로 'Brute Force로 시간 내에 가능할까?'입니다.  
  
문제에서 시간 제한을 1초로 뒀는데, 통상 1억(10^8)번의 연산에 1초가 소요됩니다.  
지금은 컴퓨터가 조항져 2억5천~3억번까지도 가능하다고 하는데,  
저희는 넉넉하게 1억 번 내의 연산으로 수행해봅시다.  
  
이 문제에서 Brute Force란,  
모든 숫자야구 조합에 대해 문답 조건들을 다 만족하는지 테스트한 다음,  
해당하는 숫자야구 조합 개수를 출력하는 거겠네요.  
  
그럼 시간복잡도를 파악해 봅시다.  
첫 번째 숫자 9가지, 두 번째 숫자 8가지, 세 번째 숫자 7가지가 있으므로  
총 504가지 숫자야구 조합이 있습니다.  
  
그리고 각 조합에 대해 문답 개수 N만큼 테스트를 해야 하는데,  
문제 조건을 보면 N은 최대 100까지 가능하네요.  
따라서 총 50,400번의 테스트 끝에 우리는 답을 얻어낼 수 있습니다.  
  
50,400이면 1억보다 매우 작은 수이므로 충분히 시간 안에 풀 수 있겠죠?  
따라서 우리는 복잡한 알고리즘을 고민하기보단, Brute Force를 적용하면 되겠습니다.  
  
  
그럼 자유롭게 풀어 보시고, 이후 아래의 제 코드를 참고하시죠!  
(정답만 보실 분들은 맨 아래로 내리시면 됩니다.)  
  
  
<script src="https://gist.github.com/redjo99/ab5c94e0572ff25951243545c7354802.js"></script>  
  
백준 채점 3퍼센트에서 막혔습니다. 저도 한번만에 풀지 못했네요.  
원래 알고리즘 문제를 풀 때 반례 찾는 것도 중요하니, 함께 찾아보죠.  
위 코드는 뭐가 문제였을까요?  
정답은...  
  
모든 숫자야구 조합에 대해 검사할 때(line 15), 987을 빼놓고 검사했기 때문입니다.  
자 그럼 아래 코드처럼 987에 등호를 포함시켜 검사해 보죠!  
  
<script src="https://gist.github.com/redjo99/650e7eada9c148a54b9643c70b279719.js"></script>  
  
이번엔 18퍼센트에서 막혔네요. 이번 원인도 한번 찾아보시죠!  
정답은...  
  네, 그냥 배열 크기가 부족해서 그런 거였네요.  
코드 짤 때 N을 10 이하로 잘못봐서.. 배열 크기를 13이 아닌 103으로 선언해야 맞겠죠?^^  
(참고로 저는 out of index 에러를 방지하기 위해 배열 크기에 3 정도 여유를 두는 편입니다.)  
  
반례가 뭘까 한 시간을 고민했는데.. 여러분은 문제 조건을 잘 보시기 바랍니다ㅠㅠ  
어쨌든 최종 정답 코드는 아래와 같습니다.  
  
<script src="https://gist.github.com/redjo99/d345f2019b620f6c1936f181412336ca.js"></script>  
  
  
그럼 다음 포스팅에서 새로운 Brute Force 예제와 함께 만나요!
