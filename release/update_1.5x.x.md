# - API 변경 내용 -

## 추가 API

#### JSVec3Array 내 좌표들 중 같은 지점 값을 가진 중복점을 제가하는 API

```javascript
var list = new Module.JSVec3Array();
list.push(new Module.JSVector3D(129.128265, 35.171834, 1000));
list.push(new Module.JSVector3D(129.128845, 35.171145, 1000));
list.push(new Module.JSVector3D(129.128845, 35.171145, 1000)); // 중복점
list.push(new Module.JSVector3D(129.128951, 35.170951, 1000));

var removed_count = list.removeDuplicateVectors(Number.EPSILON);
```

#### 고스트 심볼 조명 색상 변경 API

```javascript
let object = Module.createGhostSymbol("오브젝트 명칭");
// 생성 정보 코드
object.lightColor = new Module.JSColor(255, 128, 128, 128);
```

#### JSPipe 오브젝트를 담는 파이프 레이어(ELT_PIPE) 의 수직 단면 교차점 반환 API

-   class : JSLayer
-   parameter : 교차점을 계산하고자 하는 수직 평면 경로(입력 타입 JSVec2Array)
-   return : 위치(경도, 위도, 고도)와 교차점이 발생한 파이프의 오브젝트 키 리스트를 배열로 반환
    ![](../../.gitbook/release_note/1.5/jspipe_vertex.png)

```javascript
var path = new Module.JSVec2Array();
path.push(new Module.JSVector2D(126.92326703887365, 37.5249592425154));
path.push(new Module.JSVector2D(126.923563634119, 37.524387028175454));
path.push(new Module.JSVector2D(126.92490490575213, 37.52439598531512));

var intersection = pipeLayer.getPipeIntersection(path);
console.log(intersection);
```

#### JSSolarManager API 업데이트

-   getLayerPannelInfo
-   addPlannelObject

## 개선 API

#### 브이월드 요청 URL 변경에 따른 API 사용방법

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

#### JSColorPolygon 생성 기능 개선

```javascript
var polygon = Module.createColorPolygon("GRADATION_POLYGON");
polygon.set({
    vertex: [
        new Module.JSVector3D(129.12909050967076, 35.17110889362373, 4.22),
        new Module.JSVector3D(129.130474460754, 35.17110084682464, 4.0),
        new Module.JSVector3D(129.13056137846394, 35.17032570132414, 4.07),
        new Module.JSVector3D(129.12921614563658, 35.17031032880493, 4.39),
    ],
    color: [
        new Module.JSColor("#FF0000"),
        new Module.JSColor("#FF0000"),
        new Module.JSColor("#FFFF00"),
        new Module.JSColor("#FFFF00"),
    ],
    index: [0, 1, 2, 0, 2, 3],
});
```

#### JSLineString 생성 기능 개선

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

## 샌드박스 업데이트

