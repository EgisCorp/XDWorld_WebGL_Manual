# 1.6x 버전 업데이트

## 추가된 클래스

## 추가된 API

## 변경된 API

## 샌드박스 업데이트 내역

## - 업데이트 내역 -

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
