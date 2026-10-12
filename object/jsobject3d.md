---
description: 지도 내 모든 3D 객체(JSPoint, JSPolygon 등)가 공통으로 상속하는 최상위 기능을 제공하는 API 입니다.
---

# JSObject3D

> 각 세부 객체 생성 API(`Module.createPoint()`, `Module.createPolygon()` 등)로 생성된 객체는 모두 이 클래스의 기능을 상속하여 사용할 수 있습니다.

```javascript
var object = new Module.JSObject3D();
```

## Properties

| Name         | Type                                | Description                                       |
| :----------- | -------------------------------------- | ------------------------------------------------------ |
| position     | [JSVector3D](../core/jsvector3d.md) | 객체 중심 좌표(경도, 위도, 고도).                       |
| layer        | string                                  | 객체가 속한 부모 레이어 이름(읽기 전용).                |
| object_ahead | boolean                                 | 지형 또는 시설물이 앞에 존재할 경우 비가시화 옵션.      |

## Function

### getId() → string

> 객체의 고유 명칭을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 객체 고유 명칭.

{% endtab %}
{% tab title="Template" %}

```javascript
var id = object.getId();
```

{% endtab %}
{% endtabs %}

### getLayerName() → string

> 객체가 속한 부모 레이어의 이름을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 부모 레이어 이름.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerName = object.getLayerName();
```

{% endtab %}
{% endtabs %}

### getObjectType() → number

> 객체의 내부 타입 번호를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 객체 타입 번호.
    -   -1: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var type = object.getObjectType();
```

{% endtab %}
{% endtabs %}

### getCenter() → [JSVector3D](../core/jsvector3d.md)

> 객체를 포함하는 경계 상자의 중심 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 중심 좌표(경도, 위도, 고도).
    -   [JSVector3D](../core/jsvector3d.md)(0, 0, 0): 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var center = object.getCenter();
```

{% endtab %}
{% endtabs %}

### setMinDistance(distance) → boolean

> 객체 가시화 최소 거리를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description       |
| :------- | ------ | ---------------------- |
| distance | number | 최소 가시 거리(meters). |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setMinDistance(0.0);
```

{% endtab %}
{% endtabs %}

### setMaxDistance(distance) → boolean

> 객체 가시화 최대 거리를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description       |
| :------- | ------ | ---------------------- |
| distance | number | 최대 가시 거리(meters). |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setMaxDistance(5000.0);
```

{% endtab %}
{% endtabs %}

### setClipping(set) → boolean

> 객체에 클리핑 박스 적용 여부를 설정합니다. true로 설정하면 전역 클리핑 박스(월드에 하나뿐인 박스)의 **내부에 있는 부분만** 그려지고 박스 밖 부분은 잘려나갑니다. 잘려나간 부분을 반투명한 잔상으로 남길지는 [setClippingAlpha(alpha)](jsobject3d.md#setclippingalpha-alpha-boolean)로 정합니다.
>
> 클리핑 박스는 전역 객체이며, 박스의 생성, 위치, 크기, 표시 여부는 별도의 전역 클리핑 박스 API로 설정합니다. 박스를 생성하기 전에는 기본값(10m x 10m x 10m, 중심 좌표 미설정)의 박스가 기준이 되므로 의도한 영역이 잘리지 않을 수 있습니다. 클리핑 영역 판정은 박스의 표시 여부와 무관하게 적용됩니다.
>
> 다면체(polyhedron) 기반 3D 객체의 렌더링에서만 반영되며, 그 외 객체는 호출이 성공해도 화면에 영향이 없습니다. 기본값은 false입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                         |
| :--- | ------- | ------------------------------------------------------------------- |
| set  | boolean | <p>true: 클리핑 박스 적용.<br>false: 적용하지 않음(기본값).</p>      |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
// 클리핑 박스를 먼저 만든 뒤, 대상 객체에 클리핑을 적용
Module.createClippingBox(new Module.JSVector3D(127.0, 37.5, 50.0), 100.0, 100.0, 100.0);
object.setClipping(true);
```

{% endtab %}
{% endtabs %}

### setClippingAlpha(alpha) → boolean

