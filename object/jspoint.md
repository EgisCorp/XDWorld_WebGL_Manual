---
description: 포인트 오브젝트 설정 및 반환 API를 제공합니다.
---

# JSPoint

Module createPoint API로 생성할 수 있습니다.

```text
var object = Module.createPoint("newObject");
```

## setFontStyle\(string font_name, number font_size, number font_weight, [JSColor]([)JSColor.md) text_fill_color, [JSColor](JSColor.md) text_outline_color\)
> POI 텍스트 스타일 (폰트, 크기, 굵기 및 색상 등)을 설정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| font_name | string | 폰트 이름 |
| font_size | number | 텍스트 크기 |
| font_weight | number | 텍스트 굵기 |
| text_fill_color | [JSColor](JSColor.md) | 텍스트 색상 |
| text_outline_color | [JSColor](JSColor.md) | 텍스트 외곽 색상 |
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance
{% endtab %}
{% endtabs %}

## setImage\(array image_pixels, number image_width, number image_height\) → boolean
> POI 이미지를 설정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| image_pixels | array | 이미지 픽셀 값 배열 |
| image_width | [Collection](Collection.md) | 폴리곤 Part 리스트 |
| image_height | [JSVec2Array](JSVec2Array.md) | 폴리곤 uv 좌표 리스트  |
* Detail
  * image_width : 1 이상 값으로 설정
  * image_height : 1 이상 값으로 설정
* Return
  * 성공 : true
  * 실패 : false
    - image_width, image_height 값이 0
    - image_pixels 가 빈 배열
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_point
{% endtab %}
{% endtabs %}

## setPosition\([JSVector3D](JSVector3D.md) positiont\) → boolean
> POI 위치를 지정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| vertex_list | [JSVector3D](JSVector3D.md) | POI 위치 |
* Return
  * 성공 : true
  * 실패 : false
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_point
{% endtab %}
{% endtabs %}

## setPositionLine\(number line_length, [JSColor](JSColor.md) color\) → boolean
> 지면과 수직한 라인을 지정한 길이만큼 보이도록 설정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| line_length | number | POI 수직 라인 색상 |
| color | [JSColor](JSColor.md) | POI 수직 라인 길이 |
* Detail
  * line_length : 0이 아닌 양수 값으로 입력합니다.
* Return
  * 성공 : true
  * 실패 : false
    - line_length <= 0.0
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_point_line
{% endtab %}
{% endtabs %}

## setRenderToTerrainTexture\(boolean set\) → boolean
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
  * http://sandbox.dtwincloud.com/code/main.do?id=object_point_rtt
{% endtab %}
{% endtabs %}

## setText\(string text\) → boolean
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
  * http://sandbox.dtwincloud.com/code/main.do?id=object_point
{% endtab %}
{% endtabs %}