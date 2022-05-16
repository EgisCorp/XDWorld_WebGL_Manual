---
description: 지도 내 지진파 분석 기능 설정 API.
---

# JSEarthquake

> Module.getEarthquake API 생성.

```javascript
var earthquake = Module.getEarthquake();
```

### Clear() → boolean

> 지진파 분석 초기화

{% tabs %}
{% tab title="Information" %}
{% endtab %}

* Return
  * true : 지진파 초기화 성공.
  * false : 지진파 초기화 실패.
    * 지진파 초기화 실패 조건.
      * 지도 갱신이 안된 경우.
      * 지진파 분석이 없는 경우.

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### SetResolution(resolution) → boolean

> 지진파 크기 설정.
>
> 설정된 resolution(단위 : m)으로 가로 세로가 같은 정사각형 영역 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| resolution | number | 지진파 가로세로 크기 설정. |

* Return
  * true : 지진파 크기 설정 성공.
  * false : 지진파 크기 설정 실패.
    * 지진파 크기 설정 실패 조건.
      * 0.001 보다 작은 값이 설정된 경우.

* Sample
  * function setEarthquakeMesh 참조.
  * [샌드박스\_지진파](http://sandbox.dtwincloud.com/code/main.do?id=object_earthquakewave)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### SetHeightWeight(height) → boolean

> 지진파 파형 높이 설정.
>
> 설정된 height(단위 : m) 기준으로 지진파 높이 비율 파형 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| height | number | 지진파 최대 표현 높이 설정. |

* Return
  * true : 지진파 높이 비율 설정 성공.
  * false : 지진파 높이 비율 설정 실패.
    * 지진파 높이 비율 설정 실패 조건.
      * 0.01 보다 작은 값이 설정된 경우.
      * 200 보다 큰 값이 설정된 경우.

* Sample
  * function setEarthquakeMesh 참조.
  * [샌드박스\_지진파](http://sandbox.dtwincloud.com/code/main.do?id=object_earthquakewave)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### SetBaseAltitude(altitude) → boolean

> 지진파 생성 높이 설정.
>
> 해발고도 기준으로 설정된 altitude(단위 : m) 높이 만큼 지진파 위치 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| altitude | number | 지진파 생성 높이 설정. |

* Return
  * true : 지진파 높이 설정 성공.
  * false : 지진파 높이 설정 실패.

* Sample
  * function setEarthquakeMesh 참조.
  * [샌드박스\_지진파](http://sandbox.dtwincloud.com/code/main.do?id=object_earthquakewave)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}


### GetEarthquakeData(url, position) → boolean

> 지진파 생성.
>
> 설정 된 url(.eqs file)은 자체 지진파 파일 포맷.
>
> 지진파 파일 포맷을 로드 하여 지진 파형을 구성.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| url | string | (.eqs) 파일 URL 주소. |
| position | [JSVector2D](../core/jsvector2d.md) | 지진파 생성 경위도. |

* Return
  * true : 지진파 생성 성공.
  * false : 지진파 생성 실패.

* Sample
  * function setEarthquakeMesh 참조.
  * [샌드박스\_지진파](http://sandbox.dtwincloud.com/code/main.do?id=object_earthquakewave)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}