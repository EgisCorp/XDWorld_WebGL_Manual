---
description: 
---

# JSGhostSymbol

Module createGhostSymbol API로 생성할 수 있습니다.

```javascript
var object = Module.createGhostSymbol("ID");
```

## setGhostSymbol\(string model_id\) → boolean

> 고스트 심볼 맵에 등록된 오브젝트의 모델을 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| model_id | string | 모델 키 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setPosition\([JSVector3D](../core/jsvector3d.md) position\) → boolean

> 고스트 심볼 오브젝트의 위치를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 오브젝트의 위치 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setScale\([JSSize3D	](../core/jssize3d.md) scale\) → boolean

> 고스트 심볼 오브젝트의 스케일을 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| scale | [JSSize3D	](../core/jssize3d.md) | 오브젝트의 스케일 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getPosition\(\) → [JSVector3D](../core/jsvector3d.md)

> 오브젝트 위치를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * 오브젝트 위치
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getScale\(\) → [JSSize3D	](../core/jssize3d.md)
> 오브젝트 스케일을 반환합니다.
{% tabs %}
{% tab title="Information" %}

* Return
  * 오브젝트 스케일
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getGhostSymbolMapKey\(\) → string
> 오브젝트에 지정 된 원본 모델 키 값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * 지정된 원본 모델 키
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setRotation\(number x, number y, number z\) → boolean

> 오브젝트의 회전 각도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| x | number | x축 방향 회전 각도 |
| y | number | y축 방향 회전 각도 |
| z | number | z축 방향 회전 각도 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getRotationX\(\) → number

> 오브젝트의 X축 방향 회전 각도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * X축 방향 회전 각도
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getRotationY\(\) → number

> 오브젝트의 Y축 방향 회전 각도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * Y축 방향 회전 각도
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getRotationZ\(\) → number

> 오브젝트의 Z축 방향 회전 각도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * Z축 방향 회전 각도
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setBasePoint\(number x, number y, number z\) → boolean

> 오브젝트의 중점 위치를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| x | number | x축 중점 |
| y | number | y축 중점 |
| z | number | z축 중점 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getBasePointX\(\) → number

> 오브젝트 중점 X축 좌표를 반환합니다.
{% tabs %}
{% tab title="Information" %}

* Return
  * 오브젝트 중점 X축 좌표
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getBasePointY\(\) → number

> 오브젝트 중점 Y축 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |

* Return
  * 오브젝트 중점 Y축 좌표
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getBasePointZ\(\) → number

> 오브젝트 중점 Z축 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |

* Return
  * 오브젝트 중점 Z축 좌표
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getOpacity\(\) → number

> 오브젝트 투명도를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |

* Return
  * 오브젝트 투명도
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setOpacity\(object opacity\) → string

> 오브젝트 투명도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| opacity | number | 오브젝트 투명도 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getColor\(\) → [JSColor](../core/jscolor.md)

> 오브젝트 색상을 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * 오브젝트 색상
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setColor\([JSColor](../core/jscolor.md) color)\) → string

> 오브젝트 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| color | [JSColor](../core/jscolor.md) | 오브젝트 색상 |

* Return
  * 설정 결과
  
* Code
  * 
{% endtab %}
{% endtabs %}