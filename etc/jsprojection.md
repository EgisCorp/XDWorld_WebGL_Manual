---
description: 좌표계 변환 계산 API를 제공합니다.
---

# JSProjection

> Module.getProjection API 생성.

```javascript
var projection = Module.getProjection();
```

### getCoordCount() → number

> 사용 가능한 좌표계 리스트 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * 사용 가능한 좌표계 리스트 개수

{% endtab %}

{% tab title="Template" %}
```javascript
var coordList = Module.getProjection();
var coordCount = coordList.getCoordCount();
```
{% endtab %}
{% endtabs %}

### getCoordName(index) → string

> 좌표계 리스트 중 인덱스에 해당하는 좌표 명칭을 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ------ | -------- |
| index  | number | 좌표계 인덱스 |

* Return
  * 인덱스에 해당하는 좌표 명칭
{% endtab %}

{% tab title="Template" %}
```javascript
var coordList = Module.getProjection();
var coordName = coordList.getCoordName(2);
```
{% endtab %}
{% endtabs %}

### convertProjection(source, position, target) → [JSVector2D](../core/jsvector2d.md)

> 좌표 변환을 실행합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----------- | ------ | -------- |
| source | [좌표 목록.](type-list.md#coordinate-type-list) | 원본 좌표계 번호 |
| position | [JSVector2D](../core/jsvector2d.md) | 변환할 좌표 |
| target | [좌표 목록.](type-list.md#coordinate-type-list) | 변환할 좌표계 번호 |

* Return
  * 변환된 좌표
{% endtab %}

{% tab title="Template" %}
```javascript
var coordList = Module.getProjection();
var coordName = coordList.convertProjection(13, new Module.JSVector2D(126.876282, 38.387802), 26);
```
{% endtab %}
{% endtabs %}

### convertMercatorToLonLat(position) → [JSVector2D](../core/jsvector2d.md)

> 메르카토르좌표를 경위도 좌표로 변환합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ------ | -------- |
| position  | [JSVector2D](../core/jsvector2d.md) | 변환할 좌표 |

* Return
  * 변환된 경위도 좌표
{% endtab %}

{% tab title="Template" %}
```javascript
var coordList = Module.getProjection();
var lonlat = coordList.convertMercatorToLonLat(new Module.JSVector2D(14123803.104017733, 4634355.047472151));
```
{% endtab %}
{% endtabs %}

### convertLonLatToMercator(position) → [JSVector2D](../core/jsvector2d.md)

> 경위도 좌표를 메르카토르좌표로 변환합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---------- | ------------------------------- | ------------- |
| position  | [JSVector2D](../core/jsvector2d.md) | 변환할 좌표 |

* Return
  * 변환된 메르카토르좌표  
{% endtab %}

{% tab title="Template" %}
```javascript
var coordList = Module.getProjection();
var mercator = coordList.convertLonLatToMercator(new Module.JSVector2D(126.876282, 38.387802));
```
{% endtab %}
{% endtabs %}