---
author: Rn
title: "[Rn] 시간 복잡도 기본 (Time Complexity Basic) - Part 3"
date: 2023-02-26 12:18:02 +0900
categories: [Algorithm, Time Complexity]
tag: [Algorithm, Time Complexity]
math: true
---

## 목차
{: .no_toc }

1. TOC
{: toc }

## 이 글과 연관된 글
{: .no_toc }

- [시간 복잡도 기본 (Time Complexity Basic) - Part 1](https://thak1411.github.io/posts/Time-Complexity-Basic-1/)
- [시간 복잡도 기본 (Time Complexity Basic) - Part 2](https://thak1411.github.io/posts/Time-Complexity-Basic-2/)
- [시간 복잡도 기본 (Time Complexity Basic) - Part 4](https://thak1411.github.io/posts/Time-Complexity-Basic-4/)

---

## 시간 복잡도 계산 방법

시간 복잡도를 계산하는 방법은, 코드를 한 줄씩 읽으면서, 각 줄이 실행되는 횟수를 계산하면 됩니다.

단, 실제로 실행되는 코드 줄 수를 정확하게 세는 것이 아닙니다. 시간 복잡도는 입력에 따라 실행되는 횟수가 바뀌는 줄 수만 계산합니다.

즉, 어떤 입력이 들어와도 실행되는 횟수가 바뀌지 않는다면, 어떤 입력을 넣던 항상 고정된 상수 시간이 걸리는 코드라고 볼 수 있습니다.

이때, 들어오는 입력이 무한대(매우 큰 수)로 커질 때, 상수 시간이 걸리는 코드는 실행 시간이 무시할 수 있을 정도로 작아집니다.

따라서 상수 시간이 걸리는 코드는 시간 복잡도를 계산할 때 무시하는 게 일반적입니다.

> 하지만, 상수 시간이 제한 시간 안에 실행되지 않을 정도로 크다면, 경우에 따라 $$O(100,000)$$ 처럼 상수 시간이 얼마나 걸리는지 표현하기도 합니다.
자세한 내용은 이후 파트를 확인해 주세요.
{: .prompt-danger }

## 예시 1

먼저 다음 코드를 보겠습니다.

```c
#include <stdio.h>

int main() {
    int n, sum = 0;
    scanf("%d", &n);
    for (int i = 1; i <= n; ++i) {
        sum += i;
    }
    printf("sum = %d", sum);
    return 0;
}
```

위 코드는 `n`을 입력받은 뒤, `1`부터 `n`까지 합을 구하는 코드입니다.

코드에서 각 줄이 실행되는 횟수를 계산해 보겠습니다.

> 이때 `scanf`, `printf` 는 내부적으로 실행되는 코드가 여러 줄 더 있지만, 보통 무시해도 되는 수준이므로 이 글에서도 무시합니다.
{: .prompt-info }

```c
#include <stdio.h>

int main() {
    int n, sum = 0;
    scanf("%d", &n); // 1번
    for (int i = 1; i <= n; ++i) { // 이 포문은 n번 반복합니다.
        sum += i; // n번
    }
    printf("sum = %d", sum); // 1번
    return 0;
}
```

위 코드는 총 $$1 + n + n + 1 = 2n + 2$$ 줄이 실행됩니다.

하지만 `scanf`, `printf`는 실행 시간이 상수 시간이므로 시간 복잡도에 포함시키지 않습니다.

또 $$2n$$ 의 경우 시간 복잡도에서는 $$n$$처럼 상수를 제외하고 표현합니다.

> $$2n$$ 의 경우 $$n$$처럼 상수를 제외하고 표현하는 이유는, 어차피 시간 복잡도가 완벽하게 계산되지 않기 때문에 상수를 제외하고 표현하는 것이 일반적입니다.  
시간 복잡도가 완벽하지 않기 때문에 시간 복잡도를 계산할 때 쓸모없는 행동(정확히 몇 번 실행되는지 세고 있는 행동 등)을 하지 않기 위함입니다.  
위에서 언급했던 것처럼 매우 큰 상수가 붙어서 실행 시간에 지장을 줄 정도라면 $$1,000n$$ 처럼 표현하기도 합니다.
{: .prompt-info }

> 따라서 같은 시간 복잡도를 갖는 알고리즘을 비교할 때, 이 알고리즘은 상수가 작다, 크다 라는 표현을 사용하기도 합니다.
{: .prompt-tip }

따라서 이 코드는 다음과 같이 시간 복잡도를 표기할 수 있습니다.

### Big-O Notation

* $$O(n)$$ - 아무리 느려도 $$n$$번 안에 실행이 끝납니다.
* $$O(n\sqrt{n})$$ - 아무리 느려도 $$n\sqrt{n}$$번 안에 실행이 끝납니다.
* $$O(n^2)$$ - 아무리 느려도 $$n^2$$번 안에 실행이 끝납니다.

### Big-Ω Notation

* $$\Omega(n)$$ - 아무리 빨라도 $$n$$번 이상 실행됩니다.
* $$\Omega(\sqrt{n})$$ - 아무리 빨라도 $$\sqrt{n}$$번 이상 실행됩니다.
* $$\Omega(1)$$ - 아무리 빨라도 상수 시간은 걸립니다.

### Big-θ Notation

* $$\Theta(n)$$ - 이 코드는 $$O(n)$$이면서 $$\Omega(n)$$입니다.

Big-θ Notation은 위 경우처럼 Big-O Notation과 Big-Ω Notation 두 표현법 모두 모순이 없을 때 사용할 수 있습니다.

상한선과 하한선이 모두 $$n$$ 이므로 이 코드는 항상 $$n$$번 실행된다는 것을 보장합니다.

### 시간 복잡도 계산 결과

따라서, 위 코드의 시간 복잡도는 $$O(n)$$, $$\Omega(n)$$, $$\Theta(n)$$ 입니다.

> 일반적으로 블로그에선 $$O(n)$$만 표기합니다.
{: .prompt-info }

## 예시 2

다음 코드를 보겠습니다.

```c
#include <stdio.h>

int main() {
    int n, m, sum = 0;
    scanf("%d%d", &n, &m);
    for (int i = 1; i <= n; ++i) {
        for (int j = 1; j <= m; ++j) {
            sum += i * j;
        }
    }
    printf("sum = %d", sum);
    return 0;
}
```

위 코드는 (1 * 1) + (1 * 2) + ... + (1 * m) + (2 * 1) + (2 * 2) + ... + (2 * m) + ... + (n * 1) + (n * 2) + ... + (n * m) 을 구하는 코드입니다.

코드에서 각 줄이 실행되는 횟수를 계산해 보겠습니다.

```c
#include <stdio.h>

int main() {
    int n, m, sum = 0;
    scanf("%d%d", &n, &m); // 1번
    for (int i = 1; i <= n; ++i) { // 이 포문은 n번 반복합니다.
        for (int j = 1; j <= m; ++j) { // 이 포문은 m번 반복합니다.
            // m번 반복하는 포문이 n번 반복되므로, 총 n * m번 반복됩니다.
            sum += i * j; // n * m번
        }
    }
    printf("sum = %d", sum); // 1번
    return 0;
}
```

위 코드는 총 $$1 + n + m + n \times m + 1 = n \times m + n + m + 2$$ 줄이 실행됩니다.

따라서, 이 코드의 시간 복잡도는 $$\Theta(nm)$$ 입니다.

> $$\Theta(nm + n + m)$$ 으로 표기하지 않는 이유는 $$n$$, $$m$$이 무한대(매우 큰 수)로 커지면 $$n + m$$은 무시해도 되는 수준이기 때문입니다.  
하지만 경우에 따라 $$\Theta(nm + n + m)$$으로 표현하기도 합니다.
{: .prompt-info }