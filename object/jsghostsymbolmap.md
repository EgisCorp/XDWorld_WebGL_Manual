---
description: 지도 내 고스트 심볼 객체를 등록 관리하기 위한 API 입니다.
---

# JSGhostSymbolMap

> Module.getGhostSymbolMap() API를 생성합니다.

```javascript
var object = Module.getGhostSymbolMap();
```

## Function

### addGhostSymbolBy3DS(id, url, name) → boolean

> 3ds 포맷 파일을 고스트 심볼 모델로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | 고스트 심볼 고유 명칭. |
| url  | string | 3ds 파일 위치 경로.    |
| name | string | 3ds 파일 명칭.         |

-   Return
    -   true: 등록 성공.
    -   false: 등록 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();
ghostSymbolMap.addGhostSymbolBy3DS("STREET_LIGHT", "./data", "StreetLight");
```

{% endtab %}
{% endtabs %}

### addGhostSymbolByXDO(id, url, name, version) → boolean

> xdo 포맷 파일을 고스트 심볼 모델로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                               |
| ------- | ------ | ------------------------------------------------------------------------- |
| id      | string | 고스트 심볼 고유 명칭.                                                    |
| url     | string | xdo 파일 위치 경로.                                                       |
| name    | string | xdo 파일 명칭.                                                            |
| version | bool   | <p>xdo 포맷 버전.<br>true: Version 3.0.0.2.<br>false: Version 3.0.0.1.<p> |

-   Return
    -   true: 등록 성공.
    -   false: 등록 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();
ghostSymbolMap.addGhostSymbolByXDO("STREET_LIGHT", "./data", "StreetLight", false);
```

{% endtab %}
{% endtabs %}

### insert(option) → string

