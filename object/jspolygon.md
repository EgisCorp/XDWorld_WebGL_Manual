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

### loadTexture(name, url) → boolean

> 평면 객체에 사용할 이미지를 설정합니다.
>
> 입력 변수값(name)은 [setFaceTexture](jspolygon.md#setfacetextureindex-name--boolean) API로 텍스쳐를 적용할 때 텍스쳐를 구분하는 용도로 사용합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                |
| ---- | ------ | -------------------------- |
| name | string | Texture registration name. |
| url  | string | Texture image URL.         |

-   Return
    -   true: Object creation successful.
    -   false: Object creation failed.
    -   Failure conditions.
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

> Creates a circular planar object based on the center coordinates.
>
> Must set radius input value \> 0.
>
> Must set segment input value \> 3.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                                                   |
| -------- | ----------------------------------- | ------------------------------------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | Polygon location coordinates (longitude, latitude, altitude). |
| radius   | number                              | Radius.                                                       |
| segment  | number                              | Number of vertices.                                           |

-   Sample
    -   the createCirclePolygon function 참조.
    -   [Sandbox_Circle Polygon](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_circle)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFaceTexture(index, name) → boolean

> Sets the face texture that makes up the polygon object.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                       |
| ----- | ------ | ------------------------------------------------- |
| index | number | Polygon face index where the texture will be used |
| name  | string | Texture name specified with the loadTexture API   |

-   Return
    -   true: Object creation successful.
    -   false: Object creation failed
    -   Failure conditions.
        -   If the specified texture name does not exist
        -   If the polygon face with the specified index does not exist
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

> Sets a fire effect on the surface of the polygon.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                                         |
| ---- | ------- | ----------------------------------------------------------------------------------- |
| type | boolean | <p>true for fire effect visualization(RTT).<br>false for default visualization.</p> |

-   Return
    -   true: Object setting successful.
    -   false: Object setting failed.
    -   Failure conditions.
        -   If the polygon coordinates are not set.
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

> Creates a 3D polygon with height from a planar polygon.
>
> Must set height input value \> 0 (in meters).

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description     |
| ------ | ------ | --------------- |
| height | number | Polygon height. |

-   Return
    -   true: Object setting successful.
    -   false: Object setting failed.
    -   Failure conditions.
        -   If the polygon coordinates are not set.
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

> Create polygons based on input data (vertex, part).

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                        |
| ----------- | ------------------------------------- | -------------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | List of longitude, latitude, altitude coordinates. |
| parts       | [Collection](../core/collection.md)   | List of point counts composing the face.           |

-   Return
    -   true: Object creation successful.
    -   false: Object creation failed.
    -   Failure conditions
        -   If there are no components entered for coordinates or if the number of vertices is less than 3.
        -   If there are no components entered for parts or if there is less than 1 part.
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

> Create polygons based on input data (vertex, part, uv).

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                                                              |
| ----------- | ------------------------------------- | ---------------------------------------------------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | List of longitude, latitude, altitude coordinates.                                       |
| parts       | [Collection](../core/collection.md)   | List of point counts composing the face.                                                 |
| uv          | [JSVec2Array](../core/jsvec2array.md) | List of UV coordinates for the face.                                                     |
| type        | boolean                               | <p>true for terrain combined visualization(RTT).<br>false for default visualization.</p> |

-   Return
    -   true: Object creation successful.
    -   false: Object creation failed
    -   Failure conditions
        -   If there are no components entered for coordinates or if the number of vertices is less than 3.
        -   If there are no components entered for parts or if there is less than 1 part.
        -   If there are no components entered for uv or if there are less than 3 uv coordinates.
        -   If the number of coordinates and uv do not match.
-   Sample
    -   the init function 참조.
    -   [Sandbox_Polygon RTT](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_image_changing)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setStyle(style)

> Sets the style of the polygon.
>
> Sets the color transparency of the polygon, and the color and transparency of the polygon outline.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                  | Description  |
| ----- | ------------------------------------- | ------------ |
| style | [JSPolygonStyle](./jspolygonstyle.md) | Object style |

-   Sample
    -   the createBurnEffectPolygon function 참조.
    -   [Sandbox_Fire Effect](https://sandbox.egiscloud.com/code/main.do?id=effect_fire)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getCoordinates(), setCoordinates(coordinates) → [Collection](../core/collection.md)

> Sets the list of coordinates for the polygon object.
>
> Must set the number of components in coordinates \> 3.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                | Description                                        |
| ----------- | ----------------------------------- | -------------------------------------------------- |
| coordinates | [Collection](../core/collection.md) | List of longitude, latitude, altitude coordinates. |

-   Return
    -   [Collection](../core/collection.md): List of longitude, latitude, altitude coordinates.

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

> Set a description for the object.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                |
| ---- | ------ | -------------------------- |
| desc | string | Object description string. |

-   Return
    -   string: Successful return of the object's description string.
    -   null: If the object is null.

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

> Sets the name of the object.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                     |
| ---- | ------ | ------------------------------- |
| name | string | The name to set for the object. |

-   Return
    -   string: Successful return of the object's name.
    -   null: If the object is null.

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

> Sets the visibility state of an object.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                                      |
| ------- | ------- | ---------------------------------------------------------------- |
| visible | boolean | <p>true: Make the object visible.<br>false: Hide the object.</p> |

-   Return
    -   true: Object visible state.
    -   false: Object hidden state.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setVisible(true);
```

{% endtab %}
{% endtabs %}

### getStyle(), setStyle(style) → [JSPolygonStyle](./jspolygonstyle.md)

> Changes the object style with options applied in [JSPolygonStyle](./jspolygonstyle.md).
>
> Sets the color, thickness, and transparency.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                  | Description  |
| ----- | ------------------------------------- | ------------ |
| style | [JSPolygonStyle](./jspolygonstyle.md) | Object style |

-   Return
    -   A valid object style ([JSPolygonStyle](./jspolygonstyle.md)): If the object style is successfully returned.
    -   A simply initialized object style ([JSPolygonStyle](./jspolygonstyle.md)): If the object is null.

{% endtab %}
{% tab title="Template" %}

```javascript
var objectStyle = polyLine.getStyle();
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSPolygon.loadFileOption

> Options for creating a polygon object after loading a 3ds file.
>
> Modifications are required due to changes.

| Name     | Type                                | Attributes | Default | Description                                                   |
| -------- | ----------------------------------- | ---------- | ------- | ------------------------------------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) |            |         | Polygon location coordinates (longitude, latitude, altitude). |
| url      | string                              |            |         | URL address of the 3D modeling object to be visualized.       |
| align    | string                              |            |         | Alignment.                                                    |
