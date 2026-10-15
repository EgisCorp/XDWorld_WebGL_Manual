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
| quality                                     | [Quality](jsImageryProvider.md#quality)   | 배경 영상 지도 이미지 품질.       			|
| zeroLevel                                   | number									  | 서로 다른 타일구조의 매칭을 위한 보간 값(높은값일 수록 요청수가 많아진다).        			|
| zerolevelOffset                             | string                                    | 배경 영상 지도 이미지 LOD offset. 			|
| maxLevel                                    | number                                    | 배경 영상 지도 최대 레벨.         			|
| minLevel                                    | number                                    | 배경 영상 지도 최소 레벨.         			|
| crackValue                                  | number                                    | 크랙발생시 보간값(보간값 만큼 이미지를 더 생성한다).         			|
| apikey                                      | string                                    | 배경 영상 지도 apikey. **GoogleMap()·ArcMap()은 필수**이며, 키가 비어 있으면 [refresh()](jsImageryProvider.md#refresh)가 적용하지 않습니다.         			|
| language                                    | string                                    | 배경 영상 지도 언어 설정.         			|
| [directSampling](jsImageryProvider.md#directsampling-property-boolean) | boolean      | 배경 영상 직접 샘플링 사용 여부(기본 true).         			|
	
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
>
> 지형이 이미 만들어져 있으면 지형 트리는 그대로 두고 영상만 교체합니다. 화면에 잡히는 메쉬부터 새 영상을 받고, 받는 동안에는 이전 영상으로 그리므로 지구본이 하얗게 비지 않습니다. 지형이 아직 없거나 첫 로딩이 끝나지 않은 경우, 평면 모드, 사용자 DEM·사용자 영상·사용자 지구본 이미지를 쓰는 경우에는 이전처럼 지형을 처음부터 다시 만듭니다.

{% tabs %}
{% tab title="Information" %}

-   `GoogleMap()` 또는 `ArcMap()`을 선택했는데 `apikey`가 비어 있으면 아무것도 바꾸지 않고(이전 배경지도·레이어명·품질·zeroLevelOffset 설정으로 되돌림) 콘솔에 경고를 출력합니다. 키는 `layername`을 지정하기 전에 먼저 설정하십시오. `layername`·`directSampling` 설정, `clear()`, `setblank()`도 내부적으로 `refresh()`를 호출하므로 같게 동작합니다.
-   Google은 `apikey`와 `layername`·`language` 조합으로 세션을 발급받으며, 세션이 준비될 때까지 지형 생성을 미룹니다.

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

## Getter / Setter

### directSampling (property) → boolean

> 배경 영상 직접 샘플링 사용 여부를 조회하거나 설정합니다. (기본값 true)
>
> 켜면 메르카토르 타일의 원본 화소를 확대·축소·워프 없이 1:1로 이어 붙여 지형 셰이더가 화소마다 경위도를 메르카토르 좌표로 변환해 읽습니다(경위도로 다시 그리는 단계가 없어 더 선명합니다). 끄면 예전 방식(경위도 텍스처로 다시 그리기)으로 되돌아갑니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                                                                          |
| :---- | :------ | :----------------------------------------------------------------------------------- |
| value | boolean | <p>true: 직접 샘플링 사용(기본).<br>false: 사용 안 함(비교용).</p>                   |

-   Return
    -   boolean: 현재 설정값(`Module.GoogleMap()` 등 어느 `JSImageryProvider`로 읽어도 같은 전역 값입니다).

* Note
  * 현재 값과 다른 값을 설정하면 요청 레벨이 바뀌므로 [refresh()](jsImageryProvider.md#refresh)가 자동으로 호출되어 배경 영상을 다시 받습니다. 같은 값을 다시 설정하면 아무 일도 하지 않습니다.
  * 켠 상태에서는 웹 메르카토르 레이어(TM 좌표계 레이어 제외)의 영상 요청 레벨을 [quality](jsImageryProvider.md#quality)에 따라 높입니다: `low`(256) +1, `middle`(512) +2, `high`(1024) +3 레벨. 서비스 최고 레벨(레이어의 `zeroLevel + maxLevel`)을 넘지 않으므로 요청 타일 수·메모리가 늘어납니다.
  * 조건이 맞지 않는 메쉬는 해당 메쉬만 예전 모자이크 방식으로 그립니다: 0레벨 지형 타일, 평면 모드, 시계열 영상 합성, 서로 다른 타일 구조 매칭이 켜진 경우, 지형 타일을 원본 타일이 빠짐없이 덮지 못하거나(일부 타일 요청 실패·단색 빈 타일 포함) 메르카토르 한계 위도를 벗어나는 경우, 좌표 변환 오차가 0.05화소 이상인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var google = Module.GoogleMap();
google.apikey = "YOUR_GOOGLE_MAP_TILES_API_KEY";
google.layername = "satellite";

console.log(google.directSampling); // true

google.directSampling = false; // 예전 방식과 비교 (배경 영상을 다시 받음)
google.directSampling = true;
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

> 배경 영상 지도 레이어 정보.

| Name            | Type   | Description           |
| --------------- | ------ | --------------------- |
| normal          | string | 일반 지도.            |
| terrain         | string | 등고선 지도.          |
| vectorhybrid    | string | 벡터 하이브리드 지도. |
| satellitehybrid | string | 영상 하이브리드 지도. |
| satellite       | string | 영상 지도.            |
| cadastral       | string | 지적편집도.           |

#### Provider

> 배경 영상 지도 설정.

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
| iscrack    	| boolean                                          | optional   | false         | 타일링시 크랙이 발생 할 경우(true).        |
| crackvalue    | number                                           | optional   | 1000          | 크랙발생시 보간값(보간값 만큼 이미지를 더 생성한다).        |

#### Quality

> 배경 영상 지도 해상도.

| Value 		| Type                | Description       |
| ------------- | ------------------- | ----------------  |
| low           | string              | 256 x 256 해상도   |
| middle    	| string              | 512 x 512 해상도   |
| high    		| string              | 1024 x 1024 해상도   |

#### ZeroLevel

![](../.gitbook/assets/Tile구조.png)

> 예를들어 EGIS Tile 구조와 다른 Google 이미지를 사용할 경우 Tile이 서로 1:1 매칭되지 않는다. 
>
> 그렇기 때문에 EGIS Tile에 걸치는 Google Tile을 모두 요청하여 EGIS Tile에 맞게 이미지를 자른다.
>
> 이 과정에서 동일한 레벨의 Google Tile 1개로 EGIS Tile 1개를 만들때 이미지 해상도 차이가 발생한다.
>
> 이것을 해결하기 위해 zeroLevel 변수를 활용하여 EGIS의 실제 Tile 레벨 보다 높은 레벨(EGIS 레벨 + zeroLevel)의 Google Tile 이미지를 요청한다.
