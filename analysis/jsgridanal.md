---
description: 그리드 분석 오브젝트 생성 및 가시화
---

# JSGridAnal

Module getAnalysis().getGridAnal API로 생성할 수 있습니다.

```javascript
var object = Module.getAnalysis().getGridAnal();
```

## clear\(\)

> 그리드 분석 기능 초기화

{% tabs %}
{% tab title="Information" %}

* Detail
  * 현재 처리되는 모든 그리드 분석 결과를 초기화
  
* Return
  * 
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## openGridDataURL\(string szURL, number nTime, number nStripSize, number nStriptStart, number nStripEnd, number nDataType\)

> 바이너리 격자 분석 결과 데이터를 URL 호출

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| szURL | string | 분석 결과 데이터의 URL |
| nTime | number | 분석 결과 데이터의 시계열 인덱스 |
| nStripSize | number | 격자 데이터 셀의 byte 크기 \(정수형\) |
| nStriptStart | number | 수집할 데이터 셀의 시작 오프셋 \(정수형\) |
| nStripEnd | number | 수집할 데이터 셀의 종료 오프셋 \(정수형\) |
| nDataType | number | 데이터 형식 \(정수형\) |

* Detail
  * szURL : http 통신을 통한 접속가능한 파일 URL
  * nTime : 0을 포함한 정수형 인덱스, 0-base 배열 번호
  * nStripSize : 0보다 큰 정수형 byte 크기
  * nStriptStart : 각셀의 시작 포인터부터 데이터를 읽기를 진행할 시작점 byte 오프셋
  * nStripEnd : 각셀의 시작 포인터부터 데이터를 읽기를 종료할 지점 byte 오프셋
  * 읽을 셀의 크기 = \(nStripEnd - nStriptStart\), 단위 byte
  * nDataType : 0 \- 정수형 \( int : 4 byte \)
  * nDataType : 1 \- 실수형 \( float : 4 byte \)
  * nDataType : 2 \- 실수형 \( double : 8 byte \)
  
* Return
  * 비동기 이벤트 \- Fire_EventLoadDataFinish 통해서 모든 시계열 데이터가 모두 로드되면 발생
  * 예) Module.canvas.addEventListener\("Fire_EventLoadDataFinish", OnWindDataLoad\);
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## setHRange\(number fmin, number fmax\)

> 표출할 격자 분석 결과 데이터의 최소, 최대값 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| fmin | number | 최소값 |
| fmax | number | 최대값 |

* Detail
  * 
  
* Return
  * 
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## createRasterData\(string szCat, number nTime\) → boolean

> 바이너리 격자 분석 결과 데이터를 지정한 시간 인덱스에 2D Raster 객체로 생성

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| szCat | string | 생성 객체의 키값 |
| nTime | number | 시계열 인덱스 번호 (정수형) |

* Detail
  * szCat : 이전 결과의 키값과 중복 불가
  * nTime : 0 이상의 정수형 시간 인덱스, setTimeRange 값 이상 불가
  * setLayerName\("layer_name"\) API 레이어 명 지정이 없으면 UserLayer에 추가
  
* Return
  * 생성 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## createPlaneData\(string szCat\) → boolean

> 바이너리 격자 분석 결과 데이터를 3D 애니메이션 평면 객체로 생성

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| szCat | string | 생성 객체의 키값 |

* Detail
  * szCat : 이전 결과의 키값과 중복 불가
  * 생성시 기본적으로 시계열 인덱스가 0~최대 시계열수까지 진행으로 애니메이션 수행
  
* Return
  * 생성 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## createArrowData\(number nTime\) → boolean

> 바이너리 격자 분석 결과 데이터를 지정한 시계열 인덱스에 3D 화살표 객체들로 생성

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| nTime | number | 시계열 인덱스 번호 (정수형) |

* Detail
  * nTime : 0 이상의 정수형 시간 인덱스, setTimeRange 값 이상 불가
  
* Return
  * 생성 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## setTimeRange\(number nTimeCnt\)

> 바이너리 격자 분석 결과 데이터의 시계열 총 수를 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| nTimeCnt | number | 시계열 총수 (정수형) |

* Detail
  * nTimeCnt : 기본값 6, 1 이상의 정수값 필요
  * 설정 변경은 바이너리 격자 분석 데이터 요청전에 적용 필요
    
