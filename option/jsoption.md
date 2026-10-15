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

### setTextureDrawLevel(level)

> 카메라 기준 몇 단계 LOD까지의 텍스처를 상주(메모리에 유지)시킬지 설정합니다. 기본값은 3입니다.
>
> 값을 낮추면 상주 텍스처 양이 줄어 메모리를 절약하지만, 멀리 있는 지형 텍스처가 더 일찍 사라집니다(화질과 메모리 사용량의 트레이드오프).

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                          |
| ----- | ------ | ---------------------------------------- |
| level | number | 상주 LOD 단계(0~5 범위로 clamp됨). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTextureDrawLevel() → number

> [setTextureDrawLevel(level)](jsoption.md#settexturedrawlevel-level)로 설정된 상주 LOD 단계를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 현재 설정된 상주 LOD 단계.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTextureUsedSize() → number

> 현재 GPU 텍스처 사용량을 반환합니다(진단용). 지형/건물 등 타일 텍스처와 POI 라벨 등 UI 텍스처를 합한 전체 사용량입니다(전체 = 타일 + UI).
>
> 텍스처 예산 판정에 쓰이는 타일 전용 사용량은 getTileTextureUsedSize(), UI 텍스처만의 사용량은 getUiTextureUsedSize()로 각각 확인할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 현재 텍스처 전체 사용량(byte 단위, 타일 + UI).
    -   0: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTileTextureUsedSize() → number

> 타일 텍스처(지형, 건물 등)의 현재 GPU 사용량을 반환합니다(진단용). POI 라벨 등 UI 텍스처는 제외되며, 텍스처 예산([setTexturePoolSize(size)](jsoption.md#settexturepoolsize-size-boolean)) 초과 여부를 판정할 때 실제로 사용되는 값입니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 타일 텍스처 사용량(byte 단위).

{% endtab %}
{% tab title="Template" %}

```javascript
var tileSize = Module.getOption().getTileTextureUsedSize();
var budget = Module.getOption().getTexturePoolSize();
```

{% endtab %}
{% endtabs %}

### getUiTextureUsedSize() → number

> POI 라벨 등 UI 텍스처만의 현재 GPU 사용량을 반환합니다(진단용). 타일 텍스처는 제외됩니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: UI 텍스처 사용량(byte 단위).

{% endtab %}
{% tab title="Template" %}

```javascript
var uiSize = Module.getOption().getUiTextureUsedSize();
```

{% endtab %}
{% endtabs %}

### getTexturePoolSize() → number

> [setTexturePoolSize(size)](jsoption.md#settexturepoolsize-size-boolean)로 설정된 텍스처 예산(byte)을 반환합니다(진단용).

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 텍스처 예산(byte 단위).
    -   0: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setMaxTextureDecodePerFrame(size), getMaxTextureDecodePerFrame() → number

> 한 프레임에 디코드할 수 있는 최대 텍스처 개수를 설정하여, 텍스처 디코드 부하를 여러 프레임에 걸쳐 분산시킵니다.
>
> 아이폰 등 일부 환경에서 텍스처/건물팩 디코드가 몰릴 때 발생하는 화면 프리징 대응 기능입니다. 기본값은 -1(기능 꺼짐, 기존과 동일하게 즉시 처리)입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                |
| ---- | ------ | -------------------------------------------------------------- |
| size | number | <p>-1: 기능 비활성화(기본값, 즉시 처리).<br>0 이상: 프레임당 처리할 최대 개수(부하 분산 활성화).</p> |

-   Return(getMaxTextureDecodePerFrame)
    -   number: 현재 설정된 프레임당 최대 디코드 개수.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setMaxTextureDecodePerFrame(2);
var count = Module.getOption().getMaxTextureDecodePerFrame();
```

{% endtab %}
{% endtabs %}

### setMaxReal3DPackDecodePerFrame(size), getMaxReal3DPackDecodePerFrame() → number

> 한 프레임에 디코드할 수 있는 최대 Real3D 건물팩 개수를 설정하여, 디코드 부하를 여러 프레임에 걸쳐 분산시킵니다.
>
> 기본값은 -1(기능 꺼짐, 기존과 동일하게 즉시 처리)입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                |
| ---- | ------ | -------------------------------------------------------------- |
| size | number | <p>-1: 기능 비활성화(기본값, 즉시 처리).<br>0 이상: 프레임당 처리할 최대 개수(부하 분산 활성화).</p> |

-   Return(getMaxReal3DPackDecodePerFrame)
    -   number: 현재 설정된 프레임당 최대 디코드 개수.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setMaxReal3DPackDecodePerFrame(2);
var count = Module.getOption().getMaxReal3DPackDecodePerFrame();
```

{% endtab %}
{% endtabs %}

### getMax3DTilesApplyPerFrame(), setMax3DTilesApplyPerFrame(count) → number

> 웹 워커가 파싱을 마친 3D Tiles 타일을 한 프레임에 최대 몇 개까지 객체로 적용할지(건수 상한)를 설정합니다. 기본값은 64입니다.
>
> 실질적인 적용 예산은 시간 기준인 [setMax3DTilesApplyMsPerFrame(ms)](jsoption.md#getmax3dtilesapplymsperframe-setmax3dtilesapplymsperframe-ms-number)이며, 이 값은 안전 상한 역할을 합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                        |
| ----- | ------ | -------------------------------------------------- |
| count | number | 프레임당 최대 적용 건수. 1 미만의 값은 1로 설정됩니다. |

-   Return(getMax3DTilesApplyPerFrame)
    -   number: 현재 설정된 프레임당 최대 적용 건수.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setMax3DTilesApplyPerFrame(32);
var count = Module.getOption().getMax3DTilesApplyPerFrame();
```

{% endtab %}
{% endtabs %}

### getMax3DTilesApplyMsPerFrame(), setMax3DTilesApplyMsPerFrame(ms) → number

> 워커가 파싱을 마친 3D Tiles 타일을 한 프레임에 적용하는 데 쓸 수 있는 시간 예산(ms)을 설정합니다. 기본값은 6.0입니다.
>
> 한 프레임에서 이 시간을 넘기면 적용을 중단하고 남은 타일은 다음 프레임에 처리하며, 최소 1건은 반드시 적용합니다. 지도 이동 중에는 예산이 절반으로 줄고, 적용 대기 중인 타일이 32개를 넘으면 2배, 128개를 넘으면 다시 2배로 늘어납니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                        |
| ---- | ------ | -------------------------------------------------- |
| ms   | number | 프레임당 적용 시간 예산(ms). 0.5 미만의 값은 0.5로 설정됩니다. |

-   Return(getMax3DTilesApplyMsPerFrame)
    -   number: 현재 설정된 프레임당 적용 시간 예산(ms).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setMax3DTilesApplyMsPerFrame(4.0);
var ms = Module.getOption().getMax3DTilesApplyMsPerFrame();
```

{% endtab %}
{% endtabs %}

### getMaxTileParseQueue(), setMaxTileParseQueue(count) → number

> 3D Tiles 파싱 워커 대기열(워커에서 파싱 중이거나 적용 대기 중인 타일)의 최대 건수를 설정합니다. 기본값은 256입니다.
>
> 대기열이 상한에 도달하면 이후 도착한 타일은 워커로 보내지 않고 메인 스레드에서 동기 파싱합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                                       |
| ----- | ------ | --------------------------------------------------------------------------------- |
| count | number | <p>대기열 최대 건수.<br>0: 건수 제한 없음.<br>음수: 무시되며 기존 값이 유지됩니다.</p> |

-   Return(getMaxTileParseQueue)
    -   number: 현재 설정된 대기열 최대 건수.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setMaxTileParseQueue(128);
var count = Module.getOption().getMaxTileParseQueue();
```

{% endtab %}
{% endtabs %}

### getMaxTileParseQueueMB(), setMaxTileParseQueueMB(size) → number

> 3D Tiles 파싱 워커 응답을 기다리는 동안 메인 스레드가 보관 중인 원본 데이터의 최대 크기(MB)를 설정합니다. 기본값은 96입니다.
>
> 이 예산을 초과하는 타일은 워커로 보내지 않고 메인 스레드에서 동기 파싱합니다. [setMaxTileParseQueue(count)](jsoption.md#getmaxtileparsequeue-setmaxtileparsequeue-count-number)의 건수 상한과 별개로 동작하며, 둘 중 하나라도 초과하면 동기 파싱합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                                       |
| ---- | ------ | --------------------------------------------------------------------------------- |
| size | number | <p>보관 예산(MB).<br>0: 크기 제한 없음.<br>음수: 무시되며 기존 값이 유지됩니다.</p> |

-   Return(getMaxTileParseQueueMB)
    -   number: 현재 설정된 보관 예산(MB).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setMaxTileParseQueueMB(64);
var size = Module.getOption().getMaxTileParseQueueMB();
```

{% endtab %}
{% endtabs %}

### getPolyTriangulateMinVertex(), setPolyTriangulateMinVertex(count) → number

> 폴리곤 삼각분할을 web worker로 보낼 최소 정점 수를 설정합니다. 기본값은 512입니다.
>
> [JSPolygon](../object/jspolygon.md)으로 평면·각기둥 등을 만들 때 정점 수(여러 파트를 한 번에 만드는 경우는 정점 합계)가 이 값 이상이면 삼각분할을 web worker에서 비동기로 처리하고, 미만이면 종전처럼 그 자리에서 동기로 처리합니다. 비동기로 처리하는 동안 해당 폴리곤의 면은 아직 만들어지지 않아 렌더링과 피킹에서 제외되며, 결과가 적용되면 나타납니다. 이동·UV 지정처럼 정점을 직접 읽거나 바꾸는 작업을 하면 대기 중인 요청을 그 자리에서 동기로 끝낸 뒤 진행합니다.
>
> web worker를 쓰지 않는 경우(`worker.use`가 false이거나 `worker.polyTriangulate`가 false이거나 worker가 없는 경우), 처리 중·적용 대기 요청이 64건 이상인 경우, worker가 30초 안에 응답하지 않은 경우에는 정점 수와 관계없이 동기로 처리합니다. 변경한 값은 이후에 만드는 폴리곤부터 적용됩니다. 처리 현황은 [XDEGetPolyTriangulateStats](../module/moduleapi.md#xdegetpolytriangulatestats-object)로 확인합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                  |
| ----- | ------ | ------------------------------------------------------------ |
| count | number | 워커로 보낼 최소 정점 수. 3 미만의 값은 3으로 설정됩니다. |

-   Return(getPolyTriangulateMinVertex)
    -   number: 현재 설정된 최소 정점 수.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setPolyTriangulateMinVertex(1000);
var count = Module.getOption().getPolyTriangulateMinVertex();
```

{% endtab %}
{% endtabs %}

### getMaxPolyApplyPerFrame(), setMaxPolyApplyPerFrame(count) → number

> 웹 워커가 삼각분할을 마친 폴리곤 결과를 한 프레임에 최대 몇 건까지 면에 적용할지 설정합니다. 기본값은 8입니다.
>
> 한 프레임에 적용하는 건수를 제한해 폴리곤이 한꺼번에 나타나면서 프레임이 끊기는 것을 막습니다. 남은 결과는 다음 프레임에 처리합니다. 지도를 이동(패닝) 중일 때는 이 값이 2보다 커도 프레임당 2건으로 제한됩니다. [setPolyTriangulateMinVertex(count)](jsoption.md#getpolytriangulateminvertex-setpolytriangulateminvertex-count-number)에 따라 워커로 보낸 폴리곤에만 해당합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                        |
| ----- | ------ | -------------------------------------------------- |
| count | number | 프레임당 최대 적용 건수. 1 미만의 값은 1로 설정됩니다. |

-   Return(getMaxPolyApplyPerFrame)
    -   number: 현재 설정된 프레임당 최대 적용 건수.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setMaxPolyApplyPerFrame(4);
var count = Module.getOption().getMaxPolyApplyPerFrame();
```

{% endtab %}
{% endtabs %}

### getMaxTilesRetainedMB(), setMaxTilesRetainedMB(size) → number

> 3D Tiles가 메모리에 보유하는 타일 콘텐츠(정점, 인덱스, 텍스처 원본)의 총 크기 상한(MB)을 설정합니다. 기본값은 512입니다.
>
> 보유량이 상한을 넘으면 최근에 그려지지 않은 타일부터 콘텐츠를 해제합니다. 해제된 타일은 다시 필요해질 때 재요청됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                                 |
| ---- | ------ | --------------------------------------------------------------------------- |
| size | number | <p>보유 상한(MB).<br>0: 상한 없음(해제하지 않음).<br>음수: 무시되며 기존 값이 유지됩니다.</p> |

-   Return(getMaxTilesRetainedMB)
    -   number: 현재 설정된 보유 상한(MB).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setMaxTilesRetainedMB(256);
var size = Module.getOption().getMaxTilesRetainedMB();
```

{% endtab %}
{% endtabs %}

### getTextureTranscodeTarget(), setTextureTranscodeTarget(target) → number

> KTX2 텍스처를 GPU 압축 포맷으로 트랜스코딩할 때의 타깃 포맷을 직접 지정합니다. 기본값은 브라우저/GPU가 지원하는 확장에 따라 엔진이 자동으로 선택한 값(BC7, ASTC, ETC2, BC3 순으로 우선, 모두 미지원 시 비압축 RGBA)입니다.
>
> 포맷에 따라 화질, 트랜스코딩 속도, 텍스처 메모리 사용량이 달라집니다. 화질/속도 우선 중 하나만 고르려면 [setTextureTranscodeMode(mode)](jsoption.md#gettexturetranscodemode-settexturetranscodemode-mode-string)를 사용하세요.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                                                                                                                                                                                                                        |
| ------ | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| target | number | <p>트랜스코딩 타깃 포맷 번호.<br>0: 자동 판정 값으로 복원.<br>1: ETC2 RGBA.<br>2: BC1(DXT1). 알파를 담지 못하므로 투명 텍스처의 투명도가 사라집니다(비교 측정용).<br>3: BC3(DXT5).<br>6: BC7.<br>10: ASTC 4x4.<br>13: 비압축 RGBA32.<br>그 외 값은 무시되며 기존 값이 유지됩니다.</p> |

-   Return(getTextureTranscodeTarget)
    -   number: 현재 적용 중인 타깃 포맷 번호.

{% endtab %}
{% tab title="Template" %}

```javascript
// BC3로 트랜스코딩(화질을 일부 낮추고 속도를 높임)
Module.getOption().setTextureTranscodeTarget(3);
var target = Module.getOption().getTextureTranscodeTarget();

// 자동 판정 값으로 복원
Module.getOption().setTextureTranscodeTarget(0);
```

{% endtab %}
{% endtabs %}

### getTextureTranscodeMode(), setTextureTranscodeMode(mode) → string

> KTX2 텍스처 트랜스코딩을 화질 우선 또는 속도 우선으로 선택합니다. 기기가 지원하는 포맷은 엔진이 이미 판정해 두었으므로 포맷 번호를 알 필요 없이 둘 중 하나만 고르면 됩니다.
>
> 반환값은 설정 후 실제로 적용된 모드입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                                                                                                                                       |
| ---- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| mode | string | <p>트랜스코딩 모드.<br>"quality": 화질 우선(기본값). 자동 판정된 최적 포맷을 사용합니다.<br>"auto": "quality"와 동일.<br>"speed": 속도 우선. 트랜스코딩이 가장 저렴한 포맷(ETC2, BC3, ASTC, BC7 순)을 사용합니다.<br>그 외 문자열 또는 문자열이 아닌 값은 무시되며 현재 모드가 반환됩니다.</p> |

-   Return(getTextureTranscodeMode, setTextureTranscodeMode)
    -   "quality": 화질 우선 포맷이 적용 중인 경우.
    -   "speed": 속도 우선 포맷이 적용 중인 경우.
    -   "custom": [setTextureTranscodeTarget(target)](jsoption.md#gettexturetranscodetarget-settexturetranscodetarget-target-number)으로 포맷을 직접 지정한 경우.

> 기기가 지원하는 속도 우선 포맷과 화질 우선 포맷이 같으면 "speed"를 설정해도 "quality"가 반환됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var mode = Module.getOption().setTextureTranscodeMode("speed");
console.log(mode, Module.getOption().getTextureTranscodeMode());
```

{% endtab %}
{% endtabs %}

### getTextureOpaqueOptimize(), setTextureOpaqueOptimize(use) → boolean

> 알파(투명도)가 없는 텍스처를 절반 크기(4bpp)의 불투명 전용 포맷(BC1/DXT1)으로 트랜스코딩할지 설정합니다. 텍스처 메모리를 크게 줄일 수 있으며, 화질 저하는 소폭입니다.
>
> 불투명 전용 포맷을 지원하는 환경(S3TC를 지원하는 데스크탑 등)에서만 동작합니다. 지원하지 않는 환경에서는 true로 설정해도 적용되지 않으며 getTextureOpaqueOptimize()는 false를 반환합니다. 기본적으로는 지원 환경에서 켜져 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                                                   |
| ---- | ------- | --------------------------------------------------------------------------------------------- |
| use  | boolean | <p>true: 알파 없는 텍스처를 불투명 전용 포맷으로 변환(지원 환경 기본값).<br>false: 모든 텍스처를 알파 지원 포맷으로 처리.</p> |

-   Return(getTextureOpaqueOptimize)
    -   true: 불투명 최적화가 적용 중인 경우.
    -   false: 꺼져 있거나 지원하지 않는 환경인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setTextureOpaqueOptimize(false);
var use = Module.getOption().getTextureOpaqueOptimize();
```

{% endtab %}
{% endtabs %}

### getWebWorkerCount(), setWebWorkerCount(count) → number

> 웹 워커 풀의 목표 워커 수를 런타임에 조절합니다. 기본값은 5이며, 적용된 목표 수를 반환합니다.
>
> 워커 수를 늘리면 즉시 생성하고, 줄이면 작업 큐가 빈 워커부터 파괴합니다. 작업 중인 워커는 큐가 빌 때까지 남아 있으므로 줄이는 동안에는 목표 수(getWebWorkerCount)와 실제 동작 중인 워커 수([getWebWorkerActiveCount()](jsoption.md#getwebworkeractivecount-number))가 잠시 다를 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type             | Description                                                                                                                                                                                                              |
| ----- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| count | number \| string | <p>목표 워커 수.<br>숫자: 1 ~ 최대 워커 수([setWebWorkerMaxCount(max)](jsoption.md#getwebworkermaxcount-setwebworkermaxcount-max-number)) 범위로 조정됩니다.<br>"auto": 브라우저의 코어 수(hardwareConcurrency)에서 1을 뺀 값(최소 2)을 기준으로 하고, 장치 메모리(deviceMemory)를 알 수 있으면 GB당 2개(최소 2)를 넘지 않게 제한한 뒤 최대 워커 수 이하로 조정합니다.<br>그 외 문자열 또는 숫자가 아닌 값은 무시되며 현재 목표 수가 반환됩니다.</p> |

-   Return(getWebWorkerCount, setWebWorkerCount)
    -   number: 적용된(현재) 목표 워커 수.
    -   0: 웹 워커를 사용하지 않도록 설정된 경우(setWebWorkerCount에서 숫자 또는 "auto"를 전달했을 때).

{% endtab %}
{% tab title="Template" %}

```javascript
var applied = Module.getOption().setWebWorkerCount(4);
var auto = Module.getOption().setWebWorkerCount("auto");
var target = Module.getOption().getWebWorkerCount();
```

{% endtab %}
{% endtabs %}

### getWebWorkerActiveCount() → number

> 현재 실제로 살아 있는 웹 워커 수를 반환합니다(진단용). 워커 수를 줄이는 중에는 목표 수([getWebWorkerCount()](jsoption.md#getwebworkercount-setwebworkercount-count-number))보다 클 수 있습니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 현재 생성되어 있는 웹 워커 수.

{% endtab %}
{% tab title="Template" %}

```javascript
var active = Module.getOption().getWebWorkerActiveCount();
```

{% endtab %}
{% endtabs %}

### getWebWorkerMaxCount(), setWebWorkerMaxCount(max) → number

> 웹 워커 풀의 최대 워커 수(상한)를 설정합니다. 기본값은 8입니다. [setWebWorkerCount(count)](jsoption.md#getwebworkercount-setwebworkercount-count-number)의 숫자 지정, "auto", 그리고 대용량(16MB 초과) 작업용 임시 워커 생성 모두 이 값을 넘지 않습니다.
>
> 현재 목표 워커 수가 새 상한보다 크면 즉시 상한에 맞게 줄입니다. 적용된 상한을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                           |
| ---- | ------ | ------------------------------------- |
| max  | number | 최대 워커 수. 1 ~ 255 범위로 조정됩니다. |

-   Return(getWebWorkerMaxCount, setWebWorkerMaxCount)
    -   number: 적용된(현재) 최대 워커 수.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setWebWorkerMaxCount(12);
Module.getOption().setWebWorkerCount("auto");
var max = Module.getOption().getWebWorkerMaxCount();
```

{% endtab %}
{% endtabs %}

### setEnableWBOIT(enable)

> Weighted Blended OIT(순서 독립 투명도) 렌더링을 런타임에 켜거나 끕니다. 기본값은 false(기존 알파 블렌딩 방식)입니다.
>
> 하드웨어가 필요한 확장(EXT_color_buffer_float/half_float)을 지원하지 않으면 true로 설정해도 자동으로 기존 방식으로 대체됩니다. 현재 설정값을 조회하는 getter는 제공되지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                                                          |
| ------ | ------- | ------------------------------------------------------------------------------------ |
| enable | boolean | <p>true: Weighted Blended OIT 사용.<br>false: 기존 알파 블렌딩 사용(기본값).</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getOption().setEnableWBOIT(true);
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
