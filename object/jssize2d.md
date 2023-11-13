---
description: JSSize2D 객체 생성 및 수정 기능 API. JSSize2D는 width, height로 구성된 2차원 상의 크기를 정의.
---

# JSSize2D

| 변수명    | 자료형    | 프로퍼티 역할 |
| ------ | ------ | ------- |
| width  | double | 너비.      |
| height | double | 높이.      |
| scale  | double | 비율.      |

```javascript
let width = 300;
let height = 200;
let scale = 1.0;

let size0 = new Module.CJSSize2D();
let size1 = new Module.CJSSize2D(width, height);
let size2 = new Module.CJSSize2D(width, height, scale);
```

### CJSSize2D()

> width, height는 0.0, scale은 1.0으로 자동 초기화.

### CJSSize2D(width, height)

> scale은 1.0으로 자동 초기화.

| Name | Type | Description |
| :--- | :--- | :--- |
| width | double | 너비. |
| height | double | 높이. |

### CJSSize2D(width, height, scale)

| Name | Type | Description |
| :--- | :--- | :--- |
| width | double | 너비. |
| height | double | 높이. |
| scale | double | 비율. |
