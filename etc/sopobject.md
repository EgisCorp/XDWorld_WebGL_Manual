---
description: Object를 생성하는 API를 제공합니다.
---

# SOPObject

> Module.getAddObject API 생성.

```javascript
var sopObject = Module.getAddObject();
```

### Add3DPoint(layername, string key, number lon, number lat, number alt, object imageData, number width, number height, string text\)

> 지도에 3D POI를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| layername | string | 객체를 생성할 레이어 명칭.|
| key | string | POI 생성 객체 명칭. |
| lon | number | POI 생성 경도 위치. |
| lat | number | POI 생성 위도 위치. |
| alt | number | POI 생성 고도 위치. |
| imageData | object | 이미지 Byte Array |
| width | number | 이미지 가로 크기 |
| height | number | 이미지 세로 크기 |
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