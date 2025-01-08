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

### 2.10.1 (2025/01/03)

1. `createTMCoordPlane()` 기능 개선
    - `createTMCoordPlane()` API의 매개변수 정의 방식이 수정되었습니다. 자세한 사항은 아래 문서를 확인하여 주시기 바랍니다.
        - 변경된 양식
            ```Javascript
            JSPolygon.createTMCoordPlane({
                llcorner : {
                  coordCode : [좌표계코드, 필수],
                  x : [좌하단 X 좌표, 필수],
                  y : [좌하단 Y 좌표, 필수]
                },
                grid : {
                  col : [그리드 가로 총수, 필수],
                  row : [그리드 세로 총수, 필수],
                  cellSize : [그리드 셀의 가로 세로 크기, 필수],
                  ratioMode : [New 배율모드 사용 여부 0 - 기존 gab방식, 1 - 배율모드사용, 선택],
                  xSplit : [ New 가로 분할 배율, ratioMode  1일때 필수],
                  ySplit : [ New 세로 분할 배율, ratioMode  1일때 필수]
                }
              });
            ```
        - 사용 예시
            ```Javascript
            polygon.createTMCoordPlane({
              llcorner : {
                coordCode : 20,
                x : 216701.99445382116 ,
                y : 220328.8122727003
              },
              grid : {
                col : 644,
                row : 585,
                cellSize : 10,
                ratioMode : 1,
                xSplit : 10,
                ySplit : 10
              }
            });
            ```

### 2.10.0 (2024/12/27)

#### 1. `Stereo View` 모드의 로컬 레이어 오류 수정

-   `Stereo View` 모드에서 로컬 레이어를 사용할 경우, POI가 왼쪽 화면에만 그려지는 오류를 수정하였습니다.

### 2.9.2 (2024/12/16)

#### 1. `Real3D` 텍스처 요청 개수 제한 API 추가

-   `Real3D`에서 최대 텍스처 요청 개수를 제한할 수 있도록, `JSOption::setMaxRequestTextureQueueSize()` API가 추가되었습니다.

    | Name           | Type   | Description                                 |
    | -------------- | ------ | ------------------------------------------- |
    | maxTextureSize | number | <p>텍스처를 요청하는 최대 개수(1~20개).</p> |

    ```javascript
    Module.getOption().setMaxRequestTextureQueueSize(20); // 20개의 텍스쳐 요청
    ```

#### 2. `Real3D` 텍스처 레벨 고정 API 추가

-   `Real3D`에서 요청하는 텍스처 레벨을 고정할 수 있도록, `JSMap::fixedTextureLevel()` API가 추가되었습니다.

    | Name  | Type   | Description                       |
    | ----- | ------ | --------------------------------- |
    | level | number | <p>텍스처 요청하는 레벨(0~5).</p> |

    ```javascript
    Module.getMap().fixedTextureLevel(0); // 고정레벨 지정
    ```

### 2.9.1 (2024/12/06)

#### 1. glTF 모델의 회전 및 크기 조절 기능 추가

-   glTF 모델을 유연하게 사용할 수 있도록, 회전과 크기 조절 기능이 추가되었습니다.
-   회전의 경우 XYZ축을 기준으로 회전 각도를 조절할 수 있습니다.
    ```javascript
    var polygon = Module.createGLTF("GLTF_Object");
    polygon.loadFile({
        url: url,
        type: "glb",
        position: pos,
        rotate: [0, 90, 0], // XYZ 축 방향 회적 각도(Degree)
        scale: [1.0, 10.0, 1.0], // XYZ축 방향 스케일 변경. (1.0= 원래 크기)
        rebuild: true,
    });
    ```

#### 2. split view 하이브리드 가시화 기능 추가

-   하이브리드 모드가 `split view`에서도 정상적으로 보일 수 있도록 기능을 추가하였습니다.

#### 3. stereo view/split view 모드 오브젝트 렌더링 오류 수정

