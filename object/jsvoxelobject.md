---
description: 지도 내 볼륨(연기, 구름, 불꽃, 물 등) 시각화를 위한 복셀(Voxel) 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSVoxelObject

> Module.createVoxelObject() API를 생성합니다.
>
> 레이 마칭(Ray Marching) 기반의 3D 텍스처를 사용해 구름, 불꽃, 물, 태풍 등의 볼륨 효과를 표현합니다. [textureType](jsvoxelobject.md#texturetype-gettexturetype-settexturetypetype-number) 설정에 따라 여러 속성 값이 프리셋으로 일괄 조정됩니다.

```javascript
var voxel = Module.createVoxelObject("ID");
```

## Function

### createVoxel(option) → string

> 단일 형태(박스 또는 구)의 복셀 볼륨 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type                                | Description                                          |
| :--------- | -------------------------------------- | ---------------------------------------------------------- |
| option     | object                                  | 생성 옵션.                                                 |
| ↳ type     | string                                  | 형태("box" 또는 "sphere").                                 |
| ↳ position | [JSVector3D](../core/jsvector3d.md)  | 중심 좌표(경도, 위도, 고도).                                |
| ↳ color    | [JSColor](../core/jscolor.md)(optional, 기본값 흰색) | 채움 색상.                                    |
| ↳ size     | [JSVector3D](../core/jsvector3d.md)  | (type이 "box"인 경우 필수) 박스 크기(x, y, z).             |
| ↳ radius   | number                                  | (type이 "sphere"인 경우 필수) 구 반지름.                   |

-   Return
    -   "success": 생성 성공.
    -   "null": 월드 또는 객체가 초기화되지 않은 경우.
    -   이 외 문자열: 실패 원인 메시지(필수 항목 누락 등).

{% endtab %}
{% tab title="Template" %}

```javascript
var voxel = Module.createVoxelObject("Voxel_1");
voxel.createVoxel({
    type: "box",
    position: new Module.JSVector3D(127.0, 37.5, 100.0),
    size: new Module.JSVector3D(50.0, 50.0, 50.0),
    color: new Module.JSColor(150, 255, 255, 255)
});
```

{% endtab %}
{% endtabs %}

### createGridVoxel(option) → string

> 격자(grid) 데이터 또는 다각형(polygon) 좌표를 기반으로, 여러 개의 복셀 인스턴스로 구성된 볼륨 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name           | Type                        | Description                                                                |
| :------------- | ------------------------------ | -------------------------------------------------------------------------------- |
| option         | object                          | 생성 옵션.                                                                        |
| ↳ type         | string                          | 생성 방식("grid" 또는 "polygon").                                                 |
| ↳ color        | [JSColor](../core/jscolor.md)(optional, 기본값 흰색) | 채움 색상.                                                     |
| ↳ union        | boolean(optional, 기본값 false) | 지형 고도 결합 여부(true 시 position/좌표의 고도를 지형 고도로 자동 계산).       |
| ↳ gridData     | array(number)                   | 각 셀(인스턴스)의 값 배열(밀도/표시 여부 등으로 사용되는 것으로 추정).           |
| ↳ cellSize     | [JSVector3D](../core/jsvector3d.md) | 셀 크기(x, y, z).                                                          |
| ↳ position     | [JSVector3D](../core/jsvector3d.md) | (type이 "grid"인 경우 필수) 격자 기준 좌표.                                |
| ↳ gridWidth    | number                          | (type이 "grid"인 경우) 격자 X 방향 셀 개수.                                       |
| ↳ gridHeight   | number                          | (type이 "grid"인 경우) 격자 Y 방향 셀 개수.                                       |
| ↳ gridDepth    | number                          | (type이 "grid"인 경우) 격자 Z 방향 셀 개수.                                       |
| ↳ lon          | array(number)                   | (type이 "polygon"인 경우 필수) 각 인스턴스의 경도 목록.                           |
| ↳ lat          | array(number)                   | (type이 "polygon"인 경우 필수) 각 인스턴스의 위도 목록.                           |
| ↳ alt          | array(number)(optional)         | (type이 "polygon"인 경우) 각 인스턴스의 고도 목록(union이 true면 무시되고 지형 고도 사용, 생략 시 0). |

-   Return
    -   "success": 생성 성공.
    -   "null": 월드 또는 객체가 초기화되지 않은 경우.
    -   이 외 문자열: 실패 원인 메시지(필수 항목 누락 등).

{% endtab %}
{% tab title="Template" %}

```javascript
var voxel = Module.createVoxelObject("GridVoxel_1");
voxel.createGridVoxel({
    type: "grid",
    position: new Module.JSVector3D(127.0, 37.5, 0.0),
    gridWidth: 10,
    gridHeight: 10,
    gridDepth: 10,
    cellSize: new Module.JSVector3D(5.0, 5.0, 5.0),
    gridData: gridValueArray,
    union: true
});
```

{% endtab %}
{% endtabs %}

### updateGridData(gridData) → string

> [createGridVoxel()](jsvoxelobject.md#creategridvoxeloption-string)로 "grid" 타입으로 생성한 인스턴스들의 데이터를 갱신합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type          | Description        |
| :------- | ------------- | -------------------------- |
| gridData | array(number) | 갱신할 셀 값 배열.          |

-   Return
    -   "success": 갱신 성공.
    -   "null": 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.updateGridData(newGridValueArray);
```

{% endtab %}
{% endtabs %}

### updatePolygonData(gridData) → string

> [createGridVoxel()](jsvoxelobject.md#creategridvoxeloption-string)로 "polygon" 타입으로 생성한 인스턴스들의 데이터를 갱신합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type          | Description        |
| :------- | ------------- | -------------------------- |
| gridData | array(number) | 갱신할 인스턴스 값 배열.    |

-   Return
    -   "success": 갱신 성공.
    -   "null": 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.updatePolygonData(newValueArray);
```

{% endtab %}
{% endtabs %}

### setColor(color) → boolean

> 복셀 객체의 색상을 설정합니다. [red](jsvoxelobject.md#red-getred-setredred-number), [green](jsvoxelobject.md#green-getgreen-setgreengreen-number), [blue](jsvoxelobject.md#blue-getblue-setblueblue-number), [alpha](jsvoxelobject.md#alpha-getalpha-setalphaalpha-number) 프로퍼티를 통해 개별 채널만 변경할 수도 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description |
| :---- | ----------------------------- | ----------- |
| color | [JSColor](../core/jscolor.md) | 설정할 색상. |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.setColor(new Module.JSColor(150, 255, 255, 255));
```

{% endtab %}
{% endtabs %}

### setTextureData(data, size) → void

> 미리 계산된 3D 텍스처 픽셀 데이터를 직접 업로드합니다. 호출 시 [textureType](jsvoxelobject.md#texturetype-gettexturetype-settexturetypetype-number)이 내부적으로 8(사용자 정의 텍스처)로 설정됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type          | Description                                        |
| :--- | ------------- | -------------------------------------------------------- |
| data | array(number) | 3D 텍스처 픽셀 데이터(R8 포맷, size\*size\*size 길이).    |
| size | number        | 텍스처 한 변의 크기(정육면체, size x size x size).        |

-   Note
    -   호출 후 [scale](jsvoxelobject.md#scale-getscale-setscalescale-number), [amount](jsvoxelobject.md#amount-getamount-setamountamount-number), [softness](jsvoxelobject.md#softness-getsoftness-setsoftnesssoftness-number), [width](jsvoxelobject.md#width-getwidth-setwidthwidth-number)/[height](jsvoxelobject.md#height-getheight-setheightheight-number)/[depth](jsvoxelobject.md#depth-getdepth-setdepthdepth-number) 프로퍼티는 `textureType`이 8인 동안 변경되지 않습니다(내부적으로 무시됨).

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.setTextureData(texture3DPixelData, 64);
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### textureType (property), getTextureType(), setTextureType(type) → number

> 볼륨 효과 프리셋 타입을 설정합니다. 설정 시 [threshold](jsvoxelobject.md#threshold-getthreshold-setthresholdthreshold-number), [range](jsvoxelobject.md#range-getrange-setrangerange-number), [opacity](jsvoxelobject.md#opacity-getopacity-setopacityopacity-number), [steps](jsvoxelobject.md#steps-getsteps-setstepssteps-number), [width](jsvoxelobject.md#width-getwidth-setwidthwidth-number)/[height](jsvoxelobject.md#height-getheight-setheightheight-number)/[depth](jsvoxelobject.md#depth-getdepth-setdepthdepth-number), 색상 등 다수의 속성이 프리셋 값으로 일괄 재설정됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                                                                    |
| :--- | ------ | --------------------------------------------------------------------------------------------------------------------- |
| type | number | <p>0: 세슘 구름<br>1: 일반 구름<br>2: 불꽃<br>3~5: 산불<br>6: 물<br>7: 태풍<br>8: 사용자 정의 텍스처([setTextureData()](jsvoxelobject.md#settexturedatadata-size-void) 사용 시 자동 설정)</p> |

-   Note
    -   0 미만 값은 무시됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.textureType = 1; // 일반 구름 프리셋 적용
```

{% endtab %}
{% endtabs %}

### voxelCount (property), getVoxelCount(), setVoxelCount(count) → number

> 복셀 인스턴스 개수를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
| :---- | ------ | ------------------------ |
| count | number | 복셀 인스턴스 개수.       |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.voxelCount = 100;
```

{% endtab %}
{% endtabs %}

### red (property), getred(), setred(red) → number

> 색상 R 채널 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
| :--- | ------ | ---------------------- |
| red  | number | R 채널 값(0~255).        |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.red = 255;
```

{% endtab %}
{% endtabs %}

### green (property), getgreen(), setgreen(green) → number

> 색상 G 채널 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| :---- | ------ | ---------------------- |
| green | number | G 채널 값(0~255).        |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.green = 255;
```

{% endtab %}
{% endtabs %}

### blue (property), getblue(), setblue(blue) → number

> 색상 B 채널 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
| :--- | ------ | ---------------------- |
| blue | number | B 채널 값(0~255).        |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.blue = 255;
```

{% endtab %}
{% endtabs %}

### alpha (property), getalpha(), setalpha(alpha) → number

> 색상 투명도(Alpha) 채널 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| :---- | ------ | ---------------------- |
| alpha | number | 투명도 값(0~255).        |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.alpha = 150;
```

{% endtab %}
{% endtabs %}

### threshold (property), getthreshold(), setthreshold(threshold) → number

> 레이 마칭 시 볼륨을 표시하는 밀도 임계값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description  |
| :-------- | ------ | ------------------ |
| threshold | number | 밀도 임계값.         |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.threshold = 0.3;
```

{% endtab %}
{% endtabs %}

### range (property), getrange(), setrange(range) → number

> 볼륨 효과의 표시 범위(효과별로 물결 진폭 등으로도 사용됨)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | ------ | ------------------ |
| range | number | 표시 범위 값.        |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.range = 0.1;
```

{% endtab %}
{% endtabs %}

### opacity (property), getopacity(), setopacity(opacity) → number

> 볼륨 효과의 전체 투명도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description  |
| :------ | ------ | ------------------ |
| opacity | number | 투명도(0.0~1.0 범위로 추정). |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.opacity = 0.25;
```

{% endtab %}
{% endtabs %}

### steps (property), getsteps(), setsteps(steps) → number

> 레이 마칭 반복 계산 스텝 수를 설정합니다(값이 클수록 품질이 높아지나 연산량이 증가합니다).

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                          |
| :---- | ------ | ------------------------------------------ |
| steps | number | 레이 마칭 스텝 수(1 미만 입력 시 1로 보정). |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.steps = 100;
```

{% endtab %}
{% endtabs %}

### scale (property), getscale(), setscale(scale) → number

> 볼륨 노이즈 스케일을 설정합니다. [textureType](jsvoxelobject.md#texturetype-gettexturetype-settexturetypetype-number)이 8(사용자 정의 텍스처)인 경우 무시됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| :---- | ------ | ------------------ |
| scale | number | 노이즈 스케일 값.    |

-   Note
    -   설정 시 내부적으로 캐시된 3D 텍스처가 재생성됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.scale = 2.0;
```

{% endtab %}
{% endtabs %}

### amount (property), getamount(), setamount(amount) → number

> 볼륨 노이즈 임계값(양)을 설정합니다. [textureType](jsvoxelobject.md#texturetype-gettexturetype-settexturetypetype-number)이 8인 경우 무시됩니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                          |
| :----- | ------ | ------------------------------------------ |
| amount | number | 노이즈 임계값(1.0 초과 입력 시 1.0으로 보정). |

-   Note
    -   설정 시 내부적으로 캐시된 3D 텍스처가 재생성됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.amount = 0.45;
```

{% endtab %}
{% endtabs %}

### softness (property), getsoftness(), setsoftness(softness) → number

> 볼륨 노이즈의 대비(Contrast, 경계 부드러움)를 설정합니다. [textureType](jsvoxelobject.md#texturetype-gettexturetype-settexturetypetype-number)이 8인 경우 무시됩니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description   |
| :------- | ------ | ------------------ |
| softness | number | 노이즈 대비 값.      |

-   Note
    -   설정 시 내부적으로 캐시된 3D 텍스처가 재생성됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.softness = 2.5;
```

{% endtab %}
{% endtabs %}

### width (property), getwidth(), setwidth(width) → number

> 볼륨 3D 텍스처의 X축(너비) 해상도를 설정합니다. [textureType](jsvoxelobject.md#texturetype-gettexturetype-settexturetypetype-number)이 8인 경우 무시됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| :---- | ------ | ---------------------- |
| width | number | 텍스처 X축 해상도.       |

-   Note
    -   설정 시 내부적으로 캐시된 3D 텍스처가 재생성됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.width = 100;
```

{% endtab %}
{% endtabs %}

### height (property), getheight(), setheight(height) → number

> 볼륨 3D 텍스처의 Y축(높이) 해상도를 설정합니다. [textureType](jsvoxelobject.md#texturetype-gettexturetype-settexturetypetype-number)이 8인 경우 무시됩니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description       |
| :----- | ------ | ---------------------- |
| height | number | 텍스처 Y축 해상도.       |

-   Note
    -   설정 시 내부적으로 캐시된 3D 텍스처가 재생성됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.height = 100;
```

{% endtab %}
{% endtabs %}

### depth (property), getdepth(), setdepth(depth) → number

> 볼륨 3D 텍스처의 Z축(깊이) 해상도를 설정합니다. [textureType](jsvoxelobject.md#texturetype-gettexturetype-settexturetypetype-number)이 8인 경우 무시됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| :---- | ------ | ---------------------- |
| depth | number | 텍스처 Z축 해상도.       |

-   Note
    -   설정 시 내부적으로 캐시된 3D 텍스처가 재생성됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.depth = 100;
```

{% endtab %}
{% endtabs %}

### union (property), getunion(), setunion(union) → boolean

> 복셀 위치의 고도를 지형 고도에 결합할지 여부를 설정합니다. [createGridVoxel()](jsvoxelobject.md#creategridvoxeloption-string)의 `option.union`과 동일한 값입니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                            |
| :---- | ------- | -------------------------------------------- |
| union | boolean | <p>true: 지형 고도 결합.<br>false: 미결합.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
voxel.union = true;
```

{% endtab %}
{% endtabs %}
