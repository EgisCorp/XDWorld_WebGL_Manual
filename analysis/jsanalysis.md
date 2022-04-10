---
description: 지도 내 분석 기능 설정 API.
---

# JSAnalysis

Module getAnalysis API로 생성할 수 있습니다.

```javascript
var analysis = Module.getAnalysis();
```

### createSlopePlane(angle, color) → boolean

> 시곡면분석 삼각형 평면을 생성합니다.

{% tabs %}
{% tab title="Name" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| angle | number | 지형으로 부터 각도. |
| color | [JSColor](../core/jscolor.md) | 평면 색상 |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
  
* Sample
  * function getSlopePlane 참조.
  * [샌드박스\_시곡면 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_building_height_regulation)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### CreateInterpolationPath(option) → array

> 보간된 라인을 좌표를 반환합니다.

{% tabs %}
{% tab title="Name" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| option | [JSAnalysis.InterpolationOption](jsanalysis.md#jsanalysis.interpolationoption) | 시작점, 입력점, 영역, 정점 갯수, 라인 길이 |

* Return
  * array : 보간된 라인 좌표 목록 반환 성공.
  * NULL : 보간된 라인 좌표 목록 반환 실패.

* Sample
  * function createInterpolatedLine 참조.
  * [샌드박스\_라인 보간 (곡선)](http://sandbox.dtwincloud.com/code/main.do?id=object_line_interpolate_curved)  
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getGridAnal() → [JSGridAnal](../analysis/jsgridanal.md)

> JSGridAnal 클래스를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSGridAnal](../analysis/jsgridanal.md) : JSGridAnal 객체 반환 성공.
  * null : JSGridAnal 객체 반환 성공.
  
* Sample
  * function setWindRenderMode 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getJomangRatio(height) → string

> 조망 차폐율을 반환합니다.
> 
> height 입력값이 설정한 높이 이하는 지형, 그 이상은 산으로 판단.

{% tabs %}
{% tab title="Name" %}

| Name | Type | Description |
| :--- | :--- | :--- |
| height | number | 지형 기준 높이 |

* Return
  * 건물#차폐율#산#차폐율#지형#차폐율#하늘#차폐율
  * build#43.15#mount#17.47#terrain#35.04#sky#4.34
  
* Sample
  * function getJomangRatio 참조.
  * [샌드박스\_조망 비율](http://sandbox.dtwincloud.com/code/main.do?id=camera_jomang_ratio)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getJudong(angle) → string

> 주동길이를 측정하고 반환합니다.
> 
> height 입력값은 좌우 퍼짐각 설정.

{% tabs %}
{% tab title="Name" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| angle | number | 퍼짐각 |

* Return
  * 레이어명#객체키#주동길이#경도#위도,
  * facility_build#263500000000000023630202#157.677215#129.123663#35.176768, ...
  
* Sample
  * function getJudong 참조.
  * [샌드박스\_주동길이 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_building_width)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setAllObjectRenderShadow(type)

> 건물 선택 여부와 상관없이 모든 객체의 그림자를 그리도록 설정합니다.

{% tabs %}
{% tab title="Name" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 모든 객체 그림자 생성.<br>false인 경우 선택 객체만 그림자 생성.</p> |
	
* Sample
  * function initPage 참조.
  * [샌드박스\_그림자](http://sandbox.dtwincloud.com/code/main.do?id=effect_shadow_play)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setShadowSimulation(type)

> 일조 시뮬레이션을 실행, 종료합니다.

{% tabs %}
{% tab title="Name" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 시뮬레이션 시작.<br>false인 경우 시뮬레이션 종료.</p> |
	
* Sample
  * function executeShadowSimulation 참조.
  * [샌드박스\_그림자](http://sandbox.dtwincloud.com/code/main.do?id=effect_shadow_play)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setShadowSimulTerm(term)

> 일조 시뮬레이션 진행 시간 간격을 설정합니다.

{% tabs %}
{% tab title="Name" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| term | number | 시뮬레이션 진행 시간 간격 설정(분 단위). |

* Sample
  * function setShadowSimulationTimeTerm 참조.
  * [샌드박스\_그림자](http://sandbox.dtwincloud.com/code/main.do?id=effect_shadow_play)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setShadowSimulTime(year, month, day, startHour, startMin, endHour, endMin)

> 일조 시뮬레이션 날짜(년도, 월, 일), 시작 시각(시간, 분), 종료 시각(시간, 분)을 설정합니다.

{% tabs %}
{% tab title="Name" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| year | number | 시뮬레이션 년도 |
| month | number | 시뮬레이션 월 |
| day | number | 시뮬레이션 일 |
| startHour | number | 시뮬레이션 시작 시간 |
| startMin | number | 시뮬레이션 시작 분 |
| endHour | number | 시뮬레이션 종료 시간 |
| endMin | number | 시뮬레이션 종료 분 |

* Sample
  * function setShadowSimulationTimeTerm 참조.
  * [샌드박스\_그림자](http://sandbox.dtwincloud.com/code/main.do?id=effect_shadow_play)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setViewshedMode(apply)

> 가시권 분석을 실행, 종료합니다.

{% tabs %}
{% tab title="Name" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| apply | boolean | <p>true인 경우 가시권 분석 시작.<br>false인 경우 가시권 분석 종료.</p> |

{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSAnalysis.InterpolationOption

> 보간 라인 좌표 생성 옵션.

| Name         | Type                          | Attributes | Default                 | Description      |
| ------------ | ----------------------------- | ---------- | ----------------------- | ---------------- |
| 1 | 1 | 1 | 1 | 1 |

