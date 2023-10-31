---
description: 지도 내 객체를 관리하는 API.
---

# JSLayer

> Module createLayer API로 생성할 수 있습니다.
>
> Module [createObjectLayer](jslayerlist.md#createobjectlayer-option-jslayer) API로 사용자 레이어를 생성할 수 있습니다.
>
> Module [createXDServerLayer](jslayerlist.md#createxdserverlayer-option-jslayer) API로 서비스 레이어를 생성할 수 있습니다.

```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.createLayer("레이어 명칭");
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

> 해당 사용자 레이어 객체 추가.
>
> 사용자 레이어만 가능.
>
> level 0으로 고정적으로 사용.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| --------- | -------- | ----------- |
| object | JSObject | 생성 된 객체 추가 |
| ~~level~~ | number | 0 값으로 사용 |
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

> 로드 된 WMS 레이어 이미지 캐시를 비움.

{% tabs %}
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
..(WMS 레이어 추가)..
var layer = layerList.nameAtLayer(“WMSLayer”);
layer.clearWMSCache();
```

{% endtab %}
{% endtabs %}

### getType() → number

> 레이어의 타입 값 반환.

{% tabs %}
{% tab title="Infomation" %}
-  Return
  -  number(0 이상) : 레이어 타입(E_LAYER_TYPE) 반환.
  -  number(-1) : 레이어 오브젝트가 존재하지 않는 경우.
{% endtab %}
{% tab title="Template" %}
```javascript
var layerList = new Module.JSLayerList(false);
//..(WMS 레이어 추가)..
var layer = layerList.nameAtLayer(“WMSLayer”);
var bVisible = layer.getType();
```
{% endtab %}
{% endtabs %}

### indexAtKey(index) → string

> 해당 사용자 레이어에서 객체 ID 반환.
>
> 해당 사용자 레이어 객체는 리스트로 관리하며 리스트 Index 해당되는 객체 ID 반환.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ----- | ------ | ------------ |
| index | number | 목표 객체 Index. |

-   Return
    -   string : Index 해당 객체 ID 반환 성공.
    -   "" : Index 해당 객체 ID 반환 실패.
-   객체 ID 반환 실패 조건.
    -   Index 객체 리스트 범위를 초과한 경우 (0보다 작거나 객체 리스트 수 보다 큰 경우)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### indexAtObject(index) → JSObject

> 해당 사용자 레이어에서 객체 반환.
>
> 해당 사용자 레이어 객체는 리스트로 관리하며 리스트 index 해당되는 객체 반환.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ----- | ------ | ----------- |
| index | number | 등록 객체 인덱스. |

-   Return
    -   JSObject : Index 해당 객체 반환 성공.
    -   null : Index 해당 객체 반환 실패.
-   객체 반환 실패 조건.
    -   Index가 객체 리스트 범위를 초과한 경우 (0보다 작거나 객체 리스트 수 보다 큰 경우).
    -   해당 레이어 객체 개수가 0인 경우.
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### keyAtObject(name) → JSObject

> 해당 사용자 레이어에서 객체 반환.
>
> 해당 사용자 레이어 객체는 리스트로 관리하며 순차적으로 객체 ID와 objectid 비교 후 조건에 만족하는 객체 반환.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------ | ----------- |
| name | string | 등록 객체 명칭. |

-   Return
    -   JSObject : 동일 명칭 객체 반환 성공.
    -   null : 동일 명칭 객체 반환 실패.
-   객체 반환 실패 조건.
    -   동일 명칭 객체가 없는 경우.
    -   name 문자 데이터가 없는 경우.
    -   해당 레이어 객체 개수가 0인 경우.
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeAtIndex(index) → boolean

> 해당 사용자 레이어에서 객체 삭제.
>
> 해당 사용자 레이어 객체는 리스트로 관리하며 리스트 Index 해당되는 객체 삭제.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ----- | ------ | ----------- |
| index | number | 등록 객체 인덱스. |

-   Return
    -   true : 객체 삭제 성공.
    -   false : 객체 삭제 실패.
-   삭제 실패 조건
    -   index가 객체 리스트 범위를 초과한 경우 (0보다 작거나 객체 리스트 수 보다 큰 경우).
    -   해당 레이어 객체 수가 0인 경우.
    -   서비스 레이어 경우(서비스 레이어는 tile 기반으로 객체는 tile에 종속).
    -   외부 서버를 통해 로드된 데이터인 경우(Ex. WMS, WFS).
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

> 해당 사용자 레이어에서 객체 삭제.
>
> 해당 사용자 레이어 객체는 리스트로 관리하며 순차적으로 객체 명칭과 name 비교 후 조건에 만족하는 객체 삭제.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------ | ----------- |
| name | string | 등록 객체 명칭. |

-   Return
    -   true : 객체 삭제 성공.
    -   false : 객체 삭제 실패.
-   삭제 실패 조건
    -   objectid가 동일한 객체가 없을 경우.
    -   name 문자 데이터가 없는 경우.
    -   해당 레이어 객체 수가 0인 경우.
    -   서비스 레이어 경우(서비스 레이어는 tile 기반으로 객체는 tile에 종속).
    -   외부 서버를 통해 로드된 데이터인 경우(Ex. WMS, WFS).
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeAtObject(object) → boolean

> 해당 사용자 레이어에서 객체 삭제.
>
> 해당 사용자 레이어 객체는 리스트로 관리하며 순차적으로 객체와 object 비교 후 조건에 만족하는 객체 삭제.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | -------- | ----------- |
| object | JSObject | 등록 객체. |

-   Return
    -   true : 객체 삭제 성공.
    -   false : 객체 삭제 실패.
-   삭제 실패 조건
    -   object와 동일한 객체가 없을 경우.
    -   해당 레이어 객체 수가 0인 경우.
    -   서비스 레이어 경우(서비스 레이어는 tile 기반으로 객체는 tile에 종속).
    -   외부 서버를 통해 로드된 데이터인 경우(Ex. WMS, WFS).
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### removeAll() → boolean

> 해당 사용자 레이어에서 객체 삭제.
>
> 해당 레이어 객체 리스트 전체 삭제.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   true : 객체 삭제 성공.
    -   false : 객체 삭제 실패.
-   삭제 실패 조건
    -   해당 레이어 객체 수가 0인 경우.
    -   서비스 레이어 인 경우(서비스 레이어에서 객체는 tile에 종속).
    -   외부 서버를 통해 로드된 데이터인 경우(Ex. WMS, WFS).
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getObjectCount() → number

> 해당 레이어 객체 리스트 갯수 반환.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   \-1 : 해당 레이어에 객체가 존재 하지 않는 경우.
    -   result>0 : 해당 레이어 객체 갯수.
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getObjectKeyList() → string

> 해당 레이어에서 객체 명칭 반환.
>
> 해당 사용자 레이어 객체는 리스트로 관리하며 모든 리스트 객체 명칭 반환
>
> 사용자 레이어에서 사용 가능

{% tabs %}
{% tab title="Infomation" %}

-   Return
    -   string : 객체 명칭 반환 성공(구분자 ",").
    -   "" : 객체 명칭 반환 실패.
-   ID 반환 실패 조건.
    -   해당 레이어 객체 수가 0인 경우.
    -   서비스 레이어 인 경우(서비스 레이어에서 객체는 tile에 종속).
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setConnectionWFS(url, port, param) → boolean

> WFS 레이어 연결 정보를 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| url | string | 데이터 요청 url. |
| port | number | 데이터 요청 Port. |
| param | string | 데이터 요청 파라미터. |

-   Return
    -   true : 설정에 성공할 경우.
    -   false : 해당 레이어가 존재하지 않거나, 해당 레이어 타입이 타일 레이어 타입이 아닌 경우.
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWFSLayer”, 0);
var dataURL = “http://...(데이터 요청 URL)...”;
var parameter= “...(데이터 요청 파라미터)...”;
layer.setConnectionWFS(dataURL, 0, parameter);
```
{% endtab %}
{% endtabs %}

### setConnectionWMS(url, port, param) → boolean

> WMS 레이어 연결 정보를 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| url | string | 데이터 요청 url. |
| port | number | 데이터 요청 Port. |
| param | string | 데이터 요청 파라미터. |

-   Return
    -   true : 설정에 성공할 경우.
    -   false : 해당 레이어가 존재하지 않거나, 해당 레이어 타입이 타일 레이어 타입이 아닌 경우.
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWMSLayer(“newWMSLayer”, 0);
var dataURL = “http://...(데이터 요청 URL)...”;
var parameter= “...(데이터 요청 파라미터)...”;
layer.setConnectionWMS(dataURL, 0, parameter);
```
{% endtab %}
{% endtabs %}

### setFontStyle(fontName, fontSize, fontWeight, color, outColor)

> WFS 글꼴 스타일을 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| fontName | string | 글꼴 명칭. |
| fontSize | number | 글꼴 크기. |
| fontWeight | number | 글꼴 두께. |
| color | [JSColor](../core/jscolor.md) | 글꼴 색상. |
| outColor | [JSColor](../core/jscolor.md) | 글꼴 외곽 색상. |
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWFSLayer”, 0);
var dataURL = “http://...(데이터 요청 URL)...”;  
var parameter= “...(데이터 요청 파라미터)...”;
layer.setConnectionWFS(dataUrl, 0, parameter);
var clrFont     = new Module.JSColor(255, 255, 255, 255);
var clrOutLine  = new Module.JSColor(255, 0, 0, 0);
layer.setFontStyle(“굴림”, 20, 10, clrFont, clrOutLine); 
```
{% endtab %}
{% endtabs %}

### setLevelWFS(level)

> WFS 레이어의 데이터 출력 레벨 범위를 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| level | number | 데이터 출력 최대 레벨. |
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWFSLayer”, 0);
var dataURL = “http://...(데이터 요청 URL)...”;
var parameter= “...(데이터 요청 파라미터)...”;
layer.setConnectionWFS(dataUrl, 0, parameter);
layer.setLevelWFS(10);
```
{% endtab %}
{% endtabs %}

