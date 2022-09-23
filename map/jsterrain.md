---
description: 지형 설정 및 제어 기능 API.
---

# JSTerrain

> Module.getTerrain API 생성.

```javascript
var map = Module.getTerrain();
```

### makeTerrainElevationCellData(option) → string

> 입력 정점 좌표를 기준으로 Grid Cell 데이터 생성 및 반환.
>
> argument 변수로 GRID 데이터 생성 후 정보 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| option | [JSTerrain.GridOption](jsterrain.md#jsterrain.gridoption) | WMS 요청 속성 정보. |

* Return
  * .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
  * .name : 동작 API 명칭.
  * .return : API 반환 정보 ( [JSTerrain.GridData](jsterrain.md#jsterrain.griddata) : 정상적인 반환값, 문자열 : 실패 에러 코드 ).

{% endtab %}

{% tab title="Template" %}
```javascript
let point = new Module.JSVec3Array();
	point.push(new Module.JSVector3D(127.01969238371277, 37.56514815604788, 24.40620245039463));
	point.push(new Module.JSVector3D(127.01962748647728, 37.56392380491751, 25.515124042518437));
	point.push(new Module.JSVector3D(127.02194230953037, 37.56375530181643, 33.266184841282666));
	point.push(new Module.JSVector3D(127.02220846619382, 37.56494396175599, 26.32035342976451));

let parameter = {
	coordinates: {
		style: "JSVector3D",
		coordinate: point,
	},
	vertical: 10,
	horizontal: 10,
}
let result = Module.getTerrain().makeTerrainElevationCellData(parameter);
```
{% endtab %}
{% endtabs %}


### Type Definitions

#### JSTerrain.GridOption

> Grid 기본 설정 옵션.

| Name | Type | Attributes | Default | Description |
| :--- | :--- | :- | :- | :--- |
| option | [coordinates Type](tag-list.md#coordinate-type-list) |  |  | 분석 영역 경위도 좌표 목록, 좌표 목록 타입 설정. |
| vertical | number | optional | 5 | Grid를 구성하는 Cell 세로 길이(단위 : m). |
| horizontal | number | optional | 5 | Grid를 구성하는 Cell 가로 길이(단위 : m). |

#### JSTerrain.GridData

> Grid 반환 정보.

| Name | Type | Description |
| :--- | :-- | :--- |
| min | [JSVector2D](../core/jsvector2d.md) | Grid 좌하단 경위도 좌표. |
| max | [JSVector2D](../core/jsvector2d.md) | Grid 우상단 경위도 좌표. |
| center | [JSVector2D](../core/jsvector2d.md) | Grid 중심 경위도 좌표. |
| vertical | number | Grid를 구성하는 Cell 세로 길이(단위 : m). |
| verticalCount | number | Grid를 구성하는 Cell 세로 개수. |
| horizontal | number | Grid를 구성하는 Cell 가로 길이(단위 : m). |
| horizontalCount | number | Grid를 구성하는 Cell 가로 개수. |
| cells | [JSTerrain.CellData](jsterrain.md#jsterrain.celldata) | Grid를 구성하는 Cell 정보 배열. |

#### JSTerrain.CellData

> Grid를 구성하는 Cell 데이터 정보.

| Name | Type | Description |
| :--- | :-- | :--- |
| type | boolean | 분석 영역 포함 유무. |
| elevation | number | Cell 중심 경위도 좌표의 해발고도. |
| min | [JSVector2D](../core/jsvector2d.md) | Cell 좌하단 경위도 좌표. |
| max | [JSVector2D](../core/jsvector2d.md) | Cell 우상단 경위도 좌표. |
| center | [JSVector2D](../core/jsvector2d.md) | Cell 중심 경위도 좌표. |