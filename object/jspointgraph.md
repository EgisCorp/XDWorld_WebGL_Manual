---
description: 포인트 그래프 객체 생성 및 수정 기능 API.
---

# CJSPointGraph

> Module.createPointGraph API 생성.

```javascript
var object = Module.createPointGraph("ID");
```

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

### create(position, size) → boolean

> 포인트 그래프를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 포인트 그래프 경위도 위치. |
| size | [JSSize3D](../core/jssize3d.md) | 그래프 크기 |

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