-   `stereo view/split view` 모드에서, 반투명한 상태의 오브젝트 출력이 제대로 되지 않는 오류를 수정하였습니다.

#### 4. JSPolygon::setHeightByType() API 추가

-   `type`에 따라 평면 폴리곤의 윗면을 생성하는 API를 추가하였습니다.

    | Name             | Type   | Description                                                                                                                               |
    | ---------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
    | heightOrAltitude | number | <p>버텍스에 적용할 높이 혹은 고도.</p><p>0일 경우: 높이로 사용.</p><p>1일 경우: 고도로 사용.</p>                                          |
    | type             | number | <p>윗면 생성 방식 설정.</p><p>0일 경우: 각 밑면 버텍스에서 height만큼 높인 윗면 생성.</p><p>1일 경우: 균일한 고도의 평평한 윗면 생성.</p> |

    ```javascript
    var polygon = Module.createPolygon("POLYGON");
    var vertex = new Module.JSVec3Array();
    var part = new Module.Collection();

    for (var i = 0; i < _vertex.length; i++) {
        for (var j = 0; j < _vertex[i].length; j++) {
            vertex.push(_vertex[i][j]);
        }
        part.add(_vertex[i].length);
    }
    polygon.setPartCoordinates(vertex, part);

    // Set as a polyhedron polygon with height
    // type == 0
    //polygon.setHeightByType(80, 0);
    // type == 1
    polygon.setHeightByType(120, 1);

    //...
    ```

### 2.9.0 (2024/11/29)

#### 1. Inspector 기능 항목 추가

-   기존 `Inspector` 기능에서, 지형 데이터(dem/image)를 요청하는 대기열의 크기를 확인할 수 있도록 수정하였습니다.
-   자세한 사용법은 [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=option_inspector)을 참고해주시기 바랍니다.

### 2.8.4_hotfix (2024/11/22)

#### 1. 깜박임 오류 수정

-   특정한 상황에서, 지도가 제대로 그려지지 않고 깜박이는 오류를 수정하였습니다.

#### 2. 건물 simple mode 옵션 추가

-   그라데이션 모드(아래에서부터 위로 점점 밝아지는 음영 효과)가 추가 되었습니다.
-   Light 방향을 조절할 수 있는 옵션이 추가되었습니다.

#### 3. HTMLObject의 element 속성 추가

-   `HTMLObject.element` 프로퍼티가 추가되었습니다.
-   자세한 사용법은 [메뉴얼](https://egiscorp.gitbook.io/xdworld-webgl-manual/introduce-1/object/jshtmlobject#properties)을 참고해주시기 바랍니다.

### 2.8.3_hotfix (2024/11/15)

#### 1. JSPolygon.setWaterEffect() 오류 수정

-   `JSPolygon`에서 setWaterEffect()를 호출시, 검은 배경이 나타나는 오류를 수정하였습니다.

### 2.8.2_hotfix (2024/11/08)

#### 1. glTF 애니메이션 오류 수정

-   특정 glTF 모델의 애니메이션이 정상적으로 재생되지 않는 오류를 해결하였습니다.

#### 2. `JSLayer`에 `object_ahead` 속성 추가

-   레이어 차원에서 `object_ahead` 옵션을 관리할 수 있도록, `JSLayer`의 속성이 추가되었습니다.
-   사용법
    1. 먼저 해당 옵션을 사용하기 위해, `JSOption.object_ahead` 를 `true`로 설정하여야 합니다.
    2. `JSOption`와 `JSLayer`의 `object_ahead` 가 모두 `true`일 경우, 해당 레이어에 속한 3d point 오브젝트에 옵션이 적용됩니다.
    -   `JSOption`의 `object_ahead` 가 `true`여도 `JSLayer` 의 `object_ahead` 가 `false`이면 옵션이 적용되지 않습니다.
-   `object_ahead` 란?
    -   (카메라 기준)지형 및 시설물(건물)이 3d point 오브젝트보다 가까이 있을 경우, 오브젝트가 가려지도록 하는 옵션
    -   자세한 사용법은 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_ahead)를 참고해주시기 바랍니다.
