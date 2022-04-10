---
description: 2D 그리드 객체 생성 및 수정 기능 API.
---

# JSColorGrid

> Module.createColorGrid API 생성.

```javascript
var colorGrid = Module.createColorGrid("ID");
```

### SetGridPosition(leftTop, rightTop, rightBottom, leftBottom, altitude, row, col) → number

> 4개의 경위도 좌표를 기준으로 2D 그리드 객체 생성.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                          | Description   |
| ----------- | ----------------------------- | ---------- |
| leftTop     | [JSVector2D](../core/jsvector2d.md) | 좌상단 경위도 좌표. |
| rightTop    | [JSVector2D](../core/jsvector2d.md) | 우상단 경위도 좌표. |
| rightBottom | [JSVector2D](../core/jsvector2d.md) | 우하단 경위도 좌표. |
| leftBottom  | [JSVector2D](../core/jsvector2d.md) | 좌하단 경위도 좌표. |
| altitude    | number                        | 객체 높이.      |
| row      | number                        | 그리드 가로 개수.  |
| col      | number                        | 그리드 세로 개수.  |

* Return
  * 총 그리드 개수.

* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(2D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d)
  
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid("COLOR_GRID_2D");
var gridCellNum = colorGrid2D.SetGridPosition(
	new Module.JSVector2D(124.2, 39),
	new Module.JSVector2D(130.5, 39),
	new Module.JSVector2D(130.5, 34.5),
	new Module.JSVector2D(124.2, 34.5),
	100000.0,
	100,
	100
);
```
{% endtab %}
{% endtabs %}

### SetGridPositionByCellOptions(leftTop, altitude, width, height, row, col) → number

> 좌상단 위치로 2D 그리드 객체 생성.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                          | Description   |
| ----------- | ----------------------------- | ---------- |
| leftTop     | [JSVector2D](../core/jsvector2d.md) | 좌상단 경위도 좌표. |
| altitude    | number                        | 객체 높이.      |
| width    	  | number                        | 그리드 가로 길이.  |
| height      | number                        | 그리드 세로 길이.  |
| row     	 | number                        | 그리드 가로 개수.  |
| col     	 | number                        | 그리드 세로 개수.  |

* Return
  * 총 그리드 개수.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid("COLOR_GRID_2D");
var gridCellNum = colorGrid2D.SetGridPositionByCellOptions(
	new Module.JSVector2D(124.2, 39),
	100000.0,
	1000,
	1000,
	100,
	100
);
```
{% endtab %}
{% endtabs %}

### SetGridPositionByCellSize(leftTop, rightBottom, altitude, width, height) → number

> 최소, 최대 경위도 좌표를 기준으로 2D 그리드 객체 생성.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                          | Description   |
| ----------- | ----------------------------- | ---------- |
| leftTop     | [JSVector2D](../core/jsvector2d.md) | 좌상단 경위도 좌표. |
| rightBottom | [JSVector2D](../core/jsvector2d.md) | 우하단 경위도 좌표. |
| altitude    | number                        | 객체 높이.      |
| width    	  | number                        | 그리드 가로 길이.  |
| height      | number                        | 그리드 세로 길이.  |

* Return
  * 총 그리드 개수.
{% endtab %}

{% tab title="Template" %}
```javascript

var colorGrid2D = Module.createColorGrid("COLOR_GRID_2D");
var gridCellNum = colorGrid2D.SetGridPositionByCellSize(
	new Module.JSVector2D(124.2, 39),
	new Module.JSVector2D(130.5, 34.5),
	100000.0,
	1000,
	1000,
);
```
{% endtab %}
{% endtabs %}

### SetGridCellDefaultColor(color) → boolean

> 초기 그리드 색상값을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description |
| --------- | ----------------------- | -------- |
| color     | [JSColor](../core/jscolor.md) | 그리드 색상값.  |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
  	
