---
description: 지도 내 그리드 분석 객체 생성 및 설정 API.
---

# JSGridAnal

> Module.getAnalysis().getGridAnal API 생성.

```javascript
var object = Module.getAnalysis().getGridAnal();
```

## clear()

> 현재 처리되는 모든 그리드 분석 결과를 초기화.

{% tabs %}
{% tab title="Information" %} 

* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## openGridDataURL(url, nTime, nStripSize, nStriptStart, nStripEnd, nDataType)

> 바이너리 격자 분석 결과 데이터를 URL 호출.
> 
> nTime 입력값 범위 0을 포함한 정수형 인덱스, 0-base 배열 번호.
> 
> nStripSize 입력값 범위 0보다 큰 정수형 byte 크기.
> 
> nStriptStart 입력값 범위 각 셀의 시작 포인터부터 데이터를 읽기를 진행할 시작점 byte 오프셋.
> 
> nStripEnd 입력값 범위 각셀의 시작 포인터부터 데이터를 읽기를 종료할 지점 byte 오프셋.
> 
> 읽을 셀의 크기 = (nStripEnd - nStriptStart), 단위 byte.
>
> nDataType 입력값에 따른 정보 0 (정수형 4 byte), 1(실수형 4 byte), 2(실수형 8 byte).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| url | string | http 통신 요청 파일 URL. |
| nTime | number | 분석 결과 데이터의 시계열 인덱스. |
| nStripSize | number | 격자 데이터 셀의 byte 크기 (정수형). |
| nStriptStart | number | 수집할 데이터 셀의 시작 오프셋 (정수형). |
| nStripEnd | number | 수집할 데이터 셀의 종료 오프셋 (정수형). |
| nDataType | number | 데이터 형식 (정수형). |

* Return
  * 비동기 이벤트 \- Fire_EventLoadDataFinish 통해서 모든 시계열 데이터가 모두 로드되면 발생
  * 예) Module.canvas.addEventListener("Fire_EventLoadDataFinish", OnWindDataLoad);
  
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## setHRange(fmin, fmax)

> 표출할 격자 분석 결과 데이터의 최소, 최대값 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| fmin | number | 최소값. |
| fmax | number | 최대값. | 

* Sample
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## createRasterData(szCat, time) → boolean

> 바이너리 격자 분석 결과 데이터를 지정한 시간 인덱스에 2D Raster 객체로 생성.
> 
> szCat 입력값은 이전 키값과 중복 불가.
> 
> time 입력값은 0 이상의 정수형 시간 인덱스, setTimeRange 값 이상 불가.
> 
> setLayerName("layer_name") API 레이어 명 지정이 없으면 UserLayer에 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| szCat | string | 생성 객체의 키값. |
| time | number | 시계열 인덱스 번호 (정수형). |
  
* Return
  * true : 생성 성공.
  * false : 생성 실패.
  
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## createPlaneData(szCat) → boolean

> 바이너리 격자 분석 결과 데이터를 3D 애니메이션 평면 객체로 생성.
>
> szCat 입력값은 이전 키값과 중복 불가.
>
> 생성 시 기본적으로 시계열 인덱스가 0~최대 시계열수까지 진행으로 애니메이션 수행.
 
