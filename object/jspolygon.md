---
description: 폴리곤 객체 생성 및 수정 기능 API.
---

# JSPolygon

> Module.createPolygon API 생성.

```javascript
var object = Module.createPolygon("ID");
```

### getArea() → number

> 오브젝트의 면적 값을 반환.
> 
> 반환되는 면적 값은 지형을 고려하지 않은 단순 평면 오브젝트로 계산한 값.
> 
> 따라서 지형 RTT로 렌더링되는 평면의 경우 보이는 면적과 다소 차이가 있을 수 있음.

{% tabs %}
{% tab title="Information" %}

* Return
  * number(> 0) : 오브젝트 면적 반환 성공.
  * number(0) : 오브젝트가 null인 경우.

{% endtab %}

{% tab title="Template" %}
```javascript
var area = object.getArea();
```
{% endtab %}
{% endtabs %}

### getBoundary() → JSAABBox3D

> 오브젝트의 바운더리를 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * 유효한 오브젝트 바운더리(JSAABBox3D) : 오브젝트 바운더리 반환 성공.
  * 단순 초기화 상태의 오브젝트 바운더리(JSAABBox3D) : 오브젝트가 null인 경우.

{% endtab %}

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

* Return
  * 유효한 좌표(JSVector3D) : 오브젝트의 중심점 반환 성공.
    * x : 오브젝트 중심 경도 (Degree 단위).
    * y : 오브젝트 중심 위도 (Degree 단위).
    * z : 오브젝트 중심 고도 (m 단위).
  * 단순 초기화 상태의 좌표(JSVector3D) : 오브젝트가 null인 경우

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
* Return
  * 유효한 문자열(string) : 오브젝트의 Key 반환 성공.
  * 빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var strKey = object.getId();
