---
description: 배경지도 객체를 관리하는 API.
---

# JSImageryProvider

> Module.[JSImageryProvider.Type](jsImageryProvider.md#jsimageryprovider.type)() API 생성.

```javascript
var naver = Module.NaverMap();		( nomal, satellite 지원 )
var daum = Module.DaumMap();		( nomal, satellite 지원 )
var google = Module.GoogleMap();	( nomal, terrain, vectorhybrid, satellitehybrid, satellite 지원 )
var bing = Module.BingMap();		( nomal, satellitehybrid, satellite 지원 )
var osm = Module.OpenStreetMap();	( nomal, terrain 지원 )
var arc = Module.ArcMap();			( nomal, terrain, vectorhybrid, satellite 지원 )
var mapbox = Module.MapBox();		( satellite 지원 )
var skymap = Module.SKYMap();		( 2012 ~ 2018, 2020 지원 )
var wmts = Module.WMTS();		
```

## properties

| Name            | Type                                                                          | Description              |
| --------------- | ----------------------------------------------------------------------------- | ------------------------ |
| provider        | [JSImageryProvider.Provider](JSImageryProvider.md#JSImageryProvider.provider) | 배경 영상 지도 타일링 정보설정.       |
| zeroLevel       | string                                                                        | 배경 영상 지도 이미지 LOD.        |
| quality         | string                                                                        | 배경 영상 지도 이미지 품질.         |
| [JSImageryProvider.Layername](JSImageryProvider.md#JSImageryProvider.Layername)       | string                                                                        | 배경 영상 지도 레이어명.           |
| zerolevelOffset | string                                                                        | 배경 영상 지도 이미지 LOD offset. |

### clear()

> 배경 영상 지도 초기화.

{% tabs %}
{% tab title="Information" %}
* Sample
  * function clearMap 참조
  * [샌드박스\_배경지도 설정](http://sandbox.dtwincloud.com/code/main.do?id=layer\_basemap)
  * [샌드박스\_WMTS](http://sandbox.dtwincloud.com/code/main.do?id=layer\_wmts)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.NaverMap().clear();
Module.DaumMap().clear();
Module.GoogleMap().clear();
Module.BingMap().clear();
Module.OpenStreetMap().clear();
Module.ArcMap().clear();
Module.MapBox().clear();
Module.SKYMap().clear();
Module.WMTS().clear();
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSImageryProvider.Type

> 배경 영상 지도 서버 옵션.

| Name            | Type   | Attributes | Default | Description                           |
| --------------- | ------ | ---------- | ------- | ------------------------------------- |
| NaverMap()      | object |            |         | Naver Map 배경 영상 지도 설정.                |
| DaumMap()       | object |            |         | Daum Map 배경 영상 지도 설정.                 |
| GoogleMap()     | object |            |         | Google Map 배경 영상 지도 설정.               |
| BingMap()       | object |            |         | Bing Map 배경 영상 지도 설정.                 |
| OpenStreetMap() | object |            |         | OpenStreet Map 배경 영상 지도 설정.           |
| ArcMap()        | object |            |         | ArcMap Map 배경 영상 지도 설정.               |
| MapBox()        | object |            |         | MapBox Map 배경 영상 지도 설정.               |
| SKYMap()        | object |            |         | SKY Map 배경 영상 지도 설정.                  |
| WMTS()          | object |            |         | WMTS(웹 맵 타일 서비스) 표준 프로토콜 배경 영상 지도 설정. |

#### JSImageryProvider.Layername

> 배경 영상 지도 레이어명.

| Name            | Type   | Attributes | Default | Description                           |
| --------------- | ------ | ---------- | ------- | ------------------------------------- |
| nomal      	  | string |            |         | 일반 지도.                |
| terrain         | string |            |         | 지형 등고선 지도.                 |
| vectorhybrid    | string |            |         | 벡터 하이브리드 지도.               |
| satellitehybrid | string |            |         | 영상 하이브리드 지도.                 |
| satellite 	  | string |            |         | 영상 지도.           |

#### JSImageryProvider.Provider

> 배경 영상 지도 서버 정보 옵션.

| Name          | Type                                             | Attributes | Default       | Description                        |
| ------------- | ------------------------------------------------ | ---------- | ------------- | ---------------------------------- |
| url           | string                                           |            |               | 요청 서버 URL 구성요소.                    |
| tileExtent    | [Rect2D](../etc/tag-list.md#rect2d-style-type)   |            |               | 지도 타일링 영역 설정(좌하단, 우상단).            |
| projection    | string                                           |            |               | 지도 원본 EPSG 코드.                     |
| resolutions   | array(number)                                    |            |               | 타일링 해상도.                           |
| matrixIds     | array(number)                                    |            |               | 타일링 레벨(해상도와 매칭).                   |
| tileSize      | number                                           | optional   | 256           | 타일에 가시화 이미지 사이즈 설정.                |
| serviceLevel  | [Range2D](../etc/tag-list.md#range2d-style-type) | optional   | min=0, max=18 | 최소, 최대 이미지 가시화 레벨 설정.              |
| vworldTileSet | boolean                                          | optional   | false         | 브이월드 타일구조로 타일링일 경우(true).          |
| indexOrder    | boolean                                          | optional   | true          | 타일 인덱싱 기준점(false: 좌하단, true: 좌상단). |
| boxRequest    | boolean                                          | optional   | false         | 인덱싱이 아닌 박스단위 요청일 경우(true).         |