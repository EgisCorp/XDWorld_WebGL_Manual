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
| object    | [JSObject](../object/jsobject3d.md) | Add created object |
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

### createGaussianSplat(objectKey) → [JSGaussianSplat](../object/jsgaussiansplat.md)

> 3D Gaussian Splatting 객체([JSGaussianSplat](../object/jsgaussiansplat.md))를 생성하여 이 레이어에 등록합니다.
>
> 서비스 레이어에서 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description     |
| :-------- | ------ | --------------- |
| objectKey | string | 객체 고유 명칭. |

-   Return
    -   [JSGaussianSplat](../object/jsgaussiansplat.md): 생성 성공(동일한 키가 이미 있으면 기존 객체를 반환).
    -   null: 레이어가 초기화되지 않았거나, 동일한 키의 객체가 다른 타입으로 이미 존재하는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var splat = layer.createGaussianSplat("splat_01");
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

### getObjectTileInfo(objkey) → object

> 객체 고유 명칭으로 해당 객체가 소속된 타일의 정보(레벨, 인덱스)를 반환합니다.
>
> 선택한 객체의 타일 정보를 표출할 때 사용합니다.
>
> 지구본 타일 기반 레이어(`ELST_PLANET_TILE`)에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description |
| ------ | ------ | ----------- |
| objkey | string | 객체 고유 명칭    |

* Return
  * object : 반환 성공.
    * | Name  | Type   | Description |
      | ----- | ------ | ----------- |
      | level | number | 타일 레벨.     |
      | idx   | number | 타일 인덱스(idx). |
      | idy   | number | 타일 인덱스(idy). |
  * null : 반환 실패.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 레이어가 없는 경우.
    * 지구본 타일 기반 레이어가 아닌 경우.
    * 입력값(objkey)을 갖는 객체가 레이어에 등록되어 있지 않은 경우(타일 로드 시점에 등록되므로 아직 로드되지 않은 타일의 객체는 조회되지 않음).
{% endtab %}

{% tab title="Template" %}
```javascript
let info = layer.getObjectTileInfo("BUILDING_001");
if (info) {
    console.log(info.level, info.idx, info.idy);
}
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

### indexAtObject(index) → [JSObject](../object/jsobject3d.md)

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
  * [JSObject](../object/jsobject3d.md) : 반환 성공.
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

### keyAtObject(name) → [JSObject](../object/jsobject3d.md)

> 사용자 레이어에 포함된 객체를 반환합니다.
>
> 사용자 레이어에 포함된 객체는 목록으로 관리하고 객체 고유 명칭과 입력 변수 name 비교 후 만족하는 객체를 반환합니다.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 고유 명칭.   |

* Return
  * [JSObject](../object/jsobject3d.md) : 반환 성공.
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
| object | [JSObject](../object/jsobject3d.md) | 객체.         |

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
> [setRecoverHsvValue](jslayer.md#setrecoverhsvvalue-hue-saturation-value-boolean) 설정된 색상 채널을 가시화 유무를 설정합니다.
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
| objects | array([JSObject](../object/jsobject3d.md))  | 추가할 객체 배열.    |

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

> [setObjectColorListByKey](jslayer.md#setobjectcolorlistbykey-simplecolormode-color-objectkeylist-boolean) 로 설정된 객체 색상 목록을 초기화하고, 색상이 변경된 건물(Real3D) 객체를 원래 색상으로 되돌립니다.

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
| ↳ autoTerrainFit      | boolean (optional, 기본값 false) | 지형 자동 맞춤 사용 여부. [setTileAutoTerrainFit](jslayer.md#settileautoterrainfit-enable)와 같은 스위치입니다. |
| ↳ Authorization       | boolean (optional, 기본값 false) | 인증 헤더 사용 여부.                                  |

* Return
  * true : 로드 요청 성공.
  * false : 실패.
  * 실패 조건
    * 3D Tiles 레이어가 아닌 경우.
    * option이 null/undefined인 경우.
    * url이 없는 경우.
* Note
  * `autoTerrainFit`의 기본값이 false이므로 기존 호출의 동작은 바뀌지 않습니다. 로드 직후 측정을 처음부터 시작합니다.
  * 정점→batchId 대응(`_BATCHID`)이 있는 배치 테이블을 가진 타일(b3dm)은 `discardVertexData`가 true여도 정점을 남깁니다(속성만 있고 대응이 없는 표는 해당하지 않음). 정점이 GPU로 올라간 뒤 지워지면 피킹과 feature 선택이 불가능해지기 때문입니다([getPickInfo](jslayer.md#getpickinfo-linefrom-lineto-object)의 `batchId`, [extractTileFeature](jslayer.md#extracttilefeature-parameter-jspolygon)). 이렇게 사용자 설정을 덮어쓴 타일 수는 [get3DTilesDiagnostics](jslayer.md#get3dtilesdiagnostics-object)의 `discardKeptForBatch`로 확인할 수 있습니다.
  * 루트 URL의 호스트가 `tile.googleapis.com`이면 구글 레이어로 판별되어 [setFillOnlyHorizonFactor](jslayer.md#getfillonlyhorizonfactor-setfillonlyhorizonfactor-factor-number-boolean)와 [setFillSkirtCut](jslayer.md#getfillskirtcut-setfillskirtcut-cut-boolean)의 기본값이 켜집니다.
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

### getReal3dLightFlat(), setReal3dLightFlat(value) → number

> Real3D(건물) 레이어 재질의 조명 반응 세기를 설정합니다.
>
> 0은 조명을 그대로 적용하고, 1은 조명을 전혀 적용하지 않습니다. 파사드 텍스처에는 이미 음영이 구워져 있어 조명을 그대로 곱하면 어두워지고, 조명을 완전히 끄면(`setLighting(false)`) 건물이 납작해 보이므로 그 사이 값을 고르기 위한 옵션입니다. 0.3 ~ 0.5에서 입체감은 유지하면서 파사드가 덜 어두워집니다.
>
> Real3D 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                                                          |
| ----- | ------ | -------------------------------------------------------------------- |
| value | number | 조명 반응 세기(0.0 ~ 1.0, 기본값 0.0). 범위를 벗어난 값은 0.0 ~ 1.0으로 보정합니다. |

* Return(getReal3dLightFlat)
  * number : 설정된 값.
  * 0.0 : 월드가 초기화되지 않았거나 레이어가 없거나 타일 구조 레이어가 아닌 경우.
* Return(setReal3dLightFlat)
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 레이어가 없는 경우.
    * 타일 구조 레이어가 아닌 경우.
    * Real3D 레이어가 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setReal3dLightFlat(0.4);
let flat = layer.getReal3dLightFlat();
```
{% endtab %}
{% endtabs %}

### setImpostorEnable(enable) → boolean

