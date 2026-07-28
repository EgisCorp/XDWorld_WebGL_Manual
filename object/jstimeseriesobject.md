---
description: 지도 내 시계열 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSTimeSeriesObject

> Module.createTimeSeriesObject() API를 생성합니다.
>
> 생성 후 create() 혹은 createbyJson() API에 파라메터를 전달하여 시계열 데이터 초기화 합니다.
>
> 데이터 갱신이 필요할 경우, insert(), merge() 순으로 함수를 호출하여 데이터 갱신.

```javascript
let object = Module.createTimeSeriesObject("ID");

// For detailed parameters, refer to the API documentation
object.create(/*parameter*/);
// ... or ...
object.createbyJson(/*parameter*/);
// ... or ...
object.insert(/*parameter*/);
// ... or ...
object.merge(/*parameter*/);
```

## Function

### create(parameter) → object

> 시계열 객체를 생성합니다.
>
> 여러 개의 시계열 오브젝트를 한번에 그리지 않고, 하나의 오브젝트만 생성할 때 사용합니다.
>
> parameter.legend는 사용되지 않으며, parameter.shape는 내부적으로 항상 평면(plane)으로 강제 설정되어 무시됩니다. 범례(legend)가 필요하거나 폴리곤 형태(polygon)로 생성하려면 [createbyJson()](jstimeseriesobject.md#createbyjson-parameter-object)을 사용하십시오.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                                                                  | Description |
| :-------- | :------------------------------------------------------------------------------------ | :---------- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeseriesobject.md#jstimeseriesobject.objectdata) | 속성 정보.  |

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name: 동작 API 명칭.
    -   .return: API 반환 정보 ( 문자열 : 실패 에러 코드 ).
    -   실패 조건
        -   지도가 로드되지 않은 경우.
        -   parameter.position이 없는 경우.
        -   parameter.segment 값이 2 미만인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createbyJson(parameter) → object

> 시계열 객체를 생성합니다.
>
> parameter.legend(범례 정보)가 필수이며, parameter.shape 값에 따라 폴리곤(polygon)/평면(plane) 형태를 선택할 수 있습니다.
>
> parameter.horizontal, parameter.vertical, parameter.area, parameter.color는 이 API에서는 사용되지 않습니다( [create()](jstimeseriesobject.md#create-parameter-object) 전용 필드 ).

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                                                                  | Description |
| :-------- | :------------------------------------------------------------------------------------ | :---------- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeseriesobject.md#jstimeseriesobject.objectdata) | 속성 정보.  |

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name: 동작 API 명칭.
    -   .return: API 반환 정보 ( 문자열 : 실패 에러 코드 ).
    -   실패 조건
        -   지도가 로드되지 않은 경우.
        -   parameter.position이 없는 경우.
        -   parameter.legend가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### insert(parameter) → object

> 새로운 시계열 데이터를 추가합니다.
>
> 이후 [merge()](jstimeseriesobject.md#merge-object)를 호출하여 입력한 데이터를 기존 객체에 추가하는 작업 필요합니다.
>
> parameter 중 position 만 실제로 사용되며, segment/rotate/horizontal/vertical/shape/color/area/image 등 나머지 필드는 파싱만 되고 내부적으로 사용되지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                                                                  | Description |
| :-------- | :------------------------------------------------------------------------------------ | :---------- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeseriesobject.md#jstimeseriesobject.objectdata) | 속성 정보.  |

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name: 동작 API 명칭.
    -   .return: API 반환 정보 ( 문자열 : 실패 에러 코드 ).
    -   실패 조건
        -   지도가 로드되지 않은 경우.
        -   parameter.position이 없는 경우.

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### merge() → object

> [insert()](jstimeseriesobject.md#insert-parameter-object)로 입력한 데이터를 기존 시계열 객체에 추가합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name: 동작 API 명칭.
    -   .return: API 반환 정보 ( 문자열 : 실패 에러 코드 ).
    -   실패 조건
        -   지도가 로드되지 않은 경우.
        -   [insert()](jstimeseriesobject.md#insert-parameter-object)로 추가된 데이터가 하나도 없는 경우.
        -   이미 병합되어 오브젝트가 생성되어 있는 경우(중복 실행 방지).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTimeSeriesObject.ObjectData

> 시계열 객체 생성 정보.

| Name       | Type                                                                                | Attributes | Default                                           | Description                                               |
| ---------- | ----------------------------------------------------------------------------------- | ---------- | ------------------------------------------------- | --------------------------------------------------------- |
| position   | [JSVector3D](../core/jsvector3d.md)                                                 |            |                                                   | 중심 좌표 (경도, 위도, 고도). create()/createbyJson()/insert() 공통 필수 항목.                             |
| segment    | number                                                                              | optional   | 4                                                 | 평면 형태 (2: 평면, 3: 삼각형, 4: 사각형, 5: 오각형). create()/createbyJson()에서 사용되며, insert()에서는 무시됩니다. create()의 경우 2 미만이면 생성에 실패합니다.     |
| rotate     | number                                                                              | optional   | 0                                                 | 객체 회전 (0,360: north, 90: east, 180: south, 270: west). create()/createbyJson()에서 사용되며, insert()에서는 무시됩니다. |
| horizontal | number                                                                              | optional   | 5.0                                               | 시계열 객체의 가로 크기 설정. create() 전용 항목이며, createbyJson()/insert()에서는 사용되지 않습니다.                             |
| vertical   | number                                                                              | optional   | 5.0                                               | 시계열 객체의 세로 크기 설정. create() 전용 항목이며, createbyJson()/insert()에서는 사용되지 않습니다.                             |
| shape      | number                                                                              | optional   | 0                                                 | 객체 형태 (0: 3D 다각면, 1: 2D 평면). createbyJson()에서만 적용되며, create()에서는 내부적으로 항상 1(평면)로 강제되어 무시되고, insert()에서도 사용되지 않습니다.                      |
| color      | [JSColor](../core/jscolor.md)                                                       | optional   | [JSColor](../core/jscolor.md)(255, 255, 255, 255) | 객체 색상. create() 전용 항목이며, createbyJson()/insert()에서는 사용되지 않습니다.                                                |
| area       | [JSTimeSeriesObject.AreaData](jstimeseriesobject.md#jstimeseriesobject.areadata)   | optional   |                                                   | 객체 크기 (이미지 연산이 필요). create() 전용 항목이며, createbyJson()/insert()에서는 사용되지 않습니다.                           |
| image      | [JSTimeSeriesObject.ImageData](jstimeseriesobject.md#jstimeseriesobject.imagedata) | optional   |                                                   | 이미지 정보. create()/createbyJson()에서 사용되며, insert()에서는 무시됩니다.                                              |
| legend     | [JSTimeSeriesObject.Legend](jstimeseriesobject.md#jstimeseriesobject.legend)       |            |                                                    | 범례 생성 정보. createbyJson()에서만 필수이며, create()/insert()에서는 사용되지 않습니다.                                           |

#### JSTimeSeriesObject.AreaData

> 시계열 객체의 크기를 설정합니다.

| Name | Type                                | Attributes | Default                                      | Description                        |
| ---- | ----------------------------------- | ---------- | -------------------------------------------- | ---------------------------------- |
| min  | [JSVector3D](../core/jsvector3d.md) | optional   | [JSVector3D](../core/jsvector3d.md)(0, 0, 0) | 최소 영역 좌표 (경도, 위도, 고도). |
| max  | [JSVector3D](../core/jsvector3d.md) | optional   | [JSVector3D](../core/jsvector3d.md)(0, 0, 0) | 최대 영역 좌표 (경도, 위도, 고도). |

#### JSTimeSeriesObject.ImageData

| Name   | Type   | Description    |
| ------ | ------ | -------------- |
| width  | number | 이미지 너비.   |
| height | number | 이미지 높이.   |
| image  | object | 이미지 픽셀 데이터(canvas 등에서 얻은 이미지 데이터). |

#### JSTimeSeriesObject.Legend

> Legend data. Store multiple data and color items grouped together in an array.

| Name  | Type                                                                          | Description     |
| ----- | ----------------------------------------------------------------------------- | --------------- |
| data  | number                                                                        | 범례 구간 크기. |
| color | [JSColor](../core/jscolor.md) 또는 { a, r, g, b } 형태의 object, 혹은 16진수 색상 문자열 | 범례의 색상값.  |
