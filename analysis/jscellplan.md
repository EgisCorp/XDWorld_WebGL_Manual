---
description: 특정 지점을 기준으로 한 부채꼴(섹터) 가시권 분석(Cell Plan) 결과를 조회 및 설정하기 위한 API 입니다.
---

# JSCellPlan / JSCPCollection

> 이 문서는 하나의 cpp 파일(JSCPCollection.cpp)에 정의된 컨테이너 클래스 `JSCPCollection`과, 그와 짝을 이루는 개별 분석 결과 클래스 `JSCellPlan`(JSCellPlan.cpp)을 함께 다룹니다.
>
> `JSCPCollection`은 [JSAnalysis](jsanalysis.md)를 통해 접근하는 전역 가시권 분석(Cell Plan) 목록 컨테이너이며, `JSCPCollection.createCellPlan()` 또는 `indexAt()`을 통해 개별 `JSCellPlan` 객체를 얻습니다.

```javascript
var cpCollection = Module.getAnalysis().getCellPlanCollection();
var cellPlan = cpCollection.createCellPlan(
    new Module.JSVector3D(127.0, 37.5, 50.0), // 시작 좌표
    0.0,    // 방위(orient)
    0.0,    // 기울기(tilt)
    500.0,  // 분석 거리(dist)
    30.0,   // 수평 화각(xAngle)
    20.0,   // 수직 화각(yAngle)
    5.0     // 섹터 세그먼트 각도(segAngle)
);
```

## JSCPCollection

### getCount() → number

> 등록된 가시권 분석(Cell Plan) 결과 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number(0 이상): 등록된 결과 개수.
    -   0: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = cpCollection.getCount();
```

{% endtab %}
{% endtabs %}

### indexAt(index) → [JSCellPlan](jscellplan.md#jscellplan)

> 지정한 인덱스에 해당하는 가시권 분석 결과 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | :----- | :----------- |
| index | number | 조회할 인덱스([getCount()](jscellplan.md#getcount-number) 범위 내). |

-   Return
    -   [JSCellPlan](jscellplan.md#jscellplan): 반환 성공.
    -   null: index가 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var cellPlan = cpCollection.indexAt(0);
```

{% endtab %}
{% endtabs %}

### createCellPlan(start, orient, tilt, distance, xAngle, yAngle, segmentAngle) → [JSCellPlan](jscellplan.md#jscellplan)

> 새로운 부채꼴(섹터) 가시권 분석을 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type                                  | Description                          |
| :----------- | ---------------------------------------- | ---------------------------------------- |
| start        | [JSVector3D](../core/jsvector3d.md)   | 분석 시작 좌표(경도, 위도, 고도).       |
| orient       | number                                    | 방위각(degrees).                        |
| tilt         | number                                    | 기울기 각도(degrees).                   |
| distance     | number                                    | 분석 거리(meters).                      |
| xAngle       | number                                    | 수평 화각(degrees).                     |
| yAngle       | number                                    | 수직 화각(degrees).                     |
| segmentAngle | number                                    | 섹터를 구성하는 세그먼트 단위 각도.      |

