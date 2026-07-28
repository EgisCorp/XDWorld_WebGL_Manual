---
description: 실내(Indoor) 1인칭 이동 모드를 설정하기 위한 API 입니다.
---

# JSIndoor

> Module.getIndoor() API를 생성합니다.

```javascript
var indoor = Module.getIndoor();
```

## Function

### setIndoorMode(set) → boolean

> 실내 1인칭 이동 모드의 활성화 여부를 설정합니다.
>
> 활성화 시 카메라 뷰 모드가 1인칭(Walk) 모드로 전환되고 마우스 팬/휠 조작이 비활성화되며, 비활성화 시 일반 비행(Fly) 모드로 복귀합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                          |
| :--- | ------- | --------------------------------------------------------- |
| set  | boolean | <p>true: 실내 이동 모드 활성화.<br>false: 비활성화.</p>   |

-   Return
    -   true: 설정 성공.
    -   false: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getIndoor().setIndoorMode(true);
```

{% endtab %}
{% endtabs %}

### setIndoorObject(object)

> 실내 이동(벽 충돌 검사 등) 기준이 되는 건물/실내 객체를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                              | Description       |
| :----- | ---------------------------------- | ---------------------- |
| object | [JSObject](../object/jsobject3d.md) | 실내 이동 기준 객체.   |

-   Note
    -   월드가 초기화되지 않았거나 object가 null(또는 내부 객체가 없는 경우) 아무 동작도 하지 않습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getIndoor().setIndoorObject(building);
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getCheckWallCollision(), setCheckWallCollision(set) → boolean

> 실내 이동 시 벽 충돌 검사 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                  |
| :--- | ------- | -------------------------------------------------- |
| set  | boolean | <p>true: 벽 충돌 검사 사용.<br>false: 미사용.</p>  |

-   Return
    -   true: 설정/조회 성공(또는 사용 상태).
    -   false: 월드가 초기화되지 않았거나 미사용 상태.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getIndoor().setCheckWallCollision(true);
var isChecking = Module.getIndoor().getCheckWallCollision();
```

{% endtab %}
{% endtabs %}

### setFixCameraHighFromFloor(set) → boolean

> 실내 이동 시 바닥으로부터의 카메라 높이를 고정할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                          |
| :--- | ------- | ---------------------------------------------------------- |
| set  | boolean | <p>true: 바닥 기준 카메라 높이 고정.<br>false: 미고정.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getIndoor().setFixCameraHighFromFloor(true);
```

{% endtab %}
{% endtabs %}
