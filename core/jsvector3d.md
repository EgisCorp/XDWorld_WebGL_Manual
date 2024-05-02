---
description: 지도 내 3차원 좌표와 관련된 기능을 관리하기 위한 API 입니다.
---

# JSVector3D

> Module.JSVector3D() API를 생성합니다.
>
> JSVector3D 생성 시 기본값 Longitude, Latitude, Altitude(0, 0, 0) 설정.

```javascript
var position = new Module.JSVector3D(129.128265, 35.171834, 100.0);

var position = new Module.JSVector3D();
```

## properties

| Name      | Type   | Description              |
| :-------- | :----- | :----------------------- |
| Longitude | number | 좌표 경도 (degrees 단위) |
| Latitude  | number | 좌표 위도 (degrees 단위) |
| Altitude  | number | 좌표 고도 (meter 단위)   |
