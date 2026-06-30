---
description: Fire_이벤트 정리
---

# EVENT

## 기본 Event

> HTML Canvas 이벤트 등록으로 엔진과 연동되는 이벤트

```javascript
var canvas = document.createElement('canvas');
canvas.id = "canvas";
	
canvas.addEventListener("Fire_~~~~", function(e){
		// 기능 구현
});
```

| Index | Name                      | Description       |
| ----- | ------------------------- | ----------------- |
| 0     | Fire\_MouseDown | 마우스 Down 시 이벤트 |
| 1     | Fire\_MouseUp | 마우스 Up 시 이벤트 |
| 2     | Fire\_MouseMove | 마우스 이동 시 이벤트 |
| 3     | Fire\_MouseWheel | 마우스 휠 시 이벤트 |
| 4     | Fire\_RMouseDown | 마우스 RB Down 시 이벤트 |
| 5     | Fire\_RMouseUp | 마우스 RB Up 시 이벤트 |
| 6     | Fire\_click | 마우스 LB 클릭(Down) 시 이벤트 |
| 7     | Fire\_dblClick | 마우스 LB 더블 클릭 시 이벤트|
| 8     | Fire\_EventMouseMove | 마우스 이동 시 이벤트???? |
| 9     | Fire\_EventMouseDrag | 마우스 드래그 시 이벤트???? |
| 10    | Fire\_EventClickPosition | 특정 지점 클릭(Down-Up) 시 이벤트 |
| 11    | Fire\_EventRotateCompass  | 나침반 회전 시 이벤트      |
| 12    | Fire\_EventCameraMoveEnd  | 카메라 이동 종료 시 이벤트   |
| 13    | Fire\_JSEventResize       | 캔버스 리사이즈 시 이벤트    |
| 14    | Fire\_EventAddRadius      | 수직 평면 반경 생성 시 이벤트 |
| 15    | Fire\_EventAddDistancePoint      | 거리 측정 값 반환 시 이벤트 |
| 16    | Fire\_EventAddAreaPoint      | 면적 측정 값 반환 시 이벤트 |
| 17    | Fire\_EventSelectedObject | 객체 선택 시 이벤트       |
| 18    | Fire\_EventSelectedMultiObject | 다중 객체 선택 시 이벤트 |
| 19    | Fire\_EventAddAltitudePoint      | 높이 측정 값 반환 시 이벤트 |
| 20    | Fire\_EventFinishAutoMove | 카메라 자동 이동 종료 이벤트 |
| 21    | Fire\_EventFinishTransparencyAutoMove      | 터파기 자동 이동 종료 시 이벤트 |
| 22    | Fire\_EventSimulationTime | 그림자 시뮬레이션 시 이벤트 |
| 23    | Fire\_EventErrorGL | 그림자 시뮬레이션 에러 시 이벤트 |
| 24    | Fire\_EventCompleteGridData | 서버 기반 경사도/경사향 분석 완료 시 이벤트 |
| 25    | Fire\_EventCompleteShadowSimulation      | 일조 분석(그림자) 시뮬레이션 종료 시 이벤트 |
| 26    | Fire\_EventCurrentTime | 일조 분석(그림자) 시뮬레이션 시 이벤트|
| 27    | Fire\_EventBinaryTextureLoad | 바이너리 텍스처 지정 폴리곤 생성 시 이벤트 |
| 28   | Fire\_EventTyphoonMoveFinished | 태풍 이동 종료 이벤트 |
| 29   | Fire\_EventAnalysisPos | 분석 지점 선택 시 이벤트 |
| 30   | Fire\_EventWMTSRequest | 타일 메쉬 생성 시 이벤트 |
| 31   | Fire\_EventCreateBoundBox | 타일 메쉬 생성 시 이벤트(BoundBox 가시화) |
| 32   | Fire\_EventCreateBox | 타일 메쉬 생성 시 이벤트(Box 가시화) |

### Fire_MouseDown
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| nMouse  | int  | 마우스 버튼(0: LB, 1: MB, 2: RB) |
| nButton | int  | 키보드 입력(Shift: +1, Ctrl: +2, Alt: +4) |
| x       | long | 마우스 위치의 X 좌표 |
| y       | long | 마우스 위치의 Y 좌표 |

