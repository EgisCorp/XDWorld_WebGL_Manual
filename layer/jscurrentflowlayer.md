---
description: 해류·조류 등 시간별 유속 격자 데이터를 파티클로 흘려 표현하는 흐름 레이어 객체의 API 입니다.
---

# JSCurrentFlowLayer

> [JSFlowLayerList.createCurrentFlowLayer(options)](jsflowlayerlist.md#createcurrentflowlayer-options-jscurrentflowlayer) 또는 [JSFlowLayerList.getLayer(name)](jsflowlayerlist.md#getlayer-name-jscurrentflowlayer)로 얻는 레이어 핸들입니다.
>
> 해류·조류처럼 시각별로 제공되는 유속 격자(PNG) 데이터를 파티클로 흘려 표현합니다. 레이어를 [remove()](jscurrentflowlayer.md#remove-boolean)(또는 `JSFlowLayerList.removeLayer`)로 제거한 뒤에는 핸들의 모든 함수가 아무 동작 없이 false 또는 null을 반환합니다. 이때 핸들의 [isValid()](jscurrentflowlayer.md#isvalid-boolean)는 false를 반환합니다.

```javascript
let flow = Module.getFlowLayerList().createCurrentFlowLayer({
    name: "current_flow",
    bbox: [124.0, 33.0, 132.0, 39.0],
    frameUrl: "https://example.com/api/frame/{time}.png",
    times: [1, 2, 3, 4, 5, 6],
});

// 이미 생성된 레이어를 이름으로 가져오기
let sameFlow = Module.getFlowLayerList().getLayer("current_flow");
```

## 사용 흐름

레이어는 **JS에서 데이터를 밀어 넣는 방식이 아니라, 엔진이 URL을 보고 직접 받아오는 방식**입니다. 콜백으로 데이터를 전달할 필요가 없습니다.

1.  **서버 준비** : 시각마다 격자 PNG(RGBA) 한 장을 제공합니다. `bbox` 전체를 덮는 프레임을 `frameUrl`로, (선택) 확대용 고해상도 타일을 `tiles.urlTemplate`로 제공합니다. 엔진이 브라우저 `fetch`로 요청하므로 다른 도메인이면 CORS 허용이 필요합니다.
2.  **레이어 생성** : [createCurrentFlowLayer](jsflowlayerlist.md#createcurrentflowlayer-options-jscurrentflowlayer)는 데이터 로드를 기다리지 않고 즉시 반환합니다. 첫 렌더링 시점부터 엔진이 프레임을 요청합니다.
3.  **프레임 로드** : 현재 시각이 속한 구간 `[times[k], times[k+1]]`의 두 장이 모두 로드되어야 화면에 표시되고 [getValueAt](jscurrentflowlayer.md#getvalueat-lon-lat-jscurrentflowlayer.flowvalue)이 값을 돌려줍니다. 그 전에는 아무것도 그려지지 않으며 `getValueAt`은 null입니다. 두 장의 유속은 시각에 따라 선형 보간됩니다.
4.  **미리 받기·교체** : 앞(`prefetch.ahead`)·뒤(`prefetch.behind`) 프레임을 미리 받아 두며, 시각이 새 구간으로 넘어가도 새 구간의 두 장이 모두 도착하기 전까지는 이전 구간을 계속 사용합니다. 재생 중 다음 구간이 아직 로드되지 않았으면 구간 끝에서 기다렸다가 이어서 재생합니다(건너뛰지 않음). `tiles`를 쓰는 경우 지금 화면에 쓰는 타일이 새 구간의 두 시각에도 모두 로드될 때까지(최대 1.5초) 이전 구간을 유지하며, 재생 중(또는 최근 1.5초 안에 [setTime](jscurrentflowlayer.md#gettime-settime-time-number-boolean)으로 시각을 앞으로 넘기는 중)에는 다음 두 시각의 타일도 미리 받아 둡니다.
5.  **타일(선택)** : `tiles`를 지정하면 카메라 확대 정도에 맞는 타일을 추가로 요청하고, 파티클은 두 시각이 모두 로드된 가장 세밀한 타일에서 유속을 샘플링합니다.
6.  **비동기 상태 확인** : [on](jscurrentflowlayer.md#on-event-callback-boolean)의 `frameLoad`/`tileLoad`/`tileUnload`/`error` 이벤트, 또는 [getStatus()](jscurrentflowlayer.md#getstatus-jscurrentflowlayer.flowstatus)의 `pending`(요청 중인 프레임·타일 수), `framesLoaded`, `activeTime` 등으로 로딩 진행 상황을 확인할 수 있습니다.
7.  **실패 처리** : 요청이 실패해도 이전에 로드한 프레임을 계속 표시하고, 프레임은 3초 뒤, 타일은 5초 뒤에 다시 요청합니다. 실패할 때마다 `error` 이벤트가 발생합니다.

* Note
  * 레이어 표시가 꺼져 있으면([setVisible(false)](jscurrentflowlayer.md#getvisible-setvisible-visible-boolean-boolean)) 그리기뿐 아니라 시간 진행과 데이터 요청도 멈춥니다.
  * 평면(2D) 지도 모드에서는 그려지지 않습니다.
  * 지형·건물이 그려진 뒤에 그려지므로 깊이 버퍼로 가려짐을 판정합니다([setDepthTest](jscurrentflowlayer.md#setdepthtest-on-boolean)).
  * 흐름선은 기본적으로 수면 높이(`altitude`)에 그려집니다. 수면보다 높은 지형에서도 흐름선이 보이게 하려면 지형 결합([setUnionTerrain](jscurrentflowlayer.md#getunionterrain-setunionterrain-options-boolean-boolean))을 켜십시오. 지구 뒷면 판정은 눈과 점을 잇는 선분이 수면 구(수면 높이 - 50m)를 지나는지로 하므로, 카메라보다 높은 산 위의 흐름선도 틸트를 낮췄을 때 사라지지 않습니다.
  * `times`와 `hoursPerSecond`의 시간 단위는 시간(hour)입니다. 격자 데이터의 유속 단위는 m/s입니다.

### 데이터 형식

서버가 제공하는 PNG는 아래 규격(`encoding.type = "dir8-logspeed8"`)을 따라야 합니다. 이미지는 색 변환이나 premultiply 없이 읽히며, 행 0이 북쪽이고 픽셀 중심이 경위도 등간격으로 배치된 격자입니다.

| Channel | Description                                                                                                                      |
| :------ | :------------------------------------------------------------------------------------------------------------------------------- |
| R       | 흐르는 방향 `atan2(v, u)`. 0~255 = 0~360° (동쪽 0°, 반시계 방향).                                                                |
| G       | 유속의 로그 눈금. 0 = `smin` 미만(정지), 1~255 = `smin`~`smax` (로그 등간격).                                                    |
| A       | 255 = 바다, 0 = 육지·격자 밖·해당 시각에 건조한 칸. 육지로는 입자가 흐르지 않습니다.                                              |

* 전체 범위 프레임은 `bbox` 전체를, 타일은 엔진 타일 격자(레벨 L의 한 변 36°/2^L, `x`는 경도 -180°에서 동쪽으로, `y`는 위도 -90°에서 북쪽으로 증가)의 해당 영역을 같은 규격으로 덮습니다.
* **원시 RGBA 응답(선택)** : 응답의 `Content-Type`이 `application/x-xdcf-rgba`로 시작하면 PNG 디코딩을 건너뛰고 본문을 그대로 격자로 읽습니다. 본문 = 너비·높이(uint32 little-endian 2개, 8바이트) + RGBA 픽셀(`너비 × 높이 × 4`바이트)이며 채널 규격은 위 표와 같습니다. 본문이 `8 + 너비 × 높이 × 4`바이트보다 짧으면 요청 실패로 처리합니다. `fetch`를 가로채 앱이 유속장을 직접 만들어 주는 경우(재생 중 초당 수십~수백 장) PNG 압축·해제 비용을 없애기 위한 경로입니다.

## Function

### getName() → string

> 레이어 이름을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 레이어 이름.
    -   "": 제거되어 유효하지 않은 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
let flow = Module.getFlowLayerList().getLayer("current_flow");
console.log(flow.getName());
```

{% endtab %}
{% endtabs %}

### isValid() → boolean

> 레이어가 아직 유효한지(제거되지 않았는지) 확인합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 유효한 레이어.
    -   false: 제거된 레이어. 이 핸들은 다시 사용할 수 없습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
if (flow.isValid()) {
    flow.play();
}
```

{% endtab %}
{% endtabs %}

### play(options) → boolean

> 시간 재생을 시작합니다.
>
> 시각이 `hoursPerSecond`(실제 1초당 진행하는 시간) 속도로 진행되며, 마지막 시각에 도달하면 생성 옵션 `loop`가 true일 때 처음으로 돌아가 반복하고, false이면 마지막 시각에서 재생이 멈춥니다. `loop`가 false로 마지막 시각에서 멈춘 뒤에는 [setTime](jscurrentflowlayer.md#gettime-settime-time-number-boolean)으로 시각을 되돌린 뒤 `play()`를 호출하십시오.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                                                | Description                                                                                                         |
| :------ | :-------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------ |
| options | number \| [JSCurrentFlowLayer.PlayOptions](jscurrentflowlayer.md#jscurrentflowlayer.playoptions) | 재생 속도(시간/초) 숫자 또는 옵션 객체. 생략하거나 0 이하이면 기존 속도를 유지합니다(초기값은 생성 옵션 `hoursPerSecond`). |

-   Return
    -   true: 재생 시작.
    -   false: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.play(); // 현재 속도로 재생
flow.play({ hoursPerSecond: 2 }); // 1초에 2시간씩 진행
flow.play(0.5); // 숫자만 전달해도 됩니다.
```

{% endtab %}
{% endtabs %}

### pause() → boolean

> 시간 재생을 일시정지합니다. 파티클은 현재 시각의 유속장으로 계속 흐릅니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 정지됨.
    -   false: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.pause();
```

{% endtab %}
{% endtabs %}

### isPlaying() → boolean

> 시간이 재생 중인지 반환합니다. `loop`가 false인 레이어가 마지막 시각에 도달하면 자동으로 false가 됩니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 재생 중.
    -   false: 정지 상태이거나 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
if (flow.isPlaying()) {
    flow.pause();
} else {
    flow.play();
}
```

{% endtab %}
{% endtabs %}

### setParticleOptions(options) → boolean

> 파티클 표현 옵션을 변경합니다. 전달한 필드만 변경되며 전달하지 않은 필드(또는 undefined/null)는 현재 값을 유지합니다. 각 필드의 의미와 생성 시 기본값은 [JSFlowLayerList.CreateCurrentFlowLayerOptions](jsflowlayerlist.md#jsflowlayerlist.createcurrentflowlayeroptions)의 `particles`와 같습니다.
>
> `count` 또는 `trail`이 바뀌면 파티클이 다시 생성됩니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                                                       | Description    |
| :------ | :--------------------------------------------------------------------------------------------------------- | :------------- |
| options | [JSCurrentFlowLayer.ParticleOptions](jscurrentflowlayer.md#jscurrentflowlayer.particleoptions)            | 파티클 옵션.   |

-   Return
    -   true: 적용됨.
    -   false: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.setParticleOptions({
    count: 10000,
    trail: 50,
    lifetime: [60, 150],
    lineWidth: 1.5,
    hideWhileMoving: true,
});
```

{% endtab %}
{% endtabs %}

### setColorRamp(options) → boolean

> 유속 색상 램프를 변경합니다. 파티클과 배경 유속 색상에 모두 적용됩니다.
>
> `min`/`max`를 생략하면 현재 값을 유지하고, `stops`를 생략하면 현재 색상 단계를 유지합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                                              | Description        |
| :------ | :------------------------------------------------------------------------------------------------ | :----------------- |
| options | [JSCurrentFlowLayer.ColorRampOptions](jscurrentflowlayer.md#jscurrentflowlayer.colorrampoptions) | 색상 램프 옵션.    |

-   Return
    -   true: 적용됨.
    -   false: 제거된 레이어이거나, `stops`를 지정했지만 유효한 항목이 하나도 없는 경우(콘솔에 `Failed to parse colorRamp.stops.` 경고, 아무것도 변경되지 않음).

{% endtab %}
{% tab title="Template" %}

```javascript
flow.setColorRamp({
    min: 0.0,
    max: 2.0,
    stops: [
        [0.0, "#78D2FF"],
        [0.5, "#FFDC00"],
        [1.0, [255, 40, 40]],
    ],
});
```

{% endtab %}
{% endtabs %}

### setBackground(options) → boolean

> 해수면 배경 유속 색상 면의 표시 여부와 불투명도를 설정합니다. 배경은 두 시각의 격자를 `colorRamp`로 채색해 해수면에 칠합니다.
>
> 전달하지 않은 필드는 현재 값을 유지합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                                              | Description  |
| :------ | :------------------------------------------------------------------------------------------------ | :----------- |
| options | [JSCurrentFlowLayer.BackgroundOptions](jscurrentflowlayer.md#jscurrentflowlayer.backgroundoptions) | 배경 옵션.   |

-   Return
    -   true: 적용됨.
    -   false: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.setBackground({ visible: true, opacity: 0.5 });
```

{% endtab %}
{% endtabs %}

### setDepthTest(on) → boolean

> 지형·건물에 의한 가려짐 판정을 켜거나 끕니다. 끄면 지형·건물 뒤에 있는 흐름도 항상 보입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                    |
| :--- | :------ | :------------------------------------------------------------- |
| on   | boolean | <p>true: 가려짐 판정 사용(기본).<br>false: 사용 안 함.</p>      |

-   Return
    -   true: 적용됨.
    -   false: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.setDepthTest(false);
```

{% endtab %}
{% endtabs %}

### getStatus() → [JSCurrentFlowLayer.FlowStatus](jscurrentflowlayer.md#jscurrentflowlayer.flowstatus)

> 레이어의 로딩·재생·렌더링 상태를 객체로 반환합니다.
>
> 로딩 진행 확인용 필드(`framesLoaded`, `tilesLoaded`, `pending` 등)와 성능·내부 동작 진단용 필드가 함께 들어있습니다. 호출 시 모든 파티클을 순회해 값을 계산하므로 매 프레임 호출하지 말고 디버깅·모니터링 용도로 가끔 호출하십시오.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSCurrentFlowLayer.FlowStatus](jscurrentflowlayer.md#jscurrentflowlayer.flowstatus): 상태 객체.
    -   null: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
let status = flow.getStatus();
console.log("로드된 프레임:", status.framesLoaded, "요청 중:", status.pending);
console.log("파티클 수:", status.particles, "그리기(ms):", status.drawMs);
```

{% endtab %}
{% endtabs %}

### getValueAt(lon, lat) → [JSCurrentFlowLayer.FlowValue](jscurrentflowlayer.md#jscurrentflowlayer.flowvalue)

> 지정한 경위도의 유속(현재 화면에 쓰이는 시각 쌍을 보간한 값)을 조회합니다.
>
> 확대용 타일이 로드되어 있으면 두 시각이 모두 로드된 가장 세밀한 타일에서, 없으면 전체 범위 프레임에서 값을 읽습니다. 해당 위치가 바다가 아닌 경우(육지, `bbox` 밖, 두 시각 모두 건조)나 아직 첫 프레임 쌍이 로드되지 않은 경우에는 null을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                |
| :--- | :----- | :----------------------------------------- |
| lon  | number | 경도(Degree). `bbox`와 같은 경도 체계.     |
| lat  | number | 위도(Degree).                              |

-   Return
    -   [JSCurrentFlowLayer.FlowValue](jscurrentflowlayer.md#jscurrentflowlayer.flowvalue): 유속 정보.
    -   null: 값이 없는 경우(제거된 레이어, 데이터 미로드, 육지·범위 밖).

{% endtab %}
{% tab title="Template" %}

```javascript
let v = flow.getValueAt(127.5, 35.2);
if (v !== null) {
    console.log("유속(m/s):", v.speed, "흐르는 방위(진북 기준 시계방향):", v.bearing);
}
```

{% endtab %}
{% endtabs %}

### getTimes() → array(number)

> 레이어에 등록된 시각 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   array(number): 생성 옵션 `times`를 숫자로 변환한 오름차순 배열(최대 4096개). 제거된 레이어는 빈 배열.

{% endtab %}
{% tab title="Template" %}

```javascript
let times = flow.getTimes();
flow.setTime(times[times.length - 1]); // 마지막 시각으로 이동
```

{% endtab %}
{% endtabs %}

### on(event, callback) → boolean

> 이벤트 핸들러를 등록합니다. 이벤트마다 핸들러는 하나이며, 같은 이벤트에 다시 등록하면 이전 핸들러가 교체됩니다. 생성 옵션의 `onFrameLoad` 등과 같은 핸들러를 가리킵니다.
>
> 이벤트 이름은 대소문자를 구분하지 않으며 `on` 접두사를 붙여(`"onFrameLoad"`) 써도 됩니다. 핸들러는 엔진 내부 처리가 끝난 뒤 비동기로 호출되며, 핸들러 안의 예외는 콘솔에 `[CurrentFlow] event handler` 오류로 출력되고 엔진에 전파되지 않습니다. 핸들러 안에서 [remove()](jscurrentflowlayer.md#remove-boolean)를 호출해도 안전합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description                                                            |
| :------- | :------- | :--------------------------------------------------------------------- |
| event    | string   | 이벤트 이름. 아래 표 참고.                                             |
| callback | function | 이벤트 핸들러. 함수가 아닌 값(null 등)을 전달하면 핸들러가 해제됩니다. |

| event          | 발생 시점                                                                                                  | callback 인자                                                                                           |
| :------------- | :--------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------ |
| `"frameLoad"`  | 전체 범위 프레임 한 장이 로드되었을 때.                                                                    | [FrameLoadEvent](jscurrentflowlayer.md#jscurrentflowlayer.frameloadevent)                               |
| `"tileLoad"`   | 확대용 타일 한 장이 로드되었을 때.                                                                         | [TileLoadEvent](jscurrentflowlayer.md#jscurrentflowlayer.tileloadevent)                                 |
| `"tileUnload"` | 로드된 타일이 캐시 한도(`tiles.cacheSize`) 초과로 메모리에서 해제될 때. (레이어 제거 시에는 발생하지 않음) | [TileUnloadEvent](jscurrentflowlayer.md#jscurrentflowlayer.tileunloadevent)                             |
| `"error"`      | 프레임·타일 요청이 실패했을 때. 재시도(프레임 3초, 타일 5초 후)에도 실패하면 매번 다시 발생합니다.          | [ErrorEvent](jscurrentflowlayer.md#jscurrentflowlayer.errorevent)                                       |

-   Return
    -   true: 등록 성공.
    -   false: 제거된 레이어이거나, 알 수 없는 이벤트 이름인 경우(콘솔에 `Unknown event` 경고).

{% endtab %}
{% tab title="Template" %}

```javascript
flow.on("frameLoad", function (e) {
    console.log("프레임 로드:", e.time, e.width + "x" + e.height, e.ms + "ms");
});

flow.on("error", function (e) {
    console.warn("로드 실패:", e.url, e.status);
});

flow.on("tileLoad", null); // 핸들러 해제
```

{% endtab %}
{% endtabs %}

### remove() → boolean

> 레이어를 제거합니다. 진행 중인 데이터 요청은 취소되고 GPU 자원이 해제됩니다. 제거 후 이 핸들은 유효하지 않으며, 같은 이름으로 새 레이어를 만들 수 있습니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 제거 성공.
    -   false: 이미 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.remove();
console.log(flow.isValid()); // false
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getTime(), setTime(time) → number, boolean

> 레이어의 현재 시각을 조회하거나 설정합니다.
>
> 시각은 `times`의 최소~최대 범위로 제한됩니다. 설정해도 재생 상태는 바뀌지 않으며, 새 시각이 속한 구간의 두 프레임(`tiles`를 쓰면 지금 화면에 쓰는 타일의 두 시각분도, 최대 1.5초까지)이 로드되기 전까지는 화면이 이전 구간 그대로 유지됩니다. 시각을 현재보다 앞으로 설정하면 그 뒤 1.5초 동안은 엔진 재생과 같이 다음 두 시각의 타일을 미리 받아 두므로, `setTime`을 반복 호출해 직접 재생하는 앱도 별도 처리 없이 타일 지연이 줄어듭니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                       |
| :--- | :----- | :------------------------------------------------ |
| time | number | 설정할 시각(`times`와 같은 단위, 최소~최대로 제한). |

-   Return
    -   `getTime()`: number - 현재 시각. 제거된 레이어는 NaN.
    -   `setTime(time)`: boolean - true: 설정됨 / false: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.setTime(120.5);
console.log(flow.getTime()); // 120.5
```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean, boolean

> 레이어 표시 여부를 조회하거나 설정합니다.
>
> 표시가 꺼지면 그리기뿐 아니라 시간 진행과 데이터 요청도 멈춥니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                     |
| :------ | :------ | :---------------------------------------------- |
| visible | boolean | <p>true: 표시.<br>false: 숨김.</p>              |

-   Return
    -   `getVisible()`: boolean - 표시 여부. 제거된 레이어는 false.
    -   `setVisible(visible)`: boolean - true: 설정됨 / false: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.setVisible(false);
console.log(flow.getVisible()); // false
```

{% endtab %}
{% endtabs %}

### getOpacity(), setOpacity(opacity) → number, boolean

> 레이어 전체 불투명도를 조회하거나 설정합니다. 설정값은 0~1로 제한됩니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                       |
| :------ | :----- | :-------------------------------- |
| opacity | number | 불투명도(0.0 ~ 1.0, 범위 밖은 제한). |

-   Return
    -   `getOpacity()`: number - 현재 불투명도. 제거된 레이어는 NaN.
    -   `setOpacity(opacity)`: boolean - true: 설정됨 / false: 제거된 레이어.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.setOpacity(0.7);
console.log(flow.getOpacity()); // 0.7
```

{% endtab %}
{% endtabs %}

### getUnionTerrain(), setUnionTerrain(options) → boolean, boolean

> 지형 결합(흐름선을 그 자리 지형 높이에 얹기) 사용 여부를 조회하거나 설정합니다.
>
> 꺼져 있으면(기본) 파티클이 수면 높이(`altitude`)에 그려져, 수면보다 높은 섬·산·해안 DEM 구간에서는 흐름선이 지형 속으로 들어가 가려집니다. 켜면 파티클의 높이가 **현재 화면에 그려진 지형 면의 높이 + 띄우는 높이(`terrainOffset`)** 로 바뀌되, 그 값이 수면 높이보다 높을 때만 적용되고 지형이 수면보다 낮거나 DEM이 아직 없는 곳은 수면 높이 그대로입니다. 지형 면이 카메라를 등진 비탈의 선분은 흐려집니다. 값이 실제로 바뀌면 파티클을 새로 뿌립니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                                              | Description                                                                                                                                                                              |
| :------ | :------------------------------------------------------------------------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| options | boolean \| [JSCurrentFlowLayer.UnionTerrainOptions](jscurrentflowlayer.md#jscurrentflowlayer.unionterrainoptions) | `true`/`false`: 지형 결합 켜기/끄기(띄우는 높이는 그대로). 객체: `enabled`로 켜기/끄기(생략하면 true), `offset`으로 띄우는 높이(m, 0~1000으로 제한) 변경(생략하면 그대로). |

-   Return
    -   `getUnionTerrain()`: boolean - 현재 지형 결합 여부. 제거된 레이어는 false.
    -   `setUnionTerrain(options)`: boolean
        -   true: 적용됨.
        -   false: 제거된 레이어, 또는 `options`가 boolean도 객체도 아닌 경우(숫자, 문자열, null, undefined 등. 값은 바뀌지 않습니다).

* Note
  * 생성 옵션 `unionTerrain` / `terrainOffset`([createCurrentFlowLayer](jsflowlayerlist.md#createcurrentflowlayer-options-jscurrentflowlayer))으로 처음부터 켤 수 있습니다. 띄우는 높이 기본값은 2.0m입니다.
  * 현재 띄우는 높이와 켜짐 여부는 [getStatus()](jscurrentflowlayer.md#getstatus-jscurrentflowlayer.flowstatus)의 `unionTerrain`, `terrainOffset`으로도 읽을 수 있습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
flow.setUnionTerrain(true); // 지형 결합 켜기
flow.setUnionTerrain({ enabled: true, offset: 5 }); // 지형 위 5m에 띄워 켜기
flow.setUnionTerrain({ offset: 10 }); // enabled 생략 = 켜기, 띄우는 높이만 10m로
console.log(flow.getUnionTerrain()); // true

flow.setUnionTerrain(false); // 끄기 (띄우는 높이는 보존)
```

{% endtab %}
{% endtabs %}

## Sample

레이어 생성 → 이벤트 등록 → 재생 → 유속 조회 → 제거까지의 전체 예제입니다.

```javascript
let flowList = Module.getFlowLayerList();

// 1시간 간격 240개 시각 (서버는 /api/frame/1.png ... /api/frame/240.png 제공)
let times = [];
for (let t = 1; t <= 240; t++) times.push(t);

// 1) 생성: 데이터는 엔진이 frameUrl/타일 URL로 직접 받아옵니다.
let flow = flowList.createCurrentFlowLayer({
    name: "tidal_current",
    bbox: [124.0, 33.0, 132.0, 39.0],
    frameUrl: "https://example.com/api/frame/{time}.png",
    encoding: { type: "dir8-logspeed8", smin: 0.0001, smax: 5.0 },
    times: times,
    prefetch: { ahead: 3, behind: 1 },
    tiles: {
        urlTemplate: "https://example.com/api/tile/{time}/{level}/{x}/{y}.png",
        tileSize: 256,
        minLevel: 6,
        maxLevel: 12,
    },
    particles: { count: 8000, trail: 40, lineWidth: 1.2 },
    colorRamp: { min: 0.0, max: 1.5 },
    background: { visible: false, opacity: 0.65 },
    loop: true,
    hoursPerSecond: 2.0,
});

if (flow === null) {
    throw new Error("흐름 레이어 생성 실패: 콘솔의 [CurrentFlow] 경고를 확인하십시오.");
}

// 2) 이벤트 등록
let frameCount = 0;
flow.on("frameLoad", function (e) {
    frameCount++;
    console.log("프레임 로드", e.index, "시각", e.time, e.ms.toFixed(0) + "ms");

    // 첫 프레임 쌍이 준비되면 재생 시작 (로드 전에는 getValueAt이 null)
    if (frameCount === 2) {
        flow.setTime(1);
        flow.play({ hoursPerSecond: 2.0 });
    }
});
flow.on("tileLoad", function (e) {
    console.log("타일 로드 level", e.level, "(" + e.idx + "," + e.idy + ")");
});
flow.on("tileUnload", function (e) {
    console.log("타일 해제 level", e.level, "(" + e.idx + "," + e.idy + ")");
});
flow.on("error", function (e) {
    console.warn("로드 실패", e.url, "HTTP", e.status);
});

// 3) 표현 조정
flow.setColorRamp({
    min: 0.0,
    max: 2.0,
    stops: [
        [0.0, "#78D2FF"],
        [0.5, "#FFDC00"],
        [1.0, "#FF2828"],
    ],
});
flow.setBackground({ visible: true, opacity: 0.4 });
flow.setOpacity(0.9);

// 4) 상태·유속 조회
setTimeout(function () {
    let status = flow.getStatus();
    console.log("현재 시각:", flow.getTime(), "재생 중:", flow.isPlaying(), "요청 중:", status.pending);

    let v = flow.getValueAt(127.5, 35.2);
    if (v !== null) {
        console.log("유속", v.speed.toFixed(3), "m/s, 방위", v.bearing.toFixed(1) + "°");
    }
}, 5000);

// 5) 일시정지 / 제거
setTimeout(function () {
    flow.pause();
    flowList.removeLayer("tidal_current"); // 또는 flow.remove()
    console.log(flow.isValid(), flowList.count()); // false 0
}, 30000);
```

## Type Definitions

#### JSCurrentFlowLayer.PlayOptions

> [play(options)](jscurrentflowlayer.md#play-options-boolean) 옵션.

| Name           | Type   | Attributes | Default                                  | Description                                                                |
| :------------- | :----- | :--------- | :--------------------------------------- | :------------------------------------------------------------------------- |
| hoursPerSecond | number | optional   | 현재 재생 속도 (초기값 0.6667 = 1 / 1.5) | 실제 1초당 진행할 시각(시간 단위). 0 이하이거나 생략하면 기존 속도를 유지합니다. |

#### JSCurrentFlowLayer.ParticleOptions

> [setParticleOptions(options)](jscurrentflowlayer.md#setparticleoptions-options-boolean) 옵션. 모든 필드가 optional이며 전달한 필드만 변경됩니다. 숫자 필드는 문자열 숫자도 허용합니다.

| Name            | Type                         | Attributes | Description                                                                                                                       |
| :-------------- | :--------------------------- | :--------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| count           | number                       | optional   | 파티클 수. 0 이하는 무시되며 최대 100000으로 제한됩니다. 값이 바뀌면 파티클이 다시 생성됩니다.                                    |
| trail           | number                       | optional   | 꼬리 길이(선분 수). 0 이하는 무시되며 2~128로 제한됩니다. 값이 바뀌면 파티클이 다시 생성됩니다.                                   |
| speedScale      | number                       | optional   | 유속 1 m/s일 때 프레임당 화면 이동 거리(CSS px). 0 이상만 적용됩니다.                                                             |
| speedExponent   | number                       | optional   | 화면 이동량이 비례하는 유속의 지수. 0 이상만 적용됩니다.                                                                          |
| lifetime        | array(number)\[2] \| number  | optional   | 파티클 수명(프레임). `[최소, 최대]` 또는 단일 숫자(최소=최대). 0 이하 값은 무시되며, 최대가 최소보다 작으면 최소로 보정됩니다.    |
| lineWidth       | number                       | optional   | 선 굵기(CSS px). 0 이하는 무시됩니다.                                                                                             |
| rebalance       | boolean                      | optional   | 카메라 이동으로 새로 드러난 영역에 파티클 재배치.                                                                                 |
| densityBalance  | boolean                      | optional   | 화면 칸별 파티클 수를 바다 면적에 맞춰 균등화.                                                                                    |
| prefill         | boolean                      | optional   | 새 파티클의 꼬리를 태어날 때 미리 채움.                                                                                           |
| hideWhileMoving | boolean                      | optional   | 줌·이동 중에는 흐름선을 숨기고 멈추면 서서히 다시 표시.                                                                           |
| lod             | boolean                      | optional   | 위치별 줌 레벨에 따라 파티클 보이는 정도를 조절하는 지리 LOD.                                                                     |

#### JSCurrentFlowLayer.ColorRampOptions

> [setColorRamp(options)](jscurrentflowlayer.md#setcolorramp-options-boolean) 옵션.

| Name  | Type                  | Attributes | Description                                                                                                                                                                                                                      |
| :---- | :-------------------- | :--------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| min   | number                | optional   | 램프 최소 유속(m/s). 생략하면 현재 값을 유지합니다.                                                                                                                                                                              |
| max   | number                | optional   | 램프 최대 유속(m/s). 생략하면 현재 값을 유지하며, `max <= min`이면 `min + 0.000001`로 보정됩니다.                                                                                                                                |
| stops | array(array)          | optional   | 색상 단계 `[[위치, 색], ...]`. 위치는 `min`~`max`를 0~1로 정규화한 값이며 정렬 순서는 상관없습니다. 색은 `"#RGB"`, `"#RRGGBB"`, `"#RRGGBBAA"` 문자열 또는 `[r, g, b]`, `[r, g, b, a]` 배열(r·g·b는 0~255, a는 0~1, 생략 시 1)입니다. 형식이 잘못된 항목은 건너뛰며 유효한 항목이 없으면 함수가 false를 반환합니다. |

#### JSCurrentFlowLayer.BackgroundOptions

> [setBackground(options)](jscurrentflowlayer.md#setbackground-options-boolean) 옵션.

| Name    | Type    | Attributes | Description                                                                              |
| :------ | :------ | :--------- | :--------------------------------------------------------------------------------------- |
| visible | boolean | optional   | 배경 표시 여부. 생략하면 현재 값을 유지합니다.                                           |
| opacity | number  | optional   | 배경 불투명도. 1을 넘으면 1로 제한되며, 생략하거나 음수이면 현재 값을 유지합니다.         |

#### JSCurrentFlowLayer.UnionTerrainOptions

> [setUnionTerrain(options)](jscurrentflowlayer.md#getunionterrain-setunionterrain-options-boolean-boolean) 의 객체 형식 옵션. 생성 옵션 `unionTerrain`도 같은 형식(`true`/`false` 또는 이 객체)을 받습니다.

| Name    | Type    | Attributes | Default      | Description                                                                                   |
| :------ | :------ | :--------- | :----------- | :-------------------------------------------------------------------------------------------- |
| enabled | boolean | optional   | true         | 지형 결합 켜기/끄기. 생략하면 켭니다.                                                         |
| offset  | number  | optional   | 현재 값 (초기 2.0) | 지형 위로 띄우는 높이(m). 0~1000으로 제한됩니다. 생략하면 현재 값을 유지합니다.         |

#### JSCurrentFlowLayer.FlowValue

> [getValueAt(lon, lat)](jscurrentflowlayer.md#getvalueat-lon-lat-jscurrentflowlayer.flowvalue)가 반환하는 유속 정보.

| Name      | Type   | Description                                                                                                              |
| :-------- | :----- | :----------------------------------------------------------------------------------------------------------------------- |
| u         | number | 동쪽 방향 유속 성분(m/s).                                                                                                |
| v         | number | 북쪽 방향 유속 성분(m/s).                                                                                                |
| speed     | number | 유속 크기(m/s).                                                                                                          |
| direction | number | 흐르는 방향의 수학 각도(Degree, 0~360). 동쪽 0°, 반시계 방향.                                                            |
| bearing   | number | 흘러가는 방위(Degree, 0~360). 진북 0°, 시계 방향. (`bearing = 90 - direction`)                                           |
| time      | number | 레이어의 현재 시각([getTime()](jscurrentflowlayer.md#gettime-settime-time-number-boolean) 값).                           |
| level     | number | 값을 읽은 데이터 해상도. -1 = 전체 범위 프레임, 0 이상 = 해당 레벨의 타일.                                               |

#### JSCurrentFlowLayer.FlowStatus

> [getStatus()](jscurrentflowlayer.md#getstatus-jscurrentflowlayer.flowstatus)가 반환하는 상태 객체.

**로딩 · 재생**

| Name         | Type            | Description                                                                                                              |
| :----------- | :-------------- | :----------------------------------------------------------------------------------------------------------------------- |
| framesLoaded | number          | 메모리에 로드되어 있는 전체 범위 프레임 수.                                                                              |
| framesOnGpu  | number          | 배경 색상용으로 GPU 텍스처로 올라간 프레임 수(배경을 켠 경우에 사용됨).                                                  |
| unionTerrain | boolean         | 현재 지형 결합 여부([getUnionTerrain()](jscurrentflowlayer.md#getunionterrain-setunionterrain-options-boolean-boolean)).                                         |
| terrainOffset | number         | 지형 결합 시 지형 위로 띄우는 높이(m).                                                                                   |
| tilesLoaded  | number          | 로드된 타일 수.                                                                                                          |
| tilesWanted  | number          | 현재 화면에서 요청 대상으로 선택된 타일 수(시각 제외).                                                                   |
| pending      | number          | 요청 중인 프레임·타일 수.                                                                                                |
| frameStates  | array(array)    | 받아 둔·받는 중인 프레임 목록 `[시각, 상태]`. 상태: 0 = 없음, 1 = 받는 중, 2 = 로드됨, 3 = 실패.                         |
| lastFrameMs  | number          | 가장 최근에 로드된 프레임의 요청·디코딩 소요 시간(ms).                                                                   |
| time         | number          | 레이어의 현재 시각.                                                                                                      |
| activeTime   | number \| null  | 지금 화면(파티클·배경)에 실제로 사용 중인 시각. 새 구간이 로드되기 전에는 `time`보다 뒤처질 수 있으며, 아직 사용 가능한 프레임 쌍이 없으면 null. |
| playing      | boolean         | 재생 중 여부.                                                                                                            |

**렌더링 · 진단용**

> 아래 필드는 성능 확인과 내부 동작 진단용입니다. 값의 의미는 엔진 내부 구현에 따라 달라질 수 있으므로 애플리케이션 로직에 사용하지 않는 것을 권장합니다.

| Name            | Type    | Description                                                                                                                     |
| :-------------- | :------ | :------------------------------------------------------------------------------------------------------------------------------ |
| drawMs          | number  | 가장 최근 프레임의 이 레이어 갱신·그리기 소요 시간(ms).                                                                          |
| particles       | number  | 현재 살아있는 파티클 수.                                                                                                        |
| rebalance       | boolean | 현재 `rebalance` 설정값.                                                                                                        |
| densityBalance  | boolean | 현재 `densityBalance` 설정값.                                                                                                   |
| prefill         | boolean | 현재 `prefill` 설정값.                                                                                                          |
| hideWhileMoving | boolean | 현재 `hideWhileMoving` 설정값.                                                                                                  |
| lod             | boolean | 현재 `lod` 설정값.                                                                                                              |
| expDeficit      | number  | 새로 드러난 화면 영역에 더 보내야 할 파티클 수.                                                                                  |
| lineAmount      | number  | 화면에 그려지는 선의 양(파티클별 보이는 정도·나타남 흐림·꼬리 비율의 합).                                                        |
| aliveSlots      | number  | 살아있는 파티클 슬롯 수.                                                                                                        |
| poolSlots       | number  | 파티클 배열(풀) 크기. `lod`가 켜져 있으면 `count`의 2배.                                                                         |
| lastSpawns      | number  | 직전 갱신에서 새로 생성된 파티클 수.                                                                                            |
| spawnTriesLeft  | number  | 직전 갱신에서 남은 파티클 생성 시도 수.                                                                                          |
| stepScale       | number  | 파티클 이동 배율(경과 시간 / (1/60초), 0.25~4 범위로 제한 후 평활).                                                              |
| moveFade        | number  | `hideWhileMoving`에 의한 흐름선 전체 불투명도 배수(0 = 숨김, 1 = 표시).                                                          |
| densityError    | number  | 화면 칸별 파티클 밀도 오차(RMS, 0 = 완전 균일).                                                                                 |
| grid            | object  | 화면을 `w × h` 칸으로 나눈 통계. `w`, `h`(칸 수), `count`(칸별 파티클 수), `sea`(칸별 보이는 바다 비율), `speed`(칸별 평균 유속) 배열은 길이가 `w × h`이며 아래 줄부터 채워집니다(인덱스 = `x + y × w`). |

#### JSCurrentFlowLayer.FrameLoadEvent

> `"frameLoad"` 이벤트 인자.

| Name   | Type   | Description                                   |
| :----- | :----- | :-------------------------------------------- |
| time   | number | 로드된 프레임의 시각.                         |
| index  | number | `times` 배열에서의 인덱스(0부터).             |
| ms     | number | 요청부터 디코딩 완료까지 걸린 시간(ms).       |
| width  | number | 이미지 너비(px).                              |
| height | number | 이미지 높이(px).                              |

#### JSCurrentFlowLayer.TileLoadEvent

> `"tileLoad"` 이벤트 인자.

| Name      | Type   | Description                                                                 |
| :-------- | :----- | :-------------------------------------------------------------------------- |
| level     | number | 타일 레벨.                                                                  |
| idx       | number | 타일 X 인덱스(경도 -180°에서 동쪽으로 증가).                                |
| idy       | number | 타일 Y 인덱스(위도 -90°에서 북쪽으로 증가).                                 |
| rect      | object | 타일 영역(도). `minx`, `miny`, `maxx`, `maxy` (경도·위도의 최소/최대).      |
| time      | number | 타일의 시각.                                                                |
| ms        | number | 요청부터 디코딩 완료까지 걸린 시간(ms).                                     |

#### JSCurrentFlowLayer.TileUnloadEvent

> `"tileUnload"` 이벤트 인자.

| Name  | Type   | Description                                                            |
| :---- | :----- | :--------------------------------------------------------------------- |
| level | number | 타일 레벨.                                                             |
| idx   | number | 타일 X 인덱스.                                                         |
| idy   | number | 타일 Y 인덱스.                                                         |
| rect  | object | 타일 영역(도). `minx`, `miny`, `maxx`, `maxy`.                         |
| time  | number | 타일의 시각.                                                           |

#### JSCurrentFlowLayer.ErrorEvent

> `"error"` 이벤트 인자. 프레임과 타일 요청 실패 모두에 사용됩니다.

| Name   | Type   | Description                                                                                                                     |
| :----- | :----- | :------------------------------------------------------------------------------------------------------------------------------ |
| time   | number | 실패한 요청의 시각.                                                                                                             |
| url    | string | 요청한 URL.                                                                                                                     |
| status | number | HTTP 상태 코드. 네트워크·CORS·이미지 디코딩 실패 등 HTTP 응답이 없는 경우 0이며, 응답은 왔으나 이미지가 비정상인 경우 200일 수 있습니다. |
| level  | number | 타일 요청이 실패한 경우에만 포함되는 타일 레벨. 프레임 요청 실패에는 없습니다.                                                  |
