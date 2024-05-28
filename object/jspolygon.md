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
> 입력 변수값(id)은 [setFaceTexture](jspolygon.md#setfacetexture-index-name-boolean) API로 텍스쳐를 적용할 때 텍스쳐를 구분하는 용도로 사용합니다.

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
>
> 입력 변수값(radius)은 0보다 큰값, 입력 변수값(segment)은 3보다 큰값이 설정됩니다.

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

### setFaceTexture(index, id) → boolean

> 평면 객체를 구성하는 face에 이미지를 설정합니다.
>
> 입력 변수값(id)은 [loadTexture](jspolygon.md#loadTexture-id-url-boolean) API에 입력된 고유명칭 입니다.

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

### setHeight(height) → boolean

> 평면 객체 생성 시 높이값을 가진 3d 객체를 생성합니다.
>
> 입력 변수값(height)은 0보다 큰값이 설정됩니다.

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

### setPartCoordinates(coordinates, parts) → boolean

> 평면 객체 생성에 필요한 정점 좌표 목록을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                            |
| ----------- | ------------------------------------- | -------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 정점 좌표 목록 (경도, 위도, 경도).     |
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

### setPartCoordinatesUV(coordinates, parts, uv, type) → boolean

> 평면 객체를 생성합니다.
>
> 입력 변수값(uv)로 평면에 이미지 표현 좌표를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                                |
| ----------- | ------------------------------------- | ---------------------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 정점 좌표 목록 (경도, 위도, 경도).                         |
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

## Getter / Setter

### getCoordinates(), setCoordinates(coordinates) → [Collection](../core/collection.md)

> 평면 객체를 구성하는 좌표 목록을 설정합니다.
>
> 입력 변수값(coordinates)은 최소 3개 이상의 배열로 구성합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ----------------------------------- | -------------------------------------------------- |
| coordinates | [Collection](../core/collection.md) | 정점 좌표 목록 (경도, 위도, 경도). |

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
> 평면 객체의 색상, 투명도, 외각선 등을 설정합니다.

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

### Type Definitions

#### JSPolygon.loadFileOption

> 3ds 포맷 파일을 이용하여 평면 객체를 생성합니다.

| Name     | Type                                | Attributes | Default | Description                        |
| -------- | ----------------------------------- | ---------- | ------- | ---------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) |            |         | 생성 중심 좌표 (경도, 위도, 고도). |
| url      | string                              |            |         | 3ds 요청 url.                      |
| align    | string                              |            |         | 정렬 옵션.                         |
