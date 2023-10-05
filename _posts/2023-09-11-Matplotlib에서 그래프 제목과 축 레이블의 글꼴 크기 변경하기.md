---
title: Matplotlib에서 그래프 제목과 축 레이블의 글꼴 크기 변경하기
date: 2023-09-11 20:00:00 +0900
categories:
  - python
tags:
  - Matplotlib
---

## 기본적인 방법: `title()`과 `xlabel()`, `ylabel()` 메소드 사용하기

Matplotlib에서 그래프의 제목과 축 레이블의 글꼴 크기를 변경하려면 `title()`, `xlabel()`, `ylabel()` 메소드를 사용하여 `fontsize` 매개변수를 설정할 수 있습니다. 이 매개변수는 글꼴의 크기를 숫자로 지정합니다.

```python
import matplotlib.pyplot as plt

plt.title('제목', fontsize=20)
plt.xlabel('x축', fontsize=14)
plt.ylabel('y축', fontsize=14)
```

## 고급 방법: `rcParams` 설정 변경하기

글꼴 크기를 프로그램 전체에서 일괄적으로 변경하려면 `rcParams` 설정을 사용할 수 있습니다. `rcParams`는 Matplotlib 설정의 사전(dictionary) 형태입니다. 이 설정을 변경하면 모든 그래프에서 동일한 글꼴 크기를 사용할 수 있습니다.

```python
import matplotlib.pyplot as plt
import matplotlib as mpl

mpl.rcParams['font.size'] = 16
mpl.rcParams['axes.labelsize'] = 12
mpl.rcParams['xtick.labelsize'] = 10
mpl.rcParams['ytick.labelsize'] = 10
```

이 코드를 실행한 후에 그리는 모든 그래프는 지정한 글꼴 크기를 가집니다.

## 결론

Matplotlib을 사용할 때 그래프의 제목과 축 레이블의 글꼴 크기를 변경하는 방법은 두 가지입니다. 첫째, 각 그래프를 그릴 때 `fontsize` 매개변수를 설정하는 것이고, 둘째는 `rcParams` 설정을 변경하여 프로그램 전체의 글꼴 크기를 일괄적으로 변경하는 것입니다. 이 두 가지 방법을 통해 데이터 시각화의 명확성과 가독성을 높일 수 있습니다.