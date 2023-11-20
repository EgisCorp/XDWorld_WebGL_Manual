---
description: 3차원 공간에서 박스(육면체) 형태의 공간 위치를 정의하고 관련 API를 호출합니다.
---

# JSAABBox3D

```javascript
let min = new Module.JSVector3D(129.14, 35.18, 100.0);
let max = new Module.JSVector3D(129.18, 35.189, 200.0);

let boxDefault = new Module.JSAABBox3D(); // min, max 모두 JSVector3D(0.0, 0.0, 0.0)

let boxWithMinMax = new Module.JSAABBox3D(min, max);
```
