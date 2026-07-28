---
description: JSON 데이터를 기반으로 포인트/라인/그리드/폴리곤 형태의 대량 데이터를 시각화하기 위한 API 입니다.
---

# JSDataVisualizer

> Module.getDataVisualizer() API를 통해 획득하는 데이터 시각화 관리 객체입니다.
>
> JSON 형태로 전달된 데이터를 포인트(Position), 라인(Line), 그리드(Grid), 폴리곤(Polygon) 시각화 객체로 변환하여 지도에 표시하고, 생성된 객체를 key 문자열 단위로 조회/조작(색상, 애니메이션, 가시화 옵션, 인스턴스 단위 효과 등)합니다.
>
> 내부적으로 `.constructor<>()`도 등록되어 있어 `new Module.JSDataVisualizer()`로 직접 생성할 수도 있으나, 엔진이 관리하는 단일 인스턴스를 그대로 사용하려면 `Module.getDataVisualizer()`를 사용하는 것이 일반적입니다.

```javascript
var visualizer = Module.getDataVisualizer();
```

## Function

### getType() → string

> 객체 타입 문자열(`"JSDataVisualizer"`)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: `"JSDataVisualizer"` 고정 문자열.

{% endtab %}
{% tab title="Template" %}

```javascript
var strType = visualizer.getType();
```

{% endtab %}
{% endtabs %}

### add(json) → boolean

> JSON 문자열로 전달된 정의에 따라 하나 이상의 데이터 시각화 객체를 생성합니다.
>
> 최상위 `objects` 배열의 각 항목이 하나의 시각화 객체(`key`)가 되며, `dataType`에 따라 포인트/라인/그리드/폴리곤 생성 로직으로 분기됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                     |
| ---- | ------ | -------------------------------- |
| json | string | 아래 구조를 따르는 JSON 문자열. |

**최상위 구조**

