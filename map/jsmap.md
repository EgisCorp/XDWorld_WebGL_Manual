---
description: 지도 설정 및 제어 기능 API.
---

# JSMap

> Module.getMap API 생성.

```javascript
var map = Module.getMap();
```

### addHeatMaps(coordinates)

> 히트맵 좌표 리스트 배열을 설정.

{% tabs %}
{% tab title="Information" %}
| Name  | Type                                 | Description      |
| ---------- | ------------------------------------ | ------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 히트맵 좌표 목록. |

* Sample
  * function loadHeatmapPoint 참조
  * [샌드박스\_히트맵](http://sandbox.dtwincloud.com/code/main.do?id=effect\_heatmap)
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
	[129.12837451707335, 35.171954803028704, -127.18164411373436]
];

positions.forEach(function(item, idx) {
	vList.push(new Module.JSVector3D(item[0], item[1], 0));
}); 

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1)
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```
{% endtab %}
{% endtabs %}

### addInputPoint(lon, lat) → number

> 사용자 입력 점을 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| lon  | number | 입력점 경도(Degree 단위).   |
| lat  | number | 입력점 위도(Degree 단위).   |

* Return
  * number : API 실행 후 누적된 입력점 수.
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
* Sample
  * function loadHeatmapPoint 참조
  * [샌드박스\_히트맵](http://sandbox.dtwincloud.com/code/main.do?id=effect\_heatmap)
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
	[129.12837451707335, 35.171954803028704, -127.18164411373436]
];

positions.forEach(function(item, idx) {
	vList.push(new Module.JSVector3D(item[0], item[1], 0));
}); 

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1)
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```
{% endtab %}
{% endtabs %}

### clearInputPoint()

> 입력된 좌표 리스트 초기화.

