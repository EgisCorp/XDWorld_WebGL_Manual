---
description: 지도 내 객체를 관리하기 위한 API 입니다.
---

# JSLayer

> Module.createLayer () API를 생성합니다.
>
> [createObjectLayer](jslayerlist.md#createobjectlayer-option-jslayer) API로 사용자 레이어를 생성할 수 있습니다.
>
> [createXDServerLayer](jslayerlist.md#createxdserverlayer-option-jslayer) API로 서비스 레이어를 생성할 수 있습니다.

```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.createLayer("Layer Name");
```

## Properties

| Name                    | Type    | Description                                      |
| ----------------------- | ------- | ------------------------------------------------ |
| altitude_offset         | number  | 포인트클라우드, 드론LOD 데이터 실시간 높이 설정. |
| lod_object_alpha        | number  | 서비스 레이어 속성 색상 알파값 설정.             |
| lod_object_detail_ratio | number  | 서비스 레이어 객체 가시화 거리 비율 설정.        |
| serverURL               | string  | 요청 서버 url 반환.                              |
| simple_real3d           | boolean | 건물 객체 심플모드 설정.                         |
| text_character_set      | string  | 레이어 텍스트 문자셋 값 설정.                    |
| tile_load_ratio         | number  | 서비스 레이어 가시화 거리 비율 설정.             |

## Function

### addObject(object, level)

> 사용자 레이어에 객체를 추가합니다.
>
> 사용자 레이어에서 사용할 수 있습니다.
>
> 입력 변수 level은 0으로 고정 사용(현재 미사용)

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type                              | Description        |
| --------- | --------------------------------- | ------------------ |
| object    | [JSObject](../object/jsobject.md) | Add created object |
| ~~level~~ | ~~number~~                        | ~~0 고정 사용~~    |

{% endtab %}

{% tab title="Template" %}

```javascript
let layername = "objectlayer";
let layerList = new Module.JSLayerList(true);
let layer = layerList.createLayer(layername);
layer.addObject(object, 0);
```

{% endtab %}
{% endtabs %}

### clearWMSCache()

> 로드된 WMS 레이어 이미지의 캐시를 지웁니다.

{% tabs %}
{% tab title="Infomation" %}

{% endtab %}

{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
//...(Add WMS layer)...
var layer = layerList.nameAtLayer(“WMSLayer”);
layer.clearWMSCache();
```

{% endtab %}
{% endtabs %}

### getObjectCount() → number

> 레이어의 객체 수를 반환합니다.
>
> 사용자 레이어에서 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   result>0 : 레이어에 포함된 객체 수.
    -   \-1 : 레이어에 포하된 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getObjectKeyList() → string

> 레이어에 포함된 객체의 고유 명칭을 반환합니다.
>
> 사용자 레이어에 포함된 객체는 목록으로 관리하고 모든 목록 객체의 고유 명칭을 반환합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   string : 반환 성공 (구분자 ",").
    -   "" : 반환 실패.
    -   실패 조건
        -   사용자 레이어에 포함된 객체 수가 0인 경우.
        -   서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getType() → number

> 레이어 타입 번호를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   number(0 이상) : 레이어 타입 반환([Layer Type List](../etc/type-list.md#layer-type-list)).
    -   number(-1) : 레이어가 존재하지 않는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
//...(Add WMS layer)...
var layer = layerList.nameAtLayer(“WMSLayer”);
var bVisible = layer.getType();
```

{% endtab %}
{% endtabs %}

### indexAtKey(index) → string

> 사용자 레이어에 포함된 객체 고유 명칭을 반환합니다.
>
> 사용자 레이어에 포함된 객체는 목록으로 관리하고 목록 Index에 해당되는 객체의 고유 명칭을 반환합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| index | number | 인덱스 번호. |

-   Return
    -   string : 반환 성공.
    -   "" : 반환 실패.
    -   실패 조건
        -   입력 변수 index가 레이어에 포함된 객체 목록의 범위를 초과하는 경우(0보다 작거나 목록의 개체 수보다 큰 경우).
        -   레이어의 포함 객체 수가 0인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### indexAtObject(index) → [JSObject](../object/jsobject.md)

> 사용자 레이어에 포함된 객체를 반환합니다.
>
> 사용자 레이어에 포함된 객체는 목록으로 관리하고 목록 Index에 해당되는 객체의 고유 명칭을 반환합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| index | number | 인덱스 번호. |

-   Return
    -   [JSObject](../object/jsobject.md) : 반환 성공.
    -   null : 반환 실패.
    -   실패 조건
        -   입력 변수 index가 레이어에 포함된 객체 목록의 범위를 초과하는 경우(0보다 작거나 목록의 개체 수보다 큰 경우).
        -   레이어의 포함 객체 수가 0인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### keyAtObject(name) → [JSObject](../object/jsobject.md)

> 사용자 레이어에 포함된 객체를 반환합니다.
>
> 사용자 레이어에 포함된 객체는 목록으로 관리하고 객체 고유 명칭과 입력 변수 name 비교 후 만족하는 객체를 반환합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| name | string | 객체 고유 명칭. |

-   Return
    -   [JSObject](../object/jsobject.md) : 반환 성공.
    -   null : 반환 실패.
    -   실패 조건
        -   동일한 고유 명칭 객체가 없는 경우.
        -   입력 변수 name 문자열 데이터가 없는 경우.
        -   레이어의 포함 객체 수가 0인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeAtIndex(index) → boolean

> 사용자 레이어에 포함된 객체를 삭제합니다.
>
> 사용자 레이어에 포함된 객체는 목록으로 관리하고 목록 Index에 해당되는 객체를 삭제합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| index | number | 인덱스 번호. |

-   Return
    -   true : 삭제 성공.
    -   false : 삭제 실패.
    -   실패 조건
        -   입력 변수 index가 레이어에 포함된 객체 목록의 범위를 초과하는 경우(0보다 작거나 목록의 개체 수보다 큰 경우).
        -   레이어의 포함 객체 수가 0인 경우.
        -   서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속).
        -   외부 서버를 통해 가시화 된 데이터인 경우(Ex. WMS, WFS).

{% endtab %}
{% tab title="Template" %}

```javascript
let layername = "objectlayer"
let layerList = new Module.JSLayerList(true);
let layerList.createLayer(layername );

layer.addObject(object, 0);
layer.removeAtIndex(0);
```

{% endtab %}
{% endtabs %}

### removeAtKey(name) → boolean

> 사용자 레이어에 포함된 객체를 삭제합니다.
>
> 사용자 레이어에 포함된 객체는 목록으로 관리하고 객체 고유 명칭과 입력 변수 name 비교 후 만족하는 객체를 삭제합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| name | string | 객체 고유 명칭. |

-   Return
    -   true : 삭제 성공.
    -   false : 삭제 실패.
    -   실패 조건
        -   사용자 레이어에 포함된 객체을 고유 명칭이 입력 변수 name와 동일한 객체가 없는 경우.
        -   입력 변수 name 문자열 데이터가 없는 경우.
        -   레이어의 포함 객체 수가 0인 경우.
        -   서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속).
        -   외부 서버를 통해 가시화 된 데이터인 경우(Ex. WMS, WFS).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeAtObject(object) → boolean

> 사용자 레이어에 포함된 객체를 삭제합니다.
>
> 사용자 레이어에 포함된 객체는 목록으로 관리하고 입력 변수 object와 비교 후 만족하는 객체를 삭제합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type                              | Description |
| ------ | --------------------------------- | ----------- |
| object | [JSObject](../object/jsobject.md) | 객체.       |

-   Return
    -   true : 삭제 성공.
    -   false : 삭제 실패.
    -   실패 조건
        -   사용자 레이어에 포함된 객체와 입력 변수 object와 동일한 객체가 없는 경우.
        -   레이어의 포함 객체 수가 0인 경우.
        -   서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속).
        -   외부 서버를 통해 가시화 된 데이터인 경우(Ex. WMS, WFS).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeAll() → boolean

