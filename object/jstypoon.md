---
description: 태풍 오브젝트 설정 및 반환 기능 API.
---

# JSTypoon

Module createTypoon API로 생성할 수 있습니다.

```javascript
var object = Module.createTypoon("typoon");
```

## properties

| name | Type | Contents |
| :--- | :--- | :--- |

### createbyJson\(object options\) → object

> 태풍 오브젝트를 생성.
>
> argument 변수로 태풍 오브젝트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| option | JSTypoon.CreateOptions | 초기화 옵션 속성 정보. |

* Return
  * .result : API 성공 유무 상태 \( 1 : 성공,  0 : 실패\)
  * .name : 동작 API 명칭
  * .return : API 반환 정보 \( object : 정상적인 반환값, 문자열 : 실패 에러 코드\)
  
* Sample
  * function initPage 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.createLayer("LAYER_TYPOON", Module.ELT_TYPOON);
layer.setMaxDistance(100000.0);	

let typoon = Module.createTypoon("Typoon");
let json = {
	id: "Typoon",
	size: 800,
	height: 1000,
	position: new Module.JSVector3D(126.7852637, 35.0183227, 30.0),
	complete: complete,
	damage: {
		size: 500,
		altitude: 10,
		color: new Module.JSColor(200, 0, 0, 255),
		unionterrain: false,
	},	
};

typoon.createbyJson(json);
layer.addObject(typoon, 0);
```
{% endtab %}
{% endtabs %}

### moveStart\(\)

> 태풍 이동 시작.
>
> JSTypoon API moveList에 추가 한 경위도 좌표로 태풍 이동.
>
> 태풍 이동 이벤트 종료 후 생성 위치로 초기화.

{% tabs %}
{% tab title="Information" %}

* Sample
  * function moveTypoon 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}
```javascript
let typoon = Module.createTypoon("Typoon");

var movePosition = new Module.Collection();
movePosition.add(new Module.JSVector3D(126.77599416643791, 35.02714918251881, 34.293371013365686));
movePosition.add(new Module.JSVector3D(126.78374897355015, 35.03318059967435, 35.54886215366423));
movePosition.add(new Module.JSVector3D(126.79212321528658, 35.03203801070689, 25.686076117679477));
movePosition.add(new Module.JSVector3D(126.79408620811664, 35.019259090964134, 29.999966450035572));
movePosition.add(new Module.JSVector3D(126.78978362530727, 35.011527249861985, 24.815993944182992));

typoon.moveList(movePosition);
typoon.moveStart();
```
{% endtab %}
{% endtabs %}

### moveEnd\(\)

> 태풍 강제 이동 종료.
>
> 태풍 강제 이동 종료 후 생성 위치로 초기화.

{% tabs %}
{% tab title="Information" %}

* Sample
  * function stopTypoon 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.nameAtLayer("LAYER_TYPOON");
let typoon = Typoonlayer.keyAtObject("Typoon");

typoon.moveEnd();
```
{% endtab %}
{% endtabs %}

### moveList\([Collection](../core/collection.md) movelist\)

> 태풍 이동 경위도 설정.
>
> 입력된 경위도 좌표로 순차적으로 이동.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| movelist | [Collection](../core/collection.md) | 태풍 경위도 좌표 리스트. |

* Sample
  * function moveTypoon 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}
```javascript
let typoon = Module.createTypoon("Typoon");

var movePosition = new Module.Collection();
movePosition.add(new Module.JSVector3D(126.77599416643791, 35.02714918251881, 34.293371013365686));
movePosition.add(new Module.JSVector3D(126.78374897355015, 35.03318059967435, 35.54886215366423));
movePosition.add(new Module.JSVector3D(126.79212321528658, 35.03203801070689, 25.686076117679477));
movePosition.add(new Module.JSVector3D(126.79408620811664, 35.019259090964134, 29.999966450035572));
movePosition.add(new Module.JSVector3D(126.78978362530727, 35.011527249861985, 24.815993944182992));

typoon.moveList(movePosition);
```
{% endtab %}
{% endtabs %}

### setSpeed\(number speed\)

> 태풍 이동 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| speed | number | 태풍 이동 속도. |

* Sample
  * function setTypoonSpeed 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.nameAtLayer("LAYER_TYPOON");
let typoon = Typoonlayer.keyAtObject("Typoon");

typoon.setSpeed(20.0);
```
{% endtab %}
{% endtabs %}

### setUnionTerrain\(boolean union\)

> 태풍 영향권 범위 가시화 옵션.
>
> 태풍 영향권 지형 결합 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| union | boolean | true인 경우 지형결합 가시화\(RTT\)<br> false인 경우 평면 폴리곤 가시화. |

* Sample
  * function setDamageRangeDisplay 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.nameAtLayer("LAYER_TYPOON");
let typoon = Typoonlayer.keyAtObject("Typoon");

Typoon.setUnionTerrain(true);
```
{% endtab %}
{% endtabs %}

### setVisibleDamageRange\(boolean visible\)

> 태풍 영향권 범위 가시화 옵션.
>
> 태풍 영향권 가시화 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| visible | boolean | true인 경우 태풍 영향권 표시<br> false인 경우 태풍 영향권 미표시. |

* Sample
  * function setDamageRangeDisplay 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.nameAtLayer("LAYER_TYPOON");
let typoon = Typoonlayer.keyAtObject("Typoon");

Typoon.setVisibleDamageRange(true);
```
{% endtab %}
{% endtabs %}

### Properties

#### JSTypoon.CreateOptions

| Name     | Type                                | Attributes | Default | Description |
| :---     | :---                                | :---       | :---    | :---        |
| id       | string                              |            |         | 태풍 ID.      |
| position | [JSVector3D](../core/jsvector3d.md) |            |         | 태풍 경위도 위치. |
| size     | number                              | optional   | 500     | 태풍 가시화 크기. |
| height   | number                              | optional   | 100     | 태풍 가시화 높이. |
| complete | function 							 | optional   |         | 태풍 이동 완료 시 동작하는 CallBack |
| damage   | JSTypoon.CreateOptions.Damage 		 | optional   |         | 태풍 영향권 생성 속성 정보. |

#### JSTypoon.CreateOptions.Damage
| Name     | Type                                | Attributes | Default | Description |
| :---     | :---                                | :---       | :---    | :---        |
| size     | number 		                     | optional   | 500     | 영향권 가시화 크기(m단위). |
| altitude     | number 		                 | optional   | 10      | 영향권 가시화 고도(m단위). |
| unionterrain     | boolean 		             | optional   | false   | 영향권 가시화 지형결합 유무. |
| color     | [JSColor](../core/jscolor.md)      | optional   | JSColor\(200, 255, 0, 0\)     | 영향권 가시화 색상. |