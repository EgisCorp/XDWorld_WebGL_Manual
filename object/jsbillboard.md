---
description: 
---

# CJSBillboard

Module createBillboard API로 생성할 수 있습니다.

```javascript
var object = Module.createBillboard("ID");
```

## set\([JSVector3D](../core/jsvector3d.md) _vPosition, JSIcon _icon, number _width, number _height\) → boolean

> 빌보드 객체에 필수적 요소를 적용한다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _vPosition | [JSVector3D](../core/jsvector3d.md) | 객체의 위치 |
| _icon | JSIcon | 객체의 이미지 아이콘 |
| _width | number | 객체의 가로 표현 크기 |
| _height | number | 객체의 세로 표현 크기 |

* Detail
  * _vPosition : 경위도 좌표에 바닥면 기준 높이
  * _width, _height : 미터 단위
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_billboard_create
{% endtab %}
{% endtabs %}

## setImage\([JSVector3D](../core/jsvector3d.md) _vPosition, object _resopnse, number _iimagewidth, number _iimagewidth\) → boolean

> 중심 좌표와 반경, 버텍스 수로 원 모양의 평면 좌표를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _vPosition | [JSVector3D](../core/jsvector3d.md) | 객체의 위치 |
| _resopnse | object | 이미지 바이너리 데이터 |
| _iimagewidth | number | 이미지의 너비 |
| _iimagewidth | number | 이미지의 높이 |

* Detail
  * _vPosition : 경위도 좌표에 바닥면 기준 높이
  * _resopnse : Uint8Array 기반의 바이너리 배열 데이터
  * _iimagewidth, _iimagewidth : 이미지의 픽셀 크기 (정수형)
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setSizeScale\(number _fx, number _fy, number _fz\) → boolean

> 객체의 표현 배율 제어

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _fx | number | x축 배율 |
| _fy | number | y축 배율 |
| _fz | number | z축 배율 |

* Detail
  * _fx, _fy, _fz : 반드시 0 보다 큰 값이 필요
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setSizeFix\(boolean _bSet\) → boolean

> 객체의 표현 크기를 고정 또는 가변 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _bSet | boolean | 크기 고정 설정 |

* Detail
  * _bSet : True - 사물의 거리와 관계 없이 고정 픽셀 크기
  * _bSet : False - 사물과 거리에 관계한 실제 크기로 화면상 가변 픽셀 크기
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_billboard_fix_size
{% endtab %}
{% endtabs %}

## setRotationMode\(boolean _bMode\) → boolean

> 빌보드 객체의 표현 방향성을 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _bMode | boolean | 방향 모드 |

* Detail
  * _bMode : true - 화면 정면 방향으로 표현 방향 고정
  * _bMode : false - 좌우 표현 방향은 고정, 상하 표현은 가변
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}