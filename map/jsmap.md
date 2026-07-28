---
description: 지도 설정 및 제어하기 위한 API 입니다.
---

# JSMap

> Module.getMap() API를 생성합니다.

```javascript
var map = Module.getMap();
```

## Properties

| Name           | Type   | Description                                                                        |
| -------------- | ------ | ------------------------------------------------------------------------------------ |
| lastRenderTime | object | 마지막 렌더링 시각. `{ year, month, day, hour, minute, second }` 형태 (읽기 전용). |

## Function

### addHeatMaps(coordinates)

> 히트맵 좌표 목록 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                              |
| ----------- | ------------------------------------- | ---------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 히트맵 위치 좌표(경도, 위도, 고도) 목록. |

-   Sample
    -   function loadHeatmapPoint 참조.
    -   [Sandbox_Heatmap](https://sandbox.egiscloud.com/code/main.do?id=effect_heatmap)

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(true);
var layer = layerList.createLayer("HEATMAP_POI", Module.ELT_3DPOINT);
layer.setMaxDistance(60000000.0);

var vList = new Module.JSVec3Array();
var positions = [
    [129.12628252638348, 35.174613788186335, -127.18464569468051],
    [129.1278597986113, 35.1730738804656, -127.16845162212849],
    [129.12691776723804, 35.17243834516552, -127.23446262534708],
    [129.12837451707335, 35.171954803028704, -127.18164411373436],
];

positions.forEach(function (item, idx) {
    vList.push(new Module.JSVector3D(item[0], item[1], 0));
});

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1);
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```

{% endtab %}
{% endtabs %}

### addInputPoint(lon, lat) → number

> 사용자 입력 지점을 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description               |
| ---- | ------ | ------------------------- |
| lon  | number | 경도 좌표 (degrees 단위). |
| lat  | number | 위도 좌표 (degrees 단위). |

-   Return
    -   number: 등록된 사용자 입력 지점 총 수.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().addInputPoint(127.4347, 35.7016);
```

{% endtab %}
{% endtabs %}

### clearHeatMap()

> 히트맵을 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   function loadHeatmapPoint 참조.
    -   [Sandbox_Heatmap](https://sandbox.egiscloud.com/code/main.do?id=effect_heatmap)

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(true);
var layer = layerList.createLayer("HEATMAP_POI", Module.ELT_3DPOINT);
layer.setMaxDistance(60000000.0);

var vList = new Module.JSVec3Array();
var positions = [
    [129.12628252638348, 35.174613788186335, -127.18464569468051],
    [129.1278597986113, 35.1730738804656, -127.16845162212849],
    [129.12691776723804, 35.17243834516552, -127.23446262534708],
    [129.12837451707335, 35.171954803028704, -127.18164411373436],
];

positions.forEach(function (item, idx) {
    vList.push(new Module.JSVector3D(item[0], item[1], 0));
});

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1);
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```

{% endtab %}
{% endtabs %}

### clearInputPoint()

> 사용자 입력 좌표 목록을 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   function clearInputPoint 참조.
    -   [Sandbox_LineBuffering](https://sandbox.egiscloud.com/code/main.do?id=object_line_buffering)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().clearInputPoint();
```

{% endtab %}
{% endtabs %}

### clearSelectObj()

> 지도 내 선택된 모든 오브젝트를 선택 해제 상태로 변환합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}

{% tab title="Template" %}

```javascript
Module.getMap().clearSelectObj();
```

{% endtab %}
{% endtabs %}

### clearSnowfallArea()

> 적설 효과를 초기화 합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}

