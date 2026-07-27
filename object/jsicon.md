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

{% tabs %}
{% tab title="Information" %}

| Name      | Type          | Description                             |
| --------- | ------------- | ---------------------------------------- |
| imageData | Uint8Array    | 이미지 픽셀 byte 배열 데이터(A8R8G8B8). |
| width     | number        | 이미지 가로 크기(px).                    |
| height    | number        | 이미지 세로 크기(px).                    |

-   Return
    -   true: 텍스처 생성 성공.
    -   false: 텍스처 생성 실패.
    -   실패 조건
        -   맵이 정상적으로 로드되지 않은 경우.
        -   imageData의 길이가 1 이하인 경우(픽셀 데이터 없음).
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
