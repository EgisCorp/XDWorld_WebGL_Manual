---
description: 지도 내 고스트 심볼 객체를 등록 관리하기 위한 API 입니다.
---

# JSGhostSymbolMap

> Module.getGhostSymbolMap() API를 생성합니다.

```javascript
var object = Module.getGhostSymbolMap();
```

## Function

### addGhostSymbolBy3DS(id, url, name, options) → boolean

> 3ds 포맷 파일을 고스트 심볼 모델로 등록합니다.
>
> 입력 변수값(options)으로 텍스처 기준 경로와 텍스처 자동 요청 여부를 지정할 수 있습니다. 4번째 인자는 바인딩상 필수이므로 옵션이 필요 없을 때는 `{}`(또는 `null`)를 전달하세요. 파일 요청은 비동기로 수행되며, 반환값은 요청 시작 여부일 뿐 파일 로드 결과가 아닙니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                 |
| ------- | ------ | --------------------------------------------------------------------------- |
| id      | string | 고스트 심볼 고유 명칭.                                                      |
| url     | string | 3ds 파일 위치 경로.                                                         |
| name    | string | 3ds 파일 명칭.                                                              |
| options | object | 등록 옵션 (아래 표 참고).                                                   |

**options 구조**

| Name            | Type    | Required | Default                | Description                                                                                       |
| --------------- | ------- | -------- | ---------------------- | ------------------------------------------------------------------------------------------------- |
| textureBasePath | string  |          | 3ds 파일 위치 경로(url) | 텍스처 파일을 요청할 기준 경로. 끝에 `/`가 없으면 자동으로 붙습니다.                              |
| autoLoadTexture | boolean |          | true                   | 모델 등록 시 텍스처를 자동으로 요청할지 여부. false이면 텍스처를 요청하지 않습니다.               |

-   Return
    -   true: 등록 성공.
    -   false: 등록 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();
ghostSymbolMap.addGhostSymbolBy3DS("STREET_LIGHT", "./data", "StreetLight", {});

// 텍스처를 별도 경로에서 받고, 자동 요청은 끄기
ghostSymbolMap.addGhostSymbolBy3DS("STREET_LIGHT2", "./data", "StreetLight", {
    textureBasePath: "./data/textures",
    autoLoadTexture: false,
});
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

### addGhostSymbolByGLB(id, url, name) → boolean

> glb 포맷 파일을 고스트 심볼 모델로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | 고스트 심볼 고유 명칭. |
| url  | string | glb 파일 위치 경로.    |
| name | string | glb 파일 명칭.         |

-   Return
    -   true: 등록 성공.
    -   false: 등록 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();
ghostSymbolMap.addGhostSymbolByGLB("MODEL_KEY", "./data", "model");
```

{% endtab %}
{% endtabs %}

### addGhostSymbolBy3DSbyJson(info) → string

> 3ds 포맷 파일을 JSON 옵션 정보로 고스트 심볼 모델로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
| ---- | ------ | ------------------- |
| info | object | 등록 옵션 정보.    |

**info 구조**

| Key      | Type     | Required | Description                        |
| -------- | -------- | -------- | ------------------------------------- |
| id       | string   | true     | 고스트 심볼 고유 명칭.               |
| file     | string   | true     | 3ds 파일 명(확장자 없이 입력).        |
| basePath | string   | true     | 3ds 파일 위치 경로.                   |
| complete | function | false    | 등록 완료 시 호출되는 콜백 함수(등록된 객체의 key 문자열을 인자로 전달). |

-   Return
    -   "success" : 등록 성공.
    -   실패 조건에 따른 예외 메시지 문자열 반환.
        -   id, file, basePath 속성이 없는 경우.
        -   지도가 로드되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
let info = {
    id: "STREET_LIGHT",
    file: "StreetLight",
    basePath: "./data"
};
let ghostSymbolMap = Module.getGhostSymbolMap();
ghostSymbolMap.addGhostSymbolBy3DSbyJson(info);
```

{% endtab %}
{% endtabs %}

### insert(option) → string

