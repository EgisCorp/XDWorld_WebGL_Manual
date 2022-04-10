---
description: 지도 내 지형 편집 기능 설정 API.
---

# JSEditTerrain

> Module.getEditTerrain API 생성.

```javascript
var editTerrain = Module.getEditTerrain();
```

### clear() → boolean

> 지형 편집을 초기화

{% tabs %}
{% tab title="Information" %}
* Sample
  * function clearEditTerrain 참조.
  * [샌드박스\_지형 성절토](http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### create(coordinates, height, angle) → boolean

> 분석 영역 기준으로 지형 성절토를 수행

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec3Array](../core/jsvec3aray.md) | 성절토 분석여역 경위도 좌표 목록. |
| height | number | 성절토할 기준 높이 (기준 : 해발고도, 단위 : 미터)|
| angle | number | 성절토할 사면 각도 (단위 : degree ) |

* Sample
  * function createEditTerrain 참조.
  * [샌드박스\_지형 성절토](http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### createBoundary(min, max, height, angle) → boolean

> 분석 범위를 기준으로 지형 성절토를 수행

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| min | [JSVector2D](../core/jsvector2d.md) | 성절토 영역 좌하단 |
| max | [JSVector2D](../core/jsvector2d.md) | 성절토 영역 우상단 |
| height | number | 성절토할 기준 높이 (기준 : 해발고도, 단위 : 미터)|
| angle | number | 성절토할 사면 각도 (단위 : degree ) |

* Sample
  * function createEditTerrain 참조.
  * [샌드박스\_지형 성절토](http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setEditFaceColor(data, width, height, type) → boolean

> 지형 성절토시 바닥면, 사면 텍스쳐를 설정
> 
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| data | object | 이미지 바이너리 데이터. |
| width | number | 이미지의 너비. |
| height | number | 이미지의 높이. |
| type | boolean | 바닥면, 사면 구분 (true : 바닥면, false : 사면) |

* Sample
  * function createEditTerrain 참조.
  * [샌드박스\_지형 성절토](http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}