### setLevelWMS(minLevel, maxLevel) → boolean

> WMS 레이어의 데이터 출력 레벨 범위를 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| minLevel | number | 데이터 출력 최소 레벨. |
| maxLevel | number | 데이터 출력 최대 레벨. |

- Return
  - true : 설정에 성공할 경우.
  - 다음의 경우 API는 false를 반환.
    - 해당 레이어가 존재하지 않는 경우.
    - 해당 레이어 타입이 타일 레이어 타입이 아닌 경우.
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWMSLayer(“newWMSLayer”);
var dataURL = “http://...(데이터 요청 URL)...”;
var parameter= “...(데이터 요청 파라미터)...”;
layer.setConnectionWMS(dataUrl, 0, parameter);
layer.setLevelWMS(10, 12);
```
{% endtab %}
{% endtabs %}

### setLODRatio(ratio)

> 해당 레이어 가시화 범위 설정
>
> 해당 서비스 레이어 LOD 변경으로 객체 가시화 조절.
>
> 서비스 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ----- | ------ | -------------------------- |
| ratio | number | LOD 단계 설정(높을수록 가시화 범위 증가). |

-   Sample
    -   function init 참조.
    -   [샌드박스\_포물선 라인](http://sandbox.dtwincloud.com/code/main.do?id=object_line_arc)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setName(layerName)

> 레이어의 이름을 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| layerName | string | 설정하고자 하는 레이어 이름. |
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
//..(WMS 레이어 추가)..
var layer = layerList.nameAtLayer(“WMSLayer”);
layer.setName(“WMSLayer2”);
```
{% endtab %}
{% endtabs %}

