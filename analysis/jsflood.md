---
description: 물판 설정 및 제어를 위한 API를 제공합니다.
---

# JSFlood

Module getFlood API로 생성할 수 있습니다.

```javascript
var flood = Module.getFlood();
```

## active\(boolean active\)

> 물판을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| active | boolean | 물판 설정 |

* Detail
  * active
    * false : 물판 효과를 해제합니다.
    * true : 물판 효과를 적용합니다.
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_flood
{% endtab %}
{% endtabs %}

## setColor\([CJSColor](CJSColor.md) color\)

> 물판 색상을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| color | [CJSColor](CJSColor.md) | 물판 색상 |

* Detail
  * color : [CJSColor](CJSColor.md)

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_flood
{% endtab %}
{% endtabs %}

## setHeight\(number height\)

> 물판 높이를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| height | number | 물판 높이 |

* Detail
  * height : 물판 높이를 설정합니다.

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_flood
{% endtab %}
{% endtabs %}

## setVisibleAltitude\(number altitude\)

> 물판 가시거리를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| altitude | number | 물판 가시거리 |

* Detail
  * altitude : 값이 클수록 멀리서도 물판이 보입니다.

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_flood
{% endtab %}
{% endtabs %}

## setWaterSpeed\(number speed\)

> 물판 유속을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| speed | number | 물판 유속 |

* Detail
  * speed : 값이 클수록 유속이 빨라집니다.

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_flood
{% endtab %}
{% endtabs %}

## visibleWaterPlane\(boolean visible\)

> 물판 on/off를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| visible | boolean | 물판 on/off |

* Detail
  * visible
    * false : 물판 효과를 off 합니다.
    * true : 물판 효과를 on 합니다.
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=weather_flood
{% endtab %}
{% endtabs %}