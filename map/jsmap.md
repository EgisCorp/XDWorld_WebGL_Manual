---
description: 지도 설정 및 제어를 위한 API를 제공합니다.
---

# JSMap

## setDistance\(number distance\)
> 히트맵 반경 거리를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| distance | number | 히트맵 반경 |
* Detail
  * distance : 히트맵의 크기를 설정합니다. (최소값 1)
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_heatmap
{% endtab %}
{% endtabs %}

## setEffectDistance\(number maxDistance\)
> 히트맵 효과가 표현되는 최대 거리를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| maxDistance | number | 최대 가시 거리 |
* Detail
  * maxDistance : 히트맵 효과를 가시화할 최대 가시거리
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_heatmap
{% endtab %}
{% endtabs %}

## setWeight\(number weight\)
> 히트맵 가중치를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| weight | number | 가중치 |
* Detail
  * weight : 히트맵 포인트의 가중치
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_heatmap
{% endtab %}
{% endtabs %}

## addHeatMaps\([CJSVec3Array](CJSVec3Array.md) pointArray\)
> 히트맵 좌표 리스트 배열을 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| pointArray | [CJSVec3Array](CJSVec3Array.md) | 히트맵 좌표 리스트 배열 |
* Detail
  * pointArray : ([JSVector3D](JSVector3D.md), [JSVector3D](JSVector3D.md), ...) 히트맵 좌표 리스트 배열
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_heatmap
{% endtab %}
{% endtabs %}

## clearHeatMap\(\)
> 히트맵을 초기화 합니다.
{% tabs %}
{% tab title="Parameter" %}
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_heatmap
{% endtab %}
{% endtabs %}

## setFog\([CJSColor](CJSColor.md) color, number start, number end, number density\)
> 안개 효과를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| color | [CJSColor](CJSColor.md) | 안개 색상 |
| start | number | 안개 효과 적용 시작 거리 |
| end | number | 안개 효과 적용 종료 거리 |
| density | number | 안개 농도 |
* Detail
  * color : [CJSColor](CJSColor.md)
  * start : 안개 효과 적용 최소 가시거리 (최소값 1)
  * end : 안개 효과 적용 최대 가시거리
  * density : 안개 효과 농도 가중치 (0.0 ~ 1.0 사이 값으로 설정)
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_fog
{% endtab %}
{% endtabs %}

## setFogEnable\(boolean enable\)
> 안개 효과 적용 여부를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| enable | boolean | 안개 효과 적용 여부 |
* Detail
  * enable
    * false : 안개 효과를 해제합니다.
	* true : 안개 효과를 적용합니다.
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_fog
{% endtab %}
{% endtabs %}

## setFogLimitAltitude\(number alt\)
> 안개 효과 적용 고도를 제한합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| alt | number | 고도 제한 값 |
* Detail
  * alt : 제한된 고도값 아래에 카메라가 위치할 경우 안개 효과 적용
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_fog
{% endtab %}
{% endtabs %}

## setSnowfall\(number state\)
> 적설 효과 출력 타입을 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| state | number | 적설 효과 출력 타입 |
* Detail
  * state
    * 0 : 적설 효과 해제
	* 1 : 적설 표시 설정 (지형 텍스쳐 출력)
	* 2 : 적설 표시 설정 (지형 텍스쳐 미출력)
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_snow
{% endtab %}
{% endtabs %}

## setSnowfallLevel\(number snowFallLevel\) → number
> 적설 효과 출력 중 적설량을 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| snowFallLevel | number | 적설량 |
* Detail
  * snowFallLevel : 적설량 설정 (0 ~ 100 사이값으로 설정)
* Return
  * 적설량
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_snow
{% endtab %}
{% endtabs %}

## setSnowImageURL\(string imageURL\) → boolean
> 적설 효과 이미지 경로를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| imageURL | string | 눈 표현 이미지 경로 |
* Detail
  * imageURL : 눈 표현으로 사용할 이미지 경로
* Return
  * 설정 성공 (true) 혹은 실패 (false)
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_snow
{% endtab %}
{% endtabs %}

## clearSnowfallArea\(\)
> 적설 효과를 초기화 합니다.
{% tabs %}
{% tab title="Parameter" %}
* Code
  * Module.getMap().clearSnowfallArea();
{% endtab %}
{% endtabs %}

## setRainImageURL\(string imageURL\) → boolean
> 비 효과 이미지 경로를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| imageURL | string | 비 표현 이미지 경로 |
* Detail
  * imageURL : 비 표현으로 사용할 이미지 경로
* Return
  * 설정 성공 (true) 혹은 실패 (false)
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_rain
{% endtab %}
{% endtabs %}

## startWeather\(number type, number size, number speed\) → boolean
> 날씨 표현 기능을 활성화 합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| type | number | 날씨 표현 타입 |
| size | number | 표현 강도 |
| speed | number | 표현 속도 |
* Detail
  * type
    * 0 : 눈
	* 1 : 비
  * size
    * 0 : 약하게
	* 1 : 보통
	* 2 : 강하게
  * speed
    * 0 : 느리게
	* 1 : 보통
	* 2 : 빠르게
* Return
  * 설정 성공 (true) 혹은 실패 (false)
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_rain
{% endtab %}
{% endtabs %}

