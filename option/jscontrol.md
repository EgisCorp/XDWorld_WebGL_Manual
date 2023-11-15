---
description: 지도 컨트롤 관련 기능 관리 API.
---

# JSControl

> Module.getControl API 생성.

```javascript
var object = Module.getControl();
```

### activeMouse(type) → boolean

> 마우스 콜백 이벤트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 마우스 콜백 이벤트 활성화.<br>false인 경우 마우스 콜백 이벤트 비 활성화.</p> |

* Return
  * true : 마우스 콜백 이벤트 사용 활성화 상태.
  * false : 마우스 콜백 이벤트 사용 비 활성화 상태.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setMouseWheelCenterMode(type)

> 마우스 휠로 인한 확대 축소 동작에서 마우스 커서 중심 여부 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 화면 중심으로 확대, 축소.<br>false인 경우 마우스 위치로 확대, 축소.</p> |

{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## Getter / Setter

### getKeyControlEnable() → boolean

> 키보드 카메라 조작 여부 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 키보드 이벤트 활성화 상태.
  * false : 키보드 이벤트 비 활성화 상태.

* Sample
  * function setMouseOption 참조
  * [샌드박스\_키보드 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_key)
{% endtab %}

{% tab title="Template" %}
```javascript
var vKeyEnable = Module.getControl().getKeyControlEnable();
```
{% endtab %}
{% endtabs %}

### setKeyControlEnable(type)

> 키보드 카메라 조작 여부 설정.
>
> 키보드 입력에 따른 카메라 이벤트 정보.
>
> 키보드 화살표 : 전후좌우 이동.
>
> delete, Q(좌회전), insert, E(우회전), home(확대), end(축소), pageup(상단회전), pagedown(하단회전).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 키보드 이벤트 활성화.<br>false인 경우 키보드 이벤트 비 활성화.</p> |

* Sample
  * function setMouseOption 참조
  * [샌드박스\_키보드 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_key)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setKeyControlEnable(false);
```
{% endtab %}
{% endtabs %}

### getKeyPanMode() → boolean

> 키보드의 화살표 입력으로 동작하는 이동(pan) 동작 여부 설정값 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 키보드 이동(pan) 활성화 상태.
  * false : 키보드 이동(pan) 비 활성화 상태.

* Sample
  * function setMouseOption 참조
  * [샌드박스\_키보드 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_key)
{% endtab %}

{% tab title="Template" %}
```javascript
var bPanEnable = Module.getControl().getKeyPanMode();
```
{% endtab %}
{% endtabs %}

### setKeyPanMode(type)

> 키보드의 화살표 입력으로 동작하는 이동(pan) 상태 설정.
>
> 키보드 이동 기본값은 true.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 이동(pan) 활성화.<br>false인 경우 이동(pan) 비 활성화.</p> |

* Sample
  * function setMouseOption 참조
  * [샌드박스\_키보드 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_key)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setKeyPanMode(false);
```
{% endtab %}
{% endtabs %}

### getKeyRotMode() → boolean

> 키보드의 Q, E delete, insert, pageup, pagedown으로 동작하는 회전(rotation) 상태 설정값 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 키보드 회전 활성화 상태.
  * false : 키보드 회전 비 활성화 상태.

* Sample
  * function setMouseOption 참조
  * [샌드박스\_키보드 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_key)
{% endtab %}

{% tab title="Template" %}
```javascript
var bRotEnable = Module.getControl().getKeyRotMode();
```
{% endtab %}
{% endtabs %}

### setKeyRotMode(type)

> 키보드의 Q, E delete, insert, pageup, pagedown으로 동작하는 회전(rotation) 상태 설정.
>
> 키보드 회전 상태 기본값은 true.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 회전(rotation) 활성화.<br>false인 경우 회전(rotation) 비 활성화.</p> |

* Sample
  * function setMouseOption 참조
  * [샌드박스\_키보드 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_key)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setKeyRotMode(false);
```
{% endtab %}
{% endtabs %}

### getKeyZoomMode() → boolean

> 키보드의 home, end으로 동작하는 확대, 축소(zoom) 상태 설정값 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 키보드 확대, 축소 활성화 상태.
  * false : 키보드 확대, 축소 비 활성화 상태.

* Sample
  * function setMouseOption 참조
  * [샌드박스\_키보드 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_key)
{% endtab %}

{% tab title="Template" %}
```javascript
var bZoomEnable = Module.getControl().getKeyZoomMode();
```
{% endtab %}
{% endtabs %}

### setKeyZoomMode(type)

> 키보드의 home, end으로 동작하는 확대, 축소(zoom) 상태 설정.
>
> 키보드 확대, 축소 상태 기본값은 true.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 확대, 축소 활성화.<br>false인 경우 확대, 축소 비 활성화.</p> |

* Sample
  * function setMouseOption 참조
  * [샌드박스\_키보드 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_key)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setKeyZoomMode(true);
```
{% endtab %}
{% endtabs %}

### getMousePanMode() → boolean

> 마우스 왼쪽 드래그로 동작하는 이동(Pan) 상태 설정값 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 마우스 이동(pan) 활성화 상태.
  * false : 마우스 이동(pan) 비 활성화 상태.

* Sample
  * function setMouseOption 참조
  * [샌드박스\_마우스 버튼 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse)
{% endtab %}

{% tab title="Template" %}
```javascript
var bPanEnable = Module.getControl().getMousePanMode();
```
{% endtab %}
{% endtabs %}

### setMousePanMode(type)

> 마우스 왼쪽 드래그로 동작하는 이동(pan) 상태 설정.
>
> 마우스 이동 상태 기본값은 true.
>
> false 설정 시 마우스 이동 동작 비활성화.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 이동(pan) 활성화.<br>false인 경우 이동(pan) 비 활성화.</p> |

* Sample
  * function setMouseOption 참조
  * [샌드박스\_마우스 버튼 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setMousePanMode(false);
```
{% endtab %}
{% endtabs %}

### getMouseRotMode() → boolean

> 마우스 오른쪽 드래그로 동작하는 회전(rotation) 상태 설정값 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 마우스 회전(rotation) 활성화 상태.
  * false : 마우스 회전(rotation) 비 활성화 상태.
  
* Sample
  * function setMouseOption 참조
  * [샌드박스\_마우스 버튼 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse)
{% endtab %}

{% tab title="Template" %}
```javascript
var bRotEnable = Module.getControl().getMouseRotMode();
```
{% endtab %}
{% endtabs %}

### setMouseRotMode(type)

> 마우스 오른쪽 드래그로 동작하는 회전(rotation) 상태 설정.
>
> 마우스 회전 상태 기본값은 true.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 회전(rotation) 활성화.<br>false인 경우 회전(rotation) 비 활성화.</p> |

* Sample
  * function setMouseOption 참조
  * [샌드박스\_마우스 버튼 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}
-------------------------------------------------------------
-------------------------------------------------------------
-------------------------------------------------------------
-------------------------------------------------------------
-------------------------------------------------------------
-------------------------------------------------------------
-------------------------------------------------------------
-------------------------------------------------------------
### getMouseWheelDelta() → number

> 마우스 휠의 델타(동작량)을 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * 마우스 휠의 델타량 값.

* Sample
  * function setMouseWheelDelta 참조
  * [샌드박스\_마우스 버튼 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse)
{% endtab %}

{% tab title="Template" %}
```javascript
var wheelDelta = Module.getControl().getMouseWheelDelta();
```
{% endtab %}
{% endtabs %}

### setMouseWheelDelta(value)

> 마우스 휠의 델타(동작량)을 설정.
>
> value 입력값>0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 마우스 휠 이벤트 시 가변 거리 조정 배율값 설정. |

* Sample
  * function setMouseWheelDelta 참조
  * [샌드박스\_마우스 버튼 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setMouseWheelDelta(0.8);
```
{% endtab %}
{% endtabs %}

### getMouseWheelMode() → boolean

> 마우스 휠 동작 방향의 반전 여부 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 마우스 휠 반전 상태.
  * false : 마우스 휠 기본 상태.

* Sample
  * function setMouseInvert 참조
  * [샌드박스\_마우스 휠 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse_wheel)
{% endtab %}

{% tab title="Template" %}
```javascript
var wheelInvert = Module.getControl().getMouseWheelMode();
```
{% endtab %}
{% endtabs %}

### setMouseWheelMode(type)

> 마우스 휠 동작 방향 반전 설정.
> 
> 기본값은 false(기본 마우스 휠 방향).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 반전 마우스 휠 방향.<br>false인 경우 기본 마우스 휠 방향.</p> |

* Sample
  * function setMouseInvert 참조
  * [샌드박스\_마우스 휠 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse_wheel)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setMouseWheelMode(true);
```
{% endtab %}
{% endtabs %}

### getMouseZoomMode() → boolean

> 마우스 휠 굴림으로 동작하는 확대, 축소(Zoom) 상태 설정값 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 마우스 확대, 축소 활성화 상태.
  * false : 마우스 확대, 축소 비 활성화 상태.

* Sample
  * function setMouseOption 참조
  * [샌드박스\_마우스 버튼 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse)
{% endtab %}

{% tab title="Template" %}
```javascript
var bZoomEnable = Module.getControl().getMouseZoomMode();
```
{% endtab %}
{% endtabs %}

### setMouseZoomMode(type) → boolean

> 마우스 휠 굴림으로 동작하는 확대, 축소(zoom) 상태 설정.
>
> 마우스 확대, 축소 상태 기본값은 true.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 확대, 축소 활성화.<br>false인 경우 확대, 축소 비 활성화.</p> |

* Sample
  * function setMouseOption 참조
  * [샌드박스\_마우스 버튼 컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_mouse)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setMouseZoomMode(true);
```
{% endtab %}
{% endtabs %}

### getRotateSensitivity() → number

> 카메라 회전 민감도 값 반환.
> 
> 기본값은 7.

{% tabs %}
{% tab title="Information" %}

* Return
  * number(1.0 ~ 10.0) : 카메라 민감도 값.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setRotateSensitivity(value)

> 카메라 회전 민감도 설정.
> 
> value 입력값은 1.0~10.0 사이 값으로 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 카메라 민감도 값. |

{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}
