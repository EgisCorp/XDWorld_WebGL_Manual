# Type List

## Layer Type List

| Index | Name | Description |
| :--- | :--- | :--- |
| 0 | ELT_POLYHEDRON | 다면체 |
| 1 | ELT_PLANE | 평면 |
| 2 | ELT_PIPE | 관\(실린더\) |
| 3 | ELT_BILLBOARD | 빌보드 |
| 4 | ELT_3DLINE | 3차원 선 |
| 5 | ELT_3DPOINT | 심볼 텍스트 |
| 6 | ELT_3DS\_SYMBOL | 3차원 심볼 |
| 7 | ELT_GHOST\_3DSYMBOL | 유령 심볼 |
| 8 | ELT_TERRAIN | 지형 |
| 9 | ELT_MULTILPE | 다용도 |
| 10 | ELT_KML\_GROUND | KML |
| 11 | ELT_TERRAIN\_IMAGE | 지형 영상 |
| 12 | ELT_PICTOMETRY | 픽토 메트리 |
| 13 | ELT_WATER | Water 가시화 |
| 102 | ELT_SKY\_LINE | RTT 미적용 3차원 선 |
| 112 | ELT_TYPOON | 태풍 가시화 |
| 113 | ELT_GRAPH | 차트 가시화 |

```javascript
var layerList = new Module.JSLayerList(true);
layerList.createLayer("Layer_Name", Module.ELT_3DPOINT);	// 심볼 텍스트 레이어 생성
```

## WFS Type List

| Index | Name | Description |
| :--- | :--- | :--- |
| 0 | POI | POI Type |
| 1 | Polygon | Polygon Type |
| 2 | Line | Line Type |

```javascript
let layerList = new Module.JSLayerList( false );
layerList.createWFSLayer(“WFS_POI" , 0);
layerList.createWFSLayer(“WFS_Polygon" , 1);
layerList.createWFSLayer(“WFS_Line" , 2);
```

## Navigation Postion Type List

| Index | Name | Description |
| :--- | :--- | :--- |
| 0 | JS_NAVIGATION_LT | 좌상단 위치 옵션. |
| 1 | JS_NAVIGATION_RT | 우상단 위치 옵션. |
| 2 | JS_NAVIGATION_LB | 좌하단 위치 옵션. |
| 3 | JS_NAVIGATION_RB | 우하단 위치 옵션. |

```javascript
Module.getNavigation().setNaviPos(Module.JS_NAVIGATION_LT);
```
	
## Navigation Visible Type List

| Index | Name | Description |
| :--- | :--- | :--- |
| 0 | JS_VISIBLE_ON | 네비게이션(나침판) 가시화 활성화. |
| 1 | JS_VISIBLE_OFF | 네비게이션(나침판) 가시화 비 활성화. |
| 2 | JS_VISIBLE_AUTO | 네비게이션(나침판) 간소화 가시화 활성화. |

```javascript
Module.getNavigation().setNaviVisible(Module.JS_VISIBLE_ON);
```

## Mouse Type List

