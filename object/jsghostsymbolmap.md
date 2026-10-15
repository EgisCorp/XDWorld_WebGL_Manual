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

> 등록된 고스트 심볼 모델를 구성하는 face 하나에 이미지를 텍스처로 적용합니다. 이미지는 URL로 요청하거나, 이미 가지고 있는 파일 바이트(`Uint8Array`)를 `data`로 직접 전달할 수 있습니다.
>
> 3DS 재질 단위로 여러 face에 한 번에 적용하려면 [setModelMaterialTexture(option)](jsghostsymbolmap.md#setmodelmaterialtexture-option-string), 적용한 텍스처를 없애려면 [clearModelTexture(option)](jsghostsymbolmap.md#clearmodeltexture-option-string)를 사용합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                                             | Description |
| ------ | -------------------------------------------------------------------------------- | ----------- |
| option | [JSGhostSymbolMap.LoadTexture](jsghostsymbolmap.md#jsghostsymbolmap.loadtexture) | 속성 정보.  |

-   Return
    -   "success": 설정 성공. `url`로 요청한 경우 이미지 다운로드가 끝나기 전에 반환되며, 실제 적용은 다운로드 완료 후에 이루어집니다. `data`를 전달한 경우에는 반환 전에 적용이 끝납니다.
    -   "failed find model": 해당 id의 모델이 등록되어 있지 않은 경우.
    -   "failed load texture": `face_index`가 모델의 face 개수 이상인 경우. 이미지 다운로드 자체의 실패는 반환값으로 알 수 없고 콘솔에만 출력됩니다.
    -   "error  { id }  Undefined" 등: 필수 속성(`id`, 그리고 `data`가 없을 때의 `url`)이 없거나(`Undefined`/`NULL`) 타입이 다른 경우(`Type Mismatch`)의 오류 문자열. 속성 이름이 `{ }` 안에 들어갑니다.
    -   빈 문자열(""): 지도가 로드되지 않은 경우.
-   동작
    -   텍스처가 적용된 face의 색상은 흰색(255, 255, 255)으로 바뀝니다(재질 색과 곱해져 어둡게 보이지 않도록). 투명도(알파)는 유지됩니다. 적용 전 색상으로 되돌리려면 [clearModelTexture(option)](jsghostsymbolmap.md#clearmodeltexture-option-string)를 사용합니다.
    -   `face_index`가 음수이면 0으로 처리하고, 숫자가 아니면 지정하지 않은 것으로 봅니다(face 0).
    -   `data`는 `Uint8Array`일 때만 사용됩니다. 비어 있지 않은 `Uint8Array`이면 `url`은 무시하고 다운로드 없이 적용하며, 그 외의 값(길이 0 포함)이면 `url`을 사용합니다.
    -   `callback`은 모든 대상 face에 텍스처를 적용한 뒤 한 번 호출되며, 인자로 option에 넣은 속성이 모두 복사된 객체가 전달됩니다. `data`를 사용한 경우에는 이 함수가 반환되기 전에 동기로 호출됩니다. `url` 다운로드가 실패하면 콜백은 호출되지 않습니다. 이미지 디코딩에 실패해도 별도의 오류는 반환되지 않고(콘솔 로그만 출력) 콜백이 호출됩니다.
    -   다면체(3DS 등) 모델에만 사용합니다. GLB 등 다른 유형의 모델에는 적용되지 않으며, 특히 `data`는 사용하지 마세요.
-   Sample
    -   function init 참조.
    -   [Sandbox_Ghost Symbol Editing](https://sandbox.egiscloud.com/code/main.do?id=object_ghost_symbol_edit)

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();

// 1) URL로 face 0에 적용
ghostSymbolMap.setModelTexture({
    id: "model_01",
    face_index: 0,
    url: "./texture/wall.jpg",
    callback: function (param) {
        console.log("적용 완료", param.id);
    },
});

// 2) 이미 받아 둔 이미지 파일 바이트로 face 2에 적용(다운로드 없이 즉시 적용)
fetch("./texture/roof.png")
    .then((res) => res.arrayBuffer())
    .then((buf) => {
        var result = ghostSymbolMap.setModelTexture({
            id: "model_01",
            face_index: 2,
            data: new Uint8Array(buf),
        });
        console.log(result); // "success"
    });
```

{% endtab %}
{% endtabs %}

### setModelMaterialTexture(option) → string

> 3DS 모델의 재질(material) 하나를 사용하는 face 전부에 같은 이미지를 텍스처로 적용합니다.
>
> 대상 재질은 [getModelMaterials(id)](jsghostsymbolmap.md#getmodelmaterials-id-array)가 돌려주는 재질 목록의 `index`로 지정합니다. 재질이 쓰는 face를 일일이 골라 [setModelTexture(option)](jsghostsymbolmap.md#setmodeltexture-option-string)를 반복 호출하는 것과 같은 결과를, 이미지를 한 번만 만들어 모든 face가 공유하면서 얻습니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                                                             | Description |
| ------ | ------------------------------------------------------------------------------------------------ | ----------- |
| option | [JSGhostSymbolMap.MaterialTexture](jsghostsymbolmap.md#jsghostsymbolmap.materialtexture)         | 속성 정보.  |

-   Return
    -   "success": 설정 성공. `url`로 요청한 경우 이미지 다운로드 후 적용되고, `data`를 전달한 경우에는 반환 전에 적용이 끝납니다.
    -   "failed find model": 해당 id의 모델이 등록되어 있지 않은 경우.
    -   "failed find material": 다면체 모델이 아니거나(재질 정보가 있는 것은 3DS 모델뿐), `material`이 0 미만이거나 모델의 재질 개수 이상인 경우.
    -   "failed find material face": 그 재질을 사용하는 face가 하나도 없는 경우.
    -   "failed load texture": 이미지 적용 요청에 실패한 경우(정상 입력에서는 발생하지 않습니다). 이미지 다운로드 자체의 실패는 반환값으로 알 수 없고 콘솔에만 출력됩니다.
    -   "error  { material }  Undefined" 등: 필수 속성(`id`, `material`, 그리고 `data`가 없을 때의 `url`)이 없거나 타입이 다른 경우의 오류 문자열. 속성 이름이 `{ }` 안에 들어갑니다.
    -   빈 문자열(""): 지도가 로드되지 않은 경우.
-   동작
    -   `data`, `url`, `reuse`, `callback`의 규칙과 적용된 face가 흰색으로 바뀌는 동작은 [setModelTexture(option)](jsghostsymbolmap.md#setmodeltexture-option-string)와 같습니다. 콜백은 재질의 모든 face에 적용한 뒤 한 번만 호출됩니다.
    -   `face_index`, `uv` 속성은 없습니다.
    -   오류는 id, 모델, 재질, face, 이미지(`url`/`data`) 순서로 검사하므로, 여러 입력이 잘못되면 앞 단계의 오류가 먼저 반환됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();

// 재질 목록에서 이름으로 대상 재질을 찾아, 그 재질의 모든 face에 텍스처 적용
var materials = ghostSymbolMap.getModelMaterials("model_01");
var wall = materials.find(function (m) { return m.name === "WALL"; });
if (wall) {
    var result = ghostSymbolMap.setModelMaterialTexture({
        id: "model_01",
        material: wall.index,
        url: "./texture/wall.jpg",
        callback: function (param) {
            console.log("재질 텍스처 적용 완료", param.material);
        },
    });
    console.log(result);
}
```

{% endtab %}
{% endtabs %}

### clearModelTexture(option) → string

> 고스트 심볼 모델의 face에 적용된 텍스처를 해제하고 face 색상을 재질 색으로 되돌립니다.
>
> 해제할 대상은 `material`(재질이 쓰는 face 전부), `face_index`(face 하나), 둘 다 없으면 모델 전체 face 순으로 결정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                                                       | Description |
| ------ | ------------------------------------------------------------------------------------------ | ----------- |
| option | [JSGhostSymbolMap.ClearTexture](jsghostsymbolmap.md#jsghostsymbolmap.cleartexture)         | 속성 정보.  |

-   Return
    -   "success": 해제 성공.
    -   "failed find model": 해당 id의 모델이 등록되어 있지 않은 경우.
    -   "failed find face": 다면체 모델이 아니거나, `face_index`가 0 미만이거나 모델의 face 개수 이상인 경우.
    -   "failed find material": `material`이 0 미만이거나 모델의 재질 개수 이상인 경우.
    -   "failed find material face": 그 재질을 사용하는 face가 하나도 없는 경우.
    -   "failed clear texture": 해제할 face가 없는 경우(face가 0개인 모델).
    -   "error  { material }  Undefined" 등: `id`가 없거나, 지정한 `material`/`face_index`가 숫자가 아닌 경우의 오류 문자열. 속성 이름이 `{ }` 안에 들어갑니다.
    -   빈 문자열(""): 지도가 로드되지 않은 경우.
-   동작
    -   대상 face의 텍스처 참조를 해제합니다. 다른 face가 같은 텍스처를 쓰고 있으면 그 face에는 영향이 없고, 마지막 사용자가 해제되면 텍스처가 삭제됩니다.
    -   대상 face의 색상을 그 face의 재질(3DS) 기본 색상으로 되돌립니다. 투명도(알파)는 유지합니다. 재질 정보가 없는 모델의 face는 색상을 바꾸지 않습니다(텍스처 적용 때 흰색이 된 색이 그대로 남습니다).
    -   텍스처가 없던 face도 색상이 재질 색으로 되돌아가므로, [setModelFaceColor(id, index, color)](jsghostsymbolmap.md#setmodelfacecolor-id-index-color-boolean)로 바꿔 둔 색상도 함께 초기화됩니다.
    -   아직 다운로드 중인 텍스처 요청은 취소하지 않습니다. 해제 이후에 다운로드가 끝나면 그 텍스처가 다시 적용됩니다.
    -   `material`이 지정되어 있으면(`undefined`/`null`이 아니면) `face_index`는 무시합니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var ghostSymbolMap = Module.getGhostSymbolMap();

// 재질 하나의 텍스처 해제
ghostSymbolMap.clearModelTexture({ id: "model_01", material: 2 });

// face 하나의 텍스처 해제
ghostSymbolMap.clearModelTexture({ id: "model_01", face_index: 5 });

// 모델 전체 해제
ghostSymbolMap.clearModelTexture({ id: "model_01" });
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

> 3DS 파일로 등록한 고스트 심볼 모델이 가진 재질(material) 목록을 반환합니다. 재질별 이름, 텍스처 파일명, 기본 색상, 그 재질을 사용하는 face 인덱스와 삼각형 수를 알 수 있어, [setModelFaceColor(id, index, color)](jsghostsymbolmap.md#setmodelfacecolor-id-index-color-boolean), [setModelTexture(option)](jsghostsymbolmap.md#setmodeltexture-option-string) 등 face 단위 편집의 대상 face를 재질 기준으로 고를 때 사용합니다. 재질 전체에 텍스처를 적용하려면 [setModelMaterialTexture(option)](jsghostsymbolmap.md#setmodelmaterialtexture-option-string)에 이 목록의 `index`를 전달합니다.
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
| url        | string                                | optional*  |              | 고스트 심볼 모델 이미지 요청 URL. `data`가 없을 때 필수. |
| data       | Uint8Array                            | optional*  |              | 이미지 파일 내용(png, jpg 등 파일 바이트 그대로). 비어 있지 않은 `Uint8Array`이면 `url` 대신 사용하며 다운로드 없이 즉시 적용. |
| face_index | number                                | optional   | 0            | 텍스쳐를 적용할 face Index.          |
| uv         | [JSVector2D](../core/jsvector2d.md)  | optional   | (1.0, 1.0)   | 텍스쳐 UV 반복(tiling) 배율. 현재 구현에서는 값을 읽기만 하고 적용하지 않으므로 효과가 없음. |
| reuse      | boolean                               | optional   | false        | 텍스처 이미지 재사용 여부(export용). |
| callback   | function                              | optional   |              | 텍스처 적용이 끝나면 한 번 호출되는 CallBack. 인자는 option의 속성이 복사된 객체. |

#### JSGhostSymbolMap.MaterialTexture

> [setModelMaterialTexture(option)](jsghostsymbolmap.md#setmodelmaterialtexture-option-string)에 전달하는 속성. 재질이 쓰는 face 전부에 같은 텍스처를 적용합니다.

| Name       | Type        | Attributes | Default | Description                                                                 |
| ---------- | ----------- | ---------- | ------- | --------------------------------------------------------------------------- |
| id         | string      |            |         | 고스트 심볼 고유 명칭.                                                      |
| material   | number      |            |         | 대상 재질 인덱스([getModelMaterials(id)](jsghostsymbolmap.md#getmodelmaterials-id-array)의 `index`). |
| url        | string      | optional*  |         | 이미지 요청 URL. `data`가 없을 때 필수.                                     |
| data       | Uint8Array  | optional*  |         | 이미지 파일 바이트. 비어 있지 않은 `Uint8Array`이면 `url` 대신 사용.        |
| reuse      | boolean     | optional   | false   | 텍스처 이미지 재사용 여부(export용).                                         |
| callback   | function    | optional   |         | 재질의 모든 face에 적용한 뒤 한 번 호출되는 CallBack. 인자는 option의 속성이 복사된 객체. |

#### JSGhostSymbolMap.ClearTexture

> [clearModelTexture(option)](jsghostsymbolmap.md#clearmodeltexture-option-string)에 전달하는 속성. `material`, `face_index`가 모두 없으면 모델 전체를 대상으로 합니다.

| Name       | Type    | Attributes | Default | Description                                                         |
| ---------- | ------- | ---------- | ------- | ------------------------------------------------------------------- |
| id         | string  |            |         | 고스트 심볼 고유 명칭.                                              |
| material   | number  | optional   |         | 이 재질을 사용하는 face 전부를 대상으로 함. 지정하면 `face_index`는 무시. |
| face_index | number  | optional   |         | 이 face 하나를 대상으로 함.                                         |

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
