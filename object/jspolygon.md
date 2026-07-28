---
description: 지도 내 평면 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSPolygon

> Module.createPolygon() API를 생성합니다.

```javascript
var object = Module.createPolygon("ID");
```

## Function

### getArea() → number

> 평면 객체의 면적을 반환합니다.
>
> 평면 객체의 면적은 지형 곡면률을 고려하지 않는 단순 면적값을 계산합니다.
>
> RTT 가시화 중인 평면 객체의 면적과 3D 가시화 평면 객체의 면적은 서로 상이 할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number > 0: 반환 성공.
    -   number == 0: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var area = object.getArea();
```

{% endtab %}
{% endtabs %}

### getBoundary() → [JSAABBox3D](../core/jsaabbox3d.md)

> 평면 객체의 공간 영역 좌표(경도, 위도, 고도)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSAABBox3D](../core/jsaabbox3d.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var boundary = object.getBoundary();
var boundary_min = boundary.min;
var boundary_max = boundary.max;
```

{% endtab %}
{% endtabs %}

### getCenter() → [JSVector3D](../core/jsvector3d.md)

> 객체의 중심 좌표(경도, 위도, 고도)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var vCenter = object.getCenter();
var dCenterLon = vCenter.Longitude;
var dCenterLat = vCenter.Latitude;
var dCenterAlt = vCenter.Altitude;
```

{% endtab %}
{% endtabs %}

### getParts() → [Collection](../core/collection.md)

> 객체의 파트 리스트를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [Collection](../core/collection.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getExtent() → number

> 평면 객체의 공간 영역의 장축 거리를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 거리 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var bExtends = object.getExtent();
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

### loadFile(option) → boolean

> 3ds 포맷 파일 정보를 기반으로 평면 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                              | Description |
| ------ | ----------------------------------------------------------------- | ----------- |
| option | [JSPolygon.loadFileOption](jspolygon.md#jspolygon.loadfileoption) | 속성 정보.  |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   positionmode=true 일 때 projectioncode가 설정되지 않은 경우
        -   positionmode=false 일 때 position이 지정되지 않은 경우
-   Sample
    -   the load3DS function 참조.
    -   [Sandbox_3DS](https://sandbox.egiscloud.com/code/main.do?id=object_file_3ds)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### loadTexture(id, url) → boolean

> 평면 객체에 사용할 이미지를 설정합니다.
>
> 입력 변수값(id)은 [setFaceTexture](jspolygon.md#setfacetexture-index-id-boolean) API로 텍스쳐를 적용할 때 텍스쳐를 구분하는 용도로 사용합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| id   | string | 고유 명칭.  |
| url  | string | 이미지 url. |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   If there is already a texture with the same name.
        -   If name, url are empty strings.
-   Sample
    -   the init function 참조.
    -   [Sandbox_Polygon RTT](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_image_changing)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setCircle(position, radius, segment)

> 중심 좌표(경도, 위도, 고도)를 기준으로 원 객체를 생성합니다.
>
> 입력 변수값(radius)으로 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                   |
| -------- | ----------------------------------- | ----------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 중심 좌표 (경도, 위도, 고도). |
| radius   | number                              | 반지름 (in meter).            |
| segment  | number                              | 단면의 다각수.                |

-   Sample
    -   the createCirclePolygon function 참조.
    -   [Sandbox_Circle Polygon](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_circle)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSphere(parameter) → object

> 중심 좌표(경도, 위도, 고도)를 기준으로 구 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description                   |
| -------- | ------ | ----------------------------- |
| paramter | object | 구의 속성을 구성하는 객체입니다. `{ position, radius, segment, color }` 형태로 구성됩니다. |

-   Return
    -   object
        -   result: 1 → 생성 성공 / 0 → 실패
        -   name: `"JSPolygon.setSphere"`
        -   return: 메시지 문자열 (실패 시 오류 메시지, 성공 시 `"success"`)
-   Description
    -   `position`([JSVector3D](../core/jsvector3d.md))이 포함되지 않으면 구 폴리곤이 생성되지 않고 실패 결과를 반환합니다.
    -   속성에는 `radius`(number), `segment`(number), `color`([JSVector3D](../core/jscolor.md))가 포함됩니다.
    -   각 속성의 기본값은 `radius`(10), `segment`(30), `color`({255, 255, 255, 255}) 입니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var polygon = Module.createPolygon("SPHERE");

var param = {
    position : new Module.JSVector3D(129.127, 35.17, 160.0),
    radius : 10,
    segment : 30,
    color : new Module.JSColor(255, 255, 255, 0)
};

polygon.setSphere(param);
```

{% endtab %}
{% endtabs %}

### setFaceTexture(index, id) → boolean

