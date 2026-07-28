---
description: 지도 내 분석 기능 설정을 위한 API입니다.
---

# JSAnalysis

> Module.getAnalysis API를 생성합니다.

```javascript
var analysis = Module.getAnalysis();
```

## Function

### createShadow(year, month, day, hour, minute) → boolean

> 설정한 날짜, 시간을 기준으로 건물에 대한 그림자를 생성합니다.

{% tabs %}
{% tab title="Name" %}

| Name   | Type   | Description |
| :----- | :----- | :---------- |
| year   | number | 년도.       |
| month  | number | 월.         |
| day    | number | 일.         |
| hour   | number | 시간.       |
| minute | number | 분.         |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis.createShadow(2018, 5, 28, 15, 0);
```

{% endtab %}
{% endtabs %}

### createSlopePlane(angle, color) → boolean

> 시곡면 분석 삼각형 평면을 생성합니다.

{% tabs %}
{% tab title="Name" %}

| Name  | Type                          | Description    |
| :---- | :---------------------------- | :------------- |
| angle | number                        | 지형과의 각도. |
| color | [JSColor](../core/jscolor.md) | 평면 색상.     |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
-   Sample
    -   function getSlopePlane 참조.
    -   [Sandbox_Slope Analysis](https://sandbox.egiscloud.com/code/main.do?id=analysis_building_height_regulation)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### CreateInterpolationPath(option) → array

> 보간된 선을 구성하는 좌표 목록을 반환합니다.

{% tabs %}
{% tab title="Name" %}

| Name   | Type                                                                           | Description |
| :----- | :----------------------------------------------------------------------------- | :---------- |
| option | [JSAnalysis.InterpolationOption](jsanalysis.md#jsanalysis.interpolationoption) | 속성 정보.  |

-   Return
    -   array: 보간된 선 좌표 목록 반환 성공.
    -   NULL: 보간된 라인 좌표 모곩 반환 실패.
-   Sample
    -   function createInterpolatedLine 참조.
    -   [Sandbox_Line Interpolation (Curved)](https://sandbox.egiscloud.com/code/main.do?id=object_line_interpolate_curved)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getGridAnal() → [JSGridAnal](../analysis/jsgridanal.md)

> JSGridAnal 클래스를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSGridAnal](../analysis/jsgridanal.md): 반환 성공.
    -   null : 반환 실패.
-   Sample
    -   function setWindRenderMode 참조.
    -   [Sandbox_Wind Representation](https://sandbox.egiscloud.com/code/main.do?id=effect_wind)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getJomangRatio(height) → string

> 조망 차폐율을 반환합니다.
>
> 입력 변수값이 설정한 높이 이하 인 지형 고도 값을 가진 영역은 지형, 이상은 산으로 판단합니다.

{% tabs %}
{% tab title="Name" %}

| Name   | Type   | Description                      |
| :----- | :----- | :------------------------------- |
| height | number | 지형, 산 기준 높이 (meter 단위). |

-   Return

    -   다음 순서로 문자열이 구성 (건물#차폐율#산#차폐율#지형#차폐율#하늘#차폐율)

-   Sample
    -   function getJomangRatio 참조.
    -   [Sandbox_View Ratio](https://sandbox.egiscloud.com/code/main.do?id=camera_jomang_ratio)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getJudong(angle) → string

> 지동 길이를 측정하고 측정 정보를 반환합니다.
>
> 입력 변수값은 측정의 기준 퍼짐각도 입니다.

{% tabs %}
{% tab title="Name" %}

| Name  | Type   | Description |
| :---- | :----- | :---------- |
| angle | number | 퍼짐각      |

-   Return

    -   다음 순서로 문자열이 구성 (레이어명#객체키#주동길이#경도#위도)

-   Sample
    -   function getJudong 참조.
    -   [Sandbox_Main Building Length Analysis](https://sandbox.egiscloud.com/code/main.do?id=analysis_building_width)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setAllObjectRenderShadow(type)

> 가시화 된 시설물에 대한 그림자 생성 유무를 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name | Type    | Description                                                                        |
| :--- | :------ | :--------------------------------------------------------------------------------- |
| type | boolean | <p>true: 모든 시설물 그림자 객체 생성.<br>false: 선택 시설물 그림자 객체 생성.</p> |

-   Sample
    -   function initPage 참조.
    -   [Sandbox_Shadow](https://sandbox.egiscloud.com/code/main.do?id=effect_shadow_play)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShadowSimulation(type)

> 그림자 시뮬레이션 실행, 종료를 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name | Type    | Description                                                            |
| :--- | :------ | :--------------------------------------------------------------------- |
| type | boolean | <p>true: 그림자 시뮬레이션 실행.<br>false: 그림자 시뮬레이션 종료.</p> |

-   Sample
    -   function executeShadowSimulation 참조.
    -   [Sandbox_Shadow](https://sandbox.egiscloud.com/code/main.do?id=effect_shadow_play)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShadowSimulTerm(term)

> 그림자 시뮬레이션 진행 시간 간격을 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name | Type   | Description                                 |
| :--- | :----- | :------------------------------------------ |
| term | number | 그림자 시뮬레이션 진행 간격 설정 (분 단위). |

-   Sample
    -   function setShadowSimulationTimeTerm 참조.
    -   [Sandbox_Shadow](https://sandbox.egiscloud.com/code/main.do?id=effect_shadow_play)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis.setShadowSimulTerm(30);
```

