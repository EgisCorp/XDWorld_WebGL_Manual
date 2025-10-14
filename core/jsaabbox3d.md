---
description: 지도 내 박스(육면체) 형태의 공강 위치를 사용하기 위한 API 입니다.
---

# JSAABBox3D

> Module.JSAABBox3D() API를 생성합니다.
>
> JSAABBox3D 생성 시 기본값 min, max(JSVector3D(0.0, 0.0, 0.0), JSVector3D(0.0, 0.0, 0.0)) 설정으로 설정 됩니다.

```javascript
let min = new Module.JSVector3D(129.14, 35.18, 100.0);
let max = new Module.JSVector3D(129.18, 35.189, 200.0);
let boxDefault = new Module.JSAABBox3D(); // Both min and max are JSVector3D(0.0, 0.0, 0.0)
let boxWithMinMax = new Module.JSAABBox3D(min, max);
```

## properties

| Name | Type                                | Description     |
| :--- | :---------------------------------- | :-------------- |
| min  | [JSVector3D](../core/jsvector3d.md) | 최소 좌표 위치. |
| max  | [JSVector3D](../core/jsvector3d.md) | 최대 좌표 위치. |
