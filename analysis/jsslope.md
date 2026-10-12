---
description: 지도 내 지형의 경사 분석 기능 설정을 위한 API입니다.
---

# JSSlope

> Module.getSlope API를 생성합니다.

```javascript
var Slope = Module.getSlope();
```

## Function

### clearSlope(key) → boolean

> 지정한 키에 해당하는 단일 경사 분석 결과를 초기화(삭제) 합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                          |
| :--- | :----- | :------------------------------------- |
| key  | string | 삭제할 경사 분석 오브젝트 고유 명칭. |

-   Return
    -   true: 초기화 성공.
    -   false: key에 해당하는 분석 결과가 없거나, 결과가 등록된 레이어를 찾지 못한 경우.
-   Sample
    -   http://api.xdmap.com/Analysis/Slope/TerrainSlopeAngle

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getSlope().clearSlope(key);
```

{% endtab %}
{% endtabs %}

### clearAnalysisData()

> 모든 경사 분석 결과를 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   http://api.xdmap.com/Analysis/Slope/TerrainSlopeAngle

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getSlope().clearAnalysisData();
```

{% endtab %}
{% endtabs %}

### clearColorList() → boolean

> 분석 결과에 해당되는 범례 색상 목록을 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true : 초기화 성공.
    -   false : 초기화 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getSlope().clearColorList();
```

{% endtab %}
{% endtabs %}

### analysisTerrainSlope(options) → object

> 지형 경사(향/도/일사량/고도) 분석을 실행합니다.
>
> 분석 영역 좌표를 기준으로 격자를 생성하고, 결과 이미지가 생성되면 options.callback이 호출됩니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                    | Description        |
| :------ | :------------------------------------------------------- | :------------------- |
| options | [JSSlope.AnalysisOption](jsslope.md#jsslope.analysisoption) | 경사 분석 요청 옵션 객체. |

-   Return (object)
    -   성공: `{ result: 1, name: "JSSlope.analysisTerrainSlope" }`
    -   실패: `{ result: 0, name: "JSPolygon.createbyJson", return: "에러 메시지" }`
        -   지도 미로딩: `"Map Did Not Load."`
        -   options.callback 누락/타입 오류, info/coordinates/analysis/shape 태그 오류 시 각 항목에 대한 에러 메시지.
        -   좌표로 면(Face) 생성 실패: `"error coordinates { coordinate } Check => Can't Create Face"`
        -   고도(DEM) 데이터 획득 실패: `"error coordinates { coordinate } Check => Can't DEM"`

-   Sample
    -   http://api.xdmap.com/Analysis/Slope/TerrainSlopeAngle

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getSlope().analysisTerrainSlope({
    info: {
        layer: "SlopeLayer",
        key: "slope_001",
    },
    coordinates: {
        style: "XYZ",
        coordinate: [
            [127.001, 37.001, 0],
            [127.002, 37.001, 0],
            [127.002, 37.002, 0],
            [127.001, 37.002, 0],
        ],
    },
    analysis: {
        type: "TERRAIN_ANGLE",
        size: 4,
        image: true,
    },
    callback: function (result) {},
    progress: function (state) {},
});
```

{% endtab %}
{% endtabs %}

### checkServerDemAnalysis(options) → object

