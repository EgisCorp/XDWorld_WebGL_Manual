---
description: 지도 내 선 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSLineString

> Module.createLineString() API를 생성합니다.

```javascript
var object = Module.createLineString("ID");
```

## Function

### createbyJson(option) → string

> 선 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                                    | Description |
| ------ | ----------------------------------------------------------------------- | ----------- |
| option | [JSLineString.CreateOptions](#jslinestring.createoptions) | 속성 정보.  |

-   Return
    -   "success": 생성 성공.
    -   이 외 오류 원인을 포함한 에러 메시지
-   Sample
    -   function createLine 참조.
    -   [Sandbox_Line](https://sandbox.egiscloud.com/code/main.do?id=object_line_Json)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getBoundary() → [JSAABBox3D](../core/jsaabbox3d.md)

> 선 객체를 포함하는 박스 영역을 반환합니다.

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

> 선 객체를 중심 좌표(경도, 위도, 고도)를 반환합니다.

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

> 선 객체를 포함하는 박스 영역을 min, max간 거리를 반환합니다..

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 거리 반환.

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

### getLength(terrain) → number

> 선 객체의 총 길이를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                                                                                  |
| ------- | ------- | ------------------------------------------------------------------------------------------------------------ |
| terrain | boolean | <p>지형 곡면률 설정 유무.<br>true: 지형 곡면률 고려한 길이 계산.<br>false: 입력된 좌표에 대한 길이 계산.</p> |

-   Return
    -   number(0 이상): 반환 성공.
    -   number(-1.0): 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var length = object.getLength();
```

{% endtab %}
{% endtabs %}

### SetDashType(dash) → boolean

> 선 간격을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| dash | number | 점선 간격.  |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPartCoordinates(coordinates, parts)

> 선 객체를 생성합니다.
>
> 입력 변수값(coordinates)은 3개 이상 입력되어야 합니다.
>
> 입력 변수값(parts)은 1개 이상 입력되어야 합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                            |
| ----------- | ------------------------------------- | -------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 좌표 목록(경도, 위도, 고도).           |
| parts       | [Collection](../core/collection.md)   | 직선을 구성하는 coordinates 개수 목록. |

-   Sample
    -   function createBufferPolygon 참조.
    -   [Sandbox_Line Buffering](https://sandbox.egiscloud.com/code/main.do?id=object_line_buffering)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setUnionMode(type), getUnionMode() → boolean

> 선 객체 가시화 옵션을 설정 및 반환합니다.
>
> 선 생성 시 지형 결합 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                |
| ---- | ------- | ---------------------------------------------------------- |
| type | boolean | <p>true: 지형 결합 가시화(RTT).<br>false: 일반 가시화.</p> |

-   Sample
    -   function createObjectToPathPosition 참조.
    -   [Sandbox_Path Analysis](https://sandbox.egiscloud.com/code/main.do?id=analysis_line_path_distance)

{% endtab %}
{% tab title="Template" %}

```javascript
let line = Module.createLineString(id);
/* line 좌표 설정 */
line.setUnionMode(true);
```

{% endtab %}
{% endtabs %}

### setLineType(type)

> 선의 타입을 설정합니다.
>
> 실선, 점선 등과 같은 타입을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                |
| ---- | ------ | ---------------------------------------------------------- |
| type | number | <p>0(`Module.NORMAL`): NORMAL<br>1(`Module.OUTLINE`): OUTLINE<br>2(`Module.GLOW`): GLOW<br>3(`Module.ARROW`): ARROW<br>4(`Module.DASH`): DASH<br>5(`Module.FIRE`): FIRE<br>6(`Module.TWINKLE`): TWINKLE<br>7(`Module.WARNING`): WARNING</p> |

-   Sample
    -   타입 별 가시화 샘플
    -   [Sandbox_Line](https://sandbox.egiscloud.com/code/main.do?id=object_line_Json)
    -   [Sandbox_Line Effect](https://sandbox.egiscloud.com/code/main.do?id=object_line_effect)

{% endtab %}
{% tab title="Template" %}

```javascript
let line = Module.createLineString(id);
/* line 좌표 설정 */
line.setLineType(2); // GLOW
```

{% endtab %}
{% endtabs %}

### setDepthBufferTest(type)

> 선의 Depth 버퍼를 활성화/비활성화 합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description              |
| ---- | ------- | ------------------------ |
| type | boolean | <p>true: 활성화<br>false: 비활성화</p> |


{% endtab %}
{% tab title="Template" %}

```javascript
line.setDepthBufferTest(true); // 활성화
line.setDepthbufferTest(false); // 비활성화
```

{% endtab %}
{% endtabs %}

### setRenderToTexture(set) → boolean

> 선 객체의 타입을 지형 결합(3DLINE) 또는 하늘선(SKY_LINE) 타입으로 전환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                        |
| ---- | ------- | -------------------------------------------------------------------- |
| set  | boolean | true: 3DLINE(지형 결합) 타입으로 전환, false: SKY_LINE 타입으로 전환. |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
line.setRenderToTexture(true);
```

{% endtab %}
{% endtabs %}

### createGridArrowLine(option) → boolean

> 격자(Grid) 셀 데이터를 기반으로 화살표 형태의 라인 세트(예: 바람장 등 방향 시각화)를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name             | Type           | Description                                                          |
| ---------------- | -------------- | ------------------------------------------------------------------- |
| option            | object         | 격자 화살표 라인 생성 옵션.                                          |
| ↳ origin          | object         | 격자 시작 좌표 `{x, y}`(coordinate 옵션 좌표계 기준).                |
| ↳ coordinate      | string(optional) | 좌표계 문자열("5180" 포함 시 EPSG:5180, 그 외에는 EPSG:5174 처리). |
| ↳ min             | number         | 색상 매핑 최소값.                                                    |
| ↳ max             | number         | 색상 매핑 최대값.                                                    |
| ↳ cell            | array(object)  | 격자 셀 목록.                                                        |
| &nbsp;&nbsp;• cell\[].direction | object | 방향 벡터 `{x, y, z}`(크기가 화살표 색상 강도 계산에 사용됨).   |
| &nbsp;&nbsp;• cell\[].min       | object | 셀의 최소 좌표(origin 기준 상대 평면 좌표) `{x, y, z}`.          |
| &nbsp;&nbsp;• cell\[].max       | object | 셀의 최대 좌표(origin 기준 상대 평면 좌표) `{x, y, z}`.          |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   option에 cell 또는 origin이 없는 경우.
        -   origin.x, origin.y가 없는 경우.
        -   cell 배열이 비어있는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
line.createGridArrowLine({
    origin: { x: 198000, y: 450000 },
    coordinate: "5174",
    min: 0,
    max: 10,
    cell: [
        { direction: { x: 1, y: 0, z: 0 }, min: { x: 0, y: 0, z: 0 }, max: { x: 10, y: 10, z: 0 } }
    ]
});
```

{% endtab %}
{% endtabs %}

### getAxisMovePosition(pickPoint, mapPoint) → [JSVector3D](../core/jsvector3d.md)

> 축(Axis) 편집 기즈모(정점 2개, 파트 1개로 구성된 라인)에서, 축 위의 피킹 좌표(pickPoint)와 현재 마우스 위치에 대응하는 지도 좌표(mapPoint)를 이용해 축 방향으로 제한된 이동 위치를 계산합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                 | Description                        |
| --------- | ------------------------------------- | ----------------------------------- |
| pickPoint | [JSVector3D](../core/jsvector3d.md)  | 축 위에서 피킹한 좌표.              |
| mapPoint  | [JSVector3D](../core/jsvector3d.md)  | 현재 마우스 위치에 대응하는 지도 좌표. |

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 축 방향으로 제한된 이동 결과 좌표.
    -   (0, 0, 0): 객체가 정점 2개, 파트 1개로 구성된 축(Axis) 라인이 아닌 경우.
-   Note
    -   카메라 시점과 축 방향으로 구성되는 평면과 마우스 레이(ray)의 교차점을 축 방향으로 투영한 위치를 반환합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
let result = line.getAxisMovePosition(pickPoint, mapPoint);
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

### getCoordinates(), setCoordinates(coordinates) → [Collection](../core/collection.md)

> 선 객체를 구성하는 좌표 목록을 설정합니다.
>
> 입력 변수값(coordinates)은 3개 이상 입력되어야 합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                | Description                  |
| ----------- | ----------------------------------- | ---------------------------- |
| coordinates | [Collection](../core/collection.md) | 좌표 목록(경도, 위도, 고도). |

-   Return
    -   [Collection](../core/collection.md): 선을 구성하는 좌표 목록.
-   Sample
    -   function createPathLine 참조.
    -   [Sandbox_Path Analysis](https://sandbox.egiscloud.com/code/main.do?id=analysis_line_path_distance)

{% endtab %}
{% tab title="Template" %}

```javascript
var coorList = object.getCoordinates();
```

{% endtab %}
{% endtabs %}

### getStyle(), setStyle(style) → [JSPolyLineStyle](jspolylinestyle.md)

> 선 객체를 [JSPolyLineStyle](jspolylinestyle.md)으로 설정된 스타일로 설정합니다.
>
> 색상, 두께, 투명도 등을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                  | Description |
| ----- | ------------------------------------- | ----------- |
| style | [JSPolyLineStyle](jspolylinestyle.md) | 선 스타일.  |

-   Return
    -   [JSPolyLineStyle](jspolylinestyle.md): 설정 성공.
-   Sample
    -   function createBufferPolygon 참조.
    -   [Sandbox_Line Buffering](https://sandbox.egiscloud.com/code/main.do?id=object_line_buffering)

{% endtab %}
{% tab title="Template" %}

```javascript
var objectStyle = polyLine.getStyle();
```

{% endtab %}
{% endtabs %}

### isInstancedRender(), setInstancedRender(set) → boolean

> 선 객체의 인스턴싱(Instanced) 렌더링 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                  |
| ---- | ------- | ----------------------------------------------- |
| set  | boolean | true: 인스턴싱 렌더링 사용, false: 미사용.      |

-   Return
    -   true: 설정/조회 성공.
    -   false: 객체가 없거나, 라인 타입(S3dExline) 객체가 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
line.setInstancedRender(true);
var isInstanced = line.isInstancedRender();
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSLineString.CreateOptions

> 직선 객체 생성 옵션.

| Name        | Type                                                    | Attributes | Default                     | Description                                                |
| ----------- | ------------------------------------------------------- | ---------- | --------------------------- | ---------------------------------------------------------- |
| coordinates | [coordinates Type](../etc/tag-list.md#coordinates-type) |            |                             | 좌표 목록 옵션.                                            |
| type        | number                                                  | optional   | 0                           | 라인 가시화 타입.                                          |
| skip        | number                                                  | optional   | 1                           | 애니메이션 디테일 옵션.                                    |
| width       | number                                                  | optional   | 1                           | 라인 굵기 옵션.                                            |
| dash        | number                                                  | optional   | 0                           | 점선 간격 옵션.                                            |
| speed       | number                                                  | optional   | 0                           | 애니메이션 속도 옵션.                                      |
| union       | boolean                                                 | optional   | false                       | <p>true: 지형 결합 가시화(RTT).<br>false: 일반 가시화.</p> |
| depth       | boolean                                                 | optional   | true                        | <p>true: 일반 가시화.<br>false: 깊이감 미표현 가시화.</p>  |
| color       | [JSColor](../core/jscolor.md)                           | optional   | JSColor(200, 255, 255, 255) | 라인 가시화 색상.                                          |