> 3ds 포맷 파일을 고스트 심볼 모델로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                                                 | Description     |
| ------ | ------------------------------------------------------------------------------------ | --------------- |
| option | [JSGhostSymbolMap.InsertOptions](jsghostsymbolmap.md#jsghostsymbolmap.insertoptions) | 등록 속성 정보. |

-   Return
    -   "success": 등록 성공.
    -   "request failed": 3ds 파일 네트워크 요청 실패.
    -   이외 예외처리에 대한 문자열 메시지 반환.
-   Sample
    -   function init 참조.
    -   [Sandbox_Ghost Symbol Editing](https://sandbox.egiscloud.com/code/main.do?id=object_ghost_symbol_edit)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGhostSymbolTexture(id, url, name) → boolean

> 고스트 심볼 모델의 이미지를 설정합니다.
>
> 설정된 이미지는 고스트 심볼 모델에 적용한 uv(텍스쳐) 좌표에 따라 가시화 됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                             |
| ---- | ------ | --------------------------------------- |
| id   | string | 고스트 심볼 고유 명칭.                  |
| url  | string | 이미지 파일 위치 경로.                  |
| name | string | 이미지 파일 명칭(확장자 포함하여 입력). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   입력 변수값(id)에 해당되는 고스트심볼 모델이 존재하지 않는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();
ghostSymbolMap.setGhostSymbolTexture(e.strGhostSymbolKey, "./data", "StreetLightTexture.jpg");
```

{% endtab %}
{% endtabs %}

### setModelTexture(option) → string

> 등록된 고스트 심볼 모델를 구성하는 face 별 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                                             | Description       |
| ------ | -------------------------------------------------------------------------------- | ----------------- |
| option | [JSGhostSymbolMap.LoadTexture](jsghostsymbolmap.md#jsghostsymbolmap.loadtexture) | 이미지 속성 정보. |

-   Return
    -   "success": 설정 성공.
    -   "failed load texture": 이미지 파일 네트워크 요청 실패.
    -   이외 예외처리에 대한 문자열 메시지 반환.
-   Sample
    -   function init 참조.
    -   [Sandbox_Ghost Symbol Editing](https://sandbox.egiscloud.com/code/main.do?id=object_ghost_symbol_edit)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setModelFaceColor(id, index, color) → boolean

> 등록된 고스트 심볼 모델를 구성하는 face 별 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description            |
| ----- | ----------------------------- | ---------------------- |
| id    | string                        | 고스트 심볼 고유 명칭. |
| index | number                        | face 인덱스.           |
| color | [JSColor](../core/jscolor.md) | 설정 색상.             |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setModelFaceTextureRepeatU(id, index, repeat) → boolean

> 등록된 고스트 심볼 모델를 구성하는 face 가로 방향 이미지 패턴 가시화 유무를 설정합니다.
>
> uv(텍스쳐) 좌표 범위(0.0 ~ 1.0)를 벗어난 영역에 대한 가시화 방법을 설정합니다.
>
> 가시화 옵션
>
> -   GL_REPEAT : 0.0 ~ 1.0 범위를 벗어난 면에 대해서 이미지를 반복적으로 패턴화.
> -   GL_CLAMP_TO_EDGE : 0.0 ~ 1.0 범위를 벗어난 면에 이미지 가시화 금지

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                                  |
| ------ | ------- | ------------------------------------------------------------ |
| id     | string  | 고스트 심볼 고유 명칭.                                       |
| index  | number  | face 인덱스.                                                 |
| repeat | boolean | <p>true: GL_REPEAT 설정.<br>false: GL_CLAMP_TO_EDGE 설정.<p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setModelFaceTextureRepeatV(id, index, repeat) → boolean

> 등록된 고스트 심볼 모델를 구성하는 face 세로 방향 이미지 패턴 가시화 유무를 설정합니다.
>
> uv(텍스쳐) 좌표 범위(0.0 ~ 1.0)를 벗어난 영역에 대한 가시화 방법을 설정합니다.
>
> 가시화 옵션
>
> -   GL_REPEAT : 0.0 ~ 1.0 범위를 벗어난 면에 대해서 이미지를 반복적으로 패턴화.
> -   GL_CLAMP_TO_EDGE : 0.0 ~ 1.0 범위를 벗어난 면에 이미지 가시화 금지

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                                  |
| ------ | ------- | ------------------------------------------------------------ |
| id     | string  | 고스트 심볼 고유 명칭.                                       |
| index  | number  | face 인덱스.                                                 |
| repeat | boolean | <p>true: GL_REPEAT 설정.<br>false: GL_CLAMP_TO_EDGE 설정.<p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getModelFaceCount(id) → number

> 등록된 고스트 심볼 모델를 구성하는 face 갯수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | 고스트 심볼 고유 명칭. |

-   Return
    -   number: face 갯수.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### isExistID(id) → boolean

> 등록된 고스트 심볼 모델 존재 유무를 확인합니다.
>
> 입력 변수값(id)와 동일한 명칭을 가진 고스트 심볼 모델 존재 유무를 확인합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | 고스트 심볼 고유 명칭. |

-   Return
    -   true: 고스트 심볼 있음.
    -   false: 고스트 심볼 없음.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getGhostSymbolSize(id) → [JSSize3D](../core/jssize3d.md)

> 등록된 고스트 심볼 모델 크기를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | 고스트 심볼 고유 명칭. |

-   Return
    -   [JSSize3D](../core/jssize3d.md): 반환 성공(x,y,z).
    -   null: 반환 실패.
-   Sample
    -   function createGhostSymbol 참조.
    -   [Sandbox_Ghost Symbol Editing](https://sandbox.egiscloud.com/code/main.do?id=object_ghost_symbol_edit)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSGhostSymbolMap.InsertOptions

> Options for registering a 3D model object as a ghost symbol.

| Name     | Type     | Attributes | Default | Description                     |
| -------- | -------- | ---------- | ------- | ------------------------------- |
| id       | string   |            |         | 고스트 심볼 고유 명칭.          |
| url      | string   |            |         | 고스트 심볼 모델 파일 요청 URL. |
| format   | string   | optional   |         | 요청 파일 포맷(3ds만 지원).     |
| callback | function | optional   |         | 등록 완료 시 동작하는 CallBack  |

#### JSGhostSymbolMap.LoadTexture

> Options for registering face textures for the registered ghost symbol object.

| Name     | Type     | Attributes | Default | Description                       |
| -------- | -------- | ---------- | ------- | --------------------------------- |
| id       | number   |            |         | 고스트 심볼 고유 명칭.            |
| url      | boolean  |            |         | 고스트 심볼 모델 이미지 요청 URL. |
| index    | number   | optional   | 0       | 참조 객체 face Index.             |
| callback | function | optional   |         | 등록 완료 시 동작하는 CallBack    |