* Code
  * 
{% endtab %}
{% endtabs %}

## setHRatio\(number fRatio\)

> 3D 애니메이션 평면 객체의 수치별 표현 되는 형상의 높이 배율 조절

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| fRatio | number | 높이 배율 값 |

* Detail
  * fRatio : 3D 애니메이션 평면 객체 생성 후 적용가능, 0이상의 값으로 입력
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setTime\(number \_fTime\)

> 3D 애니메이션 평면 객체의 시계열 인덱스를 재설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_fTime | number | 시계열 인덱스 (정수형) |

* Detail
  * \_fTime : 0부터 시계열 총수-1까지의 정수 \(0-base Index\)
  * 수치변경에 따른 시계열 애니메이션이 흐르면서 변동, 0 → 6 시 1,2,3,4,5 까지 흐름 이후 6으로 도달
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## getTime\(\) → number

> 3D 애니메이션 평면 객체의 현재 진행중인 시계열 인덱스를 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * 현재 애니메이션 수행 중인 시계열 인덱스 정보 반환 (정수형)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## clearLegend\(\)

> 설정된 범례 값을 초기화

{% tabs %}
{% tab title="Information" %}

* Detail
  * 2D Raster 객체 및 3D 애니메이션 평면 객체에 적용되는 격자 색상 범례를 초기화
  
* Code
  * 
{% endtab %}
{% endtabs %}

## addLegendColor\(number nAlpha, number nRed, number nGreen, number nBlue\) → number

> 범레 리스트에 범례 색상 추가

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| nAlpha | number | 투명값 (정수형) |
| nRed | number | Red 색상값 (정수형) |
| nGreen | number | Green 색상값 (정수형) |
| nBlue | number | Blue 색상값 (정수형) |

* Detail
  * nAlpha, nRed, nGreen, nBlue : ARGB, 0~255 정수형 색상 범위
  * 범례는 격자의 최소~최대값 기준으로 각 격자 값이 범례 리스트의 총수에 비례값으로 적용
  
* Return
  * 추가된 범례 리스트의 총수 반환
  
* Code
  * 
{% endtab %}
{% endtabs %}

## set3DArrowSizeRatio\(number \_fratio\)

> 3D 화살표 객체의 화살표 크기 배율을 변경

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_fratio | number | 화살표 크기 배율 변경 |

* Detail
  * \_fratio : 0보다 큰 값으로 입력, 격자의 크기값에 대한 배율로 크기 정의
  * 3D 화살표 객체의 생성전에 미리 설정 필요
  
* Code
  * 
{% endtab %}
{% endtabs %}

## openGridDataJSON\(object \_options\) → boolean

> JSON 방식의 격자 결과 데이터 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_options | JSON | 격자 정보 설정값 |
* Detail
  * \_options : Object \- JSON 객체 블럭
    * kind : string \- 격자 데이터 그룹명
    * timeIndex : number \- 격자데이터 시게열 인덱스 번호 (정수형)
    * timeRange : number \- 격자데이터 시계열 총수 (정수형)
    * callback : function \- 격자데이터가 모두 로딩되면 발생하는 콜백 함수명
    * cols : number \- 격자의 가로 셀 총수 (정수형)
    * rows : number \- 격자의 세로 셀 총수 (정수형)
    * llcorner : Object \- 좌하단 공간 좌표 객체
      * projNum : number \- 격자 공간좌표계 코드 번호
      * pos : Array - 격자 공간 좌표 배열
        * [0] : number \- 경도
        * [1] : number \- 위도
    * size : number - 격자의 셀 크기 (단위 미터)
    * (kind가 같고 timeIndex가 다르면 같은 데이터 다른 시계열 정보로 격자 구성정보 처리를 생략한다)
    * fMin : number \- 전 셀 중 최소값
    * fMax : number \- 전 셀 중 최대값
    * data : Array[number] - 셀의 데이터 배열
	
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setLayerName\(string \_sLayerName\)

> 격자 분석 결과 데이터를 3D 지도 객체로 생성할 때 적용할 레이어 명칭

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| \_sLayerName | string | 레이어 명칭 |

* Detail
  * \_sLayerName : ""이면 유저레이어에 적용, 지정이 있으면 로컬레이어 리스트의 레이어로 생성하여 적용
  
* Code
  * 
{% endtab %}
{% endtabs %}