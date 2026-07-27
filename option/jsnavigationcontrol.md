---
description: 지도 내 네비게이션(난침반 UI) 기능을 설정 및 제어하기 위한 API 입니다.
---

# JSNavigationControl

> Module.getNavigation() API를 생성합니다.

```javascript
var navigation = Module.getNavigation();
```

### setZoomDelta(delta)

> 나침반(맵 컨트롤) 확대/축소 이동 비율을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
| ----- | ------ | --------------------- |
| delta | number | 확대/축소 이동 비율 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getPadding(), setPadding(left, top) → [JSVector2D](../core/jsvector2d.md)

> 나침반 Padding 값을 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description      |
| ---- | ------ | ---------------- |
| left | number | left Padding 값. |
| top  | number | top Padding 값.  |

-   Return (get)
    -   x : left Padding 설정값.
    -   y : top Padding 설정값.
-   Sample
    -   function getNavigationProperties 참조.
    -   [Sandbox_Map Control](https://sandbox.egiscloud.com/code/main.do?id=option_control_map)

{% endtab %}
{% tab title="Template" %}

```javascript
var padding = Module.getNavigation().getPadding();
// ... or ...
Module.getNavigation().setPadding(50, 50);
```

{% endtab %}
{% endtabs %}

### getControlSpeed(), setControlSpeed(speed) → number

> 나침반(맵 컨트롤) 조작 속도를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| speed | number | 조작 속도 값. |

-   Return (get)
    -   number: 현재 설정된 조작 속도 값.

{% endtab %}
{% tab title="Template" %}

```javascript
var speed = Module.getNavigation().getControlSpeed();
// ... or ...
Module.getNavigation().setControlSpeed(5.0);
```

{% endtab %}
{% endtabs %}

### getNaviPos(), setNaviPos(align) → number

> 나침반 정렬을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                                  |
| ----- | ------ | ---------------------------------------------------------------------------- |
| align | number | [Navigation alignment type.](../etc/type-list.md#navigation-align-type-list) |

-   Return
    -   number: [navigation alignment type](../etc/type-list.md#navigation-align-type-list) 반환.
-   Sample
    -   function getNavigationProperties 참조.
    -   [Sandbox_Map Control](https://sandbox.egiscloud.com/code/main.do?id=option_control_map)

{% endtab %}
{% tab title="Template" %}

```javascript
var naviAlign = Module.getNavigation().getNaviPos();
// ... or ...
Module.getNavigation().setNaviPos(Module.JS_NAVIGATION_LT);
```

{% endtab %}
{% endtabs %}

### getNaviVisible(), setNaviVisible(display) → number

> 나침반 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                     |
| ------- | ------ | ------------------------------------------------------------------------------- |
| display | number | [Navigation visibility type](../etc/type-list.md#navigation-visible-type-list). |

-   Return
    -   number: [navigation visibility type](../etc/type-list.md#navigation-visible-type-list) 반환.
-   Sample
    -   function getNavigationProperties 참조.
    -   [Sandbox_Map Control](https://sandbox.egiscloud.com/code/main.do?id=option_control_map)

{% endtab %}
{% tab title="Template" %}

```javascript
var naviDisplay = Module.getNavigation().getNaviVisible();
// ... or ...
Module.getNavigation().setNaviVisible(Module.JS_VISIBLE_AUTO);
```

{% endtab %}
{% endtabs %}
