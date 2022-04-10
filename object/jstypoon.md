---
description: 태풍 객체 생성 및 수정 기능 API.
---

# JSTypoon

> Module.createTypoon API 생성.

```javascript
var object = Module.createTypoon("typoon");
```

### createbyJson(options) → object

> 태풍 객체를 생성.
>
> argument 변수로 태풍 객체 설정.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                                                         | Description   |
| ---- | ---------------------------------------------------------- | ------------- |
| option | [JSTypoon.CreateOptions](jstypoon.md#jstypoon.createoptions) | 초기화 옵션 속성 정보. |

* Return
  * .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패)
  * .name : 동작 API 명칭
  * .return : API 반환 정보 ( object : 정상적인 반환값, 문자열 : 실패 에러 코드)
  
* Sample
  * function initPage 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather\_typoon)
{% endtab %}

{% tab title="Template" %}
```javascript
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
```
{% endtab %}
{% endtabs %}

### moveStart()

> 태풍 이동 시작.
>
> JSTypoon API moveList에 추가 한 경위도 좌표로 태풍 이동.
>
> 태풍 이동 이벤트 종료 후 생성 위치로 초기화.

{% tabs %}
{% tab title="Information" %}
* Sample
  * function moveTypoon 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather\_typoon)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### moveEnd()

> 태풍 강제 이동 종료.
>
> 태풍 강제 이동 종료 후 생성 위치로 초기화.

{% tabs %}
{% tab title="Information" %}
* Sample
  * function stopTypoon 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather\_typoon)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### moveList(movelist)

> 태풍 이동 경위도 설정.
>
> 입력된 경위도 좌표로 순차적으로 이동.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description       |
| -------- | ----------------------------------- | -------------- |
| movelist | [Collection](../core/collection.md) | 태풍 경위도 좌표 목록. |

* Sample
  * function moveTypoon 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather\_typoon)
{% endtab %}

{% tab title="Template" %}
```javascript
var movePosition = new Module.Collection();
movePosition.add(new Module.JSVector3D(126.77599416643791, 35.02714918251881, 34.293371013365686));
movePosition.add(new Module.JSVector3D(126.78374897355015, 35.03318059967435, 35.54886215366423));
movePosition.add(new Module.JSVector3D(126.79212321528658, 35.03203801070689, 25.686076117679477));
movePosition.add(new Module.JSVector3D(126.79408620811664, 35.019259090964134, 29.999966450035572));
```
{% endtab %}
{% endtabs %}

### setSpeed(speed)

> 태풍 이동 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description  |
| ----- | ------ | --------- |
| speed | number | 태풍 이동 속도. |

* Sample
  * function setTypoonSpeed 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather\_typoon)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setUnionTerrain(type)

> 태풍 영향권 범위 가시화 옵션.
>
> 태풍 영향권 지형 결합 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name  | Type    | Description                                               |
| ----- | ------- | ------------------------------------------------------ |
| type | boolean | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 평면 폴리곤 가시화.</p> |

* Sample
  * function setDamageRangeDisplay 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather\_typoon)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setVisibleDamageRange(type)

> 태풍 영향권 범위 가시화 옵션.
>
> 태풍 영향권 가시화 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name    | Type    | Description                                           |
| ------- | ------- | -------------------------------------------------- |
| type | boolean | <p>true인 경우 태풍 영향권 표시<br>false인 경우 태풍 영향권 미표시.</p> |

* Sample
  * function setDamageRangeDisplay 참조
  * [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather\_typoon)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTypoon.CreateOptions

> 태풍 객체 생성 옵션.

| Name     | Type                                                                       | Attributes | Default | Description              |
| ------ | -------------------------------------------------------------------------- | -------- | ----- | ---------------------- |
| id       | string                                                                     |            |         | 태풍 ID.                   |
| position | [JSVector3D](../core/jsvector3d.md)                                        |            |         | 태풍 경위도 위치.               |
| size     | number                                                                     | optional   | 500     | 태풍 가시화 크기.               |
| height   | number                                                                     | optional   | 100     | 태풍 가시화 높이.               |
| complete | function                                                                   | optional   |         | 태풍 이동 완료 시 동작하는 CallBack |
| damage   | [JSTypoon.CreateOptions.Damage](jstypoon.md#jstypoon.createoptions.damage) | optional   |         | 태풍 영향권 생성 속성 정보.         |

#### JSTypoon.CreateOptions.Damage

> 태풍 영향권 객체 생성 옵션.

| Name         | Type                          | Attributes | Default                 | Description      |
| ------------ | ----------------------------- | ---------- | ----------------------- | ---------------- |
| size         | number                        | optional   | 500                     | 영향권 가시화 크기(m단위). |
| altitude     | number                        | optional   | 10                      | 영향권 가시화 고도(m단위). |
| unionterrain | boolean                       | optional   | false                   | 영향권 가시화 지형결합 유무. |
| color        | [JSColor](../core/jscolor.md) | optional   | JSColor(200, 255, 0, 0) | 영향권 가시화 색상.      |
