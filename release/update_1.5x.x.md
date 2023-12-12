# 1.5x 버전 업데이트

## - API 변경 내용 -

### 추가 API

**JSVec3Array 내 좌표들 중 같은 지점 값을 가진 중복점을 제거하는 API**

```javascript
var list = new Module.JSVec3Array();
list.push(new Module.JSVector3D(129.128265, 35.171834, 1000));
list.push(new Module.JSVector3D(129.128845, 35.171145, 1000));
list.push(new Module.JSVector3D(129.128845, 35.171145, 1000)); // 중복점
list.push(new Module.JSVector3D(129.128951, 35.170951, 1000));

var removed_count = list.removeDuplicateVectors(Number.EPSILON);
```

**고스트 심볼 조명 색상 변경 API**

```javascript
let object = Module.createGhostSymbol("오브젝트 명칭");
// 생성 정보 코드
object.lightColor = new Module.JSColor(255, 128, 128, 128);
```

**JSPipe 오브젝트를 담는 파이프 레이어(ELT\_PIPE) 의 수직 단면 교차점 반환 API**

* class : JSLayer
* parameter : 교차점을 계산하고자 하는 수직 평면 경로(입력 타입 JSVec2Array)
* return : 위치(경도, 위도, 고도)와 교차점이 발생한 파이프의 오브젝트 키 리스트를 배열로 반환 ![](../.gitbook/release\_note/1.5/jspipe\_vertex.png)

```javascript
var path = new Module.JSVec2Array();
path.push(new Module.JSVector2D(126.92326703887365, 37.5249592425154));
path.push(new Module.JSVector2D(126.923563634119, 37.524387028175454));
path.push(new Module.JSVector2D(126.92490490575213, 37.52439598531512));

var intersection = pipeLayer.getPipeIntersection(path);
console.log(intersection);
```

**JSSolarManager API 업데이트**

* getLayerPannelInfo
* addPlannelObject

### 개선 API

**브이월드 요청 URL 변경에 따른 API 사용방법**

```javascript
// 지도 초기화 생성 방법
Module.initialize({
    container: document.getElementById("map"),
    terrain: {
        dem: {
            url: "http://xdworld.vworld.kr:8080",
            name: "dem",
            servername: "XDServer3d", // 요청 서버 이름
            encoding: true, // DEM 복호화
        },
        image: {
            url: "http://xdworld.vworld.kr:8080",
            name: "tile_mo_HD",
            servername: "XDServer3d", // 요청 서버 이름
        },
    },
    defaultKey: "인증키 입력",
});
// TileLayer 생성 방법
// JSLayerList의 createXDServerLayer API에 servername 옵션이 추가되었습니다. 변경된 서버 네임을 이곳에서 설정하시면 됩니다.
var layer = Module.getTileLayerList().createXDServerLayer({
    url: "http://xdworld.vworld.kr:8080",
    servername: "XDServer3d", // 요청 서버 이름
    name: "facility_build",
    type: 9,
    minLevel: 0,
    maxLevel: 15,
});
```

**JSColorPolygon 생성 기능 개선**

```javascript
var polygon = Module.createColorPolygon("GRADATION_POLYGON");
polygon.set({
    vertex: [new Module.JSVector3D(129.12909050967076, 35.17110889362373, 4.22), new Module.JSVector3D(129.130474460754, 35.17110084682464, 4.0), new Module.JSVector3D(129.13056137846394, 35.17032570132414, 4.07), new Module.JSVector3D(129.12921614563658, 35.17031032880493, 4.39)],
    color: [new Module.JSColor("#FF0000"), new Module.JSColor("#FF0000"), new Module.JSColor("#FFFF00"), new Module.JSColor("#FFFF00")],
    index: [0, 1, 2, 0, 2, 3],
});
```

**JSLineString 생성 기능 개선**

```javascript
var line = Module.createLineString("GRADATION_LINE");
line.createbyJson({
    coordinates: {
        style: "XYZ",
        coordinate: [
            [129.12486405043842, 35.17410008274932, 5.7],
            [129.12522538156702, 35.17364593649981, 5.6],
            [129.12563286539853, 35.17332821268188, 5.6],
        ],
    },
    type: 0,
    color: [
        { a: 255, r: 255, g: 0, b: 0 },
        { a: 255, r: 255, g: 127, b: 0 },
        { a: 255, r: 255, g: 255, b: 0 },
    ],
    width: 10.0,
});
```

### 샌드박스 업데이트

