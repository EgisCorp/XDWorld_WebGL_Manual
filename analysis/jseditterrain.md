---
description: 지도 내 지형 편집 기능 설정을 위한 API입니다.
---

# JSEditTerrain

> Module.getEditTerrain API를 생성합니다..

```javascript
var editTerrain = Module.getEditTerrain();
```

## Function

### clear() → boolean

> 지형 편집을 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   function clearEditTerrain 참조.
    -   [Sandbox_Terrain Cut and Fill](https://sandbox.egiscloud.com/code/main.do?id=analysis_terrain_edit)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeAtIndex(index) → boolean

> 지정한 인덱스에 해당하는 성절토 편집 내용을 원복(삭제)합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                     |
| :---- | :----- | :---------------------------------------------------------------- |
| index | number | 원복할 성절토 편집 인덱스 (0 \~ getEditCount() - 1 범위).        |

-   Return
    -   true: 원복 성공.
    -   false: 지도가 로드되지 않은 경우.
-   Sample
    -   function clearEditTerrain 참조.
    -   [Sandbox_Terrain Cut and Fill](https://sandbox.egiscloud.com/code/main.do?id=analysis_terrain_edit)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### create(coordinates, height, angle) → boolean

> 지형 성절토를 수행합니다.
>
> 분석영역을 기준으로 수행합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                   |
| :---------- | :------------------------------------ | :-------------------------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 분석영역 좌표 목록 (경도, 위도, 고도).        |
| height      | number                                | 해발 고도 기준 성절토 기준 높이 (meter 단위). |
| angle       | number                                | 성절토 사면 각도 (degree 단위).               |

-   Sample
    -   function createEditTerrain 참조.
    -   [Sandbox_Terrain Cut and Fill](https://sandbox.egiscloud.com/code/main.do?id=analysis_terrain_edit)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createBoundary(min, max, height, angle) → boolean

> 지형 성절토를 수행합니다.
>
> 최소 좌표점, 최대 좌표점으로 구성된 경계박스 영역을 기준으로 수행합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                | Description                                   |
| :----- | :---------------------------------- | :-------------------------------------------- |
| min    | [JSVector2D](../core/jsvector2d.md) | 최소 좌표점 (경도, 위도).                     |
| max    | [JSVector2D](../core/jsvector2d.md) | 최대 좌표점 (경도, 위도).                     |
| height | number                              | 해발 고도 기준 성절토 기준 높이 (meter 단위). |
| angle  | number                              | 성절토 사면 각도 (degree 단위).               |

-   Sample
    -   function createEditTerrain 참조.
    -   [Sandbox_Terrain Cut and Fill](https://sandbox.egiscloud.com/code/main.do?id=analysis_terrain_edit)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getEditCount() → number

> 등록된 성절토 편집 객체의 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number(0 \~): 등록된 편집 객체 수.
    -   -1: 지도가 로드되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getAddVolume(index) → number

> 지정한 인덱스의 성절토 편집 객체의 성토량(추가된 토양의 부피)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                              |
| :---- | :----- | :---------------------------------------------------------- |
| index | number | 조회할 성절토 편집 인덱스 (0 \~ getEditCount() - 1 범위). |

-   Return
    -   number: 성토량(부피 근사값, meter 기반 세제곱미터 단위로 추정).
    -   0.0: 지도가 로드되지 않았거나, index가 유효 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getSubVolume(index) → number

> 지정한 인덱스의 성절토 편집 객체의 절토량(제거된 토양의 부피)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                              |
| :---- | :----- | :---------------------------------------------------------- |
| index | number | 조회할 성절토 편집 인덱스 (0 \~ getEditCount() - 1 범위). |

-   Return
    -   number: 절토량(부피 근사값, meter 기반 세제곱미터 단위로 추정).
    -   0.0: 지도가 로드되지 않았거나, index가 유효 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setEditFaceTexture(data, width, height, type) → boolean

> 성절토 시 측면에 존재하는 사면/바닥면에 이미지를 적용합니다.
>
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                              |
| :----- | :------ | :------------------------------------------------------- |
| data   | object  | 사면(또는 바닥면)에 적용할 이미지 데이터.                |
| width  | number  | 이미지 너비.                                             |
| height | number  | 이미지 높이.                                             |
| type   | boolean | <p>바닥면, 사면 구분<br>true: 바닥면<br>false: 사면 </p> |

-   Return
    -   true: 텍스처 설정 성공.
    -   false: 지도가 로드되지 않은 경우.
-   Sample
    -   function createEditTerrain 참조.
    -   [Sandbox_Terrain Cut and Fill](https://sandbox.egiscloud.com/code/main.do?id=analysis_terrain_edit)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setBottomTextureTilingScale(u, v) → boolean

> 성절토 바닥면 텍스처의 반복 출력(타일링) 배율을 설정합니다.
>
> 1.0보다 큰 값을 입력하면 설정한 텍스처가 해당 배율만큼 반복 출력됩니다.
>
> API 호출 이후 생성되는 성절토 객체부터 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description        |
| :--- | :----- | :------------------ |
| u    | number | 가로(u) 반복 배율. |
| v    | number | 세로(v) 반복 배율. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 로드되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getEditTerrain().setBottomTextureTilingScale(10.0, 10.0);
```

{% endtab %}
{% endtabs %}

### setSlopeTextureTilingScale(u, v) → boolean

> 성절토 사면(옆면) 텍스처의 반복 출력(타일링) 배율을 설정합니다.
>
> 1.0보다 큰 값을 입력하면 설정한 텍스처가 해당 배율만큼 반복 출력됩니다.
>
> API 호출 이후 생성되는 성절토 객체부터 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description        |
| :--- | :----- | :------------------ |
| u    | number | 가로(u) 반복 배율. |
| v    | number | 세로(v) 반복 배율. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 로드되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getEditTerrain().setSlopeTextureTilingScale(10.0, 10.0);
```

{% endtab %}
{% endtabs %}

### setEditFaceColor(options) → boolean

> 성절토 사면(slope), 바닥면(bottom)의 색상을 설정합니다.
>
> options 객체의 각 속성은 [JSColor](../core/jscolor.md)와 동일한 ARGB 형식 객체(`{a, r, g, b}`) 또는 Hex 코드 문자열(`"#(a)(r)(g)(b)"`)로 지정할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                     |
| :------ | :----- | :------------------------------------------------------------------------------------------------ |
| options | object | `slope`(사면 색상, 선택), `bottom`(바닥면 색상, 선택) 속성을 포함하는 옵션 객체. 두 속성 모두 생략 가능하며, 생략된 속성의 색상은 변경되지 않습니다. |

-   Return
    -   true: 지도가 로드된 경우 항상 true 반환(입력한 옵션에 유효한 속성이 없어도 true).
    -   false: 지도가 로드되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getEditTerrain().setEditFaceColor({
    slope: { a: 255, r: 120, g: 80, b: 40 },
    bottom: "#FF553311",
});
```

{% endtab %}
{% endtabs %}
