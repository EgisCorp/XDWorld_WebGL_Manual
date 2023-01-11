---
description: 화살표 3차원 모델 오브젝트 생성 및 설정 API.
---

# JSArrow

> Module.CreateArrow API 생성.

```javascript
var object = Module.CreateArrow("ID");
```

### Create(position, pan, tilt, distance, radius, head\_rate, arrow\_radius, color) → boolean

> 화살표 3차원 모델 오브젝트 생성.
>
> pan 입력 값에 따른 회전 정보 0, 360(북쪽), 90(동쪽), 180(남쪽), 270(서쪽).
>
> tilt 입력 값에 따른 회전 정보 0(정면), tilt<0(상단), tilt>0(하단).

{% tabs %}
{% tab title="Information" %}
| Name          | Type                                | Description   |
| ------------- | ----------------------------------- | ------------- |
| position      | [JSVector3D](../core/jsvector3d.md) | 화살표 시작 경위도.   |
| pan           | number                              | 화살표 Y축 회전 설정. |
| tilt          | number                              | 화살표 X축 회전 설정. |
| distance      | number                              | 화살표 전체 길이 설정. |
| radius        | number                              | 화살대 굵기 지정.    |
| head\_rate    | number                              | 화살촉 비율.       |
| arrow\_radius | number                              | 화살촉 굵기 지정.    |
| color         | [JSColor](../core/jscolor.md)       | 화살표 색상 지정.    |

* Return
  * true : 오브젝트 생성 성공.
  * false : 오브젝트 생성 실패.
* Sample
  * function init 참조.
  * [샌드박스\_화살표(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object\_arrow)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}