> [setClipping(set)](jsobject3d.md#setclipping-set-boolean)로 클리핑이 켜진 객체에서, 클리핑 박스 밖으로 잘려나간 부분(잔상)의 투명도를 설정합니다. 기본값은 0입니다.
>
> -   `alpha <= 0`: 잘려나간 부분을 그리지 않습니다(완전히 잘라냄).
> -   `0 < alpha < 1`: 잘려나간 부분을 해당 알파의 반투명 잔상으로 그립니다. 잔상은 3D 장면 렌더링이 끝난 뒤 카메라 거리순으로 그려지며, 뒤쪽 지오메트리를 가리지 않습니다(깊이를 쓰지 않음). WBOIT가 꺼져 있으면 잔상 안에서 겹친 벽 중 최전면 한 겹만 보입니다.
> -   `alpha >= 1`: 클리핑 셰이더를 사용하지 않고 객체 전체를 원본처럼 불투명하게 그립니다(사실상 클리핑 해제와 같은 결과).
>
> 값은 별도로 보정(clamp)되지 않고 그대로 저장됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                  |
| :---- | ------ | ------------------------------------------------------------ |
| alpha | number | 잘려나간 부분의 알파(0.0 ~ 1.0 권장. 기본값 0.0).             |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setClipping(true);

// 박스 밖 부분을 30% 불투명한 잔상으로 표시
object.setClippingAlpha(0.3);
```

{% endtab %}
{% endtabs %}

### create(json) → boolean

> JSON 문자열을 파싱하여 객체를 구성합니다.
>
> `type` 값이 `"group"`인 경우(그룹 객체 생성)만 실제로 처리하며, 그 외의 타입 값에 대해서는 파싱만 하고 별도 처리 없이 `true`를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                             |
| :--- | ------ | -------------------------------------------- |
| json | string | 객체 구성 JSON 문자열(`type`, `key` 필드 포함). |

-   Return
    -   true: JSON 파싱 성공(실제 처리 여부와 무관).
    -   false: JSON 파싱에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.create(JSON.stringify({ type: "group", key: "Group_1" }));
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getDescription(), setDescription(desc) → string

> 객체에 대한 설명을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| :--- | ------ | ------------ |
| desc | string | 설명 문자열. |

{% endtab %}
{% tab title="Template" %}

```javascript
object.setDescription("설명 문자열");
var desc = object.getDescription();
```

{% endtab %}
{% endtabs %}

### getName(), setName(name) → string

> 객체 이름을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| :--- | ------ | ----------- |
| name | string | 객체 이름.  |

{% endtab %}
{% tab title="Template" %}

```javascript
object.setName("MyObject");
var name = object.getName();
```

{% endtab %}
{% endtabs %}

### getSelectable(), setSelectable(select) → boolean

> 객체의 선택 가능 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                    |
| :----- | ------- | -------------------------------------------------- |
| select | boolean | <p>true: 선택 가능.<br>false: 선택 불가.</p>       |

{% endtab %}
{% tab title="Template" %}

```javascript
object.setSelectable(true);
```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean

> 객체의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                        |
| :------ | ------- | -------------------------------------------------- |
| visible | boolean | <p>true: 객체 가시화.<br>false: 객체 비가시화.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
object.setVisible(true);
```

{% endtab %}
{% endtabs %}

### getPickable(), setPickable(value) → boolean

> 객체의 피킹(마우스 클릭 인식) 가능 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                                |
| :---- | ------- | -------------------------------------------- |
| value | boolean | <p>true: 피킹 가능.<br>false: 피킹 불가.</p>  |

{% endtab %}
{% tab title="Template" %}

```javascript
object.setPickable(true);
```

{% endtab %}
{% endtabs %}

### getProperty(name), setProperty(name, value) → val

> 객체에 사용자 정의 속성(문자열 또는 숫자 값)을 key-value 형태로 설정합니다.
>
> 이미 등록된 이름으로는 재설정할 수 없습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type            | Description                              |
| :---- | ------------------ | ---------------------------------------------- |
| name  | string              | 속성 이름(1자 이상).                           |
| value | number \| string    | 속성 값(숫자 또는 문자열만 지원).              |

-   Return(setProperty)
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   name이 빈 문자열인 경우.
        -   value가 숫자/문자열이 아닌 경우.
        -   동일한 name의 속성이 이미 존재하는 경우.
-   Return(getProperty)
    -   value: 등록된 속성 값.
    -   null: 월드가 초기화되지 않았거나, 해당 name의 속성이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setProperty("customId", 12345);
var value = object.getProperty("customId");
```

{% endtab %}
{% endtabs %}

### getUnderground(), setUnderground(underground) → boolean

> 객체가 지형 아래(지하)에 위치하는 것으로 처리할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type    | Description                                      |
| :---------- | ------- | ------------------------------------------------------ |
| underground | boolean | <p>true: 지형 아래(지하)로 처리.<br>false: 지형 위로 처리.</p> |

-   Return(getUnderground)
    -   true: 지하 상태.
    -   false: 지하가 아니거나 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setUnderground(true);
var isUnderground = object.getUnderground();
```

{% endtab %}
{% endtabs %}
