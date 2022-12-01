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

| Index | Name                            | Description  |
| ----- | ------------------------------- | ------------ |
| 0     | MML\_NONE                       | 기본           |
| 1     | MML\_MOVE\_GRAB                 | 지도 이동        |
| 2     | MML\_ZOOMIN\_RECT               | 영역 확대        |
| 3     | MML\_ZOOMIN\_POINT              | 지도 확대        |
| 4     | MML\_ZOOMOUT\_RECT              | 영역 축소        |
| 5     | MML\_ZOOMOUT\_POINT             | 지도 축소        |
| 6     | MML\_SELECT\_POINT              | 포인트 선택       |
| 7     | MML\_SELECT\_FACE               | 면 선택         |
| 8     | MML\_SCREEN\_RECT               | 화면 사각 선택     |
| 9     | MML\_SELECT\_RECT               | 사각 선택        |
| 10    | MML\_SELECT\_CIRCLE             | 반경 선택        |
| 11    | MML\_SELECT\_POLY               | 폴리곤 선택       |
| 12    | MML\_MOVE\_GRAB\_EX             | 클릭 시 이동 금지   |
| 20    | MML\_INPUT\_POINT               | 점 입력         |
| 21    | MML\_INPUT\_LINE                | 라인 입력        |
| 22    | MML\_INPUT\_RECT                | 사각 입력(정북방향)  |
| 23    | MML\_INPUT\_CIRCLE              | 원 입력         |
| 24    | MML\_INPUT\_AREA                | 영역 입력        |
| 25    | MML\_INPUT\_SPHERE              | 구 입력         |
| 26    | MML\_INPUT\_LINE\_DRAG          | 마우스 드래그 입력   |
| 27    | MML\_INPUT\_RECT\_SCREEN        | 사각 입력 상태     |
| 40    | MML\_OBJECT\_INSERT             | 객체 삽입(3ds..) |
| 41    | MML\_OBJECT\_MOVE\_XZ           | 선택 객체 이동     |
| 42    | MML\_OBJECT\_MOVE\_YZ           | 선택 객체 이동     |
| 43    | MML\_OBJECT\_ROTATE             | 선택 객체 회전     |
| 44    | MML\_OBJECT\_SCALE              | 선택 객체 크기 조정  |
| 45    | MML\_OBJECT\_SCALE\_Y           | 선택 객체 크기 조정  |
| 46    | MML\_OBJECT\_SCALE\_XZ          | 선택 객체 크기 조정  |
| 50    | MML\_DRAW\_CUBE                 | 박스 입력        |
| 51    | MML\_DRAW\_CYLINDER             |              |
| 52    | MML\_DRAW\_SPHERE               |              |
| 53    | MML\_DRAW\_CON                  |              |
| 54    | MML\_DRAW\_PIPE                 |              |
| 55    | MML\_DRAW\_DOME                 |              |
| 56    | MML\_DRAW\_POLYHEAD             |              |
| 57    | MML\_DRAW\_ARROW                |              |
| 70    | MML\_VERTEX\_MOVE               |              |
| 71    | MML\_VERTEX\_ADD                |              |
| 72    | MML\_VERTEX\_REMOVE             |              |
| 80    | MML\_ANALYS\_AREA               | 면적 계산        |
| 81    | MML\_ANALYS\_DISTANCE           | 거리 계산        |
| 82    | MML\_ANALYS\_VIEWSHED           | 가시권 분석       |
| 83    | MML\_ANALYS\_SLICE              | 단면도 분석       |
| 84    | MML\_ANALYS\_JOMANG             | 조망 가시화       |
| 85    | MML\_VIEW\_UNDERGROUND          | 지하 시설물 가시화   |
| 86    | MML\_ANALYS\_ALTITUDE           | 높이 측정        |
| 87    | MML\_ANALYS\_DISTANCE\_STRAIGHT |              |
| 88    | MML\_ANALYS\_AREA\_PLANE        |              |
| 89    | MML\_ANALYS\_AREA\_CIRCLE       |              |
| 90    | MML\_UI\_MEMO                   | 메모 기능        |
| 94    | MML\_ANALYS\_JOMANGPOINT        | 조망점 관리       |
| 96    | MML\_SELECT\_MULTIFACE          |              |
| 101   | MML\_FIGURE\_RECT               | 사각 박스 가시화    |
| 102   | MML\_FIGURE\_ELLIPSE            | 구 객체 가시화     |
| 103   | MML\_FIGURE\_ARROW              | 화살표 객체 가시화   |
| 104   | MML\_FIGURE\_ARROW\_DUEL        |              |
| 105   | MML\_FIGURE\_CONVEX             |              |
| 106   | MML\_FIGURE\_CONCAVE            |              |
| 107   | MML\_FIGURE\_ROUND\_RECT        |              |
| 108   | MML\_FIGURE\_BEARING\_ARC       |              |
| 109   | MML\_FIGURE\_STAR               | 별 객체 가시화     |
| 110   | MML\_FIGURE\_PLUS               |              |
| 111   | MML\_FIGURE\_TEXTURE\_RECT      |              |
| 200   | MML\_ADD\_SOLAR\_PANEL          |              |
| 201   | MML\_SELECT\_EDIT\_MODULE       |              |
| 202   | MML\_EDIT\_SOLAR\_MODULE        |              |
| 300   | MML\_OBJECT\_EDIT               |              |

```javascript
Module.XDSetMouseState(Module._NONE);
```

## Coordinate Type List

| Index | Name                      | Description |
| ----- | ------------------------- | ----------- |
| 13    | Latitude/Logitude (WGS84) | EPSG:4326.  |
| 14    | Korea TM BESSEL(West)     | EPSG:5186.  |
