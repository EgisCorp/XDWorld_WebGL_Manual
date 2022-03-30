---
description: 화살표 3차원 모델 오브젝트 생성 및 설정 API.
---

# JSArrow

Module CreateArrow API로 생성할 수 있습니다.

```javascript
var object = Module.CreateArrow("ID");
```

## createViewFrustum\([JSVector3D](JSVector3D.md) position, number pan, number tilt, number distance, number radius, number arrow_radius, [JSColor](../core/jscolor.md) color\)

> 화살표 3차원 모델 오브젝트 생성.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector3D](JSVector3D.md) | 화살표 시작 경위도 |
| pan | number | 화살표 Y축 회전 설정 |
| tilt | number | 화살표 X축 회전 설정 |
| distance | number | 화살표 전체 길이 설정 |
| radius | number | 화살대 굵기 지정 |
| arrow_radius | number | 화살촉 굵기 지정 |
| color | [JSColor](../core/jscolor.md) | 화살표 색상 지정 |

* Detail
  * pan : 0(북쪽), 90(동쪽), 180(남쪽), 270(서쪽)으로 방향 전환.
  * tilt : 0(정면), tilt&lt;0(상단), tilt&gt;0(하단) 방향 전환.  
  
* Return
  * TRUE : 오브젝트 생성 성공
  * FALSE : 오브젝트 생성 실패
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_arrow
{% endtab %}
{% endtabs %}