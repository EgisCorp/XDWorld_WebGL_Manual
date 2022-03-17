---
description: 태풍 오브젝트 설정 및 반환 기능 API.
---

# JSTypoon

Module createTypoon API로 생성할 수 있습니다.

```javascript
var object = Module.createTypoon("typoon");
```

## createbyJson\( options \) → object

> 태풍 오브젝트를 생성.
>
> argument 변수로 태풍 오브젝트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| option | object | 태풍 생성 속성 정보. |

| option\_tag | Type | Contents |
| :--- | :--- | :--- |
| id | string | 태풍 ID \(필수 항목\). |
| position | [JSVector3D](../core/jsvector3d.md) | 태풍 경위도 위치 \(필수 항목\). |
| size | number | 태풍 가시화 크기 \[미설정 시 500\]. |
| height | number | 태풍 가시화 높이 \[미설정 시 100\]. |
| complete | function | 태풍 이동 완료 시 동작하는 CallBack |
| damage | object | 태풍 영향권 생성 속성 정보. |

| damage\_tag | Type | Contents |
| :--- | :--- | :--- |
| size | number | 영향권 가시화 크기(m단위) \[미설정 시 500\] |
| altitude | number | 영향권 가시화 고도(m단위) \[미설정 시 10\] |
| unionterrain | boolean | 영향권 가시화 지형결합 유무 \[미설정 시 false\] |
| color | [JSColor](../core/jscolor.md) | 영향권 가시화 색상 \[미설정 시 JSColor\(200, 255, 0, 0\)\]|

* Return
  * .result : API 성공 유무 상태 \( 1 : 성공,  0 : 실패 \)
  * .name : 동작 API 명칭
  * .return : API 반환 정보 \( object : 정상적인 반환값, 문자열 : 실패 에러 코드 \)
* Code
  * function initPage 참조
  * [http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)
{% endtab %}
{% endtabs %}

## moveStart\( \)

> 태풍 이동 시작.
>
> JSTypoon API moveList에 추가 한 경위도 좌표로 태풍 이동.
>
> 태풍 이동 이벤트 종료 후 생성 위치로 초기화.

{% tabs %}
{% tab title="Information" %}

* Code
  * function moveTypoon 참조
  * [http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% endtabs %}

## moveEnd\( \)

> 태풍 강제 이동 종료.
>
> 태풍 강제 이동 종료 후 생성 위치로 초기화.
{% tabs %}
{% tab title="Information" %}

* Code
  * function stopTypoon 참조
  * [http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% endtabs %}

## moveList\( movelist \)

> 태풍 이동 경위도 설정.
>
> 입력된 경위도 좌표로 순차적으로 이동.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| movelist | [Collection](../core/collection.md) | 태풍 경위도 좌표 리스트. |

* Code
  * function moveTypoon 참조
  * [http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% endtabs %}

## setSpeed\( speed \)

> 태풍 이동 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| speed | number | 태풍 이동 속도. |

* Code
  * function setTypoonSpeed 참조
  * [http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% endtabs %}

## setUnionTerrain\( union \)

> 태풍 영향권 범위 가시화 옵션.
>
> 태풍 영향권 지형 결합 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| union | boolean | 태풍 영향권 가시화 옵션. |

* Detail
  * union
    * TRUE : RTT 가시화 \( 지형결합 \).
    * FALSE : 평면 폴리곤 가시화.

* Code
  * function setDamageRangeDisplay 참조
  * [http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% endtabs %}

## setVisibleDamageRange\( visible \)

> 태풍 영향권 범위 가시화 옵션.
>
> 태풍 영향권 가시화 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| visible | boolean | 태풍 영향권 가시화 옵션. |

* Detail
  * visible
    * TRUE : 태풍 영향권 표시.
    * FALSE : 태풍 영향권 미 표시.

* Code
  * function setDamageRangeDisplay 참조
  * [http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon](http://sandbox.dtwincloud.com/code/main.do?id=weather_typoon)

{% endtab %}
{% endtabs %}