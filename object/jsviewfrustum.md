---
description: 절투체 객체 생성 및 수정 기능 API.
---

# JSViewFrustum

> Module.createViewFrustum API 생성.

```javascript
var object = Module.createViewFrustum("ID");
```

### createViewFrustum(position, pan, tilt, x, y, distance)

> 절두체(frustum) 객체 생성.
>
> Name 변수로 객체 설정.
>
> pan 입력 값에 따른 회전 정보 0, 360(북쪽), 90(동쪽), 180(남쪽), 270(서쪽).
> 
> tilt 입력 값에 따른 회전 정보 0(정면), tilt&lt;0(상단), tilt&gt;0(하단).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 절두체 경위도 시작 위치. |
| pan | number | 절두체 Y축 회전 설정. |
| tilt | number | 절두체 X축 회전 설정. |
| x | number | 절두체 화각 너비 설정. |
| y | number | 절두체 화각 높이 설정. |
| distance | number | 절두체 길이 설정. |

* Sample
  * function init 참조.
  * [샌드박스\_Frustum](http://sandbox.dtwincloud.com/code/main.do?id=object_frustum)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setColor(color)

> 절두체(frustum) 객체 색상 변경.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| color | [JSColor](../core/jscolor.md) | 절두체 가시화 색상. |

* Sample
  * function createViewFrustum 참조.
  * [샌드박스\_Frustum](http://sandbox.dtwincloud.com/code/main.do?id=object_frustum)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getColor() → [JSColor](../core/jscolor.md)

> 절두체(frustum) 객체 색상 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * [JSColor](../core/jscolor.md) : 반환 성공.
  * null : 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFovX(value) → boolean

> 절두체(frustum) 화각 너비 변경.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 절두체 너비 설정 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function resutFrustum 참조.
  * [샌드박스\_Frustum](http://sandbox.dtwincloud.com/code/main.do?id=object_frustum)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFovY(value) → boolean

> 절두체(frustum) 화각 높이 변경.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 절두체 높이 설정 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function resutFrustum 참조.
  * [샌드박스\_Frustum](http://sandbox.dtwincloud.com/code/main.do?id=object_frustum)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getFov() → [JSVector2D](../core/jsvector2d.md)

> 절두체(frustum) 화각 크기 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * [JSVector2D](../core/jsvector2d.md) : 절투체 화각 크기 반환 성공(return.x : 너비, return.y : 높이).
  * null : 절투체 화각 크기 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPan(pan)

> 절두체(frustum) Y축 회전값 변경.
> 
> pan 입력 값에 따른 회전 정보 0, 360(북쪽), 90(동쪽), 180(남쪽), 270(서쪽).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| pan | number | 절두체 Y축 회전 설정 |
  
* Sample
  * function resutFrustum 참조.
  * [샌드박스\_Frustum](http://sandbox.dtwincloud.com/code/main.do?id=object_frustum)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getPan() → number

> 절두체(frustum) Y축 회전값 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * 절투체 Y축 회전값 반환
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setTilt(tilt)

> 절두체(frustum) X축 회전값 변경.
> 
> tilt 입력 값에 따른 회전 정보 0(정면), tilt&lt;0(상단), tilt&gt;0(하단).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| tilt | number | 절두체 X축 회전 설정 |

* Sample
  * function resutFrustum 참조.
  * [샌드박스\_Frustum](http://sandbox.dtwincloud.com/code/main.do?id=object_frustum)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getTilt() → number

> 절두체(frustum) X축 회전값 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * 절투체 X축 회전값 반환
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}