---
description: 지도 내 객체를 관리하기 위한 API 입니다.
---

# JSLayer

> Module.createLayer() API를 생성합니다.
>
> [createObjectLayer](jslayerlist.md#createobjectlayer-option-jslayer) API로 사용자 레이어를 생성할 수 있습니다.
>
> [createXDServerLayer](jslayerlist.md#createxdserverlayer-option-jslayer) API로 서비스 레이어를 생성할 수 있습니다.

```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.createLayer("Layer Name");
```

## Properties

| Name                       | Type    | Description                   |
| -------------------------- | ------- | ----------------------------- |
| altitude\_offset           | number  | 포인트클라우드, 드론LOD 데이터 실시간 높이 설정. |
| lod\_object\_alpha         | number  | 서비스 레이어 속성 색상 알파값 설정.         |
| lod\_object\_detail\_ratio | number  | 서비스 레이어 객체 가시화 거리 비율 설정.      |
| serverURL                  | string  | 요청 서버 url 반환.                 |
| simple\_real3d             | boolean | 건물 객체 심플모드 설정.                |
| text\_character\_set       | string  | 레이어 텍스트 문자셋 값 설정.             |
| tile\_load\_ratio          | number  | 서비스 레이어 가시화 거리 비율 설정.         |
| view\_underground          | boolean | 지형 아래에 렌더링 되는 레이어 설정.         |
| object\_ahead              | boolean | 지형 또는 시설물이 앞에 존재할 경우 비가시화 설정. |
| boundaryLimit              | boolean | 오브젝트 요청 범위 제한 설정.             |

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
| ~~level~~ | ~~number~~                        | ~~0 고정 사용~~        |
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
* Return
  * result>0 : 레이어에 포함된 객체 수.
  * -1 : 레이어에 포하된 객체가 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSBoxRatio(ratio)

> WFS 레이어의 쿼리 범위 레벨을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| ratio | number | 쿼리 범위 레벨.   |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### findInsideObject(center, range) → string

> 입력값(range) 반경 이내에 속하는 오브젝트의 고유 명칭을 반환합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type                                | Description |
| ------ | ----------------------------------- | ----------- |
| center | [JSVector3D](../core/jsvector3d.md) | 반경의 중심 좌표.  |
| range  | number                              | 반경(반지름)     |

* Return
  * string : 반환 성공 (구분자 "#").
  * "0" : 반환 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * 레이어에 포함된 객체 수가 0인 경우.
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
* Return
  * string : 반환 성공 (구분자 ",").
  * "" : 반환 실패.
  * 실패 조건
    * 사용자 레이어에 포함된 객체 수가 0인 경우.
    * 서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getObjectsInBoundary(boundary) → object

> 폴리곤 범위 내에 속하는 오브젝트를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name     | Type   | Description |
| -------- | ------ | ----------- |
| boundary | object | 폴리곤 영역 좌표.  |

* Return
  * object : 반환 성공
    * | Name | Type   | Description |
      | ---- | ------ | ----------- |
      | id   | string | 객체 고유 명칭.   |
  * return : 반환 실패.
  * 실패 조건
    * 폴리곤을 구성하는 좌표가 3개 미만인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var boundary = [
  [126.93790903169547, 37.522875202560655, 0.0],
  [126.92841620055285, 37.516978366894115, 0.0],
  [126.91894402430914, 37.52022975707285, 0.0]
] // 고도값 유무 상관 없음

var objects = Module.getTileLayerList().nameAtLayer("facility_build").getObjectsInBoundary(boundary);

console.log(objects.id);
```
{% endtab %}
{% endtabs %}

### setTileObjectInitColor(color) → boolean

> 타일 레이어 초기화 색상을 설정합니다.
>
> 벡터 파이프 레이어 또는 건물 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}
| Name  | Type                          | Description |
| ----- | ----------------------------- | ----------- |
| color | [JSColor](../core/jscolor.md) | 초기화 색상.     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * 사용자 레이어인 경우.
    * 벡터 파이프 레이어 또는 건물 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setTileObjectColor(objkey, color) → boolean

> 타일 레이어 오브젝트 색상을 설정합니다.
>
> 벡터 파이프 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type                          | Description |
| ------ | ----------------------------- | ----------- |
| objkey | string                        | 객체 고유 명칭    |
| color  | [JSColor](../core/jscolor.md) | 초기화 색상.     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * 사용자 레이어인 경우.
    * 입력값(objkey)을 갖는 오브젝트가 없는 경우.
    * 벡터 파이프 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getTileObjectCenterPosition(objkey) → [JSVector3D](../core/jsvector3d.md)

> 타일 레이어 오브젝트의 중점을 반환합니다.
>
> 벡터 파이프 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type   | Description |
| ------ | ------ | ----------- |
| objkey | string | 객체 고유 명칭    |

* Return
  * [JSVector3D](../core/jsvector3d.md) : 반환 성공.
  * null : 반환 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * 사용자 레이어인 경우.
    * 입력값(objkey)을 갖는 오브젝트가 없는 경우.
    * 벡터 파이프 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setCrsWMS(crs) → boolean

> WMS 레이어의 지도 좌표계(Coordinate Reference System)를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type   | Description |
| ---- | ------ | ----------- |
| crs  | string | 지도 입력 좌표계   |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * 사용자 레이어인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var layerList = new Module.JSLayerList(false);
//...(Add WMS layer)...
var layer = layerList.nameAtLayer(“WMSLayer”);
layer.setCrsWMS("EPSG:4326");
```
{% endtab %}
{% endtabs %}

### setWFSPointDefaultIcon(icon) → boolean

> WFS 레이어의 디폴트 포인트 심볼을 지정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type                          | Description |
| ---- | ----------------------------- | ----------- |
| icon | [JSIcon](../object/jsicon.md) | 포인트 심볼      |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
    * 레이어 타입이 WFS POI 레이어가 아닌 경우
    * icon의 텍스처가 없는 경우
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSPointDefaultHighlightIcon(icon) → boolean

> WFS 레이어의 디폴트 하이라이트 포인트 심볼을 지정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type                          | Description  |
| ---- | ----------------------------- | ------------ |
| icon | [JSIcon](../object/jsicon.md) | 하이라이트 포인트 심볼 |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
    * 레이어 타입이 WFS POI 레이어가 아닌 경우
    * icon의 텍스처가 없는 경우
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSPointHighlightActive(objkey, active) → boolean

> WFS 레이어의 포인트 하이라이트 활성화를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type    | Description                               |
| ------ | ------- | ----------------------------------------- |
| objkey | string  | 객체 고유 명칭                                  |
| active | boolean | <p>활성화 여부<br>true: 활성화<br>false: 비활성화</p> |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
    * 레이어 타입이 WFS POI 레이어가 아닌 경우
    * 입력값(objkey)을 갖는 오브젝트가 레이어에 없는 경우
    * 오브젝트가 심볼 텍스트(POI) 타입이 아닌 경우
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSPointValueIcon(value, icon) → boolean

> WFS 레이어의 데이터 태그의 값을 이용한 포인트 심볼을 지정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name  | Type                          | Description   |
| ----- | ----------------------------- | ------------- |
| value | string                        | WFS 데이터 tag 값 |
| icon  | [JSIcon](../object/jsicon.md) | 하이라이트 포인트 심볼  |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
    * 레이어 타입이 WFS POI 레이어가 아닌 경우
    * icon의 텍스처가 없는 경우
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSPointPositionLine(type) → boolean

> 지형까지 수직으로 내리는 WFS POI 라인 렌더링 여부를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type    | Description |
| ---- | ------- | ----------- |
| type | boolean | 라인 렌더링 여부   |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
    * 레이어 타입이 WFS POI 레이어가 아닌 경우
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSPointBlinkActive(active) → boolean

> WFS 레이어의 포인트 깜빡임 활성화를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type    | Description                               |
| ------ | ------- | ----------------------------------------- |
| objkey | string  | 객체 고유 명칭                                  |
| active | boolean | <p>활성화 여부<br>true: 활성화<br>false: 비활성화</p> |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
    * 레이어 타입이 WFS POI 레이어가 아닌 경우
    * 입력값(objkey)을 갖는 오브젝트가 레이어에 없는 경우
    * 오브젝트가 심볼 텍스트(POI) 타입이 아닌 경우
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSPointBlinkOptions(name, color, size, speed) → boolean

> WFS 레이어의 포인트 깜빡임 옵션을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name  | Type                          | Description |
| ----- | ----------------------------- | ----------- |
| name  | string                        | 객체 고유 명칭    |
| color | [JSColor](../core/jscolor.md) | 깜빡임 색상      |
| size  | number                        | 깜빡임 크기      |
| speed | number                        | 깜빡임 속도      |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
    * 레이어 타입이 WFS POI 레이어가 아닌 경우
    * 입력값(objkey)을 갖는 오브젝트가 레이어에 없는 경우
    * 오브젝트가 심볼 텍스트(POI) 타입이 아닌 경우
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSRTT(type) → boolean

> WFS 레이어의 RTT 적용 여부를 설정합니다.
>
> WFS LINE과 WFS POLYGON 타입 레이어에서만 적용됩니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type    | Description |
| ---- | ------- | ----------- |
| type | boolean | RTT 적용 여부   |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 레이어 타입이 WFS LINE 또는 WFS POLY 레이어가 아닌 경우
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
* Return
  * number(0 이상) : 레이어 타입 반환([Layer Type List](../etc/type-list.md#layer-type-list)).
  * number(-1) : 레이어가 존재하지 않는 경우.
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
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| index | number | 인덱스 번호.     |

* Return
  * string : 반환 성공.
  * "" : 반환 실패.
  * 실패 조건
    * 입력 변수 index가 레이어에 포함된 객체 목록의 범위를 초과하는 경우(0보다 작거나 목록의 개체 수보다 큰 경우).
    * 레이어의 포함 객체 수가 0인 경우.
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
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| index | number | 인덱스 번호.     |

* Return
  * [JSObject](../object/jsobject.md) : 반환 성공.
  * null : 반환 실패.
  * 실패 조건
    * 입력 변수 index가 레이어에 포함된 객체 목록의 범위를 초과하는 경우(0보다 작거나 목록의 개체 수보다 큰 경우).
    * 레이어의 포함 객체 수가 0인 경우.
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

{% tabs %}
{% tab title="Infomation" %}
| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 고유 명칭.   |

* Return
  * [JSObject](../object/jsobject.md) : 반환 성공.
  * null : 반환 실패.
  * 실패 조건
    * 동일한 고유 명칭 객체가 없는 경우.
    * 입력 변수 name 문자열 데이터가 없는 경우.
    * 레이어의 포함 객체 수가 0인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### containsKey(name) → string

> 사용자 레이어에 포함된 객체 중 객체 고유 명칭 입력 변수 name인 객체의 존재 여부를 반환합니다.
>
> 객체 고유 명칭에 입력 변수 name이 일부만 포함이 되어 있어도 성공적으로 반환합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 고유 명칭.   |

* Return
  * string : 반환 성공.
  * "" : 반환 실패
  * 실패 조건
    * 객체 고유 명칭에 name이 포함된 객체가 없는 경우
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
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| index | number | 인덱스 번호.     |

* Return
  * true : 삭제 성공.
  * false : 삭제 실패.
  * 실패 조건
    * 입력 변수 index가 레이어에 포함된 객체 목록의 범위를 초과하는 경우(0보다 작거나 목록의 개체 수보다 큰 경우).
    * 레이어의 포함 객체 수가 0인 경우.
    * 서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속).
    * 외부 서버를 통해 가시화 된 데이터인 경우(Ex. WMS, WFS).
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
| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 고유 명칭.   |

* Return
  * true : 삭제 성공.
  * false : 삭제 실패.
  * 실패 조건
    * 사용자 레이어에 포함된 객체을 고유 명칭이 입력 변수 name와 동일한 객체가 없는 경우.
    * 입력 변수 name 문자열 데이터가 없는 경우.
    * 레이어의 포함 객체 수가 0인 경우.
    * 서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속).
    * 외부 서버를 통해 가시화 된 데이터인 경우(Ex. WMS, WFS).
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
| object | [JSObject](../object/jsobject.md) | 객체.         |

* Return
  * true : 삭제 성공.
  * false : 삭제 실패.
  * 실패 조건
    * 사용자 레이어에 포함된 객체와 입력 변수 object와 동일한 객체가 없는 경우.
    * 레이어의 포함 객체 수가 0인 경우.
    * 서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속).
    * 외부 서버를 통해 가시화 된 데이터인 경우(Ex. WMS, WFS).
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
* Return
  * true: 삭제 성공.
  * false: 삭제 실패.
  * 실패 조건
    * 레이어의 포함 객체 수가 0인 경우.
    * 서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속).
    * 외부 서버를 통해 가시화 된 데이터인 경우(Ex. WMS, WFS).
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
| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| url   | string | 데이터 요청 url.  |
| port  | number | 데이터 요청 port. |
| param | string | 데이터 요청 파라미터. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 생성한 레이어가 WFS 서비스 레이어가 아닌 경우.
    * 생성한 레이어가 사용자 레이어인 경우.
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
| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| url   | string | 데이터 요청 url.  |
| port  | number | 데이터 요청 port. |
| param | string | 데이터 요청 파라미터. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 생성한 레이어가 WMS 레이어가 아닌 경우.
    * 생성한 레이어가 사용자 레이어인 경우.
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
| Name       | Type                          | Description |
| ---------- | ----------------------------- | ----------- |
| fontName   | string                        | 폰트 명칭.      |
| fontSize   | number                        | 폰트 크기.      |
| fontWeight | number                        | 폰트 굵기.      |
| color      | [JSColor](../core/jscolor.md) | 폰트 색상.      |
| outColor   | [JSColor](../core/jscolor.md) | 폰트 외각 색상.   |
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
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| level | number | 가시화 최대 레벨.  |
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
| Name     | Type   | Description |
| -------- | ------ | ----------- |
| minLevel | number | 가시화 최소 레벨.  |
| maxLevel | number | 가시화 최대 레벨.  |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
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
| Name  | Type   | Description               |
| ----- | ------ | ------------------------- |
| ratio | number | 가시화 거리 비율(높을수록 가시화범위 증가). |