{% tabs %}
{% tab title="Information" %}
* Sample
  * function clearInputPoint 참조.
  * [샌드박스\_라인버퍼링](http://sandbox.dtwincloud.com/code/main.do?id=object\_line\_buffering)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getMap().clearInputPoint();
```
{% endtab %}
{% endtabs %}

### clearSelectObj()

> 오브젝트 선택 상태 해제.

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

> 적설 효과 초기화.

{% tabs %}
{% tab title="Template" %}
```javascript
var pMap = Module.getMap();
pMap.clearSnowfallArea();
```
{% endtab %}
{% endtabs %}

### getFogLimitAltitude() → number

> 안개 효과 적용 고도 값을 반환.
> 
> 반환 된 고도 이하에 카메라가 위치한 경우 안개 효과 적용.

{% tabs %}
{% tab title="Information" %}
* Return
  * number : 안개 효과 적용 고도.
{% endtab %}

{% tab title="Template" %}
```javascript
var limitAltitude = Module.getMap().getFogLimitAltitude();
```
{% endtab %}
{% endtabs %}

### getInputPointCount() → number

> 현재 입력된 점 수를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number(0 이상) : 현재 입력된 점 수.
  * number(-1) : 지도가 초기화되지 않은 경우.
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

> 입력된 좌표 리스트 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * [Collection](../core/collection.md) : 입력된 좌표 리스트 반환 선공.
  * null : 입력된 좌표가 없을 경우
  
* Sample
  * function createPipe 참조
  * [샌드박스\_라인버퍼링](http://sandbox.dtwincloud.com/code/main.do?id=object\_pipe)
{% endtab %}

{% tab title="Template" %}
```javascript
var inputPoints = Module.getMap().getInputPointList();
```
{% endtab %}
{% endtabs %}

### getInputPoints() → [JSVec3Array](../core/jsvec3array.md)

> 입력된 좌표 리스트 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * [JSVec3Array](../core/jsvec3array.md) : 입력된 좌표 리스트 반환 성공.
  * null : 입력된 좌표가 없을 경우.
  
* Sample
  * function createBufferPolygon 참조.
  * [샌드박스\_라인버퍼링](http://sandbox.dtwincloud.com/code/main.do?id=object\_line\_buffering)
{% endtab %}

{% tab title="Template" %}
```javascript
var line = Module.getMap().getInputPoints();
```
{% endtab %}
{% endtabs %}

### getSelectObject() → JSObject

> 선택 상태로 설정된 오브젝트 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * JSObject : 선택된 오브젝트.
{% endtab %}

{% tab title="Template" %}
```javascript
var selObject = Module.getMap().getSelectObject();
```
{% endtab %}
{% endtabs %}

### getTerrHeight(lon, lat) → number

> 해당 위치의 지형 높이값 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| lon       | number | 경도.       |
| lat       | number | 위도.      |

* Return
  * 지형 높이값.
  * 0 : 해당 지역 dem 로드가 되지 않았을 경우.
 
{% endtab %}

{% tab title="Template" %}
```javascript
var height = Module.getMap().getTerrHeight(126.92836647767662, 37.52439503321471);
```
{% endtab %}
{% endtabs %}

### GetPointDistance(from, to, type) → number

> 두 지점 사이의 거리 반환.

{% tabs %}
{% tab title="Information" %}
| Name    | Type                                | Description   |
| ------------ | ----------------------------------- | ---------- |
| from         | [JSVector3D](../core/jsvector3d.md) | 시작 점 위치 (경도, 위도, 고도)    |
| to           | [JSVector3D](../core/jsvector3d.md) | 끝 점 위치 (경도, 위도, 고도)     |
| type | boolean                             | 지형 고려할지 여부(false: 직선거리, true: 지형을 고려한 거리) |

* Return
  * 두 지점 사이의 거리 반환.
  * 0 : 엔진이 정상적으로 load되지 않았을 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var distance = Module.getMap().GetPointDistance(new Module.JSVector3D(129.128265, 35.171834, 500.0), new Module.JSVector3D(129.118265, 35.161834, 500.0), false);
```
{% endtab %}
{% endtabs %}

### getLineBuffer(coordinates, distance) → [JSVec2Array](../core/jsvec2array.md)

> 거리 설정값에 따라 라인 버퍼 폴리곤 좌표 반환.

{% tabs %}
{% tab title="Information" %}
| Name      | Type                                 | Description   |
| -------------- | ------------------------------------ | ---------- |
| coordinates     | [JSVec2Array](../core/jsvec2array.md) | 라인 좌표 리스트 (경도, 위도)  |
| distance | number                               | 라인으로 부터 거리 (라인으로 부터 거리) |

* Return
  * [JSVec2Array](../core/jsvec2array.md) : 라인버퍼 폴리곤 경위도 좌표 목록 반환 성공.
  * null : 엔진이 정상적으로 load되지 않았을 경우
  
* Sample
  * function createBufferPolygon 참조
  * [샌드박스\_라인버퍼링](http://sandbox.dtwincloud.com/code/main.do?id=object\_line\_buffering)
{% endtab %}

{% tab title="Template" %}
```javascript
var map = Module.getMap();
var line = map.getInputPoints();
var line2D = new Module.JSVec2Array();
for (var i=0; i<line.count(); i++) {
	line2D.push(new Module.JSVector2D(line.get(i).Longitude, line.get(i).Latitude));
}
var polygonLine = map.getLineBuffer(line2D, 100);
```
{% endtab %}
{% endtabs %}

### MapRender()

> 지도 화면 갱신.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getMap().MapRender();
```
{% endtab %}
{% endtabs %}

### MapToScreenPointEX(position) → [JSVector2D](../core/jsvector2d.md)

> 3차원 지도 좌표로 화면 좌표 반환.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                                | Description  |
| ----------- | ----------------------------------- | --------- |
| position | [JSVector3D](../core/jsvector3d.md) | 3차원 지도 좌표 (경도, 위도, 고도) |

* Return
  * [JSVector2D](../core/jsvector2d.md) : 화면 스크린 좌표 반환 성공(x, y).
  * null : 엔진이 정상적으로 load되지 않았을 경우
  
* Sample
  * function displayPopUp 참조
  * [샌드박스\_지도->화면좌표변환](http://sandbox.dtwincloud.com/code/main.do?id=coordinate\_map\_to\_screen)
{% endtab %}

{% tab title="Template" %}
```javascript
var pointMapPos = Module.getMap().MapToScreenPointEX(new Module.JSVector3D(129.128265, 35.171834, 100.0));
```
{% endtab %}
{% endtabs %}


### ScreenToMapPointEX(position) → [JSVector3D](../core/jsvector3d.md)

> 화면 좌표로 3차원 지도 좌표 반환.

{% tabs %}
{% tab title="Information" %}
| Name      | Type                                | Description |
| -------------- | ----------------------------------- | -------- |
| position | [JSVector2D](../core/jsvector2d.md) | 화면 좌표 (x, y)   |

* Return
  * [JSVector3D](../core/jsvector3d.md) : 경위도 좌표 반환 성공.
  * null : 엔진이 정상적으로 load되지 않았을 경우
  
* Sample
  * function init 참조
  * [샌드박스\_지도->화면좌표변환](http://sandbox.dtwincloud.com/code/main.do?id=coordinate\_screen\_to\_map)
{% endtab %}

{% tab title="Template" %}
```javascript
var mapPosition = Module.getMap().ScreenToMapPointEX(10, 10);
```
{% endtab %}
{% endtabs %}

### setCircleInputPoint(center, radius, segment)

> 중심 좌표, radius, segment로 원을 구성하는 입력점을 리스트에 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| center    | [JSVector2D](../core/jsvector2d.md) | 원 중심점 경위도 좌표.      |
| radius    | number | 원 반지름(m 단위).      |
| segment    | number | 원 구성 세그먼트 수.      |
{% endtab %}

{% tab title="Template" %}
```javascript
var vCenter = new Module.JSVector(129.147500, 35.184338);
Module.getMap().setCircleInputPoint(vCenter, 500.0, 12);
```
{% endtab %}
{% endtabs %}

### setDistance(distance)

> 히트맵 반경 거리를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| distance  | number | 히트맵 반경.   |

* Sample
  * function loadHeatmapPoint 참조
  * [샌드박스\_히트맵](http://sandbox.dtwincloud.com/code/main.do?id=effect\_heatmap)
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
	[129.12837451707335, 35.171954803028704, -127.18164411373436]
];

positions.forEach(function(item, idx) {
	vList.push(new Module.JSVector3D(item[0], item[1], 0));
}); 

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1)
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```
{% endtab %}
{% endtabs %}

### setEffectDistance(max)

> 히트맵 효과가 표현되는 최대 거리를 설정.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description |
| ----------- | ------ | -------- |
| max | number | 히트맵 최대 가시 거리. |

* Sample
  * function loadHeatmapPoint 참조
  * [샌드박스\_히트맵](http://sandbox.dtwincloud.com/code/main.do?id=effect\_heatmap)
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
	[129.12837451707335, 35.171954803028704, -127.18164411373436]
];

positions.forEach(function(item, idx) {
	vList.push(new Module.JSVector3D(item[0], item[1], 0));
}); 

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1)
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```
{% endtab %}
{% endtabs %}

### setSelectObject(object)

> 지정한 오브젝트를 선택 상태로 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| object    | JSObject | 선택 상태로 설정할 오브젝트.      |
{% endtab %}

{% tab title="Template" %}
```javascript
var object = GLOBAL.Layer.keyAtObject("object_select");
Module.getMap().setSelectObject(object);
```
{% endtab %}
{% endtabs %}

### setSnowfallArea(array)

> 적설 효과를 부분적으로 줄 범위를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| array    | [JSVec3Array](../core/jsvec3array.md) | 범위 구성 좌표, 경도(deg), 위도(deg), 고도(m)로 구성.      |
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

> 적설 색상을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| color    | [JSColor](../core/jscolor.md) | 적설 색상.      |
{% endtab %}

{% tab title="Template" %}
```javascript
var snowColor = new Module.JSColor(178, 178, 178);
Module.getMap().setSnowfallColor(snowColor);
```
{% endtab %}
{% endtabs %}

### setTerrLODRatio(ratio)

> 지형 LOD 갱신 거리 비율을 설정합니다.
> 
> <LOD에 따른 지형 갱신 거리> = _dRatio * <지형 메쉬 사이즈>

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| ratio    | double | 지형 LOD 갱신 거리 비율.      |
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getMap().setTerrLODRatio(1.0);
```
{% endtab %}
{% endtabs %}

### setWeight(weight)

> 히트맵 가중치를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| weight    | number | 히트맵 가중치.      |

* Sample
  * function loadHeatmapPoint 참조
  * [샌드박스\_히트맵](http://sandbox.dtwincloud.com/code/main.do?id=effect\_heatmap)
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
	[129.12837451707335, 35.171954803028704, -127.18164411373436]
];

positions.forEach(function(item, idx) {
	vList.push(new Module.JSVector3D(item[0], item[1], 0));
}); 

Module.getMap().clearHeatMap();
Module.getMap().setTerrainEffect(9);
Module.getMap().setDistance(200);
Module.getMap().setWeight(1)
Module.getMap().addHeatMaps(vList);
Module.getMap().setEffectDistance(1500000);
```
{% endtab %}
{% endtabs %}

### setFog(color, start, end, density)

> 안개 효과 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                          | Description       |
| --------- | ----------------------------- | -------------- |
| color     | [JSColor](../core/jscolor.md) | 안개 색상.          |
| start     | number                        | 안개 효과 적용 최소 가시거리(최소값 1). |
| end       | number                        | 안개 효과 적용 최대 가시거리. |
| density   | number                        | 안개 농도 가중치 (0.0 \~ 1.0 사이 값으로 설정).   |

* Sample
  * function loadHeatmapPoint 참조.
  * [샌드박스\_안개](http://sandbox.dtwincloud.com/code/main.do?id=weather\_fog)
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

> 안개 효과 적용 여부를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description    |
| --------- | ------- | ----------- |
| type    | boolean | 안개 효과 적용 여부. |

* Sample
  * function loadHeatmapPoint 참조
  * [샌드박스\_안개](http://sandbox.dtwincloud.com/code/main.do?id=weather\_fog)
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

### setFogLimitAltitude(alt)

> 안개 효과 적용 고도 제한.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| alt       | number | 제한할 고도 값.  |

* Sample
  * function loadHeatmapPoint 참조.
  * [샌드박스\_안개](http://sandbox.dtwincloud.com/code/main.do?id=weather\_fog)
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

> 비 효과 이미지 경로 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description    |
| --------- | ------ | ----------- |
| url  | string | 비 표현 이미지 경로. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.

* Sample
  * function changeRainEffectOption 참조.
  * [샌드박스\_비](http://sandbox.dtwincloud.com/code/main.do?id=weather\_rain)
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

> 적설 효과 출력 타입을 설정.
>
> 0일 경우 적설효과 해제.
>
> 1일 경우 적설효과 설정 (지형 텍스쳐 가시화).
>
> 2일 경우 적설효과 설정 (지형 텍스쳐 가시화 하지 않음).

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description    |
| --------- | ------ | ----------- |
| state     | number | 적설 효과 출력 타입. |

* Sample
  * function setUseSnowEffect 참조.
  * [샌드박스\_눈](http://sandbox.dtwincloud.com/code/main.do?id=weather\_snow)
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

> 적설 효과 출력 중 적설량 설정.

{% tabs %}
{% tab title="Information" %}
| Name     | Type   | Description |
| ------------- | ------ | -------- |
| level | number | 적설량 (0 \~ 100 사이값으로 설정).  |

* Return
  * 설정된 적설량 값.

* Sample
  * function setUseSnowEffect 참조.
  * [샌드박스\_눈](http://sandbox.dtwincloud.com/code/main.do?id=weather\_snow)
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

> 적설 효과 이미지 경로를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description    |
| --------- | ------ | ----------- |
| url  | string | 눈 표현 이미지 경로 |

* Return
  * true : 설정 성공.
  * false : 설정 실패.

* Sample
  * function changeRainEffectOption 참조.
  * [샌드박스\_눈](http://sandbox.dtwincloud.com/code/main.do?id=weather\_snow)
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

> 날씨 표현 기능 활성화.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| type      | number | 날씨 표현 타입(0: 눈, 1: 비). |
| size      | number | 표현 강도(0: 약하게, 1: 보통, 2: 강하게).    |
| speed     | number | 표현 속도(0: 느리게, 1: 보통, 2: 빠르게).    |

* Return
  * true : 설정 성공.
  * false : 설정 실패.

* Sample
  * function setUseRainEffect 참조.
  * [샌드박스\_비](http://sandbox.dtwincloud.com/code/main.do?id=weather\_rain)
{% endtab %}

{% tab title="Template" %}
```javascript
var pMap = Module.getMap();
pMap.startWeather(1, 5, 5);	
```
{% endtab %}
{% endtabs %}

### stopWeather()

> 날씨 표현 기능 비활성화.

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

> 건물 심플모드 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description |
| --------- | ------- | -------- |
| type      | boolean | 건물 심플모드.  |

* Return
  * true : 설정 성공.
  * false : 설정 실패.

* Sample
  * function setUseRainEffect 참조
  * [샌드박스\_건물심플모드](http://sandbox.dtwincloud.com/code/main.do?id=layer\_building\_simplemode)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getMap().setSimpleMode(true);
```
{% endtab %}
{% endtabs %}

### setTerrainEffect(value)

> 지형 랜더링 효과 설정합.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| --------- | ------ | --------- |
| value    | number | 지형 랜더링 모드(0: 일반, 10: 경사향, 11: 경사도) |

* Sample
  * function setUseRainEffect 참조.
  * [샌드박스\_건물심플모드](http://sandbox.dtwincloud.com/code/main.do?id=terrain\_rendermode)
  
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getMap().setTerrainEffect(10);
```
{% endtab %}
{% endtabs %}

### updateRTT()

> 화면 RTT 갱신.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getMap().updateRTT();
```
{% endtab %}
{% endtabs %}