> 평면 객체를 구성하는 face에 이미지를 설정합니다.
>
> 입력 변수값(id)은 [loadTexture](jspolygon.md#loadtexture-id-url-boolean) API에 입력된 고유명칭 입니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| index | number | face 인덱스. |
| id    | string | 고유 명칭.   |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   등록한 이미지 고유 명칭이 없는 경우.
        -   입력 변수값(index)이 평면 객체 face 갯수를 초과 또는 음수값이 설정된 경우.
-   Sample
    -   the init function 참조.
    -   [Sandbox_Polygon RTT](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_image_changing)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFireEffect(type) → boolean

> 평면 객체에 불 효과를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                              |
| ---- | ------- | -------------------------------------------------------- |
| type | boolean | <p>true: 불 효과 가시화(RTT).<br>false: 기본 가시화.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   평면 객체 생성 실패한 경우.
-   Sample
    -   the createBurnEffectPolygon function 참조.
    -   [Sandbox_Fire Effect](https://sandbox.egiscloud.com/code/main.do?id=effect_fire)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWaterEffect(type, option) → boolean

> 평면 객체에 불 효과를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                     |
| ------ | ------- | ----------------------------------------------- |
| type   | boolean | <p>true: 물 효과 가시화.<br>false: 기본 가시화.</p> |
| option | object  | flow map 옵션                                    |

**options 구조**

| Name            | Type   | Description   |
| --------------- | ------ | ------------- |
| flow_map_url    | string | flow map url  |
| flow_map_width  | number | flow map 너비 |
| flow_map_height | number | flow map 높이 |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   평면 객체 생성 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setHeight(height) → boolean

> 평면 객체 생성 시 높이값을 가진 3d 객체를 생성합니다.
> 입력 변수값(height)은 0보다 큰값이 설정됩니다.
> 이 API는 기존에 `setPartCoordinates()` 또는 `setCoordinates()`로 정의된 객체에만 적용 가능합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description          |
| ------ | ------ | -------------------- |
| height | number | 객체 높이(in meter). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   평면 객체 생성 실패한 경우.
-   Sample
    -   the createPolygon function 참조.
    -   [Sandbox_Polygon Height](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_height)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setHeightByType(height, type) → boolean

> 평면 객체 생성 시 높이값을 가진 3d 객체를 생성합니다.
> 입력 변수값(type)은 윗면 정의 방법을 설정합니다.
> 이 API는 기존에 `setPartCoordinates()` 또는 `setCoordinates()`로 정의된 객체에만 적용 가능합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description          |
| ------ | ------ | -------------------- |
| height | number | 객체 높이(in meter).  |
| type   | number | <p>0: `setHeight()`(기존 방식) 사용(각 정점에서 일정 높이만큼 더함)<br>1: 윗면이 동일한 고도(height)가 되도록 보정</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   평면 객체 생성 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setHeights(height) → boolean

> 평면 객체 생성 시 높이값을 가진 3d 객체를 생성합니다.
> 입력 변수값(height)은 0보다 큰값이 설정되며, 각 정점에 대한 높이를 설정합니다.
> 이 API는 기존에 `setPartCoordinates()` 또는 `setCoordinates()`로 정의된 객체에만 적용 가능합니다.


{% tabs %}
{% tab title="Information" %}

| Name   | Type                                | Description          |
| ------ | ----------------------------------- | -------------------- |
| height | [Collection](../core/collection.md) | 각 정점에 대한 높이(in meter). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   평면 객체 생성 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setVerticalPlane(height, closed) → boolean

> 위가 뚫린 3D 객체(벽 폴리곤)를 생성합니다.
> 이 API는 기존에 `setPartCoordinates()` 또는 `setCoordinates()`로 정의된 객체에만 적용 가능합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description          |
| ------ | ------- | -------------------- |
| height | number  | 객체 높이(in meter).  |
| closed | boolean | 시작점과 끝점 연결 여부 |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   평면 객체 생성 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setVerticalPlane(50, true);
```

{% endtab %}
{% endtabs %}

### setFileMesh(path, name, pos) → boolean

> 모델 파일(3ds, xdo, 등)을 이용한 메쉬를 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                                | Description                   |
| ---- | ----------------------------------- | ----------------------------- |
| path | string                              | 파일 경로                      |
| name | string                              | 파일 이름                      |
| pos  | [JSVector3D](../core/jsvector3d.md) | 생성 중심 좌표 (경도, 위도, 고도) |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   파일 경로가 없거나 너무 긴 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetTexturePlane(coordinates, parts, uv, texture, type) → boolean

> 텍스처 지정 폴리곤을 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                            |
| ----------- | ------------------------------------- | ------------------------------------------------------ |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 정점 좌표 목록 (경도, 위도, 고도)                          |
| parts       | [Collection](../core/collection.md)   | 평면을 구성하는 coordinates 개수 목록                      |
| uv          | [JSVec2Array](../core/jsvec2array.md) | cordinates에 입력된 좌표 목록에 해당되는 uv 좌표 목록        |
| texture     | [JSIcon](../object/jsicon.md)         | 텍스쳐로 활용할 아이콘 객체                                |
| type        | boolean                               | <p>true: 지형 결합 가시화(RTT).<br>false: 기본 가시화.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   정점 좌표가 2개 이하인 경우.
        -   part가 하나도 없는 경우.
        -   uv 좌표가 2개 이하인 경우.
        -   정점 좌표 개수와 uv 좌표 개수가 다른 경우

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetTexture(texture, faceIndex, type) → boolean

> 폴리곤에 텍스처를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                          | Description                                            |
| ----------- | ----------------------------- | ------------------------------------------------------ |
| texture     | [JSIcon](../object/jsicon.md) | 텍스쳐로 활용할 아이콘 객체                                |
| faceIndex   | number                        | face 인덱스                                             |
| type        | boolean                       | <p>true: 지형 결합 가시화(RTT).<br>false: 기본 가시화.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   텍스처 객체가 없는 경우
        -   face 인덱스를 잘못 지정하는 경우

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetRenderToTexture(type) → boolean

> 지형 결합 가시화(RTT)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                          | Description                                            |
| ----------- | ----------------------------- | ------------------------------------------------------ |
| type        | boolean                       | <p>true: 지형 결합 가시화(RTT).<br>false: 기본 가시화.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setCullMode(type) → boolean

> 객체의 cull 모드를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                         | Description                                            |
| ----------- | ---------------------------- | ------------------------------------------------------ |
| type        | number                       | <p>1: none<br>2: cw<br>3: ccw</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPipe(center, radius, length, slice, color) → boolean

> 중심 좌표(경도, 위도, 고도)를 기준으로 원통 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                | Description                                       |
| ------ | ----------------------------------- | --------------------------------------------------|
| center | [JSVector3D](../core/jsvector3d.md) | 중심 좌표 (경도, 위도, 고도)                         |
| radius | number                              | 반지름 (in meter)                                  |
| length | number                              | 길이 (in meter)                                    |
| slice  | number                              | 단면의 다각수                                       |
| color  | [JSColor](../core/jscolor.md)       | 객체 색상  (기본값: 흰색 `rgba(255, 255, 255, 1)`) |

-   Description
    -   `radius`로 원통의 반지름을 설정합니다.
    -   `length`로 원통의 길이를 설정합니다.
    -   `slice`로 원통의 위/아래 면의 다각수를 설정합니다.
    -   `color`로 원통의 색상을 설정합니다.
    -   `radius`와 `length`가 너무 작거나, `slice`가 2 이하인 경우에는 원통이 생성되지 않습니다.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setExtraPosition(addLon, addLat, addHeight) → boolean

> 객체의 위치를 현재 위치에서 특정 좌표`(경도, 위도, 높이)`만큼 추가하여 이동합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description         |
| --------- | ------ | ------------------- |
| addLon    | number | 추가적으로 이동할 경도 |
| addLat    | number | 추가적으로 이동할 위도 |
| addHeight | number | 추가적으로 이동할 높이 |

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setExtraPosition(0.5, -1.5, 10.0);
```

{% endtab %}
{% endtabs %}

### move(lon, lat, alt) → boolean

> 객체의 위치를 특정 위치`(경도, 위도, 고도)`로 이동합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| lon  | number | 이동할 경도 좌표 |
| lat  | number | 이동할 위도 좌표 |
| alt  | number | 이동할 고도 값   |

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.move(129.127, 35.17, 160.0);
```

{% endtab %}
{% endtabs %}

### moveAltitude(alt, type) → boolean

> 객체의 높이를 조절합니다.
> 입력 변수(type)에 따라 상대 이동 / 절대 이동을 구분합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description  |
| ---- | ------- | ------------ |
| alt  | number  | 이동할 고도 값 |
| type | boolean | <p>true: 목표 위치로 이동(절대 이동)<br>false: 입력 위치만큼 추가로 이동(상대 이동)</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.moveAltitude(100.0, true); // 절대 이동
polygon.moveAltitude(70.0, false); // 상대 이동
```

{% endtab %}
{% endtabs %}

### setRotation(x, y, z) → boolean

> 객체를 회전시킵니다.
> x, y, z 각 축을 기준으로 일정 각도 만큼 회전합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description      |
| ---- | ------- | ---------------- |
| x    | number  | x축 기준 회전 각도 |
| y    | number  | y축 기준 회전 각도 |
| z    | number  | z축 기준 회전 각도 |

-   Sample
    -   [Sandbox_Edit Polygon](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_edit)

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setRotation(30.0, 45.0, 90.0); // x축 30도, y축 45도, z축 90도 회전
```

{% endtab %}
{% endtabs %}

### setScale(x, y, z) → boolean

> 객체의 크기를 조절합니다.
> x, y, z 각 축을 기준으로 일정 비율 만큼 확대/축소 합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description          |
| ---- | ------- | -------------------- |
| x    | number  | x축 기준 확대/축소 비율 |
| y    | number  | y축 기준 확대/축소 비율 |
| z    | number  | z축 기준 확대/축소 비율 |

-   Sample
    -   [Sandbox_Edit Polygon](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_edit)

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setScale(0.5, 1.5, 2.0); // x축 0.5배, y축 1.5배, z축 2배 확대/축소
```

{% endtab %}
{% endtabs %}

### getAxisEndpoint(axis, length) → [JSVector3D](../core/jsvector3d.md)

> 객체의 기준이 되는 축의 끝점 좌표를 반환합니다.
> 입력 변수(length)로 축의 길이를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type      | Description                     |
| ------ | ------- | ------------------------------- |
| axis   | number  | 반환할 축(0: x축, 1: y축, 2: z축) |
| length | number  | 축의 길이                        |

-   Sample
    -   [Sandbox_Edit Polygon](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_edit)

{% endtab %}
{% tab title="Template" %}

```javascript
let xvec = polygon.getAxisEndpoint(0, 200); // 객체 중심 기준 (200, 0, 0) 좌표 반환
```

{% endtab %}
{% endtabs %}

### getAltitude() → number

> 객체 중심의 고도(m)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 객체 중심의 고도(m). 객체가 NULL인 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
let alt = polygon.getAltitude();
```

{% endtab %}
{% endtabs %}


### setPartCoordinates(coordinates, parts) → boolean

> 평면 객체 생성에 필요한 정점 좌표 목록을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                            |
| ----------- | ------------------------------------- | -------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 정점 좌표 목록 (경도, 위도, 고도).     |
| parts       | [Collection](../core/collection.md)   | 평면을 구성하는 coordinates 개수 목록. |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   입력 변수값(coordinates) 구성요소가 없거나 정점 개수가 3개 이하인 경우.
        -   입력 변수값(parts) 구성요소가 없거나 입력 배열이 1개 이하인 경우.
-   Sample
    -   the createPolygon function 참조.
    -   [Sandbox_Polygon Height](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_height)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPlaneCoordinates(coordinates, altitude) → void

> 2차원 좌표로 평면 객체를 생성합니다.
> 입력 변수값(altitude)로 평면의 높이를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                            |
| ----------- | ------------------------------------- | -------------------------------------- |
| coordinates | [JSVec2Array](../core/jsvec2array.md) | 정점 좌표 목록 (경도, 위도).              |
| altitude    | number                                | 고도                                    |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPartCoordinatesUV(coordinates, parts, uv, type) → boolean

> 평면 객체를 생성합니다.
>
> 입력 변수값(uv)로 평면에 이미지 표현 좌표를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                                |
| ----------- | ------------------------------------- | ---------------------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 정점 좌표 목록 (경도, 위도, 고도).                         |
| parts       | [Collection](../core/collection.md)   | 평면을 구성하는 coordinates 개수 목록.                     |
| uv          | [JSVec2Array](../core/jsvec2array.md) | cordinates에 입력된 좌표 목록에 해당되는 uv 좌표 목록.     |
| type        | boolean                               | <p>true: 지형 결합 가시화(RTT).<br>false: 기본 가시화.</p> |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   입력 변수값(coordinates) 구성요소가 없거나 정점 개수가 3개 이하인 경우.
        -   입력 변수값(parts) 구성요소가 없거나 입력 배열이 1개 이하인 경우.
        -   입력 변수값(uv) 구성요소가 없거나 입력 배열이 3개 이하인 경우.
        -   coordinates, uv 개수가 동일하지 않는 경우.
-   Sample
    -   the init function 참조.
    -   [Sandbox_Polygon RTT](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_image_changing)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPartCoordinatesCW(coordinates, parts, cw) → boolean

> 평면 객체를 생성합니다.
>
> 입력 변수값(cw)로 폴리곤의 방향을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                                |
| ----------- | ------------------------------------- | ---------------------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 정점 좌표 목록 (경도, 위도, 고도).                             |
| parts       | [Collection](../core/collection.md)   | 평면을 구성하는 coordinates 개수 목록.                         |
| cw          | boolean                               | <p>true: 시계 방향(CW).<br>false: 반시계 방향(CCW).</p>       |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   입력 변수값(coordinates) 구성요소가 없거나 정점 개수가 3개 이하인 경우.
        -   입력 변수값(parts) 구성요소가 없거나 입력 배열이 1개 이하인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFaceTextureWrapU(faceIndex, wrapType), setFaceTextureWrapV(faceIndex, wrapType) → boolean

> 타일링 텍스쳐 매핑 방식을 설정합니다(u, v).
>
> uv(텍스쳐) 좌표 범위(0.0 ~ 1.0)를 벗어난 영역에 대한 패턴을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     	| Type   | Description           |
| --------- | ------ | --------------------- |
| faceIndex | number | face 인덱스            |
| wrapType  | number | <p>0x2901: GL_REPEAT(이미지 반복)<br>0x8370: GL_MIRRORED_REPEAT(이미지 뒤집어서 반복)<br>0x812F: GL_CLAMP_TO_EDGE(0과 1 사이의 좌표 고정. 가장자리 패턴이 늘어남)</p> |

-   Return
    -   true : 설정 성공.
    -   false : 해당 face 인덱스를 가진 face가 없을 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createVerticalGrid(layername, lefttop, rightbottom, row, col) → boolean

> 평면 그리드 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        	| Type                                  | Description                                                |
| ----------- 	| ------------------------------------- | ---------------------------------------------------------- |
| layername 	| string 								| 레이어 이름.							                     |
| lefttop       | [JSVector3D](../core/jsvector3d.md)   | 좌측 상단 좌표.                     						 |
| rightbottom   | [JSVector3D](../core/jsvector3d.md) 	| 우측 하단 좌표.     										 |
| row        	| number                                | 새로 개수. 												 |
| col        	| number                                | 가로 개수. 												 |

-   Return
    -   true : 생성 성공.
    -   false : 생성된 객체가 없을 경우.
-   Sample
    -   function createVerticalPlane 참조.
    -   [Sandbox_Vertical_grid](https://sandbox.egiscloud.com/code/main.do?id=object_vertical_grid)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setAnimationByID(id) → boolean

> GLTF 객체의 애니메이션을 ID 기준으로 설정합니다.  
> 평면 객체 타입이 GLTF 형식일 경우에만 동작합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description              |
| ---- | ------ | ------------------------ |
| id   | number | 애니메이션 ID (정수 값). |

-   Return  
    -   true: 설정 성공.  
    -   false: 설정 실패.  
        - 객체가 null이거나 GLTF 객체가 아닌 경우.  
        - 입력된 ID와 일치하는 애니메이션이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var gltfObject = Module.createPolygon("GLTF_OBJECT");
gltfObject.setAnimationByID(0);
```

{% endtab %}
{% endtabs %}

### setAnimationsByID(id) → boolean

> GLTF 객체의 다중 애니메이션을 ID 기준으로 설정합니다.
> 평면 객체 타입이 GLTF 형식일 경우에만 동작합니다.
> 입력값이 배열이 아니면 `setAnimationByID(id)`와 동일하게 단일 ID로 처리됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type            | Description                              |
| ---- | --------------- | ----------------------------------------- |
| id   | number \| number[] | 애니메이션 ID (단일 정수 값 또는 정수 배열). |

-   Return  
    -   true: 설정 성공. (배열로 입력한 경우, 모든 ID가 유효 애니메이션과 일치해야 true)
    -   false: 설정 실패.
        - 객체가 null이거나 GLTF 객체가 아닌 경우.
        - 입력된 ID 중 일치하는 애니메이션이 없는 것이 하나라도 있는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var gltfObject = Module.createPolygon("GLTF_OBJECT");
gltfObject.setAnimationsByID([0, 1]);
```

{% endtab %}
{% endtabs %}

### setAnimationSpeed(speed) → boolean

> GLTF 객체의 애니메이션 재생 속도를 설정합니다.
> 평면 객체 타입이 GLTF 형식일 경우에만 동작합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description              |
| ----- | ------ | ------------------------ |
| speed | number | 애니메이션 재생 속도(배율). |

-   Return  
    -   true: 설정 성공.  
    -   false: 설정 실패.  
        - 객체가 null이거나 GLTF 객체가 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var gltfObject = Module.createPolygon("GLTF_OBJECT");
gltfObject.setAnimationSpeed(1.5);
```

{% endtab %}
{% endtabs %}

### createWithFaces(parameter) → object

> Face 정보를 기반으로 평면 객체를 생성합니다.  
> 다각형을 Face 단위로 정의하고, 위치, 색상, 텍스처 좌표 등 세부 속성을 지정하여 생성할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                      |
| ---------- | ------ | -------------------------------- |
| parameter  | object | Face 기반 객체 정의 속성 정보.   |

- Return
  - object
    - result: 1 → 생성 성공 / 0 → 실패
    - name: `"JSPolygon.createWithFaces"`
    - return: 메시지

- 필수 속성
  - `position`: [longitude, latitude, altitude] 중심 좌표.
  - `faceInfo`: Face 배열. 각 Face는 다음과 같은 속성 포함:
    - `vertex`: [x, y, z, ...] 정점 배열.
    - `indexVertex`: [ [a, b, c], ... ] 정점 인덱스 배열.
    - `indexUV`: [ [a, b, c], ... ] 텍스처 좌표 인덱스 배열.
    - `uv`: [u, v, u, v, ...] 텍스처 좌표 배열.
    - `normal`: [x, y, z] 노멀 벡터.
    - `color`: 색상 (JSColor 형식).
    - `matrix`: 4x4 행렬 형식의 변환 매트릭스 (선택 사항).

- 선택 속성
  - `upVector`: `"y"` 또는 `"z"` (기본값: `"z"`).
  - `cullMode`: `"none"`, `"cw"`, `"ccw"` (기본값: `"ccw"`).
  - `moveOffset`: [x, y, z] 오프셋(meter 단위).
  - `vertexCombined`: boolean.

{% endtab %}
{% tab title="Template" %}

```javascript
const parameter = {
  position: [127.0, 37.5, 0],
  upVector: "z",
  cullMode: "ccw",
  faceInfo: [
    {
      vertex: [0, 0, 0, 1, 0, 0, 0, 1, 0],
      indexVertex: [[0, 1, 2]],
      indexUV: [[0, 1, 2]],
      uv: [0, 0, 1, 0, 0, 1],
      normal: [0, 0, 1],
      color: new Module.JSColor(255, 0, 0, 255),
      matrix: [
        1, 0, 0, 0,
        0, 1, 0, 0,
        0, 0, 1, 0,
        0, 0, 0, 1
      ]
    }
  ]
};

const result = Module.createPolygon("F_POLY").createWithFaces(parameter);
console.log(result);
```

{% endtab %}
{% endtabs %}

### setHeightUV(uv, height) → boolean

> 평면 객체의 높이를 설정하고, 정점에 해당하는 텍스처 좌표(UV)를 지정하여 텍스처를 입힐 수 있는 3D 객체를 생성합니다.  
> 이 API는 기존에 `setPartCoordinates()` 또는 `setCoordinates()`로 정의된 객체에만 적용 가능합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                  | Description                           |
| ------ | ------------------------------------- | ------------------------------------- |
| uv     | [JSVec2Array](../core/jsvec2array.md) | 정점 텍스처 좌표 목록 (UV 좌표계).    |
| height | number                                | 객체 높이 (단위: meter, > 0).         |

- Return
  - `true` : 생성 성공.
  - `false` : 객체가 없거나 정점 정보가 없을 경우 실패.

- 제약 조건
  - 객체에 `setPartCoordinates()` 또는 `setCoordinates()`로 정점 정보가 먼저 설정되어 있어야 합니다.
  - `uv.get(i)` 는 `i`번째 정점에 대응됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
const uvList = new Module.JSVec2Array();
uvList.push(new Module.JSVector2D(0, 0));
uvList.push(new Module.JSVector2D(1, 0));
uvList.push(new Module.JSVector2D(0, 1));

const polygon = Module.createPolygon("TEX_POLY");
polygon.setCoordinates(vertexList);
polygon.setHeightUV(uvList, 20);
```

{% endtab %}
{% endtabs %}

### setOverlayObject(options) → boolean

> 오버레이 객체를 지도에 생성합니다.  
> 주어진 정점 정보와 스타일 옵션에 따라 평면 또는 선형 오버레이를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| options | object   | 오버레이 객체 옵션. 아래 속성 참고. |

**options 구조**

| Name       | Type                                  | Required | Description                                  |
| ---------- | ------------------------------------- | -------- | -------------------------------------------- |
| coordinate | [JSVec3Array](../core/jsvec3array.md) | ✔        | 객체를 구성하는 좌표 목록 (경도, 위도, 고도). 최소 3개 이상 필요. |
| style      | string                                | ✔        | 스타일 설정. `"polygon"` 또는 `"line"` 중 하나. |
| color      | [JSColor](../core/jscolor.md)         |          | 객체 색상. (기본값: 흰색 `rgba(255, 255, 255, 1)`) |

- Return  
  - `true` : 오버레이 생성 성공.  
  - `false` : 생성 실패 (좌표 부족, 잘못된 타입, 내부 오류 등).

- 제한 사항
  - `style`이 `"polygon"` 또는 `"line"`이 아닌 경우 무시됩니다.
  - `coordinate`는 최소 3개 이상의 점이 필요합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
const coords = new Module.JSVec3Array();
coords.push(new Module.JSVector3D(127.0, 37.5, 0));
coords.push(new Module.JSVector3D(127.1, 37.5, 0));
coords.push(new Module.JSVector3D(127.1, 37.6, 0));

const poly = Module.createPolygon("OVERLAY_POLYGON");
poly.setOverlayObject({
    coordinate: coords,
    style: "polygon",
    color: new Module.JSColor(255, 255, 0, 0)
});
```

{% endtab %}
{% endtabs %}

### create(options) → boolean

> 옵션 객체를 기반으로 평면 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                        |
| ------- | ------ | ------------------------------------------------------------------- |
| options | object | 생성 옵션. `style` 속성으로 생성 방식을 구분합니다(아래 참고).        |

**options 구조 (공통)**

| Name  | Type   | Required | Description                                              |
| ----- | ------ | -------- | --------------------------------------------------------- |
| style | string | ✔        | `"edge"`, `"viewplane"`, `"triangulated"` 중 하나.        |

-   `style === "edge"`: `coordinate`([JSVec3Array](../core/jsvec3array.md), 3개 이상 필요) 로 외곽선 평면을 생성합니다.
-   `style === "viewplane"`: 내부적으로 `createViewPlane(options)`를 호출합니다(자세한 옵션은 구현부 미확인).
-   `style === "triangulated"`: `vertices`([JSVec3Array](../core/jsvec3array.md), 3개 이상), `indices`(삼각형 인덱스 배열, `[a,b,c,...]` 또는 `[[a,b,c],...]` 형태)로 삼각분할된 평면을 생성합니다.

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
        -   `style`이 없는 경우.
        -   `style === "edge"`: `coordinate`가 없거나 정점 수가 3개 미만인 경우.
        -   `style === "triangulated"`: `vertices`/`indices`가 없거나, 인덱스 개수가 3의 배수가 아니거나, 인덱스가 정점 범위를 벗어나는 경우.
        -   그 외 `style` 값인 경우(인식되지 않는 style은 무시되어 false 반환).

{% endtab %}
{% tab title="Template" %}

```javascript
var polygon = Module.createPolygon("EDGE_POLY");
polygon.create({
    style: "edge",
    coordinate: vertexList // JSVec3Array, 3개 이상
});
```

{% endtab %}
{% endtabs %}

### createByJson(parameter) → object

> JSON 형태의 파라미터로 평면 객체를 생성합니다. (바인딩된 이름은 `createByJson`이며, `createbyJson`으로도 동일하게 호출 가능합니다.)

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                    |
| --------- | ------ | ------------------------------- |
| parameter | object | 생성 파라미터(아래 구조 참고). |

**parameter 구조**

| Name                     | Type   | Required | Description                                                        |
| ------------------------ | ------ | -------- | -------------------------------------------------------------------- |
| coordinates.coordinate   | array  | ✔        | 정점 좌표 목록(경도, 위도, 고도).                                     |
| coordinates.parts        | array  | ✔        | 평면을 구성하는 coordinate 개수 목록.                                 |
| unionterrain             | boolean|          | 지형 결합(RTT) 여부. 기본값 false.                                    |
| height                   | number |          | 높이값. 0보다 크면 각기둥(prism) 형태로 생성. 기본값 0.               |
| image.uv                 | array  |          | 텍스처 좌표 목록. `image` 지정 시 좌표 수와 coordinate 수가 같아야 함. |
| style.lineWidth          | number |          | 외곽선 두께.                                                         |
| style.fill               | color  |          | 채움 색상. 기본값 흰색.                                               |
| style.stroke              | color  |          | 외곽선 색상. 기본값 검정.                                            |

-   Return (object)
    -   result: 1 → 생성 성공 / 0 → 실패
    -   name: `"JSPolygon.createbyJson"`
    -   return: 실패 사유 메시지 또는 `"success"`
-   실패 조건
    -   지도가 로드되지 않은 경우.
    -   `parameter`가 없는 경우.
    -   `coordinates.coordinate` 또는 `coordinates.parts` 파싱에 실패한 경우.
    -   `image`가 지정됐으나 `uv` 개수와 좌표 개수가 다르거나 `uv`가 비어있는 경우.
    -   폴리곤 생성(`CreatePlane`)에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var polygon = Module.createPolygon("JSON_POLY");
var result = polygon.createByJson({
    coordinates: {
        coordinate: [[127.0, 37.5, 0], [127.1, 37.5, 0], [127.1, 37.6, 0]],
        parts: [3]
    },
    style: { fill: { r: 255, g: 0, b: 0, a: 255 } }
});
console.log(result.result, result.return);
```

{% endtab %}
{% endtabs %}

### isInsidePosition(position) → boolean

> 입력한 평면 좌표(경도, 위도)가 평면 객체 내부에 포함되는지 여부를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description        |
| -------- | ------------------------------------ | ------------------- |
| position | [JSVector2D](../core/jsvector2d.md)  | 검사할 좌표(경도, 위도). |

-   Return
    -   true: position이 평면 내부에 포함됨.
    -   false: 포함되지 않거나, 판정에 필요한 정점/파트 정보가 3개 미만인 경우.
-   Description
    -   최초 호출 시 내부적으로 공간 연산용 2차원 폴리곤을 생성하여 캐시하고, 이후 호출부터는 캐시된 폴리곤으로 판정합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var isInside = polygon.isInsidePosition(new Module.JSVector2D(127.05, 37.55));
```

{% endtab %}
{% endtabs %}

### removeAllTexture() → void

> 평면 객체에 설정된 모든 face 텍스처를 제거합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   없음(void). 객체가 NULL인 경우 아무 동작도 하지 않습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.removeAllTexture();
```

{% endtab %}
{% endtabs %}

### setPartCoordinatesHeightUV(coordinates, parts, uv, height) → boolean

> 정점 좌표, 파트, UV 좌표, 높이값을 이용해 텍스처가 적용된 각기둥(prism) 형태의 평면 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                            |
| ----------- | -------------------------------------- | -------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md)  | 정점 좌표 목록 (경도, 위도, 고도).     |
| parts       | [Collection](../core/collection.md)    | 평면을 구성하는 coordinates 개수 목록. |
| uv          | [JSVec2Array](../core/jsvec2array.md)  | 정점에 대응하는 uv 좌표 목록.          |
| height      | number                                 | 각기둥 높이(m). 0 이하인 경우 1.0으로 대체되어 적용됩니다.  |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
        -   parts 구성요소가 없는 경우.
        -   coordinates 개수와 parts 합이 다른 경우.
        -   정점/파트 정보가 비어있는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDisplayGridSurface(visibleVertical, visibleHorizontal) → boolean

> 평면 객체 표면을 격자(그리드) 라인 형태로 렌더링할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name              | Type    | Description               |
| ----------------- | ------- | ------------------------- |
| visibleVertical   | boolean | 수직 방향 격자 라인 표시 여부. |
| visibleHorizontal | boolean | 수평 방향 격자 라인 표시 여부. |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 NULL인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setDisplayGridSurface(true, true);
```

{% endtab %}
{% endtabs %}

### setGridSurfaceStyle(lineColor, lineWidth, gridSize) → boolean

> 격자(그리드) 표면 라인의 색상, 두께, 격자 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                               | Description             |
| --------- | ----------------------------------- | ------------------------ |
| lineColor | [JSColor](../core/jscolor.md)      | 격자 라인 색상.          |
| lineWidth | number                              | 격자 라인 두께.          |
| gridSize  | [JSSize3D](../core/jssize3d.md)    | 격자 셀 크기(width, height, depth). |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 NULL인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDemShape(coordinates, positionAltitude, height, terrainLineNum, terrainLineInterval) → boolean

> 지정한 영역 내에 로드된 지형(DEM) 형태를 따라가는 평면 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name                | Type                                   | Description                    |
| ------------------- | --------------------------------------- | ------------------------------- |
| coordinates         | [JSVec2Array](../core/jsvec2array.md)  | 영역을 구성하는 좌표 목록(경도, 위도). 3개 이상 필요. |
| positionAltitude    | number                                  | 생성 기준 고도(m).               |
| height              | number                                  | 객체 높이(m).                    |
| terrainLineNum      | number                                  | 지형 라인 수.                    |
| terrainLineInterval | number                                  | 지형 라인 간격.                  |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패. (coordinates 개수가 3개 미만인 경우, 객체가 NULL인 경우)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRenderOffset(offset) → boolean

> 폴리곤 면의 렌더링 오프셋을 설정합니다. 동일 위치의 라인 객체와 z-fighting(깜빡임)이 발생할 때 값을 다소 높여 보정하는 용도로 사용합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description   |
| ------ | ------ | -------------- |
| offset | number | 렌더링 오프셋 값. |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 NULL인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setRenderOffset(0.5);
```

{% endtab %}
{% endtabs %}

### setTexturePlaneWithPixelData(coordinates, parts, uv, imageData, size, setRTT) → boolean

> 픽셀 데이터(바이트 배열)를 텍스처로 사용하여 평면 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                              |
| ----------- | -------------------------------------- | --------------------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 정점 좌표 목록 (경도, 위도, 고도). 3개 이상 필요.          |
| parts       | [Collection](../core/collection.md)   | 평면을 구성하는 coordinates 개수 목록. 1개 이상 필요.      |
| uv          | [JSVec2Array](../core/jsvec2array.md) | 정점에 대응하는 uv 좌표 목록. 3개 이상, coordinates와 개수 동일 필요. |
| imageData   | Uint8Array (또는 유사 배열)            | 픽셀 데이터(RGBA 바이트 배열).                            |
| size        | [JSSize2D](../core/jssize2d.md)       | 이미지 가로/세로 크기.                                    |
| setRTT      | boolean                                | true: 지형 결합(RTT) 가시화, false: 기본 가시화.          |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
        -   coordinates, parts, uv 중 하나라도 조건(정점 3개 미만/parts 없음/uv 3개 미만)을 만족하지 못하는 경우.
        -   coordinates 개수와 uv 개수가 다른 경우.
        -   imageData 길이가 0인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTexturePlaneWithBinaryTextures(vertices, uv, url, isRTT) → boolean

> 텍스처 이미지를 url로부터 비동기로 받아와 평면 객체에 적용합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                  | Description                                     |
| -------- | -------------------------------------- | ------------------------------------------------ |
| vertices | [JSVec3Array](../core/jsvec3array.md) | 정점 좌표 목록 (경도, 위도, 고도). 3개 이상 필요. |
| uv       | [JSVec2Array](../core/jsvec2array.md) | 정점에 대응하는 uv 좌표 목록. 3개 이상 필요.      |
| url      | string                                 | 텍스처(바이너리) url.                            |
| isRTT    | boolean                                | true: 지형 결합(RTT) 가시화, false: 기본 가시화. |

-   Return
    -   true: 생성 성공(비동기 텍스처 로드 요청까지 완료).
    -   false: 생성 실패. (vertices 또는 uv 개수가 3개 미만인 경우)
-   Description
    -   텍스처 로드가 완료되기 전까지 객체는 비가시화(`m_bVisible = false`) 상태이며, 로드가 끝나면 자동으로 표시됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTextureByName(textureName, faceIndex) → boolean

> 이미 등록되어 있는 텍스처 이름으로 특정 face에 텍스처를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type   | Description   |
| ----------- | ------ | -------------- |
| textureName | string | 등록된 텍스처 이름. |
| faceIndex   | number | face 인덱스.    |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
        -   등록된 텍스처 이름이 없는 경우.
        -   face 인덱스가 face 개수를 초과하거나 음수인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getNodeCount() → number

> GLTF 객체를 구성하는 하위 노드(파트) 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 노드 개수. 객체가 NULL이거나 GLTF 타입이 아닌 경우 0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = gltfObject.getNodeCount();
```

{% endtab %}
{% endtabs %}

### setNodeVisibleByIndexRange(indexMin, indexMax) → boolean

> GLTF 객체의 하위 노드 중 인덱스 범위(indexMin ~ indexMax)에 해당하는 노드만 가시화하고, 나머지는 비가시화합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description       |
| -------- | ------ | ------------------ |
| indexMin | number | 가시화할 최소 인덱스. |
| indexMax | number | 가시화할 최대 인덱스. |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 NULL이거나 GLTF 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
gltfObject.setNodeVisibleByIndexRange(0, 3);
```

{% endtab %}
{% endtabs %}

### setNodeVisibleByIndex(index, visible) → boolean

> GLTF 객체의 특정 인덱스 노드의 가시화 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description       |
| ------- | ------- | ------------------ |
| index   | number  | 노드 인덱스.        |
| visible | boolean | 가시화 여부.        |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
        -   객체가 NULL이거나 GLTF 타입이 아닌 경우.
        -   index가 음수이거나 노드 개수 이상인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
gltfObject.setNodeVisibleByIndex(2, false);
```

{% endtab %}
{% endtabs %}

### setNodeVisibleByKey(key, visible) → boolean

> GLTF 객체의 특정 키(노드 이름)를 가진 노드의 가시화 및 선택(pickable) 가능 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description        |
| ------- | ------- | ------------------- |
| key     | string  | 노드 고유 키(이름).  |
| visible | boolean | 가시화 및 선택 가능 여부. |

-   Return
    -   true: 설정 성공(일치하는 키가 없어도 true를 반환합니다).
    -   false: 객체가 NULL이거나 GLTF 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
gltfObject.setNodeVisibleByKey("Node_01", false);
```

{% endtab %}
{% endtabs %}

### getNodeKeyByIndex(index) → string

> GLTF 객체의 특정 인덱스에 해당하는 노드의 고유 키(이름)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description |
| ----- | ------ | ------------ |
| index | number | 노드 인덱스. |

-   Return
    -   string: 노드 고유 키.
    -   "" (빈 문자열): 객체가 NULL이거나 GLTF 타입이 아니거나, index가 유효 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var key = gltfObject.getNodeKeyByIndex(0);
```

{% endtab %}
{% endtabs %}

### setTextureByte(ptr, memSize, width, height, filter) → boolean

> 메모리 포인터로 전달된 픽셀 바이트 데이터를 텍스처로 직접 교체합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                     |
| ------ | ------- | --------------------------------- |
| ptr    | number  | 픽셀 데이터가 위치한 메모리 주소(포인터). |
| memSize| number  | 메모리 크기(byte).                |
| width  | number  | 이미지 가로 크기.                  |
| height | number  | 이미지 세로 크기.                  |
| filter | boolean | 텍스처 필터링 적용 여부.           |

-   Return
    -   true: 설정 성공.
    -   false: ptr이 NULL이거나, memSize/width/height 중 1 미만인 값이 있는 경우.
-   Description
    -   기존에 설정되어 있던 텍스처는 제거되고 새 텍스처로 교체됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTextureBASE64(base64Data, filter) → boolean

> base64로 인코딩된 이미지 데이터를 디코딩하여 텍스처로 교체합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type    | Description                  |
| ---------- | ------- | ------------------------------ |
| base64Data | string  | base64로 인코딩된 이미지 데이터. |
| filter     | boolean | 텍스처 필터링 적용 여부.        |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
        -   엔진이 초기화되지 않은 경우.
        -   디코딩된 이미지 데이터가 비어있는 경우.
        -   텍스처 바이트 로드에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setDome(position, radius, segment, color) → boolean

> 중심 좌표를 기준으로 3D 돔(반구) 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description               |
| -------- | ------------------------------------- | -------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)  | 중심 좌표(경도, 위도, 고도). |
| radius   | number                                | 반지름(m).                 |
| segment  | number                                | 단면의 다각수.              |
| color    | [JSColor](../core/jscolor.md)        | 돔 색상.                   |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패. (엔진이 초기화되지 않았거나 객체가 NULL인 경우)

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setDome(new Module.JSVector3D(127.0, 37.5, 0), 20, 24, new Module.JSColor(255, 255, 255, 255));
```

{% endtab %}
{% endtabs %}

### setCurvatureRect(parameter) → boolean

> 지구 곡률을 반영한 사각 평면(rect)을 생성합니다. 4개 모서리 좌표(corners) 또는 최소/최대 경위도(min/max) 두 가지 방식으로 입력할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                                   |
| --------- | ------ | ---------------------------------------------------------------- |
| parameter | object | `altitude`(number, 고도, 기본 0), `segment`(number, 기본 32)와 함께, `corners` 또는 `minLon`/`minLat`/`maxLon`/`maxLat` 중 하나를 지정합니다. |

**corners 방식**: `parameter.corners = { LT: [lon, lat], RT: [lon, lat], LB: [lon, lat], RB: [lon, lat] }`

**min/max 방식**: `parameter.minLon`, `parameter.minLat`, `parameter.maxLon`, `parameter.maxLat`(모두 number)

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
        -   엔진이 초기화되지 않았거나 객체가 NULL인 경우.
        -   `corners` 방식 사용 시, LT/RT/LB/RB 중 하나라도 없거나 좌표 요소가 2개 미만인 경우.
        -   `min/max` 방식 사용 시, minLon/minLat/maxLon/maxLat 중 하나라도 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setCurvatureRect({
    minLon: 127.0, minLat: 37.5,
    maxLon: 127.1, maxLat: 37.6,
    segment: 32
});
```

{% endtab %}
{% endtabs %}

### getSavedTextureCount() → number

> 평면 객체에 등록(저장)되어 있는 텍스처 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 등록된 텍스처 개수. 객체가 NULL인 경우 0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = polygon.getSavedTextureCount();
```

{% endtab %}
{% endtabs %}

### setFaceTextureByIndex(faceIndex, textureIndex) → boolean

> 등록된 텍스처 목록 중 인덱스(textureIndex)로 지정한 텍스처를 face(faceIndex)에 적용합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type   | Description                          |
| ------------ | ------ | -------------------------------------- |
| faceIndex    | number | 텍스처를 적용할 face 인덱스.           |
| textureIndex | number | 적용할 텍스처의 등록 순번(0부터 시작). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패. (객체가 NULL이거나, textureIndex에 해당하는 텍스처가 없거나, 텍스처 적용에 실패한 경우)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createTMCoordPlane(options) → boolean

> TM(평면 직각) 좌표계 격자를 기준으로 평면 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                 |
| ------- | ------ | ----------------------------------------------------------------------------- |
| options | object | `llcorner`(좌하단 좌표: `coordCode`, `x`, `y`), `grid`(`col`, `row`, `cellSize`, `ratioMode`, `xSplit`, `ySplit`), `gab`(간격, ratioMode 0일 때), `ureverse`/`vreverse`(uv 반전 여부) 등으로 구성됩니다. |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패. (`options`가 없거나, 필수 하위 속성이 누락된 경우)

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.createTMCoordPlane({
    llcorner: { coordCode: 5186, x: 200000, y: 500000 },
    grid: { col: 10, row: 10, cellSize: 100 },
    gab: 50
});
```

{% endtab %}
{% endtabs %}

### setRoadObject(options) → boolean

> 도로(Road) 타입 객체에 도로 형태(노면, 기둥, 가드레일, 포장, 텍스처 등)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                                                       |
| ---------- | ------ | ------------------------------------------------------------------- |
| options    | object | `coordinate`([JSVec3Array](../core/jsvec3array.md), 필수, 2개 이상), `road`(폭/중앙선/측선/차로 수/여유길이), `pillar`(기둥 타입/반지름/개수/간격/하단부 옵션), `guardrail`(가드레일 타입), `pavement`(포장 타입/폭), `texture`(각 부위별 텍스처 경로) 등으로 구성됩니다. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패. (객체가 NULL이거나 Road 타입이 아닌 경우, `coordinate`가 없거나 2개 미만인 경우, `road` 옵션이 없는 경우)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### changeRoadObject(options) → boolean

> 이미 생성된 도로(Road) 타입 객체의 옵션을 변경하고 재생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                         |
| ------- | ------ | ---------------------------------------------------------------------- |
| options | object | `setRoadObject()`와 동일한 구조(`road`, `pillar`, `guardrail`, `pavement`, `texture`). 지정된 항목만 변경됩니다. |

-   Return
    -   true: 변경 성공.
    -   false: 객체가 NULL이거나 Road 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getRoadWidth() → number

> 도로(Road) 객체의 노면 폭을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 노면 폭(m). 객체가 NULL이거나 Road 타입이 아니거나 도로 정보가 없는 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var width = roadObject.getRoadWidth();
```

{% endtab %}
{% endtabs %}

### getRoadExtraLength() → number

> 도로(Road) 객체의 노면 여유 길이(extraLength)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 여유 길이(m). 객체가 NULL이거나 Road 타입이 아니거나 도로 정보가 없는 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var length = roadObject.getRoadExtraLength();
```

{% endtab %}
{% endtabs %}

### getRoadPillarInterval() → number

> 도로(Road) 객체 기둥(pillar)의 배치 간격을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 기둥 간격(m). 객체가 NULL이거나 Road 타입이 아니거나 도로 정보가 없는 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var interval = roadObject.getRoadPillarInterval();
```

{% endtab %}
{% endtabs %}

### getRoadPillarRadius() → number

> 도로(Road) 객체 기둥(pillar)의 반지름을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 기둥 반지름(m). 객체가 NULL이거나 Road 타입이 아니거나 도로 정보가 없는 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var radius = roadObject.getRoadPillarRadius();
```

{% endtab %}
{% endtabs %}

### getRoadPillarBottomWidth() → number

> 도로(Road) 객체 기둥 하단부(bottom)의 폭을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 하단부 폭(m). 객체가 NULL이거나 Road 타입이 아니거나 도로 정보가 없는 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var width = roadObject.getRoadPillarBottomWidth();
```

{% endtab %}
{% endtabs %}

### getRoadPillarBottomDepth() → number

> 도로(Road) 객체 기둥 하단부(bottom)의 깊이를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 하단부 깊이(m). 객체가 NULL이거나 Road 타입이 아니거나 도로 정보가 없는 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var depth = roadObject.getRoadPillarBottomDepth();
```

{% endtab %}
{% endtabs %}

### getRoadPillarBottomHeight() → number

> 도로(Road) 객체 기둥 하단부(bottom)의 높이를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 하단부 높이(m). 객체가 NULL이거나 Road 타입이 아니거나 도로 정보가 없는 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var height = roadObject.getRoadPillarBottomHeight();
```

{% endtab %}
{% endtabs %}

### getRoadPavementWidth() → number

> 도로(Road) 객체 포장(pavement)의 폭을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 포장 폭(m). 객체가 NULL이거나 Road 타입이 아니거나 도로 정보가 없는 경우 0.0을 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var width = roadObject.getRoadPavementWidth();
```

{% endtab %}
{% endtabs %}

### getFormatData(format) → Uint8Array

> 도로(Road) 타입 객체의 지오메트리를 지정한 포맷의 바이너리 데이터로 변환하여 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                              |
| ------ | ------ | ------------------------------------------ |
| format | string | 변환할 포맷 문자열. (`"3DS"`, `"XDO"` 대소문자 무관) |

-   Return
    -   Uint8Array: 변환 성공("3DS" 포맷).
    -   null: 객체가 NULL이거나 Road 타입이 아닌 경우, 또는 지원되지 않는 포맷인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var bytes = roadObject.getFormatData("3DS");
```

{% endtab %}
{% endtabs %}

### create3DCubeData(options) → boolean

> 8개의 정점 좌표로 구성된 3D 육면체(큐브) 형태의 임시 인덱싱 모델을 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name              | Type   | Description                                                  |
| ----------------- | ------ | ---------------------------------------------------------------- |
| options.coordinates | array | 정점 좌표 목록. 정확히 8개(정육면체의 8개 꼭짓점)여야 합니다.       |
| options.fillColor  | [JSColor](../core/jscolor.md) | 채움 색상(선택, 기본값: 흰색). |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패. (`options`가 없거나, `coordinates`가 없거나, 좌표 개수가 8개가 아닌 경우)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGeoJSON2D(feature) → boolean

> GeoJSON Feature(Polygon 또는 MultiPolygon) 데이터를 기반으로 2D 평면 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                     |
| ------- | ------ | -------------------------------------------------- |
| feature | object | GeoJSON Feature 객체. `type`은 `"Feature"`, `geometry.type`은 `"Polygon"` 또는 `"MultiPolygon"`이어야 합니다. |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
        -   `feature`가 없거나, `type`이 `"Feature"`가 아닌 경우.
        -   `geometry`가 없거나, `geometry.type`이 `"Polygon"`/`"MultiPolygon"`이 아닌 경우.
        -   `geometry.coordinates`가 없는 경우.
-   Description
    -   `MultiPolygon`인 경우 첫 번째 폴리곤만 지원합니다.
    -   `geometry.triangles`(삼각형 인덱스 배열)가 있으면 인덱스 기반으로, 없으면 비-인덱스 방식으로 평면을 생성합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setGeoJSON2D({
    type: "Feature",
    geometry: {
        type: "Polygon",
        coordinates: [[[127.0, 37.5], [127.1, 37.5], [127.1, 37.6], [127.0, 37.5]]]
    }
});
```

{% endtab %}
{% endtabs %}

### createGridRasterPoly(url, useProxy, layerName, level, minX, minY, maxX, maxY, gridSize, type) → boolean

> 서버 기반 경사도/경사향 분석 결과를 그리드 래스터 형태의 평면 객체로 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description                              |
| --------- | ------- | ------------------------------------------ |
| url       | string  | 분석 서버 접속 URL.                        |
| useProxy  | boolean | 프록시 사용 여부.                          |
| layerName | string  | 분석할 레이어 명.                          |
| level     | number  | 분석 레벨.                                 |
| minX      | number  | 분석 영역 최소 경도.                       |
| minY      | number  | 분석 영역 최소 위도.                       |
| maxX      | number  | 분석 영역 최대 경도.                       |
| maxY      | number  | 분석 영역 최대 위도.                       |
| gridSize  | number  | 그리드 간격.                               |
| type      | number  | 분석 타입 (0: 경사도, 1: 경사향).          |

-   Return
    -   true: 요청 성공(비동기 요청이 정상적으로 시작됨).
-   Description
    -   호출과 동시에 내부적으로 객체의 좌표를 (minX,minY)~(maxX,maxY) 사각형으로 설정하고, 분석 서버로 비동기 요청을 보냅니다. 결과는 비동기 콜백을 통해 반영됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createGridRasterPolyEX(url, useProxy, layerName, level, minX, minY, maxX, maxY, gridSize, type, height) → boolean

> `createGridRasterPoly()`의 확장판으로, 기준 높이(height)를 지정하여 3D 평면 형태로 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description                              |
| --------- | ------- | ------------------------------------------ |
| url       | string  | 분석 서버 접속 URL.                        |
| useProxy  | boolean | 프록시 사용 여부.                          |
| layerName | string  | 분석할 레이어 명.                          |
| level     | number  | 분석 레벨.                                 |
| minX      | number  | 분석 영역 최소 경도.                       |
| minY      | number  | 분석 영역 최소 위도.                       |
| maxX      | number  | 분석 영역 최대 경도.                       |
| maxY      | number  | 분석 영역 최대 위도.                       |
| gridSize  | number  | 그리드 간격.                               |
| type      | number  | 분석 타입 (0: 경사도, 1: 경사향).          |
| height    | number  | 기준 높이값(m).                            |

-   Return
    -   true: 요청 성공(비동기 요청이 정상적으로 시작됨). 객체가 NULL인 경우 false.
-   Description
    -   지형 결합(RTT) 모드를 사용하지 않도록 설정한 뒤, 지정한 높이의 사각 좌표로 비동기 분석 요청을 보냅니다.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createVideo(info) → string

> 평면 객체에 비디오(RTT 영상)를 재생하는 LED 보드 형태로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name           | Type    | Description                        |
| -------------- | ------- | ------------------------------------ |
| info.url       | string  | 비디오 url.                          |
| info.streaming | boolean | 스트리밍(HLS 등) 여부.               |
| info.xaxis     | boolean | x축 반전 여부(선택, 기본 false).     |
| info.yaxis     | boolean | y축 반전 여부(선택, 기본 false).     |

-   Return
    -   "success": 설정 성공.
    -   "fail": 객체가 NULL인 경우.
    -   "url tag isn't exist.": `url`이 없는 경우.
    -   "streaming tag isn't exist.": `streaming`이 없는 경우.
-   Description
    -   설정된 비디오 재생/제어는 `element`, `canvas`, `context`, `hls`, `videoStreaming`, `isplayer` 프로퍼티([Getter/Setter](jspolygon.md#getter-setter) 참고)와 함께 사용됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var result = polygon.createVideo({ url: "video.mp4", streaming: false });
```

{% endtab %}
{% endtabs %}

### loadGLBWithOriginalVertex(option) → boolean

> GLB 파일을 원본 정점(버텍스) 정보를 유지한 상태로 비동기 로드합니다.

{% tabs %}
{% tab title="Information" %}

| Name              | Type    | Description                              |
| ----------------- | ------- | ------------------------------------------ |
| option.url        | string  | GLB 파일 url.                             |
| option.textureurl | string  | 텍스처 url(선택).                          |
| option.projection | string  | 투영 좌표계 코드.                          |
| option.callback   | function| 로드 완료 콜백(선택).                      |
| option.matrixType | number  | 변환 매트릭스 타입(선택).                  |

-   Return
    -   true: 요청 성공(비동기 로드 요청이 시작됨).
    -   false: 실패. (객체가 NULL이거나, `option`이 없거나, `url`/`projection`이 없는 경우)

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.loadGLBWithOriginalVertex({
    url: "model.glb",
    projection: "4326"
});
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getCoordinates(), setCoordinates(coordinates) → [Collection](../core/collection.md)

> 평면 객체를 구성하는 좌표 목록을 설정합니다.
>
> 입력 변수값(coordinates)은 최소 3개 이상의 배열로 구성합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ----------------------------------- | -------------------------------------------------- |
| coordinates | [Collection](../core/collection.md) | 정점 좌표 목록 (경도, 위도, 고도). |

-   Return
    -   [Collection](../core/collection.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var coorList = object.getCoordinates();
// ... or ...
var vertexList = Module.getMap().getInputPointList();
var object = Module.createPolygon("polygon");
object.setCoordinates(vertexList);
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

### getStyle(), setStyle(style) → [JSPolygonStyle](jspolygonstyle.md)

> [JSPolygonStyle](jspolygonstyle.md)으로 적용된 스타일을 평면 객체에 설정합니다.
>
> 평면 객체의 색상, 투명도, 외곽선 등을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                | Description |
| ----- | ----------------------------------- | ----------- |
| style | [JSPolygonStyle](jspolygonstyle.md) | 속성 정보.  |

-   Return
    -   [JSPolygonStyle](jspolygonstyle.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var objectStyle = polyLine.getStyle();
```

{% endtab %}
{% endtabs %}

### getUnionMode(), setUnionMode(bMode) → boolean

> 폴리곤 객체의 지형 결합(RTT Union) 모드를 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description |
|--------|--------|-------------|
| bMode  | boolean | `true`: 지형 결합(RTT) 모드 활성화, `false`: 비활성화 |

- Return
    -   getUnionMode() : boolean - 객체가 NULL이면 false, 아니면 현재 결합 모드 값(`m_bTUnion`)을 반환.
    -   setUnionMode(bMode) : 반환값 없음(void).

- Description
    -   내부적으로 `SetRenderToTexture()`와 동일하게 객체의 `m_bTUnion`(지형 결합/RTT union) 플래그를 설정합니다.
    -   설정 이후 RTT(렌더 타겟 텍스처) 갱신 플래그(`m_RTTRefresh`)가 활성화됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSPolygon : Module.getPolygon()
};

// 평면 병합 연산 모드 설정
API.JSPolygon.setUnionMode(true);

// 입체 병합 연산 모드 설정
API.JSPolygon.setUnionMode(false);
```
{% endtab %}
{% endtabs %}

### getUnderground(), setUnderground(value) → boolean

> 객체를 지하(underground) 상태로 표시할지 여부를 반환/설정합니다. (base 클래스 `JSObject`에서 상속되는 API이며, JSPolygon에도 동일하게 바인딩되어 있습니다.)

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                                          |
| ----- | ------- | ------------------------------------------------------ |
| value | boolean | true: 지하 상태(`ELEVATION_STATUS_BELOW`)로 설정, false: 지상 상태(`ELEVATION_STATUS_ABOVE`)로 설정. |

-   Return
    -   getUnderground() : boolean - 지하 상태이면 true, 아니면 false. 객체가 NULL인 경우 false.
    -   setUnderground(value) : 반환값 없음(void). 객체가 NULL인 경우 아무 동작도 하지 않습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.setUnderground(true);
var isUnderground = polygon.getUnderground();
```

{% endtab %}
{% endtabs %}

### zBufferOff (property) → boolean

> 객체의 Z-Buffer 비활성화 여부를 반환/설정하는 프로퍼티입니다. (`object.zBufferOff` 형태로 직접 접근)

{% tabs %}
{% tab title="Information" %}

| Name       | Type    | Description                          |
| ---------- | ------- | --------------------------------------- |
| zBufferOff | boolean | true: Z-Buffer 비활성화, false: 활성화(기본). |

-   Return
    -   boolean: 현재 설정값. 객체가 NULL인 경우 false.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.zBufferOff = true;
var isOff = polygon.zBufferOff;
```

{% endtab %}
{% endtabs %}

### regular (property) → boolean

> 좌표 입력값을 구면 좌표계로 변환하지 않고 그대로(평면 좌표로) 사용할지 여부를 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                                                 |
| ------- | ------- | ------------------------------------------------------------------------------- |
| regular | boolean | true: 입력 좌표를 정규화(평면 좌표)로 그대로 사용, false: 구면 좌표계로 변환하여 사용(기본). |

-   Return
    -   boolean: 현재 설정값. 객체가 NULL인 경우 false.
-   Description
    -   `true`로 설정하면 `setPartCoordinatesHeightUV()` 등에서 입력 좌표를 구면 좌표 변환 없이 `(-y, -x, z)` 형태로 그대로 사용합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.regular = true;
```

{% endtab %}
{% endtabs %}

### isplayer (property) → boolean

> 평면 객체를 비디오 렌더링(재생) 대상으로 사용할지 여부를 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type    | Description                  |
| -------- | ------- | ------------------------------ |
| isplayer | boolean | 비디오 렌더링 활성화 여부.     |

-   Return
    -   boolean: 현재 설정값.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.isplayer = true;
```

{% endtab %}
{% endtabs %}

### element (property) → object

> 비디오 재생에 사용할 HTML 엘리먼트(예: `<video>`)를 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                    |
| ------- | ------ | --------------------------------- |
| element | object | HTML 엘리먼트 참조(JS 객체).     |

-   Return
    -   object: 현재 설정된 엘리먼트 참조.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.element = document.getElementById("video1");
```

{% endtab %}
{% endtabs %}

### canvas (property) → object

> 비디오 프레임을 그리는 데 사용할 canvas 엘리먼트를 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                |
| ------ | ------ | ----------------------------- |
| canvas | object | canvas 엘리먼트 참조(JS 객체). |

-   Return
    -   object: 현재 설정된 canvas 참조.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.canvas = document.createElement("canvas");
```

{% endtab %}
{% endtabs %}

### context (property) → object

> canvas의 2D 렌더링 컨텍스트(context)를 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                    |
| ------- | ------ | --------------------------------- |
| context | object | canvas 2D context 참조(JS 객체). |

-   Return
    -   object: 현재 설정된 context 참조.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.context = polygon.canvas.getContext("2d");
```

{% endtab %}
{% endtabs %}

### hls (property) → object

> HLS(HTTP Live Streaming) 비디오 재생에 사용하는 hls.js 인스턴스 등을 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description             |
| ---- | ------ | -------------------------- |
| hls  | object | HLS 재생 인스턴스 참조(JS 객체). |

-   Return
    -   object: 현재 설정된 hls 참조.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.hls = new Hls();
```

{% endtab %}
{% endtabs %}

### videoStreaming (property) → boolean

> 비디오가 스트리밍(HLS 등) 방식으로 재생되는지 여부를 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name           | Type    | Description         |
| -------------- | ------- | ---------------------- |
| videoStreaming | boolean | 스트리밍 재생 여부.    |

-   Return
    -   boolean: 현재 설정값.

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.videoStreaming = true;
```

{% endtab %}
{% endtabs %}

### axisX (property) → boolean

> 비디오/텍스처를 x축 기준으로 반전하여 표시할지 여부를 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description       |
| ----- | ------- | -------------------- |
| axisX | boolean | x축 반전 여부.      |

-   Return
    -   boolean: 현재 설정값(내부적으로 1/0 정수 플래그를 boolean으로 변환하여 반환).

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.axisX = true;
```

{% endtab %}
{% endtabs %}

### axisY (property) → boolean

> 비디오/텍스처를 y축 기준으로 반전하여 표시할지 여부를 반환/설정하는 프로퍼티입니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description       |
| ----- | ------- | -------------------- |
| axisY | boolean | y축 반전 여부.      |

-   Return
    -   boolean: 현재 설정값(내부적으로 1/0 정수 플래그를 boolean으로 변환하여 반환).

{% endtab %}
{% tab title="Template" %}

```javascript
polygon.axisY = true;
```

{% endtab %}
{% endtabs %}

## Type Definitions

#### JSPolygon.loadFileOption

> 3ds 포맷 파일을 이용하여 평면 객체를 생성합니다.

| Name     | Type                                | Attributes | Default | Description                        |
| -------- | ----------------------------------- | ---------- | ------- | ---------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) |            |         | 생성 중심 좌표 (경도, 위도, 고도). |
| url      | string                              |            |         | 3ds 요청 url.                      |
| align    | string                              |            |         | 정렬 옵션.                         |