### Fire_MouseUp
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| nMouse  | int  | 마우스 버튼(0: LB, 1: MB, 2: RB) |
| nButton | int  | 키보드 입력(Shift: +1, Ctrl: +2, Alt: +4) |
| x       | long | 마우스 위치의 X 좌표 |
| y       | long | 마우스 위치의 Y 좌표 |

### Fire_MouseMove
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| nMouse  | int  | 마우스 버튼(0: LB, 1: MB, 2: RB) |
| nButton | int  | 키보드 입력(Shift: +1, Ctrl: +2, Alt: +4) |
| x       | long | 마우스 위치의 X 좌표 |
| y       | long | 마우스 위치의 Y 좌표 |

### Fire_MouseWheel
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| nFlags  | int  | 0 |
| nZDelta | int  | 마우스 휠 회전 방향(화면 방향으로: -1, 사용자 방향으로: 1) |
| x       | long | 마우스 위치의 X 좌표 |
| y       | long | 마우스 위치의 Y 좌표 |

### Fire_RMouseDown
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| nMouse  | int  | 마우스 버튼(0: LB, 1: MB, 2: RB) |
| nButton | int  | 키보드 입력(Shift: +1, Ctrl: +2, Alt: +4) |
| x       | long | 마우스 위치의 X 좌표 |
| y       | long | 마우스 위치의 Y 좌표 |

### Fire_RMouseUp
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| nMouse  | int  | 마우스 버튼(0: LB, 1: MB, 2: RB) |
| nButton | int  | 키보드 입력(Shift: +1, Ctrl: +2, Alt: +4) |
| x       | long | 마우스 위치의 X 좌표 |
| y       | long | 마우스 위치의 Y 좌표 |

### Fire_click
* 변수 제공 안함

### Fire_dblClick
* 변수 제공 안함

### Fire_EventMouseMove
* Module.getOption().setEventMouseMove(true); 설정 필요
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| dLon    | double  | 마우스 지점의 경도 |
| dLat    | double  | 마우스 지점의 위도 |

### Fire_EventMouseDrag
* Module.getOption().setEventMouseMove(true); 설정 필요
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| dLon    | double  | 마우스 지점의 경도 |
| dLat    | double  | 마우스 지점의 위도 |

### Fire_EventClickPosition
* Mouse Type : MML_MOVE_GRAB
|변수 이름 | 자료형 | 상세 설명|
| ------- | -----| ------------------- |
| dLon    | double  | 클릭한 지점의 경도 |
| dLat    | double  | 클릭한 지점의 위도 |
| dAlt    | double  | 클릭한 지점의 고도 |

### Fire_EventSelectedObject
|변수 이름 | 자료형 | 상세 설명|
| ------------- | ------------- | ------------------- |
| layerName     | string        | 레이어 명             |
| objKey        | string        | 오브젝트 키           |
| dataFile      | string        | 실제 객체의 파일 명    |
| objID         | unsigned int  | 오브젝트 ID           |
| objType       | unsigned char | 오브젝트 타입          |
| idx           | int           | 메쉬의 X id           |
| idy           | int           | 메쉬의 Y id           |
| iLevel        | int           | 메쉬 레벨             |
| objVersion    | unsigned int  | 오브젝트 버전          |
| bIsReal3D     | bool          | read3d 여부           |
| instanceIndex | unsigned int  | 인스턴스 오브젝트 인덱스 |
| instanceId    | string        | 인스턴스 오브젝트 ID    |

### Fire_EventSelectedMultiObject
| 변수 이름 | 자료형 | 상세 설명       |
| -------- | ----- | -------------- |
| selected | array | 선택된 객체 배열 |

### Fire_EventRotateCompass
|변수 이름 | 자료형 | 상세 설명|
| ----- | ------------------------- | ----------------- |
| dCameraHeadAngle | double | 나침반(네비게이션) 방향 각도(Degree) |

