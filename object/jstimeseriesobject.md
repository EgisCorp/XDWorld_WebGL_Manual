---
description: 시계열 오브젝트 생성 및 수정 API.
---

# JSTimeSeriesObject

> Module.createTimeSeriesObject API 생성.
> 
> 생성 후 create() 혹은 createbyJson() API에 파라메터를 전달하여 시계열 데이터 초기화.
> 
> 데이터 갱신이 필요할 경우, insert(), merge() 순으로 함수를 호출하여 데이터 갱신.

```javascript
let object = Module.createTimeSeriesObject("timeSeriesObject");

// 자세한 파라메터는 API 참고
object.create(/*parameter*/);
object.createJSON(/*parameter*/);

object.insert(/*parameter*/);
object.merge(/*parameter*/);
```

### create(parameter) → error

> 시계열 객체 생성.
>
> parameter 변수로 전체 데이터(이미지, 경위도 기준점, 객체 크기, 객체 형태) 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeobject.md#jstimeobject.objectdata) | 전체 데이터. |

* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSTimeSeriesPolygon.create" 고정.</br> |
  | return | string | (실패시)오류 메시지를 string으로 반환(자세한 사항은 메시지 참조). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### createbyJson(parameter) → error

> 시계열 객체 생성.
>
> parameter 변수로 전체 데이터(이미지, 경위도 기준점, 객체 크기, 객체 형태) 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeobject.md#jstimeobject.objectdata) | 전체 데이터. |

* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSTimeSeriesPolygon.createByJson" 고정.</br> |
  | return | string | (실패시)오류 메시지를 string으로 반환(자세한 사항은 메시지 참조). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insert(parameter) → error

> 추가할 객체 정보 입력.
> 
> 이후 merge()를 호출하여 입력한 데이터를 기존 객체에 추가하는 작업 필요.
>
> parameter 변수로 전체 데이터(이미지, 경위도 기준점, 객체 크기, 객체 형태) 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeobject.md#jstimeobject.objectdata) | 전체 데이터. |

* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSTimeSeriesPolygon.insert" 고정.</br> |
  | return | string | (실패시)오류 메시지를 string으로 반환(자세한 사항은 메시지 참조). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### merge() → error

> insert()로 입력한 데이터를 기존 객체에 추가하는 함수.

{% tabs %}
{% tab title="Information" %}
* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSTimeSeriesPolygon.merge" 고정.</br> |
  | return | string | (실패시)오류 메시지를 string으로 반환(자세한 사항은 메시지 참조). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTimeSeriesObject.ObjectData
| Name   | Type | Attributes | Default | Description |
| --- | --- | --- | --- | --- |
| position   | JSVector3D |           |           | 3차원 좌표(경위고도) |
| segment    | number | optional | 4 | 다각형 형태(2 평면, 3 삼각형, 4 사각형, 5 오각형) |
| rotate     | number | optional | 0 | 오브젝트 회전 방향(0,360 : 북쪽, 90 : 동쪽, 180 : 남쪽, 270 : 서쪽) |
| horizontal | number | optional | 5.0 | create API 동작 시 오브젝트 크기 설정(수평) |
| vertical   | number | optional | 5.0 | create API 동작 시 오브젝트 크기 설정(수직) |
| shape      | number | optional | 0 | 오브젝트 형태(0 : polygon, 1 : plane) |
| color      | JSColor | optional | JSColor(255, 255, 255, 255) | 오브젝트 메인 색상. |
| area       | [JSTimeSeriesObject.AreaData](jstimeobject.md#jstimeobject.areadata) | optional |           | 오브젝트 크기(텍스처 연산에 필요). |
| image      | [JSTimeSeriesObject.ImageData](jstimeobject.md#jstimeobject.imagedata)          |           |           |           |
| legend     | [JSTimeSeriesObject.Legend](jstimeobject.md#jstimeobject.legend) | optional | JSColor(255, 255, 255, 255) | 오브젝트 메인 색상. |

#### JSTimeSeriesObject.AreaData
| Name   | Type | Description |
| --- | --- | --- | --- | --- |
| min | JSVector3D | optional | JSVector3D(0, 0, 0) | 3차원 좌표(경위고도) |
| max | JSVector3D | optional | JSVector3D(0, 0, 0) | 다각형 형태(2 평면, 3 삼각형, 4 사각형, 5 오각형) |

#### JSTimeSeriesObject.ImageData
| Name   | Type | Description |
| --- | --- | --- |
| width | number | 이미지 가로 크기. |
| height | number | 이미지 세로 크기. |
| image | array | 이미지 픽셀 데이터(canvas에서 CanvasRenderingContext2D.getImageData()로 받아오는 픽셀 데이터). |

#### JSTimeSeriesObject.Legend

> 범례 데이터. 하나로 묶은 data와 color 항목 여러 개를 배열로 저장.

| Name   | Type | Description |
| --- | --- | --- |
| data | float | 범례의 크기. |
| color | JSColor or array(argb를 네 개의 float으로 정의한 배열) | 범례의 색상. |
