---
description: 지도 내 절두체 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSViewFrustum

> Module.createViewFrustum() API를 생성합니다.

```javascript
var object = Module.createViewFrustum("ID");
```

## Function

### createViewFrustum(position, pan, tilt, x, y, distance)

> 절두체 객체를 생성합니다.
>
> pan 입력 값에 따른 회전 정보
>
> -   0, 360: north.
> -   90: east.
> -   180: south.
> -   270: west.
>
> tilt 입력 값에 따른 회전 정보 0(정면), tilt&lt;0(상단), tilt&gt;0(하단).
>
> -   0 : front.
> -   tilt&lt;0: top.
> -   tilt&gt;0: bottom.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                  |
| :------- | :---------------------------------- | :--------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 중심 좌표(경도, 위도, 고도). |
| pan      | number                              | Y축 회전 설정.               |
| tilt     | number                              | X축 회전 설정.               |
| x        | number                              | 화각 너비 설정.              |
| y        | number                              | 화각 높이 설정.              |
| distance | number                              | 길이 설정.                   |

-   Sample
    -   function init 참조.
    -   [Sandbox_Frustum](https://sandbox.egiscloud.com/code/main.do?id=object_frustum)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getEyepos() → [JSVector3D](../core/jsvector3d.md)

> 절두체 객체의 중심 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md) : 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getFov() → [JSVector2D](../core/jsvector2d.md)

> 절두체 객체의 화각(x: 너비, y: 높이)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector2D](../core/jsvector2d.md) : 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getId() → string

> 객체의 고유 명칭을 반환 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strKey = object.getId();
```

{% endtab %}
{% endtabs %}

### setFovX(value) → boolean

> 절두체 객체의 화각 너비를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description |
| :---- | :----- | :---------- |
| value | number | 너비 값.    |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function resutFrustum 참조.
    -   [Sandbox_Frustum](https://sandbox.egiscloud.com/code/main.do?id=object_frustum)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFovY(value) → boolean

> 절두체 객체의 화각 높이를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description |
| :---- | :----- | :---------- |
| value | number | 높이 값.    |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function resutFrustum 참조.
    -   [Sandbox_Frustum](https://sandbox.egiscloud.com/code/main.do?id=object_frustum)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createSlicedViewFrustum(eye, pan, tilt, xAngle, yAngle, maxDistance, widthSegment, heightSegment)

> 절두체를 가로/세로 분할된(sliced) 셀 형태로 생성합니다.
>
> pan, tilt 입력값에 따른 회전 정보는 [createViewFrustum()](jsviewfrustum.md#createviewfrustumposition-pan-tilt-x-y-distance)과 동일합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type                                 | Description                    |
| :------------ | -------------------------------------- | --------------------------------- |
| eye           | [JSVector3D](../core/jsvector3d.md)   | 시점 중심 좌표(경도, 위도, 고도). |
| pan           | number                                  | Y축 회전 설정.                    |
| tilt          | number                                  | X축 회전 설정.                    |
| xAngle        | number                                  | 화각 너비 설정.                   |
| yAngle        | number                                  | 화각 높이 설정.                   |
| maxDistance   | number                                  | 절두체 길이.                      |
| widthSegment  | number                                  | 가로 분할 개수.                   |
| heightSegment | number                                  | 세로 분할 개수.                   |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getPlaneEdge(planeType) → [JSVec3Array](../core/jsvec3array.md)

> 절두체를 구성하는 특정 평면의 경계 좌표 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description             |
| :-------- | :----- | :------------------------- |
| planeType | number | 조회할 평면 타입 번호(내부 정의값). |

-   Return
    -   [JSVec3Array](../core/jsvec3array.md): 경계 좌표 목록(경도, 위도, 고도). 조회 실패 시 빈 배열.

{% endtab %}
{% tab title="Template" %}

```javascript
var edge = frustum.getPlaneEdge(0);
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### eyePosition, eye_position (property), setEyePosition(position) → [JSVector3D](../core/jsvector3d.md)