{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.clearSnowfallArea();
```

{% endtab %}
{% endtabs %}

### getInputPointCount() → number

> 사용자 입력 좌표 목록 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   result >= 0 : 반환 성공.
    -   -1: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    Module.getMap();
};
var nCount = API.JSMap.getInputPointCount();
```

{% endtab %}
{% endtabs %}

### getInputPointList() → [Collection](../core/collection.md)

> 사용자 입력 좌표(경도, 위도, 고도)를 모두 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [Collection](../core/collection.md): 반환 성공.
    -   null: 반환 실패.
-   Sample
    -   function createPipe 참조.
    -   [Sandbox_LineBuffering](https://sandbox.egiscloud.com/code/main.do?id=object_pipe)

{% endtab %}
{% tab title="Template" %}

```javascript
var inputPoints = Module.getMap().getInputPointList();
```

{% endtab %}
{% endtabs %}

### getInputPoints() → [JSVec3Array](../core/jsvec3array.md)

> 사용자 입력 좌표(경도, 위도, 고도)를 모두 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVec3Array](../core/jsvec3array.md): 반환 성공.
    -   null: 반환 실패.
-   Sample
    -   function createBufferPolygon 참조.
    -   [Sandbox_LineBuffering](https://sandbox.egiscloud.com/code/main.do?id=object_line_buffering)

{% endtab %}
{% tab title="Template" %}

```javascript
var line = Module.getMap().getInputPoints();
```

{% endtab %}
{% endtabs %}

### getTerrHeight(lon, lat) → number

> 입력 변수값(lon, lat)의 해발고도 기준 지형 높이값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| lon  | number | 경도.       |
| lat  | number | 위도.       |

-   Return
    -   result > 0: 반환 성공.
    -   0: 반환 실패
    -   실패 조건
        -   해당 지형 고도 데이터가 지도에 요청 되지 않는 경우.
        -   요청 지형 레벨이 낮은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var height = Module.getMap().getTerrHeight(126.92836647767662, 37.52439503321471);
```

{% endtab %}
{% endtabs %}

### GetPointDistance(from, to, type) → number

> 입력 변수값(from, to) 두 지점의 실제 거리를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                                | Description                                                                       |
| ---- | ----------------------------------- | --------------------------------------------------------------------------------- |
| from | [JSVector3D](../core/jsvector3d.md) | 시작 좌표 (경도, 위도, 고도)                                                      |
| to   | [JSVector3D](../core/jsvector3d.md) | 종료 좌표 (경도, 위도, 고도)                                                      |
| type | boolean                             | <p> 지형 결합 유무를 설정합니다.<br>true: 지형 결합 거리.<br>false: 직선 거리.<p> |

-   Return
    -   result > 0: 반환 성공.
    -   0: 반환 실패

{% endtab %}
{% tab title="Template" %}

```javascript
var distance = Module.getMap().GetPointDistance(new Module.JSVector3D(129.128265, 35.171834, 500.0), new Module.JSVector3D(129.118265, 35.161834, 500.0), false);
```

{% endtab %}
{% endtabs %}

### getLineBuffer(coordinates, distance) → [JSVec2Array](../core/jsvec2array.md)

> 입력 변수값(coordinates)을 기준으로 직선에 대한 buffer의 폴리곤 좌표 목록을 반환합니다.
>
> 입력 변수값(distance)를 기준으로 버퍼 영역을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                        |
| ----------- | ------------------------------------- | ---------------------------------- |
| coordinates | [JSVec2Array](../core/jsvec2array.md) | 선 좌표 목록 (경위도).             |
| distance    | number                                | buffer의 반지름 크기 (meter 단위). |

-   Return
    -   [JSVec2Array](../core/jsvec2array.md): 반환 성공.
    -   null: 반환 실패.
-   Sample
    -   function createBufferPolygon 참조.
    -   [Sandbox_LineBuffering](https://sandbox.egiscloud.com/code/main.do?id=object_line_buffering)

{% endtab %}
{% tab title="Template" %}

```javascript
var map = Module.getMap();
var line = map.getInputPoints();
var line2D = new Module.JSVec2Array();
for (var i = 0; i < line.count(); i++) {
    line2D.push(new Module.JSVector2D(line.get(i).Longitude, line.get(i).Latitude));
}
var polygonLine = map.getLineBuffer(line2D, 100);
```

{% endtab %}
{% endtabs %}

### MapRender()

> 3D 지도 화면을 재 갱신합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}

{% tab title="Template" %}

```javascript
Module.getMap().MapRender();
```

{% endtab %}
{% endtabs %}

### MapToScreenPointEX(position) → [JSVector2D](../core/jsvector2d.md)

> 3D 지도에서 특정 지점에 대한 화면 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                        |
| -------- | ----------------------------------- | ---------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 지도 위치 좌표 (경도, 위도, 고도). |

-   Return
    -   [JSVector2D](../core/jsvector2d.md): 반환 성공.
    -   null: 반환 실패.
-   Sample
    -   function displayPopUp 참조.
    -   [Sandbox_MapToScreenCoordinate](https://sandbox.egiscloud.com/code/main.do?id=coordinate_map_to_screen)

{% endtab %}
{% tab title="Template" %}

```javascript
var pointMapPos = Module.getMap().MapToScreenPointEX(new Module.JSVector3D(129.128265, 35.171834, 100.0));
```

{% endtab %}
{% endtabs %}

### ScreenToMapPointEX(position) → [JSVector3D](../core/jsvector3d.md)

> 화면 좌표에서 특정 지점에 대한 3D 지도 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description       |
| -------- | ----------------------------------- | ----------------- |
| position | [JSVector2D](../core/jsvector2d.md) | 화면 좌표 (x, y). |

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 반환 성공.
    -   null: 반환 실패.
-   Sample
    -   function init 참조.
    -   [Sandbox_ScreenToMapCoordinate](https://sandbox.egiscloud.com/code/main.do?id=coordinate_screen_to_map)

{% endtab %}
{% tab title="Template" %}

```javascript
var mapPosition = Module.getMap().ScreenToMapPointEX(10, 10);
```

{% endtab %}
{% endtabs %}

### setCircleInputPoint(center, radius, segment)

> 특정 지점에 대한 반경 좌표 목록을 반환합니다.
>
> 입력 변수값(center)을 기준으로 입력 변수값(radius)을 반지름으로 반경에 대한 좌표를 반환합니다.
>
> 입력 변수값(segment)으로 반경을 정밀도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                | Description                  |
| ------- | ----------------------------------- | ---------------------------- |
| center  | [JSVector2D](../core/jsvector2d.md) | 반경의 중심 좌표(경도 위도). |
| radius  | number                              | 반경의 반지름 (meters 단위). |
| segment | number                              | 반경의 정밀도.               |

{% endtab %}
{% tab title="Template" %}

```javascript
var vCenter = new Module.JSVector(129.1475, 35.184338);
Module.getMap().setCircleInputPoint(vCenter, 500.0, 12);
```

{% endtab %}
{% endtabs %}

### setDistance(distance)

> 히트맵 반경거리를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description       |
| -------- | ------ | ----------------- |
| distance | number | 히트맵 영역 거리. |

-   Sample
    -   function loadHeatmapPoint 참조.
    -   [Sandbox_Heatmap](https://sandbox.egiscloud.com/code/main.do?id=effect_heatmap)

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(true);
var layer = layerList.createLayer("HEATMAP_POI", Module.ELT_3DPOINT);
layer.setMaxDistance(60000000.0);

var vList = new Module.JSVec3Array();
var positions = [
    [129.12628252638348, 35.174613788186335, -127.18464569468051],
    [129.1278597986113, 35.1730738804656, -127.16845162212849],
    [129.12691776723804, 35.17243834516552, -127.23446262534708],
    [129.12837451707335, 35.171954803028704, -127.18164411373436],
];

positions.forEach(function (item, idx) {
    vList.push(new Module.JSVector3D(item[0], item[1], 0));
});

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1);
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```

{% endtab %}
{% endtabs %}

### setEffectDistance(max)

> 홍수, 적설, 히트맵 가시화 최대 거리를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description           |
| ---- | ------ | --------------------- |
| max  | number | 가시화 최대 가시거리. |

-   Sample
    -   function loadHeatmapPoint 참조.
    -   [Sandbox_Heatmap](https://sandbox.egiscloud.com/code/main.do?id=effect_heatmap)

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(true);
var layer = layerList.createLayer("HEATMAP_POI", Module.ELT_3DPOINT);
layer.setMaxDistance(60000000.0);

var vList = new Module.JSVec3Array();
var positions = [
    [129.12628252638348, 35.174613788186335, -127.18464569468051],
    [129.1278597986113, 35.1730738804656, -127.16845162212849],
    [129.12691776723804, 35.17243834516552, -127.23446262534708],
    [129.12837451707335, 35.171954803028704, -127.18164411373436],
];

positions.forEach(function (item, idx) {
    vList.push(new Module.JSVector3D(item[0], item[1], 0));
});

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1);
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```

{% endtab %}
{% endtabs %}

### setSnowfallArea(array)

> 적설 효과를 표현할 영역을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                  | Description                        |
| ----- | ------------------------------------- | ---------------------------------- |
| array | [JSVec3Array](../core/jsvec3array.md) | 영역 좌표 목록 (경도, 위도, 고도). |

{% endtab %}

{% tab title="Template" %}

```javascript
var vAreaList = new Module.JSVec3Array();
vAreaList.push(new Module.JSVector3D(129.0952984771729, 35.26956608261821, 130.72385844029486));
vAreaList.push(new Module.JSVector3D(129.17153320599272, 35.26955240007246, 171.6742866402492));
vAreaList.push(new Module.JSVector3D(129.17146263440185, 35.17317375381265, 34.883301799185574));
vAreaList.push(new Module.JSVector3D(129.09531779839347, 35.17318816290076, 60.5584503589198));
vAreaList.push(new Module.JSVector3D(129.0952984771729, 35.26956608261821, 130.72385844029486));
Module.getMap().setSnowfallArea(vAreaList);
```

{% endtab %}
{% endtabs %}

### setSnowfallColor(color)

> 적설 효과에서 표현되는 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description |
| ----- | ----------------------------- | ----------- |
| color | [JSColor](../core/jscolor.md) | 적설 색상.  |

{% endtab %}

{% tab title="Template" %}

```javascript
var snowColor = new Module.JSColor(178, 178, 178);
Module.getMap().setSnowfallColor(snowColor);
```

{% endtab %}
{% endtabs %}

### setTerrLODRatio(ratio)

> 지형 LOD 요청 거리 비율을 설정합니다.
>
> 설정에 따라 먼거리에서 정밀한 지형 데이터가 가시화 됩니다.
>
> \<LOD에 따른 지형 갱신 거리\> = \ratio \* \<지형 메쉬 사이즈\>

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description     |
| ----- | ------ | --------------- |
| ratio | number | 갱신 거리 비율. |

{% endtab %}

{% tab title="Template" %}

```javascript
Module.getMap().setTerrLODRatio(1.0);
```

{% endtab %}
{% endtabs %}

### setWeight(weight)

> 히트맵 가중치를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description    |
| ------ | ------ | -------------- |
| weight | number | 히트맵 가중치. |

-   Sample
    -   function loadHeatmapPoint 참조.
    -   [Sandbox_Heatmap](https://sandbox.egiscloud.com/code/main.do?id=effect_heatmap)

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(true);
var layer = layerList.createLayer("HEATMAP_POI", Module.ELT_3DPOINT);
layer.setMaxDistance(60000000.0);

var vList = new Module.JSVec3Array();
var positions = [
    [129.12628252638348, 35.174613788186335, -127.18464569468051],
    [129.1278597986113, 35.1730738804656, -127.16845162212849],
    [129.12691776723804, 35.17243834516552, -127.23446262534708],
    [129.12837451707335, 35.171954803028704, -127.18164411373436],
];

positions.forEach(function (item, idx) {
    vList.push(new Module.JSVector3D(item[0], item[1], 0));
});

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1);
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```

{% endtab %}
{% endtabs %}

### setFog(color, start, end, density)

> 안개 효과를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                          | Description                     |
| ------- | ----------------------------- | ------------------------------- |
| color   | [JSColor](../core/jscolor.md) | 안개 색상.                      |
| start   | number                        | 가시화 최소 거리 (최소값 1).    |
| end     | number                        | 가시화 최대 거리.               |
| density | number                        | 안개 농도 (0.0 and 1.0 사이값). |

-   Sample
    -   function loadHeatmapPoint 참조.
    -   [Sandbox_Fog](https://sandbox.egiscloud.com/code/main.do?id=weather_fog)

{% endtab %}
{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.setFogLimitAltitude(6000000.0);
pMap.setFogEnable(true);
var color = new Module.JSColor(255, 255, 255, 255);
pMap.setFog(color, 0, 5000, 0.3);
```

{% endtab %}
{% endtabs %}

### setFogEnable(type)

> 안개효과 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                 |
| ---- | ------- | ----------------------------------------------------------- |
| type | boolean | <p>true: 안개 효과 가시화.<br>false: 안개 효과 비가시화</p> |

-   Sample
    -   function loadHeatmapPoint 참조.
    -   [Sandbox_Fog](https://sandbox.egiscloud.com/code/main.do?id=weather_fog)

{% endtab %}
{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.setFogLimitAltitude(6000000.0);
pMap.setFogEnable(true);
var color = new Module.JSColor(255, 255, 255, 255);
pMap.setFog(color, 0, 5000, 0.3);
```

{% endtab %}
{% endtabs %}

### setRainImageURL(url) → boolean

> 비 효과에 사용할 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| url  | string | 이미지 경로. |

-   Return

    -   true: 설정 성공.
    -   false: 설정 실패.

-   Sample
    -   function changeRainEffectOption 참조.
    -   [Sandbox_Rain](https://sandbox.egiscloud.com/code/main.do?id=weather_rain)

{% endtab %}
{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.setRainImageURL("./data/snow./png");
pMap.startWeather(1, 5, 5);
```

{% endtab %}
{% endtabs %}

### setSnowfall(state)

> 지형에 적설 효과적설 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                   |
| ----- | ------ | ------------------------------------------------------------- |
| state | number | <p>0: 지형 적설 효과 비가시화<br>1: 지형 적설 효과 가시화</p> |

-   Sample
    -   function setUseSnowEffect 참조.
    -   [Sandbox_Snow](https://sandbox.egiscloud.com/code/main.do?id=weather_snow)

{% endtab %}
{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.startWeather(0, 5, 5);
pMap.setSnowfall(1);
pMap.setSnowfallLevel(2.0);
```

{% endtab %}
{% endtabs %}

### setSnowfallLevel(level) → number

> 적설 교과 가시화 중 적설 적설량 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description           |
| ----- | ------ | --------------------- |
| level | number | 적설량(0~100 사이값). |

-   Return

    -   number: 설정된 적설량.

-   Sample
    -   function setUseSnowEffect 참조.
    -   [Sandbox_Snow](https://sandbox.egiscloud.com/code/main.do?id=weather_snow)

{% endtab %}
{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.startWeather(0, 5, 5);
pMap.setSnowfall(1);
pMap.setSnowfallLevel(2.0);
```

{% endtab %}
{% endtabs %}

### setSnowImageURL(url) → boolean

> 적설 효과 시 눈 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description          |
| ---- | ------ | -------------------- |
| url  | string | 눈 표현 이미지 경로. |

-   Return

    -   true: 설정 성공.
    -   false: 설정 실패.

-   Sample
    -   function changeRainEffectOption 참조.
    -   [Sandbox_Snow](https://sandbox.egiscloud.com/code/main.do?id=weather_snow)

{% endtab %}
{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.setSnowImageURL("./data/snow./png");
pMap.startWeather(0, 5, 5);
pMap.setSnowfall(1);
pMap.setSnowfallLevel(2.0);
```

{% endtab %}
{% endtabs %}

### startWeather(type, size, speed) → boolean

> 날씨 효과 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                 |
| ----- | ------ | ------------------------------------------- |
| type  | number | 날씨 유형(0: 눈, 1: 비).                    |
| size  | number | 날씨 강도 (0: 약함, 1: 보통, 2: 강항).      |
| speed | number | 날씨 표현 속도 (0: 느림, 1: 보통, 2: 빠름). |

-   Return

    -   true: 설정 성공.
    -   false: 설정 실패.

-   Sample
    -   function setUseRainEffect 참조.
    -   [Sandbox_Rain](https://sandbox.egiscloud.com/code/main.do?id=weather_rain)

{% endtab %}
{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.startWeather(1, 5, 5);
```

{% endtab %}
{% endtabs %}

### stopWeather()

> 날씨 효과 기능을 비활성화 합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}

{% tab title="Template" %}

```javascript
var pMap = Module.getMap();
pMap.stopWeather();
```

{% endtab %}
{% endtabs %}

### setSimpleMode(type) → boolean

> 시설물 색상 표현 심플 모드 설정합니다.
>
> 시설물 텍스쳐가 없는 색상으로 가시화 됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                  |
| ---- | ------- | ------------------------------------------------------------ |
| type | boolean | <p>true: 심플 모드 활성화.<br>false: 심플 모드 비활성화.</p> |

-   Return

    -   true: 설정 성공.
    -   false: 설정 실패.

-   Sample
    -   function setUseRainEffect 참조.
    -   [Sandbox_BuildingSimpleMode](https://sandbox.egiscloud.com/code/main.do?id=layer_building_simplemode)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().setSimpleMode(true);
```

{% endtab %}
{% endtabs %}

### setTerrainEffect(value)

> 지형 가시화 효과를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                        |
| ----- | ------ | -------------------------------------------------- |
| value | number | 지형 가시화 효과 (0: 일반, 10: 경사향, 11: 경사도) |

-   Sample
    -   function setUseRainEffect 참조.
    -   [Sandbox_BuildingSimpleMode](https://sandbox.egiscloud.com/code/main.do?id=terrain_rendermode)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().setTerrainEffect(10);
```

{% endtab %}
{% endtabs %}

### updateRTT()

> 3D 지도에 RTT 가시화를 재 갱신합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().updateRTT();
```

{% endtab %}
{% endtabs %}

### setLayerVisible(layerName, visible) → boolean

> 특정 레이어의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description                                            |
| --------- | ------- | -------------------------------------------------------- |
| layerName | string  | 대상 레이어 명칭.                                       |
| visible   | boolean | <p>true: 레이어 가시화.<br>false: 레이어 비가시화.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 대상 레이어를 찾지 못한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### mapReset() → boolean

> 사용자 입력(거리/면적 측정) 및 임시 레이어를 초기화하고, 지구(Planet)의 오브젝트를 모두 초기화합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 초기화 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().mapReset();
```

{% endtab %}
{% endtabs %}

### addChild(object, level)

> 지도에 임시 레이어를 통해 오브젝트를 추가합니다.
>
> object는 JSPoint, JSLineString, JSPolygon, JSMultiObject, JSFigure, JSLODPOI 타입만 지원합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                                                                     |
| ------ | ------ | ------------------------------------------------------------------------------------------------- |
| object | object | 추가할 객체 ([JSPoint](../object/jspoint.md), [JSLineString](../object/jslinestring.md), [JSPolygon](../object/jspolygon.md), [JSMultiObject](../object/jsmultiobject.md), [JSFigure](../object/jsfigure.md), JSLODPOI 중 하나). |
| level  | number | 사용되지 않는 예약 파라미터. (cpp 구현상 값이 사용되지 않음.)                                     |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSelectColor(color)

> 오브젝트 선택 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                           | Description  |
| ----- | ------------------------------- | ------------ |
| color | [JSColor](../core/jscolor.md)  | 설정 색상 객체. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().setSelectColor(new Module.JSColor(255, 255, 0, 0));
```

{% endtab %}
{% endtabs %}

### addSelectObject(object)

> 지정한 오브젝트를 선택 상태로 추가합니다 (기존 선택은 유지되고 다중 선택 상태에 추가).

{% tabs %}
{% tab title="Information" %}

| Name   | Type                              | Description               |
| ------ | ---------------------------------- | -------------------------- |
| object | [JSObject](../object/jsobject3d.md) | 선택 상태로 추가할 오브젝트. |

{% endtab %}
{% tab title="Template" %}

```javascript
var object = GLOBAL.Layer.keyAtObject("object_2");
Module.getMap().addSelectObject(object);
```

{% endtab %}
{% endtabs %}

### getSelectObjectByIndex(index) → [JSObject](../object/jsobject3d.md)

> 다중 선택된 오브젝트 목록 중, 입력한 인덱스에 해당하는 오브젝트를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| index | number | 조회할 인덱스. |

-   Return
    -   object: 인덱스에 해당하는 오브젝트.
    -   null: 선택된 오브젝트가 없거나 index가 유효 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getSelectObjectList() → array

> 현재 선택된 오브젝트 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   array: `{ key: string, object: object }` 형태 항목의 배열.

{% endtab %}
{% tab title="Template" %}

```javascript
var list = Module.getMap().getSelectObjectList();
```

{% endtab %}
{% endtabs %}

### setSelectObjectFromPolygon(polygon) → number

> 지정한 폴리곤 좌표 영역 내에 존재하는 오브젝트를 선택 상태로 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                   | Description                        |
| ------- | --------------------------------------- | ------------------------------------ |
| polygon | [JSVec3Array](../core/jsvec3array.md)  | 선택 영역을 구성하는 폴리곤 좌표 (3개 이상). |

-   Return
    -   number: 선택된 오브젝트 수.
    -   0: 폴리곤 좌표가 3개 미만인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRenderMode(mode)

> 시설물(Real3D) 레이어의 렌더링 모드(심플 모드)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                        |
| ---- | ------ | --------------------------------------------------- |
| mode | number | <p>0: 일반 모드.<br>0이 아닌 값: 심플 모드.</p>      |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPlaneModeToggle()

> 평면(Plane) 모드와 구체(지구본) 모드를 서로 전환합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().setPlaneModeToggle();
```

{% endtab %}
{% endtabs %}

### setTileObjectRenewLevel(level) → boolean

> 타일 오브젝트의 DrawLevel 갱신 대상이 되는 타일 레벨을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| level | number | 타일 레벨 값. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### isSimpleMode() → boolean

> 현재 심플 모드 적용 상태를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 심플 모드 적용 상태.
    -   false: 일반 모드 상태 또는 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var simple = Module.getMap().isSimpleMode();
```

{% endtab %}
{% endtabs %}

### setColorEffect(effect)

> 시설물, 지형의 컬러 효과(색상 강조)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                                   |
| ------ | ------ | --------------------------------------------------------------- |
| effect | number | <p>0: 효과 없음.<br>1: 시설물/지형 회색조(GRAY) 표현.</p>     |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().setColorEffect(1);
```

{% endtab %}
{% endtabs %}

### setLighting(lighting)

> 조명 모드를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description   |
| -------- | ------ | -------------- |
| lighting | number | 조명 모드 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSnowfallDrawLevel(level) → number

> 적설 효과가 표현되는 타일 드로우 레벨(0~15)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description             |
| ----- | ------ | ------------------------ |
| level | number | 드로우 레벨 (0 ~ 15).   |

-   Return
    -   number: 설정된(0~15 범위로 보정된) 드로우 레벨.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearRangeColor()

> 범위 색상(range color) 효과 목록을 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addRangeColor(position, color, range)

> 특정 위치를 중심으로 하는 범위 색상 효과를 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                     |
| -------- | ------------------------------------- | -------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)  | 중심 위치 (경도, 위도, 고도).    |
| color    | [JSColor](../core/jscolor.md)        | 범위 색상.                       |
| range    | number                                | 범위 반경.                       |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPickTerrain(pick)

> 마우스 피킹 시 지형만 대상으로 할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                       |
| ---- | ------- | --------------------------------------------------------------------- |
| pick | boolean | <p>true: 지형만 피킹 대상.<br>false: 지형 외 오브젝트도 피킹 대상.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSimpleModeColorType(type)

> 심플 모드에서 사용할 색상 타입을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| type | number | 색상 타입 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGlobalSimpleModeColor(color)

> 심플 모드에서 전역으로 사용할 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description       |
| ----- | ------------------------------ | ------------------ |
| color | [JSColor](../core/jscolor.md) | 심플 모드 전역 색상. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setMapLoadCompleteEventLevel(level) → boolean

> 지형 로드 완료 이벤트(Fire_JSEventTerrainLoadComplete)가 발생할 기준 레벨을 설정합니다.
>
> ※ 엔진 빌드 옵션 `_EVENT_DATA_LOAD_`가 활성화된 경우에만 바인딩됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| level | number | 이벤트 발생 기준 레벨 (0 이상). |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않았거나 level이 0 미만인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getHeatMapSize() → number

> 등록된 히트맵 포인트 수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 등록된 히트맵 포인트 수.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDrawLevelVisible(visible) → boolean

> 특정 타일 레벨 이하에서 작은 오브젝트를 그리지 않는 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description  |
| ------- | ------- | ------------- |
| visible | boolean | 작은 오브젝트 가시화 여부. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### fixedTextureLevel(level)

> 고정 텍스처를 적용할 레벨을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                          |
| ----- | ------ | ------------------------------------------------------ |
| level | number | 고정 텍스처 레벨 (0 ~ 5). 범위를 벗어나면 -1(미사용)로 설정됨. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFixedTextureByLevel(level)

> 레벨별 고정 텍스처 사용 방식을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                       |
| ----- | ------ | --------------------------------------------------- |
| level | number | 설정 값 (0 ~ 2). 범위를 벗어나면 2로 설정됨.       |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getRenderTileMeshList() → string

> 현재 렌더링 범위에 있는 타일 메쉬 목록을 문자열로 반환합니다.
>
> 반환 형식: `Level#Idx#Idy#최소경도#최소위도#최대경도#최대위도,...` (타일마다 콤마로 구분).

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 렌더링 중인 타일 메쉬 정보 목록.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### GetPointsVolume(coordinates) → number

> 입력한 좌표 목록으로 구성된 폴리곤의 면적(부피)을 계산하여 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                   | Description                    |
| ----------- | ---------------------------------------- | -------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md)   | 폴리곤 좌표 목록 (2개 이상).    |

-   Return
    -   number: 계산된 면적 값.
    -   0: 좌표가 2개 미만인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetProxyRequestTerrainDEM(set)

> 지형 DEM 데이터 요청 시 프록시 서버 경유 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                          |
| ---- | ------- | -------------------------------------- |
| set  | boolean | true: 프록시 경유. false: 직접 요청. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetProxyRequestTerrainImage(set)

> 지형 이미지(텍스쳐) 요청 시 프록시 서버 경유 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                          |
| ---- | ------- | -------------------------------------- |
| set  | boolean | true: 프록시 경유. false: 직접 요청. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetProxyUrlEncoding(set)

> 프록시 요청 URL에 대한 인코딩 적용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                    |
| ---- | ------- | --------------------------------- |
| set  | boolean | true: URL 인코딩 적용. false: 미적용. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getLonLatHeight(lon, lat) → number

> 경위도 좌표에서 지형 또는 오브젝트를 기준으로 한 고도 값을 반환합니다. (지형과 오브젝트 중 더 높은 값을 반환)

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description               |
| ---- | ------ | --------------------------- |
| lon  | number | 경도 (degrees 단위).      |
| lat  | number | 위도 (degrees 단위).      |

-   Return
    -   number: 고도 값 (meter 단위).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### selectIntersectObject(polygon)

> 입력한 폴리곤 영역과 겹치는 오브젝트를 선택 상태로 처리합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                              | Description       |
| ------- | ------------------------------------ | ------------------- |
| polygon | [JSPolygon](../object/jspolygon.md) | 대상 폴리곤 객체. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ClearMap()

> 지도를 초기화합니다 (엔진 내부 XDEClearMap 수행 및 DEM 메쉬 갱신 상태 초기화).

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().ClearMap();
```

{% endtab %}
{% endtabs %}

### GetSelectedObjectInfomation() → string

> 현재 선택된 오브젝트들의 정보를 문자열로 반환합니다.
>
> 반환 형식: `선택개수@레이어명#objid#objkey@레이어명#objid#objkey...`

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 선택된 오브젝트 정보 문자열.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### requestMeshLoadCallback(callback) → boolean

> 지형 메쉬 로딩 시 호출되는 콜백 함수를 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description   |
| -------- | -------- | -------------- |
| callback | function | 콜백 함수.    |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### requestObjectLoadCallback(callback) → boolean

> 오브젝트 로딩 시 호출되는 콜백 함수를 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description   |
| -------- | -------- | -------------- |
| callback | function | 콜백 함수.    |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### changeTileMatrix(info) → boolean

> 베이스맵 타일 구조(타일 행렬 구성, 인덱싱 순서 등)를 변경합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                                                                    |
| ---- | ------ | ----------------------------------------------------------------------------------------------------------------- |
| info | object | `url`, `tileExtent`(`min`,`max`), `indexorder`, `mercator`, `quadkey`, `differentmatrix`, `servicelevel`, `tilematrix`(`x`,`y`) 속성을 포함하는 설정 객체. |

-   Return
    -   true: 설정 성공.
    -   false: 필수 항목(url, tileExtent, tilematrix)이 누락된 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getMapSelectObjectFromPosition(position) → [JSObject](../object/jsobject3d.md)

> 화면 좌표가 아닌 지도 좌표(경위도) 기준으로 오브젝트를 선택합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description         |
| -------- | -------------------------------------- | --------------------- |
| position | [JSVector2D](../core/jsvector2d.md)   | 조회할 지도 좌표 (경도, 위도). |

-   Return
    -   object: 선택된 오브젝트.
    -   null: 선택된 오브젝트가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### mapToScreenPoint(position) → [JSVector2D](../core/jsvector2d.md)
>
> 지도 좌표를 화면 좌표로 변환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                     |
| -------- | --------------------------------------- | ---------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)   | 지도 위치 좌표 (경도, 위도, 고도). |

-   Return
    -   [JSVector2D](../core/jsvector2d.md): 화면 좌표 (Y값은 정상적으로 반영되지 않음).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addWaterFall(key, position, direction, tilt, particleCount, size, imageData, imageWidth, imageHeight) → boolean

> 특정 위치에 폭포 효과를 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type                                 | Description                        |
| ------------- | --------------------------------------- | ------------------------------------- |
| key           | string                                  | 폭포 고유 키.                        |
| position      | [JSVector3D](../core/jsvector3d.md)    | 폭포 생성 위치 (경도, 위도, 고도).   |
| direction     | number                                  | 폭포 방향.                           |
| tilt          | number                                  | 폭포 기울기.                        |
| particleCount | number                                  | 파티클 수.                          |
| size          | number                                  | 파티클 크기.                        |
| imageData     | object                                  | 폭포 파티클 이미지 픽셀 데이터.     |
| imageWidth    | number                                  | 이미지 가로 크기.                   |
| imageHeight   | number                                  | 이미지 세로 크기.                   |

-   Return
    -   true: 생성 성공.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeWaterFall(key) → boolean

> 지정한 폭포를 제거합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| key  | string | 폭포 고유 키. |

-   Return
    -   true: 제거 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### stopWaterFall()

> 모든 폭포 효과를 정지합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWaterFallSpeedRatio(key, ratio)

> 지정한 폭포의 낙하 속도 비율을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| key   | string | 폭포 고유 키. |
| ratio | number | 속도 비율.    |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWaterFallDirection(key, direction, tilt)

> 지정한 폭포의 방향과 기울기를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description   |
| --------- | ------ | -------------- |
| key       | string | 폭포 고유 키. |
| direction | number | 방향.         |
| tilt      | number | 기울기.       |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWaterFallGravityRatio(key, ratio)

> 지정한 폭포의 중력 비율을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| key   | string | 폭포 고유 키. |
| ratio | number | 중력 비율.    |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWaterFallActive(key, active)

> 지정한 폭포의 활성화 상태를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                        |
| ------ | ------- | ---------------------------------------------------- |
| key    | string  | 폭포 고유 키.                                       |
| active | boolean | <p>true: 활성화.<br>false: 비활성화.</p>          |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addHeatMap(position)

> 히트맵에 좌표 1개를 추가합니다 (가중치 1.0 고정).

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                     |
| -------- | --------------------------------------- | ---------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)   | 히트맵 위치 좌표 (경도, 위도, 고도). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addHeatMapEX(position)

> 히트맵에 좌표 1개를 가중치(고도값 사용)와 함께 추가합니다.
>
> position의 z(고도) 값이 해당 지점의 히트맵 가중치로 사용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                                   |
| -------- | --------------------------------------- | ------------------------------------------------ |
| position | [JSVector3D](../core/jsvector3d.md)   | 히트맵 위치 좌표 (경도, 위도, 가중치로 사용될 값). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addHeatMapsEX(coordinates)

> 히트맵 좌표 목록을 가중치(고도값 사용)와 함께 추가합니다.
>
> 각 좌표의 z(고도) 값이 해당 지점의 히트맵 가중치로 사용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                        |
| ----------- | ------------------------------------- | ----------------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 히트맵 위치 좌표(경도, 위도, 가중치로 사용될 값) 목록. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addHeatMap3D(position)

> 3D 히트맵에 좌표를 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                     |
| -------- | --------------------------------------- | ---------------------------------- |
| position | [JSVector2D](../core/jsvector2d.md)   | 히트맵 위치 좌표 (경도, 위도).    |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getSelectObject(), setSelectObject(object) → [JSObject](../object/jsobject3d.md)

> 객체의 선택 상태를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type                              | Description  |
| ------ | --------------------------------- | ------------ |
| object | [JSObject](../object/jsobject3d.md) | 시설물 객체. |

-   Return
    -   [JSObject](../object/jsobject3d.md): 시설물 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
var selObject = Module.getMap().getSelectObject();
// ... or ...
var object = GLOBAL.Layer.keyAtObject("object_select");
Module.getMap().setSelectObject(object);
```

{% endtab %}
{% endtabs %}

### getFogLimitAltitude(), setFogLimitAltitude(altitude) → number

> 안개 효과가 적용되는 영역에 대한 고도값을 설정합니다.
>
> 카메라가 반환 고도 아래에 있으면 안개효과가 적용됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type   | Description                  |
| -------- | ------ | ---------------------------- |
| altitude | number | 안개 효과 높이 (meter 단위). |

-   Return

    -   number: 안개 효과가 적용된 해발고도 기준 높이값.

-   Sample
    -   function loadHeatmapPoint 참조.
    -   [Sandbox_Fog](https://sandbox.egiscloud.com/code/main.do?id=weather_fog)

{% endtab %}
{% tab title="Template" %}

```javascript
var limitAltitude = Module.getMap().getFogLimitAltitude();
// ... or ...
var pMap = Module.getMap();
pMap.setFogLimitAltitude(6000000.0);
pMap.setFogEnable(true);
var color = new Module.JSColor(255, 255, 255, 255);
pMap.setFog(color, 0, 5000, 0.3);
```

{% endtab %}
{% endtabs %}

### GetPathIntervalPositions(path, interval, isUnionTerrain) → [JSVec3Array](../core/jsvec3array.md)

> 경위도 경로를 일정 간격으로 나눈 좌표 목록을 반환합니다.

#### Parameters

| Name            | Type                                  | Description                        |
| --------------- | ------------------------------------- | ---------------------------------- |
| path            | [JSVec3Array](../core/jsvec3array.md) | 경위도 경로 좌표 목록              |
| interval        | number                                | 간격 (meter 단위)                  |
| isUnionTerrain  | boolean                               | true: 지형 반영, false: 단순 표면  |

#### Returns

- [JSVec3Array](../core/jsvec3array.md): 간격에 따라 분할된 좌표 목록

#### Sample

```javascript
let path = new Module.JSVec3Array();
path.push(new Module.JSVector3D(127.0, 37.5, 0));
path.push(new Module.JSVector3D(127.01, 37.51, 0));

let result = Module.getMap().GetPathIntervalPositions(path, 50, true);
```

{% endtab %}
{% endtabs %}

### getTerrHeightFast(lon, lat) → number

> 입력한 경도(lon), 위도(lat) 기준의 지형 고도 값을 빠르게 반환합니다.  
> 일반 getTerrHeight보다 성능이 빠르지만, 정밀도는 약간 낮을 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description             |
| ---- | ------ | ----------------------- |
| lon  | number | 경도 (degrees 단위)     |
| lat  | number | 위도 (degrees 단위)     |

- Return  
  - number: 지형 고도 값 (meter 단위)  
  - 0: 고도 요청 실패

{% endtab %}
{% tab title="Template" %}

```javascript
let lon = 127.0;
let lat = 37.5;
let height = Module.getMap().getTerrHeightFast(lon, lat);
```

{% endtab %}
{% endtabs %}

### getPositionByAngleDistance3D(position, distance, angle) → [JSVector3D](../core/jsvector3d.md)

> 기준 좌표(`position`)에서 주어진 거리(`distance`)와 방위각(`angle`)을 기반으로 계산된 위치를 반환합니다.  
> 방위각은 북쪽을 기준으로 시계 방향으로 증가합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                              |
| -------- | ----------------------------------- | ---------------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 기준 위치 (경도, 위도, 고도).            |
| distance | number                              | 이동 거리 (meters 단위).                 |
| angle    | number                              | 이동 방향 각도 (degrees, 북쪽 기준 시계방향). |

- Return  
  - [JSVector3D](../core/jsvector3d.md): 이동 결과 위치 (경도, 위도, 고도)

{% endtab %}
{% tab title="Template" %}

```javascript
let base = new Module.JSVector3D(127.0, 37.5, 100.0);
let result = Module.getMap().getPositionByAngleDistance3D(base, 100.0, 90.0);  // 동쪽으로 100m 이동
```

{% endtab %}
{% endtabs %}

### GetAreaIntervalPositions(area, intervalVertical, intervalHorizontal, direction) → [JSVec3Array](../core/jsvec3array.md)

> 주어진 다각형 영역(`area`) 안에 일정 간격(`intervalVertical`, `intervalHorizontal`)으로 점을 분포시켜 반환합니다.  
> `direction` 값에 따라 정렬 방향을 조절할 수 있으며, 각 점은 실제 지형고도를 반영하여 3D 좌표로 반환됩니다.

{% tabs %}
{% tab title="Information" %}

| Name              | Type                                  | Description                                         |
| ----------------- | ------------------------------------- | --------------------------------------------------- |
| area              | [JSVec3Array](../core/jsvec3array.md) | 영역 경계 좌표 목록 (경도, 위도, 고도).               |
| intervalVertical  | number                                | 세로 간격 (meter 단위).                             |
| intervalHorizontal| number                                | 가로 간격 (meter 단위).                             |
| direction         | number                                | 정렬 기준 각도 (degrees). 북쪽 기준 시계방향으로 회전 |

- Return  
  - [JSVec3Array](../core/jsvec3array.md): 영역 내부 일정 간격으로 분포된 위치 리스트 (경도, 위도, 고도)

{% endtab %}
{% tab title="Template" %}

```javascript
let area = new Module.JSVec3Array();
area.push(new Module.JSVector3D(127.0, 37.5, 0));
area.push(new Module.JSVector3D(127.01, 37.5, 0));
area.push(new Module.JSVector3D(127.01, 37.51, 0));
area.push(new Module.JSVector3D(127.0, 37.51, 0));
area.push(new Module.JSVector3D(127.0, 37.5, 0));

let result = Module.getMap().GetAreaIntervalPositions(area, 10, 10, 0);
```

{% endtab %}
{% endtabs %}

### setHeatMapOpacity(opacity)

> 히트맵의 투명도를 설정합니다.  
> 값이 작을수록 히트맵이 더 투명하게 표시됩니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type  | Description                      |
| ------- | ----- | -------------------------------- |
| opacity | float | 히트맵 투명도 (0.0 ~ 1.0 사이값). |

- `0.0`: 완전히 투명  
- `1.0`: 완전히 불투명

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().setHeatMapOpacity(0.7);  // 히트맵 투명도 70%로 설정
```

{% endtab %}
{% endtabs %}

### setDefaultHeatMapColor()

> 히트맵 색상을 기본 색상으로 초기화합니다.

{% tabs %}
{% tab title="Information" %}

- 현재 설정된 사용자 정의 히트맵 색상 구성을 제거하고, 엔진 기본 색상 구성을 복원합니다.
- 히트맵 표현이 초기 상태로 재설정됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().setDefaultHeatMapColor();
```

{% endtab %}
{% endtabs %}

### setHeatMapColor(colors)

> 히트맵 색상 구성 목록을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                | Description                      |
|--------|-------------------------------------|----------------------------------|
| colors | [Collection](../core/collection.md) | [JSColor](../core/jscolor.md)의 배열. |

- 최소 2개 이상의 색상이 필요합니다.
- 설정된 색상은 낮은 밀도부터 높은 밀도까지 순차적으로 적용됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
let colorList = new Module.Collection();
colorList.Add(new Module.JSColor(0, 0, 255));   // Low density - blue
colorList.Add(new Module.JSColor(0, 255, 0));   // Mid density - green
colorList.Add(new Module.JSColor(255, 0, 0));   // High density - red

Module.getMap().setHeatMapColor(colorList);
```

{% endtab %}
{% endtabs %}

### getPositionByAngleDistance(position, distance, angle) → [JSVector2D](../core/jsvector2d.md)

> 기준 좌표(position)에서 주어진 거리(distance)와 방위각(angle)을 기반으로 계산된 위치를 반환합니다 (2D, 고도 미반영).
>
> getPositionByAngleDistance3D(position, distance, angle)의 2D(경위도만) 버전이며, 내부적으로 해당 함수를 호출합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                                       |
| -------- | ------------------------------------- | -------------------------------------------------- |
| position | [JSVector2D](../core/jsvector2d.md)  | 기준 위치 (경도, 위도).                           |
| distance | number                                | 이동 거리 (meters 단위).                          |
| angle    | number                                | 이동 방향 각도 (degrees, 북쪽 기준 시계방향 0~360). |

-   Return
    -   [JSVector2D](../core/jsvector2d.md): 이동 결과 위치 (경도, 위도).
    -   (0, 0): distance가 0 미만이거나 angle이 0~360 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let center = new Module.JSVector2D(127.0, 37.5);
let offset = Module.getMap().getPositionByAngleDistance(center, 1000, 45);
```

{% endtab %}
{% endtabs %}

### getWorkMode(), setWorkMode(mode) → number

> 마우스 동작 모드(작업 모드)를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| mode | number | 마우스 동작 모드 값. |

-   Return (get)
    -   number: 현재 마우스 동작 모드 값.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getPlaneMode(), setPlaneMode(plane, rotation) → boolean

> 평면(Plane) 모드와 구체(지구본) 모드를 설정하거나, 현재 평면 모드 여부를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type    | Description                                                |
| -------- | ------- | ------------------------------------------------------------ |
| plane    | boolean | <p>true: 평면 모드로 전환.<br>false: 구체 모드로 전환.</p> |
| rotation | boolean | 카메라 회전 유지 여부.                                       |

-   Return (get)
    -   true: 현재 평면 모드 상태.
    -   false: 현재 구체 모드 상태.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getMap().setPlaneMode(true, false);
var isPlane = Module.getMap().getPlaneMode();
```

{% endtab %}
{% endtabs %}
