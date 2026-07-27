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
|reflect|number|오브젝트 반사 효과 맵 생성 여부|
|backgroundColor|JSColor|지도 기본 배경 색상|
|atmosphereRender|boolean|대기 렌더링 효과 사용 여부|
|selectColor|[JSColor](../core/jscolor.md)|오브젝트 선택 색상|
|limitFPS|number|프레임 제한 값 (FPS)|
|ping|any|엔진 ping 정보|

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

### setTextureCapacityLimit(limit)

> 텍스처 용량 제한 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                                  |
| ----- | ------- | -------------------------------------------- |
| limit | boolean | <p>true: 제한 사용<br>false: 제한 미사용</p> |

- Return  
  - 없음.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getOption().setTextureCapacityLimit(true);
// 또는
Module.getOption().setTextureCapacityLimit(false);
```
{% endtab %}
{% endtabs %}

### setAtmosphericSunriseTime(hour, minute)

> 대기 효과 적용 시 일출 시간을 설정합니다.
>
> 태양 위치 연산에 사용되며, 시각은 24시간제로 입력합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description       |
| ------ | ------ | ----------------- |
| hour   | number | 일출 시(hour). 0~23 |
| minute | number | 일출 분(minute). 0~59 |

- 유효하지 않은 시간 값은 무시됩니다.
- 대기광 효과가 활성화된 상태에서 적용됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
// 일출 시간을 오전 6시 30분으로 설정
Module.getOption().setAtmosphericSunriseTime(6, 30);
```
{% endtab %}
{% endtabs %}

### setAtmosphericSunsetTime(hour, minute)

> 대기 효과 적용 시 일몰 시간을 설정합니다.
>
> 태양 위치 연산에 사용되며, 시각은 24시간제로 입력합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description       |
| ------ | ------ | ----------------- |
| hour   | number | 일몰 시(hour). 0~23 |
| minute | number | 일몰 분(minute). 0~59 |