> 절두체 객체의 중심(시점) 좌표를 설정합니다.
>
> [getEyepos()](jsviewfrustum.md#geteyepos-jsvector3d) 함수와 동일한 값을 프로퍼티(`object.eyePosition` 또는 `object.eye_position`) 형태로도 조회할 수 있으며, 이 프로퍼티를 통해서만 값을 설정(set)할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                   |
| -------- | ------------------------------------ | -------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 중심(시점) 좌표(경도, 위도, 고도). |

{% endtab %}
{% tab title="Template" %}

```javascript
frustum.eyePosition = new Module.JSVector3D(127.0, 37.5, 100.0);
var eye = frustum.eyePosition;
```

{% endtab %}
{% endtabs %}

### getColor(), setColor(color) → [JSColor](../core/jscolor.md)

> 젇루체 객체의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description |
| ----- | ----------------------------- | ----------- |
| color | [JSColor](../core/jscolor.md) | 색상 값.    |

-   Return
    -   [JSColor](../core/jscolor.md): 반환 성공.
    -   null: 반환 실패.
-   Sample
    -   function createViewFrustum 참조.
    -   [Sandbox_Frustum](https://sandbox.egiscloud.com/code/main.do?id=object_frustum)

{% endtab %}
{% tab title="Template" %}

```javascript
// ... or ...
```

{% endtab %}
{% endtabs %}

### getDescription(), setDescription(desc) → string

> 객체에 대한 설명을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| desc | string | 설명 문자열. |

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strDesc = object.getDescription();
// ... or ...
object.setDescription("First Object.");
```

{% endtab %}
{% endtabs %}

### getName(), setName(name) → string

> 객체 이름을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 이름.  |

-   Return
    -   string: 객체 이름을 성공적을 반환
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setName("MyObject");
```

{% endtab %}
{% endtabs %}

### getPan(), setPan(pan) → number

> 절두체 객체의 y축 회전값을 설정합니다.
>
> pan 입력 값에 따른 회전 정보
>
> -   0, 360: north
> -   90: east
> -   180: south
> -   270: west

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| pan  | number | y축 회전 값. |

-   Return
    -   number: 설정된 y축 회전값.
-   Sample
    -   function resutFrustum 참조.
    -   [Sandbox_Frustum](https://sandbox.egiscloud.com/code/main.do?id=object_frustum)

{% endtab %}
{% tab title="Template" %}

```javascript
var frustum = Module.createViewFrustum(id);
frustum.createFrustum(
    // Somthing...
)
frustum.setPan(90);
```

{% endtab %}
{% endtabs %}

### getTilt(), setTilt(tilt) → number

> 절두체 객체의 x축 회전값을 설정합니다.
>
> tilt 입력 값에 따른 회전 정보 0(정면), tilt&lt;0(상단), tilt&gt;0(하단).
>
> -   0 : front.
> -   tilt&lt;0: top.
> -   tilt&gt;0: bottom.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| tilt | number | x축 회전 값. |

-   Return

    -   number: 설정된 x축 회전값.

-   Sample
    -   function resutFrustum 참조.
    -   [Sandbox_Frustum](https://sandbox.egiscloud.com/code/main.do?id=object_frustum)

{% endtab %}
{% tab title="Template" %}

```javascript
var frustum = Module.createViewFrustum(id);
frustum.createFrustum(
    // Somthing...
)
frustum.setTilt(-10);
```

{% endtab %}
{% endtabs %}

### getDistance(), setDistance(distance) → number

> 절두체 객체의 길이를 설정 및 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description  |
| -------- | ------ | ------------ |
| distance | number | 절두체 길이. |

-   Return
    -   number: 설정된 절두체의 길이.

{% endtab %}
{% tab title="Template" %}

```javascript
var frustum = Module.createViewFrustum(id);
frustum.createFrustum(
    // Somthing...
)
frustum.setDistance(100.0);
```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean

> 객체의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                        |
| ------- | ------- | -------------------------------------------------- |
| visible | boolean | <p>true: 객체 가시화.<br>false: 객체 비가시화.</p> |

-   Return
    -   true: 객체 가시화 상태.
    -   false: 객체 비가시화 상태.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setVisible(true);
```

{% endtab %}
{% endtabs %}
