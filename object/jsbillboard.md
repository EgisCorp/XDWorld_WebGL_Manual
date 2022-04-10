---
description: 평면으로 이루어진 빌보드 오브젝트 설정 및 수정 기능 API.
---

# CJSBillboard

> Module.createBillboard API 생성.

```javascript
var object = Module.createBillboard("ID");
```

### set(position, icon, width, height) → boolean

> 빌보드 객체 생성 옵션 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 빌보드 경위도 위치(중하단 기준).  |
| icon | JSIcon | 객체의 이미지 아이콘. |
| width | number | 객체의 가로 표현 크기(미터). |
| height | number | 객체의 세로 표현 크기(미터). |

* Return
  * true : 빌보드 옵션 설정 성공.
  * false : 빌보드 옵션 설정 실패.
  
* Sample
  * function createBillboard 참조..
  * [샌드박스\_빌보드](http://sandbox.dtwincloud.com/code/main.do?id=object_billboard_create)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setImage(position, data, width, height) → boolean

> 빌보드 객체 생성 옵션 설정
> 
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 빌보드 경위도 위치(중하단 기준). |
| data | object | 이미지 바이너리 데이터. |
| width | number | 이미지의 너비. |
| height | number | 이미지의 높이. |
  
* Return
  * true : 빌보드 옵션 설정 성공.
  * false : 빌보드 옵션 설정 실패.

* Sample
  * function createBillboard 참조..
  * [샌드박스\_빌보드 Text](http://sandbox.dtwincloud.com/code/main.do?id=object_billboard_create)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setSizeScale(x, y, z) → boolean

> 객체의 표현 배율 설정.
> 
> 각 항목은 0보다 큰 값으로 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| x | number | x축 배율. |
| y | number | y축 배율. |
| z | number | z축 배율. |
  
* Return
  * true : 빌보드 옵션 설정 성공.
  * false : 빌보드 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setSizeFix(type) → boolean

> 객체의 표현 크기를 고정 또는 가변 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 크기 고정 방식.<br>false인 경우 가변적 크기 변경 방식.</p> |
  
* Return
  * true : 빌보드 크기 옵션 설정 성공.
  * false : 빌보드 크기 옵션 설정 실패.
  
* Sample
  * function setBillboardFixSize 참조..
  * [샌드박스\_빌보드 크기 옵션](http://sandbox.dtwincloud.com/code/main.do?id=object_billboard_fix_size)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setRotationMode(type) → boolean

> 빌보드 객체의 표현 방향성을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 화면 정면 고정 방식.<br>false인 경우 좌우 고정, 상하 가변 회전 방식.</p> |

* Return
  * true : 빌보드 회전 옵션 설정 성공.
  * false : 빌보드 회전 옵션 설정 실패.
  
* Sample
  * function setBillboardRotationMode 참조..
  * [샌드박스\_빌보드 회전 옵션](http://sandbox.dtwincloud.com/code/main.do?id=object_billboard_rotation)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}