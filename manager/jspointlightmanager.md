---
description: 가로등, 조명 등 점광원을 지형과 건물에 비추기 위한 API 입니다.
---

# JSPointLightManager

> Module.getPointLightManager() API를 통해 획득합니다.
>
> 지형과 건물에 점광원(가로등, 조명 등)의 빛을 비춥니다. 점광원 기능은 기본적으로 꺼져 있으므로 [setEnable(set)](jspointlightmanager.md#getenable-setenable-set-boolean)으로 켠 뒤 [add(key, position, color, intensity, radius)](jspointlightmanager.md#add-key-position-color-intensity-radius-boolean)로 광원을 추가합니다.
>
> 광원에 방향과 원뿔 각도를 지정하면 특정 방향으로만 비추는 스포트라이트로 사용할 수 있습니다.

* 지원버전 : `2.32.1+`

```javascript
var lights = Module.getPointLightManager();
lights.setEnable(true);
lights.setAmbient(0.3);
lights.add("lamp_0", new Module.JSVector3D(126.9246, 37.5213, 12.0), new Module.JSColor(255, 255, 200), 1.0, 30.0);
```

{% hint style="info" %}
점광원 기능을 켜면 장면 전체가 환경광([setAmbient(ambient)](jspointlightmanager.md#getambient-setambient-ambient-number)) 밝기로 어두워지고, 추가한 광원 주변만 밝아집니다. 야간 장면에 사용하는 기능입니다.
{% endhint %}

* 샘플
  * [Sandbox_Light Ball](https://sandbox.egiscloud.com/code/main.do?id=effect_lightball)
  * [Sandbox_Spotlight](https://sandbox.egiscloud.com/code/main.do?id=effect_spotlight)

## Function

### getEnable(), setEnable(set) → boolean

> 점광원 기능 사용 여부를 설정/반환합니다. 기본값은 false입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                  |
| ---- | ------- | -------------------------------------------- |
| set  | boolean | <p>true: 사용.<br>false: 미사용(기본값).</p> |

-   Return(getEnable)
    -   boolean: 현재 사용 여부.

{% endtab %}
{% tab title="Template" %}

```javascript
var lights = Module.getPointLightManager();
lights.setEnable(true);
var enabled = lights.getEnable();
```

{% endtab %}
{% endtabs %}

### getAmbient(), setAmbient(ambient) → number

> 환경광(광원이 닿지 않는 곳의 기본 밝기)을 설정/반환합니다. 값이 작을수록 밤 장면이 어두워집니다.
>
> 입력 범위는 0.02 ~ 1이며 범위를 벗어난 값은 가장 가까운 한계값으로 보정됩니다. 기본값은 0.3입니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                  |
| ------- | ------ | ---------------------------- |
| ambient | number | 환경광 밝기. (0.02 ~ 1, 기본값 0.3) |

-   Return(getAmbient)
    -   number: 현재 환경광 밝기.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setAmbient(0.2);
var ambient = lights.getAmbient();
```

{% endtab %}
{% endtabs %}

### getMaxCount(), setMaxCount(count) → number

> 화면에 적용하는 광원의 최대 개수를 설정/반환합니다. 등록한 광원이 이보다 많으면 카메라에서 가까운 광원부터 적용됩니다.
>
> 입력 범위는 1 ~ 64이며 기본값은 32입니다. 기기에 따라 실제로 적용되는 최대 개수는 이보다 작을 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                         |
| ----- | ------ | ----------------------------------- |
| count | number | 최대 광원 개수. (1 ~ 64, 기본값 32) |

-   Return(getMaxCount)
    -   number: 현재 최대 광원 개수.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setMaxCount(64);
var maxCount = lights.getMaxCount();
```

{% endtab %}
{% endtabs %}

### getRange(), setRange(range) → number

> 광원이 적용되는 카메라 거리를 설정/반환합니다. 카메라에서 이 거리보다 먼 광원은 적용하지 않습니다.
>
> 단위는 meter이며 1 미만의 값은 1로 보정됩니다. 기본값은 1500입니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                |
| ----- | ------ | ------------------------------------------ |
| range | number | 카메라 기준 적용 거리. (meter, 기본값 1500) |

-   Return(getRange)
    -   number: 현재 적용 거리.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setRange(800);
var range = lights.getRange();
```

{% endtab %}
{% endtabs %}

### getOcclusion(), setOcclusion(set) → boolean

> 지형과 건물에 의한 빛 가림 판정 사용 여부를 설정/반환합니다. 켜면 건물 뒤편처럼 광원이 직접 보이지 않는 곳에는 빛이 닿지 않습니다. 기본값은 false입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                  |
| ---- | ------- | -------------------------------------------- |
| set  | boolean | <p>true: 사용.<br>false: 미사용(기본값).</p> |

-   Return(getOcclusion)
    -   boolean: 현재 사용 여부.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setOcclusion(true);
var occlusion = lights.getOcclusion();
```

{% endtab %}
{% endtabs %}

### getVolumetric(), setVolumetric(set) → boolean

> 방향성 광원(스포트라이트)에서 공기 중에 산란되는 빛줄기의 표현 여부를 설정/반환합니다. [setCone(key, innerAngle, outerAngle)](jspointlightmanager.md#setcone-key-innerangle-outerangle-boolean)으로 원뿔 각도를 360보다 작게 지정한 광원에 적용되며, 빛줄기는 화면에 보이는 표면까지만 그려집니다. 기본값은 false입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                  |
| ---- | ------- | -------------------------------------------- |
| set  | boolean | <p>true: 사용.<br>false: 미사용(기본값).</p> |

-   Return(getVolumetric)
    -   boolean: 현재 사용 여부.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setVolumetric(true);
var volumetric = lights.getVolumetric();
```

{% endtab %}
{% endtabs %}

### getVolumetricDensity(), setVolumetricDensity(density) → number

> 공기 중 빛 산란 밀도를 설정/반환합니다. 값이 클수록 빛줄기가 진하게 표현됩니다.
>
> 입력 범위는 0 ~ 1이며 범위를 벗어난 값은 가장 가까운 한계값으로 보정됩니다. 기본값은 0.006입니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                              |
| ------- | ------ | ---------------------------------------- |
| density | number | 산란 밀도. (0 ~ 1, 기본값 0.006) |

-   Return(getVolumetricDensity)
    -   number: 현재 산란 밀도.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setVolumetricDensity(0.01);
var density = lights.getVolumetricDensity();
```

{% endtab %}
{% endtabs %}

### getVolumetricLength(), setVolumetricLength(length) → number

> 빛줄기를 그리는 길이를 설정/반환합니다. 광원에서 이 거리까지만 빛줄기를 그리며 멀어질수록 옅어집니다. 광원의 반경이 이보다 짧으면 반경까지만 그려집니다.
>
> 단위는 meter이며 1 미만의 값은 1로 보정됩니다. 기본값은 100입니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                           |
| ------ | ------ | ------------------------------------- |
| length | number | 빛줄기 길이. (meter, 기본값 100) |

-   Return(getVolumetricLength)
    -   number: 현재 빛줄기 길이.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setVolumetricLength(60);
var length = lights.getVolumetricLength();
```

{% endtab %}
{% endtabs %}

### add(key, position, color, intensity, radius) → boolean

> 점광원을 추가합니다. 광원은 `key` 문자열로 구분하며, 같은 `key`를 가진 광원은 하나만 등록할 수 있습니다. 추가한 광원은 방향 없이 사방으로 퍼지는 점광원이며, 방향성이 필요하면 [setDirection(key, yaw, pitch)](jspointlightmanager.md#setdirection-key-yaw-pitch-boolean)과 [setCone(key, innerAngle, outerAngle)](jspointlightmanager.md#setcone-key-innerangle-outerangle-boolean)을 사용합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                | Description                                                   |
| --------- | ----------------------------------- | ------------------------------------------------------------- |
| key       | string                              | 광원 식별 문자열. (빈 문자열 불가)                            |
| position  | [JSVector3D](../core/jsvector3d.md) | 광원 위치. (경도, 위도, 고도(meter))                          |
| color     | [JSColor](../core/jscolor.md)       | 광원 색상. R, G, B 값만 사용하며 투명도(A)는 적용되지 않습니다. |
| intensity | number                              | 광원 세기. 0보다 작은 값은 0으로 보정됩니다.                  |
| radius    | number                              | 빛이 닿는 반경. (meter, 0보다 커야 함)                        |

-   Return
    -   true: 추가 성공.
    -   false: 추가 실패. `key`가 비어 있거나, `radius`가 0 이하이거나, 같은 `key`의 광원이 이미 있는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var position = new Module.JSVector3D(126.9246, 37.5213, 12.0);
var color = new Module.JSColor(255, 255, 235);
var ok = lights.add("lamp_0", position, color, 1.0, 30.0);
```

{% endtab %}
{% endtabs %}

### remove(key) → boolean

> `key`에 해당하는 광원을 삭제합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| key  | string | 광원 식별 문자열. |

-   Return
    -   true: 삭제 성공.
    -   false: `key`에 해당하는 광원이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.remove("lamp_0");
```

{% endtab %}
{% endtabs %}

### clear() → void

> 추가한 광원을 모두 삭제합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
lights.clear();
```

{% endtab %}
{% endtabs %}

### setPosition(key, position) → boolean

> 광원의 위치를 변경합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                          |
| -------- | ----------------------------------- | ------------------------------------ |
| key      | string                              | 광원 식별 문자열.                    |
| position | [JSVector3D](../core/jsvector3d.md) | 광원 위치. (경도, 위도, 고도(meter)) |

-   Return
    -   true: 변경 성공.
    -   false: `key`에 해당하는 광원이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setPosition("lamp_0", new Module.JSVector3D(126.9250, 37.5215, 12.0));
```

{% endtab %}
{% endtabs %}

### setColor(key, color) → boolean

> 광원의 색상을 변경합니다. R, G, B 값만 사용하며 투명도(A)는 적용되지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description       |
| ----- | ----------------------------- | ----------------- |
| key   | string                        | 광원 식별 문자열. |
| color | [JSColor](../core/jscolor.md) | 광원 색상.        |

-   Return
    -   true: 변경 성공.
    -   false: `key`에 해당하는 광원이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setColor("lamp_0", new Module.JSColor(255, 255, 160, 80));
```

{% endtab %}
{% endtabs %}

### setIntensity(key, intensity) → boolean

> 광원의 세기를 변경합니다. 0보다 작은 값은 0으로 보정됩니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| --------- | ------ | ----------------- |
| key       | string | 광원 식별 문자열. |
| intensity | number | 광원 세기.        |

-   Return
    -   true: 변경 성공.
    -   false: `key`에 해당하는 광원이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setIntensity("lamp_0", 2.0);
```

{% endtab %}
{% endtabs %}

### setRadius(key, radius) → boolean

> 광원의 영향 반경을 변경합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                        |
| ------ | ------ | ---------------------------------- |
| key    | string | 광원 식별 문자열.                  |
| radius | number | 빛이 닿는 반경. (meter, 0보다 커야 함) |

-   Return
    -   true: 변경 성공.
    -   false: `key`에 해당하는 광원이 없거나 `radius`가 0 이하인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lights.setRadius("lamp_0", 50.0);
```

{% endtab %}
{% endtabs %}

### setDirection(key, yaw, pitch) → boolean

> 광원이 비추는 방향(빛의 축)을 설정합니다. 기본값은 방위각 0, 기울기 -90(바로 아래)입니다.
>
> 방향은 [setCone(key, innerAngle, outerAngle)](jspointlightmanager.md#setcone-key-innerangle-outerangle-boolean)으로 원뿔 각도를 360보다 작게 지정했을 때 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                      |
| ----- | ------ | ---------------------------------------------------------------- |
| key   | string | 광원 식별 문자열.                                                |
| yaw   | number | 방위각. (degree, 북쪽 0에서 시계 방향)                           |
| pitch | number | 기울기. (degree, 위쪽이 +, 아래쪽이 -, -90 ~ 90으로 보정됩니다.) |

-   Return
    -   true: 설정 성공.
    -   false: `key`에 해당하는 광원이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
// 동쪽(90도) 방향, 수평선보다 30도 아래
lights.setDirection("lamp_0", 90, -30);
```

{% endtab %}
{% endtabs %}

### setCone(key, innerAngle, outerAngle) → boolean

> 광원이 비추는 원뿔 각도를 설정합니다. 각도는 원뿔의 전체 각도이며, 안쪽 각도까지는 최대 밝기를 유지하고 바깥쪽 각도의 가장자리까지 점점 어두워집니다.
>
> `outerAngle`이 360이면 방향 없이 사방으로 퍼지는 점광원(기본값)입니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                                                              |
| ---------- | ------ | ------------------------------------------------------------------------ |
| key        | string | 광원 식별 문자열.                                                        |
| innerAngle | number | 최대 밝기를 유지하는 안쪽 원뿔 각도. (degree, 0 ~ outerAngle로 보정됩니다.) |
| outerAngle | number | 빛이 닿는 바깥쪽 원뿔 각도. (degree, 1 ~ 360으로 보정됩니다.)            |

-   Return
    -   true: 설정 성공.
    -   false: `key`에 해당하는 광원이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
// 바깥 각도 40도의 스포트라이트, 안쪽 70% 구간은 최대 밝기
lights.setDirection("lamp_0", 0, -90);
lights.setCone("lamp_0", 40 * 0.7, 40);
```

{% endtab %}
{% endtabs %}
