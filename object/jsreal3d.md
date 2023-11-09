---
description: Real3D 오브젝트 생성 및 수정 기능 API.
---

# JSReal3D

> Module.createReal3D API 생성.

```javascript
var object = Module.createReal3D("ID");
```

### getId() → string

> 오브젝트의 Key를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 문자열(string) : 오브젝트의 Key 반환 성공.
  * 빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var strKey = object.getId();
```
{% endtab %}
{% endtabs %}

### setElevationSectionColor(elevation, color) → boolean

> 건물 층별 색상 리스트를 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| elevation | JSCollection | 고도 리스트. |
| color | JSCollection | 색상 리스트. |
  
* Return
  * true : 오브젝트 설정 성공.
  * false : 오브젝트 설정 실패.  
{% endtab %}

{% tab title="Template" %}
```javascript
var elevationList = new Module.Collection();
//.. 고도 값 추가 ..
var colorList = new Module.Collection();
//.. 색상 값 추가 ..
object.setElevationSectionColor(elevationList, colorList);
```
{% endtab %}
{% endtabs %}

### setFillColor(type, color) → boolean

> Real3D 오브젝트 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <br>true인 경우 심플렌더링 모드 색상 변경.<br>false인 경우 일반 모드 색상 변경.</br> |
| color | [JSColor](../core/jscolor.md) | 체움 색상 |
  
* Return
  * true : 오브젝트 설정 성공.
  * false : 오브젝트 설정 실패.  
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setShaderType(type) → boolean

> 건물 층별 색상 표시 방식을 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| type | number | 설정하고자 하는 출력 타입.<br>0 : 텍스쳐.</br><br>1 : 텍스쳐 + 색상</br><br>2 : 색상</br> |
  
* Return
  * true : 오브젝트 설정 성공.
  * false : 오브젝트 설정 실패.  
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
object.setShaderType(1);
{% endtabs %}

### setStyle(style) → boolean

> 건물의 스타일을 설정.
> 
> 현재는 건물 색상 스타일만 설정 가능.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| type | JSPolygonStyle | 설정하고자 하는 건물 스타일. |
  
* Return
  * true : 오브젝트 설정 성공.
  * false : 오브젝트 설정 실패.  
{% endtab %}
{% tab title="Template" %}
```javascript
var polyStyle = new Module.JSPolygonStyle();
polyStyle.setFill(true);
polyStyle.setFillColor(new Module.JSColor(255, 255, 0, 0));
...
object.setStyle(polyStyle);
```
{% endtab %}
object.setShaderType(1);
{% endtabs %}

### getFillColor() → [JSColor](../core/jscolor.md)

> Real3D 오브젝트 색상 반환.

{% tabs %}
{% tab title="Information" %}
  
* Return
  * [JSColor](../core/jscolor.md) : 오브젝트 색상 반환 성공.
  * null : 색상 반환 실패.  
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getPosition() → [JSVector3D](../core/jsvector3d.md)

> Real3D 오브젝트 중심 경위도 좌표 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSVector3D](../core/jsvector3d.md) : Real3D 오브젝트 중하단 중심 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getHeight() → number

> 3D 모델 자체 높이 값을 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * Real3D 오브젝트 높이값(미터) 반환 성공.  
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## Getter / Setter

### getDescription() → string

> 오브젝트의 설명에 대한 내용을 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 문자열(string) : 오브젝트 설명 문자열 반환 성공.
  * 빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var strDesc = object.getDescription();
```
{% endtab %}
{% endtabs %}

### setDescription(desc)

> 오브젝트의 설명에 대한 설명을 저장.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| desc | string | 오브젝트 설명 문자열. |
{% endtab %}

{% tab title="Template" %}
```javascript
object.setDescription('First Object.');
```
{% endtab %}
{% endtabs %}

### getName() → string

> 오브젝트의 이름을 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 문자열(string) : 오브젝트의 이름 반환 성공.
  * 빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var objName = object.getName();
```
{% endtab %}
{% endtabs %}

### setName(name)

> 오브젝트의 이름을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| name | string | 설정할 오브젝트 이름. |
{% endtab %}

{% tab title="Template" %}
```javascript
object.setName('MyObject');
```
{% endtab %}
{% endtabs %}

### getVisible() → number

> 오브젝트의 보기/숨김 여부를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * [옵션 설정 상수](../etc/type-list.md#navigation-visible-type-list) 반환.
  * 보기 : Module.JS\_VISIBLE\_ON
  * 숨김 : Module.JS\_VISIBLE\_OFF 에러 발생 : Module.JS\_SELECTABLE\_ERROR(오브젝트가 NULL인 경우)
{% endtab %}

{% tab title="Template" %}
```javascript
var objName = object.getName();
```
{% endtab %}
{% endtabs %}

### setVisible(visible)

> 오브젝트의 보기/숨김 여부를 설정.

{% tabs %}
{% tab title="Information" %}
| Name    | Type   | Description                                                                                                                                    |
| ------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| visible | number | <p><a href="../etc/type-list.md#navigation-visible-type-list">옵션 설정 상수</a>.<br>보기 : Module.JS_VISIBLE_ON<br>숨김 : Module.JS_VISIBLE_OFF<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
object.setVisible(Module.JS_VISIBLE_ON);
```
{% endtab %}
{% endtabs %}