-   [폴리곤 그라데이션](https://sandbox.dtwincloud.com/code/main.do?id=object_colorpolygon_color_gradation)에서 기능의 동작을 확인하실 수 있습니다.

# - 업데이트 내역 -

## 1.51.0 업데이트 (2023년 5월 26일)
#### 1. 화면 분할 환경에서 오브젝트의 렌더링 오류 수정 [Issue #289](/../../issues/289)
 * 화면 분할 시 투명도가 있는 오브젝트가 지정된 화면 구분 없이 렌더링 되는 현상을 수정하였습니다.

#### 2. 창문분석 기능 추가
 * 창문 영역(좌하단, 우상단 or 좌상단, 우하단)을 선택 후 창문 생성, 복사/붙여넣기, 층 복사하여 창문분석을 합니다.
 * 분석 결과는 json 형태로 반환되며, 연속 일조량, 전체 일조량이 반환됩니다.
 * [샌드박스(창문분석)](http://sandbox.dtwincloud.com/code/main.do?id=analysis_window_shadow)

## 1.51.1 Hotfix (2023/6/2)
### 1. 컬러 폴리곤 생성 기능 추가
 * 다수의 정점(vertex)과 인덱싱 정보로 폴리곤 형상을 직접 정의할 수 있는 API가 추가되었습니다.
   * 정점(vertex) : 폴리곤을 구성하는 점의 위치 리스트
   * 인덱스 : 각 정점을 삼각형으로 매핑하는 정수 리스트 

  ![image](https://github.com/EgisCorp/XDWorld/assets/82925313/c509a5a1-a6f1-4657-8cdc-86fae89e182d)


* 각 정점은 1:1로 매칭되는 색상 리스트를 정의할 수도 있습니다. 

  ![image](https://github.com/EgisCorp/XDWorld/assets/82925313/036694b8-4670-4f72-b868-5aa0eb71de99)


* 버텍스만으로 폴리곤의 삼각형을 구성하는 경우 인덱스를 생략할 수도 있습니다. 단, 이 경우 중복된 점이 리스트에 추가되므로 인덱싱 방법보다 비효율적일 수 있습니다. 

  ![image](https://github.com/EgisCorp/XDWorld/assets/82925313/b487577a-b75f-4541-8ea9-f6fce68d7259)


* 해당 기능은 JSColorPolygon의 set API를 통해 활용하실 수 있습니다.
   ``` javascript
   var polygon = Module.createColorPolygon("GRADATION_POLYGON");
   polygon.set({
       vertex : [
           new Module.JSVector3D(129.12909050967076, 35.17110889362373, 4.22),
           new Module.JSVector3D(129.130474460754, 35.17110084682464, 4.00),
           new Module.JSVector3D(129.13056137846394, 35.17032570132414, 4.07),
           new Module.JSVector3D(129.12921614563658, 35.17031032880493, 4.39)
       ],
       color : [
           new Module.JSColor("#FF0000"),
           new Module.JSColor("#FF0000"),
           new Module.JSColor("#FFFF00"),
           new Module.JSColor("#FFFF00")
       ],
       index : [0, 1, 2, 0, 2, 3]
   });
   ```
 * [샌드박스](https://sandbox.dtwincloud.com/code/main.do?id=object_colorpolygon_color_gradation)에서 기능의 동작을 확인하실 수 있습니다.

### 2. 라인 생성 시 각 지점 별 색상 설정 기능 추가
 * JSLineString으로 라인을 생성하였을 경우, 각 정점에 색상을 개별 지정 가능하도록 기능이 추가되었습니다.
 * 기존 API에서는 color 태그를 통해 단일 색상 지정만 가능했으나, 이번 업데이트를 통해 각 정점 별 색상 지정이 가능하도록 업데이트되었습니다.
 * 각 정점 별 색상 지정 시 color 태그에 색상값 배열을 입력하시면 됩니다.
 * 각 정점 별 색상 수가 1:1로 매칭되어야 합니다. 매칭되지 않을 시 배열의 첫번째 색상만 참조하여 단일 색상으로 적용됩니다.
   ``` javascript
   var line = Module.createLineString("GRADATION_LINE");
   line.createbyJson({
		coordinates: {
                    style : "XYZ",
                    coordinate : [
                        [129.12486405043842, 35.17410008274932, 5.7],
                        [129.12522538156702, 35.17364593649981, 5.6],
                        [129.12563286539853, 35.17332821268188, 5.6]
                    ]
                },
		type: 0,
		color: [
                    {a: 255, r : 255, g : 0, b : 
                    {a: 255, r : 255, g : 127, b : 0},
                    {a: 255, r : 255, g : 255, b : 0},
                ],
		width: 10.0
	});
   ```
 * [샌드박스](https://sandbox.dtwincloud.com/code/main.do?id=object_colorpolygon_color_gradation)에서 기능의 동작을 확인하실 수 있습니다.

## 1.51.2 Hotfix (2023/6/9)
### 1. JSSolarManager API 업데이트
 * 태양광 패널 배치 정보 반환 API(getLayerPannelInfo)를 추가하였습니다.
 * 태양광 패널 직접 배치 가능 API(addPlannelObject)를 추가 하였습니다.
### 2. [이슈 296](https://github.com/EgisCorp/XDWorld/issues/296#:~:text=%ED%99%94%EB%A9%B4%20%EC%98%A4%EB%A5%98%20%EB%AC%B8%EC%9D%98-,%23296,-Open) 오류 수정 완료

## 1.51.3(Hotfix) 업데이트 (2023년 6월 15일)
### 1. WMTS API 개선
 * 불필요한 WMTS 요청 예외처리 추가하였습니다.

## 1.51.1 Hotfix (2023/6/12)

> -   컬러 폴리곤 생성 기능 추가
>     -   다수의 정점(vertex)과 인덱싱 정보로 폴리곤 형상을 직접 정의할 수 있는 API가 추가되었습니다.
>         -   정점(vertex) : 폴리곤을 구성하는 점의 위치 리스트
>         -   인덱스 : 각 정점을 삼각형으로 매핑하는 정수 리스트

![](../../.gitbook/release_note/1.5/colorpolygon_vertex1.png)

> -   각 정점은 1:1로 매칭되는 색상 리스트를 정의할 수도 있습니다.

![](../../.gitbook/release_note/1.5/colorpolygon_color.png)

> -   버텍스만으로 폴리곤의 삼각형을 구성하는 경우 인덱스를 생략할 수도 있습니다. 단, 이 경우 중복된 점이 리스트에 추가되므로 인덱싱 방법보다 비효율적일 수 있습니다.

![](../../.gitbook/release_note/1.5/colorpolygon_vertex2.png)

> -   라인 생성 시 각 지점 별 색상 설정 기능 추가
>     -   JSLineString으로 라인을 생성하였을 경우, 각 정점에 색상을 개별 지정 가능하도록 기능이 추가되었습니다.
>     -   기존 API에서는 color 태그를 통해 단일 색상 지정만 가능했으나, 이번 업데이트를 통해 각 정점 별 색상 지정이 가능하도록 업데이트되었습니다.
>     -   각 정점 별 색상 지정 시 color 태그에 색상값 배열을 입력하시면 됩니다.
>     -   각 정점 별 색상 수가 1:1로 매칭되어야 합니다. 매칭되지 않을 시 배열의 첫번째 색상만 참조하여 단일 색상으로 적용됩니다.

## 1.51.2 Hotfix (2023/6/9)

> -   태양광 패널 배치 정보 반환 API(getLayerPannelInfo)를 추가하였습니다.
> -   태양광 패널 직접 배치 가능 API(addPlannelObject)를 추가 하였습니다.
> -   [이슈 296](https://github.com/EgisCorp/XDWorld/issues/296#:~:text=%ED%99%94%EB%A9%B4%20%EC%98%A4%EB%A5%98%20%EB%AC%B8%EC%9D%98-,%23296,-Open) 오류 수정 완료

## 1.50.2 Hotfix (2023/05/17)

> -   배경지도(Google, MapBox, OpenStreetMap) 오류 수정
>     -   일부 배경지도의 특정지역 누락현상이 발생하여 수정되었습니다.

## 1.50.1 Hotfix (2023/05/12)

> -   브이월드 서버 변경에 따른 API 개선
>     -   요청 URL 변경 http://xdworld.vworld.kr:8080/XDServer/ 에서 http://xdworld.vworld.kr:8080/XDServer3d/
>     -   브이월드 DEM 데이터가 암호화되어 제공됩니다.
>     -   지도 및 시설물 레이어 설정 기능 제공
> -   JSPipe 오브젝트를 담는 파이프 레이어(ELT_PIPE) 의 수직 단면 교차점 반환 API가 추가되었습니다.

## 1.50.0 (2023/04/28)

> -   JSFlow에 API 및 속성 추가
>     -   JSFlow::setJSON( \_option ) - 바람장 기반 통합 생성 API 추가 합니다.
>     -   JSFlow 클래스에 실시간 적용 및 반환 속성이 아래와 같이 추가됩니다.
>     -   [바람표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind_path) 참조
> -   거리측정 중 같은 지점 입력 필터링 단계 추가
>     -   거리측정 중 동일한 점을 중복 클릭하였을 경우 발생하는 예외처리 과정을 추가하였습니다.
> -   JSVec3Array 좌표 리스트의 중복점 제거 API 추가
>     -   같은 점을 판별하는 판별 값은 외부에서 설정 가능하도록 파라미터를 설정하였습니다.
>     -   판별 값의 단위는 m 단위 입니다.
>     -   위 예제에서는 부동 소수점의 오차 값(Number.EPSIOIN)을 지정하였으나, 파라미터로 0.1 값을 지정하시면 0.1m 내 거리 차가 있는 점은 같은 점으로 간주되어 제거됩니다.
>     -   위 API는 중복점 제거 실행 시 삭제된 점 수를 반환합니다.
> -   파이프 생성 시 경로 간소화 과정 삭제
>     -   JSPipe오브젝트 create API 내에서 경로 간소화 과정이 제거되었습니다.
>     -   기존 create API에서는 거리가 0.1m 미만의 가까운 점은 중복점으로 간주하여 생략하는 과정이 있었으나, 이는 정밀한 좌표점 입력 시 데이터가 왜곡되는 문제가 있어 삭제되었습니다.
>     -   만약 기존과 같이 중복점 제거 후 파이프를 생성하여야 하는 경우 위 항목 4번 JSVec3Array의 removeDuplicateVectors API를 활용하실 수 있습니다.
> -   거리 측정 중 중복점 입력 감지 추가
>     -   거리 측정 중 같은 지점을 두 번 클릭하였을 경우를 감지하여 중복 입력을 방지하는 단계를 추가하였습니다.
> -   수인한도분석 기능 추가
>     -   선택한 영역에 격자를 생성(영역에 딱 맞게 or 균일하게)하여 수인한도분석을 합니다.
>     -   분석 결과는 json 형태로 반환되며, 연속 일조량, 전체 일조량이 반환됩니다.
> -   JSFigure 객체 편집 기능 추가
>     -   Shift키를 누른 상태에서 크기 조절시 정비율로 조절이 가능하도록 추가됐습니다.
> -   JSGhostSymbol를 구성하는 property (lightColor) 추가
>     -   Ghost Symbol 가시화에 적용되는 Light Color 변경합니다.
>     -   변경된 색상이 0에 근접할수록 검은색으로 표현되며 반대로 255에 근접할수록 흰색으로 표현됩니다.
>     -   알파 값은 적용되지 않습니다.
