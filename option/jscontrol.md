---
description: 지도 컨트롤 관련 기능 관리 API.
---

# JSControl

> Module.getControl API 생성.

```javascript
var object = Module.getControl();
```

### setMouseWheelDelta(value)

> 마우스 휠의 델타(동작량)을 설정.
>
> value 입력값>0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 마우스 휠 이벤트 시 가변 거리 조정 배율값 설정. |

{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setMouseWheelDelta(0.8);
```
{% endtab %}
{% endtabs %}

### getMouseWheelDelta() → number

> 마우스 휠의 델타(동작량)을 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * 마우스 휠의 델타량 값.
{% endtab %}

{% tab title="Template" %}
```javascript
var wheelDelta = Module.getControl().getMouseWheelDelta();
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
> insert(좌회전), delete(우회전), home(확대), end(축소), pageup(상단회전), pagedown(하단회전).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 키보드 이벤트 활성화.<br>false인 경우 키보드 이벤트 비 활성화.</p> |

{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setKeyControlEnable(false);
```
{% endtab %}
{% endtabs %}

### getKeyControlEnable() → boolean

> 키보드 카메라 조작 여부 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 키보드 이벤트 활성화 상태.
  * false : 키보드 이벤트 비 활성화 상태.
{% endtab %}

{% tab title="Template" %}
```javascript
var vKeyEnable = Module.getControl().getKeyControlEnable();
```
{% endtab %}
{% endtabs %}

### setMouseWheelMode(type)

> 마우스 휠 동작 방향을 반전 설정
> 
> 마우스 흴 동작 방향 기본값은 false.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 기본 마우스 흴 방향.<br>false인 경우 반전 마우스 휠 방향.</p> |

{% endtab %}

{% tab title="Template" %}
```javascript
Module.getControl().setMouseWheelMode(true);
```
{% endtab %}
{% endtabs %}

### getMouseWheelMode() → boolean

> 마우스 휠 동작 방향을 반전 설정 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 마우스 휠 기본 상태.
  * false : 마우스 반전 휠 이동 상태.
  
{% endtab %}

{% tab title="Template" %}
```javascript
var wheelInvert = Module.getControl().getMouseWheelMode();
```
{% endtab %}
{% endtabs %}

### setMousePanMode(type)

> 마우스 왼쪽 드래그로 동작하는 이동(Pan) 동작 여부 여부를 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | Pan 기능 사용 여부 값 |

* Detail
  * type : 기본값 true, false시 왼쪽 마우스 버튼 이동 동작 비활성화
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getMousePanMode() → boolean

> 마우스 왼쪽 드래그로 동작하는 이동(Pan) 동작 여부 설정값 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 이동(Pan) 동작 기능 설정값 
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setMouseRotMode(type)

> 마우스 오른쪽 드래그로 동작하는 회전(Rotation) 동작 여부 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | 회전 동작 여부 설정 |

* Detail
  * type : 기본값 true, false일시 우측 마우스 드래그로 회전하지 않음

* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getMouseRotMode() → boolean

> 마우스 오른쪽 드래그로 동작하는 회전(Rotation) 동작 여부 설정 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * radius : 0이상의 값으로 입력, 단위는 미터 단위.
  
* Return
  * 마우스 회전(Rotation) 동작 여부 설정값
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setMouseZoomMode(type) → boolean

> 마우스 휠 굴림에 의한 확대, 축소(Zoom) 동작 여부를 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | 줌 동작 여부 설정 |

* Detail
  * type : 마우스 휠 굴림에 확대, 축소 동작 여부 설정
  
* Return
  * 
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getMouseZoomMode() → boolean

> 마우스 휠 굴림에 의한 확대, 축소(Zoom) 동작 여부값 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * 마우스 휠 굴림에 의한 확대, 축소(Zoom) 동작 여부값
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setKeyPanMode(type)

> 키보드의 전후좌우 이동(Pan)의 동작 여부 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | 키보드 이동 동작 여부 값 |

* Detail
  * type : 기본값 true, false시 화살표 키로 이동기능 불가
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getKeyPanMode() → boolean

> 키보드의 전후좌우 이동(Pan)의 동작 여부 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 키보드 이동 동작 여부값 
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setKeyRotMode(type)

> 키보드의 수평,수직 회전(Rot)의 동작 여부 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | 키보드의 회전 동작 여부 값 |

* Detail
  * type : 기본값 true, false시 키보드의 수직,수평회전 동작 불가

* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getKeyRotMode() → boolean

> 키보드의 수평,수직 회전(Rot)의 동작 여부 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 키보드의 회전 동작 여부 값
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setKeyZoomMode(type)

> 키보드의 확대,축소(Zoom)의 동작 여부 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | 키보드 확대축소 동작 설정 값 |

* Detail
  * type : 기본값 true, false시 키보드 확대,축소 동작이 불가
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getKeyZoomMode() → boolean

> 키보드의 확대,축소(Zoom)의 동작 여부 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 키보드 확대축소 동작 설정 값
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setRotateSensitivity(value)

> 카메라 회전 민감도 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 카메라 민감도 값 |

* Detail
  * value : 1.0~10.0 범위. 기본값 4.0
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getRotateSensitivity() → number

> 카메라 회전 민감도 값 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 카메라 민감도 값
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setMouseWheelCenterMode(type)

> 마우스 휠로 인한 확대 축소 동작에서 마우스 커서 중심 여부 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | 마우스 휠 동작 모드 설정 |

* Detail
  * type : false \- 마우스 커서 중심 모드 (기본값), true \- 화면 중심 모드
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### activeMouse(type) → boolean

> 마우스 동작 활성화 여부 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | 반경 |

* Detail
  * boolean : false - 마우스 동작 처리 비활성화, true \- 마우스 동작 처리 활성화 (기본값)
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}