{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| szCat | string | 생성 객체의 키값. |
  
* Return
  * true : 생성 성공.
  * false : 생성 실패.
  
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## createArrowData(time) → boolean

> 바이너리 격자 분석 결과 데이터를 지정한 시계열 인덱스에 3D 화살표 객체들로 생성.
>
> time 입력값은 0 이상의 정수형 시간 인덱스, setTimeRange 값 이상 불가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| time | number | 시계열 인덱스 번호 (정수형). |
  
* Return
  * true : 생성 성공.
  * false : 생성 실패.
  
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## setTimeRange(time)

> 바이너리 격자 분석 결과 데이터의 시계열 총 수를 설정.
>
> time 입력값은 기본값 6, 1 이상의 정수값 필요.
>
> 설정 변경은 바이너리 격자 분석 데이터 요청전에 적용 필요.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| time | number | 시계열 총수 (정수형). |
    
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## setHRatio(ratio)

> 3D 애니메이션 평면 객체의 수치별 표현 되는 형상의 높이 배율 조절
>
> ratio 입력값은 3D 애니메이션 평면 객체 생성 후 적용가능, 0이상의 값으로 입력.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| ratio | number | 높이 배율 값 |

* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## setTime(time)

> 3D 애니메이션 평면 객체의 시계열 인덱스를 재설정
>
> time 입력값은 0부터 시계열 총수-1까지의 정수 (0-base Index).
>
> 수치변경에 따른 시계열 애니메이션이 흐르면서 변동, 0 → 6 시 1,2,3,4,5 까지 흐름 이후 6으로 도달

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| time | number | 시계열 인덱스 (정수형) |

* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## getTime() → number

> 3D 애니메이션 평면 객체의 현재 진행중인 시계열 인덱스를 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * 현재 애니메이션 수행 중인 시계열 인덱스 정보 반환 (정수형).
  
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## clearLegend()

> 설정된 범례 값을 초기화.
> 
> 2D Raster 객체 및 3D 애니메이션 평면 객체에 적용되는 격자 색상 범례를 초기화

{% tabs %}
{% tab title="Information" %}

* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## addLegendColor(alpha, red, green, blue) → number

> 범레 리스트에 범례 색상 추가.
> 
> alpha, red, green, blue : ARGB, 0~255 정수형 색상 범위.
> 
> 범례는 격자의 최소~최대값 기준으로 각 격자 값이 범례 리스트의 총수에 비례값으로 적용.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| alpha | number | 투명값 (정수형) |
| red | number | Red 색상값 (정수형) |
| green | number | Green 색상값 (정수형) |
| nBlue | number | Blue 색상값 (정수형) |

* Return
  * 추가된 범례 리스트의 총수 반환
  
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## set3DArrowSizeRatio(ratio)

> 3D 화살표 객체의 화살표 크기 배율을 변경
> 
> ratio 입력값은 0보다 큰 값으로 입력, 격자의 크기값에 대한 배율로 크기 정의.
> 
> 3D 화살표 객체의 생성전에 미리 설정 필요.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| ratio | number | 화살표 크기 배율 변경 |

* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## openGridDataJSON(options) → boolean

> JSON 방식의 격자 결과 데이터 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| options | [JSGridAnal.GridDataOption](jsgridanal.md#jsgridanal.griddataoption) | 격자 정보 설정값 |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
let json = {
	kind : "TestWind",
	timeIndex : 0,
	timeRange : 6,
	callback : cbLoadComple,
	cols : 400,
	rows : 400,
	llcorner : {
		projNum : 13,
		pos : [ 
			[ _x1, _y1],
			[ _x2, _y2]
		]
	},
	size : 25,
	fMin : 1,
	fMax : 1500,
	data : [ 1,2,3,4,5,6,7,8,9,10 ]
};
```
{% endtab %}
{% endtabs %}

## setLayerName(name)

> 격자 분석 결과 데이터를 3D 지도 객체로 생성할 때 적용할 레이어 명칭
> 
> name 입력값은 ""이면 유저레이어에 적용, 지정이 있으면 로컬레이어 리스트의 레이어로 생성하여 적용

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 레이어 명칭 |
  
* Sample
  * function 참조.
  * [샌드박스\_바람 표현](http://sandbox.dtwincloud.com/code/main.do?id=effect_wind)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSGridAnal.GridDataOption

> 그리드 데이터 요청 파라메터

| Name     | Type                                                                       | Attributes | Default | Description              |
| ------ | -------------------------------------------------------------------------- | -------- | ----- | ---------------------- |
| kind | string | | | 격자 데이터 그룹명 |
| timeIndex | number | | | 격자데이터 시게열 인덱스 번호 (정수형) |
| timeRange | number | | | 격자데이터 시계열 총수 (정수형) |
| callback | function | optional | | 격자데이터가 모두 로딩되면 발생하는 콜백 함수 |
| cols | number | | | 격자의 가로 셀 총수 (정수형) | 
| rows | number | | | 격자의 세로 셀 총수 (정수형) |
| llcorner | [JSGridAnal.GridDataOption.llcornerParam](jsgridanal.md#jsgridanalgriddataparamllcornerparam) | | | 좌하단 공간 좌표 객체 |
| size | number | | | 격자의 셀 가로,세로 크기 (단위 : 미터) |
| fMin | number | | | 격자 셀의 최소값 |
| fmax | number | | | 격자 셀의 최대값 |
| data | number | array | | 격자 셀의 데이터 베열 |


#### JSGridAnal.GridDataOption.llcornerParam
> 격자 그리드의 공간 범위 설정 파라메터

| Name     | Type                                                                       | Attributes | Default | Description              |
| ------ | -------------------------------------------------------------------------- | -------- | ----- | ---------------------- |
| projNum | number | | | 좌표계 코드 번호 |
| pos | number | array | | 좌표 범위 배열 \[\[minx, miny\], \[maxx, maxy\]\] 형식 |
