# 프로그래머스 signal: segmentation fault (core dumped) 에러

오랜만에 코테를 풀었다
입문문제 - 약수 구하기

저번에 분수의 덧셈을 풀었을 때의 기억을 되살려 해봤다

### 그런데!!..

오류가 터져버렸지 뭐야~ 아이 좋아라~

#### 문제된 코드

```
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

int* solution(int n) {
    // return 값은 malloc 등 동적 할당을 사용해주세요. 할당 길이는 상황에 맞게 변경해주세요.
    int* answer = (int*)malloc(sizeof(int) * n);
    int a = 0;
    while(n > 0)
    {
        for(int i = 1; i <= n; i++)
        {
            if(n % i == 0)
            {
                answer[a++] = i;
            }
        }
     }
    return answer;
}
```

분수의 덧셈을 풀었을 때는 더해진 분수에서 분모와 분자의 공약수를 구해야 했다
c언어로 풀었을 땐 while 문을 사용해 0이 됐을 때 빠져나올 수 있게 했다
그 기억을 가지고 아주 자연스럽게 while문을 썼다

그게 문제가 됐다 ㅎ..
이미 for문에서 한계를 정해줬는데 while문을 쓰니까 오류가 난 것 같다

#### 수정한 코드

```
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

int* solution(int n) {
    // return 값은 malloc 등 동적 할당을 사용해주세요. 할당 길이는 상황에 맞게 변경해주세요.
    int* answer = (int*)malloc(sizeof(int) * n);
    int a = 0;
        for(int i = 1; i <= n; i++)
        {
            if(n % i == 0)
            {
                answer[a++] = i;
            }
        }
    return answer;
}
```

while 문을 뿅 없애면 되는 일이었다

## 해결방법 모색

- 시그맨테이션 에러가 뜨자마자 일다 그걸 복붙해다 검색했다
  하지만 원인을 찾지 못했다
- 해당 문제를 풀이해놓은 티스토리를 찾아 대조하며 문제를 찾았다
  내가 쓴것과 흡사했지만 while문이 없는걸 보고 문제를 알았다

## 주저리주저리

요즘 계속 프로젝트 퍼블리싱만 했더니 코테가 하고싶어졌다
평소에는 하기 싫었는데..
뭔가 하기 싫으면 다른걸 해서 시선을 돌리는것도 나쁘진 않은 것 같다
오랜만에 벨로그에 들어와서 학기 초에 쓴 일기를 보는데
와.. 그래도 많이 성장하고 적응한거구나..
이런 일기를 계속 써서 남겨놓으면 나중에 봤을 때 신선한 자극이 될 수 있겠구나 싶었다
