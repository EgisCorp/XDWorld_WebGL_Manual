---
description: 지도 내 수인한도 분석 기능 설정 API.
---

# JSAnalysisGridShadow

> Module getAnalysisGridShadow API로 생성할 수 있습니다.

```javascript
var gridShadow = Module.getAnalysisGridShadow();
```

## Function

### clear() → boolean

> 가시화 된 수인한도 분석 결과를 초기화 합니다.
>
> 가시화 된 격자, 선택 객체를 해제합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true : 수인한도 분석 초기화 성공.
    -   false : 수인한도 분석 초기화 실패.
        -   격자가 없을 경우.
        -   레이어가 없을 경우.
-   Sample - function setEarthquakeMesh 참조. - [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
    {% endtab %}
    {% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.clear();
```

{% endtab %}
{% endtabs %}

### create(layerName, gap, isClip) → boolean

> 수인한도 분석 격자를 생성합니다.
>
> 설정된 gap(단위 : m)크기로 가로, 세로 격자를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| layerName | string | 가시화 할 격자 객체를 담는 레이어 명칭 |
| gap | number | 격자의 크기(가로 x 세로) |
| isClip | boolean | 지정된 영역에 격자 크기를 균등 분할 생성 여부 설정 |
{% endtab %}

-   Return

    -   true : 수인한도 분석 격자 생성 성공.
    -   false : 수인한도 분석 격자 생성 실패.
        -   입력된 점이 3개 이하일 경우.

-   Sample - function setEarthquakeMesh 참조. - [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
    {% endtab %}
    {% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.create("gridlayer", 10, true);
```

{% endtab %}
{% endtabs %}

### getResult() → string

> 수인한도 분석 결과 반환.
>
> 수인한도 분석 결과(각 격자별 일조량) 반환.

{% tabs %}
{% tab title="Information" %}
{% endtab %}

-   Return
    -   각 격자별 일조량, 연속 일조량 json 반환.
-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
var result = gridShadow.getResult();
const json = JSON.parse(result);
```

{% endtab %}
{% endtabs %}

### reset() → boolean

> 수인한도 분석 격자 옵션 초기화.
>
> 배척격자, 격자색상 등 옵션 초기화.

{% tabs %}
{% tab title="Information" %}
{% endtab %}

-   Return

    -   true : 수인한도 분석 격자 옵션 초기화 성공.
    -   false : 수인한도 분석 격자 옵션 초기화 실패.
        -   격자가 없을 경우.
        -   레이어가 없을 경우.

-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.reset();
```

{% endtab %}
{% endtabs %}

### setAnalysis(id, isanalysis) → boolean

> 배척격자 설정.
>
> 해당 id의 격자를 수인한도 분석에서 제외.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| id | string | 격자 id |
| isanalysis | boolean | 분석 여부 |
{% endtab %}

-   Return
    -   true : 배척격자 설정 성공.
    -   false : 배척격자 설정 실패.
        -   격자가 없을 경우.
        -   레이어가 없을 경우.
-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.setAnalysis("id", false);
```

{% endtab %}
{% endtabs %}

### setColor(id, color) → boolean

> 수인한도 분석 격자 색상 설정.
>
> 해당 id의 격자 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| id | string | 격자 id |
| color | [JSColor](../core/jscolor.md) | 격자 색상 설정 |
{% endtab %}

-   Return

    -   true : 수인한도 분석 격자 색상 설정 성공.
    -   false : 수인한도 분석 격자 색상 설정 실패.
        -   레이어가 없을 경우.
        -   격자가 없을 경우.

-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.setColor("id", new Module.JSColor(150, 0, 255, 0));
```

{% endtab %}
{% endtabs %}

### startAnalysis(startTime, endTime, interval) → boolean

> 수인한도 분석 시작.
>
> 시작시간, 종료시간, 시간간격을 바탕으로 수인한도 분석 시작.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| startTime | [JSDateTime](../core/jsdatetime.md) | 분석 시작 시간 |
| endTime | [JSDateTime](../core/jsdatetime.md) | 분석 종료 시간 |
| interval | number | 분석 시간 간격(단위 : 분) |
{% endtab %}

-   Return

    -   true : 수인한도 분석 성공.
    -   false : 수인한도 분석 실패.
        -   레이어가 없을 경우.
    -   격자가 없을 경우.
        -   선택된 객체가 없을 경우.

-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.startAnalysis(
    new Module.JSDateTime(2023, 4, 17, 9, 30, 0),
    new Module.JSDateTime(2023, 4, 17, 15, 30, 0),
    10
);
```

{% endtab %}
{% endtabs %}