> 레이어의 Impostor LOD를 켜거나 끕니다.
>
> Impostor LOD는 화면에서 작아진 원거리 건물을 실제 메시 대신 미리 구워 둔 스프라이트(빌보드)로 그려 렌더 부하를 줄이는 기능입니다. 건물의 화면 크기가 [setImpostorSwitchPixel](jslayer.md#setimpostorswitchpixel-pixel-boolean) 값보다 작아지면 임포스터로 전환됩니다.
>
> 기본값은 꺼짐이며, 꺼진 상태에서는 기존 렌더 경로와 완전히 동일하게 동작합니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type    | Description                           |
| ------ | ------- | ------------------------------------- |
| enable | boolean | Impostor LOD 사용 여부(true: 켜기, false: 끄기). |

* Return
  * true : 설정 성공.
  * false : 옥트리 구조 레이어가 아니거나 레이어가 없는 경우.
* Note
  * 이 함수는 두 가지를 설정합니다.
    * 시설물(Real3D 타일 객체) 경로의 전역 Impostor 정책: 호출한 레이어 종류와 관계없이 항상 켜거나 끕니다. 따라서 Real3D 등 타일 레이어에서 호출하면 `false`를 반환하지만 전역 정책은 변경됩니다.
    * 옥트리 구조 레이어(폴리헤드론 객체 등)의 레이어 단위 Impostor: 옥트리 구조 레이어에서만 켜거나 끕니다.
  * 임포스터는 폴리헤드론과 Real3D 객체만 대상이며, 다음의 경우 전환하지 않고 메시로 그립니다.
    * 카메라 시선이 수평에서 45° 이상 아래를 향하는 경우(내려다보는 뷰).
    * 선택(하이라이트)된 객체.
    * 정점 수가 [setImpostorMinVertex](jslayer.md#setimpostorminvertex-count-boolean) 값 미만인 단순한 형상.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setImpostorEnable(true);
layer.setImpostorSwitchPixel(48);
layer.setImpostorMinVertex(100);
```
{% endtab %}
{% endtabs %}

### setImpostorSwitchPixel(pixel) → boolean

> Impostor로 전환할 화면 픽셀 크기를 설정합니다.
>
> 건물의 화면 투영 크기(가로·세로 중 큰 변)가 이 값보다 작아지면 임포스터로 바뀝니다. 거리(m)가 아니라 화면 픽셀 기준이라 화각, 해상도, 건물 높이에 자동으로 맞춰집니다.
>
> [setImpostorEnable](jslayer.md#setimpostorenable-enable-boolean)로 Impostor LOD를 켠 뒤 호출합니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                                                         |
| ----- | ------ | ------------------------------------------------------------------- |
| pixel | number | 전환 화면 픽셀 크기(16 ~ 128). 범위를 벗어난 값은 16 ~ 128로 보정합니다. |

* Return
  * true : 설정 성공.
  * false : 옥트리 구조 레이어가 아니거나, 해당 레이어의 Impostor가 켜져 있지 않은 경우.
* Note
  * 기본값은 옥트리 구조 레이어 24, 시설물(Real3D 타일 객체) 전역 정책 64입니다.
  * `false`를 반환해도 시설물 전역 정책(켜져 있는 경우)과 임포스터 아틀라스 설정에는 값이 반영됩니다. 레이어 단위 값은 옥트리 구조 레이어의 Impostor가 켜져 있을 때만 반영됩니다.
  * 값이 64를 넘으면 아틀라스가 큰 건물용 셀(96/128px)을 포함하는 배분으로 전환되어 큰 건물이 64px 셀로 강등되지 않지만, 페이지당 수용 건물 수가 줄어듭니다(소스 주석 기준 202채 → 145채). 64 이하로 되돌리면 원래 배분으로 복귀하며, 양쪽 모두 임포스터를 전부 다시 굽습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setImpostorEnable(true);
layer.setImpostorSwitchPixel(48);
```
{% endtab %}
{% endtabs %}

### setImpostorMinVertex(count) → boolean

> Impostor로 대체할 최소 정점 수를 설정합니다.
>
> 이 값보다 정점이 적은 단순한 형상(큐브 등)은 메시로 그려도 삼각형이 몇 개뿐이라 이득이 없고 아틀라스 자리만 차지해 복잡한 건물이 밀리므로 임포스터로 바꾸지 않습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                                              |
| ----- | ------ | -------------------------------------------------------- |
| count | number | 최소 정점 수(기본값 100). 0이면 조건을 끔. 음수는 0으로, 소수는 버림 처리. |

* Return
  * true : 설정 성공.
  * false : 옥트리 구조 레이어가 아니거나, 해당 레이어의 Impostor가 켜져 있지 않은 경우.
* Note
  * `false`를 반환해도 시설물(Real3D 타일 객체) 전역 정책이 켜져 있으면 값이 반영됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setImpostorEnable(true);
layer.setImpostorMinVertex(200);
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

> [setDefineMeshColorByObjectKey](jslayer.md#setdefinemeshcolorbyobjectkey-checkstring-comparetype-color-issimplemode-boolean), [setDefineEdgeLineColorByObjectKey](jslayer.md#setdefineedgelinecolorbyobjectkey-checkstring-comparetype-color-boolean), [setDefineVisibleByFileName](jslayer.md#setdefinevisiblebyfilename-checkstring-comparetype-visible-boolean) 로 정의된 스타일 조건을 모두 초기화합니다.

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
      | object | [JSObject](../object/jsobject3d.md)      | 객체.           |
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
  * [setPointCloudPointSize](jslayer.md#getpointcloudpointsize-setpointcloudpointsize-size-number-boolean) 와 유사하나, 3D Tiles 레이어 전용으로 동작합니다.
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

### getPointCloudPointSize(), setPointCloudPointSize(size) → number, boolean

> 포인트 클라우드 객체의 점 크기를 조회하거나 설정합니다.
>
> 포인트 클라우드 레이어와 3D Tiles 레이어에서 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description               |
| ---- | ------ | ------------------------- |
| size | number | 점 크기(0.001 이상, meter 단위). |

* Return(getPointCloudPointSize)
  * number : 레이어에 설정된 점 크기(`setPointCloudPointSize`로 마지막에 설정한 값. 설정한 적이 없으면 기본값 3.0).
  * 0.0 : 레이어가 없거나 포인트 클라우드 레이어/3D Tiles 레이어가 아닌 경우(값 0과 구분되지 않음).
* Return(setPointCloudPointSize)
  * true: 설정 성공
  * false: 잘못된 값(0.001 미만)이거나 포인트 클라우드 레이어/3D Tiles 레이어가 아닌 경우
* Note
  * `getPointCloudPointSize`는 레이어의 점 크기 옵션 값을 읽습니다. 3D Tiles 레이어 전용 [setPointCloudeSize](jslayer.md#setpointcloudesize-size)는 이 값을 바꾸지 않으므로 그 함수로 설정한 크기는 이 getter에 반영되지 않습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
let layer = layerList.nameAtLayer("PointCloudLayer");
layer.setPointCloudPointSize(0.05);
console.log(layer.getPointCloudPointSize()); // 0.05
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
| tileKey   | string                              | (3D Tiles 레이어 전용) 맞힌 타일의 콘텐츠 URL. [extractTileFeature](jslayer.md#extracttilefeature-parameter-jspolygon)가 타일을 다시 찾는 핸들입니다. |
| batchId   | number \| null                      | (3D Tiles 레이어 전용) 맞힌 feature의 배치 테이블 행 번호. 타일에 배치 테이블(b3dm)이 없거나 맞힌 삼각형이 어느 feature 범위에도 들지 않으면 null. |
| properties | object                             | (3D Tiles 레이어 전용) `batchId`가 정수일 때만 포함. 배치 테이블 속성 이름 → 문자열 값. |

* Note
  * 카메라의 뷰 영역 내부인 객체만 피킹합니다.
  * 3D Tiles 레이어에서 glTF 타일(`s3dGltf`) 객체를 맞혔을 때만 `tileKey`, `batchId`, `properties`가 추가됩니다. 다른 레이어 타입의 반환 형식은 그대로입니다. `properties.batchId`처럼 데이터 속성에 같은 이름이 있어도 행 번호는 최상위 `batchId`입니다.
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
| tileKey   | string                              | (3D Tiles 레이어 전용) 맞힌 타일의 콘텐츠 URL. [extractTileFeature](jslayer.md#extracttilefeature-parameter-jspolygon)가 타일을 다시 찾는 핸들입니다. |
| batchId   | number \| null                      | (3D Tiles 레이어 전용) 맞힌 feature의 배치 테이블 행 번호. 타일에 배치 테이블(b3dm)이 없거나 맞힌 삼각형이 어느 feature 범위에도 들지 않으면 null. |
| properties | object                             | (3D Tiles 레이어 전용) `batchId`가 정수일 때만 포함. 배치 테이블 속성 이름 → 문자열 값. |

* Note
  * 카메라의 뷰 영역에 상관없이 피킹합니다.
  * 3D Tiles 레이어에서 glTF 타일(`s3dGltf`) 객체를 맞혔을 때만 `tileKey`, `batchId`, `properties`가 추가됩니다. 다른 레이어 타입의 반환 형식은 그대로입니다. `properties.batchId`처럼 데이터 속성에 같은 이름이 있어도 행 번호는 최상위 `batchId`입니다.
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

### extractTileFeature(parameter) → [JSPolygon](../object/jspolygon.md)

> 3D Tiles(b3dm) 레이어에서 feature 하나의 기하만 떼어 독립 폴리곤 객체로 추출합니다.
>
> [getPickInfo](jslayer.md#getpickinfo-linefrom-lineto-object) / [getPickInfoAtView](jslayer.md#getpickinfoatview-linefrom-lineto-object)의 `tileKey`, `batchId`를 그대로 넘깁니다. 복사이지 이동이 아니므로 원본 타일은 그대로입니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name      | Type   | Description                                                                 |
| --------- | ------ | --------------------------------------------------------------------------- |
| parameter | object | 추출 대상. `{ tileKey: string, batchId: number }` 객체.                      |
| ↳ tileKey | string | 피킹 결과의 `tileKey`(맞힌 타일의 콘텐츠 URL).                                |
| ↳ batchId | number | 피킹 결과의 최상위 `batchId`. 0 이상 4294967295 미만의 정수. `properties.batchId`(속성 컬럼)가 아닙니다. |

* Return
  * [JSPolygon](../object/jspolygon.md) : 추출된 객체. 어느 레이어에도 들어 있지 않으므로 원하는 사용자 레이어에 [addObject](jslayer.md#addobject-object-level)로 추가해 사용합니다. 레이어에 넣지 않으면 해제되지 않습니다.
  * `null` : 실패. 콘솔에 사유가 출력됩니다.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
    * `parameter`가 객체가 아니거나 `tileKey`(문자열), `batchId`(숫자)가 없거나 형식이 틀린 경우(피킹 결과의 `batchId`가 null이면 맞힌 타일에 배치 테이블이 없는 것입니다).
    * `batchId`가 NaN, 음수, 소수, 4294967295 이상인 경우.
    * `tileKey`에 해당하는 타일이 없는 경우(아직 받지 못했거나 이미 해제됨. 피킹 직후에 호출하십시오).
    * 타일에 배치 테이블이 없는 경우.
    * 그 `batchId`의 삼각형이 하나도 없는 경우.
    * 그 `batchId`의 정점이 이미 지워진 경우(`discardVertexData`로 정점이 지워진 타일. 일부만 추출하지 않고 통째로 거부합니다).
    * 배치 테이블의 정점 구간이 면의 정점 수를 넘어 표와 기하가 어긋난 경우.
* Note
  * 한 feature가 여러 (메시, 면)에 걸치면 전부 모읍니다. 세 정점이 모두 그 feature의 정점인 삼각형만 가져갑니다.
  * 정점은 월드(ECEF) 좌표로 구워지고 객체 중심 기준 상대 좌표 + 경계 상자로 만들어집니다. 렌더 위치는 호출 시점에 원본 타일이 그려진 자리와 같으며, 이후 타일이 다시 적재돼도 추출 객체는 따라가지 않습니다.
  * 텍스처는 복사하지 않습니다(색, 알파, 조명 속성만 복사). [setTileHeightOffset](jslayer.md#gettileheightoffset-settileheightoffset-meter-number)과 지형 자동 맞춤의 보정도 적용하지 않으며 데이터의 실제 위치로 만들어집니다.
  * 같은 `tileKey`를 가진 타일이 여럿이면(서로 다른 중첩 타일셋이 같은 상대경로를 쓴 경우) 경고를 출력하고 먼저 찾은 타일을 사용합니다.
  * 객체 키는 `tileKey + "#" + batchId` 형식이며, 100자 이상이면 `tile_<타일키 해시>#batchId`로 줄어듭니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
let layer = layerList.nameAtLayer("3dtiles_layer");

// 1) 피킹으로 feature 정보 얻기
let info = layer.getPickInfo(from, to);
if (info && info.batchId !== null && info.batchId !== undefined) {
    console.log(info.tileKey, info.batchId, info.properties);

    // 2) feature 추출
    let polygon = layer.extractTileFeature({
        tileKey: info.tileKey,
        batchId: info.batchId
    });

    // 3) 원하는 사용자 레이어에 추가
    if (polygon) {
        let userLayerList = new Module.JSLayerList(true);
        let userLayer = userLayerList.createLayer("extracted");
        userLayer.addObject(polygon, 0);
    }
}
```
{% endtab %}
{% endtabs %}

### getSelectedTileFeature() → [TileFeature](jslayer.md#tilefeature)

> 엔진이 지금 이 3D Tiles 레이어에서 선택하고 있는 feature를 반환합니다. (읽기 전용)
>
> [getPickInfo](jslayer.md#getpickinfo-linefrom-lineto-object)로 따로 피킹하면 광선이 달라 클릭한 건물과 다른 건물이 나올 수 있으므로, "엔진이 실제로 고른 것"을 보여 줄 때 사용합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * [TileFeature](jslayer.md#tilefeature) : 선택된 feature(`tileKey`, `batchId`, `properties`). `batchId`는 항상 정수입니다.
  * `null` : 아래 경우.
    * 월드가 초기화되지 않았거나 3D Tiles 레이어가 아닌 경우.
    * 이 레이어에서 선택된 타일이 없는 경우.
    * 선택은 있지만 feature 선택이 아닌 경우(배치 테이블이 없는 타일, 광선이 빗나감, JS `setSelectObject`로 한 선택 - 그 타일은 통째로 선택된 것).
    * 선택을 들던 타일이 해제됐고(LOD 축출, 보유 용량 상한) 그 건물을 담은 타일이 아직 그려지지 않은 경우. 그 타일이 그려지면 선택을 넘겨받아 다시 값을 돌려줍니다.
* Note
  * 여러 타일이 선택돼 있으면(shift+클릭) 가장 나중에 선택된 feature를 반환합니다.
  * **`tileKey`와 `batchId`는 "선택을 들고 있는 타일" 기준입니다.** 선택은 LOD가 바뀌어도 같은 건물에 유지되지만(자세한 내용은 [setTileFeatureIdentityKey](jslayer.md#gettilefeatureidentitykey-settilefeatureidentitykey-key-string)), 선택을 들고 있는 타일은 클릭한 때의 타일 그대로라 지금 그려지지 않는 부모나 거친 조상일 수 있습니다. 그래서 같은 건물에 `getPickInfo`를 걸어 얻은 `tileKey`/`batchId`와 다를 수 있습니다. 건물의 정체성은 행 번호(`batchId`, 타일 레벨마다 바뀝니다)가 아니라 `properties`의 정체성 속성(기본 `name`)으로 판단하십시오.
{% endtab %}

{% tab title="Template" %}
```javascript
let feature = layer.getSelectedTileFeature();
if (feature) {
    console.log("선택된 건물:", feature.properties.name, "tile:", feature.tileKey, "batchId:", feature.batchId);
}
```
{% endtab %}
{% endtabs %}

### getTileFeatureIdentityKey(), setTileFeatureIdentityKey(key) → string

> 3D Tiles 건물 정체성 키(배치 테이블 속성 이름)를 조회하거나 설정합니다.
>
> 엔진은 줌으로 LOD(타일 레벨)가 바뀌어도 같은 건물의 선택을 유지하려고 건물을 배치 테이블 속성 하나의 값으로 알아봅니다(기본 `"name"`). 그 값이 같은 행은 전부 한 건물로 취급되어 함께 칠해집니다. 레이어마다 따로 가집니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description                                                                                  |
| ---- | ------ | -------------------------------------------------------------------------------------------- |
| key  | string | 정체성 속성 이름(대소문자 구분, 기본값 `"name"`). **빈 문자열이면 기능을 끕니다.**             |

* Return(getTileFeatureIdentityKey)
  * string : 현재 키(기본 `"name"`, 꺼져 있으면 `""`).
  * "" : 끈 상태이거나 3D Tiles 레이어가 아닌 경우.
* Return(setTileFeatureIdentityKey)
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
* Note
  * **끄는 경우**: 그 속성이 건물 하나를 가리키는 값이 아니라 분류(용도, 구역 이름 등)인 데이터셋에서는 건물 하나를 고르면 화면의 같은 값을 가진 건물이 전부 칠해집니다. 그런 데이터셋에서는 `""`로 끕니다. 끄면 선택은 선택을 든 타일 안에서만 유지됩니다(LOD로 다른 타일이 그려지면 하이라이트가 사라지고, 선택을 든 타일이 해제되면 선택도 사라짐).
  * 데이터에 없는 속성 이름을 주면 끈 것과 같습니다(그 속성이 없는 feature의 선택은 타일 안에서만 유지).
  * 선택이 있는 중에 바꿔도 되며 다음 프레임부터 새 키로 칠할 행을 다시 정합니다. 옛 키로 남아 있던 이름(선택을 들던 타일이 해제돼 이름만 남은 것)은 버려집니다. 같은 키를 다시 주면 아무 일도 하지 않습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
console.log(layer.getTileFeatureIdentityKey()); // "name"

layer.setTileFeatureIdentityKey("bldg_id"); // 건물 식별 속성으로 변경
layer.setTileFeatureIdentityKey("");        // 끄기
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
| object   | [JSObject](../object/jsobject3d.md) | 삽입할 객체.                       |

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

### getMinGeometricError(), setMinGeometricError(value) → number

> 3D Tiles 레이어의 최소 기하 오차(geometricError)를 설정합니다.
>
> 설정한 값 이하의 geometricError를 가진 노드는 더 이상 정제(자식 요청)하지 않으므로 최대 상세도를 제한합니다.
>
> geometricError 기준이라 데이터셋이 바뀌어도 "이 정도 해상도까지만"이라는 의미가 유지됩니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                                       |
| ----- | ------ | ------------------------------------------------- |
| value | number | 최소 기하 오차값(m). 0 이하를 입력하면 제한을 해제합니다. |

* Return(getMinGeometricError)
  * number : 설정된 최소 기하 오차값.
  * 0.0 : 제한이 설정되지 않았거나 3D Tiles 레이어가 아닌 경우.
* Return(setMinGeometricError)
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
* Note
  * 의미 있는 값은 데이터셋의 geometricError 분포에 따라 다릅니다. [get3DTilesDiagnostics](jslayer.md#get3dtilesdiagnostics-object)의 `geMin`, `geMax`, `geAvg`, `geHist`로 확인할 수 있습니다.
  * 반대로 상세도를 올리는 최대 화면 오차는 [setMaxGeometricError](jslayer.md#getmaxgeometricerror-setmaxgeometricerror-value-number)로 설정합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
// geometricError 8 이하의 노드는 더 정제하지 않음
layer.setMinGeometricError(8.0);
let minError = layer.getMinGeometricError();

// 제한 해제
layer.setMinGeometricError(0);
```
{% endtab %}
{% endtabs %}

### getRefineHysteresisRatio(), setRefineHysteresisRatio(ratio) → number

> 3D Tiles 정제 히스테리시스 비율을 설정합니다.
>
> 정제는 최대 화면 오차([setMaxGeometricError](jslayer.md#getmaxgeometricerror-setmaxgeometricerror-value-number))를 초과할 때 시작하고, 되돌리기는 그 값을 이 비율로 나눈 값 미만으로 내려갔을 때만 합니다. (예: 최대 화면 오차 16, 비율 1.5 → 16 초과에서 정제 시작, 약 10.7 미만에서 되돌림)
>
> 카메라 회전으로 타일까지의 거리가 오르내려도 임계값 근처 타일이 정제와 되돌림을 왕복하며 자식이 해제/재요청되는 현상을 줄입니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                              |
| ----- | ------ | ---------------------------------------- |
| ratio | number | 히스테리시스 비율(1.0 ~ 4.0, 기본값 1.5). |

* Return(getRefineHysteresisRatio)
  * number : 설정된 비율.
  * 0.0 : 3D Tiles 레이어가 아닌 경우.
* Return(setRefineHysteresisRatio)
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
    * ratio가 1.0 미만이거나 4.0 초과인 경우(값은 변경되지 않음).
* Note
  * 1.0으로 설정하면 되돌림 지연이 사라져 CesiumJS와 같은 판정이 되지만, 임계값 근처 타일이 회전 중 팝핑하고 재요청이 늘어납니다.
  * 값이 클수록 되돌림이 늦어져 그려지는 삼각형이 늘어납니다(소스 주석 실측: 기본 1.5에서 CesiumJS 대비 약 +17%). 삼각형 예산이 빠듯하거나 CesiumJS와 수치를 맞춰 비교할 때만 낮추는 것을 권장합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let ok = layer.setRefineHysteresisRatio(1.5);
let ratio = layer.getRefineHysteresisRatio();
```
{% endtab %}
{% endtabs %}

### getRefineHoldTime(), setRefineHoldTime(ms) → number, boolean

> 3D Tiles 정제 유지(팝아웃 방지) 창(ms)을 조회하거나 설정합니다.
>
> REPLACE 정제에서 이미 자식으로 정제해 그리던 노드는, 새로 보이게 된 자식이 아직 오지 않았다는 이유로 거친 부모로 되돌아가지 않습니다(빠진 자리는 조상 채움이 덮습니다). 이 값은 "마지막으로 자식이 전부 준비됐던 시점"부터의 실제 경과 시간입니다.
>
> 창이 지나 만료돼도 되돌림이 화면을 더 덮을 때만 부모로 되돌립니다(그 노드가 자기를 그릴 수 있는데 조상 채움으로는 못 그리는 경우, 예: 가우시안 스플랫 타일). 그 밖에는 만료 뒤에도 지금 화면을 유지합니다. 레이어 알파가 250 미만이어도 더 이상 되돌림 사유가 아닙니다(알파 패스의 조상 채움이 빠진 자리를 덮습니다).
>
> 3D Tiles 레이어에서만 사용할 수 있으며, 값은 레이어 단위로 설정됩니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description                                                   |
| ---- | ------ | ------------------------------------------------------------- |
| ms   | number | 정제 유지 창(ms, 기본값 10000). 0 ~ 600000. 유한한 수여야 합니다.   |

* Return(getRefineHoldTime)
  * number : 설정된 창(ms).
  * 0.0 : 3D Tiles 레이어가 아닌 경우(창 0과 구분되지 않음).
* Return(setRefineHoldTime)
  * true : 설정 성공.
  * false : 설정 실패. 값은 변경되지 않으며 콘솔에 사유가 출력됩니다.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
    * ms가 0 미만이거나 600000 초과이거나 유한한 수가 아닌 경우(NaN, Infinity).
* Note
  * 기본값 10000ms는 종전의 600프레임(60fps 기준 약 10초)을 시간으로 옮긴 값입니다.
  * [get3DTilesDiagnostics](jslayer.md#get3dtilesdiagnostics-object)의 `refineHoldMs`(설정값), `holdKept`(창이 지났지만 유지를 계속한 노드 수), `holdReverted`(창이 지나 되돌린 노드 수)로 확인할 수 있습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let ok = layer.setRefineHoldTime(10000);
let ms = layer.getRefineHoldTime();
```
{% endtab %}
{% endtabs %}

### getTileUnloadDistance(), setTileUnloadDistance(meter) → number, boolean

> 3D Tiles 모델 데이터의 거리 기반 해제 거리를 조회하거나 설정합니다.
>
> 카메라가 멀어져 더는 필요 없는 타일의 모델 데이터(정점/텍스처)와 중첩 타일셋(노드 트리)을 풀어 메모리를 돌려줍니다. 종전에는 보유 용량 상한([setMaxTilesRetainedMB](../option/jsoption.md#getmaxtilesretainedmb-setmaxtilesretainedmb-size-number), 기본 512MB)을 넘을 때만 풀렸고 상한 안쪽인 데이터셋은 카메라가 아무리 멀어져도 처음 받은 것이 그대로 남았습니다. 이 해제는 상한과 무관하게 돌고, 풀린 데이터는 다시 필요해지면(가까이 돌아오면) 다시 받습니다.
>
> 3D Tiles 레이어에서만 사용할 수 있으며, 값은 레이어 단위로 설정됩니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                                                                                        |
| ----- | ------ | -------------------------------------------------------------------------------------------------- |
| meter | number | 해제 거리(m). 0: 자동(기본값), 0 초과: 고정 거리(m), 0 미만: 거리 기반 해제 끔. 유한한 수여야 합니다. |

* Return(getTileUnloadDistance)
  * number : 설정된 값(0 자동 / > 0 고정 m / < 0 끔).
  * 0.0 : 3D Tiles 레이어가 아닌 경우(자동 모드와 구분되지 않음).
* Return(setTileUnloadDistance)
  * true : 설정 성공.
  * false : 설정 실패. 값은 변경되지 않으며 콘솔에 사유가 출력됩니다.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
    * meter가 유한한 수가 아닌 경우(NaN, Infinity).
* Note
  * **0(자동)**: SSE에서 거리를 파생합니다. 어떤 타일의 데이터는 그 부모가 정제를 시작할 때만 다시 필요하므로, 부모가 정제를 멈추는 거리(부모 geometricError × 화면 상수 / (최대 SSE / 히스테리시스 비율))의 1.5배보다 멀면 풉니다. [setMaxGeometricError](jslayer.md#getmaxgeometricerror-setmaxgeometricerror-value-number)와 [setRefineHysteresisRatio](jslayer.md#getrefinehysteresisratio-setrefinehysteresisratio-ratio-number)를 바꾸면 이 거리도 따라 바뀝니다. 해제 거리가 다시 받기 시작하는 거리의 2.25배라서 그 경계 근처에서 카메라를 앞뒤로 움직여도 풀었다 받기를 되풀이하지 않습니다.
  * **0 초과(고정)**: 카메라와 부모 타일 경계 볼륨 사이가 이 값을 넘고 SSE가 정제를 요구하지 않는 타일만 풉니다. 자동의 1.5 여유 배수는 얹지 않으므로(숫자가 곧 해제 거리) 해제/재요청 간격이 자동보다 좁을 수 있습니다(판정에 쓰는 히스테리시스에 최소 1.5를 둡니다). 넉넉한 간격이 필요하면 `get3DTilesDiagnostics().unloadRootDist`(자동 거리)의 1.5배 이상으로 정하십시오.
  * **화면이 필요로 하는 타일(그려지는 타일, SSE가 정제를 요구하는 부모의 자식)은 이 값이 작아도 풀리지 않습니다.** SSE 렌더링 수준이 우선입니다.
  * 풀리지 않는 것: 지금 그려지는 타일, 최근 1초 안에 그려진 타일, 응답 대기 중인 json이 있는 중첩 타일셋(안쪽 중첩 타일셋 포함), 자동 모드에서 루트 타일 자신의 콘텐츠(고정 거리 모드에서만 그 거리 밖이고 지금 그려지지 않을 때 풂). 선택을 든 타일이 풀리면 그 건물의 이름이 남아 다시 그려질 때 선택이 돌아옵니다([setTileFeatureIdentityKey](jslayer.md#gettilefeatureidentitykey-settilefeatureidentitykey-key-string) 참고).
  * 판정은 0.5초 간격으로 하고 카메라가 멈추고 새 콘텐츠도 없으면 곧 멈춥니다(카메라가 멈춘 채 새 콘텐츠만 들어오는 동안은 2초 간격). 한 번의 순회는 해제 예산(2ms)을 넘으면 남은 것을 다음 순회로 미룹니다.
  * 시간과 해제 수는 [get3DTilesDiagnostics](jslayer.md#get3dtilesdiagnostics-object)의 `unload*` 필드로 읽습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setTileUnloadDistance(0);      // 자동(기본)
layer.setTileUnloadDistance(3000);   // 3km 밖 타일 데이터 해제
layer.setTileUnloadDistance(-1);     // 끔(보유 용량 상한으로만 해제)

let distance = layer.getTileUnloadDistance();
```
{% endtab %}
{% endtabs %}

### getFillOnlyHorizonFactor(), setFillOnlyHorizonFactor(factor) → number, boolean

> 3D Tiles 지평선 규모를 넘는 타일의 "채움 전용" 처리 배수를 조회하거나 설정합니다.
>
> 카메라를 크게 돌리거나 내린 직후에는 자식이 아직 없어 부모(더 거친 타일)가 대신 그려집니다. 그 부모가 지구 규모면 메시 오차가 카메라 높이를 훨씬 넘어, 정밀 타일을 가로막는 가짜 벽과 카메라 앞을 가로지르는 띠(바다 텍스처의 파란 띠)로 보입니다.
>
> 카메라 높이 h(200m 하한)에서 지평선까지의 거리 `sqrt(2*R*h + h*h)`의 factor배보다 큰 타일 중 **자식 대신 서 있는 REPLACE 타일**(자식 미준비/미요청/하강 공백으로 부모가 대신 그려진 것)만 정밀 목록에서 빼 조상 채움 패스(어떤 정밀 타일도 덮지 못한 화소에만 그림)로 내립니다. 그리지 않는 것이 아니라 정밀 타일이 있는 화소에서만 물러나므로 화면이 비지 않습니다. ADD 노드, SSE가 정답이라 그린 타일, 리프는 크기와 무관하게 옮기지 않으며, 한계 이하 타일이 화면에 하나도 없으면(시작 직후 큰 타일만 받은 상태) 아무것도 옮기지 않습니다.
>
> 3D Tiles 레이어에서만 사용할 수 있으며, 값은 레이어 단위로 설정됩니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description                                                                                      |
| ------ | ------ | ------------------------------------------------------------------------------------------------ |
| factor | number | 지평선 거리 대비 배수. 0: 끔(종전 동작). 클수록 더 큰 타일까지 정밀 목록에 둡니다. 0 이상의 유한한 값만 받습니다(카메라 250m에서 3.0 = 약 169km 초과 타일). |

* Return(getFillOnlyHorizonFactor)
  * number : 유효값(명시한 값이 있으면 그 값, 없으면 기본값).
  * 0.0 : 3D Tiles 레이어가 아니거나 끈 경우(구분되지 않음).
* Return(setFillOnlyHorizonFactor)
  * true : 설정 성공.
  * false : 설정 실패. 값은 변경되지 않으며 콘솔에 사유가 출력됩니다.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
    * factor가 음수이거나 유한한 수가 아닌 경우.
* Note
  * **기본값(명시하지 않았을 때): 구글 레이어 3.0, 그 밖의 레이어 0(끔).** 구글 판별은 import한 루트 URL의 호스트가 `tile.googleapis.com`인 것 하나뿐입니다. 사내 프록시, Cesium ion의 구글 자산, CDN 재배포처럼 다른 호스트를 거치면 구글 데이터여도 기본은 꺼져 있으며, 그런 경우 `setFillOnlyHorizonFactor(3)` / [setFillSkirtCut(true)](jslayer.md#getfillskirtcut-setfillskirtcut-cut-boolean)를 직접 호출하십시오. (`get3DTilesDiagnostics().googleTiles`로 판별 결과를 확인할 수 있습니다.)
  * 명시한 값은 구글 판별보다 우선하고 레이어를 다시 import해도 유지됩니다. 명시한 값을 지우고 기본(자동)으로 되돌리려면 [resetFillDefaults](jslayer.md#resetfilldefaults-boolean)를 부릅니다(`-1` 같은 음수는 거부됩니다).
  * **주의**: 불투명 레이어(알파 250 이상)에서 알파 재질(투명 메시)을 가진 타일이 대신 서는 타일로 내려가면 그 투명 부분이 그려지지 않습니다(그 레이어의 조상 채움 패스는 불투명 부분만 그림). 가우시안 스플랫 타일은 레이어 알파와 무관하게 채움에서 통째로 건너뜁니다. 불투명하지 않은 REPLACE 타일셋에는 켜지 마십시오. 레이어 알파가 250 미만이면 내린 타일의 메시도 전부 알파 패스의 조상 채움으로 그려집니다.
  * 이번 프레임에 내린 타일 수는 `get3DTilesDiagnostics().fillOnlyDemoted`입니다.
{% endtab %}

{% tab title="Template" %}
```javascript
// 구글 3D Tiles를 사내 프록시로 받는 경우 직접 켠다
layer.setFillOnlyHorizonFactor(3);
layer.setFillSkirtCut(true);

console.log(layer.getFillOnlyHorizonFactor()); // 3
```
{% endtab %}
{% endtabs %}

### getFillSkirtCut(), setFillSkirtCut(cut) → boolean

> 3D Tiles 조상 채움 타일의 치마(skirt) 제거 여부를 조회하거나 설정합니다.
>
> 정밀 타일이 덮지 못한 자리를 거친 조상으로 메우는 채움 패스에서만, 구글 타일 가장자리의 치마(텍스처가 세로로 늘어난 면) 조각을 버려 계단 사이의 벽을 없앱니다. 정밀 타일은 건드리지 않아 타일 사이 이음매는 그대로입니다. 그림자가 켜져 있으면(그림자 전용 프로그램) 적용되지 않습니다.
>
> 3D Tiles 레이어에서만 사용할 수 있으며, 값은 레이어 단위로 설정됩니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description                                |
| ---- | ------- | ------------------------------------------ |
| cut  | boolean | true: 치마 제거, false: 제거 안 함.        |

* Return(getFillSkirtCut)
  * boolean : 유효값(명시한 값이 있으면 그 값, 없으면 기본값).
  * false : 3D Tiles 레이어가 아닌 경우.
* Return(setFillSkirtCut)
  * true : 설정 성공.
  * false : 설정 실패. 콘솔에 사유가 출력됩니다.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
* Note
  * **기본값(명시하지 않았을 때): 구글 레이어 true, 그 밖의 레이어 false.** 구글 판별 기준은 [setFillOnlyHorizonFactor](jslayer.md#getfillonlyhorizonfactor-setfillonlyhorizonfactor-factor-number-boolean)와 같습니다. 비구글 REPLACE 데이터에서는 정상 면이 버려질 수 있습니다(소스 주석 실측: 한 데이터셋의 루트 면적 2.7%).
  * 명시한 값은 판별보다 우선하며 [resetFillDefaults](jslayer.md#resetfilldefaults-boolean)로 지웁니다.
  * 치마 제거 유니폼을 실제로 건 조상 채움 타일 수는 `get3DTilesDiagnostics().skirtCutTiles`입니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setFillSkirtCut(true);
console.log(layer.getFillSkirtCut()); // true
```
{% endtab %}
{% endtabs %}

### resetFillDefaults() → boolean

> [setFillOnlyHorizonFactor](jslayer.md#getfillonlyhorizonfactor-setfillonlyhorizonfactor-factor-number-boolean)와 [setFillSkirtCut](jslayer.md#getfillskirtcut-setfillskirtcut-cut-boolean)로 명시한 값을 지우고 기본(자동)으로 되돌립니다.
>
> 자동 기본값은 구글 레이어 3.0 / true, 그 밖의 레이어 0 / false입니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 두 기능의 명시한 값을 모두 지움.
  * false : 실패(월드가 초기화되지 않았거나 3D Tiles 레이어가 아닌 경우. 콘솔에 사유 출력).
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setFillOnlyHorizonFactor(0);
layer.setFillSkirtCut(false);

layer.resetFillDefaults(); // 다시 자동(구글 레이어만 켜짐)
```
{% endtab %}
{% endtabs %}

### setTileBoundary(minLon, minLat, maxLon, maxLat)

> 3D Tiles 레이어를 경위도(degree) 사각 범위로 제한합니다.
>
> 범위 안에 **완전히 포함되는** 타일만 요청하고 그립니다. 범위에 걸치기만 하는 타일은 하위 타일로 내려가기 위해 순회는 하지만 자신의 콘텐츠는 받지도 그리지도 않습니다.
>
> 범위를 나중에 좁힌 경우 이미 받아 둔 타일도 그리지 않습니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description         |
| ------ | ------ | ------------------- |
| minLon | number | 최소 경도(degree).   |
| minLat | number | 최소 위도(degree).   |
| maxLon | number | 최대 경도(degree).   |
| maxLat | number | 최대 위도(degree).   |

* Return
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
* Note
  * min 값이 max 값보다 큰 경우 자동으로 바꿔서 사용합니다.
  * [clearTileBoundary](jslayer.md#cleartileboundary)로 해제합니다.
  * [setTileExcludeArea](jslayer.md#settileexcludearea-option-boolean)와 서로 독립이며, 둘 다 설정하면 둘 다 적용됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
// 서울시청 일대(경도 126.97 ~ 126.99, 위도 37.55 ~ 37.57)만 표시
layer.setTileBoundary(126.97, 37.55, 126.99, 37.57);
```
{% endtab %}
{% endtabs %}

### clearTileBoundary()

> [setTileBoundary](jslayer.md#settileboundary-minlon-minlat-maxlon-maxlat)로 설정한 사각 범위 제한을 해제합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.clearTileBoundary();
```
{% endtab %}
{% endtabs %}

### setTileExcludeArea(option) → boolean

> 3D Tiles 레이어에서 경위도 폴리곤 영역 안의 형상을 렌더/선택/그림자에서 제외합니다.
>
> 영역 안에 완전히 들어온 타일은 요청과 렌더를 하지 않고, 영역 경계에 걸친 타일은 셰이더 마스크로 영역 안쪽만 지웁니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                                                          | Description                               |
| ------ | ------------------------------------------------------------- | ----------------------------------------- |
| option | [TileExcludeAreaOptions](jslayer.md#tileexcludeareaoptions)   | 제외 영역 옵션(`areas` 배열).                    |

* Return
  * true : 설정 성공.
  * false : 설정 실패. 콘솔에 사유가 출력됩니다.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
    * `areas` 배열이 없는 경우.
    * 정점이 3개 이상인 링이 하나도 없는 경우.
    * 영역 생성에 실패한 경우(기존 제외 영역은 유지됨).
    * 마스크 텍스처 생성에 실패한 경우(기존 제외 영역도 모두 해제됨).
* Note
  * 호출할 때마다 이전 제외 영역을 대체합니다. 일부만 해제하는 기능은 없으며 [clearTileExcludeArea](jslayer.md#cleartileexcludearea)로 전체를 해제합니다.
  * 정점이 3개 미만인 `ring`/`holes` 항목은 경고만 출력하고 건너뜁니다.
  * 평면 모드에서는 제외 영역 판정이 동작하지 않습니다. 설정은 저장되며 지구본 모드로 전환되면 적용됩니다(호출 시 경고 출력).
  * [setTileBoundary](jslayer.md#settileboundary-minlon-minlat-maxlon-maxlat)와 서로 독립이며, 둘 다 설정하면 둘 다 적용됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let ok = layer.setTileExcludeArea({
    areas: [
        {
            // 경위도(degree) [lon, lat], 3개 이상
            ring: [
                [126.970, 37.560],
                [126.980, 37.560],
                [126.980, 37.570],
                [126.970, 37.570]
            ],
            // 선택: 영역 안의 구멍
            holes: [
                [
                    [126.973, 37.563],
                    [126.977, 37.563],
                    [126.977, 37.567]
                ]
            ]
        }
    ]
});
```
{% endtab %}
{% endtabs %}

### clearTileExcludeArea()

> [setTileExcludeArea](jslayer.md#settileexcludearea-option-boolean)로 설정한 제외 영역을 모두 해제합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.clearTileExcludeArea();
```
{% endtab %}
{% endtabs %}

### getTileHeightOffset(), setTileHeightOffset(meter) → number

> 3D Tiles 전체를 지구 중심 기준으로 지정한 높이(m)만큼 띄웁니다.
>
> 엔진 지구본과 3D Tiles 지표면이 같은 깊이에 놓여 생기는 z-fighting을 없애기 위한 보정입니다. [import3DTiles](jslayer.md#import3dtiles-option-boolean)의 `offsetZ` 옵션과 같은 값을 런타임에 바꿉니다.
>
> 평행이동이 아니라 지구 중심 기준 균일 스케일로 적용되므로 인접 타일 이음매가 벌어지지 않습니다. 대신 형상 자체도 소폭 커집니다(소스 주석 기준 5m 보정 시 400m 건물이 약 0.3mm 커지는 수준).
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                         |
| ----- | ------ | ----------------------------------- |
| meter | number | 높이 오프셋(m, 기본값 0.0). 0이면 보정 없음. |

* Return(getTileHeightOffset)
  * number : 설정된 높이 오프셋(m).
  * 0.0 : 3D Tiles 레이어가 아닌 경우.
* Return(setTileHeightOffset)
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
* Note
  * 이 값은 수동 보정값만 나타냅니다. [지형 자동 맞춤](jslayer.md#settileautoterrainfit-enable)을 켠 경우 렌더에는 "수동 보정 + 자동 보정"의 합이 적용되며, 자동 보정값은 [getTileTerrainFit](jslayer.md#gettileterrainfit-tileterrainfit)의 `offsetZ`로 읽습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setTileHeightOffset(5.0);
let offset = layer.getTileHeightOffset();
```
{% endtab %}
{% endtabs %}

### setTileAutoTerrainFit(enable)

> 3D Tiles 레이어의 지형 자동 맞춤을 켜거나 끕니다.
>
> 포인트클라우드·메시·가우시안 스플랫이 지형 위에 떠 있거나 파묻힌 것을 자동으로 보정합니다. 데이터의 높이 기준(타원체고/표고)은 파일에 적혀 있지 않으므로 추정하지 않고 엔진 지형을 실제로 조회해 보정값을 구합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다. [import3DTiles](jslayer.md#import3dtiles-option-boolean)의 `autoTerrainFit` 옵션과 같은 스위치입니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type    | Description                                                           |
| ------ | ------- | --------------------------------------------------------------------- |
| enable | boolean | true: 켜고 측정을 처음부터 다시 시작. false: 끄고 자동 보정값을 0으로 되돌림. |

* Return
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
* Note
  * **측정 방식**: 표본은 점 객체(PNTS/glTF POINTS, 루트부터 깊이 4까지의 첫 점 객체)가 있으면 그 점을 쓰고, 없으면 로드된 메시 정점을, 그것도 없으면 스플랫 중심점을 씁니다(`getTileTerrainFit().source`). 표본을 10m 격자로 나눠 셀마다 가장 낮은 점(지면 반사)을 고르고, 그 자리의 엔진 지형 고도(DEM 비율 반영)와의 차를 모아 **30 백분위**를 구해 그 음수를 자동 보정(`offsetZ`)으로 씁니다. 중앙값이 아닌 이유는 수관만 잡힌 셀이 차를 양수 쪽으로 치우치게 하기 때문입니다.
  * 지형이 아직 올라오지 않은 시점의 조회는 거친 레벨 값을 주므로, 한 번 재고 끝내지 않고 매 프레임 다시 재면서 표본이 읽은 지형 레벨의 최솟값이 120프레임 동안 더 오르지 않으면(또는 1800프레임이 되면) 확정합니다(`state` 1 → 2). 측정 중에도 현재 값을 바로 적용하므로 수렴 과정이 화면에 보입니다.
  * 메시·스플랫은 측정 중인 동안 새로 로드된 노드(루트부터 깊이 4)를 계속 표본에 합칩니다(정점 예산 200만 개, 스플랫은 타일당 최대 2만 점). 점·메시·스플랫 정점이 3600프레임이 지나도록 전혀 없으면 포기합니다(`state` 3).
  * 새 타일셋을 import하면 이전 보정과 표본을 버립니다(옵션은 import 직후 다시 적용됩니다).
{% endtab %}

{% tab title="Template" %}
```javascript
// 로드 시 켜기
layer.import3DTiles({ url: "http://.../tileset.json", autoTerrainFit: true });

// 런타임에 켜기/끄기
layer.setTileAutoTerrainFit(true);
layer.setTileAutoTerrainFit(false);
```
{% endtab %}
{% endtabs %}

### getTileTerrainFit() → [TileTerrainFit](jslayer.md#tileterrainfit)

> 3D Tiles 레이어의 지형 자동 맞춤 상태, 보정값, 루트 바운딩 정보를 반환합니다.
>
> 측정 진행 확인과 카메라 프레이밍(루트 위치로 이동)에 사용합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * [TileTerrainFit](jslayer.md#tileterrainfit) : 상태 객체.
  * `{}` (속성이 없는 빈 객체) : 3D Tiles 레이어가 아닌 경우.
* Note
  * `rootLon`, `rootLat`, `rootAlt`, `rootRadius`는 타일셋 루트가 로드된 뒤에만 포함됩니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let fit = layer.getTileTerrainFit();
console.log("enabled:", fit.enabled, "state:", fit.state, "보정:", fit.offsetZ, "m");

if (fit.rootLon !== undefined) {
    // 루트 위치 확인 (경도, 위도, 높이, 반경)
    console.log(fit.rootLon, fit.rootLat, fit.rootAlt, fit.rootRadius);
}
```
{% endtab %}
{% endtabs %}

### getSplatAlphaScale(), setSplatAlphaScale(scale) → number, boolean

> 3D Tiles 레이어에 포함된 가우시안 스플랫의 진하기(불투명도 배수)를 조회하거나 설정합니다.
>
> 1.0이 자료 그대로입니다. 올리면 SPZ 불투명도가 그만큼 곱해져 지형이 비쳐 보이던 것이 줄어듭니다. 1을 넘는 값은 셰이더에서 1.0으로 포화하므로 "완전 불투명"이 상한입니다.
>
> 스플랫은 타일마다 별개 객체이고 타일이 계속 흘러들어오므로 값을 레이어가 들고 렌더 루프가 매 프레임 타일에 밀어 줍니다(나중에 온 타일도 같은 진하기로 그려집니다).
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                                       |
| ----- | ------ | ------------------------------------------------- |
| scale | number | 진하기 배수(기본값 1.0). 0 초과 8 이하.             |

* Return(getSplatAlphaScale)
  * number : 설정된 배수.
  * 0.0 : 레이어가 없거나 3D Tiles 레이어가 아닌 경우.
* Return(setSplatAlphaScale)
  * true : 설정 성공.
  * false : 설정 실패. 값은 변경되지 않습니다.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
    * scale이 0 이하이거나 8을 초과하거나 NaN인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setSplatAlphaScale(2.0); // 진하게
console.log(layer.getSplatAlphaScale()); // 2
```
{% endtab %}
{% endtabs %}

### getSplatScale(), setSplatScale(scale) → number, boolean

> 3D Tiles 레이어에 포함된 가우시안 스플랫의 크기 배수를 조회하거나 설정합니다.
>
> 1.0이 자료 그대로이며 배수는 스플랫 공분산에 곱해집니다. 값은 [setSplatAlphaScale](jslayer.md#getsplatalphascale-setsplatalphascale-scale-number-boolean)과 같이 레이어가 들고 매 프레임 타일에 적용합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                                       |
| ----- | ------ | ------------------------------------------------- |
| scale | number | 크기 배수(기본값 1.0). 0 초과 8 이하.               |

* Return(getSplatScale)
  * number : 설정된 배수.
  * 0.0 : 레이어가 없거나 3D Tiles 레이어가 아닌 경우.
* Return(setSplatScale)
  * true : 설정 성공.
  * false : 설정 실패. 값은 변경되지 않습니다.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
    * scale이 0 이하이거나 8을 초과하거나 NaN인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setSplatScale(1.5);
console.log(layer.getSplatScale()); // 1.5
```
{% endtab %}
{% endtabs %}

### setTileCopyrightCallback(callback) → boolean

> 3D Tiles 레이어의 저작자 표시(attribution) 콜백을 설정합니다.
>
> 화면에 그려진 타일의 데이터 제공자는 타일마다 다르고 카메라를 옮기면 바뀌므로, 매 프레임 "그려진 타일의 집합"에서 제공자를 모아 그 결과가 실제로 바뀐 프레임에만 콜백을 호출합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
| Name     | Type     | Description                           |
| -------- | -------- | ------------------------------------- |
| callback | function | 저작자 목록이 바뀔 때 호출될 콜백 함수. |

* Callback Parameter

| Name      | Type          | Description                                                                          |
| --------- | ------------- | ------------------------------------------------------------------------------------ |
| layername | string        | 레이어 이름.                                                                           |
| copyright | string        | 제공자를 세미콜론(`;`)으로 합친 문자열(예: `"Airbus;Google;Maxar Technologies"`).               |
| list      | array(string) | 같은 내용의 제공자 배열.                                                                    |
| counts    | array(number) | `list`와 같은 순서로 각 제공자가 그려진 타일에 나타난 횟수.                                         |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  * 실패 조건
    * 월드가 초기화되지 않은 경우.
    * 3D Tiles 레이어가 아닌 경우.
* Note
  * 제공자는 그려진 타일의 glTF 저작권 문자열과 tileset.json의 `asset.copyright`를 세미콜론 기준으로 분해해 모읍니다.
  * 출현 횟수가 많은 순으로 정렬되며, 횟수가 같으면 이름순입니다.
  * 콜백은 목록이 바뀐 프레임에만 호출되므로, 콜백을 설정하기 전에 이미 표시된 값이나 초기 표시는 [getTileCopyright](jslayer.md#gettilecopyright-string)로 읽습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.setTileCopyrightCallback(function(e) {
    console.log(e.layername, e.copyright);
    // e.list : ["Airbus", "Google", ...]
    // e.counts : [120, 85, ...]
});
```
{% endtab %}
{% endtabs %}

### getTileCopyright() → string

> 3D Tiles 레이어의 현재 화면 기준 저작자 표시 문자열을 반환합니다.
>
> [setTileCopyrightCallback](jslayer.md#settilecopyrightcallback-callback-boolean)을 놓쳤거나 초기 표시를 그릴 때 사용합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * string : 제공자를 세미콜론(`;`)으로 합친 문자열(출현 횟수가 많은 순).
  * "" : 그려진 타일에 저작자 정보가 없거나, 3D Tiles 레이어가 아니거나, 월드가 초기화되지 않은 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
let copyright = layer.getTileCopyright();
```
{% endtab %}
{% endtabs %}

### get3DTilesDiagnostics() → object

> 3D Tiles 레이어의 진단 정보를 반환합니다. (진단용)
>
> 순회별 소요 시간, 그려진 노드/삼각형 수, 파싱 워커 상태, 타일 보유 메모리, geometricError 분포, 화면 구멍/배제 사유 등을 마지막 프레임 기준으로 반환합니다. CPU 고착이나 화면 공백이 재현된 시점에 원인 구간을 읽기 위한 상설 계측값입니다.
>
> 3D Tiles 레이어에서만 사용할 수 있습니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * object : 진단 정보. 필드는 [3DTilesDiagnostics](jslayer.md#3dtilesdiagnostics)를 참조합니다.
  * null : 3D Tiles 레이어가 아니거나 월드가 초기화되지 않은 경우.
* Note
  * `nodes`, 파싱 누적 값, 메모리 값은 레이어 단위가 아니라 엔진 전역 값입니다.
  * 매 호출마다 객체를 새로 만들므로 매 프레임이 아니라 필요할 때만 호출하는 것을 권장합니다.
{% endtab %}

{% tab title="Template" %}
```javascript
let d = layer.get3DTilesDiagnostics();
if (d) {
    console.log("drawn", d.drawn, "triangles", d.triangles);
    console.log("SSE", d.setDrawLevelMs, "draw", d.viewListMs, "load", d.moveLoadMs);
    console.log("retained", d.retainedMB, "/", d.retainedCapMB, "MB");
}
```
{% endtab %}
{% endtabs %}

### get3DTilesLoadLeadFrames(), set3DTilesLoadLeadFrames(frames) → number

> 3D Tiles 로딩 순회가 그리기 순회보다 앞서 갈 수 있는 신선도 창(프레임 수)을 설정합니다.
>
> 그리기 순회가 최근 이 프레임 수 안에 도달한 노드는 "렌더러가 여기까지 왔다"고 보고 로딩 순회가 그 아래로 내려갈 수 있습니다.
>
> 0이면 제한을 끄며, 이 경우 로딩 순회가 SSE만 보고 트리 끝까지 내려가 요청이 급증합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있으며, 값은 레이어 단위로 설정됩니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description                                         |
| ------ | ------ | --------------------------------------------------- |
| frames | number | 선행 허용 프레임 수(기본값 8). 음수는 0으로 처리. 0이면 제한 해제. |

* Return(get3DTilesLoadLeadFrames)
  * number : 설정된 프레임 수.
  * 0 : 3D Tiles 레이어가 아닌 경우(제한 해제 상태와 구분되지 않음).
* Return(set3DTilesLoadLeadFrames)
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.set3DTilesLoadLeadFrames(8);
let frames = layer.get3DTilesLoadLeadFrames();
```
{% endtab %}
{% endtabs %}

### get3DTilesLoadLookahead(), set3DTilesLoadLookahead(levels) → number

> 3D Tiles 로딩 순회가 그리기 순회가 아직 도달하지 않은 구간을 몇 레벨까지 앞질러 받을지 설정합니다.
>
> 값이 작으면 정제가 "한 레벨 내려감 → 네트워크 왕복 → 한 레벨 더" 사슬에 묶여, 카메라를 크게 움직인 뒤 화면이 선명해지는 데 오래 걸립니다. 0이면 선행 없이 렌더러가 도달한 곳까지만 받습니다.
>
> [set3DTilesLoadLeadFrames](jslayer.md#get3dtilesloadleadframes-set3dtilesloadleadframes-frames-number)는 "얼마나 오래된 방문까지 인정하나"만 정하고 깊이는 늘리지 않으므로, 깊이는 이 값으로 조절합니다.
>
> 3D Tiles 레이어에서만 사용할 수 있으며, 값은 레이어 단위로 설정됩니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description                                      |
| ------ | ------ | ------------------------------------------------ |
| levels | number | 앞질러 받을 레벨 수(기본값 2). 음수는 0으로 처리. 0이면 선행 없음. |

* Return(get3DTilesLoadLookahead)
  * number : 설정된 레벨 수.
  * 0 : 3D Tiles 레이어가 아닌 경우(선행 없음 상태와 구분되지 않음).
* Return(set3DTilesLoadLookahead)
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.set3DTilesLoadLookahead(2);
let levels = layer.get3DTilesLoadLookahead();
```
{% endtab %}
{% endtabs %}

### get3DTilesTilesetFreeFrames(), set3DTilesTilesetFreeFrames(frames) → number

> 그리기 순회가 이 프레임 수 이상 도달하지 않은 중첩 타일셋을 통째로 해제하기까지 대기하는 프레임 수를 설정합니다.
>
> 노드 트리가 무한정 커지는 것을 막기 위한 값으로, 해제된 타일셋은 다시 필요해지면 json을 재요청해 복원됩니다. 값이 작을수록 해제가 빨라 메모리는 줄지만 재요청이 늘어납니다.
>
> 3D Tiles 레이어에서만 사용할 수 있으며, 값은 레이어 단위로 설정됩니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description                                                      |
| ------ | ------ | ---------------------------------------------------------------- |
| frames | number | 해제 대기 프레임 수(기본값 900, 약 15초). 음수는 0으로 처리. 0이면 해제하지 않음. |

* Return(get3DTilesTilesetFreeFrames)
  * number : 설정된 프레임 수.
  * 0 : 3D Tiles 레이어가 아닌 경우(해제하지 않는 상태와 구분되지 않음).
* Return(set3DTilesTilesetFreeFrames)
  * 반환값 없음. 3D Tiles 레이어가 아니면 아무 동작도 하지 않습니다.
* Note
  * 0으로 두면 노드 트리가 계속 커질 수 있습니다. 값을 올릴 때는 `get3DTilesDiagnostics().nodes`가 실제로 수렴하는지 함께 확인하세요.
{% endtab %}

{% tab title="Template" %}
```javascript
layer.set3DTilesTilesetFreeFrames(900);
let frames = layer.get3DTilesTilesetFreeFrames();
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

#### TileExcludeAreaOptions

> 3D Tiles 레이어 제외 영역 설정 옵션([setTileExcludeArea](jslayer.md#settileexcludearea-option-boolean) 파라미터).

| Name  | Type                                                  | Attributes | Default | Description                    |
| ----- | ----------------------------------------------------- | ---------- | ------- | ------------------------------ |
| areas | array([TileExcludeArea](jslayer.md#tileexcludearea)) |            |         | 제외할 영역 목록(배열이 아니면 설정 실패). |

#### TileExcludeArea

> 3D Tiles 제외 영역 하나(외곽 링과 선택적 홀).
>
> 좌표는 경위도(degree) `[lon, lat]`이며, `[lon, lat, alt]` 3요소 좌표(GeoJSON)를 그대로 넣어도 앞의 두 값만 사용합니다.
>
> 외곽 링과 홀 링은 구분 없이 짝수-홀수(even-odd) 규칙으로 판정하므로, 홀 안쪽은 제외 영역에서 빠집니다.

| Name  | Type                                | Attributes | Default | Description                                                                |
| ----- | ----------------------------------- | ---------- | ------- | -------------------------------------------------------------------------- |
| ring  | array(array(number))                |            |         | 외곽 링 좌표 배열(각 원소 `[lon, lat]`, 3개 이상 필요). 마지막 점이 첫 점과 같으면 중복 점을 제거. 3개 미만이면 해당 영역은 건너뜀. |
| holes | array(array(array(number)))         | optional   |         | 홀 링 배열(각 링은 ring과 같은 형식). 3개 미만인 홀은 건너뜀.                              |

#### TileFeature

> 3D Tiles feature 한 건 정보. [getSelectedTileFeature](jslayer.md#getselectedtilefeature-tilefeature)의 반환 객체이며, [getPickInfo](jslayer.md#getpickinfo-linefrom-lineto-object) / [getPickInfoAtView](jslayer.md#getpickinfoatview-linefrom-lineto-object) 결과의 같은 이름 필드와 같은 모양입니다.

| Name       | Type   | Description                                                                                      |
| ---------- | ------ | ------------------------------------------------------------------------------------------------ |
| tileKey    | string | 타일의 콘텐츠 URL. [extractTileFeature](jslayer.md#extracttilefeature-parameter-jspolygon)의 입력.        |
| batchId    | number | 배치 테이블 행 번호(0 이상의 정수). 타일 레벨마다 같은 건물이라도 달라집니다.                          |
| properties | object | 배치 테이블 속성 이름 → 문자열 값. 해당 행이 배치 테이블 범위 밖이면 포함되지 않습니다.                |

#### TileTerrainFit

> [getTileTerrainFit](jslayer.md#gettileterrainfit-tileterrainfit) 반환 객체의 필드.

| Name         | Type    | Description                                                                                                       |
| ------------ | ------- | ----------------------------------------------------------------------------------------------------------------- |
| enabled      | boolean | 지형 자동 맞춤 사용 여부.                                                                                         |
| state        | number  | 측정 상태. 0 = 꺼짐, 1 = 측정 중, 2 = 확정, 3 = 포기(점·메시 정점·스플랫을 찾지 못함).                              |
| offsetZ      | number  | 적용 중인 자동 보정(m, 위쪽이 +). 측정 중에는 현재 추정값입니다.                                                  |
| heightOffset | number  | 수동 높이 보정(m, [setTileHeightOffset](jslayer.md#gettileheightoffset-settileheightoffset-meter-number) / import `offsetZ`). 렌더에는 `heightOffset + offsetZ`가 적용됩니다. |
| level        | number  | 표본이 읽은 지형 레벨의 최솟값(-1 = 아직 없음).                                                                   |
| samples      | number  | 보정값 계산에 쓴 10m 격자 셀 수.                                                                                  |
| frames       | number  | 측정에 쓴 프레임 수.                                                                                              |
| p30          | number  | (표본 높이 - 지형 높이)의 30 백분위(m). `offsetZ = -p30`.                                                          |
| median       | number  | 같은 차의 중앙값(m, 진단용).                                                                                      |
| source       | number  | 표본 출처. 0 = 없음, 1 = 점 객체, 2 = 메시 정점, 3 = 스플랫(표본이 전부 스플랫에서 나온 경우).                      |
| vertices     | number  | 훑은 표본 정점 수(점: 객체의 점 수, 메시·스플랫: 예산 2,000,000까지 누적).                                         |
| nodes        | number  | 메시·스플랫: 표본을 보탠 노드 수.                                                                                 |
| rootLon      | number  | (루트 로드 후에만) 루트 경계 상자 중심의 경도(degree).                                                            |
| rootLat      | number  | (루트 로드 후에만) 루트 경계 상자 중심의 위도(degree).                                                            |
| rootAlt      | number  | (루트 로드 후에만) 루트 경계 상자 중심의 지구 반경 기준 높이(m). 높이 보정은 반영되지 않습니다.                     |
| rootRadius   | number  | (루트 로드 후에만) 루트 경계 상자 대각선 길이의 절반(m). 카메라 프레이밍용.                                         |

#### 3DTilesDiagnostics

> [get3DTilesDiagnostics](jslayer.md#get3dtilesdiagnostics-object) 반환 객체의 필드(진단용).
>
> 별도 표기가 없으면 마지막 프레임 기준 값입니다. "누적"은 엔진 시작 이후의 누적값입니다.
>
> 이름이 `ms`로 끝나는 값은 밀리초(ms)입니다.

**순회/렌더 비용**

| Name           | Type   | Description                                                                 |
| -------------- | ------ | --------------------------------------------------------------------------- |
| nodes          | number | 살아 있는 노드 수(모든 3D Tiles 레이어의 합). 아래 세 순회 비용에 그대로 곱해집니다.                  |
| tilesets       | number | 이 레이어가 보유한 중첩 타일셋 수.                                                  |
| drawn          | number | 그리기 순회가 반환한 객체 수(채움 전용 처리로 내리기 **전**의 수). 갑자기 떨어지면 LOD 붕괴/화면 공백을 의심합니다. 내린 뒤의 목록 크기는 `drawnFine`/`fillDrawn`입니다. |
| drawnFine      | number | 내린 뒤 정밀 목록에 남은 객체 수.                                                       |
| fillDrawn      | number | 내린 뒤 조상 채움 목록의 객체 수.                                                       |
| refineHold     | number | 정제 유지(팝아웃 방지)가 발동한 노드 수. 0이 아니면 로딩 대기 중입니다.                           |
| refineHoldMs   | number | 정제 유지 창 설정값(ms, [setRefineHoldTime](jslayer.md#getrefineholdtime-setrefineholdtime-ms-number-boolean)). |
| holdKept       | number | 이번 프레임에 창이 지났지만 되돌려도 더 덮을 것이 없어 유지를 계속한 노드 수(`refineHold`에 포함).      |
| holdReverted   | number | 창이 지났고 되돌림이 더 덮어서(자기는 그릴 수 있는데 조상 채움으로는 못 그림 - 스플랫 등) 자기로 되돌린 노드 수. |
| setDrawLevelMs | number | SSE 평가 순회 시간(트리 전체를 건너뛰기 없이 도는 유일한 순회).                                |
| viewListMs     | number | 그리기 순회 시간.                                                              |
| moveLoadMs     | number | 로딩 순회 시간.                                                               |
| clearMs        | number | 정리 순회 + 중첩 타일셋 스윕 시간(스윕은 30프레임마다 한 번이라 그 프레임에만 갱신).                    |
| renderMs       | number | 객체 드로우 루프 시간. 새 타일이 몰리면 VBO/텍스처 생성·업로드로 커집니다.                         |
| drawCalls      | number | 이 레이어가 이번 프레임에 발생시킨 드로우콜 수.                                           |
| triangles      | number | 이 레이어가 이번 프레임에 그린 삼각형 수(점·스플랫은 포함되지 않음).                     |
| points         | number | 이번 프레임에 그린 점군(glTF mode 0 / pnts)의 점 수 합. 드로우콜은 따로 셉니다.           |
| splats         | number | 이번 프레임에 그린 가우시안 스플랫 수. 알파 패스에서 그려져 `drawCalls`/`triangles`에 잡히지 않습니다. |
| splatDraws     | number | 스플랫 드로우 수.                                                                      |
| splatTiles     | number | 스플랫을 그린 타일 수.                                                                 |
| renderFrame    | number | 렌더 프레임 번호(유휴 시 멈추는지 확인용).                                              |

**파싱/워커**

| Name            | Type   | Description                                                                         |
| --------------- | ------ | ----------------------------------------------------------------------------------- |
| parseMs         | number | 동기(폴백) 파싱에 쓴 시간(프레임 사이 누적분을 프레임 경계에서 확정한 값).                         |
| parsed          | number | 동기(폴백) 파싱한 타일 수.                                                              |
| applyMs         | number | 워커 응답 적용(버퍼 → 객체 변환, 텍스처 업로드)에 메인 스레드가 쓴 시간.                          |
| applied         | number | 응답을 적용한 타일 수.                                                                 |
| workerMs        | number | 응답 헤더가 보고한 워커 파싱 시간의 합.                                                  |
| workerParsed    | number | 워커가 파싱한 타일 수.                                                                 |
| parseFailed     | number | 응답 적용에 실패한 수(프로토콜 손상 등).                                                 |
| parseInFlight   | number | 워커 파싱 진행 중인 요청 수.                                                            |
| applyQueued     | number | 적용 대기 중인 응답 수.                                                               |
| parseQueueMB    | number | 백프레셔 예산 사용량(MB) = 워커 응답 대기 + 적용 대기.                                      |
| parseDeferred   | number | 백프레셔 예산 초과로 받지 않고 미요청 상태로 되돌린 수(누적).                                    |
| parseDroppedStale | number | 응답이 왔을 때 노드/타일셋이 이미 삭제되어 버린 수(누적).                                    |
| parseFallback   | number | 워커 대신 동기 파서로 처리하게 된 수(누적). `tileset.json` 폴백까지 섞인 합입니다.          |
| tileParseWorker | boolean | 워커 파싱 경로가 켜져 있는가(`initialize`에 `worker: { use: true }`가 있고 `tileParse`를 끄지 않았으며 워커가 만들어진 경우). |
| fallbackNoWorker | number | 콘텐츠가 워커 없음 때문에 동기 로더로 간 수(누적, 전체 레이어 합).                       |
| fallbackUnsupported | number | 콘텐츠가 워커 미지원 포맷 때문에 동기 로더로 간 수(누적).                             |
| fallbackOther   | number | 그 밖의 사유로 동기 로더로 간 수(누적).                                                  |
| syncParsed      | number | 동기 로더가 만들기를 시도한 콘텐츠 수(파싱 실패 포함, 누적). `parsedTotal`은 워커 적용 수입니다. |
| syncParsedBy    | object  | `syncParsed`의 포맷별 분해. `{ glb, b3dm, pnts, i3dm }`(누적).                          |
| splatMsTotal    | number | 워커가 가우시안 스플랫을 푼 시간(SPZ 복호 + 공분산 조립, 누적 ms).                        |
| splatWorkerTiles | number | 워커가 푼 스플랫 타일 수(누적).                                                         |
| texResponseDropped | number | 요청한 glTF가 응답 전에 해제돼 버린 텍스처(imageProcess) 응답 수(누적, 전체 합). 동기 로더로 간 타일이 텍스처를 받기 전에 풀리면 오르며 정상 동작입니다. |
| parseResponseBroken | number | 응답이 비었거나 헤더가 손상되어 강제로 닫은 수(누적).                                    |
| parseTimedOut   | number | 워커 무응답(30초 초과)으로 동기 폴백 후 회수한 수(누적).                                     |
| workerMsTotal   | number | 워커가 잰 파싱 전체 시간(누적, ms).                                                  |
| gltfMsTotal     | number | `workerMsTotal` 중 glTF 파싱 구간(누적, ms).                                       |
| imageMsTotal    | number | `workerMsTotal` 중 텍스처 디코딩 구간(누적, ms).                                    |
| vertexMsTotal   | number | `workerMsTotal` 중 정점 변환 구간(누적, ms).                                       |
| parsedTotal     | number | 워커가 파싱을 마친 타일 수(누적).                                                     |
| imageFormats    | array  | 텍스처 포맷별 분해. `ktx2`, `jpeg`, `png`, `webp`, `other` 순서의 5개 원소이며 각 원소는 `{fmt, ms, count, inMB, outMB}`(포맷명, 디코딩 시간(누적 ms), 개수(누적), 입력 MB, 출력 MB). |
| basisTarget     | number | KTX2(Basis) 트랜스코딩 타깃 포맷 코드(기본값 13: RGBA32).                                |
| basisProbeCtx   | number | 트랜스코딩 타깃 판정 시 사용한 컨텍스트 핸들(기본값 -1, 0이면 확장 질의가 전부 실패해 13으로 떨어짐).       |
| texOutFormats   | object | 실제로 수신한 텍스처 포맷 히스토그램. 포맷 코드(문자열 키, 압축 포맷은 99 이상) → 수신 수(누적). 수신 수가 0인 포맷은 포함되지 않음. |

**메모리**

| Name          | Type   | Description                                                                                  |
| ------------- | ------ | -------------------------------------------------------------------------------------------- |
| retainedMB    | number | 현재 보유 중인 타일 콘텐츠 크기(MB, 정점+인덱스+텍스처). 워커 적용과 동기 로더가 같은 정의로 셉니다(텍스처는 GL에 올린 바이트). 점(PNTS)·스플랫은 어느 경로든 세지 않습니다. |
| retainedCapMB | number | 보유 크기 상한(MB, 기본값 512). 초과하면 오래 그려지지 않은 타일부터 콘텐츠를 해제합니다.                     |
| tilesEvicted  | number | 상한 초과로 해제한 타일 수(누적).                                                              |
| evictReloaded | number | 상한으로 푼 뒤 10초 안에 다시 만든 수(누적, 전체 레이어 합). 버렸는데 곧 다시 필요했던 것(thrash)입니다. |
| evictedUnvisited | number | 상한으로 푼 것 가운데 도착한 뒤 한 번도 그려지지 않은 수(누적). 형제를 기다리던 막 받은 콘텐츠입니다. |
| evictGraceHeld | number | 상한을 넘은 마지막 스윕에서 도착 유예(5초)로 해제 후보에서 뺀 수(마지막 값).                  |
| arrivalVisitHist | array(number) | 콘텐츠가 도착한 뒤 그리기 순회가 처음 오기까지 걸린 시간 분포(7개, 누적). 구간(초): [0,0.5) [0.5,1) [1,2) [2,3) [3,5) [5,10) [10,~). |

**거리 기반 모델 데이터 해제** ([setTileUnloadDistance](jslayer.md#gettileunloaddistance-settileunloaddistance-meter-number-boolean))

> `tilesEvicted`와 별개입니다. 그쪽은 보유 상한 초과로 푼 수만 셉니다. 아래 값 중 `unloadDistance`, `unloadRootDist`, `unload*`로 시작하는 값은 이 레이어의 값이고 `tilesetJsonDropped`, `jsonRetried`, `jsonFailed`는 전체 레이어 합입니다.

| Name               | Type   | Description                                                                                     |
| ------------------ | ------ | ----------------------------------------------------------------------------------------------- |
| unloadDistance     | number | 설정값(0 자동 / > 0 고정 m / < 0 끔).                                                            |
| unloadRootDist     | number | 자동 모드에서 루트 아래 데이터가 풀리기 시작하는 거리(m, 카메라와 루트 경계 볼륨 사이). 마지막 순회 때의 값이며 참고용입니다. |
| unloadSweeps       | number | 트리를 훑은 횟수(누적).                                                                          |
| unloadSkipped      | number | 판정 간격은 채웠지만 바뀐 것이 없어 건너뛴 횟수(누적).                                            |
| unloadBudgetStops  | number | 한 번의 순회가 해제 예산(2ms)을 넘겨 남은 것을 다음 순회로 미룬 횟수(누적).                        |
| unloadedTiles      | number | 거리로 콘텐츠를 푼 타일 수(누적).                                                                |
| unloadedTilesets   | number | 푼 중첩 타일셋 수(누적).                                                                         |
| unloadedNodes      | number | 푼 타일셋과 함께 사라진 노드 수(누적).                                                           |
| unloadedMB         | number | 푼 콘텐츠 크기(MB, 누적, 타일셋 안의 콘텐츠 포함. 보유 바이트로 잰다).                            |
| unloadReloaded     | number | 거리로 풀린 뒤 다시 받은 콘텐츠 수(누적). 풀었다 받기가 되풀이되면(thrash) 오릅니다.              |
| unloadReloadedSets | number | 거리로 풀린 뒤 다시 받은 중첩 타일셋 수(누적).                                                   |
| unloadSweepMs      | number | 마지막 순회 시간(ms).                                                                            |
| unloadSweepMsMax   | number | 가장 오래 걸린 순회 시간(ms).                                                                    |
| unloadVisited      | number | 마지막 순회가 방문한 노드 수.                                                                    |
| unloadLastTiles    | number | 마지막 순회에서 푼 타일 수.                                                                      |
| unloadLastTilesets | number | 마지막 순회에서 푼 중첩 타일셋 수.                                                               |
| tilesetJsonDropped | number | 죽은 타일셋으로 온 json 응답을 버린 횟수(누적).                                                  |
| jsonRetried        | number | 파싱 대기열 예산에 걸려 버려졌거나 요청이 실패한 `tileset.json`을 다시 보낸 횟수(누적).          |
| jsonFailed         | number | `tileset.json` 요청이 실패한 횟수(누적). 실패한 json은 1초부터 두 배씩(최대 30초) 간격을 두고 다시 보냅니다. |

**채움 전용 / 치마 제거** ([setFillOnlyHorizonFactor](jslayer.md#getfillonlyhorizonfactor-setfillonlyhorizonfactor-factor-number-boolean), [setFillSkirtCut](jslayer.md#getfillskirtcut-setfillskirtcut-cut-boolean))

| Name            | Type    | Description                                                                                   |
| --------------- | ------- | --------------------------------------------------------------------------------------------- |
| fillOnlyFactor  | number  | 유효 배수(명시한 값 > 구글 판별 기본).                                                         |
| googleTiles     | boolean | 루트 URL의 호스트가 `tile.googleapis.com`인가.                                                 |
| fillOnlyDemoted | number  | 이번 프레임에 정밀 목록에서 채움 전용으로 옮긴 타일 수.                                         |
| fillSkirtCut    | boolean | 유효 치마 제거 설정.                                                                           |
| skirtCutTiles   | number  | 치마 제거 유니폼을 실제로 건 조상 채움 타일 수(그림자가 켜져 그림자 전용 프로그램으로 그린 타일은 세지 않음). |
| fillAlpha       | number  | 레이어 알파(< 250)의 조상 채움: 알파 패스에서 그린 채움 타일 수.                                |
| fillAlphaCover  | number  | 그 프레임에 색과 함께 스텐실 덮개를 남긴 정밀 타일 수.                                          |
| fillAlphaRecover | number | 지형 아래 패스라 스텐실만 다시 그린 정밀 타일 수(추가 드로우).                                  |

**geometricError 분포**

| Name   | Type          | Description                                                                                  |
| ------ | ------------- | -------------------------------------------------------------------------------------------- |
| geMin  | number        | 이번 프레임에 그린 노드의 geometricError 최솟값(m).                                                 |
| geMax  | number        | 이번 프레임에 그린 노드의 geometricError 최댓값(m).                                                 |
| geAvg  | number        | 이번 프레임에 그린 노드의 geometricError 평균(m). 그린 노드가 없으면 0.                                  |
| geHist | array(number) | 구간별 노드 수(10개). 구간(m): [0,1) [1,2) [2,4) [4,8) [8,16) [16,32) [32,64) [64,128) [128,256) [256,~). |

[setMinGeometricError](jslayer.md#getmingeometricerror-setmingeometricerror-value-number)에 줄 값을 정할 때 참고합니다.

**부모로 폴백해 그린 사유별 노드 수**

| Name              | Type   | Description                         |
| ----------------- | ------ | ----------------------------------- |
| fbLeaf            | number | 자식이 없는 진짜 리프.                      |
| fbNoVisibleChild  | number | 프러스텀/바운더리 안에 있는 자식이 하나도 없음.        |
| fbChildNotReady   | number | 자식이 있으나 로딩/텍스처가 끝나지 않음.            |
| fbDrawLevel       | number | SSE가 여기서 멈추라고 판정(KEEP).              |

**화면 구멍(그리기로 결정했으나 그릴 객체가 없는 노드)**

| Name             | Type   | Description                                         |
| ---------------- | ------ | --------------------------------------------------- |
| holeTotal        | number | 그리기로 결정됐는데 객체가 없는 노드 수.                       |
| holeUnrequested  | number | 요청 이력이 없음.                                       |
| holeQueued       | number | 요청 큐에서 대기 중.                                    |
| holeInFlight     | number | 전송 중.                                              |
| holeLoadedEmpty  | number | 로딩은 끝났는데 객체가 없음(콘텐츠 없음/건너뜀).                  |
| holeEmptyNoUrl   | number | `holeLoadedEmpty` 중 콘텐츠 URL 자체가 없음(구조용 중간 노드).    |
| holeEmptyJson    | number | `holeLoadedEmpty` 중 중첩 타일셋(json)인데 셋이 없음.           |
| holeEmptySkipped | number | `holeLoadedEmpty` 중 바운더리 때문에 콘텐츠를 건너뜀.            |
| holeEmptyParsed  | number | `holeLoadedEmpty` 중 URL이 있고 받았는데 객체가 만들어지지 않음.   |
| holeFailed       | number | 콘텐츠 요청이 실패해 재시도 간격(1초부터 두 배씩, 최대 30초)을 기다리는 구멍. 종전에는 `holeUnrequested`로 셌습니다. |
| holeNoTexture    | number | 객체는 있는데 텍스처가 준비되지 않아 구멍으로 올린 REPLACE 타일 수(`holeTotal`에는 들지 않음). |

**그리기 순회에서 배제된 노드 수**

| Name          | Type   | Description                                                                 |
| ------------- | ------ | --------------------------------------------------------------------------- |
| exclFrustum   | number | 프러스텀 밖.                                                                  |
| exclBoundary  | number | [setTileBoundary](jslayer.md#settileboundary-minlon-minlat-maxlon-maxlat) 범위 밖(교차 판정). |
| exclHorizon   | number | 지평선 밖.                                                                   |
| exclContained | number | 바운더리에 완전히 포함되지 않아 그리기 직전에 제외.                                 |
| exclArea      | number | [setTileExcludeArea](jslayer.md#settileexcludearea-option-boolean) 영역으로 통째로 빠진 노드 수. |
| maskPartial   | number | 제외 영역 경계에 걸쳐 셰이더 마스크를 켠 타일 수. 0이면 걸친 타일이 없다는 뜻입니다.            |

**빈 하강/기타 진단**

| Name               | Type    | Description                                                                         |
| ------------------ | ------- | ----------------------------------------------------------------------------------- |
| emptyDescendReady  | number  | 자식 준비 검사를 통과해 하강했는데 그 서브트리가 아무것도 그리지 못한 수.                      |
| emptyDescendHold   | number  | 정제 유지로 하강했는데 그 서브트리가 아무것도 그리지 못한 수.                               |
| emptyDump          | string  | 빈 하강 노드와 자식들의 상태 덤프(프레임당 앞쪽 몇 건만 기록).                                |
| refineUnset        | number  | 정제 방식이 ADD/REPLACE 어느 분기에도 속하지 않은 노드 수.                                |
| exclFrustumNoVol   | number  | 프러스텀 밖 판정 중 바운딩 볼륨이 없는 노드 수.                                         |
| proxySkipDrawLevel | number  | 중첩 타일셋 프록시가 루트 KEEP 게이트에 막힌 수.                                         |
| childEmptyPartial  | number  | 형제 중 일부만 그리지 못한 수(부분 구멍).                                              |
| ancestorFill       | number  | 순회가 조상 채움으로 넣은 타일 수(채움 전용 처리로 내려간 타일은 포함되지 않음).        |
| fillBubbled        | number  | `ancestorFill` 가운데 직속 자식이 아니라 손자 이하에서 올라온 구멍(콘텐츠 없는 노드 아래에서 데이터를 기다리는 자리) 때문에 넣은 채움 수. |
| holeTop            | number  | 1이면 루트까지 올라가도 콘텐츠를 가진 조상이 없어 못 덮은 구멍이 남았다는 뜻입니다(그 자리는 검게 보임). |
| priorityMarked     | number  | 이번 프레임에 요청을 앞당기도록 표시한 노드 수(정제 유지 중인 조상 아래에서 데이터를 기다리는 보이는 노드).  |
| prioritySent       | number  | 우선 요청으로 보낸 수(누적).                                                         |
| priorityOverCap    | number  | `prioritySent` 가운데 동시 요청 상한 위 예약분으로 보낸 수(누적).                      |
| requestFailed      | number  | 콘텐츠(b3dm / glb / i3dm / pnts) 요청 실패 수(누적, 전체 레이어 합). 실패한 요청은 1초부터 두 배씩(최대 30초) 간격을 두고 다시 보냅니다. |
| jsonSkipHorizon    | number  | 지평선 밖이라 요청하지 않은 중첩 타일셋(json) 수.                                       |
| nearPlane          | number  | 렌더에 쓰인 근평면 거리.                                                              |
| farPlane           | number  | 렌더에 쓰인 원평면 거리.                                                              |
| heightRelTerrain   | number  | 지형 기준 카메라 높이(진단용).                                                        |
| loadBaseDist       | number  | 로딩 기준 거리(진단용).                                                              |
| rootCulled         | number  | 이번 프레임에 루트가 프러스텀 밖으로 판정되었는지(0 또는 1).                                 |
| rootDrawLevel      | number  | 루트의 드로우 레벨.                                                                   |
| proxyDescend       | number  | 중첩 타일셋으로 정상 하강한 수.                                                        |
| proxyNullRoot      | number  | 타일셋은 있으나 json이 아직 도착하지 않은(루트 없음) 수.                                   |
| proxyToken         | number  | 토큰 요청 중인 수.                                                                    |
| curTilt            | number  | 렌더에 쓰인 실제 틸트(목표 틸트와 비교용).                                                |

**b3dm 배치 테이블 (feature 피킹/추출)**

> 모두 누적값이며 전체 레이어 합입니다. 워커 경로는 파싱 결과를 응답 헤더로 받아 세고, 동기 경로(`tileParse` off / 워커 폴백)는 동기 로더가 셉니다.

| Name              | Type   | Description                                                                                       |
| ----------------- | ------ | ------------------------------------------------------------------------------------------------- |
| batchTiles        | number | 배치 테이블 속성을 읽은 b3dm 수.                                                                    |
| batchFaces        | number | `_BATCHID`에서 정점 대응을 만든 (메시, 면) 수. 면이 둘 이상인 타일이 있으면 `batchTiles`보다 큽니다.  |
| batchRanges       | number | `_BATCHID`에서 만든 정점 범위(= feature) 수.                                                        |
| batchIndexRanges  | number | feature별 삼각형 인덱스 구간 수(하이라이트가 부분 그리기로 그릴 구간). 폴백 면 등 때문에 `batchRanges`와 같다는 보장이 없어, 같은 데이터셋의 기준선으로만 쓰십시오. |
| batchSpanChecked  | number | 엔진이 타일을 적용할 때 (메시, 면) 대응을 엔진 기하와 대조한 면 수. 정상이면 `batchFaces`와 같습니다. 0이면 `batchSpanMismatch == 0`은 아무것도 증명하지 못합니다(검증이 안 돈 것). |
| batchSpanMismatch | number | 위 대조에서 어긋나 버린 면 수. 정상 데이터에서는 0이며 0이 아니면 정점 키가 어긋난 것입니다.         |
| discardKeptForBatch | number | 정점→batchId 대응이 있는 배치 테이블 때문에 `discardVertexData`를 무시하고 정점을 남긴 타일 수. `discardVertexData`를 켰는데 0이면 아직 표를 가진 타일이 적용되지 않았거나 표 없는 타일만 받은 것입니다. |

**feature 선택 유지 (LOD가 바뀌어도 같은 건물 유지)** ([setTileFeatureIdentityKey](jslayer.md#gettilefeatureidentitykey-settilefeatureidentitykey-key-string))

| Name              | Type   | Description                                                                                   |
| ----------------- | ------ | --------------------------------------------------------------------------------------------- |
| featureNames      | number | 지금 이 레이어에서 선택된 건물 이름 수(선택 목록에서 파생한 것 + 고아). 선택이 없으면 0.            |
| featureOrphans    | number | 그 가운데 고아 이름 수. 선택을 들던 타일이 해제됐고 그 건물을 가진 타일이 아직 그려지지 않은 상태입니다. |
| featureReanchored | number | 타일이 고아 이름을 넘겨받아 선택 목록에 다시 올린 횟수(누적).                                    |
| featureGeneration | number | 선택 이름 집합이 바뀐 횟수(누적). 타일은 이 값이 바뀔 때만 하이라이트를 다시 만듭니다.             |
| highlightRebuilds | number | 타일이 하이라이트를 다시 만든 횟수(누적). 선택이 안 바뀌는 동안에는 오르지 않아야 합니다.          |
