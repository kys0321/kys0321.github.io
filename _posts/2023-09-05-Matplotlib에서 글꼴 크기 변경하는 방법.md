---
title: Matplotlib에서 글꼴 크기 변경하는 방법
date: 2023-09-05 20:00:00 +0900
categories:
  - python
tags:
  - Matplotlib
---

## 개요
Matplotlib는 파이썬에서 그래프를 그릴 때 널리 사용되는 라이브러리입니다. 이 라이브러리를 사용하면 다양한 그래프와 차트를 쉽게 만들 수 있습니다. 그러나 그래프의 글꼴 크기를 변경하려면 어떻게 해야 할까요? 이 문제를 해결하기 위해 다음 내용을 자세히 살펴보겠습니다.

## 글꼴 크기를 변경하는 여러 가지 방법
### `rcParams`를 이용한 전역 설정
Matplotlib의 `rcParams`를 사용하면 전체 그래프에 대한 설정을 할 수 있습니다. 아래의 코드를 예로 들겠습니다.

```python
import matplotlib.pyplot as plt
plt.rcParams['font.size'] = 14
```

이렇게 하면 그 이후에 그리는 모든 그래프의 기본 글꼴 크기가 14로 설정됩니다.

### `fontsize` 인자를 이용한 개별 설정
개별 텍스트 요소에 대한 글꼴 크기를 변경하려면 `fontsize` 인자를 사용하면 됩니다. 예를 들어, x축과 y축의 레이블에 대한 글꼴 크기를 변경하려면 다음과 같이 할 수 있습니다.

```python
plt.xlabel('X-axis', fontsize=16)
plt.ylabel('Y-axis', fontsize=16)
```

### 에러와 해결책: `ValueError`
코드에서 글꼴 크기를 문자열로 입력하는 경우, `ValueError`라는 오류가 발생할 수 있습니다. 이럴 경우, 글꼴 크기를 숫자로 변경해 주어야 합니다.

## 결론
Matplotlib에서 글꼴 크기를 변경하는 것은 복잡하지 않습니다. 전역 설정으로는 `rcParams`를, 개별 설정으로는 `fontsize` 인자를 사용하여 쉽게 변경할 수 있습니다. 특히, `ValueError` 오류를 피하기 위해서는 글꼴 크기를 숫자로 지정해야 함을 기억해 주세요. 이렇게 하면 효과적으로 그래프의 가독성을 높일 수 있습니다.