> 3ds 포맷 파일을 고스트 심볼 모델로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                                                 | Description |
| ------ | ------------------------------------------------------------------------------------ | ----------- |
| option | [JSGhostSymbolMap.InsertOptions](jsghostsymbolmap.md#jsghostsymbolmap.insertoptions) | 속성 정보.  |

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

### addGhostSymbolByBinary(id, data, extension, options) → boolean

> 바이너리 데이터를 고스트 심볼 모델로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                   |
| --------- | ------ | ----------------------------------------------- |
| id        | string | 고스트 심볼 고유 명칭.                          |
| data      | array  | 모델 파일 바이너리 데이터(byte 배열).           |
| extension | string | 파일 확장자.                                    |
| options   | object | <p>등록 옵션.<br>`isAxisYUp`(boolean, 기본값 true): Y축 업벡터 여부.<br>`textureBasePath`(string, 기본값 없음): 3ds 모델의 텍스처를 요청할 기준 경로(끝에 `/`가 없으면 자동으로 붙음). 지정하지 않으면 현재 페이지 폴더에서 찾습니다.<br>`autoLoadTexture`(boolean, 기본값 true): 모델 등록 시 텍스처를 자동으로 요청할지 여부.</p> |

-   Return
    -   true: 등록 성공.
    -   false: 등록 실패.
    -   실패 조건
        -   data가 비어있거나 id가 빈 문자열인 경우.
        -   내부 모델 파싱(insertByBinary)이 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGhostSymbolTextureByPixels(id, imageData, width, height) → boolean

> 픽셀 데이터(raw image data)로 고스트 심볼 모델의 텍스쳐를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                    |
| --------- | ------ | --------------------------------- |
| id        | string | 고스트 심볼 고유 명칭.           |
| imageData | array  | 이미지 픽셀 바이너리 데이터.     |
| width     | number | 이미지 너비(pixel 단위).         |
| height    | number | 이미지 높이(pixel 단위).         |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   imageData가 비어있거나 id가 빈 문자열인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGhostSymbolPositionOffset(id, front, right, up) → boolean

> 고스트 심볼 모델의 오프셋을 설정합니다.
>
> 설정된 오프셋 만큼 고스트 심볼 모델을 이동시킵니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
| ----- | ------ | ------------------ |
| id    | string | 고스트 심볼 고유 명칭 |
| front | number | front 방향 오프셋    |
| right | number | front 방향 오프셋    |
| up    | number | front 방향 오프셋    |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
    -   실패 조건
        -   입력 변수값(id)에 해당되는 고스트심볼 모델이 존재하지 않는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();
ghostSymbolMap.setGhostSymbolPositionOffset(e.strGhostSymbolKey, 1.0, 2.0, 3.0);
```

{% endtab %}
{% endtabs %}

### setModelTexture(option) → string

> 등록된 고스트 심볼 모델를 구성하는 face 별 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                                             | Description |
| ------ | -------------------------------------------------------------------------------- | ----------- |
| option | [JSGhostSymbolMap.LoadTexture](jsghostsymbolmap.md#jsghostsymbolmap.loadtexture) | 속성 정보.  |

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

### setModelFaceReflect(id, index, reflect) → boolean

> 등록된 고스트 심볼 모델를 구성하는 face 별 반사도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description         |
| ------- | ------ | ------------------- |
| id      | string | 고스트 심볼 고유 명칭. |
| index   | number | face 인덱스.         |
| reflect | number | 설정 반사도.          |

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

### getModelMaterials(id) → array

> 3DS 파일로 등록한 고스트 심볼 모델이 가진 재질(material) 목록을 반환합니다. 재질별 이름, 텍스처 파일명, 기본 색상, 그 재질을 사용하는 face 인덱스와 삼각형 수를 알 수 있어, [setModelFaceColor(id, index, color)](jsghostsymbolmap.md#setmodelfacecolor-id-index-color-boolean), [setModelTexture(option)](jsghostsymbolmap.md#setmodeltexture-option-string) 등 face 단위 편집의 대상 face를 재질 기준으로 고를 때 사용합니다.
>
> 재질 정보는 3DS 모델을 로드할 때만 채워지므로, 3DS가 아닌 모델(XDO, GLB 등)이나 재질 정보가 없는 모델은 빈 배열을 반환합니다. `faces`에 담기는 번호는 [getModelFaceCount(id)](jsghostsymbolmap.md#getmodelfacecount-id-number)가 세는 face 단위의 인덱스입니다(삼각형 번호가 아님).

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | 고스트 심볼 고유 명칭. |

-   Return
    -   array([JSGhostSymbolMap.ModelMaterial](jsghostsymbolmap.md#jsghostsymbolmap.modelmaterial)): 재질 목록(재질 인덱스 순서).
    -   빈 배열: 재질 정보가 없는 모델인 경우(3DS 이외의 모델, 또는 다면체(polyhedron) 타입이 아닌 모델).
    -   null: 월드가 없거나, 해당 id의 모델이 등록되어 있지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var materials = Module.getGhostSymbolMap().getModelMaterials("model_01");
if (materials) {
    for (var i = 0; i < materials.length; i++) {
        var m = materials[i];
        console.log(m.index, m.name, m.texture, m.color, m.triangleCount, m.faces);
    }

    // 첫 번째 재질을 사용하는 모든 face의 색상 변경
    var color = new Module.JSColor(255, 255, 0, 0);
    materials[0].faces.forEach(function (faceIndex) {
        Module.getGhostSymbolMap().setModelFaceColor("model_01", faceIndex, color);
    });
}
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

### getReferenceCount(id) → number

> 입력 변수값(id)과 동일한 명칭을 가진 고스트 심볼 모델을 참조하는 객체의 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | 고스트 심볼 고유 명칭. |

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();
var count = ghostSymbolMap.getReferenceCount(e.strGhostSymbolKey);
```

{% endtab %}
{% endtabs %}

### removeModel(id) → boolean

> 입력 변수값(id)과 동일한 명칭을 가진 고스트 심볼 모델을 삭제합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description            |
| ---- | ------ | ---------------------- |
| id   | string | 고스트 심볼 고유 명칭. |

-   Return
    -   true: 삭제 성공.
    -   false: 삭제 실패.
    -   실패 조건
        -   입력 변수값(id)에 해당되는 고스트심볼 모델이 존재하지 않는 경우.
        -   입력 변수값(id)에 해당되는 고스트심볼 모델을 참조로 사용하는 객체가 존재하는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();
var count = ghostSymbolMap.getReferenceCount(e.strGhostSymbolKey);
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

## Type Definitions

#### JSGhostSymbolMap.InsertOptions

> Options for registering a 3D model object as a ghost symbol.
>
> url, polygon 중 하나는 반드시 지정해야 합니다(둘 다 없으면 실패).

| Name     | Type                      | Attributes | Default | Description                     |
| -------- | ------------------------- | ---------- | ------- | ------------------------------- |
| id       | string                    |            |         | 고스트 심볼 고유 명칭.          |
| url      | string                    | optional*  |         | 고스트 심볼 모델 파일 요청 URL(polygon과 양자택일). |
| polygon  | [JSPolygon](jspolygon.md) | optional*  |         | 고스트 심볼 모델 폴리곤(url과 양자택일).            |
| format   | string                    | optional   |         | 요청 파일 포맷(3ds만 지원).     |
| callback | function                  | optional   |         | 등록 완료 시 동작하는 CallBack  |

#### JSGhostSymbolMap.LoadTexture

> Options for registering face textures for the registered ghost symbol object.

| Name       | Type                                 | Attributes | Default      | Description                          |
| ---------- | ------------------------------------- | ---------- | ------------ | -------------------------------------- |
| id         | string                                |            |              | 고스트 심볼 고유 명칭.               |
| url        | string                                |            |              | 고스트 심볼 모델 이미지 요청 URL.    |
| face_index | number                                | optional   | 0            | 텍스쳐를 적용할 face Index.          |
| uv         | [JSVector2D](../core/jsvector2d.md)  | optional   | (1.0, 1.0)   | 텍스쳐 UV 반복(tiling) 배율.         |
| reuse      | boolean                               | optional   | false        | 텍스처 이미지 재사용 여부(export용). |
| callback   | function                              | optional   |              | 등록 완료 시 동작하는 CallBack       |

#### JSGhostSymbolMap.ModelMaterial

> [getModelMaterials(id)](jsghostsymbolmap.md#getmodelmaterials-id-array)가 반환하는 재질 정보 하나.

| Name          | Type          | Description                                                                                  |
| ------------- | ------------- | ---------------------------------------------------------------------------------------------- |
| index         | number        | 재질 인덱스(0부터).                                                                          |
| name          | string        | 재질 이름.                                                                                   |
| texture       | string        | 재질에 지정된 텍스처 파일명(없으면 빈 문자열).                                               |
| color         | array(number) | 재질의 기본(diffuse) 색상 `[r, g, b]`.                                                       |
| faces         | array(number) | 이 재질을 사용하는 face 인덱스 목록.                                                         |
| triangleCount | number        | 이 재질로 칠해지는 삼각형 수.                                                                |