> 사용자 레이어에 포함된 객체를 삭제합니다.
>
> 사용자 레이어에 포함된 객체 목록의 모두 삭제합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   true: 삭제 성공.
    -   false: 삭제 실패.
    -   실패 조건
        -   레이어의 포함 객체 수가 0인 경우.
        -   서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속).
        -   외부 서버를 통해 가시화 된 데이터인 경우(Ex. WMS, WFS).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setConnectionWFS(url, port, param) → boolean

> WFS 서비스 레이어 연결 정보를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description           |
| ----- | ------ | --------------------- |
| url   | string | 데이터 요청 url.      |
| port  | number | 데이터 요청 port.     |
| param | string | 데이터 요청 파라미터. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   생성한 레이어가 WFS 서비스 레이어가 아닌 경우.
        -   생성한 레이어가 사용자 레이어인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWFSLayer”, 0);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWFS(dataURL, 0, parameter);
```

{% endtab %}
{% endtabs %}

### setConnectionWMS(url, port, param) → boolean

> WMS 레이어 연결 정보를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description           |
| ----- | ------ | --------------------- |
| url   | string | 데이터 요청 url.      |
| port  | number | 데이터 요청 port.     |
| param | string | 데이터 요청 파라미터. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   생성한 레이어가 WMS 레이어가 아닌 경우.
        -   생성한 레이어가 사용자 레이어인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWMSLayer(“newWMSLayer”, 0);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWMS(dataURL, 0, parameter);
```

