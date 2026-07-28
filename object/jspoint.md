---
description: 지도 내 POI 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSPoint

> Module.createPoint() API를 생성합니다.

```javascript
var object = Module.createPoint("ID");
```

## Properties

| Name            | Type                                  | Description                                |
| --------------- | ------------------------------------- | ----------------------------------------- |
| image_scale     | 이미지 스케일                          | 1.0을 기본으로 이미지의 스케일을 조정        |

## Function

### getAltitude() → number

> POI 객체의 중심 좌표 중 고도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 반환 성공(meters 단위).

{% endtab %}
{% tab title="Template" %}

```javascript
var dAltitude = point.getAltitude();
```

{% endtab %}
{% endtabs %}

### getFontColor() → [JSColor](../core/jscolor.md)

> POI 객체를 구성하는 문자의 색상을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSColor](../core/jscolor.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var fontColor = object.getFontColor();
```

{% endtab %}
{% endtabs %}

### getFontName() → string

> POI 객체를 구성하는 문자의 폰트를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var fontName = object.getFontName();
```

{% endtab %}
{% endtabs %}

### getFontOutColor() → [JSColor](../core/jscolor.md)

> POI 객체를 구성하는 문자의 외각선 색상을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   ([JSColor](../core/jscolor.md)): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var fontOutLineColor = object.getFontOutColor();
```

{% endtab %}
{% endtabs %}

### getFontSize() → number

> POI 객체를 구성하는 문자의 크기를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number (0 or higher): 반환 성공.
    -   number (-1): 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var fontSize = object.getFontSize();
```

{% endtab %}
{% endtabs %}

### getFontWeight() → number

> POI 객체를 구성하는 문자의 두께를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number (0 or higher): 반환 성공.
    -   number (-1): 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var fotnWeight = object.getFontWeight();
```

{% endtab %}
{% endtabs %}

### getHighlightIcon() → [JSIcon](./jsicon.md)

> POI 객체를 구성하는 하이라이트 이미지를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSIcon](./jsicon.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var icon_hg = object.getHighlightIcon();
```

{% endtab %}
{% endtabs %}

### getIcon() → [JSIcon](./jsicon.md)

> POI 객체를 구성하는 이미지를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSIcon](./jsicon.md): 반환 성공.

{% endtab %}
{% tab title="Template" %}

```javascript
var icon_normal = object.getIcon();
```

{% endtab %}
{% endtabs %}

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

### getLatitude() → number

> > POI 객체의 중심 좌표 중 위도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 반환 성공(degrees 단위).

{% endtab %}
{% tab title="Template" %}

```javascript
var dLatitude = point.getLatitude();
```

{% endtab %}
{% endtabs %}

### getLongitude() → number

> > POI 객체의 중심 좌표 중 경도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 반환 성공(degrees 단위).

{% endtab %}
{% tab title="Template" %}

```javascript
var dLongitude = point.getLongitude();
```

{% endtab %}
{% endtabs %}

### getPosition() → [JSVector3D](../core/jsvector3d.md)

> POI 객체의 중심 좌표(경도, 위도, 고도)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var vPos = point.getPosition();
```

{% endtab %}
{% endtabs %}

### getVisibleRangeActivate() → boolean

> POI 객체의 가시 범위 값을 사용 유무를 반환합니다.
>
> 가시 범위 값이 비활성화 되면 POI 객체의 가시 범위는 POI 객체가 소속된 레이어의 가시 범위값을 참조 받습니다.
>
> 서비스 레이어를 통해 생성된 POI 객체는 가시 범위값을 설정할 수 없습니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 가시 범위 사용.
    -   false: 레이어 가시 범위 사용.
    -   실패 조건
        -   서비스 레이어를 통해 생성된 POI 객체인 경우.
        -   POI 객체가 생성되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var bActive = object.getVisibleRangeActivate();
```

{% endtab %}
{% endtabs %}

### getVisibleRangeMax() → number

