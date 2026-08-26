---
description: 화면 포스트프로세싱(DoF, Bloom, Sharpen) 설정을 위한 API 입니다.
---

# JSPostProcess

> Module.getPostProcess() API를 생성합니다.
>
> DoF/Bloom/Sharpen 세 효과는 각각 독립적인 활성화 플래그를 가지며, 서로 다른 효과의 on/off와 무관하게 개별적으로 켜고 끌 수 있습니다. 특히 Sharpen은 DoF/Bloom이 모두 꺼져 있어도 단독으로 동작합니다.

```javascript
var postProcess = Module.getPostProcess();
```

## Depth of Field

> 피사계 심도(초점 거리 밖 영역을 흐리게 표현) 효과입니다.

### getEnableDoF(), setEnableDoF(set) → boolean

> DoF 포스트프로세싱 사용 여부를 설정/반환합니다. 기본값은 false입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                |
| ---- | ------- | ---------------------------------------------- |
| set  | boolean | <p>true: 사용.<br>false: 미사용(기본값).</p> |

-   Return(getEnableDoF)
    -   boolean: 현재 DoF 사용 여부.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setEnableDoF(true);
var enabled = postProcess.getEnableDoF();
```

{% endtab %}
{% endtabs %}

### getDofAutoFocus(), setDofAutoFocus(set) → boolean

> 자동 초점(화면 중앙 깊이 기준) 사용 여부를 설정/반환합니다.
>
> 켜면 화면 중앙 픽셀의 실제 깊이를 매 프레임 다시 읽어 그 지점을 초점 중심으로 삼습니다 — 카메라 위치나 거리를 미리 알 필요 없이 항상 "지금 보고 있는 곳"에 초점이 맞습니다. 기본값은 false이며, 꺼져 있으면 [setDofFocusStart(distance)](jspostprocess.md#getdoffocusstart-setdoffocusstart-distance-number)/[setDofFocusEnd(distance)](jspostprocess.md#getdoffocusend-setdoffocusend-distance-number)로 설정한 수동 초점 구간이 사용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                   |
| ---- | ------- | ------------------------------------------------------------------ |
| set  | boolean | <p>true: 자동 초점 사용.<br>false: 수동 초점 구간 사용(기본값).</p> |

-   Return(getDofAutoFocus)
    -   boolean: 현재 자동 초점 사용 여부.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofAutoFocus(true);
var autoFocus = postProcess.getDofAutoFocus();
```

{% endtab %}
{% endtabs %}

### getDofAutoFocusRange(), setDofAutoFocusRange(range) → number

> 자동 초점 사용 시, 초점 구간의 반폭(world unit)을 설정/반환합니다. 화면 중앙의 실제 깊이를 기준으로 ± range 범위가 초점 구간이 됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                    |
| ----- | ------ | ---------------------------------------------------- |
| range | number | 자동 초점 반폭(world unit). 1 미만은 1로 clamp. 기본값 60. |

-   Return(getDofAutoFocusRange)
    -   number: 현재 설정된 자동 초점 반폭.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofAutoFocusRange(80);
var range = postProcess.getDofAutoFocusRange();
```

{% endtab %}
{% endtabs %}

### getDofFocusStart(), setDofFocusStart(distance) → number

> 수동 초점 구간의 시작 거리(world unit)를 설정/반환합니다. 이 거리보다 가까운 오브젝트는 흐려집니다. 자동 초점([setDofAutoFocus(true)](jspostprocess.md#getdofautofocus-setdofautofocus-set-boolean))이 켜져 있으면 이 값 대신 자동 계산된 구간이 사용됩니다.
>
> [setDofFocusEnd(distance)](jspostprocess.md#getdoffocusend-setdoffocusend-distance-number)와의 대소 순서는 강제하지 않습니다 — 셰이더가 내부적으로 두 값을 정렬해서 사용하므로, start > end로 설정해도 정상 동작합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description                                          |
| -------- | ------ | ------------------------------------------------------- |
| distance | number | 초점 시작 거리(world unit). 0 미만은 0으로 clamp. 기본값 800. |

-   Return(getDofFocusStart)
    -   number: 현재 설정된 초점 시작 거리.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofFocusStart(700);
var start = postProcess.getDofFocusStart();
```

{% endtab %}
{% endtabs %}

### getDofFocusEnd(), setDofFocusEnd(distance) → number

> 수동 초점 구간의 종료 거리(world unit)를 설정/반환합니다. 이 거리보다 먼 오브젝트는 흐려집니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description                                           |
| -------- | ------ | -------------------------------------------------------- |
| distance | number | 초점 종료 거리(world unit). 0 미만은 0으로 clamp. 기본값 1200. |

-   Return(getDofFocusEnd)
    -   number: 현재 설정된 초점 종료 거리.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofFocusEnd(1300);
