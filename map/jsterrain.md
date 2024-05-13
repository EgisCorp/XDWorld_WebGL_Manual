---
description: 지도 내 지형 설정 및 제어하기 위한 API 입니다.
---

# JSTerrain

> Module.getTerrain() API를 생성합니다.

```javascript
var map = Module.getTerrain();
```

## Function

### makeTerrainElevationCellData(option) → object

> 입력된 정점 좌표 목록을 기반으로 변수값 격자 구조를 생성하고 정보를 반환합니다.
>
> 격자 구조는 위치Returns information after creating GRID data with an argument variable.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                      | Description                     |
| ------ | --------------------------------------------------------- | ------------------------------- |
| option | [JSTerrain.GridOption](jsterrain.md#jsterrain.gridoption) | Grid data creation information. |

-   Return
    -   .result : API success status ( 1 : success, 0 : failure ).
    -   .name : Name of the operation API.
    -   .return : API return information ( [JSTerrain.GridData](jsterrain.md#jsterrain.griddata) : Normal return value, string : Failure error code ).

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
};
let result = Module.getTerrain().makeTerrainElevationCellData(parameter);
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTerrain.GridOption

> Basic Grid setting options.

| Name       | Type                                                    | Attributes | Default | Description                                                                                     |
| ---------- | ------------------------------------------------------- | ---------- | ------- | ----------------------------------------------------------------------------------------------- |
| option     | [coordinates Type](../etc/tag-list.md#coordinates-type) |            |         | List of latitude and longitude coordinates for the analysis area, coordinate list type setting. |
| vertical   | number                                                  | optional   | 5       | Length of the Cell composing the Grid vertically (in meters).                                   |
| horizontal | number                                                  | optional   | 5       | Length of the Cell composing the Grid horizontally (in meters).                                 |

#### JSTerrain.GridData

> Grid return information.

| Name            | Type                                                  | Description                                                     |
| --------------- | ----------------------------------------------------- | --------------------------------------------------------------- |
| min             | [JSVector2D](../core/jsvector2d.md)                   | Lower left latitude and longitude coordinates of the Grid.      |
| max             | [JSVector2D](../core/jsvector2d.md)                   | Upper right latitude and longitude coordinates of the Grid.     |
| center          | [JSVector2D](../core/jsvector2d.md)                   | Center latitude and longitude coordinates of the Grid.          |
| vertical        | number                                                | Length of the Cell composing the Grid vertically (in meters).   |
| verticalCount   | number                                                | Number of Cells composing the Grid vertically.                  |
| horizontal      | number                                                | Length of the Cell composing the Grid horizontally (in meters). |
| horizontalCount | number                                                | Number of Cells composing the Grid horizontally.                |
| cells           | [JSTerrain.CellData](jsterrain.md#jsterrain.celldata) | Array of Cell information composing the Grid.                   |

#### JSTerrain.CellData

> Data information of the Cell composing the Grid.

| Name      | Type                                | Description                                                      |
| --------- | ----------------------------------- | ---------------------------------------------------------------- |
| type      | boolean                             | Inclusion status of the analysis area.                           |
| elevation | number                              | Elevation of the cell center latitude and longitude coordinates. |
| min       | [JSVector2D](../core/jsvector2d.md) | Lower left latitude and longitude coordinates of the Cell.       |
| max       | [JSVector2D](../core/jsvector2d.md) | Upper right latitude and longitude coordinates of the Cell.      |
| center    | [JSVector2D](../core/jsvector2d.md) | Center latitude and longitude coordinates of the Cell.           |
