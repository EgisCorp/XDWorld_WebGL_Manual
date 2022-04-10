---
description: 아이콘 객체 등록 관리하는 API.
---

# JSSymbol

> Module.getSymbol API 생성.

```javascript
var symbol = Module.getSymbol();
```

### getIcon(name) → JSIcon

> JSSymbol 내부에 추가된 JSIcon 객체를 반환.

{% tabs %}
{% tab title="Name" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| name  | string | 등록된 객체 명칭.   |

* Return
  * JSIcon : JSIcon 객체 반환 성공.
  * null : 좌표 반환 실패.
    * 객체 반환 실패 조건
	  * name과 동일한 명칭을 가진 객체가 없는 경우
	
* Sample
  * function createPOI 참조.
  * [샌드박스\_높이측정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_altitude)
{% endtab %}

{% tab title="Template" %}
```javascript
var icon = Module.getSymbol.getIcon("Icon\_name");
```
{% endtab %}
{% endtabs %}

### insertIcon(name, data, width, height) → boolean

> JSSymbol 내부에 새로운 JSIcon 등록.
>
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터.
>
> width, height 이미지 실제 크기 입력( &gt;1 ).

{% tabs %}
{% tab title="Name" %}
| Name   | Type   | Description     |
| ----------- | ------ | ------------ |
| name  | string | 등록할 객체 명칭. |
| data | object | 이미지 바이너리 데이터. |
| width | number | 이미지의 너비. |
| height | number | 이미지의 높이. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 설정 실패 조건
	  * name과 동일한 명칭을 가진 객체가 존재하는 경우.
	  * data 값이 null 인 경우.
      * width, height &lt;0 인 경우
	  
* Sample
  * function createPOI 참조.
  * [샌드박스\_높이측정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_altitude)
{% endtab %}

{% tab title="Template" %}
```javascript
var canvas = document.createElement("canvas");
var ctx = canvas.getContext('2d');
...(canvas 내 이미지 렌더링)...
var data = ctx.getImageData(0, 0, canvas.width, canvas.height).data;
Module.getSymbol.insertIcon("Icon\_name", data, canvas.width, canvas.height);
```
{% endtab %}
{% endtabs %}

### deleteIcon(name) → boolean

> JSSymbol 내부에 존재하는 JSIcon 삭제.

{% tabs %}
{% tab title="Name" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| name  | string | 삭제할 등록 객체 명칭.  |

* Return
  * true : 객체 삭제 성공.
  * false : 객체 삭제 실패.
    * 객체 삭제 실패 조건
	  * name과 동일한 명칭을 가진 객체가 없는 경우
	  * 해당 JSIcon을 참조 받는 객체가 하나 이상 존재하는 경우.(참조 객체 텍스쳐 삭제 후 동작)
	  
* Sample
  * function clearAnalysis 참조.
  * [샌드박스\_높이측정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_altitude)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getSymbol.deleteIcon("Icon\_name");
```
{% endtab %}
{% endtabs %}
