---
description: 
---

# JSEarthquake

Module getEarthquake API로 생성할 수 있습니다.

```javascript
var object = Module.getEarthquake();
```

## GetEarthquakeData\(string url, [JSVector2D](../core/jsvector2d.md) position\) → boolean

> 지정 포맷 데이터를 로드하여 지진파 오브젝트를 가시화 합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| url | string | 파일 URL |
| position | [JSVector2D](../core/jsvector2d.md) | 오브젝트 생성 위치 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## SetBaseAlphaColor\(number alpha\) → boolean

> 오브젝트의 투명도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| alpha | number | 투명도 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## SetBaseAltitude\(number altitude\) → boolean

> 오브젝트 고도 위치를 설정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| altitude | number | 고도(m) |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## SetHeightWeight\(number weight\) → boolean

> 지진파 높이 편차를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| weight | number | 높이 편차 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## SetResolution\(number resolution\) → boolean

> 오브젝트 표현 해상도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| resolution | number | 해상도 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}