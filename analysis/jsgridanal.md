---
description: 
---

# JSGridAnal

Module getAnalysis().getGridAnal API로 생성할 수 있습니다.

```javascript
var object = Module.getAnalysis().getGridAnal();
```

## clear\(\) → void

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

## openGridDataURL\(string szURL, number nTime, number nStripSize, number nStriptStart, number nStripEnd, number nDataType\) → void

> 바이너리 격자 분석 결과 데이터를 URL 호출

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| szURL | string | 분석 결과 데이터의 URL |
| nTime | number | 분석 결과 데이터의 시계열 인덱스 |
| nStripSize | number | 격자 데이터 셀의 byte 크기 (정수형) |
| nStriptStart | number | 수집할 데이터 셀의 시작 오프셋 (정수형) |
| nStripEnd | number | 수집할 데이터 셀의 종료 오프셋 (정수형) |
| nDataType | number | 데이터 형식 (정수형) |

* Detail
  * szURL : http 통신을 통한 접속가능한 파일 URL
  * nTime : 0을 포함한 정수형 인덱스, 0-base 배열 번호
  * nStripSize : 0보다 큰 정수형 byte 크기
  * nStriptStart : 각셀의 시작 포인터부터 데이터를 읽기를 진행할 시작점 byte 오프셋
  * nStripEnd : 각셀의 시작 포인터부터 데이터를 읽기를 종료할 지점 byte 오프셋
  * 읽을 셀의 크기 = (nStripEnd - nStriptStart), 단위 byte
  * nDataType : 0 - 정수형 ( int : 4 byte )
  * nDataType : 1 - 실수형 ( float : 4 byte )
  * nDataType : 2 - 실수형 ( double : 8 byte )
  
* Return
  * 비동기 이벤트 - Fire_EventLoadDataFinish 통해서 모든 시계열 데이터가 모두 로드되면 발생
  * 예) Module.canvas.addEventListener("Fire_EventLoadDataFinish", OnWindDataLoad);
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=effect_wind
{% endtab %}
{% endtabs %}

## setHRange\(number fmin, number fmax\) → void

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
  * setLayerName의 레이어 명 지정이 없으면 UserLayer에 추가
  
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