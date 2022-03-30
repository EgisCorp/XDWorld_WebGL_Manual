---
description: 
---

# JSPointGraph

Module createPointGraph API로 생성할 수 있습니다.

```javascript
var object = Module.createPointGraph("ID");
```

## create\([JSVector3D](../core/jsvector3d.md) position, [JSSize3D	](../core/jssize3d.md) size\) → boolean

> 그래프를 생성합니다.

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

## insertLegend\(number sectionValue, [JSColor](../core/jscolor.md) color\) → boolean

> 범례 위치 값 및 색상을 설정합니다

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| sectionValue | number | 범례 구간 값 |
| color | [JSColor](../core/jscolor.md) | 범례 색상 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## insertAxisPoint\(number axisType, number axisPoint\) → boolean

> X, Y축의 눈금 값을 리스트에 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| axisType | number | 축 타입(0 : X축, 1 : Y축) |
| axisPoint | number | 눈금 값 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setData\(number x, number y, number value\) → boolean

> 그래프 데이터를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| x | number | X축 눈금 값 |
| y | number | Y축 눈금 값 |
| value | number | 데이터 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setValueRange\(number min, number max, number interval\) → boolean

> 그래프 높이 축 범위를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| min | number | 축 최소 값 |
| max | number | 축 최대 값 |
| interval | number | 그래프 눈금 표시 간격 (0.0 이상의 값으로 입력) |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setUnitText\(string unitText\) → boolean

> 높이 축 단위 표시 텍스트를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| unitText | string | 단위 표시 텍스트 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setAnimationSpeed\(number speed\) → boolean

> 그래프 애니메이션 재생 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| speed | number | 바 상승 애니메이션 속도 (0.1~1.0 사이 값 설정) |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}