---
description: 지도 내 형태에 따라 다양한 객체가 존재하고 JSObject는 이런 다양한 객체를 포괄적으로 관리하기 위한 API 입니다.
---

# JSObject

> 객체 프로토 타입 API.

## Function

### getId() → string

> 객체의 고유 명칭을 반환 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strKey = object.getId();
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getDescription(), setDescription(desc) → string

> 객체에 대한 설명을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| desc | string | 설명 문자열. |

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strDesc = object.getDescription();
// ... or ...
object.setDescription("First Object.");
```

{% endtab %}
{% endtabs %}

### getName(), setName(name) → string

> 객체 이름을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 이름.  |

-   Return
    -   string: 객체 이름을 성공적을 반환
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setName("MyObject");
```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean

> 객체의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                        |
| ------- | ------- | -------------------------------------------------- |
| visible | boolean | <p>true: 객체 가시화.<br>false: 객체 비가시화.</p> |

-   Return
    -   true: 객체 가시화 상태.
    -   false: 객체 비가시화 상태.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setVisible(true);
```

{% endtab %}
{% endtabs %}

### setPickable(value) → boolean

> 객체의 피킹(Picking) 가능 여부를 설정합니다.  
> 피킹 기능이 활성화된 경우, 마우스 이벤트 또는 선택 연산 시 해당 객체를 대상으로 인식할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                            |
| ----- | ------- | -------------------------------------- |
| value | boolean | `true`: 피킹 가능, `false`: 피킹 불가 |

- Return  
  - `true` : 설정 성공  
  - `false` : 설정 실패 (객체가 null인 경우 등)

{% endtab %}
{% tab title="Template" %}

```javascript
const obj = Module.createPolygon("PICKABLE_OBJECT");
obj.setPickable(true); // 마우스 피킹 가능 설정
```

{% endtab %}
{% endtabs %}
