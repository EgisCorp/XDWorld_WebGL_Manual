---
description: 3D Gaussian Splatting 데이터를 지도에 표시하기 위한 API 입니다.
---

# JSGaussianSplat

> `Module.createXXX()` 계열 API가 아니라, 등록할 서비스 레이어의 [JSLayer.createGaussianSplat(objectKey)](../layer/jslayer.md#creategaussiansplat-objectkey-jsgaussiansplat)를 통해 생성됩니다(레이어에 등록되는 시점의 위치 확정이 중요하기 때문입니다).
>
> `.ply` / `.splat` 포맷의 3D Gaussian Splatting 데이터를 로드하여 지도 위에 표시합니다.

```javascript
var layerList = new Module.JSLayerList(false);
var layer = layerList.nameAtLayer("myLayer");
var splat = layer.createGaussianSplat("splat_01");
```

## Function

### loadData(uint8Array) → string

> `.ply` 또는 `.splat` 포맷의 바이트 배열(fetch 등으로 받은 ArrayBuffer)을 그대로 전달하여 데이터를 로드합니다. 포맷은 파일 헤더로 자동 판별됩니다.
>
> 데이터가 크면 내부에서 한 번의 메모리 복사가 발생합니다(GB 단위 데이터에서는 [loadDataPtr(ptr, size)](jsgaussiansplat.md#loaddata-uint8array-string) 사용을 고려하십시오).

{% tabs %}
{% tab title="Information" %}

| Name       | Type       | Description                              |
| ---------- | ---------- | ----------------------------------------- |
| uint8Array | Uint8Array | `.ply`/`.splat` 파일의 바이트 배열.      |

-   Return
    -   "": 로드 성공.
    -   "object isn't ready.": 객체가 준비되지 않은 경우.
    -   "data is null.": uint8Array가 null 또는 undefined인 경우.
    -   "data is empty.": 데이터가 비어있는 경우.
    -   "unsupported or broken splat data.": 지원하지 않는 형식이거나 데이터가 손상된 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
fetch("model.ply")
    .then(res => res.arrayBuffer())
    .then(buffer => {
        var error = splat.loadData(new Uint8Array(buffer));
        if (error !== "") console.error(error);
    });
```

{% endtab %}
{% endtabs %}

### loadDataPtr(ptr, size) → string

> `Module._malloc`으로 직접 확보한 wasm 힙 버퍼의 포인터를 전달하여 데이터를 로드합니다. [loadData(uint8Array)](jsgaussiansplat.md#loaddata-uint8array-string)와 달리 JS→wasm 복사가 발생하지 않아, GB 단위의 대용량 데이터에서 메모리 사용량 피크를 절반으로 줄일 수 있습니다.
>
> 전달한 버퍼의 해제(`Module._free`)는 호출한 쪽(JS)의 책임입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                    |
| ---- | ------ | ------------------------------------------------- |
| ptr  | number | wasm 힙 상의 버퍼 포인터(`Module._malloc` 반환값). |
| size | number | 버퍼 크기(byte 단위).                             |

-   Return
    -   "": 로드 성공.
    -   "object isn't ready.": 객체가 준비되지 않은 경우.
    -   "data is empty.": ptr 또는 size가 0인 경우.
    -   "unsupported or broken splat data.": 지원하지 않는 형식이거나 데이터가 손상된 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var ptr = Module._malloc(byteLength);
Module.HEAPU8.set(new Uint8Array(arrayBuffer), ptr);
var error = splat.loadDataPtr(ptr, byteLength);
Module._free(ptr);
if (error !== "") console.error(error);
```

{% endtab %}
{% endtabs %}

### createTestData(count, radius) → string

> 실제 데이터 없이, 렌더링 경로만 확인하기 위한 무작위 테스트 스플랫 데이터를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                |
| ------ | ------ | ---------------------------- |
| count  | number | 생성할 스플랫 개수.         |
| radius | number | 스플랫 분포 반경(meter 단위). |

-   Return
    -   "": 생성 성공.
    -   "object isn't ready.": 객체가 준비되지 않은 경우.
    -   "failed to create test data.": 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var error = splat.createTestData(100000, 50.0);
```

{% endtab %}
{% endtabs %}

### setPlacement(options) → string

> 위치, 스케일, 자세(방향), 반전, 거리 기반 LOD 등 배치 관련 속성을 한 번에 설정합니다. 전달한 필드만 반영되며, 나머지는 기존 값을 유지합니다.
>
> 위치(longitude/latitude)는 스케일이 경계 박스 계산에 영향을 주기 때문에 다른 필드보다 나중에 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type    | Attributes | Description                                                                 |
| ----------- | ------- | ---------- | ----------------------------------------------------------------------------- |
| longitude   | number  | optional   | 배치 경도(latitude와 함께 지정해야 위치가 반영됨).                          |
| latitude    | number  | optional   | 배치 위도(longitude와 함께 지정해야 위치가 반영됨).                         |
| altitude    | number  | optional   | 배치 고도(m 단위, 기본값 0.0, longitude/latitude 지정 시에만 적용).         |
| scale       | number  | optional   | 모델 스케일.                                                                |
| heading     | number  | optional   | 방향각(Degree).                                                             |
| pitch       | number  | optional   | 피치 각(Degree, 지역 접평면 기준).                                          |
| roll        | number  | optional   | 롤 각(Degree, 지역 접평면 기준).                                            |
| upAxis      | number  | optional   | <p>모델의 위 방향 축.<br>0: 로컬 +Z가 위(기본).<br>1: 로컬 -Y가 위(COLMAP/3DGS 학습 결과물의 기본 좌표계).</p> |
| flipX       | boolean | optional   | X축 반전 여부(거울상으로 들어온 모델 보정용).                              |
| flipY       | boolean | optional   | Y축 반전 여부.                                                              |
| flipZ       | boolean | optional   | Z축 반전 여부(flipX/flipY/flipZ 중 하나라도 전달되면, 전달 안 한 축은 현재 값 유지).|
| lod         | boolean | optional   | 거리 기반 LOD 사용 여부.                                                    |
| lodNear     | number  | optional   | LOD 근거리 기준값(lod가 true일 때만 적용).                                  |
| lodFar      | number  | optional   | LOD 원거리 기준값(lod가 true일 때만 적용).                                  |
| lodMinRatio | number  | optional   | 최대 LOD 거리에서의 최소 스플랫 표시 비율(lod가 true일 때만 적용).          |
| splatScale  | number  | optional   | 개별 스플랫 크기 배율.                                                      |
| alphaScale  | number  | optional   | 개별 스플랫 투명도 배율.                                                    |

-   Return
    -   "": 설정 성공.
    -   "object isn't ready.": 객체가 준비되지 않은 경우.
    -   "parameter is null.": options가 null 또는 undefined인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
splat.setPlacement({
    longitude: 127.0, latitude: 37.5, altitude: 0.0,
    scale: 1.0, heading: 0.0, pitch: 0.0, roll: 0.0,
    upAxis: 1,
    lod: true, lodNear: 100, lodFar: 2000, lodMinRatio: 0.15,
    splatScale: 1.0, alphaScale: 1.0
});
```

{% endtab %}
{% endtabs %}

### getSplatCount() → number

> 로드된 전체 스플랫 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 로드된 전체 스플랫 개수.
    -   0: 객체가 준비되지 않았거나 데이터가 로드되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = splat.getSplatCount();
```

{% endtab %}
{% endtabs %}

### getState() → object

> 렌더링 파이프라인의 진단 상태를 반환합니다. 화면에 표시되지 않을 때 어느 단계에서 문제가 발생했는지 확인하는 용도로 사용합니다.
>
> `splatCount`가 0이면 데이터 로드 실패, `geoSet`이 false면 [setPlacement(options)](jsgaussiansplat.md#setplacement-options-string) 미호출, `inserted`가 false면 레이어 등록 실패, `renderCall`이 0이면 렌더 순회에서 컬링됨, `program`이 0이면 셰이더 컴파일 실패, `renderCall`은 있는데 `drawCall`이 0이면 업로드/attribute 바인딩 문제, `drawCall`은 있는데 화면에 보이지 않으면 투영/스케일 문제일 가능성이 높습니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   object: 아래 필드를 포함하는 진단 정보 객체.
        -   ready (boolean): 객체 준비 상태.
        -   splatCount (number): 로드된 전체 스플랫 개수.
        -   drawCount (number): LOD 적용 후 실제로 그리는 스플랫 개수.
        -   geoSet (boolean): 위치(경위도)가 설정되었는지 여부.
        -   inserted (boolean): 레이어에 정상 등록되었는지 여부.
        -   uploaded (boolean): GPU 업로드 완료 여부.
        -   renderCall (number): 렌더 순회에 포함된 횟수.
        -   drawCall (number): 실제 draw call 횟수.
        -   program (number): 사용 중인 셰이더 프로그램 ID(0이면 컴파일 실패).
        -   visible (boolean): 가시화 여부.
        -   flipX, flipY, flipZ (boolean): 현재 적용된 축 반전 상태.

{% endtab %}
{% tab title="Template" %}

```javascript
var state = splat.getState();
console.log(state);
```

{% endtab %}
{% endtabs %}
