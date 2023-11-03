---
description: 포인트 객체 생성 및 수정 기능 API.
---

# JSPoint

> Module.createPoint API 생성.

```javascript
var object = Module.createPoint("ID");
```

### getFontColor() → [JSColor](../core/jscolor.md)

> 오브젝트의 텍스트 색상을 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * 유효한 색상([JSColor](../core/jscolor.md)) : 텍스트 색상 반환 성공.
  * 초기화 상태의 색상([JSColor](../core/jscolor.md)) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var fontColor = object.getFontColor();
```
{% endtab %}
{% endtabs %}

### getFontName() → wstring

> 오브젝트의 텍스트 글꼴 명칭을 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * 유효한 문자열(wstring) : 텍스트 글꼴 명칭 반환 성공.
  * 초기화 상태의 색상(wstring) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var fontName = object.getFontName();
```
{% endtab %}
{% endtabs %}

### getFontOutColor() → [JSColor](../core/jscolor.md)

> 오브젝트의 텍스트 외곽 색상을 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * 유효한 색상([JSColor](../core/jscolor.md)) : 텍스트 외곽 색상 반환 성공.
  * 초기화 상태의 색상([JSColor](../core/jscolor.md)) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var fontOutLineColor = object.getFontOutColor();
```
{% endtab %}
{% endtabs %}

### getFontSize() → number

> 오브젝트의 텍스트 크기를 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * number(0 이상) : 오브젝트의 텍스트 크기 반환 성공.
  * number(-1) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var fontSize = object.getFontSize();
```
{% endtab %}
{% endtabs %}

### getFontWeight() → number

> 오브젝트의 텍스트 Weight를 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * number(0 이상) : 오브젝트의 텍스트 Weight 반환 성공.
  * number(-1) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var fotnWeight = object.getFontWeight();
```
{% endtab %}
{% endtabs %}

### getId() → string

> 오브젝트의 Key를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   유효한 문자열(string) : 오브젝트의 Key 반환 성공.
    -   빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}
{% tab title="Template" %}

```javascript
var strKey = object.getId();
```

{% endtab %}
{% endtabs %}

### getPosition() → JSVector3D

> 오브젝트의 위치를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * JSVector3D : 오브젝트의 위치 좌표.
    * x : 오브젝트 경도 (Degree 단위).
    * y : 오브젝트 위도 (Degree 단위).
    * z : 오브젝트 고도 (m 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var vPos = point.getPosition();
```
{% endtab %}
{% endtabs %}

### getVisibleRangeActivate() → boolean

> POI 오브젝트의 가시 범위 값 활성화 여부를 반환.
> 
> 가시 범위 값이 비활성화 된 경우 POI 오브젝트의 가시범위는 소속된 레이어의 가시범위 값을 따름.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   POI 오브젝트가 외부 서버로부터 데이터를 불러와 생성 된 오브젝트인 경우 가시범위를 설정할 수 없음.
    -   true : 가시범위 값 설정 성공.
    -   false
        -   POI 오브젝트가 외부 서버로부터 데이터를 불러와 생성 된 오브젝트인 경우.
        -   POI 오브젝트가 null 인 경우.
{% endtab %}
{% tab title="Template" %}

```javascript
var bActive = object.getVisibleRangeActivate();
```

{% endtab %}
{% endtabs %}

### getVisibleRangeMax() → number

> POI 오브젝트의 최대 가시범위 값을 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   유효한 number : 최대 가시범위 값 반환 성공.
    -   다음의 경우 API는 항상 고정 값을 반환.
        - -999.0 : POI 오브젝트가 null인 경우.
        - -998.0 : POI 오브젝트가 외부 서버로부터 데이터를 불러와 생성 된 오브젝트인 경우.
        - -997.0 : 가시범위 설정이 비활성화 상태인 경우.
{% endtab %}
{% tab title="Template" %}

```javascript
var rangeMax = object.getVisibleRangeMax();
```

{% endtab %}
{% endtabs %}

### getVisibleRangeMin() → number

> POI 오브젝트의 최소 가시범위 값을 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   유효한 number : 최소 가시범위 값 반환 성공.
    -   다음의 경우 API는 항상 고정 값을 반환.
        - -999.0 : POI 오브젝트가 null인 경우.
        - -998.0 : POI 오브젝트가 외부 서버로부터 데이터를 불러와 생성 된 오브젝트인 경우.
        - -997.0 : 가시범위 설정이 비활성화 상태인 경우.
{% endtab %}
{% tab title="Template" %}

