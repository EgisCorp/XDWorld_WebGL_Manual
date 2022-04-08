---
description: 지도 환경 옵션 설정을 위한 API
---

# JSOption

Module getOption API로 생성할 수 있습니다.

```javascript
var math = Module.getOption();
```

## callBackAddPoint\(function event \) → string

> 측정 기능 동작 시 마우스 클릭 콜백 등록.
> 
> 마우스 클릭 시 현재 위치지점, 이전 점과의 중점, 길이, 총 길이를 받는 function 연동

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| event | function | 측정 시 동작 예정 function |

* Detail
  * event : 개발자 생성 function.

* Return
  * 성공 : "success"
  * 실패
    * "error map load" : 오브젝트가 초기화 되지 않음.
    * "error { callback } Undefined" : event 변수 Undefined 일 경우.
	* "error { callback } null" : event 변수 null 일 경우.
	* "error { callback } Type Mismatch" : event Type이 function이 아닌 경우.
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_distance
{% endtab %}
{% endtabs %}

## callBackCompletePoint\(function event \) → string

> 측정 동작 시 마우스 측정 종료 콜백 등록.
> 
> 마우스 더블클릭 시 측정 오브젝트 키를 받는 function 연동

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| event | function | 측정 종료 시 동작 예정 function |

* Detail
  * event : 개발자 생성 function.

* Return
  * 성공 : "success"
  * 실패
    * "error map load" : 오브젝트가 초기화 되지 않음.
    * "error { callback } Undefined" : event 변수 Undefined 일 경우.
	* "error { callback } null" : event 변수 null 일 경우.
	* "error { callback } Type Mismatch" : event Type이 function이 아닌 경우.
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_distance
{% endtab %}
{% endtabs %}

## SetAreaMeasurePolygonDepthBuffer\(boolean depth \) → boolean

> 면적 측정 동작 시 생성된 오브젝트 Depth Buffer 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| depth | boolean | 면적 측정 오브젝트 GL\_DEPTH\_TEST 옵션 사용유무 |

* Detail
  * depth : DepthBuffer 설정 유무
      * TRUE : GL\_DEPTH\_TEST 미설정 (오브젝트 겸침 발생 가능)
      * FALSE : GL\_DEPTH\_TEST 설정
	  
* Return
  * 성공 : TRUE
  * 실패 : FALSE
	* depth 설정 실패 조건
	  * 지도 갱신이 안된 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_area
{% endtab %}
{% endtabs %}

## SetDistanceMeasureLineDepthBuffer\(boolean depth \) → boolean

> 거리 측정 동작 시 생성된 오브젝트 Depth Buffer 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| depth | boolean | 거리 측정 오브젝트 GL\_DEPTH\_TEST 옵션 사용유무 |

* Detail
  * depth : DepthBuffer 설정 유무
      * TRUE : GL\_DEPTH\_TEST 미설정 (오브젝트 겸침 발생 가능)
      * FALSE : GL\_DEPTH\_TEST 설정
	  
* Return
  * 성공 : TRUE
  * 실패 : FALSE
	* depth 설정 실패 조건
	  * 지도 갱신이 안된 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_measure_distance
{% endtab %}
{% endtabs %}

## setSlideScreenCount\(number screen \) → boolean

> 화면 분할 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| screen | number | 화면 갯수 설정. |

* Detail
  * screen : 화면 설정 갯수 범위는 1, 2로 구성.

* Return
  * 성공 : TRUE
  * 실패 : FALSE
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_screen_split
{% endtab %}
{% endtabs %}

## setTwoSlideScreenDivideRate\(number rate \) → boolean

> 화면 분활 비율 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| rate | number | 분할 화면 비율 설정. |

* Detail
  * rate : 0~1 사이 값으로 화면 비율 설정

* Return
  * 성공 : TRUE
  * 실패 : FALSE
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_screen_split
{% endtab %}
{% endtabs %}

## setTwoSlideScreenLayerList\(string left\_layername, string right\_layername \) → number

> 화면 분활 비율 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| left\_layername | number | 왼쪽 화면에 가시화 레이어 설정. |
| right\_layername | number | 오른쪽 화면에 가시화 레이어 설정. |

* Detail
  * left\_layername : 다중 레이어 설정시 "1번레이어명칭,2번레이어명칭"으로 설정
  * right\_layername : 다중 레이어 설정시 "1번레이어명칭,2번레이어명칭"으로 설정

* Return
  * result&gt;0 : 왼쪽, 오른쪽 가시화 레이어 총 갯수 반환
  * result&gt==0 : 가시화 레이어 없음
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_screen_split
{% endtab %}
{% endtabs %}