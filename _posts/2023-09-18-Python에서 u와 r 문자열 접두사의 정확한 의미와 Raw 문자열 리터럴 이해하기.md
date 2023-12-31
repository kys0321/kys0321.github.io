---
title: Python에서 u와 r 문자열 접두사의 정확한 의미와 Raw 문자열 리터럴 이해하기
date: 2023-09-18 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬문자열
---

## u와 r 접두사란 무엇인가?

Python에서 문자열을 생성할 때 다양한 방법이 있습니다. 그 중에서도 `u`와 `r` 이라는 접두사(prefix)를 사용할 수 있습니다. 접두사란 문자열 앞에 붙는 특별한 기호입니다. `u`는 Unicode 문자열을, `r`은 Raw 문자열을 만듭니다.

### u 접두사와 Unicode

`u` 접두사는 문자열이 Unicode 문자열임을 나타냅니다. Python 2에서는 이 접두사를 사용하여 Unicode 문자열을 명시적으로 만들 수 있습니다. 하지만 Python 3에서는 모든 문자열이 기본적으로 Unicode이므로 `u` 접두사가 필요 없습니다.

### r 접두사와 Raw 문자열

`r` 접두사는 Raw 문자열을 만듭니다. 일반 문자열에서는 `\n`, `\t` 등의 이스케이프 시퀀스(escape sequence)가 특별한 기능을 합니다. 예를 들어, `\n`은 줄바꿈을 의미합니다. 그러나 Raw 문자열에서는 이러한 이스케이프 시퀀스가 일반 텍스트로 처리됩니다. 즉, `r'\n'`은 문자열 안에서 두 개의 문자, 백슬래시(`\`)와 `n`으로 저장됩니다.

## 왜 이 접두사가 필요한가?

### Unicode 문자열의 중요성

Unicode는 세계 각국의 다양한 언어와 기호를 표현할 수 있는 국제 표준입니다. 따라서 다양한 언어를 처리할 때 Unicode 문자열이 필요합니다.

### Raw 문자열의 활용

Raw 문자열은 주로 정규 표현식(regular expression) 같은 곳에서 사용됩니다. 정규 표현식에서는 다양한 이스케이프 시퀀스가 사용되므로, 이를 그대로 표현하기 위해 Raw 문자열이 사용됩니다.

## 사용 예시와 주의점

### Unicode 문자열 사용 예

Python 2에서는 다음과 같이 사용합니다.

```python
text = u"안녕하세요"
```

Python 3에서는 다음과 같이 사용할 수 있습니다.

```python
text = "안녕하세요"
```

### Raw 문자열 사용 예

```python
import re
pattern = r"\d+"
```

여기에서 `\d+`는 숫자 하나 이상을 의미하는 정규 표현식입니다.

### 주의점

- `u` 접두사는 Python 3에서는 필요하지 않습니다.
- `r` 접두사를 사용할 때 마지막에 백슬래시(`\`)를 사용하면 SyntaxError가 발생합니다.

## 결론

`u`와 `r` 접두사는 문자열을 다룰 때 유용한 도구입니다. `u`는 다양한 언어와 기호를 처리할 때, `r`은 이스케이프 시퀀스를 그대로 표현할 때 사용됩니다. 이러한 접두사를 이해하고 올바르게 사용하면 Python 프로그래밍이 더욱 효율적이게 됩니다.