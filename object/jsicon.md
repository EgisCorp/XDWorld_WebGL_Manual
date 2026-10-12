---
description: 텍스처로 사용되는 아이콘 개체입니다. [JSSymbol](./jssymbol.md) 클래스 객체로 등록하여 사용하며, 각 아이콘은 등록 시 고유 명칭으로 설정됩니다. 고유 명칭은 중복하여 등록할 수 없습니다.
---

# JSIcon

> Module.getSymbol API를 생성합니다.

```javascript
var symbol = Module.getSymbol();
symbol.insertIcon(/*..parameter*/);
var icon = symbol.getIcon("ID");
```

## Function

### getId() → string

> 객체의 고유 명칭을 반환 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strKey = object.getId();
```

{% endtab %}
{% endtabs %}

### getReferenceCount() → number

> JSIcon을 참조 중인 오브젝트 수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number(0 ~ ): 참조된 오브젝트 수.
    -   -1: 반환 실패.
    -   실패 조건
        -   JSIcon이 정상적으로 생성되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var icon = Module.getSymbol().getIcon("mapIcon");
var refCount = icon.getReferenceCount();
```

{% endtab %}
{% endtabs %}

### getBoundaryRect() → [JSAABBox3D](../core/jsaabbox3d.md)

> 아이콘(Normal) 텍스처 크기를 기반으로 한 경계 박스를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSAABBox3D](../core/jsaabbox3d.md): min(0, 0, 0), max(텍스처 width, 텍스처 height, 0)로 설정된 박스.
    -   [JSAABBox3D](../core/jsaabbox3d.md): 텍스처가 없는 경우 min, max가 모두 (0, 0, 0)으로 초기화된 박스.

{% endtab %}
{% tab title="Template" %}

```javascript
var box = icon.getBoundaryRect();
```

{% endtab %}
{% endtabs %}

### getNormalSize() → [JSSize2D](../core/jssize2d.md)

> Normal 아이콘 텍스처의 크기(width, height)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSSize2D](../core/jssize2d.md): 텍스처 크기.
    -   [JSSize2D](../core/jssize2d.md): 텍스처가 없는 경우 width, height가 모두 0으로 초기화된 값.

{% endtab %}
{% tab title="Template" %}

```javascript
var size = icon.getNormalSize();
```

{% endtab %}
{% endtabs %}

### getHGSize() → [JSSize2D](../core/jssize2d.md)

> 강조(Highlight) 아이콘 텍스처의 크기(width, height)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSSize2D](../core/jssize2d.md): 텍스처 크기.
    -   [JSSize2D](../core/jssize2d.md): 텍스처가 없는 경우 width, height가 모두 0으로 초기화된 값.

{% endtab %}
{% tab title="Template" %}

```javascript
var size = icon.getHGSize();
```

{% endtab %}
{% endtabs %}

### setNormalIconByImageData(imageData, width, height) → boolean

