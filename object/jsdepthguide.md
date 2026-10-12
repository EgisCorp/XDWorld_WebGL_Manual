---
description: 지하 지층, GLB, 3D Tiles 등 어떤 데이터 위에도 붙일 수 있는 독립 깊이 눈금 가이드(눈금 상자)를 생성 및 설정하기 위한 API 입니다.
---

# JSDepthGuide

> Module.createDepthGuide() API를 통해 생성합니다.
>
> 지하 데이터의 깊이를 읽을 수 있도록 수직벽 4면과 기준면(수평 격자) 1면으로 이루어진 눈금 상자를 세웁니다. 레이어에 등록하는 일반 객체이므로 폴리곤 지층, GLB, 3D Tiles 등 어떤 데이터 위에도 붙일 수 있습니다.
>
> [JSObject3D](jsobject3d.md)를 상속하므로 `setVisible(visible)`, `setMinDistance(distance)`, `setMaxDistance(distance)` 등 [JSObject3D](jsobject3d.md)의 함수와 프로퍼티를 그대로 사용할 수 있습니다(표출 여부 역시 [setVisible(visible)](jsobject3d.md#getvisible-setvisible-visible-boolean)로 제어합니다).

```javascript
var guide = Module.createDepthGuide("ID");
```

## 용도 및 [JSGridAnal](../analysis/jsgridanal.md)의 깊이 가이드와의 차이

| 구분 | JSDepthGuide | [JSGridAnal.setDepthGuide(options)](../analysis/jsgridanal.md#setdepthguide-options-boolean) |
| :-- | :-- | :-- |
| 대상 데이터 | 데이터 종류 제한 없음(폴리곤 지층, GLB, 3D Tiles 등). 격자 분석과 무관하게 단독으로 사용. | 지하 격자 분석(JSGridAnal) 결과에만 표시. |
| 상자 범위 | 사용자가 직접 지정([setBox(options)](jsdepthguide.md#setbox-options-boolean): 수평 코너 4점, 상단/하단/기준면 고도). | 로딩된 격자 데이터에서 자동으로 산출. |
| 눈금 라벨 | 사용자가 직접 지정([setGradation(options)](jsdepthguide.md#setgradation-options-boolean): 벽 하단/상단에 놓을 라벨 값). | 격자의 데이터 값, 기준 고도, 배율에서 자동으로 계산(`mode`에 따라 값 변환). |
| 표시/해제 | 레이어에 등록해야 표시되며([JSLayer.addObject(object, level)](../layer/jslayer.md#addobject-object-level)), 일반 객체처럼 레이어에서 제거. | `setDepthGuide({visible})`로 표시/숨김, `clear()` 시 함께 제거. |

두 가이드는 같은 엔진 구현(눈 위치 기준으로 카메라에서 먼 쪽 수직벽만 그리고, 기준면 격자는 항상 그리는 방식)을 공유하며, 격자 분석을 사용하지 않는 데이터에 깊이 눈금이 필요할 때 `JSDepthGuide`를 사용합니다.

### 사용 시 주의사항

-   화면에 표시되려면 [setBox(options)](jsdepthguide.md#setbox-options-boolean)와 [setGradation(options)](jsdepthguide.md#setgradation-options-boolean)를 모두 설정하고 레이어에 등록해야 합니다. [setBox(options)](jsdepthguide.md#setbox-options-boolean)를 호출하기 전에는 아무것도 그려지지 않습니다.
-   사용자 레이어의 거리 컬링 기본 최대 가시 거리는 3000m입니다. 멀리서도 가이드가 보이려면 [JSLayer.setMaxDistance(distance)](../layer/jslayer.md#getmaxdistance-setmaxdistance-distance-number)로 값을 올려야 합니다. 이 설정은 레이어의 모든 객체에 적용되므로 가이드 전용 레이어를 사용하는 것이 좋습니다.
-   [setBox(options)](jsdepthguide.md#setbox-options-boolean)는 레이어에 등록된 상태에서 호출하면 레이어(옥트리)를 다시 구성합니다. 다른 객체와 한 레이어를 공유하면 호출할 때마다 레이어의 모든 객체가 재삽입되므로 가이드 전용 레이어를 사용하십시오.
-   수직벽은 카메라에서 먼 쪽 벽만 표시되고(가까운 벽은 시야를 가리므로 그리지 않음), 기준면 수평 격자는 항상 표시됩니다.

## Function

### setBox(options) → boolean

> 깊이 눈금 상자의 기하 정보(수평 코너, 상단/하단/기준면 고도)를 설정합니다. 호출에 실패하면 이전 상태가 그대로 유지됩니다.
>
> 기준면 고도가 상단~하단 범위를 벗어나면 상자가 기준면까지 확장됩니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                | Description                                                    |
| :------ | ------------------------------------------------------------------- | ---------------------------------------------------------------- |
| options | [JSDepthGuide.BoxOption](jsdepthguide.md#jsdepthguide.boxoption)     | 상자 설정 옵션.                                                |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   실패 조건
    -   객체가 없는 경우.
    -   `options`가 null/undefined인 경우.
    -   필수 항목(`corners`, `topAltitude`, `bottomAltitude`)이 없거나 타입이 맞지 않는 경우, `datumAltitude`를 지정했는데 숫자가 아닌 경우.
    -   `corners`의 개수가 4개가 아닌 경우, 또는 코너 좌표/고도가 유효한 숫자가 아닌 경우(NaN, 무한대).
    -   `topAltitude`가 `bottomAltitude`보다 작은 경우.
    -   (기준면 확장 후) 상자 높이가 1m 미만인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
// 가이드 전용 레이어 (거리 컬링 상한을 올려야 멀리서도 보임)
var layer = Module.getLayerList().createLayer("DEPTH_GUIDE", Module.ELT_GRAPH);
layer.setMaxDistance(999999999);

var guide = Module.createDepthGuide("STRATA_GUIDE");
guide.setBox({
    corners: [
        new Module.JSVector3D(126.970, 37.520, 0.0),    // SW
        new Module.JSVector3D(126.990, 37.520, 0.0),    // SE
        new Module.JSVector3D(126.990, 37.540, 0.0),    // NE
        new Module.JSVector3D(126.970, 37.540, 0.0)     // NW
    ],
    topAltitude: 260,
    bottomAltitude: -130,
    datumAltitude: 0
});
guide.setGradation({ min: -130, max: 260, unit: "m", mode: "depth" });

layer.addObject(guide, 0);
```

{% endtab %}
{% endtabs %}

### setGradation(options) → boolean

> 깊이 눈금의 라벨 범위와 표시 간격, 단위를 설정합니다. 호출에 실패하면 이전 상태가 그대로 유지됩니다.
>
> 벽 하단에 `min`, 벽 상단에 `max` 값이 놓이며, 그 사이를 `interval` 간격으로 눈금과 라벨이 표시됩니다. `min`이 `max`보다 크면 축이 뒤집혀 라벨이 아래로 갈수록 커집니다(깊이 값을 그대로 표시할 때 사용). 라벨 값은 호출자가 지정한 값이 그대로 쓰이며, `mode`는 그 값의 의미를 기록해 두는 용도일 뿐 눈금이나 라벨 그리기 결과를 바꾸지 않습니다.
>
> 눈금 라벨 텍스트는 ASCII 문자 단위(`"m"` 등)를 사용하십시오(문자열이 바이트 단위로 변환되므로 한글 등 비ASCII 문자는 정상 표시되지 않을 수 있음).

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                          | Description                    |
| :------ | ----------------------------------------------------------------------------- | -------------------------------- |
| options | [JSDepthGuide.GradationOption](jsdepthguide.md#jsdepthguide.gradationoption)   | 눈금 설정 옵션.                |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   실패 조건
    -   객체가 없는 경우.
    -   `options`가 null/undefined인 경우.
    -   필수 항목(`min`, `max`)이 없거나 숫자가 아닌 경우, 또는 `interval`/`unit`/`mode`를 지정했는데 타입이 맞지 않는 경우.
    -   `min` 또는 `max`가 유효한 숫자가 아닌 경우(NaN, 무한대).
    -   `mode`가 `"value"`, `"depth"`, `"elevation"` 중 하나가 아닌 경우.
    -   `min`과 `max`가 같은 경우.
    -   지정한 `interval`로 만들어지는 눈금선이 200개를 넘는 경우(눈금선 개수 = `floor(|max - min| / interval)`). 간격을 임의로 키워 주지 않으므로, 자동 산출을 원하면 `interval`을 0으로 지정하십시오.

{% endtab %}
{% tab title="Template" %}

```javascript
// 눈금 간격 자동 산출, 기준면(0)을 기준으로 한 높이 라벨
guide.setGradation({
    min: -130,
    max: 260,
    interval: 0,
    unit: "m",
    mode: "depth"
});

// 간격만 변경 (unit, mode는 이전 값 유지)
guide.setGradation({ min: -130, max: 260, interval: 50 });

// 위에서 아래로 갈수록 값이 커지는 라벨 (축 반전)
guide.setGradation({ min: 390, max: 0, unit: "m" });
```

{% endtab %}
{% endtabs %}

### setDatumDivision(divW, divH) → boolean

> 기준면 수평 격자의 가로/세로 분할 수를 설정합니다. 기본값은 가로 10 x 세로 10입니다. 데이터 해상도보다 촘촘한 격자선이 데이터를 덮을 때 낮추어 사용합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                      |
| :--- | ------ | ---------------------------------- |
| divW | number | 가로(남북) 분할 수(1~200).        |
| divH | number | 세로(동서) 분할 수(1~200).        |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   실패 조건
    -   객체가 없는 경우.
    -   분할 수가 1 미만이거나 200을 초과하는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
guide.setDatumDivision(4, 4);
```

{% endtab %}
{% endtabs %}

## Type Definitions

#### JSDepthGuide.BoxOption

> [setBox(options)](jsdepthguide.md#setbox-options-boolean) 옵션.

| Name           | Type                                          | Attributes | Default | Description                                                                                                                                              |
| -------------- | --------------------------------------------- | ---------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| corners        | array([JSVector3D](../core/jsvector3d.md))\[4] |            |         | 수평 코너 4점. 경도(x), 위도(y)를 도 단위로 지정하며 고도(z) 값은 사용하지 않습니다. 지리적 **SW → SE → NE → NW** 순서여야 합니다(벽 노멀이 상자 바깥을 향한다는 전제가 이 순서에 걸려 있음). |
| topAltitude    | number                                        |            |         | 상자 상단 고도(meter). `bottomAltitude` 이상이어야 합니다.                                                                                               |
| bottomAltitude | number                                        |            |         | 상자 하단 고도(meter).                                                                                                                                   |
| datumAltitude  | number                                        | optional   | 0       | 기준면(수평 격자) 고도(meter). 생략하면 이전에 지정한 값을 유지합니다(최초 0). 상단~하단 범위를 벗어나면 상자가 기준면까지 확장됩니다.                    |

#### JSDepthGuide.GradationOption

> [setGradation(options)](jsdepthguide.md#setgradation-options-boolean) 옵션.

| Name     | Type   | Attributes | Default | Description                                                                                                                                                                                                                                                              |
| -------- | ------ | ---------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| min      | number |            |         | 벽 하단에 놓을 라벨 값.                                                                                                                                                                                                                                                  |
| max      | number |            |         | 벽 상단에 놓을 라벨 값. `min`보다 작으면 두 값을 교환하고 축을 뒤집어, 라벨이 아래로 갈수록 커집니다. `min`과 같으면 실패합니다.                                                                                                                                         |
| interval | number | optional   | 0       | 눈금 간격(라벨 값 단위). 0, 음수, NaN이면 라벨 범위에서 1/2/5×10ⁿ 값으로 자동 산출합니다(목표 눈금 약 10개). 양수면 그대로 사용하며 눈금선이 200개를 넘으면 실패합니다. 생략하면 이전 값을 유지합니다(최초 0). |
| unit     | string | optional   | "m"     | 라벨에 붙는 단위 문자열. 생략하면 이전 값을 유지합니다.                                                                                                                                                                                                                  |
| mode     | string | optional   | "value" | <p>라벨 값의 종류를 기록하는 값이며 그려지는 결과는 바꾸지 않습니다. 생략하면 이전 값을 유지합니다.<br>"value": 원시 데이터 값.<br>"depth": 기준면을 0으로 둔 높이.<br>"elevation": 해발고도.</p> |
