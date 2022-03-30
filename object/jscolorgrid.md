---
description: 2D 그리드 객체를 위한 API를 제공합니다.
---

# JSColorGrid

Module createColorGrid API로 생성할 수 있습니다.

```javascript
var colorGrid = Module.createColorGrid("ID");
```

## SetGridPosition([JSVector2D](../core/jsvector2d.md) leftTop, [JSVector2D](../core/jsvector2d.md) rightTop, [JSVector2D](../core/jsvector2d.md) rightBottom, [JSVector2D](../core/jsvector2d.md) leftBottom, number altitude, number rowNum, number colNum) → number

> 4개의 좌표, 높이, 가로, 세로 개수를 이용하여 2D 그리드 객체를 생성합니다.

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
var colorGrid2D = Module.createColorGrid("COLOR_GRID_2D");
var gridCellNum = colorGrid2D.SetGridPosition(
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
  * http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d
{% endtab %}
{% endtabs %}

## SetGridPositionByCellOptions([JSVector2D](../core/jsvector2d.md) leftTop, number altitude, number width, number height, number rowNum, number colNum) → number

> > 좌상단 좌표, 높이, 가로, 세로 개수, 길이를 이용하여 2D 그리드 객체를 생성합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter   | Type                          | Contents   |
| ----------- | ----------------------------- | ---------- |
| leftTop     | [JSVector2D](../core/jsvector2d.md) | 좌상단 경위도 좌표 |
| altitude    | number                        | 객체 높이      |
| width    	  | number                        | 그리드 가로 길이  |
| height      | number                        | 그리드 세로 길이  |
| rowNum      | number                        | 가로 그리드 개수  |
| colNum      | number                        | 세로 그리드 개수  |

* Detail

* Code
```
var colorGrid2D = Module.createColorGrid("COLOR_GRID_2D");
var gridCellNum = colorGrid2D.SetGridPositionByCellOptions(
	new Module.JSVector2D(124.2, 39), 	// 그리드 좌상단
	100000.0, 				// 그리드 바닥면 고도
	width, 					// 그리드 가로 길이
	height,					// 그리드 세로 길이
	rowNum, 				// 그리드 가로 셀 갯수
	colNum					// 그리드 세로 셀 갯수
);
```

* Return
  * 총 그리드 개수
{% endtab %}
{% endtabs %}

## SetGridPositionByCellSize([JSVector2D](../core/jsvector2d.md) leftTop, [JSVector2D](../core/jsvector2d.md) rightBottom, number altitude, number width, number height) → number

> > 좌상단 좌표, 우하단 좌표, 높이, 가로, 세로 길이를 이용하여 2D 그리드 객체를 생성합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter   | Type                          | Contents   |
| ----------- | ----------------------------- | ---------- |
| leftTop     | [JSVector2D](../core/jsvector2d.md) | 좌상단 경위도 좌표 |
| rightBottom | [JSVector2D](../core/jsvector2d.md) | 우하단 경위도 좌표 |
| altitude    | number                        | 객체 높이      |
| width    	  | number                        | 그리드 가로 길이  |
| height      | number                        | 그리드 세로 길이  |

* Detail

* Code
```
var colorGrid2D = Module.createColorGrid("COLOR_GRID_2D");
var gridCellNum = colorGrid2D.SetGridPositionByCellSize(
	new Module.JSVector2D(124.2, 39), 	// 그리드 좌상단
	new Module.JSVector2D(130.5, 34.5), 	// 그리드 우하단
	100000.0, 				// 그리드 바닥면 고도
	width, 					// 그리드 가로 길이
	height					// 그리드 세로 길이
);
```

* Return
  * 총 그리드 개수
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
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetGridCellDefaultColor(new Module.JSColor(255, 255, 255, 0));
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetGridCellColor(number rowIndex, number colIndex, [JSColor](../core/jscolor.md) color) → boolean

> 가로, 세로 Index에 해당하는 cell의 색상값을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| rowIndex  | number                  | cell 가로 index |
| colIndex  | number                  | cell 세로 index |
| color     | [JSColor](../core/jscolor.md) | cell 색상값      |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetGridCellColor(0, 0, new Module.JSColor(255, 255, 0, 0));
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 입력된 가로, 세로 index가 범위를 벗어난 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetLeftToRightSlopeAngle(number angle) → boolean

> x축 기울기를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| angle  | number                  | 각도 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetLeftToRightSlopeAngle(30);
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetLeftToRightSlopeAngleByAltitude(number leftAltitude, number rightAltitude) → boolean

> 왼쪽, 오른쪽 고도값으로 기울기를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| leftAltitude  | number                  | 고도 |
| rightAltitude  | number                  | 고도 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetLeftToRightSlopeAngleByAltitude(100000, 150000);
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetFrontToBackSlopeAngle(number angle) → boolean

> y축 기울기를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| angle  | number                  | 각도 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetFrontToBackSlopeAngle(30);
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetFrontToBackSlopeAngleByAltitude(number topAltitude, number bottomAltitude) → boolean

> 위, 아래 고도값으로 기울기를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| topAltitude  | number                  | 고도 |
| bottomAltitude  | number                  | 고도 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetFrontToBackSlopeAngleByAltitude(100000, 150000);
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetDirectionAngle(number angle) → boolean

> 2D 그리드 객체의 방향을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| angle  | number                  | 방향 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetDirectionAngle(0);
```

* angle
  * 0, 360: 북쪽
  * 90: 동쪽
  * 180: 남쪽
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetTerrainUnion(boolean union) → boolean

> 2D 그리드 객체를 지형에 결합합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| union  | boolean                  | 지형 결합 flag |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetTerrainUnion(true);
```
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetTerrainUnionGap(number altitude) → boolean

> 지형결합 사용시 지혀으로 부터 높이를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| altitude  | number                  | 지형으로 부터 높이 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetTerrainUnion(true);
colorGrid2D.SetTerrainUnionGap(100);
```
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetDrawLine(boolean line) → boolean

> 2D 그리드 객체의 테두리 생성 유무를 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| line  | boolean                  | 테두리 생성 유무 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetDrawLine(true);
```
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## SetGridLineColor([JSColor](../core/jscolor.md) color) → boolean

> 2D 그리드 객체의 테두리 색상을 설정합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type                    | Contents      |
| --------- | ----------------------- | ------------- |
| color  | [JSColor](../core/jscolor.md)                  | 테두리 색상 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetGridLineColor(new Module.JSColor(255, 255, 0, 0));
```
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## GetGridLeftTopPosition() → [JSVector3D](../core/jsvector3d.md)

> 2D 그리드 객체의 좌상단  경위도 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var position = colorGrid2D.GetGridLeftTopPosition();

var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
  
* Return
  * 설정 성공 ([JSVector3D](../core/jsvector3d.md)) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## GetGridRightTopPosition() → [JSVector3D](../core/jsvector3d.md)

> 2D 그리드 객체의 우상단  경위도 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var position = colorGrid2D.GetGridRightTopPosition();

var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
  
* Return
  * 설정 성공 ([JSVector3D](../core/jsvector3d.md)) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## GetGridRightBottomPosition() → [JSVector3D](../core/jsvector3d.md)

> 2D 그리드 객체의 우하단  경위도 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var position = colorGrid2D.GetGridRightBottomPosition();

var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
  
* Return
  * 설정 성공 ([JSVector3D](../core/jsvector3d.md)) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## GetGridLeftBottomPosition() → [JSVector3D](../core/jsvector3d.md)

> 2D 그리드 객체의 좌하단  경위도 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var position = colorGrid2D.GetGridLeftBottomPosition();

var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
  
* Return
  * 설정 성공 ([JSVector3D](../core/jsvector3d.md)) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## GetGridCellPosition(number rowIndex, number colIndex) → [JSVector3D](../core/jsvector3d.md)

> 가서, 세로 Index에 해당하는 cell 중심의 경위도 좌표를 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter  | Type                            | Contents      |
| ---------- | ------------------------------- | ------------- |
| rowIndex  | number                  | cell 가로 index |
| colIndex  | number                  | cell 세로 index |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var position = colorGrid2D.GetGridCellPosition(0, 0);

var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
  
* Return
  * 설정 성공 ([JSVector3D](../core/jsvector3d.md)) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## GetGridCellRect(number rowIndex, number colIndex) → [CJSVec3Array](CJSVec3Array.md)

> 가서, 세로 Index에 해당하는 cell의 경위도 좌표(좌상단, 우상단, 우하단, 좌하단)를 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter  | Type                            | Contents      |
| ---------- | ------------------------------- | ------------- |
| rowIndex  | number                  | cell 가로 index |
| colIndex  | number                  | cell 세로 index |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var position = colorGrid2D.GetGridCellRect(0, 0);

var leftTop = position.get(0);
var rightTop = position.get(1);
var rightbottom = position.get(2);
var leftbottom = position.get(3);

var lon = leftTop.Longitude;
var lat = leftTop.Latitude;
var alt = leftTop.Altitude;
...
```
  
* Return
  * 설정 성공 ([CJSVec3Array](CJSVec3Array.md)) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## GetGridCellIndexByPosition([JSVector3D](../core/jsvector3d.md) position) → string

> 해당 위치의 cell index를 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter  | Type                            | Contents      |
| ---------- | ------------------------------- | ------------- |
| position  | [JSVector3D](../core/jsvector3d.md)                  | 경위도 좌표 |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var index = colorGrid2D.GetGridCellIndexByPosition(new Module.JSVector2D(124.2, 39.5, 100));
```
  
* Return
  * 설정 성공 (string) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## GetGridEdgeLinePosition(string type, number margin) → [CJSVec3Array](CJSVec3Array.md)

> 2D 그리드 객체 전체 테두리의 시작점, 끝점을 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter  | Type                            | Contents      |
| ---------- | ------------------------------- | ------------- |
| type  | string                  | 테두리 위치별 타입(top, bottom, right, left) |
| margin  | number                  | 테두리 margin |

* Detail
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var linelist = colorGrid2D.GetGridEdgeLinePosition(0, 0);
```

* type
  * 0: top
  * 1: right
  * 2: bottom
  * 3: left
  
* Return
  * 설정 성공 ([CJSVec3Array](CJSVec3Array.md)) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우
	2\) 입력된 type이 4 이상일 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}

## Create() → boolean

> 설정한 옵션으로 그리드 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}
```
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 을 반환합니다.\
    1\) 엔진이 정상적으로 로드되지 않았을 경우 
	2\) 설정된 좌표가 없을 경우 
	3\) 설정된 가로, 세로 index가 범위를 벗어난 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d
{% endtab %}
{% endtabs %}