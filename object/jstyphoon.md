---
description: 지도 내 태풍을 표현하는 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSTyphoon

> Module.createTyphoon() API를 생성합니다.

```javascript
var object = Module.createTyphoon("id");
```

## Function

### create(position, size, alt) → boolean

> 태풍 객체의 위치와 크기를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                   |
| -------- | ----------------------------------- | ----------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 중심 좌표 (경도, 위도, 고도). |
| size     | number                              | 크기.                         |
| alt      | number                              | 높이.                         |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
var vPosition = new Module.JSVector3D(126.7824826, 35.0119469, 15.2752179);
typhoon.create(vPosition, 500.0, 150.0);
```

{% endtab %}
{% endtabs %}

### createbyJson(options) → object

> 태풍 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                            | Description |
| ------ | --------------------------------------------------------------- | ----------- |
| option | [JSTyphoon.CreateOptions](jstyphoon.md#jstyphoon.createoptions) | 속성 정보.  |

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패)
    -   .name : 동작 API 명칭
    -   .return : API 반환 정보 ( object : 정상적인 반환값, 문자열 : 실패 에러 코드)
-   Sample
    -   function initPage 참조.
    -   [Sandbox_Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}

```javascript
let json = {
    id: "Typhoon",
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

### getId() → string

> 객체의 고유 명칭을 반환 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strKey = object.getId();
```

{% endtab %}
{% endtabs %}

### moveStart()

> 태풍 객체 이동 이벤트를 동작 합니다.
>
> [moveList()](jstyphoon.md#movelistlist)를 통해 추가된 좌표로 태풍이 이동합니다.
>
> 태풍 객체 이동 이벤트 종료 후 위치로 초기화합니다.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   function moveTyphoon 참조.
    -   [Sandbox_Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### moveEnd()

> 태풍 객체 이동 이벤트를 종료합니다.
>
> 태풍 객체 이동 이벤트 종료 후 위치로 초기화합니다.

{% tabs %}
{% tab title="Information" %}

-   Sample
    -   function stopTyphoon 참조.
    -   [Sandbox_Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### moveList(list)

> 태풍 객체을 이동 정점 좌표(경도, 위도, 고도)을 추가합니다.
>
> 입력된 정점 좌표를 순차적으로 이동합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                                | Description    |
| ---- | ----------------------------------- | -------------- |
| list | [Collection](../core/collection.md) | 이동 좌표 목록 |

-   Sample
    -   function moveTyphoon 참조.
    -   [Sandbox_Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typoon)

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

### setDamageRange(danger, size, alt, color)

> 태풍 객체의 피해 범위를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                          | Description                                                   |
| ------ | ----------------------------- | ------------------------------------------------------------- |
| danger | boolean                       | <p>true: '위험' 상태 가시화.<br>false: '경도' 상태 가시화.<p> |
| size   | number                        | 피해 범위(in meter).                                          |
| alt    | number                        | 피해 범위 출력 해발고도(in meter).                            |
| color  | [JSColor](../core/jscolor.md) | 표시 색상값.                                                  |

{% endtab %}
{% tab title="Template" %}

```javascript
var rangeColor = new Module.JSColor(255, 255, 255, 0);
typhoon.setDamageRange(true, 300.0, 10.0, rangeColor);
```

{% endtab %}
{% endtabs %}

### setRotationSpeed(speed)

> 태풍 객체의 회전 속도를 설정합니다..

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| speed | number | 회전 속도.  |

-   Sample
    -   function setTyphoonSpeed 참조.
    -   [Sandbox_Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSize(radius, alt)

> 태풍 객체 크기를 설정 합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description |
| ------ | ------ | ----------- |
| radius | number | 태풍 반경.  |
| alt    | number | 태풍 높이.  |

{% endtab %}

{% tab title="Template" %}

```javascript
typhoon.setSize(500.0, 150.0);
```

{% endtab %}
{% endtabs %}

### setSpeed(speed)

> 태풍 이동 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| speed | number | 이동 속도.  |

-   Sample
    -   function setTyphoonSpeed 참조.
    -   [Sandbox_Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setUnionTerrain(type)

> 태풍 객체를 구성하는 영향권 범위 가시화 옵션을 설정합니다.
>
> 영향권 범위를 지형 결합 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                |
| ---- | ------- | ---------------------------------------------------------- |
| type | boolean | <p>true: 지형 결합 가시화(RTT).<br>false: 일반 기시화.</p> |

-   Sample
    -   function setDamageRangeDisplay 참조.
    -   [Sandbox_Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTextureURL(url)

> 태풍 객체를 구성하는 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| url  | string | 이미지 url. |

{% endtab %}
{% tab title="Template" %}

```javascript
typhoon.setTextureURL("./image/Typhoon.png");
```

{% endtab %}
{% endtabs %}

### setVisibleDamageRange(type)

> 태풍 객체를 구성하는 영향권 범위 가시화 유무 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                                      |
| ---- | ------- | ---------------------------------------------------------------- |
| type | boolean | <p>true: 영향권 범위 가시화.<br>false: 영향권 범위 비가시화.</p> |

-   Sample
    -   function setDamageRangeDisplay 참조.
    -   [Sandbox_Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getPosition() → [JSVector3D](../core/jsvector3d.md)

> 태풍 객체의 현재 위치(경도, 위도, 고도)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 반환 성공.
    -   [JSVector3D](../core/jsvector3d.md)(0, 0, 0): 객체가 없거나 태풍 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var position = typhoon.getPosition();
```

{% endtab %}
{% endtabs %}

### setMoveFinishReturn(set) → boolean

> 이동 이벤트([moveStart()](jstyphoon.md#movestart)) 종료 후 시작 위치로 복귀할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                          |
| ---- | ------- | ------------------------------------------------------ |
| set  | boolean | true: 이동 종료 후 시작 위치로 복귀, false: 복귀 안 함. |

-   Return
    -   true: 설정 성공.
    -   false: 객체가 없거나 태풍 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
typhoon.setMoveFinishReturn(true);
```

{% endtab %}
{% endtabs %}

### currentMoveListIndex() → number

> [moveList()](jstyphoon.md#movelistlist)로 설정된 이동 경로 중, 현재 진행 중인 구간의 시작점 인덱스를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 현재 이동 구간의 시작점 인덱스.

{% endtab %}
{% tab title="Template" %}

```javascript
var index = typhoon.currentMoveListIndex();
```

{% endtab %}
{% endtabs %}

### setMoveListIndex(index) → boolean

> [moveList()](jstyphoon.md#movelistlist)로 설정된 이동 경로 중, 지정한 인덱스의 좌표로 위치를 이동시킵니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| ----- | ------ | ------------- |
| index | number | 이동할 목표 인덱스. |

-   Return
    -   true: 이동 성공.
    -   false: 이동 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
typhoon.setMoveListIndex(2);
```

{% endtab %}
{% endtabs %}

### movePauseResume()

> 진행 중인 이동([moveStart()](jstyphoon.md#movestart))을 일시정지하거나 다시 재개합니다.
>
> 호출할 때마다 정지/재개 상태가 반전됩니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
typhoon.movePauseResume(); // 정지
typhoon.movePauseResume(); // 재개
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getDescription(), setDescription(desc) → string

> 객체에 대한 설명을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| desc | string | 설명 문자열. |

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strDesc = object.getDescription();
// ... or ...
object.setDescription("First Object.");
```

{% endtab %}
{% endtabs %}

### getName(), setName(name) → string

> 객체 이름을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 이름.  |

-   Return
    -   string: 객체 이름을 성공적을 반환
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setName("MyObject");
```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean

> 객체의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                        |
| ------- | ------- | -------------------------------------------------- |
| visible | boolean | <p>true: 객체 가시화.<br>false: 객체 비가시화.</p> |

-   Return
    -   true: 객체 가시화 상태.
    -   false: 객체 비가시화 상태.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setVisible(true);
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTyphoon.CreateOptions

> 태풍 객체 생성 옵션.

| Name     | Type                                                                         | Attributes | Default | Description                            |
| -------- | ---------------------------------------------------------------------------- | ---------- | ------- | -------------------------------------- |
| id       | string                                                                       |            |         | 고유 명칭.                             |
| position | [JSVector3D](../core/jsvector3d.md)                                          |            |         | 중심 좌표 (경도, 위도, 고도).          |
| size     | number                                                                       | optional   | 500     | 태풍 크기 (in meters).                 |
| height   | number                                                                       | optional   | 100     | 태풍 높이 (in meters).                 |
| complete | function                                                                     | optional   |         | 이동 이벤트 완료 시 동작하는 callback. |
| damage   | [JSTypoon.CreateOptions.Damage](jstyphoon.md#jstyphoon.createoptions.damage) | optional   |         | 영향권 생성 속성 정보.                 |

#### JSTyphoon.CreateOptions.Damage

> Typhoon impact range object creation options.

| Name         | Type                          | Attributes | Default                 | Description                   |
| ------------ | ----------------------------- | ---------- | ----------------------- | ----------------------------- |
| size         | number                        | optional   | 500                     | 영향권 크기 (in meters).      |
| altitude     | number                        | optional   | 10                      | 영향권 생성 고도 (in meters). |
| unionterrain | boolean                       | optional   | false                   | 지형 결합 유무.               |
| color        | [JSColor](../core/jscolor.md) | optional   | JSColor(200, 255, 0, 0) | 생상값.                       |