### Fire_EventCameraMoveEnd
|변수 이름   | 자료형  |   상세 설명 |
| --------- | ------ | --------- |
| longitude | double | 카메라 경도 |
| latitude  | double | 카메라 위도 |
| altitude  | double | 카메라 고도 |

### Fire_KeyDown
|변수 이름 | 자료형  |   상세 설명 |
| ------- | ------ | --------- |
| nChar   | int |  |
| nFlag   | int | 0 |

### Fire_KeyUp
|변수 이름 | 자료형  |   상세 설명 |
| ------- | ------ | --------- |
| nChar   | int | 키 코드 |
| nFlag   | int | 0 |

### Fire_JSEventResize
* 변수 제공 안함

### Fire_EventAddRadius
* Mouse Type : MML_MOVE_GRAB
|변수 이름        | 자료형  |   상세 설명 |
| -------------- | ------ | --------- |
| dLon           | double | 클릭 지점의 경도 |
| dLat           | double | 클릭 지점의 위도 |
| dAlt           | double | 클릭 지점의 고도 |
| dMidLon        | double | 라인의 중심 경도 |
| dMidLat        | double | 라인의 중심 위도 |
| dMidAlt        | double | 라인의 중심 고도 |
| dTotalDistance | double | 라인의 총 길이 |

### Fire_EventAddDistancePoint
|변수 이름 | 자료형 | 상세 설명|
| ----- | ------------------------- | ----------------- |
| dDistance | double | 부분 측정 거리 값(이전 입력점과 마지막 입력점 간의 거리, m 단위) |
| dTotalDistance | double | 전체 측정 거리 값(첫 입력점과 마지막 입력점 간의 거리, m 단위) |
| dMidLon | double | 부분 측정 거리 값 표시 경도 (Degree 단위) |
| dMidLat | double | 부분 측정 거리 값 표시 위도 (Degree 단위) |
| dMidAlt | double | 부분 측정 거리 값 표시 고도 (m 단위) |
| dLon | double | 전체 측정 거리 값 표시 경도 (Degree 단위) |
| dLat | double | 전체 측정 거리 값 표시 위도 (Degree 단위) |
| dAlt | double | 전체 측정 거리 값 표시 고도 (m 단위) |
		
### Fire_EventAddAreaPoint
|변수 이름 | 자료형 | 상세 설명|
| ----- | ------------------------- | ----------------- |
| dArea | double | 면적 측정 값 (제곱 m 단위) |
| dLon | double | 면적 측정 표시 경도 (Degree 단위) |
| dLat | double | 면적 측정 표시 위도 (Degree 단위) |
| dAlt | double | 면적 측정 표시 고도 (m 단위) |

### Fire_EventAddAltitudePoint
|변수 이름 | 자료형 | 상세 설명|
| ----- | ------------------------- | ----------------- |
| dGroundAltitude | double | 해발 고도 측정 값 (m 단위) |
| dObjectAltitude | double | 지형에서 부터 선택 지점까지의 높이 측정 값 (m 단위) |
| dLon | double | 높이 측정 표시 경도(Degree 단위) |
| dLat | double | 높이 측정 표시 위도(Degree 단위) |
| dAlt | double | 높이 측정 표시 고도(m 단위) |

### Fire_EventFinishAutoMove
* 변수 제공 안함

### Fire_EventSimulationTime
|변수 이름 | 자료형 | 상세 설명|
| ----- | --- | ----------------- |
| Year  | int | 시뮬레이션 시각(년) |
| Month | int | 시뮬레이션 시각(월) |
| Day   | int | 시뮬레이션 시각(일) |
| Hour  | int | 시뮬레이션 시각(시) |
| Min   | int | 시뮬레이션 시각(분) |
| Sec   | int | 시뮬레이션 시각(초) |

### Fire_EventErrorGL
|변수 이름 | 자료형 | 상세 설명|
| ----------- | ------------ | ----------------- |
| ErrorStatus | unsigned int | GL 에러 타입 |

### Fire__EventCompleteGridData
|변수 이름 | 자료형 | 상세 설명|
| ----------- | ------ | ------------- |
| strJSONData | string | 분석 결과 Json |

### Fire_EventFinishTransparencyAutoMove
* 변수 제공 안함

