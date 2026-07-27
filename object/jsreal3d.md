---
description: 지도 내 시설물 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSReal3D

> Module.createReal3D() API를 생성합니다.
>
> JSReal3D는 시설물(건물) 형태를 출력하는 오브젝트 입니다.

```javascript
var object = Module.createReal3D("ID");
```

## properties

| Name            | Type   | Description                                                                                   |
| :-------------- | :----- | :---------------------------------------------------------------------------------------------- |
| idx             | number | 객체(메쉬)의 X 인덱스 값(읽기 전용). 값이 없으면 -1.                                              |
| idy             | number | 객체(메쉬)의 Y 인덱스 값(읽기 전용). 값이 없으면 -1.                                              |
| level           | number | 객체 데이터의 레벨 값(읽기 전용). 값이 없으면 -1.                                                 |
| modelFileName   | string | 객체가 사용하는 3D 모델 데이터 파일명(읽기 전용).                                                 |
| textureFileName | object | 객체의 각 면(face)이 사용하는 텍스쳐 파일명 목록(읽기 전용). 면 인덱스를 key로, 해당 면의 밉레벨별 텍스쳐 파일명 배열을 값으로 갖는 객체입니다. 면 정보가 없으면 null. |

```javascript
console.log(object.idx, object.idy, object.level);
console.log(object.modelFileName);
console.log(object.textureFileName); // { "0": ["tex_0.png"], "1": ["tex_1.png"], ... }
```

> 위 property들은 getter만 등록되어 있어(setter 없음) 값을 대입할 수 없습니다.

## Function

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

### setElevationSectionColor(elevation, color) → boolean

> 시설물 객체에 대한 층별 색상 리스트를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                | Description |
| --------- | ----------------------------------- | ----------- |
| elevation | [Collection](../core/collection.md) | 고도 목록.  |
| color     | [Collection](../core/collection.md) | 색상 목록.  |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var elevationList = new Module.Collection();
//.. add elevation values ..
var colorList = new Module.Collection();
//.. add color values ..
object.setElevationSectionColor(elevationList, colorList);
```

{% endtab %}
{% endtabs %}

### setFillColor(type, color) → boolean

> 시설물 객체의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description                                              |
| ----- | ----------------------------- | -------------------------------------------------------- |
| type  | boolean                       | <p>true: 심플렌더링 설정.<br>false: 일반 렌더링 설정.<p> |
| color | [JSColor](../core/jscolor.md) | 색상값.                                                  |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShaderType(type) → boolean

> 시설물 객체의 층별 색상 표시 방식을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                        |
| ---- | ------ | -------------------------------------------------- |
| type | number | <p>0: 이미지.<br>1: 이미지 + 색상.<br>2: 색상.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setShaderType(1);
```

{% endtab %}
{% endtabs %}

### setStyle(style) → boolean

> 시설물 객체의 스타일을 설정합니다.
>
> 시설물 객체는 색상 스타일만 설정 가능합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                  | Description       |
| ----- | ------------------------------------- | ----------------- |
| style | [JSPolygonStyle](./jspolygonstyle.md) | 스타일 속성 정보. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var polyStyle = new Module.JSPolygonStyle();
polyStyle.setFill(true);
polyStyle.setFillColor(new Module.JSColor(255, 255, 0, 0));
//...
object.setStyle(polyStyle);
```

{% endtab %}
{% endtabs %}

### getFillColor() → [JSColor](../core/jscolor.md)

> 시설물 객체의 색상을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSColor](../core/jscolor.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getPosition() → [JSVector3D](../core/jsvector3d.md)

> 시설물 객체의 중심 좌표(경도, 위도, 고도)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getHeight() → number

> 시설물 객체의 높이값(in meter)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number : 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### cutObjectHeight(height) → void

> 시설물 객체를 지정한 높이 기준으로 잘라서 표시합니다(층별 단면 시각화 등에 사용).
>
> height 보다 높은 부분은 렌더링에서 잘려 보이지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                                              |
| ------ | ------ | ------------------------------------------------------------------------- |
| height | number | 절단 기준 높이. 기본값은 99999.9로, 사실상 잘라내지 않는 상태와 같습니다. |

-   Return
    -   없음(void). 객체가 null인 경우 아무 동작도 하지 않습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
object.cutObjectHeight(10);
```

{% endtab %}
{% endtabs %}

### cutObjectHeightAlpha(alpha) → void

