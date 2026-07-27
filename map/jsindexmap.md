---
description: 지도 내 인덱스 맵을 설정 및 제어하기 위한 API 입니다.
---

# JSIndexMap

> Module.getIndexMap() API를 생성합니다.

```javascript
var map = Module.getIndexMap();
```

## Function

### createLayer(layerName, layerType)

> 인덱스 맵에 새로운 레이어를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description      |
| --------- | ------ | ----------------- |
| layerName | string | 생성할 레이어 명칭. |
| layerType | number | 레이어 타입 값.    |

{% endtab %}
{% tab title="Template" %}

```javascript
var indexMap3D = Module.getIndexMap();
indexMap3D.createLayer("layer1", 0);
```

{% endtab %}
{% endtabs %}

### addObject(layerName, object) → boolean

> 인덱스 맵의 특정 레이어에 객체를 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                     | Description        |
| --------- | ----------------------------------------- | ------------------- |
| layerName | string                                    | 대상 레이어 명칭.   |
| object    | [JSObject3D](../object/jsobject3d.md)     | 추가할 객체.        |

-   Return
    -   true: 추가 성공.
    -   false: 대상 레이어를 찾지 못했거나, 객체의 내부 오브젝트가 유효하지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeObject(layerName, objectKey) → boolean

> 인덱스 맵의 특정 레이어에서 객체를 제거합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description         |
| --------- | ------ | -------------------- |
| layerName | string | 대상 레이어 명칭.    |
| objectKey | string | 제거할 객체 고유 키. |

-   Return
    -   true: 제거 성공.
    -   false: 대상 레이어를 찾지 못했거나, 레이어에 객체가 없거나, 레이어가 메모리 기반 레이어가 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### keyAtObject(layerName, objectKey) → object

> 인덱스 맵의 특정 레이어에서 고유 키에 해당하는 객체를 조회합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description         |
| --------- | ------ | -------------------- |
| layerName | string | 대상 레이어 명칭.    |
| objectKey | string | 조회할 객체 고유 키. |

-   Return
    -   object: 조회된 객체.
    -   null: 대상 레이어 또는 객체를 찾지 못한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDistanceMinMax(min, max)

> 인덱스 맵에서 사용할 카메라 옵션을 설정합니다.
>
> 인덱스 맵과 카메라의 시야 최소, 최대 거리를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                     |
| ---- | ------ | ------------------------------- |
| min  | number | 가시화 최소 거리 (meters 단위). |
| max  | number | 가시화 최대 거리 (meters 단위). |

{% endtab %}

{% tab title="Template" %}

```javascript
var indexMap3D = Module.getIndexMap();
indexMap3D.setDistanceMinMax(50, 3000);
indexMap3D.setVisible(true);
```

{% endtab %}
{% endtabs %}

### setDistance(min, max)

> setDistanceMinMax(min, max)와 동일한 기능입니다 (cpp에서 같은 구현부에 바인딩된 별칭 함수).

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                     |
| ---- | ------ | ------------------------------- |
| min  | number | 가시화 최소 거리 (meters 단위). |
| max  | number | 가시화 최대 거리 (meters 단위). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getDistanceMin() → number

> 설정된 시야 최소 거리를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 시야 최소 거리 (meters 단위).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getDistanceMax() → number

> 설정된 시야 최대 거리를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 시야 최대 거리 (meters 단위).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setCameraMode(mode)

> 인덱스 맵 카메라 모드를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| mode | number | 카메라 모드 값. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setVisibleLayer(layerName, visible)

> 인덱스 맵(메인뷰) 내 특정 레이어의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description                                            |
| --------- | ------- | ------------------------------------------------------- |
| layerName | string  | 대상 레이어 명칭.                                       |
| visible   | boolean | <p>true: 레이어 가시화.<br>false: 레이어 비가시화.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getCameraTilt(), setCameraTilt(tilt) → number

> 인덱스 맵에서 사용할 카메라 기울기(degrees 단위)를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| tilt | number | 카메라 기울기. |

-   Return (get)
    -   number: 현재 카메라 기울기.

{% endtab %}

{% tab title="Template" %}

```javascript
var indexMap3D = Module.getIndexMap();
indexMap3D.setCameraTilt(89.9);
var tilt = indexMap3D.getCameraTilt();
indexMap3D.setVisible(true);
```

{% endtab %}
{% endtabs %}

