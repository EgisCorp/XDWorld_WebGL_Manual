---
description: 3차원 그래프 오브젝트 설정 및 수정 기능 API.
---

# JSBarGraph3D

> Module.createBarGraph3D API 생성.

```javascript
var object = Module.createBarGraph3D("ID");
```

### create(position, size) → boolean

> 3차원 그래프 오브젝트 생성.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 그래프 생성 경위도 위치. |
| size | JSSize3D | 그래프 크기. |

* Return
  * true : 오브젝트 생성 성공.
  * false : 오브젝트 생성 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
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

### insertColumn(name, label, color) → boolean

> 그래프 Column 정보 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | column 구분 명칭. |
| label | string | column 명칭 (그래프 하단부 표시). |
| color | [JSColor](../core/jscolor.md) | 그래프 바 색상. |

* Return
  * true : Column 추가 성공.
  * false : Column 추가 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insertRow(name, label) → boolean

> 그래프 Row 정보 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | Row 구분 명칭. |
| label | string | Row 이름 (그래프 하단부 표시). |

* Return
  * true : Row 추가 성공.
  * false : Row 추가 실패.
    
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setAnimationSpeed(speed) → boolean

> 그래프 바 상승 애니메이션 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| speed | number | 바 상승 애니메이션 속도 (0.1~1.0 사이 값 설정). |

* Return
  * true : 속도 설정 성공.
  * false : 속도 설정 실패.

* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setColumnTextBackgroundColor(key, color) → boolean

> 그래프 바 하단부 Column 라벨 배경 색상을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| key | string | 텍스트 색상을 변경하고자 하는 Column 키. |
| color | JSColor | 라벨 배경 색상. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var graph = Module.createBarGraph3D("Graph");
//...
var backgroundColor = new Module.JSColor(255, 255, 0);
graph.setColumnTextColor("Column0", backgroundColor);
```
{% endtab %}
{% endtabs %}

### setColumnTextColor(key, outColor, fillColor) → boolean

> 그래프 바 하단부 Column 라벨 배경 색상을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| key | string | 텍스트 색상을 변경하고자 하는 Column 키. |
| outColor | JSColor | 텍스트 외곽 색상. |
| fillColor | JSColor | 텍스트 채움 색상. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var graph = Module.createBarGraph3D("Graph");
//...
var outlineColor = new Module.JSColor(255, 255, 255);
var fillColor = new Module.JSColor(0, 0, 0);
graph.setColumnTextColor("Column0", outlineColor, fillColor);
```
{% endtab %}
{% endtabs %}

### setData(name, label, data) → boolean

> 지정한 Column, Row에 해당하는 그래프 데이터를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | column 구분 명칭. |
| label | string | Row 구분 명칭. |
| data | number | 그래프 데이터. |

* Return
  * true : 데이터 추가 성공.
  * false : 데이터 추가 실패.
    
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setUnitText(unit) → boolean

> 그래프 높이 축 단위 표시 텍스트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| unit | string | 단위 표시 텍스트. |

* Return
  * true : 단위 텍스트 설정 성공.
  * false : 단위 텍스트 설정 실패.
      
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setValueRange(min, max, value) → boolean

> 그래프 높이 축의 최소, 최대 값 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| min | number | 높이 축 최소 값. |
| max | number | 높이 축 최대 값. |
| value | number | 눈금 표시 간격. |

* Return
  * true : 크기 설정 성공.
  * false : 크기 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
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


