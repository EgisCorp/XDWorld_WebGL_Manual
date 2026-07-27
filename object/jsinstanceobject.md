---
description: 지도 내 인스턴스 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSInstanceObject

> Module.createInstanceObject API를 생성합니다.

```javascript
let instanceObject = Module.createInstanceObject("object");
```

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

### getIntersectObjects(parameter) → error

> 등록된 인스턴스 객체와 입력 변수값(parameter)에서 설정된 직선과 겹치는 항목을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                                                                                         | Description     |
| --------- | ------------------------------------------------------------------------------------------------------------ | --------------- |
| parameter | [JSInstanceObject.IntersectObjectsParameter](jsinstanceobject.md#jsinstanceobject.intersectobjectsparameter) | 비교 속성 정보. |

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name: 동작 API 명칭.
    -   .return: API 반환 정보 ( object : 정상적인 반환값, 문자열 : 실패 에러 코드 ).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### loadFile(options) → boolean

> 좌표 목록에 인스턴스 객체를 생성합니다. `options.url`을 지정하지 않으면 각 좌표 위치에 단순 박스 형태로 생성하고, `url`을 지정하면 해당 메쉬 파일을 비동기로 로드하여 각 좌표에 인스턴스로 배치합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                                                       | Description        |
| ------- | --------------------------------------------------------------------------- | ------------------- |
| options | [JSInstanceObject.LoadFileOptions](jsinstanceobject.md#jsinstanceobject.loadfileoptions) | 인스턴스 생성 옵션. |

-   Return
    -   true: 박스 생성 성공, 또는 파일 로드 요청 성공(실제 로드 완료 여부는 `callback`으로 확인).
    -   false: 생성/요청 실패.
    -   실패 조건
        -   맵이 정상적으로 로드되지 않은 경우.
        -   options가 null/undefined인 경우.
        -   options.listPosition이 없거나 파싱에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("object");
instanceObject.loadFile({
    listPosition: [[127.0, 37.5, 0], [127.001, 37.501, 0]],
    url: "model.dae",
    callback: function (key) {
        console.log("load complete : " + key);
    }
});
```

{% endtab %}
{% endtabs %}

### create(parameter) → object

> 인스턴스 객체를 생성합니다.
>
> `parameter.type`이 지정된 경우, `startPosition`/`info`에 정의된 값 목록을 기준으로 박스 형태의 인스턴스를 생성합니다.
>
> `parameter.type`이 없는 경우, `parameter.object`(JSPolygon 타입 오브젝트)를 원본 메쉬로 하여 `array`에 정의된 위치/회전/크기/색상 목록만큼 인스턴스를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                                                     | Description      |
| --------- | -------------------------------------------------------------------------- | ----------------- |
| parameter | [JSInstanceObject.CreateOptions](jsinstanceobject.md#jsinstanceobject.createoptions) | 인스턴스 생성 옵션. |

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name: 동작 API 명칭("JSInstanceObject.create").
    -   .return: API 반환 정보 ( "success" : 정상 생성, 이 외 문자열 : 실패 에러 메시지 ).

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("object");
let result = instanceObject.create({
    object: sourcePolygon,
    verticalAlign: "bottom",
    array: {
        position: [[127.0, 37.5, 0], [127.001, 37.501, 0]]
    }
});
```

{% endtab %}
{% endtabs %}

### createObjectInArea(options) → number

> 지정된 영역(폴리곤) 내부에 일정 간격으로 박스 형태의 인스턴스 객체를 격자 배치로 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                                     | Description                                  |
| -------- | ----------------------------------------------------------- | ---------------------------------------------- |
| options  | [JSInstanceObject.CreateObjectInAreaOptions](jsinstanceobject.md#jsinstanceobject.createobjectinareaoptions) | 영역 및 간격 옵션. |

-   Return
    -   number(1 이상): 생성된 인스턴스 개수.
    -   number(0): 생성 실패(맵 미준비, 옵션 누락/파싱 실패, 또는 간격 옵션 값이 2개 미만인 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("object");
let count = instanceObject.createObjectInArea({
    area: [[127.0, 37.5], [127.01, 37.5], [127.01, 37.51], [127.0, 37.51]],
    interval: [10, 10]
});
```

{% endtab %}
{% endtabs %}

### applyViewObject(parameter) → object

> 입력한 인덱스 목록에 해당하는 인스턴스만 화면에 표시되도록 적용합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                | Description                          |
| --------- | -------------------------------------- | --------------------------------------- |
| parameter.array | [Collection](../core/collection.md) 또는 number 배열 | 화면에 표시할 인스턴스 인덱스 목록. |

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name: 동작 API 명칭.
    -   .return: API 반환 정보 ( "success" : 정상 적용, 이 외 문자열 : 실패 에러 메시지 ).
-   Note
    -   실제 코드상 반환되는 `.name` 값은 복사/붙여넣기 흔적으로 인해 "JSInstanceObject.getOverlappingObjects" 로 고정 반환됩니다(함수 자체 동작에는 영향 없음).

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("object");
instanceObject.applyViewObject({ array: [0, 2, 5] });
```

{% endtab %}
{% endtabs %}

### clearViewObject() → object

> `applyViewObject`로 적용된 화면 표시 인스턴스 목록을 초기화(해제)합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공 ).
    -   .name: 동작 API 명칭.
    -   .return: "success".
-   Note
    -   실제 코드상 반환되는 `.name` 값은 복사/붙여넣기 흔적으로 인해 "JSInstanceObject.getOverlappingObjects" 로 고정 반환됩니다(함수 자체 동작에는 영향 없음).

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("object");
instanceObject.clearViewObject();
```

{% endtab %}
{% endtabs %}

### setInstanceColor(index, color)

> 지정한 인덱스의 인스턴스 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description        |
| ----- | ------------------------------- | -------------------- |
| index | number                          | 인스턴스 인덱스.     |
| color | [JSColor](../core/jscolor.md)   | 설정할 색상.         |

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("object");
instanceObject.setInstanceColor(0, new Module.JSColor(255, 255, 0, 0));
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getAlpha(), setAlpha(alpha) → number

> 인스턴스 객체 투명도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| alpha | number | 투명도.     |

-   Return
    -   number: 설정된 투명도.

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("object");
let alpha = instanceObject.getAlpha();
// ... or ...
let instanceObject = Module.createInstanceObject("object");
instanceObject.setAlpha(0.5);
```

{% endtab %}
{% endtabs %}

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

### applyViewCount → number

> `applyViewObject`로 적용되어 현재 화면에 표시 중인 인스턴스 개수를 반환합니다.

> setter는 현재 반영되지 않습니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 현재 적용되어 화면에 표시 중인 인스턴스 개수.

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("object");
let count = instanceObject.applyViewCount;
// ... or ...
instanceObject.applyViewCount = 5; // 주의: 실제로는 설정되지 않음(스텁)
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSInstanceObject.LoadFileOptions

> `loadFile` 호출 시 사용하는 옵션.

| Name         | Type                                | Attributes | Default  | Description                                                                 |
| ------------ | ------------------------------------- | ---------- | -------- | ------------------------------------------------------------------------------ |
| listPosition | array                                  |            |          | 인스턴스를 배치할 좌표 목록(경도, 위도, 고도).                                 |
| listRotation | array                                  | optional   |          | 각 인스턴스의 회전 값 목록(x, y, z).                                           |
| listScale    | array                                  | optional   |          | 각 인스턴스의 크기(스케일) 값 목록(x, y, z).                                   |
| listColor    | array                                  | optional   |          | 각 인스턴스의 색상 목록.                                                       |
| align        | string                                 | optional   | "center" | 좌표 정렬 기준. "center" \| "bottom" \| "top"                                 |
| url          | string                                 | optional   |          | 로드할 메쉬 파일 경로/URL. 지정하지 않으면 좌표마다 단순 박스 형태로 생성됩니다. |
| callback     | function                               | optional   |          | `url` 지정 시, 파일 로드가 완료되면 호출됩니다. 인자로 생성된 오브젝트 key(string)를 전달받습니다. |

#### JSInstanceObject.CreateOptions

> `create` 호출 시 사용하는 옵션. 아래 두 형태 중 하나로 사용됩니다.

**형태 1: 타입 기반 생성 (`type` 지정)**

| Name         | Type   | Attributes | Description                                                       |
| ------------ | ------ | ---------- | --------------------------------------------------------------------- |
| type         | string |            | 생성할 인스턴스 타입.                                                  |
| startPosition| array  |            | 기준 좌표 [경도, 위도, (고도)]. 최소 2개 값 필요.                       |
| info         | object |            | 생성 정보.                                                             |
| info.value   | array  |            | 인스턴스 값 목록(number 배열).                                         |
| info.position| array  |            | 인스턴스 상대 위치 목록(좌표 배열).                                    |
| align        | string | optional   | 정렬 기준 문자열.                                                      |

**형태 2: 오브젝트 기반 생성 (`type` 미지정)**

| Name              | Type                            | Attributes | Default  | Description                                                    |
| ----------------- | ---------------------------------- | ---------- | -------- | ------------------------------------------------------------------ |
| object            | [JSPolygon](jspolygon.md)          |            |          | 인스턴스의 원본이 되는 JSPolygon 타입 오브젝트.                     |
| verticalAlign     | string                              | optional   | "bottom" | 수직 정렬 기준. "middle" \| "bottom" \| "top"                       |
| array             | object                              |            |          | 인스턴스 배치 정보.                                                 |
| array.position    | array                               |            |          | 인스턴스 위치 목록(좌표 배열). 필수.                                |
| array.rotation    | array                               | optional   |          | 인스턴스 회전 목록.                                                 |
| array.scale       | array                               | optional   |          | 인스턴스 크기(스케일) 목록.                                         |
| array.color       | array of [JSColor](../core/jscolor.md) | optional |          | 인스턴스 색상 목록.                                                 |

#### JSInstanceObject.CreateObjectInAreaOptions

> `createObjectInArea` 호출 시 사용하는 옵션.

| Name     | Type   | Description                                                              |
| -------- | ------ | ---------------------------------------------------------------------------- |
| area     | array  | 영역을 구성하는 좌표 목록(경도, 위도, (고도)). 폴리곤 형태로 닫혀야 합니다.  |
| interval | array  | 격자 간격 [x축 간격, y축 간격] (m 단위). 최소 2개 값 필요.                   |

#### JSInstanceObject.IntersectObjectsParameter

> 등록된 인스턴스 객체와 겸침 유무 정보를 설정합니다.

| Name        | Type                                                                                                                                 | Default | Description                  |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------- | ---------------------------- |
| objectType  | string                                                                                                                               | "line"  | 객체 타입(점, 선, 면).       |
| coordinates | [JSInstanceObject.IntersectObjectsParameter.coordinates](jsinstanceobject.md#jsinstanceobject.intersectobjectsparameter.coordinates) |         | 좌표 목록(경도, 위도, 고도). |

#### JSInstanceObject.IntersectObjectsParameter.coordinates

| Name        | Type   | Description                                                                                                                                                                                                                                                           |
| ----------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| style       | string | 좌표 변환 타입. 아래 네 가지에 해당되지 않는 경우, 오류 발생.<br>XY : 경위도 배열 값 [x, y], [x, y]</br><br>XYZ : 경위고도 배열 값 [x, y, z], [x, y, z]</br><br>XYZARRAY : 경위고도 배열 값 [x, y, z, x, y, z]</br><br>JSVector3D : 경위고도 JSVec3Array 배열 값</br> |
| coordinates | number | 좌표 목록(경도, 위도, 고도).                                                                                                                                                                                                                                          |
