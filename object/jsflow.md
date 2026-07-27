---
description: 지도 내 바람 흐름을 표현하는 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSFlow

> Module.getFlow() API를 생성합니다.
>
> 입력 변수값은 [JSFlow.FlowDataOption](jsflow.md#jsflow.flowdataoption) 참조.

```javascript
let flow = Module.getFlow();
```

## Properties

| Name         | Type   | Description                       |
| ------------ | ------ | ------------------------------------ |
| velocity     | number | 바람장 파티클 이동속도 스케일.     |
| offsetHeight | number | 바람장 파티클 높이.                |
| particleNum  | number | 화면에 표출되는 파티클 수.         |

## Function

### createFlow(options) → boolean

> 고유 ID를 가진 새로운 바람장(Flow) 객체를 비동기로 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                                                                                            |
| ------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| options | object | `url`(필수, 바람장 파일 경로), `id`(필수, 고유 식별자), `start_color`, `end_color`(object, 파티클 시작/종료 색상), `velocity`, `base_altitude`, `particle_count`, `particle_life_time_min`, `particle_life_time_max`, `underground_altitude`, `thickness` 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 요청 성공(비동기 로드 시작).
    -   false: `url` 또는 `id`가 없거나, 이미 동일한 `id`가 존재하는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### deleteFlow(id) → boolean

> 지정한 ID의 바람장 객체를 제거합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
| ---- | ------ | -------------------- |
| id   | string | 제거할 바람장 고유 ID. |

-   Return
    -   true: 제거 성공.
    -   false: 해당 ID가 존재하지 않는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### isExist(id) → boolean

> 지정한 ID의 바람장 객체가 존재하는지 확인합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description        |
| ---- | ------ | --------------------- |
| id   | string | 확인할 바람장 고유 ID. |

-   Return
    -   true: 존재함.
    -   false: 존재하지 않음.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### GetFlowData(url, type, velocity, height, particleNum)

> (레거시) 바람장 파일을 요청하여 가시화 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type   | Description               |
| ----------- | ------ | ---------------------------- |
| url         | string | 바람장 파일 경로.          |
| type        | number | 바람장 파일 타입.          |
| velocity    | number | 파티클 이동속도 스케일.    |
| height      | number | 파티클 높이.               |
| particleNum | number | 파티클 수.                 |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### GetWaterDepthData(url, type, scale)

> (레거시) 해수심도 데이터 파일을 요청하여 가시화 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
| ----- | ------ | --------------------- |
| url   | string | 해수심도 파일 경로. |
| type  | number | 파일 타입.          |
| scale | number | 표현 스케일 값.     |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetFlowColor(startRed, startGreen, startBlue, endRed, endGreen, endBlue)

> (레거시) 바람장 파티클의 시작/종료 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description        |
| ---------- | ------ | --------------------- |
| startRed   | number | 시작 색상 red 값.   |
| startGreen | number | 시작 색상 green 값. |
| startBlue  | number | 시작 색상 blue 값.  |
| endRed     | number | 종료 색상 red 값.   |
| endGreen   | number | 종료 색상 green 값. |
| endBlue    | number | 종료 색상 blue 값.  |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ClearFlowData()

> 바람장 데이터 초기화

{% tabs %}
{% tab title="Information" %}

{% endtab %}

{% tab title="Template" %}

```javascript
let flow = Module.getFlow();
flow.ClearFlowData();
```

{% endtab %}
{% endtabs %}

### CreateFlowData(velocity, height, particleNum) → boolean

> (레거시) AddFlowData()로 등록한 데이터를 기반으로 바람장 가시화 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type   | Description               |
| ----------- | ------ | ---------------------------- |
| velocity    | number | 파티클 이동속도 스케일.    |
| height      | number | 파티클 높이.               |
| particleNum | number | 파티클 수.                 |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### AddFlowData(lat, lon, speed, direction)

> (레거시) 바람장 데이터 지점(위경도, 풍속, 방향)을 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description   |
| --------- | ------ | -------------- |
| lat       | number | 위도.          |
| lon       | number | 경도.          |
| speed     | number | 풍속.          |
| direction | number | 풍향.          |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setJSON(options) → boolean

> [JSFlow.FlowDataOption](jsflow.md#jsflow.flowdataoption) 형식의 통합 옵션으로 바람장을 생성합니다.
>
> `data.url`(바람장 파일) 또는 `data.grid`(격자 데이터 직접 입력) 중 하나를 사용해 데이터를 구성하며, `data.dem`으로 DEM 결합, `legend`로 색상 표현 방식을 설정할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                     | Description  |
| ------- | --------------------------------------------------------------------------- | -------------- |
| options | [JSFlow.FlowDataOption](jsflow.md#jsflow.flowdataoption)                | 속성 정보.   |

-   Return
    -   true: 설정 성공.
    -   false: `data`가 없거나, `data.grid`/`data.url`이 모두 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setUnionTerrain(unionTerrain) → boolean

> 바람장 파티클의 지형 결합(지표면 높이 반영) 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type    | Description                                    |
| ------------ | ------- | -------------------------------------------------- |
| unionTerrain | boolean | <p>true: 지형 결합.<br>false: 미결합.</p>       |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getVisible(id), setVisible(id, visible) → boolean

> 지정한 ID의 바람장 가시화 유무를 설정하거나 반환합니다.
>
> setVisible()의 첫 번째 인자가 문자열이 아닌 경우, ID로 구분되지 않는 기본(전역) 바람장 객체에 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                          |
| ------- | ------- | ------------------------------------------------------- |
| id      | string  | 대상 바람장 고유 ID.                                  |
| visible | boolean | <p>true: 가시화.<br>false: 비가시화.</p>             |

-   Return (get)
    -   true: 가시화 상태.
    -   false: 비가시화 상태이거나 해당 ID가 존재하지 않는 경우.
-   Return (set)
    -   true: 설정 성공.
    -   false: id가 문자열이고 해당 ID가 존재하지 않는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSFlow.FlowDataOption

> 바람 표현 입력 정보.

| Name   | Type                                                                             | Attributes | Default | Description       |
| ------ | -------------------------------------------------------------------------------- | ---------- | ------- | ----------------- |
| data   | [JSFlow.FlowDataOption.dataParam](jsflow.md#jsflow.flowdataoption.dataparam)     |            |         | 구성 데이터 필드. |
| option | [JSFlow.FlowDataOption.optionParam](jsflow.md#jsflow.flowdataoption.optionparam) | optional   |         | 초기 데이터 설정. |
| legend | [JSFlow.FlowDataOption.legendParam](jsflow.md#jsflow.flowdataoption.legendparam) | optional   |         | 범례 표현.        |

#### JSFlow.FlowDataOption.dataParam

> 구성 데이터 필드.

| Name | Type                                                                                 | Attributes | Default | Description                                                                   |
| ---- | ------------------------------------------------------------------------------------ | ---------- | ------- | ----------------------------------------------------------------------------- |
| url  | string                                                                               |            |         | 바람장 파일 url 경로.                                                         |
| dem  | [JSFlow.FlowDataOption.dataParam.dem](jsflow.md#jsflow.flowdataoption.dataparam.dem) | optional   |         | 바람장 분석시 저장파일 루트의 height.txt 파일을 파싱해서 미리 다운 받아 사용. |

#### JSFlow.FlowDataOption.dataParam.dem

> height.txt의 DEM 정보를 전환한 Float Array 데이터.

| Name     | Type   | Description                              |
| -------- | ------ | ---------------------------------------- |
| cols     | number | DEM 가로 셀수.                           |
| rows     | number | DEM 세로 셀수.                           |
| size     | number | DEM의 해상도 (단위 미터).                |
| llcorner | string | DEM의 좌하단 좌표 (GRS80 TM 중부, 60만). |
| data     | array  | DEM 데이터.                              |

#### JSFlow.FlowDataOption.dataParam.dem.llcorner

> DEM의 좌하단 좌표 (GRS80 TM 중부, 60만).

| Name     | Type   | Description                        |
| -------- | ------ | ---------------------------------- |
| left     | number | DEM 시작점의 x 좌표.               |
| lower    | number | DEM 시작점의 y 좌표.               |
| projCord | number | DEM 투영 데이터 크기(20으로 고정). |

#### JSFlow.FlowDataOption.optionParam

> 초기 데이터 설정.

| Name         | Type   | Description                                                          |
| ------------ | ------ | -------------------------------------------------------------------- |
| velocity     | number | 바람장 파티클 이동속도 스케일.                                       |
| offsetHeight | number | 바람장 파티클 높이 (DEM이 없으면 해발고도 기준, 있으면 지표면 기준). |
| maxParticle  | number | 화면에 최대 표출가능한 파티클 수 (5000 이하 권장).                   |
| minLifeTime  | number | 파티클 유지시간 최소 값.                                             |
| maxLifeTime  | number | 파티클 유지시간 최대 값 ( maxLifeTime > LifeTime > minLifeTime ).    |

#### JSFlow.FlowDataOption.legendParam

> 풍속별 범례를 적용하는 방법과 진행 궤적을 그라데이션으로 표현하는 방법이 있음.

-   풍속별 범례

| Name     | Type                                                                                               | Description                                 |
| -------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| maxIndex | number                                                                                             | 궤적 표현시 사용(풍속별 범례에선 255 고정). |
| fixValue | [JSFlow.FlowDataOption.legendParam.fixValue](jsflow.md#jsflow.flowdataoption.legendparam.fixvalue) | 풍속 기준 범례 사용 배열.                   |

-   진행 궤적 표현

| Name             | Type                                                                                       | Description                   |
| ---------------- | ------------------------------------------------------------------------------------------ | ----------------------------- |
| maxIndex         | number                                                                                     | 바람장 이동 속도.             |
| fixValue or band | [JSFlow.FlowDataOption.legendParam.band](jsflow.md#jsflow.flowdataoption.legendparam.band) | 풍속별 범례 또는 궤적 데이터. |

#### JSFlow.FlowDataOption.legendParam.fixValue

> 풍속 기준 범례 사용 배열.
>
> value와 color로 표현한 범례별 색상을 나열하여 배열에 저장(value 이하 풍속에서 color의 색상 적용).

| Name  | Type   | Description                                     |
| ----- | ------ | ----------------------------------------------- |
| value | number | 범례 풍속.                                      |
| color | array  | 해당 범례에 해당하는 색상 설정. r, g, b로 구성. |

#### JSFlow.FlowDataOption.legendParam.band

> 바람장 궤적 표현 배열.
>
> 전체 궤적을 maxIndex 구간으로 나누며, startIndex/endIndex을 통해 구간별로 색상을 지정.
>
> 배열에 나열된 start-end 색상 정보를 그라데이션 형태로 표현.
>
> ex) start: 빨강, end: 하양일 경우. 하양 ------------> 빨강

| Name       | Type   | Description                                |
| ---------- | ------ | ------------------------------------------ |
| startIndex | number | 구간을 반영할 시작부분 Table Index (꼬리). |
| startColor | array  | 꼬리에 해당하는 색상 설정. r, g, b로 구성. |
| endIndex   | number | 구간을 반영할 끝부분 Table Index (머리).   |
| endColor   | array  | 머리에 해당하는 색상 설정. r, g, b로 구성. |
