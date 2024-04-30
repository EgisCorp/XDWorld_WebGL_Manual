---
description: JSLine3D 객체 생성 및 수정 기능 API. JSLine3D는 start, end로 구성된 3차원 상의 라인을 정의.
---

# JSLine3D

<table><thead><tr><th width="255">변수명</th><th width="244.33333333333331">자료형</th><th>프로퍼티 역할</th></tr></thead><tbody><tr><td>start</td><td><a href="../core/jsvector3d.md">JSVector3D</a></td><td>라인의 시작 지점.</td></tr><tr><td>end</td><td><a href="../core/jsvector3d.md">JSVector3D</a></td><td>라인의 끝 지점.</td></tr></tbody></table>

```javascript
let start = new Module.JSVector3D(129.14, 35.18, 100.0);
let end = new Module.JSVector3D(129.18, 35.189, 200.0);

let lineDefault = new Module.JSLine3D();
let lineWithStartEnd = new Module.JSLine3D(start, end);
```



#### JSLine3D()

> start, end는 JSVector3D(0.0, 0.0, 0.0)으로 자동 초기화.

#### JSLine3D(start, end)

| Name  | Type                                | Description |
| ----- | ----------------------------------- | ----------- |
| start | [JSVector3D](../core/jsvector3d.md) | 라인의 시작 지점.  |
| end   | [JSVector3D](../core/jsvector3d.md) | 라인의 끝 지점.   |
