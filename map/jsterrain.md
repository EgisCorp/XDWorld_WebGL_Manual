---
description: 지도 내 지형 설정 및 제어하기 위한 API 입니다.
---

# JSTerrain

> Module.getTerrain() API를 생성합니다.

```javascript
var map = Module.getTerrain();
```

## Properties

| Name              | Type   | Description        |
| ----------------- | ------ | ------------------ |
| demRate           | number | DEM 높이 표현 비율       |
| recoverHSV        | number | 색상 조정 설정 여부        |
| recoverHue        | number | 색상 Hue 조정 값        |
| recoverSaturation | number | 색상 Saturation 조정 값 |
| recoverValue      | number | 색상 Value 조정 값      |
| demServerURL      | string | (읽기 전용) DEM 서버 요청 URL |
| demServerRoot     | string | (읽기 전용) DEM 서버 루트 경로 |
| demLayerName      | string | (읽기 전용) DEM 서버 레이어 명칭 |
| imageServerURL    | string | (읽기 전용) 지형 영상 서버 요청 URL |
| imageServerRoot   | string | (읽기 전용) 지형 영상 서버 루트 경로 |
| imageLayerName    | string | (읽기 전용) 지형 영상 서버 레이어 명칭 |
| demBox            | object | (읽기 전용) 설정된 DEM Box 정보. `getDemBox()`와 동일한 형태. |

## Function

### insertTerrainHoleArea(areaPositions) → boolean

> 지정한 경위도 영역에 지형 홀(구멍) 영역을 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type                                   | Description                    |
| ------------- | ----------------------------------------- | --------------------------------- |
| areaPositions | [JSVec2Array](../core/jsvec2array.md)   | 홀 영역을 구성하는 좌표 목록 (2개 이상). |

-   Return
    -   항상 false (구현상 성공 여부와 무관하게 false 반환).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTerrainHoleAreaVisible(index, visible) → boolean

> 등록된 지형 홀(구멍) 영역의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                          |
| ------- | ------- | ------------------------------------------------------- |
| index   | number  | 대상 홀 영역 인덱스 (`insertTerrainHoleArea` 등록 순서). |
| visible | boolean | <p>true: 가시화.<br>false: 비가시화.</p>              |

-   Return
    -   true: 설정 성공.
    -   false: index가 유효 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setMaxLevel(level)

> 지형 요청 최대 레벨을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| level | number | 지형 최대 레벨. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRequestUrlOption(options) → boolean

> DEM(고도) 및 지형 영상 데이터 요청 URL 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                                        |
| ------- | ------ | --------------------------------------------------------------------------------------------------------------------- |
| options | object | `urltype`(필수, "xdserver" 또는 "user"), `dem`(`url`,`server`/`path`,`layer`/`format`), `image`(`url`,`server`/`path`,`layer`/`format`) 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 설정 성공.
    -   false: `urltype`이 누락되었거나 "xdserver", "user" 중 어디에도 해당하지 않는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setUseDemBox(use)

> DEM Box(특정 영역에 대한 별도 DEM 요청) 기능 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                        |
| ---- | ------- | ------------------------------------------------------ |
| use  | boolean | <p>true: DEM Box 사용.<br>false: 미사용.</p>       |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDemBox(options) → boolean

> DEM Box 영역 및 서버 요청 정보를 설정합니다. `demBox` 속성(getDemBox())으로 설정된 값을 조회할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                                                             |
| ------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| options | object | `server`(`url`, `request_type`("file"/그 외), `format` 또는 `layer_name`), `area`(`min`,`max`: `{lon,lat}`, `minlevel`, `maxlevel`), `encoding`(boolean) 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않았거나, `area`의 `min`/`max`에 `lon`/`lat`이 누락된 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearDemBoxArea() → boolean

> 설정된 DEM Box 타일 인덱스 정보를 초기화합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 초기화 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setBlankTileTextureURL(url) → boolean

