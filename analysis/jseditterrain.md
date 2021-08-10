---
description: 지형 편집을 위한 API를 제공합니다.
---

# JSEditTerrain

## clear\(\) → boolean
> 지형 편집을 초기화 합니다.
{% tabs %}
{% tab title="Parameter" %}
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit
{% endtab %}
{% endtabs %}

## create\([CJSVec3Array](CJSVec3Array.md) pointlist, number height, number angle\) → boolean
> 지형 성절토를 실행합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| pointlist | [CJSVec3Array](CJSVec3Array.md) | 성절토 영역 |
| height | number | 성절토할 높이 |
| angle | number | 성절토할 사면 각도 |
* Detail
  * pointArray : ([JSVector3D](JSVector3D.md), [JSVector3D](JSVector3D.md), ...) 성절토 좌표 리스트 배열
  * height : 설정한 높이로 지형을 성절토 합니다.
  * angle : 설정한 각도로 지형 사면각을 설정합니다.
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit
{% endtab %}
{% endtabs %}

## createBoundary\([CJSVector2D](CJSVector2D.md) min, [CJSVector2D](CJSVector2D.md) max, number height, number angle\) → boolean
> 지형 성절토를 실행합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| min | [CJSVector2D](CJSVector2D.md) | 성절토 영역 좌하단 |
| max | [CJSVector2D](CJSVector2D.md) | 성절토 영역 우상단 |
| height | number | 성절토할 높이 |
| angle | number | 성절토할 사면 각도 |
* Detail
  * min : 성절토할 영역의 좌하단 좌표
  * max : 성절토할 영역의 우상단 좌표
  * height : 설정한 높이로 지형을 성절토 합니다.
  * angle : 설정한 각도로 지형 사면각을 설정합니다.
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit
{% endtab %}
{% endtabs %}

## setEditFaceColor\(val imageData, number width, number height, boolean type\) → boolean
> 지형 성절토시 바닥면, 사면 텍스쳐를 설정합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| imageData | val | 텍스쳐로 사용할 이미지 Byte Array |
| width | number | 이미지 가로 크기 |
| height | number | 이미지 세로 크기 |
| type | boolean | 바닥면, 사면 구분 값 |
* Detail
  * type
    * false : 사면 텍스쳐로 설정합니다.
    * true : 바닥면 텍스쳐로 설정합니다.
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_terrain_edit
{% endtab %}
{% endtabs %}