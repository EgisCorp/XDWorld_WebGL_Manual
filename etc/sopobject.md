---
description: Object를 생성하는 API를 제공합니다.
---

# SOPObject

Module getAddObject API로 생성할 수 있습니다.

```javascript
var sopObject = Module.getAddObject();
```

## setOverlabTexture\(object imageData, number width, number height\) → boolean

> 지도에 이미지 오버랩할 이미지를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| imageData | object | 이미지 Byte Array |
| width | number | 이미지 가로 크기 |
| height | number | 이미지 세로 크기 |

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_image_overlab
{% endtab %}
{% endtabs %}

## InsertOverlabRTT\(string layername, boolean cutregion\) → boolean

> 지도에 이미지 오버랩합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| layername | string | 레이어 이름 |
| cutregion | boolean | 지형 성절토 유무  |

* Detail
  * layername : 객체를 생성할 레이어의 이름
  * cutregion
    * true : 오버랩 영역을 성절토 합니다.
    * false : 오버랩 영역을 성절토하지 않습니다.
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_image_overlab
{% endtab %}
{% endtabs %}

## Add3DPoint\(string layername, string key, number lon, number lat, number alt, object imageData, number width, number height, string text\)

> 지도에 3D POI를 생성합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| layername | string | 레이어 이름 |
| key | string | 객체 key |
| lon | number | 경도 |
| lat | number | 위도 |
| alt | number | 고도 |
| imageData | object | 이미지 Byte Array |
| width | number | 이미지 가로 크기 |
| height | number | 이미지 세로 크기 |
| text | string | POI에 표시할 글자 |

* Detail
  * layername : 객체를 생성할 레이어의 이름
  * key : 생성할 POI key
  * lon : POI의 경도
  * lat : POI의 위도
  * alt : POI의 고도
  * text : POI에 표시할 글자

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_image_overlab
{% endtab %}
{% endtabs %}