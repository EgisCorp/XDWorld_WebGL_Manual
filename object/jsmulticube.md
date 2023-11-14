---
description: MultiCube 생성 및 수정 기능 API. MultiCube는 여러 개의 Cube로 구성된 오브젝트.
---

# JSMultiCube

> Module.createMultiCube API 생성.

```javascript
var vPosition = new Module.JSVector3D(129.1292403, 35.1721634, 100.0);
var object = Module.createMultiCube("newObject", vPosition, false);
```

### addCube(key, size, count, angle, interval, fillColor, outLine, outLineColor)

> MultiCube 내 새로운 큐브를 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| key | string | 큐브 객체 키. |
| size | JSSize2D | 큐브 크기. |
| count | number | 큐브 각 수(n값 설정 시 n각형의 큐브 생성). |
| angle | number | 큐브 y축 회전 각도. |
| interval | number | 큐브 간 간격. |
| fillColor | JSColor | 채움 색상. |
| outLine | boolean | 외곽 라인 적용 여부. |
| outLineColor | JSColor | 외곽 라인 색상. |
{% endtab %}

{% tab title="Template" %}
```javascript
var size = new Module.JSSize2D(100.0, 200.0);
var fillColor = new Module.JSColor(255, 255, 255, 255);
var outlineColor = new Module.JSColor(255, 255, 0, 0);
object.addCube("newObject", size, 6, 30.0, 10.0, fillColor, true, outlineColor);
```
{% endtab %}
{% endtabs %}

### getCubeCount() → number

> MultiCube의 입력된 큐브 개수를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number(0 ~) : 입력된 큐브 개수 반환 성공.
  * number(-1) : MultiCube 내부의 컨테이너 오브젝트가 NULL인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var cubeCount = object.getCubeCount();
```
{% endtab %}
{% endtabs %}

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

### setRowSize(size)

> MultiCube의 가로 큐브 열 수를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| size | number | 가로 큐브 열 수. |
{% endtab %}

{% tab title="Template" %}
```javascript
object.setRowSize(3);
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
