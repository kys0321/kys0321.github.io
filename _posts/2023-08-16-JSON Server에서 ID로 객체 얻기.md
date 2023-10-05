---
title: JSON Server에서 ID로 객체 얻기
date: 2023-08-16 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 제이슨서버
---

## 개요
JSON Server는 개발 중에 REST API를 가상으로 생성하여 사용할 수 있는 도구입니다. 여러분이 데이터를 테스트하거나 프론트엔드 작업을 하면서 실제 백엔드 서버가 없을 때 유용하게 사용됩니다. 이 글에서는 JSON Server를 사용해 ID로 특정 객체를 얻는 방법에 대해 자세히 알아보겠습니다.

## 기본 사용법
JSON Server에서 ID를 이용해 객체를 얻기 위해서는 HTTP `GET` 메서드를 사용합니다. 예를 들어, `posts`라는 이름의 리소스가 있고, 해당 리소스 내에 ID가 1인 객체를 얻고 싶다면 다음과 같이 진행합니다.

1. **JSON 파일 생성**: 먼저 `db.json`이라는 파일을 생성하고, `posts` 리소스와 그에 속한 객체들을 정의합니다.
    ```json
    {
      "posts": [
        {
          "id": 1,
          "title": "Hello World"
        },
        {
          "id": 2,
          "title": "Goodbye World"
        }
      ]
    }
    ```
  
2. **서버 실행**: 터미널에서 `json-server --watch db.json` 명령어를 실행하여 서버를 구동합니다.

3. **HTTP 요청**: 웹 브라우저나 Postman 같은 도구를 사용하여 `http://localhost:3000/posts/1`로 HTTP `GET` 요청을 보냅니다.

### 응답 예시
```
{
  "id": 1,
  "title": "Hello World"
}
```

## 주의사항
- **ID는 유일해야 함**: 같은 리소스 내에서 ID는 유일한 값을 가져야 합니다. 중복된 ID가 있을 경우 예상치 못한 문제가 발생할 수 있습니다.
- **Port 충돌**: 다른 애플리케이션과 Port가 충돌하는 경우, `--port` 옵션을 이용해 포트를 변경할 수 있습니다. 예: `json-server --watch db.json --port 4000`

## 결론
JSON Server를 사용하여 ID를 통해 객체를 얻는 것은 간단합니다. `GET` 요청을 통해 원하는 객체의 정보를 쉽게 얻을 수 있으며, 이를 위해선 JSON 파일 설정과 서버의 실행이 필요합니다. 이 방법은 백엔드 서버가 아직 구축되지 않았거나 테스트 목적으로 사용될 때 특히 유용합니다.