{% endtab %}
{% endtabs %}

### setFontStyle(fontName, fontSize, fontWeight, color, outColor)

> WFS 폰트 스타일을 설정합니다.
>
> WFS를 통해 POI 생성 시 사용됩니다.

{% tabs %}
{% tab title="Infomation" %}

| Name       | Type                          | Description     |
| ---------- | ----------------------------- | --------------- |
| fontName   | string                        | 폰트 명칭.      |
| fontSize   | number                        | 폰트 크기.      |
| fontWeight | number                        | 폰트 굵기.      |
| color      | [JSColor](../core/jscolor.md) | 폰트 색상.      |
| outColor   | [JSColor](../core/jscolor.md) | 폰트 외각 색상. |

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWFSLayer”, 0);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWFS(dataUrl, 0, parameter);
var clrFont     = new Module.JSColor(255, 255, 255, 255);
var clrOutLine  = new Module.JSColor(255, 0, 0, 0);
layer.setFontStyle(“Arial ”, 20, 10, clrFont, clrOutLine);
```

{% endtab %}
{% endtabs %}

### setLevelWFS(level)

> WFS 서비스 레이어의 데이터 출력 레벨 범위를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description       |
| ----- | ------ | ----------------- |
| level | number | 가시화 최대 레벨. |

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWFSLayer”, 0);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWFS(dataUrl, 0, parameter);
layer.setLevelWFS(10);
```

{% endtab %}
{% endtabs %}

### setLevelWMS(minLevel, maxLevel) → boolean

