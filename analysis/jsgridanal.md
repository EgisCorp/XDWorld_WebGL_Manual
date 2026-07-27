---
description: 지도 내 물판 기능 설정을 위한 API입니다.
---

# JSGridAnal

> Module.getAnalysis().getGridAnal() API를 생성합니다.

```javascript
var object = Module.getAnalysis().getGridAnal();
```

## Properties

| Name              | Type    | Description                                    |
| ----------------- | ------- | ------------------------------------------------- |
| view_underground  | boolean | 지형 아래에 렌더링되는 레이어 표시 여부.        |

## Function

### objectClear()

> 그리드 분석의 가시화 객체만 삭제합니다 (분석 데이터 자체는 유지).

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### openMultipleGridDataURL(url, time, size, start, end, type, multipleCount, multipleIndex)

> openGridDataURL()의 다중 격자 병합 버전입니다. 여러 데이터를 하나의 격자로 병합해서 사용할 때 사용합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type   | Description                       |
| ------------- | ------ | ------------------------------------ |
| url           | string | 파일 주소.                         |
| time          | number | 분석 결과 데이터의 시계열 인덱스. |
| size          | number | Grid를 구성하는 Cell의 Byte 크기. |
| start         | number | 수집 데이터 Cell의 시작 Offset.   |
| end           | number | 수집 데이터 Cell의 종료 Offset.   |
| type          | number | 데이터 형식.                       |
| multipleCount | number | 병합할 데이터 총 개수.            |
| multipleIndex | number | 현재 데이터의 병합 순서 인덱스.   |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getAreaByAltitude(resolution, minLon, minLat, maxLon, maxLat, checkAltitude) → number

> 지정한 영역 내에서, 지형 고도가 기준 고도 이하인(바다 제외) 영역의 면적을 계산합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type   | Description                                     |
| ------------- | ------ | -------------------------------------------------- |
| resolution    | number | 계산 해상도(격자 간격, meter 단위).             |
| minLon        | number | 대상 영역 최소 경도.                              |
| minLat        | number | 대상 영역 최소 위도.                              |
| maxLon        | number | 대상 영역 최대 경도.                              |
| maxLat        | number | 대상 영역 최대 위도.                              |
| checkAltitude | number | 판정 기준 고도 (이 고도 이하이면서 0.2m 초과인 지형을 포함). |

-   Return
    -   number: 계산된 면적 (m²).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getEditAreaWindTerrainData(resolution) → string

> 현재 편집 영역의 지형 고도 데이터를 ESRI ASCII Grid(.asc) 형식 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description             |
| ---------- | ------ | -------------------------- |
| resolution | number | 격자 해상도 (meter 단위). |

-   Return
    -   string: ASCII Grid 형식의 지형 고도 데이터.
    -   빈 문자열: 데이터 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getEditAreaWindBuildingData(resolution, minLon, minLat, maxLon, maxLat) → string

> 지정한 영역 내 시설물(건물) 높이 데이터를 ESRI ASCII Grid(.asc) 형식 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description             |
| ---------- | ------ | -------------------------- |
| resolution | number | 격자 해상도 (meter 단위). |
| minLon     | number | 대상 영역 최소 경도.     |
| minLat     | number | 대상 영역 최소 위도.     |
| maxLon     | number | 대상 영역 최대 경도.     |
| maxLat     | number | 대상 영역 최대 위도.     |

-   Return
    -   string: ASCII Grid 형식의 건물 높이 데이터.
    -   빈 문자열: 데이터 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getEditAreaWindLandCoverMapData(resolution) → string

> 현재 편집 영역의 토지피복도 데이터를 ESRI ASCII Grid(.asc) 형식 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description             |
| ---------- | ------ | -------------------------- |
| resolution | number | 격자 해상도 (meter 단위). |

-   Return
    -   string: ASCII Grid 형식의 토지피복도 데이터.
    -   빈 문자열: 데이터 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setMouseCallback(callback)

> 그리드 분석 관련 마우스 업(mouse up) 이벤트 콜백을 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description   |
| -------- | -------- | -------------- |
| callback | function | 콜백 함수.    |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGridLineVisible(visible)

> 그리드 라인 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                    |
| ------- | ------- | -------------------------------------------------- |
| visible | boolean | <p>true: 그리드 라인 표시.<br>false: 미표시.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGridLineBaseAlt(altitude)

> 그리드 라인 표시 기준 고도(여백)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description   |
| -------- | ------ | -------------- |
| altitude | number | 기준 고도 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGridLineMaxDistance(distance)

> 그리드 라인이 표시되는 최대 거리를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description   |
| -------- | ------ | -------------- |
| distance | number | 최대 표시 거리. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setBaseAltitude(altitude)