> 데이터가 없는 빈 타일에 대해 표시할 대체 텍스처 URL을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
| ---- | ------ | ------------------- |
| url  | string | 대체 텍스처 URL 경로. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTerrainColor(options) → boolean

> 고도 기반 지형 색상(DEM Color) 표현 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                     |
| ------- | ------ | --------------------------------------------------------------------------------------------------- |
| options | object | `altitudemin`(필수, 최소 고도), `altitudemax`(필수, 최대 고도), `colorlist`(고도 구간별 색상 목록, [JSColor](../core/jscolor.md) 배열) 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않았거나, `altitudemin`/`altitudemax`가 누락된 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSkirtHeight(height)

> 지형 타일 경계의 스커트(skirt, 이음새 가림용 수직 벽) 높이를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                |
| ------ | ------ | ---------------------------- |
| height | number | 스커트 높이 (meter 단위). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setImageryQuality(quality) → boolean

> 지형 영상(이미지) 품질을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description       |
| ------- | ------ | ------------------- |
| quality | number | 영상 품질 값.       |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGridLine(options) → boolean

> 경위도 그리드 라인 표시 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                          |
| ------- | ------ | ---------------------------------------------------------------------------------------- |
| options | object | `active`(boolean, 표시 여부), `width`(number, 라인 두께), `fadeAngle`(number, 페이드 시작 각도) 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않았거나 options가 유효하지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### makeTerrainElevationCellData(option) → object

