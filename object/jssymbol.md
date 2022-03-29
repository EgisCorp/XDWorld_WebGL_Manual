---
description: 아이콘 객체를 관리하는 클래스입니다.
---

# JSSymbol

Module getSymbol API로 생성할 수 있습니다.

```javascript
var symbol = Module.getSymbol();
```

## getIcon(string iconName) → JSIcon

> symbol 내 저장된 JSIcon 객체를 반환합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type   | Contents |
| --------- | ------ | -------- |
| iconName  | string | 아이콘 이름   |

* Detail
```
var icon = Module.getSymbol.getIcon("Icon\_name");
```

* Return
  * 설정 성공 ([CJSIcon](CJSIcon.md)) 혹은 실패 (null)
  * 다음의 경우 API는 null 을 반환합니다.\
    1\) 해당 이름으로 등록된 아이콘이 없는 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_multipoint
{% endtab %}
{% endtabs %}

## insertIcon(string iconName, object iconImage, number imageWidth, number imageHeight) → boolean

> symbol 내 아이콘 텍스쳐를 등록합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter   | Type   | Contents     |
| ----------- | ------ | ------------ |
| iconName    | string | 아이콘 이름       |
| iconImage   | object | 이미지 바이너리 데이터 |
| imageWidth  | number | 이미지 Width    |
| imageHeight | number | 이미지 Height   |

* Detail
```
var canvas = document.createElement("canvas");
var ctx = canvas.getContext('2d');
...(canvas 내 이미지 렌더링)...
var data = ctx.getImageData(0, 0, canvas.width, canvas.height).data;
Module.getSymbol.insertIcon("Icon\_name", data, canvas.width, canvas.height);
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 를 반환합니다.\
    1\) 해당 이름으로 등록된 아이콘이 이미 존재하는 경우\
    2\) 이미지 바이너리 데이터가 null 경우
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_multipoint
{% endtab %}
{% endtabs %}

## deleteIcon(string iconName) → boolean

> symbol 내 등록된 아이콘을 삭제합니다.

{% tabs %}
{% tab title="Parameter" %}
| Parameter | Type   | Contents |
| --------- | ------ | -------- |
| iconName  | string | 아이콘 이름   |

* Detail
```
Module.getSymbol.deleteIcon("Icon\_name");
```

* Return
  * 설정 성공 (true) 혹은 실패 (false)
  * 다음의 경우 API는 false 를 반환합니다.\
    1\) 해당 이름으로 등록된 아이콘이 존재하지 않는 경우\
    2\) 아이콘 텍스쳐를 참조하는 오브젝트가 하나 이상 존재하는 경우 (이 경우, 아이콘 텍스쳐는 삭제하지 않고 API를 종료합니다.)
	
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object\_multipoint
{% endtab %}
{% endtabs %}
