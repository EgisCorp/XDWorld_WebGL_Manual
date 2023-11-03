---
description: 3D 오브젝트 기본 클래스. 3D 오브젝트는 형태에 따라 여러 종류가 있으며, JSObject3D 객체는 3D 오브젝트 타입의 기본형입니다.
---

# JSObject

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
