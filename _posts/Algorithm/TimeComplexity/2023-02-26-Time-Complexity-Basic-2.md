---
author: Rn
title: "[Rn] 시간 복잡도 기본 (Time Complexity Basic) - Part 2"
date: 2023-02-26 12:18:01 +0900
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
- [시간 복잡도 기본 (Time Complexity Basic) - Part 3](https://thak1411.github.io/posts/Time-Complexity-Basic-3/)
- [시간 복잡도 기본 (Time Complexity Basic) - Part 4](https://thak1411.github.io/posts/Time-Complexity-Basic-4/)

---

## 시간 복잡도를 표현하는 방법

1. 빅 오 표기법 (Big-O Notation)
2. 빅 오메가 표기법 (Big-Ω Notation)
3. 빅 세타 표기법 (Big-θ Notation)

세 가지 말고도 Little-O Notation 등 다양한 표기법이 존재하지만, 이 글에서는 자주 사용되는 위 세 가지 표기법에 대해서만 다루겠습니다.

> 일반적으로 알고리즘 블로그를 보면 Big-O Notation으로 표현하는 것을 볼 수 있습니다. 하지만, 일반적으로 Big-θ Notation으로 표현하는 수치를 Big-O Notation으로 표현하는 경우가 많습니다.
{: .prompt-tip }

## Big-O Notation

Big-O Notation은 코드 실행 시간이 아무리 느려도 지금 예측하는 시간보다 항상 빠르다는 것을 의미합니다.

간단한 예시를 들면, 아무리 느려도 30초 안에 실행이 완료되는 코드가 있다고 가정해 보겠습니다.

이때, "이 코드는 30초 안에 동작한다" 라고 말할 수도 있지만, Big-O Notation에서는 "이 코드는 항상 100초보다 빠르게 동작한다" 라고 말할 수 있습니다.

Big-O Notation은 상한선을 의미합니다.

## Big-Ω Notation

Big-Ω Notation은 코드 실행 시간이 아무리 빠르더라도 지금 예측하는 시간보다 항상 느리다는 것을 의미합니다.

간단한 예시를 들면, 아무리 빠르더라도 30초가 지나고 실행이 완료되는 코드가 있다고 가정해 보겠습니다.

이때, "이 코드는 30초 이상 걸린다" 라고 말할 수도 있지만, Big-Ω Notation에서는 "이 코드는 항상 5초보다 느리게 동작한다" 라고 말할 수 있습니다.

Big-Ω Notation은 하한선을 의미합니다.

## Big-θ Notation

Big-θ Notation은 코드 실행 시간이 지금 예측하는 시간과 매우 유사하다는 것을 의미합니다.

간단한 예시를 들면, 아무리 빨라도 30초, 아무리 느려도 60초 정도 걸리는 코드가 있다고 가정해 보겠습니다.

이때, "이 코드는 30~60초 정도 걸린다" 라고 말할 수 있습니다.

Big-θ Notation은 상한선과 하한선을 모두 지킨다는 의미입니다.

조금 더 자세한 의미로는 같은 수치를 Big-O Notation과 Big-Ω Notation로 표현했을 때, 모순되지 않는 경우라고 생각할 수 있습니다.