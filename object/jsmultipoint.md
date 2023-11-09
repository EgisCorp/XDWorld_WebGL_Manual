---
description: 멀티 POI 생성 및 수정 기능 API.
---

# JSMultiPoint

> Module.createMultiPoint API 생성.

```javascript
var object = Module.createMultiPoint("ID");
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

### setMainPoint(name, position, icon) → boolean

> 멀티 포인트 객체 생성.
> 
> 중심 좌표로 가시화 메인 POI 생성.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 멀티 POI 객체 명칭. |
| position | [JSVector3D](../core/jsvector3d.md) | 멀티 POI 경위도 위치. |
| icon | JSIcon | 객체의 표출 아이콘. |
  
* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
  
* Sample
  * function initPage 참조.
  * [샌드박스\_멀티포인트](http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint)  
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setMainPointVisible(visible) → boolean

> Main POI의 출력 여부를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| visible | boolean | 출력 여부 설정.<br>true일 경우 출력, false일 경우 출력하지 않음.</br> |
  
* Return
  * true : 오브젝트 설정 성공.
  * false : 오브젝트가 존재하지 않는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
object.setMainPointVisible(true);  // Visible On
object.setMainPointVisible(false);  // Visible Off
```
{% endtab %}
{% endtabs %}

### setSpreadEffect(set) → boolean

> 카메라와 오브젝트 간 거리에 따라 Sub POI가 펼쳐져 보이는 효과를 on/off 설정.
> 
> Off 설정 시 Sub POI는 카메라 거리와 관계 없이 펼쳐 진 상태를 유지.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| set | boolean | 효과 on/off 설정.<br>true일 경우 on, false일 경우 off.</br> |
  
* Return
  * true : 오브젝트 설정 성공.
  * false : 오브젝트가 존재하지 않는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
object.setSpreadEffect(true);  // Effect On
object.setSpreadEffect(false);  // Effect Off
```
{% endtab %}
{% endtabs %}

### insertSubPoint(name, icon) → boolean

> 멀티 포인트 객체 추가.
> 
> 중신 좌표를 기준으로 시계 방향 순으로 자동 배치 되는 POI 추가.
>
> 객체의 키구성은 (메인 POI 명칭)#(입력받는 name)로 구성

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 멀티 POI 객체 명칭. |
| icon | JSIcon | 객체의 표출 아이콘. |
  
* Return
  * true : 객체 추가 성공.
  * false : 객체 추가 실패.
  
* Sample
  * function createSubPoints 참조.
  * [샌드박스\_멀티포인트](http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint)  
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setBar(color, altitude, width) → boolean

> 메인 POI 위치로 부터 지형을 연결하는 라인 생성.
> 
> altitude, width 단위는 미터.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| color | [JSColor](../core/jscolor.md) | 직선 가시화 색상 |
| altitude | number | 기둥의 시작 높이 |
| width | number | 기둥의 두께 |

* Return
  * true : 객체 추가 성공.
  * false : 객체 추가 실패.
  
* Sample
  * function createMultiPoint 참조.
  * [샌드박스\_멀티포인트](http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint)  
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
