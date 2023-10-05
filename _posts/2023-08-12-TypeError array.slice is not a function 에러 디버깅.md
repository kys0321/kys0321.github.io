---
title: TypeError array.slice is not a function 에러 디버깅
date: 2023-08-12 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 타입에러
---
## 해결 방법 1: `slice`와 `for` 루프 사용

`slice` 메서드를 사용하여 배열을 나눌 수 있습니다. `for` 루프를 돌려서 `slice`를 적용하면 됩니다.

```javascript
function splitArray(array, size) {
  const result = [];
  for (let i = 0; i < array.length; i += size) {
    result.push(array.slice(i, i + size));
  }
  return result;
}
```

`slice`는 배열의 특정 부분을 새로운 배열로 만들어 반환합니다. `for` 루프는 배열을 순회하면서 `slice`를 적용합니다.

## 해결 방법 2: `reduce` 메서드 사용

`reduce` 메서드는 배열을 하나의 값으로 줄입니다. 여기서는 하위 배열의 배열을 만드는 것입니다.

```javascript
function splitArrayWithReduce(array, size) {
  return array.reduce((acc, val, i) => {
    const idx = Math.floor(i / size);
    if (!acc[idx]) {
      acc[idx] = [];
    }
    acc[idx].push(val);
    return acc;
  }, []);
}
```

`reduce`는 누적값(`acc`)와 현재 값(`val`), 그리고 인덱스(`i`)를 인자로 받습니다. `Math.floor(i / size)` 계산을 통해 현재 값이 어느 하위 배열에 들어가야 하는지 결정합니다.

## 해결 방법 3: `splice` 메서드 사용

`splice` 메서드는 배열에서 요소를 추가하거나 삭제할 수 있습니다. `splice`를 사용하면 원본 배열이 수정됩니다.

```javascript
function splitArrayWithSplice(array, size) {
  const result = [];
  while (array.length > 0) {
    result.push(array.splice(0, size));
  }
  return result;
}
```

`splice(0, size)`는 배열의 처음부터 `size`까지의 요소를 삭제하고, 삭제된 요소를 새로운 배열로 반환합니다.

## 결론

배열을 그룹으로 나누는 방법은 여러 가지가 있습니다. `slice`와 `for` 루프를 사용할 수도 있고, `reduce`나 `splice` 메서드를 사용할 수도 있습니다. 선택은 여러분의 필요에 따라 달라집니다. 이러한 방법들을 이해하고 활용하면 배열을 효율적으로 나눌 수 있습니다.