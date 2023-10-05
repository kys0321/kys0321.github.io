---
title: Google Maps API에서 마커 색상 변경하기
date: 2023-08-14 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 구글맵API
---

## 속성 기반으로 마커 색상을 변경하는 방법

Google Maps API를 사용하면 지도에 마커를 추가할 수 있습니다. 여러분이 더 나아가 원한다면, 이 마커들의 색상을 특정 속성에 따라 다르게 설정할 수도 있습니다. 예를 들어, 여러 지점의 온도나 혼잡도 등에 따라 색상을 변경하고 싶을 수 있습니다.

### 준비사항
우선 Google Maps API를 사용하려면 HTML, CSS, 그리고 JavaScript의 기본 지식이 필요합니다. 이러한 기술들을 사용해 웹 페이지를 만들고, 그 안에 Google Maps를 삽입할 것입니다.

### 마커 생성과 색상 설정
Google Maps API에서 마커를 생성할 때, `icon`이라는 옵션을 사용해서 마커의 색상을 지정할 수 있습니다. 이 `icon` 옵션 안에는 `path`, `fillColor`, `fillOpacity`, `strokeWeight` 등 여러 설정이 가능합니다.

```javascript
const marker = new google.maps.Marker({
  position: myLatLng,
  map: map,
  icon: {
    path: google.maps.SymbolPath.CIRCLE,
    fillColor: 'red',
    fillOpacity: 0.8,
    strokeWeight: 0
  }
});
```

### 조건부 색상 설정

이제 특정 조건에 따라 마커의 색상을 변경하고 싶다면 어떻게 해야 할까요? 그럴 때는 JavaScript의 조건문을 사용할 수 있습니다.

```javascript
let fillColor;
if (propertyValue > 10) {
  fillColor = 'red';
} else {
  fillColor = 'green';
}

const marker = new google.maps.Marker({
  position: myLatLng,
  map: map,
  icon: {
    path: google.maps.SymbolPath.CIRCLE,
    fillColor: fillColor,
    fillOpacity: 0.8,
    strokeWeight: 0
  }
});
```

이 코드 예시에서는 `propertyValue`라는 변수가 10보다 크면 색상을 빨간색으로, 그렇지 않으면 녹색으로 설정합니다.

### `Uncaught TypeError: Cannot read properties of undefined (reading 'maps')`
주의: 위의 코드를 사용할 때 종종 발생하는 오류 중 하나는 `Uncaught TypeError: Cannot read properties of undefined (reading 'maps')`입니다. 이 오류는 Google Maps API가 아직 로딩되지 않았을 때 발생합니다. API를 불러오는 코드가 페이지의 하단에 위치하거나 `async` 옵션이 설정되어 있을 경우 이러한 문제가 발생할 수 있습니다. 이를 해결하기 위해서는 API 로딩 코드를 페이지의 상단에 배치하거나, `async` 옵션을 삭제해야 할 수 있습니다.

이렇게 하면 특정 속성에 따라 마커의 색상을 쉽게 변경할 수 있습니다. 이 방법을 통해 사용자에게 더 많은 정보를 직관적으로 전달할 수 있습니다.