# Type List

### coordinates Type

| Name | Type | Description |
| :--- | :--- | :--- |
| coordinate | object | 경위도 좌표 목록. |
| stype | string | 경위도 좌표 목록을 구성하는 스타일. |

### coordinates Style Type

| Name | Type | Description |
| :--- | :--- | :--- |
| XY | string |\[\[x, y\], \[x, y\], ...\] |
| XYZ | string |\[\[x, y, z\], \[x, y, z\], ...\] |
| XYZARRAY | string | \[x, y, z, x, y, z,...\] |
| JSVector3D | string | \[JSVector3D, JSVector3D, ...\] |

### Rect2D Style Type
| Name | Type | Description |
| :--- | :--- | :--- |
| min | [JSVector2D](../core/jsvector2d.md) | 좌하단 경위도 좌표. |
| max | [JSVector2D](../core/jsvector2d.md) | 우상단 경위도 좌표. |