```
{% endtab %}
{% endtabs %}

### loadFile(option) → boolean

> 3ds 파일 로드 후 폴리곤 객체를 생성.
>
> argument 변수로 태풍 객체 설정.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                                                              | Description   |
| ------ | ----------------------------------------------------------------- | ------------- |
| option | [JSPolygon.loadFileOption](jspolygon.md#jspolygon.loadfileoption) | 초기화 옵션 속성 정보. |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
    * 객체 생성 실패 조건
      * positionmode=true 일 때 projectioncode가 설정되지 않음
      * positionmode=false 일 때 position이 지정되지 않음
	  
* Sample
  * function load3DS 참조.
  * [샌드박스\_3DS](http://sandbox.dtwincloud.com/code/main.do?id=object\_file\_3ds)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### loadTexture(name, url) → boolean

> 폴리곤에 사용할 텍스쳐 이미지 등록.
>
> name은 setFaceTexture API로 텍스쳐를 적용할 때 텍스쳐를 구분하는 용도로 사용.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| name | string | 텍스쳐 등록 명칭.   |
| url  | string | 텍스쳐 이미지 URL. |

* Return
  * 성공 : true
  * 실패 : false
    * 이미 동일한 texture\_name의 텍스쳐가 있음
    * texture\_name이나 texture\_url 이 빈 문자열
* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
    * 객체 생성 실패 조건
      * 동일한 name의 텍스쳐가 있을 경우.
      * name, url이 빈 문자열 경우.
* Sample
  * function init 참조.
  * [샌드박스\_폴리곤 RTT](http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_rtt\_image\_changing)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setCircle(position, radius, segment)

> 중심좌표 기준으로 원 모양 평면 객체를 생성.
>
> radius 입력값>0 필수 설정.
>
> segment 입력값>3 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description      |
| -------- | ----------------------------------- | ---------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 원 폴리곤 중심 경위도 좌표. |
| radius   | number                              | 반경.              |
| segment  | number                              | 버텍스 수.           |

* Return
  * 객체 생성 실패 조건
    * radius 값이 0
    * segment 값이 3 미만
	
* Sample
  * function createCirclePolygon 참조.
  * [샌드박스\_원 폴리곤](http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_circle)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFaceTexture(index, name) → boolean

> 중심 좌표와 반경, 버텍스 수로 원 모양의 평면 좌표를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                 |
| ----- | ------ | --------------------------- |
| index | number | 텍스쳐를 사용할 폴리곤 face index     |
| name  | string | loadTexture API로 지정한 텍스쳐 이름 |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패
    * 객체 생성 실패 조건
      * 지정한 텍스쳐 이름이 없음
      * 지정한 index의 폴리곤 face가 존재하지 않음
* Sample
  * function init 참조.
  * [샌드박스\_폴리곤 RTT](http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_rtt\_image\_changing)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFireEffect(type) → boolean

> 폴리곤 표면에 불 효과 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description                                        |
| ---- | ------- | -------------------------------------------------- |
| type | boolean | <p>true인 경우 불 효과 가시화(RTT)<br>false인 경우 기본 가시화.</p> |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 설정 실패 조건
      * 폴리곤 좌표 설정이 안된 경우.
* Sample
  * function createBurnEffectPolygon 참조.
  * [샌드박스\_불 효과](http://sandbox.dtwincloud.com/code/main.do?id=effect\_fire)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setHeight(height) → boolean

> 평면 폴리곤을 높이를 가진 3차원 폴리곤으로 생성.
>
> height 입력값>0 필수 설정(미터).

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description |
| ------ | ------ | ----------- |
| height | number | 폴리곤 높이      |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 설정 실패 조건
      * 폴리곤 좌표 설정이 안된 경우.
* Sample
  * function createPolygon 참조.
  * [샌드박스\_폴리곤 높이](http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_height)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPartCoordinates(coordinates, parts) → boolean

> 폴리곤 좌표(vertex, part)를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Name        | Type                                  | Description      |
| ----------- | ------------------------------------- | ---------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 폴리곤 경위도 좌표 목록.   |
| parts       | [Collection](../core/collection.md)   | 폴리곤 구성 점정 개수 목록. |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
    * 객체 생성 실패 조건.
      * 입력된 coordinates 구성요소가 없거나 정점 개수가 3개 이하인 경우.
      * 입력된 parts 구성요소가 없거나 1개 이하인 경우.
* Sample
  * function createPolygon 참조.
  * [샌드박스\_폴리곤 높이](http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_height)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPartCoordinatesUV(coordinates, parts, uv, type) → boolean

> 텍스쳐 uv를 포함한 폴리곤 좌표(vertex, part, uv)를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Name        | Type                                  | Description                                        |
| ----------- | ------------------------------------- | -------------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 폴리곤 경위도 좌표 목록.                                     |
| parts       | [Collection](../core/collection.md)   | 폴리곤 구성 점정 개수 목록.                                   |
| uv          | [JSVec2Array](../core/jsvec2array.md) | 폴리곤 구성 UV 좌표 목록.                                   |
| type       | boolean                               | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 기본 가시화.</p> |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패
    * 객체 생성 실패 조건
      * 입력된 coordinates 구성요소가 없거나 정점 개수가 3개 이하인 경우.
      * 입력된 parts 구성요소가 없거나 1개 이하인 경우.
      * 입력된 uv 구성요소가 없거나 3개 이하인 경우.
      * coordinates, uv 개수가 동일하지 않는 경우.
	  
* Sample
  * function init 참조.
  * [샌드박스\_폴리곤 RTT](http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_rtt\_image\_changing)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setStyle(style)

> 폴리곤 스타일 설정.
>
> 폴리곤의 색상 투명도, 폴리곤 외각선을 색상, 투명도 설정.

{% tabs %}
{% tab title="Information" %}
| Name  | Type           | Description  |
| ----- | -------------- | ------------ |
| style | JSPolygonStyle | 객체 스타일 설정 객체 |

* Sample
  * function createBurnEffectPolygon 참조.
  * [샌드박스\_불 효과](http://sandbox.dtwincloud.com/code/main.do?id=effect\_fire)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## Getter / Setter

### getCoordinates() → Collection

> PolyLine을 구성하는 좌표 리스트를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   Collection : 좌표 리스트
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
| coordinates | Collection | 라인 구성 경위도 좌표 목록. |
{% tab title="Template" %}

```javascript
var vertexList = Module.getMap().getInputPointList();
var object = Module.createPolygon("polygon");
object.setCoordinates(vertexList);
```

{% endtab %}
{% endtabs %}

### getDescription() → string

> 오브젝트의 설명에 대한 내용을 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 문자열(string) : 오브젝트 설명 문자열 반환 성공.
  * 빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}

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
| Name | Type   | Description  |
| ---- | ------ | ------------ |
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
* Return
  * 유효한 문자열(string) : 오브젝트의 이름 반환 성공.
  * 빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}

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
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| name | string | 설정할 오브젝트 이름. |
{% endtab %}

{% tab title="Template" %}
```javascript
object.setName('MyObject');
```
{% endtab %}
{% endtabs %}

### getStyle() → JSPolyLineStyle

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
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVisible() → number

> 오브젝트의 보기/숨김 여부를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * [옵션 설정 상수](../etc/type-list.md#navigation-visible-type-list) 반환.
  * 보기 : Module.JS\_VISIBLE\_ON
  * 숨김 : Module.JS\_VISIBLE\_OFF 에러 발생 : Module.JS\_SELECTABLE\_ERROR(오브젝트가 NULL인 경우)
{% endtab %}

{% tab title="Template" %}
```javascript
var objName = object.getName();
```
{% endtab %}
{% endtabs %}

### setVisible(visible)

> 오브젝트의 보기/숨김 여부를 설정.

{% tabs %}
{% tab title="Information" %}
| Name    | Type   | Description                                                                                                                                    |
| ------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| visible | number | <p><a href="../etc/type-list.md#navigation-visible-type-list">옵션 설정 상수</a>.<br>보기 : Module.JS_VISIBLE_ON<br>숨김 : Module.JS_VISIBLE_OFF<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
object.setVisible(Module.JS_VISIBLE_ON);
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSPolygon.loadFileOption

> 3ds 파일 로드 후 폴리곤 객체 생성 옵션.
>
> 변경 사항이 있어 수정 요망

| Name | Type | Attributes | Default | Description |
| ---- | ---- | ---------- | ------- | ----------- |
| position     | [JSVector3D](../core/jsvector3d.md)  |            |         | 객체 생성 경위도, 고도 위치. |
| url     | string     |            |         | 가시화 할 3D 모델링 객체 URL 주소. |
| align     | string     |            |         | 정렬.            |
