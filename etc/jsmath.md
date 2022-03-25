---
description: 수학적 알고리즘 처리를 위한 API
---

# JSAntenna

Module getMath API로 생성할 수 있습니다.

```javascript
var math = Module.getMath();
```

## convertBezierCurve\(object options \) → [JSVec3Array](../core/JSVec3Array.md)

> 경위도 좌표 목록 정보를 통해 베지어 곡선이 적용된 좌표 목록 반환.
> 
> argument 변수로 정점 리스트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| option | object | 변환 좌표 속성 정보. |

| option\_tag | Type | Contents |
| :--- | :--- | :--- |
| coordinate | object | 정점 좌표 목록. |
| style | string | 좌표 리스트 type. |

* Detail
  * coordinate : 정점 좌푝 목록. 포맷은 style 속성에 맞춰 적용.
  * style : coordinates 배열 포맷을 맞춰 입력합니다.
      * style="XY" → \[\[x, y\], \[x, y\], ...\]
      * style="XYZ" → \[\[x, y, z\], \[x, y, z\], ...\]
      * style="XYZARRAY" → \[x, y, z, x, y, z\], ...\]
      * style="JSVector3D" → \[JSVector3D, JSVector3D, ...\]

* Return
  * 성공 : [JSVec3Array](../core/JSVec3Array.md) 베지어 알고리즘 적용 좌표 목록 반환.
  * 실패 : [JSVec3Array](../core/JSVec3Array.md) 사이즈 0 반환.

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_interpolate_curved
{% endtab %}
{% endtabs %}

## convertBeZierLine\(object options \) → object

> 경위도 시작, 끝 위치 기준으로 베지어 곡선 좌표 목록 반환.
> 
> argument 변수로 정점 리스트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| option | object | 변환 좌표 속성 정보. |

| option\_tag | Type | Contents |
| :--- | :--- | :--- |
| start | [JSVector3D](../core/jsvector3d.md) | 직선 경위도 시작 위치. |
| end | [JSVector3D](../core/jsvector3d.md) | 직선 경위도 끝 위치. |
| detail | number | 곡선 생성 본간 점 수. |
| height | number | 곡선 최대 높이. |
| percent | number | 최대 높이 비율. |

* Detail
  * detail : 값이 클수록 곡선에 가까운 형태로 좌표 생성.
  * percent : 시작 위치 0%, 끝 위치 100%를 기준으로 곡선 최대 높이 위치 비율을 설정.  
  
* Return
  * .result : API 성공 유무 상태 \( 1 : 성공,  0 : 실패 \)
  * .name : 동작 API 명칭
  * .return : API 반환 정보 \( object : 정상적인 반환값, 문자열 : 실패 에러 코드 \)

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_arc
{% endtab %}
{% endtabs %}


