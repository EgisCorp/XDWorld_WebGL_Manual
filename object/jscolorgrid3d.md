---
description: 3D 그리드 객체를 위한 API를 제공합니다.
---

# JSColorGrid3D

Module createColorGrid3D API로 생성할 수 있습니다.

```javascript
var colorGrid3D = Module.createColorGrid3D("ID");
```

## SetGridPosition([JSVector2D](../core/jsvector2d.md) leftTop, [JSVector2D](../core/jsvector2d.md) rightTop, [JSVector2D](../core/jsvector2d.md) rightBottom, [JSVector2D](../core/jsvector2d.md) leftBottom, number altitude, number rowNum, number colNum) → number

> > 4개의 점, 높이, 가로, 세로 개수를 이용하여 3D 그리드 객체를 생성합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter   | Type                          | Contents   |
| ----------- | ----------------------------- | ---------- |
| leftTop     | [JSVector2D](../core/jsvector2d.md) | 좌상단 경위도 좌표 |
| rightTop    | [JSVector2D](../core/jsvector2d.md) | 우상단 경위도 좌표 |
| rightBottom | [JSVector2D](../core/jsvector2d.md) | 우하단 경위도 좌표 |
| leftBottom  | [JSVector2D](../core/jsvector2d.md) | 좌하단 경위도 좌표 |
| altitude    | number                        | 객체 높이      |
| rowNum      | number                        | 가로 그리드 개수  |
| colNum      | number                        | 세로 그리드 개수  |

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
var gridCellNum = colorGrid3D.SetGridPosition(
	new Module.JSVector2D(124.2, 39), 	// 그리드 좌상단
	new Module.JSVector2D(130.5, 39), 	// 그리드 우상단
	new Module.JSVector2D(130.5, 34.5), 	// 그리드 우하단
	new Module.JSVector2D(124.2, 34.5), 	// 그리드 좌하단
	100000.0, 				// 그리드 바닥면 고도
	rowNum, 				// 그리드 가로 셀 갯수
	colNum					// 그리드 세로 셀 갯수
);
```

* Return
  * 총 그리드 개수
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}

## SetGridCellDefaultColor([JSColor](../core/jscolor.md) color) → boolean

> 초기 그리드 색상값을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents |
| --------- | ----------------------- | -------- |
| color     | [JSColor](../core/jscolor.md) | 그리드 색상값  |

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridCellDefaultColor(new Module.JSColor(255, 255, 255, 0));
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}

## SetGridCellColor(number rowIndex, number colIndex, [JSColor](../core/jscolor.md) color) → boolean

> 가서, 세로 Index에 해당하는 cell의 색상값을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| rowIndex  | number                  | cell 가로 index |
| colIndex  | number                  | cell 세로 index |
| color     | [JSColor](../core/jscolor.md) | cell 색상값      |

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridCellColor(0, 0, new Module.JSColor(255, 255, 0, 0));
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 입력된 가로, 세로 index가 범위를 벗어난 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}

## SetGridLineColor([JSColor](../core/jscolor.md) color) → boolean

> 그리드 객체 테두리 색상을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents |
| --------- | ----------------------- | -------- |
| color     | [JSColor](../core/jscolor.md) | 테두리 색상값  |

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridLineColor(new Module.JSColor(150, 255, 0, 0));
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우 2) 그리드 객체 테두리를 생성하지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}

## SetGridCellLineColor(number rowIndex, number colIndex, [JSColor](../core/jscolor.md) color) → boolean

> 가서, 세로 Index에 해당하는 cell의 테두리 색상을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| rowIndex  | number                  | cell 가로 index |
| colIndex  | number                  | cell 세로 index |
| color     | [JSColor](../core/jscolor.md) | 테두리 색상값       |

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridCellLineColor(0, 0, new Module.JSColor(150, 255, 0, 0));
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우 2) 입력된 가로, 세로 index가 범위를 벗어난 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}

## SetGridCellHeight(number rowIndex, number colIndex, number height) → boolean

> 가서, 세로 Index에 해당하는 cell의 높이값을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type   | Contents      |
| --------- | ------ | ------------- |
| rowIndex  | number | cell 가로 index |
| colIndex  | number | cell 세로 index |
| height    | number | cell 높이값      |

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridCellHeight(0, 0, 30);
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 입력된 가로, 세로 index가 범위를 벗어난 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}

## SetDrawLine(boolean drawLine) → boolean

> 그리드 객체 테두리 생성 유무를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type    | Contents                 |
| --------- | ------- | ------------------------ |
| drawLine  | boolean | 테두리 생성 유무 설정(초기값: false) |

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetDrawLine(true);
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}

## SetNormal(boolean nomal) → boolean

> 그리드 객체 음영 효과를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type    | Contents            |
| --------- | ------- | ------------------- |
| nomal     | boolean | 음영효과 설정(초기값: false) |

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetNormal(true);
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}

## Create() → boolean

> 설정한 옵션으로 그리드 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

* Detail
```
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
...그리드 객체 옵션 설정...
colorGrid3D.Create();
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우 2) 설정된 좌표가 없을 경우 3) 설정된 가로, 세로 index가 범위를 벗어난 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_3d
{% endtab %}
{% endtabs %}
