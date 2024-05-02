---
description: 지도 내 분석 기능 설정을 위한 API입니다.
---

# JSAnalysis

> Module.getAnalysis API를 생성합니다.

```javascript
var analysis = Module.getAnalysis();
```

## Function

### createShadow(year, month, day, hour, minute) → boolean

> 설정한 날짜, 시간을 기준으로 건물에 대한 그림자를 생성합니다.

{% tabs %}
{% tab title="Name" %}

| Name   | Type   | Description |
| :----- | :----- | :---------- |
| year   | number | 년도.       |
| month  | number | 월.         |
| day    | number | 일.         |
| hour   | number | 시간.       |
| minute | number | 분.         |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis.createShadow(2018, 5, 28, 15, 0);
```

{% endtab %}
{% endtabs %}

### createSlopePlane(angle, color) → boolean

> 시곡면 분석 삼각형 평면을 생성합니다.

{% tabs %}
{% tab title="Name" %}

| Name  | Type                          | Description    |
| :---- | :---------------------------- | :------------- |
| angle | number                        | 지형과의 각도. |
| color | [JSColor](../core/jscolor.md) | 평면 색상.     |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
-   Sample
    -   function getSlopePlane 참조.
    -   [Sandbox_Slope Analysis](https://sandbox.egiscloud.com/code/main.do?id=analysis_building_height_regulation)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### CreateInterpolationPath(option) → array

> 보간된 선을 구성하는 좌표 목록을 반환합니다.

{% tabs %}
{% tab title="Name" %}

| Name   | Type                                                                           | Description         |
| :----- | :----------------------------------------------------------------------------- | :------------------ |
| option | [JSAnalysis.InterpolationOption](jsanalysis.md#jsanalysis.interpolationoption) | 보간된 선 생성 옵션 |

-   Return
    -   array: 보간된 선 좌표 목록 반환 성공.
    -   NULL: 보간된 라인 좌표 모곩 반환 실패.
-   Sample
    -   function createInterpolatedLine 참조.
    -   [Sandbox_Line Interpolation (Curved)](https://sandbox.egiscloud.com/code/main.do?id=object_line_interpolate_curved)

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

-   Return
    -   [JSGridAnal](../analysis/jsgridanal.md): 반환 성공.
    -   null : 반환 실패.
-   Sample
    -   function setWindRenderMode 참조.
    -   [Sandbox_Wind Representation](https://sandbox.egiscloud.com/code/main.do?id=effect_wind)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getJomangRatio(height) → string

> 조망 차폐율을 반환합니다.
>
> 입력 변수값이 설정한 높이 이하 인 지형 고도 값을 가진 영역은 지형, 이상은 산으로 판단합니다.

{% tabs %}
{% tab title="Name" %}

| Name   | Type   | Description                      |
| :----- | :----- | :------------------------------- |
| height | number | 지형, 산 기준 높이 (meter 단위). |

-   Return

    -   다음 순서로 문자열이 구성 (건물#차폐율#산#차폐율#지형#차폐율#하늘#차폐율)

-   Sample
    -   function getJomangRatio 참조.
    -   [Sandbox_View Ratio](https://sandbox.egiscloud.com/code/main.do?id=camera_jomang_ratio)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getJudong(angle) → string

> 지동 길이를 측정하고 측정 정보를 반환합니다.
>
> 입력 변수값은 측정의 기준 퍼짐각도 입니다.

{% tabs %}
{% tab title="Name" %}

| Name  | Type   | Description |
| :---- | :----- | :---------- |
| angle | number | 퍼짐각      |

-   Return

    -   다음 순서로 문자열이 구성 (레이어명#객체키#주동길이#경도#위도)

-   Sample
    -   function getJudong 참조.
    -   [Sandbox_Main Building Length Analysis](https://sandbox.egiscloud.com/code/main.do?id=analysis_building_width)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setAllObjectRenderShadow(type)

> 가시화 된 시설물에 대한 그림자 생성 유무를 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name | Type    | Description                                                                        |
| :--- | :------ | :--------------------------------------------------------------------------------- |
| type | boolean | <p>true: 모든 시설물 그림자 객체 생성.<br>false: 선택 시설물 그림자 객체 생성.</p> |

-   Sample
    -   function initPage 참조.
    -   [Sandbox_Shadow](https://sandbox.egiscloud.com/code/main.do?id=effect_shadow_play)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShadowSimulation(type)

> 그림자 시뮬레이션 실행, 종료를 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name | Type    | Description                                                            |
| :--- | :------ | :--------------------------------------------------------------------- |
| type | boolean | <p>true: 그림자 시뮬레이션 실행.<br>false: 그림자 시뮬레이션 종료.</p> |

-   Sample
    -   function executeShadowSimulation 참조.
    -   [Sandbox_Shadow](https://sandbox.egiscloud.com/code/main.do?id=effect_shadow_play)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShadowSimulTerm(term)

> 그림자 시뮬레이션 진행 시간 간격을 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name | Type   | Description                                 |
| :--- | :----- | :------------------------------------------ |
| term | number | 그림자 시뮬레이션 진행 간격 설정 (분 단위). |

-   Sample
    -   function setShadowSimulationTimeTerm 참조.
    -   [Sandbox_Shadow](https://sandbox.egiscloud.com/code/main.do?id=effect_shadow_play)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis.setShadowSimulTerm(30);
```

{% endtab %}
{% endtabs %}

### setShadowSimulTime(year, month, day, startHour, startMin, endHour, endMin)

> 그림자 시뮬레이션에 필요한 시간 정보를 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name      | Type   | Description           |
| :-------- | :----- | :-------------------- |
| year      | number | 시뮬레이션 년도.      |
| month     | number | 시뮬레이션 월.        |
| day       | number | 시뮬레이션 일.        |
| startHour | number | 시뮬레이션 시작 시간. |
| startMin  | number | 시뮬레이션 시작 분.   |
| endHour   | number | 시뮬레이션 종료 시간. |
| endMin    | number | 시뮬레이션 종료 분.   |

-   Sample
    -   function setShadowSimulationTimeTerm 참조.
    -   [Sandbox_Shadow](https://sandbox.egiscloud.com/code/main.do?id=effect_shadow_play)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis.setShadowSimulTime(2018, 05, 28, 9, 0, 14, 30);
```

{% endtab %}
{% endtabs %}

### setViewshedMode(apply)

> 가시권 분석을 실행, 종료를 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name  | Type    | Description                                                |
| :---- | :------ | :--------------------------------------------------------- |
| apply | boolean | <p>true: 가시권 분석 실행.<br>false: 가시권 분석 종료.</p> |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSAnalysis.InterpolationOption

> Interpolation line coordinate creation options.

| Name        | Type                                                          | Description            |
| ----------- | ------------------------------------------------------------- | ---------------------- |
| positions   | array([JSVector2D](../core/jsvector2d.md))                    | 보간 선 시작점 목록.   |
| input       | array([Interpolation](../etc/tag-list.md#interpolation-type)) | 보간 계산 입력점 목록. |
| rect        | [Rect2D](../etc/tag-list.md#rect2d-style-type)                | 선 생성 영역.          |
| vertexcount | number                                                        | 선 형상 정점 수.       |
| scale       | number                                                        | 선 생성 간격.          |
