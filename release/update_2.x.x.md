# 1.6x 버전 업데이트

## 추가된 클래스

## 추가된 API

## 변경된 API

## 샌드박스 업데이트 내역

## - 업데이트 내역 -

### 2.4.0 (2024/6/28)

#### 1. 화면 분할 시 잔상이 남는 현상 수정
  * 지형 투명도 조절과 함께 화면 분할 기능 사용 시 분할 화면에 잔상이 남는 현상을 수정하였습니다.
  * 화면 분할 기능 사용 시 레이어 배치 방향이 반대로 보이는 점을 확인하여 수정하였습니다.

#### 2. Camera Quake의 진동 오류 수정
  * Camera Quake(카메라 흔들림)기능에서, 진동 주기가 초단위로 적용되는 오류를 수정하였습니다.

#### 3. JSFlowPolygon 객체 색상 설정 오류 수정
  * create API 실행 전 color 속성 설정 시 값이 정상적으로 반영되지 않는 현상을 수정하였습니다.

#### 4. 전광판, 비디오 객체 기능 개선 
  * 사용자 편의성을 위해 객체 생성 이후의 기능들 엔진 내부에 삽입 및 속도개선되었습니다.
  * 기존 비디오 텍스쳐 관련 기능은 2024년까지 지원합니다.
  * 새로운 사용법은 [비디오텍스쳐](https://sandbox.egiscloud.com/code/main.do?id=object_video)를 참고하시기 바랍니다.

#### 5. WMS 로딩 방식 선택
  * 사용자의 통신 환경과 WMS 및 하이브리드 상태에 따라 선택 가능하도록 API가 추가되었습니다.
  ``` javascript
  // Default : 0
  //Module.getOption().setHybridRenderType(0);   // 기존과 동일
  Module.getOption().setHybridRenderType(1);   // 변경된 순서에 따라 바로 반영
  ```

#### 6. 장해물 판별 기능 추가
 * 카메라와 JSPoint, JSHTMLObject 객체 사이에 장해물(지형, 시설물) 존재 시 가시화 유무를 설정하는 변수를 추가 하였습니다.
  ```javascript
  Module.getOption().object_ahead = 0; 기존 방식(장해물 미판정)
  Module.getOption().object_ahead = 1; 장해물에 따른 가시화 설정
  ```

#### 7. 카메라 좌/우 이동 API 추가
  * 카메라 이동 함수 moveLeftRight가 추가되었습니다.
  * 지정한 값 만큼 카메라가 좌/우 방향으로 이동합니다.
  ``` javascript
  Module.getViewCamera().moveLeftRight(0.01);
  Module.getViewCamera().moveLeftRight(-0.01);
  ```

#### 8. 레이어 화면 분할 렌더링 기능 오류 수정
  * 화면 분할 기능 사용 시 좌/우 방향이 반대로 적용되는 현상을 수정하였습니다.
  * 화면 분할 후 특정 화면에서 화면의 잔상이 남는 현상을 수정하였습니다 [이슈 #401](https://github.com/EgisCorp/XDWorld/issues/401)

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