| Index | Name | Description |
| :--- | :--- | :--- |
| 0 | MML\_NONE | 기본 |
| 1 | MML\_MOVE\_GRAB | 지도 이동 |
| 2 | MML\_ZOOMIN\_RECT | 영역 확대 |
| 3 | MML\_ZOOMIN\_POINT | 지도 확대 |
| 4 | MML\_ZOOMOUT\_RECT | 영역 축소 |
| 5 | MML\_ZOOMOUT\_POINT | 지도 축소 |
| 6 | MML\_SELECT\_POINT | 포인트 선택 |
| 7 | MML\_SELECT\_FACE | 면 선택 |
| 8 | MML\_SCREEN\_RECT | 화면 사각 선택 |
| 9 | MML\_SELECT\_RECT | 사각 선택 |
| 10 | MML\_SELECT\_CIRCLE | 반경 선택 |
| 11 | MML\_SELECT\_POLY | 폴리곤 선택 |
| 12 | MML\_MOVE\_GRAB\_EX | 클릭 시 이동 금지 |
| 20 | MML\_INPUT\_POINT | 점 입력 |
| 21 | MML\_INPUT\_LINE | 라인 입력 |
| 22 | MML\_INPUT\_RECT | 사각 입력\(정북방향\) |
| 23 | MML\_INPUT\_CIRCLE | 원 입력 |
| 24 | MML\_INPUT\_AREA | 영역 입력 |
| 25 | MML\_INPUT\_SPHERE | 구 입력 |
| 26 | MML\_INPUT\_LINE\_DRAG | 마우스 드래그 입력 |
| 27 | MML\_INPUT\_RECT\_SCREEN | 사각 입력 상태 |
| 40 | MML\_OBJECT\_INSERT | 객체 삽입\(3ds..\) |
| 41 | MML\_OBJECT\_MOVE\_XZ | 선택 객체 이동 |
| 42 | MML\_OBJECT\_MOVE\_YZ | 선택 객체 이동 |
| 43 | MML\_OBJECT\_ROTATE | 선택 객체 회전 |
| 44 | MML\_OBJECT\_SCALE | 선택 객체 크기 조정 |
| 45 | MML\_OBJECT\_SCALE\_Y | 선택 객체 크기 조정 |
| 46 | MML\_OBJECT\_SCALE\_XZ | 선택 객체 크기 조정 |
| 50 | MML\_DRAW\_CUBE | 박스 입력 |
| 51 | MML\_DRAW\_CYLINDER |  |
| 52 | MML\_DRAW\_SPHERE |  |
| 53 | MML\_DRAW\_CON |  |
| 54 | MML\_DRAW\_PIPE |  |
| 55 | MML\_DRAW\_DOME |  |
| 56 | MML\_DRAW\_POLYHEAD |  |
| 57 | MML\_DRAW\_ARROW |  |
| 70 | MML\_VERTEX\_MOVE |  |
| 71 | MML\_VERTEX\_ADD |  |
| 72 | MML\_VERTEX\_REMOVE |  |
| 80 | MML\_ANALYS\_AREA | 면적 계산 |
| 81 | MML\_ANALYS\_DISTANCE | 거리 계산 |
| 82 | MML\_ANALYS\_VIEWSHED | 가시권 분석 |
| 83 | MML\_ANALYS\_SLICE | 단면도 분석 |
| 84 | MML\_ANALYS\_JOMANG | 조망 가시화 |
| 85 | MML\_VIEW\_UNDERGROUND | 지하 시설물 가시화 |
| 86 | MML\_ANALYS\_ALTITUDE | 높이 측정 |
| 87 | MML\_ANALYS\_DISTANCE\_STRAIGHT |  |
| 88 | MML\_ANALYS\_AREA\_PLANE |  |
| 89 | MML\_ANALYS\_AREA\_CIRCLE |  |
| 90 | MML\_UI\_MEMO | 메모 기능 |
| 94 | MML\_ANALYS\_JOMANGPOINT | 조망점 관리 |
| 96 | MML\_SELECT\_MULTIFACE |  |
| 101 | MML\_FIGURE\_RECT | 사각 박스 가시화 |
| 102 | MML\_FIGURE\_ELLIPSE | 구 객체 가시화 |
| 103 | MML\_FIGURE\_ARROW | 화살표 객체 가시화 |
| 104 | MML\_FIGURE\_ARROW\_DUEL |  |
| 105 | MML\_FIGURE\_CONVEX |  |
| 106 | MML\_FIGURE\_CONCAVE |  |
| 107 | MML\_FIGURE\_ROUND\_RECT |  |
| 108 | MML\_FIGURE\_BEARING\_ARC |  |
| 109 | MML\_FIGURE\_STAR | 별 객체 가시화 |
| 110 | MML\_FIGURE\_PLUS |  |
| 111 | MML\_FIGURE\_TEXTURE\_RECT |  |
| 200 | MML\_ADD\_SOLAR\_PANEL |  |
| 201 | MML\_SELECT\_EDIT\_MODULE |  |
| 202 | MML\_EDIT\_SOLAR\_MODULE |  |
| 300 | MML\_OBJECT\_EDIT |  |

```javascript
Module.XDSetMouseState(Module._NONE);
```

## Coordinate Type List

| Index | Name | Description |
| :--- | :--- | :--- |
| 13 | Latitude/Logitude (WGS84) | EPSG:4326. |
| 14 | Korea TM BESSEL(West) | EPSG:5186. |
