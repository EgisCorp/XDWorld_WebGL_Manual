---
description: 지도 내 파이프 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSPipe

> Module.createPipe() API를 생성합니다.

```javascript
var object = Module.createPipe("ID");
```

## Function

### create(coordinates, startColor, endColor, segment, radius, width) → boolean

> 3d 파이프 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                | Description                                                                     |
| :---------- | :---------------------------------- | :-------------------------------------------------------------------------------- |
| coordinates | [Collection](../core/collection.md) | 좌표 목록(경도, 위도, 고도).                                                     |
| startColor  | [JSColor](../core/jscolor.md)       | 시작 파이프 색상.                                                                |
| endColor    | [JSColor](../core/jscolor.md)       | 끝 파이프 색상.                                                                  |
| segment     | number                              | 단면의 다각수(값이 클수록 파이프 단면이 원형에 가까워지며, 비례하여 메모리 소모량이 증가함). |
| radius      | number                              | 반지름.                                                                          |
| width       | number                              | 라인 형태로 표현 시 적용될 라인 두께 설정.                                       |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패. (좌표(coordinates) 개수가 2개 미만이거나 객체가 NULL인 경우)
-   Sample
    -   function createUndergroundFacility 참조.
    -   [Sandbox_Creating Excavation](https://sandbox.egiscloud.com/code/main.do?id=analysis_transparency_create)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getExtent() → number

> 3d 파이프 객체의 공간 영역의 장축 거리를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 거리 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var bExtends = figure.getExtent();
```

{% endtab %}
{% endtabs %}

### getFormatData(format) → Uint8Array

> 3d 파이프 객체의 지오메트리를 지정한 포맷의 바이너리 데이터로 변환하여 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                     |
| :----- | :----- | :------------------------------- |
| format | string | 변환할 포맷 문자열 (예: "3DS"). |

-   Return
    -   Uint8Array: 변환 성공.
    -   null: 객체가 NULL이거나 지원하지 않는 포맷인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var bytes = object.getFormatData("3DS");
// ... 사용 후 ...
object.releaseFormatDataMemory();
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

### getPositions() → [JSVec3Array](../core/jsvec3array.md)

> 3d 파이프를 구성하는 좌표(경도, 위도, 고도) 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVec3Array](../core/jsvec3array.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### moveVertically(altitude) → boolean

> 3d 파이프 객체의 고도를 설정합니다.
>
> 입력 변수값(altitude)이 -1000보다 작은 경우, 자동으로 -1000으로 제한(clamp)되어 적용됩니다(해발고도 기준, 실패 처리되지 않음).

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description |
| :------- | :----- | :---------- |
| altitude | number | 고도 설정.  |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패. (객체가 NULL인 경우)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### releaseFormatDataMemory()

> `getFormatData()` 호출로 할당된 포맷 변환용 버퍼 메모리를 해제합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   없음.

{% endtab %}
{% tab title="Template" %}

```javascript
object.releaseFormatDataMemory();
```

{% endtab %}
{% endtabs %}

### setColor(starColor, endColor) → boolean

> 3d 파이프 객체의 시작, 끝에 대한 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type                          | Description |
| :--------- | :---------------------------- | :---------- |
| startColor | [JSColor](../core/jscolor.md) | 시작 색상.  |
| endColor   | [JSColor](../core/jscolor.md) | 끝 색상.    |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFlow(startColor, endColor, segment, interval) → boolean

> 3d 파이프 객체 내부 흐름 표현 형태를 설정합니다.
>
> 입력 변수값(segment)은 3 이상의 값이 설정되어야 합니다(3 미만인 경우 설정 실패).
>
> 입력 변수값(interval)은 0 이상의 값이 설정되어야 합니다(음수인 경우 설정 실패).

{% tabs %}
{% tab title="Information" %}

| Name       | Type                          | Description              |
| :--------- | :---------------------------- | :----------------------- |
| startColor | [JSColor](../core/jscolor.md) | 시작 색상.               |
| endColor   | [JSColor](../core/jscolor.md) | 끝 색상.                 |
| segment    | number                        | 흐름 구성을 위한 점수.   |
| interval   | number                        | 흐름 표현 화살표의 간격. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createUndergroundFacility 참조.
    -   [Sandbox_Creating Excavation](https://sandbox.egiscloud.com/code/main.do?id=analysis_transparency_create)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFlowDisplay(type) → boolean

> 3d 파이프 객체 내부 흐름 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                        |
| :--- | :------ | :------------------------------------------------- |
| type | boolean | <p>true: 흐름 가시화.<br>false: 흐름 비가시화.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createUndergroundFacility 참조.
    -   [Sandbox_Creating Excavation](https://sandbox.egiscloud.com/code/main.do?id=analysis_transparency_create)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setFlowWaitFrame(frame) → boolean

> 3d 파이프 내부 흐름에 대한 갱신 프레임 수를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description     |
| :---- | :----- | :-------------- |
| frame | number | 갱신 프레임 수. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createUndergroundFacility 참조.
    -   [Sandbox_Creating Excavation](https://sandbox.egiscloud.com/code/main.do?id=analysis_transparency_create)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSimplifyRange(range) → boolean

> 3d 파이프 객체의 간소화 표현 거리를 설정합니다.
>
> 입력 변수값(range)은 0 이상의 값이 설정되어야 합니다(음수인 경우 설정 실패).
>
> 간소화 표현 중 흐름 표현은 생략됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | :----- | :----------- |
| range | number | 간소화 거리. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createPipe 참조.
    -   [Sandbox_Pipe](https://sandbox.egiscloud.com/code/main.do?id=object_pipe)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getRadius(), setRadius(radius) → number, boolean

> 3d 파이프 객체의 반지름(meter 단위)을 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description |
| ------ | ------ | ----------- |
| radius | number | 반지름(m).  |

-   Return
    -   getRadius() : number - 반지름 반환.
    -   setRadius(radius) : true - 설정 성공. / false - 객체가 NULL인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var radius = object.getRadius();
// ... or ...
object.setRadius(5.0);
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
