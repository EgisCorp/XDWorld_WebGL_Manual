---
description: 지도 내 레이어 설정 API를 제공합니다.
---

# JSLayer

## 생성자 **Constructor -&gt; \( JSLayer \)**

> 인스턴스 JSLayer 생성

{% tabs %}
{% tab title="Infomation" %}
| No. | API | Contents |
| :--- | :--- | :--- |
| 1 | JSLayer\(\) | 사용자 레이어 반환 |
* Code
```javascript
let layerList = new Module.JSLayerList( true );
let layer = layerList.createLayer( layername );
```
{% endtab %}
{% endtabs %}

## addObject\( JSObject \_object, number \_level \)

> 해당 레이어 오브젝트 추가

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_object | JSObject | 생성 된 오브젝트 추가 |
| \_level | number | 0 값으로 사용 |
* Code

```javascript
let layername = "objectlayer"
let layerList = new Module.JSLayerList( true );
let layer = layerList.createLayer( layername );
// object 생성 과정
layer.addObject(object, 0);
```
{% endtab %}
{% endtabs %}

## indexAtKey\( number \_index \)\) -&gt; **\(** string **\)**

> 해당 레이어에서 오브젝트 명칭 반환
>
> 레이어 오브젝트 관리는 리스트로 구성
>
> 리스트 해당 인덱스 번호로 오브젝트 명칭 반환

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_index | number | 목표 오브젝트 인덱스. |
* Return
	* 문자열 : 인덱스 해당 오브젝트 명칭 반환 성공
	* 빈 문자열 : 인덱스 해당 오브젝트 명칭 반환 실패
		- 명칭 반환 실패 조건
			- \_index가 오브젝트 리스트 범위를 초과한 경우 \(0보다 작거나 오브젝트 리스트 수 보다 큰 경우\)
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## indexAtObject\( number \_index \)\) -&gt; **\(** JSObject **\)**

> 해당 레이어에서 오브젝트 반환
>
> 레이어 오브젝트 관리는 리스트로 구성
>
> 리스트 해당 인덱스 번호로 오브젝트 반환

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_index | number | 목표 오브젝트 인덱스. |
* Return
	* JSObject : 비교 ID와 동일한 오브젝트 반환 성공
	* null : 비교 ID와 동일한 오브젝트 반환 실패
		- 명칭 반환 실패 조건
			- \_index가 오브젝트 리스트 범위를 초과한 경우 \(0보다 작거나 오브젝트 리스트 수 보다 큰 경우\)
			- 해당 레이어 객체 수가 0인 경우
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## keyAtObject\( string \_objectid \)\) -&gt; **\(** JSObject **\)**

> 해당 레이어에서 오브젝트 반환
>
> 레이어 오브젝트 관리는 리스트로 구성
>
> 오브젝트 리스트 ID와 \_objectid 비교 후 조건에 만족하는 오브젝트 반환

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_objectid | string | 목표 오브젝트 ID. |
* Return
	* JSObject : 비교 ID와 동일한 오브젝트 반환 성공
	* NULL : 비교 ID와 동일한 오브젝트 반환 실패
	  - 명칭 반환 실패 조건
		- ID와 동일한 오브젝트가 없을 경우
		- \_objectid 빈공백 일 경우
		- 해당 레이어 객체 수가 0인 경우
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## removeAtIndex\(number \_index\) -&gt; **\(** boolean **\)**

> 레이어 속한 오브젝트 삭제
>
> 레이어 오브젝트 리스트에서 인덱스 번호에 해당되는 오브젝트 삭제

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_index | number | 삭제 오브젝트 인덱스 |
* Return
	* TRUE : 오브젝트 삭제 성공
	* FALSE : 오브젝트 삭제 실패
	  - 삭제 실패 조건
		- \_index가 오브젝트 리스트 범위를 초과한 경우 \(0보다 작거나 오브젝트 리스트 수 보다 큰 경우\)
		- 해당 레이어 객체 수가 0인 경우
		- 서비스 레이어 경우\(서비스 레이어는 tile 기반으로 오브젝트는 tile에 종속 된다.\)
		- 외부 서버를 통해 로드된 데이터인 경우\(Ex. WMS, WFS\)
* Code
```javascript
let layername = "objectlayer"
let layerList = new Module.JSLayerList(true);
let    layerList.createLayer(layername );

// object 생성 과정

layer.addObject(object, 0);
layer.removeAtIndex(0);
```
{% endtab %}
{% endtabs %}

## removeAtKey\( string \_objectid \) -&gt; **\(** boolean **\)**

> 레이어 속한 오브젝트 삭제
>
> 오브젝트 리스트 ID와 \_objectid 비교 후 조건에 만족하는 오브젝트 삭제

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_objectid | string | 목표 오브젝트 ID. |
* Return
	* TRUE : 오브젝트 삭제 성공
	* FALSE : 오브젝트 삭제 실패
	  - 삭제 실패 조건
		- \_objectid가 동일한 오브젝트가 없을 경우
		- \_objectid 빈공백 일 경우
		- 해당 레이어 객체 수가 0인 경우
		- 서비스 레이어 경우\(서비스 레이어는 tile 기반으로 오브젝트는 tile에 종속 된다.\)
		- 외부 서버를 통해 로드된 데이터인 경우\(Ex. WMS, WFS\)
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## removeAtObject\( JSObject \_object \) -&gt; **\(** boolean **\)**

