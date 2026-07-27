---
description: 지도 내 jsicon 객체를 등록 및 관리하기 위한 API 입니다.
---

# JSSymbol

> Module.getSymbol() API를 생성합니다.

```javascript
var symbol = Module.getSymbol();
```

## Function

### getIcon(id) → [JSIcon](./jsicon.md)

> JSSymbol 등록된 [JSIcon](./jsicon.md) 객체를 반환합니다..

{% tabs %}
{% tab title="Name" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| id   | string | 고유 명칭.  |

-   Return
    -   [JSIcon](./jsicon.md): 반환 성공.
    -   null: 반환 실패.
    -   실패 조건
        -   입력 변수값(id)와 동일한 고유 명칭을 가진 [JSIcon](./jsicon.md) 객체가 없는 경우.
-   Sample
    -   the createPOI function 참조.
    -   [Sandbox_Height Measurement](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_altitude)

{% endtab %}
{% tab title="Template" %}

```javascript
var icon = Module.getSymbol.getIcon("Icon_name");
```

{% endtab %}
{% endtabs %}

### insertIcon(id, data, width, height) → boolean

> [JSIcon](./jsicon.md) 객체를 추가합니다.
>
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터 입니다.
>
> 입력 변수값(width, height)은 이미지의 실제 크기 입니다.

{% tabs %}
{% tab title="Name" %}

| Name   | Type   | Description    |
| ------ | ------ | -------------- |
| id     | string | 고유 명칭.     |
| data   | object | 이미지 데이터. |
| width  | number | 이미지 너비.   |
| height | number | 이미지 높이.   |

-   Return
    -   true: 추가 성공.
    -   false: 추가 실패.
    -   실패 조건
        -   입력 변수값(id)와 동일한 고유 명칭을 가진 [JSIcon](./jsicon.md) 객체가 이미 등록되어 있는 경우.
        -   입력 변수값(data)의 길이가 0(비어있음)인 경우.
-   Sample
    -   the createPOI function 참조.
    -   [Sandbox_Height Measurement](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_altitude)

{% endtab %}
{% tab title="Template" %}

```javascript
var canvas = document.createElement("canvas");
var ctx = canvas.getContext("2d");
//...render image on canvas...
var data = ctx.getImageData(0, 0, canvas.width, canvas.height).data;
Module.getSymbol.insertIcon("Icon_name", data, canvas.width, canvas.height);
```

{% endtab %}
{% endtabs %}

### deleteIcon(id) → boolean

> JSSymbol 등록된 [JSIcon](./jsicon.md) 객체를 삭제합니다.
>
> 입력 변수값(id)와 동일한 고유 명칭을 가진 [JSIcon](./jsicon.md) 객체를 삭제합니다.

{% tabs %}
{% tab title="Name" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| id   | string | 고유 명칭.  |

-   Return
    -   true: 삭제 성공.
    -   false: 삭제 실패.
    -   실패 조건
        -   입력 변수값(id)와 동일한 고유 명칭을 가진 [JSIcon](./jsicon.md) 객체가 없는 경우.
        -   해당 [JSIcon](./jsicon.md)를 참조 받는 객체가 하나 이상 존재하는 경우(참조 객체 삭제 후 재 동작).
-   Sample
    -   the clearAnalysis function 참조.
    -   [Sandbox_Height Measurement](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_altitude)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getSymbol.deleteIcon("Icon_name");
```

{% endtab %}
{% endtabs %}

### parseIamgeMap(data) → object

> 바이너리 이미지 맵 데이터를 파싱하여, 내부에 포함된 다수의 이미지를 텍스쳐로 일괄 등록합니다.
>
> data 변수는 `버전(32byte) + 이미지 개수 + [이름 길이, 이름, 데이터 길이, 이미지 바이너리] * N` 형식으로 구성된 바이너리(ArrayBuffer/Uint8Array 등, byteLength 속성을 가진 객체) 데이터입니다.

{% tabs %}
{% tab title="Name" %}

| Name | Type   | Description        |
| ---- | ------ | ------------------- |
| data | object | 바이너리 이미지 맵 데이터. |

-   Return
    -   (object) `{ result: number, name: string, return?: string }` 형태의 결과 객체.
        -   result: 처리 결과 코드.
        -   name: API 명칭("JSIcon.parseIamgeMap").
        -   return: 실패 시에만 포함되는 오류 메시지.
    -   실패 조건(이 경우 return 필드에 오류 메시지가 담깁니다)
        -   지도가 로드되지 않은 경우(return: "Map Did Not Load.").
        -   입력 변수값(data)이 없거나 파싱할 수 없는 경우(return: "Error byte Tag.").

{% endtab %}
{% tab title="Template" %}

```javascript
// data는 서버 등에서 내려받은 이미지 맵 바이너리 데이터(ArrayBuffer 등)
var result = Module.getSymbol.parseIamgeMap(data);
if (result.return) {
	console.log(result.return); // 오류 메시지
}
```

{% endtab %}
{% endtabs %}
