# Type List

## Layer Type List

| Index | Name               | Description        |
| ----- | ------------------ | ------------------ |
| 0     | ELT_POLYHEDRON     | 다면체             |
| 1     | ELT_PLANE          | 평면               |
| 2     | ELT_PIPE           | 관(실린더)         |
| 3     | ELT_BILLBOARD      | 빌보드             |
| 4     | ELT_3DLINE         | 3차원 선           |
| 5     | ELT_3DPOINT        | POI                |
| 6     | ELT_3DS_SYMBOL     | 3차원 심볼         |
| 7     | ELT_GHOST_3DSYMBOL | 고스트 심볼        |
| 8     | ELT_TERRAIN        | 지형 레이어        |
| 9     | ELT_MULTILPE       | 다용도 레이어      |
| 10    | ELT_KML_GROUND     | kml ground         |
| 11    | ELT_TERRAIN_IMAGE  | 영상 레이어        |
| 12    | ELT_PICTOMETRY     | 픽토 메트리 데이터 |

```javascript
let layerList = new Module.JSLayerList(true);
layerList.createLayer("Layer_Name", Module.ELT_3DPOINT); // Creates a symbol text layer
```

## Tile Layer Type List

| Index | Name                | Description       |
| ----- | ------------------- | ----------------- |
| 9     | ETLT_REAL3D         | 건물              |
| 10    | ETLT_PNG_IMAGE      | 하이브리드 이미지 |
| 19    | ETLT_POINT_CLOUD    | 포인트 클라우드   |
| 20    | ETLT_TILE_LOD_MODEL | LOD 오브젝트      |

```javascript

```

## WFS Type List

| Index | Name    | Description  |
| ----- | ------- | ------------ |
| 0     | POI     | POI Type     |
| 1     | Polygon | Polygon Type |
| 2     | Line    | Line Type    |

```javascript
let layerList = new Module.JSLayerList( false );
layerList.createWFSLayer(“WFS_POI" , 0);
layerList.createWFSLayer(“WFS_Polygon" , 1);
layerList.createWFSLayer(“WFS_Line" , 2);
```

## Navigation Align Type List

| Index | Name             | Description       |
| ----- | ---------------- | ----------------- |
| 0     | JS_NAVIGATION_LT | 좌상단 위치 옵션. |
| 1     | JS_NAVIGATION_RT | 우상단 위치 옵션. |
| 2     | JS_NAVIGATION_LB | 좌하단 위치 옵션. |
| 3     | JS_NAVIGATION_RB | 우하단 위치 옵션. |

```javascript
Module.getNavigation().setNaviPos(Module.JS_NAVIGATION_LT);
```

## Navigation Visible Type List

| Index | Name            | Description                              |
| ----- | --------------- | ---------------------------------------- |
| 0     | JS_VISIBLE_ON   | 네비게이션(나침판) 가시화 활성화.        |
| 1     | JS_VISIBLE_OFF  | 네비게이션(나침판) 가시화 비 활성화.     |
| 2     | JS_VISIBLE_AUTO | 네비게이션(나침판) 간소화 가시화 활성화. |

```javascript
Module.getNavigation().setNaviVisible(Module.JS_VISIBLE_ON);
```

## Mouse Type List

