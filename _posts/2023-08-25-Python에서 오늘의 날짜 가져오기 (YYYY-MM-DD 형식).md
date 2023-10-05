---
title: Python에서 오늘의 날짜 가져오기 (YYYY-MM-DD 형식)
date: 2023-08-25 20:00:00 +0900
categories:
  - python
tags:
  - 파이썬날짜
---

## datetime 모듈 이용하기

Stackoverflow에 올라온 글을 보면, Python에서 날짜를 가져오려면 어떻게 해야 하는지 여러 방법이 설명되어 있습니다. 그 중 하나는 `datetime` 모듈을 이용하는 방법입니다. 이 모듈은 Python 표준 라이브러리에 포함되어 있으므로, 따로 설치할 필요가 없습니다.

다음은 `datetime` 모듈을 사용해서 오늘의 날짜를 YYYY-MM-DD 형식으로 가져오는 코드 예시입니다.

```python
from datetime import datetime

# 현재 날짜와 시간을 가져옵니다.
now = datetime.now()

# 날짜를 YYYY-MM-DD 형식으로 출력합니다.
print(now.strftime("%Y-%m-%d"))
```

여기서 `strftime`은 "string format time"의 약자로, 날짜와 시간을 원하는 형식의 문자열로 바꿔주는 함수입니다. `%Y`는 년도를, `%m`은 월을, `%d`는 일을 나타냅니다.

## 다른 방법: date 함수 사용하기

`datetime` 모듈 내에는 `date` 함수도 있습니다. 이 함수를 사용하면 시간 정보는 무시하고 날짜 정보만을 가져올 수 있습니다.

```python
from datetime import date

# 현재 날짜를 가져옵니다.
today = date.today()

# 날짜를 YYYY-MM-DD 형식으로 출력합니다.
print(today)
```

이 방법은 시간 정보가 필요하지 않을 때 유용합니다.

## 주의할 점: 시간대(Timezone)

`datetime` 모듈을 사용할 때 주의해야 할 점은 시간대입니다. 위의 예시 코드들은 시스템의 로컬 시간을 사용합니다. 그래서 다른 시간대에서 실행하면 결과가 달라질 수 있습니다. 시간대를 고려해야 하는 경우에는 `pytz` 라이브러리를 사용할 수 있습니다.

## 정리

Python에서 날짜를 가져오는 방법은 여러 가지가 있지만, 가장 흔하게 사용되는 방법은 `datetime` 모듈을 이용하는 것입니다. 이를 통해 원하는 형식으로 날짜와 시간 정보를 쉽게 가져올 수 있습니다.