---
description: 절투체 오브젝트 생성 설정 API.
---

# JSViewFrustum

Module createViewFrustum API로 생성할 수 있습니다.

```javascript
var object = Module.createViewFrustum("ID");
```

## createViewFrustum\([JSVector3D](JSVector3D.md) position, number pan, number tilt, number fov_x, number fov_y, number distance \)

> 절두체(frustum) 오브젝트 생성.
>
> parameter 변수로 절두체(frustum) 오브젝트 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector3D](JSVector3D.md) | 절두체 경위도 시작 위치 |
| pan | number | 절두체 Y축 회전 설정 |
| tilt | number | 절두체 X축 회전 설정 |
| fov_x | number | 절두체 화각 너비 설정 |
| fov_y | number | 절두체 화각 높이 설정 |
| distance | number | 절두체 길이 설정 |

* Detail
  * pan : 0(북쪽), 90(동쪽), 180(남쪽), 270(서쪽)으로 방향 전환.
  * tilt : 0(정면), tilt&lt;0(상단), tilt&gt;0(하단) 방향 전환.  
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_frustum
{% endtab %}
{% endtabs %}

## setColor \([JSColor](../core/jscolor.md) color\)

> 절두체(frustum) 오브젝트 색상 변경.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| color | [JSColor](../core/jscolor.md) | 절두체 가시화 색상 |

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_frustum
{% endtab %}
{% endtabs %}

## getColor \(\) → [JSColor](../core/jscolor.md)

> 절두체(frustum) 오브젝트 색상 반환.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| xxxx | number | xxxx |
  
* Return
  * [JSColor](../core/jscolor.md) : 반환 성공.
  * null : 반환 실패.
{% endtab %}
{% endtabs %}

## setFovX \(number width\) → boolean

> 절두체(frustum) 화각 너비 변경.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| width | number | 절두체 너비 설정 |

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_frustum
{% endtab %}
{% endtabs %}

## setFovY \(number height\) → boolean

> 절두체(frustum) 화각 높이 변경.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| height | number | 절두체 높이 설정 |

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_frustum
{% endtab %}
{% endtabs %}

## getFov \(\) → [JSVector3D](JSVector3D.md)

> 절두체(frustum) 화각 크기 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * [JSVector3D](JSVector3D.md) : 절투체 화각 크기 반환 성공.
	* return.x : 화각 너비.
	* return.y : 화각 높이.
{% endtab %}
{% endtabs %}

## setPan \(number pan \)

> 절두체(frustum) Y축 회전값 변경.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| pan | number | 절두체 Y축 회전 설정 |

* Detail
  * pan : 0(북쪽), 90(동쪽), 180(남쪽), 270(서쪽)으로 방향 전환.
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_frustum
{% endtab %}
{% endtabs %}

## getPan \(\) → number

> 절두체(frustum) Y축 회전값 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * 절투체 Y축 회전값 반환
{% endtab %}
{% endtabs %}

## setTilt \(number tilt\)

> 절두체(frustum) X축 회전값 변경.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| tilt | number | 절두체 X축 회전 설정 |

* Detail
  * tilt : 0(정면), tilt&lt;0(상단), tilt&gt;0(하단) 방향 전환.  
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_frustum
{% endtab %}
{% endtabs %}

## getTilt \(\) → number

> 절두체(frustum) X축 회전값 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * 절투체 X축 회전값 반환
{% endtab %}
{% endtabs %}