-   주의 사항
    -   `JSLayer.object_ahead` 속성은 `ELT_3DPOINT` 레이어에만 적용됩니다. 다른 속성의 레이어에서는 `JSOption.object_ahead`을 사용해주시기 바랍니다.

### 2.8.1_hotfix (2024/11/01)

#### 1. JSTraceTarget의 glTF 애니메이션 포맷 지원

-   JSTraceTarget에서 애니메이션이 포함된 glTF 포맷을 지원하도록 기능이 확장되었습니다.

#### 2. Real3DPack의 객체 버전 확장 적용

-   Real3DPack 레이어가 다양한 버전의 객체를 사용할 수 있도록 기능이 확장되었습니다.

### 2.8.0 (2024/10/25)

#### 1. 지형과 알파 값이 있는 객체 간의 렌더링 순서 정리

-   지형과 알파(투명) 값이 존재하는 객체들과의 가시화가 어색하지 않도록, 렌더링 순서를 변경하였습니다.

#### 2. 파이프 색상 변경 오류 수정

-   간소화 상태에서 파이프 색상 변경 시 색상 값이 정상적으로 적용되지 않는 현상을 수정하였습니다.

#### 3. 외부 폰트 기반 POI Text 이미지 생성시 발생하는 오류 수정

-   Text 이미지 생성이 정상적으로 작동되지 않는 현상을 수정하였습니다.

#### 4. 소형 시설물의 LOD Texture 미적용 오류 수정

-   카메라 거리에 따른 시설물 LOD 변경 기능이 동작되지 않는 현상을 수정하였습니다.

#### 5. JSPolygon::createVerticalGrid() API 추가

-   수직 평면 그리드 객체를 생성하는 API가 추가되었습니다.
-   파라미터: 레이어명, 좌하단, 우상단, 새로 개수, 가로 개수
-   자세한 사용법은 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_vertical_grid)를 참고해주시기 바랍니다.

#### 6. JSFigure::getRectInfo() API 추가

-   생성된 `Figure` 객체에서 4개의 꼭지점을 반환합니다.
-   자세한 사용법은 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_figure_coordinate)를 참고해주시기 바랍니다.

### 2.6.1 (2024/09/03)

#### 1. 배경지도 오류 수정

-   0레벨 로딩시 텍스쳐 깨지는 현상 발생하여 수정하였습니다.

### 2.6.0 (2024/08/30)

#### 1. 지형 쉐이더 컴파일 오류 처리 기능 추가

-   지형 쉐이더를 컴파일할 경우, 디바이스별로 쉐이더 컴파일 조건이 다르므로 실패하는 경우가 있습니다.
-   이를 방지하기 위해, 컴파일 실패시 조건 수정후 다시 컴파일하는 기능이 추가되었습니다.

#### 2. 멀티뷰(화면 분할) 모드 오류 수정

-   `멀티뷰 모드`에서 지형이 깜박이던 현상을 수정했습니다.

#### 3. 멀티뷰(화면 분할) 모드 레이어 가시화 기능 추가

-   `멀티뷰 모드`에서, `RTT/하이브리드` 레이어의 가시화를 제어할 수 있는 기능이 추가되었습니다.

#### 4. POI 가시화 개선

-   POI 레벨 범위(시작, 끝)에 따른 가시화 구조를 수정하였습니다.
-   `ETLT_USER_LAYER`를 통해 생성한 POI에 대한 `object_ahead` 옵션 설정에 따른 가시화 기능을 수정하였습니다.

#### 5. Base Map 기능에서, Bing Map(전체)/OSM(Terrain) 항목 서비스 종료

-   Base Map에서, Bing Map과 Open Street Map(terrain)에 대한 서비스를 종료하였습니다.
-   자세한 사항은 [링크](https://sandbox.egiscloud.com/code/main.do?id=layer_basemap)를 참고해주시기 바랍니다.

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