> WMS 레이어의 데이터 출력 레벨 범위를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type   | Description       |
| -------- | ------ | ----------------- |
| minLevel | number | 가시화 최소 레벨. |
| maxLevel | number | 가시화 최대 레벨. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWMSLayer(“newWMSLayer”);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWMS(dataUrl, 0, parameter);
layer.setLevelWMS(10, 12);
```

{% endtab %}
{% endtabs %}

### setLODRatio(ratio)

> 레이어 가시화 범위를 설정합니다.
>
> 서비스 레이어 LOD 변경으로 객체 가시화 거리를 조절합니다.
>
> 서비스 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description                                 |
| ----- | ------ | ------------------------------------------- |
| ratio | number | 가시화 거리 비율(높을수록 가시화범위 증가). |

-   Sample
    -   function init 참조.
    -   [Sandbox_Parabolic Line](https://sandbox.egiscloud.com/code/main.do?id=object_line_arc)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setProxyRequest(type)

> 서비스 레이어에 대한 프록시 사용을 설정합니다.
>
> 객체 통신 요청에 프록시 통신 사용 유무를 설정합니다.
>
> 낮은 통신 속도를 가집니다.
>
> 서비스 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                              |
| ---- | ------- | -------------------------------------------------------- |
| type | boolean | <p>true: 프록시 서버 사용.<br>false: 기본 서버 사용.</p> |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   사용자 레이어인 경우.
-   Sample
    -   function createLayerWMS 참조.
    -   [Sandbox_WMS](https://sandbox.egiscloud.com/code/main.do?id=layer_wms)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRecoverHsvValue(hue, saturation, value) → boolean

> 서비스 레이어의 HSV 색상 채널을 설정합니다.
>
> 입력 변수 hue(색상), saturation(채도), value(명도) 값으로 객체 HSV 색상 채널을 설정합니다.
>
> 시설물, 드론 LOD 레이어만 적용 합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name       | Type   | Description         |
| ---------- | ------ | ------------------- |
| hue        | number | HSV channel (색상). |
| saturation | number | HSV channel (채도). |
| value      | number | HSV channel (명도). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function setHSV 참조.
    -   [Sandbox_Adjust layer color](https://sandbox.egiscloud.com/code/main.do?id=layer_color_tone)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRequestFeatureCount(count)

> WFS 데이터 요청 단위의 타일 크기를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| count | number | 타일 크기.  |

-   Return
    -   true: 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   서비스 레이어가 아닌 경우.
        -   WFS 서비스 레이어 타입이 아닌 경우.
-   Note
    -   요창 단위가 클수록 큰 타일 범위의 WFS 데이터 요청.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
layer.setRequestFeatureCount(64);
```

{% endtab %}
{% endtabs %}

### setStylesWMS(style)

> WMS 데이터 요청 시 스타일을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| style | string | 스타일.     |

-   Return
    -   true: 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   서비스 레이어가 아닌 경우.
        -   WMS 레이어 타입이 아닌 경우.
