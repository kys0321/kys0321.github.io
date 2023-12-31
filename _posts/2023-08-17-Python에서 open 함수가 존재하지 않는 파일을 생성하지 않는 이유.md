---
title: Python에서 open 함수가 존재하지 않는 파일을 생성하지 않는 이유
date: 2023-08-17 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬open
---

## 개요
Python에서 파일을 다루기 위해 `open` 함수를 사용하곤 합니다. 그러나 이 함수를 사용할 때, 파일이 존재하지 않으면 자동으로 파일을 생성하지 않는 경우가 있습니다. 이러한 현상이 발생하는 주된 이유와 해결 방안을 살펴보겠습니다.

## 파일 열기 모드와 그 차이점
Python의 `open` 함수를 호출할 때는 다양한 파일 열기 모드('r', 'w', 'a', 'x' 등)를 지정할 수 있습니다. 이 모드에 따라 파일의 존재 여부와 작동 방식이 달라집니다.

- `r` (읽기 모드): 파일이 존재하지 않을 경우, `FileNotFoundError` 에러가 발생합니다.
- `w` (쓰기 모드): 파일이 존재하지 않을 경우, 새로운 파일을 생성합니다.
- `a` (추가 모드): 파일이 존재하지 않을 경우, 새로운 파일을 생성합니다.
- `x` (배타적 생성 모드): 파일이 이미 존재하면 에러가 발생하고, 존재하지 않으면 새로운 파일을 생성합니다.

따라서, 'r' 모드로 파일을 열려고 시도하면 파일이 존재하지 않을 때 에러가 발생하는 것입니다.

## 해결 방안
파일이 존재하지 않을 때도 자동으로 파일을 생성하고 싶다면, `w` 또는 `a` 모드를 사용해야 합니다. 다만, 이 두 모드는 파일이 이미 존재할 경우 기존 내용을 덮어쓰거나 추가합니다.

```python
with open('newfile.txt', 'w') as f:
    f.write("Hello, World!")
```

이 코드는 `newfile.txt`가 존재하지 않을 경우, 새로운 파일을 생성하고 "Hello, World!"라는 텍스트를 입력합니다.

## 주의사항
`w` 모드는 기존에 존재하는 파일의 내용을 모두 지워버리므로, 데이터 손실을 피하기 위해 신중하게 사용해야 합니다.

## 결론
Python의 `open` 함수는 파일 열기 모드에 따라 자동으로 파일을 생성하지 않을 수 있습니다. 특히 'r' 모드를 사용할 때는 이러한 현상이 발생하므로, 자동으로 파일을 생성하고 싶다면 `w` 또는 `a` 모드를 사용해야 합니다.