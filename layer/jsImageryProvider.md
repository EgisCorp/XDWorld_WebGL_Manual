---
description: 지도 내 배경지도를 관리하기 위한 api 입니다.
---

# JSImageryProvider

> Module.[Type](jsImageryProvider.md#type)() API를 생성합니다.

```javascript
var google = Module.GoogleMap();    ( supports: normal, terrain, vectorhybrid, satellitehybrid, satellite )
var osm = Module.OpenStreetMap();   ( supports: normal )
var arc = Module.ArcMap();          ( supports: normal, terrain, vectorhybrid, satellite )
var mapbox = Module.MapBox();       ( supports: normal, satellite )
var wmts = Module.WMTS();
```

## Properties

| Name                                        | Type                                      | Description                     	|
| ------------------------------------------- | ----------------------------------------- | ----------------------------------- |
| [layername](jsImageryProvider.md#layername) | string                                    | 배경 영상 지도 레이어명.          			|
| provider                                    | [Provider](jsImageryProvider.md#provider) | 배경 영상 지도 타일링 정보설정.   				|
| layerName                                   | string                                    | 배경 영상 지도 레이어명.         			|
| quality                                     | string                                    | 배경 영상 지도 이미지 품질.       			|
| zeroLevel                                   | string                                    | 배경 영상 지도 이미지 LOD.        			|
| zerolevelOffset                             | string                                    | 배경 영상 지도 이미지 LOD offset. 			|
| maxLevel                                    | number                                    | 배경 영상 지도 최대 레벨.         			|
| minLevel                                    | number                                    | 배경 영상 지도 최소 레벨.         			|
| apikey                                      | string                                    | 배경 영상 지도 apikey.         			|
	
## Function

### clear()

> 배경 영상을 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   function clearMap 참조.
    -   [Sandbox_Base Map Setting](https://sandbox.egiscloud.com/code/main.do?id=layer_basemap)
    -   [Sandbox_WMTS](https://sandbox.egiscloud.com/code/main.do?id=layer_wmts)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.GoogleMap().clear();
Module.OpenStreetMap().clear();
Module.ArcMap().clear();
Module.MapBox().clear();
Module.WMTS().clear();
```

{% endtab %}
{% endtabs %}

### refresh()

> 배경 영상을 새로 고침 합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}

{% tab title="Template" %}

```javascript
Module.GoogleMap().refresh();
Module.OpenStreetMap().refresh();
Module.ArcMap().refresh();
Module.MapBox().refresh();
Module.WMTS().refresh();
```

{% endtab %}
{% endtabs %}

### setblank()

> 배경 영상에서 빈 타일 공백 이미지를 설정합니다.
>
> 256 \* 256 검은색 이미지로 지정합니다.
>
> 적용 후 refresh() 실행해 주시기 바랍니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}

{% tab title="Template" %}

```javascript
Module.GoogleMap().setblank();
Module.OpenStreetMap().setblank();
Module.ArcMap().setblank();
Module.MapBox().setblank();
Module.WMTS().setblank();
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### Type

> 배경 영상 지도 서버 옵션.

| Name            | Type   | Description                                                |
| --------------- | ------ | ---------------------------------------------------------- |
| GoogleMap()     | object | Google Map 배경 영상 지도 설정.                            |
| OpenStreetMap() | object | OpenStreet Map 배경 영상 지도 설정.                        |
| ArcMap()        | object | ArcMap Map 배경 영상 지도 설정.                            |
| MapBox()        | object | MapBox Map 배경 영상 지도 설정.                            |
| WMTS()          | object | WMTS(웹 맵 타일 서비스) 표준 프로토콜 배경 영상 지도 설정. |

#### LayerName

> Background video map layer name.

| Name            | Type   | Description           |
| --------------- | ------ | --------------------- |
| normal          | string | 일반 지도.            |
| terrain         | string | 등고선 지도.          |
| vectorhybrid    | string | 벡터 하이브리드 지도. |
| satellitehybrid | string | 영상 하이브리드 지도. |
| satellite       | string | 영상 지도.            |
| cadastral       | string | 지적편집도.           |

#### Provider

> Background video map server information option.

| Name          | Type                                             | Attributes | Default       | Description                                      |
| ------------- | ------------------------------------------------ | ---------- | ------------- | ------------------------------------------------ |
| url           | string                                           |            |               | 요청 서버 URL 구성요소.                          |
| tileExtent    | [Rect2D](../etc/tag-list.md#rect2d-style-type)   |            |               | 지도 타일링 영역 설정(좌하단, 우상단).           |
| gridSubset    | [Rect2D](../etc/tag-list.md#rect2d-style-type)   |            |               | 데이터 최소/최대 영역 설정(좌하단, 우상단).      |
| projection    | string                                           |            |               | 지도 원본 EPSG 코드.                             |
| resolutions   | array(number)                                    |            |               | 타일링 해상도.                                   |
| matrixIds     | array(number)                                    |            |               | 타일링 레벨(해상도와 매칭).                      |
| tileSize      | number                                           | optional   | 256           | 타일에 가시화 이미지 사이즈 설정.                |
| serviceLevel  | [Range2D](../etc/tag-list.md#range2d-style-type) | optional   | min=0, max=18 | 최소, 최대 이미지 가시화 레벨 설정.              |
| vworldTileSet | boolean                                          | optional   | false         | 브이월드 타일구조로 타일링일 경우(true).         |
| indexOrder    | boolean                                          | optional   | true          | 타일 인덱싱 기준점(false: 좌하단, true: 좌상단). |
| boxRequest    | boolean                                          | optional   | false         | 인덱싱이 아닌 박스단위 요청일 경우(true).        |
