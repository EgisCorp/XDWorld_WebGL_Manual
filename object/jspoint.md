---
description: 포인트 오브젝트 설정 및 반환 API를 제공합니다.
---

# JSPoint

Module createPoint API로 생성할 수 있습니다.

```javascript
var object = Module.createPoint("newObject");
```

## setFontStyle\( font\_name, font\_size, font\_weight, text\_fill\_color, text\_outline\_color\)

> POI 텍스트 스타일 \(폰트, 크기, 굵기 및 색상 등\)을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| font\_name | string | 폰트 이름 |
| font\_size | number | 텍스트 크기 |
| font\_weight | number | 텍스트 굵기 |
| text\_fill\_color | JSPolyLineStyle | 텍스트 색상 |
| text\_outline\_color | JSPolyLineStyle | 텍스트 외곽 색상 |

* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_line\_path\_distance](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
{% endtab %}
{% endtabs %}

## setImage\( image\_pixels, image\_width, image\_height \) → boolean

> POI 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| image\_pixels | array | 이미지 픽셀 값 배열 |
| image\_width | number | 이미지 너비 |
| image\_height | number | 이미지 높이 |

* Detail
  * image\_width : 1 이상 값으로 설정
  * image\_height : 1 이상 값으로 설정
* Return
  * 성공 : true
  * 실패 : false
    * image\_width, image\_height 값이 0
    * image\_pixels 가 빈 배열
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_point](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}
{% endtabs %}

## setPosition\( positiont\) → boolean

> POI 위치를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| vertex\_list | [JSVector3D](../core/jsvector3d.md) | POI 위치 |

* Return
  * 성공 : true
  * 실패 : false
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_point](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}
{% endtabs %}

## setPositionLine\( line\_length, color\) → boolean

> 지면과 수직한 라인을 지정한 길이만큼 보이도록 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| line\_length | number | POI 수직 라인 색상 |
| color | [JSColor](../core/jscolor.md) | POI 수직 라인 길이 |

* Detail
  * line\_length : 0이 아닌 양수 값으로 입력합니다.
* Return
  * 성공 : true
  * 실패 : false
    * line\_length &lt;= 0.0
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_point\_line](http://sandbox.dtwincloud.com/code/main.do?id=object_point_line)
{% endtab %}
{% endtabs %}

## setRenderToTerrainTexture\( set \) → boolean

> POI를 RTT 기반으로 지형에 그리도록 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| set | boolean | RTT 렌더링 여부 |

* Return
  * 성공 : true
  * 실패 : false
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_point\_rtt](http://sandbox.dtwincloud.com/code/main.do?id=object_point_rtt)
{% endtab %}
{% endtabs %}

## setText\( text \) → boolean

> POI 텍스트 문자열을 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| string | text | POI 텍스트 |

* Return
  * 성공 : true
  * 실패 : false
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_point](http://sandbox.dtwincloud.com/code/main.do?id=object_point)
{% endtab %}
{% endtabs %}

