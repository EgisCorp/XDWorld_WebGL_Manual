---
description: 라인 객체 생성 및 수정 기능 API.
---

# JSLineString

> Module.createLineString API 생성.

```javascript
var object = Module.createLineString("ID");
```

### createbyJson(option) → string

> 라인 객체를 생성.
>
> argument 변수로 라인 객체 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| option | [JSLineString.CreateOptions](jslinestring.md#jslinestring.createoptions) | 초기화 옵션 속성 정보 |
	
* Return
  * "success" : 생성 성공.
  * "error variable undefined null" : options 객체가 없음
  * 이 외 오류 원인을 포함한 에러 메시지
  
* Sample
  * function createLine 참조.
  * [샌드박스\_라인](http://sandbox.dtwincloud.com/code/main.do?id=object_line_Json)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setCoordinates(coordinates)

> 라인 객체를 생성.
>
> coordinates 구성 요소 개수&gt;3 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [Collection](../core/collection.md) | 라인 구성 경위도 좌표 목록. |

* Sample
  * function createPathLine 참조.
  * [샌드박스\_경로 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### SetDashType(dash) → boolean

> 줄선 간격 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| dash | number | 점선 간격 |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPartCoordinates(coordinates, parts)

> 라인 객체를 생성.
>
> coordinates 구성 요소 개수&gt;3 필수 설정.
>
> parts 구성요소가 개수&gt;0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 라인 구성 경위도 좌표 목록. |
| parts | [Collection](../core/collection.md) | 라인 구성 점정 개수 목록 |

* Sample
  * function createBufferPolygon 참조.
  * [샌드박스\_라인 버퍼링](http://sandbox.dtwincloud.com/code/main.do?id=object_line_buffering)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setStyle(style)

> JSPolyLineStyle 적용된 옵션으로 라인 스타일 변경.
> 
> 색상, 두께, 투명도 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| style | JSPolyLineStyle | 라인 스타일 설정 객체 |

* Sample
  * function createBufferPolygon 참조.
  * [샌드박스\_라인 버퍼링](http://sandbox.dtwincloud.com/code/main.do?id=object_line_buffering)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setUnionMode(type)

> 라인 가시화 옵션.
>
> 라인 지형 결합 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 기본 가시화.</p> |

* Sample
  * function createObjectToPathPosition 참조.
  * [샌드박스\_경로 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSLineString.CreateOptions

> 라인 객체 생성 옵션.

| Name     | Type                           | Attributes | Default | Description              |
| ------ | -------------------------------- | -------- | ----- | ---------------------- |
| coordinates | tag-list                    |            |         | 정점 관리 옵션.        |
| type | number (tag-list)  				| optional   | 0        | 라인 가시화 타입.     |
| skip  | number							| optional   | 1        | 애니메이션 디테일 옵션.  |
| width  | number 							| optional   | 1        | 라인 굵기 옵션.     |
| dash  | number							| optional   | 0        | 점선 간격 옵션.      |
| speed  | number							| optional   | 0       | 애니메이션 속도 옵션.   |
| union  | boolean						    | optional   | false   | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 기본 가시화.</p>. |
| depth  | boolean					        | optional   | true        | .               |
| color  | [JSColor](../core/jscolor.md) 	| optional   | JSColor(200, 255, 255, 255) | 라인 가시화 색상.      |