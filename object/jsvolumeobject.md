---
description: 지도 내 볼륨(연기, 화염, 산불, 수면, 태풍 등) 효과를 표현하기 위한 볼륨(Volume) 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSVolumeObject

> Module.createVolumeObject() API를 생성합니다.
>
> 레이 마칭(Ray Marching) 기반으로, 박스 하나에 3D 밀도 데이터를 올려 한 번에 그리는 방식으로 구름·화염·산불·수면·태풍·불꽃축제 같은 부피감 있는 효과를 표현합니다. [effect](jsvolumeobject.md#effect-property-geteffect-seteffect-effect-number) 프로퍼티로 효과 종류를 선택하며, 효과별로 [setParams(info)](jsvolumeobject.md#setparams-info-string)에 전달하는 세부 옵션 이름이 다릅니다.

```javascript
var volume = Module.createVolumeObject("ID");
```

## Function

### setBounds(info) → string

> 볼륨 효과가 표시될 영역을 경위도 중심 좌표와 크기(박스)로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type                                | Description                                    |
| :----------- | -------------------------------------- | ----------------------------------------------- |
| info         | object                                  | 영역 설정 옵션.                                 |
| ↳ position   | [JSVector3D](../core/jsvector3d.md)  | 박스 중심 좌표(경도, 위도, 고도).               |
| ↳ size       | [JSVector3D](../core/jsvector3d.md)  | 박스 크기(x: 동서 방향, y: 높이, z: 남북 방향, meter 단위). |

-   Return
    -   "": 설정 성공.
    -   이 외 문자열: 실패 원인 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.setBounds({
    position: new Module.JSVector3D(127.0, 37.5, 100.0),
    size: new Module.JSVector3D(50.0, 100.0, 50.0)
});
```

{% endtab %}
{% endtabs %}

### setPolygonBounds(info) → string

> 다각형 좌표(경위도 목록)와 최소/최대 고도로 영역을 감싸는 박스를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type          | Description        |
| :------ | ------------- | -------------------- |
| info    | object        | 영역 설정 옵션.       |
| ↳ lon   | array(number) | 다각형 꼭짓점 경도 목록. |
| ↳ lat   | array(number) | 다각형 꼭짓점 위도 목록. |
| ↳ minAlt | number       | 최소 고도.            |
| ↳ maxAlt | number       | 최대 고도.            |

-   Return
    -   "": 설정 성공.
    -   이 외 문자열: 실패 원인 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.setPolygonBounds({
    lon: [127.0, 127.01, 127.01, 127.0],
    lat: [37.5, 37.5, 37.51, 37.51],
    minAlt: 0.0,
    maxAlt: 100.0
});
```

{% endtab %}
{% endtabs %}

### setPosition(position) → string

> 박스 크기는 그대로 두고 박스 중심 위치만 옮깁니다(태풍 이동 경로 추적 등). [setBounds(info)](jsvolumeobject.md#setbounds-info-string)로 박스를 먼저 만든 뒤에만 의미가 있습니다. 지형 결합([conformTerrain(resolution)](jsvolumeobject.md#conformterrain-resolution-boolean))이 설정되어 있으면 옮긴 위치에 맞게 지형 높이를 다시 샘플링합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                                  |
| :------- | ----------------------------------- | ----------------------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 새 박스 중심 좌표(경도, 위도, 고도(meter 단위)). |

-   Return
    -   "success": 설정 성공.
    -   "null": 객체가 생성되지 않은 경우.
    -   "box isn't created yet.": 박스가 아직 만들어지지 않은 경우([setBounds(info)](jsvolumeobject.md#setbounds-info-string) 또는 [setPolygonBounds(info)](jsvolumeobject.md#setpolygonbounds-info-string)를 먼저 호출해야 함).

{% endtab %}
{% tab title="Template" %}

```javascript
// 태풍 박스를 새 위치로 이동 (크기 유지)
volume.setPosition(new Module.JSVector3D(127.5, 36.0, 0.0));
```

{% endtab %}
{% endtabs %}

### setDensityGrid(info) → string

> 3D 밀도 데이터(0~1 값의 배열)로 볼륨 형태를 직접 설정합니다.
>
> 배열의 인덱스는 `index = (z * height + y) * width + x` (x: 동서, y: 높이, z: 남북) 순서로 계산됩니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type          | Description                    |
| :------ | ------------- | -------------------------------- |
| info    | object        | 밀도 데이터 옵션.                |
| ↳ data  | array(number) | 셀별 밀도 값 배열(0~1).          |
| ↳ width  | number       | 그리드 X축(동서) 셀 개수.        |
| ↳ height | number       | 그리드 Y축(높이) 셀 개수.        |
| ↳ depth  | number       | 그리드 Z축(남북) 셀 개수.        |

-   Return
    -   "": 설정 성공.
    -   이 외 문자열: 실패 원인 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.setDensityGrid({
    data: densityValueArray,
    width: 16, height: 16, depth: 16
});
```

{% endtab %}
{% endtabs %}

### updateDensityGrid(data) → string

> [setDensityGrid(info)](jsvolumeobject.md#setdensitygrid-info-string)로 설정한 것과 같은 크기의 배열로 밀도 데이터 내용만 교체합니다. 텍스처가 재할당되지 않으므로, 매 프레임(틱) 호출해도 비용이 낮습니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type          | Description                                                   |
| :--- | ------------- | ----------------------------------------------------------------- |
| data | array(number) | 갱신할 밀도 값 배열([setDensityGrid(info)](jsvolumeobject.md#setdensitygrid-info-string)와 동일한 크기여야 함). |

-   Return
    -   "": 갱신 성공.
    -   이 외 문자열: 실패 원인 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.updateDensityGrid(newDensityValueArray);
```

{% endtab %}
{% endtabs %}

### clearDensityGrid()

> [setDensityGrid(info)](jsvolumeobject.md#setdensitygrid-info-string)로 설정한 밀도 데이터를 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript
volume.clearDensityGrid();
```

{% endtab %}
{% endtabs %}

### setPointSources(info) → string

> 위치 목록만으로 볼륨 효과를 표시합니다(3D 밀도 텍스처를 만들 필요가 없는 경량 방식). 박스 위치/크기와 지형 결합은 엔진이 자동으로 계산합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type          | Description                                        |
| :------------ | ------------- | ----------------------------------------------------- |
| info          | object        | 점 소스 옵션.                                        |
| ↳ lon         | array(number) | 각 점의 경도 목록.                                   |
| ↳ lat         | array(number) | 각 점의 위도 목록.                                   |
| ↳ radius      | number        | 점 하나가 차지하는 반경(meter 단위).                 |
| ↳ thickness   | number        | 지면 위 효과 두께(meter 단위, opacity 및 효과 높이의 기준). |
| ↳ resolution  | number        | 밀도 그리드 한 변 해상도.                            |

-   Return
    -   "": 설정 성공.
    -   이 외 문자열: 실패 원인 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.setPointSources({
    lon: [127.0, 127.001, 127.002],
    lat: [37.5, 37.501, 37.502],
    radius: 5.0,
    thickness: 2.0,
    resolution: 16
});
```

{% endtab %}
{% endtabs %}

### updatePointSources(info) → string

> [setPointSources(info)](jsvolumeobject.md#setpointsources-info-string)와 같은 설정을 유지한 채 점 위치만 교체합니다. 점이 기존 박스 범위를 벗어나면 박스가 자동으로 넓혀집니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type          | Description         |
| :---- | ------------- | ---------------------- |
| info  | object        | [setPointSources(info)](jsvolumeobject.md#setpointsources-info-string)와 동일한 구조(위치만 교체). |

-   Return
    -   "": 갱신 성공.
    -   이 외 문자열: 실패 원인 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.updatePointSources({
    lon: [127.0, 127.001, 127.003],
    lat: [37.5, 37.501, 37.503],
    radius: 5.0,
    thickness: 2.0,
    resolution: 16
});
```

{% endtab %}
{% endtabs %}

### conformTerrain(resolution) → boolean

> 박스 바닥 대신 지형 표면을 기준으로 효과를 올립니다(지형 결합). 셀마다 지형을 조회하지 않고 `resolution` x `resolution` 격자로 한 번만 샘플링합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                    |
| :--------- | ------ | --------------------------------- |
| resolution | number | 지형 고도 샘플링 격자 한 변 해상도. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.conformTerrain(8);
```

{% endtab %}
{% endtabs %}

### clearTerrain()

> [conformTerrain(resolution)](jsvolumeobject.md#conformterrain-resolution-boolean)으로 설정한 지형 결합을 해제하고 박스 바닥 기준으로 되돌립니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript
volume.clearTerrain();
```

{% endtab %}
{% endtabs %}

### setColor(color) → boolean

> 볼륨 효과의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description |
| :---- | ----------------------------- | ----------- |
| color | [JSColor](../core/jscolor.md) | 설정할 색상. |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.setColor(new Module.JSColor(255, 255, 255, 255));
```

{% endtab %}
{% endtabs %}

### setParams(info) → string

> 현재 [effect](jsvolumeobject.md#effect-property-geteffect-seteffect-effect-number) 값에 따른 세부 효과 파라미터를 설정합니다. 효과별로 유효한 키 이름이 다르며, 같은 이름이 효과마다 다른 의미를 갖지 않도록 분리되어 있습니다.

{% tabs %}
{% tab title="Information" %}

| effect 값        | Type   | 옵션(info) 구조                                        |
| ----------------- | ------ | -------------------------------------------------------- |
| EVOL_CLOUD(0)     | object | `{ threshold, softness, tiling, drift }`                  |
| EVOL_FIRE(1)      | object | `{ threshold, sway, speed }`                              |
| EVOL_WILDFIRE(2)  | object | `{ fireHeight, smoke, speed }`                             |
| EVOL_WATER(3)     | object | `{ level, amplitude, speed, foam }`                        |
| EVOL_STORM(4)     | object | `{ eye, funnel, speed, threshold, arms }`                  |
| EVOL_FIREWORKS(5) | [JSVolumeObject.FireworksParams](jsvolumeobject.md#jsvolumeobject.fireworksparams) | `{ radiusMin, radiusMax, altMin, altMax, period, sparkle, count, tint, pattern, stars, falloff, riseSize, spread }` |

-   `EVOL_STORM`의 `speed`는 부호가 회전 방향을 결정합니다(양수: 시계 방향, 음수: 반시계 방향. 나선 팔이 감기는 방향도 함께 바뀝니다). `arms`는 나선 강우대 팔의 개수입니다(기본값 3, 최소 1).
-   `EVOL_FIREWORKS`의 각 키 설명과 기본값은 [JSVolumeObject.FireworksParams](jsvolumeobject.md#jsvolumeobject.fireworksparams)를 참고하십시오.
-   현재 `effect`에 해당하는 키만 적용되며, 다른 효과의 키는 무시됩니다. 전달하지 않은 키는 이전 값을 유지합니다.
-   [effect](jsvolumeobject.md#effect-property-geteffect-seteffect-effect-number)를 바꾸면 모든 파라미터와 색상, `opacity`가 새 효과의 기본값으로 초기화되므로, `setParams`는 `effect`를 지정한 뒤에 호출해야 합니다.

-   Return
    -   "success": 설정 성공.
    -   "null": 객체가 생성되지 않은 경우.
    -   "unknown effect.": 현재 effect가 알 수 없는 값인 경우.
    -   "no matching parameter for the current effect.": info에 현재 effect에 해당하는 키가 하나도 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.effect = Module.EVOL_CLOUD;
volume.setParams({ threshold: 0.3, softness: 2.0, tiling: 1.0, drift: 0.1 });

// 불꽃축제: 폭발 반경 20~150m, 도달 높이 100~300m
volume.effect = Module.EVOL_FIREWORKS;
volume.setParams({ radiusMin: 20, radiusMax: 150, altMin: 100, altMax: 300, count: 8 });
```

{% endtab %}
{% endtabs %}

### setInfluenceCircle(info) → string

> 효과와 별개로 지면 근처에 항상 채워진 원판을 얹어 영향 범위(태풍 강풍/폭풍 반경 등)를 표시합니다. 원의 중심은 박스 중심의 수평 위치이며, 밀도 그리드 유무와 무관하게 항상 보입니다. 원이 박스보다 크면 박스 밖으로 나간 부분은 잘려 보입니다.
>
> 지형 결합([conformTerrain(resolution)](jsvolumeobject.md#conformterrain-resolution-boolean))이 설정되어 있으면 `altitude`는 지면 위 높이, 아니면 박스 바닥 위 높이입니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type                          | Description                                                                                         |
| :----------- | ----------------------------- | ---------------------------------------------------------------------------------------------------- |
| info         | object                        | 영향권 옵션. 구조는 [JSVolumeObject.InfluenceCircleOption](jsvolumeobject.md#jsvolumeobject.influencecircleoption)를 참고. |

-   Return
    -   "success": 설정 성공(`enable`이 false인 경우 포함. 이때는 나머지 값을 그대로 둡니다).
    -   "null": 객체가 생성되지 않은 경우.
    -   "radius tag isn't exist.": `enable`이 true인데 `radius`가 없는 경우.
    -   "radius must be positive.": `radius`가 0 이하인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
// 반경 200km 단색 영향권
volume.setInfluenceCircle({
    enable: true,
    radius: 200000,
    altitude: 100,
    color: new Module.JSColor(160, 255, 210, 60),
    opacity: 0.8
});

// 영향권 끄기
volume.setInfluenceCircle({ enable: false });
```

{% endtab %}
{% endtabs %}

### setInfluenceCircleColorStops(stops) → string

> 영향권 원판을 태풍 눈(중심)으로부터의 거리에 따라 색이 바뀌는 색상범례로 채웁니다. 스톱 사이는 선형 보간되고, 가장 안쪽 스톱보다 안쪽은 첫 스톱의 색, 가장 바깥 스톱보다 바깥은 영향권 밖으로 보고 그리지 않습니다(경계는 부드럽게 페이드아웃).
>
> 색상범례는 [setInfluenceCircle(info)](jsvolumeobject.md#setinfluencecircle-info-string)로 영향권을 켜 둔 상태에서만 보입니다. 범례를 사용하면 `setInfluenceCircle`의 `radius`와 `color`는 사용되지 않고(각 스톱의 `color.a`가 알파가 됨), 전체 투명도는 `setInfluenceCircle`의 `opacity`로만 조절합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                                                                                              | Description                                                                                  |
| :---- | ----------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| stops | array([JSVolumeObject.InfluenceCircleColorStop](jsvolumeobject.md#jsvolumeobject.influencecirclecolorstop))       | 색상 스톱 배열(비어 있으면 안 됨). 거리 오름차순이 아니어도 내부에서 정렬하며, 최대 8개까지만 사용됩니다(초과분 무시). |

-   Return
    -   "success": 설정 성공.
    -   "null": 객체가 생성되지 않은 경우.
    -   "stops isn't exist.": stops가 undefined/null인 경우.
    -   "stops must be a non-empty array.": 빈 배열인 경우.
    -   "stop radius tag isn't exist.": 스톱에 `radius`가 없는 경우.
    -   "failed to set color stops.": 내부 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.setInfluenceCircle({ enable: true, radius: 300000, altitude: 100, opacity: 0.8 });

volume.setInfluenceCircleColorStops([
    { radius: 50000,  color: new Module.JSColor(200, 255, 0, 0) },
    { radius: 150000, color: new Module.JSColor(160, 255, 160, 0) },
    { radius: 300000, color: new Module.JSColor(100, 255, 255, 0) }
]);
```

{% endtab %}
{% endtabs %}

### clearInfluenceCircleColorStops()

> [setInfluenceCircleColorStops(stops)](jsvolumeobject.md#setinfluencecirclecolorstops-stops-string)로 설정한 색상범례를 지웁니다. 이후 원판은 [setInfluenceCircle(info)](jsvolumeobject.md#setinfluencecircle-info-string)의 단색으로 되돌아갑니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript
volume.clearInfluenceCircleColorStops();
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### effect (property), getEffect(), setEffect(effect) → number

> 볼륨 효과의 종류를 설정합니다. [Module.EVOL_\*](jsvolumeobject.md#effect-property-geteffect-seteffect-effect-number) 상수를 사용합니다.
>
> 효과를 설정하면 세부 파라미터와 색상, `opacity`가 해당 효과의 기본값으로 초기화됩니다(범위를 벗어난 값은 무시). 따라서 [setParams(info)](jsvolumeobject.md#setparams-info-string), [setColor(color)](jsvolumeobject.md#setcolor-color-boolean), [opacity](jsvolumeobject.md#opacity-property-getopacity-setopacity-opacity-number)는 `effect`를 지정한 뒤에 호출해야 합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                                                                                                |
| :----- | ------ | ------------------------------------------------------------------------------------------------------------------------------- |
| effect | number | <p>Module.EVOL_CLOUD(0): 구름<br>Module.EVOL_FIRE(1): 화염<br>Module.EVOL_WILDFIRE(2): 산불<br>Module.EVOL_WATER(3): 수면<br>Module.EVOL_STORM(4): 태풍<br>Module.EVOL_FIREWORKS(5): 불꽃축제(연속 발사 + 폭발)</p> |

-   Return(getEffect)
    -   number: 현재 설정된 효과 값.
    -   -1: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.effect = Module.EVOL_FIRE;
var effect = volume.effect;
```

{% endtab %}
{% endtabs %}

### quality (property), getQuality(), setQuality(quality) → number

> 레이 마칭 스텝 간격과 상한을 함께 결정하는 렌더링 품질 값을 설정합니다(0.05~1.0 범위로 clamp됨). 화면에서 작게 보이는 경우 엔진이 자동으로 더 낮춥니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                   |
| :------ | ------ | -------------------------------- |
| quality | number | 렌더링 품질(0.05~1.0, 기본값 낮을수록 성능 우선). |

{% endtab %}
{% tab title="Template" %}

```javascript
volume.quality = 0.7;
```

{% endtab %}
{% endtabs %}

### opacity (property), getOpacity(), setOpacity(opacity) → number

> 볼륨 효과의 전체 농도(불투명도)를 설정합니다(0.0~1.0 범위로 clamp됨). 박스 크기나 스텝 수가 달라져도 같은 값이면 같은 농도로 보이도록 정규화되어 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description         |
| :------ | ------ | ---------------------- |
| opacity | number | 전체 농도(0.0~1.0). |

{% endtab %}
{% tab title="Template" %}

```javascript
volume.opacity = 0.8;
```

{% endtab %}
{% endtabs %}

### animationSpeed (property), getAnimationSpeed(), setAnimationSpeed(speed) → number

> 볼륨 효과 애니메이션(노이즈 흐름 등) 재생 속도를 설정합니다(0 미만은 0으로 보정됨).

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description             |
| :---- | ------ | -------------------------- |
| speed | number | 애니메이션 속도(0 이상). |

{% endtab %}
{% tab title="Template" %}

```javascript
volume.animationSpeed = 1.0;
```

{% endtab %}
{% endtabs %}

### thickness (property), getThickness(), setThickness(thickness) → number

> 지면 위 효과 두께(meter 단위)를 설정합니다(0 미만은 0으로 보정됨). [opacity](jsvolumeobject.md#opacity-property-getopacity-setopacity-opacity-number)가 "이 두께를 수직으로 통과했을 때의 불투명도"라는 뜻을 갖게 되는 기준 길이이며, 효과의 높이 정규화에도 같은 값이 쓰입니다.
>
> 0이면 박스 세 변의 평균을 대신 사용합니다. 박스가 세 축 모두 비슷한 크기일 때는 무난하지만, 태풍처럼 박스가 납작하고 넓은 경우(가로세로 수백~수천 km, 높이는 그보다 훨씬 얇음)에는 평균값이 실제 두께보다 훨씬 커져 전체가 흐릿해 보입니다. 이때 박스 높이 정도로 직접 지정하면 의도한 농도로 돌아옵니다.
>
> [setPointSources(info)](jsvolumeobject.md#setpointsources-info-string)를 호출하면 그 `thickness` 값(0 이하이면 100)으로 덮어써집니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                              |
| :-------- | ------ | ---------------------------------------------------------- |
| thickness | number | 효과 두께(meter 단위, 0 이상. 기본값 0 = 박스 세 변 평균 사용). |

-   Return(getThickness)
    -   number: 현재 설정된 두께.
    -   0: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
// 납작하고 넓은 태풍 박스: 두께를 박스 높이로 지정
volume.thickness = 15000;
var thickness = volume.thickness;
```

{% endtab %}
{% endtabs %}

## Type Definitions

#### JSVolumeObject.FireworksParams

> `EVOL_FIREWORKS` 효과의 [setParams(info)](jsvolumeobject.md#setparams-info-string) 옵션. 모든 키는 생략 가능하며, 생략하면 이전 값(효과를 지정한 직후에는 아래 기본값)을 유지합니다. 박스는 `altMax + radiusMax`를 담을 만큼 커야 하며, 모자라면 폭발 껍질이 박스 벽에서 잘려 사각 단면이 드러납니다.

| Name      | Type   | Attributes | Default | Description                                                                                                                                         |
| --------- | ------ | ---------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| radiusMin | number | optional   | 5       | 폭발 반경 최소값(meter). 발마다 `radiusMin`~`radiusMax` 사이에서 무작위로 뽑습니다. 최소 1로 취급됩니다.                                              |
| radiusMax | number | optional   | 300     | 폭발 반경 최대값(meter). `radiusMin`보다 작으면 `radiusMin`으로 취급됩니다.                                                                          |
| altMin    | number | optional   | 80      | 도달 높이 최소값(meter, 박스 바닥 기준). 발마다 무작위로 뽑습니다. 최소 1로 취급됩니다.                                                               |
| altMax    | number | optional   | 350     | 도달 높이 최대값(meter, 박스 바닥 기준). `altMin`보다 작으면 `altMin`으로 취급됩니다.                                                                |
| period    | number | optional   | 3.2     | 발사 주기(초). 최소 0.8로 취급됩니다.                                                                                                                |
| sparkle   | number | optional   | 0.8     | 알갱이 또렷함. 0~1로 제한됩니다(0: 매끄러운 껍질, 1: 또렷하게 흩어진 점).                                                                            |
| count     | number | optional   | 6       | 동시에 떠 있는 발수. 1~12로 제한됩니다.                                                                                                              |
| tint      | number | optional   | 0       | 색 통일 비율. 0~1로 제한됩니다(0: 발마다 내장 팔레트에서 색을 뽑음, 1: [setColor(color)](jsvolumeobject.md#setcolor-color-boolean) 색으로 통일).        |
| pattern   | number | optional   | 0       | <p>폭발 형태.<br>0: 혼합(발마다 무작위)<br>1: 구형<br>2: 고리<br>3: 버들<br>4: 반짝임</p>                                                            |
| stars     | number | optional   | 800     | 폭죽 하나의 알갱이(별) 개수. 1~10000으로 제한됩니다.                                                                                                 |
| falloff   | number | optional   | 3       | 경계 감쇠 지수. 1~100으로 제한됩니다. 2는 가우시안이라 알갱이 밖까지 빛이 번지고, 높일수록 꼬리가 잘려 알갱이가 또렷해지면서 같은 밀도에서 더 밝아집니다. |
| riseSize  | number | optional   | 0.045   | 올라가는 발사체의 반경(폭발 반경 대비 비율, 0.045 = 4.5%). 0~0.30으로 제한되며, 0이면 발사체를 그리지 않고 폭발만 나타납니다.                          |
| spread    | number | optional   | 0.15    | 발사 지점이 박스 안에서 수평으로 퍼지는 범위. 0~1로 제한됩니다(0: 박스 중심 한 지점에서만 발사, 1: 박스 전역으로 퍼짐).                                |

> 기존 코드 호환을 위해 `radius`, `shell` 키도 오류 없이 받아들이지만 더 이상 효과에 반영되지 않습니다(`radiusMin`/`radiusMax`를 사용하십시오). `EVOL_FIREWORKS`의 기본 색상은 `JSColor(255, 255, 200, 120)`, 기본 `opacity`는 0.9입니다.

#### JSVolumeObject.InfluenceCircleOption

> [setInfluenceCircle(info)](jsvolumeobject.md#setinfluencecircle-info-string) 옵션.

| Name     | Type                          | Attributes | Default                      | Description                                                                                                                                                       |
| -------- | ----------------------------- | ---------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| enable   | boolean                       | optional   | true                         | 영향권 표시 여부. false이면 나머지 값은 무시하고 끄기만 합니다(이전에 설정한 값은 유지).                                                                           |
| radius   | number                        |            |                              | 원 반경(meter). `enable`이 true이면 필수이며 0보다 커야 합니다. 색상범례를 사용하면 범례의 가장 바깥 스톱이 경계가 되어 사용되지 않습니다.                         |
| altitude | number                        | optional   | 0                            | 지면(지형 결합 시) 또는 박스 바닥 위 높이(meter). 0 미만은 0으로 보정됩니다.                                                                                       |
| color    | [JSColor](../core/jscolor.md) | optional   | JSColor(160, 255, 210, 60)   | 단색 영향권 색상(alpha 포함). 색상범례를 사용하면 무시됩니다.                                                                                                      |
| opacity  | number                        | optional   | 1                            | 영향권 전체에 곱해지는 투명도 배율. 0~1로 제한됩니다. 단색/색상범례 모두에 적용되며, 색상범례 사용 시 전체 투명도를 조절할 수 있는 유일한 값입니다.                |

#### JSVolumeObject.InfluenceCircleColorStop

> [setInfluenceCircleColorStops(stops)](jsvolumeobject.md#setinfluencecirclecolorstops-stops-string)의 색상 스톱 하나.

| Name   | Type                          | Attributes | Default                  | Description                                                              |
| ------ | ----------------------------- | ---------- | ------------------------ | ------------------------------------------------------------------------ |
| radius | number                        |            |                          | 태풍 눈(박스 중심)으로부터의 거리(meter). 0 미만은 0으로 보정됩니다.      |
| color  | [JSColor](../core/jscolor.md) | optional   | JSColor(255, 255, 255, 255) | 해당 거리의 색상(alpha 포함). 스톱 사이는 선형 보간됩니다.            |
