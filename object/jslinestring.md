---
description: 라인 객체 생성 및 수정 기능 API.
---

# JSLineString

> Module.createLineString API 생성.

```javascript
var object = Module.createLineString("ID");
```

### createbyJson(option) → string

> 라인 객체를 생성.
>
> argument 변수로 라인 객체 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| option | [JSLineString.CreateOptions](jslinestring.md#jslinestring.createoptions) | 초기화 옵션 속성 정보 |

-   Return
    -   "success" : 생성 성공.
    -   "error variable undefined null" : options 객체가 없음
    -   이 외 오류 원인을 포함한 에러 메시지
-   Sample
    -   function createLine 참조.
    -   [샌드박스\_라인](http://sandbox.dtwincloud.com/code/main.do?id=object_line_Json)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getBoundary() → number

> 오브젝트의 바운더리를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   유효한 값이 들어 있는 JSAABBox3D : 오브젝트 바운더리 반환 성공.
    -   단순 초기화 상태의 JSAABBox3D : 오브젝트가 null인 경우.

{% tab title="Template" %}

```javascript
var boundary = object.getBoundary();
var boundary_min = boundary.min;
var boundary_max = boundary.max;
```

{% endtab %}
{% endtabs %}

### getCenter() → JSVector3D

> 오브젝트의 중심점을 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   [JSVector3D](../core/jsvector3d.md) : 오브젝트의 중심 좌표 반환 성공.
        -   Longitude : 오브젝트 중심 경도(Degree 단위).
        -   Latitude : 오브젝트 중심 위도 (Degree 단위).
        -   Altitude : 오브젝트 중심 고도 (m 단위).
    -   단순 초기화 상태의 JSVector3D : 오브젝트가 null인 경우.

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

> 오브젝트 바운더리 Box의 Min-Max 간 거리를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -  number : 오브젝트 바운더리 Box의 Min-Max 간 거리 반환.
{% tab title="Template" %}

```javascript
var bExtends = object.getExtent();
```

{% endtab %}
{% endtabs %}

### getId() → string

> 오브젝트의 Key를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -  유효한 문자열(string) : 오브젝트 Key 문자열.
    -  빈 문자열(string) : 오브젝트가 null인 경우.
{% tab title="Template" %}

```javascript
var strKey = object.getId();
```

{% endtab %}
{% endtabs %}

### getLength(terrainUnion) → number

> 라인의 길이를 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| terrainUnion | boolean | 지형 결합 고려 여부.<br>true : 라인을 지형과 결합하여 지형 높이를 고려한 길이를 계산.</br><br>false : 라인을 지형과 결합하지 않고 입력한 좌표 리스트의 거리 계산을 통해 길이를 계산.</br> |

-   Return
    -  number(0 이상) : 라인 길이 반환에 성공한 경우.
    -  number(-1.0) : 오브젝트가 null인 경우.
{% tab title="Template" %}

```javascript
var length = object.getLength();
```

{% endtab %}
{% endtabs %}

### SetDashType(dash) → boolean

> 줄선 간격 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| dash | number | 점선 간격 |

-   Return
    -   true : 객체 옵션 설정 성공.
    -   false : 객체 옵션 설정 실패.
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPartCoordinates(coordinates, parts)

> 라인 객체를 생성.
>
> coordinates 구성 요소 개수&gt;3 필수 설정.
>
> parts 구성요소가 개수&gt;0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 라인 구성 경위도 좌표 목록. |
| parts | [Collection](../core/collection.md) | 라인 구성 점정 개수 목록 |

-   Sample
    -   function createBufferPolygon 참조.
    -   [샌드박스\_라인 버퍼링](http://sandbox.dtwincloud.com/code/main.do?id=object_line_buffering)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setUnionMode(type)

> 라인 가시화 옵션.
>
> 라인 지형 결합 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 기본 가시화.</p> |

-   Sample
    -   function createObjectToPathPosition 참조.
    -   [샌드박스\_경로 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getCoordinates() → JSCollection

> PolyLine을 구성하는 좌표 리스트를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   JSCollection : 좌표 리스트
{% tab title="Template" %}

```javascript
var coorList = object.getCoordinates();
```

{% endtab %}
{% endtabs %}

### setCoordinates(coordinates)

> 라인 오브젝트의 좌표 리스트 설정.
>
> coordinates 구성 요소 개수&gt;3 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [Collection](../core/collection.md) | 라인 구성 경위도 좌표 목록. |

-   Sample
    -   function createPathLine 참조.
    -   [샌드박스\_경로 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getDescription() → string

> 오브젝트의 설명에 대한 내용을 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -  유효한 문자열(string) : 오브젝트 설명 문자열 반환에 성공했을 경우.
    -  빈 문자열(string) : 오브젝트가 null일 경우.
{% tab title="Template" %}

```javascript
var strDesc = object.getDescription();
```

{% endtab %}
{% endtabs %}

### setDescription(desc)

> 오브젝트의 설명에 대한 설명을 저장.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| desc | string | 오브젝트 설명 문자열. |
{% endtab %}
{% tab title="Template" %}

```javascript
object.setDescription('First Object.');
```

{% endtab %}
{% endtabs %}

### getName() → string

> 오브젝트의 이름을 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -  유효한 문자열(string) : 오브젝트의 이름 반환에 성공한 경우.
    -  빈 문자열(string) : 오브젝트가 null인 경우.
{% tab title="Template" %}

```javascript
var objName = object.getName();
```

{% endtab %}
{% endtabs %}

### setName(name)

> 오브젝트의 이름을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 설정할 오브젝트 이름. |
{% endtab %}
{% tab title="Template" %}

```javascript
object.setName('MyObject');
```

{% endtab %}
{% endtabs %}

### getStyle() → CJSPolyLineStyle

> 설정된 오브젝트 스타일을 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -  유효한 오브젝트 스타일 객체(JSPolyLineStyle) : 오브젝트 스타일 객체 반환에 성공한 경우.
    -  단순 초기화 상태의 오브젝트 스타일 객체(JSPolyLineStyle) : 오브젝트가 null인 경우.
{% tab title="Template" %}

```javascript
var objectStyle = polyLine.getStyle();
```

{% endtab %}
{% endtabs %}

### setStyle(style)

> JSPolyLineStyle 적용된 옵션으로 라인 스타일 변경.
>
> 색상, 두께, 투명도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| style | JSPolyLineStyle | 라인 스타일 설정 객체 |

-   Sample
    -   function createBufferPolygon 참조.
    -   [샌드박스\_라인 버퍼링](http://sandbox.dtwincloud.com/code/main.do?id=object_line_buffering)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVisible() → number

> 오브젝트의 보기/숨김 여부를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -  number : 옵션 설정 상수
       -  Module.JS_VISIBLE_ON : 보기.
       -  Module.JS_VISIBLE_OFF : 숨김.
       -  Module.JS_VISIBLE_ERROR : 에러 발생(오브젝트가 null인 경우).
{% tab title="Template" %}

```javascript
var bVisible = object.getVisible();
```

{% endtab %}
{% endtabs %}

### setVisible(visible)

> JSPolyLineStyle 적용된 옵션으로 라인 스타일 변경.
>
> 색상, 두께, 투명도 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| visible | long | 옵션 설정 상수.<br>Module.JS_VISIBLE_ON인 경우 보기.</br><br>Module.JS_VISIBLE_OFF인 경우 숨김.</br> |
{% tab title="Template" %}

```javascript
object.setVisible(Module.JS_VISIBLE_ON);
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSLineString.CreateOptions

> 라인 객체 생성 옵션.

| Name        | Type                          | Attributes | Default                     | Description                                                           |
| ----------- | ----------------------------- | ---------- | --------------------------- | --------------------------------------------------------------------- |
| coordinates | tag-list                      |            |                             | 정점 관리 옵션.                                                       |
| type        | number                        | optional   | 0                           | 라인 가시화 타입.                                                     |
| skip        | number                        | optional   | 1                           | 애니메이션 디테일 옵션.                                               |
| width       | number                        | optional   | 1                           | 라인 굵기 옵션.                                                       |
| dash        | number                        | optional   | 0                           | 점선 간격 옵션.                                                       |
| speed       | number                        | optional   | 0                           | 애니메이션 속도 옵션.                                                 |
| union       | boolean                       | optional   | false                       | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 기본 가시화.</p>. |
| depth       | boolean                       | optional   | true                        | .                                                                     |
| color       | [JSColor](../core/jscolor.md) | optional   | JSColor(200, 255, 255, 255) | 라인 가시화 색상.                                                     |
