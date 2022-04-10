---
description: 포인트 객체 생성 및 수정 기능 API.
---

# JSPoint

> Module.createPoint API 생성.

```javascript
var object = Module.createPoint("ID");
```

### setFontStyle(name, size, weight, fill_color, outline_color) → boolean

> POI 텍스트 스타일 설정.
> 
> 폰트, 크기, 굵기, 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 폰트 이름 |
| size | number | 텍스트 크기 |
| weight | number | 텍스트 굵기 |
| fill_color | JSPolyLineStyle | 텍스트 색상 |
| outline_color | JSPolyLineStyle | 텍스트 외곽 색상 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPoint 참조.
  * [샌드박스\_경로 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setImage(data, width, height) → boolean

> POI 이미지를 설정.
> 
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터.
>
> width, height 이미지 실제 크기 입력( &gt;1 ).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| data | array | 이미지 픽셀 값 배열. |
| width | number | 이미지 너비. |
| height | number | 이미지 높이. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 생성 실패 조건
	  * data 값이 null 인 경우.
	  * width, height &lt;0 인 경우
	  
* Sample
  * function createPOI 참조.
  * [샌드박스\_POI](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPosition(position) → boolean

> POI 위치 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | POI 경위도 위치. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPOI 참조.
  * [샌드박스\_POI](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPositionLine(length, color) → boolean

> 지면과 수직한 라인을 지정한 길이만큼 보이도록 설정.
> 
> length 입력값&gt;0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| length | number | POI 수직 라인 길이. |
| color | [JSColor](../core/jscolor.md) | POI 수직 라인 색상. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 생성 실패 조건
	  * type&lt;0 값이 설졍 된 경우

* Sample
  * function createPOI 참조.
  * [샌드박스\_POI 라인](http://sandbox.dtwincloud.com/code/main.do?id=object_point_line)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setRenderToTerrainTexture(type) → boolean

> POI를 RTT 기반으로 지형에 그리도록 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 기본 가시화.</p> |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPOI 참조.
  * [샌드박스\_POI RTT](http://sandbox.dtwincloud.com/code/main.do?id=object_point_rtt)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setText(text) → boolean

> POI 기사화 텍스트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| text | string | POI 텍스트 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPOI 참조.
  * [샌드박스\_POI](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

