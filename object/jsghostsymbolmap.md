---
description: 고스트 심볼 객체 등록 관리하는 API.
---

# JSGhostSymbolMap

> Module.getGhostSymbolMap API 생성.

```javascript
var object = Module.getGhostSymbolMap();
```

### insert(option) → string

> 3DS 파일을 사용하여 고스트 심볼 등록.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description |
| ---------- | ------ | -------- |
| option | [JSGhostSymbolMap.InsertOptions](jsghostsymbolmap.md#jsghostsymbolmap.insertoptions) | 고스트 심볼 등록 속성 정보.  |

* Return
  * "success" : 등록 성공.
  * "request failed" : 3ds 파일 네트워크 요청 실패.  
  * 이 외 예외처리에 대한 문자열 메시지 반환
  
* Sample
  * function init 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setModelTexture(option) → string

> 등록된 고스트 심볼 객체를 구성하는 face 텍스쳐 지정.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description |
| ---------- | ------ | -------- |
| option | [JSGhostSymbolMap.LoadTexture](jsghostsymbolmap.md#jsghostsymbolmap.loadtexture) | 고스트 심볼 이미지 속성 정보.  |

* Return
  * "success" : 등록 성공.
  * "failed load texture" : 이미지 파일 네트워크 요청 실패.
  * 이 외 예외처리에 대한 문자열 메시지 반환
  
* Sample
  * function init 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setModelFaceColor(name, index, color) → boolean

> 등록된 고스트 심볼 객체 face 색상을 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                          | Description    |
| ----------- | ----------------------------- | ----------- |
| name          | string                        | 참조 객체 등록 명칭. |
| index | number                        | 참조 객체 face Index. |
| color       | [JSColor](../core/jscolor.md) | 변경 색상. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setModelFaceTextureRepeatU(id, index, repeat) → boolean

> 등록된 고스트 심볼 객체 가로 방향 Wrapping 설정.

{% tabs %}
{% tab title="Information" %}
| Name   | Type    | Description    |
| ----------- | ------- | ----------- |
| id          | string  | 참조 객체 등록 명칭.       |
| index       | number  | 참조 객체 face Index. |
| repeat       | boolean | <p>true인 경우 가로 GL_REPEAT 설정.<br>false인 경우 가로 GL_CLAMP_TO_EDGE 설정.</p>     |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setModelFaceTextureRepeatV(name, index, repeat) → boolean

> 등록된 고스트 심볼 객체 세로 방향 Wrapping 설정.

{% tabs %}
{% tab title="Information" %}
| Name   | Type    | Description    |
| ----------- | ------- | ----------- |
| name          | string  | 참조 객체 등록 명칭.       |
| index       | number  | 참조 객체 face Index. |
| repeat       | boolean | <p>true인 경우 세로 GL_REPEAT 설정.<br>false인 경우 세로 GL_CLAMP_TO_EDGE 설정.</p>     |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getModelFaceCount(name) → number

> 등록된 고스트 심볼 객체 face 개수 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| name          | string  | 참조 객체 등록 명칭.       |

* Return
  * 참조 객체 face 개수.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### isExistID(name) → boolean

> 등록된 고스트 심볼 존재 유무 확인.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| name          | string  | 참조 객체 등록 명칭.       |

* Return
  * true : 객체 존재 확인.
  * false : 객체 존재 확인 불가.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getGhostSymbolSize(name) → [JSSize3D](../core/jssize3d.md)

> 등록된 고스트 심볼 크기 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| --------- | ------ | -------- |
| name          | string  | 참조 객체 등록 명칭.       |

* Return
  * [JSSize3D](../core/jssize3d.md) : 고스트 심볼 크기(x,y,z) 반환 성공.
  * null : 크기 반환 실패.
  
* Sample
  * function createGhostSymbol 참조.
  * [샌드박스\_고스트 심볼 편집](http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

##### JSGhostSymbolMap.InsertOptions

> 고스트 심볼 3D 모델 객체 등록 옵션.

| Name     | Type                                                                       | Attributes | Default | Description              |
| ------ | -------------------------------------------------------------------------- | -------- | ----- | ---------------------- |
| id       | string                                                                     |            |         | 참조 객체 등록 명칭.     |
| url      | string                                                                     |            |         | 참조 객체 요청 URL.     |
| format   | string                                                                     | optional   |         | 요청 파일 포맷(3ds만 지원).|
| callback | function                                                                   | optional   |         | 등록 완료 시 동작하는 CallBack |

##### JSGhostSymbolMap.LoadTexture

> 등록된 고스트 심볼 객체 face 텍스쳐 등록 옵션.

| Name         | Type                          | Attributes | Default                 | Description      |
| ------------ | ----------------------------- | ---------- | ----------------------- | ---------------- |
| id         | number                        |    |                      | 참조 객체 등록 명칭. |
| url | boolean                              |    |                    | 참조 이미지 요청 URL. |
| index     | number                        | optional | 0                      | 참조 객체 face Index. |
| callback | function                            | optional |         | 등록 완료 시 동작하는 CallBack |
