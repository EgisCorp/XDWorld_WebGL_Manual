---
description: 좌표계 변환 계산 API를 제공합니다.
---

# JSProjection

Module getProjection API로 생성할 수 있습니다.

```javascript
var projection = Module.getProjection();
```

## getCoordCount() → number

> 사용 가능한 좌표계 리스트 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * 사용 가능한 좌표계 리스트 개수
  
* Code
```
var coordList = Module.getProjection();
var coordCount = coordList.getCoordCount();
```
{% endtab %}
{% endtabs %}

## getCoordName(number index) → string

> 좌표계 리스트 중 인덱스에 해당하는 좌표 명칭을 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type   | Contents |
| --------- | ------ | -------- |
| index  | number | 좌표계 인덱스 |

* Return
  * 인덱스에 해당하는 좌표 명칭
  
* Code
```
var coordList = Module.getProjection();
var coordName = coordList.getCoordName(2);
```
{% endtab %}
{% endtabs %}

## convertProjection(number sourceProjectionCode, [JSVector2D](../core/jsvector2d.md) position, number targetProjectionCode) → [JSVector2D](../core/jsvector2d.md)

> 좌표 변환을 실행합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter   | Type   | Contents |
| ----------- | ------ | -------- |
| sourceProjectionCode | number | 현재 좌표계 번호 |
| position | [JSVector2D](../core/jsvector2d.md) | 변환할 좌표 |
| targetProjectionCode | number | 변환할 좌표계 번호 |

* Return
  * 변환된 좌표
  
* Code
```
var coordList = Module.getProjection();
var coordName = coordList.convertProjection(13, new Module.JSVector2D(126.876282, 38.387802), 26);
```
{% endtab %}
{% endtabs %}

## convertMercatorToLonLat([JSVector2D](../core/jsvector2d.md) position) → [JSVector2D](../core/jsvector2d.md)

> 메르카토르좌표를 경위도 좌표로 변환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type   | Contents |
| --------- | ------ | -------- |
| position  | [JSVector2D](../core/jsvector2d.md) | 변환할 좌표 |

* Return
  * 변환된 경위도 좌표
  
* Code
```
var coordList = Module.getProjection();
var lonlat = coordList.convertMercatorToLonLat(new Module.JSVector2D(14123803.104017733, 4634355.047472151));
```
{% endtab %}
{% endtabs %}

## convertLonLatToMercator([JSVector2D](../core/jsvector2d.md) position) → [JSVector2D](../core/jsvector2d.md)

> 경위도 좌표를 메르카토르좌표로 변환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter  | Type                            | Contents      |
| ---------- | ------------------------------- | ------------- |
| position  | [JSVector2D](../core/jsvector2d.md) | 변환할 좌표 |

* Return
  * 변환된 메르카토르좌표
  
* Code
```
var coordList = Module.getProjection();
var mercator = coordList.convertLonLatToMercator(new Module.JSVector2D(126.876282, 38.387802));
```
{% endtab %}
{% endtabs %}