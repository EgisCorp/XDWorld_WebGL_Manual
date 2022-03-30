---
description: 폴리곤 오브젝트 설정 및 반환 API를 제공합니다.
---

# JSAnalysis

Module getAnalysis API로 생성할 수 있습니다.

```javascript
var analysis = Module.getAnalysis();
```

## createSlopePlane\(number angle, [JSColor](../core/jscolor.md) color\) → boolean

> 시곡면분석 삼각형 평면을 생성합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| angle | number | 평면 각도 |
| color | [JSColor](../core/jscolor.md) | 평면 색상 |

* Detail
  * angle : 지형으로 부터 각도

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_building_height_regulation
{% endtab %}
{% endtabs %}

## CreateInterpolationPath\(object param\) → Array

> 보간된 라인을 좌표를 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| param | object | 시작점, 입력점, 영역, 정점 갯수, 라인 길이 |

* Return
  * 보간된 라인 좌표를 반환
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_interpolate_curved
{% endtab %}
{% endtabs %}

## getGridAnal\(\) → [JSGridAnal](../analysis/jsgridanal.md)

> JSGridAnal 클래스를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSGridAnal](../analysis/jsgridanal.md)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_interpolate_curved
{% endtab %}
{% endtabs %}

## getJomangRatio\(number height\) → string

> 조망 차폐율을 반환합니다.

{% tabs %}
{% tab title="Parameter" %}

| Parameter | Type | Contents |
| :--- | :--- | :--- |
| height | number | 지형 기준 높이 |

* Detail
  * height : 설정한 높이 이하는 지형으로 판단. 그 이상은 산으로 판단.

* Return
  * 건물#차폐율#산#차폐율#지형#차폐율#하늘#차폐율
  * build#43.15#mount#17.47#terrain#35.04#sky#4.34
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=camera_jomang_ratio
{% endtab %}
{% endtabs %}

## getJudong\(number angle\) → string

> 주동길이를 측정하고 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| angle | number | 퍼짐각 |

* Detail
  * angle : 좌우로 퍼짐각 설정

* Return
  * 레이어명#객체키#주동길이#경도#위도,
  * facility_build#263500000000000023630202#157.677215#129.123663#35.176768, ...
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_building_width
{% endtab %}
{% endtabs %}

## setAllObjectRenderShadow\(boolean mode\)

> 건물 선택 여부와 상관없이 모든 객체의 그림자를 그리도록 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| mode | boolean | 그림자 생성 모드 |

* Detail
  * mode
    * false : 선택된 객체만 그림자 생성합니다.
    * true : 모든 객체의 그림자를 생성합니다.
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_shadow_play
{% endtab %}
{% endtabs %}

## setShadowSimulation\(boolean start\)

> 일조 시뮬레이션을 실행, 종료합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| start | boolean | 시뮬레이션 설정 |

* Detail
  * start
    * false : 시뮬레이션을 종료합니다.
    * true : 시뮬레이션을 시작합니다.
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_shadow_play
{% endtab %}
{% endtabs %}

## setShadowSimulTerm\(number term\)

> 일조 시뮬레이션 진행 시간 간격을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| term | number | 진행시간 간격(분 단위) |

* Detail
  * term : 시뮬레이션 진행 시간 간격을 설정합니다.

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_shadow_play
{% endtab %}
{% endtabs %}

## setShadowSimulTime\(number year, number month, number day, number startHour, number startMin, number endHour, number endMin\)

> 일조 시뮬레이션 날짜(년도, 월, 일), 시작 시각(시간, 분), 종료 시각(시간, 분)을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| year | number | 시뮬레이션 년도 |
| month | number | 시뮬레이션 월 |
| day | number | 시뮬레이션 일 |
| startHour | number | 시뮬레이션 시작 시간 |
| startMin | number | 시뮬레이션 시작 분 |
| endHour | number | 시뮬레이션 종료 시간 |
| endMin | number | 시뮬레이션 종료 분 |

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_shadow_play
{% endtab %}
{% endtabs %}

## setViewshedMode\(boolean apply\)

> 가시권 분석을 실행, 종료합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| apply | boolean | 가시권 분석 설정 |

* Detail
  * apply
    * false : 가시권 분석을 종료합니다.
    * true : 가시권 분석을 시작합니다.
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_viewshed_3d
{% endtab %}
{% endtabs %}