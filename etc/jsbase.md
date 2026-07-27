---
description: 엔진 내 객체(JSObject 계열)의 최상위 공통 기능을 제공하는 API 입니다.
---

# JSBase

> Module.JSBase() API를 생성합니다.
>
> JSObject 계열 클래스(JSPoint, JSPolygon 등)들이 공통으로 상속하는 최상위 클래스이며, 대부분의 경우 직접 생성하기보다는 각 객체 생성 API(`Module.createPoint()` 등)를 통해 간접적으로 사용됩니다.

```javascript
var object = new Module.JSBase();
```

## Function

### getType() → string

> 객체의 클래스 타입 문자열을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 객체 클래스 타입 문자열(예: "JSPoint", "JSPolygon" 등).

{% endtab %}
{% tab title="Template" %}

```javascript
var point = Module.createPoint("ID");
var strType = point.getType();
console.log(strType); // "JSPoint"
```

{% endtab %}
{% endtabs %}