var end = postProcess.getDofFocusEnd();
```

{% endtab %}
{% endtabs %}

### getDofAperture(), setDofAperture(aperture) → number

> 조리개 강도를 설정/반환합니다. 값이 클수록 초점 밖 영역의 흐림이 강해집니다. 0이면 DoF 효과가 전혀 나타나지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description                              |
| -------- | ------ | ------------------------------------------- |
| aperture | number | 조리개 강도. 0~1 범위로 clamp. 기본값 0.9. |

-   Return(getDofAperture)
    -   number: 현재 설정된 조리개 강도.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofAperture(0.8);
var aperture = postProcess.getDofAperture();
```

{% endtab %}
{% endtabs %}

### getDofTransitionWidth(), setDofTransitionWidth(width) → number

> 초점 경계에서 완전히 흐려지기까지 걸리는 전환 거리(world unit)를 설정/반환합니다. 값이 짧을수록 경계가 급격하게 흐려지고, 길수록 부드럽게 전환됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                  |
| ----- | ------ | ------------------------------------------------ |
| width | number | 전환 거리(world unit). 1 미만은 1로 clamp. 기본값 100. |

-   Return(getDofTransitionWidth)
    -   number: 현재 설정된 전환 거리.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofTransitionWidth(150);
var width = postProcess.getDofTransitionWidth();
```

{% endtab %}
{% endtabs %}

### getDofMaxBlurRadius(), setDofMaxBlurRadius(radius) → number

> CoC(Circle of Confusion)가 최대(1.0)일 때 적용되는 블러 반경(텍셀 단위)을 설정/반환합니다. 값을 키우면 블러 반복 횟수를 늘리지 않고도 한 번에 훨씬 강한 블러 효과를 얻을 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                        |
| ------ | ------ | ------------------------------------------------------ |
| radius | number | 최대 블러 반경(텍셀). 1~256 범위로 clamp. 기본값 10. |

-   Return(getDofMaxBlurRadius)
    -   number: 현재 설정된 최대 블러 반경.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofMaxBlurRadius(48);
var radius = postProcess.getDofMaxBlurRadius();
```

{% endtab %}
{% endtabs %}

### getDofBlurIterations(), setDofBlurIterations(count) → number

> 분리형(separable) 블러의 반복 횟수(수평+수직 1쌍 기준)를 설정/반환합니다. 값이 클수록 더 강하고 부드러운 블러를 얻지만 렌더링 비용도 늘어납니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                 |
| ----- | ------ | ---------------------------------------------- |
| count | number | 블러 반복 횟수. 1~8 범위로 clamp. 기본값 1. |

-   Return(getDofBlurIterations)
    -   number: 현재 설정된 블러 반복 횟수.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofBlurIterations(3);
var count = postProcess.getDofBlurIterations();
```

{% endtab %}
{% endtabs %}

### getDofBlurScale(), setDofBlurScale(scale) → number

> 블러 패스의 렌더링 해상도 배율을 설정/반환합니다. 저사양 기기는 0.2에 가깝게, 화질 우선이면 1.0으로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                |
| ----- | ------ | -------------------------------------------------------------- |
| scale | number | 블러 해상도 배율. 0.2~1.0 범위로 clamp. 기본값 1.0(풀 해상도). |

-   Return(getDofBlurScale)
    -   number: 현재 설정된 블러 해상도 배율.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setDofBlurScale(0.5);
var scale = postProcess.getDofBlurScale();
```

{% endtab %}
{% endtabs %}

## Bloom

> 밝은 영역이 주변으로 은은하게 번지는 글로우 효과입니다. DoF와 독립적으로 켜고 끌 수 있습니다.

### getEnableBloom(), setEnableBloom(set) → boolean

> Bloom 포스트프로세싱 사용 여부를 설정/반환합니다. 기본값은 false입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                |
| ---- | ------- | ---------------------------------------------- |
| set  | boolean | <p>true: 사용.<br>false: 미사용(기본값).</p> |

-   Return(getEnableBloom)
    -   boolean: 현재 Bloom 사용 여부.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setEnableBloom(true);
var enabled = postProcess.getEnableBloom();
```

{% endtab %}
{% endtabs %}

### getBloomThreshold(), setBloomThreshold(threshold) → number

> Bloom 추출 휘도 임계값을 설정/반환합니다. 이 값을 넘는 밝기의 픽셀만 블러링되어 다시 더해집니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                            |
| --------- | ------ | ------------------------------------------ |
| threshold | number | 휘도 임계값. 0~1 범위로 clamp. 기본값 0.7. |

-   Return(getBloomThreshold)
    -   number: 현재 설정된 휘도 임계값.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setBloomThreshold(0.6);
var threshold = postProcess.getBloomThreshold();
```

{% endtab %}
{% endtabs %}

### getBloomIntensity(), setBloomIntensity(intensity) → number

> Bloom 합성 시 additive(가산) 강도를 설정/반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                     |
| --------- | ------ | ---------------------------------------------------- |
| intensity | number | Additive 합성 강도. 0~2 범위로 clamp. 기본값 0.6. |

