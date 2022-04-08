---
description: 지도 내 레이어 분석을 위한 API.
---

# JSSightAnalysis

> Module.getSightAnalysis API 생성.

```javascript
var sightAnalysis = Module.getSightAnalysis();
```

### GetObjectPositionsOnPath(path, searchBuffer, verticalScope, targetLayer) → [JSON](jssightanalysis.md#jssightanalysis.objectonpathresult)

> 지정된 경로에서 객체까지의 거리, 위치를 반환.
>
> 경로에 검색 범위를 바탕으로 범위 내에 존재하는 객체에 대한 경로의 이정 거리 기준으로 분석.
>
> searchBuffer 입력값은 수평 버퍼 크기. 값이 클수록 수평으로 넓은 범위의 객체 분석.
>
> verticalScope 입력값은 수직 버퍼 크기. 값이 클수록 수직으로 넓은 범위의 객체 분석.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| path | [JSVec3Array](../core/jsvec3aray.md) | ([JSVector3D](../core/jsvector3d.md), [JSVector3D](../core/jsvector3d.md), ...) 분석할 경로 배열. |
| searchBuffer | number | 수평 버퍼 크기 |
| verticalScope | number | 수직 버퍼 크기 |
| targetLayer | [JSLayer](../layer/jslayer.md) | 분석할 객체가 속하는 레이어 |

* Return
  * 지정된 경로 진행 중 오브젝트와 수직 방향으로 만나는 지점들의 위치 반환 ([JSON](jssightanalysis.md#jssightanalysis.objectonpathresult))
  
* Sample
  * function 참조.
  * [샌드박스\_경로 분석](http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance)
{% endtab %}

{% tab title="Template" %}
```javascript
let rstjson = "{
	[
		{
			Longitude : 129.2,
			Latitude : 36.8,
			Altitude : 10.2,
			ObjectKey : "Test1",
			Distance : 10,
			Side : "Left"
		},
		{
			Longitude : 129.222,
			Latitude : 36.811,
			Altitude : 13.5,
			ObjectKey : "Test2",
			Distance : 30,
			Side : "Right"
		},
	]	
```
{% endtab %}
{% endtabs %}

#### Type Definitions

###### JSSightAnalysis.ObjectOnPathResult

> GetObjectPositionsOnPath의 분석 결과의 형식 
>
> JSON 구조를 가진 문자열로 반환

| Name         | Type                          | Attributes | Default                 | Description      |
| ------------ | ----------------------------- | ---------- | ----------------------- | ---------------- |
| - | [JSSightAnalysis.ObjectOnPathResult.Position](jssightanalysis.md#jssightanalysis.objectonpathresult.position) | array | | 개별 분석 결과 배열

###### JSSightAnalysis.ObjectOnPathResult.Position

> [JSSightAnalysis.ObjectOnPathResult](jssightanalysis.md#jssightanalysisobjectonpathresult)의 단위 객체 정보

| Name         | Type                          | Attributes | Default                 | Description      |
| ------------ | ----------------------------- | ---------- | ----------------------- | ---------------- |
| Longitude | number | | | 검출된 객체의 경도 |
| Latitude | number | | | 검출된 객체의 위도 |
| Altitude | number | | | 검출된 객체의 높이 |
| ObjectKey | string | | | 검출된 객체의 키값 |
| Distance | number | | | 검출된 객체의 경로상 이정 거리 |
| Side | string | | | 검출된 객체가 경로상 좌측, 우측여부 (좌측 : "Left", 우측 : "Right") |