* [폴리곤 그라데이션](https://sandbox.dtwincloud.com/code/main.do?id=object\_colorpolygon\_color\_gradation)에서 기능의 동작을 확인하실 수 있습니다.

## - 업데이트 내역 -

### 1.56.0  (2023/12/12)

* [이슈 357](https://github.com/EgisCorp/XDWorld/issues/357) 해결

### 1.55.2 Hotfix (2023/11/24)

* 조망보기 오류 수정

### 1.55.1 Hotfix (2023/11/245)

* [이슈 341](https://github.com/EgisCorp/XDWorld/issues/341)  해결

### 1.55.0 (2023/10/27)

#### 1. JSPolygon 내 픽셀 기반 텍스쳐 로드 기능이 추가되었습니다.

* 기존 URL로 데이터를 로드하는 loadTexture API에 픽셀 데이터를 바로 적용할 수 있도록 기능이 업데이트 되었습니다.
* 네트워크를 통해 데이터를 로드하지 않으므로 API 실행 후 바로 setFaceTexture API를 통해 텍스쳐를 적용할 수 있습니다.

```javascript
function setFaceTextureByPixelColors(_polygon, _faceIndex) {

    // 이미지를 그릴 캔버스 생성
    var canvas = document.createElement("canvas");
    canvas.width = 128;
    canvas.height = 128;

    var context = canvas .getContext("2d");

    (... context를 활용하여 canvas 이미지 그리기...)

    // canvas에 그려진 픽셀 데이터 반환

    // JSPolygon의 텍스쳐 리스트로 저장
    _polygon.loadTexture("텍스쳐이름", {
       width : canvas.width,
       height : canvas.height,
       pixels : context.getImageData(0, 0, canvas.width, canvas.height).data
   });

   // JSPolygon 첫번째 Face에 텍스쳐 지정
   _polygon.setFaceTexture(0, "텍스쳐이름");
}
```

### 1.54.1 Hotfix (2023/10/13)

#### 1. WMS, WMTS 이미지 투명도 설정 오류 수정

* 이미지 일부 영역에 투명 값이 정상적으로 설정되지 않는 부분을 수정하였습니다.

#### 2. JSPolygon loadTexture API 콜백 프로퍼티 추가 ([이슈 #336](https://github.com/EgisCorp/XDWorld/issues/336))

*   Fire\_EventTextureLoadComplete 이벤트 처리 대신 loadTexture API에 이미지 로드 콜백을 받을 수 있도록 수정되었습니다.

    ```javascript
    polygon.loadTexture("polygon_rtt_texture", {
        url: "./data/polygon_rtt_texture",
        callback: function (e) {
            console.log(e);
        },
    });
    ```
*   기존 콜백 처리가 없는 loadTexture API도 혼용 가능합니다.

    ```javascript
    polygon.loadTexture("polygon_rtt_texture", "./data/polygon_rtt_texture");
    ```

### 1.54.0 (2023/9/26)

#### 1. 대기 노을 효과

* 지정한 일출, 일물 시간에 따라 대기 색상이 변경 되도록 API가 추가되었습니다.
* API
  * JSOption.setAtmosphericSunriseTime(시간, 분);
  * JSOption.setAtmosphericSunsetTime(시간, 분);
  * JSOption.setAtmosphericTime(시간, 분);
*   샘플코드

    ```javascript
    // 일출 시간 설정
    Module.getOption().setAtmosphericSunriseTime(6, 30);
    ```

    ```javascript
    // 일몰 시간 설정
    Module.getOption().setAtmosphericSunsetTime(19, 0);
    ```

    ```javascript
    // 대기 시간 설정
    Module.getOption().setAtmosphericTime(12, 0);
    ```

#### 2. 하이브리드 투명도 편집 기능 추가

* JSLayer에 투명값 조절 API가 수정되었습니다.
* API : JSLayer.setAlpha(parameter);
*   샘플코드

    ```javascript
    let layerList = new Module.JSLayerList(false);
    var layer = layerList.nameAtLayer("layername");
    layer.setAlpha(180);
    ```

#### 3. 하이브리드 투명도 편집 기능 추가

* JSLayer에 투명값 조절 API가 수정되었습니다.
* API : JSLayer.setAlpha(parameter);
*   샘플코드

    ```javascript
    let layerList = new Module.JSLayerList(false);
    var layer = layerList.nameAtLayer("layername");
    layer.setAlpha(180);
    ```

#### 4. WMTS 예외처리

* 타일링에 따른 WMTS 예외처리가 추가되었습니다.

### 1.53.3 Hotfix (2023/9/12)

> * [이슈 321](https://github.com/EgisCorp/XDWorld/issues/321) 오류 수정 완료

### 1.53.2 (2023/9/12)

#### 1. 구 폴리곤 생성 API 추가 [이슈 #322](https://github.com/EgisCorp/XDWorld/issues/322)

* JSPolygon에 구체 폴리곤을 생성하는 API가 추가되었습니다.
* API : JSPolygon.setSphere(parameter);
*   샘플코드

    ```javascript
    var polygon = Module.createPolygon("GRADATION_POLYGON");
    let parameter = {
        position: new Module.JSVector3D(lon, lat, alt), // 경도, 위도, 고도 좌표
        color: new Module.JSColor(255, 0, 255, 0), // 구 표현색상 default : JSColor(255, 0, 255, 0)
        radius: 40, // 구 반지름 설정(m 단위)  default : 10
        segment: 50, // 구 정밀도 설정   default : 30
    };
    polygon.setSphere(parameter);
    ```

#### 2. 폴리곤 깊이 버퍼 on/off 프로퍼티 추가

* JSPolygon에 깊어 버퍼 테스트를 on/off 할 수 있도록 bool 타입 프로퍼티 'zBufferOff'가 추가되었습니다.
* 디폴트 값은 false 입니다.
*   샘플코드

    ```javascript
    polygon.zBufferOff = true;
    ```

#### 3. PNG 타일맵 레이어 투명도 조절 기능 추가 [이슈 #321](https://github.com/EgisCorp/XDWorld/issues/321)

* JSLayer의 setAlpha API의 하이브리드 투명값 조절 기능이 추가되었습니다.
* API : JSLayer.setAlpha(parameter);
*   샘플코드

    ```javascript
    let layerList = new Module.JSLayerList(false);
    var layer = layerList.nameAtLayer("layername");
    layer.setAlpha(180);
    ```

### 1.53.1 Hotfix (2023/8/4)

> * [이슈 317](https://github.com/EgisCorp/XDWorld/issues/317) 오류 수정 완료

### 1.53.0 (2023/7/28)

> * [이슈 316](https://github.com/EgisCorp/XDWorld/issues/316) 오류 수정 완료

### 1.52.1 Hotfix (2023/7/14)

#### 1. 엔진 내 마우스 버튼 눌림 상태 프로퍼티가 추가되었습니다.

*   JSControl 내 마우스 왼쪽 버튼 눌림(mouseLeftButtonDown), 오른쪽 버튼 눌림(mouseRightButtonDown) 프로퍼티가 추가되었습니다.

    ```javascript
    console.log(Module.getControl().mouseLeftButtonDown);
    console.log(Module.getControl().mouseRightButtonDown);
    ```

#### 2. Mobile Touch Rotate Event tilt 제한 기능을 수정하였습니다.

* JSCamera.setLimitTilt("입력값") 설정 후 모바일 touch rotate event시 제한이 안되는 문제를 수정하였습니다.

#### 3. 측면 두께를 가진 Polygon 생성 기능을 추가 하였습니다.

* 고도를 기준 축으로 측면으로 두께가 있는 JSColorPolygon 생성 기능을 추가하였습니다.
* API : JSColorPolygon.createbyJson(parameter);
* 샘플코드

```javascript
var polygon = Module.createColorPolygon("GRADATION_POLYGON");
let parameter = {
    coordinates: {
        coordinate: vertices, // geometry 경위도좌표 목록
        index: indices, // geometry 가시화 인덱스 설정
    },
    color: colors, // 정점 색상 설정
    thickness: 0, // 두께 설정(m 단위)
};
polygon.createbyJson(parameter);
```

#### 3. JSColorPolygon 경위도 좌표 반환 기능을 추가 하였습니다.

* JSColorPolygon을 구성하는 geometry 경위도 좌표 목록을 반환하는 기능
* API : JSColorPolygon.toLonlatArray();

### 1.52.0 (2023/6/30)

#### 1. 레이어의 지상/지하 렌더링 구분 프로퍼티 추가 ([이슈 297](https://github.com/EgisCorp/XDWorld/issues/297))

* 해당 레이어의 지상에 위치하는지, 혹은 지하에 위치하는지 구분하는 view\_underground 프로퍼티가 추가되었습니다.
* `layer.view_underground = true`
* 디폴트 값은 false 입니다. (Module.TILE\_LAYER\_TYPE\_VECTOR\_PIPE 타입 레이어에 한하여 디폴트 값은 true로 적용됩니다.)

#### 2. 태양광 패널관련 JSSolarManager API 업데이트

* 태양광 패널에 배치 정보를 API 레벨로 받을 수 있는 getLayerPannelInfo 추가됩니다.
  * 패널의 위치, 가로너비, 세로너비, 패널 두께, 방향각, 수직각 정보가 String Json 정보로 제공하며 아래 API로 재배치 가능합니다.
* 태양광 패널 정보를 바탕으로 직접 패널 배치하는 bool addPlannelObject 추가됩니다.
* 옥상 패널 배치 시뮬레이션 : http://sandbox.dtwincloud.com/code/main.do?id=analysis\_pannel\_roof
* 지상 패널 배치 시뮬레이션 : http://sandbox.dtwincloud.com/code/main.do?id=analysis\_pannel\_terrain
* 배란다 패널 배치 시뮬레이션 : http://sandbox.dtwincloud.com/code/main.do?id=analysis\_pannel\_veranda
* 벽면(BI) 패널 배치 시뮬레이션 : http://sandbox.dtwincloud.com/code/main.do?id=analysis\_pannel\_wall

#### 3. JSVector3Array - JSVector2Array 간 변환 API 추가

* JSVector3Array - JSVector2Array 간 원활한 변환이 가능하도록 toJSVector3Array, toJSVector2Array API가 추가되었습니다.
* JSVector2Array에서 JSVector3Array로 변환하는 경우 고도 값 입력이 필요합니다.
*   JSVector3Array에서 JSVector2Array로 변환하는 경우 고도 값은 소실됩니다.

    ```javascript
    var array2D = new Module.JSVector2Array();
    var array3D = new Module.JSVector3Array();
    ...
    console.log(array2D.toJSVector3Array(10.0));         // JSVector2Array에서 JSVector3Array로 변환
    console.log(array3D.toJSVector2Array());   // JSVector3Array에서 JSVector2Array로 변환
    ```

#### 4. JSVector3Array, JSVector2Array에 getBoundary API 추가

*   JSVector3Array, JSVector2Array의 min, max 값이 반환 되는 getBoundary API가 각각 추가되었습니다.

    ```javascript
    var boundary = array2D.getBoundary());
    console.log(boundary.min);
    console.log(boundary.max);
    ```
* 리스트에 값이 없어 비어있는 경우 null을 반환합니다.

### 1.51.3 Hotfix (2023/6/15)

#### 1. WMTS API 개선

* 불필요한 WMTS 요청 예외처리 추가하였습니다.

### 1.51.2 Hotfix (2023/6/9)

> * 태양광 패널 배치 정보 반환 API(getLayerPannelInfo)를 추가하였습니다.
> * 태양광 패널 직접 배치 가능 API(addPlannelObject)를 추가 하였습니다.
> * [이슈 296](https://github.com/EgisCorp/XDWorld/issues/296) 오류 수정 완료

### 1.51.1 Hotfix (2023/6/12)

> * 컬러 폴리곤 생성 기능 추가
>   * 다수의 정점(vertex)과 인덱싱 정보로 폴리곤 형상을 직접 정의할 수 있는 API가 추가되었습니다.
>     * 정점(vertex) : 폴리곤을 구성하는 점의 위치 리스트
>     * 인덱스 : 각 정점을 삼각형으로 매핑하는 정수 리스트

![](../.gitbook/release\_note/1.5/colorpolygon\_vertex1.png)

> * 각 정점은 1:1로 매칭되는 색상 리스트를 정의할 수도 있습니다.

![](../.gitbook/release\_note/1.5/colorpolygon\_color.png)

> * 버텍스만으로 폴리곤의 삼각형을 구성하는 경우 인덱스를 생략할 수도 있습니다. 단, 이 경우 중복된 점이 리스트에 추가되므로 인덱싱 방법보다 비효율적일 수 있습니다.

![](../.gitbook/release\_note/1.5/colorpolygon\_vertex2.png)

> * 라인 생성 시 각 지점 별 색상 설정 기능 추가
>   * JSLineString으로 라인을 생성하였을 경우, 각 정점에 색상을 개별 지정 가능하도록 기능이 추가되었습니다.
>   * 기존 API에서는 color 태그를 통해 단일 색상 지정만 가능했으나, 이번 업데이트를 통해 각 정점 별 색상 지정이 가능하도록 업데이트되었습니다.
>   * 각 정점 별 색상 지정 시 color 태그에 색상값 배열을 입력하시면 됩니다.
>   * 각 정점 별 색상 수가 1:1로 매칭되어야 합니다. 매칭되지 않을 시 배열의 첫번째 색상만 참조하여 단일 색상으로 적용됩니다.

### 1.51.0 업데이트 (2023년 5월 26일)

**1. 화면 분할 환경에서 오브젝트의 렌더링 오류 수정** [**Issue #289**](../issues/289/)

* 화면 분할 시 투명도가 있는 오브젝트가 지정된 화면 구분 없이 렌더링 되는 현상을 수정하였습니다.

**2. 창문분석 기능 추가**

* 창문 영역(좌하단, 우상단 or 좌상단, 우하단)을 선택 후 창문 생성, 복사/붙여넣기, 층 복사하여 창문분석을 합니다.
* 분석 결과는 json 형태로 반환되며, 연속 일조량, 전체 일조량이 반환됩니다.
* [샌드박스(창문분석)](http://sandbox.dtwincloud.com/code/main.do?id=analysis\_window\_shadow)

### 1.50.2 Hotfix (2023/05/17)

> * 배경지도(Google, MapBox, OpenStreetMap) 오류 수정
>   * 일부 배경지도의 특정지역 누락현상이 발생하여 수정되었습니다.

### 1.50.1 Hotfix (2023/05/12)

> * 브이월드 서버 변경에 따른 API 개선
>   * 요청 URL 변경 http://xdworld.vworld.kr:8080/XDServer/ 에서 http://xdworld.vworld.kr:8080/XDServer3d/
>   * 브이월드 DEM 데이터가 암호화되어 제공됩니다.
>   * 지도 및 시설물 레이어 설정 기능 제공
> * JSPipe 오브젝트를 담는 파이프 레이어(ELT\_PIPE) 의 수직 단면 교차점 반환 API가 추가되었습니다.

### 1.50.0 (2023/04/28)

> * JSFlow에 API 및 속성 추가
>   * JSFlow::setJSON( \_option ) - 바람장 기반 통합 생성 API 추가 합니다.
>   * JSFlow 클래스에 실시간 적용 및 반환 속성이 아래와 같이 추가됩니다.
>   * [바람표현](http://sandbox.dtwincloud.com/code/main.do?id=effect\_wind\_path) 참조
> * 거리측정 중 같은 지점 입력 필터링 단계 추가
>   * 거리측정 중 동일한 점을 중복 클릭하였을 경우 발생하는 예외처리 과정을 추가하였습니다.
> * JSVec3Array 좌표 리스트의 중복점 제거 API 추가
>   * 같은 점을 판별하는 판별 값은 외부에서 설정 가능하도록 파라미터를 설정하였습니다.
>   * 판별 값의 단위는 m 단위 입니다.
>   * 위 예제에서는 부동 소수점의 오차 값(Number.EPSIOIN)을 지정하였으나, 파라미터로 0.1 값을 지정하시면 0.1m 내 거리 차가 있는 점은 같은 점으로 간주되어 제거됩니다.
>   * 위 API는 중복점 제거 실행 시 삭제된 점 수를 반환합니다.
> * 파이프 생성 시 경로 간소화 과정 삭제
>   * JSPipe오브젝트 create API 내에서 경로 간소화 과정이 제거되었습니다.
>   * 기존 create API에서는 거리가 0.1m 미만의 가까운 점은 중복점으로 간주하여 생략하는 과정이 있었으나, 이는 정밀한 좌표점 입력 시 데이터가 왜곡되는 문제가 있어 삭제되었습니다.
>   * 만약 기존과 같이 중복점 제거 후 파이프를 생성하여야 하는 경우 위 항목 4번 JSVec3Array의 removeDuplicateVectors API를 활용하실 수 있습니다.
> * 거리 측정 중 중복점 입력 감지 추가
>   * 거리 측정 중 같은 지점을 두 번 클릭하였을 경우를 감지하여 중복 입력을 방지하는 단계를 추가하였습니다.
> * 수인한도분석 기능 추가
>   * 선택한 영역에 격자를 생성(영역에 딱 맞게 or 균일하게)하여 수인한도분석을 합니다.
>   * 분석 결과는 json 형태로 반환되며, 연속 일조량, 전체 일조량이 반환됩니다.
> * JSFigure 객체 편집 기능 추가
>   * Shift키를 누른 상태에서 크기 조절시 정비율로 조절이 가능하도록 추가됐습니다.
> * JSGhostSymbol를 구성하는 property (lightColor) 추가
>   * Ghost Symbol 가시화에 적용되는 Light Color 변경합니다.
>   * 변경된 색상이 0에 근접할수록 검은색으로 표현되며 반대로 255에 근접할수록 흰색으로 표현됩니다.
>   * 알파 값은 적용되지 않습니다.
