---
title: Express Validator와 XML 입력의 유효성 검사 문제
date: 2023-08-02 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Validator
---

## Express Validator가 무엇인가요?

Express Validator는 Node.js와 Express를 사용할 때 요청의 유효성을 검사하는 미들웨어입니다. 여기서 미들웨어란, 서버와 클라이언트 사이에서 데이터를 처리하는 소프트웨어 구성 요소를 의미합니다. Express Validator는 주로 JSON 형식의 데이터를 검사하는 데 사용됩니다.

## 왜 XML 입력에 문제가 생기는가?

`express-validator`는 기본적으로 JSON 데이터를 유효성 검사하도록 설계되어 있습니다. XML(XML Markup Language)은 JSON과 다른 데이터 형식으로, 이러한 차이 때문에 `express-validator`가 XML 데이터에서 누락된 필드를 감지하지 못하는 경우가 있습니다.

## 문제의 원인은 무엇인가?

XML 데이터를 처리할 때, `express-validator`는 `req.body` 객체에 접근합니다. 하지만 XML 파싱 라이브러리를 사용하지 않으면, `req.body`는 비어있거나 올바르지 않을 수 있습니다. 이러한 상황에서 `express-validator`가 필드를 제대로 검사할 수 없기 때문에, 유효성 검사에서 누락된 필드를 감지하지 못하게 됩니다.

## 어떻게 해결할 수 있을까?

이 문제를 해결하기 위해서는 별도의 XML 파싱 라이브러리를 사용해 `req.body`를 적절히 설정해야 합니다. 그 후에 `express-validator`를 사용하면, 누락된 필드도 제대로 감지할 수 있습니다. 예를 들어, `xml2js`와 같은 라이브러리를 사용하면 이 문제를 해결할 수 있습니다.

## 결론

`express-validator`는 기본적으로 JSON 데이터에 최적화되어 있어, XML 데이터에서는 제대로 동작하지 않을 수 있습니다. 이를 해결하기 위해선 별도의 XML 파싱 라이브러리를 사용하여 `req.body`를 설정한 후, 유효성 검사를 진행해야 합니다. 이렇게 하면 문제없이 유효성 검사를 수행할 수 있습니다.