---
description: 지도 네비게이션(나침반) 설정 기능 API.
---

# JSNavigationControl

Module getNavigation API로 생성할 수 있습니다.

```javascript
var navigation = Module.getNavigation();
```

### setPadding(number left, number top)

> 네비게이션(나침반) Padding 값을 설정합니다.

{% tabs %}
{% tab title="Name" %}
| Name | Type   | Description    |
| ---- | ------ | -------------- |
| left | number | left Padding 값 |
| top  | number | top Padding 값  |

* Sample
  * function setNavigationPadding 참조.
  * [샌드박스\_맵 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option\_control\_map)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getNavigation().setPadding(50, 50);
```
{% endtab %}
{% endtabs %}

### getPadding() → [JSVector2D](../core/jsvector2d.md)

> 네비게이션(나침반) Padding 값을 반환합니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * x : left Padding 설정값.
  * y : top Padding 설정값.
* Sample
  * function getNavigationProperties 참조.
  * [샌드박스\_맵 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option\_control\_map)
{% endtab %}

{% tab title="Template" %}
```javascript
var padding = Module.getNavigation().getPadding();
```
{% endtab %}
{% endtabs %}

### setNaviPos(align)

> 네비게이션(나침반) 정렬 방식(Align)을 설정합니다.

{% tabs %}
{% tab title="Name" %}
| Name  | Type   | Description                                                    |
| ----- | ------ | -------------------------------------------------------------- |
| align | number | [네비게이션 정렬 타입.](../etc/type-list.md#navigation-align-type-list) |

* Sample
  * function setNavigationAlign 참조.
  * [샌드박스\_맵 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option\_control\_map)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getNavigation().setNaviPos(Module.JS_NAVIGATION_LT);
```
{% endtab %}
{% endtabs %}

### getNaviPos() → number

> 네비게이션(나침반) 정렬 방식(Align) 상태를 반환합니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * [네비게이션 정렬 타입](../etc/type-list.md#navigation-align-type-list) 반환.
* Sample
  * function getNavigationProperties 참조.
  * [샌드박스\_맵 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option\_control\_map)
{% endtab %}

{% tab title="Template" %}
```javascript
var naviAlign = Module.getNavigation().getNaviPos();
```
{% endtab %}
{% endtabs %}

### setNaviVisible(number display)

> 네비게이션(나침반) 가시화 설정.

{% tabs %}
{% tab title="Name" %}
| Name    | Type   | Description                                                       |
| ------- | ------ | ----------------------------------------------------------------- |
| display | number | [네비게이션 가시화 타입](../etc/type-list.md#navigation-visible-type-list). |

* Sample
  * function setNavigationVisible 참조.
  * [샌드박스\_맵 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option\_control\_map)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getNavigation().setNaviVisible(Module.JS_VISIBLE_AUTO);
```
{% endtab %}
{% endtabs %}

### getNaviVisible() → number

> 네비게이션(나침반) Display 상태를 반환합니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * [네비게이션 가시화 타입](../etc/type-list.md#navigation-visible-type-list) 반환.
* Sample
  * function getNavigationProperties 참조.
  * [샌드박스\_맵 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option\_control\_map)
{% endtab %}

{% tab title="Template" %}
```javascript
var naviDisplay = Module.getNavigation().getNaviVisible();
```
{% endtab %}
{% endtabs %}