> [cutObjectHeight()](jsreal3d.md#cutobjectheightheight-void)로 잘려진 단면 부분의 투명도(alpha)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                    |
| ----- | ------ | ----------------------------------------------- |
| alpha | number | 단면 투명도 값(0.0 ~ 1.0). 기본값은 0.3 입니다. |

-   Return
    -   없음(void). 객체가 null인 경우 아무 동작도 하지 않습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
object.cutObjectHeightAlpha(0.3);
```

{% endtab %}
{% endtabs %}

### setFileMesh(layerName, filePath, fileName, position, scaleX, scaleY, scaleZ, rotation) → boolean

> 외부 3D 메쉬 파일을 읽어와 시설물 객체로 로드합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description               |
| -------- | ------------------------------------- | -------------------------- |
| layerName| string                                 | 객체가 등록될 레이어 이름.  |
| filePath | string                                 | 메쉬 파일 경로.             |
| fileName | string                                 | 메쉬 파일 이름.             |
| position | [JSVector3D](../core/jsvector3d.md)   | 배치 좌표(경도, 위도, 고도).|
| scaleX   | number                                 | X축 스케일.                 |
| scaleY   | number                                 | Y축 스케일.                 |
| scaleZ   | number                                 | Z축 스케일.                 |
| rotation | number                                 | 회전각.                     |

-   Return
    -   true: 로드 성공.
    -   false: 로드 실패.
    -   실패 조건
        -   지도가 로드되지 않은 경우.
        -   메쉬 파일 로드(내부 `LoadFileMesh`)에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setFileMesh(
	"MeshLayer",
	"https://example.com/models/",
	"building.xdo",
	new Module.JSVector3D(127.0, 37.5, 0),
	1, 1, 1,
	0
);
```

{% endtab %}
{% endtabs %}

### setScale(scaleX, scaleY, scaleZ) → boolean

> 시설물 객체의 스케일(X, Y, Z)을 설정합니다.
>
> 헤더 주석에는 "아직 사용 안함(Hoon(추가_190904))"이라고 표기되어 있으나, 실제로는 내부 스케일 값이 객체의 렌더링 변환 행렬 계산에 사용되고 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description |
| ------ | ------ | ----------- |
| scaleX | number | X축 스케일. |
| scaleY | number | Y축 스케일. |
| scaleZ | number | Z축 스케일. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   객체 또는 지도가 준비되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setScale(1.5, 1.5, 1.5);
```

{% endtab %}
{% endtabs %}

### createBuilding(list, color, height) → boolean

> 좌표 목록(바닥 다각형)을 기반으로 지정한 높이의 건물 형태 오브젝트를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                     | Description                       |
| ------ | ----------------------------------------- | ----------------------------------- |
| list   | [JSVec3Array](../core/jsvec3array.md)     | 바닥 다각형을 구성하는 좌표 목록(3개 이상 필요). |
| color  | [JSColor](../core/jscolor.md)             | 건물 색상.                            |
| height | number                                    | 건물 높이.                            |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   list의 좌표 개수가 3개 미만인 경우.
        -   객체 또는 지도가 준비되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var list = new Module.JSVec3Array();
list.push(new Module.JSVector3D(127.0, 37.5, 0));
list.push(new Module.JSVector3D(127.001, 37.5, 0));
list.push(new Module.JSVector3D(127.001, 37.501, 0));
object.createBuilding(list, new Module.JSColor(255, 200, 200, 200), 30);
```

{% endtab %}
{% endtabs %}

### dividFaceByTriangleCount(count) → boolean

> 객체를 구성하는 모든 삼각형(triangle)을 지정한 개수 단위로 묶어서 새로운 면(face)들로 재구성합니다.
>
> 원본 주석에 "아직 범용적으로 활용될지 모르므로 API 단에서만 동작하도록 구성함"이라고 명시되어 있어, 제한적/실험적 기능일 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                              |
| ----- | ------ | ------------------------------------------ |
| count | number | 한 face로 묶을 삼각형 개수(0을 초과해야 함, 1byte 범위). |

-   Return
    -   true: 재구성 성공.
    -   false: 재구성 실패.
    -   실패 조건
        -   객체 또는 지도가 준비되지 않은 경우.
        -   count가 0인 경우.
        -   객체 타입이 Real3D(시설물) 타입이 아닌 경우.
        -   객체에 face 정보가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.dividFaceByTriangleCount(50);
```

{% endtab %}
{% endtabs %}

### setData(ptr, len, version) → boolean

> Emscripten heap 메모리에 있는 바이너리 데이터(XDO 등)로부터 시설물 객체 데이터를 직접 구성합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                          |
| ------- | ------ | ---------------------------------------------------------------------- |
| ptr     | number | 데이터가 위치한 Emscripten heap 메모리 주소(포인터).                    |
| len     | number | 데이터 길이(byte).                                                      |
| version | number | 데이터 버전.                                                            |

-   Return
    -   true: 데이터 구성 성공.
    -   false: 데이터 구성 실패.
    -   실패 조건
        -   지도가 로드되지 않은 경우.
        -   len이 1보다 작거나 ptr이 0인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
// ptr, len은 Module._malloc 등으로 확보한 heap 메모리의 주소/길이입니다.
object.setData(ptr, len, 1);
```

{% endtab %}
{% endtabs %}

### setTextureData(faceId, ptr, len, width, height) → boolean

> Emscripten heap 메모리에 있는 이미지 바이트 데이터로 지정한 면(face)의 텍스쳐를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                                       |
| ------ | ------ | ---------------------------------------------------- |
| faceId | number | 텍스쳐를 적용할 면(face)의 인덱스.                    |
| ptr    | number | 이미지 데이터가 위치한 Emscripten heap 메모리 주소.   |
| len    | number | 이미지 데이터 길이(byte).                             |
| width  | number | 이미지 너비.                                          |
| height | number | 이미지 높이.                                          |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   지도가 로드되지 않은 경우.
        -   객체가 [setData()](jsreal3d.md#setdataptr-len-version-boolean)로 생성된 데이터 기반 객체가 아닌 경우.
        -   len이 1보다 작거나, ptr이 0이거나, width/height가 1보다 작은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setTextureData(0, ptr, len, 512, 512);
```

{% endtab %}
{% endtabs %}

### getFloorSliceEdge(height) → object

> 지정한 높이에서 시설물(건물)을 수평으로 자른 단면의 외곽선(edge) 좌표를 계산하여 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description       |
| ------ | ------ | ------------------ |
| height | number | 단면을 구하는 높이. |

-   Return
    -   (object)
        -   header
            -   minLon, minLat, maxLon, maxLat: 단면 외곽선의 경위도 범위.
            -   cutHeight: 입력한 height 값.
            -   location: 객체 중심 좌표( {lon, lat, alt} ).
            -   elevation: 객체의 최소/최대 고도( {min, max} ).
        -   edge: 단면 외곽선을 구성하는 선분(edge) 목록. 각 항목은 `[x1, y1, z1, x2, y2, z2]` 형태(경도, 위도, 고도 두 점)의 배열입니다.
    -   null: 반환 실패.
    -   실패 조건
        -   내부 모델 절단 처리(`S3DModelCut::setModel`)에 실패한 경우.
        -   단면 외곽선 추출(`exportEdge`)에 실패한 경우(예: 해당 높이에 단면이 존재하지 않는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
var result = object.getFloorSliceEdge(10);
if (result) {
	console.log(result.header.cutHeight, result.edge);
}
```

{% endtab %}
{% endtabs %}

### getOutterVector(alt, heading, extendDist) → object

> 객체 중심에서 지정한 고도/방위각(heading) 방향으로 진행했을 때, 시설물 외벽과 만나는 지점과 그 지점의 법선(normal), 그리고 법선 방향으로 일정 거리 연장한 지점을 계산하여 반환합니다.
>
> 3D POI 외곽선 출력 계산에 사용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                          |
| ---------- | ------ | -------------------------------------- |
| alt        | number | 기준 고도.                              |
| heading    | number | 진행 방향(방위각).                      |
| extendDist | number | 벽면 교차 지점에서 법선 방향으로 연장할 거리. |

-   Return
    -   (object)
        -   wallpos: 외벽과 만나는 지점의 좌표( {lon, lat, alt} ).
        -   normal: 교차 지점의 법선 벡터( {x, y, z} ).
        -   realpos: wallpos에서 법선 방향으로 extendDist 만큼 연장한 지점의 좌표( {lon, lat, alt} ).
    -   null: 반환 실패.
    -   실패 조건
        -   지도가 로드되지 않은 경우.
        -   객체가 null이거나, [setData()](jsreal3d.md#setdataptr-len-version-boolean)로 생성된 데이터 기반 객체가 아닌 경우.
        -   외벽과의 교차점을 찾지 못한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var result = object.getOutterVector(50, 90, 5);
if (result) {
	console.log(result.wallpos, result.normal, result.realpos);
}
```

{% endtab %}
{% endtabs %}

## Getter / Setter

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
