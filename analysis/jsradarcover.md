---
description: 레이더/시선 기반 가시권(전파 도달 범위) 분석(Radar Cover) 결과를 조회 및 설정하기 위한 API 입니다.
---

# JSRadarCover / JSRCCollection

> 이 문서는 하나의 짝을 이루는 두 cpp 파일에 정의된 클래스, `JSRadarCover`(JSRadarCover.cpp, 개별 분석 결과)와 `JSRCCollection`(JSRCCollection.cpp, 분석 결과 목록 컨테이너)을 함께 다룹니다.
>
> `JSRCCollection`은 [JSAnalysis](jsanalysis.md)를 통해 접근하는 전역 레이더 가시권 분석 결과 목록 컨테이너이며, `JSRCCollection.createRadarCover()` 또는 `indexAt()`을 통해 개별 `JSRadarCover` 객체를 얻습니다.

```javascript
var rcCollection = Module.getAnalysis().getRadarCoverCollection();
var radarCover = rcCollection.createRadarCover(
    new Module.JSVector3D(127.0, 37.5, 50.0), // 시작 좌표
    0.0,    // 방위(orient)
    0.0,    // 기울기(tilt)
    500.0,  // 분석 거리(dist)
    360.0,  // 수평 화각(xAngle)
    30.0,   // 수직 화각(yAngle)
    5.0     // 세그먼트 각도(segAngle)
);
```

## JSRCCollection

### getCount() → number

> 등록된 레이더 가시권 분석 결과 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number(0 이상): 등록된 결과 개수.
    -   0: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = rcCollection.getCount();
```

{% endtab %}
{% endtabs %}

### indexAt(index) → [JSRadarCover](jsradarcover.md#jsradarcover)

> 지정한 인덱스에 해당하는 레이더 가시권 분석 결과 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | :----- | :----------- |
| index | number | 조회할 인덱스([getCount()](jsradarcover.md#getcount-number) 범위 내). |

-   Return
    -   [JSRadarCover](jsradarcover.md#jsradarcover): 반환 성공.
    -   null: index가 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var radarCover = rcCollection.indexAt(0);
```

{% endtab %}
{% endtabs %}

### createRadarCover(start, orient, tilt, distance, xAngle, yAngle, segmentAngle) → [JSRadarCover](jsradarcover.md#jsradarcover)

> 새로운 레이더 가시권(구형) 분석을 생성합니다.

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
| segmentAngle | number                                    | 분석 세그먼트 단위 각도.                 |

