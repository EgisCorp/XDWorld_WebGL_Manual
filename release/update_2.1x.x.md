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

### 2.13.0 (2025/04/07)

1. 터파기 가시화 오브젝트 추가(https://github.com/EgisCorp/XDWorld/issues/476)
     * 기존 JSColorPipe 뿐만 아니라 JSFlowPolygon, JSPolygon, JSReal3d(건물) 오브젝트도 원형 터파기 영역에 보이도록 기능을 추가하였습니다.
     * 보이고자 하는 JSLayer의 setViewInTransparency API를 통해 보이기 여부를 설정할 수 있습니다.
     * 기본 값은 보이지 않음(false) 이며, JSColorPipe 객체는 예외적으로 보임 상태를 유지합니다.
     * void setViewInTransparency(bool _set)
       * Class : JSLayer
       * Parameter
         * _set(bool) : 보이기 여부(true 보임 / false 보이지 않음)
       ``` javascript
       layer.setViewInTransparency(true);
       ```
     * bool getViewInTransparency();
       * Class : JSLayer
       * Return
         * 보임 설정 여부(bool)
       ``` javascript
       var visible = layer.getViewInTransparency();
       ```

2. JSPolygon의 Union mode 오류 수정 (https://github.com/EgisCorp/XDWorld/issues/478)
    - JSPolygon에 Union mode 설정 후 RTT 적용이 되지 않는 점을 수정하였습니다.

3. 라인 효과 추가 및 정리
     - 라인 타입에 따른 옵션 및 매개변수 구조를 보다 사용하기 쉽도록 수정하였습니다.
     - 변경 사항
       - type: 기존 숫자로 입력하는 방식에서 Module.BLING (type: NORMAL, OUTLINE, GLOW, ARROW, DASH, FIRE, BLING, WARNING)등의 상수로 정의하도록 변경되었습니다.
       - animation, loopcount 속성을 추가하여 가시화 효과(type)에 따라 애니메이션 효과가 적용되도록 변경되었습니다.
     - 라인 크기를 고정시키는 옵션을 추가하였습니다.
     ```javascript
     [기존방식]
     let data = {
       coordinates: coordinates,
       type: 0,						// Solid line creation
       union: false,						// Terrain union status
       depth: true,						// Object overlap status
       color: new Module.JSColor(255, 255, 0, 0),		// ARGB
       width: 1,						// Line width
     };

     [변경된 방식]
     let data = {
       coordinates: coordinates,
       type: Module.BLING,					// Solid line creation
       union: false,						// Terrain union status
       depth: true,						// Object overlap status
       color: new Module.JSColor(255, 255, 0, 0),		// ARGB
       width: 1,						// Line width
       animation: true,					// Animation
       sizefix: true,						// size fixed
       loopcount: 1						// Animation loop count
     };
     ```

4. POI 가시화 오류 수정

     - 카메라 영역을 벗어날 경우, POI가 화면에서 사라지는 오류를 수정하였습니다.
     - 이제부터 영역을 벗어나면 POI 높이를 조절하여 화면 내부에서 볼 수 있도록 변경됩니다.

5. 빌보드 회전 타입 추가
     * 아래 이미지와 같이 지면과 수평한 빌보드의 회전 타입이 추가되었습니다.
       ![Image](https://github.com/user-attachments/assets/4002a632-4efe-4ba7-8bec-9382c1402d48)
     * JSBillboard의 setRotationMode API를 통해 mode 2번을 선택하시면 적용하실 수 있습니다.
       ``` javascript
       billboard.setRotationMode(2);
       ```

6. 마우스 조작 이벤트 버튼 설정 기능 추가
     * 마우스 버튼을 통해 지도 조작(이동, 회전, 줌) 동작에 사용할 버튼을 설정할 수 있도록 하는 기능이 추가되었습니다.  
     * `setMouseControlEvent`를 통해 조작 타입별 버튼을 설정할 수 있으며, `getMouseControlEvent`로 현재 설정된 버튼 값을 조회할 수 있습니다.  
     * 조작 타입은 `"translate"`, `"rotate"`, `"zoom"` 중 하나이며, 버튼 값은 0(좌클릭), 1(휠클릭), 2(우클릭) 중 하나입니다.  
     * `bool setMouseControlEvent(string type, int button)`  
       * Class : JSControl  
       * Parameter  
         * `type` (string) : 조작 타입 ("translate", "rotate", "zoom")  
         * `button` (int) : 마우스 버튼 값 (0: 좌클릭, 1: 휠클릭, 2: 우클릭)  
       * Return  
         * 설정 성공 여부 (bool)  
       ```javascript
       JSControl.setMouseControlEvent("rotate", 2);  // 회전을 우클릭으로 설정
       ```
     * `int getMouseControlEvent(string type)`  
       * Class : JSControl  
       * Parameter  
         * `type` (string) : 조작 타입 ("translate", "rotate", "zoom")  
       * Return  
         * 해당 타입의 현재 마우스 버튼 값 (int)  
       ```javascript
       var zoomButton = JSControl.getMouseControlEvent("zoom");
       ```

### 2.12.3 (2025/03/17)
- XDServer의 POI 레이어 서비스에서 데이터 처리중 발생하는 오류를 수정하였습니다.
  - 이슈 : https://github.com/EgisCorp/XDWorld/issues/475

### 2.12.2 (2025/03/12)
- JSOption::setMaxRequestQueueSize() API 추가
  - 데이터 요청 큐의 크기(기본값은 5)를 조절하는 setMaxRequestQueueSize()가 추가되었습니다.
    ```javascript
    Module.getOption().setMaxRequestQueueSize(20);
    ```
    - 매개변수: 변경할 요청 큐의 크기(number)
- 3D 서비스 모델 요청시 처리 성능이 향상되었습니다.

### 2.12.1 (2025/03/11)
- 이미지 레이어가 가시화되지 않는 오류를 수정하였습니다.

### 2.12.0 (2025/03/10)

1. POI 선택시 Text 위치 오류 수정
    - POI 선택시 setTextMargin 이 Text 에 적용되지 않는 오류를 수정하였습니다.

2. 화면분할(Streo View) 모드에서 좌우 객체를 인식할 수 있도록 기능을 수정하였습니다.

3. Text 형태의 POI 선택 인식 및 선택 효과 추가
    - 기존 POI처럼 Text도 선택과 선택 색상(picking color) 적용이 가능하도록 수정하였습니다.

4. 3DTiles B3DM 선택 오류를 수정하였습니다.

5. `AutoMove` 모드에서 카메라 회전 옵션 `lock orientation` 추가
    - `AutoMove` 모드에서 카메라를 자유롭게 회전시킬 수 있도록, `lock orientation` 옵션이 추가되었습니다.
       - 활성화(기본값): 카메라가 항상 다음 경로의 위치를 바라봅니다.
       - 비활성화: 카메라를 1인칭 시점에서 회전시킬 수 있습니다(오른쪽 마우스 버튼 사용).
    - 사용 방법
        ```Javascript
        // AutoMove 설정
        Module.getViewCamera().setAnimationSpeed(1);
        Module.getViewCamera().startAutoMove();
        Module.XDRenderData();

        // 비활성화 함으로써, 카메라 자유롭게 이동 가능
        Module.getViewCamera().setLockOrientationAutoMove(false);
        ```
      - 자세한 사용 방법은 [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path_visualize)을 확인해주시기 바랍니다.

6. 서비스 레이어 범위 제한 옵션 `boundaryLimit` 추가
     - 서비스 레이어에서 오브젝트를 요청할 때, 요청하는 범위를 경도/위도로 제한할 수 있도록 `boundaryLimit` 옵션이 추가되었습니다.
       - 활성화: 기존 방식에서, 미리 지정해 놓은 범위에 포함되는 오브젝트만 호출합니다.
          - 활성화한 이후에도, `JSLayer::setLimitBoundary()` API를 사용하여 범위를 제한하여야 합니다.
       - 비활성화(기본값): 기존 방식과 동일하게 오브젝트를 호출합니다.
     - 사용 방법
        ```Javascript
          // 샌드박스에서 제공하는 
          let layer = Module.getTileLayerList().createXDServerLayer({
            url : "https://xdworld.vworld.kr",
            servername : "XDServer3d",
            name : "facility_build",
            type : 9,
            minLevel : 0,
            maxLevel : 15
          });

          // Json 형태의 매개변수로 범위 지정
          layer.setLimitBoundary({
            boundary: {
              min: [129.125, 35.161],		// Lower left
              max: [129.141, 35.168]		// Upper right
            }
          });

          layer.boundaryLimit = true;   // 옵션 활성화
        ```
       - 자세한 사용 방법은 [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=layer_request_boundary)을 확인해주시기 바랍니다.

### 2.11.2 (2025/02/24)

- 3DTiles B3DM 피킹이 제대로 되지 않던 오류를 수정하였습니다.

### 2.11.1 (2025/02/17)

- 다울지도 네트워크 요청시 발생하는 오류가 수정되었습니다.

### 2.11.0 (2025/02/10)

1. `3DTiles` 높이 오프셋 옵션 추가
     - `import3DTiles()`에 높이 오프셋(단위 m)를 설정할 수 있는 옵션 `offsetZ`가 추가되었습니다.
     - 자세한 사용법은 아래 예시를 확인해주시기 바랍니다.
       ```javascript
       var pLayerList = new Module.JSLayerList(true);
       if(pLayerList==null) return;

       var pLayer = pLayerList.nameAtLayer("Layer3DTiles");
       if(pLayer==null)
       {
         pLayer = pLayerList.createLayer("Layer3DTiles", Module.ELT_3DTILES);
       }
       pLayer.import3DTiles({
         url : _strURL,
         autoMove : true,
         offsetZ : _fOffsetZ,  // 높이 오프셋. 단위 m
       });
       ```

2. 성절토 바닥/옆면 타일링 텍스쳐 설정 API 추가
     * 성절토 바닥 텍스쳐 설정 시 텍스쳐 반복 출력(타일링)이 가능하도록 API가 추가되었습니다.
     * API 설정 시 1.0보다 큰 값을 n값을 입력하면 설정한 텍스쳐가 n번 반복 출력됩니다.
     * API 호출 이후 생성되는 성절토 객체에 해당 값이 적용됩니다.
     * 성절토 바닥면 텍스쳐 설정
       * bool setBottomTextureTilingScale(float u, float v)
         * class : JSEditTerrain
         * parameter
           * u : 가로 반복 u 좌표
           * v : 세로 반복 v 좌표 
      * 성절토 옆면 텍스쳐 설정
        * bool setSlopeTextureTilingScale(float u, float v)
          * class : JSEditTerrain
          * parameter
            * u : 가로 반복 u 좌표
            * v : 세로 반복 v 좌표 
     ``` javascript
     Module.getEditTerrain().setBottomTextureTilingScale(10.0, 10.0);
     Module.getEditTerrain().setSlopeTextureTilingScale(10.0, 10.0);
     ```

3. 비디오 객체 오류 수정
    * 초기화 시 계속적으로 Hls 네트워크 요청하는 오류가 수정되었습니다.
    * 뒷배경 on/off 기능이 추가되었습니다. [비디오 객체](https://sandbox.egiscloud.com/code/main.do?id=object_video_placement)

4. `JSLayer::setObjectVisibleWithBoundary()` API 추가
   - 매개변수로 전달한 좌표를 벗어날 경우, 오브젝트를 그리지 않도록 설정하는 함수를 추가하였습니다.
   - 함수 정보
     - boolean setObjectVisibleWithBoundary(number minLon, number maxLon, number minLat, number maxLat)
     - class : JSLayer
     - parameter
       - minLon: 최소 경도
       - maxLon: 최대 경도
       - minLat : 최소 위도
       - maxLat : 최대 위도
     ```javascript
      // 레이어 및 오브젝트 생성
      sampleLayer.setObjectVisibleWithBoundary(129.5, 130, 35.16, 35.19);
     ```

### 2.10.2 (2025/01/21)

1. `3DTiles` 포맷 처리 기능 안정화
   - `3DTiles` 파일 처리 속도를 개선하였습니다.
   - 로딩한 모델이 깜박이는 오류를 수정하였습니다.

2. 성절토 바닥 타일링 텍스처 설정 API 추가
   - 성절토 바닥 텍스쳐 설정 시 텍스쳐 반복 출력(타일링)이 가능하도록 API가 추가되었습니다.
   - API 설정 시 1.0보다 큰 값을 n값을 입력하면 설정한 텍스쳐가 n번 반복 출력됩니다.
   - API 호출 이후 생성되는 성절토 객체에 해당 값이 적용됩니다.
   - bool setBottomTextureTilingScale(float u, float v)
     - class : JSEditTerrain
     - parameter
      - u : 가로 반복 u 좌표
      - v : 세로 반복 v 좌표
    ```javascript
      Module.getEditTerrain().setBottomTextureTilingScale(10.0, 10.0);
    ```

3. `JSPolygon` 텍스처 오류 수정
   - `JSpolygon` 객체에 반투명한 텍스처가 제대로 적용되지 않는 오류를 수정하였습니다.

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
