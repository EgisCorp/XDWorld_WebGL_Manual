---
description: 도로 기하구조 분석의 횡단면(Cross Section) 결과를 조회하기 위한 API 입니다.
---

# JSRoadAnlCross / JSRoadAnlCrossContainer

> 이 문서는 하나의 cpp 파일(JSRoadAnlCross.cpp)에 정의된 두 개의 JS 클래스, `JSRoadAnlCross`(횡단면 결과 개별 항목)와 `JSRoadAnlCrossContainer`(횡단면 결과 목록 컨테이너)를 함께 다룹니다.
>
> [JSRoadAnalysis.getCrossSection()](jsroadanalysis.md#getcrosssection-jsroadanlcrosscontainer-jsroadanlcrossmdjsroadanlcrosscontainer)의 반환 객체(JSRoadAnlCrossContainer)를 통해 접근하며, 직접 생성해서 사용하지는 않습니다.

```javascript
var roadAnalysis = new Module.JSRoadAnalysis();
// ...(setJsonData로 분석 수행)...
var container = roadAnalysis.getCrossSection();
var count = container.getCount();
var cross = container.indexAt(0);
```

## JSRoadAnlCrossContainer

### getCount() → number

> 분석된 횡단면 결과의 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number(0 이상): 횡단면 결과 개수.
    -   0: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = container.getCount();
```

{% endtab %}
{% endtabs %}

### indexAt(index) → [JSRoadAnlCross](jsroadanlcross.md#jsroadanlcross)

> 지정한 인덱스에 해당하는 횡단면 분석 결과 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | :----- | :----------- |
| index | number | 조회할 인덱스([getCount()](jsroadanlcross.md#getcount-number) 범위 내). |

-   Return
    -   [JSRoadAnlCross](jsroadanlcross.md#jsroadanlcross): 반환 성공.
    -   null: index가 0보다 작거나 [getCount()](jsroadanlcross.md#getcount-number) 값 이상인 경우.
-   Note
    -   호출할 때마다 내부적으로 최신 분석 결과를 다시 동기화합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var cross = container.indexAt(0);
```

{% endtab %}
{% endtabs %}

## JSRoadAnlCross

### getID() → number

> 횡단면 결과의 구간 번호(인덱스)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 구간 번호. 초기화되지 않은 경우 -1.

{% endtab %}
{% tab title="Template" %}

```javascript
var id = cross.getID();
```

{% endtab %}
{% endtabs %}

### getDist() → number

> 시작 지점으로부터 해당 횡단면까지의 진행 거리를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 진행 거리(meters 단위).
    -   -1: 내부 데이터가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var dist = cross.getDist();
```

{% endtab %}
{% endtabs %}

### getJSONData() → string

> 횡단면 상세 정보(좌우 경계 좌표, 차선 폭, 차선 경사, 최대/최소 고도, 폭 등)를 JSON 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 횡단면 정보 JSON 문자열(`type: "Cross-section Geometry Analisys Output"`).
    -   "": 내부 데이터가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var json = cross.getJSONData();
console.log(JSON.parse(json));
```

{% endtab %}
{% endtabs %}

### getDistPoint(distance) → [JSVector3D](../core/jsvector3d.md)

> 횡단면 진행 방향을 따라 지정한 거리만큼 이동한 지점의 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description       |
| :------- | :----- | ---------------------- |
| distance | number | 진행 거리(meters 단위). |

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 반환 성공.
    -   [JSVector3D](../core/jsvector3d.md)(0, 0, 0): 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var point = cross.getDistPoint(10.0);
```

{% endtab %}
{% endtabs %}