{% endtab %}
{% endtabs %}

### setShadowSimulTime(year, month, day, startHour, startMin, endHour, endMin)

> 그림자 시뮬레이션에 필요한 시간 정보를 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name      | Type   | Description           |
| :-------- | :----- | :-------------------- |
| year      | number | 시뮬레이션 년도.      |
| month     | number | 시뮬레이션 월.        |
| day       | number | 시뮬레이션 일.        |
| startHour | number | 시뮬레이션 시작 시간. |
| startMin  | number | 시뮬레이션 시작 분.   |
| endHour   | number | 시뮬레이션 종료 시간. |
| endMin    | number | 시뮬레이션 종료 분.   |

-   Sample
    -   function setShadowSimulationTimeTerm 참조.
    -   [Sandbox_Shadow](https://sandbox.egiscloud.com/code/main.do?id=effect_shadow_play)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis.setShadowSimulTime(2018, 05, 28, 9, 0, 14, 30);
```

{% endtab %}
{% endtabs %}

### setViewshedMode(apply)

> 가시권 분석을 실행, 종료를 설정합니다.

{% tabs %}
{% tab title="Name" %}

| Name  | Type    | Description                                                |
| :---- | :------ | :--------------------------------------------------------- |
| apply | boolean | <p>true: 가시권 분석 실행.<br>false: 가시권 분석 종료.</p> |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShadowDrawMode(mode)

> 그림자 종류를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                                                |
| ----  | ------  | ---------------------------------------------------------- |
| mode  | number  | <p>0: 선택되지 않은 건물의 그림자영역 제외하고 가시화.<br>1: 선택된 건물의 그림자 가시화.<br>2: 그림자 가시화 중지.<br>3: 그림자를 선으로 가시화.<br>4: 그림자를 면으로 가시화.</p> 										|

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### CreateShadowOutLine(time, color) → boolean

> 그림자 종류를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    							   | Description                    |
| ----  | -----------------------------------  | ------------------------------ |
| time  | [JSDateTime](../core/jsdatetime.md)  | 그림자 생성할 시간.			    |
| color | [JSColor](../core/jscolor.md)  	   | 그림자 색상.			   			|

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   엔진 로드에 실패했을 경우.

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetRenderTerrainShadow(option)

> 지형 그림자 생성여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    	| Description                    |
| ----  | --------  | ------------------------------ |
| option | boolean  | 지형 그림자 생성 여부.		     |

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearShadow()

> 그림자를 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### checkInsideArea(array, object, type) → boolean

> 입력된 영역과 객체의 포함여부를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    								  | Description                    					 		|
| ----  | --------------------------------------  | ------------------------------------------------------- |
| array | [JSVec3Array](../core/jsvec3array.md)   | 비교할 영역 좌표 배열.		    					 		|
| object | [JSObject](../object/jsobject3d.md)  	  | 비교할 객체.		    							 		|
| type   | number  								  | <p>0: 완전 포함될 경우.<br>1: 일부라도 포함될 경우.</p>	  	|

-   Return
    -   true : 설정 성공.
    -   false : 설정 조건에 맞는 객체가 없을 경우.
		
{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### checkInsideAreas(array, parts, object, type) → array
>
> 여러개의 입력된 영역과 객체의 포함여부를 확인하고, 포함되는 영역의 인덱스 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    								  | Description                    					 		|
| ----  | --------------------------------------  | ------------------------------------------------------- |
| array | [JSVec3Array](../core/jsvec3array.md)   | 비교할 영역 좌표 배열.		    					 		|
| parts | [JSCollection](../core/collection.md)   | 비교할 영역 parts.		    							|
| object | [JSObject](../object/jsobject3d.md)  	  | 비교할 객체.		    							 		|
| type   | number  								  | <p>0: 완전 포함될 경우.<br>1: 일부라도 포함될 경우.</p>	  	|

-   Return
    -   array: 입력된 여러 영역(parts로 구분) 중 조건에 맞는 영역들의 인덱스 목록.

-   Sample
    -   function setShadowSimulationTimeTerm 참조.
    -   [Sandbox_Object Inside Area](https://sandbox.egiscloud.com/code/main.do?id=analysis_object_inside_area)

{% endtab %}

{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getSunset(year, month, day) → number

> 입력한 날짜를 기준으로 일몰 시간(시각)을 반환합니다.  

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description |
| ------ | ------ | ----------- |
| year   | number | 년도        |
| month  | number | 월 (1~12)   |
| day    | number | 일 (1~31)   |

- Return  
  - number: 일몰 시간
  - 0.0: 계산 실패 (지도 미로드 등)

{% endtab %}
{% tab title="Template" %}

```javascript
const sunsetTime = Module.getAnalysis().getSunset(2025, 4, 2);
console.log("Sunset:", sunsetTime);
```

{% endtab %}
{% endtabs %}

### getSunrise(year, month, day) → number

> 입력한 날짜를 기준으로 일출 시간(시각)을 반환합니다.  
> 반환된 값은 24시간제 기준의 실수형 시간값입니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description |
| ------ | ------ | ----------- |
| year   | number | 년도        |
| month  | number | 월 (1~12)   |
| day    | number | 일 (1~31)   |

- Return  
  - number: 일출 시간
  - 0.0: 계산 실패 (지도 미로드 등)

{% endtab %}
{% tab title="Template" %}

```javascript
const sunriseTime = Module.getAnalysis().getSunrise(2025, 4, 2);
console.log("Sunrise:", sunriseTime);
```

{% endtab %}
{% endtabs %}

### SetShadowMapSize(size)
>
> 그림자 맵 해상도를 설정합니다.  

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                      |
| ---- | ------ | -------------------------------- |
| size | number | 그림자 맵 해상도 (픽셀 단위) 입력 |

- Return  
  - 없음 (void)
 
> 너무 큰 해상도를 설정할 경우 성능 저하가 발생할 수 있습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis().SetShadowMapSize(2048);
```

{% endtab %}
{% endtabs %}

### SetLimitSunAngle(enable, angle)

> 태양 고도 각도 제한 여부와 제한 각도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                  |
| ------ | ------- | -------------------------------------------- |
| enable | boolean | <p>true: 제한 활성화<br>false: 제한 비활성화</p> |
| angle  | number  | 제한할 최소 태양 고도 각도 (degree 단위)      |

- Return  
  - 없음 (void)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis().SetLimitSunAngle(true, 5.0);
```

{% endtab %}
{% endtabs %}

### SetSunshineObject(objectNames)

> 일조량 분석 시 분석 대상 객체들을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type   | Description                                  |
| ----------- | ------ | -------------------------------------------- |
| objectNames | string | 분석 대상 객체들의 키 값 |

-   Return  
    -   없음 (void)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getAnalysis().SetSunshineObject("Building01,Building02");
```

{% endtab %}
{% endtabs %}

### CalculateSunshineJson(options) → array

> 지정된 지점들의 일조 시간을 분석하여 각 지점의 일조 시간을 분 단위로 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                      |
| ------- | ------ | ------------------------------------------------ |
| options | object | 일조 분석 옵션 객체.                             |

**options 필드 설명**:

| Field         | Type     | Required | Default         | Description                                                      |
| ------------- | -------- | -------- | --------------- | ---------------------------------------------------------------- |
| positions     | array    | ✅       |                 | 분석할 지점 목록. `[longitude, latitude, altitude]` 형식 배열. |
| timerange     | object   | ❌       | 오늘 5시~20시   | 시뮬레이션 시간 정보. year, month, day, starthour, endhour 등 포함. |
| interval      | number   | ❌       | 20              | 분석 시간 간격(단위: 분).                                       |
| analysistype  | number   | ❌       | 1               | 분석 대상 타입. `0`: 선택 객체, `1`: 가시 객체.                |
| skip          | number   | ❌       | 0               | 분석 생략할 객체 개수.                                           |

- Return:
    - array: 각 지점별 일조 시간(분) 리스트.
    - null: 분석 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
const options = {
  positions: [
    [127.0, 37.5, 20],
    [127.01, 37.51, 25]
  ],
  timerange: {
    year: 2025,
    mounth: 4,
    day: 2,
    starthour: 6,
    startminute: 0,
    startsecond: 0,
    endhour: 18,
    endminute: 0,
    endsecond: 0
  },
  interval: 10,
  analysistype: 1
};

const sunshine = Module.getAnalysis().CalculateSunshineJson(options);
console.log(sunshine); // [520, 430] 분 단위 일조량
```

{% endtab %}
{% endtabs %}



### getType() → string

> 클래스 타입 문자열("JSAnalysis")을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: "JSAnalysis".

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setGroundLandscapeViewPoint(enable, position)

> 지상 경관 분석 기준 시점(방향)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                          |
| -------- | --------------------------------------- | --------------------------------------- |
| enable   | boolean                              | true: 기준 시점 사용, false: 미사용.  |
| position | [JSVector3D](../core/jsvector3d.md)  | 기준 시점 위치 (경도, 위도, 고도).    |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearArea()

> 면적 측정 결과를 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearDist()

> 거리 측정 결과를 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addAreaObject()

> 현재 입력된 좌표 목록으로 면적 측정 객체를 추가하고, 입력 좌표를 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### addDistObject()

> 현재 입력된 좌표 목록으로 거리 측정 객체를 추가하고, 입력 좌표를 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getAreaMeasureValue() → number

> 마지막 면적 측정 값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 측정된 면적 값.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWindDistance(wind) → boolean

> 거리 측정 시 바람 방향 반영 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                     |
| ---- | ------- | --------------------------------------------------- |
| wind | boolean | <p>true: 바람 방향 반영.<br>false: 미반영.</p>    |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setViewshedParam(angle, segAngle, eyePos)

> 가시권 분석 시야각과 정밀도, 관측자 높이를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description                       |
| -------- | ------ | ------------------------------------ |
| angle    | number | 시야 각도.                          |
| segAngle | number | 세그먼트 각도(정밀도).              |
| eyePos   | number | 관측자 고도(altitude).              |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createViewshed(start, end)

> 두 지점을 기준으로 가시권 분석을 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                 | Description                    |
| ----- | --------------------------------------- | --------------------------------- |
| start | [JSVector3D](../core/jsvector3d.md)  | 관측 시작 위치 (경도, 위도, 고도). |
| end   | [JSVector3D](../core/jsvector3d.md)  | 관측 대상 위치 (경도, 위도, 고도). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setViewshedColor(rangeColor, viewColor, notViewColor) → boolean

> 가시권 분석 결과의 범위/가시/비가시 영역 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type                          | Description         |
| ------------ | ------------------------------- | --------------------- |
| rangeColor   | [JSColor](../core/jscolor.md) | 분석 범위 색상.     |
| viewColor    | [JSColor](../core/jscolor.md) | 가시 영역 색상.     |
| notViewColor | [JSColor](../core/jscolor.md) | 비가시 영역 색상.   |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getViewshedCount() → number

> 생성된 가시권 분석 결과 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 가시권 분석 결과 개수.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearViewshed()

> 가시권 분석 결과를 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getViewshedTotalArea(index) → number

> 인덱스에 해당하는 가시권 분석의 전체 면적을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| ----- | ------ | -------------------- |
| index | number | 가시권 분석 결과 인덱스. |

-   Return
    -   number: 전체 면적.
    -   0.0: 지도가 초기화되지 않았거나 index가 유효 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getViewshedVisibleArea(index) → number

> 인덱스에 해당하는 가시권 분석의 가시 영역 면적을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| ----- | ------ | -------------------- |
| index | number | 가시권 분석 결과 인덱스. |

-   Return
    -   number: 가시 영역 면적.
    -   0.0: 지도가 초기화되지 않았거나 index가 유효 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setPlaneViewshed(set) → boolean

> 가시권 분석 결과의 지형 결합 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                    |
| ---- | ------- | -------------------------------------------------- |
| set  | boolean | <p>true: 지형 결합.<br>false: 미결합.</p>       |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createViewshedEx(start, end) → boolean

> createViewshed(start, end)와 유사하나, 두 지점 간 거리가 3000m를 초과하면 생성하지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                 | Description                    |
| ----- | --------------------------------------- | --------------------------------- |
| start | [JSVector3D](../core/jsvector3d.md)  | 관측 시작 위치 (경도, 위도, 고도). |
| end   | [JSVector3D](../core/jsvector3d.md)  | 관측 대상 위치 (경도, 위도, 고도). |

-   Return
    -   true: 생성 성공.
    -   false: 지도가 초기화되지 않았거나, 두 지점 간 거리가 3000m를 초과하는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShadowColor(color)

> 그림자 외곽선 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description       |
| ----- | ------------------------------- | ------------------- |
| color | [JSColor](../core/jscolor.md) | 그림자 외곽선 색상. |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getShadowColor() → [JSColor](../core/jscolor.md)

> 설정된 그림자 색상을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSColor](../core/jscolor.md): 그림자 색상.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShadowTagetPos(position, valid)

> 일조 유효 판정 대상 위치를 추가하고 유효성을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                    |
| -------- | --------------------------------------- | --------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)  | 대상 위치 (경도, 위도, 고도).    |
| valid    | boolean                              | 유효 여부.                       |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ClearSunshinePosition()

> 등록된 일조 유효 판정 위치 목록을 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### AddSunshinePosition(position)

> 일조 유효 판정 위치를 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                    |
| -------- | --------------------------------------- | --------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)  | 추가할 위치 (경도, 위도, 고도).  |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### CalculateSunshineEX(start, end, interval, type) → string

> 지정 기간동안의 일조 시간을 분석하여 결과를 문자열로 반환합니다 (다수 지점 분석).

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                                        |
| -------- | --------------------------------------- | ----------------------------------------------------- |
| start    | [JSDateTime](../core/jsdatetime.md)  | 분석 시작 일시.                                     |
| end      | [JSDateTime](../core/jsdatetime.md)  | 분석 종료 일시.                                     |
| interval | number                                | 분석 시간 간격 (분 단위).                           |
| type     | number                                | 분석 대상 (0: 선택된 오브젝트, 1: 렌더링된 오브젝트). |

-   Return
    -   string: 분석 결과 문자열.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### CalculateSunshine(position, start, end, interval, type) → number

> 지정한 한 지점에 대해 지정 기간동안의 일조 시간(분)을 계산하여 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                                        |
| -------- | --------------------------------------- | ----------------------------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)  | 분석 대상 위치 (경도, 위도, 고도).                  |
| start    | [JSDateTime](../core/jsdatetime.md)  | 분석 시작 일시.                                     |
| end      | [JSDateTime](../core/jsdatetime.md)  | 분석 종료 일시.                                     |
| interval | number                                | 분석 시간 간격 (분 단위).                           |
| type     | number                                | 분석 대상 (0: 선택된 오브젝트, 1: 렌더링된 오브젝트). |

-   Return
    -   number: 일조 시간 (분 단위).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### GetSunshineObject() → string

> SetSunshineObject()로 설정된 분석 대상 객체 키 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 설정된 객체 키 목록 문자열.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ClearSunshineObject()

> SetSunshineObject()로 설정된 분석 대상 객체 목록을 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### ShadowMultiSimulation(start, tmStart, tmEnd, interval)

> 다중 그림자 시뮬레이션을 실행/종료합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                              |
| -------- | --------------------------------------- | ------------------------------------------- |
| start    | boolean                              | <p>true: 실행.<br>false: 종료.</p>       |
| tmStart  | [JSDateTime](../core/jsdatetime.md)  | 시뮬레이션 시작 일시.                    |
| tmEnd    | [JSDateTime](../core/jsdatetime.md)  | 시뮬레이션 종료 일시.                    |
| interval | number                                | 진행 시간 간격 (분 단위).                |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getShadowObjCnt() → number

> 현재 선택된 그림자 분석 대상 오브젝트 수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number: 선택된 오브젝트 수.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetBrightness(brightness)

> 그림자 생성 시 밝기 정도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                        |
| ---------- | ------ | ------------------------------------- |
| brightness | number | 밝기 값 (0.0 ~ 3.0 사이로 보정됨). |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getSunPosition(year, month, day, hour, minute, second) → [JSVector2D](../core/jsvector2d.md)

> 지정한 일시 기준 태양의 위치(방위각, 고도각)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description   |
| ------ | ------ | -------------- |
| year   | number | 년도.          |
| month  | number | 월.            |
| day    | number | 일.            |
| hour   | number | 시.            |
| minute | number | 분.            |
| second | number | 초.            |

-   Return
    -   [JSVector2D](../core/jsvector2d.md): 태양 위치 (x: 방위각, y: 고도각).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getCrossSection(start, end, interval) → [Collection](../core/collection.md)

> 두 지점 사이의 지형 단면 좌표 목록(경도, 위도, 고도)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                     |
| -------- | --------------------------------------- | ----------------------------------- |
| start    | [JSVector2D](../core/jsvector2d.md)  | 시작 좌표 (경도, 위도).           |
| end      | [JSVector2D](../core/jsvector2d.md)  | 종료 좌표 (경도, 위도).           |
| interval | number                                | 단면 추출 간격 (meter 단위).      |

-   Return
    -   [Collection](../core/collection.md): 지형 단면 좌표 목록 ([JSVector3D](../core/jsvector3d.md) 요소).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetAnalysisTerrain(state)

> 지형 분석 표현 상태를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                              |
| ----- | ------ | ------------------------------------------------------------ |
| state | number | <p>0: 분석 종료.<br>1: 경사도 표현.<br>2: 경사향 표현.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### CheckNeighborPolygon(list1, list2, distance) → boolean

> 두 폴리곤(경계선) 목록이 서로 교차하거나, 지정한 거리 이내로 인접한지 확인합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                  | Description                    |
| -------- | -------------------------------------- | ---------------------------------- |
| list1    | [JSVec2Array](../core/jsvec2array.md) | 폴리곤 1 좌표 목록.               |
| list2    | [JSVec2Array](../core/jsvec2array.md) | 폴리곤 2 좌표 목록.               |
| distance | number                                | 인접 판정 거리.                   |

-   Return
    -   true: 교차하거나 인접한 경우.
    -   false: 교차하지 않고 인접하지도 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### UnionPolygon(list1, list2) → [JSVec2Array](../core/jsvec2array.md)

> 두 폴리곤의 합집합 좌표를 계산하여 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                  | Description        |
| ----- | -------------------------------------- | --------------------- |
| list1 | [JSVec2Array](../core/jsvec2array.md) | 폴리곤 1 좌표 목록. |
| list2 | [JSVec2Array](../core/jsvec2array.md) | 폴리곤 2 좌표 목록. |

-   Return
    -   [JSVec2Array](../core/jsvec2array.md): 합집합 결과 좌표 목록.
    -   size 0: 합집합 결과가 다중 파트(홀 등)로 구성되어 실패로 간주되는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getSliceData(from, to) → string

> 두 지점 간의 단면도 분석을 수행하고 결과를 JSON 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                                 | Description                  |
| ---- | --------------------------------------- | -------------------------------- |
| from | [JSVector3D](../core/jsvector3d.md)  | 시작 위치 (경도, 위도, 고도). |
| to   | [JSVector3D](../core/jsvector3d.md)  | 종료 위치 (경도, 위도, 고도). |

-   Return
    -   string: 단면도 분석 결과 JSON 문자열.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getPositionFromDist(distance) → [JSVector3D](../core/jsvector3d.md)

> getSliceData()로 생성된 단면도 상에서, 시작점으로부터 특정 거리에 해당하는 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description                   |
| -------- | ------ | -------------------------------- |
| distance | number | 시작점으로부터의 거리 (meter). |

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 해당 거리의 좌표 (경도, 위도, 고도).
    -   (0, 0, 0): 단면도 데이터가 없거나 조회 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getJSONRasterLegend(json) → number

> 레스터 분석 범례 정보를 JSON 문자열로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                                            |
| ---- | ------ | --------------------------------------------------------- |
| json | string | 범례 정보 JSON 문자열 (`RLegend` 배열 형식, 10자 이상). |

-   Return
    -   number: 등록된 범례 개수.
    -   0: 문자열 길이가 10 미만이거나, JSON 파싱에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getRoadAnalysis() → [JSRoadAnalysis](jsroadanalysis.md)

> 도로 분석 객체를 반환합니다 (최초 호출 시 생성).

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSRoadAnalysis](jsroadanalysis.md): 도로 분석 객체.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getCPCollection() → [JSCPCollection](jscpcollection.md)

> Cell Plan(전원주택단지 등 필지 분석) 컬렉션 객체를 반환합니다 (최초 호출 시 생성).

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSCPCollection](jscpcollection.md): CellPlan 컬렉션 객체.
    -   null: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getTotalSlice(layerName, from, to, angle, gap) → boolean

> 지정한 레이어에 대해 광역 단면(와이드 슬라이스) 분석을 수행합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                 | Description                  |
| --------- | --------------------------------------- | -------------------------------- |
| layerName | string                                | 대상 레이어 명칭.              |
| from      | [JSVector3D](../core/jsvector3d.md)  | 시작 위치 (경도, 위도, 고도). |
| to        | [JSVector3D](../core/jsvector3d.md)  | 종료 위치 (경도, 위도, 고도). |
| angle     | number                                | 단면 폭 각도.                 |
| gap       | number                                | 단면 간격.                    |

-   Return
    -   true: 분석 성공.
    -   false: 분석 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getGridAnalysis() → [JSGridAnal](jsgridanal.md)

> getGridAnal()과 동일한 기능입니다 (cpp에서 같은 구현부에 바인딩된 별칭).

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSGridAnal](jsgridanal.md): 반환 성공.
    -   null: 반환 실패.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getApplySlope(floor, mode)

> 사선 제한 분석을 적용합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                                                         |
| ----- | ------ | ------------------------------------------------------------------------ |
| floor | number | 기준 층수.                                                              |
| mode  | number | <p>1: 건물 기준 분석.<br>2: 입력한 두 지점(토지) 기준 분석.</p>       |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setShadowCadastralRenderMode(set)

> 쉐이더 그림자 방식으로 지적도(경계선)를 렌더링할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                   |
| ---- | ------- | -------------------------------------------------- |
| set  | boolean | <p>true: 지적도 렌더링 적용.<br>false: 해제.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### createInterpolationPathUsingIDW(rectMin, rectMax, positions, directions, strengths, altitudeGap, lineScale) → [JSVec3Array](../core/jsvec3array.md)

> IDW(역거리 가중치) 알고리즘을 이용해, 지정한 영역 안에서 임의 위치를 시작점으로 하는 보간 경로 좌표 목록을 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                                    |
| ----------- | -------------------------------------- | -------------------------------------------------- |
| rectMin     | [JSVector2D](../core/jsvector2d.md)   | 대상 영역 최소 좌표 (경도, 위도).                 |
| rectMax     | [JSVector2D](../core/jsvector2d.md)   | 대상 영역 최대 좌표 (경도, 위도).                 |
| positions   | [JSVec2Array](../core/jsvec2array.md) | 입력 기준점 좌표 목록.                            |
| directions  | array                                  | 각 기준점의 방향 각도 목록 (positions와 개수 동일). |
| strengths   | array                                  | 각 기준점의 세기 목록 (positions와 개수 동일).     |
| altitudeGap | number                                 | 생성 좌표에 추가할 고도 오프셋.                    |
| lineScale   | number                                 | 경로 생성 간격 스케일.                             |

-   Return
    -   [JSVec3Array](../core/jsvec3array.md): 생성된 보간 경로 좌표 목록.
    -   size 0: positions, directions, strengths의 개수가 서로 일치하지 않는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getFlowJson(options) → boolean

> 바람장(Flow) 데이터를 JSON 형태로 변환하여 가시화합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                                            |
| ------- | ------ | ----------------------------------------------------------------------------------------------------------- |
| options | object | `layername`(레이어 명칭, 기본값 "flow"), `velocity`, `height`, `particleNum`, `callback`, `data`(필수, `{longitude,latitude,u,v}` 목록), `minRange`, `maxRange`, `rasterLayer` 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 처리 성공.
    -   false: options가 없거나, `data`가 없거나 비어 있는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setWaterDepth(options) → boolean

> 해수면 심도 표현 데이터를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type   | Description                                                                       |
| ------- | ------ | -------------------------------------------------------------------------------------- |
| options | object | `drawType`(표현 타입, 기본값 30), `callback`, `data`(필수, `[x,y,z]` 좌표 목록) 속성을 포함하는 옵션 객체. |

-   Return
    -   true: 설정 성공.
    -   false: 지도가 초기화되지 않았거나 `data`가 없거나 비어 있는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearWaterDepth()

> 해수면 심도 표현 데이터를 초기화합니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getRCCollection() → [JSRCCollection](jsrccollection.md)

> 레이더 커버 컬렉션 객체를 반환합니다 (최초 호출 시 생성).

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSRCCollection](jsrccollection.md): 레이더 커버 컬렉션 객체.
    -   null: 지도가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### exportDistanceGeoJSON()

> 등록된 거리 측정 결과를 GeoJSON 형식으로 내보냅니다.

{% tabs %}
{% tab title="Information" %}
{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter (3D 가시권 - 실시간 쉐이더 방식)

### setVFMode(render)

> 실시간(쉐이더 방식) 3D 가시권 분석 실행 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                                    |
| ------ | ------- | -------------------------------------------------- |
| render | boolean | <p>true: 분석 실행.<br>false: 분석 종료.</p>    |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setVFCreateClickMode(mode)

> 3D 가시권 분석 지점을 마우스 클릭으로 생성할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                        |
| ---- | ------- | ------------------------------------------------------ |
| mode | boolean | <p>true: 클릭으로 생성.<br>false: 클릭으로 생성 안 함.</p> |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVFPosition(), setVFPosition(position) → [JSVector3D](../core/jsvector3d.md)

> 3D 가시권 분석 관측자(eye) 위치를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                 | Description                    |
| -------- | --------------------------------------- | --------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md)  | 관측자 위치 (경도, 위도, 고도). |

-   Return (get)
    -   [JSVector3D](../core/jsvector3d.md): 현재 관측자 위치.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVFLootAt() → [JSVector3D](../core/jsvector3d.md)

> 3D 가시권 분석의 현재 주시점(Look At) 위치를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 주시점 위치 (경도, 위도, 고도).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVFPan(), setVFPan(pan) → number

> 3D 가시권 분석 카메라의 pan(수평 회전) 값을 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description   |
| ---- | ------ | -------------- |
| pan  | number | pan 각도 값. |

-   Return (get)
    -   number: 현재 pan 값.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVFTilt(), setVFTilt(tilt) → number

> 3D 가시권 분석 카메라의 기울기(tilt) 값을 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| tilt | number | 기울기 값.     |

-   Return (get)
    -   number: 현재 기울기 값.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVFFov(), setVFFov(angle) → [JSVector2D](../core/jsvector2d.md)

> 3D 가시권 분석 카메라의 시야각(x, y)을 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                | Description                    |
| ----- | -------------------------------------- | --------------------------------- |
| angle | [JSVector2D](../core/jsvector2d.md) | 시야각 (x: 수평, y: 수직).       |

-   Return (get)
    -   [JSVector2D](../core/jsvector2d.md): 현재 시야각.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### getVFDistance(), setVFDistance(distance) → number

> 3D 가시권 분석 카메라의 관측 거리를 설정하거나 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description   |
| -------- | ------ | -------------- |
| distance | number | 관측 거리 값. |

-   Return (get)
    -   number: 현재 관측 거리 값.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSAnalysis.InterpolationOption

> Interpolation line coordinate creation options.

| Name        | Type                                                          | Description            |
| ----------- | ------------------------------------------------------------- | ---------------------- |
| positions   | array([JSVector2D](../core/jsvector2d.md))                    | 보간 선 시작점 목록.   |
| input       | array([Interpolation](../etc/tag-list.md#interpolation-type)) | 보간 계산 입력점 목록. |
| rect        | [Rect2D](../etc/tag-list.md#rect2d-style-type)                | 선 생성 영역.          |
| vertexcount | number                                                        | 선 형상 정점 수.       |
| scale       | number                                                        | 선 생성 간격.          |