> POI 객체의 최대 가시범위 값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 반환 성공.
    -   실패 조건
        -   -999.0: POI 객체가 생성되지 않은 경우.
        -   -998.0: POI 객체가 서비스 레이어에서 생성 된 경우.
        -   -997.0: 가시범위 설정이 비활성화 상태인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var rangeMax = object.getVisibleRangeMax();
```

{% endtab %}
{% endtabs %}

### getVisibleRangeMin() → number

> POI 객체의 최소 가시범위 값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 반환 성공.
    -   실패 조건
        -   -999.0: POI 객체가 생성되지 않은 경우.
        -   -998.0: POI 객체가 서비스 레이어에서 생성 된 경우.
        -   -997.0: 가시범위 설정이 비활성화 상태인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var rangeMin = object.getVisibleRangeMin();
```

{% endtab %}
{% endtabs %}

### isExistHighlightIcon() → boolean

> POI 객체를 구성하는 하이라이트 이미지 설정 유무를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 하이라이트 이미지 설정.
    -   false: 하이라이트 이미지 미설정.

{% endtab %}
{% tab title="Template" %}

```javascript
var bExistHighlightIcon = object.isExistHighlightIcon();
```

{% endtab %}
{% endtabs %}

### isExistIcon() → boolean

> POI 객체를 구성하는 이미지 설정 유무를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 이미지 설정.
    -   false: 이미지 미설정.

{% endtab %}
{% tab title="Template" %}

```javascript
var bExistNormalIcon = object.isExistIcon();
```

{% endtab %}
{% endtabs %}

### setAltitude(alt) → boolean

> POI 객체의 고도를 설정합니다.
>
> POI 객체의 중심 좌표(경도, 위도)는 유지합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| alt  | number | 해발고도(meters 단위). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
point.setAltitude(50.0);
```

{% endtab %}
{% endtabs %}

### setFontStyle(name, size, weight, fill_color, outline_color) → boolean

> POI 객체를 구성하는 문자 스타일을 설정합니다.
>
> 폰트, 크기, 두께, 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type                          | Description       |
| :------------ | :---------------------------- | :---------------- |
| name          | string                        | 폰트 이름.        |
| size          | number                        | 텍스트 크기.      |
| weight        | number                        | 텍스트 굵기.      |
| fill_color    | [JSColor](../core/jscolor.md) | 텍스트 색상.      |
| outline_color | [JSColor](../core/jscolor.md) | 텍스트 외곽 색상. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createPoint 참조.
    -   [Sandbox_Path Analysis](https://sandbox.egiscloud.com/code/main.do?id=analysis_line_path_distance)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setHighlightIcon(icon) → boolean

> POI 객체를 구성하는 하이라이트 이미지 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                  | Description |
| ---- | --------------------- | ----------- |
| icon | [JSIcon](./jsicon.md) | 아이콘.     |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var icon_hg = Module.getSymbol().getIcon("Icon_hg");
object.setHighlightIcon(icon_hg);
```

{% endtab %}
{% endtabs %}

### setIcon(icon) → boolean

> POI 객체를 구성하는 이미지 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                  | Description |
| ---- | --------------------- | ----------- |
| icon | [JSIcon](./jsicon.md) | 아이콘.     |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var icon = Module.getSymbol().getIcon("Icon2");
object.setIcon(icon);
```

{% endtab %}
{% endtabs %}

### setImage(data, width, height) → boolean

> POI 객체를 구성하는 이미지 설정합니다.
>
> 입력 변수값(data)은 Uint8Array 기반의 바이너리 배열 데이터 입니다.
>
> 입력 변수값(width, height)은 이미지의 실제 크기를 입력 받습니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description          |
| :----- | :----- | :------------------- |
| data   | array  | 이미지 픽셀 값 배열. |
| width  | number | 이미지 너비.         |
| height | number | 이미지 높이.         |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   입력 변수값(data) 값이 null인 경우.
        -   입력 변수값(width, height) 값이 0 보다 작은 경우.
-   Sample
    -   function createPOI 참조.
    -   [Sandbox_POI](https://sandbox.egiscloud.com/code/main.do?id=object_point)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setLatitude(lat) → boolean

> POI 객체의 위도를 설정합니다.
>
> POI 객체의 중심 좌표(경도, 고도)는 유지합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description         |
| ---- | ------ | ------------------- |
| lat  | number | 경도(degrees 단위). |

-   Return

    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
point.setLatitude(35.1713096);
```

