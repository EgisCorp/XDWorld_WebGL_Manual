---
description: 3D Figure 객체 생성 및 수정 기능 API.
---

# JSFigure

> Module.createFigure API 생성.
> 생성 후 JSFigure.createFigure API를 사용하여 초기화.
> 
> [샌드박스_JSFigure(전광판 생성)](https://sandbox.dtwincloud.com/code/main.do?id=object_ledboard)
> 
> [JSFigure 타입 상수](../etc/type-list.md#jsfigure-type-list)

| 변수명    | 자료형    | 프로퍼티 역할 |
| ------ | ------ | ------- |
| position  | number | 너비.      |
| size | number | 높이.      |
| color  | number | 깊이.      |
| type   | number | 오브젝트 타입. |

```javascript
let figure = Module.createFigure("fig");
let position = new Module.JSVector3D(127.063451, 37.509597, 38.821713);
let size = new Module.JSVector3D(30, 15, 1);
let color = new Module.JSColor(255, 255, 255, 255);

figure.createFigure(position, size, color, 4); // 사각형
```

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
var boundary = figure.getBoundary();
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
var vCenter = figure.getCenter();
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
var bExtends = figure.getExtent();
```

{% endtab %}
{% endtabs %}

### getFigureType() → number

> 오브젝트의 Figure 타입을 반환.
> 
> [JSFigure 타입 상수](../etc/type-list.md#jsfigure-type-list)

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 상수(number) : Figure 타입 반환 성공.
  * -1(number) : 오브젝트가 null인 경우.

{% endtab %}

{% tab title="Template" %}
```javascript
var figureType = figure.getFigureType();
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
lat strKey = figure.getId();
```
{% endtab %}
{% endtabs %}

### setDepth(depth)

> 오브젝트의 깊이(Z축 방향 크기)를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| depth | number | 오브젝트 깊이. |

- Return
  - true : 오브젝트 깊이 설정 성공.
  - false : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
figure.setDepth(200.0);
```
{% endtab %}
{% endtabs %}

### setHeight(height)

> 오브젝트의 높이(Y축 방향 크기)를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| height | number | 오브젝트 높이. |

- Return
  - true : 오브젝트 높이 설정 성공.
  - false : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
figure.setHeight(100.0);
```
{% endtab %}
{% endtabs %}

### setWidth(width)

> 오브젝트의 너비(X축 방향 크기)를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| width | number | 오브젝트 너비. |

- Return
  - true : 오브젝트 너비 설정 성공.
  - false : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
figure.setWidth(130.0);
```
{% endtab %}
{% endtabs %}

## Getter / Setter

### getAngle() → number

> 오브젝트의 y축 중심 회전 각도를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 각도(number) : 회전 각도 반환 성공.
  * -999.0(number) : 오브젝트가 null인 경우.

{% endtab %}

{% tab title="Template" %}
```javascript
var dAngle = figure.getAngle();
```
{% endtab %}
{% endtabs %}

### setAngle(angle)

> 오브젝트의 y축 중심 회전 각도를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| angle | number | y축 중심 회전 각도 (Degree 단위). |

- Return
  - true : 회전 각도 설정 성공.
  - false : 오브젝트가 null이거나, 입력한 각도가 0º ~ 360º를 벗어나는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
figure.setAngle(50.0);
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
lat strDesc = figure.getDescription();
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
figure.setDescription('First Figure.');
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
lat figureName = figure.getName();
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
figure.setName('MyFigure');
```
{% endtab %}
{% endtabs %}

### getPosition() → JSVector3D

> 오브젝트의 바닥면 중심 위치를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 오브젝트(JSVector3D) : 오브젝트의 바닥면 중심 위치.
    * x : 중심 경도 (Degree 단위).
    * y : 중심 위도 (Degree 단위).
    * z : 중심 고도 (m 단위).
  * 단순 초기화 상태의 오브젝트(JSVector3D) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
let position = figure.getPosition();
let longitude = position.x;
let latitude = position.y;
let altitude = position.z;
```
{% endtab %}
{% endtabs %}

### setPosition(position) → boolean

> 오브젝트 바닥면 중심 위치 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 오브젝트 바닥면 중심 위치(경위도). |

* Return
  * true : 오브젝트 위치 설정 성공.
  * false : 오브젝트 위치 설정 실패.  
{% endtab %}

{% tab title="Template" %}
```javascript
var vPos = new Module.JSVector3D('127.0273188', '37.4977981', '30.0');
figure.setPosition(vPos);
```
{% endtab %}
{% endtabs %}

### getSize() → JSVector3D

> 오브젝트의 크기 값을 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 오브젝트(JSVector3D) : 오브젝트의 크기.
    * x : 오브젝트 너비(x축 방향 크기).
    * y : 오브젝트 높이(y축 방향 크기).
    * z : 오브젝트 깊이(z축 방향 크기).
  * 단순 초기화 상태의 오브젝트(JSVector3D) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
let size = figure.getSize();
let width = size.x;
let height = size.y;
let depth = size.z;
```
{% endtab %}
{% endtabs %}

### setSize(width, height, depth) → boolean

> 오브젝트 크기를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| width | number | 오브젝트 너비(x축 방향 크기). |
| height | number | 오브젝트 높이(y축 방향 크기). |
| depth | number | 오브젝트 깊이(z축 방향 크기). |

* Return
  * true : 오브젝트 위치 설정 성공.
  * false : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
figure.setSize(50.0, 100.0, 150.0);
```
{% endtab %}
{% endtabs %}

### getStyle() → JSPolygonStyle

> 설정된 오브젝트 스타일을 반환.
> 
> 현재 설정 가능한 스타일(추후 업데이트 될 수 있음_JSPolygonStyle 참조)
> - Fill Color : 오브젝트 채움 색상.
> - OutLine Color : 오브젝트 외곽 라인 색상.

{% tabs %}
{% tab title="Information" %}
-   Return
    -  유효한 오브젝트 스타일 객체(JSPolygonStyle) : 오브젝트 스타일 객체 반환에 성공한 경우.
    -  단순 초기화 상태의 오브젝트 스타일 객체(JSPolygonStyle) : 오브젝트가 null인 경우.
{% tab title="Template" %}

```javascript
var figure = new Module.JSFigure();
var figureStyle = figure.getStyle();
```

{% endtab %}
{% endtabs %}

### setStyle(style)

> JSPolygonStyle 적용된 옵션으로 오브젝트 스타일 변경.
>
> 현재 설정 가능한 스타일(추후 업데이트 될 수 있음_JSPolygonStyle 참조)
> - Fill Color : 오브젝트 채움 색상.
> - OutLine Color : 오브젝트 외곽 라인 색상.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| style | JSPolygonStyle | 오브젝트 스타일 객체 |
{% tab title="Template" %}

```javascript
var figure = new Module.JSFigure();
var figureStyle = new Module.JSFigureStyle();
//...
figure.setStyle(figureStyle);
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
lat objName = object.getName();
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
