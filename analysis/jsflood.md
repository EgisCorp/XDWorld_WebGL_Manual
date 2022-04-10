---
description: 물판 생성 및 설정 기능 API.
---

# JSFlood

> Module.getFlood API 생성.

```javascript
var flood = Module.getFlood();
```

### active(active)

> 물판 동작 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| active | boolean | 물판 동작 설정 (true : 물판 동작, false : 물판 해제)| 

* Sample
  * function init 참조.
  * [샌드박스\_홍수](http://sandbox.dtwincloud.com/code/main.do?id=weather_flood)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setColor(color)

> 물판 색상을 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| color | [JSColor](../core/jscolor.md) | 물판 색상 |

* Sample
  * function SetFloodColor 참조.
  * [샌드박스\_홍수](http://sandbox.dtwincloud.com/code/main.do?id=weather_flood)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setHeight(height)

> 물판 높이 기준 높이 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| height | number | 물판 기준 높이 (해발고도 기준, 단위 : 미터) |

* Sample
  * function setFloodHeight 참조.
  * [샌드박스\_홍수](http://sandbox.dtwincloud.com/code/main.do?id=weather_flood)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setVisibleAltitude(altitude)

> 물판 표현 가시거리를 설정
>
> 수치가 크면 먼거리에서도 물판이 표현

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| altitude | number | 물판 가시거리 (단위 : 미터) |

* Sample
  * function setFloodVisibleAltitude 참조.
  * [샌드박스\_홍수](http://sandbox.dtwincloud.com/code/main.do?id=weather_flood)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWaterSpeed(speed)
> 물판 유속을 설정
> 
> 수치가 높을 수록 유속이 빠름

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| speed | number | 물판 유속 |

* Sample
  * function SetWaterSpeed 참조.
  * [샌드박스\_홍수](http://sandbox.dtwincloud.com/code/main.do?id=weather_flood)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### visibleWaterPlane(type)
> 물판의 화면 시각화 여부를 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| type | boolean | 물판 시각화 (true : 표현, false : 숨김) |
  
* Sample
  * function visibleWaterPlane 참조.
  * [샌드박스\_홍수](http://sandbox.dtwincloud.com/code/main.do?id=weather_flood)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}