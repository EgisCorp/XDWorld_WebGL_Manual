---
description: 2차원 막대 그래프 객체 생성 및 설정 API.
---

# JSBarGraph

> Module.createBarGraph API 생성.

```javascript
var object = Module.createBarGraph("ID");
```

### create(position, size, type) → boolean

> 2차원 막대 그래프 객체 생성.
> 
> type 입력 값에 따른 가시화 변경 0(가로 그래프 형태), 1(세로 그래프 형태).

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 그래프 경위도 위치(중하단 기준점). |
| size | [JSSize2D](../core/jssize2d.md) | 그래프 크기(너비, 높이 설정). |
| type | number | 그래프 타입 설정 |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.  

* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setValueRange(min, max, interval) → boolean

> 그래프 Y축 범위를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| min | number | 그래프 Y축 최소 값. |
| max | number | 그래프 Y축 최대 값. |
| interval | number | 그래프 격자 간격. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setAnimationSpeed(speed) → boolean

> 그래프 애니메이션 실행 속도를 설정합니다.
> 
> speed 입력값은 0.1 ~ 1.0 사이 값을 가지며 1.0 가까울 수록 빠르게 재생.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| speed | number | 그래프 애니메이션 실행 속도 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFloorColor(color) → boolean

> 그래프 바닥 평면 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| color | [JSColor](../core/jscolor.md) | 색상 값. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setLegendBoxSize(size) → boolean

> 범례 색상 표시 박스 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| size | [JSSize3D](../core/jssize3d.md) | 박스 크기. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
      
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setUnitText(text) → boolean

> 그래프 Y축 단위 텍스트를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| text | string | 단위 텍스트. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
        
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setGridVisible(type) → boolean

> 그래프 Y축과 격자를 가시화 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 Y축 격자 가시화(RTT)<br>false인 경우 Y축 격자 숨김.</p>|

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insertLegend(name, label, color) → boolean

> 그래프 범례를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| name | string | 그래프 범례 그룹 명칭. |
| label | string | 그래프 범례 명칭. |
| color | [JSColor](../core/jscolor.md) | 그래프 범례 색상. |

* Return
  * true : 객체 추가 성공.
  * false : 객체 추가 실패.
         
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}

{% tab title="Template" %}
```javascript
var graph = Module.createBarGraph("Graph");
graph.insertLegend("Legend1", "가스", new Module.JSColor(200, 255, 0, 0));
graph.insertLegend("Legend2", "전기", new Module.JSColor(200, 255, 255, 0));
graph.insertLegend("Legend3", "수도", new Module.JSColor(200, 0, 0, 255));
graph.insertLegend("Legend4", "기타", new Module.JSColor(200, 255, 255, 255));
```
{% endtab %}
{% endtabs %}

### insertDataSet(name, data) → boolean

> 그래프 데이터 셋을 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| name | string | 데이터 셋 명칭 (그래프 하단 텍스트 출력).  |
| data | [Collection](../core/collection.md) | 데이터 값 리스트 (범례 추가 순서를 따르며, 범례와 1:1 대응). |

* Return
  * true : 객체 추가 성공.
  * false : 객체 추가 실패.
           
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}

{% tab title="Template" %}
```javascript
var graph = Module.createBarGraph("Graph");

var dataValue = [10.5, 50.1, 97.0, 11.6, 34.9];
var data = new Module.Collection();

for (var i=0, len=dataValue.length; i<len; i++) {
	data.add(dataValue[i]);
}
		
graph.insertDataSet("2010년", data);
```
{% endtab %}
{% endtabs %}

### setDataSetNameFont(name, font) → boolean

> 데이터 셋 이름 텍스트 폰트 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| name | string | 데이터 셋 이름. |
| font | string | 폰트 이름. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.

* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setDataSetNameTextSize(name, size) → boolean

> 데이터 셋 이름 텍스트 크기 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| name | string | 데이터 셋 이름. |
| size | number | 텍스트 크기. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.

* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setDataSetNameTextColor(name, textcolor, textOutlineColor) → boolean

> 데이터 셋 이름 텍스트 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| name | string | 데이터 셋 이름. |
| textcolor | [JSColor](../core/jscolor.md) | 텍스트 채움 색상. |
| textOutlineColor | [JSColor](../core/jscolor.md) | 텍스트 외곽 색상. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setDataSetNameInterval(interval) → boolean

> 그래프 화면과 필드 이름 텍스트 간 간격 설정.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| interval | number | 그래프 화면과 필드 이름 텍스트 간 간격. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFloorDepth(depth) → boolean

> 그래프 바닥 평면 세로방향 너비.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Description |
| :--- | :--- | :--- |
| depth | number | 그래프 바닥 평면 세로방향 너비.|

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.

* Sample
  * function createGraph 참조.
  * [샌드박스\_2D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_2d_stack)
  
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}