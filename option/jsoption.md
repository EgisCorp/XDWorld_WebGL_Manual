---
description: 지도 환경 옵션 설정을 위한 API.
---

# JSOption

> Module.getOption API 생성.

```javascript
var math = Module.getOption();
```

### callBackAddPoint(event) → string

> 측정 기능 동작 시 마우스 클릭 콜백 등록.
> 
> 마우스 클릭 시 현재 위치지점, 이전 점과의 중점, 길이, 총 길이를 받는 function 연동.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| event | function | 측정 시 동작 예정 function. |

* Return
  * "success" : 측정 기능 동작 콜백 함수 등록 성공.
  * "error map load" : 오브젝트가 초기화 되지 않으므로 실패.
  * "error { callback } Undefined" : event 변수 Undefined 임으로 실패.
  * "error { callback } null" : event 변수 null 임으로 실패.
  * "error { callback } Type Mismatch" : event Type이 function이 아님으로 실패.
	
* Sample
  * function init 참조.
  * [샌드박스\_거리측정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_distance)
{% endtab %}
{% endtabs %}

### callBackCompletePoint(event) → string

> 측정 동작 시 마우스 측정 종료 콜백 등록.
> 
> 마우스 더블클릭 시 측정 오브젝트 키를 받는 function 연동.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| event | function | 측정 종료 시 동작 예정 function. |

* Return
  * "success" : 측정 기능 동작 콜백 함수 등록 성공.
  * "error map load" : 오브젝트가 초기화 되지 않으므로 실패.
  * "error { callback } Undefined" : event 변수 Undefined 임으로 실패.
  * "error { callback } null" : event 변수 null 임으로 실패.
  * "error { callback } Type Mismatch" : event Type이 function이 아님으로 실패.

* Sample
  * function init 참조.
  * [샌드박스\_거리측정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_distance)
{% endtab %}
{% endtabs %}

### SetAreaMeasurePolygonDepthBuffer(type) → boolean

> 면적 측정 동작 시 생성된 오브젝트 Depth Buffer 설정.
> 
> DepthBuffer 미 설정 시 오브젝트 겹침 시 z-fighting 현상 발생.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 WebGL Depth 미설정.<br>false인 경우 WebGL Depth 설정.</p> |

* Return
  * true : 설정 성공.
  * false : 설정 실패.  
    * 설정 실패 조건.
      * 지도 갱신이 안된 경우.

* Sample
  * function init 참조.
  * [샌드박스\_면적측정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_area)
{% endtab %}
{% endtabs %}

### SetDistanceMeasureLineDepthBuffer(type) → boolean

> 거리 측정 동작 시 생성된 오브젝트 Depth Buffer 설정.
> 
> DepthBuffer 미 설정 시 오브젝트 겹침 시 z-fighting 현상 발생.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 WebGL Depth 미설정.<br>false인 경우 WebGL Depth 설정.</p> |
	  
* Return
  * true : 설정 성공.
  * false : 설정 실패.  
    * 설정 실패 조건.
      * 지도 갱신이 안된 경우.
	
* function init 참조.
  * [샌드박스\_거리측정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_distance)
{% endtab %}
{% endtabs %}

### setSlideScreenCount(value) → boolean

> 화면 분할 설정.
> 
> value 입력값은 1(단일화면), 2(분할화면) 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 화면 갯수 설정. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.

* Sample
  * function setSplitScreen 참조.
  * [샌드박스\_화면 분할](http://sandbox.dtwincloud.com/code/main.do?id=effect_screen_split)
{% endtab %}
{% endtabs %}

### setTwoSlideScreenDivideRate(value) → boolean

> 화면 분활 비율 설정.
> 
> value 입력값은 0~1 사이 값으로 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| value | number | 분할 화면 비율 설정. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  
* Sample
  * function setSplitScreen 참조.
  * [샌드박스\_화면 분할](http://sandbox.dtwincloud.com/code/main.do?id=effect_screen_split)
{% endtab %}
{% endtabs %}

### setTwoSlideScreenLayerList(leftName, rightName) → number

> 화면 분활 비율 설정.
> 
> leftName 다중 레이어 설정 시 "1번레이어명칭,2번레이어명칭"으로 설정.
> 
> rightName 다중 레이어 설정 시 "1번레이어명칭,2번레이어명칭"으로 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| leftName | number | 왼쪽 화면에 가시화 레이어 설정. |
| rightName | number | 오른쪽 화면에 가시화 레이어 설정. |

* Return
  * result>0 : 왼쪽, 오른쪽 가시화 레이어 총 갯수 반환
  * result==0 : 가시화 레이어 없음
	
* Sample
  * function setSplitScreen 참조.
  * [샌드박스\_화면 분할](http://sandbox.dtwincloud.com/code/main.do?id=effect_screen_split)
{% endtab %}
{% endtabs %}