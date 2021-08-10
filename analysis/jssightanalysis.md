---
description: 레이어 분석을 위한 API를 제공합니다.
---

# JSSightAnalysis

## GetObjectPositionsOnPath\([CJSVec3Array](CJSVec3Array.md) path, number searchBuffer, number verticalScope, [CJSLayer](CJSLayer.md) targetLayer\) → string
> 지정된 경로에서 객체까지의 거리, 위치를 반환합니다.
{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| path | [CJSVec3Array](CJSVec3Array.md) | 경로 |
| searchBuffer | number | 수평 버퍼 크기 |
| verticalScope | number | 수직 버퍼 크기 |
| targetLayer | [CJSLayer](CJSLayer.md) | 분석할 레이어 |
* Detail
  * path : ([JSVector3D](JSVector3D.md), [JSVector3D](JSVector3D.md), ...) 분석할 경로 배열
  * searchBuffer : 수평 버퍼 크기. 값이 클수록 수평으로 넓은 범위의 객체를 분석합니다.
  * verticalScope : 수직 버퍼 크기. 값이 클수록 수직으로 넓은 범위의 객체를 분석합니다.
  * targetLayer : 분석할 객체가 속하는 레이어
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance
{% endtab %}
{% endtabs %}