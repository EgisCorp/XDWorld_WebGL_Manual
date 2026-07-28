---
description: 지도 생성 및 설정하기 위한 API 입니다.
---

# Module_API

> Module.initialize를 통해 기본 지도를 생성할 수 있습니다.
>
> Module을 통해 다른 Class를 생성 후 사용이 가능합니다.

{% hint style="info" %}
Function initialize에 추가된 worker 항목은 2024년 2월 1일부터 베타 버전 엔진에서 지원됩니다. 엔진과 함께 제공되는 'XDWorldWorker.js', 'XDWorldWorker.wasm'을 이용하여 엔진에 발생할 수 있는 부하를 분산하여 처리합니다.
{% endhint %}

```javascript
Module.initialize({
    container: document.querySelector("Container ID"),
    terrain: {
        dem: {
            url: "Terrain DEM data request URL",
            name: "Terrain DEM layer name",
            servername: "Request Server name",
        },
        image: {
            url: "Terrain image data request URL",
            name: "Terrain image layer name",
            servername: "Request Server name",
        },
        worker: {
            use: "Use of web worker",
            path: "Web worker file request URL",
            count: "Set the number of web workers to use",
        },
    },
    defaultKey: "Issued key",
});
```

## Function

### initialize(object) → object

> 지도를 생성합니다.
>
> worker 항목 옵션을 통해 web worker 기능을 활성화 합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type                                                                  | Description                         |
| ---------- | --------------------------------------------------------------------- | ----------------------------------- |
| container  | HTML Element                                                          | 3D 지도를 포함할 Container Element. |
| terrain    | [Module.CreateOptions](moduleapi.md#module.createterrainoptions)      | 지형 설정 정보.                     |
| worker     | [Module.CreateWorkerOptions](moduleapi.md#module.createworkeroptions) | web worker 설정 정보.               |
| defaultKey | string                                                                | Engine API 발급키.                  |

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name: 동작 API 명칭.
    -   .return: API 반환 정보.

{% endtab %}
{% tab title="Template" %}

```javascript
// Use sandbox
Module.initialize({
    container: document.getElementById("map"),
    terrain: {
        dem: {
            url: "https://xdworld.vworld.kr",
            name: "dem",
            servername: "XDServer3d",
            encoding: true,
        },
        image: {
            url: "https://xdworld.vworld.kr",
            name: "tile_mo_HD",
            servername: "XDServer3d",
        },
    },
    worker: {
        use: true,
        path: "./worker/XDWorldWorker.js",
        count: 5,
    },
    defaultKey: "Issued key",
});
```

{% endtab %}
{% endtabs %}

### getVersion() → string

> 현재 엔진의 버전을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   엔진 버전

{% endtab %}
{% tab title="Template" %}

```javascript
let version = Module.getVersion();
```

{% endtab %}
{% endtabs %}

### createBarGraph(id) → [JSBarGraph](../object/jsbargraph.md)

> 2차원 막대 그래프 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSBarGraph](../object/jsbargraph.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createBarGraph("newBarGraph");
```

{% endtab %}
{% endtabs %}

### createBarGraph3D(id) → [JSBarGraph3D](../object/jsbargraph3d.md)

> 3차원 막대 그래프 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSBarGraph3D](../object/jsbargraph3d.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createBarGraph3D("newBarGraph3D");
```

{% endtab %}
{% endtabs %}

### createBillboard(id) → [JSBillboard](../object/jsbillboard.md)

> 빌보드 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| key  | string | 객체 고유 명칭. |

-   Return
    -   [JSBillboard](../object/jsbillboard.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createBillboard("newBillboard");
```

{% endtab %}
{% endtabs %}

### createGhostSymbol(id) → [JSGhostSymbol](../object/jsghostsymbol.md)

> 고스트 심볼 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSGhostSymbol](../object/jsghostsymbol.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let ghostSymbol = Module.createGhostSymbol("newGhostSymbol");
```

{% endtab %}
{% endtabs %}

### createLineString(id) → [JSLineString](../object/jslinestring.md)

> 선 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSLineString](../object/jslinestring.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createLineString("newPolyLine");
```

{% endtab %}
{% endtabs %}

### createMultiPoint(id) → [JSMultiPoint](../object/jsmultipoint.md)

> 멀티 포인트 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSMultiPoint](../object/jsmultipoint.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createMultiPoint("newMultiPoint");
```

{% endtab %}
{% endtabs %}

### createPipe(id) → [JSPipe](../object/jspipe.md)

> 3차원 파이프 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSPipe](../object/jspipe.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createPipe("newPipe");
```

{% endtab %}
{% endtabs %}

### createPoint(id) → [JSPoint](../object/jspoint.md)

> POI 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSPoint](../object/jspoint.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createPoint("newPoint");
```

{% endtab %}
{% endtabs %}

### createPointGraph(id) → [JSPointGraph](../object/jspointgraph.md)

> 3차원 포인트 그래프 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSPointGraph](../object/jspointgraph.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createPointGraph("newGraph");
```

{% endtab %}
{% endtabs %}

### createSurfaceGraph(id) → [JSSurfaceGraph](../object/jssurfacegraph.md)

> 3차원 그물형 격자 그래프 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSSurfaceGraph](../object/jssurfacegraph.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createSurfaceGraph("newBarGraph3D");
```

{% endtab %}
{% endtabs %}

### createHTMLObject(id) → [JSHTMLObject](../object/jshtmlobject.md)

> HTML 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSHTMLObject](../object/jshtmlobject.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createHTMLObject("newHTML");
```

{% endtab %}
{% endtabs %}

### getAnalysis() → [JSAnalysis](../analysis/jsanalysis.md)

> 분석 기능을 실행하는 [JSAnalysis](../analysis/jsanalysis.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSAnalysis](../analysis/jsanalysis.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var analysis = Module.getAnalysis();
```

{% endtab %}
{% endtabs %}

### getGhostSymbolMap() → [JSGhostSymbolMap](../object/jsghostsymbolmap.md)

> 고스트 심볼을 관리하는 [JSGhostSymbolMap](../object/jsghostsymbolmap.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSGhostSymbolMap](../object/jsghostsymbolmap.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let map = Module.getGhostSymbolMap();
```

{% endtab %}
{% endtabs %}

### getMap() → [JSMap](../map/jsmap.md)

> 지도 기능을 호출하는 ([JSMap](../map/jsmap.md)) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSMap](../map/jsmap.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

javascript
let map = Module.getMap();


{% endtab %}
{% endtabs %}

### getSlope() → [JSSlope](../analysis/jsslope.md)

> 경사 분석을 관리하는 [JSSlope](../analysis/jsslope.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSSlope](../analysis/jsslope.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let slope = Module.getSlope();
```

{% endtab %}
{% endtabs %}

### getSymbol() → [JSSymbol](../object/jssymbol.md)

> 이미지 아이콘([JSIcon](../object/jsicon.md))을 관리하는 [JSSymbol](../object/jssymbol.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSSymbol](../object/jssymbol.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let symbol = Module.getSymbol();
```

{% endtab %}
{% endtabs %}

### getTerrain() → [JSTerrain](../map/jsterrain.md)

> 지형 설정 API를 호출하는 [JSTerrain](../map/jsterrain.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSTerrain](../map/jsterrain.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let terrain = Module.getTerrain();
```

{% endtab %}
{% endtabs %}

### Resize(width, height)

> 3D 지도 화면의 크기를 변경하는 API 입니다.
>
> 설정이 없을 경우, canvas 크기를 기준으로 3D viewport를 설정합니다.
>
> container 설정 시 container 크기에 맞츄어 3D viewprot를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type   | Description |
| ------ | ------ | ----------- |
| width  | number | 화면 너비.  |
| height | number | 화면 높이.  |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.Resize(400, 300);
```

{% endtab %}
{% endtabs %}

### SetSimpleMode(type)

> 시설물 가시화 심플 모드를 설정합니다.
>
> 시설물 심플 모드 설정 시 시설물 이미지가 있더라도 단순한 색상으로 객체를 가시화 합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                |
| ---- | ------- | ---------------------------------------------------------- |
| type | boolean | <p>true: 심플모드 활성화.<br>false: 심플모드 비활성화.</p> |

{% endtab %}

{% tab title="Template" %}

```javascript
Module.SetSimpleMode(0);
Module.SetSimpleMode(1);
```

{% endtab %}
{% endtabs %}

### XDClearInputPoint() → boolean

> 입력 점 리스트를 초기화합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   true: 초기화 성공.
    -   false : 초기화 실패.

{% endtab %}

{% tab title="Template" %}

```javascript
Module.XDClearInputPoint();
```

{% endtab %}
{% endtabs %}

### XDEMapCreateLayer(layerName, url, port, select, visible, userLayer, layerType, minLevel, maxLevel)

> XDServer 기반 타일 레이어를 추가합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type    | Description                                                      |
| ----- | ------- | ---------------------------------------------------------------- |
| layerName | string | <p>레이어 이름.<br>XDServer에서 서비스 되는 레이어 이름 적용.</p> |
| url | string | <p>XDServer 서비스 URL</p> |
| port | boolean | <p>포트 번호(현재 미사용).</p> |
| select | boolean | <p>레이어 오브젝트 선택 가능 여부.</p> |
| visible | boolean | <p>레이어 가시화 여부.</p> |
| userLayer | boolean | <p>XDServer 서비스 여부<br>true: 서비스하는 경우.<br>false: 서비스하지 않는 경우.</p> |
| layerType | number | <p>레이어 타입.</p> |
| minLevel | number | <p>레이어 타일 최소 레벨.</p> |
| maxLevel | number | <p>레이어 타일 최대 레벨.</p> |

{% endtab %}

{% tab title="Template" %}

```javascript
Module.XDEMapCreateLayer("facility_build", "server.url", 0, true, true, false, 9, 0, 15);
```

{% endtab %}
{% endtabs %}

### XDEPlanetRefresh()

> 지형,영상 서버 변경 후 화면의 재 갱신을 요청합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDEPlanetRefresh();
```

{% endtab %}
{% endtabs %}

### XDSetCamPositionLonLat(longitude, latitude, distance, angle) → boolean

> 경/위도 기준으로 카메라 위치를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type    | Description                                                      |
| ----- | ------- | ---------------------------------------------------------------- |
| longitude | number | <p>카메라 위치 좌표(경도).</p> |
| latitude | number | <p>카메라 위치 좌표(위도).</p> |
| distance | number | <p>카메라 위치 좌표(고도).</p> |
| angle | number | <p>카메라의 기울기(tilt).</p> |

-   Return
    -   true: 이동 성공.
    -   false: 이동 실패(초기화가 되지 않았을 경우).

{% endtab %}

{% tab title="Template" %}

```javascript
Module.XDSetCamPositionLonLat(129.128265, 35.171834, 500.0, 20);
```

{% endtab %}
{% endtabs %}

### XDIsMouseOverDiv(block)

> 지도 내 클릭 이벤트 사용 유무를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type    | Description                                                      |
| ----- | ------- | ---------------------------------------------------------------- |
| block | boolean | <p>true: 클릭 이벤트 비활성화.<br>false: 클릭 이벤트 활성화.</p> |

{% endtab %}

{% tab title="Template" %}

```javascript
Module.XDIsMouseOverDiv(false);
```

{% endtab %}
{% endtabs %}

### XDIsKeyOverDiv(block)

> 지도 내 키보드 이벤트 사용 유무를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type    | Description                                                      |
| ----- | ------- | ---------------------------------------------------------------- |
| block | boolean | <p>true: 키보드 이벤트 비활성화.<br>false: 키보드 이벤트 활성화.</p> |

{% endtab %}

{% tab title="Template" %}

```javascript
Module.XDIsKeyOverDiv(false);
```

{% endtab %}
{% endtabs %}

### XDRenderData()

> 화면의 재 갱신을 요청합니다.
>
> 이벤트가 없을 경우 화면을 유지합니다.
>
> 이벤트 없이 화면 갱신이 필요할 경우 사용 가능합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDRenderData();
```

{% endtab %}
{% endtabs %}

### XDSetMouseState(mode)

> 마우스 모드를 변경합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                             |
| ---- | ------ | ------------------------------------------------------- |
| mode | number | [Mouse Type List](../etc/type-list.md#mouse-type-list). |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### XDSetLayerMoveZ(layername, alt)

> 드론 LOD 높이를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name 		 | Type   | Description                         |
| ---------- | ------ | ----------------------------------- |
| layername  | string | 드론 LOD 레이어 이름. 				|
| alt 		 | number | 드론 LOD 레이어 높이 설정. 			|

-   Return
    -   true: 높이 설정 성공.
    -   false: 높이 설정 실패.
    -   실패 조건
        -   엔진이 로드되지 않았을 경우.
        -   레이어가 없을 경우.
	
-   Sample
    -   [Sandbox_Layer Drone LOD](https://sandbox.egiscloud.com/code/main.do?id=layer_drone_lod)

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### GoogleMap() / OpenStreetMap() / ArcMap() / WMTS() / BingMap() / KakaoMap() / NaverMap() / XDLMap() / SKYMap() / DawulMap()

> 배경지도를 변경합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSImageryProvider](../layer/jsImageryProvider.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
```

{% endtab %}
{% endtabs %}

### setInspector(mode)

> 엔진 모니터링 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                             |
| ---- | ------ | ------------------------------------------------------- |
| mode | boolean | 엔진 모니터링 사용 여부 설정. |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getInspector() → object

> 엔진 모니터링 결과값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   FPS: 현재 FPS.
    -   Terrain: 지형 요청 URL.
    -   Satellite: 영상 요청 URL.
    -   LayerCount: 총 레이어 수.
    -   LayerName: 레이어 이름.
    -   RequestCount: 요청 수.
    -   SuccessCount: 요청 성공 수.
    -   TotalRequestTime: 총 요청 시간.
    -   MaxRequestTime: 최대 요청 시간.
    -   AvgRequestTime: 평균 요청 시간.
    -   RenderObjCount: 현재 랜더링 객체 수.
    -   MaxRenderTime: 최대 랜더링 시간.
    -   AvgRenderTime: 평균 랜더링 시간.
    -   Layer: 레이어 리스트.
    -   LayerType: 레이어 타입.
    -   ObjectCount: 객체 수.
    -   FaceCount: face 수.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### refreshInspector()

> 엔진 모니터링을 초기화 합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                             |
| ---- | ------ | ------------------------------------------------------- |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTileLayerList() → [CJSLayerList](../layer/jslayerlist.md)

> 타일 레이어 리스트를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                             |
| ---- | ------ | ------------------------------------------------------- |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getObjectLayerList() → [CJSLayerList](../layer/jslayerlist.md)

> 옥트리 레이어 리스트를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                             |
| ---- | ------ | ------------------------------------------------------- |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### PauseMainLoop()

> 엔진의 메인 루프를 일시 정지합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.PauseMainLoop();
```

{% endtab %}
{% endtabs %}

### ResumeMainLoop()

> 일시 정지된 엔진의 메인 루프를 재개합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.ResumeMainLoop();
```

{% endtab %}
{% endtabs %}

### SetAPIKey(key)

> 브이월드 API 인증키를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                    |
| ---- | ------ | ------------------------------- |
| key  | string | Base64로 인코딩된 API 인증키.  |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetAPIKey("BASE64_ENCODED_API_KEY");
```

{% endtab %}
{% endtabs %}

### SetStart2D()

> 지도를 2D(평면) 모드로 시작하도록 설정합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.SetStart2D();
```

{% endtab %}
{% endtabs %}

### RefreshRTT()

> RTT(Render To Texture) 갱신을 요청합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.RefreshRTT();
```

{% endtab %}
{% endtabs %}

### ReadReservoir(layerName, objectName, hostName, waterSHP, altitude)

> 서울시 상수도 배수지(저수조) 데이터를 읽어와 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name       | Type   | Description                |
| ---------- | ------ | ---------------------------- |
| layerName  | string | 레이어 명칭.                |
| objectName | string | 객체 고유 명칭.             |
| hostName   | string | 데이터 요청 서버 주소.      |
| waterSHP   | string | 배수지 수면 SHP 파일 명칭. |
| altitude   | number | 배수지 고도 값.             |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.ReadReservoir("reservoirLayer", "reservoir_01", "server.url", "water.shp", 50.0);
```

{% endtab %}
{% endtabs %}

### SetHeightReservoirWater(layerName, objectName, height)

> 배수지(저수조) 객체의 수위 높이를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name       | Type   | Description          |
| ---------- | ------ | ---------------------- |
| layerName  | string | 레이어 명칭.          |
| objectName | string | 객체 고유 명칭.       |
| height     | number | 설정할 수위 높이 값. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetHeightReservoirWater("reservoirLayer", "reservoir_01", 5.0);
```

{% endtab %}
{% endtabs %}

### unload()

> 엔진(월드) 인스턴스를 해제합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.unload();
```

{% endtab %}
{% endtabs %}

### setRemoveVertexMemory(remove)

> 사용한 정점(vertex) 데이터를 메모리에서 제거할지 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type    | Description                                                    |
| ------ | ------- | ------------------------------------------------------------------|
| remove | boolean | <p>true: 사용 후 정점 메모리 제거.<br>false: 정점 메모리 유지.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setRemoveVertexMemory(true);
```

{% endtab %}
{% endtabs %}

### SetEffectWeight(weight)

> 이펙트(효과) 가중치를 설정합니다. 0 ~ 100 범위로 제한됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type   | Description                            |
| ------ | ------ | ---------------------------------------- |
| weight | number | 이펙트 가중치 값 (0 ~ 100 범위로 clamp). |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetEffectWeight(50.0);
```

{% endtab %}
{% endtabs %}

### createColor() → [JSColor](../core/jscolor.md)

> 기본값(ARGB 255,255,255,255)을 갖는 [JSColor](../core/jscolor.md) 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSColor](../core/jscolor.md): 생성한 색상 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let color = Module.createColor();
```

{% endtab %}
{% endtabs %}

### createPolygon(id) → [JSPolygon](../object/jspolygon.md)

> 평면 폴리곤 객체를 생성합니다.
>
> 좌표 없이 생성되며, 좌표는 [JSPolygon](../object/jspolygon.md)의 setCoordinates()로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSPolygon](../object/jspolygon.md): 생성한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createPolygon("newPolygon");
```

{% endtab %}
{% endtabs %}

### createFlowPolygon(id) → [JSFlowPolygon](../object/jsflowpolygon.md)

> 물 흐름 효과 폴리곤 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSFlowPolygon](../object/jsflowpolygon.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let flowPolygon = Module.createFlowPolygon("newFlowPolygon");
```

{% endtab %}
{% endtabs %}

### createTimeSeriesObject(id) → [JSTimeSeriesObject](../object/jstimeseriesobject.md)

> 시계열 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSTimeSeriesObject](../object/jstimeseriesobject.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createTimeSeriesObject("newTimeSeries");
```

{% endtab %}
{% endtabs %}

### createAnimationObject(id) → [JSAnimationObject](../object/jsanimationobject.md)

> 시간 경과에 따라 회전하는 원기둥형 애니메이션 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSAnimationObject](../object/jsanimationobject.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createAnimationObject("newAnimation");
```

{% endtab %}
{% endtabs %}

### createColorPolygon(id) → [JSColorPolygon](../object/jscolorpolygon.md)

> 그라데이션 폴리곤 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSColorPolygon](../object/jscolorpolygon.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let colorPolygon = Module.createColorPolygon("newColorPolygon");
```

{% endtab %}
{% endtabs %}

### createColorGrid(id) → [JSColorGrid](../object/jscolorgrid.md)

> 2차원 격자 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSColorGrid](../object/jscolorgrid.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let colorGrid = Module.createColorGrid("newColorGrid");
```

{% endtab %}
{% endtabs %}

### createColorGrid3D(id) → [JSColorGrid3D](../object/jscolorgrid3d.md)

> 3차원 격자 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSColorGrid3D](../object/jscolorgrid3d.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let colorGrid3D = Module.createColorGrid3D("newColorGrid3D");
```

{% endtab %}
{% endtabs %}

### createMultiCube(id, position, combineTerrain) → [JSMultiCube](../object/jsmulticube.md)

> 멀티 큐브 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name           | Type                                    | Description                                                            |
| -------------- | ---------------------------------------- | ------------------------------------------------------------------------ |
| id             | string                                    | 객체 고유 명칭.                                                        |
| position       | [JSVector3D](../core/jsvector3d.md)      | 큐브 중심 위치 좌표(경도, 위도, 고도).                                 |
| combineTerrain | boolean                                   | <p>true: 지형 고도값을 반영하여 위치 계산.<br>false: 지형 고도 미반영.</p> |

-   Return
    -   [JSMultiCube](../object/jsmulticube.md): 생성한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let vPosition = new Module.JSVector3D(129.1292403, 35.1721634, 100.0);
let object = Module.createMultiCube("newMultiCube", vPosition, false);
```

{% endtab %}
{% endtabs %}

### createReal3D(id) → [JSReal3D](../object/jsreal3d.md)

> 시설물(건물) 형태를 출력하는 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSReal3D](../object/jsreal3d.md): 생성한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createReal3D("newReal3D");
```

{% endtab %}
{% endtabs %}

### createInstanceObject(id) → [JSInstanceObject](../object/jsinstanceobject.md)

> 인스턴스 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSInstanceObject](../object/jsinstanceobject.md): 생성한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let instanceObject = Module.createInstanceObject("newInstance");
```

{% endtab %}
{% endtabs %}

### getLayerList() → [JSLayerList](../layer/jslayerlist.md)

> 서비스 레이어 리스트([JSLayerList](../layer/jslayerlist.md)) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSLayerList](../layer/jslayerlist.md): 반환한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let layerList = Module.getLayerList();
```

{% endtab %}
{% endtabs %}

### getUserLayer() → [JSLayer](../layer/jslayer.md)

> Module.create\* 계열 API로 생성한 객체가 기본으로 속하는 사용자 임시 레이어([JSLayer](../layer/jslayer.md)) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSLayer](../layer/jslayer.md): 반환한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let layer = Module.getUserLayer();
```

{% endtab %}
{% endtabs %}

### GetClickPosition() → string

> 마지막으로 클릭한 지점의 좌표를 문자열로 반환합니다.
>
> "경도_위도_고도" 형식("\_"로 구분된 문자열)으로 반환됩니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: "경도_위도_고도" 형식의 좌표 문자열.

{% endtab %}
{% tab title="Template" %}

```javascript
let position = Module.GetClickPosition(); // ex) "129.128265_35.171834_50.000000"
```

{% endtab %}
{% endtabs %}

### getClickPointColor() → [JSColor](../core/jscolor.md)

> 클릭 지점에 표시되는 포인트의 색상을 반환합니다.
>
> 기본값은 ARGB(255, 255, 255, 255) 입니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSColor](../core/jscolor.md): 클릭 지점 포인트의 색상.

{% endtab %}
{% tab title="Template" %}

```javascript
let color = Module.getClickPointColor();
```

{% endtab %}
{% endtabs %}

### setClickPointColor(color)

> 클릭 지점에 표시되는 포인트의 색상을 설정합니다.
>
> 투명도(alpha) 값은 255로 고정 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                           | Description  |
| ----- | ------------------------------- | ------------ |
| color | [JSColor](../core/jscolor.md)  | 설정할 색상. |

{% endtab %}
{% tab title="Template" %}

```javascript
let color = new Module.JSColor(255, 255, 0, 0);
Module.setClickPointColor(color);
```

{% endtab %}
{% endtabs %}

### getClickPointScale() → number

> 클릭 지점에 표시되는 포인트의 크기(scale) 값을 반환합니다.
>
> 기본값은 1.0 입니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 클릭 지점 포인트의 크기(scale) 값.

{% endtab %}
{% tab title="Template" %}

```javascript
let scale = Module.getClickPointScale();
```

{% endtab %}
{% endtabs %}

### setClickPointScale(scale)

> 클릭 지점에 표시되는 포인트의 크기(scale) 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description             |
| ----- | ------ | ------------------------ |
| scale | number | 설정할 포인트 크기 값. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setClickPointScale(2.0);
```

{% endtab %}
{% endtabs %}

### InitCameraPosition(longitude, latitude, altitude, tilt)

> 지도 초기화(Module.initialize()) 시 적용될 카메라의 초기 위치를 설정합니다.
>
> Module.initialize() 호출 전에 사용해야 합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description               |
| --------- | ------ | -------------------------- |
| longitude | number | 카메라 초기 위치 좌표(경도). |
| latitude  | number | 카메라 초기 위치 좌표(위도). |
| altitude  | number | 카메라 초기 위치 좌표(고도). |
| tilt      | number | 카메라의 초기 기울기(tilt).  |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.InitCameraPosition(129.128265, 35.171834, 500.0, 20);
```

{% endtab %}
{% endtabs %}

### createLODPOI(id) → [JSLODPOI](../object/jslodpoi.md)

> 카메라 거리(LOD)에 따라 헤드/타겟 아이콘과 연결선을 표시하는 POI 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSLODPOI](../object/jslodpoi.md): 생성한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let lodPoi = Module.createLODPOI("newLODPOI");
```

{% endtab %}
{% endtabs %}

### createGLTF(id) → [JSPolygon](../object/jspolygon.md)

> glTF 포맷 객체를 생성합니다.
>
> [JSPolygon](../object/jspolygon.md) 타입으로 반환되며, JSPolygon의 API를 통해 제어합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSPolygon](../object/jspolygon.md): 생성한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createGLTF("newGLTF");
```

{% endtab %}
{% endtabs %}

### createOverlayObject(id) → [JSPolygon](../object/jspolygon.md)

> 오버레이 객체를 생성합니다.
>
> [JSPolygon](../object/jspolygon.md) 타입으로 반환되며, JSPolygon의 API를 통해 제어합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSPolygon](../object/jspolygon.md): 생성한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createOverlayObject("newOverlay");
```

{% endtab %}
{% endtabs %}

### createRoadObject(id, type) → [JSPolygon](../object/jspolygon.md)

> 도로 객체를 생성합니다.
>
> [JSPolygon](../object/jspolygon.md) 타입으로 반환되며, JSPolygon의 API를 통해 제어합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                                                     |
| ---- | ------ | -------------------------------------------------------------------------------- |
| id   | string | 객체 고유 명칭.                                                                |
| type | number | 도로 타입(ROAD_OVERPASS, ROAD_TUNNEL, ROAD_UNDERPASS, ROAD_BRIDGE 중 하나 지정). |

-   Return
    -   [JSPolygon](../object/jspolygon.md): 생성한 객체.

{% endtab %}
{% tab title="Template" %}

```javascript
let object = Module.createRoadObject("newRoad", Module.ROAD_BRIDGE);
```

{% endtab %}
{% endtabs %}

### getDataVisualizer() → [JSDataVisualizer](../datavisualizer/jsdatavisualizer.md)

> JSON 데이터를 기반으로 포인트/라인/그리드/폴리곤 형태의 대량 데이터를 시각화하는 [JSDataVisualizer](../datavisualizer/jsdatavisualizer.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSDataVisualizer](../datavisualizer/jsdatavisualizer.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var visualizer = Module.getDataVisualizer();
```

{% endtab %}
{% endtabs %}

### getControl() → [JSControl](../option/jscontrol.md)

> 지도 내 각종 이벤트 관련 기능을 제어하는 [JSControl](../option/jscontrol.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSControl](../option/jscontrol.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var object = Module.getControl();
```

{% endtab %}
{% endtabs %}

### createFigure(id) → [JSFigure](../object/jsfigure.md)

> 다각기둥 형태의 [JSFigure](../object/jsfigure.md) 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSFigure](../object/jsfigure.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
let figure = Module.createFigure("newFigure");
```

{% endtab %}
{% endtabs %}

### createVideoObject(id) → [JSVideoObject](../object/jsvideoobject.md)

> 멀티 비디오 텍스쳐 객체([JSVideoObject](../object/jsvideoobject.md))를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSVideoObject](../object/jsvideoobject.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var object = Module.createVideoObject("newVideo");
```

{% endtab %}
{% endtabs %}

### createVoxelObject(id) → [JSVoxelObject](../object/jsvoxelobject.md)

> 볼륨(연기, 구름, 불꽃, 물 등) 시각화를 위한 복셀(Voxel) 객체([JSVoxelObject](../object/jsvoxelobject.md))를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSVoxelObject](../object/jsvoxelobject.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var voxel = Module.createVoxelObject("newVoxel");
```

{% endtab %}
{% endtabs %}

### getAnalysisGridShadow() → [JSAnalysisGridShadow](../analysis/jsanalysisgridshadow.md)

> 수인한도(일영) 분석 기능을 제어하는 [JSAnalysisGridShadow](../analysis/jsanalysisgridshadow.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSAnalysisGridShadow](../analysis/jsanalysisgridshadow.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var gridShadow = Module.getAnalysisGridShadow();
```

{% endtab %}
{% endtabs %}

### getIndoor() → [JSIndoor](../camera/jsindoor.md)

> 실내(Indoor) 1인칭 이동 모드를 제어하는 [JSIndoor](../camera/jsindoor.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSIndoor](../camera/jsindoor.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var indoor = Module.getIndoor();
```

{% endtab %}
{% endtabs %}

### getEditTerrain() → [JSEditTerrain](../analysis/jseditterrain.md)

> 성절토(지형 편집) 분석 기능을 제어하는 [JSEditTerrain](../analysis/jseditterrain.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSEditTerrain](../analysis/jseditterrain.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var editTerrain = Module.getEditTerrain();
```

{% endtab %}
{% endtabs %}

### getOption() → [JSOption](../option/jsoption.md)

> 엔진 환경 설정 기능을 제어하는 [JSOption](../option/jsoption.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSOption](../option/jsoption.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var option = Module.getOption();
```

{% endtab %}
{% endtabs %}

### getIndexMap() → [JSIndexMap](../map/jsindexmap.md)

> 인덱스 맵 기능을 제어하는 [JSIndexMap](../map/jsindexmap.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSIndexMap](../map/jsindexmap.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var map = Module.getIndexMap();
```

{% endtab %}
{% endtabs %}

### XDConvertCartesianToSpherical(x, y, z) → string

> 직교좌표(X, Y, Z)를 구면좌표(경도, 위도, 고도)로 변환합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description   |
| ---- | ------ | --------------- |
| x    | number | 직교좌표 X 값. |
| y    | number | 직교좌표 Y 값. |
| z    | number | 직교좌표 Z 값. |

-   Return
    -   string: "경도#위도#고도" 형식("#"로 구분된 문자열).

{% endtab %}
{% tab title="Template" %}

```javascript
let result = Module.XDConvertCartesianToSpherical(-3040429.86, 3568342.65, 3645082.05); // ex) "129.128265#35.171834#50.000000"
```

{% endtab %}
{% endtabs %}

### XDEClearMeasurement()

> 모든 측정/분석(성절토 셀 플랜, 가시권, 거리, 면적, 레이더 커버리지) 객체와 입력 점 리스트를 초기화합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDEClearMeasurement();
```

{% endtab %}
{% endtabs %}

### XDClearCircleMeasurement()

> 반경(원형) 측정 객체와 입력 점 리스트를 초기화합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDClearCircleMeasurement();
```

{% endtab %}
{% endtabs %}

### XDClearDistanceMeasurement()

> 거리 측정 객체와 입력 점 리스트를 초기화합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDClearDistanceMeasurement();
```

{% endtab %}
{% endtabs %}

### XDClearAltDistanceMeasurement()

> 고도차(수직) 거리 측정 객체와 지형 절개(단면) 표시, 입력 점 리스트를 초기화합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDClearAltDistanceMeasurement();
```

{% endtab %}
{% endtabs %}

### XDClearAreaMeasurement()

> 면적 측정 객체와 입력 점 리스트를 초기화합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDClearAreaMeasurement();
```

{% endtab %}
{% endtabs %}

### XDClearDistanceObject(key) → boolean

> 지정한 키의 거리 측정 객체를 삭제합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                          |
| ---- | ------ | ----------------------------------------------------------------------|
| key  | string | 삭제할 거리 측정 객체의 고유 키(`Module.XDGetDistanceList()`로 조회 가능). |

-   Return
    -   true: 삭제 성공.
    -   false: 삭제 실패(해당 키의 객체가 없을 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDClearDistanceObject("ANAL_DIST_0");
```

{% endtab %}
{% endtabs %}

### XDClearAreaObject(key) → boolean

> 지정한 키의 면적 측정 객체를 삭제합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                       |
| ---- | ------ | ---------------------------------------------------------------------|
| key  | string | 삭제할 면적 측정 객체의 고유 키(`Module.XDGetAreaeList()`로 조회 가능). |

-   Return
    -   true: 삭제 성공.
    -   false: 삭제 실패(해당 키의 객체가 없을 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDClearAreaObject("ANAL_AREA_0");
```

{% endtab %}
{% endtabs %}

### XDGetDistanceList() → string

> 등록된([XDAddDistanceMeasurement](moduleapi.md)로 추가된) 거리 측정 객체의 키 목록을 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   string: 거리 측정 객체 키 목록(","로 구분된 문자열).

{% endtab %}
{% tab title="Template" %}

```javascript
let list = Module.XDGetDistanceList(); // ex) "ANAL_DIST_0,ANAL_DIST_1"
```

{% endtab %}
{% endtabs %}

### XDGetAreaeList() → string

> 등록된([XDAddAreaMeasurement](moduleapi.md)로 추가된) 면적 측정 객체의 키 목록을 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   string: 면적 측정 객체 키 목록(","로 구분된 문자열).

{% endtab %}
{% tab title="Template" %}

```javascript
let list = Module.XDGetAreaeList(); // ex) "ANAL_AREA_0,ANAL_AREA_1"
```

{% endtab %}
{% endtabs %}

### XDAddDistanceMeasurement()

> 현재 입력 중인 거리 측정 점들을 리스트에 확정 추가하고, 입력 점 리스트를 초기화합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDAddDistanceMeasurement();
```

{% endtab %}
{% endtabs %}

### XDAddAreaMeasurement()

> 현재 입력 중인 면적 측정 폴리곤을 리스트에 확정 추가하고, 입력 점 리스트를 초기화합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDAddAreaMeasurement();
```

{% endtab %}
{% endtabs %}

### XDSetViewPoint(set)

> 조망점(조망권 분석) 지정 모드를 설정합니다.
>
> true 설정 시 현재 카메라 위치를 백업하고 조망점 지정 모드로 전환하며, false 설정 시 백업된 카메라 위치로 복귀합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                                       |
| ---- | ------- | ------------------------------------------------------------------------------------|
| set  | boolean | <p>true: 조망점 지정 모드 시작.<br>false: 조망점 지정 모드 종료(카메라 복귀).</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDSetViewPoint(true);
```

{% endtab %}
{% endtabs %}

### XDSetViewPointHeight(height)

> 조망 분석에 사용되는 조망 높이를 설정합니다.
>
> 최대 500.0으로 제한됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type   | Description                          |
| ------ | ------ | --------------------------------------|
| height | number | 조망 높이 값(최대 500.0으로 clamp). |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDSetViewPointHeight(100.0);
```

{% endtab %}
{% endtabs %}

### start(options) → number

> 지정한 canvas 엘리먼트에 지도를 생성합니다.
>
> [initialize](moduleapi.md) 이전부터 사용되던 초기화 API로, canvas ID 문자열 기반의 단순한 옵션 객체를 사용합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name         | Type    | Description                                              |
| ------------ | ------- | --------------------------------------------------------- |
| canvas       | string  | 지도를 표시할 canvas 엘리먼트의 ID.                        |
| width        | number  | 지도 화면 너비(px). 미입력 시 canvas의 clientWidth 값 사용. |
| height       | number  | 지도 화면 높이(px). 미입력 시 canvas의 clientHeight 값 사용.|
| worker_use   | boolean | web worker 사용 여부.                                      |
| worker_path  | string  | web worker 파일 요청 URL.                                  |
| worker_count | number  | 생성할 web worker 개수.                                    |

-   Return
    -   1: 생성 성공.
    -   0: 생성 실패(canvas를 찾지 못했거나 초기화에 실패한 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.start({
    canvas: "canvas",
    width: 1280,
    height: 720,
    worker_use: true,
    worker_path: "./XDWorldWorker.js",
    worker_count: 5,
});
```

{% endtab %}
{% endtabs %}

### preventDefault(event)

> addEventListener로 등록된 이벤트(예: 마우스 오른쪽 클릭 시 컨텍스트 메뉴)의 기본 동작을 막습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description                          |
| ----- | ------ | ------------------------------------- |
| event | object | 이벤트 발생 시 전달되는 이벤트 객체. |

{% endtab %}
{% tab title="Template" %}

```javascript
canvas.addEventListener("contextmenu", function (e) {
    Module.preventDefault(e);
});
```

{% endtab %}
{% endtabs %}

### SetUseWebWorker(use)

> web worker 사용 여부를 설정합니다.
>
> false로 설정 시 현재 생성되어 있는 web worker를 모두 종료합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description             |
| ---- | ------- | ------------------------ |
| use  | boolean | web worker 사용 여부.   |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetUseWebWorker(false);
```

{% endtab %}
{% endtabs %}

### SetResourceServerAddr(url)

> 엔진에서 사용하는 리소스(별자리, 태풍, 파티클 이미지 등) 요청 서버 주소를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description        |
| ---- | ------ | -------------------- |
| url  | string | 리소스 서버 주소.   |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetResourceServerAddr("//xdworld.vworld.kr");
```

{% endtab %}
{% endtabs %}

### XDSetStarBox(show)

> 우주(별자리) 배경 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                                                    |
| ---- | ------- | ------------------------------------------------------------------------------------------------ |
| show | boolean | <p>true: 별자리 배경 표시(최초 호출 시 관련 리소스를 초기화).<br>false: 별자리 배경 숨김.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDSetStarBox(true);
```

{% endtab %}
{% endtabs %}

### XDGetMouseState() → number

> 현재 설정된 마우스 모드 값을 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   number: 현재 마우스 모드 값. [Mouse Type List](../etc/type-list.md#mouse-type-list).
    -   -1: 지도가 생성되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let mode = Module.XDGetMouseState();
```

{% endtab %}
{% endtabs %}

### XDAnalClear()

> 성절토 셀 플랜, 가시권, 거리, 면적, 레이더 커버리지 등 분석 결과 객체를 초기화합니다.
>
> [XDEClearMeasurement](moduleapi.md)와 달리 현재 입력 중인 점 리스트는 초기화하지 않습니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDAnalClear();
```

{% endtab %}
{% endtabs %}

### XDCamMoveCommand(cmd)

> 키보드 입력과 동일한 카메라 이동/회전 명령을 코드로 직접 실행합니다.
>
> 이동/회전/줌 각각의 명령은 [JSCamera](../camera/jscamera.md)의 관련 사용 설정(키 입력 이동/회전/줌 허용 여부)이 켜져 있을 때만 동작합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                                                                                                                                                       |
| ---- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| cmd  | number | <p>카메라 이동/회전 명령 코드(키보드 keyCode와 동일).<br>19: 전방 이동(패닝).<br>20: 후방 이동(패닝).<br>21: 좌측 이동(패닝).<br>22: 우측 이동(패닝).<br>33: Y축(heading) 회전.<br>45: Y축(heading) 반대 방향 회전.<br>92: X축(tilt) 회전.<br>93: X축(tilt) 반대 방향 회전.<br>102 / 103: 카메라 고도(줌) 이동(서로 반대 방향).</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDCamMoveCommand(19); // 카메라 전방 이동
```

{% endtab %}
{% endtabs %}

### XDCamRotateXAxis(angle)

> 카메라의 X축 회전(tilt, 상하 기울기)을 각도만큼 누적 적용합니다.
>
> 설정된 최소/최대 tilt 각도 범위를 벗어나면 해당 한계값으로 고정됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description                        |
| ----- | ------ | ------------------------------------ |
| angle | number | 누적 적용할 X축(tilt) 회전 각도.   |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDCamRotateXAxis(1.0);
```

{% endtab %}
{% endtabs %}

### XDCamRotateYAxis(angle)

> 카메라의 Y축 회전(heading, 방위각)을 각도만큼 누적 적용합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description                            |
| ----- | ------ | ---------------------------------------- |
| angle | number | 누적 적용할 Y축(heading) 회전 각도.    |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDCamRotateYAxis(1.0);
```

{% endtab %}
{% endtabs %}

### EventMouseWheel(delta, canvasX, canvasY)

> 지정한 canvas 좌표를 기준으로 마우스 휠(줌) 이벤트를 코드로 직접 실행합니다.
>
> 브라우저의 wheel 이벤트 발생 시 내부적으로 호출되는 로직과 동일한 함수입니다.

{% tabs %}
{% tab title="Infomation" %}

| Name    | Type   | Description                                    |
| ------- | ------ | ------------------------------------------------ |
| delta   | number | 휠 이동량(부호에 따라 확대/축소 방향이 결정).   |
| canvasX | number | 이벤트가 발생한 canvas 기준 X좌표.              |
| canvasY | number | 이벤트가 발생한 canvas 기준 Y좌표.              |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.EventMouseWheel(-100, 640, 360);
```

{% endtab %}
{% endtabs %}

### getViewCamera() → [JSCamera](../camera/jscamera.md)

> 카메라 제어를 위한 [JSCamera](../camera/jscamera.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSCamera](../camera/jscamera.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var camera = Module.getViewCamera();
```

{% endtab %}
{% endtabs %}

### getAddObject() → object

> 레이어에 점/보드(이미지)/선/폴리곤/원/멀티큐브 등의 3D 객체를 낮은 수준(low-level)으로 직접 추가·삭제하는 내부 헬퍼 객체(CSOPAddObject)를 반환합니다.
>
> 각 JSObject 계열 클래스가 제공되기 이전부터 존재하던 방식으로, 레이어 이름과 객체 키를 직접 지정하여 객체를 다룹니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   object(CSOPAddObject): 아래와 같은 함수를 제공.
        -   Add3DPoint, AddImgBoardObject, AddBoardLine, AddCanvasTexture, AddTypeLine, Add3DPolygon: 각 형태의 3D 객체를 레이어에 추가.
        -   CreateCircleObject, CreateMultiCube, CreateBoardTexture, CreateCelAniOjbect: 원/멀티큐브/보드 텍스쳐/Cel 애니메이션 객체 생성.
        -   FindObjectKey, Delete3DObject: 객체 키 조회 및 삭제.
        -   SearchEstateData 등 기타 부가 기능.

{% endtab %}
{% tab title="Template" %}

```javascript
var addObject = Module.getAddObject();
```

{% endtab %}
{% endtabs %}

### getMath() → [JSMath](../etc/jsmath.md)

> 좌표/수학 연산 유틸리티를 제공하는 [JSMath](../etc/jsmath.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSMath](../etc/jsmath.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var math = Module.getMath();
```

{% endtab %}
{% endtabs %}

### getLandScape() → [JSLandScape](../analysis/jslandscape.md)

> 조망(경관) 분석(둘러보기) 기능을 제어하는 [JSLandScape](../analysis/jslandscape.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSLandScape](../analysis/jslandscape.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var landscape = Module.getLandScape();
```

{% endtab %}
{% endtabs %}

### GetJavaScriptVal(response)

> JavaScript에서 전달한 배열(바이트) 데이터의 길이를 콘솔에 출력합니다.
>
> 전달받은 데이터를 별도로 반환하거나 유지하지 않으며, 그 외의 부수효과는 없습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type  | Description                       |
| -------- | ----- | ----------------------------------- |
| response | array | 길이를 확인할 바이트 배열 데이터. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.GetJavaScriptVal(new Uint8Array([1, 2, 3]));
```

{% endtab %}
{% endtabs %}

### setEnableMapControl(set)

> 화면에 표시되는 맵 컨트롤(방향 이동/회전 컴퍼스 형태의 UI) 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                                                             |
| ---- | ------ | ---------------------------------------------------------------------------------------------------------|
| set  | number | <p>0: 맵 컨트롤 숨김.<br>1: 맵 컨트롤 표시(히든 모드 사용).<br>2: 맵 컨트롤 표시(히든 모드 미사용).</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setEnableMapControl(2);
```

{% endtab %}
{% endtabs %}

### setPositionMapControl(set)

> 맵 컨트롤 UI가 표시되는 화면상 기준 위치(3x3 그리드)를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                                                                                                       |
| ---- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------|
| set  | number | <p>맵 컨트롤 위치 기준점(0~8).<br>0-1-2<br>3-4-5<br>6-7-8<br>(기본은 좌측 상단 기준이며, 우측 열은 우측, 하단 행은 하단을 기준으로 여백이 계산됩니다.)</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setPositionMapControl(8); // 우측 하단 기준
```

{% endtab %}
{% endtabs %}

### setVisibleRange(layerName, range, maxHidden)

> 지정한 레이어의 LOD(가시화) 비율과 최대 숨김 거리를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description                |
| --------- | ------ | ---------------------------- |
| layerName | string | 설정할 레이어 이름.        |
| range     | number | LOD 비율 값.               |
| maxHidden | number | 최대 숨김 거리 값.         |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setVisibleRange("facility_build", 1.0, 5000.0);
```

{% endtab %}
{% endtabs %}

### SetMobileMode(mode)

> 서비스 모드(PC/모바일)를 설정하고, 지형 LOD 비율을 함께 조정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                             |
| ---- | ------ | -------------------------------------------------------------------------|
| mode | number | <p>0: PC 모드(지형 LOD 비율 1.0).<br>0이 아닌 값: 모바일 모드(지형 LOD 비율 2.0).</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetMobileMode(1);
```

{% endtab %}
{% endtabs %}

### SetSimpleModeLineRender(mode)

> [SetSimpleMode](moduleapi.md) 적용 시, 오브젝트의 엣지 라인 렌더링 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                                       |
| ---- | ------- | ------------------------------------------------------------------------------------|
| mode | boolean | <p>true: 심플 모드에서 엣지 라인 표시.<br>false: 엣지 라인 미표시.</p>            |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetSimpleModeLineRender(true);
```

{% endtab %}
{% endtabs %}

### XDESHPStatsElement(fieldIndex, maxHeight, alpha)

> SHP 통계(높이 돌출) 표현에 사용할 필드, 최대 높이, 투명도를 설정합니다.
>
> [XDEMashupFile](moduleapi.md)을 통계 모드(mashType 12: statsSHPFilePlanet)로 호출하기 전에 설정해야 하며, 지정한 필드 값이 클수록 maxHeight에 비례하여 더 높게 돌출됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description                                                    |
| --------- | ------ | ---------------------------------------------------------------- |
| fieldIndex | number | <p>통계 값으로 사용할 SHP(DBF) 필드 인덱스.<br>-1: 통계 미사용(기본값).</p> |
| maxHeight | number | 필드 최대값에 대응하는 돌출 높이(단위: m).                      |
| alpha     | number | 통계 표현 색상의 투명도(0~255).                                 |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESHPStatsElement(2, 1000.0, 200);
```

{% endtab %}
{% endtabs %}

### XDEMapRemoveLayer(layerName)

> 지정한 이름의 레이어를 지도(Map)와 지형(Planet) 양쪽에서 모두 제거합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description          |
| --------- | ------ | ---------------------- |
| layerName | string | 제거할 레이어 이름. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDEMapRemoveLayer("facility_build");
```

{% endtab %}
{% endtabs %}

### GetScreenShot(filename)

> 현재 화면을 캡쳐하여 로컬 파일로 다운로드합니다.
>
> 지정한 파일명의 확장자(.jpg/.jpeg 또는 .bmp)에 따라 저장 형식이 결정되며, 인식되지 않는 확장자인 경우 파일이 저장되지 않습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type   | Description                              |
| -------- | ------ | ------------------------------------------ |
| filename | string | 다운로드할 파일명(확장자 포함, jpg/bmp). |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.GetScreenShot("screenshot.jpg");
```

{% endtab %}
{% endtabs %}

### XDEMapCreateLayerEX(layerName, url, port, homeDir, select, visible, userLayer, layerType, minLevel, maxLevel)

> XDServer 기반 타일 레이어를 추가합니다. [XDEMapCreateLayer](moduleapi.md)에 URL 컨텍스트(homeDir) 지정 기능이 추가된 버전입니다.
>
> homeDir을 지정하지 않으면 레이어의 기본 컨텍스트 경로("/XDServer")가 그대로 사용되며, 타일/오브젝트 요청 URL 생성 시 이 경로가 서버 주소 뒤에 덧붙습니다.
>
> 레이어 생성 후 내부적으로 화면 Resize를 다시 호출합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type    | Description                                                                          |
| --------- | ------- | --------------------------------------------------------------------------------------|
| layerName | string  | <p>레이어 이름.<br>XDServer에서 서비스 되는 레이어 이름 적용.</p>                    |
| url       | string  | XDServer 서비스 URL                                                                  |
| port      | number  | 포트 번호(현재 미사용).                                                              |
| homeDir   | string  | 레이어의 URL 컨텍스트 경로(예: "/XDServer"). 요청 URL의 서버 주소 뒤에 덧붙습니다. |
| select    | boolean | 레이어 오브젝트 선택 가능 여부.                                                      |
| visible   | boolean | 레이어 가시화 여부.                                                                  |
| userLayer | boolean | <p>XDServer 서비스 여부<br>true: 서비스하는 경우.<br>false: 서비스하지 않는 경우.</p> |
| layerType | number  | 레이어 타입.                                                                         |
| minLevel  | number  | 레이어 타일 최소 레벨.                                                               |
| maxLevel  | number  | 레이어 타일 최대 레벨.                                                               |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDEMapCreateLayerEX("facility_build", "server.url", 0, "/XDServer2", true, true, false, 9, 0, 15);
```

{% endtab %}
{% endtabs %}

### XDCreateLayer(cType, layerName) → boolean

> 웹 요청 기반이 아닌 기본 레이어를 생성합니다.
>
> cType 값은 현재 내부 로직에서 사용되지 않으며, 생성되는 레이어는 항상 다용도 레이어(ELT_MULTILPE) 타입으로 고정됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description                                                              |
| --------- | ------ | --------------------------------------------------------------------------|
| cType     | number | <p>레이어 타입 지정용 문자 코드(ASCII).<br>현재 내부에서 사용되지 않음.</p> |
| layerName | string | 생성할 레이어 이름.                                                      |

-   Return
    -   true: 생성 성공(동일 이름 레이어가 없어 새로 생성됨).
    -   false: 생성 실패(초기화가 되지 않았거나, 동일 이름 레이어가 이미 존재하는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDCreateLayer("M".charCodeAt(0), "myLayer");
```

{% endtab %}
{% endtabs %}

### SetViewFPS(view)

> 화면에 FPS(초당 프레임 수) 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                             |
| ---- | ------- | ---------------------------------------------------------|
| view | boolean | <p>true: FPS 표시.<br>false: FPS 미표시.</p>            |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetViewFPS(true);
```

{% endtab %}
{% endtabs %}

### SetViewInfo(view)

> 화면에 엔진 정보창 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                             |
| ---- | ------- | ---------------------------------------------------------|
| view | boolean | <p>true: 정보창 표시.<br>false: 정보창 미표시.</p>      |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetViewInfo(true);
```

{% endtab %}
{% endtabs %}

### CreateViewInfo(data)

> 사용자 정의 콜백을 통해 얻은 픽셀 데이터로 정보창(엔진 정보) 표시용 텍스처를 생성합니다.
>
> data.callback 함수를 data.info를 인자로 호출한 결과에서 픽셀 데이터(data)와 크기(size.width/size.height)를 받아 텍스처를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                                                                                                                       |
| ---- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| data | object | <p>callback: function(info) → { data: Uint8Array(RGBA 픽셀 배열), size: { width: number, height: number } } 형태를 반환하는 함수.<br>info: callback 호출 시 전달할 값.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.CreateViewInfo({
    info: myInfo,
    callback: function (info) {
        // info를 이용해 캔버스 등에 그린 뒤 픽셀 데이터를 반환합니다.
        return { data: pixelArray, size: { width: 256, height: 128 } };
    },
});
```

{% endtab %}
{% endtabs %}

### SetViewInfoPosition(x, y)

> 정보창 UI가 표시되는 화면상 좌표를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description        |
| ---- | ------ | --------------------|
| x    | number | 정보창 X 좌표.    |
| y    | number | 정보창 Y 좌표.    |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetViewInfoPosition(10, 10);
```

{% endtab %}
{% endtabs %}

### SetViewShadowMap(shadowMap)

> 쉐도우맵(그림자) 사용 여부를 설정합니다.
>
> 설정 변경 시 기존 쉐도우맵 리소스를 초기화한 뒤 다시 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type    | Description                                             |
| --------- | ------- | ---------------------------------------------------------|
| shadowMap | boolean | <p>true: 쉐도우맵 사용.<br>false: 쉐도우맵 미사용.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetViewShadowMap(true);
```

{% endtab %}
{% endtabs %}

### XDESHPPipeElement(radius, depth, segment, alpha, r, g, b)

> SHP 기반 실시간 파이프(관로) 생성(스마트시티) 시 사용할 반지름, 깊이, 세그먼트 수, 색상을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name    | Type   | Description                          |
| ------- | ------ | ---------------------------------------|
| radius  | number | 파이프 반지름.                       |
| depth   | number | 파이프 매설 깊이.                    |
| segment | number | 파이프 원통 분할 세그먼트 수.        |
| alpha   | number | 색상 투명도(0~255).                  |
| r       | number | 색상 Red 값(0~255).                  |
| g       | number | 색상 Green 값(0~255).                |
| b       | number | 색상 Blue 값(0~255).                 |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESHPPipeElement(0.5, 1.0, 12, 255, 0, 128, 255);
```

{% endtab %}
{% endtabs %}

### XDESetDemUrlLayerName(url, layerName)

> 지형(DEM) 서버 URL과 레이어 이름을 변경합니다.
>
> 설정 값은 다음 지형 재생성 시 적용되며, 즉시 화면에 반영하려면 [XDEPlanetRefresh](moduleapi.md)를 호출해야 합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description             |
| --------- | ------ | -------------------------|
| url       | string | 지형(DEM) 서비스 URL. |
| layerName | string | 지형(DEM) 레이어 이름. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESetDemUrlLayerName("//server.url:8080", "dem_layer");
Module.XDEPlanetRefresh();
```

{% endtab %}
{% endtabs %}

### XDESetSatUrlLayerName(url, layerName)

> 영상(위성/항공 영상) 서버 URL과 레이어 이름을 변경합니다.
>
> 설정 값은 다음 지형 재생성 시 적용되며, 즉시 화면에 반영하려면 [XDEPlanetRefresh](moduleapi.md)를 호출해야 합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description              |
| --------- | ------ | --------------------------|
| url       | string | 영상 서비스 URL.        |
| layerName | string | 영상 레이어 이름.       |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESetSatUrlLayerName("//server.url:8080", "sat_layer");
Module.XDEPlanetRefresh();
```

{% endtab %}
{% endtabs %}

### XDESetDemUrlLayerNameEX(url, contextRoot, layerName)

> 지형(DEM) 서버 URL, 레이어 이름을 변경합니다. [XDESetDemUrlLayerName](moduleapi.md)에 URL 컨텍스트(contextRoot) 지정 기능이 추가된 버전입니다.
>
> url에 "http://" 또는 "https://"가 포함되어 있지 않으면 자동으로 앞에 "//"를 붙여 프로토콜 상대경로로 처리합니다.
>
> 설정 값은 다음 지형 재생성 시 적용되며, 즉시 화면에 반영하려면 [XDEPlanetRefresh](moduleapi.md)를 호출해야 합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name        | Type   | Description                          |
| ----------- | ------ | ---------------------------------------|
| url         | string | 지형(DEM) 서비스 URL.               |
| contextRoot | string | 지형(DEM) 서비스 URL 컨텍스트 경로. |
| layerName   | string | 지형(DEM) 레이어 이름.              |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESetDemUrlLayerNameEX("server.url:8080", "/XDServer", "dem_layer");
Module.XDEPlanetRefresh();
```

{% endtab %}
{% endtabs %}

### XDESetSatUrlLayerNameEX(url, contextRoot, layerName)

> 영상(위성/항공 영상) 서버 URL, 레이어 이름을 변경합니다. [XDESetSatUrlLayerName](moduleapi.md)에 URL 컨텍스트(contextRoot) 지정 기능이 추가된 버전입니다.
>
> url에 "http://" 또는 "https://"가 포함되어 있지 않으면 자동으로 앞에 "//"를 붙여 프로토콜 상대경로로 처리합니다.
>
> 설정 값은 다음 지형 재생성 시 적용되며, 즉시 화면에 반영하려면 [XDEPlanetRefresh](moduleapi.md)를 호출해야 합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name        | Type   | Description                     |
| ----------- | ------ | ----------------------------------|
| url         | string | 영상 서비스 URL.                |
| contextRoot | string | 영상 서비스 URL 컨텍스트 경로. |
| layerName   | string | 영상 레이어 이름.               |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESetSatUrlLayerNameEX("server.url:8080", "/XDServer", "sat_layer");
Module.XDEPlanetRefresh();
```

{% endtab %}
{% endtabs %}

### XDECreateTimeSeriesLayer(layerName, url, year, minLevel, maxLevel) → boolean

> 연도별 시계열 데이터를 표시하는 시계열 레이어를 등록합니다.
>
> 엔진 내부에 시계열 레이어를 하나만 유지하며, 재호출 시 기존에 등록된 시계열 레이어는 삭제되고 새 설정으로 교체됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description                 |
| --------- | ------ | ------------------------------|
| layerName | string | 시계열 레이어 이름.        |
| url       | string | 시계열 데이터 서비스 URL.  |
| year      | number | 조회할 연도.                |
| minLevel  | number | 레이어 타일 최소 레벨.      |
| maxLevel  | number | 레이어 타일 최대 레벨.      |

-   Return
    -   true: 등록 성공.
    -   false: 등록 실패(지형이 초기화되지 않은 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDECreateTimeSeriesLayer("timeseries_layer", "server.url", 2020, 0, 15);
```

{% endtab %}
{% endtabs %}

### XDECreateTimeSeriesLayerEX(layerName, url, contextRoot, year, minLevel, maxLevel) → boolean

> 연도별 시계열 데이터를 표시하는 시계열 레이어를 등록합니다. [XDECreateTimeSeriesLayer](moduleapi.md)에 URL 컨텍스트(contextRoot) 지정 기능이 추가된 버전입니다.
>
> 엔진 내부에 시계열 레이어를 하나만 유지하며, 재호출 시 기존에 등록된 시계열 레이어는 삭제되고 새 설정으로 교체됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name        | Type   | Description                       |
| ----------- | ------ | ------------------------------------|
| layerName   | string | 시계열 레이어 이름.               |
| url         | string | 시계열 데이터 서비스 URL.         |
| contextRoot | string | 시계열 데이터 서비스 URL 컨텍스트 경로. |
| year        | number | 조회할 연도.                       |
| minLevel    | number | 레이어 타일 최소 레벨.             |
| maxLevel    | number | 레이어 타일 최대 레벨.             |

-   Return
    -   true: 등록 성공.
    -   false: 등록 실패(지형이 초기화되지 않은 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDECreateTimeSeriesLayerEX("timeseries_layer", "server.url", "/XDServer", 2020, 0, 15);
```

{% endtab %}
{% endtabs %}

### getRenderSpec(constant) → number

> 지정한 OpenGL/WebGL 파라미터 상수의 최대값을 조회합니다. 클라이언트(GPU/드라이버) 환경의 렌더링 성능/한계치 확인용입니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                     |
| -------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| constant | number | <p>조회할 OpenGL/WebGL 상수 값.<br>0x8DFC(GL_MAX_VARYING_VECTORS): 가변(varying) 벡터 최대 개수.<br>0x8DFD(GL_MAX_FRAGMENT_UNIFORM_VECTORS): 프래그먼트 쉐이더 uniform vec4 최대 개수.<br>0x8B4C(GL_MAX_VERTEX_TEXTURE_IMAGE_UNITS): 버텍스 쉐이더가 접근 가능한 텍스처 유닛 최대 개수.<br>0x8DFB(GL_MAX_VERTEX_UNIFORM_VECTORS): 버텍스 쉐이더 uniform vec4 최대 개수.<br>0x8869(GL_MAX_VERTEX_ATTRIBS): 정점 속성(attribute) 최대 개수.</p> |

-   Return
    -   number: 해당 상수의 값.
    -   0: 지원하지 않는 상수를 전달한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var maxVertexAttribs = Module.getRenderSpec(0x8869);
```

{% endtab %}
{% endtabs %}

### XDESetPlanetTransparecny(alpha)

> 지구본 지형(터레인) 전체의 투명도를 설정합니다.
>
> 사용자가 입력한 영역만 투명하게 만드는 "터파기"(XDEAddTransparecny 등) 기능과는 별개로, 지형 전체를 대상으로 하는 투명도입니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description                                                                          |
| ----- | ------ | ---------------------------------------------------------------------------------------|
| alpha | number | 지형 투명도(0.0~1.0). 기본값 1.0(불투명). 0.9 미만으로 설정 시 지형 스커트(skirt) 렌더링이 생략됩니다. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESetPlanetTransparecny(0.5);
```

{% endtab %}
{% endtabs %}

### XDEMashupFile(mashtype, fileurl, layerType, keyf, porj)

> 서버로부터 파일을 비동기로 요청하여, 형식(mashtype)에 맞는 방식으로 지도에 반영(레이어 생성, 바람길/수심/지진파 데이터 등록 등)합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description                                                                                                                                                                                                                                                     |
| --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mashtype  | number | <p>파일 처리 방식을 구분하는 형식 값.<br>10 미만: 기타 파일(0: KML, 3: TIFF 등), layerType으로 레이어 생성.<br>10~19: SHP 파일(11: 지구본 결합, 12: 통계(높이 돌출) 표현 - [XDESHPStatsElement](moduleapi.md) 참고), keyf(DBF 키 필드)/porj 사용.<br>20~22: 바람길(Flow) 데이터.<br>30~35: 수심(Water Depth) 데이터.<br>40~41: 지진파(Earthquake) 데이터.</p> |
| fileurl   | string | 요청할 파일 URL.                                                                                                                                                                                                                                                |
| layerType | number | 생성할 레이어 타입(기타 파일 처리 시 사용).                                                                                                                                                                                                                     |
| keyf      | number | SHP(DBF) 키 필드 인덱스(SHP 파일 처리 시 사용).                                                                                                                                                                                                                 |
| porj      | number | 좌표계(투영법) 구분 값.                                                                                                                                                                                                                                         |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDEMashupFile(0, "server.url/data.kml", 0, 0, 0);
```

{% endtab %}
{% endtabs %}

### createTyphoon(id) → [JSTyphoon](../object/jstyphoon.md)

> 태풍 객체를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSTyphoon](../object/jstyphoon.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var typhoon = Module.createTyphoon("typhoon01");
```

{% endtab %}
{% endtabs %}

### getPylonManager() → [JSPylonManager](../manager/jspylonmanager.md)

> 송전탑(철탑)/전선(Wire) 등 전력 설비 생성 및 관리 기능을 제어하는 [JSPylonManager](../manager/jspylonmanager.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSPylonManager](../manager/jspylonmanager.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var pylonManager = Module.getPylonManager();
```

{% endtab %}
{% endtabs %}

### getFlow() → [JSFlow](../object/jsflow.md)

> 지도 내 바람 흐름(Flow) 객체 생성 및 설정 기능을 제어하는 [JSFlow](../object/jsflow.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSFlow](../object/jsflow.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var flow = Module.getFlow();
```

{% endtab %}
{% endtabs %}

### getEarthquake() → [JSEarthquake](../analysis/jsearthquake.md)

> 지도 내 지진파 분석 기능을 제어하는 [JSEarthquake](../analysis/jsearthquake.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSEarthquake](../analysis/jsearthquake.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var earthquake = Module.getEarthquake();
```

{% endtab %}
{% endtabs %}

### getFlood() → [JSFlood](../analysis/jsflood.md)

> 지도 내 물판(침수) 기능을 제어하는 [JSFlood](../analysis/jsflood.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSFlood](../analysis/jsflood.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var flood = Module.getFlood();
```

{% endtab %}
{% endtabs %}

### createSolarPanel(id) → [JSSolarPanel](../object/jssolarpanel.md)

> 태양광 패널 3차원 객체를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSSolarPanel](../object/jssolarpanel.md): 생성 성공.
    -   null: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var panel = Module.createSolarPanel("panel01");
```

{% endtab %}
{% endtabs %}

### GetSolarManager() → [JSSolarManager](../manager/jssolarmanager.md)

> 태양광 패널 배치, 설정, 분석 기능을 제어하는 [JSSolarManager](../manager/jssolarmanager.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSSolarManager](../manager/jssolarmanager.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var solarManager = Module.GetSolarManager();
```

{% endtab %}
{% endtabs %}

### getTransparency() → [JSTransparency](../analysis/jstransparency.md)

> 지형의 "터파기"(사용자 입력 영역 투명 처리) 분석 기능을 제어하는 [JSTransparency](../analysis/jstransparency.md) 객체를 반환합니다.
>
> 최초 호출 시 내부적으로 객체를 생성/초기화하며, 이후 호출부터는 동일한 인스턴스를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSTransparency](../analysis/jstransparency.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var transparency = Module.getTransparency();
```

{% endtab %}
{% endtabs %}

### XDEAddTransparecny() → number

> 사용자가 마우스로 입력해 둔 영역 좌표를 기반으로 지형을 파내고, 투명 터파기 객체를 생성합니다.
>
> [JSTransparency.create](../analysis/jstransparency.md)와 유사한 기능이나, 좌표를 파라미터로 직접 전달받지 않고 이전에 입력되어 있던 좌표(사용자 입력 점)를 사용하며, 호출 후 해당 입력 좌표는 초기화됩니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   number(0 이상): 생성 성공, 생성된 터파기 인덱스.
    -   -1: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var transIndex = Module.XDEAddTransparecny();
```

{% endtab %}
{% endtabs %}

### XDESetTransparencyDepth(depth)

> 터파기(지형 투명 영역)의 깊이를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description                                             |
| ----- | ------ | ---------------------------------------------------------|
| depth | number | 터파기 깊이(m). 기본값 50.0이며, 0.1 미만 지정 시 0.1로 보정됩니다. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESetTransparencyDepth(5.5);
```

{% endtab %}
{% endtabs %}

### XDESetTransparencyTexture(imageData, imageWidth, imageHeight, bFaceType) → boolean

> 터파기(지형 투명 영역)를 구성하는 면에 적용할 텍스쳐 이미지를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name        | Type    | Description                                                                                                    |
| ----------- | ------- | ------------------------------------------------------------------------------------------------------------------|
| imageData   | object  | Uint8Array 등 바이너리 이미지 데이터.                                                                          |
| imageWidth  | number  | 이미지 너비.                                                                                                    |
| imageHeight | number  | 이미지 높이.                                                                                                    |
| bFaceType   | boolean | <p>true: 터파기 바닥면에 적용.<br>false: 터파기 옆면(측면)에 적용.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESetTransparencyTexture(imageData, canvas.width, canvas.height, true);
```

{% endtab %}
{% endtabs %}

### XDEClearTransparecnyObject()

> 생성된 모든 터파기(지형 투명 영역) 데이터를 초기화(삭제)합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDEClearTransparecnyObject();
```

{% endtab %}
{% endtabs %}

### XDESetAntoMoveTransparency(position, waitFrame) → boolean

> 원형 터파기가 자동으로 이동할 경로(좌표 목록)와 지점 간 이동 속도를 설정합니다.
>
> 입력한 경/위도 좌표에 대해 지형 고도를 자동으로 조회하여 이동 경로에 반영합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type                                   | Description                       |
| --------- | ---------------------------------------- | ------------------------------------|
| position  | [CJSVec2Array](../core/jsvec2array.md) | 터파기 이동 경로(경도, 위도) 좌표 목록. |
| waitFrame | number                                  | 경로 지점 간 이동에 걸리는 대기 프레임 수. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var movePositionList = new Module.JSVec2Array();
movePositionList.push(new Module.JSVector2D(127.03691229708741, 37.509635136930626));
movePositionList.push(new Module.JSVector2D(127.03987097629198, 37.50932526196098));
Module.XDESetAntoMoveTransparency(movePositionList, 5);
```

{% endtab %}
{% endtabs %}

### XDEStartAntoMoveTransparencny() → boolean

> [XDESetAntoMoveTransparency](moduleapi.md)로 설정된 경로를 따라 원형 터파기의 자동 이동을 시작합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   true: 시작 성공.
    -   false: 등록된 이동 경로가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDEStartAntoMoveTransparencny();
```

{% endtab %}
{% endtabs %}

### XDEStopAntoMoveTransparency()

> 진행 중인 터파기 자동 이동을 멈추고, 이동 중 생성된 터파기 벽(wall)을 정리합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.XDEStopAntoMoveTransparency();
```

{% endtab %}
{% endtabs %}

### XDESetTransparencyRadius(radius)

> 원형 터파기의 반지름을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type   | Description                            |
| ------ | ------ | -----------------------------------------|
| radius | number | 터파기 반지름(m). 기본값 500.0.        |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.XDESetTransparencyRadius(500.0);
```

{% endtab %}
{% endtabs %}

### setPipeLineRenderMode(mode)

> 상수관(파이프) 표현 모드를 설정합니다.
>
> mode 값에 따라 파이프 렌더링 방식이 달라지며, mode가 0일 때는 터파기(투명 공간) 오브젝트와 파이프 단면 분석 그래프 레이어도 함께 표시 상태로 전환됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                                                                                        |
| ---- | ------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| mode | number | <p>파이프 렌더 모드.<br>0: 파이프(원통) 형태로 렌더링(터파기 및 파이프 단면 분석 그래프 표시 포함).<br>1: RTT(Render To Texture)로 렌더링.<br>2: 지형 표면에 붙는 라인 형태로 렌더링.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setPipeLineRenderMode(0);
```

{% endtab %}
{% endtabs %}

### setPipeGraphPosition(position)

> 상수관(파이프) 단면 분석 그래프가 표시될 위치를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type                                 | Description                                        |
| -------- | ------------------------------------- | ---------------------------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)  | 파이프 단면 분석 그래프 위치 좌표(경도, 위도, 고도). |

{% endtab %}
{% tab title="Template" %}

```javascript
let vPosition = new Module.JSVector3D(129.1292403, 35.1721634, 100.0);
Module.setPipeGraphPosition(vPosition);
```

{% endtab %}
{% endtabs %}

### getPipeGraphPosition(index) → [JSVector3D](../core/jsvector3d.md)

> 지정한 인덱스의 파이프 단면 분석 그래프 위치를 반환합니다.
>
> 반환값의 경도/위도는 해당 그래프의 실제 위치이지만, 고도(altitude) 값은 그래프 자신의 높이가 아닌 호출 시점의 카메라 고도로 채워집니다. 함수 자체는 카메라를 이동시키지 않으며, 반환된 좌표를 이용해 카메라를 그래프 위치로 이동시키는 것은 호출부의 몫입니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description                              |
| ----- | ------ | ------------------------------------------ |
| index | number | 조회할 파이프 단면 분석 그래프의 인덱스. |

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 그래프의 위치 좌표(경도, 위도) + 호출 시점의 카메라 고도.
    -   [JSVector3D](../core/jsvector3d.md): index가 범위를 벗어난 경우 기본값(0, 0, 0)을 반환.

{% endtab %}
{% tab title="Template" %}

```javascript
let vPosition = Module.getPipeGraphPosition(0);
```

{% endtab %}
{% endtabs %}

### clearPipeGraph()

> 생성된 모든 파이프 단면 분석 그래프를 초기화합니다.
>
> 오브젝트 선택 상태를 해제하고 파이프 단면 분석 그래프 목록을 정리하며, 원본/절단 파이프 레이어(ORIGINAL_PIPE, CUT_PIPE)와 터파기(투명 공간) 상태도 함께 초기화합니다.

{% tabs %}
{% tab title="Template" %}

```javascript
Module.clearPipeGraph();
```

{% endtab %}
{% endtabs %}

### setTerrainImageMode(mode)

> 지형 영상(위성/항공 사진) 타일의 이미지 모드를 설정합니다.
>
> mode 값에 따라 타일 텍스처의 캐시 파일 확장자(jpg/png)와, 별도의 위성 레이어 이름이 지정되지 않았을 때 사용할 기본 영상 레이어 이름(tile_mo_HD/tile_mo2d 계열)이 달라집니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                                        |
| ---- | ------ | ------------------------------------------------------------------------------------- |
| mode | number | <p>지형 영상 이미지 모드.<br>0: 기본 모드(jpg, tile_mo_HD 계열 레이어).<br>0이 아닌 값: 이미지맵 모드(png, tile_mo2d 계열 레이어).</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setTerrainImageMode(1);
```

{% endtab %}
{% endtabs %}

### createTraceTarget(id) → [JSTraceTarget](../object/jstracetarget.md)

> 지도 내 경로(트레이스 타겟) 기능을 관리하기 위한 [JSTraceTarget](../object/jstracetarget.md) 객체를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description     |
| ---- | ------ | ---------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSTraceTarget](../object/jstracetarget.md): 생성 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
let traceTarget = Module.createTraceTarget("newTraceTarget");
```

{% endtab %}
{% endtabs %}

### CreateAntenna(id) → [JSAntenna](../object/jsantenna.md)

> 지도 내 전파 범위 3차원 모델(안테나) [JSAntenna](../object/jsantenna.md) 객체를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description     |
| ---- | ------ | ---------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSAntenna](../object/jsantenna.md): 생성 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
let antenna = Module.CreateAntenna("newAntenna");
```

{% endtab %}
{% endtabs %}

### GetFPS() → number

> 현재 렌더링 프레임률(FPS) 값을 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   number: 현재 FPS 값.
    -   number: 0 (엔진 또는 비디오 드라이버가 아직 초기화되지 않은 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
let fps = Module.GetFPS();
```

{% endtab %}
{% endtabs %}

### createViewFrustum(id) → [JSViewFrustum](../object/jsviewfrustum.md)

> 지도 내 절두체(View Frustum) [JSViewFrustum](../object/jsviewfrustum.md) 객체를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description     |
| ---- | ------ | ---------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSViewFrustum](../object/jsviewfrustum.md): 생성 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
let viewFrustum = Module.createViewFrustum("newViewFrustum");
```

{% endtab %}
{% endtabs %}

### CreateArrow(id) → [JSArrow](../object/jsarrow.md)

> 지도 내 3차원 모델 화살표 [JSArrow](../object/jsarrow.md) 객체를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description     |
| ---- | ------ | ---------------- |
| id   | string | 객체 고유 명칭. |

-   Return
    -   [JSArrow](../object/jsarrow.md): 생성 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
let arrow = Module.CreateArrow("newArrow");
```

{% endtab %}
{% endtabs %}

### getSightAnalysis() → [JSSightAnalysis](../analysis/jssightanalysis.md)

> 시야 분석 기능을 제어하는 [JSSightAnalysis](../analysis/jssightanalysis.md) 객체를 반환합니다.
>
> 최초 호출 시 내부적으로 객체를 생성/초기화하며, 이후 호출부터는 동일한 인스턴스를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSSightAnalysis](../analysis/jssightanalysis.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var sightAnalysis = Module.getSightAnalysis();
```

{% endtab %}
{% endtabs %}

### SetEncodingVWorldDEM(set)

> 브이월드 DEM(지형 고도) 데이터의 난독화 여부를 설정합니다.
>
> [Module.initialize](moduleapi.md#initialize-object-object)의 terrain.dem.encoding 옵션과 동일한 전역 설정값을 제어합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                  |
| ---- | ------- | ----------------------------------------------- |
| set  | boolean | DEM 난독화 사용 여부(true: 사용, false: 미사용). |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetEncodingVWorldDEM(true);
```

{% endtab %}
{% endtabs %}

### SetFlowColor(sr, sg, sb, er, eg, eb)

> 바람장(Flow) 파티클 애니메이션의 그라데이션 색상표를 설정합니다.
>
> 내부적으로 256단계 색상 배열을 새로 생성하며, 인덱스 0~250 구간에 (er, eg, eb) 색상에서 (sr, sg, sb) 색상으로 보간되는 그라데이션이 채워집니다. 즉 실제로는 er/eg/eb가 그라데이션 시작 색상, sr/sg/sb가 끝 색상으로 적용됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                              |
| ---- | ------ | -------------------------------------------- |
| sr   | number | 그라데이션 끝 색상의 Red 값(0~255).      |
| sg   | number | 그라데이션 끝 색상의 Green 값(0~255).    |
| sb   | number | 그라데이션 끝 색상의 Blue 값(0~255).     |
| er   | number | 그라데이션 시작 색상의 Red 값(0~255).    |
| eg   | number | 그라데이션 시작 색상의 Green 값(0~255).  |
| eb   | number | 그라데이션 시작 색상의 Blue 값(0~255).   |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetFlowColor(255, 255, 255, 0, 0, 255);
```

{% endtab %}
{% endtabs %}

### GetFlowData(url, ftype, velocity, height, particleNum)

> 바람장(Flow) 데이터를 URL로부터 비동기로 읽어와 파티클 형태로 가시화합니다.
>
> 파티클 이동 속도, 표시 높이, 개수를 먼저 설정한 뒤 ftype에 지정된 데이터 형식에 맞춰 파일을 요청하며, 파티클 최소/최대 수명(lifetime)은 기본값이 적용됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name        | Type   | Description                                                                                                                       |
| ----------- | ------ | -------------------------------------------------------------------------------------------------------------------------------- |
| url         | string | 바람장 데이터 파일 URL.                                                                                                          |
| ftype       | number | <p>바람장 데이터 형식.<br>0: 해양조사원 그리드 형식(해상도가 낮음).<br>1: 자체 제작 그리드(bin) 형식.<br>2: 재난피해예측 시스템 포맷.</p> |
| velocity    | number | 파티클 이동 속도 배율.                                                                                                          |
| height      | number | 파티클을 표시할 높이(고도).                                                                                                      |
| particleNum | number | 생성할 파티클 개수.                                                                                                              |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.GetFlowData("https://xdworld.vworld.kr/sample/wind.txt", 0, 1.0, 50.0, 1000);
```

{% endtab %}
{% endtabs %}

### SetFlowVisible(bVisible)

> 바람장(Flow) 파티클의 화면 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type    | Description                                              |
| -------- | ------- | ------------------------------------------------------- |
| bVisible | boolean | <p>true: 바람장 파티클 표시.<br>false: 바람장 파티클 숨김.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.SetFlowVisible(true);
```

{% endtab %}
{% endtabs %}

### setLimitObjectMax(count)

> 한 프레임(타일 JSON 데이터 처리 1회)당 생성할 수 있는 오브젝트 개수의 최대치를 설정합니다.
>
> 타일 레이어의 JSON 데이터를 오브젝트로 변환하는 과정에서 누적 생성 개수가 이 값을 넘으면 나머지는 다음 처리 시점으로 넘겨 순차적으로 생성합니다. 기본값은 10입니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description                     |
| ----- | ------ | ---------------------------------- |
| count | number | 프레임당 최대 오브젝트 생성 개수. |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setLimitObjectMax(50);
```

{% endtab %}
{% endtabs %}

### setOverlayMode(set) → boolean

> 지도 화면을 정사영(직교 투영) 방식의 오버레이(Overlay) 텍스처로 렌더링하는 모드를 설정합니다.
>
> true로 설정하면 그림자맵(ShadowMap) 갱신 시 카메라 시점 대신 지표면 수직 방향에서 내려다보는 투영으로 전환되며, 이 모드가 활성화된 동안에는 GLTF, 파이프 단면 분석 그래프 등 일부 부가 3D 객체는 렌더링에서 제외됩니다. false로 설정하면 오버레이 모드를 해제합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                    |
| ---- | ------- | ------------------------------------------------------------------ |
| set  | boolean | <p>true: 오버레이 모드 활성화.<br>false: 오버레이 모드 비활성화.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패(엔진 인스턴스가 초기화되지 않은 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setOverlayMode(true);
```

{% endtab %}
{% endtabs %}

### getRoadManager() → [JSRoadManager](../manager/jsroadmanager.md)

> 도로 객체에서 사용할 텍스처를 등록하기 위한 [JSRoadManager](../manager/jsroadmanager.md) 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   [JSRoadManager](../manager/jsroadmanager.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var roadManager = Module.getRoadManager();
```

{% endtab %}
{% endtabs %}

### getCallback(key) → function

> 지정한 key로 등록되어 있는 콜백 함수를 조회합니다.
>
> "completepoint", "addpoint", "mousechange", "altdistance", "cameramovecomplete", "objectLoadCallback", "loadDataCallback", "3dscomplete", "timeupdate", "gridprograss" 등 엔진 내부에서 각 API가 콜백을 등록할 때 사용하는 key 문자열과 동일한 값을 전달합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                     |
| ---- | ------ | ---------------------------------- |
| key  | string | 조회할 콜백의 식별자 문자열. |

-   Return
    -   function: 해당 key로 등록된 콜백 함수.
    -   undefined: 해당 key로 등록된 콜백이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var callback = Module.getCallback("cameramovecomplete");
```

{% endtab %}
{% endtabs %}

### setGizmoMode(mode)

> 3차원 기즈모(Gizmo, 이동/회전/크기조절 조작 핸들)의 동작 모드를 설정합니다.
>
> mode 값이 -1(NONE)~2(SCALE) 범위를 벗어나면 아무 동작도 하지 않습니다.
>
> 현재 SCALE 모드는 동작하지 않습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description                                                                                         |
| ---- | ------ | -------------------------------------------------------------------------------------------------- |
| mode | number | <p>기즈모 모드.<br>-1: 없음(NONE).<br>0: 이동(TRANSLATE).<br>1: 회전(ROTATE).<br>2: 크기 조절(SCALE).</p> |

{% endtab %}
{% tab title="Template" %}

```javascript
Module.setGizmoMode(0);
```

{% endtab %}
{% endtabs %}

### getGizmoMode() → number

> 현재 설정된 기즈모(Gizmo)의 동작 모드를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   number: 현재 기즈모 모드(-1: 없음, 0: 이동, 1: 회전, 2: 크기 조절).
    -   -1: 엔진 인스턴스가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var mode = Module.getGizmoMode();
```

{% endtab %}
{% endtabs %}

## Type Definitions

### Module.CreateTerrainOptions

| Name  | Type                                                                                | Description          |
| ----- | ----------------------------------------------------------------------------------- | -------------------- |
| dem   | [Module.CreateTerrainOptions.DEM](moduleapi.md#module.createterrainoptions.dem)     | 지형 고도 설정 정보. |
| image | [Module.CreateTerrainOptions.Image](moduleapi.md#module.createterrainoptions.image) | 지형 영상 설정 정보. |

### Module.CreateWorkerOptions

| Name  | Type    | Description           |
| ----- | ------- | --------------------- |
| use   | boolean | web worker 사용 유무. |
| path  | string  | web worker 요청 url.  |
| count | number  | web worker 사용 개수. |

### Module.CreateTerrainOptions.DEM

| Name       | Type    | Description                                                                                              |
| ---------- | ------- | -------------------------------------------------------------------------------------------------------- |
| url        | string  | 지형 고도 요청 url.                                                                                      |
| name       | string  | 지형 고도 레이어 명칭.                                                                                   |
| servername | string  | 요청 서버 명칭.                                                                                          |
| encoding   | boolean | <p>지형 고도 암호화 유무 설정.<br>true: 암호화 된 지형 고도 데이터.<br>false: 일반 지형 고도 데이터.</p> |

### Module.CreateTerrainOptions.Image

| Name       | Type   | Description            |
| ---------- | ------ | ---------------------- |
| url        | string | 지형 영상 요청 url.    |
| name       | string | 지형 영상 레이어 명칭. |
| servername | string | 요청 서버 명칭.        |
