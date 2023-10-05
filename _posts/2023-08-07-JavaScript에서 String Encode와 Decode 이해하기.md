---
title: JavaScript에서 String Encode와 Decode 이해하기
date: 2023-08-07 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트인코딩
---

## String Encoding 이란?

String Encoding이란 특수 문자나 공백 등을 안전한 형태로 변환하는 과정을 의미합니다. 이렇게 하면 웹 브라우저나 서버가 오류 없이 데이터를 처리할 수 있습니다. JavaScript에서는 주로 `encodeURIComponent`나 `encodeURI` 함수를 사용합니다.

## String Decoding 이란?

반대로 String Decoding은 인코딩된 문자열을 원래의 형태로 되돌리는 과정입니다. JavaScript에서는 `decodeURIComponent`나 `decodeURI` 함수를 사용해서 이 작업을 수행합니다.

## 문제상황: JavaScript에서 `stringEncoded`로 인코딩된 문자열 해독하기

웹 개발을 하다 보면 종종 다른 언어로 작성된 코드와 호환성을 유지해야 하는 상황이 발생합니다. 이럴 때 `stringEncoded`로 인코딩된 문자열을 JavaScript에서 어떻게 해독할지에 대한 문제가 발생할 수 있습니다.

## 해결방법: `unescape` 함수 사용

이 문제를 해결하는 가장 간단한 방법은 JavaScript 내장 함수인 `unescape`를 사용하는 것입니다. 이 함수는 인코딩된 문자열을 원래 상태로 되돌립니다.

```javascript
const decodedString = unescape(encodedString);
```

## 주의사항: `unescape`와 `decodeURIComponent` 차이점

물론, `unescape` 함수는 현대의 웹 표준에서는 권장되지 않습니다. 그러나 `stringEncoded`와 같은 특별한 인코딩을 해독할 필요가 있는 경우에는 유용할 수 있습니다. 일반적인 경우에는 `decodeURIComponent`를 사용하는 것이 더 안전하고 표준적입니다.

## 에러 예외 처리: `URIError: URI malformed`

때로는 디코딩 과정에서 문제가 발생할 수 있습니다. 이럴 때 자주 보게 되는 에러는 `URIError: URI malformed`입니다. 이 에러는 문자열이 올바르게 인코딩되지 않았을 때 발생하므로, 디코딩을 시도하기 전에 문자열이 올바르게 인코딩되었는지 확인해야 합니다.

## 결론

문자열 인코딩과 디코딩은 웹 개발에서 중요한 작업 중 하나입니다. JavaScript에서는 이를 위한 여러 함수가 제공되므로, 상황에 맞는 함수를 선택해서 사용하면 됩니다. 특별한 경우에는 `unescape` 함수도 유용하게 사용할 수 있습니다.