> canvas의 getImageData 등으로 얻은 byte 배열 데이터를 기반으로 Normal 아이콘 텍스처를 생성합니다.
>
> 이 아이콘이 텍스처를 직접 소유하며, 이 아이콘을 [JSPoint.setIcon(icon)](jspoint.md#seticon-icon-boolean)으로 여러 POI에 설정하면 같은 텍스처를 공유합니다(함수를 다시 호출하면 이전에 만든 텍스처는 해제됨). 엔진의 POI 텍스처 16비트 모드가 켜져 있으면(iOS 환경에서 자동으로 켜짐) 메모리를 절반으로 줄이기 위해 RGBA4444로 변환하여 올립니다. 필터링 없이 텍셀:픽셀 1:1로 그려집니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type          | Description                             |
| --------- | ------------- | ---------------------------------------- |
| imageData | Uint8Array    | 이미지 픽셀 byte 배열 데이터(픽셀당 R, G, B, A 순서 4byte. canvas `getImageData().data` 형식). 길이가 `width x height x 4` 이상이어야 합니다. |
| width     | number        | 이미지 가로 크기(px).                    |
| height    | number        | 이미지 세로 크기(px).                    |

-   Return
    -   true: 텍스처 생성 성공.
    -   false: 텍스처 생성 실패.
    -   실패 조건
        -   맵이 정상적으로 로드되지 않은 경우, 또는 월드와 연결되지 않은 아이콘인 경우(`new Module.JSIcon()`으로 직접 만든 아이콘은 사용할 수 없으며, [JSSymbol.getIcon(id)](jssymbol.md#geticon-id-jsicon)로 얻거나 `Module.createIcon()`으로 만든 아이콘을 사용).
        -   width 또는 height가 0 이하인 경우.
        -   imageData의 길이가 1 미만이거나 `width x height x 4`보다 작은 경우(픽셀 데이터 부족).
        -   텍스처 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var ctx = canvas.getContext("2d");
var imgData = ctx.getImageData(0, 0, width, height);
icon.setNormalIconByImageData(imgData.data, width, height);
```

{% endtab %}
{% endtabs %}

### setNormalIconByCompressedData(data, format, width, height) → boolean

> 압축 텍스처 데이터(BC3, ASTC 등)로 Normal 아이콘 텍스처를 생성합니다. [JSPoint.setImageCompressed(data, format, width, height)](jspoint.md#setimagecompressed-data-format-width-height-boolean)와 같은 검증과 업로드를 거치되, 텍스처를 이 아이콘이 소유하므로 [JSPoint.setIcon(icon)](jspoint.md#seticon-icon-boolean)으로 여러 POI에 설정하면 같은 텍스처를 공유합니다(같은 라벨을 수천 개 만들 때 텍스처와 메모리를 1개분으로 줄일 수 있음).
>
> 변환 없이 압축 블록을 그대로 GPU에 업로드합니다. 압축 인코딩은 호출자(예: 워커)가 미리 수행해야 합니다. 필터링 없이 텍셀:픽셀 1:1로 그려집니다. 함수를 다시 호출하면 이전에 만든 텍스처는 해제됩니다.
>
> 입력 변수값(format)은 숫자가 아닌 이름 문자열이며 대소문자를 구분하지 않습니다. 기기가 해당 포맷의 WebGL 확장을 지원하지 않으면 실패하므로, 실패 시 [setNormalIconByImageData(imageData, width, height)](jsicon.md#setnormaliconbyimagedata-imagedata-width-height-boolean)로 대체하십시오. 입력 변수값(data)의 크기는 `ceil(width/블록가로) × ceil(height/블록세로) × 블록당 바이트 수`와 정확히 같아야 합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type       | Description                                  |
| :----- | :--------- | :------------------------------------------- |
| data   | Uint8Array | 압축 텍스처 블록 데이터.                     |
| format | string     | 압축 포맷 이름 (아래 표 참고).               |
| width  | number     | 이미지 너비(px). 0보다 커야 합니다.          |
| height | number     | 이미지 높이(px). 0보다 커야 합니다.          |

**format 목록**

| format                | 블록 크기 | 블록당 바이트 | 필요한 WebGL 확장                   |
| :-------------------- | :-------- | :------------ | :---------------------------------- |
| "bc3", "dxt5"         | 4×4       | 16            | WEBGL_compressed_texture_s3tc       |
| "bc1", "dxt1"         | 4×4       | 8             | WEBGL_compressed_texture_s3tc       |
| "bc7"                 | 4×4       | 16            | EXT_texture_compression_bptc        |
| "etc2", "etc2rgba"    | 4×4       | 16            | WEBGL_compressed_texture_etc        |
| "etc2rgb"             | 4×4       | 8             | WEBGL_compressed_texture_etc        |
| "astc4x4"             | 4×4       | 16            | WEBGL_compressed_texture_astc       |
| "astc6x6"             | 6×6       | 16            | WEBGL_compressed_texture_astc       |
| "astc8x8"             | 8×8       | 16            | WEBGL_compressed_texture_astc       |

-   Return
    -   true: 텍스처 생성 성공.
    -   false: 텍스처 생성 실패.
    -   실패 조건
        -   월드와 연결되지 않은 아이콘인 경우(`new Module.JSIcon()`으로 직접 만든 아이콘은 사용할 수 없으며, [JSSymbol.getIcon(id)](jssymbol.md#geticon-id-jsicon)로 얻거나 `Module.createIcon()`으로 만든 아이콘을 사용).
        -   width 또는 height가 0 이하인 경우.
        -   알 수 없는 format 이름인 경우.
        -   기기가 해당 포맷의 WebGL 확장을 지원하지 않는 경우.
        -   data 크기가 포맷과 이미지 크기로 계산한 크기와 다른 경우.
        -   텍스처 생성/업로드에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
// 400x128 BC3 이미지: (400/4) * (128/4) * 16 = 51,200 bytes
let icon = Module.createIcon();
if (icon.setNormalIconByCompressedData(bc3Bytes, "bc3", 400, 128)) {
    // 같은 아이콘(텍스처)을 여러 POI가 공유
    poi1.setIcon(icon);
    poi2.setIcon(icon);
} else {
    // 미지원 기기 등에서는 RGBA 데이터로 대체
    icon.setNormalIconByImageData(rgbaBytes, 400, 128);
}
```

{% endtab %}
{% endtabs %}

### getImageData() → Uint8Array

> Normal 아이콘 텍스처의 픽셀 데이터를 byte 배열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   Uint8Array: 텍스처의 픽셀 byte 배열 데이터.
    -   null: 반환 실패.
    -   실패 조건
        -   Normal 텍스처가 존재하지 않는 경우.
        -   텍스처 포맷이 압축 포맷인 경우(비트맵으로 변환 불가).
        -   이미지 데이터 크기가 0인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var data = icon.getImageData();
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getScale(), setScale(scale) → number

> 아이콘(Normal)의 배율(스케일)을 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| scale | number | 아이콘 배율. |

-   Return
    -   number: 설정된 배율 값.
    -   number(1.0): Normal 텍스처가 존재하지 않는 경우 기본값 1.0 반환.

{% endtab %}
{% tab title="Template" %}

```javascript
var scale = icon.getScale();
// ... or ...
icon.setScale(1.5);
```

{% endtab %}
{% endtabs %}

### getHighlightScale(), setHighlightScale(scale) → number

> 강조(Highlight) 아이콘의 배율(스케일)을 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| ----- | ------ | ------------ |
| scale | number | 아이콘 배율. |

-   Return
    -   number: 설정된 배율 값.
    -   number(1.0): 강조 텍스처가 존재하지 않는 경우 기본값 1.0 반환.

{% endtab %}
{% tab title="Template" %}

```javascript
var scale = icon.getHighlightScale();
// ... or ...
icon.setHighlightScale(1.5);
```

{% endtab %}
{% endtabs %}

### getHighlightIcon(), setHighlightIcon(imageFile) → string

> 강조(Highlight) 아이콘 이미지의 경로/이름을 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                                                                                                                                                    |
| --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| imageFile | string | <p>강조 아이콘 이미지 경로/이름.<br>"http://" 로 시작하는 경우: 원격 URL 이미지로 처리.<br>"#" 로 시작하는 경우: 이미 등록된 아이콘 이름(문자열)으로 처리.<br>그 외: 입력값을 경로 및 파일명으로 그대로 사용.</p> |

-   Return
    -   string: 등록된 강조 아이콘의 경로+파일명, 또는 텍스처 이름.
    -   string(""): 강조 텍스처가 존재하지 않는 경우 빈 문자열 반환.

{% endtab %}
{% tab title="Template" %}

```javascript
var strIcon = icon.getHighlightIcon();
// ... or ...
icon.setHighlightIcon("hgIcon.png");
```

{% endtab %}
{% endtabs %}

### getNormalIcon(), setNormalIcon(imageFile) → string

> Normal 아이콘 이미지의 경로/이름을 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                   |
| --------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| imageFile | string | <p>Normal 아이콘 이미지 경로/이름.<br>"http://" 로 시작하는 경우: 원격 URL 이미지로 처리.<br>"#" 로 시작하는 경우: 이미 등록된 아이콘 이름(문자열)으로 처리.<br>그 외: 입력값을 경로 및 파일명으로 그대로 사용.</p> |

-   Return
    -   string: 등록된 Normal 아이콘의 경로+파일명, 또는 텍스처 이름.
    -   string(""): Normal 텍스처가 존재하지 않는 경우 빈 문자열 반환.

{% endtab %}
{% tab title="Template" %}

```javascript
var strIcon = icon.getNormalIcon();
// ... or ...
icon.setNormalIcon("mapIcon.png");
```

{% endtab %}
{% endtabs %}

### getHotspot(), setHotspot(hotspot) → [JSVector2D](../core/jsvector2d.md)

> Normal 아이콘 텍스처의 클릭 기준점(Hotspot, 픽셀 좌표)을 반환/설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type                                   | Description                  |
| ------- | --------------------------------------- | ----------------------------- |
| hotspot | [JSVector2D](../core/jsvector2d.md)    | 아이콘 기준점(x, y, 픽셀 단위). |

-   Return
    -   [JSVector2D](../core/jsvector2d.md): 설정된 hotspot 좌표.
    -   [JSVector2D](../core/jsvector2d.md): Normal 텍스처가 존재하지 않는 경우 x, y가 모두 0으로 초기화된 값.

{% endtab %}
{% tab title="Template" %}

```javascript
var hotspot = icon.getHotspot();
// ... or ...
icon.setHotspot(new Module.JSVector2D(10, 10));
```

{% endtab %}
{% endtabs %}
