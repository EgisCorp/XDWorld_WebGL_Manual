---
description: 포인트 그래프 객체 생성 및 수정 기능 API.
---

# CJSPointGraph

> Module.createPointGraph API 생성.

```javascript
var object = Module.createPointGraph("ID");
```

### create(position, size) → boolean

> 포인트 그래프를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 포인트 그래프 경위도 위치. |
| size | JSSize3D | 그래프 크기 |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_포인트 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_point)
{% endtab %}

{% tab title="Template" %}
```javascript
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

### insertData(x, y, z, value) → boolean

> 그래프 포인터 데이터 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| x | number | x축 위치. |
| y | number | y축 위치. |
| z | number | z축 위치. |
| value | number | 데이터 값. |

* Return
  * true : 객체 추가 성공.
  * false : 객체 추가 실패
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_포인트 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insertLegend(value, color) → boolean

> 그래프 범례에 대한 값, 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 범례 구간 값. |
| color | [JSColor](../core/jscolor.md) | 범례 색상 설정. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_포인트 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setAxisRange(axis, min, max, interval) → boolean

> 그래프의 x, y, z 축의 범위 및 눈금 표시 간격 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| axis | number | 축 타입(0 : X축, 1 : Y축, 2 : Z축). |
| min | number | 축 최소 값. |
| max | number | 축 최대 값. |
| interval | number | 그래프 눈금 표시 간격. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_포인트 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPointLineVisible(type) → boolean

> 포인트 그래프와 지형을 연결하는 라인 가시화 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 라인 가시화<br>false인 경우 기본 가시화.</p> |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_포인트 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_point)
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
