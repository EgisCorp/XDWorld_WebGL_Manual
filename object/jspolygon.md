---
description: 폴리곤 객체 생성 및 수정 기능 API.
---

# JSPolygon

> Module.createPolygon API 생성.

```javascript
var object = Module.createPolygon("ID");
```

### loadFile(option) → boolean

> 3ds 파일 로드 후 폴리곤 객체를 생성.
>
> argument 변수로 태풍 객체 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| option | 연결 | 초기화 옵션 속성 정보. |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
    * 객체 생성 실패 조건
      * positionmode=true 일 때 projectioncode가 설정되지 않음
	  * positionmode=false 일 때 position이 지정되지 않음  

* Sample
  * function load3DS 참조.
  * [샌드박스\_3DS](http://sandbox.dtwincloud.com/code/main.do?id=object_file_3ds)
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
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 텍스쳐 등록 명칭. |
| url | string | 텍스쳐 이미지 URL. |

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
  * [샌드박스\_폴리곤 RTT](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_rtt_image_changing)  
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setCircle(position, radius, segment) → boolean

> 중심좌표 기준으로 원 모양 평면 객체를 생성.
> 
> radius 입력값&gt;0 필수 설정.
>
> segment 입력값&gt;3 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](../core/jsvector3d.md) | 원 폴리곤 중심 경위도 좌표. |
| radius | number | 반경. |
| segment | number | 버텍스 수. |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
    * 객체 생성 실패 조건
      * radius 값이 0
	  * segment 값이 3 미만

* Sample
  * function createCirclePolygon 참조.
  * [샌드박스\_원 폴리곤](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_circle)  
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setCoordinates(coordinates)

> Polygon 평면을 구성하는 좌표 리스트를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [Collection](../core/collection.md)) | 폴리곤 경위도 좌표 목록. |

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
| Name | Type | Description |
| :--- | :--- | :--- |
| index | number | 텍스쳐를 사용할 폴리곤 face index |
| name | string | loadTexture API로 지정한 텍스쳐 이름 |

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패
    * 객체 생성 실패 조건
	  * 지정한 텍스쳐 이름이 없음
	  * 지정한 index의 폴리곤 face가 존재하지 않음
	
* Sample
  * function init 참조.
  * [샌드박스\_폴리곤 RTT](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_rtt_image_changing)  
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
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 불 효과 가시화(RTT)<br>false인 경우 기본 가시화.</p> |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 설정 실패 조건
      * 폴리곤 좌표 설정이 안된 경우.
	  
* Sample
  * function createBurnEffectPolygon 참조.
  * [샌드박스\_불 효과](http://sandbox.dtwincloud.com/code/main.do?id=effect_fire)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setHeight(height) → boolean

> 평면 폴리곤을 높이를 가진 3차원 폴리곤으로 생성.
> 
> height 입력값&gt;0 필수 설정(미터).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| height | number | 폴리곤 높이 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
    * 객체 설정 실패 조건
      * 폴리곤 좌표 설정이 안된 경우.
	
* Sample
  * function createPolygon 참조.
  * [샌드박스\_폴리곤 높이](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_height)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPartCoordinates(coordinates, parts) → boolean

> 폴리곤 좌표(vertex, part)를 지정합니다.
> 
> 

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 폴리곤 경위도 좌표 목록. |
| parts | [Collection](../core/collection.md)) | 폴리곤 구성 점정 개수 목록. |

* Detail
  * part\_list : 파트를 이루는 버텍스 갯수의 리스트를 입력합니다.

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
    * 객체 생성 실패 조건.
	  * 입력된 coordinates 구성요소가 없거나 정점 개수가 3개 이하인 경우.
	  * 입력된 parts 구성요소가 없거나 1개 이하인 경우.

* Sample
  * function createPolygon 참조.
  * [샌드박스\_폴리곤 높이](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_height)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPartCoordinatesUV(coordinates, parts, uv, union) → boolean

> 텍스쳐 uv를 포함한 폴리곤 좌표(vertex, part, uv)를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 폴리곤 경위도 좌표 목록. |
| parts | [Collection](../core/collection.md)) | 폴리곤 구성 점정 개수 목록. |
| uv | [JSVec2Array](../core/jsvec2array.md) | 폴리곤 구성 UV 좌표 목록. |
| union | boolean | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 기본 가시화.</p> |

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
  * [샌드박스\_폴리곤 RTT](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_rtt_image_changing)  
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
| Name | Type | Description |
| :--- | :--- | :--- |
| style | JSPolygonStyle | 객체 스타일 설정 객체 |

* Sample
  * function createBurnEffectPolygon 참조.
  * [샌드박스\_불 효과](http://sandbox.dtwincloud.com/code/main.do?id=effect_fire)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

##### Type Definitions

####### JSPolygon.loadFile

> 3ds 파일 로드 후 폴리곤 객체 생성 옵션.
> 
> 변경 사항이 있어 수정 요망
| Name         | Type                          | Attributes | Default                 | Description      |
| ------------ | ----------------------------- | ---------- | ----------------------- | ---------------- |
