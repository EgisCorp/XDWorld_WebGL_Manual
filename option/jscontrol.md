---
description: 컨트롤 관련 기능 담당
---

# JSControl

Module getControl API로 생성할 수 있습니다.

```javascript
var object = Module.getControl();
```

## setMouseWheelDelta\(number \_dDelta\)

> 마우스 휠의 델타\(동작량\)을 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_dDelta | number | 반경 |

* Detail
  * \_dDelta : 0보다 큰 값 필요, 마우스 휠 동작시 가변 거리조정에 대한 배율값으로 동작

* Code
  * 
{% endtab %}
{% endtabs %}

## getMouseWheelDelta\(\) → number

> 마우스 휠의 델타\(동작량\)을 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 마우스 휠의 델타량 값
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setKeyControlEnable\(boolean \_bEnable\)

> 키보드 카메라 조작 여부 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bEnable | boolean | 키보드 사용 여부 |
* Detail
  * \_bEnable : true - 키보드 제어 가능
    * 위쪽 화살표 : 카메라 전진
    * 아래쪽 화살표 : 카메라 후진
    * 왼쪽 화살표 : 카메라 좌측 이동
    * 오른쪽 화살표 : 카메라 우측 이동
    * Insert\(Ins\) : 카메라 좌회전
    * Delete\(Del\) : 카메라 우회전
    * Home : 카메라 확대
    * End : 카메라 축소
    * PgUp : 카메라 위로 회전
    * PgDown : 카메라 아래로 회전

* Code
  * 
{% endtab %}
{% endtabs %}

## getKeyControlEnable\(\) → boolean

> 키보드 카메라 조작 여부 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 키보드 카메라 조작 설정 반환
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setMouseWheelMode\(boolean \_bInvert\)

> 마우스 휠 동작 방향을 반전 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bInvert | boolean | 마우스 휠 동작 반전 설정 |

* Detail
  * \_bInvert : 기본값 false
    
* Code
  * 
{% endtab %}
{% endtabs %}

## getMouseWheelMode\(\) → boolean

> 마우스 휠 동작 방향을 반전 설정 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 마우스 휠 동작 방향 설정 값
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setMousePanMode\(boolean \_bPanEnable\)

> 마우스 왼쪽 드래그로 동작하는 이동\(Pan\) 동작 여부 여부를 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bPanEnable | boolean | Pan 기능 사용 여부 값 |

* Detail
  * \_bPanEnable : 기본값 true, false시 왼쪽 마우스 버튼 이동 동작 비활성화
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getMousePanMode\(\) → boolean

> 마우스 왼쪽 드래그로 동작하는 이동\(Pan\) 동작 여부 설정값 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 이동\(Pan\) 동작 기능 설정값 
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setMouseRotMode\(boolean \_bRotEnable\)

> 마우스 오른쪽 드래그로 동작하는 회전\(Rotation\) 동작 여부 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bRotEnable | boolean | 회전 동작 여부 설정 |

* Detail
  * \_bRotEnable : 기본값 true, false일시 우측 마우스 드래그로 회전하지 않음

* Code
  * 
{% endtab %}
{% endtabs %}

## getMouseRotMode\(\) → boolean

> 마우스 오른쪽 드래그로 동작하는 회전\(Rotation\) 동작 여부 설정 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * radius : 0이상의 값으로 입력, 단위는 미터 단위.
  
* Return
  * 마우스 회전\(Rotation\) 동작 여부 설정값
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setMouseZoomMode\(boolean _bZoomEnable\) → boolean

> 마우스 휠 굴림에 의한 확대, 축소\(Zoom\) 동작 여부를 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bZoomEnable | boolean | 줌 동작 여부 설정 |

* Detail
  * \_bZoomEnable : 마우스 휠 굴림에 확대, 축소 동작 여부 설정
  
* Return
  * 
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getMouseZoomMode\(\) → boolean

> 마우스 휠 굴림에 의한 확대, 축소\(Zoom\) 동작 여부값 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * 마우스 휠 굴림에 의한 확대, 축소\(Zoom\) 동작 여부값
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setKeyPanMode\(boolean \_bKeyPanEnable\)

> 키보드의 전후좌우 이동\(Pan\)의 동작 여부 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bKeyPanEnable | boolean | 키보드 이동 동작 여부 값 |

* Detail
  * \_bKeyPanEnable : 기본값 true, false시 화살표 키로 이동기능 불가
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getKeyPanMode\(\) → boolean

> 키보드의 전후좌우 이동\(Pan\)의 동작 여부 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 키보드 이동 동작 여부값 
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setKeyRotMode\(boolean \_bKeyRotEnable\)

> 키보드의 수평,수직 회전\(Rot\)의 동작 여부 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bKeyRotEnable | boolean | 키보드의 회전 동작 여부 값 |

* Detail
  * \_bKeyRotEnable : 기본값 true, false시 키보드의 수직,수평회전 동작 불가

* Code
  * 
{% endtab %}
{% endtabs %}

## getKeyRotMode\(\) → boolean

> 키보드의 수평,수직 회전\(Rot\)의 동작 여부 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 키보드의 회전 동작 여부 값
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setKeyZoomMode\(boolean \_bKeyEnableZoom\)

> 키보드의 확대,축소\(Zoom\)의 동작 여부 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bKeyEnableZoom | boolean | 키보드 확대축소 동작 설정 값 |

* Detail
  * \_bKeyEnableZoom : 기본값 true, false시 키보드 확대,축소 동작이 불가
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getKeyZoomMode\(\) → boolean

> 키보드의 확대,축소\(Zoom\)의 동작 여부 반환

{% tabs %}
{% tab title="Information" %}


* Return
  * 키보드 확대축소 동작 설정 값
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setRotateSensitivity\(number \_fSensivitity\)

> 카메라 회전 민감도 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_fSensivitity | number | 카메라 민감도 값 |

* Detail
  * \_fSensivitity : 1.0~10.0 범위. 기본값 4.0
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getRotateSensitivity\(\) → number

> 카메라 회전 민감도 값 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 카메라 민감도 값
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setMouseWheelCenterMode\(boolean \_bMode\)

> 마우스 휠로 인한 확대 축소 동작에서 마우스 커서 중심 여부 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_bMode | boolean | 마우스 휠 동작 모드 설정 |

* Detail
  * \_bMode : false \- 마우스 커서 중심 모드 \(기본값\), true \- 화면 중심 모드
  
* Code
  * 
{% endtab %}
{% endtabs %}

## activeMouse\(boolean \_active) → boolean

> 마우스 동작 활성화 여부 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_active | boolean | 반경 |

* Detail
  * boolean : false - 마우스 동작 처리 비활성화, true \- 마우스 동작 처리 활성화 \(기본값\)
  
* Return
  * 설정 성공 \(true\) 혹은 실패 \(false\)
  
* Code
  * 
{% endtab %}
{% endtabs %}