| Name             | Type    | Required | Description |
| ---------------- | ------- | -------- | ----------- |
| loadDataCallback | string  |          | 데이터 로드 후 인스턴스 가시거리 진입/이탈 시 호출할 전역(global) JS 함수 이름. |
| objects           | array   | ✔        | 시각화 객체 정의 목록. 아래 [JSDataVisualizer.AddObject](jsdatavisualizer.md#jsdatavisualizer.addobject) 참고. |

-   Return
    -   true: `objects` 배열의 모든 항목이 생성 성공한 경우.
    -   false: JSON 파싱 실패, `objects`가 없거나 배열이 아닌 경우, 또는 항목 중 하나라도 생성에 실패한 경우(단, 실패한 항목이 있어도 나머지 항목 처리는 계속됨).

{% endtab %}
{% tab title="Template" %}

```javascript
var json = JSON.stringify({
    objects: [
        {
            key: "POINT_1",
            dataType: "position",
            shape: "cylinder",
            minDistance: 0,
            maxDistance: 50000,
            autoFocus: true,
            data: [
                { id: "p1", position: [127.0, 37.5, 0], value: 10 },
                { id: "p2", position: [127.01, 37.5, 0], value: 20 }
            ],
            legend: [
                { value: 0, color: [0, 255, 0, 255] },
                { value: 50, color: [255, 0, 0, 255] }
            ]
        }
    ]
});

visualizer.add(json);
```

{% endtab %}
{% endtabs %}

### addMultiObject(json) → boolean

> `add()`와 동일한 JSON 구조를 사용하지만, 동일한 `data`/색상 범례를 공유하는 다중 오브젝트(멀티 인스턴스) 생성 전용 API입니다. 현재는 `dataType === "position"`만 지원합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                     |
| ---- | ------ | -------------------------------- |
| json | string | `add()`와 동일한 최상위 구조(`objects` 배열)의 JSON 문자열. |

-   Return
    -   true: `objects` 배열의 모든 항목이 생성 성공한 경우.
    -   false: JSON 파싱 실패, `objects`가 없거나 배열이 아닌 경우, 또는 `dataType`이 `"position"`이 아니어서 생성되지 않은 경우 등.

{% endtab %}
{% tab title="Template" %}

```javascript
var json = JSON.stringify({
    objects: [
        {
            key: "MULTI_1",
            dataType: "position",
            shape: "icon",
            data: [
                { id: "m1", position: [127.0, 37.5, 0], value: 5 }
            ]
        }
    ]
});

visualizer.addMultiObject(json);
```

{% endtab %}
{% endtabs %}

### removeAll() → void

> 생성된 모든 데이터 시각화 객체를 삭제합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   없음(void). 지도가 준비되지 않았거나 데이터 시각화 관리자가 없는 경우 아무 동작도 하지 않습니다.
-   Description
    -   삭제 전 현재 선택된 객체(`setSelectObj`)를 해제합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.removeAll();
```

{% endtab %}
{% endtabs %}

### remove(id) → boolean

> key(`id`)와 일치하는 데이터 시각화 객체 하나를 삭제합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
| ---- | ------ | ------------------ |
| id   | string | 삭제할 객체의 key. |

-   Return
    -   true: 삭제 성공.
    -   false: 지도가 준비되지 않았거나, 일치하는 key를 가진 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.remove("POINT_1");
```

{% endtab %}
{% endtabs %}

### setWeight(key, x, y, z) → boolean

> key에 해당하는 객체의 크기 가중치(weight)를 설정합니다.
>
> `VERTICAL_LINE`(수직선) 표현 방식인 경우 (x, y, z)를 그대로 적용하고, 그 외에는 (x, z, y) 순서로 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| key  | string | 대상 객체 key. |
| x    | number | x축 가중치.    |
| y    | number | y축 가중치.    |
| z    | number | z축 가중치.    |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 준비되지 않았거나, key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setWeight("POINT_1", 1.0, 1.0, 2.0);
```

{% endtab %}
{% endtabs %}

### setAnimationSpeed(key, speed) → boolean

> 포인트(인스턴스) 객체의 애니메이션(예: path 이동) 재생 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| ----- | ------ | ------------------ |
| key   | string | 대상 객체 key.      |
| speed | number | 애니메이션 재생 속도. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 준비되지 않았거나, key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setAnimationSpeed("POINT_1", 2.0);
```

{% endtab %}
{% endtabs %}

### setAnimationRate(key, animationRate) → boolean

> 포인트(인스턴스) 객체의 애니메이션 진행률(rate)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type   | Description        |
| ------------- | ------ | -------------------- |
| key           | string | 대상 객체 key.       |
| animationRate | number | 애니메이션 진행률.   |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 준비되지 않았거나, key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setAnimationRate("POINT_1", 0.5);
```

{% endtab %}
{% endtabs %}

### indexAtKey(index) → string

> index 순번에 해당하는 데이터 시각화 객체의 key 문자열을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
| ----- | ------ | -------------------- |
| index | number | 조회할 순번(0부터 시작). |

-   Return
    -   string: index에 해당하는 객체의 key.
    -   null: 지도가 준비되지 않았거나, index가 전체 개수 이상인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = visualizer.count();
for (var i = 0; i < count; i++) {
    console.log(visualizer.indexAtKey(i));
}
```

{% endtab %}
{% endtabs %}

### count() → number

> 생성된 데이터 시각화 객체의 총 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 객체 개수. 지도가 준비되지 않았거나 데이터 시각화 관리자가 없는 경우 0.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = visualizer.count();
```

{% endtab %}
{% endtabs %}

### focus(key) → void

> key에 해당하는 객체의 공간 영역(경위도 범위)으로 카메라를 이동시킵니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| key  | string | 대상 객체 key. |

-   Return
    -   없음(void). 대상 객체가 없거나 영역 정보를 구할 수 없으면 아무 동작도 하지 않습니다.
-   Description
    -   카메라 고도는 화면에 전체 영역이 들어오도록 자동 계산되며, 계산값이 `NaN`이거나 1000 미만이면 1000(m)으로 보정됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.focus("POINT_1");
```

{% endtab %}
{% endtabs %}

### getInstancePosition(key, instanceId) → [JSVector3D](../core/jsvector3d.md)

> key로 지정된 객체 내에서 instanceId에 해당하는 개별 인스턴스(점/심볼 등)의 현재 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description        |
| ---------- | ------ | -------------------- |
| key        | string | 대상 객체 key.       |
| instanceId | string | 인스턴스 id(`data[].id`). |

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 좌표(경도, 위도, 고도) 반환 성공.
    -   null: 지도가 준비되지 않았거나, key/instanceId가 일치하는 인스턴스가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var pos = visualizer.getInstancePosition("POINT_1", "p1");
```

{% endtab %}
{% endtabs %}

### setUnionTerrain(key, set) → boolean

> key에 해당하는 객체의 지형 결합(Union Terrain) 가시화 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                |
| ---- | ------- | -------------------------------------------- |
| key  | string  | 대상 객체 key.                                |
| set  | boolean | true: 지형 결합 가시화, false: 기본 가시화.  |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setUnionTerrain("POINT_1", true);
```

{% endtab %}
{% endtabs %}

### setZbuffer(key, set) → boolean

> key에 해당하는 객체의 Z-buffer(깊이 테스트) 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                    |
| ---- | ------- | -------------------------------- |
| key  | string  | 대상 객체 key.                   |
| set  | boolean | true: Z-buffer 사용, false: 미사용. |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setZbuffer("POINT_1", false);
```

{% endtab %}
{% endtabs %}

### setUnionTerrainAltitude(key, altitude) → boolean

> key에 해당하는 객체의 지형 결합 고도(오프셋)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description       |
| -------- | ------ | ------------------- |
| key      | string | 대상 객체 key.       |
| altitude | number | 지형 결합 고도(m).  |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setUnionTerrainAltitude("POINT_1", 5.0);
```

{% endtab %}
{% endtabs %}

### setUnderground(key, underground) → boolean

> key에 해당하는 객체를 지하(underground) 상태로 표시할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type    | Description                                                    |
| ----------- | ------- | ------------------------------------------------------------------ |
| key         | string  | 대상 객체 key.                                                   |
| underground | boolean | true: 지하 상태(`ELEVATION_STATUS_BELOW`), false: 지상 상태(`ELEVATION_STATUS_ABOVE`). |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setUnderground("POINT_1", true);
```

{% endtab %}
{% endtabs %}

### getMapPositionByScreenPosition(key, screenX, screenY) → [JSVector3D](../core/jsvector3d.md)

> 화면 좌표(픽셀)에 대응하는, key 객체가 표현하는 지도상의 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description        |
| ------- | ------ | -------------------- |
| key     | string | 대상 객체 key.       |
| screenX | number | 화면 x 좌표(px).     |
| screenY | number | 화면 y 좌표(px).     |

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 좌표(경도, 위도, 고도) 반환 성공.
    -   null: 지도가 준비되지 않았거나, key가 일치하는 객체가 없거나, 화면 좌표에 대응하는 위치를 찾지 못한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var pos = visualizer.getMapPositionByScreenPosition("POINT_1", 400, 300);
```

{% endtab %}
{% endtabs %}

### getIntersectWithLine(key, from, to) → [JSVector3D](../core/jsvector3d.md)

> key 객체와 두 좌표(`from`, `to`)로 이루어진 선분의 교차점을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                                 | Description             |
| ---- | ------------------------------------- | ------------------------ |
| key  | string                                 | 대상 객체 key.           |
| from | [JSVector3D](../core/jsvector3d.md)  | 선분 시작 좌표.          |
| to   | [JSVector3D](../core/jsvector3d.md)  | 선분 끝 좌표.            |

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 교차점 좌표(경도, 위도, 고도) 반환 성공.
    -   null: 지도가 준비되지 않았거나, key가 일치하는 객체가 없거나, 교차점이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var from = new Module.JSVector3D(127.0, 37.5, 1000.0);
var to = new Module.JSVector3D(127.0, 37.5, -1000.0);
var hit = visualizer.getIntersectWithLine("POINT_1", from, to);
```

{% endtab %}
{% endtabs %}

### setLegend(key, legend) → boolean

> key 객체에 값(value)-색상(color) 구간으로 이루어진 색상 범례를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type  | Description                                                                       |
| ------ | ----- | ----------------------------------------------------------------------------------- |
| key    | string | 대상 객체 key.                                                                     |
| legend | array | [JSDataVisualizer.LegendItem](jsdatavisualizer.md#jsdatavisualizer.legenditem) 배열. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
        -   `legend`가 배열이 아닌 경우.
        -   각 항목에 `value`/`color` 속성이 없거나 `color`가 4개 요소 배열이 아닌 경우(해당 항목만 무시하고 계속 진행).
        -   유효한 항목이 하나도 없는 경우.
        -   key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLegend("POINT_1", [
    { value: 0, color: [0, 255, 0, 255] },
    { value: 50, color: [255, 255, 0, 255] },
    { value: 100, color: [255, 0, 0, 255] }
]);
```

{% endtab %}
{% endtabs %}

### clearLegend(key) → boolean

> key 객체에 설정된 색상 범례를 제거합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| key  | string | 대상 객체 key. |

-   Return
    -   true: 제거 성공.
    -   false: 지도가 준비되지 않았거나, key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.clearLegend("POINT_1");
```

{% endtab %}
{% endtabs %}

### setShape(key, option) → boolean

> 포인트(Position) 객체의 표현 형태(shape)를 문자열 또는 옵션 객체로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type            | Description |
| ------ | --------------- | ----------- |
| key    | string          | 대상 객체 key. |
| option | string \| object | 문자열인 경우 아래 shape 이름 중 하나. 객체인 경우 [JSDataVisualizer.ShapeOption](jsdatavisualizer.md#jsdatavisualizer.shapeoption) 참고. |

**문자열로 지정 가능한 shape 이름**

`vertical_line`, `cylinder`, `rect`, `circle`, `sphere`, `pointcloud2d`, `pointcloud3d`, `arrow2d`, `arrow3d`, `polygon`, `box`, `mesh`, `point`, `cone`, `icon`, `flow`, `symbol` 등

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
        -   `key`가 빈 문자열이거나 `option`이 null인 경우.
        -   `option`이 string도 object도 아닌 경우.
        -   문자열이 위 shape 이름과 일치하지 않는 경우.
        -   대상 객체가 `POSITION` 타입이 아니거나 key가 일치하지 않는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setShape("POINT_1", "sphere");
```

{% endtab %}
{% endtabs %}

### setLineAnimationSpeed(key, speed) → boolean

> 라인 객체의 흐름 애니메이션 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| key   | string | 대상 객체 key(라인 타입). |
| speed | number | 애니메이션 속도. |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineAnimationSpeed("LINE_1", 20.0);
```

{% endtab %}
{% endtabs %}

### setLineWidth(key, width) → boolean

> 라인 객체의 두께(폭)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| key   | string | 대상 객체 key(라인 타입). |
| width | number | 라인 두께.     |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineWidth("LINE_1", 15.0);
```

{% endtab %}
{% endtabs %}

### setLineStrokeWidth(key, strokewidth) → boolean

> 라인 객체의 외곽선(스트로크) 두께를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type   | Description   |
| ----------- | ------ | -------------- |
| key         | string | 대상 객체 key(라인 타입). |
| strokewidth | number | 외곽선 두께.   |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineStrokeWidth("LINE_1", 5.0);
```

{% endtab %}
{% endtabs %}

### setLineDensity(key, density) → boolean

> 라인 객체의 패턴(대시/화살표 등) 밀도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description   |
| ------- | ------ | -------------- |
| key     | string | 대상 객체 key(라인 타입). |
| density | number | 패턴 밀도.     |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineDensity("LINE_1", 2.0);
```

{% endtab %}
{% endtabs %}

### setLineAnimation(key, animation) → boolean

> 라인 객체의 흐름 애니메이션 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description   |
| --------- | ------- | -------------- |
| key       | string  | 대상 객체 key(라인 타입). |
| animation | boolean | true: 애니메이션 사용, false: 미사용. |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineAnimation("LINE_1", true);
```

{% endtab %}
{% endtabs %}

### setLineSymbolAnimation(key, animation) → boolean

> 라인에 부착된 심볼(3D 메쉬)의 애니메이션(이동) 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description   |
| --------- | ------- | -------------- |
| key       | string  | 대상 객체 key(라인 타입). |
| animation | boolean | true: 심볼 애니메이션 사용, false: 미사용. |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineSymbolAnimation("LINE_1", true);
```

{% endtab %}
{% endtabs %}

### setLineSymbol(key, options) → boolean

> 라인 위에 표시할 심볼(3D 메쉬) 또는 아이콘(이미지)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description |
| ------- | ------ | ----------- |
| key     | string | 대상 객체 key(라인 타입). |
| options | object | [JSDataVisualizer.LineSymbolOption](jsdatavisualizer.md#jsdatavisualizer.linesymboloption) 참고. |

-   Return
    -   true: 설정 성공(리소스가 없는 경우에도 심볼/아이콘 해제로 처리되어 true 반환).
    -   false: 설정 실패.
        -   `key`가 비어있거나, `options`가 object 타입이 아닌 경우.
        -   지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.
        -   `symbol.data`/`icon.data`의 각 배열 요소가 숫자가 아닌 경우.
        -   3ds 파싱 또는 텍스처 로드에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineSymbol("LINE_1", {
    icon: { data: base64ImageString }
});
```

{% endtab %}
{% endtabs %}

### setLineSymbolAnimationSpeed(key, speed) → boolean

> 라인에 부착된 심볼의 애니메이션(이동) 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| key   | string | 대상 객체 key(라인 타입). |
| speed | number | 심볼 애니메이션 속도. |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineSymbolAnimationSpeed("LINE_1", 10.0);
```

{% endtab %}
{% endtabs %}

### setLineSymbolRotate(key, rotate) → boolean

> 라인에 부착된 심볼(3D 메쉬)의 회전값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                | Description        |
| ------ | ------------------------------------ | -------------------- |
| key    | string                                | 대상 객체 key(라인 타입). |
| rotate | [JSVector3D](../core/jsvector3d.md) | 회전값(x, y, z 각도). |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineSymbolRotate("LINE_1", new Module.JSVector3D(0, 0, 90));
```

{% endtab %}
{% endtabs %}

### setLineSizeFixed(key, sizefix) → boolean

> 라인 두께(또는 심볼 크기)가 화면상에서 고정된 크기로 표시될지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                     |
| ------- | ------- | -------------------------------------------------- |
| key     | string  | 대상 객체 key(라인 타입).                          |
| sizefix | boolean | true: 화면 고정 크기, false: 월드 단위 크기.       |

-   Return
    -   true: 설정 성공.
    -   false: `key`가 비어있거나, 지도가 준비되지 않았거나, key에 해당하는 라인 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setLineSizeFixed("LINE_1", true);
```

{% endtab %}
{% endtabs %}

### setInstanceEffect(key, instanceId, set) → boolean

> key 객체 내 특정 instanceId의 강조 효과(실루엣 타입 2)를 켜거나 끕니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type    | Description                             |
| ---------- | ------- | ------------------------------------------ |
| key        | string  | 대상 객체 key.                            |
| instanceId | string  | 인스턴스 id.                               |
| set        | boolean | true: 효과 활성화(실루엣 타입 2), false: 비활성화(타입 -1). |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 준비되지 않았거나, key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setInstanceEffect("POINT_1", "p1", true);
```

{% endtab %}
{% endtabs %}

### setInstanceSilhouette(key, instanceId, type) → boolean

> key 객체 내 특정 instanceId의 실루엣(윤곽선) 표현 타입을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description   |
| ---------- | ------ | -------------- |
| key        | string | 대상 객체 key. |
| instanceId | string | 인스턴스 id.   |
| type       | number | 실루엣 타입(엔진 내부 정의값, -1: 없음). |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 준비되지 않았거나, key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setInstanceSilhouette("POINT_1", "p1", 2);
```

{% endtab %}
{% endtabs %}

### setPositionValues(key, values) → boolean

> 포인트(Position) 객체의 값(value)을 갱신합니다. 배열의 첫 요소 타입에 따라 두 가지 방식으로 동작합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type  | Description |
| ------ | ----- | ----------- |
| key    | string | 대상 객체 key(포인트 타입). |
| values | array  | 요소가 object이면 `[{ id, value }, ...]`(instance 단위 갱신), 요소가 number이면 `[value, value, ...]`(전체 인스턴스 순서대로 일괄 갱신). |

-   Return
    -   true: 갱신 성공.
    -   false: 지도가 준비되지 않았거나, `values`가 빈 배열이거나 배열이 아닌 경우, key와 일치하는 POSITION 타입 객체가 없는 경우.
-   Description
    -   object 형태 항목 중 `id`/`value`가 없거나 `value`가 숫자가 아닌 항목은 건너뜁니다.

{% endtab %}
{% tab title="Template" %}

```javascript
// 인스턴스 단위 갱신
visualizer.setPositionValues("POINT_1", [
    { id: "p1", value: 30 },
    { id: "p2", value: 60 }
]);

// 전체 인스턴스 일괄 갱신(순서대로)
visualizer.setPositionValues("POINT_1", [30, 60]);
```

{% endtab %}
{% endtabs %}

### setPositionColor(key, color) → boolean

> 포인트(Position) 객체 전체의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type  | Description                                        |
| ----- | ----- | ---------------------------------------------------- |
| key   | string | 대상 객체 key(포인트 타입).                        |
| color | array  | `[R, G, B, A]` 형태의 숫자 배열(0~255).             |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
        -   `color`가 배열이 아니거나 요소가 4개가 아닌 경우.
        -   지도가 준비되지 않았거나, key와 일치하는 POSITION 타입 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPositionColor("POINT_1", [255, 0, 0, 255]);
```

{% endtab %}
{% endtabs %}

### setEffectSilhouetteThickness(key, thickness) → boolean

> key 객체의 실루엣(윤곽선) 효과 두께를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description   |
| --------- | ------ | -------------- |
| key       | string | 대상 객체 key. |
| thickness | number | 실루엣 두께.   |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setEffectSilhouetteThickness("POINT_1", 2.0);
```

{% endtab %}
{% endtabs %}

### setEffectSpinSpeed(key, speed) → boolean

> key 객체의 회전(spin) 효과 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| key   | string | 대상 객체 key. |
| speed | number | 회전 속도.     |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setEffectSpinSpeed("POINT_1", 1.5);
```

{% endtab %}
{% endtabs %}

### setSilhouette(key, set) → boolean

> key 객체의 실루엣(윤곽선) 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                    |
| ---- | ------- | -------------------------------- |
| key  | string  | 대상 객체 key.                   |
| set  | boolean | true: 실루엣 표시, false: 표시 안 함. |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setSilhouette("POINT_1", true);
```

{% endtab %}
{% endtabs %}

### getGridCell(key, instanceId) → object

> 그리드(Grid) 객체 내 특정 셀(instanceId)의 값/방향/기울기/좌표 정보를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description       |
| ---------- | ------ | ------------------- |
| key        | string | 대상 객체 key(그리드 타입). |
| instanceId | string | 셀 id.               |

-   Return (object)
    -   `value`(number): 셀 값.
    -   `direction`(number): 방향 값.
    -   `tilt`(number): 기울기 값.
    -   `idx`, `idy`(number): 셀 인덱스(x, y).
    -   `longitude`, `latitude`(number): 셀 위치가 유효한 경우에만 포함.
    -   null: 지도가 준비되지 않았거나, key가 그리드 타입이 아니거나, instanceId에 해당하는 셀이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var cell = visualizer.getGridCell("GRID_1", "0_0");
console.log(cell.value, cell.longitude, cell.latitude);
```

{% endtab %}
{% endtabs %}

### setPositionSizeModeValueWeight(key, weight) → boolean

> 포인트(Position) 객체의 크기 모드를 "값(value) 가중치 기반"으로 설정합니다. 값에 (weight.x, weight.y, weight.z)를 곱한 크기로 표현됩니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                | Description        |
| ------ | ------------------------------------ | -------------------- |
| key    | string                                | 대상 객체 key(포인트 타입). |
| weight | [JSVector3D](../core/jsvector3d.md) | 축별 가중치(x, y, z). |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 POSITION 타입 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPositionSizeModeValueWeight("POINT_1", new Module.JSVector3D(1, 1, 1));
```

{% endtab %}
{% endtabs %}

### setPositionSizeModeFixedScreen(key, size) → boolean

> 포인트 객체의 크기 모드를 "화면 고정 크기"로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description         |
| ---- | ------ | --------------------- |
| key  | string | 대상 객체 key(포인트 타입). |
| size | number | 화면 고정 크기(px).   |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 POSITION 타입 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPositionSizeModeFixedScreen("POINT_1", 20);
```

{% endtab %}
{% endtabs %}

### setPositionSizeModeFixedWorld(key, size) → boolean

> 포인트 객체의 크기 모드를 "월드(실제 좌표계) 고정 크기"로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type  | Description                              |
| ---- | ----- | ------------------------------------------- |
| key  | string | 대상 객체 key(포인트 타입).                |
| size | array  | `[x, y, z]` 형태의 숫자 배열 3개(월드 단위 크기). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
        -   key와 일치하는 POSITION 타입 객체가 없는 경우.
        -   `size`가 배열이 아니거나 요소가 3개가 아니거나 숫자가 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPositionSizeModeFixedWorld("POINT_1", [10, 10, 10]);
```

{% endtab %}
{% endtabs %}

### setVisibleDistance(key, min, max) → boolean

> key 객체의 가시화 거리 범위(최소/최대)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
| ---- | ------ | ------------------- |
| key  | string | 대상 객체 key.       |
| min  | number | 최소 가시화 거리(m). |
| max  | number | 최대 가시화 거리(m). |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setVisibleDistance("POINT_1", 0, 50000);
```

{% endtab %}
{% endtabs %}

### setTimestep(key, timestep) → boolean

> 포인트 객체가 다중 시계열 값(`data[].value`가 배열인 경우)을 가질 때, 표시할 시점(timestep) 인덱스를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description        |
| -------- | ------ | -------------------- |
| key      | string | 대상 객체 key(포인트 타입). |
| timestep | number | 시점 인덱스(0 이상). |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 POSITION 타입 객체가 없거나, `timestep`이 음수인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setTimestep("POINT_1", 3);
```

{% endtab %}
{% endtabs %}

### setPointCloudSize(key, size, is3d) → boolean

> 포인트 클라우드(`pointcloud2d`/`pointcloud3d`) shape의 점 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                |
| ---- | ------- | --------------------------------------------- |
| key  | string  | 대상 객체 key(포인트 타입).                  |
| size | number  | 점 크기(0 이상).                             |
| is3d | boolean | true: `pointcloud3d`, false: `pointcloud2d` 대상. |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 POSITION 타입 객체가 없거나, `size`가 음수인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPointCloudSize("CLOUD_1", 3.0, true);
```

{% endtab %}
{% endtabs %}

### setPointCloudRadius(key, radius, is3d) → boolean

> 포인트 클라우드 shape의 점 반경(radius)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                |
| ------ | ------- | --------------------------------------------- |
| key    | string  | 대상 객체 key(포인트 타입).                  |
| radius | number  | 점 반경(0 이상).                              |
| is3d   | boolean | true: `pointcloud3d`, false: `pointcloud2d` 대상. |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 POSITION 타입 객체가 없거나, `radius`가 음수인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPointCloudRadius("CLOUD_1", 0.5, true);
```

{% endtab %}
{% endtabs %}

### setPointCloudCount(key, count, is3d) → boolean

> 포인트 클라우드 shape을 구성하는 점 개수를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                                |
| ----- | ------- | --------------------------------------------- |
| key   | string  | 대상 객체 key(포인트 타입).                  |
| count | number  | 점 개수(0 이상).                              |
| is3d  | boolean | true: `pointcloud3d`, false: `pointcloud2d` 대상. |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 POSITION 타입 객체가 없거나, `count`가 음수인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPointCloudCount("CLOUD_1", 100, true);
```

{% endtab %}
{% endtabs %}

### setPositionThickness(key, thickness) → boolean

> 포인트 객체(예: `vertical_line`)의 두께를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| --------- | ------ | ------------------- |
| key       | string | 대상 객체 key(포인트 타입). |
| thickness | number | 두께(0 이상).       |

-   Return
    -   true: 설정 성공.
    -   false: `thickness`가 음수이거나, key와 일치하는 POSITION 타입 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPositionThickness("POINT_1", 2.0);
```

{% endtab %}
{% endtabs %}

### defaultByWeight(key, value, height) → boolean

> 특정 value 값을 기준으로 한 기본 높이(weight) 보정값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                         |
| ------ | ------ | -------------------------------------- |
| key    | string | 대상 객체 key(포인트 타입).           |
| value  | number | 기준이 되는 value 값.                 |
| height | number | 해당 value에 대응하는 높이(m).        |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 POSITION 타입 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.defaultByWeight("POINT_1", 50, 100.0);
```

{% endtab %}
{% endtabs %}

### setPointAnimation(key, play) → boolean

> 포인트 객체의 애니메이션(예: path 이동) 재생 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description               |
| ---- | ------- | ---------------------------- |
| key  | string  | 대상 객체 key(포인트 타입). |
| play | boolean | true: 애니메이션 재생, false: 정지. |

-   Return
    -   true: 설정 성공.
    -   false: key와 일치하는 POSITION 타입 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setPointAnimation("POINT_1", true);
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getOpacity(key), setOpacity(key, opacity) → number, boolean

> key 객체의 투명도(0.0 ~ 1.0)를 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description         |
| ------- | ------ | --------------------- |
| key     | string | 대상 객체 key.        |
| opacity | number | 투명도(0.0 ~ 1.0).    |

-   Return
    -   getOpacity(key): number - 투명도 값. key와 일치하는 객체가 없으면 `-1.0`.
    -   setOpacity(key, opacity): boolean - true(설정 성공) / false(key와 일치하는 객체가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setOpacity("POINT_1", 0.5);
var opacity = visualizer.getOpacity("POINT_1");
```

{% endtab %}
{% endtabs %}

### getUnionTerrainOffset(key), setUnionTerrainOffset(key, offset) → number, boolean

> key 객체의 지형 결합(Union Terrain) 렌더링 오프셋을 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description       |
| ------ | ------ | ------------------- |
| key    | string | 대상 객체 key.       |
| offset | number | 지형 결합 오프셋 값. |

-   Return
    -   getUnionTerrainOffset(key): number - 오프셋 값. key와 일치하는 객체가 없으면 `0.0`.
    -   setUnionTerrainOffset(key, offset): boolean - true(설정 성공) / false(key와 일치하는 객체가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setUnionTerrainOffset("POINT_1", 0.2);
var offset = visualizer.getUnionTerrainOffset("POINT_1");
```

{% endtab %}
{% endtabs %}

### getVisible(key), setVisible(key, set) → boolean, boolean

> key 객체의 가시화 여부를 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                     |
| ---- | ------- | ---------------------------------- |
| key  | string  | 대상 객체 key.                    |
| set  | boolean | true: 가시화, false: 비가시화.    |

-   Return
    -   getVisible(key): boolean - 가시화 상태. key와 일치하는 객체가 없으면 false.
    -   setVisible(key, set): boolean - true(설정 성공) / false(key와 일치하는 객체가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setVisible("POINT_1", false);
var visible = visualizer.getVisible("POINT_1");
```

{% endtab %}
{% endtabs %}

### getValueRange(key), setValueRange(key, min, max, timestep) → object, boolean

> key 객체의 값(value) 범위(최소/최대)를 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description                                          |
| -------- | ------ | ------------------------------------------------------- |
| key      | string | 대상 객체 key.                                         |
| min      | number | 최소값.                                                |
| max      | number | 최대값.                                                |
| timestep | number | 값 범위를 적용할 시점(timestep) 인덱스(기본값 0).      |

-   Return
    -   getValueRange(key): object `{ min, max }`. key가 없거나 값 범위를 구할 수 없으면 null.
    -   setValueRange(key, min, max, timestep): boolean - true(설정 성공) / false(key와 일치하는 POSITION 타입 객체가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
visualizer.setValueRange("POINT_1", 0, 100, 0);
var range = visualizer.getValueRange("POINT_1");
console.log(range.min, range.max);
```

{% endtab %}
{% endtabs %}

## Type Definitions

#### JSDataVisualizer.AddObject

> [add()](jsdatavisualizer.md#add-json-boolean) / [addMultiObject()](jsdatavisualizer.md#addmultiobject-json-boolean)의 `objects` 배열 항목 공통 구조입니다. `dataType`에 따라 실제로 사용되는 하위 속성이 달라집니다.

| Name                | Type    | Attributes | Default | Description |
| ------------------- | ------- | ---------- | ------- | ----------- |
| key                 | string  | 필수       |         | 시각화 객체 고유 key. |
| dataType            | string  | 필수       |         | `"position"`, `"line"`, `"grid"`, `"polygon"` 중 하나. |
| shape               | string  | 필수       |         | 표현 형태. [setShape()](jsdatavisualizer.md#setshape-key-option-boolean) 문자열 목록 참고(dataType별로 유효한 값이 다름). |
| type                | string  |            |         | 파싱만 되고 현재 로직에서는 사용되지 않는 보조 타입 문자열. |
| animaion            | boolean |            | false   | (원문 그대로 `animation`이 아닌 `animaion`) 애니메이션 사용 여부. |
| minDistance         | number  |            | 0       | 인스턴스 가시화 최소 거리(m). |
| maxDistance         | number  |            | 9999999 | 인스턴스 가시화 최대 거리(m). |
| callbackMinDistance | number  |            | 0       | `loadDataCallback` 호출 기준 거리(m). |
| legend              | array   |            |         | [JSDataVisualizer.LegendItem](jsdatavisualizer.md#jsdatavisualizer.legenditem) 배열. |
| autoFocus           | boolean |            | false   | true면 생성 직후 [focus()](jsdatavisualizer.md#focus-key-void)를 자동 호출. |
| child               | array   |            |         | 자식 객체 목록(재귀적으로 같은 구조). `add()`에서는 `dataType === "position"`인 항목만 자식으로 생성됩니다. |
| data                | array   |            |         | `dataType === "position"` \| `"line"`인 경우 필요. 항목: `{ id, position:[lon,lat,alt], value(number\|number[]), path?:[lon,lat,alt], rotate?:[x,y,z], parts?(line 전용) }`. |
| points, value       | array   |            |         | `dataType === "polygon"`인 경우 필요. `points`는 `[[[lon,lat], ...], ...]`(폴리곤별 링 좌표), `value`는 폴리곤별 값 배열. |
| range / cellCount, longitude / latitude, startPosition / resolution, rect | object/array |  |  | `dataType === "grid"`인 경우, 4가지 방식 중 하나로 격자 범위를 지정(자세한 옵션 조합은 구현부 참고, 문서에는 개요만 기재). |
| symbol / icon       | object  |            |         | `data`(base64 문자열 또는 byte 배열), `texture`(문자열, symbol 전용) 등을 포함하는 3D 심볼/이미지 리소스 정의. |
| size                | array   |            |         | `dataType === "polygon"`인 경우 `[x, y, z]` 형태의 기본 크기. |
| altitude            | number  |            | 0       | `dataType === "polygon"`인 경우 고도값. |

#### JSDataVisualizer.LegendItem

> [setLegend()](jsdatavisualizer.md#setlegend-key-legend-boolean) 및 `add()`의 `legend` 배열 항목 구조입니다.

| Name  | Type   | Attributes | Default | Description                          |
| ----- | ------ | ---------- | ------- | -------------------------------------- |
| value | number | 필수       |         | 색상이 적용되는 기준 값.               |
| color | array  | 필수       |         | `[R, G, B, A]` 형태의 숫자 배열(0~255). |

#### JSDataVisualizer.ShapeOption

> [setShape()](jsdatavisualizer.md#setshape-key-option-boolean)에 객체(object)를 전달할 때의 구조입니다.

| Name              | Type   | Attributes | Default | Description |
| ------------------ | ------ | ---------- | ------- | ----------- |
| shape              | string | 필수       |         | `"symbol"` 또는 `"icon"`. |
| symbol             | string |            |         | `shape === "symbol"`인 경우 사용. base64로 인코딩된 3ds 메쉬 데이터 문자열. |
| symbol.texture     | string |            |         | 심볼에 적용할 텍스처 url(선택). |
| image              | string |            |         | `shape === "icon"`인 경우 사용. base64로 인코딩된 이미지 데이터 문자열. |

#### JSDataVisualizer.LineSymbolOption

> [setLineSymbol()](jsdatavisualizer.md#setlinesymbol-key-options-boolean)에 전달하는 옵션 객체 구조입니다.

| Name          | Type            | Attributes | Default | Description |
| -------------- | --------------- | ---------- | ------- | ----------- |
| symbol         | object          |            |         | 3D 메쉬 심볼을 부착할 때 사용. `icon`과 동시에 지정하면 `symbol`이 우선 처리됩니다. |
| symbol.data    | string \| array |            |         | base64 문자열 또는 바이트(0~255) 배열 형태의 3ds 메쉬 데이터. |
| symbol.texture | string          |            |         | 심볼에 적용할 텍스처 url(선택). |
| icon           | object          |            |         | 이미지 아이콘을 부착할 때 사용(`symbol`이 없을 때만 처리됨). |
| icon.data      | string \| array |            |         | base64 문자열 또는 바이트(0~255) 배열 형태의 이미지 데이터. |