-   Return
    -   [JSRadarCover](jsradarcover.md#jsradarcover): 생성 성공.
    -   null: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var radarCover = rcCollection.createRadarCover(
    new Module.JSVector3D(127.0, 37.5, 50.0), 0.0, 0.0, 500.0, 360.0, 30.0, 5.0
);
```

{% endtab %}
{% endtabs %}

### indexAtDelete(index) → boolean

> 지정한 인덱스에 해당하는 레이더 가시권 분석 결과를 삭제합니다.

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
rcCollection.indexAtDelete(0);
```

{% endtab %}
{% endtabs %}

### clear()

> 등록된 모든 레이더 가시권 분석 결과를 삭제합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
rcCollection.clear();
```

{% endtab %}
{% endtabs %}

### setColor(rangeColor, viewColor, notViewColor)

> 분석 결과의 표시 색상(분석 범위, 가시 영역, 비가시 영역)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type                          | Description       |
| :----------- | ----------------------------- | ------------------ |
| rangeColor   | [JSColor](../core/jscolor.md) | 분석 범위 색상.    |
| viewColor    | [JSColor](../core/jscolor.md) | 가시 영역 색상.    |
| notViewColor | [JSColor](../core/jscolor.md) | 비가시 영역 색상.  |

{% endtab %}
{% tab title="Template" %}

```javascript
rcCollection.setColor(
    new Module.JSColor(100, 255, 255, 255),
    new Module.JSColor(150, 0, 255, 0),
    new Module.JSColor(150, 255, 0, 0)
);
```

{% endtab %}
{% endtabs %}

### analysisCover(option) → object

> 구형(sphere), 그리드형(grid), 사용자 지정 경로(custom) 세 가지 방식 중 하나로 가시권 분석을 수행하고, 분석된 각 시선(line) 정보를 배열로 반환합니다.
>
> 결과로 반환된 정보를 바탕으로 [create3DLayByJson()](jsradarcover.md#create3dlaybyjsonlays-boolean)를 호출하여 실제 3D 가시화를 생성할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name                        | Type     | Description                                                              |
| :-------------------------- | -------- | ---------------------------------------------------------------------------- |
| option                      | object   | 분석 옵션.                                                                |
| ↳ type                      | string   | 분석 방식("grid": 그리드형, "custom": 사용자 지정 경로, 그 외: 구형).      |
| ↳ progressCallback          | function(optional) | 분석 진행 상황 콜백.                                          |
| ↳ position                  | object   | 분석 시작 좌표 `{x, y, z, projection}`(type이 "custom"이 아닐 때 필수).    |
| ↳ range.pan                 | number   | (구형 전용) 수평 화각.                                                    |
| ↳ range.tilt                | number   | (구형 전용) 수직 화각.                                                    |
| ↳ range.distance            | number   | (구형 전용) 분석 거리.                                                    |
| ↳ angle.orient              | number   | (구형 전용) 방위각.                                                       |
| ↳ angle.tilt                | number   | (구형 전용) 기울기 각도.                                                  |
| ↳ angle.segment             | number   | (구형 전용) 세그먼트 각도.                                                |
| ↳ grid.cellCount.x/y/z      | number   | (그리드 전용) 각 축 셀 개수.                                              |
| ↳ grid.cellSize.x/y/z       | number   | (그리드 전용) 각 축 셀 크기.                                              |
| ↳ limit.range.pan/tilt      | number(optional) | (그리드 전용) 분석 반경 제한(기본값 pan 360, tilt 30).           |
| ↳ limit.angle.orient/tilt   | number(optional) | (그리드 전용) 분석 방향 제한(기본값 0).                          |
| ↳ lays                      | array(object)(optional) | (사용자 지정 경로 전용) 분석 경로 목록 `{from, to}` 또는 `{from, angle}`. |

-   Return
    -   object(array): 분석된 시선(line) 목록. 각 요소는 `from`, `to`, `direction`, `info`(거리별 피킹 정보) 및 (그리드형의 경우) `cellID` 또는 (구형의 경우) `index`를 포함.
    -   null: 월드가 초기화되지 않았거나, option이 유효하지 않거나, 분석에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var result = rcCollection.analysisCover({
    type: "sphere",
    position: { x: 127.0, y: 37.5, z: 50.0, projection: "EPSG:4326" },
    range: { pan: 360, tilt: 30, distance: 1000 },
    angle: { orient: 0, tilt: 0, segment: 5 }
});
```

{% endtab %}
{% endtabs %}

### create3DLayByJson(lays) → boolean

> [analysisCover()](jsradarcover.md#analysiscoveroption-object)의 결과(각 시선별 `visible` 정보가 포함된 배열)를 입력받아, 가시/비가시 구간을 색상으로 구분한 3D 시각화 라인을 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type          | Description                                                                     |
| :--- | ------------- | ------------------------------------------------------------------------------ |
| lays | array(object) | 시선 목록. 각 요소는 `from`, `to`, `direction`, `visible.distance/color/isVisible` 정보를 포함. |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   월드가 초기화되지 않았거나 lays가 없거나 비어있는 경우.
        -   각 요소의 `visible.color`, `visible.isVisible` 배열 길이가 다르거나 비어있는 경우.
        -   생성된 가시/비가시 정점이 2개 미만인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var result = rcCollection.analysisCover({ type: "sphere", /* ... */ });
rcCollection.create3DLayByJson(result);
```

{% endtab %}
{% endtabs %}

## JSRadarCover

### getPosition() → [JSVector3D](../core/jsvector3d.md)

> 분석 시작 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 분석 시작 좌표(경도, 위도, 고도).

{% endtab %}
{% tab title="Template" %}

```javascript
var position = radarCover.getPosition();
```

{% endtab %}
{% endtabs %}

### getOrient() → number

> 분석 방위각을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 방위각(degrees).

{% endtab %}
{% tab title="Template" %}

```javascript
var orient = radarCover.getOrient();
```

{% endtab %}
{% endtabs %}

### getTilt() → number

> 분석 기울기 각도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 기울기 각도(degrees).

{% endtab %}
{% tab title="Template" %}

```javascript
var tilt = radarCover.getTilt();
```

{% endtab %}
{% endtabs %}

### getDist() → number

> 분석 거리를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 분석 거리(meters).

{% endtab %}
{% tab title="Template" %}

```javascript
var dist = radarCover.getDist();
```

{% endtab %}
{% endtabs %}

### getXAngle() → number

> 분석 수평 화각을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 수평 화각(degrees).

{% endtab %}
{% tab title="Template" %}

```javascript
var xAngle = radarCover.getXAngle();
```

{% endtab %}
{% endtabs %}

### getYAngle() → number

> 분석 수직 화각을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 수직 화각(degrees).

{% endtab %}
{% tab title="Template" %}

```javascript
var yAngle = radarCover.getYAngle();
```

{% endtab %}
{% endtabs %}

### getVisible(index) → boolean

> 지정한 섹션 인덱스(0: 가시 영역, 1: 비가시 영역)의 가시화 여부를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                    |
| :---- | :----- | ---------------------------------- |
| index | number | 조회할 섹션 인덱스(0 또는 1).      |

-   Return
    -   true: 가시화 상태.
    -   false: 비가시화 상태이거나, index가 유효 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var isVisibleSectionShown = radarCover.getVisible(0);
```

{% endtab %}
{% endtabs %}

### setVisible(visible, notVisible)

> 가시 영역(섹션 0)과 비가시 영역(섹션 1)의 가시화 여부를 각각 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type    | Description                     |
| :--------- | ------- | ------------------------------------ |
| visible    | boolean | 가시 영역(섹션 0) 가시화 여부.       |
| notVisible | boolean | 비가시 영역(섹션 1) 가시화 여부.     |

{% endtab %}
{% tab title="Template" %}

```javascript
radarCover.setVisible(true, false); // 가시 영역만 표시
```

{% endtab %}
{% endtabs %}

### getViewRatio() → number

> 분석 대상 볼륨 대비 실제 가시(교차) 볼륨의 비율을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 가시 볼륨 비율(`m_sVol / m_tVol`).

{% endtab %}
{% tab title="Template" %}

```javascript
var ratio = radarCover.getViewRatio();
```

{% endtab %}
{% endtabs %}

### create3DGrid(option) → boolean

> 그리드 기반 분석을 위한 3D 격자를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name                          | Type   | Description                                              |
| :---------------------------- | ------ | ------------------------------------------------------------ |
| option                        | object | 격자 생성 옵션.                                              |
| ↳ position.x/y                | number | 격자 중심점 평면(TM) 좌표.                                   |
| ↳ position.z                  | number | 격자 중심점 고도.                                            |
| ↳ position.projCode           | number | 좌표계 코드(TM 계열만 지원, 경위도 좌표계(13)는 사용 불가).  |
| ↳ cellCnt.x/y/z                | number | 각 축 셀 개수.                                              |
| ↳ cellSize.x/y/z               | number | 각 축 셀 크기.                                              |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   option, position, grid, cellCnt, cellSize 중 필수 항목이 없는 경우.
        -   position.projCode가 13(EPSG:4326, 경위도)인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
radarCover.create3DGrid({
    position: { x: 198000.0, y: 450000.0, z: 0.0, projCode: 5186 },
    grid: {},
    cellCnt: { x: 10, y: 10, z: 5 },
    cellSize: { x: 10.0, y: 10.0, z: 10.0 }
});
```

{% endtab %}
{% endtabs %}

### analysis3DGridCover(callback) → object

> [create3DGrid()](jsradarcover.md#create3dgridoption-boolean)로 생성한 격자를 기준으로 각 셀의 가시권 분석을 수행하고 결과를 JSON 형태로 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description             |
| :------- | -------- | -------------------------- |
| callback | function | 분석 진행 시 호출되는 콜백. |

-   Return
    -   object: 분석 결과 JSON.
    -   null: 월드가 초기화되지 않았거나, [create3DGrid()](jsradarcover.md#create3dgridoption-boolean)로 격자가 생성되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var result = radarCover.analysis3DGridCover(function(progress) {
    console.log(progress);
});
```

{% endtab %}
{% endtabs %}