### Fire_EventCompleteShadowSimulation
* 변수 제공 안함

### Fire_EventCurrentTime
|변수 이름 | 자료형 | 상세 설명|
| ----- | --- | ---------------- |
| Year  | int | 시뮬레이션 시각(년) |
| Month | int | 시뮬레이션 시각(월) |
| Day   | int | 시뮬레이션 시각(일) |
| Hour  | int | 시뮬레이션 시각(시) |
| Min   | int | 시뮬레이션 시각(분) |
| Sec   | int | 시뮬레이션 시각(초) |

### Fire_EventBinaryTextureLoad
|변수 이름 | 자료형 | 상세 설명|
| --------- | ------ | --------- |
| objectKey | string | 오브젝트 키 |

### Fire_EventTyphoonMoveFinished
|변수 이름 | 자료형 | 상세 설명|
| --------- | ------ | --------- |
| objectKey | string | 오브젝트 키 |

### Fire_EventAnalysisPos
|변수 이름 | 자료형 | 상세 설명|
| --- | ------ | --------- |
| lon | double | 선택 지점 경도 |
| lat | double | 선택 지점 위도 |
| alt | double | 선택 지점 고도 |

### Fire_EventWMTSRequest
|변수 이름 | 자료형 | 상세 설명|
| ----- | ------ | --------- |
| lon1  | double | 매쉬 중심 경도 |
| lat1  | double | 메쉬 중심 위도 |
| lon2  | double | 매쉬 중심 경도 | 
| lat2  | double | 메쉬 중심 위도 |
| alt   | doubel | 메쉬 중심 고도 |
| level | int    | 메쉬 레벨     |
| idx   | int    | 메쉬 idx     |
| idy   | int    | 메쉬 idy      |

### Fire_EventCreateBox
|변수 이름 | 자료형 | 상세 설명|
| ------ | ------ | --------------- |
| lon0   | double | AABB 꼭짓점0 경도 |
| lat0   | double | AABB 꼭짓점0 위도 |
| lon1   | double | AABB 꼭짓점1 경도 |
| lat1   | double | AABB 꼭짓점1 위도 |
| lon2   | double | AABB 꼭짓점2 경도 |
| lat2   | double | AABB 꼭짓점2 위도 |
| lon3   | double | AABB 꼭짓점3 경도 |
| lat3   | double | AABB 꼭짓점3 위도 |
| minalt | double | 최소 고도         |
| maxalt | double | 최대 고도         |
| level  | int    | 메쉬 레벨         |
| idx    | int    | 메쉬 idx         |
| idy    | int    | 메쉬 idy         |

### Fire_EventCreateBoundBox
|변수 이름 | 자료형 | 상세 설명|
| ------ | ------ | --------------- |
| lon0   | double | Bound Box 꼭짓점0 경도 |
| lat0   | double | Bound Box 꼭짓점0 위도 |
| lon1   | double | Bound Box 꼭짓점1 경도 |
| lat1   | double | Bound Box 꼭짓점1 위도 |
| lon2   | double | Bound Box 꼭짓점2 경도 |
| lat2   | double | Bound Box 꼭짓점2 위도 |
| lon3   | double | Bound Box 꼭짓점3 경도 |
| lat3   | double | Bound Box 꼭짓점3 위도 |
| minalt | double | 최소 고도              |
| maxalt | double | 최대 고도              |
| level  | int    | 메쉬 레벨              |
| idx    | int    | 메쉬 idx              |
| idy    | int    | 메쉬 idy              |

## Ghost Symbol Event

> 고스트 심볼 이벤트 등록으로 엔진과 연동되는 이벤트

```javascript
var canvas = document.createElement('canvas');
canvas.id = "canvas";
canvas.addEventListener("Fire_GhostSymbolRegistComplete", function(e){
		// 기능 구현
});

~
Module.getGhostSymbolMap().addGhostSymbolBy3DS()
~
	
```

| Index | Name                            | Description     |
| ----- | ------------------------------- | --------------- |
| 0     | Fire\_GhostSymbolRegistComplete | 고스트 심볼 등록 시 이벤트 |