> 레이어 속한 오브젝트 삭제
>
> 레이어 오브젝트 리스트와 \_object와 비교 후 조건에 만족하는 오브젝트 삭제

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_object | JSObject | 목표 오브젝트. |

* Return
	* TRUE : 오브젝트 삭제 성공
	* FALSE : 오브젝트 삭제 실패
	  - 삭제 실패 조건
		- \_object와 동일한 오브젝트가 없을 경우
		- 해당 레이어 객체 수가 0인 경우
		- 서비스 레이어 경우\(서비스 레이어는 tile 기반으로 오브젝트는 tile에 종속 된다.\)
		- 외부 서버를 통해 로드된 데이터인 경우\(Ex. WMS, WFS\)
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## removeAll\( \) -&gt; **\(** boolean **\)**

> 레이어 속한 오브젝트 삭제
>
> 레이어 오브젝트 리스트 전체 삭제

{% tabs %}
{% tab title="Infomation" %}
* Return
	* TRUE : 오브젝트 삭제 성공
	* FALSE : 오브젝트 삭제 실패
	  - 삭제 실패 조건
		- 해당 레이어 객체 수가 0인 경우
		- 서비스 레이어 인 경우\( 서비스 레이어에서 오브젝트는 tile에 종속.\)
		- 외부 서버를 통해 로드된 데이터인 경우\(Ex. WMS, WFS\)
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## getObjectCount\( \) -&gt; **\(** number **\)**

> 레이어 속한 오브젝트 갯수 반환

{% tabs %}
{% tab title="Infomation" %}
* Return
	* result&gt;0 : 해당 레이어 오브젝트 갯수
	* -1 : 해당 레이어에 오브젝트가 존재 하지 않는 경우
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## setConnectionWMS\( string \_url, number \_port, string \_option \) -&gt; **\(** boolean **\)**

> WMS 연결 옵션을 설정합니다.
>
> WMS 연결 URL 구성 요소.
>
> WMS는 서비스 레이어

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_url | string | GeoServer 해당 레이어 URL. |
| ~~\_port~~ | ~~number~~ | ~~통신 포트 번호.~~ |
| ~~\_option~~ | ~~string~~ | ~~GeoServer 레이어 옵션.~~ |
* Return
	* TRUE : WMS 연결 옵션 설정 성공
	* FALSE : WMS 연결 옵션 설정 실패
	  - 옵션 설정 실패 조건
		- 사용자 레이어 인 경우
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## clearWMSCache\( \)

> WMS 레이어 삭제
>
> 가시화 된 WMS 이미지 정보를 삭제 합니다.

{% tabs %}
{% tab title="Infomation" %}
* Input, Output 정보 없음
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## setWMSTransparent\( boolean \_option \)

> WMS 가시화 옵션을 설정
>
> WMS 연결 URL 구성 요소.
>
> WMS 투명 처리 옵션 설정

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_option | boolean | WMS 투명 설정. |

* Detail
	*  \_move Type
		- TRUE : 이미지 반투명 출력\(영상 이미지 + WMS 이미지\)
		- FALSE : 이미지 불투명 출력\(WMS 이미지\)
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## setLayersWMS\( string \_layername \) -&gt; **\(** boolean **\)**

> WMS 가시화 옵션을 설정
>
> WMS 연결 URL 구성 요소.
>
> GoeServer 요청 레이어 명칭 설정

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layername | string | WMS 요청 레이어 명칭 설정. |
* Return
	* TRUE : WMS 가시화 옵션 설정 성공
	* FALSE : WMS 가시화 옵션 설정 실패
	  - 옵션 설정 실패 조건
		- 사용자 레이어 인 경우
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## setLevelWMS\( number \_minlevel, number \_maxlevel \) -&gt; **\(** boolean **\)**

> WMS 가시화 옵션을 설정
>
> WMS 연결 URL 구성 요소.
>
> GoeServer 요청 레벨 범위 설정

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_minlevel | number | WMS 요청 가시화 최소 레벨 설정. |
| \_maxlevel | number | WMS 요청 가시화 최대 레벨 설정. |
* Return
	* TRUE : WMS 가시화 옵션 설정 성공
	* FALSE : WMS 가시화 옵션 설정 실패
	  - 옵션 설정 실패 조건
		- 사용자 레이어 인 경우
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## setTileSizeWMS\( number \_size \) -&gt; **\(** boolean **\)**

> WMS 가시화 옵션을 설정
>
> WMS 연결 URL 구성 요소.
>
> GoeServer 요청 이미지 사이즈 설정

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_size | number | WMS 요청 이미지 사이즈\(가로 세로 정사각형 비율\). |
* Return
	* TRUE : WMS 가시화 옵션 설정 성공
	* FALSE : WMS 가시화 옵션 설정 실패
	  - 옵션 설정 실패 조건
		- 사용자 레이어 인 경우
* Code
```javascript

```
{% endtab %}
{% endtabs %}

## setStylesWMS\( number \_size \) -&gt; **\(** boolean **\)**

> WMS 가시화 옵션을 설정
>
> WMS 연결 URL 구성 요소.
>
> GoeServer 요청 스타일 설정

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_size | number | WMS 요청 이미지 사이즈\(가로 세로 정사각형 비율\). |
* Return
	* TRUE : WMS 가시화 옵션 설정 성공
	* FALSE : WMS 가시화 옵션 설정 실패
	  - 옵션 설정 실패 조건
		- 사용자 레이어 인 경우
* Code
```javascript

```
{% endtab %}
{% endtabs %}