> 서버 DEM 기반 경사 분석(`analysis.server: true`)을 실행하기 전에, 분석에 필요한 DEM 타일 수와 분석 가능 여부를 미리 확인합니다. 분석은 실행하지 않으며 서버 요청도 보내지 않고 즉시(동기) 결과를 반환합니다.
>
> 입력 좌표의 경위도 범위(bbox)와 요청 레벨을 기준으로 타일 수를 계산하므로, 실제 분석 시 셀 격자 경계에 맞춰 영역이 한 셀 정도 커질 수 있어 타일 수는 추정값입니다(경계에서 한 행/열 차이가 날 수 있음).

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                            | Description              |
| :------ | :--------------------------------------------------------------- | :------------------------- |
| options | [JSSlope.CheckServerDemOption](jsslope.md#jsslope.checkserverdemoption) | 확인할 분석 영역과 서버 DEM 옵션 객체. |

-   Return (object)
    -   `result`: 1(분석 가능), 0(분석 불가).
    -   `name`: `"JSSlope.checkServerDemAnalysis"`.
    -   `level`: 분석에 사용될 DEM 레벨. `analysis.level`이 숫자이면 그 값, 미지정/`"max"`이면 지형 서비스 레벨이며 0 ~ 서비스 레벨 범위로 보정됩니다. 이전 분석에서 DEM 데이터가 실제로 존재하는 최대 레벨이 확인된 경우 그보다 높은 값은 확인된 레벨로 낮춰집니다.
    -   `serviceLevel`: 지형 서비스 레벨(지도 초기화 시 설정한 `info.servicelevel`).
    -   `resolved`: true이면 `level`이 DEM 데이터 레벨 탐색으로 확정된 값, false이면 요청 레벨 기준 추정값(한 번도 분석을 실행하지 않아 아직 탐색 전).
    -   `tile`: 필요한 DEM 타일 수(추정값).
    -   `tileBudget`: 타일 수 상한. `analysis.tileBudget`이 0보다 크면 그 값, 아니면 내부 최대값(65519).
    -   `spacing`: DEM 샘플 간격(meter, 위도 방향 기준).
    -   `allowedAreaSize`: 이 레벨에서 `tileBudget` 안에서 분석 가능한 정사각형 영역의 한 변 길이(meter).
    -   `downloadSize`: 분석 시 내려받을 DEM 데이터 크기(MB, 타일당 65x65x4byte로 계산).
    -   `return`: 안내/오류 메시지(해당하는 경우에만 포함).
        -   `"Terrain DEM format can not be sampled as a grid ( .terrain )"`: DEM 서비스가 quantized mesh(.terrain) 형식이라 서버 기반 분석이 불가능한 경우(`result`: 0).
        -   `"Analysis area is too large for the requested DEM level"`: 타일 수가 0이거나 `tileBudget`을 넘어 분석할 수 없는 경우(`result`: 0).
        -   `"DEM data level is not probed yet. tile count is an estimate based on the requested level"`: `result`는 1이지만 `resolved`가 false라서 타일 수가 추정값인 경우.
    -   실패(검사 이전 오류): `{ result: 0, name: "JSSlope.checkServerDemAnalysis", return: "에러 메시지" }`
        -   지도 미로딩: `"Map Did Not Load."`
        -   coordinates/analysis 태그 오류(좌표 3개 미만 포함) 시 각 항목에 대한 에러 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript
var check = Module.getSlope().checkServerDemAnalysis({
    coordinates: {
        style: "XYZ",
        coordinate: [
            [127.001, 37.001, 0],
            [127.002, 37.001, 0],
            [127.002, 37.002, 0],
            [127.001, 37.002, 0],
        ],
    },
    analysis: {
        server: true,
        level: "max",
        tileBudget: 100,
    },
});

if (check.result === 1) {
    console.log("level:", check.level, "tile:", check.tile, "download(MB):", check.downloadSize);
} else {
    console.warn(check.return, "허용 영역 한 변(m):", check.allowedAreaSize);
}
```

{% endtab %}
{% endtabs %}

### exportSlopeData(key) → string

> 지정한 키에 해당하는 경사 분석 결과를 JSON 문자열로 내보냅니다(info, coordinates, analysis, shape(형상 분석인 경우), color, output 항목 포함).

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                    |
| :--- | :----- | :-------------------------------- |
| key  | string | 내보낼 경사 분석 오브젝트 고유 명칭. |

-   Return
    -   string: 분석 정보 JSON 문자열.
    -   `"error NULL ObjKey"`: key에 해당하는 분석 결과를 찾지 못한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let json = Module.getSlope().exportSlopeData(key);
```

{% endtab %}
{% endtabs %}

### importSlopeData(options, callback, progress) → string

> exportSlopeData()로 얻은 형태와 동일한 JSON 옵션을 기반으로 경사 분석 결과를 다시 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                                    | Description                                   |
| :------- | :------------------------------------------------------- | :----------------------------------------------- |
| options  | [JSSlope.AnalysisOption](jsslope.md#jsslope.analysisoption) | 경사 분석 요청 옵션 객체(options.callback/progress는 사용되지 않으며, 별도의 callback/progress 인자가 사용됩니다). |
| callback | function                                                 | 분석 결과 이미지 생성이 완료되면 호출되는 콜백 함수(필수). |
| progress | function                                                 | 분석 진행 상태 콜백 함수(선택).                |

-   Return
    -   `"success"`: 생성 성공.
    -   `"error map load"`: 지도가 로드되지 않은 경우.
    -   callback 누락/타입 오류, info/coordinates/analysis 태그 오류, `analysis.type`이 `"TERRAIN_DIRECTION_SHAPE"`인 경우 shape 태그 오류 시 각 항목에 대한 에러 메시지.
    -   `"error coordinates { coordinate } Check => Can't Create Face"`: 좌표로 면(Face) 생성 실패.
    -   `"error coordinates { coordinate } Check => Can't DEM"`: 고도(DEM) 데이터 획득 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getSlope().importSlopeData(
    json,
    function (result) {},
    function (state) {}
);
```

{% endtab %}
{% endtabs %}

### insertColorMap(colorMap) → string

> 경사 분석 결과에 적용할 범례 색상 목록을 등록합니다(등록 이후 실행되는 analysisTerrainSlope()/importSlopeData()에 적용됩니다).

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                                            | Description                    |
| :------- | :---------------------------------------------------------------- | :-------------------------------- |
| colorMap | [JSSlope.ColorMapOption](jsslope.md#jsslope.colormapoption)         | 범례 색상 목록 옵션 객체.        |

-   Return
    -   `"success"`: 등록 성공.
    -   `"error map load"`: 지도가 로드되지 않은 경우.
    -   `"error type Tag NULL"`: `type` 또는 `list` 속성이 없는 경우(두 경우 모두 동일한 메시지가 반환됨).
    -   `"error size < 0"`: `list`의 길이가 0보다 작은 경우.
    -   `"error Over Size ( MAX 25 )"`: `list`의 길이가 25(0\~24)를 초과하는 경우.
    -   `"error type lenght Zero"`: `type` 문자열 길이가 0인 경우(원문 그대로, "length" 오탈자).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getSlope().insertColorMap({
    type: "TERRAIN_ANGLE",
    list: [
        { num: 0, a: 255, r: 0, g: 128, b: 0, begin: 0, end: 10 },
        { num: 1, a: 255, r: 255, g: 165, b: 0, begin: 10, end: 30 },
        { num: 2, a: 255, r: 255, g: 0, b: 0, begin: 30, end: 90 },
    ],
});
```

{% endtab %}
{% endtabs %}

### getAnalysisResult(key, resultType, resultData) → number

> 경사 분석 결과값(향/도 분석의 평균/최소/최대값)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                                                        |
| :--------- | :----- | :--------------------------------------------------------------------- |
| key        | string | 분석 결과 가시화 객체 고유 명칭.                                     |
| resultType | number | <p>결과 타입 구분<br>0: 향 분석 데이터<br>1: 도 분석 데이터</p>       |
| resultData | number | <p>결과 분류 타입<br>0: 평균값<br>1: 최소값<br>2: 최대값</p>          |

-   Return
    -   number: 요청한 분석값.
    -   -1.0: 지도가 로드되지 않았거나, key에 해당하는 분석 결과를 찾지 못한 경우.
    -   0: resultType, resultData가 위 값 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getSlope().getAnalysisResult(key, 0, 0); // 향 분석 평균값
Module.getSlope().getAnalysisResult(key, 0, 1); // 향 분석 최소값
Module.getSlope().getAnalysisResult(key, 0, 2); // 향 분석 최대값
Module.getSlope().getAnalysisResult(key, 1, 0); // 도 분석 평균값
Module.getSlope().getAnalysisResult(key, 1, 1); // 도 분석 최소값
Module.getSlope().getAnalysisResult(key, 1, 2); // 도 분석 최대값
```

{% endtab %}
{% endtabs %}

### getColorArea(key, index) → number

> 각 범례 인덱스 별 면적 값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                      |
| :---- | :----- | :------------------------------- |
| key   | string | 분석 결과 가시화 객체 고유 명칭. |
| index | number | 면적 값을 반환할 인덱스.         |

-   Return
    -   number(0 ~) : 범례에 해당하는 면적 반환 성공 (square meters 단위).
    -   -1 : index가 유효하지 않거나, key에 해당하는 오브젝트를 찾지 못한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getImageWidth(key) → number

> 경사 분석 결과 이미지(RTT)의 너비를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                      |
| :--- | :----- | :------------------------------- |
| key  | string | 분석 결과 가시화 객체 고유 명칭. |

-   Return
    -   number: 결과 이미지 너비(픽셀 단위). `analysis.type`이 `"TERRAIN_DIRECTION_SHAPE"`인 경우 `(격자 가로 셀 수 × 형상 크기) - 형상 크기`로 계산되며, 그 외에는 격자 가로 셀 수와 동일합니다.
    -   -1: 지도가 로드되지 않았거나, key에 해당하는 분석 결과를 찾지 못한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getImageHeight(key) → number

> 경사 분석 결과 이미지(RTT)의 높이를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                      |
| :--- | :----- | :------------------------------- |
| key  | string | 분석 결과 가시화 객체 고유 명칭. |

-   Return
    -   number: 결과 이미지 높이(픽셀 단위). `analysis.type`이 `"TERRAIN_DIRECTION_SHAPE"`인 경우 `(격자 세로 셀 수 × 형상 크기) - 형상 크기`로 계산되며, 그 외에는 격자 세로 셀 수와 동일합니다.
    -   -1: 지도가 로드되지 않았거나, key에 해당하는 분석 결과를 찾지 못한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getLineSlopeAngle(from, to) → number

> 두 지점 사이의 경사각을 반환합니다(고도가 낮은 지점을 시작점으로 하여 계산).

{% tabs %}
{% tab title="Information" %}

| Name | Type                                     | Description        |
| :--- | :----------------------------------------- | :-------------------- |
| from | [JSVector3D](../core/jsvector3d.md)      | 시작 좌표(경도, 위도, 고도). |
| to   | [JSVector3D](../core/jsvector3d.md)      | 종료 좌표(경도, 위도, 고도). |

-   Return
    -   number: 두 지점 사이의 경사각(degree 단위).
    -   0.0: 지도가 로드되지 않았거나, 두 지점 사이 거리가 0에 가까운 경우(0.0001 미만).

{% endtab %}
{% tab title="Template" %}

```javascript
let angle = Module.getSlope().getLineSlopeAngle(fromPos, toPos);
```

{% endtab %}
{% endtabs %}

### getLonLatSlopeData(options) → string

> 지정한 경위도 지점 및 그 주변 8방향 셀의 경사 향/각도 분석 데이터를 조회합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                          | Description                |
| :------ | :--------------------------------------------------------------- | :---------------------------- |
| options | [JSSlope.PositionOption](jsslope.md#jsslope.positionoption)       | 조회할 위치 정보 옵션 객체. |

-   Return
    -   string: 조회 지점을 포함한 3x3 셀(중심점 기준 상하좌우 대각선 포함 9개)의 `isInside`, `direct`(향), `angle`(경사각), `lon`, `lat` 값을 담은 JSON 문자열(`{ "output": [ {...}, ... ] }` 형식).
    -   `"error Out Of Area"`: 좌표가 분석 영역을 벗어난 경우.
    -   그 외 각 태그 유효성 오류 메시지(`options.position` 또는 하위 항목 누락/타입 오류, `options.analysis.key`에 해당하는 분석 결과 없음).

{% endtab %}
{% tab title="Template" %}

```javascript
let json = Module.getSlope().getLonLatSlopeData({
    position: {
        key: "slope_001",
        lon: 127.0015,
        lat: 37.0015,
    },
});
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSSlope.AnalysisOption

> analysisTerrainSlope(), importSlopeData()에서 사용하는 분석 요청 옵션.

| Name        | Type                                                                    | Attributes | Default              | Description                                                                          |
| ----------- | ------------------------------------------------------------------------ | ---------- | --------------------- | ---------------------------------------------------------------------------------------- |
| info        | [JSSlope.AnalysisOption.info](jsslope.md#jsslope.analysisoption.info)             |            |                       | 결과를 등록할 레이어/키 정보.                                                        |
| coordinates | [JSSlope.AnalysisOption.coordinates](jsslope.md#jsslope.analysisoption.coordinates) |            |                       | 분석 영역 좌표 정보.                                                                 |
| analysis    | [JSSlope.AnalysisOption.analysis](jsslope.md#jsslope.analysisoption.analysis)     | optional   |                       | 분석 타입/해상도 정보.                                                               |
| shape       | [JSSlope.AnalysisOption.shape](jsslope.md#jsslope.analysisoption.shape)           | optional   |                       | 형상(화살표) 표시 옵션. analysisTerrainSlope()는 항상 파싱하며, importSlopeData()는 `analysis.type`이 `"TERRAIN_DIRECTION_SHAPE"`인 경우에만 사용합니다. |
| color       | [JSSlope.ColorMapOption](jsslope.md#jsslope.colormapoption)                      | optional   |                       | importSlopeData() 전용. `analysis.type`이 `"TERRAIN_DIRECTION_SHAPE"`가 아닌 경우 범례 색상 등록에 사용됩니다. |
| callback    | function                                                                |            |                       | analysisTerrainSlope() 전용. 분석 결과 이미지 생성 완료 시 호출되는 콜백(필수).      |
| progress    | function                                                                | optional   |                       | analysisTerrainSlope() 전용. 분석 진행 상태 콜백(1: 시작, 100: 완료, -1: 고도 데이터 오류). |

#### JSSlope.AnalysisOption.info

| Name  | Type   | Attributes | Default | Description                                                    |
| ----- | ------ | ---------- | ------- | ---------------------------------------------------------------- |
| layer | string |            |         | 분석 결과를 표시할 레이어 명칭(없으면 새로 생성).             |
| key   | string |            |         | 분석 결과 오브젝트 고유 키(이미 사용 중인 키인 경우 오류).    |

#### JSSlope.AnalysisOption.coordinates

| Name       | Type           | Attributes | Default | Description                        |
| ---------- | -------------- | ---------- | ------- | ------------------------------------- |
| style      | string         |            |         | 좌표 형식.                          |
| coordinate | array          |            |         | 분석 영역 좌표 목록(3개 이상 필요). |

#### JSSlope.AnalysisOption.analysis

| Name  | Type    | Attributes | Default              | Description                                                                                                                                                                          |
| ----- | ------- | ---------- | --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type  | string  | optional   | `"TERRAIN_DIRECTION"` | 분석 타입. `TERRAIN_DIRECTION`(향), `TERRAIN_DIRECTION_SHAPE`(향+화살표 형상), `TERRAIN_DIRECTION_ANGLE`(향+경사각), `TERRAIN_ANGLE`(경사각), `TERRAIN_SUN`(일사량), `TERRAIN_ALTITUDE`(고도). |
| size  | number  | optional   | 2                     | 분석 격자 크기(analysisTerrainSlope 기준 2~256로 보정됨).                                                                                                                        |
| image | boolean | optional   | true                  | 분석 결과 이미지를 생성할지 여부. false이거나 결과 이미지가 2048x2048을 초과하면 callback이 호출되지 않습니다.                                                                     |

#### JSSlope.AnalysisOption.shape

| Name       | Type   | Attributes | Default | Description                                                                        |
| ---------- | ------ | ---------- | ------- | --------------------------------------------------------------------------------------- |
| size       | number | optional   | 64      | 형상(화살표) 크기(analysisTerrainSlope 기준 8~256으로 보정됨).                       |
| r, g, b, a | number | optional   | 255     | 형상 색상.                                                                          |

#### JSSlope.ColorMapOption

> insertColorMap(), importSlopeData()의 color 옵션에서 사용하는 범례 색상 목록.

| Name | Type                                                       | Attributes | Default | Description                                             |
| ---- | ------------------------------------------------------------ | ---------- | ------- | ----------------------------------------------------------- |
| type | string                                                     |            |         | 범례 대상 분석 타입 문자열([JSSlope.AnalysisOption.analysis](jsslope.md#jsslope.analysisoption.analysis)의 type과 동일한 값). |
| list | array([JSSlope.ColorMapOption.item](jsslope.md#jsslope.colormapoption.item)) |            |         | 범례 항목 배열(최대 25개, 0~24 인덱스).                    |

#### JSSlope.ColorMapOption.item

| Name      | Type   | Attributes                                                                        | Default | Description                              |
| --------- | ------ | ------------------------------------------------------------------------------------ | ------- | ------------------------------------------- |
| num       | number |                                                                                    |         | 범례 인덱스 번호.                        |
| a, r, g, b | number |                                                                                    |         | 범례 색상(ARGB).                        |
| direction | string | `type`이 `TERRAIN_DIRECTION`, `TERRAIN_DIRECTION_SHAPE`, `TERRAIN_DIRECTION_ANGLE`인 경우에만 사용 |         | 방위(`N`,`NE`,`E`,`SE`,`S`,`SW`,`W`,`NW`). |
| begin, end | number | `type`이 `TERRAIN_DIRECTION_ANGLE`, `TERRAIN_ANGLE`, `TERRAIN_SUN`, `TERRAIN_ALTITUDE`인 경우에만 사용 |         | 범례 시작/종료 값.                      |

#### JSSlope.PositionOption

> getLonLatSlopeData()에서 사용하는 위치 조회 옵션.

| Name     | Type   | Attributes | Default | Description                              |
| -------- | ------ | ---------- | ------- | ------------------------------------------- |
| position | [JSSlope.PositionOption.position](jsslope.md#jsslope.positionoption.position) |            |         | 조회할 위치 정보.                        |
| analysis | [JSSlope.AnalysisOption.analysis](jsslope.md#jsslope.analysisoption.analysis) | optional   |         | 파싱은 되지만 결과에는 영향을 주지 않습니다. |

#### JSSlope.PositionOption.position

| Name | Type   | Attributes | Default | Description                              |
| ---- | ------ | ---------- | ------- | ------------------------------------------- |
| key  | string |            |         | 조회할 경사 분석 오브젝트 고유 명칭.     |
| lon  | number |            |         | 조회할 경도.                             |
| lat  | number |            |         | 조회할 위도.                             |

#### JSSlope.CheckServerDemOption

> checkServerDemAnalysis()에서 사용하는 옵션. info, callback 등 다른 분석 옵션은 필요하지 않습니다.

| Name        | Type                                                                                | Attributes | Default | Description                                  |
| ----------- | ------------------------------------------------------------------------------------- | ---------- | ------- | ---------------------------------------------- |
| coordinates | [JSSlope.AnalysisOption.coordinates](jsslope.md#jsslope.analysisoption.coordinates) |            |         | 분석 영역 좌표 정보(3개 이상 필요).          |
| analysis    | [JSSlope.CheckServerDemOption.analysis](jsslope.md#jsslope.checkserverdemoption.analysis) | optional   |         | 서버 DEM 요청 레벨/타일 상한 정보.           |

#### JSSlope.CheckServerDemOption.analysis

> 서버 DEM 기반 분석 옵션 중 확인 결과에 영향을 주는 속성입니다. `analysis.server`는 `analysisTerrainSlope()`에서 서버 DEM 분석을 켜는 속성이며, `checkServerDemAnalysis()`는 이 값과 무관하게 항상 서버 DEM 기준으로 확인합니다.

| Name       | Type             | Attributes | Default  | Description                                                                                         |
| ---------- | ---------------- | ---------- | -------- | ----------------------------------------------------------------------------------------------------- |
| level      | number \| string | optional   | `"max"`  | 요청 DEM 레벨. 숫자가 아닌 값(`"max"` 등)은 지형 서비스 레벨을 사용합니다.                          |
| tileBudget | number           | optional   | 0        | 허용 타일 수 상한. 0 이하이면 내부 최대값(65519)을 사용합니다.                                     |
