---
description: 지도 내 환경 옵션을 설정하기 위한 API 입니다.
---

# JSOption

> Module.getOption() API를 생성합니다

```javascript
var math = Module.getOption();
```

## Properties

| Name         | Type   | Description                                                                                                                                                    |
| ------------ | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| object_ahead | number | <p>화면 시야 기준 [JSPoint](../object/jspoint.md), HTMLObject 객체 앞 장해물(지형, 시설물) 존재 시 가시화 유무 설정.<br>0: 기본 가시화.<br>1: 장해물 판별.</p> |

## Funtion

### callBackAddPoint(event) → string

> 측정 기능(거리, 면적 등) 동작 시 마우스 클릭 이벤트에 발생하는 콜백 함수를 추가합니다.
>
> 입력 변수값(event)에서 선언된 매개 변수를 통해 입력된 위치, 이전 위치와의 거리, 총길이를 제공합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type     | Description |
| :---- | :------- | :---------- |
| event | function | 콜백 함수.  |

-   Return
    -   "success" : 추가 성공.
    -   "error map load" : 정상적으로 지도가 생성되지 못한 경우.
    -   "error { callback } Undefined" : 콜백 함수가 Undefined으로 입력된 경우.
    -   "error { callback } null" : 콜백 함수가 없는 경우.
    -   "error { callback } Type Mismatch" : 입력된 event가 function 타입이 아닌경우.
-   Sample
    -   the function init 참조.
    -   [Sandbox_Distance Measurement](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_distance)

{% endtab %}
{% tab title="Template" %}

```javascript
function addPoint(e) {
    console.log(e);
}

Module.getOption().callBackAddPoint(addPoint);
```

{% endtab %}
{% endtabs %}

### callBackCompletePoint(event) → string

> 측정 기능(거리, 면적 등) 종료 시 발생하는 콜백 함수를 추가합니다.
>
> 입력 변수값(event)에서 선언된 매개 변수를 통해 측정 객체의 고유 명칭을 제공합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type     | Description |
| :---- | :------- | :---------- |
| event | function | 콜백 함수.  |

-   Return
    -   "success" : 추가 성공.
    -   "error map load" : 정상적으로 지도가 생성되지 못한 경우.
    -   "error { callback } Undefined" : 콜백 함수가 Undefined으로 입력된 경우.
    -   "error { callback } null" : 콜백 함수가 없는 경우.
    -   "error { callback } Type Mismatch" : 입력된 event가 function 타입이 아닌경우.
-   Sample
    -   the function init 참조.
    -   [Sandbox_Distance Measurement](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_distance)

{% endtab %}
{% tab title="Template" %}

```javascript
function endPoint(e) {
    console.log(e);
}

Module.getOption().callBackCompletePoint(endPoint);
```

{% endtab %}
{% endtabs %}

### SetAreaMeasurePolygonDepthBuffer(type) → boolean

> 면적 측정 동작 시 생성된 객체의 depth 설정합니다.
>
> depth 미 설정 시 객체 겹침 시 z-fighting 현상 발생합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                      |
| :--- | :------ | :----------------------------------------------- |
| type | boolean | <p>true: depth 미설정.<br>false: depth 설정.</p> |

-   Return

    -   true : 설정 성공.
    -   false : 설정 실패.

-   Sample
    -   the function init 참조.
    -   [Sandbox_Area Measurement](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_area)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().SetAreaMeasurePolygonDepthBuffer(false);
// ... or ...
Module.getOption().SetAreaMeasurePolygonDepthBuffer(true);
```

{% endtab %}
{% endtabs %}

### SetDistanceMeasureLineDepthBuffer(type) → boolean

> 거리 측정 동작 시 생성된 객체의 depth 설정합니다.
>
> depth 미 설정 시 객체 겹침 시 z-fighting 현상 발생합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                      |
| :--- | :------ | :----------------------------------------------- |
| type | boolean | <p>true: depth 미설정.<br>false: depth 설정.</p> |

-   Return

    -   true : 설정 성공.
    -   false : 설정 실패.

-   Sample
    -   the function init 참조.
    -   [Sandbox_Distance Measurement](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_distance)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().SetDistanceMeasureLineDepthBuffer(false);
or;
Module.getOption().SetDistanceMeasureLineDepthBuffer(ture);
```

{% endtab %}
{% endtabs %}

### setSlideScreenCount(value) → boolean

> 화면 분할을 설정합니다.
>
> 입력 변수값(value)은 1(단일화면), 2(분할화면) 필수 설정.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description     |
| :---- | :----- | :-------------- |
| value | number | 화면 분활 갯수. |

-   Return

    -   true : 설정 성공.
    -   false : 설정 실패.

-   Sample
    -   the function setSplitScreen 참조.
    -   [Sandbox_Screen Split](https://sandbox.egiscloud.com/code/main.do?id=effect_screen_split)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setSlideScreenCount(1);
or;
Module.getOption().setSlideScreenCount(2);
```

{% endtab %}
{% endtabs %}

### setTwoSlideScreenDivideRate(value) → boolean

> 화면 분활 비율을 설정합니다.
>
> 입력 변수값(value)은 0~1 사이 값으로 설정합니다..

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description     |
| :---- | :----- | :-------------- |
| value | number | 화면 비율 설정. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   the function setSplitScreen 참조.
    -   [Sandbox_Screen Split](https://sandbox.egiscloud.com/code/main.do?id=effect_screen_split)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setTwoSlideScreenDivideRate(0~1);
```

{% endtab %}
{% endtabs %}

### setTwoSlideScreenLayerList(leftName, rightName) → number

> 분활된 화면에 대해 출력할 레이어를 설정합니다.
>
> 입력 변수값(leftName) 다중 레이어 설정 시 "레이어명칭(1st),레이어명칭(2st)"으로 설정합니다.
>
> 입력 변수값(rightName) 다중 레이어 설정 시 "레이어명칭(1st),레이어명칭(2st)"으로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                          |
| :-------- | :----- | :----------------------------------- |
| leftName  | number | 왼쪽 화면 가시화 레이어 명칭 목록.   |
| rightName | number | 오른쪽 화면 가시화 레이어 명칭 목록. |

-   Return
    -   result>0 : 설정된 레이어 총 갯수 반환.
    -   result==0 : 등록된 레이어 없음.
-   Sample
    -   the function setSplitScreen 참조.
    -   [Sandbox_Screen Split](https://sandbox.egiscloud.com/code/main.do?id=effect_screen_split)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setTwoSlideScreenLayerList("Left_Layer_1,Left_Layer_2", "Right_Layer_1");
```

{% endtab %}
{% endtabs %}
