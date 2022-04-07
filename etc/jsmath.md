---
description: 수학적 알고리즘 처리를 위한 API
---

# JSMath

> Module.getMath API 생성.

```javascript
var math = Module.getMath();
```

### convertBezierCurve(options) → [JSVec3Array](../core/JSVec3Array.md)

> 경위도 좌표 목록 정보를 통해 베지어 곡선이 적용된 좌표 목록 반환.
>
> argument 변수로 정점 리스트 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type                                               | Description  |
| ------ | -------------------------------------------------- | ------------ |
| option | [JSMath.BezierCurve](jsmath.md#jsmath.beziercurve) | 변환 좌표 속성 정보. |

* Return
  * 성공 : [JSVec3Array](../core/JSVec3Array.md) 베지어 알고리즘 적용 좌표 목록 반환.
  * 실패 : [JSVec3Array](../core/JSVec3Array.md) 사이즈 0 반환.
* Sample
  * function createCurvedLine 참조.
  * [샌드박스\_라인보간(곡선)](http://sandbox.dtwincloud.com/code/main.do?id=object\_line\_interpolate\_curved)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### convertBeZierLine(options) → object

> 경위도 시작, 끝 위치 기준으로 베지어 곡선 좌표 목록 반환.
>
> argument 변수로 정점 리스트 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type                                             | Description  |
| ------ | ------------------------------------------------ | ------------ |
| option | [JSMath.BezierLine](jsmath.md#jsmath.BezierLine) | 변환 좌표 속성 정보. |

* Return
  * .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
  * .name : 동작 API 명칭.
  * .return : API 반환 정보 ( object : 정상적인 반환값, 문자열 : 실패 에러 코드 ).
* Sample
  * function createBallPath 참조
  * [샌드박스\_포물선라인](http://sandbox.dtwincloud.com/code/main.do?id=object\_line\_arc)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSMath.BezierCurve

> 경위도 좌표 목록 정보를 베지어 곡선 변환 옵션.

| Name       | Type                                                  | Attributes | Default | Description |
| ---------- | ----------------------------------------------------- | ---------- | ------- | ----------- |
| coordinate | string                                                |            |         | 정점 좌표 목록.   |
| style      | [좌표 스타일 타입.](type-list.md#coordinate-style-type-list) |            |         | 좌표 스타일 타입.  |

#### JSMath.BezierLine

> 태풍 영향권 오브젝트 생성 옵션

| Name    | Type                                | Attributes | Default | Description                              |
| ------- | ----------------------------------- | ---------- | ------- | ---------------------------------------- |
| start   | [JSVector3D](../core/jsvector3d.md) |            | 500     | 직선 경위도 시작 위치.                            |
| end     | [JSVector3D](../core/jsvector3d.md) |            | 10      | 직선 경위도 끝 위치.                             |
| detail  | number                              | optional   | 50      | 곡선 생성 보간 점 수.                            |
| height  | number                              | optional   | 100     | 곡선 최대 높이.                                |
| percent | number                              | optional   | 50      | 시작 위치 0%, 끝 위치 100% 기준으로 곡선 최대 높이 지점 설정. |
