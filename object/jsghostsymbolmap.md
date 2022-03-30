# JSGhostSymbolMap

Module getEarthquake API로 생성할 수 있습니다.

```javascript
var object = Module.getGhostSymbolMap();
```

## insert(object properties) → string

> 모델 파일을 사용하여 고스트심볼 모델을 등록합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter  | Type   | Contents |
| ---------- | ------ | -------- |
| properties | object | 모델 프로퍼티  |

* Detail
  * properties(object) 태그 정보
    * id : (string) 모델 ID
    * url : (string) 모델 파일 URL
    * callback : (function) 모델 등록 완료 콜백 함수
    * format : (string) 파일 포맷. 현재 3ds 파일을 지원합니다.
* Return
  * 모델 등록 결과
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_ghost\_symbol\_edit](http://sandbox.dtwincloud.com/code/main.do?id=object\_ghost\_symbol\_edit)
{% endtab %}
{% endtabs %}

## setModelTexture(object properties) → string

> 모델 face 텍스쳐를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter  | Type   | Contents |
| ---------- | ------ | -------- |
| properties | object | 모델 프로퍼티  |

* Detail
  * properties(object) 태그 정보
    * id : (string) 모델 ID
    * face\_index : (number) 모델 face 인덱스
    * url : (string) 텍스쳐 이미지 URL
    * callback : (function) 텍스쳐 등록 완료 콜백 함수
* Return
  * 모델 텍스쳐 등록 결과
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_ghost\_symbol\_edit](http://sandbox.dtwincloud.com/code/main.do?id=object\_ghost\_symbol\_edit)
{% endtab %}
{% endtabs %}

## setModelFaceColor(string id, number face\_index, [JSColor](../core/jscolor.md) color) → boolean

> 모델 face 색상을 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter   | Type                          | Contents    |
| ----------- | ----------------------------- | ----------- |
| id          | string                        | 모델 ID       |
| face\_index | number                        | 모델 face 인덱스 |
| color       | [JSColor](../core/jscolor.md) | face 색상     |

* Return
  * 설정 결과
{% endtab %}
{% endtabs %}

## setModelFaceTextureRepeatU(string id, number face\_index, boolean repeat) → boolean

> 모델 Face 텍스쳐의 가로 방향 반복 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter   | Type    | Contents    |
| ----------- | ------- | ----------- |
| id          | string  | 모델 ID       |
| face\_index | number  | 모델 face 인덱스 |
| color       | boolean | face 색상     |

* Return
  * 설정 결과
{% endtab %}
{% endtabs %}

## setModelFaceTextureRepeatV(string id, number face\_index, boolean repeat) → boolean

> 모델 Face 텍스쳐의 세로 방향 반복 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter   | Type    | Contents    |
| ----------- | ------- | ----------- |
| id          | string  | 모델 ID       |
| face\_index | number  | 모델 face 인덱스 |
| color       | boolean | face 색상     |

* Return
  * 설정 결과
{% endtab %}
{% endtabs %}

## getModelFaceCount(string id) → number

> 모델 Face 수를 반환합니다.   &#x20;

{% tabs %}
{% tab title="Information" %}
| Parameter | Type   | Contents |
| --------- | ------ | -------- |
| id        | string | 모델 ID    |

* Return
  * 모델의 face 수
{% endtab %}
{% endtabs %}

## isExistID(string id) → boolean

> 지정한 ID를 가진 모델이 존재하는지 여부를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type   | Contents |
| --------- | ------ | -------- |
| id        | string | 모델 ID    |

* Return
  * 지정한 ID 를 가지는 모델의 존재 여부
{% endtab %}
{% endtabs %}

## getGhostSymbolSize(string id) → [JSSize3D](../core/jssize3d.md)

> 모델의 기본 크기를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type   | Contents |
| --------- | ------ | -------- |
| id        | string | 모델 ID    |

* Return
  * 모델 크기
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_ghost_symbol_edit
{% endtab %}
{% endtabs %}