---
description: 3D 그리드 객체 생성 및 수정 기능 API.
---

# JSColorGrid3D

> Module.createColorGrid3D API 생성.

```javascript
var colorGrid3D = Module.createColorGrid3D("ID");
```

### SetGridPosition(leftTop, rightTop, rightBottom, leftBottom, altitude, row, col) → number

> 4개의 경위도 좌표, 높이, 가로, 세로, 입력 값의 기준으로 3D 그리드 객체 생성.

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
  * [샌드박스\_그리드(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
var gridCellNum = colorGrid3D.SetGridPosition(
	new Module.JSVector2D(124.2, 39),
	new Module.JSVector2D(130.5, 39),
	new Module.JSVector2D(130.5, 34.5),
	new Module.JSVector2D(124.2, 34.5),
	1000.0,
	100,
	100
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
  * TRUE : 객체 옵션 설정 성공.
  * FALSE : 객체 옵션 설정 실패.
  
* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridCellDefaultColor(new Module.JSColor(255, 255, 255, 0));
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
  * TRUE : 객체 옵션 설정 성공.
  * FALSE : 객체 옵션 설정 실패.
    * 객체 옵션 설정 실패 조건.
	  * 설정된 가로, 세로 Index 범위 초과인 경우.
  
* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridCellColor(0, 0, new Module.JSColor(255, 255, 0, 0));
```
{% endtab %}
{% endtabs %}

### SetGridLineColor(color) → boolean

> 3D 그리드 객체의 테두리 색상 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description |
| --------- | ----------------------- | -------- |
| color     | [JSColor](../core/jscolor.md) | 테두리 색상값.  |

* Return
  * TRUE : 객체 옵션 설정 성공.
  * FALSE : 객체 옵션 설정 실패.
    * 객체 옵션 설정 실패 조건.
	  * 3D 그리드 태두리 생성하지 않은 경우.

* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridLineColor(new Module.JSColor(150, 255, 0, 0));
```
{% endtab %}
{% endtabs %}

### SetGridCellLineColor(row, column, color) → boolean

> 가로, 세로 Index에 해당하는 Cell의 테두리 색상값 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type                    | Description      |
| --------- | ----------------------- | ------------- |
| row  | number                  | Cell 가로 Index. |
| column  | number                  | Cell 세로 Index. |
| color     | [JSColor](../core/jscolor.md) | 테두리 색상값.       |

* Return
  * TRUE : 객체 옵션 설정 성공.
  * FALSE : 객체 옵션 설정 실패.
    * 객체 옵션 설정 실패 조건.
	  * 설정된 가로, 세로 Index 범위 초과인 경우.

* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridCellLineColor(0, 0, new Module.JSColor(150, 255, 0, 0));
```
{% endtab %}
{% endtabs %}

### SetGridCellHeight(row, column, color) → boolean

> 가로, 세로 Index에 해당하는 Cell의 높이값 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description      |
| --------- | ------ | ------------- |
| row  | number | Cell 가로 Index. |
| column  | number | Cell 세로 Index. |
| height    | number | Cell 높이값.      |

* Return
  * TRUE : 객체 옵션 설정 성공.
  * FALSE : 객체 옵션 설정 실패.
    * 객체 옵션 설정 실패 조건.
	  * 설정된 가로, 세로 Index 범위 초과인 경우.

* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetGridCellHeight(0, 0, 30);
```
{% endtab %}
{% endtabs %}

### SetDrawLine(type) → boolean

> 3D 그리드 객체의 테두리 생성 설정.
> 
> 테두리 생성 초기 설정 false.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description                 |
| --------- | ------- | ------------------------ |
| type  | boolean | <p>true인 경우 테두리 생성.<br>false인 경우 테두리 미생성.</p> |

* Return
  * TRUE : 객체 옵션 설정 성공.
  * FALSE : 객체 옵션 설정 실패.

{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetDrawLine(true);
```
{% endtab %}
{% endtabs %}

### SetNormal(type) → boolean

> 3D 그리드 객체의 음영 효과 설정.
> 
> 음영 효과 초기 설정 false.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description            |
| --------- | ------- | ------------------- |
| type     | boolean | <p>true인 경우 음영 효과 설정.<br>false인 경우 기본 가시화.</p> |

* Return
  * TRUE : 객체 옵션 설정 성공.
  * FALSE : 객체 옵션 설정 실패.

* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.SetNormal(true);
```
{% endtab %}
{% endtabs %}

### Create() → boolean

> 설정된 옵션을 기준으로 3D 그리드 객체 생성.

{% tabs %}
{% tab title="Information" %}

* Return
  * TRUE : 객체 생성 성공.
  * FALSE : 객체 생성 실패.
    * 객체 생성 실패 조건.
      * 입력된 좌표가 없는 경우.
	  * 설정된 가로, 세로 Index 범위 초과인 경우.

* Sample
  * function showGrid 참조.
  * [샌드박스\_그리드(3D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_3d)
{% endtab %}

{% tab title="Template" %}
```javascript
var colorGrid3D = Module.createColorGrid3D("COLOR_GRID_3D");
colorGrid3D.Create();
```
{% endtab %}
{% endtabs %}