> 입력된 정점 좌표 목록을 기반으로 변수값 격자 구조를 생성하고 정보를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                                                      | Description |
| ------ | --------------------------------------------------------- | ----------- |
| option | [JSTerrain.GridOption](jsterrain.md#jsterrain.gridoption) | 속성 정보.      |

* Return
  * .result: API success status ( 1 : success, 0 : failure ).
  * .name: Name of the operation API.
  * .return: API return information ( [JSTerrain.GridData](jsterrain.md#jsterrain.griddata) : Normal return value, string : Failure error code ).
{% endtab %}

{% tab title="Template" %}
```javascript
let point = new Module.JSVec3Array();
point.push(new Module.JSVector3D(127.01969238371277, 37.56514815604788, 24.40620245039463));
point.push(new Module.JSVector3D(127.01962748647728, 37.56392380491751, 25.515124042518437));
point.push(new Module.JSVector3D(127.02194230953037, 37.56375530181643, 33.266184841282666));
point.push(new Module.JSVector3D(127.02220846619382, 37.56494396175599, 26.32035342976451));

let parameter = {
    coordinates: {
        style: "JSVector3D",
        coordinate: point,
    },
    vertical: 10,
    horizontal: 10,
};
let result = Module.getTerrain().makeTerrainElevationCellData(parameter);
```
{% endtab %}
{% endtabs %}

### getServerAltitude(options, callback) → boolean

> 입력된 좌표 목록에 대해 서버로부터 고도값을 요청하고, 결과를 콜백 함수로 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type     | Description                 |
| -------- | -------- | --------------------------- |
| options  | object   | 요청할 좌표 정보.                  |
| callback | function | 요청 완료 후 결과 고도값을 반환하는 콜백 함수. |

**options 구조**

| Key       | Type   | Description                                                                |
| --------- | ------ | -------------------------------------------------------------------------- |
| level     | number | 요청할 지형 타일 레벨.                                                              |
| positions | array  | 고도 요청할 좌표 목록. 2D 배열(lon, lat) 또는 [JSVec2Array](../core/jsvec2array.md) 가능. |

* Return
  * `true`: 요청 성공.
  * `false`: 파라미터 오류 또는 실패.
* Error Conditions
  * `callback`이 함수가 아닌 경우.
  * `positions`가 배열도 JSVec2Array도 아닌 경우.
  * `level` 또는 `positions`가 누락된 경우.
* Sample
  * [Sandbox\_TerrainAltitude](https://sandbox.egiscloud.com/code/main.do?id=terrain_dem_from_server)
{% endtab %}

{% tab title="Template" %}
```javascript
var input = {
    level: 10,
    positions: [
        [127.01, 37.55],
        [127.02, 37.56]
    ]
};

Module.getTerrain().getServerAltitude(input, function (result) {
    console.log("Altitude result:", result);
});
```
{% endtab %}
{% endtabs %}

### setImageMask(option) → bool

> 지정한 경위도 사각 범위 바깥의 지역을 임의의 색상으로 마스킹합니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                                                              | Description |
| ------ | ----------------------------------------------------------------- | ----------- |
| option | [JSTerrain.MaskingOptions](jsterrain.md#jsterrain.maskingoptions) | 속성 정보       |

* Return
  * 성공 시 true, 실패 시 false를 반환합니다.
* Sample
  * [Sandbox\_RequestBoundary](https://sandbox.egiscloud.com/code/main.do?id=layer_building_request_boundary)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getTerrain().setImageMask({
    active : true,
    range : {
        min : [126.930052, 37.529214],
        max : [126.941028, 37.520294]
    },
    color : {
        a : 200,
        r : 0,
        g : 0,
        b : 0
    }
});
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTerrain.GridOption

> Basic Grid setting options.

| Name       | Type                                                    | Attributes | Default | Description                                                                                     |
| ---------- | ------------------------------------------------------- | ---------- | ------- | ----------------------------------------------------------------------------------------------- |
| option     | [coordinates Type](../etc/tag-list.md#coordinates-type) |            |         | List of latitude and longitude coordinates for the analysis area, coordinate list type setting. |
| vertical   | number                                                  | optional   | 5       | Length of the Cell composing the Grid vertically (in meters).                                   |
| horizontal | number                                                  | optional   | 5       | Length of the Cell composing the Grid horizontally (in meters).                                 |

#### JSTerrain.GridData

> Grid return information.

| Name            | Type                                                  | Description                                                     |
| --------------- | ----------------------------------------------------- | --------------------------------------------------------------- |
| min             | [JSVector2D](../core/jsvector2d.md)                   | Lower left latitude and longitude coordinates of the Grid.      |
| max             | [JSVector2D](../core/jsvector2d.md)                   | Upper right latitude and longitude coordinates of the Grid.     |
| center          | [JSVector2D](../core/jsvector2d.md)                   | Center latitude and longitude coordinates of the Grid.          |
| vertical        | number                                                | Length of the Cell composing the Grid vertically (in meters).   |
| verticalCount   | number                                                | Number of Cells composing the Grid vertically.                  |
| horizontal      | number                                                | Length of the Cell composing the Grid horizontally (in meters). |
| horizontalCount | number                                                | Number of Cells composing the Grid horizontally.                |
| cells           | [JSTerrain.CellData](jsterrain.md#jsterrain.celldata) | Array of Cell information composing the Grid.                   |

#### JSTerrain.CellData

> Data information of the Cell composing the Grid.

| Name      | Type                                | Description                                                      |
| --------- | ----------------------------------- | ---------------------------------------------------------------- |
| type      | boolean                             | Inclusion status of the analysis area.                           |
| elevation | number                              | Elevation of the cell center latitude and longitude coordinates. |
| min       | [JSVector2D](../core/jsvector2d.md) | Lower left latitude and longitude coordinates of the Cell.       |
| max       | [JSVector2D](../core/jsvector2d.md) | Upper right latitude and longitude coordinates of the Cell.      |
| center    | [JSVector2D](../core/jsvector2d.md) | Center latitude and longitude coordinates of the Cell.           |

#### JSTerrain.MaskingOptions

> 지형 영상 마스킹 옵션 속성

| Name   | Type    | Description                                |
| ------ | ------- | ------------------------------------------ |
| active | boolean | 옵션 활성화 여부                                  |
| range  | object  | 2차원 경위도 좌표 min, max 속성으로 이루어진 마스킹 범위       |
| color  | object  | 0\~255 사이 정수 a, r, g, b 속성으로 이루어진 마스킹 색상 값 |
