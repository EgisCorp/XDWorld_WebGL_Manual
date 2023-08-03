---
description: 인덱스 맵 설정 및 제어 기능 API.
---

# JSIndexMap3D

> Module.getIndexMap API 생성.

```javascript
var map = Module.getIndexMap();
```

## Function

### setCameraTilt(tilt)

> 인덱스맵 카메라 옵션 설정.
>
> 카메라 기울기 변경, 단위 Degree

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| tilt | number | 카메라 tilt. |

{% endtab %}

{% tab title="Template" %}

```javascript
var indexMap3D = Module.getIndexMap();
indexMap3D.setCameraTilt(89.9);
indexMap3D.setVisible(true);
```

{% endtab %}
{% endtabs %}

### setDistanceMinMax(min, max)

> 인덱스맵 카메라 옵션 설정.
>
> 보이는 지점으로 부터 카메라까지의 최소, 최대 거리 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ------ | -------- |
| min | number | 카메라 최소 시야거리(m단위). |
| max | number | 카메라 최소 시야거리(m단위). |

{% endtab %}

{% tab title="Template" %}

```javascript
var indexMap3D = Module.getIndexMap();
indexMap3D.setDistanceMinMax(50, 3000);
indexMap3D.setVisible(true);
```

{% endtab %}
{% endtabs %}