-   Note
    -   [스타일 설정 참조](http://dev.vworld.kr/dev/v4dv_wmsguide_s001.do)

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWMSLayer(“newWMSLayer”);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWMS(dataUrl, 0, parameter);
layer.setStylesWMS(“LT_C_UQ111”);
```

{% endtab %}
{% endtabs %}

### setTileAltitudeOffset(offset) → boolean

> 서비스 레이어의 초기 설정 고도값을 설정합니다.
>
> 서비스 레이어에서 객체를 불러올 때 입력 변수 offset을 기준으로 높이 설정합니다.
>
> 포인트 클라우드 레이어만 적용됩니다.
>
> 입력 변수 offset 입력값에 따른 높이 고도 설정은 offset<0(상승), 0(원본 고도), offseta>0하강)

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type   | Description       |
| ------ | ------ | ----------------- |
| offset | number | 초기 고도 설정값. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function init 참조.
    -   [Sandbox_Point Cloud](https://sandbox.egiscloud.com/code/main.do?id=layer_pointcloud_point_size)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTileSizeWMS(size)

> WMS 레이어에서 이미지 요청 크기를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| size | number | 이미지 크기. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   서비스 레이어가 아닌 경우.
        -   WMS 레이어 타입이 아닌 경우.
-   Note
    -   [스타일 설정 참조](http://dev.vworld.kr/dev/v4dv_wmsguide_s001.do)

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWMSLayer(“newWMSLayer”);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWMS(dataUrl, 0, parameter);
layer.setTileSizeWMS(tileSize);
```

{% endtab %}
{% endtabs %}

### setUseRecoverHsv(type) → boolean

> 서비스 레이어 HSV 색상 적용 유무를 설정합니다.
>
> [setRecoverHsvValue](jslayer.md#setRecoverHsvValue) 설정된 색상 채널을 가시화 유무를 설정합니다.
>
> 시설물, 드론 LOD 레이어만 적용 합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                              |
| ---- | ------- | -------------------------------------------------------- |
| type | boolean | <p>true: HSV 색상 채널 시각화.<br>false: 일반 시각화.<p> |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   function setHSV 참조.
    -   [Sandbox_Terrain Color Adjustment](https://sandbox.egiscloud.com/code/main.do?id=terrain_color_tone)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWFSDescField(fieldName) → boolean

> WFS 데이터 중 Description 데이터로 저장할 태그 이름을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description |
| --------- | ------ | ----------- |
| fieldName | string | 태그 명칭.  |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
layer.setWFSPropertyName(“STD_SGGCD,BONBUN,AG_GEOM”);
layer.setWFSDescField(“STD_SGGCD”);

"Received WFS Data"
<gml:featureMember>
<LT_P_BONBUN gml:id="LT_P_BONBUN.253000">
//...omitted...
<STD_SGGCD>26500</STD_SGGCD>
<BONBUN>708</BONBUN>
<AG_GEOM>
//...omitted...
</gml:featureMember>
```

{% endtab %}
{% endtabs %}

### setWFSPointName(fieldName)

> WFS 서비스 레이어에서 요창 받은 XML 포맷에서 POI 가시화 문자열 태그 이름을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type   | Description |
| --------- | ------ | ----------- |
| fieldName | string | 태그 명칭.  |

-   Return
    -   true: 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   서비스 레이어가 아닌 경우.
        -   WFS 레이어 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWFSLayer”, 0);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWFS(dataUrl, 0, parameter);
layer.setWFSPointName(“BONBUN”);

"Received WFS Data"
<gml:featureMember>
<LT_P_BONBUN gml:id="LT_P_BONBUN.253000">
//...omitted...
<STD_SGGCD>26500</STD_SGGCD>
<BONBUN>708</BONBUN>
<AG_GEOM>
//...omitted...
</gml:featureMember>
```

{% endtab %}
{% endtabs %}

### setWFSPropertyName(propertyName)

> WFS에 대한 속성 데이터로 받을 태그 이름을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name         | Type   | Description |
| ------------ | ------ | ----------- |
| propertyName | string | 태그 명칭.  |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   서비스 레이어가 아닌 경우.
        -   WFS 레이어 타입이 아닌 경우.
-   Note
    -   설정된 WFS 태그 목록은 WFS 데이터 요청 파라미터 중 “propertyname” 파라미터에 설정한 내용이 적용된다.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
layer.setWFSPropertyName(“STD_SGGCD,BONBUN,AG_GEOM”);
```

{% endtab %}
{% endtabs %}

### setWFSTextColor(lineColor, fillColor)

> WFS 서비스 레이어 중 POI 객체를 출력하기 위한 텍스쳐의 윤곽선 및 채우기 색상을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name      | Type                          | Description       |
| --------- | ----------------------------- | ----------------- |
| lineColor | [JSColor](../core/jscolor.md) | 문자 윤곽선 색상. |
| fillColor | [JSColor](../core/jscolor.md) | 문자 색상.        |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   서비스 레이어가 아닌 경우.
        -   WFS 레이어 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
var lineColor = new Module.JSColor(255, 255, 255, 255);
var fillColor = new Module.JSColor(255, 0, 0, 0);
layer.setWFSTextColor(lineColor , fillColor);
```

{% endtab %}
{% endtabs %}

### setWMSProvider(option) → string

> WMS 서비스 레이어를 생성합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name   | Type                                | Description    |
| ------ | ----------------------------------- | -------------- |
| option | [WMSOptions](jslayer.md#wmsoptions) | WMS 생성 정보. |

-   Return
    -   success : 생성 성공.
    -   string : 생성 실패 (실패 오류 메시지 반환).
-   Sample
    -   function createLayerWMS 참조.
    -   [Sandbox_WMS](https://sandbox.egiscloud.com/code/main.do?id=layer_wms)

{% endtab %}
{% tab title="Template" %}

```javascript
let slopeoption = {
	url: strUrl,
	layer: strLayer,
	minimumlevel: 0,
	maximumlevel: 20,
	tilesize: 256,
	crs: "EPSG:5174",
	parameters: {
		version: "1.1.0",
		SERVICE=WMS,
		REQUEST=GetMap,
		FORMAT=image/png,
		VERSION=1.1.0,
		TRANSPARENT=TRUE,
		enablePickFeatures: true,
	}
};
```

{% endtab %}
{% endtabs %}

### setWMSTransparent(transparent)

> WMS 서비스 레이어의 투명 유무를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name        | Type    | Description                                         |
| ----------- | ------- | --------------------------------------------------- |
| transparent | boolean | <p>true: 반투명 가시화.<br>false: 불투명 가시화</p> |

-   Note
    -   true로 설정한 경우 지형 이미지가 함께 보이는 반투명 상태로 출력되며, False로 설정한 경우 지형 이미지가 보이지 않는 불투명 상태로 출력된다.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
//...
var layer = layerList.nameAtLayer(“WMSLayer”);
layer.setWMSTransparent(true);
```

{% endtab %}
{% endtabs %}

### setWMSVersion(version)

> WMS 서비스 레이어 이밎 요청 버전을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name    | Type   | Description |
| ------- | ------ | ----------- |
| version | string | 버전 정보.  |

-   Return
    -   true : 설정 성공.
        -   false : 설정 실패.
    -   실패 조건
        -   서비스 레이어가 아닌 경우.
        -   WMS 레이어 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
//...(Add WMS layer)...
var layer = layerList.nameAtLayer(“WMSLayer”);
layer.setWMSVersion(“1.1.0”);
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getAlpha(), setAlpha(alpha) → number

> 서비스 건물 레이어에 존재하는 객체 투명도 설정합니다.
>
> 서비스 건물 레이어 심플 모드 객체 투명도 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| alpha | number | 투명도.     |

-   실패 조건
    -   사용자 레이어인 경우.
    -   시설물 이외 서비스 레이어인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getBBoxOrder(), setBBoxOrder(type) → boolean

> WMS 서비스 레이어 옵션 설정을 설정합니다.
>
> geoserver로 요청하는 좌표 정보 옵션을 설정합니다.
>
> 입력 변수값(type)에 따른 요청 파라미터 변경가 변경됩니다 (true(BBOX=minx,miny,maxx,maxy), false(BBOX=minY,minX,maxY,maxX).maxX)).
>
> WMS 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description |
| ---- | ------- | ----------- |
| type | boolean | 좌표 옵션.  |

-   Sample
    -   function createLayerWMS 참조.
    -   [Sandbox_WMS](https://sandbox.egiscloud.com/code/main.do?id=layer_wms)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getEditable(), setEditable(edit) → boolean

> 레이어를 편집 레이어로 설정합니다.
>
> 엔진 내부에서 생성되는 객체를 관리하는 레이어 입니다.
>
> 편집레이어 변경 시 기존 편집레이어는 사용자 레이어로 변경됩니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                  |
| ---- | ------- | ------------------------------------------------------------ |
| edit | boolean | <p>true: 편집 레이어 설정.<br>false: 일반 레이어로 설정.</p> |

-   실패조건
    -   서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속)
-   Sample
    -   function initSamplePage 참조.
    -   [Sandbox_Shape Creation](https://sandbox.egiscloud.com/code/main.do?id=object_figure)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getMinDistance(), setMinDistance(distance) → number

> 사용자 레이어 가시 거리를 설정합니다.
>
> 사용자 레이어 최소 가시 거리를 설정합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type   | Description                   |
| -------- | ------ | ----------------------------- |
| distance | number | 최소 가시 거리 (meters 단위). |

-   실패조건
    -   최소 가시거리가 최대 가시거리보다 큰 경우.
    -   서비스 레이어인 경우.
-   Sample
    -   function showGrid 참조.
    -   [Sandbox_Grid (2D)](https://sandbox.egiscloud.com/code/main.do?id=object_grid_2d)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getMaxDistance(), setMaxDistance(distance) → number

> 사용자 레이어 가시 거리를 설정합니다.
>
> 사용자 레이어 최대 가시 거리를 설정합니다.
>
> 사용자 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type   | Description                   |
| -------- | ------ | ----------------------------- |
| distance | number | 최대 가시 거리 (meters 단위). |

-   실패조건
    -   최대 가시거리가 최소 가시거리보다 작은 경우.
    -   서비스 레이어인 경우.
-   Sample
    -   function showGrid 참조.
    -   [Sandbox_Grid (2D)](https://sandbox.egiscloud.com/code/main.do?id=object_grid_2d)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getMaxLevel(), setMaxLevel(level) → number

> 서비스 레이어 가시 레벨을 설정합니다.
>
> 서비스 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description     |
| ----- | ------ | --------------- |
| level | number | 최대 가시 레벨. |

-   실패조건
    -   사용자 레이어인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getName(), setName(name) → string

> 레이어 명칭을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| name | string | 레이어 명칭. |

{% endtab %}

{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
//...(Add WMS layer)...
var layer = layerList.nameAtLayer(“WMSLayer”);
layer.setName(“WMSLayer2”);
```

{% endtab %}
{% endtabs %}

### getObjectHorizontal(), setObjectHorizontal(horizontal) → number

> 레이어에 종속된 박스 크기를 설정합니다.
>
> 시계월 애니메이션에서 가시화 되는 박스 크기를 실시간으로 설정합니다.
>
> 박스 객체의 가로 크기를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name       | Type   | Description     |
| ---------- | ------ | --------------- |
| horizontal | number | 객체 가로 크기. |

-   실패조건
    -   0 보다 작은 값이 입력 된 경우.
    -   [createTimeSeriesObject()](jstimeseriesobject.md#JSTimeSeriesObject) API로 객체 생성이 안된 경우.
-   Sample
    -   function JsonLoad 참조.
    -   [Sandbox_Time Series Bar](https://sandbox.egiscloud.com/code/main.do?id=effect_time_bar)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getObjectVertical(), setObjectVertical(vertical) → number

> 레이어에 종속된 박스 크기를 설정합니다.
>
> 시계월 애니메이션에서 가시화 되는 박스 크기를 실시간으로 설정합니다.
>
> 박스 객체의 세로 크기를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name     | Type   | Description     |
| -------- | ------ | --------------- |
| vertical | number | 객체 세로 크기. |

-   실패조건
    -   0 보다 작은 값이 입력 된 경우.
    -   [createTimeSeriesObject()](jstimeseriesobject.md#JSTimeSeriesObject) API로 객체 생성이 안된 경우.
-   Sample
    -   function JsonLoad 참조.
    -   [Sandbox_Time Series Bar](https://sandbox.egiscloud.com/code/main.do?id=effect_time_bar)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getSelectable(), setSelectable(type) → boolean

> 레이어에 포함된 객체에 대한 선택 유무를 설정합니다.
>
> 레이어에 대한 객체 선택 이벤트를 설정합니다.
>
> 사용자 및 서비스 레이어 모두에서 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                      |
| ---- | ------- | ---------------------------------------------------------------- |
| type | boolean | <p>true: 선택 이벤트 활성화.<br>false: 선택 이벤트 비활성화.</p> |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTimeSeriesCount(), setTimeSeriesCount(step) → number

> 레이어에 포함된 시계월 애니메이션 단계를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description      |
| ---- | ------ | ---------------- |
| step | number | 애니메이션 단계. |

-   실패조건
    -   입력 변수값(step)이 설정된 최소 step보다 작은값이 입력된 경우.
    -   입력 변수값(step)이 설정된 최대 step보다 큰값이 입력된 경우.
    -   [createTimeSeriesObject()](jstimeseriesobject.md#JSTimeSeriesObject) API로 객체 생성이 안된 경우.
-   Sample
    -   function JsonLoad 참조.
    -   [Sandbox_Time Series Bar](https://sandbox.egiscloud.com/code/main.do?id=effect_time_bar)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTimeSpeed(), setTimeSpeed(speed) → number

> 레이어에 포함된 시계월 애니메이션 step 변경 시 객체 변환 속도를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| speed | number | 변환 속도.  |

-   실패조건
    -   [createTimeSeriesObject()](jstimeseriesobject.md#JSTimeSeriesObject) API로 객체 생성이 안된 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getViewLimit(), setViewLimit(tilt) → number

> 서비스 레이어 tilt 시 서비스 레이어에 포함된 객체 가시화 제한을 설정합니다.
>
> 입력 변수값(tilt)이 카메라 tilt 보다 작으면 투명 상태로 설정합니다.
>
> csv, billboard, poi, 시설물 객체에 대해 제한을 설정합니다.
>
> 서비스 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type   | Description              |
| ---- | ------ | ------------------------ |
| tilt | number | 제한 tilt(degrees 단위). |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(type) → boolean

> 레이어에 포함된 객체에 대한 가시 유무를 설정합니다.
>
> 레이어가 투명/불투명 정보를 반환합니다.
>
> 사용자 및 서비스 레이어 모두에서 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}

| Name | Type    | Description                                                                |
| ---- | ------- | -------------------------------------------------------------------------- |
| type | boolean | <p>true: 레이어 포함 객체 가시화.<br>false: 레이어 포함 객체 불가시화.</p> |

-   Sample
    -   function JsonLoad 참조.
    -   [Sandbox_Time Series Bar](https://sandbox.egiscloud.com/code/main.do?id=effect_time_bar)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ~~getWMSRequestParam(), setWMSRequestParam(parameter) → string~~

{% tabs %}
{% tab title="Infomation" %}

-   대체 API: setWMSProvider

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ~~getWMSVersion(), setWMSVersion(version) → string~~

{% tabs %}
{% tab title="Infomation" %}

-   대체 API: setWMSProvider

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ~~getUnion(), setUnion(union) → boolean~~

{% tabs %}
{% tab title="Infomation" %}

-   사용되지 않음

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Type Definitions

#### WMSOptions

> WMS 레이어의 기본 생성 옵션.

| Name         | Type                                                      | Attributes | Default   | Description                  |
| ------------ | --------------------------------------------------------- | ---------- | --------- | ---------------------------- |
| url          | string                                                    |            |           | GeoServer 요청 url.          |
| layer        | string                                                    |            |           | GeoServer 요청 레이어 명칭.  |
| minimumLevel | number                                                    | optional   | 0         | WMS 가시화 최소 레벨.        |
| maximumLevel | number                                                    | optional   | 15        | WMS 가시화 최대 레벨.        |
| tileSize     | number                                                    | optional   | 256       | WMS 요청 이미지 크기.        |
| crs          | string                                                    | optional   | EPSG:4326 | WMS 등록 레이어 원본 좌표계. |
| parameters   | [WMSOptions.SubOptions](jslayer.md#wmsoptions.suboptions) | optional   |           | WMS 요청 스타일, 속성 정보.. |

#### WMSOptions.SubOptions

> WMS 레이어 추가 생성 옵션.
>
> 추가 옵션은 parameters 구성 시 키, 벨류로 추가하며 자동으로 요청 url 구성에 포함.
>
> ex) style 옵션 등.

| Name        | Type   | Attributes | Default   | Description                            |
| ----------- | ------ | ---------- | --------- | -------------------------------------- |
| version     | string | optional   | 1.1.0     | GeoServer 버전.                        |
| service     | string | optional   | WMS       | GeoServer 요청 타입.                   |
| request     | string | optional   | GetMap    | GeoServer 요청 지도 타입.              |
| format      | string | optional   | image/png | GeoServer 요청 이미지 타입.            |
| transparent | string | optional   | TRUE      | Transparency 이미지 요청 시 투명 옵션. |
