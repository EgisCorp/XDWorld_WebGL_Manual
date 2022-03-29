---
description: 
---

# JSBarGraph3D

Module createBarGraph3D API로 생성할 수 있습니다.

```javascript
var object = Module.createBarGraph3D("ID");
```

## create\([JSVector3D](../core/jsvector3d.md) position, [JSSize3D](../core/jssize3d.md) size\) → boolean

> 그래프를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 그래프 생성 위치 |
| size | [JSSize3D](../core/jssize3d.md) | 그래프 크기 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## insertColumn\(string columnKey, string columnLabel, [JSColor](../core/jscolor.md) color\) → boolean

> 그래프 Column 정보를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| columnKey | string | column 키 |
| columnLabel | string | column 이름 (그래프 하단부 텍스트로 표시됩니다) |
| color | [JSColor](../core/jscolor.md) | 그래프 바 색상 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## insertRow\(string rowKey, string rowLabel\) → boolean

> 그래프 Row 정보를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| rowKey | string | Row 키 |
| rowLabel | string | Row 이름 (그래프 하단부 텍스트로 표시됩니다) |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setData\(string columnKey, string rowKey, number data\) → boolean

> 지정한 Column, Row에 해당하는 그래프 데이터를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| columnKey | string | Column 키 |
| rowKey | string | Row 키 |
| data | number | 그래프 데이터 |

* Return
  * 설정 결과
  
* Code
  * 
  
{% endtab %}
{% endtabs %}

## setUnitText\(string unitText\) → boolean

> 그래프 높이 축 단위 표시 텍스트를 설정합니다.

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

## setValueRange\(number min, number max, number interval\) → boolean

> 그래프 높이 축의 최소, 최대 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| min | number | 높이 축 최소 값 |
| max | number | 높이 축 최대 값 |
| interval | number | 눈금 표시 간격 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setAnimationSpeed\(number speed\) → boolean

> 그래프 바 상승 애니메이션 속도를 설정합니다.

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