### getViewMode(), setViewMode(mode) → number

> 인덱스 맵 뷰 모드를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------- |
| mode | number | 뷰 모드 값.   |

-   Return (get)
    -   number: 현재 뷰 모드 값.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean

> 인덱스 맵 가시화 유무를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                                 |
| ------- | ------- | ----------------------------------------------------------- |
| visible | boolean | <p>true: 인덱스 맵 가시화.<br>false: 인덱스 맵 비가시화.<p> |

-   Return (get)
    -   true: 가시화 상태.
    -   false: 비가시화 상태.

{% endtab %}

{% tab title="Template" %}

```javascript
var indexMap3D = Module.getIndexMap();
indexMap3D.setVisible(true);
var visible = indexMap3D.getVisible();
```

{% endtab %}
{% endtabs %}

### getRatio(), setRatio(ratio) → number

> 인덱스 맵 축척 비율을 설정하거나 반환합니다.
>
> 입력 변수값(ratio)이 1.0 미만인 경우 1.0으로 보정됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| ----- | ------ | -------------- |
| ratio | number | 축척 비율 값. (1.0 이상) |

-   Return (get)
    -   number: 현재 축척 비율 값.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getSize(), setSize(width, height) → JSSize2D

> 인덱스 맵 가로 세로 크기를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description              |
| ------ | ------ | ------------------------ |
| width  | number | 가로 크기 (pixels 단위). |
| height | number | 세로 크기 (pixels 단위). |

-   Return (get)
    -   [JSSize2D](../core/jssize2d.md): 현재 가로, 세로 크기.

{% endtab %}

{% tab title="Template" %}

```javascript
var indexMap3D = Module.getIndexMap();
indexMap3D.setSize(400, 200);
var size = indexMap3D.getSize();
indexMap3D.setVisible(true);
```

{% endtab %}
{% endtabs %}

### getPosition(), setPosition(x, y) → JSVector2D

> 인덱스 맵의 화면상 위치를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                  |
| ---- | ------ | ---------------------------- |
| x    | number | 화면 X축 좌표 (pixels 단위). |
| y    | number | 화면 Y축 좌표 (pixels 단위). |

-   Return (get)
    -   [JSVector2D](../core/jsvector2d.md): 현재 화면상 위치 (x, y).

{% endtab %}

{% tab title="Template" %}

```javascript
var indexMap3D = Module.getIndexMap();
indexMap3D.setPosition(1300, 10);
var position = indexMap3D.getPosition();
indexMap3D.setVisible(true);
```

{% endtab %}
{% endtabs %}

### getVisionColor(), setVisionColor(red, green, blue, alpha) → JSColor

> 인덱스 맵 시야 영역(vision) 색상을 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| ----- | ------ | ------------------ |
| red   | number | 색상 red 값 (0~255).   |
| green | number | 색상 green 값 (0~255). |
| blue  | number | 색상 blue 값 (0~255).  |
| alpha | number | 색상 alpha 값 (0~255). |

-   Return (get)
    -   [JSColor](../core/jscolor.md): 현재 시야 영역 색상.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getCameraPosition(), setCameraPosition(position) → JSVector3D

> 인덱스 맵 카메라 위치를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                   | Description         |
| -------- | --------------------------------------- | -------------------- |
| position | [JSVector3D](../core/jsvector3d.md)     | 카메라 위치 (경도, 위도, 거리). |

-   Return (get)
    -   [JSVector3D](../core/jsvector3d.md): 현재 카메라 위치.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTilt(), setTilt(tilt) → number

> getCameraTilt() / setCameraTilt(tilt)와 동일한 기능입니다 (cpp 내부적으로 서로를 호출하는 별칭 함수).

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| tilt | number | 카메라 기울기. |

-   Return (get)
    -   number: 현재 카메라 기울기.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getDirection(), setDirection(direction) → number

> 인덱스 맵 카메라 방향(회전각, degrees 단위)을 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| --------- | ------ | ------------------ |
| direction | number | 카메라 방향 (degrees 단위). |

-   Return (get)
    -   number: 현재 카메라 방향.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getFOV(), setFOV(fov) → number

> 인덱스 맵 카메라 시야각(FOV, degrees 단위)을 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description               |
| ---- | ------ | -------------------------- |
| fov  | number | 카메라 시야각 (degrees 단위). |

-   Return (get)
    -   number: 현재 카메라 시야각.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}
