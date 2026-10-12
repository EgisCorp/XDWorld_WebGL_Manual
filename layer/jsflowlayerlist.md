---
description: 해류·조류 흐름 레이어(JSCurrentFlowLayer)를 생성하고 관리하기 위한 API 입니다.
---

# JSFlowLayerList

> `Module.getFlowLayerList()`로 흐름 레이어 목록 객체를 얻습니다. (싱글톤이며 호출할 때마다 같은 객체를 반환합니다.)
>
> 해류·조류처럼 시각별로 제공되는 유속 격자(PNG) 데이터를 파티클로 흘려 표현하는 [JSCurrentFlowLayer](jscurrentflowlayer.md)를 생성하고 관리합니다. [JSLayerList](jslayerlist.md)의 레이어와는 독립적으로 동작하므로 기존 레이어 API(`getLayerNames` 등)에는 나타나지 않습니다.

```javascript
let flowList = Module.getFlowLayerList();

let flow = flowList.createCurrentFlowLayer({
    name: "current_flow",
    bbox: [124.0, 33.0, 132.0, 39.0],
    frameUrl: "https://example.com/api/frame/{time}.png",
    times: [1, 2, 3, 4, 5, 6],
});
```

## Function

### createCurrentFlowLayer(options) → [JSCurrentFlowLayer](jscurrentflowlayer.md)