-   Return(getBloomIntensity)
    -   number: 현재 설정된 합성 강도.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setBloomIntensity(0.6);
var intensity = postProcess.getBloomIntensity();
```

{% endtab %}
{% endtabs %}

### getBloomSpread(), setBloomSpread(spread) → number

> Bloom 반복 블러의 반경 배수를 설정/반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                     |
| ------ | ------ | ------------------------------------------------------ |
| spread | number | 블러 반경 배수. 0~1 범위로 clamp. 기본값 1.0(최대). |

-   Return(getBloomSpread)
    -   number: 현재 설정된 블러 반경 배수.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setBloomSpread(0.8);
var spread = postProcess.getBloomSpread();
```

{% endtab %}
{% endtabs %}

### getBloomMaxBlurRadius(), setBloomMaxBlurRadius(radius) → number

> Bloom의 u_spread가 1일 때 적용되는 최대 블러 반경(텍셀 단위)을 설정/반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                        |
| ------ | ------ | ------------------------------------------------------ |
| radius | number | 최대 블러 반경(텍셀). 1~256 범위로 clamp. 기본값 32. |

-   Return(getBloomMaxBlurRadius)
    -   number: 현재 설정된 최대 블러 반경.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setBloomMaxBlurRadius(40);
var radius = postProcess.getBloomMaxBlurRadius();
```

{% endtab %}
{% endtabs %}

### getBloomBlurIterations(), setBloomBlurIterations(count) → number

> Bloom 분리형 블러의 반복 횟수(수평+수직 1쌍 기준)를 설정/반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                 |
| ----- | ------ | ---------------------------------------------- |
| count | number | 블러 반복 횟수. 1~8 범위로 clamp. 기본값 2. |

-   Return(getBloomBlurIterations)
    -   number: 현재 설정된 블러 반복 횟수.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setBloomBlurIterations(3);
var count = postProcess.getBloomBlurIterations();
```

{% endtab %}
{% endtabs %}

### getBloomBlurScale(), setBloomBlurScale(scale) → number

> Bloom 블러 패스의 렌더링 해상도 배율을 설정/반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                     |
| ----- | ------ | -------------------------------------------------- |
| scale | number | 블러 해상도 배율. 0.2~1.0 범위로 clamp. 기본값 0.5. |

-   Return(getBloomBlurScale)
    -   number: 현재 설정된 블러 해상도 배율.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setBloomBlurScale(0.7);
var scale = postProcess.getBloomBlurScale();
```

{% endtab %}
{% endtabs %}

## Sharpen

> 화면을 언샤프 마스크로 선명하게 만드는 효과입니다. **DoF/Bloom과 완전히 독립적으로 동작**하며, 두 효과가 모두 꺼져 있어도 단독으로 켤 수 있습니다. 렌더링 순서상 DoF/Bloom보다 먼저 적용되므로, Sharpen이 켜져 있으면 DoF/Bloom도 이미 선명화된 화면을 원본으로 사용합니다.

### getEnableSharpen(), setEnableSharpen(set) → boolean

> Sharpen 포스트프로세싱 사용 여부를 설정/반환합니다. 기본값은 false입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                |
| ---- | ------- | ---------------------------------------------- |
| set  | boolean | <p>true: 사용.<br>false: 미사용(기본값).</p> |

-   Return(getEnableSharpen)
    -   boolean: 현재 Sharpen 사용 여부.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setEnableSharpen(true);
var enabled = postProcess.getEnableSharpen();
```

{% endtab %}
{% endtabs %}

### getSharpenStrength(), setSharpenStrength(strength) → number

> 언샤프 마스크 강도를 설정/반환합니다. 값이 클수록 화면 경계 대비가 강하게 또렷해집니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description                               |
| -------- | ------ | ---------------------------------------------- |
| strength | number | 선명화 강도. 0~2 범위로 clamp. 기본값 0.5. |

-   Return(getSharpenStrength)
    -   number: 현재 설정된 선명화 강도.

{% endtab %}
{% tab title="Template" %}

```javascript
postProcess.setSharpenStrength(0.5);
var strength = postProcess.getSharpenStrength();
```

{% endtab %}
{% endtabs %}

## Sample

```javascript
var pp = Module.getPostProcess();

// DoF: 자동 초점 + 강한 흐림
pp.setEnableDoF(true);
pp.setDofAutoFocus(true);
pp.setDofAutoFocusRange(80);
pp.setDofAperture(0.8);
pp.setDofMaxBlurRadius(48);
pp.setDofBlurIterations(3);

// Bloom
pp.setEnableBloom(true);
pp.setBloomThreshold(0.6);
pp.setBloomIntensity(0.6);

// Sharpen — DoF/Bloom 없이도 단독 사용 가능
pp.setEnableSharpen(true);
pp.setSharpenStrength(0.5);
```
