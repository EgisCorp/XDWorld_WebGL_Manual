# 1.6x 버전 업데이트

## 추가된 클래스

## 추가된 API

-   Module.getOption().setHybridRenderType(number)
-   Module.getViewCamera().moveLeftRight(number)
-   Module.getOption().object_ahead
-   Module.createBillboard("id").setVerticalLine(parameter);
-   JSHTMLObject.position;
-   JSPolygon.createWithFaces()

## 변경된 API

## 샌드박스 업데이트 내역

## - 업데이트 내역 -

### 2.5.1 (2024/08/09)

#### 1. JSHTMLObject 이동 기능 추가

-   JSHTMLObject 내부 변수 "position"을 통해 현재 위치와, 변경 위치 설정하는 변수가 추가되었습니다.
    ```javascript
    // Get
    let position = htmlObject.position;
    // Set
    let position = new Module.JSVector3D(lon, lat, alt);
    htmlObject.position = position;
    ```
-   입력, 출력은 경위도 값이 기준입니다.

#### 2. POI 가시범위 API 기능 개선 확장

-   JSPoint에 개선된 가시범위 설정 API가 추가되었습니다.
    ```javascript
    // 가시 범위 설정 예시
    poi.setRange({
        enable: true, // 가시 범위 사용 여부 setVisibleRange의 bEnable 파라메터와 동일
        min: 1.0, // 가시 범위 최소 범위 setVisibleRange의 dMin 파라메터와 동일
        max: 1000.0, // 가시 범위 최대 범위 setVisibleRange의 dMax 파라메터와 동일
        textMin: 1.0, // 가시 범위 텍스트 최소 범위 min 과 같거나 커야함
        textMax: 300.0, // 가시 범위 텍스트 최대 범위 max 과 같거나 작아야함
    });
    ```
-   기존 POI 객체 표현범위 설정 (Icon 기준)에서 Text에 대한 추가 표현 범위를 설정합니다.

#### 3. JSPipe 흐름 화살표 기능 개선

-   평면 형태의 화살표를 3차원 입체 구조로 개선하였습니다.
-   일부 지역에서 화살표 생성 시 방향이 올바르게 정렬되지 않는 현상을 수정하였습니다.
-   파이프 지점 높낮이에 따라 화살표의 틸트 각도가 함께 적용되도록 수정하였습니다.

#### 4. face 데이터로 JSPolygon을 생성하는 'JSPolygon.createWithFaces()' API 추가

-   사용자가 정의한 face 데이터를 기반으로 JSPolygon을 생성하는 기능이 추가되었습니다.
-   사용자는 형식에 맞춘 JSON 데이터를 파라메터로 전달함으로써, JSPolygon을 생성할 수 있습니다.
-   자세한 사용법은 샌드박스 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_faces_to_polygon)를 참고하시기 바랍니다.

```javascript
let parameter = {
	upVector: /*업벡터 좌표축*/,
	cullMode: /*버텍스 정의 방향*/,
	position: /*모델 중심 위치*/,
	moveOffset: /*위치 오프셋(세부 조정)*/,
	faceInfo: [
		{
			vertex: /*버텍스 위치*/,
			matrix: /*변환(4x4 행렬)*/,
			indexVertex: /*버텍스 인덱스*/,
			indexUV: /*텍스처 좌표 인덱스*/,
			uv: /*실제 텍스처 좌표*/,
			normal: /*노멀 벡터*/,
			color: /*색상*/
		}
	]
}
polygon.createWithFaces(parameter);
```

### 2.5.0 (2024/7/26)

#### 1. 웹 워커 기능 개선

-   기능 개선 및 파일 용량을 감소하여 기능 개선하였습니다.

#### 2. 도로 시설물 생성 기능 개선

-   도로 시설물 중 교량의 교각이 일정 높이 이하인 부분은 생성이 되지 않도록 예외처리 단계가 추가되었습니다.

#### 3. 빌보드 수직선 옵션 추가

-   빌보드 중심을 기준으로, 지면까지의 수직선을 생성 및 수정하는 API가 추가되었습니다.
    ```javascript
    parameter = {
        visible: true, // 가시화 여부(기본값: false)
        width: 10.0, // 수직선 두께(기본값: 1.0)
        color: JSColor(255, 15, 100, 200), // 수직선 색상(기본값: JSColor(255, 255, 255, 255))
        altitude: 30.0, // 수직선 끝점 고도(기본값: 0)
    };
    billboard.setVerticalLine(parameter);
    ```
-   성공적으로 생성/수정하였을 경우 true를 반환합니다.
-   API의 자세한 사용법은 샌드박스 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_billboard_line)를 확인해주시기 바랍니다.

#### 4. 지형의 0레벨 지구본 위성영상 자체 포함

-   0레벨에 대한 지구본 위성영상을 자체 포함하도록 적용 되었습니다.
-   지도 서버에 연결이 정상적이 않아도 지구본은 기본적으로 구성됩니다.
-   0 레벨 요청을 실패하여 반복적 네트워크 요청을 처리하지 않습니다.
-   엔진의 파일용량이 소폭 증가합니다.

### 2.4.0 (2024/6/28)

#### 1. 화면 분할 시 잔상이 남는 현상 수정

-   지형 투명도 조절과 함께 화면 분할 기능 사용 시 분할 화면에 잔상이 남는 현상을 수정하였습니다.
-   화면 분할 기능 사용 시 레이어 배치 방향이 반대로 보이는 점을 확인하여 수정하였습니다.