- 유효하지 않은 시간 값은 무시됩니다.
- 대기광 효과가 활성화된 상태에서 적용됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
// 일몰 시간을 오후 7시 15분으로 설정
Module.getOption().setAtmosphericSunsetTime(19, 15);
```
{% endtab %}
{% endtabs %}

### setAtmosphericTime(hour, minute)

> 대기 효과 적용 시 현재 시간을 설정하여 하늘 색상 변화를 조정합니다.
>
> 설정된 시간은 일출/일몰 및 하늘 색상 변화에 영향을 줍니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description          |
| ------ | ------ | -------------------- |
| hour   | number | 현재 시각(hour), 0~23 |
| minute | number | 현재 분(minute), 0~59 |

- 유효하지 않은 시간 값은 무시됩니다.
- 대기광 효과가 활성화된 상태에서 적용됩니다.
- 일출(`setAtmosphericSunriseTime`) / 일몰(`setAtmosphericSunsetTime`) 시간과 함께 사용하면 하늘 색상 전환 효과를 더 자연스럽게 조절할 수 있습니다.

{% endtab %}
{% tab title="Template" %}
```javascript
// 현재 시각을 오후 4시 30분으로 설정
Module.getOption().setAtmosphericTime(16, 30);
```
{% endtab %}
{% endtabs %}

### setTexturePoolSize(size) → boolean

> GPU 텍스처 풀 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ------------------------ |
| size | number | 텍스처 풀 크기 (byte 단위). |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setEventMouseMove(type)

> 마우스 이동 위치 이벤트(Fire_EventMouseMove) 발생 여부를 설정합니다.
>
> ※ 엔진 빌드 옵션 `_EVENT_MOUSE_CONTROL_`가 활성화된 경우에만 바인딩됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                              |
| ---- | ------- | ------------------------------------------------------------ |
| type | boolean | <p>true: 마우스 이동 위치 이벤트 발생.<br>false: 미발생.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFixedRenderPOI(type)

> POI 객체의 고정 렌더링(LOD 무관 항상 렌더링) 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                          |
| ---- | ------- | ------------------------------------------------------- |
| type | boolean | <p>true: 고정 렌더링.<br>false: 일반 LOD 렌더링.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setClickPointVisible(type) → boolean

> 마우스 클릭 지점(하얀색 구) 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                          |
| ---- | ------- | ------------------------------------------------------- |
| type | boolean | <p>true: 클릭 지점 표시.<br>false: 미표시.</p>       |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setMeasureDistancePointUnionTerrain(type)

> 거리 측정 시, 측정선이 지형 고도와 결합되도록 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                             |
| ---- | ------- | ---------------------------------------------------------- |
| type | boolean | <p>true: 지형 결합.<br>false: 지형 결합 미적용.</p>     |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPointsDepthBuffer(type) → boolean

> 포인트(점) 객체의 depth 사용 여부를 설정합니다.
>
> depth 미 설정 시 객체 겹침 시 z-fighting 현상이 발생합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                      |
| ---- | ------- | ----------------------------------------------------- |
| type | boolean | <p>true: depth 미설정.<br>false: depth 설정.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### callMouseModeChange(event) → string

> 마우스 동작 모드 변경 시 발생하는 콜백 함수를 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type     | Description  |
| ----- | -------- | ------------- |
| event | function | 콜백 함수.   |

-   Return
    -   "success": 등록 성공.
    -   "error map load": 지도가 초기화되지 않은 경우.
    -   그 외 문자열: 콜백 함수 유효성 오류 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTextureBias(bias)

> 텍스쳐 LOD Bias 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| bias | number | 텍스쳐 Bias 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setLightDirection(x, y, z)

> 광원 방향 벡터를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| x    | number | 광원 방향 벡터 x 값. |
| y    | number | 광원 방향 벡터 y 값. |
| z    | number | 광원 방향 벡터 z 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDisplayOptionOfTerrain(option)

> 지형 표현 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description       |
| ------ | ------ | ------------------ |
| option | number | 지형 표현 옵션 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDisplayOptionOfBuilding(option)

> 시설물(건물) 표현 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description           |
| ------ | ------ | ----------------------- |
| option | number | 시설물 표현 옵션 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDisplayOptionOfDebug(option)

> 디버그 표현 옵션을 설정합니다 (지형 RTT 갱신 및 타일 메쉬 재생성을 트리거함).

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description         |
| ------ | ------ | --------------------- |
| option | number | 디버그 표현 옵션 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### applyShaderCode(options) → object

> 지정한 셰이더 프로그램의 Vertex/Fragment 셰이더 코드를 런타임에 교체합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                          |
| ------- | ------ | ------------------------------------------------------------------------------------------------------- |
| options | object | `type`(셰이더 프로그램 명칭, 예: "Prog3D", "ProgTerrain" 등), `vs`(Vertex Shader 코드 문자열), `fs`(Fragment Shader 코드 문자열) 속성을 포함하는 옵션 객체. |

-   Return
    -   `.result`: API 성공 유무 (1: 성공, 0: 실패).
    -   `.name`: 동작 API 명칭.
    -   `.return`: "success" 또는 실패 사유 문자열. (컴파일 실패 시 `.result`에 컴파일 에러 로그가 담김.)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setIndexedDB(use)

> IndexedDB 캐시 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                    |
| ---- | ------- | ------------------------------------------------- |
| use  | boolean | <p>true: IndexedDB 사용.<br>false: 미사용.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setMaxIndexedDB(level)

> IndexedDB에 캐시할 최대 타일 레벨을 설정합니다 (최대 15).

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                      |
| ----- | ------ | ---------------------------------- |
| level | number | 캐시할 최대 레벨 (최대값 15로 제한). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setAnisotropy(use)

> 비등방성 필터링(Anisotropic Filtering) 적용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                     |
| ---- | ------- | --------------------------------------------------- |
| use  | boolean | <p>true: 비등방성 필터 적용.<br>false: 미적용.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setStereoView(set)

> 스테레오(양안) 뷰 모드를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                        |
| ---- | ------- | ------------------------------------------------------ |
| set  | boolean | <p>true: 스테레오 뷰 활성화.<br>false: 비활성화.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setMaxRequestTextureQueueSize(size)

> 텍스처(타일맵) 요청 시 동시에 처리할 최대 요청 개수를 설정합니다 (최대 20).

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                              |
| ---- | ------ | ------------------------------------------- |
| size | number | 동시에 처리할 텍스처 요청 최대 개수 (0 ~ 20). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### callBackAltDistance(event) → string

> 높이/거리/직선거리 측정 관련 콜백 함수를 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type     | Description  |
| ----- | -------- | ------------- |
| event | function | 콜백 함수.   |

-   Return
    -   "success": 등록 성공.
    -   "error map load": 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setMaxGeometricError(value)

> 3D Tiles 등 지형/타일의 최대 허용 기하 오차(Screen Space Error)를 설정합니다 (최소값 1.0).

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                  |
| ----- | ------ | ------------------------------ |
| value | number | 최대 허용 기하 오차 (최소값 1.0). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRequestOrderType(type)

> 타일/데이터 요청 순서 방식을 설정합니다 (0 또는 1, 범위를 벗어나면 0/1로 보정).

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description             |
| ---- | ------ | ------------------------- |
| type | number | 요청 순서 방식 (0 또는 1). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### _setDebugView(set)

> 디버그 뷰 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                     |
| ---- | ------- | --------------------------------------------------- |
| set  | boolean | <p>true: 디버그 뷰 표시.<br>false: 미표시.</p>   |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setUserInputPointAltitudeOffset(offset)

> 사용자 입력 지점(측정 등)의 고도 표시 오프셋 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                    |
| ------ | ------ | --------------------------------- |
| offset | number | 고도 오프셋 값 (meter 단위).   |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRenderSelectSilhouette(set)

> 오브젝트 선택 시 실루엣(외곽선) 렌더링 효과 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                       |
| ---- | ------- | ---------------------------------------------------- |
| set  | boolean | <p>true: 실루엣 효과 사용.<br>false: 미사용.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getCurrentBrowser() → string

> 현재 실행 중인 브라우저 종류를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 현재 브라우저 명칭.

{% endtab %}
{% tab title="Template" %}

```javascript
var browser = Module.getOption().getCurrentBrowser();
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getPickingCalculateType(), setPickingCalculateType(type) → boolean / number