> 조류(해류) 흐름 레이어를 생성합니다.
>
> 레이어는 `options.frameUrl`로 지정한 시각별 PNG 격자를 엔진이 직접 요청(fetch)해서 사용합니다. 함수는 데이터 로드를 기다리지 않고 즉시 레이어 객체를 반환하며, 첫 프레임이 로드되어야 화면에 표시됩니다. 데이터 형식과 사용 흐름은 [JSCurrentFlowLayer](jscurrentflowlayer.md)의 "사용 흐름"을 참고하십시오.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                                                                     | Description |
| :------ | :----------------------------------------------------------------------------------------------------------------------- | :---------- |
| options | [JSFlowLayerList.CreateCurrentFlowLayerOptions](jsflowlayerlist.md#jsflowlayerlist.createcurrentflowlayeroptions) | 레이어 생성 옵션. |

-   Return
    -   [JSCurrentFlowLayer](jscurrentflowlayer.md) : 생성 성공.
    -   null : 생성 실패. 실패 사유는 콘솔에 `[CurrentFlow] ...` 경고로 출력됩니다.

-   실패 조건
    -   엔진이 아직 초기화되지 않은 경우.
    -   `options`가 undefined 또는 null인 경우.
    -   `name`이 이미 등록된 흐름 레이어와 같은 경우.
    -   `bbox`가 4개 이상의 숫자를 가진 배열이 아니거나, `lon0 < lon1`, `lat0 < lat1` 조건을 만족하지 않는 경우. (날짜변경선을 가로지르는 범위는 지정할 수 없습니다.)
    -   `frameUrl`이 없거나 빈 문자열(또는 문자열이 아닌 값)인 경우.
    -   `encoding.smin`, `encoding.smax`가 `0 < smin < smax` 조건을 만족하지 않는 경우.
    -   `times`가 배열이 아니거나 비어있는 경우.
    -   `times`가 오름차순이 아닌 경우. (같은 값이 연속되어도 실패합니다.)

-   실패하지 않고 보정되는 경우 (콘솔 경고만 출력)
    -   `encoding.type`이 `"dir8-logspeed8"`가 아니면 경고 후 `"dir8-logspeed8"`로 처리합니다.
    -   `times`가 4096개를 초과하면 앞의 4096개만 사용합니다.
    -   `tiles`를 지정했지만 `tiles.urlTemplate`이 비어있으면 타일 기능만 끄고 레이어는 생성합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
let flowList = Module.getFlowLayerList();

// 1시간 간격 240개 시각
let times = [];
for (let t = 1; t <= 240; t++) times.push(t);

let flow = flowList.createCurrentFlowLayer({
    name: "tidal_current",
    bbox: [124.0, 33.0, 132.0, 39.0],
    frameUrl: "https://example.com/api/frame/{time}.png",
    encoding: { type: "dir8-logspeed8", smin: 0.0001, smax: 5.0 },
    times: times,
    particles: { count: 8000, trail: 40 },
    colorRamp: { min: 0.0, max: 1.5 },
    autoPlay: true,
    onError: function (e) {
        console.warn("프레임 로드 실패", e.url, e.status);
    },
});

if (flow === null) {
    console.error("흐름 레이어 생성 실패 (콘솔 경고 확인)");
}
```

{% endtab %}
{% endtabs %}

### getLayer(name) → [JSCurrentFlowLayer](jscurrentflowlayer.md)

> 이름으로 흐름 레이어를 조회합니다.
>
> [createCurrentFlowLayer(options)](jsflowlayerlist.md#createcurrentflowlayer-options-jscurrentflowlayer)가 반환한 것과 같은 객체를 돌려줍니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description    |
| :--- | :----- | :------------- |
| name | string | 레이어 이름.   |

-   Return
    -   [JSCurrentFlowLayer](jscurrentflowlayer.md) : 해당 이름의 레이어.
    -   null : 해당 이름의 레이어가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let flow = Module.getFlowLayerList().getLayer("tidal_current");
if (flow !== null) {
    flow.pause();
}
```

{% endtab %}
{% endtabs %}

### removeLayer(name) → boolean

> 이름으로 흐름 레이어를 제거합니다.
>
> 진행 중인 데이터 요청은 취소되고 GPU 자원이 해제됩니다. 제거된 레이어의 기존 핸들은 이후 [isValid()](jscurrentflowlayer.md#isvalid-boolean)가 false를 반환하며, 모든 함수가 아무 동작 없이 false(또는 null)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| :--- | :----- | :----------- |
| name | string | 레이어 이름. |

-   Return
    -   true : 제거 성공.
    -   false : 해당 이름의 레이어가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let removed = Module.getFlowLayerList().removeLayer("tidal_current");
console.log(removed);
```

{% endtab %}
{% endtabs %}

### count() → number

> 등록된 흐름 레이어의 수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 등록된 흐름 레이어 수.

{% endtab %}
{% tab title="Template" %}

```javascript
let flowList = Module.getFlowLayerList();
console.log(flowList.count());
```

{% endtab %}
{% endtabs %}

### getLayerNames() → array(string)

> 등록된 흐름 레이어의 이름 목록을 생성한 순서대로 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   array(string): 레이어 이름 배열. 등록된 레이어가 없으면 빈 배열.

{% endtab %}
{% tab title="Template" %}

```javascript
let flowList = Module.getFlowLayerList();
let names = flowList.getLayerNames();
for (let i = 0; i < names.length; i++) {
    console.log(names[i]);
}
```

{% endtab %}
{% endtabs %}

## Type Definitions

#### JSFlowLayerList.CreateCurrentFlowLayerOptions

> 흐름 레이어 생성 옵션. 하위 객체(`encoding`, `prefetch`, `tiles`, `particles`, `colorRamp`, `background`)는 지정하지 않은 필드가 아래 기본값으로 채워집니다.
>
> 생성 후에는 [setParticleOptions](jscurrentflowlayer.md#setparticleoptions-options-boolean), [setColorRamp](jscurrentflowlayer.md#setcolorramp-options-boolean), [setBackground](jscurrentflowlayer.md#setbackground-options-boolean), [setOpacity](jscurrentflowlayer.md#getopacity-setopacity-opacity-number-boolean), [setVisible](jscurrentflowlayer.md#getvisible-setvisible-visible-boolean-boolean), [setDepthTest](jscurrentflowlayer.md#setdepthtest-on-boolean) 등으로 일부 값을 변경할 수 있습니다.

**기본**

| Name     | Type                      | Attributes | Default                          | Description                                                                                                                                                  |
| :------- | :------------------------ | :--------- | :------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name     | string                    | optional   | `"current_flow_N"`               | 레이어 이름. 생략하거나 문자열이 아니면 `"current_flow_N"`(N = 생성 시점의 등록 레이어 수 + 1)이 사용됩니다. 이미 사용 중인 이름이면 생성에 실패합니다.        |
| bbox     | array(number)\[4]         |            |                                  | 데이터 범위 `[lon0, lat0, lon1, lat1]` (서, 남, 동, 북 / 도 단위). `lon0 < lon1`, `lat0 < lat1`이어야 합니다. 프레임 PNG 한 장이 이 범위 전체를 덮습니다.   |
| frameUrl | string                    |            |                                  | 시각별 전체 범위 프레임 PNG의 URL 템플릿. `{time}`은 해당 시각의 `times` 값(문자열)으로, `{index}`는 `times` 배열 내 인덱스(0부터)로 치환됩니다.            |
| times    | array(number \| string)   |            |                                  | 프레임 시각 목록. 1~4096개, 반드시 오름차순(중복 불가). 숫자는 정수면 `217`, 소수면 `217.5`처럼 문자열로 바뀌어 `{time}`에 들어가고, 문자열은 그대로 들어가며 시각 값은 숫자로 해석(`atof`)됩니다. 시각의 단위는 시간(hour)이며 `hoursPerSecond`와 같은 단위입니다. |
| time     | number                    | optional   | `times[0]`                       | 초기 시각. `times`의 최소~최대 범위로 제한됩니다.                                                                                                          |

**encoding** : 프레임 PNG의 인코딩 규격 (생략 가능)

| Name          | Type   | Attributes | Default            | Description                                                                         |
| :------------ | :----- | :--------- | :----------------- | :---------------------------------------------------------------------------------- |
| encoding.type | string | optional   | `"dir8-logspeed8"` | 인코딩 방식. 현재 `"dir8-logspeed8"`만 지원하며 다른 값은 경고 후 이 방식으로 처리됩니다. |
| encoding.smin | number | optional   | 0.0001             | 유속 최솟값(m/s). G 채널 1에 해당. `0 < smin < smax`이어야 합니다.                  |
| encoding.smax | number | optional   | 5.0                | 유속 최댓값(m/s). G 채널 255에 해당.                                                |

**prefetch** : 시각 프레임 미리 받기 (생략 가능)

| Name            | Type   | Attributes | Default | Description                                                                                       |
| :-------------- | :----- | :--------- | :------ | :------------------------------------------------------------------------------------------------ |
| prefetch.ahead  | number | optional   | 3       | 현재 시각 구간 이후로 미리 받아 둘 프레임 수. 0~16으로 제한됩니다. (`loop`가 true면 끝에서 처음으로 이어서 계산)   |
| prefetch.behind | number | optional   | 1       | 현재 시각 구간 이전으로 유지할 프레임 수. 0~16으로 제한됩니다.                                    |

**tiles** : 확대 시 고해상도 타일 (생략하면 타일을 사용하지 않음)

> `tiles`를 지정하면 `urlTemplate`에 해당하는 타일 PNG를 카메라가 확대된 화면에 맞춰 추가로 요청하고, 파티클은 두 시각이 모두 로드된 가장 세밀한 타일에서 유속을 샘플링합니다. 타일이 없으면 전체 범위 프레임을 사용합니다. 타일 격자는 엔진 타일 격자와 같습니다(레벨 L의 한 변 = 36°/2^L, `x`는 경도 -180°에서 동쪽으로, `y`는 위도 -90°에서 북쪽으로 증가).

| Name            | Type    | Attributes | Default | Description                                                                                                                                                    |
| :-------------- | :------ | :--------- | :------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| tiles.enabled   | boolean | optional   | true    | 타일 사용 여부. (`tiles` 객체를 지정했을 때의 기본값)                                                                                                          |
| tiles.urlTemplate | string |           |         | 타일 PNG URL 템플릿. 치환 문자열: `{time}`, `{index}`, `{bbox}`(`minLon,minLat,maxLon,maxLat`), `{size}`, `{w}`, `{h}`(모두 `tileSize`), `{level}`, `{x}`, `{y}`. `enabled`가 true인데 비어있으면 타일 기능이 꺼집니다. |
| tiles.tileSize  | number  | optional   | 256     | 타일 한 장의 픽셀 크기(`{size}`, `{w}`, `{h}`에 들어가는 값). 16~1024로 제한됩니다.                                                                            |
| tiles.minLevel  | number  | optional   | 6       | 사용할 최소 타일 레벨. 0~20으로 제한됩니다.                                                                                                                    |
| tiles.maxLevel  | number  | optional   | 12      | 사용할 최대 타일 레벨. `minLevel`~20으로 제한됩니다.                                                                                                           |
| tiles.cacheSize | number  | optional   | 128     | CPU 메모리에 유지할 로드된 타일 수 상한. 8 이상이며, 넘으면 오래 쓰지 않은 타일부터 해제됩니다(`tileUnload` 이벤트 발생).                                       |
| tiles.maxVisible | number | optional   | 64      | 한 시각에 요청할 화면 타일 수 상한. 1~512로 제한됩니다.                                                                                                        |

**particles** : 파티클 표현 (생략 가능)

| Name                      | Type                                  | Attributes | Default  | Description                                                                                                                                 |
| :------------------------ | :------------------------------------ | :--------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------ |
| particles.count           | number                                | optional   | 6000     | 파티클 수. 1~100000으로 제한됩니다.                                                                                                         |
| particles.trail           | number                                | optional   | 40       | 파티클 꼬리 길이(꼬리를 이루는 선분 수). 2~128로 제한됩니다.                                                                                |
| particles.speedScale      | number                                | optional   | 1.0      | 유속 1 m/s일 때 파티클이 프레임당 이동하는 화면 거리(CSS px).                                                                               |
| particles.speedExponent   | number                                | optional   | 0.2      | 화면 이동량이 유속의 몇 제곱에 비례하는지 지정합니다. 값이 작을수록 약한 해류와 강한 조류의 꼬리 길이 차이가 줄어듭니다.                     |
| particles.lifetime        | array(number)\[2] \| number           | optional   | \[40, 120] | 파티클 수명(프레임). `[최소, 최대]` 또는 단일 숫자(최소=최대). 최소 1, 최대는 최소 이상으로 보정됩니다.                                      |
| particles.lineWidth       | number                                | optional   | 1.1      | 선 굵기(CSS px).                                                                                                                            |
| particles.rebalance       | boolean                               | optional   | true     | 화면 이동 재배치. 카메라 이동으로 새로 드러난 영역으로 파티클을 옮겨 채웁니다.                                                              |
| particles.densityBalance  | boolean                               | optional   | true     | 밀도 균등화. 화면 칸별 파티클 수를 보이는 바다 면적에 비례하도록 맞춥니다.                                                                  |
| particles.prefill         | boolean                               | optional   | true     | 새 파티클 꼬리 미리 채우기. 태어날 때 유속장을 거꾸로 따라가 꼬리를 미리 만들어 처음부터 완전한 꼬리를 가지게 합니다.                       |
| particles.hideWhileMoving | boolean                               | optional   | false    | 움직이는 동안 숨기기. 줌·이동 중에는 흐름선을 감추고, 멈추면 새 화면에 다시 뿌려 서서히 나타냅니다.                                         |
| particles.lod             | boolean                               | optional   | false    | 지리 LOD. 파티클마다 LOD 레벨을 두어 그 위치의 줌 레벨에 따라 보이는 정도를 정합니다. (켜면 파티클 배열이 `count`의 2배로 확보됩니다.)        |

**colorRamp** : 유속 색상 (생략 가능)

| Name           | Type                                                                                        | Attributes | Default              | Description                                                                                                                                                                                  |
| :------------- | :------------------------------------------------------------------------------------------ | :--------- | :------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| colorRamp.min  | number                                                                                      | optional   | 0.0                  | 색상 램프의 최소 유속(m/s). 이 값 이하의 유속은 첫 번째 색을 사용합니다.                                                                                                                     |
| colorRamp.max  | number                                                                                      | optional   | 1.0                  | 색상 램프의 최대 유속(m/s). `max <= min`이면 `min + 0.000001`로 보정됩니다.                                                                                                                  |
| colorRamp.stops | array(array) | optional | 6단계 기본 램프 | `[[위치, 색], ...]` ([JSCurrentFlowLayer.ColorRampOptions](jscurrentflowlayer.md#jscurrentflowlayer.colorrampoptions)의 `stops`와 같은 형식). 위치는 `min`~`max`를 0~1로 정규화한 값, 색은 `"#RGB"`, `"#RRGGBB"`, `"#RRGGBBAA"` 또는 `[r, g, b(, a)]`. 형식이 잘못된 항목은 건너뛰며, 유효한 항목이 하나도 없으면 기본 램프를 사용합니다. |

기본 램프(위치 → 색): 0.0 `#78D2FF`, 0.2 `#00FFC8`, 0.4 `#B4FF00`, 0.6 `#FFDC00`, 0.8 `#FF7800`, 1.0 `#FF2828`.

**background** : 배경 유속 색상 (생략 가능)

> 해수면에 유속을 색상으로 칠하는 배경 면입니다. 두 시각의 PNG를 셰이더에서 유속으로 복원하고 보간해 `colorRamp`로 채색합니다.

| Name               | Type    | Attributes | Default | Description                    |
| :----------------- | :------ | :--------- | :------ | :----------------------------- |
| background.visible | boolean | optional   | false   | 배경 유속 색상 표시 여부.      |
| background.opacity | number  | optional   | 0.65    | 배경 불투명도. 0~1로 제한됩니다. |

**표현 / 재생**

| Name           | Type     | Attributes | Default            | Description                                                                                                                                  |
| :------------- | :------- | :--------- | :----------------- | :------------------------------------------------------------------------------------------------------------------------------------------- |
| altitude       | number   | optional   | 0.0                | 수면 높이(m). 파티클과 배경이 그려지는 해수면 고도입니다.                                                                                    |
| depthTest      | boolean  | optional   | true               | 지형·건물에 의한 가려짐 판정 사용 여부.                                                                                                      |
| depthBias      | number   | optional   | 0.002              | 해수면과 지형이 겹쳐 깜빡이는 현상(z-fighting)을 막기 위해 깊이를 시선 방향으로 당기는 비율(카메라 거리 대비). 0~0.05로 제한됩니다.         |
| opacity        | number   | optional   | 1.0                | 레이어 전체 불투명도. 0~1로 제한됩니다.                                                                                                      |
| visible        | boolean  | optional   | true               | 레이어 표시 여부. false이면 그리기, 시간 진행, 데이터 요청이 모두 멈춥니다.                                                                  |
| loop           | boolean  | optional   | true               | 재생이 마지막 시각에 도달했을 때 처음으로 되돌아가 반복할지 여부. false이면 마지막 시각에서 재생이 멈춥니다.                                 |
| hoursPerSecond | number   | optional   | 0.6667 (= 1 / 1.5) | 재생 속도. 실제 1초당 진행하는 시각(시간 단위). [play()](jscurrentflowlayer.md#play-options-boolean)에서 값을 지정하면 그 값으로 바뀝니다.     |
| autoPlay       | boolean  | optional   | false              | 생성 직후 재생을 시작할지 여부.                                                                                                              |

**이벤트 콜백** (모두 생략 가능, 함수가 아니면 무시됩니다. 생성 후에는 [on(event, callback)](jscurrentflowlayer.md#on-event-callback-boolean)으로 교체할 수 있습니다.)

| Name         | Type     | Attributes | Description                                                                                                                                |
| :----------- | :------- | :--------- | :----------------------------------------------------------------------------------------------------------------------------------------- |
| onFrameLoad  | function | optional   | 전체 범위 프레임 한 장이 로드될 때 호출. 인자: [JSCurrentFlowLayer.FrameLoadEvent](jscurrentflowlayer.md#jscurrentflowlayer.frameloadevent). |
| onTileLoad   | function | optional   | 타일 한 장이 로드될 때 호출. 인자: [JSCurrentFlowLayer.TileLoadEvent](jscurrentflowlayer.md#jscurrentflowlayer.tileloadevent).              |
| onTileUnload | function | optional   | 로드된 타일이 캐시에서 해제될 때 호출. 인자: [JSCurrentFlowLayer.TileUnloadEvent](jscurrentflowlayer.md#jscurrentflowlayer.tileunloadevent). |
| onError      | function | optional   | 프레임·타일 요청이 실패할 때 호출. 인자: [JSCurrentFlowLayer.ErrorEvent](jscurrentflowlayer.md#jscurrentflowlayer.errorevent).              |
