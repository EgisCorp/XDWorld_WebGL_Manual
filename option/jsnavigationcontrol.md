---
description: 지도 네비게이션(나침반) 설정 API를 제공합니다.
---

# JSNavigationControl

Module getNavigation API로 생성할 수 있습니다.

```javascript
var navigation = Module.getNavigation();
```

## setPadding(number left, number top)

> 네비게이션(나침반) Padding 값을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| --------- | ---- | -------- |
| left | number  | left Padding 값  |
| top | number  | top Padding 값  |

* Code
```
Module.getNavigation().setPadding(50, 50);
```
{% endtab %}
{% endtabs %}

## getPadding() → [JSVector2D](../core/jsvector2d.md)

> 네비게이션(나침반) Padding 값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * x : left Padding 설정값
  * y : top Padding 설정값
  
* Code
```
var padding = Module.getNavigation().getPadding();
```
{% endtab %}
{% endtabs %}

## setNaviPos(number align)

> 네비게이션(나침반) 정렬 방식(Align)을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| --------- | ---- | -------- |
| align | number  | 정렬 방식 상태  |

* Detail
  * type
    * Module.JS_NAVIGATION_LT : Left/Top
    * Module.JS_NAVIGATION_RT : Right/Top
    * Module.JS_NAVIGATION_LB : Left/Buttom
    * Module.JS_NAVIGATION_RB : Right/Buttom
	
* Code
```
Module.getNavigation().setNaviPos(Module.JS_NAVIGATION_LT);
```
{% endtab %}
{% endtabs %}

## getNaviPos() → number

> 네비게이션(나침반) 정렬 방식(Align) 상태를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Detail
  * type
    * Module.JS_NAVIGATION_LT : Left/Top
	* Module.JS_NAVIGATION_RT : Right/Top
	* Module.JS_NAVIGATION_LB : Left/Buttom
	* Module.JS_NAVIGATION_RB : Right/Buttom
	
* Return
  * 네비게이션 정렬 방식 상태

* Code
```
var naviAlign = Module.getNavigation().getNaviPos();
```
{% endtab %}
{% endtabs %}

## setNaviVisible(number display)

> 네비게이션(나침반) Display 상태를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| --------- | ---- | -------- |
| display | number  | Display 상태  |

* Detail
  * type
    * Module.JS_VISIBLE_OFF : 네비게이션 숨김 설정
    * Module.JS_VISIBLE_ON : 네비게이션 보기 설정(활성화)
    * Module.JS_VISIBLE_AUTO : 네비게이션 보기 설정(간소화)
  
* Code
```
Module.getNavigation().setNaviVisible(Module.JS_VISIBLE_AUTO);
```
{% endtab %}
{% endtabs %}

## getNaviVisible() → number

> 네비게이션(나침반) Display 상태를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Detail
  * type
    * Module.JS_VISIBLE_OFF : 네비게이션 숨김 설정
	* Module.JS_VISIBLE_ON : 네비게이션 보기 설정(활성화)
	* Module.JS_VISIBLE_AUTO : 네비게이션 보기 설정(간소화)
	
* Return
  * 네비게이션 Display 상태

* Code
```
var naviDisplay = Module.getNavigation().getNaviVisible();
```
{% endtab %}
{% endtabs %}