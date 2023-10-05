---
title: Extension Rejected Due to Could not find or load Firebase core component 해결 방안
date: 2023-08-03 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 원인: Firebase 초기화 문제

이 오류는 대부분 Firebase를 초기화(initialize)하는 과정에서 발생합니다. Firebase SDK를 사용하려면, 초기에 몇 가지 설정 작업이 필요한데, 이 작업이 제대로 이루어지지 않으면 위와 같은 오류 메시지가 나타납니다. 주로 이런 문제는 다음과 같은 원인에서 비롯됩니다.

1. **Firebase 설정 정보 누락**: `firebase.initializeApp()` 함수를 호출할 때 필요한 설정 정보가 누락되었을 가능성이 있습니다.
2. **라이브러리 누락**: 필요한 Firebase 라이브러리가 포함되지 않았거나, 라이브러리 버전이 맞지 않을 수 있습니다.

## 해결 방법 1: 설정 정보 확인

첫 번째 해결 방법은 `firebase.initializeApp()` 함수에 전달되는 설정 정보를 확인하는 것입니다. 이 설정 정보는 Firebase 콘솔에서 프로젝트를 생성하면 얻을 수 있으며, 다음과 같은 형태로 이루어져 있습니다.

```javascript
var firebaseConfig = {
  apiKey: "your-api-key",
  authDomain: "your-auth-domain",
  projectId: "your-project-id",
  storageBucket: "your-storage-bucket",
  messagingSenderId: "your-messaging-sender-id",
  appId: "your-app-id"
};
```

## 해결 방법 2: 라이브러리 확인

라이브러리가 제대로 포함되어 있는지 확인해야 합니다. Firebase SDK는 여러 개의 라이브러리로 나누어져 있습니다. 따라서, 프로젝트에 필요한 라이브러리가 모두 포함되어 있는지 확인하십시오. 예를 들어, 실시간 데이터베이스를 사용한다면 `firebase-database` 라이브러리가 필요합니다.

## 결론: 문제 해결을 위한 체계적 접근

Firebase SDK의 `Could not find or load Firebase core component` 오류는 초기화 과정에서 주로 발생합니다. 이 오류를 해결하기 위해서는 설정 정보와 라이브러리를 체계적으로 확인해야 합니다. 이 두 가지 원인을 주의 깊게 살펴보면 문제를 해결할 수 있는 가능성이 큽니다.