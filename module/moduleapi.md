---
description: 핵심 제어를 담당하는 기능 목록.
---

# Module_API

> Module API 생성.

```javascript

```

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