* Sample
  * function showGrid 참조..
  * [샌드박스\_그리드(2D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetGridCellDefaultColor(new Module.JSColor(255, 255, 255, 0));
```
{% endtab %}
{% endtabs %}

### SetGridCellColor(row, column, color) → boolean

> 가로, 세로 Index에 해당하는 Cell의 색상값 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| row  | number                  | Cell 가로 Index. |
| column  | number                  | Cell 세로 Index. |
| color     | [JSColor](../core/jscolor.md) | Cell 색상값.      |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
    * 객체 옵션 설정 실패 조건.
	  * 설정된 가로, 세로 Index 범위 초과인 경우.
	  
* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(2D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetGridCellColor(0, 0, new Module.JSColor(255, 255, 0, 0));
```
{% endtab %}
{% endtabs %}

### SetLeftToRightSlopeAngle(angle) → boolean

> x축 기울기 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| angle  | number                  | 각도. |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
  
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetLeftToRightSlopeAngle(30);
```
{% endtab %}
{% endtabs %}

### SetLeftToRightSlopeAngleByAltitude(left, right) → boolean

> 왼쪽, 오른쪽 고도값 기준 기울기 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| left  | number                  | 고도. |
| right  | number                  | 고도. |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetLeftToRightSlopeAngleByAltitude(100000, 150000);
```
{% endtab %}
{% endtabs %}

### SetFrontToBackSlopeAngle(angle) → boolean

> y축 기울기 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| angle  | number                  | 각도. |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetFrontToBackSlopeAngle(30);
```
{% endtab %}
{% endtabs %}

### SetFrontToBackSlopeAngleByAltitude(top, bottom) → boolean

> 위, 아래 고도값 기준 기울기 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| top  | number                  | 고도. |
| bottom  | number                  | 고도. |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetFrontToBackSlopeAngleByAltitude(100000, 150000);
```
{% endtab %}
{% endtabs %}

### SetDirectionAngle(angle) → boolean

> 2D 그리드 객체 방향 설정.
>
> angle 입력 값에 따른 회전 정보 0, 360(북쪽), 90(동쪽), 180(남쪽), 270(서쪽).

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| angle  | number                  | 방향 |
  
* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetDirectionAngle(0);
```
{% endtab %}
{% endtabs %}

### SetTerrainUnion(union) → boolean

> 2D 그리드 객체 지형 결합 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| union  | boolean                  | <p>true인 경우 지형결합.<br>false인 경우 객체 위치 기준.</p> |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetTerrainUnion(true);
```
{% endtab %}
{% endtabs %}

### SetTerrainUnionGap(altitude) → boolean

> 2D 그리드 객체 지형 결합 후 높이값 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| altitude  | number                  | 지형으로 부터 높이. |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetTerrainUnion(true);
colorGrid2D.SetTerrainUnionGap(100);
```
{% endtab %}
{% endtabs %}

### SetDrawLine(type) → boolean

> 2D 그리드 객체의 테두리 생성 설정.
>
> 테두리 생성 초기 설정 false.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| type  | boolean                  | <p>true인 경우 테두리 생성.<br>false인 경우 테두리 미생성.</p> |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetDrawLine(true);
```
{% endtab %}
{% endtabs %}

### SetGridLineColor(color) → boolean

> 2D 그리드 객체의 테두리 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| color  | [JSColor](../core/jscolor.md)                  | 테두리 색상. |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
    * 객체 옵션 설정 실패 조건.
	  * 2D 그리드 태두리 생성하지 않은 경우.
  
* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(2D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.SetGridLineColor(new Module.JSColor(255, 255, 0, 0));
```
{% endtab %}
{% endtabs %}

### GetGridLeftTopPosition() → [JSVector3D](../core/jsvector3d.md)

> 2D 그리드 객체 좌상단 경위도 좌표 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSVector3D](../core/jsvector3d.md) : 좌상단 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.Create();

var position = colorGrid2D.GetGridLeftTopPosition();
var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
{% endtab %}
{% endtabs %}

### GetGridRightTopPosition() → [JSVector3D](../core/jsvector3d.md)

> 2D 그리드 객체 우상단 경위도 좌표 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSVector3D](../core/jsvector3d.md) : 우상단 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.Create();

var position = colorGrid2D.GetGridRightTopPosition();
var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
{% endtab %}
{% endtabs %}

### GetGridLeftBottomPosition() → [JSVector3D](../core/jsvector3d.md)

> 2D 그리드 객체 좌하단 경위도 좌표 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSVector3D](../core/jsvector3d.md) : 좌하단 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
...그리드 객체 옵션 설정...
colorGrid2D.Create();

var position = colorGrid2D.GetGridLeftBottomPosition();

var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
{% endtab %}
{% endtabs %}

### GetGridRightBottomPosition() → [JSVector3D](../core/jsvector3d.md)

> 2D 그리드 객체 우하단 경위도 좌표 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSVector3D](../core/jsvector3d.md) : 우하단 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.Create();

var position = colorGrid2D.GetGridRightBottomPosition();
var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
{% endtab %}
{% endtabs %}



### GetGridCellPosition(row, column) → [JSVector3D](../core/jsvector3d.md)

> 가로, 세로 Index에 해당하는 Cell의 중심 경위도 좌표 반환.

{% tabs %}
{% tab title="Information" %}
| Name  | Type                            | Description      |
| ---------- | ------------------------------- | ------------- |
| row  | number                  | Cell 가로 Index. |
| column  | number                  | Cell 세로 Index. |

* Return
  * [JSVector3D](../core/jsvector3d.md) : 중심 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.Create();

var position = colorGrid2D.GetGridCellPosition(0, 0);
var lon = position.Longitude;
var lat = position.Latitude;
var alt = position.Altitude;
```
{% endtab %}
{% endtabs %}

### GetGridCellRect(row, column) → [JSVec3Array](../core/jsvec3array.md)

> 가로, 세로 Index에 해당하는 Cell의 각 지점(4개) 좌표 반환.

{% tabs %}
{% tab title="Information" %}
| Name  | Type                            | Description      |
| ---------- | ------------------------------- | ------------- |
| row  | number                  | Cell 가로 Index. |
| column  | number                  | Cell 세로 Index. |

* Return
  * [JSVector3D](../core/jsvector3d.md) : 각 지점 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.Create();

var position = colorGrid2D.GetGridCellRect(0, 0);

var leftTop = position.get(0);
var rightTop = position.get(1);
var rightbottom = position.get(2);
var leftbottom = position.get(3);

var lon = leftTop.Longitude;
var lat = leftTop.Latitude;
var alt = leftTop.Altitude;
```
{% endtab %}
{% endtabs %}

### GetGridCellIndexByPosition(position) → string

> 경위도 좌표에 해당되는 Cell Index 반환.

{% tabs %}
{% tab title="Information" %}
| Name  | Type                            | Description      |
| ---------- | ------------------------------- | ------------- |
| position  | [JSVector3D](../core/jsvector3d.md)                  | 경위도 좌표. |

* Return
  * string : Cell Index 번호 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.Create();

var Index = colorGrid2D.GetGridCellIndexByPosition(new Module.JSVector2D(124.2, 39.5, 100));
```
{% endtab %}
{% endtabs %}

### GetGridEdgeLinePosition(type, value) → [JSVec3Array](../core/jsvec3array.md)

> 2D 그리드 객체 테두리 시작, 끝 점 경위도 좌표 반환.
> 
> type 입력 값에 따른 좌표 반환 정보 0(top), 1(right), 2(bottom), 3(left).

{% tabs %}
{% tab title="Information" %}
| Name  | Type                            | Description      |
| ---------- | ------------------------------- | ------------- |
| type  | string                  | 반환 테두리 설정값.|
| value  | number                  | 테두리 margin. |

* Return
  * [JSVec3Array](../core/jsvec3array.md) : 테두리 시작, 끝점 경위도 좌표 반환 성공.
  * null : 좌표 반환 실패.
    * 오브젝트 생성 실패 조건
	  * type&gt;4 값이 설졍 된 경우
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.Create();

var linelist = colorGrid2D.GetGridEdgeLinePosition(0, 0);
```
{% endtab %}
{% endtabs %}

### Create() → boolean

> 설정된 옵션을 기준으로 2D 그리드 객체 생성.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
    * 오브젝트 생성 실패 조건.
	  * 입력된 좌표가 없는 경우.
	  * 설정된 가로, 세로 Index 범위 초과인 경우.
* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(2D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid2D = Module.createColorGrid2D("COLOR_GRID_2D");
colorGrid2D.Create();
```
{% endtab %}
{% endtabs %}