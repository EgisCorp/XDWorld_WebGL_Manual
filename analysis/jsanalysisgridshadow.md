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
-   초기화 실패 조건
    -   격자가 없을 경우.
    -   레이어가 없을 경우.
-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
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

-   Return

    -   true : 수인한도 분석 격자 생성 성공.
    -   false : 수인한도 분석 격자 생성 실패.

-   격자 생성 실패 조건

    -   입력된 점이 3개 이하일 경우.

-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
        {% endtab %}

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.create("gridlayer", 10, true);
```

{% endtab %}
{% endtabs %}

### getResult() → string

> 수인한도 분석 결과를 반환합니다.
>
> 격자 별 일조량 분석 결과를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   각 격자별 일조량, 연속 일조량 json 반환.
-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
        {% endtab %}

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
var result = gridShadow.getResult();
const json = JSON.parse(result);
```

{% endtab %}
{% endtabs %}

### reset() → boolean

> 수인한도 분석 격자 옵션을 초기화 합니다.
>
> 배척격자, 격자색상과 같은 옵션을 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return

    -   true : 수인한도 분석 격자 옵션 초기화 성공.
    -   false : 수인한도 분석 격자 옵션 초기화 실패.

-   옵션 초기화 실패 조건 - 격자가 없을 경우. - 레이어가 없을 경우.

-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
        {% endtab %}

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.reset();
```

{% endtab %}
{% endtabs %}

### setAnalysis(id, isAnalysis) → boolean

> 배척격자를 설정합니다..
>
> 입력된 id의 격자를 수인한도 분석에서 제외합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| id | string | 격자 id |
| isAnalysis | boolean | 분석 여부 |

-   Return

    -   true : 배척격자 설정 성공.
    -   false : 배척격자 설정 실패.

-   배척격자 설정 실패 조건
    -   격자가 없을 경우.
    -   레이어가 없을 경우.
-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
        {% endtab %}

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.setAnalysis("id", false);
```

{% endtab %}
{% endtabs %}

### setColor(id, color) → boolean

> 수인한도 분석 격자 색상을 변경합니다.
>
> 해당 id 객체 격자 색상을 변경합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| id | string | 격자 id |
| color | [JSColor](../core/jscolor.md) | 격자 색상 설정 |

-   Return

    -   true : 수인한도 분석 격자 색상 설정 성공.
    -   false : 수인한도 분석 격자 색상 설정 실패.

-   수인한도 분석 격자 색상 설정 실패 조건

    -   레이어가 없을 경우.
    -   격자가 없을 경우.

-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
        {% endtab %}

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.setColor("id", new Module.JSColor(150, 0, 255, 0));
```

{% endtab %}
{% endtabs %}

### startAnalysis(startTime, endTime, interval) → boolean

> 수인한도 분석을 실행합니다.
>
> 시작시간, 종료시간, 시간간격을 바탕으로 수인한도 분석을 실행합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| startTime | [JSDateTime](../core/jsdatetime.md) | 분석 시작 시간 |
| endTime | [JSDateTime](../core/jsdatetime.md) | 분석 종료 시간 |
| interval | number | 분석 시간 간격(단위 : 분) |

-   Return

    -   true : 수인한도 분석 성공.
    -   false : 수인한도 분석 실패.

-   수인한도 분석 실행 실패 조건

    -   레이어가 없을 경우.
    -   격자가 없을 경우.
    -   선택된 객체가 없을 경우.

-   Sample
    -   function setEarthquakeMesh 참조.
    -   [샌드박스\_수인한도분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_grid_shadow)
        {% endtab %}

{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
gridShadow.startAnalysis(new Module.JSDateTime(2023, 4, 17, 9, 30, 0), new Module.JSDateTime(2023, 4, 17, 15, 30, 0), 10);
```

{% endtab %}
{% endtabs %}

### createWindow(layerName) → boolean

> 창문분석을 위해 창문을 생성합니다.
>
> 마우스(Module.MML_ANALYS_WINDOWSHADOW) 클릭으로 입력된 2점으로 창문을 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| layerName | string | 레이어명 |

-   Return

    -   true : 창문 생성 성공.
    -   false : 창문 생성 실패.

-   창문 생성 실패 조건

    -   입력된 점이 2개가 아닐 경우.

-   Sample
    -   function inputWindow 참조.
    -   [샌드박스\_창문분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_window_shadow)
        {% endtab %}

{% endtab %}
{% endtabs %}

### copyPasteWindow() → boolean

> 창문분석을 위해 창문을 복사 붙여넣기 합니다.
>
> 마우스(Module.MML_ANALYS_WINDOWSHADOW) 클릭으로 입력된 지점을 좌상단으로 최근에 생성한 창문을 붙여넣습니다.

{% tabs %}
{% tab title="Information" %}

-   Return

    -   true : 창문 복사 성공.
    -   false : 창문 복사 실패.

-   창문 복사 실패 조건

    -   레이어가 없을 경우.
    -   생성된 창문이 없을 경우.
    -   입력된 지점이 없을 경우.

-   Sample
    -   function copyPasteWindow 참조.
    -   [샌드박스\_창문분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_window_shadow)
        {% endtab %}

{% endtab %}
{% endtabs %}

### copyPasteFloor() → boolean

> 창문분석을 위해 층을 복사 붙여넣기 합니다.
>
> 마우스(Module.MML_ANALYS_WINDOWSHADOW) 클릭으로 입력된 지점을 좌상단으로 최근에 생성한 창문을 모두 붙여넣습니다.

{% tabs %}
{% tab title="Information" %}

-   Return

    -   true : 층 복사 성공.
    -   false : 층 복사 실패.

-   층 복사 실패 조건

    -   레이어가 없을 경우.
    -   생성된 창문이 없을 경우.
    -   입력된 지점이 없을 경우.

-   Sample
    -   function copyPasteFloor 참조.
    -   [샌드박스\_창문분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_window_shadow)
        {% endtab %}

{% endtab %}
{% endtabs %}
