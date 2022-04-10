---
description: Object를 생성하는 API를 제공합니다.
---

# SOPObject

> Module.getAddObject API 생성.

```javascript
var sopObject = Module.getAddObject();
```

### Add3DPoint(name, key, lon, lat, alt, data, width, height, text\)

> 지도에 3D POI를 생성합니다.
> 
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 객체를 생성할 레이어 명칭.|
| key | string | POI 생성 객체 명칭. |
| lon | number | POI 생성 경도 위치. |
| lat | number | POI 생성 위도 위치. |
| alt | number | POI 생성 고도 위치. |
| data | object | 이미지 바이너리 데이터. |
| width | number | 이미지의 너비. |
| height | number | 이미지의 높이. |
| text | string | POI에 표시할 글자 |

* Sample
  * function getJudong 참조
  * [샌드박스\_주동길이 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_building_width)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}