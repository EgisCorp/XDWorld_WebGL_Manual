---
description: 
---

# JSBarGraph

Module createBarGraph API로 생성할 수 있습니다.

```javascript
var object = Module.createBarGraph("ID");
```

## create\(string legendKey, string label, [JSColor](../core/jscolor.md) color\) → boolean

> 그래프 범례를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| legendKey | string | 그래프 범례 키 |
| label | string | 그래프 범례 명칭 |
| color | [JSColor](../core/jscolor.md) | 그래프 범례 색상 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## insertColumn\(string filedName, [Collection](../core/collection.md) data\) → boolean

> 그래프 데이터 셋을 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| filedName | string | 데이터 셋 명칭 (그래프 하단에 텍스트로 출력됩니다.)  |
| data | [Collection](../core/collection.md) | 데이터 값 리스트 (범례 추가 순서를 따르며, 범례와 1:1 대응됩니다.) |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## insertRow\(string dataSetName, string fontName\) → boolean

> 데이터 셋의 텍스트 폰트를 설정합니다. 

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| dataSetName | string | 데이터 셋 이름 |
| fontName | string | 폰트 이름 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setData\(float interval\) → boolean

> 그래프 화면과 필드 이름 텍스트 간 간격을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Parameter | Type | Contents |
| :--- | :--- | :--- |
| interval | float | 간격 값 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setUnitText\(string dataSetName, number textSize\) → boolean

> 데이터 셋의 텍스트 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| dataSetName | string | 데이터 셋 이름 |
| textSize | number | 텍스트 크기 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setValueRange\(string dataSetName, [JSColor](../core/jscolor.md) textColor, [JSColor](../core/jscolor.md) textOutlineColor\) → boolean

> 데이터 셋의 텍스트 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| dataSetName | string | 데이터 셋 이름 |
| textColor | [JSColor](../core/jscolor.md) | 텍스트 채움 색상 |
| textOutlineColor | [JSColor](../core/jscolor.md) | 텍스트 외곽 색상 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setAnimationSpeed\(float depth\) → boolean

> 그래프 바닥 평면 너비 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| depth | float | 너비 값 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setFloorColor\([JSColor](../core/jscolor.md) color\) → boolean

> 그래프 바닥 평면 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| color | [JSColor](../core/jscolor.md) | 색상 값 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setLegendBoxSize\([JSSize3D	](../core/jssize3d.md) boxSize\) → boolean

> 범례 색상 표시 박스 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| boxSize | [JSSize3D](../core/jssize3d.md) | 박스 크기 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setValueRange\(number min, number max, number interval\) → boolean

> 그래프 Y축 범위를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| min | number | 그래프 Y축 최소 값 |
| max | number | 그래프 Y축 최대 값 |
| interval | number | 그래프 격자 간격 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setUnitText\(string unitText\) → boolean

> 그래프 Y축 단위 텍스트를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| unitText | string | 단위 텍스트 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setAnimationSpeed\(number speed\) → boolean

> 그래프 애니메이션 실행 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| speed | number | 그래프 애니메이션 실행 속도 (0.1~1.0 사이 값을 가지며 값이 클 수록 빠르게 애니메이션이 재생됩니다.) |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## create\([JSVector3D](../core/jsvector3d.md) position, [JSSize3D	](../core/jssize2d.md) size, number barType\) → boolean

> 지정한 데이터, 위치, 크기로 그래프 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 그래프 위치 (그래프 중앙 하단점 기준) |
| size | [JSSize3D](../core/jssize2d.md) | 그래프 크기 |
| barType | number | 그래프 막대 형태 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setGridVisible\(boolean visible\) → boolean

> 그래프 Y축과 격자를 보기/숨김 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| visible | boolean | 그래프 Y축 및 격자 보기/숨김 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}