---
description: 
---

# CJSPointGraph

Module createPointGraph API로 생성할 수 있습니다.

```javascript
var object = Module.createPointGraph("ID");
```

## insertLegend\(number sectionValue, [JSColor](../core/jscolor.md) color\) → boolean

> 그래프 범례의 구간 값과 색상을 지정합니다. 포인트 색상은 지정된 범례 구간 값에 해당하는 색상으로 설정됩니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| sectionValue | number | 범례 구간 값 |
| color | [JSColor](../core/jscolor.md) | 범례 색상 설정 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setAxisRange\(number axisType, number min, number max, number interval\) → boolean

> 그래프의 x, y, z 축의 범위 및 눈금 표시 간격을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| axisType | number | 축 타입(0 : X축, 1 : Y축, 2 : Z축) |
| min | number | 축 최소 값 |
| max | number | 축 최대 값 |
| interval | number | 그래프 눈금 표시 간격 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## insertData\(number x, number y, number z, number value\) → boolean

> 그래프 포인터 데이터를 입력합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| x | number | x축 위치 |
| y | number | y축 위치 |
| z | number | z축 위치 |
| value | number | 데이터 값 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setPointLineVisible\(boolean visible\) → boolean

> 포인트와 그래프 바닥을 잇는 라인의 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| visible | boolean | 라인 표시 여부 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## create\([JSVector3D](../core/jsvector3d.md) position, [JSSize3D	](../core/jssize3d.md) size\) → boolean

> 포인트 그래프를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 그래프 위치 |
| size | [JSSize3D	](../core/jssize3d.md) | 그래프 크기 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}