* Sample
  * function init 참조.
  * [Sandbox\_Parabolic Line](https://sandbox.egiscloud.com/code/main.do?id=object_line_arc)
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
| Name | Type    | Description                                 |
| ---- | ------- | ------------------------------------------- |
| type | boolean | <p>true: 프록시 서버 사용.<br>false: 기본 서버 사용.</p> |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
* Sample
  * function createLayerWMS 참조.
  * [Sandbox\_WMS](https://sandbox.egiscloud.com/code/main.do?id=layer_wms)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setWFSPointsHeightFromGround(height)

> WFS POI 레이어의 지형으로부터의 높이를 지정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type   | Description |
| ------ | ------ | ----------- |
| height | number | 지형으로부터의 높이  |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 사용자 레이어인 경우.
    * 레이어 타입이 WFS POI 레이어가 아닌 경우
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
| Name       | Type   | Description       |
| ---------- | ------ | ----------------- |
| hue        | number | HSV channel (색상). |
| saturation | number | HSV channel (채도). |
| value      | number | HSV channel (명도). |

* Return
  * true: 설정 성공.
  * false: 설정 실패.
* Sample
  * function setHSV 참조.
  * [Sandbox\_Adjust layer color](https://sandbox.egiscloud.com/code/main.do?id=layer_color_tone)
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
| count | number | 타일 크기.      |

* Return
  * true: 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 서비스 레이어가 아닌 경우.
    * WFS 서비스 레이어 타입이 아닌 경우.
* Note
  * 요창 단위가 클수록 큰 타일 범위의 WFS 데이터 요청.
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
| style | string | 스타일.        |

* Return
  * true: 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 서비스 레이어가 아닌 경우.
    * WMS 레이어 타입이 아닌 경우.
* Note
  * [스타일 설정 참조](http://dev.vworld.kr/dev/v4dv_wmsguide_s001.do)
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
| Name   | Type   | Description |
| ------ | ------ | ----------- |
| offset | number | 초기 고도 설정값.  |

* Return
  * true: 설정 성공.
  * false: 설정 실패.
* Sample
  * function init 참조.
  * [Sandbox\_Point Cloud](https://sandbox.egiscloud.com/code/main.do?id=layer_pointcloud_point_size)
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
| Name | Type   | Description |
| ---- | ------ | ----------- |
| size | number | 이미지 크기.     |

* Return
  * true: 설정 성공.
  * false: 설정 실패.
  * 실패 조건
    * 서비스 레이어가 아닌 경우.
    * WMS 레이어 타입이 아닌 경우.
* Note
  * [스타일 설정 참조](http://dev.vworld.kr/dev/v4dv_wmsguide_s001.do)
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
| Name | Type    | Description                                   |
| ---- | ------- | --------------------------------------------- |
| type | boolean | <p>true: HSV 색상 채널 시각화.<br>false: 일반 시각화.</p> |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
* Sample
  * function setHSV 참조.
  * [Sandbox\_Terrain Color Adjustment](https://sandbox.egiscloud.com/code/main.do?id=terrain_color_tone)
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
| fieldName | string | 태그 명칭.      |

* Return
  * true: 설정 성공.
  * false: 설정 실패.
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

> WFS 서비스 레이어에서 요청 받은 XML 포맷에서 POI 가시화 문자열 태그 이름을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name      | Type   | Description |
| --------- | ------ | ----------- |
| fieldName | string | 태그 명칭.      |
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

### setLayersWFS(fieldName)

> 요청 하고자 하는 WFS 명칭을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name      | Type   | Description |
| --------- | ------ | ----------- |
| fieldName | string | 요청 WFS 명칭.  |
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
layer.setLayersWFS(“BONBUN”);
```
{% endtab %}
{% endtabs %}

### setLayersWMS(fieldName)

> 요청 하고자 하는 WMS 명칭을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name      | Type   | Description |
| --------- | ------ | ----------- |
| fieldName | string | 요청 WMS 명칭.  |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSLayerList : new Module.JSLayerList(false)
};
var layer = API.JSLayerList.createWFSLayer(“newWMSLayer”, 0);
var dataURL = “http://...(Data request URL)...”;
var parameter= “...(Data request parameters)...”;
layer.setConnectionWMS(dataUrl, 0, parameter);
layer.setLayersWMS(“BONBUN”);
```
{% endtab %}
{% endtabs %}

### setWFSPropertyName(propertyName)

> WFS에 대한 속성 데이터로 받을 태그 이름을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name         | Type   | Description |
| ------------ | ------ | ----------- |
| propertyName | string | 태그 명칭.      |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 서비스 레이어가 아닌 경우.
    * WFS 레이어 타입이 아닌 경우.
* Note
  * 설정된 WFS 태그 목록은 WFS 데이터 요청 파라미터 중 “propertyname” 파라미터에 설정한 내용이 적용된다.
{% endtab %}

{% tab title="Template" %}
```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
layer.setWFSPropertyName(“STD_SGGCD,BONBUN,AG_GEOM”);
```
{% endtab %}
{% endtabs %}

### setWFSColor(lineColor, fontSize, fillColor)

> WFS 서비스 레이어 중 POI 객체를 출력하기 위한 텍스쳐의 윤곽선, 크기 및 채우기 색상을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name      | Type                          | Description |
| --------- | ----------------------------- | ----------- |
| lineColor | [JSColor](../core/jscolor.md) | 문자 윤곽선 색상.  |
| fontSize  | number                        | 문자 크기       |
| fillColor | [JSColor](../core/jscolor.md) | 문자 색상.      |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 서비스 레이어가 아닌 경우.
    * WFS 레이어 타입이 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var layerList = new Module.JSLayerList(false);
var layer = GLOBAL.JSLayerList.createWFSLayer(“NewWFSLayer”, 0);
var lineColor = new Module.JSColor(255, 255, 255, 255);
var fillColor = new Module.JSColor(255, 0, 0, 0);
layer.setWFSColor(lineColor, 12, fillColor);
```
{% endtab %}
{% endtabs %}

### setWFSTextColor(lineColor, fillColor)

> WFS 서비스 레이어 중 POI 객체를 출력하기 위한 텍스쳐의 윤곽선 및 채우기 색상을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name      | Type                          | Description |
| --------- | ----------------------------- | ----------- |
| lineColor | [JSColor](../core/jscolor.md) | 문자 윤곽선 색상.  |
| fillColor | [JSColor](../core/jscolor.md) | 문자 색상.      |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 서비스 레이어가 아닌 경우.
    * WFS 레이어 타입이 아닌 경우.
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
| Name   | Type                                | Description |
| ------ | ----------------------------------- | ----------- |
| option | [WMSOptions](jslayer.md#wmsoptions) | 속성 정보.      |

* Return
  * success : 생성 성공.
  * string : 생성 실패 (실패 오류 메시지 반환).
* Sample
  * function createLayerWMS 참조.
  * [Sandbox\_WMS](https://sandbox.egiscloud.com/code/main.do?id=layer_wms)
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
| Name        | Type    | Description                             |
| ----------- | ------- | --------------------------------------- |
| transparent | boolean | <p>true: 반투명 가시화.<br>false: 불투명 가시화</p> |

* Note
  * true로 설정한 경우 지형 이미지가 함께 보이는 반투명 상태로 출력되며, False로 설정한 경우 지형 이미지가 보이지 않는 불투명 상태로 출력된다.
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
| version | string | 버전 정보.      |

* Return
  * true : 설정 성공.
    * false : 설정 실패.
  * 실패 조건
    * 서비스 레이어가 아닌 경우.
    * WMS 레이어 타입이 아닌 경우.
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

### setWMTSProvider(option)

> WMTS 서비스 레이어를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name          | Type                                               | Description |
| ------------- | -------------------------------------------------- | ----------- |
| serverSetting | \[WMTSOption.Server]\(jslayer.md#wmtsoption.server | 서버 정보 설정.   |
| userSetting   | \[WMTSOption.User]\(jslayer.md#wmtsoption.user     | 서비스 정보 설정.  |

* Return
  * success : 생성 성공.
  * string : 생성 실패 (실패 오류 메시지 반환).
* Sample
  * [Sandbox\_WMTS](https://sandbox.egiscloud.com/code/main.do?id=layer_wmts)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### addObjects(objects)

> 여러 객체를 사용자 레이어에 한 번에 추가합니다.
>
> 이미 동일한 고유 명칭의 객체가 존재하는 경우 해당 객체는 건너뜁니다.

{% tabs %}
{% tab title="Information" %}
| Name    | Type                                      | Description       |
| ------- | ------------------------------------------ | ------------------- |
| objects | array([JSObject](../object/jsobject.md))  | 추가할 객체 배열.    |

* Note
  * 입력값이 배열이 아니거나 비어있는 경우 아무 동작도 하지 않습니다.
  * 배열 내 개별 객체가 null/undefined 이거나 이미 등록된 키를 가진 경우 해당 객체만 건너뛰고 나머지는 계속 처리합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.createLayer("objectlayer");
layer.addObjects([object1, object2, object3]);
```
{% endtab %}
{% endtabs %}

### setObjectColorListByKey(simpleColorMode, color, objectKeyList) → boolean

> 지정한 객체 고유 명칭 목록에 대해 색상을 일괄 설정합니다.
>
> 건물(Real3D) 타입 서비스 레이어에서 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name            | Type                           | Description                                          |
| ---------------- | ------------------------------ | ------------------------------------------------------- |
| simpleColorMode  | boolean                        | true: 심플 모드 색상 설정, false: 텍스처 모드 색상 설정. |
| color            | [JSColor](../core/jscolor.md)  | 설정할 색상.                                             |
| objectKeyList    | array(string)                  | 색상을 설정할 객체 고유 명칭 목록.                        |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * 사용자 레이어인 경우.
* Note
  * 이미 등록된 객체 고유 명칭인 경우 심플/텍스처 모드에 해당하는 색상값만 갱신합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
var layer = Module.getTileLayerList().nameAtLayer("facility_build");
var color = new Module.JSColor(255, 255, 0, 0);
layer.setObjectColorListByKey(true, color, ["obj_key_1", "obj_key_2"]);
```
{% endtab %}
{% endtabs %}

### clearObjectColorList() → boolean

> [setObjectColorListByKey](jslayer.md#setobjectcolorlistbykeysimplecolormode-color-objectkeylist-boolean) 로 설정된 객체 색상 목록을 초기화하고, 색상이 변경된 건물(Real3D) 객체를 원래 색상으로 되돌립니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 초기화 성공.
  * false : 초기화 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * 사용자 레이어인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var layer = Module.getTileLayerList().nameAtLayer("facility_build");
layer.clearObjectColorList();
```
{% endtab %}
{% endtabs %}

### setWFSGroupIcon(layerName, imageData, width, height) → boolean

> WFS 레이어에서 다수 포인트가 겹칠 경우 표시할 그룹 아이콘 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name      | Type          | Description                         |
| --------- | ------------- | -------------------------------------- |
| layerName | string        | 레이어 명칭(현재 미사용).               |
| imageData | array(number) | 이미지 픽셀 데이터(ARGB, byte 배열).    |
| width     | number        | 이미지 너비.                            |
| height    | number        | 이미지 높이.                            |

* Return
  * true : 설정 성공.
* Note
  * imageData 배열 길이가 1 이하인 경우 아이콘 텍스처 없이 설정됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setShaderReal3D(shaderType) → boolean

> Real3D(건물) 레이어의 셰이더 타입을 설정합니다.
>
> Real3D 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name       | Type   | Description             |
| ---------- | ------ | -------------------------- |
| shaderType | number | 셰이더 타입(0\~10 범위). |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * Real3D 레이어가 아닌 경우.
* Note
  * 이미 로드된 타일 내 모든 객체에도 즉시 반영됩니다.
  * 범위를 벗어난 값(0 미만 또는 10 초과)은 0으로 보정됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### import3DTiles(option) → boolean

> 3D Tiles 포맷 데이터를 레이어에 로드합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name                 | Type                            | Description                                       |
| -------------------- | -------------------------------- | ---------------------------------------------------- |
| option                | object                            | 3D Tiles 로드 옵션.                                  |
| ↳ url                 | string                            | tileset.json 요청 url.                               |
| ↳ autoMove            | boolean (optional, 기본값 false)  | 로드 후 카메라 자동 이동 여부.                        |
| ↳ offsetZ             | number (optional, 기본값 0.0)     | 높이(Z) 오프셋(meters 단위).                         |
| ↳ discardVertexData   | boolean (optional, 기본값 false) | 정점 데이터 보관 여부(true: 미보관, 메모리 절약).      |
| ↳ Authorization       | boolean (optional, 기본값 false) | 인증 헤더 사용 여부.                                  |

* Return
  * true : 로드 요청 성공.
  * false : 실패.
  * 실패 조건
    * 3D Tiles 레이어가 아닌 경우.
    * option이 null/undefined인 경우.
    * url이 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var layerList = new Module.JSLayerList(false);
var layer = layerList.create3DTilesLayer("3dtiles_layer");
layer.import3DTiles({
    url: "http://.../tileset.json",
    autoMove: true,
    offsetZ: 0.0
});
```
{% endtab %}
{% endtabs %}

### setDebugMode(debug) → boolean

> 3D Tiles 레이어의 디버그 모드(바운딩 볼륨 등 시각화)를 설정합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type    | Description                                |
| ----- | ------- | --------------------------------------------- |
| debug | boolean | true: 디버그 모드 활성화, false: 비활성화.     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 3D Tiles 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### reloadTiles() → boolean

> 타일 기반 레이어의 로드된 타일을 모두 지우고 다시 로드합니다.
>
> 지구본 타일 기반 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 재로드 성공.
  * false : 실패.
  * 실패 조건
    * 지구본 타일 기반 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.reloadTiles();
```
{% endtab %}
{% endtabs %}

### setRenderReal3dEdgeLine(set) → boolean

> Real3D(건물) 레이어 심플 모드의 외곽 라인 렌더링 여부를 설정합니다.
>
> Real3D 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description                               |
| ---- | ------- | -------------------------------------------- |
| set  | boolean | true: 외곽 라인 렌더링, false: 렌더링 안함.   |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
* Note
  * 이미 로드된 객체에도 즉시 반영됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setReal3dEdgeLineColor(color) → boolean

> Real3D(건물) 레이어 심플 모드 외곽 라인 색상을 설정합니다.
>
> Real3D 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type                          | Description    |
| ----- | ----------------------------- | ------------------ |
| color | [JSColor](../core/jscolor.md) | 외곽 라인 색상.    |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setReal3dEdgeLineWidth(width) → boolean

> Real3D(건물) 레이어 외곽 라인 두께를 설정합니다.
>
> Real3D 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description     |
| ----- | ------ | ------------------- |
| width | number | 외곽 라인 두께.     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setRenderReal3dWireFrame(set) → boolean

> Real3D(건물) 레이어의 와이어프레임 렌더링 여부를 설정합니다.
>
> Real3D 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description                                  |
| ---- | ------- | ------------------------------------------------ |
| set  | boolean | true: 와이어프레임 렌더링, false: 렌더링 안함.    |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setReal3dWireFrameColor(color) → boolean

> Real3D(건물) 레이어 와이어프레임 색상을 설정합니다.
>
> Real3D 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type                          | Description       |
| ----- | ----------------------------- | --------------------- |
| color | [JSColor](../core/jscolor.md) | 와이어프레임 색상.    |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getReal3DFormatData(objectKey, format) → ArrayBuffer

> Real3D(건물) 객체 데이터를 지정한 포맷(3DS 또는 XDO)의 바이너리 데이터로 반환합니다.
>
> VWorld 건물 서비스 레이어인 경우 보안상 사용할 수 없습니다.

{% tabs %}
{% tab title="Information" %}
| Name      | Type   | Description                              |
| --------- | ------ | -------------------------------------------- |
| objectKey | string | 객체 고유 명칭.                              |
| format    | string | 변환 포맷("3DS" 또는 "XDO", 대소문자 무관).  |

* Return
  * ArrayBuffer(typed array) : 반환 성공.
  * null : 반환 실패.
  * 실패 조건
    * VWorld 건물 서비스 레이어인 경우.
    * Real3D 레이어가 아닌 경우.
    * 입력값(objectKey)을 갖는 오브젝트가 없거나 Real3D 타입이 아닌 경우.
    * format이 "3DS", "XDO" 둘 다 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getReal3dTexture(objectKey, textureLevel) → [JSIcon](../object/jsicon.md)

> Real3D(건물) 객체의 텍스처를 JSIcon 형태로 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name         | Type   | Description                                     |
| ------------ | ------ | --------------------------------------------------- |
| objectKey    | string | 객체 고유 명칭.                                     |
| textureLevel | number | 텍스처 레벨(-1 입력 시 로드된 것 중 최고화질 반환). |

* Return
  * [JSIcon](../object/jsicon.md) : 반환 성공.
  * null : 반환 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
    * 입력값(objectKey)을 갖는 오브젝트가 없는 경우.
    * 오브젝트에 텍스처가 없는 경우.
    * 지정한 레벨의 텍스처가 로드되지 않은 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getReal3dTextureFileName(objectKey) → string

> Real3D(건물) 객체의 텍스처 파일 이름을 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name      | Type   | Description     |
| --------- | ------ | ------------------- |
| objectKey | string | 객체 고유 명칭.    |

* Return
  * string : 반환 성공.
  * "" : 반환 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
    * 입력값(objectKey)을 갖는 오브젝트가 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getReal3dTextureData(objectKey, textureLevel) → ArrayBuffer

> Real3D(건물) 객체 텍스처의 픽셀 데이터를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name         | Type   | Description                                     |
| ------------ | ------ | --------------------------------------------------- |
| objectKey    | string | 객체 고유 명칭.                                     |
| textureLevel | number | 텍스처 레벨(-1 입력 시 로드된 것 중 최고화질 반환). |

* Return
  * ArrayBuffer(typed array) : 반환 성공.
  * null : 반환 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
    * 입력값(objectKey)을 갖는 오브젝트가 없는 경우.
    * 오브젝트에 텍스처가 없는 경우.
    * 텍스처가 압축 포맷인 경우.
    * 지정한 레벨의 텍스처가 로드되지 않은 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setReal3dLodTextureRatio(ratio) → boolean

> Real3D(건물) 레이어 텍스처 LOD 비율을 조정합니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description             |
| ----- | ------ | --------------------------- |
| ratio | number | 텍스처 LOD 비율(0 이상).   |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * ratio가 0보다 작은 경우.
    * Real3D 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setDefineMeshColorByObjectKey(checkString, compareType, color, isSimpleMode) → boolean

> 객체 고유 명칭 조건에 따라 Real3D 타일 객체의 메쉬 색상을 정의합니다.

{% tabs %}
{% tab title="Information" %}
| Name         | Type                           | Description                                              |
| ------------ | ------------------------------ | ------------------------------------------------------------ |
| checkString  | string                          | 비교할 문자열.                                              |
| compareType  | number                          | 비교 방식(내부 정의값).                                      |
| color        | [JSColor](../core/jscolor.md)  | 설정할 메쉬 색상.                                            |
| isSimpleMode | boolean                         | true: 심플 모드 색상 설정, false: 텍스처 모드 색상 설정.     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
* Note
  * 이미 로드된 타일 내 객체에도 즉시 반영됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setDefineMeshColorByObjectKeyList(objectKeyList, compareType, color, isSimpleMode) → boolean

> 객체 고유 명칭 목록에 대해 Real3D 타일 객체의 메쉬 색상을 정의합니다.

{% tabs %}
{% tab title="Information" %}
| Name          | Type                           | Description                                              |
| ------------- | ------------------------------- | ------------------------------------------------------------ |
| objectKeyList | array(string)                   | 색상을 설정할 객체 고유 명칭 목록.                          |
| compareType   | number                          | 비교 방식(내부 정의값).                                      |
| color         | [JSColor](../core/jscolor.md)  | 설정할 메쉬 색상.                                            |
| isSimpleMode  | boolean                         | true: 심플 모드 색상 설정, false: 텍스처 모드 색상 설정.     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
* Note
  * 목록 중 실제 레이어에 존재하는 객체에 대해서만 적용됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setDefineEdgeLineColorByObjectKey(checkString, compareType, color) → boolean

> 객체 고유 명칭 조건에 따라 Real3D 타일 객체의 외곽 라인 색상을 정의합니다.

{% tabs %}
{% tab title="Information" %}
| Name        | Type                           | Description                     |
| ----------- | ------------------------------- | ------------------------------------ |
| checkString | string                           | 비교할 문자열.                       |
| compareType | number                           | 비교 방식(내부 정의값).               |
| color       | [JSColor](../core/jscolor.md)   | 설정할 외곽 라인 색상.                |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
* Note
  * 이미 로드된 타일 내 객체에도 즉시 반영됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setDefineVisibleByFileName(checkString, compareType, visible) → boolean

> 파일 이름 조건에 따라 Real3D 타일 객체의 가시화 여부를 정의합니다.

{% tabs %}
{% tab title="Information" %}
| Name        | Type    | Description                    |
| ----------- | ------- | ---------------------------------- |
| checkString | string  | 비교할 파일 이름 문자열.           |
| compareType | number  | 비교 방식(내부 정의값).            |
| visible     | boolean | true: 가시화, false: 비가시화.     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어가 아닌 경우.
* Note
  * 이미 로드된 타일 내 객체에도 즉시 반영됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### clearDefineTileObjectStyle() → boolean

> [setDefineMeshColorByObjectKey](jslayer.md#setdefinemeshcolorbyobjectkeycheckstring-comparetype-color-issimplemode), [setDefineEdgeLineColorByObjectKey](jslayer.md#setdefineedgelinecolorbyobjectkeycheckstring-comparetype-color), [setDefineVisibleByFileName](jslayer.md#setdefinevisiblebyfilenamecheckstring-comparetype-visible) 로 정의된 스타일 조건을 모두 초기화합니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 초기화 성공.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setReal3dCutHeight(objectKey, height) → boolean

> Real3D(건물) 객체의 수평 단면 절단 높이를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name      | Type   | Description                          |
| --------- | ------ | ---------------------------------------- |
| objectKey | string | 객체 고유 명칭.                          |
| height    | number | 절단 기준 높이(고도, meters 단위).       |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어(또는 XDO 패킹 레이어)가 아닌 경우.
    * 레이어에 객체가 없는 경우.
    * 입력값(objectKey)을 갖는 오브젝트가 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setReal3dCutUse(objectKey, use) → boolean

> Real3D(건물) 객체의 수평 단면 절단 효과 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name      | Type    | Description                            |
| --------- | ------- | ------------------------------------------ |
| objectKey | string  | 객체 고유 명칭.                            |
| use       | boolean | true: 단면 절단 효과 사용, false: 미사용.  |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * Real3D 레이어(또는 XDO 패킹 레이어)가 아닌 경우.
    * 레이어에 객체가 없는 경우.
    * 입력값(objectKey)을 갖는 오브젝트가 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### cutReal3d(objectKey, option) → boolean

> Real3D(건물) 객체의 횡단면(절단) 가시화를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name        | Type                                       | Description                            |
| ----------- | -------------------------------------------- | ------------------------------------------ |
| objectKey   | string                                        | 객체 고유 명칭.                            |
| option      | object                                         | 절단 옵션.                                 |
| ↳ use       | boolean (optional)                             | 절단 효과 사용 여부.                        |
| ↳ height    | number (optional, 기본값 9999.9)               | 절단 기준 높이.                            |
| ↳ alpha     | number (optional, 기본값 1.0)                  | 절단면 투명도.                              |
| ↳ lineColor | [JSColor](../core/jscolor.md) (optional)      | 절단면 외곽선 색상.                         |
| ↳ lineWidth | number (optional)                              | 절단면 외곽선 두께.                         |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 지구본 타일 기반 레이어가 아닌 경우.
    * 입력값(objectKey)을 갖는 오브젝트가 없는 경우.
* Note
  * option에 없는 필드는 변경하지 않고 이전 값을 그대로 유지합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.cutReal3d("obj_key_1", {
    use: true,
    height: 50.0,
    alpha: 0.5,
    lineColor: new Module.JSColor(255, 255, 0, 0),
    lineWidth: 2.0
});
```
{% endtab %}
{% endtabs %}

### setVectorPipeDirectionEffect(startColor, endColor, interval, speed) → boolean

> 벡터 파이프 레이어의 흐름 방향 효과 색상, 간격, 속도를 설정합니다.
>
> 벡터 파이프 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name       | Type                          | Description       |
| ---------- | ----------------------------- | --------------------- |
| startColor | [JSColor](../core/jscolor.md) | 효과 시작 색상.      |
| endColor   | [JSColor](../core/jscolor.md) | 효과 끝 색상.        |
| interval   | number                         | 효과 간격.           |
| speed      | number                         | 효과 이동 속도.       |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 벡터 파이프 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setVectorPipeDirectionEffectVisible(visible) → boolean

> 벡터 파이프 레이어의 흐름 방향 효과 표시 여부를 설정합니다.
>
> 벡터 파이프 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name    | Type    | Description                        |
| ------- | ------- | -------------------------------------- |
| visible | boolean | true: 효과 표시, false: 효과 비표시.   |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 벡터 파이프 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setVectorPipeDirectionEffectAltitude(altitude) → boolean

> 벡터 파이프 레이어의 흐름 방향 효과 표시 고도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type   | Description |
| -------- | ------ | ----------- |
| altitude | number | 표시 고도.  |

* Return
  * true : 설정 성공.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setVectorPipeDirectionEffectMinimumRadius(minimumRadius) → boolean

> 벡터 파이프 레이어의 흐름 방향 효과가 표시되는 최소 반경을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name          | Type   | Description             |
| ------------- | ------ | --------------------------- |
| minimumRadius | number | 최소 반경(0.001 이상).     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * minimumRadius가 0.001보다 작은 경우.
    * 벡터 파이프 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setVectorPipeMinimumRadius(minimumRadius) → boolean

> 벡터 파이프 오브젝트가 렌더링되는 최소 반경을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name          | Type   | Description             |
| ------------- | ------ | --------------------------- |
| minimumRadius | number | 최소 반경(0.001 이상).     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * minimumRadius가 0.001보다 작은 경우.
    * 벡터 파이프 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setVectorPipeSimplyRange(simplyRange) → boolean

> 벡터 파이프 오브젝트의 단순화(Simplify) 범위를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name        | Type   | Description               |
| ----------- | ------ | ----------------------------- |
| simplyRange | number | 단순화 범위(0.001 이상).     |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * simplyRange가 0.001보다 작은 경우.
    * 벡터 파이프 레이어가 아닌 경우.
* Note
  * 이미 로드된 파이프 객체에도 즉시 반영됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getPipeIntersection(path) → array

> 지정한 경로(path)와 옥트리 레이어 내 벡터 파이프 오브젝트가 교차하는 지점들을 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type                                     | Description     |
| ---- | ------------------------------------------ | ------------------- |
| path | [JSVec2Array](../core/jsvec2array.md)     | 교차 검사 경로.    |

* Return
  * array : 교차점 목록.
    * | Name      | Type                                  | Description                |
      | --------- | -------------------------------------- | ------------------------------ |
      | objectKey | string                                 | 교차한 파이프 객체 고유 명칭. |
      | position  | [JSVector3D](../core/jsvector3d.md)   | 교차 위치.                    |
  * [] : 레이어에 객체가 없는 경우.
* Note
  * 파이프(EOT\_PIPE) 타입 오브젝트만 대상으로 검사합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let path = new Module.JSVec2Array();
//...(경로 좌표 추가)...
let intersections = layer.getPipeIntersection(path);
```
{% endtab %}
{% endtabs %}

### setOctreeLoadCallback(callback) → boolean

> 옥트리 레이어 타일 로드 완료 시 호출될 콜백 함수를 설정합니다.
>
> 옥트리 구조 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type     | Description              |
| -------- | -------- | ---------------------------- |
| callback | function | 로드 완료 시 호출될 콜백 함수. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 옥트리 구조 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setOctreeLoadCallback(function() {
    console.log("Octree loaded!");
});
```
{% endtab %}
{% endtabs %}

### getObjects() → array

> 레이어에 포함된 모든 객체와 고유 명칭 목록을 반환합니다.
>
> 지구본 타일 기반 레이어 또는 옥트리 구조 레이어에서 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * array : 반환 성공.
    * | Name   | Type                                | Description   |
      | ------ | -------------------------------------- | --------------- |
      | key    | string                                  | 객체 고유 명칭. |
      | object | [JSObject](../object/jsobject.md)      | 객체.           |
  * [] : 반환 실패.
  * 실패 조건
    * 지구본 타일 기반 레이어 또는 옥트리 구조 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
let objects = layer.getObjects();
objects.forEach(o => console.log(o.key, o.object));
```
{% endtab %}
{% endtabs %}

### setGhostSymbolTilePosition(option) → boolean

> 고스트 심볼(Ghost 3D Symbol) 레이어의 심볼 위치 정렬 기준을 설정합니다.
>
> 고스트 심볼 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name        | Type                      | Description                                     |
| ----------- | -------------------------- | ---------------------------------------------------- |
| option      | object                     | 정렬 옵션.                                            |
| ↳ align     | string (optional)          | "CENTER", "BOTTOM", "TOP" 중 하나(대소문자 무관).      |
| ↳ basepoint | array(number) (optional)   | 기준점 좌표 [x, y, z] (3개 원소 필요).                 |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 고스트 심볼 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setGhostSymbolTilePosition({
    align: "BOTTOM",
    basepoint: [0, 0, 0]
});
```
{% endtab %}
{% endtabs %}

### pick(screenX, screenY) → object

> 화면 좌표를 기준으로 레이어 내 오브젝트를 피킹합니다.

{% tabs %}
{% tab title="Information" %}
| Name    | Type   | Description             |
| ------- | ------ | --------------------------- |
| screenX | number | 화면 X 좌표(pixel).         |
| screenY | number | 화면 Y 좌표(pixel).         |

* Return
  * object : 피킹 성공.
    * | Key       | Type                                  | Description             |
      | --------- | -------------------------------------- | --------------------------- |
      | position  | [JSVector3D](../core/jsvector3d.md)   | 피킹된 좌표.               |
      | objectKey | string                                  | 피킹된 객체 고유 명칭.     |
  * null : 피킹 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let pickInfo = layer.pick(500, 300);
if (pickInfo) {
    console.log(pickInfo.objectKey, pickInfo.position);
}
```
{% endtab %}
{% endtabs %}

### rebuildObjectLayer() → boolean

> 옥트리 레이어의 오브젝트를 다시 배치(트리 재구성)합니다.
>
> 옥트리 구조 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 재배치 성공.
  * false : 옥트리 구조 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.rebuildObjectLayer();
```
{% endtab %}
{% endtabs %}

### setMouseHover(hover)

> 레이어의 마우스 호버 모드 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type    | Description                                 |
| ----- | ------- | ----------------------------------------------- |
| hover | boolean | true: 마우스 호버 모드 사용, false: 미사용.     |
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setMouseHover(true);
```
{% endtab %}
{% endtabs %}

### setUserTileJsonParsing(set) → boolean

> 사용자 레이어 타일 로드 시 JSON 파싱 사용 여부를 설정합니다.
>
> 사용자 레이어(지구본 타일 기반)에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description                          |
| ---- | ------- | ----------------------------------------- |
| set  | boolean | true: JSON 파싱 사용, false: 미사용.      |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 지구본 타일 기반 사용자 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setMaxLevelOverlap(overlap) → boolean

> 하이브리드 레이어의 최대 레벨 초과 시 부모 타일 참조 여부를 설정합니다.
>
> 하이브리드 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name    | Type    | Description                                        |
| ------- | ------- | ----------------------------------------------------- |
| overlap | boolean | true: 최대 레벨 초과 시 부모 타일 참조, false: 미참조. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 지구본 타일 기반 레이어가 아닌 경우.
    * 하이브리드 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getObjectInScreenRect(startX, startY, endX, endY) → array

> 화면 영역(사각형) 내에 보이는 레이어 객체 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description           |
| ------ | ------ | -------------------------- |
| startX | number | 영역 시작 X 좌표(pixel).  |
| startY | number | 영역 시작 Y 좌표(pixel).  |
| endX   | number | 영역 끝 X 좌표(pixel).    |
| endY   | number | 영역 끝 Y 좌표(pixel).    |

* Return
  * array : 화면 영역 내 객체 목록.
    * | Name      | Type                                  | Description        |
      | --------- | -------------------------------------- | ---------------------- |
      | objectKey | string                                  | 객체 고유 명칭.       |
      | position  | [JSVector3D](../core/jsvector3d.md)   | 객체 중심 좌표.       |
  * [] : 반환 실패.
  * 실패 조건
    * 지구본 타일 기반 레이어 또는 옥트리 구조 레이어가 아닌 경우.
    * 화면 영역 내 시야에 들어온 객체가 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
let objects = layer.getObjectInScreenRect(100, 100, 500, 500);
```
{% endtab %}
{% endtabs %}

### setPointCloudeSize(size)

> 포인트 클라우드(3D Tiles 기반) 레이어의 포인트 크기를 설정합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ----------------- |
| size | number | 포인트 크기.      |

* Note
  * [setPointCloudPointSize](jslayer.md#setpointcloudpointsizesize-boolean) 와 유사하나, 3D Tiles 레이어 전용으로 동작합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPointCloudInterpolateMode(mode) → boolean

> 포인트 클라우드 레이어의 보간 모드를 설정합니다.
>
> 포인트 클라우드 또는 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description     |
| ---- | ------ | ------------------- |
| mode | number | 보간 모드 값.       |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 포인트 클라우드 또는 3D Tiles 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setLimitBoundary(option) → boolean

> 타일 레이어의 요청 범위를 다각형 경계로 제한합니다.

{% tabs %}
{% tab title="Information" %}
| Name       | Type                     | Description                                              |
| ---------- | ------------------------ | ------------------------------------------------------------ |
| option     | object                   | 경계 옵션.                                                    |
| ↳ boundary | object                   | 경계 정의(아래 두 형태 중 하나).                              |
| &nbsp;&nbsp;• min/max | array(number)[2] | 사각형 경계(최소, 최대 좌표) [lon, lat].               |
| &nbsp;&nbsp;• 배열     | array(array(number)[2]) | 다각형 경계 좌표 배열(각 원소 [lon, lat], 3개 이상 필요). |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 월드 또는 레이어가 없는 경우.
    * boundary가 없는 경우.
    * min/max 또는 배열 형식이 올바르지 않은 경우.
    * 유효 좌표 개수가 3개 미만인 경우.
* Note
  * [boundaryLimit](jslayer.md#properties) 속성과 함께 사용되어 요청 범위를 제한합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setLimitBoundary({
    boundary: {
        min: [126.9, 37.5],
        max: [127.0, 37.6]
    }
});
```
{% endtab %}
{% endtabs %}

### getViewInTransparency() → boolean

> 레이어가 투명 상태에서도 보이도록 설정되었는지 여부를 반환합니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 투명 상태에서도 렌더링됨.
  * false : 투명 상태에서 렌더링 안됨.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getPickInfoWithinRadius(center, radius) → object

> 중심 좌표(center)로부터 일정 반경(radius) 이내에서 카메라 뷰와 상관없이 피킹된 객체 정보를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                                  | Description               |
| ------ | -------------------------------------- | ------------------------------ |
| center | [JSVector3D](../core/jsvector3d.md)   | 피킹 기준 중심 좌표.          |
| radius | number                                  | 피킹 반경(meters 단위).      |

* Return
  * `object` : 피킹 성공 시 위치 및 객체 정보 반환
  * `null` : 피킹 실패 시
* 반환 객체 구조

| Key       | Type                                | Description         |
| --------- | ----------------------------------- | -------------------- |
| position  | [JSVector3D](../core/jsvector3d.md) | 피킹된 좌표 위치.     |
| objectKey | string                               | 피킹된 객체의 고유 키. |
| layerName | string                               | 피킹된 객체가 포함된 레이어 이름. |
{% endtab %}

{% tab title="Template" %}
```javascript
let center = new Module.JSVector3D(127.0, 37.5, 50.0);
let pickInfo = layer.getPickInfoWithinRadius(center, 100.0);

if (pickInfo) {
    console.log("Position:", pickInfo.position);
    console.log("Object Key:", pickInfo.objectKey);
}
```
{% endtab %}
{% endtabs %}

### addTileInData(tileInfo) → boolean

> 바람장(Wind Layer/Tile Flow) 레이어의 타일에 UV 흐름 데이터를 삽입합니다.
>
> 타일 흐름(Tile Flow) 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name                 | Type                     | Description                          |
| --------------------- | ------------------------ | ---------------------------------------- |
| tileInfo              | object                    | 타일 데이터 정보.                        |
| ↳ header              | object                    | 타일 위치/크기 정보.                     |
| &nbsp;&nbsp;• level/idx/idy | number             | 타일 위치 정보.                          |
| &nbsp;&nbsp;• col/row       | number             | 타일 데이터 그리드 열/행 개수.           |
| ↳ data                | array(array(number)[2])  | UV 데이터 배열([u, v] 쌍의 배열).        |

* Return
  * true : 삽입 성공.
  * false : 삽입 실패.
  * 실패 조건
    * 타일 흐름(Tile Flow) 레이어가 아닌 경우.
    * header 또는 data 누락, 혹은 level/idx/idy/col/row 누락.
    * data 배열 길이가 (col + 2\*halo) \* (row + 2\*halo) 와 다른 경우.
    * 해당 위치의 타일이 존재하지 않는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### windlayerStart()

> 타일 흐름(Tile Flow) 레이어의 바람장 파티클 흐름 효과를 시작합니다.
>
> 타일 흐름 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}

{% tab title="Template" %}
```javascript
layer.windlayerStart();
```
{% endtab %}
{% endtabs %}

### setWindLayerProperty(option) → boolean

> 바람장(Wind Layer) 파티클 옵션을 설정합니다.
>
> 타일 흐름(Tile Flow) 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name           | Type               | Description                             |
| -------------- | ------------------ | ------------------------------------------- |
| option         | object              | 바람장 옵션.                                |
| ↳ particleNum  | number (optional)   | 파티클 개수(최대 5000개로 제한됨).          |
| ↳ velocity     | number (optional)   | 파티클 이동 속도 배율.                      |
| ↳ height       | number (optional)   | 파티클 표시 높이.                           |
| ↳ colorMode    | number (optional)   | 파티클 색상 모드.                           |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 타일 흐름(Tile Flow) 레이어가 아닌 경우.
    * option이 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setWindLayerProperty({
    particleNum: 2000,
    velocity: 1.0,
    height: 10.0,
    colorMode: 0
});
```
{% endtab %}
{% endtabs %}

### setBounderyBox(box)

> 옥트리 레이어의 바운더리 박스를 설정합니다.
>
> 옥트리 구조 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type              | Description               |
| ----- | ----------------- | ---------------------------- |
| box   | object             | 바운더리 박스 옵션.          |
| ↳ min | array(number)[2]   | 최소 좌표 [lon, lat].       |
| ↳ max | array(number)[2]   | 최대 좌표 [lon, lat].       |

* Note
  * 옥트리 구조 레이어가 아닌 경우 아무 동작도 하지 않습니다.
  * min/max가 모두 존재하는 경우에만 적용됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setBounderyBox({
    min: [126.9, 37.5],
    max: [127.0, 37.6]
});
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
| alpha | number | 투명도.        |

* 실패 조건
  * 사용자 레이어인 경우.
  * 시설물 이외 서비스 레이어인 경우.
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
| type | boolean | 좌표 옵션.      |

* Sample
  * function createLayerWMS 참조.
  * [Sandbox\_WMS](https://sandbox.egiscloud.com/code/main.do?id=layer_wms)
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
| Name | Type    | Description                                   |
| ---- | ------- | --------------------------------------------- |
| edit | boolean | <p>true: 편집 레이어 설정.<br>false: 일반 레이어로 설정.</p> |

* 실패 조건
  * 서비스 레이어인 경우(서비스 레이어에서 객체는 Tile에 종속)
* Sample
  * function initSamplePage 참조.
  * [Sandbox\_Shape Creation](https://sandbox.egiscloud.com/code/main.do?id=object_figure)
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
| Name     | Type   | Description           |
| -------- | ------ | --------------------- |
| distance | number | 최소 가시 거리 (meters 단위). |

* 실패 조건
  * 최소 가시거리가 최대 가시거리보다 큰 경우.
  * 서비스 레이어인 경우.
* Sample
  * function showGrid 참조.
  * [Sandbox\_Grid (2D)](https://sandbox.egiscloud.com/code/main.do?id=object_grid_2d)
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
| Name     | Type   | Description           |
| -------- | ------ | --------------------- |
| distance | number | 최대 가시 거리 (meters 단위). |

* 실패 조건
  * 최대 가시거리가 최소 가시거리보다 작은 경우.
  * 서비스 레이어인 경우.
* Sample
  * function showGrid 참조.
  * [Sandbox\_Grid (2D)](https://sandbox.egiscloud.com/code/main.do?id=object_grid_2d)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getMaxLevel(), setMaxLevel(level) → number

> 서비스 레이어 최대 가시 레벨을 설정합니다.
>
> 서비스 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| level | number | 최대 가시 레벨.   |

* 실패 조건
  * 사용자 레이어인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getMinLevel(), setMinLevel(level) → number

> 서비스 레이어 최소 가시 레벨을 설정합니다.
>
> 서비스 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| level | number | 최소 가시 레벨.   |

* 실패 조건
  * 사용자 레이어인 경우.
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
| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 레이어 명칭.     |
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
| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| horizontal | number | 객체 가로 크기.   |

* 실패 조건
  * 0 보다 작은 값이 입력 된 경우.
  * [createTimeSeriesObject()](../object/jstimeseriesobject.md#JSTimeSeriesObject) API로 객체 생성이 안된 경우.
* Sample
  * function JsonLoad 참조.
  * [Sandbox\_Time Series Bar](https://sandbox.egiscloud.com/code/main.do?id=effect_time_bar)
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
| Name     | Type   | Description |
| -------- | ------ | ----------- |
| vertical | number | 객체 세로 크기.   |

* 실패 조건
  * 0 보다 작은 값이 입력 된 경우.
  * [createTimeSeriesObject()](../object/jstimeseriesobject.md#JSTimeSeriesObject) API로 객체 생성이 안된 경우.
* Sample
  * function JsonLoad 참조.
  * [Sandbox\_Time Series Bar](https://sandbox.egiscloud.com/code/main.do?id=effect_time_bar)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setObjectVisibleWithBoundary(minLon, maxLon, minLat, maxLat) → number

> 경위도 범위 내의 오브젝트 가시화를 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name   | Type   | Description         |
| ------ | ------ | ------------------- |
| minLon | number | 최소 경도값(degrees 단위). |
| maxLon | number | 최대 경도값(degrees 단위). |
| minLat | number | 최소 위도값(degrees 단위). |
| maxLat | number | 최대 위도값(degrees 단위). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setOctreeCullDistanceCheckType(type) → boolean

> 거리로 컬링할 때의 기준을 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type   | Description                                               |
| ---- | ------ | --------------------------------------------------------- |
| type | string | <p>"layer": 레이어와의 거리로 컬링.<br>"object": 오브젝트와의 거리로 컬링.</p> |
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
| Name | Type    | Description                                     |
| ---- | ------- | ----------------------------------------------- |
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
| Name | Type   | Description |
| ---- | ------ | ----------- |
| step | number | 애니메이션 단계.   |

* 실패 조건
  * 입력 변수값(step)이 설정된 최소 step보다 작은값이 입력된 경우.
  * 입력 변수값(step)이 설정된 최대 step보다 큰값이 입력된 경우.
  * [createTimeSeriesObject()](https://github.com/EgisCorp/XDWorld_WebGL_Manual/blob/master/layer/jstimeseriesobject.md#JSTimeSeriesObject) API로 객체 생성이 안된 경우.
* Sample
  * function JsonLoad 참조.
  * [Sandbox\_Time Series Bar](https://sandbox.egiscloud.com/code/main.do?id=effect_time_bar)
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
| speed | number | 변환 속도.      |

* 실패 조건
  * [createTimeSeriesObject()](https://github.com/EgisCorp/XDWorld_WebGL_Manual/blob/master/layer/jstimeseriesobject.md#JSTimeSeriesObject) API로 객체 생성이 안된 경우.
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
| Name | Type   | Description          |
| ---- | ------ | -------------------- |
| tilt | number | 제한 tilt(degrees 단위). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getVisible(), setVisible(type) → boolean

> 레이어에 포함된 객체에 대한 가시화 유무를 설정합니다.
>
> 레이어가 투명/불투명 정보를 반환합니다.
>
> 사용자 및 서비스 레이어 모두에서 사용할 수 있습니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type    | Description                                           |
| ---- | ------- | ----------------------------------------------------- |
| type | boolean | <p>true: 레이어 포함 객체 가시화.<br>false: 레이어 포함 객체 비가시화.</p> |

* Sample
  * function JsonLoad 참조.
  * [Sandbox\_Time Series Bar](https://sandbox.egiscloud.com/code/main.do?id=effect_time_bar)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### ~~getWMSRequestParam(), setWMSRequestParam(parameter) → string~~

{% tabs %}
{% tab title="Infomation" %}
* 대체 API: setWMSProvider
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### ~~getWMSVersion(), setWMSVersion(version) → string~~

{% tabs %}
{% tab title="Infomation" %}
* 대체 API: setWMSProvider
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### ~~getUnion(), setUnion(union) → boolean~~

{% tabs %}
{% tab title="Infomation" %}
* 사용되지 않음
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setPointCloudRenderModeRGB(offsetR, offsetG, offsetB) → boolean

> 포인트 클라우드 레이어의 RGB 색상 오프셋을 설정하고, 렌더링 모드를 RGB 모드로 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name    | Type   | Description            |
| ------- | ------ | ---------------------- |
| offsetR | number | 빨간색(R) 채널 오프셋 (0\~255) |
| offsetG | number | 초록색(G) 채널 오프셋 (0\~255) |
| offsetB | number | 파란색(B) 채널 오프셋 (0\~255) |

* Return
  * true: 설정 성공
  * false: 포인트 클라우드 레이어가 아닌 경우
* Note
  * alpha 값은 항상 255로 고정됨
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
let layer = layerList.nameAtLayer("PointCloudLayer");
layer.setPointCloudRenderModeRGB(255, 100, 100);
```
{% endtab %}
{% endtabs %}

### setPointCloudRenderModeIntensity(min, max, useColor) → boolean

> 포인트 클라우드 레이어의 Intensity 기반 렌더링 모드를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type    | Description                 |
| -------- | ------- | --------------------------- |
| min      | number  | Intensity 최소값               |
| max      | number  | Intensity 최대값               |
| useColor | boolean | true: 컬러맵 적용, false: 그레이스케일 |

* Return
  * true: 설정 성공
  * false: 포인트 클라우드 레이어가 아닌 경우
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
let layer = layerList.nameAtLayer("PointCloudLayer");
layer.setPointCloudRenderModeIntensity(0.0, 255.0, true);
```
{% endtab %}
{% endtabs %}

### setPointCloudRenderModeAltitude(min, max, useColor) → boolean

> 포인트 클라우드 레이어의 고도 기반 렌더링 모드를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type    | Description                     |
| -------- | ------- | ------------------------------- |
| min      | number  | 고도 컬러맵 적용 범위 최소값 (meter 단위).    |
| max      | number  | 고도 컬러맵 적용 범위 최대값 (meter 단위).    |
| useColor | boolean | true: 컬러맵 적용, false: 그레이스케일 적용. |

* Return
  * true: 설정 성공
  * false: 포인트 클라우드 레이어가 아닌 경우
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
let layer = layerList.nameAtLayer("PointCloudLayer");
layer.setPointCloudRenderModeAltitude(0.0, 100.0, true);
```
{% endtab %}
{% endtabs %}

### setPointCloudPointSize(size) → boolean

> 포인트 클라우드 객체의 점 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description               |
| ---- | ------ | ------------------------- |
| size | number | 점 크기(0.001 이상, meter 단위). |

* Return
  * true: 설정 성공
  * false: 잘못된 값이거나 포인트 클라우드 레이어가 아닌 경우
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
let layer = layerList.nameAtLayer("PointCloudLayer");
layer.setPointCloudPointSize(0.05);
```
{% endtab %}
{% endtabs %}

### getPickInfoAtView(lineFrom, lineTo) → object

> 주어진 뷰 라인(lineFrom → lineTo)을 기준으로 해당 레이어 내 피킹된 객체 정보를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description   |
| -------- | ----------------------------------- | ------------- |
| lineFrom | [JSVector3D](../core/jsvector3d.md) | 피킹 라인의 시작 좌표. |
| lineTo   | [JSVector3D](../core/jsvector3d.md) | 피킹 라인의 끝 좌표.  |

* Return
  * `object` : 피킹 성공 시 위치 및 객체 정보 반환
  * `null` : 피킹 실패 시
* 반환 객체 구조

| Key       | Type                                | Description         |
| --------- | ----------------------------------- | ------------------- |
| position  | [JSVector3D](../core/jsvector3d.md) | 피킹된 좌표 위치.          |
| objectKey | string                              | 피킹된 객체의 고유 키.       |
| layerName | string                              | 피킹된 객체가 포함된 레이어 이름. |

* Note
  * ~~현재 타일 기반 레이어에서만 동작합니다.~~
  * 카메라의 뷰 영역 내부인 객체만 피킹합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let from = new Module.JSVector3D(127.0, 37.5, 100.0);
let to = new Module.JSVector3D(127.0, 37.5, 0.0);

let pickInfo = layer.getPickInfoAtView(from, to);

if (pickInfo) {
    console.log("Position:", pickInfo.position);
    console.log("Object Key:", pickInfo.objectKey);
    console.log("Layer Name:", pickInfo.layerName);
}
```
{% endtab %}
{% endtabs %}

### getPickInfo(lineFrom, lineTo) → object

> 주어진 뷰 라인(lineFrom → lineTo)을 기준으로 해당 레이어 내 피킹된 객체 정보를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description   |
| -------- | ----------------------------------- | ------------- |
| lineFrom | [JSVector3D](../core/jsvector3d.md) | 피킹 라인의 시작 좌표. |
| lineTo   | [JSVector3D](../core/jsvector3d.md) | 피킹 라인의 끝 좌표.  |

* Return
  * `object` : 피킹 성공 시 위치 및 객체 정보 반환
  * `null` : 피킹 실패 시
* 반환 객체 구조

| Key       | Type                                | Description         |
| --------- | ----------------------------------- | ------------------- |
| position  | [JSVector3D](../core/jsvector3d.md) | 피킹된 좌표 위치.          |
| objectKey | string                              | 피킹된 객체의 고유 키.       |
| layerName | string                              | 피킹된 객체가 포함된 레이어 이름. |

* Note
  * ~~현재 타일 기반 레이어에서만 동작합니다.~~
  * 카메라의 뷰 영역에 상관없이 피킹합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let from = new Module.JSVector3D(127.0, 37.5, 100.0);
let to = new Module.JSVector3D(127.0, 37.5, 0.0);

let pickInfo = layer.getPickInfo(from, to);

if (pickInfo) {
    console.log("Position:", pickInfo.position);
    console.log("Object Key:", pickInfo.objectKey);
    console.log("Layer Name:", pickInfo.layerName);
}
```
{% endtab %}
{% endtabs %}

### setTileLoadCallback(callback) → boolean

> 타일 로딩 완료 시 호출될 콜백 함수를 설정합니다.\
> 타일 기반 레이어(`ELST_PLANET_TILE`)에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type     | Description        |
| -------- | -------- | ------------------ |
| callback | function | 타일 로딩 시 호출될 콜백 함수. |

* Return
  * `true` : 설정 성공
  * `false` : 설정 실패
    * 비타일 레이어일 경우
    * 월드가 초기화되지 않은 경우
* Note
  * 콜백 함수는 JavaScript 함수 객체로 전달되어야 합니다.
  * 콜백은 각 타일 로드 완료 시마다 실행됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let layer = Module.getLayerByName("MyTileLayer");
layer.setTileLoadCallback(function() {
    console.log("Tile loaded!");
});
```
{% endtab %}
{% endtabs %}

### addTileInObject(tileInfo, object) → boolean

> 지정한 타일 위치에 객체를 수동으로 삽입합니다.\
> 지구본 타일 기반 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                              | Description                   |
| -------- | --------------------------------- | ----------------------------- |
| tileInfo | object                            | 타일 위치 정보 `{level, idx, idy}`. |
| object   | [JSObject](../object/jsobject.md) | 삽입할 객체.                       |

* Return
  * `true` : 객체 추가 성공
  * `false` : 실패
    * 비타일 기반 레이어
    * 유효하지 않은 오브젝트
    * RTT(Render to Texture) 객체
    * 이미 등록된 객체
    * tileInfo 누락 또는 오류
    * 타일 존재하지 않음
* Note
  * 해당 타일에 객체를 삽입하고 렌더링을 갱신합니다.
{% endtab %}

{% tab title="Template" %}
```javascript;
layer.addTileInObject(tileInfo, obj);
```
{% endtab %}
{% endtabs %}

### setTileInObjectEnd(tileInfo) → boolean

> 지정한 타일의 객체 수동 삽입 종료를 명시적으로 설정합니다.\
> 객체 수동 삽입 이후 타일의 요청 플래그를 비활성화합니다.\
> 지구본 타일 기반 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type   | Description                   |
| -------- | ------ | ----------------------------- |
| tileInfo | object | 타일 위치 정보 `{level, idx, idy}`. |

* Return
  * `true` : 설정 성공
  * `false` : 실패
    * 비타일 기반 레이어
    * tileInfo 누락 또는 오류
    * 타일 존재하지 않음
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setTileInObjectEnd(tileInfo);
```
{% endtab %}
{% endtabs %}

### setUserTileLoadCallback(callback) → boolean

> 사용자 레이어 또는 콜백 레이어에서 타일 로드 시 사용자 정의 콜백 함수를 등록합니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type     | Description   |
| -------- | -------- | ------------- |
| callback | function | 사용자 정의 콜백 함수. |

* Return
  * `true`: 콜백 등록 성공
  * `false`: 콜백 등록 실패
    * 레이어 타입이 사용자 또는 콜백 타입이 아닌 경우
    * 지구본 타일 기반 레이어가 아닌 경우
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
let layer = layerList.createLayer("UserCallbackLayer");

layer.setUserTileLoadCallback(function(...) {
    ...
});
```
{% endtab %}
{% endtabs %}

### getObjectHeight(), setObjectHeight(height)

> 애니메이션 오브젝트에서 레이어에 포함된 객체의 높이 기준값을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description    |
| ------ | ------ | -------------- |
| height | number | 객체 기준 높이 값(m). |

* Note
  * 객체 생성 시 높이 보정이 필요한 경우 사용합니다.
  * 값 변경 시, 가시화 정보가 즉시 갱신됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
var layerList = new Module.JSLayerList(true);
var layer = layerList.createLayer("MyLayer");
layer.setObjectHeight(30.0);
```
{% endtab %}
{% endtabs %}

### SetPointCloudRenderModeIntensity(intensityMin, intensityMax, colorMode) → boolean

> 포인트 클라우드의 intensity 기반 렌더링 모드를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name         | Type    | Description                                   |
| ------------ | ------- | --------------------------------------------- |
| intensityMin | float   | intensity 값의 최소 범위                            |
| intensityMax | float   | intensity 값의 최대 범위                            |
| colorMode    | boolean | `true`: 색상 모드 사용, `false`: intensity 단일 색상 사용 |

* Return
  * `true`: 설정 성공
  * `false`: 설정 실패 (레이어 타입이 포인트 클라우드가 아닐 경우 등)
* Description
  * 포인트 클라우드 레이어에 대해 intensity 기반 렌더링 모드를 설정합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSLayer : Module.getLayerByName("MyPointCloud")
};

// intensity 범위 50 ~ 200, 색상 모드 사용
var success = API.JSLayer.SetPointCloudRenderModeIntensity(50.0, 200.0, true);

if (!success) {
    console.error("설정 실패: 해당 레이어는 포인트 클라우드 타입이 아닙니다.");
}
```
{% endtab %}
{% endtabs %}

### getTileLODMaxLevel(), setTileLODMaxLevel(level) → number

> 드론 LOD(Tile LOD Model) 레이어에서 가시화할 최대 레벨을 설정합니다.
>
> 드론 LOD 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description        |
| ----- | ------ | ---------------------- |
| level | number | 최대 가시화 레벨.      |

* Return(getTileLODMaxLevel)
  * number : 설정된 최대 레벨.
  * -999 : 반환 실패.
  * 실패 조건
    * 레이어가 없는 경우.
    * 드론 LOD 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setTileLODMaxLevel(15);
let maxLevel = layer.getTileLODMaxLevel();
```
{% endtab %}
{% endtabs %}

### getMaxGeometricError(), setMaxGeometricError(value) → number

> 3D Tiles 레이어의 최대 기하 오차(Maximum Screen Space Error)를 설정합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                                       |
| ----- | ------ | ------------------------------------------------------ |
| value | number | 최대 기하 오차값(1.0 미만 입력 시 기본값으로 초기화).  |

* Return(getMaxGeometricError)
  * number : 설정된 최대 기하 오차값.
  * 0.0 : 3D Tiles 레이어가 아니거나 설정되지 않은 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setMaxGeometricError(16.0);
let error = layer.getMaxGeometricError();
```
{% endtab %}
{% endtabs %}

### getLayerStyle(), setLayerStyle(style) → object

> 레이어의 POI 스타일(크기, 페이드 옵션)을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name                                                          | Type                | Description                                     |
| --------------------------------------------------------------- | -------------------- | ---------------------------------------------------- |
| style                                                           | object               | 레이어 스타일 옵션.                                    |
| ↳ poi                                                           | object (optional)    | POI 스타일 옵션.                                       |
| &nbsp;&nbsp;• poi.scaleable.activate                            | boolean (optional)   | 거리에 따른 크기 조절 사용 여부.                        |
| &nbsp;&nbsp;• poi.scaleable.range.min/max                       | number (optional)    | 크기 조절 적용 거리 범위.                               |
| &nbsp;&nbsp;• poi.scaleable.minPixel.x/y                        | number (optional)    | 최소 픽셀 크기.                                        |
| &nbsp;&nbsp;• poi.scaleable.tiltRange.activate/minAngle/maxAngle | (optional)            | 카메라 tilt 각도에 따른 크기 조절 옵션.                 |
| &nbsp;&nbsp;• poi.fadeable.activate                             | boolean (optional)   | 거리에 따른 페이드 사용 여부.                           |
| &nbsp;&nbsp;• poi.fadeable.range.min/max                        | number (optional)    | 페이드 적용 거리 범위.                                 |
| &nbsp;&nbsp;• poi.fadeable.minAlpha                             | number (optional)    | 페이드 최소 투명도.                                    |
| &nbsp;&nbsp;• poi.fadeable.tiltRange.activate/minAngle/maxAngle | (optional)            | 카메라 tilt 각도에 따른 페이드 옵션.                    |

* Return(getLayerStyle)
  * object : 현재 설정된 레이어 스타일(위 poi 옵션 구조와 동일).
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setLayerStyle({
    poi: {
        scaleable: {
            activate: true,
            range: { min: 100, max: 5000 }
        },
        fadeable: {
            activate: true,
            range: { min: 3000, max: 5000 },
            minAlpha: 0.0
        }
    }
});

let style = layer.getLayerStyle();
console.log(style.poi.scaleable.activate);
```
{% endtab %}
{% endtabs %}

## Type Definitions

#### WMSOptions

> WMS 레이어의 기본 생성 옵션.

| Name         | Type                                                      | Attributes | Default   | Description          |
| ------------ | --------------------------------------------------------- | ---------- | --------- | -------------------- |
| url          | string                                                    |            |           | GeoServer 요청 url.    |
| layer        | string                                                    |            |           | GeoServer 요청 레이어 명칭. |
| minimumLevel | number                                                    | optional   | 0         | WMS 가시화 최소 레벨.       |
| maximumLevel | number                                                    | optional   | 15        | WMS 가시화 최대 레벨.       |
| tileSize     | number                                                    | optional   | 256       | WMS 요청 이미지 크기.       |
| crs          | string                                                    | optional   | EPSG:4326 | WMS 등록 레이어 원본 좌표계.   |
| parameters   | [WMSOptions.SubOptions](jslayer.md#wmsoptions.suboptions) | optional   |           | WMS 요청 스타일, 속성 정보..  |

#### WMSOptions.SubOptions

> WMS 레이어 추가 생성 옵션.
>
> 추가 옵션은 parameters 구성 시 키, 벨류로 추가하며 자동으로 요청 url 구성에 포함.
>
> ex) style 옵션 등.

| Name        | Type   | Attributes | Default   | Description                  |
| ----------- | ------ | ---------- | --------- | ---------------------------- |
| version     | string | optional   | 1.1.0     | GeoServer 버전.                |
| service     | string | optional   | WMS       | GeoServer 요청 타입.             |
| request     | string | optional   | GetMap    | GeoServer 요청 지도 타입.          |
| format      | string | optional   | image/png | GeoServer 요청 이미지 타입.         |
| transparent | string | optional   | TRUE      | Transparency 이미지 요청 시 투명 옵션. |

#### WMTSOption.Server

> WMTS 레이어 서버 정보.

| Name          | Type                                             | Attributes | Default | Description                        |
| ------------- | ------------------------------------------------ | ---------- | ------- | ---------------------------------- |
| url           | string                                           |            |         | 요청 서버 URL 구성요소.                    |
| vworldTileSet | boolean                                          | optional   | false   | 브이월드 타일구조로 타일링일 경우(true).          |
| projection    | string                                           |            |         | 지도 원본 EPSG 코드.                     |
| tileExtent    | [Rect2D](../etc/tag-list.md#rect2d-style-type)   |            |         | 지도 타일링 영역 설정(좌하단, 우상단).            |
| gridSubset    | [Range2D](../etc/tag-list.md#range2d-style-type) | optional   | 지구전체 영역 | 데이터 최소/최대 영역 설정(좌하단, 우상단).         |
| tileSize      | number                                           | optional   | 256     | 타일에 가시화 이미지 사이즈 설정.                |
| resolutions   | array(number)                                    |            |         | 타일링 해상도.                           |
| matrixIds     | array(number)                                    |            |         | 타일링 레벨(해상도와 매칭).                   |
| indexOrder    | boolean                                          | optional   | true    | 타일 인덱싱 기준점(false: 좌하단, true: 좌상단). |
| serviceLevel  | [Range2D](../etc/tag-list.md#range2d-style-type) |            |         | 최소, 최대 이미지 가시화 레벨 설정.              |

#### WMTSOption.User

> WMTS 레이어 서비스 정보.

| Name       | Type    | Attributes | Default | Description                                 |
| ---------- | ------- | ---------- | ------- | ------------------------------------------- |
| zeroLevel  | number  | optional   | 2       | 서로 다른 타일구조의 매칭을 위한 보간 값(높은값일 수록 요청수가 많아진다). |
| quality    | string  | optional   | 256     | 이미지 해상도.                                    |
| iscrack    | boolean | optional   | false   | 타일링시 크랙이 발생 할 경우(true).                     |
| crackvalue | number  | optional   | 1000    | 크랙발생시 보간값(보간값 만큼 이미지를 더 생성한다).              |
