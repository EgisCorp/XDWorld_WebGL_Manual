---
description: 지도 내 전파 범위 3차원 모델 객체를 생성 및 설정하기 위한 API 입니다.
---

# CJSBillboard

Module.createBillboard() API를 생성합니다.

```javascript
var object = Module.createBillboard("ID");
```

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

### set(position, icon, width, height) → boolean

> 빌보드 객체 생성 옵션을 설정합니다..

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                                       |
| :------- | :---------------------------------- | :------------------------------------------------ |
| position | [JSVector3D](../core/jsvector3d.md) | 빌보드 위치 좌표(경도, 위도, 고도) 기준은 중하단. |
| icon     | [JSIcon](jsicon.md)                 | 객체의 이미지 아이콘.                             |
| width    | number                              | 객체의 가로 표현 크기(미터).                      |
| height   | number                              | 객체의 세로 표현 크기(미터).                      |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createBillboard 참조.
    -   [Sandbox_Billboard](https://sandbox.egiscloud.com/code/main.do?id=object_billboard_create)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setImage(position, data, width, height) → boolean

> 빌보드 객체 생성 옵션을 설정합니다.
>
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터 입니다..

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                                       |
| :------- | :---------------------------------- | :------------------------------------------------ |
| position | [JSVector3D](../core/jsvector3d.md) | 빌보드 위치 좌표(경도, 위도, 고도) 기준은 중하단. |
| data     | object                              | 이미지 바이너리 데이터.                           |
| width    | number                              | 이미지의 너비.                                    |
| height   | number                              | 이미지의 높이.                                    |

-   Return

    -   true: 설정 성공.
    -   false: 설정 실패.

-   Sample
    -   function createBillboard 참조.
    -   [Sandbox_Billboard Text](https://sandbox.egiscloud.com/code/main.do?id=object_billboard_create)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSizeScale(x, y, z) → boolean

> 객체의 크기 배율을 설정합니다.
>
> 각 항목은 0보다 큰 값으로 설정합니다..

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| :--- | :----- | :---------- |
| x    | number | x축 배율.   |
| y    | number | y축 배율.   |
| z    | number | z축 배율.   |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSizeFix(type) → boolean

> 객체의 표현 크기를 고정 또는 가변으로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                            |
| :--- | :------ | :----------------------------------------------------- |
| type | boolean | <p>true: 고정 크기 설정.<br>false: 가변 크기 설정.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function setBillboardFixSize 참조.
    -   [Sandbox_Billboard Size Option](https://sandbox.egiscloud.com/code/main.do?id=object_billboard_fix_size)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRotationMode(type) → boolean

> 빌보드 객체의 회전 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                        |
| :--- | :------ | :----------------------------------------------------------------- |
| type | boolean | <p>true: 화면 정면 고정.<br>false: 좌우만 고정, 상하 가변 회전.<p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function setBillboardRotationMode 참조.
    -   [Sandbox_Billboard Rotation Option](https://sandbox.egiscloud.com/code/main.do?id=object_billboard_rotation)

{% endtab %}
{% tab title="Template" %}

```javascript

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
