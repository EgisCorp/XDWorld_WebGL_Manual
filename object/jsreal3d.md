---
description: Real3D 객체 생성 및 수정 기능 API.
---

# JSReal3D

> Module.createReal3D API 생성.

```javascript
var object = Module.createReal3D("ID");
```

### setFillColor(type, color) → boolean

> Real3D 객체 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 심플렌더링 모드 색상 변경.<br>false인 경우 일반 모드 색상 변경.</p> |
| color | [JSColor](../core/jscolor.md) | 체움 색상 |
  
* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.  
{% endtab %}
{% endtabs %}

### getFillColor() → [JSColor](../core/jscolor.md)

> Real3D 객체 색상 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * [JSColor](../core/jscolor.md) : 객체 색상 반환 성공.
  * null : 색상 반환 실패.  
{% endtab %}
{% endtabs %}

### getPosition() → [JSVector3D](../core/jsvector3d.md)

> Real3D 객체 중심 경위도 좌표 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSVector3D](../core/jsvector3d.md) : Real3D 객체 중하단 중심 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}
{% endtabs %}

### getHeight() → number

> 3D 모델 자체 높이 값을 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * Real3D 객체 높이값(미터) 반환 성공.  
{% endtab %}
{% endtabs %}