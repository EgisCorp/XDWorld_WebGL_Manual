---
description: 도로 기하구조(선형/횡단/종단) 분석 기능을 위한 독립형(Standalone) API 입니다.
---

# JSSRoadAnalysis

> Module.JSSRoadAnalysis() API를 생성합니다.
>
> [JSRoadAnalysis](../analysis/jsroadanalysis.md)와 API 구성 및 동작이 거의 동일하나, 지도(맵/월드) 객체에 종속되지 않고 프로세스 전역에서 공유되는 단일 분석 인스턴스(전역 싱글턴)를 사용하는 독립형(Standalone) 버전입니다. 인스턴스를 여러 개 생성해도 내부적으로 동일한 분석 데이터를 공유합니다.

```javascript
var roadAnalysis = new Module.JSSRoadAnalysis();
```

## Function

### setJsonData(json) → boolean

> 도로 기하구조 분석에 필요한 데이터를 JSON 문자열로 입력받아 분석을 수행합니다.
>
> JSON에는 도로 경계선(roadSides), 차선(lanes), 도로면(roadPolys), 노드(nodes), 링크(links), 분석 기준점(param) 정보가 포함되어야 합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                    |
| :--- | ------ | --------------------------------------------------- |
| json | string | 도로 기하구조 분석 입력 JSON 문자열(`type: "Geometry Analisys Input"`). |

-   Return
    -   true: 분석 성공.
    -   false: 분석 실패.
    -   실패 조건
        -   입력 문자열 길이가 10 미만인 경우.
        -   JSON 파싱에 실패한 경우.
        -   `type` 값이 "Geometry Analisys Input"이 아닌 경우.
        -   내부 분석(doAnlysis)이 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var roadAnalysis = new Module.JSSRoadAnalysis();
var result = roadAnalysis.setJsonData(JSON.stringify({
    type: "Geometry Analisys Input",
    feature: {
        roadSides: [], lanes: [], roadPolys: [], nodes: [], links: [],
        param: { x: 127.0, y: 37.5, range: 100.0 }
    }
}));
```

{% endtab %}
{% endtabs %}

### setSegment(distance)

> 분석 시 사용할 구간 분할 간격(세그먼트 거리)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description   |
| :------- | ------ | ------------------ |
| distance | number | 구간 분할 거리.    |

{% endtab %}
{% tab title="Template" %}

```javascript
roadAnalysis.setSegment(5.0);
```

{% endtab %}
{% endtabs %}

### chkAngle(straightAngle, curveAngleDiff, safeCurveAngle1, safeCurveAngle2)

> 직선/곡선 구간 판정과 안전 각도 기준값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name            | Type   | Description                    |
| :-------------- | ------ | ---------------------------------- |
| straightAngle   | number | 직선 구간 판정 기준 각도.         |
| curveAngleDiff  | number | 곡선 구간 판정 각도 차이 기준값.  |
| safeCurveAngle1 | number | 안전 곡선 각도 기준값 1.          |
| safeCurveAngle2 | number | 안전 곡선 각도 기준값 2.          |

{% endtab %}
{% tab title="Template" %}

```javascript
roadAnalysis.chkAngle(2.0, 1.0, 5.0, 8.0);
```

{% endtab %}
{% endtabs %}

### getProfile() → [JSSRoadAnlProfile](jssroadanlprofile.md)

> [setJsonData()](jssroadanalysis.md#setjsondatajson-boolean)로 분석된 결과 중, 종단면(Profile) 분석 결과 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSSRoadAnlProfile](jssroadanlprofile.md): 종단면 분석 결과 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
var profile = roadAnalysis.getProfile();
var json = profile.getProfileJSON();
```

{% endtab %}
{% endtabs %}

### getCrossSection() → [JSSRoadAnlCrossContainer](jssroadanlcross.md#jssroadanlcrosscontainer)

> [setJsonData()](jssroadanalysis.md#setjsondatajson-boolean)로 분석된 결과 중, 횡단면(Cross Section) 분석 결과 목록 컨테이너를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSSRoadAnlCrossContainer](jssroadanlcross.md#jssroadanlcrosscontainer): 횡단면 분석 결과 컨테이너.

{% endtab %}
{% tab title="Template" %}

```javascript
var container = roadAnalysis.getCrossSection();
var count = container.getCount();
```

{% endtab %}
{% endtabs %}

### getFlatLinearJSON() → string

> 평면 선형(곡률, 안전각도 등) 분석 결과를 JSON 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 분석 결과 JSON 문자열(`type: "Flat Linear Geomtery Analisys Output"`).
    -   "": 분석된 곡률 구간이 2개 미만인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var json = roadAnalysis.getFlatLinearJSON();
console.log(JSON.parse(json));
```

{% endtab %}
{% endtabs %}

### clear()

> 전역으로 공유되는 분석 데이터를 초기화합니다.

{% tabs %}
{% tab title="Information" %}

-   Note
    -   전역 싱글턴 데이터이므로, 다른 JSSRoadAnalysis 인스턴스의 데이터도 함께 초기화됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
roadAnalysis.clear();
```

{% endtab %}
{% endtabs %}

### setLineVisible(visible)

> 분석 과정에서 생성되는 보조 라인(추가 정보 표시용)의 가시화 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                              |
| :------ | ------- | -------------------------------------------- |
| visible | boolean | <p>true: 가시화.<br>false: 비가시화.</p>     |

{% endtab %}
{% tab title="Template" %}

```javascript
roadAnalysis.setLineVisible(true);
```

{% endtab %}
{% endtabs %}
