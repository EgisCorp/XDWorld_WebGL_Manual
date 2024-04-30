---
description: JSSize3D 객체 생성 및 수정 기능 API. JSSize3D는 width, height, depth로 구성된 3차원 상의 크기를 정의.
---

# JSSize3D

| 변수명    | 자료형    | 프로퍼티 역할 |
| ------ | ------ | ------- |
| width  | number | 너비.      |
| height | number | 높이.      |
| depth  | number | 깊이.      |

```javascript
let width = 300;
let height = 200;
let depth = 100;

let size0 = new Module.JSSize3D();
let size1 = new Module.JSSize3D(width, height, depth);
```

### JSSize3D()

> width, height, depth는 0.0으로 자동 초기화.

### JSSize3D(width, height, depth)

| Name | Type | Description |
| :--- | :--- | :--- |
| width | number | 너비. |
| height | number | 높이. |
| depth | number | 깊이. |
