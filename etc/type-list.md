# Type List

## Layer Type List

| Index | Name                   | Description |
| ----- | ---------------------- | ----------- |
| 3     | ELT\_BILLBOARD         | 빌보드         |
| 5     | ELT\_3DPOINT           | POI         |
| 7     | ELT\_GHOST\_3DSYMBOL   | 고스트 심볼      |
| 9     | ETLT\_REAL3D           | 건물          |
| 10    | ETLT\_IMAGE\_PNG       | 하이브리드 이미지   |
| 19    | ETLT\_POINT\_CLOUD     | 포인트 클라우드    |
| 20    | ETLT\_TILE\_LOD\_MODEL | LOD 오브젝트    |

```javascript
var layerList = new Module.JSLayerList(true);
layerList.createLayer("Layer_Name", Module.ELT_3DPOINT);	// 심볼 텍스트 레이어 생성
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

| Index | Name               | Description |
| ----- | ------------------ | ----------- |
| 0     | JS\_NAVIGATION\_LT | 좌상단 위치 옵션.  |
| 1     | JS\_NAVIGATION\_RT | 우상단 위치 옵션.  |
| 2     | JS\_NAVIGATION\_LB | 좌하단 위치 옵션.  |
| 3     | JS\_NAVIGATION\_RB | 우하단 위치 옵션.  |

```javascript
Module.getNavigation().setNaviPos(Module.JS_NAVIGATION_LT);
```

## Navigation Visible Type List

| Index | Name              | Description             |
| ----- | ----------------- | ----------------------- |
| 0     | JS\_VISIBLE\_ON   | 네비게이션(나침판) 가시화 활성화.     |
| 1     | JS\_VISIBLE\_OFF  | 네비게이션(나침판) 가시화 비 활성화.   |
| 2     | JS\_VISIBLE\_AUTO | 네비게이션(나침판) 간소화 가시화 활성화. |

```javascript
Module.getNavigation().setNaviVisible(Module.JS_VISIBLE_ON);
```

## Mouse Type List

| Index | Name                            | Description         |
| ----- | ------------------------------- | ------------------- |
| 0     | MML\_NONE                       | 기본                  |
| 1     | MML\_MOVE\_GRAB                 | 지도 이동               |
| 6     | MML\_SELECT\_POINT              | 포인트 선택              |
| 7     | MML\_SELECT\_FACE               | 면 선택                |
| 9     | MML\_SELECT\_RECT               | 사각 선택               |
| 10    | MML\_SELECT\_CIRCLE             | 반경 선택               |
| 11    | MML\_SELECT\_POLY               | 폴리곤 선택              |
| 13    | MML\_SELECT\_ROOF               | 지붕 선택               |
| 14    | MML\_SELECT\_EXCLUDE\_ROOF      | 지붕 제외지역 선택          |
| 20    | MML\_INPUT\_POINT               | 점 입력                |
| 21    | MML\_INPUT\_LINE                | 라인 입력               |
| 22    | MML\_INPUT\_RECT                | 사각 입력(정북방향)         |
| 23    | MML\_INPUT\_CIRCLE              | 원 입력                |
| 24    | MML\_INPUT\_AREA                | 영역 입력               |
| 25    | MML\_INPUT\_SPHERE              | 구 입력                |
| 27    | MML\_INPUT\_RECT\_SCREEN        | 사각 입력 상태            |
| 80    | MML\_ANALYS\_AREA               | 면적 계산               |
| 81    | MML\_ANALYS\_DISTANCE           | 거리 계산               |
| 82    | MML\_ANALYS\_VIEWSHED           | 가시권 분석              |
| 84    | MML\_ANALYS\_JOMANG             | 조망 가시화              |
| 85    | MML\_VIEW\_UNDERGROUND          | 지하 시설물 가시화          |
| 86    | MML\_ANALYS\_ALTITUDE           | 높이 측정               |
| 87    | MML\_ANALYS\_DISTANCE\_STRAIGHT | 직선거리계산              |
| 88    | MML\_ANALYS\_AREA\_PLANE        | 면적계산(일반 평면, RTT미적용) |
| 89    | MML\_ANALYS\_AREA\_CIRCLE       | 수직 평면 객체 반경 계산      |
| 94    | MML\_ANALYS\_JOMANGPOINT        | 조망점 관리              |
| 101   | MML\_FIGURE\_RECT               | 사각 박스 입력            |
| 102   | MML\_FIGURE\_ELLIPSE            | 구 객체 입력             |
| 103   | MML\_FIGURE\_ARROW              | 화살표 객체 입력           |
| 104   | MML\_FIGURE\_ARROW\_DUEL        | 양방향 화살표 다면체 입력      |
| 105   | MML\_FIGURE\_CONVEX             | 볼록형 다면체 입력          |
| 106   | MML\_FIGURE\_CONCAVE            | 오목형 다면체 입력          |
| 107   | MML\_FIGURE\_ROUND\_RECT        | 사각 라운드 육면체 입력       |
| 108   | MML\_FIGURE\_BEARING\_ARC       | 베어링 형 다면체 입력        |
| 109   | MML\_FIGURE\_STAR               | 별 형 다면체 입력          |
| 110   | MML\_FIGURE\_PLUS               | 더하기 기호 다면체 입력       |
| 200   | MML\_ADD\_SOLAR\_PANEL          | 벽면에 판넬 추가(태양광 모드)           |
| 201   | MML\_SELECT\_EDIT\_MODULE       | 벽면의 편집 판넬 선택(태양광 모드)     |
| 202   | MML\_EDIT\_SOLAR\_MODULE        | 지붕 판넬 추가 및 삭제(태양광 모드) |

```javascript
Module.XDSetMouseState(Module._NONE);
```

## Coordinate Type List

| Index | Name                      | Description |
| ----- | ------------------------- | ----------- |
| 13    | Latitude/Logitude (WGS84) | EPSG:4326.  |
| 14    | Korea TM BESSEL(West)     | EPSG:5186.  |