### setProxyRequest(type)

> 레이어 프록시 사용 설정.
>
> 객체 통신 요청 시 프록시 사용 유무를 설정.
>
> 서비스 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------------- |
| type | boolean | <p>true인 경우 프록시 서버 설정.<br>false인 경우 기본 요청 설정.</p> |

-   Return
    -   true : 프록시 설정 성공.
    -   false : 프록시 설정 실패.
-   프록시 설정 실패 조건.
    -   사용자 레이어 인 경우
-   Sample
    -   function createLayerWMS 참조.
    -   [샌드박스\_WMS](http://sandbox.dtwincloud.com/code/main.do?id=layer_wms)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRecoverHsvValue(hue, saturation, value) → boolean

> 해당 서비스 레이어 HSV 색상 채널 설정.
>
> 색상(hue), 채도(saturation), 명도(value) 입력 값으로 객체 HSV 채널 가시화 설정.
>
> 건물, 드론 LOD 레이어만 적용.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---------- | ------ | ----------- |
| hue | number | HSV 채널(명도). |
| saturation | number | HSV 채널(채도). |
| value | number | HSV 채널(명도). |

-   Return
    -   true : HSV 채널 설정 성공.
    -   false : HSV 채널 설정 실패.
-   Sample
    -   function setHSV 참조.
    -   [샌드박스\_지형 색감 조정](http://sandbox.dtwincloud.com/code/main.do?id=terrain_color_tone)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRequestFeatureCount(count)

> WFS 데이터 요청 단위의 타일 크기를 지정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| count | number | 요청 단위 타일 크기. |

- Return
  - true : 설정에 성공한 경우.
  - 다음의 경우 false 반환.
    - 해당 레이어 타입이 타일 레이어 타입이 아닌 경우.
    - 해당 레이어 타입이 WFS 레이어 타입이 아닌 경우.
- 참고
  - 요청 단위가 클수록 큰 타일 범위의 WFS 데이터 요청
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
layer.setRequestFeatureCount(64);
```
{% endtab %}
{% endtabs %}

### setStylesWMS(style)

> 요청 하고자 하는 레이어 스타일을 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| style | string | 요청 레이어 스타일. |

- Return
  - true : 설정에 성공한 경우.
  - 다음의 경우 false 반환.
    - 해당 레이어가 존재하지 않는 경우.
    - 해당 레이어 타입이 타일 레이어 타입이 아닌 경우.
- 참고
  - 스타일 설정 참조 : http://dev.vworld.kr/dev/v4dv_wmsguide_s001.do
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWMSLayer(“newWMSLayer”);
var dataURL = “http://...(데이터 요청 URL)...”;
var parameter= “...(데이터 요청 파라미터)...”;
layer.setConnectionWMS(dataUrl, 0, parameter);
layer.setStylesWMS(“LT_C_UQ111”);
```
{% endtab %}
{% endtabs %}

### setTileAltitudeOffset(offset) → boolean

> 해당 서비스 초기 설정 고도값 설정(기본 0)
>
> 객체가 로딩 시 초기 설정된 고도(offset)을 기준으로 높이 설정(가시화 된 객체 높이 변경 안됨).
>
> 포인트 클라우드 레이어만 적용.
>
> offset 입력 값에 따른 높이 고도 설정은 tilt<0(상승), 0(원본 고도), tilt>0(하강).

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | ------ | --------------- |
| offset | number | 포인트 클라우드 고도 설정. |

-   Return
    -   true : 높이 설정 성공.
    -   false : 높이 설정 실패.
-   Sample
    -   function init 참조.
    -   [샌드박스\_포인트 클라우드](http://sandbox.dtwincloud.com/code/main.do?id=layer_pointcloud_point_size)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTileSizeWMS(size)

> WMS 레이어 타일의 픽셀 크기를 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| size | number | 타일 픽셀 크기. |

- Return
  - true : 설정에 성공한 경우.
  - 다음의 경우 false 반환.
    - 해당 레이어가 존재하지 않는 경우.
    - 해당 레이어 타입이 타일 레이어 타입이 아닌 경우.
- 참고
  - 스타일 설정 참조 : http://dev.vworld.kr/dev/v4dv_wmsguide_s001.do
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWMSLayer(“newWMSLayer”);
var dataURL = “http://...(데이터 요청 URL)...”;
var parameter= “...(데이터 요청 파라미터)...”;
layer.setConnectionWMS(dataUrl, 0, parameter);
layer.setTileSizeWMS(tileSize);
```
{% endtab %}
{% endtabs %}

### setUseRecoverHsv(type) → boolean

> 해당 서비스 레이어 색상 표현 설정.
>
> HSV 색상 채널을 적용한 객체 표현 설정.
>
> 건물, 드론 LOD 레이어만 적용.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------------ |
| type | boolean | <p>true인 경우 HSV 채널 가시화.<br>false인 경우 기본 가시화.</p> |

-   Return
    -   true : HSV 채널 가시화 설정 성공.
    -   false : HSV 채널 가시화 설정 실패.
-   Sample
    -   function setHSV 참조.
    -   [샌드박스\_지형 색감 조정](http://sandbox.dtwincloud.com/code/main.do?id=terrain_color_tone)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWFSDescField(fieldName) → boolean

> WFS 데이터 중 Description 데이터로 저장할 태그 이름을 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | ----------------------------------- | ------------- |
| fieldName | string | Description 데이터를 저장할 태그 이름. |

- Return
  - true : 설정에 성공한 경우.
  - 다음의 경우 false 반환.
    - 레이어 타입이 타일 레이어 타입이 아닌 경우.
    - 레이어 타입이 WFS형 타입이 아닌 경우.
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
layer.setWFSPropertyName(“STD_SGGCD,BONBUN,AG_GEOM”);
layer.setWFSDescField(“STD_SGGCD”);

"수신 WFS 데이터"
<gml:featureMember>
<LT_P_BONBUN gml:id="LT_P_BONBUN.253000">
...중략..
<STD_SGGCD>26500</STD_SGGCD>
<BONBUN>708</BONBUN>
<AG_GEOM>
...중략...
</gml:featureMember>
```

{% endtab %}
{% endtabs %}

### setWFSPointName(fieldName)

> WFS 레이어 타일의 픽셀 크기를 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | ----------------------------------- | ------------- |
| fieldName | string | 수신한 xml형 WFS 데이터 내 태그 명칭. |

- Return
  - true : 설정에 성공한 경우.
  - 다음의 경우 false 반환.
    - 해당 레이어가 존재하지 않는 경우.
    - 해당 레이어 타입이 타일 레이어 타입이 아닌 경우.
    - 해당 레이어 타입이 WFS 레이어 타입이 아닌 경우.
{% tab title="Template" %}

```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWFSLayer”, 0);
var dataURL = “http://...(데이터 요청 URL)...”;
var parameter= “...(데이터 요청 파라미터)...”;
layer.setConnectionWFS(dataUrl, 0, parameter);
layer.setWFSPointName(“BONBUN”);

"수신 WFS 데이터"
<gml:featureMember>
<LT_P_BONBUN gml:id="LT_P_BONBUN.253000">
...중략..
<STD_SGGCD>26500</STD_SGGCD>
<BONBUN>708</BONBUN>
<AG_GEOM>
...중략...
</gml:featureMember>
```

{% endtab %}
{% endtabs %}

### setWFSPropertyName(propertyName)

> WFS 속성 데이터로 받을 태그 리스트를 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | ----------------------------------- | ------------- |
| propertyName | string | 속성 데이터 태그 리스트. |

- Return
  - true : 설정에 성공한 경우.
  - 다음의 경우 false 반환.
    - 레이어 타입이 타일 레이어 타입이 아닌 경우.
    - 레이어 타입이 WFS형 타입이 아닌 경우.
- 참고
  -   설정된 WFS 태그 리스트는 WFS 데이터 요청 파라미터 중 “propertyname” 파라미터에 설정한 내용이 적용된다.
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
layer.setWFSPropertyName(“STD_SGGCD,BONBUN,AG_GEOM”);
```

{% endtab %}
{% endtabs %}

### setWFSTextColor(lineColor, fillColor)

> POI WFS 데이터 출력 시 텍스트의 외곽 색상, 채움 색상을 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | ----------------------------------- | ------------- |
| lineColor | [JSColor](../core/jscolor.md) | 텍스트 외곽 색상. |
| fillColor | [JSColor](../core/jscolor.md) | 텍스트 채움 색상. |

- Return
  - true : 설정에 성공한 경우.
  - 다음의 경우 false 반환.
    - 레이어 타입이 타일 레이어 타입이 아닌 경우.
    - 레이어 타입이 WFS형 타입이 아닌 경우.
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

> WMS 레이어 생성
>
> argument 변수로 WMS 서비스 레이어 생성

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | ----------------------------------- | ------------- |
| option | [WMSOptions](jslayer.md#wmsoptions) | WMS 요청 속성 정보. |

-   Return
    -   success : WMS 레이어 생성 성공.
    -   문자열 : WMS 레이어 생성 과정 에러 메시지.
-   Sample
    -   function createLayerWMS 참조.
    -   [샌드박스\_WMS](http://sandbox.dtwincloud.com/code/main.do?id=layer_wms)
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

> POI WFS 데이터 출력 시 텍스트의 외곽 색상, 채움 색상을 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | ----------------------------------- | ------------- |
| transparent | boolean | 레이어 출력 방식.<br>true : 레이어 반투명 출력</br><br>false : 레이어 불투명 출력</br> |
- 참고
  - true로 설정한 경우 지형 이미지가 함께 보이는 반투명 상태로 출력되며, False로 설정한 경우 지형 이미지가 보이지 않는 불투명 상태로 출력된다.
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

> WMS 이미지의 요청 버전을 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ------ | ----------------------------------- | ------------- |
| version | string | 설정하고자 하는 데이터 요청 버전. |

- Return
  - true : 설정에 성공한 경우.
  - 다음의 경우 false 반환.
    - 레이어 객체가 존재하지 않는 경우.
    - 레이어 타입이 타일 레이어 타입이 아닌 경우.
{% tab title="Template" %}

```javascript
var layerList = new Module.JSLayerList(false);
//..(WMS 레이어 추가)..
var layer = layerList.nameAtLayer(“WMSLayer”);
layer.setWMSVersion(“1.1.0”);
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getAlpha(), setAlpha(alpha) → number

> 서비스 건물 레이어에 존재하는 객체 투명도 설정.
>
> 서비스 건물 레이어 심플 모드 객체 투명도 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ----- | ------ | -------------------- |
| alpha | number | 서비스 레이어 속성 색상 알파값 설정 |

-   투명도 설정 실패 조건
    -   유저 레이어 인 경우.
    -   건물 이외 서비스 레이어 인 경우.
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getBBoxOrder(), setBBoxOrder(type) → boolean

> WMS 서비스 레이어 옵션 설정.
>
> 지오 서버로 요청하는 좌표 정보 가시화 옵션 설정.
>
> WMS 레이어에서 사용 가능
>
> type 입력 값에 따른 좌표 정보 true(BBOX=minx,miny,maxx,maxy), false(BBOX=minY,minX,maxY,maxX).

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ----------- |
| type | boolean | 좌표 옵션 설정. |

-   Sample
    -   function createLayerWMS 참조.
    -   [샌드박스\_WMS](http://sandbox.dtwincloud.com/code/main.do?id=layer_wms)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getEditable(), setEditable(edit) → boolean

> 해당 레이어에서 편집 레이어 설정.
>
> 엔진 내부에서 생성되는 객체를 관리하는 레이어.
>
> 사용자 레이어만 가능.
>
> 편집레이어 변경 시 기존 편집레이어는 일반레이어로 변경.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------------- |
| edit | boolean | <p>true인 경우 편집레이어로 설정<br>false인 경우 일반레이어로 설정.</p> |

-   편집 레이어 설정 실패 조건
    -   서비스 레이어 인 경우(서비스 레이어에서 객체는 tile에 종속).
-   Sample
    -   function initSamplePage 참조.
    -   [샌드박스\_도형 생성](http://sandbox.dtwincloud.com/code/main.do?id=object_figure)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getMinDistance(), setMinDistance(distance) → number

> 레이어 가시 범위 설정.
>
> 레이어 최소 가시범위 거리를 설정.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| -------- | ------ | -------------------- |
| distance | number | 레이어 최소 가시범위 거리(m단위). |

-   최소 가시 범위 실패 조건.
    -   최소 가시 범위가 최대 가시 범위보다 큰 경우.
    -   서비스 레이어 일 경우.
-   Sample
    -   function showGrid 참조.
    -   [샌드박스\_그리드(2D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getMaxDistance(), setMaxDistance(distance) → number

> 레이어 가시 범위 설정
>
> 레이어 최대 가시범위 거리를 설정.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| -------- | ------ | -------------------- |
| distance | number | 레이어 최대 가시범위 거리(m단위). |

-   최대 가시 범위 실패 조건.
    -   최대 가시 범위가 최소 가시 범위보다 작은 경우.
    -   서비스 레이어 일 경우.
-   Sample
    -   function showGrid 참조.
    -   [샌드박스\_그리드(2D)](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getMaxLevel(), setMaxLevel(level) → number

> 레이어 가시 레벨 설정.
>
> 레이어 최대 가시 레벨 설정.
>
> 서비스 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ----- | ------ | -------------- |
| level | nomber | 레이어 최대 가시 레벨값. |

-   최대 가시 레벨 실패 조건.
    -   유저 레이어 일 경우.
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getName(), setName(name) → string

> 레이어 명칭 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------ | ----------- |
| name | string | 변경 레이어 명칭. |
{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getObjectHorizontal(), setObjectHorizontal(horizontal) → number

> 레이어 박스 객체 크기 설정.
>
> 시계월 애니메이션 크기 실시간 설정.
>
> 박스 객체 가로 크기 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---------- | ------ | --------------- |
| horizontal | number | 박스 객체 가로 크기 설정. |

-   박스 객체 가로 크기 설정 실패 조건.
    -   0 보다 작은 값이 입력 된 경우.
    -   createTimeSeriesObject() API로 객체 생성이 안된 경우.
-   Sample
    -   function JsonLoad 참조.
    -   [샌드박스\_시계열 Bar](http://sandbox.dtwincloud.com/code/main.do?id=effect_time_bar)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getObjectVertical(), setObjectVertical(vertical) → number

> 레이어 박스 객체 크기 설정.
>
> 시계월 애니메이션 크기 실시간 설정.
>
> 박스 객체 세로 크기 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| -------- | ------ | --------------- |
| vertical | number | 박스 객체 세로 크기 설정. |

-   박스 객체 세로 크기 설정 실패 조건.
    -   0 보다 작은 값이 입력 된 경우.
    -   createTimeSeriesObject() API로 객체 생성이 안된 경우.
-   Sample
    -   function JsonLoad 참조.
    -   [샌드박스\_시계열 Bar](http://sandbox.dtwincloud.com/code/main.do?id=effect_time_bar)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getSelectable(), setSelectable(type) → boolean

> 해당 레이어 선택 설정.
>
> 해당 레이어를 구성하는 객체 선택 이벤트 설정.
>
> 사용자, 서비스 레이어에서 사용 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | -------------------------------------------------- |
| type | boolean | <p>true인 경우 선택 이벤트 동작.<br>false인 경우 선택 이벤트 금지.</p> |
{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTimeSeriesCount(), setTimeSeriesCount(step) → number

> 레이어 박스 객체 애니메이션 step 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------ | -------------- |
| step | number | 애니메이션 Step 설정. |

-   애니메이션 Step 설정 실패 조건.
    -   입력된 최소 Step 보다 작은값이 입력 된 경우.
    -   입력된 최대 Step 보다 큰값이 입력 된 경우.
    -   createTimeSeriesObject() API로 객체 생성이 안된 경우.
-   Sample
    -   function JsonLoad 참조.
    -   [샌드박스\_시계열 Bar](http://sandbox.dtwincloud.com/code/main.do?id=effect_time_bar)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTimeSpeed(), setTimeSpeed(speed) → number

> 레이어 박스 객체 애니메이션 step 변환 시 객체 높이 변환 속도 설정.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ----- | ------ | --------------- |
| speed | number | 애니메이션 변환 속도 설정. |

-   애니메이션 Step 설정 실패 조건. - 입력된 최소 Step 보다 작은값이 입력 된 경우. - 입력된 최대 Step 보다 큰값이 입력 된 경우. - createTimeSeriesObject() API로 객체 생성이 안된 경우.
    {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getViewLimit(), setViewLimit(tilt) → number

> 레이어 가시화 Tilt 제한 설정.
>
> 카메라 tilt 값이 입력 값보다 작으면 투명 상태 설정.
>
> CSV, 빌보드, POI, 건물 객체 제한 설정.
>
> 서비스 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------ | ------------------------ |
| tilt | number | 카메라 각도에 따른 객체 가시화 유무 설정. |
{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(type) → boolean

> 레이어 가시화 옵션 정보 반환.
>
> 레이어 투명/반투명 상태 정보 반환.
>
> 사용자, 서비스 레이어 모두 사용 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| ---- | ------- | ------------------------------------------ |
| type | boolean | <p>true인 경우 레이어 가시화.<br>false인 레이어 숨김.</p> |

-   Sample
    -   function JsonLoad 참조.
    -   [샌드박스\_시계열 Bar](http://sandbox.dtwincloud.com/code/main.do?id=effect_time_bar)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ~~getWMSRequestParam(), setWMSRequestParam(parameter) → string~~

{% tabs %}
{% tab title="Infomation" %}

-   대체 API : setWMSProvider
    {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ~~getWMSVersion(), setWMSVersion(version) → string~~

{% tabs %}
{% tab title="Infomation" %}

-   대체 API : setWMSProvider
    {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ~~getUnion(), setUnion(union) → boolean~~

{% tabs %}
{% tab title="Infomation" %}

-   사용 안함
    {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Type Definitions

#### WMSOptions

> WMS 레이어 기본 생성 옵션.

| Name        | Type                                                      | Attributes | Default   | Description                              |
| ----------- | --------------------------------------------------------- | ---------- | --------- | ---------------------------------------- |
| url         | string                                                    |            |           | 요청 지오서버 url.                       |
| layer       | string                                                    |            |           | 요청 지오서버 레이어 명칭.               |
| minmumLevel | number                                                    | optional   | 0         | 최소 가시화 레벨.                        |
| maxmumLevel | number                                                    | optional   | 15        | 최대 가시화 레벨.                        |
| tileSize    | number                                                    | optional   | 256       | 요청 정사각형 이미지 크기\[Default 256]. |
| crs         | string                                                    | optional   | EPSG:4326 | 좌표 타입.                               |
| parameters  | [WMSOptions.SubOptions](jslayer.md#wmsoptions.suboptions) | optional   |           | 스타일, 옵션 설정 속성정보.              |

#### WMSOptions.SubOptions

> WMS 레이어 추가 생성 옵션.
>
> 그외 다른 옵션은 parameters 구성 시 태그 추가하며 자동으로 URL 구성.
>
> ex) stlye 옵션 등.

| Name        | Type   | Attributes | Default   | Description                        |
| ----------- | ------ | ---------- | --------- | ---------------------------------- |
| version     | string | optional   | 1.1.0     | 지오서버 요청 버전.                |
| service     | string | optional   | WMS       | 지오서버 요청 타입.                |
| request     | string | optional   | GetMap    | 지오서버 요청 지도 타입.           |
| format      | string | optional   | image/png | 지오서버 요청 이미지 타입.         |
| transparent | string | optional   | TRUE      | 지오서버 이미지 요청 시 투명 옵션. |
