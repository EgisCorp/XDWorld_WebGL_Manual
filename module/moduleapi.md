---
description: 핵심 제어를 담당하는 기능 목록.
---

# Module_API

> Module API 생성.

```javascript

```

### createBarGraph(key) -> [JSBarGraph](../object/jsbargraph.md)

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

### createBarGraph3D(key) -> [JSBarGraph3D](../object/jsbargraph3d.md)

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
