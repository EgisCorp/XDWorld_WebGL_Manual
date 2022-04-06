---
description: ARGB 색상을 정의합니다.
---

# JSColor

new Module.Color\(\) 로 생성합니다.

```javascript
var color = new Module.Color(255, 100, 100, 0);

var color = new Module.Color(100, 100, 0);

var color = new Module.Color();
```

## properties

| name | Type | Contents |
| :--- | :--- | :--- |
| a | number | alpha 색상 값 |
| r | number | red 색상 값 |
| g | number | green 색상 값 |
| b | number | blue 색상 값 |

## new Module.JSColor\( alpha, red, green, blue\) → JSColor

> ARGB 값을 활용해 새로운 색상 데이터를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| alpha | number | 0~255 사이 Alpha 값 |
| red | number | 0~255 사이 red 값 |
| green | number | 0~255 사이 green 값 |
| blue | number | 0~255 사이 blue 값 |

* Return : 색상 데이터 JSColor
{% endtab %}
{% endtabs %}

## new Module.JSColor\( red, green, blue\) → JSColor

> RGB 값을 활용해 새로운 색상 데이터를 생성합니다. Alpha 값은 255로 고정됩니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| red | number | 0~255 사이 red 값 |
| green | number | 0~255 사이 green 값 |
| blue | number | 0~255 사이 blue 값 |

* Return : 색상 데이터 JSColor
{% endtab %}
{% endtabs %}

## new Module.JSColor\(\) → JSColor

> 새로운 색상 데이터를 생성합니다. Alpha, Red, Green, Blue 값은 모두 255로 고정됩니다.

{% tabs %}
{% tab title="Information" %}
* Return : 색상 데이터 JSColor
{% endtab %}
{% endtabs %}