{% endtab %}
{% endtabs %}

### setLongitude(lon) → boolean

> POI 객체의 경도를 설정합니다.
>
> POI 객체의 중심 좌표(위도, 고도)는 유지합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description         |
| ---- | ------ | ------------------- |
| lon  | number | 위도(degrees 단위). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
point.setLongitude(129.1270931);
```

{% endtab %}
{% endtabs %}

### setLonLat(lon, lat) → boolean

> POI 객체의 경도, 위도를 설정합니다.
>
> POI 객체의 중심 좌표(고도)는 유지합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description         |
| :--- | :----- | :------------------ |
| lon  | number | 위도(degrees 단위). |
| lat  | number | 경도(degrees 단위). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
point.setLonLat(129.1270931, 35.1713096);
```

{% endtab %}
{% endtabs %}

### setPosition(position) → boolean

> POI 객체의 중심 좌표(경도, 위도, 고도)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                  |
| :------- | :---------------------------------- | :--------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 중심 좌표(경도, 위도, 고도). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createPOI 참조.
    -   [Sandbox_POI](https://sandbox.egiscloud.com/code/main.do?id=object_point)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPositionLine(length, color) → boolean

> POI 객체 중심좌표 방향으로 지형에서 수직한 직선 객체를 생성합니다.
>
> 입력 변수값(length)으로 직선을 길이가 생성됩니다.
>
> 입력 변수값(length)은 0보다 큰값이 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                          | Description  |
| :----- | :---------------------------- | :----------- |
| length | number                        | 직선을 길이. |
| color  | [JSColor](../core/jscolor.md) | 직선을 색상. |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   입력 변수값(length)이 0보다 작은 값이 설정된 경우.
-   Sample
    -   function createPOI 참조.
    -   [Sandbox_POI Line](https://sandbox.egiscloud.com/code/main.do?id=object_point_line)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setRenderToTerrainTexture(type) → boolean

> POI 객체를 RTT 가시화 방법으로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                     |
| :--- | :------ | :---------------------------------------------- |
| type | boolean | <p>true: RTT 가시화.<br>false: 일반 가시화.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createPOI 참조.
    -   [Sandbox_POI RTT](https://sandbox.egiscloud.com/code/main.do?id=object_point_rtt)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setText(text) → boolean

> > POI 객체를 구성하는 문자를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| :--- | :----- | :---------- |
| text | string | POI 문자.   |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function createPOI 참조.
    -   [Sandbox_POI](https://sandbox.egiscloud.com/code/main.do?id=object_point)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setVisibleRange(enable, min, max) → boolean

> POI 객체의 가시 범위 값 설정합니다.
>
> 최소값이 최대값보다 크면 자동으로 작은 값을 최소값으로, 큰 값을 최대값으로 자동 전환합니다.
>
> 서비스 레이어를 통해 생성된 POI 객체는 가시 범위값을 설정할 수 없습니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description     |
| :----- | :------ | :-------------- |
| enable | boolean | 값 활성화 유무. |
| min    | number  | 최소 가시거리.  |
| max    | number  | 최대 가시거리.  |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   서비스 레이어를 통해 생성된 POI 객체인 경우.
        -   POI 객체가 생성되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
object.setVisibleRange(true, 50.0, 20000.0);
```

{% endtab %}
{% endtabs %}

### isUserRegister() → boolean

> 서비스(외부 데이터) 레이어를 통해 생성된 POI 객체인지 여부를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 서비스 레이어를 통해 생성된 객체.
    -   false: 사용자 레이어 객체이거나, 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var isServiceObject = point.isUserRegister();
```

{% endtab %}
{% endtabs %}

### setTextMargin(marginX, marginY) → boolean

> POI 문자열이 표시되는 위치의 여백(현재 위치 기준 픽셀 오프셋)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description        |
| :------ | :----- | :--------------------- |
| marginX | number | X축 방향 여백(pixel). |
| marginY | number | Y축 방향 여백(pixel). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패(객체가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
point.setTextMargin(10, -10);
```

{% endtab %}
{% endtabs %}

### setRange(option) → boolean

> POI 객체의 가시 범위 및 텍스트 표시 범위를 설정합니다.
>
> [setVisibleRange()](jspoint.md#setvisiblerange-enable-min-max-boolean)의 확장판으로, 텍스트 표시 범위(textMin, textMax)를 별도로 지정할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type    | Description                                                    |
| :------- | :------ | :------------------------------------------------------------- |
| option   | object  | 가시 범위 옵션.                                                 |
| ↳ enable | boolean | 가시 범위 사용 여부(필수).                                       |
| ↳ min    | number(optional) | 최소 가시거리.                                         |
| ↳ max    | number(optional) | 최대 가시거리.                                         |
| ↳ textMin| number(optional) | 텍스트 최소 표시거리(생략 시 min 값과 동기화).         |
| ↳ textMax| number(optional) | 텍스트 최대 표시거리(생략 시 max 값과 동기화).         |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   객체가 없는 경우.
        -   option 또는 option.enable이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
point.setRange({ enable: true, min: 50.0, max: 20000.0, textMin: 100.0, textMax: 5000.0 });
```

{% endtab %}
{% endtabs %}

### releaseIcon() → boolean

> POI 객체가 참조하는 일반 이미지 텍스처의 참조를 해제합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 해제 성공.
    -   false: 해제 실패(객체가 없거나, 설정된 이미지가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
point.releaseIcon();
```

{% endtab %}
{% endtabs %}

### releaseHighlightIcon() → boolean

> POI 객체가 참조하는 하이라이트 이미지 텍스처의 참조를 해제합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 해제 성공.
    -   false: 해제 실패(객체가 없거나, 설정된 하이라이트 이미지가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
point.releaseHighlightIcon();
```

{% endtab %}
{% endtabs %}

### setBlinkColor(red, green, blue)

> POI 객체의 깜빡임(Blink) 효과 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| :---- | :----- | :---------------- |
| red   | number | 색상 R 값(0~255). |
| green | number | 색상 G 값(0~255). |
| blue  | number | 색상 B 값(0~255). |

{% endtab %}
{% tab title="Template" %}

```javascript
point.setBlinkColor(255, 0, 0);
```

{% endtab %}
{% endtabs %}

### setBlinkSize(size)

> POI 객체의 깜빡임(Blink) 효과 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description    |
| :--- | :----- | :----------------- |
| size | number | 깜빡임 효과 크기.  |

{% endtab %}
{% tab title="Template" %}

```javascript
point.setBlinkSize(20.0);
```

{% endtab %}
{% endtabs %}

### setBlinkSpeed(speed)

> POI 객체의 깜빡임(Blink) 효과 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | :----- | ----------------- |
| speed | number | 깜빡임 효과 속도. |

{% endtab %}
{% tab title="Template" %}

```javascript
point.setBlinkSpeed(1.0);
```

{% endtab %}
{% endtabs %}

### addScreenPosition(x, y) → boolean

> POI 객체의 화면상 표시 위치에 픽셀 오프셋을 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description        |
| :--- | :----- | ---------------------- |
| x    | number | X축 방향 화면 오프셋(pixel). |
| y    | number | Y축 방향 화면 오프셋(pixel). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패(객체가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
point.addScreenPosition(0, -20);
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getBlink(), setBlink(set) → boolean

> POI 객체의 깜빡임(Blink) 효과 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                    |
| :--- | :------ | :----------------------------------------------- |
| set  | boolean | <p>true: 깜빡임 효과 사용.<br>false: 미사용.</p> |

-   Return
    -   true: 깜빡임 효과 사용 상태.
    -   false: 미사용 상태(또는 객체가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
point.setBlink(true);
```

{% endtab %}
{% endtabs %}

### getRenderOrder(), setRenderOrder(order) → number

> POI 객체의 렌더링 순서(값이 클수록 나중에 그려짐)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                       |
| :---- | :----- | ------------------------------------- |
| order | number | 렌더링 순서 값(0 미만 입력 시 0으로 보정). |

-   Return
    -   number: 설정된 렌더링 순서 값(객체가 없으면 0).

{% endtab %}
{% tab title="Template" %}

```javascript
point.setRenderOrder(2);
```

{% endtab %}
{% endtabs %}

### color (property), setColor(color) → [JSColor](../core/jscolor.md)

> POI 이미지에 적용할 색상(틴트)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description |
| :---- | :----------------------------- | :---------- |
| color | [JSColor](../core/jscolor.md) | 적용할 색상.  |

{% endtab %}
{% tab title="Template" %}

```javascript
point.color = new Module.JSColor(255, 255, 0, 0);
```

{% endtab %}
{% endtabs %}

### imageScale, image_scale (property), setImageScale(scale) → number

> POI 이미지의 배율을 설정합니다. 기본값 1.0.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description   |
| :---- | :----- | ----------------- |
| scale | number | 이미지 배율(기본값 1.0). |

-   Return
    -   number: 설정된 이미지 배율(객체가 없으면 0.0).

{% endtab %}
{% tab title="Template" %}

```javascript
point.imageScale = 1.5;
```

{% endtab %}
{% endtabs %}

### zIndex, z_index (property), setZIndex(index) → number

> POI 객체의 Z-Index(렌더링 우선순위 값)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | :----- | ----------------- |
| index | number | Z-Index 값.       |

-   Return
    -   number: 설정된 Z-Index 값(객체가 없으면 0.0).

{% endtab %}
{% tab title="Template" %}

```javascript
point.zIndex = 1.0;
```

{% endtab %}
{% endtabs %}

### autoHeight (property), setautoHeight(set) → boolean

> POI 객체의 높이 자동 조절(지형 고도 자동 반영) 기능 사용 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                              |
| :--- | :------ | --------------------------------------------- |
| set  | boolean | <p>true: 자동 높이 조절 사용, false: 미사용.</p> |

-   Return
    -   true: 자동 높이 조절 사용 상태.
    -   false: 미사용 상태(또는 객체가 없는 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
point.autoHeight = true;
```

{% endtab %}
{% endtabs %}

### getDescription(), setDescription(desc) → string

> 객체에 대한 설명을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| desc | string | 설명 문자열. |

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strDesc = object.getDescription();
// ... or ...
object.setDescription("First Object.");
```

{% endtab %}
{% endtabs %}

### getHighlight(), setHighlight(highlight) → boolean

> POI 객체를 구성하는 하이라이트 이미지 사용 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description                                                              |
| --------- | ------- | ------------------------------------------------------------------------ |
| highlight | boolean | <p>true: 하이라이트 이미지 사용.<br>false: 하이라이트 이미지 미사용.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   POI 오브젝트가 null인 경우.
        -   Highlight 타입으로 설정된 아이콘이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var bHighlightUsed = object.getHighlight();
// ... or ...
object.setHighlight(true);
```

{% endtab %}
{% endtabs %}

### getName(), setName(name) → string

> 객체 이름을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 이름.  |

-   Return
    -   string: 객체 이름을 성공적을 반환
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setName("MyObject");
```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean

> 객체의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                        |
| ------- | ------- | -------------------------------------------------- |
| visible | boolean | <p>true: 객체 가시화.<br>false: 객체 비가시화.</p> |

-   Return
    -   true: 객체 가시화 상태.
    -   false: 객체 비가시화 상태.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setVisible(true);
```

{% endtab %}
{% endtabs %}
