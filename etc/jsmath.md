---
description: 수학적 알고리즘 처리를 위한 API 입니다.
---

# JSMath

> Module.getMath() API를 생성합니다.

```javascript
var math = Module.getMath();
```

### convertBezierCurve(options) → [JSVec3Array](../core/JSVec3Array.md)

> 경위도 좌표 목록 정보를 통해 베지어 곡선이 적용된 좌표 목록 반환합니다..
>
> argument 변수로 좌표 변환 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                               | Description          |
| ------ | -------------------------------------------------- | -------------------- |
| option | [JSMath.BezierCurve](jsmath.md#jsmath.beziercurve) | 변환 좌표 속성 정보. |

-   Return
    -   [JSVec3Array](../core/JSVec3Array.md): 변환 성공
    -   size 0: 변환 실패.
-   Sample
    -   function createCurvedLine 참조.
    -   [Sandbox_LineInterpolation(Curved)](https://sandbox.egiscloud.com/code/main.do?id=object_line_interpolate_curved)

{% endtab %}
{% tab title="Template" %}

```javascript
var vertices = [];

vertices.push([lon, lat, alt]);
vertices.push([lon, lat, alt]);
vertices.push([lon, lat, alt]);

let curve_pos = {
    coordinate: vertices,
    style: "XYZ",
};
```

{% endtab %}
{% endtabs %}

### convertBeZierLine(options) → object

> 시작, 끝 경위도 좌표도 기준으로 베지어 곡선 좌표 목록을 반환합니다.
>
> argument 변수로 좌표 변환 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                             | Description          |
| ------ | ------------------------------------------------ | -------------------- |
| option | [JSMath.BezierLine](jsmath.md#jsmath.bezierline) | 변환 좌표 속성 정보. |

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name : 동작 API 명칭.
    -   .return : API 반환 정보 ( object : 정상적인 반환값, 문자열 : 실패 에러 코드 ).
-   Sample
    -   function createBallPath 참조
    -   [Sandbox_ParabolicLine](https://sandbox.egiscloud.com/code/main.do?id=object_line_arc)

{% endtab %}
{% tab title="Template" %}

```javascript
let parameters = {
    start: new Module.JSVector3D(127.94080035885989, 36.336424549396064, 306.52637346833944),
    end: new Module.JSVector3D(127.9419239501012, 36.33615414434727, 300.5711971661076),
    detail: 100,
    height: 330,
    percent: 70,
};
```

{% endtab %}
{% endtabs %}

### calculationSlopeAnalysis(options) → object

> 3\*3(0 배열 좌상단 9 배열 우하단) 배열값을 통한 경사 분석 결과 반환.
>
> argument 변수로 좌표 변환 옵션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                               | Description         |
| ------ | -------------------------------------------------- | ------------------- |
| option | [JSMath.SlopeOption](jsmath.md#jsmath.slopeoption) | 경사분석 속성 정보. |

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name : 동작 API 명칭.
    -   .return : API 반환 정보 ( object : 정상적인 반환값, 문자열 : 실패 에러 코드 ).

{% endtab %}
{% tab title="Template" %}

```javascript
let slop = {
    type: "TERRAIN_DIRECTION_ANGLE",
    array: [101, 92, 85, 101, 92, 85, 101, 91, 84],
    vertical: 10,
    horizontal: 10,
};
let result = Module.getMath().calculationSlopeAnalysis(slop);
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSMath.BezierCurve

> 경위도 좌표 목록 정보를 베지어 곡선 변환 옵션.

| Name   | Type                                                 | Attributes | Default | Description                            |
| ------ | ---------------------------------------------------- | ---------- | ------- | -------------------------------------- |
| option | [coordinates Type](tag-list.md#coordinate-type-list) |            |         | 경위도 좌표 목록, 좌표 목록 타입 설정. |

#### JSMath.BezierLine

> 경위도 좌표 목록 정보를 포물선 곡선 변환 옵션.

| Name    | Type                                | Attributes | Default | Description                                                   |
| ------- | ----------------------------------- | ---------- | ------- | ------------------------------------------------------------- |
| start   | [JSVector3D](../core/jsvector3d.md) |            | 500     | 직선 경위도 시작 위치.                                        |
| end     | [JSVector3D](../core/jsvector3d.md) |            | 10      | 직선 경위도 끝 위치.                                          |
| detail  | number                              | optional   | 50      | 곡선 생성 보간 점 수.                                         |
| height  | number                              | optional   | 100     | 곡선 최대 높이.                                               |
| percent | number                              | optional   | 50      | 시작 위치 0%, 끝 위치 100% 기준으로 곡선 최대 높이 지점 설정. |

#### JSMath.SlopeOption

> 경사 분석 설정 옵션.

| Name       | Type   | Attributes | Default | Description                                                               |
| ---------- | ------ | ---------- | ------- | ------------------------------------------------------------------------- |
| type       | string |            |         | 경사분석 옵션(TERRAIN_ANGLE, TERRAIN_DIRECTION, TERRAIN_DIRECTION_ANGLE). |
| array      | array  |            |         | 경사분석을 위한 [3*3] 해발고도 배열.                                      |
| vertical   | number | optional   | 5       | 경사도 분석에 필요한 Cell 세로 길이(단위 : m).                            |
| horizontal | number | optional   | 5       | 경사도 분석에 필요한 Cell 세로 길이(단위 : m).                            |