> 그리드 분석 결과의 기준 고도(오프셋)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description   |
| -------- | ------ | -------------- |
| altitude | number | 기준 고도 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setLegendJSON(options) → boolean

> 그리드 분석 결과에 적용할 범례 색상을 JSON 옵션으로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                                                                                              |
| ------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| options | object | `legendMode`(0: 바람 범례, 1: 고정 범례), `legend`(모드에 따라 `val`/`color`(고정 범례) 또는 `wfcolor`/`wacolor`(바람 범례) 속성을 가지는 항목 배열) 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 설정 성공.
    -   false: `legendMode` 또는 `legend`가 없거나, `legend` 배열이 비어 있는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setLegendMode(mode)

> 그리드 분석 범례 표현 모드를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| mode | number | 범례 모드 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createRasterImgData(name, ptr, memSize, width, height, time) → boolean

> 메모리에 로드된 이미지 데이터를 사용해 2D Raster 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                            |
| ------- | ------ | ---------------------------------------------------------- |
| name    | string | 객체 고유 명칭.                                          |
| ptr     | number | 이미지 데이터가 위치한 메모리 포인터 주소.               |
| memSize | number | 이미지 데이터 크기 (byte 단위).                          |
| width   | number | 이미지 가로 크기 (0이면 격자의 가로 셀 수 사용).        |
| height  | number | 이미지 세로 크기 (0이면 격자의 세로 셀 수 사용).        |
| time    | number | 시계열 인덱스.                                           |

-   Return
    -   true: 생성 성공.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createPIGridDataJSON(options) → boolean

> Point/Image 기반 그리드(PIGrid) 데이터를 설정합니다. DEM 결합, 값 범위 등을 포함한 확장된 격자 생성 방식입니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                                                                                                       |
| ------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| options | object | `kind`(필수, 격자 그룹명), `cols`, `rows`(필수, 셀 개수), `llcorner`(필수, `projNum`,`pos`), `size`(필수, 셀 크기), `dem`(`size`,`data`), `range`(`min`,`max`), `callback`, `isLittleEndian` 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 설정 성공.
    -   false: 필수 항목이 누락되었거나 격자 객체 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPIGridValue(options) → boolean

> createPIGridDataJSON()으로 생성된 PIGrid의 현재/다음 시점 텍스처 데이터를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                          |
| ------- | ------ | --------------------------------------------------------------------------------------- |
| options | object | `current`(`length`,`data`: 메모리 포인터), `next`(`length`,`data`: 메모리 포인터) 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 설정 성공.
    -   false: PIGrid 객체가 없거나 필수 항목이 누락된 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clear()

