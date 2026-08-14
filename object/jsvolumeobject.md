---
description: 지도 내 볼륨(연기, 화염, 산불, 수면, 태풍 등) 효과를 표현하기 위한 볼륨(Volume) 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSVolumeObject

> Module.createVolumeObject() API를 생성합니다.
>
> 레이 마칭(Ray Marching) 기반으로, 박스 하나에 3D 밀도 데이터를 올려 한 번에 그리는 방식으로 구름·화염·산불·수면·태풍 같은 부피감 있는 효과를 표현합니다. [effect](jsvolumeobject.md#effect-property-geteffect-seteffect-effect-number) 프로퍼티로 효과 종류를 선택하며, 효과별로 [setParams(info)](jsvolumeobject.md#setparams-info-string)에 전달하는 세부 옵션 이름이 다릅니다.

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
| EVOL_STORM(4)     | object | `{ eye, funnel, speed, threshold }`                        |

-   Return
    -   "": 설정 성공.
    -   이 외 문자열: 실패 원인 메시지.

{% endtab %}
{% tab title="Template" %}

```javascript
volume.effect = Module.EVOL_CLOUD;
volume.setParams({ threshold: 0.3, softness: 2.0, tiling: 1.0, drift: 0.1 });
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### effect (property), getEffect(), setEffect(effect) → number

> 볼륨 효과의 종류를 설정합니다. [Module.EVOL_\*](jsvolumeobject.md#effect-property-geteffect-seteffect-effect-number) 상수를 사용합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                                                                                                |
| :----- | ------ | ------------------------------------------------------------------------------------------------------------------------------- |
| effect | number | <p>Module.EVOL_CLOUD(0): 구름<br>Module.EVOL_FIRE(1): 화염<br>Module.EVOL_WILDFIRE(2): 산불<br>Module.EVOL_WATER(3): 수면<br>Module.EVOL_STORM(4): 태풍</p> |

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
