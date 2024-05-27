---
description: 태풍 객체 생성 및 수정 기능 API.
---

# JSTypoon

> Module.createTypoon API 생성.

```javascript
var object = Module.createTypoon("typoon");
```

### create(pos, size, alt) → boolean

> 태풍 오브젝트의 위치 및 크기를 설정.

{% tabs %}
{% tab title="Information" %}

| Name | Type       | Description                                                                                            |
| ---- | ---------- | ------------------------------------------------------------------------------------------------------ |
| pos  | JSVector3D | 태풍 위치.<br>Longitude : 경도(Degree)</br><br>Latitude : 위도(Degree)</br><br>Altitude : 고도(m)</br> |
| size | double     | 태풍 너비.                                                                                             |
| alt  | double     | 태풍 높이.                                                                                             |

{% endtab %}
{% tab title="Template" %}

```javascript
var vPosition = new Module.JSVector3D(126.7824826, 35.0119469, 15.2752179);
typoon.create(vPosition, 500.0, 150.0);
```

{% endtab %}
{% endtabs %}

### createbyJson(options) → object

> 태풍 객체를 생성.
>
> argument 변수로 태풍 객체 설정.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                                         | Description |
| ------ | ------------------------------------------------------------ | ----------- |
| option | [JSTypoon.CreateOptions](jstypoon.md#jstypoon.createoptions) | 속성 정보.  |

-   Return
    -   .result: API 성공 유무 상태 ( 1 : 성공, 0 : 실패)
    -   .name: 동작 API 명칭
    -   .return: API 반환 정보 ( object : 정상적인 반환값, 문자열 : 실패 에러 코드)
-   Sample
    -   function initPage 참조
    -   [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

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

### getId() → string

> 오브젝트의 Key를 반환.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   유효한 문자열(string) : 오브젝트의 Key 반환 성공.
    -   빈 문자열(string) : 오브젝트가 null인 경우.
        {% endtab %}

{% tab title="Template" %}

```javascript
var strKey = object.getId();
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

-   Sample
    -   function moveTypoon 참조
    -   [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
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

-   Sample
    -   function stopTypoon 참조
    -   [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
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
| Name | Type | Description |
| -------- | ----------------------------------- | -------------- |
| movelist | [Collection](../core/collection.md) | 태풍 경위도 좌표 목록. |

-   Sample
    -   function moveTypoon 참조
    -   [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
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

> 태풍의 피해 범위를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----- | ------ | --------- |
| danger | boolean | 위혐/경고 타입 설정.<br>true : </br><br>false : 피해 범위 타입을 '경고' 수준으로 설정</br> |
| size | boolean | 피해 범위. |
| alt | boolean | 범위 출력 고도. |
| color | boolean | 표시 색상. |
{% endtab %}

{% tab title="Template" %}

```javascript
var rangeColor = new Module.JSColor(255, 255, 255, 0);
typoon.setDamageRange(true, 300.0, 10.0, rangeColor);
```

{% endtab %}
{% endtabs %}

### setRotationSpeed(speed)

> 태풍의 회전 속도를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----- | ------ | --------- |
| speed | number | 태풍 회전 속도. |

-   Sample
    -   function setTypoonSpeed 참조
    -   [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setSize(radius, alt)

> 태풍의 크기를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----- | ------ | --------- |
| radius | number | 태풍 반경. |
| alt | number | 태풍 높이. |
{% endtab %}

{% tab title="Template" %}

```javascript
typoon.setSize(500.0, 150.0);
```

{% endtab %}
{% endtabs %}

### setSpeed(speed)

> 태풍 이동 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----- | ------ | --------- |
| speed | number | 태풍 이동 속도. |

-   Sample
    -   function setTypoonSpeed 참조
    -   [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
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
| Name | Type | Description |
| ----- | ------- | ------------------------------------------------------ |
| type | boolean | <p>true인 경우 지형결합 가시화(RTT)<br>false인 경우 평면 폴리곤 가시화.</p> |

-   Sample
    -   function setDamageRangeDisplay 참조
    -   [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTextureURL(url)

> 태풍 이미지 URL을 설정합니다. (이미지는 1024\*1024 크기를 지원합니다.).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ----- | ------ | --------- |
| url | string | 태풍 이미지 URL. |
{% endtab %}

{% tab title="Template" %}

```javascript
typoon.setTextureURL("./image/Typoon.png");
```

{% endtab %}
{% endtabs %}

### setVisibleDamageRange(type)

> 태풍 영향권 범위 가시화 옵션.
>
> 태풍 영향권 가시화 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ------- | ------- | -------------------------------------------------- |
| type | boolean | <p>true인 경우 태풍 영향권 표시<br>false인 경우 태풍 영향권 미표시.</p> |

-   Sample
    -   function setDamageRangeDisplay 참조
    -   [샌드박스\_태풍](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
        {% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getDescription() → string

> 오브젝트의 설명에 대한 내용을 반환.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   유효한 문자열(string) : 오브젝트 설명 문자열 반환 성공.
    -   빈 문자열(string) : 오브젝트가 null인 경우.
        {% endtab %}

{% tab title="Template" %}

```javascript
var strDesc = object.getDescription();
```

{% endtab %}
{% endtabs %}

### setDescription(desc)

> 오브젝트의 설명에 대한 설명을 저장.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| desc | string | 오브젝트 설명 문자열. |
{% endtab %}

{% tab title="Template" %}

```javascript
object.setDescription("First Object.");
```

{% endtab %}
{% endtabs %}

### getName() → string

> 오브젝트의 이름을 반환.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   유효한 문자열(string) : 오브젝트의 이름 반환 성공.
    -   빈 문자열(string) : 오브젝트가 null인 경우.
        {% endtab %}

{% tab title="Template" %}

```javascript
var objName = object.getName();
```

{% endtab %}
{% endtabs %}

### setName(name)

> 오브젝트의 이름을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| name | string | 설정할 오브젝트 이름. |
{% endtab %}

{% tab title="Template" %}

```javascript
object.setName("MyObject");
```

{% endtab %}
{% endtabs %}

### getVisible() → number

> 오브젝트의 보기/숨김 여부를 반환.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [옵션 설정 상수](../etc/type-list.md#navigation-visible-type-list) 반환.
    -   보기 : Module.JS_VISIBLE_ON
    -   숨김 : Module.JS_VISIBLE_OFF 에러 발생 : Module.JS_SELECTABLE_ERROR(오브젝트가 NULL인 경우)
        {% endtab %}

{% tab title="Template" %}

```javascript
var objName = object.getName();
```

{% endtab %}
{% endtabs %}

### setVisible(visible)

> 오브젝트의 보기/숨김 여부를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| visible | number | <p><a href="../etc/type-list.md#navigation-visible-type-list">옵션 설정 상수</a>.<br>보기 : Module.JS_VISIBLE_ON<br>숨김 : Module.JS_VISIBLE_OFF<br></p> |
{% endtab %}

{% tab title="Template" %}

```javascript
object.setVisible(Module.JS_VISIBLE_ON);
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTypoon.CreateOptions

> 태풍 객체 생성 옵션.

| Name     | Type                                                                       | Attributes | Default | Description                         |
| -------- | -------------------------------------------------------------------------- | ---------- | ------- | ----------------------------------- |
| id       | string                                                                     |            |         | 태풍 ID.                            |
| position | [JSVector3D](../core/jsvector3d.md)                                        |            |         | 태풍 경위도 위치.                   |
| size     | number                                                                     | optional   | 500     | 태풍 가시화 크기.                   |
| height   | number                                                                     | optional   | 100     | 태풍 가시화 높이.                   |
| complete | function                                                                   | optional   |         | 태풍 이동 완료 시 동작하는 CallBack |
| damage   | [JSTypoon.CreateOptions.Damage](jstypoon.md#jstypoon.createoptions.damage) | optional   |         | 태풍 영향권 생성 속성 정보.         |

#### JSTypoon.CreateOptions.Damage

> 태풍 영향권 객체 생성 옵션.

| Name         | Type                          | Attributes | Default                 | Description                  |
| ------------ | ----------------------------- | ---------- | ----------------------- | ---------------------------- |
| size         | number                        | optional   | 500                     | 영향권 가시화 크기(m단위).   |
| altitude     | number                        | optional   | 10                      | 영향권 가시화 고도(m단위).   |
| unionterrain | boolean                       | optional   | false                   | 영향권 가시화 지형결합 유무. |
| color        | [JSColor](../core/jscolor.md) | optional   | JSColor(200, 255, 0, 0) | 영향권 가시화 색상.          |