```javascript
var rangeMin = object.getVisibleRangeMin();
```

{% endtab %}
{% endtabs %}

### isExistHighlightIcon() → boolean

> 하이라이트 타입의 아이콘 지정 여부를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   true : 아이콘이 지정되어 있음.
    -   false : 아이콘이 지정되어 있지 않음.
{% endtab %}
{% tab title="Template" %}

```javascript
var bExistHighlightIcon = object.isExistHighlightIcon();
```

{% endtab %}
{% endtabs %}

### isExistIcon() → boolean

> 기본 타입의 아이콘 지정 여부를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   true : 아이콘이 지정되어 있음.
    -   false : 아이콘이 지정되어 있지 않음.
{% endtab %}
{% tab title="Template" %}

```javascript
var bExistNormalIcon = object.isExistIcon();
```

{% endtab %}
{% endtabs %}

### setFontStyle(name, size, weight, fill_color, outline_color) → boolean

> POI 텍스트 스타일 설정.
> 
> 폰트, 크기, 굵기, 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 폰트 이름 |
| size | number | 텍스트 크기 |
| weight | number | 텍스트 굵기 |
| fill_color | JSPolyLineStyle | 텍스트 색상 |
| outline_color | JSPolyLineStyle | 텍스트 외곽 색상 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPoint 참조.
  * [샌드박스\_경로 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setImage(data, width, height) → boolean

> POI 이미지를 설정.
> 
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터.
>
> width, height 이미지 실제 크기 입력( &gt;1 ).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| data | array | 이미지 픽셀 값 배열. |
| width | number | 이미지 너비. |
| height | number | 이미지 높이. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 생성 실패 조건
	  * data 값이 null 인 경우.
	  * width, height &lt;0 인 경우
	  
* Sample
  * function createPOI 참조.
  * [샌드박스\_POI](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setLonLat(lon, lat) → boolean

> 오브젝트의 위치(경도, 위도)를 설정 (오브젝트 고도값은 그대로 유지).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| lon | double | 경도(Degree 단위). |
| lat | double | 위도(Degree 단위). |

* Return
  * true : 위치 설정 성공.
  * false : 위치 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
point.setLonLat(129.1270931, 35.1713096);
```
{% endtab %}
{% endtabs %}

### setPosition(position) → boolean

> POI 위치 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | POI 경위도 위치. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPOI 참조.
  * [샌드박스\_POI](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPositionLine(length, color) → boolean

> 지면과 수직한 라인을 지정한 길이만큼 보이도록 설정.
> 
> length 입력값&gt;0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| length | number | POI 수직 라인 길이. |
| color | [JSColor](../core/jscolor.md) | POI 수직 라인 색상. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 생성 실패 조건
	  * type&lt;0 값이 설졍 된 경우

* Sample
  * function createPOI 참조.
  * [샌드박스\_POI 라인](http://sandbox.dtwincloud.com/code/main.do?id=object_point_line)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setRenderToTerrainTexture(type) → boolean

> POI를 RTT 기반으로 지형에 그리도록 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 기본 가시화.</p> |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPOI 참조.
  * [샌드박스\_POI RTT](http://sandbox.dtwincloud.com/code/main.do?id=object_point_rtt)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setText(text) → boolean

> POI 기사화 텍스트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| text | string | POI 텍스트 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPOI 참조.
  * [샌드박스\_POI](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setVisibleRange(enable, min, max) → boolean

> POI 오브젝트의 가시 범위를 설정.
> 
> min값이 max보다 큰 경우 자동으로 작은 값을 min값으로, 큰 값을 max값으로 바꾸어 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| enable | boolean | 가시범위 값 활성화 여부. |
| min | number | 최소 가시거리. |
| max | number | 최대 가시거리. |

* Return
  * POI 오브젝트가 외부 서버로부터 데이터를 불러와 생성 된 오브젝트인 경우 가시범위를 설정할 수 없음.
  * true : 가시범위 설정 성공.
  * false
    * 다음의 경우 API는 항상 false 를 반환.
    * POI 오브젝트가 외부 서버로부터 데이터를 불러와 생성 된 오브젝트인 경우.
    * POI 오브젝트가 null 인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
object.setVisibleRange(true, 50.0, 20000.0);
```
{% endtab %}
{% endtabs %}

## Getter / Setter

### getAltitude() → number

> 오브젝트의 고도를 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * number : 오브젝트 고도 (m 단위)

{% endtab %}

{% tab title="Template" %}
```javascript
var dAltitude = point.getAltitude();
```
{% endtab %}
{% endtabs %}

### setAltitude(alt) → boolean

> 오브젝트의 고도 값을 설정(오브젝트 경위도 값은 그대로 유지).

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| alt | number | 고도(m 단위). |

* Return
  * true : 위치 설정 성공.
  * false : 위치 설정 실패.

{% endtab %}

{% tab title="Template" %}
```javascript
point.setAltitude(50.0);
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

### getHighlight() → boolean

> Highlight 타입 아이콘 사용 여부를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 설정 성공.
  * false
    * 다음의 경우 API는 항상 false 를 반환.
    * POI 오브젝트가 null인 경우.
    * Highlight 타입으로 설정된 아이콘이 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var bHighlightUsed = object.getHighlight();
```
{% endtab %}
{% endtabs %}

### setHighlight(useHighlight)

> Highlight 타입 아이콘 사용 여부를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| useHighlight | boolean | Highlight 타입 아이콘 사용 여부.<br>true : Highlight 아이콘 이미지가 출력되도록 설정.</br><br>false : 기본 아이콘 이미지가 출력되도록 설정.</br> |
{% endtab %}
{% tab title="Template" %}
```javascript
object.setHighlight(true);
```
{% endtab %}
{% endtabs %}

### getHighlightIcon() → JSIcon*

> Highlight 타입 아이콘 오브젝트를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * JSIcon* : 설정 아이콘 오브젝트.
{% endtab %}

{% tab title="Template" %}
```javascript
var icon_hg = object.getHighlightIcon();
```
{% endtab %}
{% endtabs %}

### setHighlightIcon(icon)

> 하이라이트 타입 아이콘을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| icon | JSIcon | 설정 아이콘 오브젝트.</br> |

- Return
  - true : 아이콘 설정 성공.
  - false : 오브젝트가 없거나, 텍스처가 존재하지 않는 경우.

{% endtab %}
{% tab title="Template" %}
```javascript
var icon_hg = Module.getSymbol().getIcon("Icon_hg");
object.setHighlightIcon(icon_hg);
```
{% endtab %}
{% endtabs %}

### getIcon() → JSIcon*

> 기본 타입의 아이콘 오브젝트를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * JSIcon* : 설정 아이콘 오브젝트.
{% endtab %}

{% tab title="Template" %}
```javascript
var icon_normal = object.getIcon();
```
{% endtab %}
{% endtabs %}

### setIcon(icon)

> 기본 타입 아이콘을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| icon | JSIcon | 설정 아이콘 오브젝트.</br> |

- Return
  - true : 아이콘 설정 성공.
  - false : 오브젝트가 없거나, 텍스처가 존재하지 않는 경우.

{% endtab %}
{% tab title="Template" %}
```javascript
var icon = Module.getSymbol().getIcon("Icon2");
object.setIcon(icon);
```
{% endtab %}
{% endtabs %}

### getLatitude() → number

> 오브젝트의 위도를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number : 오브젝트 위도(Degree 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var dLatitude = point.getLatitude();
```
{% endtab %}
{% endtabs %}

### setLatitude(lat)

> 오브젝트의 위도 값을 설정(오브젝트 경도, 고도값은 그대로 유지).

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| lat | number | 위도(Degree 단위). |
- Return
  - true : 위치 설정 성공.
  - false : 오브젝트가 없는 경우.
{% endtab %}
{% tab title="Template" %}
```javascript
point.setLatitude(35.1713096);
```
{% endtab %}
{% endtabs %}

### getLongitude() → number

> 오브젝트의 경도를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number : 오브젝트 경도(Degree 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var dLongitude = point.getLongitude();
```
{% endtab %}
{% endtabs %}

### setLongitude(lon)

> 오브젝트의 경도 값을 설정(오브젝트 위도, 고도값은 그대로 유지).

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| lat | number | 경도(Degree 단위). |
- Return
  - true : 위치 설정 성공.
  - false : 오브젝트가 없는 경우.
{% endtab %}
{% tab title="Template" %}
```javascript
point.setLongitude(129.1270931);
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

> 오브젝트의 이름을 설정.

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
