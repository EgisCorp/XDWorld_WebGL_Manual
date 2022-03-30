---
description: 
---

# JSEarthquake

Module createMultiPoint API로 생성할 수 있습니다.

```javascript
var object = Module.createMultiPoint();
```

## setMainPoint\(string _key, [JSVector3D](../core/jsvector3d.md) _position, JSIcon _pointIcon\) → boolean

> 주 포인트에 대한 객체 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _key | string | 객체의 고유 키 |
| _position | [JSVector3D](../core/jsvector3d.md) | 객체의 위치 |
| _pointIcon | JSIcon | 객체의 표출 아이콘 |

* Detail
  * _position : 객체의 경위도, 고도 위치
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint
{% endtab %}
{% endtabs %}

## insertSubPoint\(string _key, JSIcon _pointIcon\) → boolean

> 주 포인트에 연결된 보조 포인트를 추가

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _key | string | 객체의 고유 키 |
| _pointIcon | JSIcon | 객체의 표출 아이콘 |

* Detail
  * 보조 포인트의 위치는 주 포인트의 시계방향 순으로 자동배치
  * 객체의 키구성은 (주포인트 키)#(보조포인트 키)로 구성
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint
{% endtab %}
{% endtabs %}

## setBar\([JSColor](../core/jscolor.md) _barColor, number _startPointAltitude, number _thickness\) → boolean

> 지정 높이로부터 주 포인트까지 이어지는 기둥을 생성

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _barColor | [JSColor](../core/jscolor.md) | 기둥의 표현 색상 |
| _startPointAltitude | number | 기둥의 시작 높이 |
| _thickness | number | 기둥의 두께 |

* Detail
  * _startPointAltitude : 해발고도 기준, 단위는 미터 단위.
  * _thickness : 단위는 미터 단위.
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint
{% endtab %}
{% endtabs %}