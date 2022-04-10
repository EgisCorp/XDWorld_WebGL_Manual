---
description: 고스트 심볼 객체 생성 및 수정 기능 API.
---

# JSGhostSymbol

> Module.createGhostSymbol API 생성.

```javascript
var object = Module.createGhostSymbol("ID");
```

### setGhostSymbol(name) → boolean

> 고스트 심볼 맵에 등록된 객체 모델 지정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| name | string | 등록된 객체 명칭. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGhostSymbol 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPosition(position) → boolean

> 고스트 심볼 객체의 위치 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                                | Description |
| --------- | ----------------------------------- | -------- |
| position  | [JSVector3D](../core/jsvector3d.md) | 고스트 심볼 경위도 위치. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGhostSymbol 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setScale(scale) → boolean

> 고스트 심볼 객체의 크기 설정.
>
> scale(x,y,z) 입력 값은 0보다 큰값으로 설정.
>
> 크기 초기 설정 x,y,z(1,1,1).

{% tabs %}
{% tab title="Information" %}
| Name | Type                            | Description  |
| --------- | ------------------------------- | --------- |
| scale     | JSSize3D | 고스트 심볼 크기 설정. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGhostSymbol 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getPosition() → [JSVector3D](../core/jsvector3d.md)

> 고스트 심볼 객체의 경위도 위치 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSVector3D](../core/jsvector3d.md) : 고스트 심볼 중심 위치 반환 성공.
  * null : 좌표 반환 실패.
  
* Sample
  * function displayGhostSymbolProperties 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getScale() → JSSize3D

> 고스트 심볼 객체의 크기 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * JSSize3D : 고스트 심볼 크기(x,y,z) 반환 성공.
  * null : 크기 반환 실패.
  
* Sample
  * function displayGhostSymbolProperties 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getGhostSymbolMapKey() → string

> 고스트 심볼의 참조된 객체 명칭 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * string : 고스트 심볼의 참조된 객체 명칭 반환 성공.
  * null : 명칭 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setRotation(x, y, z) → boolean

> 고스트 심볼 객체 회전 각도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description    |
| --------- | ------ | ----------- |
| x         | number | X축 변경 회전 각도. |
| y         | number | Y축 변경 회전 각도. |
| z         | number | Z축 변경 회전 각도. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function setRotation 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getRotationX() → number

> 고스트 심볼 객체 X축 회전 각도 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * X축 회전 각도.
  
* Sample
  * function displayGhostSymbolProperties 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getRotationY() → number

> 고스트 심볼 객체 Y축 회전 각도 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * Y축 회전 각도.
  
* Sample
  * function displayGhostSymbolProperties 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getRotationZ() → number

> 고스트 심볼 객체 Z축 회전 각도 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * Z축 회전 각도.
  
* Sample
  * function displayGhostSymbolProperties 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setBasePoint(x, y, z) → boolean

> 고스트 심볼 중심 좌표를 기준으로 입력 값만큼 이동 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| x         | number | X축 이동 값(미터) |
| y         | number | Y축 이동 값(미터) |
| z         | number | Z축 이동 값(미터) |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function setBasePoint 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getBasePointX() → number

> 고스트 심볼 중심 좌표를 기준으로 X축으로 이동 값 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * X축 이동 값(미터).
  
* Sample
  * function displayGhostSymbolProperties 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getBasePointY() → number

> 고스트 심볼 중심 좌표를 기준으로 Y축으로 이동 값 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * Y축 이동 값(미터).
  
* Sample
  * function displayGhostSymbolProperties 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getBasePointZ() → number

> 고스트 심볼 중심 좌표를 기준으로 Z축으로 이동 값 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * Z축 이동 값(미터).
  
* Sample
  * function displayGhostSymbolProperties 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getOpacity() → number

> 객체 투명도를 반환합니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * 객체 투명도
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setOpacity(opacity)

> 객체 투명도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| opacity   | number | 객체 투명도 |

{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getColor() → [JSColor](../core/jscolor.md)

> 객체 색상을 반환합니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * 객체 색상
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setColor(color))

> 객체 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type                          | Description |
| --------- | ----------------------------- | -------- |
| color     | [JSColor](../core/jscolor.md) | 객체 색상  |

{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}
