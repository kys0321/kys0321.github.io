---
title: Python argparse에서 선택적 위치 인자 사용하기
date: 2023-09-09 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬argparse
---

## argparse 라이브러리란?

Python에서 명령행 인터페이스를 쉽게 만들기 위해 사용하는 것이 `argparse` 라이브러리입니다. 이 라이브러리를 이용하면 프로그램을 실행할 때 다양한 옵션과 인자를 지정할 수 있습니다.

## 선택적 위치 인자 설정 방법

`argparse`에서 선택적 위치 인자를 설정하려면 `nargs` 옵션을 사용하면 됩니다. `nargs`는 'Number of Arguments'의 줄임말로, 이 옵션을 통해 얼마나 많은 인자를 받을 것인지 설정할 수 있습니다.

```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument('filename', nargs='?', default='default.txt')
args = parser.parse_args()

print(f"파일 이름: {args.filename}")
```

이 코드를 실행하면, 사용자가 파일 이름을 지정하지 않아도 `default.txt`라는 기본값이 사용됩니다.

### 에러: `NoneType` Error

만약 `nargs`를 잘못 설정하게 되면, 다음과 같은 에러가 발생할 수 있습니다.

```
TypeError: 'NoneType' object is not iterable
```

이 에러는 `nargs`가 잘못 설정되어 `argparse`가 올바른 형태의 데이터를 받지 못했을 때 발생합니다. 이 문제를 해결하기 위해서는 `nargs`의 값을 올바르게 설정해야 합니다.

## 실제 사용 예시

다음은 간단한 파일 복사 유틸리티를 만드는 예시입니다.

```python
import argparse
import shutil

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument('source', help='원본 파일 경로')
    parser.add_argument('destination', nargs='?', default='copy.txt', help='복사될 파일 경로')
    args = parser.parse_args()

    shutil.copy(args.source, args.destination)
    print(f"{args.source} 파일을 {args.destination} (으)로 복사했습니다.")

if __name__ == "__main__":
    main()
```

이 프로그램은 `source` 파일을 `destination` 파일로 복사합니다. `destination`은 선택적 인자이며, 지정되지 않으면 `copy.txt`로 기본 설정됩니다.

## 결론

`argparse` 라이브러리는 Python에서 명령행 인터페이스를 쉽게 만들 수 있게 도와줍니다. 선택적 위치 인자를 사용하려면 `nargs` 옵션을 적절히 설정해야 하며, 이를 통해 더 유연한 프로그램을 만들 수 있습니다.