> 모든 그리드 분석 결과를 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   function setWindRenderMode 참조.
    -   [Sandbox_Wind Representation](https://sandbox.egiscloud.com/code/main.do?id=effect_wind)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### openGridDataURL(url, time, size, start, end, type)

> 바이너리 격자 분석 결과 데이터를 URL 호출.
>
> 입력 변수값(time) 범위 0을 포함한 정수형 인덱스, 0-base 배열 번호 입니다.
>
> 입력 변수값(size) 범위 0보다 큰 정수형 byte 크기.
>
> 입력 변수값(start) 범위 각 셀의 시작 포인터부터 데이터를 읽기를 진행할 시작점 byte 오프셋.
>
> 입력 변수값(end) 범위 각셀의 시작 포인터부터 데이터를 읽기를 종료할 지점 byte 오프셋.
>
> 읽을 셀의 크기 = (end - start), 단위 byte.
>
> type 입력값에 따른 정보 0 (정수형 4 byte), 1(실수형 4 byte), 2(실수형 8 byte).

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                       |
| ----- | ------ | --------------------------------- |
| url   | string | 파일 주소.                        |
| time  | number | 분석 결과 데이터의 시계열 인덱스. |
| size  | number | Grid를 구성하는 Cell을 Byte 크기. |
| start | number | 수집 데이터 Cell의 시작 Offset.   |
| end   | number | 수집 데이터 Cell의 종료 Offset.   |
| type  | number | 데이터 형식.                      |

-   Return
    -   비동기 이벤트를 통한 결과 반환.
        -Fires_EventLoadDataFinish 이벤트를 통해 시계열 불러오기 완료.
-   Sample
    -   function setWindRenderMode 참조.
    -   [Sandbox_Wind Representation](https://sandbox.egiscloud.com/code/main.do?id=effect_wind)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setHRange(min, max)

> 분석 결과에 대한 그리드 가시화 범례를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| min  | number | 최소값.     |
| max  | number | 최대값.     |

-   Sample
    -   function cbLoad 참조.
    -   [Sandbox_Time Series Polygon](https://sandbox.egiscloud.com/code/main.do?id=effect_time_visualization)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createRasterData(name, time) → boolean

> 바이너리 격자 분석 결과 데이터를 지정한 시간 인덱스에 2D Raster 객체를 생성합니다.
>
> 입력 변수값(name)은 이전 키 값과 중복이 불가능합니다.
>
> 입력 변수값(time)은 0 이상의 정수형 시간 인덱스, setTimeRange API에서 입력된 값을 초과 시 불가능합니다.
>
> setLayerName API를 통해 등록된 레이어가 없을 경우 UserLayer에 추가됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description         |
| ---- | ------ | ------------------- |
| name | string | 객체 고유 명칭.     |
| time | number | 시계열 인덱스 번호. |

-   Return
    -   true : 생성 성공.
    -   false : 생성 실패.
-   Sample
    -   function cbLoad 참조.
    -   [Sandbox_Time Series Polygon](https://sandbox.egiscloud.com/code/main.do?id=effect_time_visualization)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createPlaneData(name) → boolean

> 바이너리 격자 분석 결과 데이터를 3D 애니메이션 평면 객체로 생성합니다.
>
> 입력 변수값(name)은 이전 키 값과 중복이 불가능합니다.
>
> 생성 시 기본적으로 시계열 인덱스가 0~최대 시계열수까지 진행으로 애니메이션 수행합니다..

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| name | string | 객체 고유 명칭. |

-   Return
    -   true : 생성 성공.
    -   false : 생성 실패.
-   Sample
    -   function cbLoad 참조.
    -   [Sandbox_Time Series Polygon](https://sandbox.egiscloud.com/code/main.do?id=effect_time_visualization)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createArrowData(time) → boolean

> 바이너리 격자 분석 결과 데이터를 지정한 시계열 인덱스에 3D 화살표 객체들로 생성합니다.
>
> time 입력값은 0 이상의 정수형 시간 인덱스, setTimeRange 값 이상 불가능합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description         |
| ---- | ------ | ------------------- |
| time | number | 시계열 인덱스 번호. |

-   Return
    -   true : 생성 성공.
    -   false : 생성 실패.
-   Sample
    -   function OnWindDataLoad 참조.
    -   [Sandbox_Wind Representation](https://sandbox.egiscloud.com/code/main.do?id=effect_wind)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTimeRange(time)

> 바이너리 격자 분석 결과 데이터의 시계열 총 수를 설정합니다.
>
> 입력 변수값(time)은 기본 6으로 1 이상의 정수값을 가진다.
>
> 설정 변경 바이너리 격자 분석 데이터 요청전에 적용이 필요하다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | ------------- |
| time | number | 시계월 총 수. |

-   Sample
    -   function setWindRenderMode 참조.
    -   [Sandbox_Wind Representation](https://sandbox.egiscloud.com/code/main.do?id=effect_wind)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setHRatio(ratio)

> 3D 애니메이션 평면 객체의 수치별 표현 되는 형상의 높이 배율을 조절합니다.
>
> 입력 변수값(ratio)은 평면 객체 생성 후 적용 가능하고 0 보다 큰 값을 가진다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | ------------- |
| ratio | number | 높이 배율 값. |

-   Sample
    -   function loadloadtimeDetailspolygon 참조.
    -   [Sandbox_Time Series Polygon](https://sandbox.egiscloud.com/code/main.do?id=effect_time_visualization)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTime(time)

> 3D 애니메이션 평면 객체의 시계열 인덱스를 재설정합니다.
>
> 입력 변수값(time) 범위 0을 포함한 정수형 인덱스, 0-base 배열 번호 입니다.
>
> 수치변경에 따른 시계열 애니메이션이 흐르면서 변동됩니다.(0 → 6 시 1,2,3,4,5 까지 흐름 이후 6으로 도달)

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description         |
| ---- | ------ | ------------------- |
| time | number | 시계열 인덱스 번호. |

-   Sample
    -   function setTime 참조.
    -   [Sandbox_Time Series Polygon](https://sandbox.egiscloud.com/code/main.do?id=effect_time_visualization)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTime() → number

> 3D 애니메이션 평면 객체의 현재 진행중인 시계열 인덱스를 반환합니다..

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 애니메이션 수행 중인 시계열 인덱스 정보.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearLegend()

> 설정된 범례 값을 초기화합니다.
>
> 2D Raster 객체 및 3D 애니메이션 평면 객체에 적용되는 격자 색상 범례를 초기화.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   function loadloadtimeDetailspolygon 참조.
    -   [Sandbox_Time Series Polygon](https://sandbox.egiscloud.com/code/main.do?id=effect_time_visualization)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addLegendColor(alpha, red, green, blue) → number

> 설정된 범례 목록에 새로운 범례 색상을 추가합니다.
>
> alpha, red, green, blue : ARGB, 0~255 정수형 색상 범위.
>
> 범례는 격자의 최소~최대값 기준으로 각 격자 값이 범례 리스트의 총수에 비례값으로 적용됩니다..

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | ------------- |
| alpha | number | 투명도.       |
| red   | number | Red 색상값.   |
| green | number | Green 색상값. |
| blue  | number | Blue 색상값.  |

-   Return
    -   number: 등록된 범례 목록의 수를 반환.
-   Sample
    -   function loadloadtimeDetailspolygon 참조.
    -   [Sandbox_Time Series Polygon](https://sandbox.egiscloud.com/code/main.do?id=effect_time_visualization)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### set3DArrowSizeRatio(ratio)

> 3D 화살표 객체의 화살표 크기 배율을 변경합니다.
>
> 입력 변수값(ratio)은 0 보다 큰값으로 격자의 크기값에 대한 배율로 크기가 설정된다.
>
> 3D 화살표 객체의 생성전에 미리 설정이 필요하다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description          |
| ----- | ------ | -------------------- |
| ratio | number | 3D 화살표 크기 배율. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### openGridDataJSON(options) → boolean

> 격자 결과 데이터를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                 | Description     |
| ------- | -------------------------------------------------------------------- | --------------- |
| options | [JSGridAnal.GridDataOption](jsgridanal.md#jsgridanal.griddataoption) | 격자 생성 정보. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   function loadDetailsData 참조.
    -   [Sandbox_Time Series Polygon](https://sandbox.egiscloud.com/code/main.do?id=effect_time_visualization)

{% endtab %}
{% tab title="Template" %}

```javascript
let json = {
    kind: "TestWind",
    timeIndex: 0,
    timeRange: 6,
    callback: cbLoadComple,
    cols: 400,
    rows: 400,
    llcorner: {
        projNum: 13,
        pos: [
            [_x1, _y1],
            [_x2, _y2],
        ],
    },
    size: 25,
    fMin: 1,
    fMax: 1500,
    data: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
};
```

{% endtab %}
{% endtabs %}

### setLayerName(name)

> 격자 분석 결과 데이터를 3D 지도 객체로 생성할 때 적용할 레이어 명칭입니다.
>
> 입력 변수값(name)과 지도에서 생성한 레이어 목록을 비교 후 동일한 레이어가 없다면 UserLayer에 객체를 생성합니다.
>
> 입력 변수값(name)과 지도에서 생성한 레이어 목록을 비교 후 동일한 레이어가 있다면 레이여 명칭과 동일한 레이어에 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                          |
| ---- | ------ | ------------------------------------ |
| name | string | 격자 분석 결과를 관리할 레이어 명칭. |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSGridAnal.GridDataOption

> 격자 데이터 요청 파라미터 목록.

| Name      | Type                                                                                             | Attributes | Default | Description                                    |
| --------- | ------------------------------------------------------------------------------------------------ | ---------- | ------- | ---------------------------------------------- |
| kind      | string                                                                                           |            |         | 격자 데이터 그룹명.                            |
| timeIndex | number                                                                                           |            |         | 격자데이터 시게열 인덱스 번호.                 |
| timeRange | number                                                                                           |            |         | 격자데이터 시계열 총수.                        |
| callback  | function                                                                                         | optional   |         | 격자데이터가 모두 로딩되면 발생하는 콜백 함수. |
| cols      | number                                                                                           |            |         | 격자의 가로 셀 총수.                           |
| rows      | number                                                                                           |            |         | 격자의 세로 셀 총수.                           |
| llcorner  | [JSGridAnal.GridDataOption.llcornerParam](jsgridanal.md#jsgridanal.griddataoption.llcornerparam) |            |         | 좌하단 공간 좌표 객체.                         |
| size      | number                                                                                           |            |         | 격자의 셀 가로,세로 크기 (meter 단위).         |
| fMin      | number                                                                                           |            |         | 격자 셀의 최소값.                              |
| fmax      | number                                                                                           |            |         | 격자 셀의 최대값.                              |
| data      | array(number)                                                                                    |            |         | 격자 셀의 데이터 베열.                         |

#### JSGridAnal.GridDataOption.llcornerParam

> 격자의 범위 영역 설정 파라미터.

| Name    | Type          | Attributes | Default | Description                                     |
| ------- | ------------- | ---------- | ------- | ----------------------------------------------- |
| projNum | number        |            |         | 좌표계 코드 번호                                |
| pos     | array(number) |            |         | 좌표 범위 배열 형식 [[minx, miny], [maxx, maxy] |
