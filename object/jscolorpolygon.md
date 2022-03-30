---
description: 그라데이션 폴리곤을 위한 API를 제공합니다.
---

# JSColorPolygon

Module createColorPolygon API로 생성할 수 있습니다.

```javascript
var colorPolygon = Module.createColorPolygon("ID");
```

## SetVerticalPlane([JSVec3Array](../core/jsvec3aray.md) coordinates, [Collection](../core/collection.md) parts, number height, [JSColor](../core/jscolor.md) startColor, [JSColor](../core/jscolor.md) endColor) → boolean

> 폴리곤 수직 벽면 형태를 정의합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| --------- | ---- | -------- |
| coordinates | [JSVec3Array](../core/jsvec3aray.md)  | 폴리곤 정점 정보 |
| parts | [Collection](../core/collection.md)  | 폴리곤 parts 정보 |
| height | number  | 폴리곤 높이 |
| startColor | [JSColor](../core/jscolor.md)  | 그라데이션 시작 색상 |
| endColor | [JSColor](../core/jscolor.md)  | 그라데이션 끝 색상 |

* Detail
```
// 폴리곤 생성
var colorPolygon = Module.createColorPolygon("TEST_VERTICAL_POLYGON");

// 좌표 리스트 생성
var basePositions = [
	[129.12599597147187, 35.17339329004985, 50.0],
	[129.1264736891435, 35.172432534300555, 50.0],
	[129.12705822860582, 35.172119138064076, 50.0],
	[129.12837813524428, 35.17198042514761, 50.0],
	[129.12925806742587, 35.171677294599604, 50.0],
	[129.13014427905534, 35.1712405752301, 50.0],
	[129.13067851056573, 35.170639446735436, 50.0]
];

var coordinates = new Module.JSVec3Array();
var parts = new Module.Collection();

for (var i=0; i<_basePositions.length; i++) {
	coordinates.push( new Module.JSVector3D(_basePositions[i][0], _basePositions[i][1], _basePositions[i][2]) );
}
parts.add(_basePositions.length);

// 폴리곤 수직 벽면 형태 정의
colorPolygon.SetVerticalPlane(coordinates, parts, -50.0, new Module.JSColor(0, 255, 255, 0), new Module.JSColor(255, 255, 0, 0));
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 폴리곤 정점이 2개 이하일 경우
	2\) 폴리곤 parts가 0개일 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_colorpolygon_gradation
{% endtab %}
{% endtabs %}

## SetCullMode(number cullMode) → boolean

> 폴리곤 컬링모드를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| --------- | ---- | -------- |
| cullMode | number  | 폴리곤 컬링모드 |

* Detail
	* cullMode
	* 0, 1: cw, ccw
	* 2: cw
	* 3: ccw

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_colorpolygon_gradation
{% endtab %}
{% endtabs %}

## set(object parameter) → boolean

> 그라데이션 폴리곤을 정의합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type | Contents |
| --------- | ---- | -------- |
| parameter | object  | 그라데이션 폴리곤 설정 |

* Detail
```
// 폴리곤 생성
var colorPolygon = Module.createColorPolygon("TEST_VERTICAL_POLYGON");

let polygoninfo = {
	vertex: [
		new Module.JSVector3D(129.12599597147187, 35.17339329004985, 50.0),
		new Module.JSVector3D(129.1264736891435, 35.172432534300555, 50.0),
		new Module.JSVector3D(129.12705822860582, 35.172119138064076, 50.0),
		new Module.JSVector3D(129.12837813524428, 35.17198042514761, 50.0),
		new Module.JSVector3D(129.12925806742587, 35.171677294599604, 50.0),
		new Module.JSVector3D(129.13014427905534, 35.1712405752301, 50.0),
		new Module.JSVector3D(129.13067851056573, 35.170639446735436, 50.0)
	],
	index: [0, 1, 2, 3, 4, 5, 6],
	color: [
		new Module.JSColor(255, 0, 0),
		new Module.JSColor(0, 255, 0),
		new Module.JSColor(0, 0, 255)
	]
};

colorPolygon.set(polygoninfo);
```

* Return
  * 설정 성공 (success) 혹은 실패 (fail)
  * 다음의 경우 API는 fail 을 반환합니다.\
    1\) vertex, index, color 태그 중 하나라도 없을 경우
	2\) 폴리곤 정점이 2개 이하일 경우
	3\) 폴리곤 parts가 0개일 경우
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_colorpolygon_gradation
{% endtab %}
{% endtabs %}
