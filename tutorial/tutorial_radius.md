---
description: 반경 측정 튜토리얼
---

# 반경 측정

> 네이버, 다음, Google, BingMap, OpenStreetMap, ArcMap, MapBox, SKYMap 지도를 배경지도로 설정.

```javascript
var naver = Module.NaverMap();		( nomal, satellite 지원 )
var daum = Module.DaumMap();		( nomal, satellite 지원 )
var google = Module.GoogleMap();	( nomal, terrain, vectorhybrid, satellitehybrid, satellite 지원 )
var bing = Module.BingMap();		( nomal, satellitehybrid, satellite 지원 )
var osm = Module.OpenStreetMap();	( nomal, terrain 지원 )
var arc = Module.ArcMap();			( nomal, terrain, vectorhybrid, satellite 지원 )
var mapbox = Module.MapBox();		( satellite 지원 )
var skymap = Module.SKYMap();		( 2012 ~ 2018, 2020 지원 )
```

## Layername

> 배경 영상 지도 레이어명.

| Name            | Type   | Attributes | Default | Description                           |
| --------------- | ------ | ---------- | ------- | ------------------------------------- |
| nomal      	  | string |            |         | 일반 지도.                |
| terrain         | string |            |         | 지형 등고선 지도.                 |
| vectorhybrid    | string |            |         | 벡터 하이브리드 지도.               |
| satellitehybrid | string |            |         | 영상 하이브리드 지도.                 |
| satellite 	  | string |            |         | 영상 지도.           |

```javascript
var naver = Module.NaverMap();
naver.layername = "satellite";

var daum = Module.DaumMap();
naver.layername = "satellite";

var google = Module.GoogleMap();
naver.layername = "satellitehybrid";

var bing = Module.BingMap();
naver.layername = "satellitehybrid";

var osm = Module.OpenStreetMap();
naver.layername = "nomal";

var arc = Module.ArcMap();
naver.layername = "vectorhybrid";

var mapbox = Module.MapBox();
naver.layername = "satellite";

var skymap = Module.SKYMap();
naver.layername = "2020";
```