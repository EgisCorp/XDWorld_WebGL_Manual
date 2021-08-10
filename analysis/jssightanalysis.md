---
description: 레이어 분석을 위한 API를 제공합니다.
---

# JSSightAnalysis

## GetObjectPositionsOnPath\( path, searchBuffer, verticalScope, targetLayer \) → string

> 지정된 경로에서 객체까지의 거리, 위치를 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| path | [JSVec3Array](../core/jsvec3array.md) | 경로 |
| searchBuffer | number | 수평 버퍼 크기 |
| verticalScope | number | 수직 버퍼 크기 |
| targetLayer | [JSLayer](../layer/jslayer.md) | 분석할 레이어 |

* Detail
  * path : \([JSVector3D](../core/jsvector3d.md), [JSVector3D](../core/jsvector3d.md), ...\) 분석할 경로 배열
  * searchBuffer : 수평 버퍼 크기. 값이 클수록 수평으로 넓은 범위의 객체를 분석합니다.
  * verticalScope : 수직 버퍼 크기. 값이 클수록 수직으로 넓은 범위의 객체를 분석합니다.
  * targetLayer : 분석할 객체가 속하는 레이어
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_line\_path\_distance](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
{% endtab %}
{% endtabs %}

