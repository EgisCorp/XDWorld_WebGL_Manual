---
description: 3차원 그물형 격자 그래프 객체 생성 및 수정 기능 API.
---

# JSSurfaceGraph

Module createSurfaceGraph API로 생성할 수 있습니다.

```javascript
var object = Module.createSurfaceGraph("ID");
```

### create(position, size) → boolean

> 그래프를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 그물형 격자 그래프 경위도 좌표 위치. |
| size | JSSize3D | 그물형 격자 그래프 크기. |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_표면 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_surface)
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

### insertAxisPoint(axis, value) → boolean

> X, Y축의 눈금 값을 리스트 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| axis | number | 축 타입(0 : X축, 1 : Y축). |
| value | number | 눈금 값. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_표면 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_surface)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insertLegend(value, color) → boolean

> 범례 위치 값 및 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 범례 구간 값. |
| color | [JSColor](../core/jscolor.md) | 범례 색상. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_표면 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_surface)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setAnimationSpeed(speed) → boolean

> 3차원 그물형 격자 그래프 애니메이션 재생 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| speed | number | 바 상승 애니메이션 속도 (0.1~1.0 사이 값 설정) |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.

* Sample
  * function createGraph 참조.
  * [샌드박스\_표면 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_surface)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setData(x, y, value) → boolean

> 3차원 그물형 격자 그래프를 구성할 데이터 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| x | number | X축 눈금 값. |
| y | number | Y축 눈금 값. |
| value | number | 데이터. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_표면 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_surface)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setValueRange(min, max, interval) → boolean

> 3차원 그물형 격자 그래프 높이 축 범위 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| min | number | 축 최소 값. |
| max | number | 축 최대 값. |
| interval | number | 그래프 눈금 표시 간격 (0.0 이상의 값으로 입력). |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_표면 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_surface)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setUnitText(text) → boolean

> 3차원 그물형 격자 그래프 높이 축 단위 표시 텍스트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| text | string | 단위 표시 텍스트. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_표면 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_surface)
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