## stopWeather\(\)
> 날씨 표현 기능을 비활성화 합니다.
{% tabs %}
{% tab title="Parameter" %}
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_rain
{% endtab %}
{% endtabs %}

## setSimpleMode\(boolean set\) → boolean
> 건물 심플모드를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| set | boolean | 건물 심플모드 |
* Detail
  * true : 건물 심플모드를 실행합니다.
  * false : 건물 심플모드를 해제합니다.
* Return
  * 설정 성공 (true) 혹은 실패 (false)
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=layer_building_simplemode
{% endtab %}
{% endtabs %}

## setTerrainEffect\(number effect\)
> 지형 랜더링 효과를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| effect | number | 지형 랜더링 모드 |
* Detail
  * 0 : 일반 모드
  * 10 : 경사향 모드
  * 11 : 경사도 모드
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=terrain_rendermode
{% endtab %}
{% endtabs %}

## clearInputPoint\(\)
> 입력된 좌표 리스트를 초기화 합니다.
{% tabs %}
{% tab title="Parameter" %}
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_height
{% endtab %}
{% endtabs %}

## clearSelectObj\(\)
> 오브젝트 선택 상태를 해제합니다.
{% tabs %}
{% tab title="Parameter" %}
* Code
  * Module.getMap().clearSelectObj();
{% endtab %}
{% endtabs %}

## getInputPoints\(\) → [CJSVec3Array](CJSVec3Array.md)
> 입력된 좌표 리스트를 반환합니다.
{% tabs %}
{% tab title="Parameter" %}
* Detail
  * [CJSVec3Array](CJSVec3Array.md) : 입력된 좌표 리스트
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit
{% endtab %}
{% endtabs %}

## getInputPointList\(\) → [CJSCollection](CJSCollection.md)
> 입력된 좌표 리스트를 반환합니다.
{% tabs %}
{% tab title="Parameter" %}
* Detail
  * [CJSCollection](CJSCollection.md) : 입력된 좌표 리스트
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_pipe
{% endtab %}
{% endtabs %}

## getTerrHeight\(number lon, number lat\) → number
> 해당 위치의 지형 높이값을 반환합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| lon | number) | 경도 |
| lat | number) | 위도 |
* Return
  * 지형 높이값
* Code
  * let height = Module.getMap().getTerrHeight(129.128265, 35.171834);
{% endtab %}
{% endtabs %}

## GetPointDistance\([CJSVector3D](CJSVector3D.md) from, [CJSVector3D](CJSVector3D.md) to, boolean unionTerrain\) → number
> 두 지점 사이의 거리를 반환합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| from | [CJSVector3D](CJSVector3D.md)) | 시작 점 위치 |
| to | [CJSVector3D](CJSVector3D.md)) | 끝 점 위치 |
| unionTerrain | boolean | 지형 고려할지 여부 |
* Detail
  * [CJSVector3D](CJSVector3D.md) : (경도, 위도, 고도)
  * unionTerrain : 
    * false : 지형을 고려하지 않고 직선 거리를 반환
	* true : 지형을 고려하여 거리를 반환
* Return
  * 두 지점 사이의 거리 반환
* Code
  * let distance = Module.getMap().GetPointDistance(new Module.JSVector3D(129.128265, 35.171834, 500.0), new Module.JSVector3D(129.118265, 35.161834, 500.0), false);
{% endtab %}
{% endtabs %}

## getLineBuffer\([CJSVec2Array](CJSVec2Array.md) lineVertex, number bufferDistance\) → [CJSVec2Array](CJSVec2Array.md)
> 거리 설정값에 따라 라인 버퍼 폴리곤 좌표를 반환합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| lineVertex | [CJSVec2Array](CJSVec2Array.md)) | 라인 좌표 리스트 |
| bufferDistance | number | 라인으로 부터 거리 |
* Detail
  * [CJSVec2Array](CJSVec2Array.md) : (경도, 위도)
  * bufferDistance : 생성할 버퍼의 크기 (라인으로 부터 거리)
* Return
  * [CJSVec2Array](CJSVec2Array.md) : (경도, 위도)
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_buffering
{% endtab %}
{% endtabs %}

## MapToScreenPointEX\([CJSVector3D](CJSVector3D.md) mapPosition\) → [CJSVector2D](CJSVector2D.md)
> 3차원 지도 좌표로 화면 좌표를 반환합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| mapPosition | [CJSVector3D](CJSVector3D.md)) | 3차원 지도 좌표 |
* Detail
  * [CJSVector3D](CJSVector3D.md) : (경도, 위도, 고도) 3차원 지도 좌표
* Return
  * [CJSVector2D](CJSVector2D.md) : (x, y) 화면 좌표
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=coordinate_map_to_screen
{% endtab %}
{% endtabs %}

## ScreenToMapPointEX\([CJSVector2D](CJSVector2D.md) screenPosition\) → [CJSVector3D](CJSVector3D.md)
> 화면 좌표로 3차원 지도 좌표를 반환합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| screenPosition | [CJSVector2D](CJSVector2D.md)) | 화면 좌표 |
* Detail
  * [CJSVector2D](CJSVector2D.md) : (x, y) 화면 좌표
* Return
  * [CJSVector3D](CJSVector3D.md) : (경도, 위도, 고도) 3차원 지도 좌표
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=coordinate_screen_to_map
{% endtab %}
{% endtabs %}