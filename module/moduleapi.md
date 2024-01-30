---
description: 지도 생성, 제어를 담당하는 기능 목록.
---

# Module_API

> Module.initialize를 통해 기본 지도를 생성할 수 있습니다.
>
> Module을 통해 다른 Class를 생성 후 사용이 가능합니다.
>
> web worker 파라미터는 2024년 2월 1일 이후 베타 버전 엔진에서 사용 가능합니다.

```javascript
Module.initialize({
    container: document.querySelector("컨테이너 ID"),
    terrain: {
        dem: {
            url: "지형 DEM 데이터 요청 URL,
            name: "지형 DEM 레이어 명칭",
            servername: "요청 Server 명칭"
        },
        image: {
            url: "지형 영상 이미지 데이터 요청 URL",
            name: "지형 용상 이미지 레이어 명칭",
            servername: "요청 Server 명칭"
        },
        worker : {
			use : "web worker 사용유무",
			path : "web worker 파일 요청 URL",
			count : "web worker 사용 개수 설정"
		},
    },
    defaultKey: "발급키",
});
```

## Function

### initialize(object) -> object

> 지도를 생성합니다.
>
> worker 항목 옵션을 통해 web worker 기능을 활성화 합니다.
>
> web worker는 엔진에 종속된 기능으로 엔진 부화를 줄여주는 기능입니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ------ | -------- |
| container | HTML Element | 지도를 포함한 Container 영역. |
| terrain | [Module.CreateOptions](moduleapi.md#module.createoptions) | Map 생성 정보. |
| worker | [Module.CreateWorkerOptions](moduleapi.md#module.createworkeroptions) | web worker 생성 정보. |
| defaultKey | string | 엔진 API 발급 Key |

-   Return
    -   .result : API 성공 유무 상태 (1 : 성공, 0 : 실패)
    -   .name : 동작 API 명칭
    -   .return : API 반환 정보 (object : 정상적인 반환값, 문자열 : 실패 에러 코드)

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createBarGraph("newBarGraph");
```

{% endtab %}
{% endtabs %}

### createBarGraph(key) → [JSBarGraph](../object/jsbargraph.md)

> 2차원 막대 그래프 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSBarGraph](../object/jsbargraph.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createBarGraph("newBarGraph");
```

{% endtab %}
{% endtabs %}

### createBarGraph3D(key) → [JSBarGraph3D](../object/jsbargraph3d.md)

> 3차원 막대 그래프 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSBarGraph3D](../object/jsbargraph3d.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createBarGraph3D("newBarGraph3D");
```

{% endtab %}
{% endtabs %}

### createBillboard(key) → [JSBillboard](../object/jsbillboard.md)

> 빌보드 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSBillboard](../object/jsbillboard.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createBillboard("newBillboard");
```

{% endtab %}
{% endtabs %}

### createGhostSymbol(key) → [JSGhostSymbol](../object/jsghostsymbol.md)

> 고스트 심볼 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSGhostSymbol](../object/jsghostsymbol.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let ghostSymbol = Module.createGhostSymbol("newGhostSymbol");
```

{% endtab %}
{% endtabs %}

### createLineString(key) → [JSLineString](../object/jslinestring.md)

> 라인 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSLineString](../object/jslinestring.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createLineString("newPolyLine");
```

{% endtab %}
{% endtabs %}

### createLineString(key) → [JSLineString](../object/jslinestring.md)

> 라인 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSLineString](../object/jslinestring.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createLineString("newPolyLine");
```

{% endtab %}
{% endtabs %}

### createMultiPoint(key) → [JSMultiPoint](../object/jsmultipoint.md)

> 멀티포인트 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSMultiPoint](../object/jsmultipoint.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createMultiPoint("newMultiPoint");
```

{% endtab %}
{% endtabs %}

### createPipe(key) → [JSPipe](../object/jspipe.md)

> 파이프 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSPipe](../object/jspipe.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createPipe("newPipe");
```

{% endtab %}
{% endtabs %}

### createPoint(key) → [JSPoint](../object/jspoint.md)

> POI형 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSPoint](../object/jspoint.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createPoint("newPoint");
```

{% endtab %}
{% endtabs %}

### createPointGraph(key) → [JSPointGraph](../object/jspointgraph.md)

> 3차원 포인트 그래프의 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSPointGraph](../object/jspointgraph.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createPointGraph("newGraph");
```

{% endtab %}
{% endtabs %}

### createSurfaceGraph(key) → [JSSurfaceGraph](../object/jssurfacegraph.md)

> 3차원 그물형 격자 그래프의 오브젝트 생성 및 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| key | string | 생성하는 오브젝트 키. |

-   Return
    -   [JSSurfaceGraph](../object/jssurfacegraph.md): 오브젝트 생성 성공.
    -   null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createSurfaceGraph("newBarGraph3D");
```

{% endtab %}
{% endtabs %}

### getAnalysis() → JSAnalysis

> 분석 API 실행 클래스 JSAnalysis의 객체를 반환.

{% tabs %}
{% tab title="Information" %}

-   Return - JSAnalysis: 생성한 JSAnalysis 타입 객체. - null: 오브젝트 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var analysis = Module.getAnalysis();
```

{% endtab %}
{% endtabs %}

### getGhostSymbolMap() → JSGhostSymbolMap

> 고스트 심볼을 관리하는 API 객체 생성 및 반환.

{% tabs %}
{% tab title="Infomation" %}

-   Return
-   JSGhostSymbolMap: 객체 생성 성공.
-   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let map = Module.getGhostSymbolMap();
```

{% endtab %}
{% endtabs %}

### ~~getNavigation() → JSNavigationControl~~

> 지도 네비게이션(나침반) 설정 API 객체 생성 및 반환.

{% tabs %}
{% tab title="Infomation" %}

-   Return
-   JSNavigationControl: 객체 생성 성공.
-   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let navigation = Module.getNavigation();
```

{% endtab %}
{% endtabs %}

### getSlope() → JSSlope

> 경사도, 경사향 분석 API 객체 생성 및 반환.

{% tabs %}
{% tab title="Infomation" %}

-   Return
-   JSSlope: 객체 생성 성공.
-   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let slope = Module.getSlope();
```

{% endtab %}
{% endtabs %}

### getSymbol() → JSSymbol

> 아이콘(JSIcon) 관리 API 객체 생성 및 반환.

{% tabs %}
{% tab title="Infomation" %}

-   Return
-   JSSymbol: 객체 생성 성공.
-   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let symbol = Module.getSymbol();
```

{% endtab %}
{% endtabs %}

### Resize(width, height)

> 화면의 크기를 변경하는 함수.
>
> 별다른 설정이 없을 경우, canvas 크기에 뷰포트를 맞추어 변경.
>
> div로 설정 시 div 크기에 맞추어 뷰포트 변경.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type   | Description |
| ------ | ------ | ----------- |
| width  | number | 변경할 폭.  |
| height | number | 너비.       |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.Resize(400, 300);
```

{% endtab %}
{% endtabs %}

### SetProxy(proxy)

> 우회 프록시 URL 설정.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| proxy | string | 프록시 URL. |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetSimpleMode(type)

> 렌더링 심플 모드 설정.
>
> 심플 모드 설정시 텍스처가 적용되지 않은 오브젝트를 렌더링.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                         |
| ---- | ------- | ------------------------------------------------------------------- |
| type | boolean | true인 경우, 심플 모드 활성화.<br>false인 경우, 심플 모드 비활성화. |

{% endtab %}

{% tab title="Template" %}

```javascript
Module.SetSimpleMode(0);
Module.SetSimpleMode(1);
```

{% endtab %}
{% endtabs %}

### XDClearInputPoint() → boolean

> 입력 점 리스트를 초기화.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   true: 초기화 성공.
    -   false : 엔진이 초기화 되지 않은 경우.

{% endtab %}

{% tab title="Template" %}

```javascript
Module.XDClearInputPoint();
```

{% endtab %}
{% endtabs %}

### XDIsMouseOverDiv(block)

> 지도 클릭 이벤트 Block 여부를 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type |Description |
| ---- | ------- | ---------------------------------------------- |
| block | boolean | true인 경우, Block 활성화.<br>false인 경우, Block 비활성화. |
{% endtab %}

{% tab title="Template" %}

```html
<div id="testElementDiv" onmouseover="Module.XDIsMouseOverDiv(true);" onmouseout="Module.XDIsMouseOverDiv(false);"></div>
```

{% endtab %}
{% endtabs %}

### XDRenderData()

> 화면을 갱신.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDRenderData();
```

{% endtab %}
{% endtabs %}

### XDSetMouseState(mode)

> 마우스의 입력 상태를 변경.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type |Description |
| ---- | ------- | ----------------------------------- |
| mode | number | 설정하고자 하는 마우스 모드 값. |
{% endtab %}

{% tab title="Template" %}

```html
<div id="testElementDiv" onmouseover="Module.XDIsMouseOverDiv(true);" onmouseout="Module.XDIsMouseOverDiv(false);"></div>
```

{% endtab %}
{% endtabs %}

## Type Definitions

### Module.CreateTerrainOptions

| Name  | Type                                                                                | Description  |
| ----- | ----------------------------------------------------------------------------------- | ------------ |
| dem   | [Module.CreateTerrainOptions.DEM](moduleapi.md#module.createterrainoptions.dem)     | 지형 데이터. |
| image | [Module.CreateTerrainOptions.Image](moduleapi.md#module.createterrainoptions.image) | 영상 데이터. |

### Module.CreateWorkerOptions

| Name  | Type    | Description           |
| ----- | ------- | --------------------- |
| use   | boolean | web worker 사용유무.  |
| path  | string  | web worker 요청 url.  |
| count | number  | web worker 사용 개수. |

### Module.CreateTerrainOptions.DEM

| Name       | Type    | Description                                                                                                         |
| ---------- | ------- | ------------------------------------------------------------------------------------------------------------------- |
| url        | string  | 지형 DEM 데이터 요청 url.                                                                                           |
| name       | string  | 지형 DEM 레이어 명칭.                                                                                               |
| servername | string  | 요청 Server 명칭.                                                                                                   |
| encoding   | boolean | <p>DEM 암호화 데이터 인식 여부.<br>true인 경우 암호화 되어 있음.<br><br>false인 경우 암호화 되어 있지 않음.<br></p> |

### Module.CreateTerrainOptions.Image

| Name       | Type   | Description                       |
| ---------- | ------ | --------------------------------- |
| url        | string | 지형 영상 이미지 데이터 요청 url. |
| name       | string | 지형 영상 이미지 레이어 이름.     |
| servername | string | 요청 Server 명칭.                 |
|            |