| Index | Name                         | Description                                         |
| ----- | ---------------------------- | --------------------------------------------------- |
| 0     | MML_NONE                     | 기본                                                |
| 1     | MML_MOVE_GRAB                | 마우스 드래그 및 휠 조작으로 지도 이동, 회전, 확대/축소    |
| 6     | MML_SELECT_POINT             | 객체를 클릭하여 선택                                   |
| 7     | MML_SELECT_FACE              | 면을 클릭하여 선택(MML_SELECT_POINT와 동일)            |
| 9     | MML_SELECT_RECT              | 사각형 영역을 드래그하여 영역 내의 객체를 모두 선택        |
| 10    | MML_SELECT_CIRCLE            | 중심점과 반경을 드래그하여 원형 영역 내의 객체를 모두 선택  |
| 11    | MML_SELECT_POLY              | 다각형 선택 영역을 생성하여 영역 내의 객체를 모두 선택      |
| 13    | MML_SELECT_ROOF              | 태양광 설치 대상 지붕 선택                              |
| 14    | MML_SELECT_EXCLUDE_ROOF      | 태양광 설치 제외 영역으로 사용할 지붕 선택                |
| 15    | MML_SELECT_SOLAR_TERRAIN     | 태양광 모듈을 설치 할 지면 영역 선택                     |
| 16    | MML_SELECT_WALL_INFO         | 벽면 정보를 조회할 벽면 선택                            |
| 17    | MML_SELECT_WALL_INFO_POINT   | 벽면 정보와 조회 및 선택 효과 표시                       |
| 20    | MML_INPUT_POINT              | 클릭한 위치에 점 입력                                   |
| 21    | MML_INPUT_LINE               | 여러 점을 지정하여 라인 입력                             |
| 22    | MML_INPUT_RECT               | 사각형 영역을 드래그하여 정북 방향 기준의 사각형 입력       |
| 23    | MML_INPUT_CIRCLE             | 중심점과 반경을 드래그하여 원 입력                        |
| 24    | MML_INPUT_AREA               | 여러 개의 점을 지정하여 다각형 영역 입력                  |
| 25    | MML_INPUT_SPHERE             | 구 입력(현재 사용되지 않음)                             |
| 27    | MML_INPUT_RECT_SCREEN        | 화면 방향을 기준으로 사각형 영역 입력                     |
| 30    | MML_RETURN_ANALYSISPOS       | 분석에 사용할 선택 지점의 경위도 반환                     |
| 50    | MML_EDIT_GIZMO               | Gizmo를 이용하여 객체 편집(이동, 회전)                   |
| 80    | MML_ANALYS_AREA              | 지정한 다각형 영역의 면적 계산                           |
| 81    | MML_ANALYS_DISTANCE          | 여러 점을 지정하여 지형을 고려한 거리 계산                 |
| 82    | MML_ANALYS_VIEWSHED          | 선택한 지점을 기준으로 부채꼴 형태의 2D 가시권 분석         |
| 83    | MML_ANALYS_ALTDISTANCE       | 두 점을 지정하여 높이, 거리 및 직선거리 계산               |
| 84    | MML_ANALYS_JOMANG            | 선택한 위치의 조망 결과 가시화                           |
| 85    | MML_VIEW_UNDERGROUND         | 지하 시설물 가시화                                     |
| 86    | MML_ANALYS_ALTITUDE          | 선택한 위치의 고도 측정                                 |
| 87    | MML_ANALYS_DISTANCE_STRAIGHT | 여러 점을 지정하여 직선거리 계산                         |
| 88    | MML_ANALYS_AREA_PLANE        | RTT를 적용하지 않는 일반 평면 기준으로 면적 계산           |
| 89    | MML_ANALYS_AREA_CIRCLE       | 수직 평면 객체의 반경 계산                              |
| 90    | MML_ANALYS_GRIDSHADOW        | 수인한도분석                                           |
| 91    | MML_ANALYS_WINDOWSHADOW      | 창문분석                                              |
| 94    | MML_ANALYS_JOMANGPOINT       | 조망 분석에 사용할 조망점 관리                           |
| 101   | MML_FIGURE_RECT              | 직육면체 사각 박스 입력                                 |
| 102   | MML_FIGURE_ELLIPSE           | 원기둥 객체 입력                                       |
| 103   | MML_FIGURE_ARROW             | 단방향 화살표 객체 입력                                 |
| 104   | MML_FIGURE_ARROW_DUEL        | 양방향 화살표 객체 입력                                 |
| 105   | MML_FIGURE_CONVEX            | 볼록형 다면체 입력                                      |
| 106   | MML_FIGURE_CONCAVE           | 오목형 다면체 입력                                      |
| 107   | MML_FIGURE_ROUND_RECT        | 모서리가 둥근 직육면체 입력                              |
| 108   | MML_FIGURE_BEARING_ARC       | 베어링 형 호(Arc) 기반 다면체 입력                       |
| 109   | MML_FIGURE_STAR              | 별 모양 다면체 입력                                     |
| 110   | MML_FIGURE_PLUS              | 더하기 기호 다면체 입력                                  |
| 200   | MML_ADD_SOLAR_PANEL          | 벽면에 단일 태양광 패널 추가                              |
| 201   | MML_SELECT_EDIT_MODULE       | 편집할 벽면 태양광 패널 선택                              |
| 202   | MML_EDIT_SOLAR_MODULE        | 지붕 태양광 패널 추가 또는 삭제                           |
| 203   | MML_ADD_WALL_PANEL_RECT      | 영역을 지정하여 영역의 벽면에 태양광 패널 일괄 추가          |

```javascript
Module.XDSetMouseState(Module._NONE);
```

## JSFigure Type List

| Index | Name            | Description                       |
| ----- | --------------- | --------------------------------- |
| 0     | EFT_SOLID       | 다면체                            |
| 1     | EFT_SOLID_OPEN  | 열린 다면체                       |
| 4     | EFT_RECT        | 사각형                            |
| 5     | EFT_ELLIPSE     | 타원                              |
| 101   | EFT_ARROW       | 화살표(단방향)                    |
| 102   | EFT_ARROW_DUEL  | 화살표(양방향)                    |
| 103   | EFT_CONVEX      | 볼록 다각형                       |
| 104   | EFT_CONCAVE     | 오목 다각형                       |
| 105   | EFT_ROUND_RECT  | 사각 라운드(모서리가 둥근 사각형) |
| 106   | EFT_BEARING_ARC | 베어링 아크                       |
| 107   | EFT_STAR        | 별 모양                           |
| 108   | EFT_PLUS        | 더하기 모양(+)                    |

## Coordinate Type List

| Index | Name                      | Description |
| ----- | ------------------------- | ----------- |
| 13    | Latitude/Logitude (WGS84) | EPSG:4326.  |
| 14    | Korea TM BESSEL(West)     | EPSG:5186.  |

## Shadow Analysis Type List

| Index | Name                      	| Description 										|
| ----- | ----------------------------- | ------------------------------------------------- |
| 300   | BRIEF_ANALYSIS_MODE 			| 각 그리드의 중점만 분석.  									|
| 301   | NORMAL_ANALYSIS_MODE 			| 각 그리드에 그림자가 절반이상 생길 경우 일조권 침해.					|
| 302   | DETAIL_ANALYSIS_MODE 			| 각 그리드에 그림자가 조금이라도 생길 경우 일조권 침해.				|
