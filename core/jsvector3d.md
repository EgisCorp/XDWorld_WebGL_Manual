---
description: 3차원 좌표을 정의합니다.  
---

# JSVector3D
new Module.JSVector3D() 로 생성합니다.

```text
var position = new Module.JSVector3D(129.128265, 35.171834, 100.0);
```
```text
var position = new Module.JSVector3D();
```

## properties
| name | Type | Contents |
| :--- | :--- | :--- |
| Longitude | number | 경도 |
| Latitude | number | 위도 |
| Altitude | number | 고도 |

## new Module.JSVector3D\(number longitude, number latitude, number altitude\) → [JSVector3D](jsvector3d.md)
> x, y 값을 사용해 새로운 2차원 좌표 객체를 생성합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| longitude | number | 경도 |
| latitude | number | 위도 |
| altitude | number | 고도 |
* Return : 2차원 좌표 객체 [JSVector3D](jsvector3d.md)
{% endtab %}
{% endtabs %}

## new Module.JSVector3D\(\) → [JSVector3D](jsvector3d.md)
> 새로운 3차원 좌표 객체를 생성합니다.
> 경도, 위도 고도 속성 값은 0으로 초기화 됩니다.
{% tabs %}
{% tab title="Information" %}
* Return : 2차원 좌표 객체 [JSVector3D](jsvector3d.md)
{% endtab %}
{% endtabs %}