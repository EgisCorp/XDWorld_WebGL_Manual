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
| size | [JSSize3D](../core/jssize3d.md) | 그래프 크기. |

* Return
  * true : 오브젝트 생성 성공
  * false : 오브젝트 생성 실패
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insertColumn(id, label, color) → boolean

> 그래프 Column 정보 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| id | string | column 구분 명칭. |
| label | string | column 명칭 (그래프 하단부 표시). |
| color | [JSColor](../core/jscolor.md) | 그래프 바 색상. |

* Return
  * true : Column 추가 성공
  * false : Column 추가 실패
  
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insertRow(id, label) → boolean

> 그래프 Row 정보 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| rowKey | string | Row 구분 명칭. |
| rowLabel | string | Row 이름 (그래프 하단부 표시). |

* Return
  * true : Row 추가 성공
  * false : Row 추가 실패
    
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setData(columnID, rowID, data) → boolean

> 지정한 Column, Row에 해당하는 그래프 데이터를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| columnID | string | column 구분 명칭. |
| rowID | string | Row 구분 명칭. |
| data | number | 그래프 데이터. |

* Return
  * true : 데이터 추가 성공
  * false : 데이터 추가 실패
    
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
  * true : 단위 텍스트 설정 성공
  * false : 단위 텍스트 설정 실패
      
* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setValueRange(min, max, interval) → boolean

> 그래프 높이 축의 최소, 최대 값 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| min | number | 높이 축 최소 값. |
| max | number | 높이 축 최대 값. |
| interval | number | 눈금 표시 간격. |

* Return
  * true : 크기 설정 성공
  * false : 크기 설정 실패
  
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
  * true : 속도 설정 성공
  * false : 속도 설정 실패

* Sample
  * function createGraph 참조.
  * [샌드박스\_3D 막대 그래프](http://sandbox.dtwincloud.com/code/main.do?id=object_graph_bar_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}