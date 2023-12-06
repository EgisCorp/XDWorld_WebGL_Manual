---
description: 인스턴스 드로우 객체 생성 및 수정.
---

# JSInstanceObject

> Module.createInstanceObject API 생성.

```javascript
let instanceObject = Module.createInstanceObject("object");
```

## Function

### getIntersectObjects(parameter) → error

> 인스턴스 오브젝트와 입력받은 라인과 겹치는 배열항목 반환.
> 
> 확인할 라인을 좌표 목록으로 정의하고, parameter 변수에 담아 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ---- | -------- |
| parameter | [JSInstanceObject.IntersectObjectsParameter](jsinstanceobject.md#jsinstanceobject.intersectobjectsparameter) | 겹침 유무 확인 정보.   |

* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSInstanceObject.getOverlappingObjects" 고정.</br> |
  | return | array(number) or string | API 결과 반환.<br>성공시 겹치는 인스턴스 오브젝트의 인덱스 목록을 array로 반환.</br><br>실패시 오류 메시지를 string으로 반환.</br><br>- "Unusual input." : parameter 자체가 유효하지 않은 경우.</br><br>- "error"가 앞에 붙은 문자열 : parameter의 "coordinates" 속성이 유효하지 않은 경우(자세한 사항은 메시지 참조).</br><br>- "Object Size 0" : 충돌하는 인스턴스 오브젝트가 없는 경우.</br> |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSInstanceObject.IntersectObjectsParameter
| Name | Type | Default | Description |
| --- | --- | --- | --- |
| objectType | string | "line" | 입력받은 오브젝트의 타입 정의. |
| coordinates | [JSInstanceObject.IntersectObjectsParameter.coordinates](jsinstanceobject.md#jsinstanceobject.intersectobjectsparameter.coordinates) |  | 위도. |

#### JSInstanceObject.IntersectObjectsParameter.coordinates
| Name | Type | Description |
| --- | --- | --- |
| style | string | 좌표 변환 타입. 아래 네 가지에 해당되지 않는 경우, 오류 발생.<br>XY : 경위도 배열 값 [x, y], [x, y]</br><br>XYZ : 경위고도 배열 값 [x, y, z], [x, y, z]</br><br>XYZARRAY : 경위고도 배열 값 [x, y, z, x, y, z]</br><br>JSVector3D : 경위고도 JSVec3Array 배열 값</br> |
| coordinates | number | 좌표 목록. |