> 오브젝트 선택(Picking) 처리 시 계산 방식을 설정하거나 반환합니다.
>
> 선택 가능한 방식은 다음과 같습니다:
>
> - `0`: Ray 방식 (기본값)
> - `1`: Color Map 방식

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                |
| ---- | ------ | ------------------------------------------ |
| type | number | <p>0: Ray 방식<br>1: Color Map 방식</p>     |

- Return (set)
  - true: 설정 성공
  - false: 지도 로드 실패 또는 설정 실패
- Return (get)
  - number: 현재 설정된 계산 방식.

{% endtab %}
{% tab title="Template" %}
```javascript
// Ray 기반 Picking 사용
Module.getOption().setPickingCalculateType(0);
var type = Module.getOption().getPickingCalculateType();
```
{% endtab %}
{% endtabs %}

### getMaxRequestTileMeshSize(), setMaxRequestTileMeshSize(size) → number

> 타일 메시 요청 시 동시에 처리할 최대 요청 개수를 설정하거나 반환합니다.
>
> 값이 0보다 작으면 0으로, 50보다 크면 50으로 자동 조정됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                              |
| ---- | ------ | ---------------------------------------- |
| size | number | 동시에 처리할 타일 메시 요청 최대 개수. |

- 설정 가능한 범위: 0 ~ 50
- Return (get)
  - number: 현재 설정된 최대 요청 개수.

{% endtab %}
{% tab title="Template" %}
```javascript
// 최대 20개까지 타일 메시 요청 처리
Module.getOption().setMaxRequestTileMeshSize(20);
var size = Module.getOption().getMaxRequestTileMeshSize();
```
{% endtab %}
{% endtabs %}

### getHybridRenderType(), setHybridRenderType(type) → number

> 하이브리드 렌더링 타입을 설정하거나 반환합니다 (0~3 범위를 벗어나면 0으로 보정되며, 레이어들의 하이브리드 상태가 초기화됩니다).

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description              |
| ---- | ------ | -------------------------- |
| type | number | 하이브리드 렌더링 타입 (0 ~ 3). |

- Return (get)
  - number: 현재 하이브리드 렌더링 타입.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setHybridRenderType(1);
var type = Module.getOption().getHybridRenderType();
```

{% endtab %}
{% endtabs %}

### getColorPolygonOffset(), setColorPolygonOffset(set) → boolean

> ColorPolygon 객체의 폴리곤 오프셋 사용 여부를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                       |
| ---- | ------- | ---------------------------------------------------- |
| set  | boolean | <p>true: 폴리곤 오프셋 사용.<br>false: 미사용.</p> |

- Return (get)
  - true: 폴리곤 오프셋 사용 중.
  - false: 미사용 중.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setColorPolygonOffset(true);
var use = Module.getOption().getColorPolygonOffset();
```

{% endtab %}
{% endtabs %}