#### 2. Camera Quake의 진동 오류 수정

-   Camera Quake(카메라 흔들림)기능에서, 진동 주기가 초단위로 적용되는 오류를 수정하였습니다.

#### 3. JSFlowPolygon 객체 색상 설정 오류 수정

-   create API 실행 전 color 속성 설정 시 값이 정상적으로 반영되지 않는 현상을 수정하였습니다.

#### 4. 전광판, 비디오 객체 기능 개선

-   사용자 편의성을 위해 객체 생성 이후의 기능들 엔진 내부에 삽입 및 속도개선되었습니다.
-   기존 비디오 텍스쳐 관련 기능은 2024년까지 지원합니다.
-   새로운 사용법은 [비디오텍스쳐](https://sandbox.egiscloud.com/code/main.do?id=object_video)를 참고하시기 바랍니다.

#### 5. WMS 로딩 방식 선택

-   사용자의 통신 환경과 WMS 및 하이브리드 상태에 따라 선택 가능하도록 API가 추가되었습니다.

```javascript
// Default : 0
//Module.getOption().setHybridRenderType(0);   // 기존과 동일
Module.getOption().setHybridRenderType(1); // 변경된 순서에 따라 바로 반영
```

#### 6. 장해물 판별 기능 추가

-   카메라와 JSPoint, JSHTMLObject 객체 사이에 장해물(지형, 시설물) 존재 시 가시화 유무를 설정하는 변수를 추가 하였습니다.

```javascript
Module.getOption().object_ahead = 0; 기존 방식(장해물 미판정)
Module.getOption().object_ahead = 1; 장해물에 따른 가시화 설정
```

#### 7. 카메라 좌/우 이동 API 추가

-   카메라 이동 함수 moveLeftRight가 추가되었습니다.
-   지정한 값 만큼 카메라가 좌/우 방향으로 이동합니다.

```javascript
Module.getViewCamera().moveLeftRight(0.01);
Module.getViewCamera().moveLeftRight(-0.01);
```

#### 8. 레이어 화면 분할 렌더링 기능 오류 수정

-   화면 분할 기능 사용 시 좌/우 방향이 반대로 적용되는 현상을 수정하였습니다.
-   화면 분할 후 특정 화면에서 화면의 잔상이 남는 현상을 수정하였습니다 [이슈 #401](https://github.com/EgisCorp/XDWorld/issues/401)

### 2.3.1 (2024/5/31)

#### 1. (중요)glTF 최적화(WebWorker)

-   glTF 포맷과 관련하여, WebWorker가 업데이트 되었습니다.
-   업데이트된 WebWorker 빌드 파일의 사용을 권장합니다.

#### 2. JSColorGrid3D 오브젝트 속성 반환 함수 추가

-   JSColorGrid3D 오브젝트의 속성 반환 함수가 추가되었습니다.
-   [getCellBox] 인덱스에 해당하는 셀의 박스 좌표 정보를 반환합니다.
    -   박스 좌표는 상단/하단, 좌/우, 위/아래로 구분되는 좌표 8개를 반환합니다.
    -   반환 되는 박스의 좌표 속성 값의 순서는 아래와 같습니다.
        -   0 : upLeftTop
        -   1 : upRightTop
        -   2 : upRightBottom
        -   3 : upLeftBottom
        -   4 : downLeftTop
        -   5 : downRightTop
        -   6 : downRightBottom
        -   7 : downLeftBottom
    ```javascript
    var cellBox = grid.getCellBox(20, 12);
    ```
-   [getCellHeight] 인덱스에 해당하는 셀의 높이 값을 반환합니다.
    ```javascript
    var height = grid.getCellHeight(20, 12);
    ```
-   [getCellWidthCount] 그리드의 가로 셀 수를 반환합니다.
    ```javascript
    var widthCellCount = grid.getCellWidthCount();
    ```
-   [getCellHeightCount] 그리드의 세로 셀 수를 반환합니다.
    ```javascript
    var heightCellCount = grid.getCellHeightCount();
    ```

### 2.3.0 (2024/5/24)

#### 1. JSColorGrid 오브젝트 반환 기능 추가

-   JSLayer의 오브젝트 반환 시 JSColorGrid 오브젝트도 반환 가능하도록 기능을 추가하였습니다.

#### 2. 수인한도분석 진행률 반환 기능 추가

-   CJSAnalysisGridShadow::prograss 분석 진행률을 반환하는 callback 함수를 추가하였습니다.

#### 3. 수인한도분석 배척격자 오류 수정

-   배척격자가 그림자를 생성하거나, 선택이 되지 않는 오류가 수정되었습니다.

#### 4. JSPolygon으로 고스트 심볼 생성하는 기능 추가

-   고스트 심볼을 생성할 때 외부에서 모델 파일을 입력해주는 대신, 미리 생성한 JSPolygon으로 정의가 가능하도록 `JSGhostSymbolMap.insert()`에 `polygon`인자를 추가하였습니다.
-   자세한 사용법은 [샌드박스 - Ghostsymbol(Polygon)](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_to_ghost_symbol)을 참고해주시기 바랍니다.

### 2.2.2 (2024/5/3)

#### 1. WMS 오류 해결

-   WMS 기능을 사용할 때, 깜박거리는 현상이 수정되었습니다.
