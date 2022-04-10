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