-   Return
    -   [JSCellPlan](jscellplan.md#jscellplan): 생성 성공.
    -   null: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var cellPlan = cpCollection.createCellPlan(
    new Module.JSVector3D(127.0, 37.5, 50.0), 0.0, 0.0, 500.0, 30.0, 20.0, 5.0
);
```

{% endtab %}
{% endtabs %}

### indexAtDelete(index) → boolean

> 지정한 인덱스에 해당하는 가시권 분석 결과를 삭제합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | :----- | :----------- |
| index | number | 삭제할 인덱스. |

-   Return
    -   true: 삭제 성공.
    -   false: 삭제 실패(index에 해당하는 항목이 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
cpCollection.indexAtDelete(0);
```

{% endtab %}
{% endtabs %}

### clear()

> 등록된 모든 가시권 분석 결과를 삭제합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
cpCollection.clear();
```

{% endtab %}
{% endtabs %}

### setColor(rangeColor, viewColor, notViewColor, viewBoundaryColor, notViewBoundaryColor)

> 가시권 분석 결과의 표시 색상(전체 범위, 가시 영역, 비가시 영역, 각 경계선)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name                 | Type                          | Description         |
| :------------------- | ----------------------------- | ------------------------ |
| rangeColor           | [JSColor](../core/jscolor.md) | 분석 범위(섹터) 색상.    |
| viewColor            | [JSColor](../core/jscolor.md) | 가시 영역 색상.          |
| notViewColor         | [JSColor](../core/jscolor.md) | 비가시 영역 색상.        |
| viewBoundaryColor    | [JSColor](../core/jscolor.md) | 가시 영역 경계선 색상.  |
| notViewBoundaryColor | [JSColor](../core/jscolor.md) | 비가시 영역 경계선 색상. |

{% endtab %}
{% tab title="Template" %}

```javascript
cpCollection.setColor(
    new Module.JSColor(100, 255, 255, 255),
    new Module.JSColor(150, 0, 255, 0),
    new Module.JSColor(150, 255, 0, 0),
    new Module.JSColor(255, 0, 255, 0),
    new Module.JSColor(255, 255, 0, 0)
);
```

{% endtab %}
{% endtabs %}

## JSCellPlan

### getPosition(), setPosition(position) → [JSVector3D](../core/jsvector3d.md)

> 가시권 분석 기준 시작 좌표를 설정합니다. 설정 후 [update()](jscellplan.md#update)를 호출해야 반영됩니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                  |
| :------- | -------------------------------------- | -------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 분석 시작 좌표(경도, 위도, 고도). |

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setPosition(new Module.JSVector3D(127.01, 37.51, 60.0));
cellPlan.update();
```

{% endtab %}
{% endtabs %}

### getOrient(), setOrient(orient) → number

> 분석 방위각을 설정합니다. 설정 후 [update()](jscellplan.md#update)를 호출해야 반영됩니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description   |
| :----- | :----- | -------------- |
| orient | number | 방위각(degrees). |

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setOrient(90.0);
cellPlan.update();
```

{% endtab %}
{% endtabs %}

### getTilt(), setTilt(tilt) → number

> 분석 기울기 각도를 설정합니다. 설정 후 [update()](jscellplan.md#update)를 호출해야 반영됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
| :--- | :----- | ---------------------- |
| tilt | number | 기울기 각도(degrees). |

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setTilt(-10.0);
cellPlan.update();
```

{% endtab %}
{% endtabs %}

### getDist(), setDist(distance) → number

> 분석 거리를 설정합니다. 설정 후 [update()](jscellplan.md#update)를 호출해야 반영됩니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description    |
| :------- | :----- | ------------------- |
| distance | number | 분석 거리(meters). |

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setDist(1000.0);
cellPlan.update();
```

{% endtab %}
{% endtabs %}

### getXAngle(), setXAngle(angle) → number

> 분석 수평 화각을 설정합니다. 설정 후 [update()](jscellplan.md#update)를 호출해야 반영됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
| :---- | :----- | ------------------------ |
| angle | number | 수평 화각(degrees).     |

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setXAngle(45.0);
cellPlan.update();
```

{% endtab %}
{% endtabs %}

### getYAngle(), setYAngle(angle) → number

> 분석 수직 화각을 설정합니다. 설정 후 [update()](jscellplan.md#update)를 호출해야 반영됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
| :---- | :----- | ------------------------ |
| angle | number | 수직 화각(degrees).     |

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setYAngle(30.0);
cellPlan.update();
```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean

> 가시권 분석 결과의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                              |
| :------ | ------- | --------------------------------------------- |
| visible | boolean | <p>true: 가시화.<br>false: 비가시화.</p>       |

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setVisible(true);
```

{% endtab %}
{% endtabs %}

### getViewshedVisibleRatio() → number

> 분석 범위 대비 실제로 보이는(가시) 영역의 비율을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 가시 영역 비율(0.0 ~ 1.0 범위로 추정).

{% endtab %}
{% tab title="Template" %}

```javascript
var ratio = cellPlan.getViewshedVisibleRatio();
```

{% endtab %}
{% endtabs %}

### getIntersectionRatio() → number

> 분석 대상 볼륨과 실제 교차(간섭) 볼륨의 비율을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 교차 볼륨 비율(`m_sVol / m_tVol`).

{% endtab %}
{% tab title="Template" %}

```javascript
var ratio = cellPlan.getIntersectionRatio();
```

{% endtab %}
{% endtabs %}

### setCoverMode(set)

> 분석 결과를 지형/객체 위를 덮는(Cover) 형태로 표시할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                     |
| :--- | ------- | --------------------------------------------------- |
| set  | boolean | <p>true: Cover 모드 사용.<br>false: 일반 모드.</p>   |

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setCoverMode(true);
```

{% endtab %}
{% endtabs %}

### update()

> [getPosition](jscellplan.md#getposition-setposition-position-jsvector3d), [getOrient](jscellplan.md#getorient-setorient-orient-number), [getTilt](jscellplan.md#gettilt-settilt-tilt-number), [getDist](jscellplan.md#getdist-setdist-distance-number), [getXAngle](jscellplan.md#getxangle-setxangle-angle-number), [getYAngle](jscellplan.md#getyangle-setyangle-angle-number)로 변경한 설정값을 반영하여 가시권 분석을 다시 계산합니다.

{% tabs %}
{% tab title="Information" %}

-   Note
    -   월드가 초기화되지 않은 경우 아무 동작도 하지 않습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
cellPlan.setDist(1500.0);
cellPlan.setXAngle(60.0);
cellPlan.update();
```

{% endtab %}
{% endtabs %}
