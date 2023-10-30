---
description: 지도 내 카메라 설정 API.
---

# JSCamera

> Module.getViewCamera API 생성.

```javascript
var camera = Module.getViewCamera();
```

### look(from, to) → boolean

> from, to 두 점을 이용한 카메라 이동.

{% tabs %}
{% tab title="Information" %}
| Name | Type                                | Description                |
| ---- | ----------------------------------- | -------------------------- |
| from | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 (경도, 위도, 고도).       |
| to   | [JSVector3D](../core/jsvector3d.md) | 카메라가 바라보는 위치 (경도, 위도, 고도). |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
* Sample
  * function init 참조.
  * [샌드박스\_원형 경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_round\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().look(new Module.JSVector3D(129.128265, 35.171834, 500.0), new Module.JSVector3D(129.128265, 35.161834, 10.0));
```
{% endtab %}
{% endtabs %}

### move(position, tilt, direct, speed)

> 카메라를 원하는 위치로 이동 후 Tilt, direct 설정.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description    |
| -------- | ----------------------------------- | -------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 카메라 경위도 좌표 위치. |
| tilt     | number                              | 카메라 tilt.      |
| direct   | number                              | 카메라 direct.    |
| speed    | number                              | 카메라 speed.     |

* Sample
  * function init 참조.
  * [샌드박스\_위치이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_position)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().move(new Module.JSVector3D(129.128265, 35.171834, 500.0), 70, 0, 0);
```
{% endtab %}
{% endtabs %}

### moveLonLatBoundarybyJson(option) → string

> min, max boundary를 이용한 카메라 이동.

{% tabs %}
{% tab title="Information" %}
| Name   | Type                                                                   | Description            |
| ------ | ---------------------------------------------------------------------- | ---------------------- |
| option | [JSCamera.MoveBoundaryOption](jscamera.md#jscamera.moveboundaryoption) | 카메라 min, max boundary. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
    * complete 태그가 없을 경우.
* Sample
  * function moveTestArea 참조.
  * [샌드박스\_카메라영역설정](http://sandbox.dtwincloud.com/code/main.do?id=camera\_set\_viewrect)
{% endtab %}

{% tab title="Template" %}
```javascript
function complete(...args) {
	console.log(args);
}

let json = {
	boundary: {														// 카메라 이동 위치
		min: new Module.JSVector2D(area_min_lon, area_min_lat),		// 좌하단
		max: new Module.JSVector2D(area_max_lon, area_max_lat)		// 우상단
	},																
	complete: complete,												// 이동완료 후 발생하는 CallBack
};
```
{% endtab %}
{% endtabs %}

### moveLonLatAlt(x, y, z, type)

> 카메라를 지정한 고도, 경위도 위치로 이동.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description         |
| ---- | ------- | ------------------- |
| x    | number  | 카메라 경도.             |
| y    | number  | 카메라 위도.             |
| z    | number  | 카메라 고도.             |
| type | boolean | 카메라 이동 애니메이션 적용 여부. |

* Sample
  * function init 참조.
  * [샌드박스\_경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
var height = Module.getMap().getTerrHeight(126.92836647767662, 37.52439503321471);
```
{% endtab %}
{% endtabs %}

### moveOval(position, tilt, direct, speed)

> 카메라를 지정한 고도, 경위도 위치로 이동 및 애니메이션 효과.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description          |
| -------- | ----------------------------------- | -------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 (경도, 위도, 고도). |
| tilt     | number                              | 카메라 tilt.            |
| direct   | number                              | 카메라 direct.          |
| speed    | number                              | 카메라 speed.           |

* Sample
  * function initPage 참조.
  * [샌드박스\_경관보기](http://sandbox.dtwincloud.com/code/main.do?id=camera\_landscape)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().moveOval(new Module.JSVector3D(129.128265, 35.171834, 500.0), 70, 0, 1);
```
{% endtab %}
{% endtabs %}

### setLocation(position) → boolean

> 카메라 위치 설정.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description          |
| -------- | ----------------------------------- | -------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 (경도, 위도, 고도). |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
* Sample
  * function setMove 참조.
  * [샌드박스\_카메라 설정](http://sandbox.dtwincloud.com/code/main.do?id=camera\_set)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setLocation(new Module.JSVector3D(129.128265, 35.171834, 500.0));
```
{% endtab %}
{% endtabs %}

### setLimitTilt(tilt)

> 카메라의 제한 tilt 각도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description      |
| ---- | ------ | ---------------- |
| tilt | number | 제한하고자하는 tilt 각도. |

* Sample
  * function initPage 참조.
  * [샌드박스\_카메라 경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setLimitTilt(80);
```
{% endtab %}
{% endtabs %}

### setTilt(tilt)

> 카메라의 tilt 각도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| ---- | ------ | ----------- |
| tilt | number | 카메라 tilt.   |

* Sample
  * function setTilt 참조.
  * [샌드박스\_카메라 설정](http://sandbox.dtwincloud.com/code/main.do?id=camera\_set)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setTilt(80);
```
{% endtab %}
{% endtabs %}

### setDirect(direct)

> 카메라 방향 설정.
>
> direct 입력 값에 따른 회전 정보 0, 360(북쪽), 90(동쪽), 180(남쪽), 270(서쪽).

{% tabs %}
{% tab title="Information" %}
| Name   | Type   | Description |
| ------ | ------ | ----------- |
| direct | number | 카메라 direct. |

* Sample
  * function setDirect 참조.
  * [샌드박스\_카메라 설정](http://sandbox.dtwincloud.com/code/main.do?id=camera\_set)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setDirect(0);
```
{% endtab %}
{% endtabs %}

### setAltitude(alt)

> 카메라 고도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| ---- | ------ | ----------- |
| alt  | number | 카메라 고도.     |

* Sample
  * function setAltitude 참조.
  * [샌드박스\_카메라 설정](http://sandbox.dtwincloud.com/code/main.do?id=camera\_set)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setAltitude(1000);
```
{% endtab %}
{% endtabs %}

### setFov(fov)

> 카메라 FOV 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description |
| ---- | ------ | ----------- |
| fov  | number | 카메라 fov.    |

* Sample
  * function setFOV 참조.
  * [샌드박스\_카메라 설정](http://sandbox.dtwincloud.com/code/main.do?id=camera\_set)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setFov(50);
```
{% endtab %}
{% endtabs %}

### setMoveMode(type)

> 카메라 회전 모드 설정.
>
> type 입력 값에 따른 정보 true(1인칭 시점 회전모드), false(3인칭 시점 회전모드).

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description |
| ---- | ------- | ----------- |
| type | boolean | 카메라 시점.     |

* Sample
  * function setPerson 참조.
  * [샌드박스\_카메라 설정](http://sandbox.dtwincloud.com/code/main.do?id=camera\_set)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setMoveMode(true);
```
{% endtab %}
{% endtabs %}

### setLimitAltitude(alt)

> 카메라 제한 고도 값을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description       |
| ---- | ------ | ----------------- |
| alt  | number | 제한하고자하는 고도(m 단위). |

* Sample
  * function initPage 참조
  * [샌드박스\_경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setLimitAltitude(3000);
```
{% endtab %}
{% endtabs %}

### setAnimationSpeed(speed)

> 마우스 카메라 이동 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description                  |
| ----- | ------ | ---------------------------- |
| speed | number | 카메라 이동 속도(1.0 \~ 10.0 사이 값). |

* Sample
  * function setEvent 참조.
  * [샌드박스\_경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setAnimationSpeed(5);
```
{% endtab %}
{% endtabs %}

### setAutoMovePosition(coordinates) → boolean

> 카메라 자동이동 좌표 리스트 설정.

{% tabs %}
{% tab title="Information" %}
| Name        | Type                                  | Description     |
| ----------- | ------------------------------------- | --------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 자동이동 경로 좌표 리스트. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
    * 엔진이 정상적으로 load되지 않았을 경우.
* Sample
  * function setAutoMovePosition 참조.
  * [샌드박스\_경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
var vMovePositionList = new Module.JSVec3Array();
vMovePositionList.push(new Module.JSVector3D(129.12695440075726, 35.16601614946393, 50.0));
vMovePositionList.push(new Module.JSVector3D(129.12188858001704, 35.173578909363805, 50.0));
vMovePositionList.push(new Module.JSVector3D(129.12027302076595, 35.17489727168604, 50.0));
vMovePositionList.push(new Module.JSVector3D(129.1193336034672, 35.176296224587475, 50.0));
Module.getViewCamera().setAutoMovePosition(vMovePositionList);
```
{% endtab %}
{% endtabs %}

### setAutoMoveWaitFrame(speed) → boolean

> 카메라 자동이동 위치 갱신 프레임 수 설정.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description      |
| ----- | ------ | ---------------- |
| speed | number | 카메라 위치 갱신 프레임 수. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
    * 엔진이 정상적으로 load되지 않았을 경우.
* Sample
  * function setAutoMovePosition 참조.
  * [샌드박스\_경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setAutoMoveWaitFrame(3);
```
{% endtab %}
{% endtabs %}

### setAutoMoveRoundPositions(center, distance, altitude, startAngle, endAngle, type) → boolean

> 카메라 원형 경로 이동 설정.

{% tabs %}
{% tab title="Information" %}
| Name       | Type                                | Description                     |
| ---------- | ----------------------------------- | ------------------------------- |
| center     | [JSVector3D](../core/jsvector3d.md) | 카메라가 바라보는 지점 (경도, 위도, 고도)       |
| distance   | number                              | 중심점과 카메라의 거리                    |
| altitude   | number                              | 카메라 고도                          |
| startAngle | number                              | 시작 방향                           |
| endAngle   | number                              | 종료 방향                           |
| type       | boolean                             | 방향 설정(true: 반시계방향, false: 시계방향) |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
* Sample
  * function setAutoMovePosition 참조
  * [샌드박스\_원형 경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_round\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setAutoMoveRoundPositions(new Module.JSVector3D(129.12732457984308, 35.171000072302796, 4.0), 400.0, 350.0, -130.0, -160.0, true);
```
{% endtab %}
{% endtabs %}

### SetCameraShakeEffect(type) → boolean

> 카메라 흔들림 효과 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description    |
| ---- | ------- | -------------- |
| type | boolean | 카메라 흔들림 효과 설정. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
    * 엔진이 정상적으로 load되지 않았을 경우.
* Sample
  * function ShakeCamera 참조.
  * [샌드박스\_카메라흔들림](http://sandbox.dtwincloud.com/code/main.do?id=camera\_quake)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().SetCameraShakeEffect(true);
```
{% endtab %}
{% endtabs %}

### SetCameraShakeStrength(value) → boolean

> 카메라 흔들림 효과 강도 설정.

{% tabs %}
{% tab title="Information" %}
| Name  | Type   | Description              |
| ----- | ------ | ------------------------ |
| value | number | 카메라 흔들림 효과 강도 (1 \~ 100) |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
    * 엔진이 정상적으로 load되지 않았을 경우.
* Sample
  * function SetShakeEffectStrength 참조.
  * [샌드박스\_카메라흔들림](http://sandbox.dtwincloud.com/code/main.do?id=camera\_quake)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().SetCameraShakeStrength(50);
```
{% endtab %}
{% endtabs %}

### setPermitUnderGround(type)

> 카메라 지형 아래 이동 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type    | Description        |
| ---- | ------- | ------------------ |
| type | boolean | 카메라 지형 아래 위치 허용 여부 |
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setPermitUnderGround(true);
```
{% endtab %}
{% endtabs %}

### startAutoMove() → boolean

> 카메라 자동이동 실행.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 설정 성공.
  * false : 설정 실패.
* Sample
  * function startCameraAutoMove 참조
  * [샌드박스\_경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().startAutoMove();
```
{% endtab %}
{% endtabs %}

### stopAutoMove() → boolean

> 카메라 자동이동 종료.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 설정 성공.
  * false : 설정 실패.
* Sample
  * function stopCameraAutoMove 참조
  * [샌드박스\_경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().stopAutoMove();
```
{% endtab %}
{% endtabs %}

### pauseAutoMove() → boolean

> 카메라 자동이동 일시정지.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 설정 성공.
  * false : 설정 실패.
* Sample
  * function pauseCameraAutoMove 참조.
  * [샌드박스\_경로이동](http://sandbox.dtwincloud.com/code/main.do?id=camera\_move\_path)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().pauseAutoMove();
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSCamera.MoveBoundaryOption

> 영역 정보를 기준으로 카메라 이동 옵션.

| Name     | Type                                           | Attributes | Default | Description        |
| -------- | ---------------------------------------------- | ---------- | ------- | ------------------ |
| boundary | [Rect2D](../etc/tag-list.md#rect2d-style-type) |            |         | 카메라 이동 위치.         |
| complete | function                                       |            |         | 이동 완료 후 발생 이벤트 함수. |

### AltitudeDown()

> 카메라의 고도를 낮춤.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.AltitudeDown();
```
{% endtab %}
{% endtabs %}

### AltitudeUp()

> 카메라의 고도를 높임.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.AltitudeUp();
```
{% endtab %}
{% endtabs %}

### AngleDown()

> 카메라의 각도(tilt) 낮춤.
>
> 회전을 지원하지 않는 평면 모드에서는 동작하지 않음.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.AngleDown();
```
{% endtab %}
{% endtabs %}

### AngleUp()

> 카메라의 각도(tilt) 높임.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.AngleUp();
```
{% endtab %}
{% endtabs %}

### FOVDecrease()

> 카메라의 FOV를 내림.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getViewCamera().FOVDecrease();
```
{% endtab %}
{% endtabs %}

### FOVIncrease()

> 카메라의 FOV를 올림.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getViewCamera().FOVIncrease();
```
{% endtab %}
{% endtabs %}

### getAnimationSpeed() -> number

> 카메라 이동 애니메이션 속도 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number: 이동 애니메이션 속도
{% endtab %}

{% tab title="Template" %}
```javascript
var speed = Module.getViewCamera().getAnimationSpeed();
```
{% endtab %}
{% endtabs %}

### getDirect() -> number

> 카메라의 현재 방향 각도 반환.
>
> 방향 각도 값은 -180도\~180도 사이의 값을 가진다. 각도별 카메라가 바라보는 방향은 다음과 같다.
>
> * 0도 : 북쪽
> * \+90도 : 동쪽
> * \+180도(=-180도) : 남쪽
> * \-90도 : 서쪽

{% tabs %}
{% tab title="Information" %}
* Return
  * number: 현재 카메라 각도의 방향 각도 반환 (Degree 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var direct= API.JSCamera.getDirect();
```
{% endtab %}
{% endtabs %}

### getFov() -> number

> 카메라의 FOV 각도 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number: 현재 카메라 FOV 각도 (Degree 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var FOV= API.JSCamera.getFOV();
```
{% endtab %}
{% endtabs %}

### getLimitAltitude() -> number

> 카메라에 제한된 최소 고도 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number: 현재 카메라의 최소 고도 반환(m 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var limitAltitude = API.JSCamera.getLimitAltitude();
```
{% endtab %}
{% endtabs %}

### getLimitTilt() -> number

> 카메라의 제한된 최소 tilt 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number: 현재 카메라의 제한 tilt 반환(Degree 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var limitTilt = API.JSCamera.getLimitTilt();
```
{% endtab %}
{% endtabs %}

### getLocation() -> JSVector3D

> 카메라의 위치 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * JSVector3D: 카메라 위치.
    * x : 카메라 위치의 경도 (Degree 단위).
    * y : 카메라 중심점의 위도 (Degree 단위).
    * z : 카메라 중심점의 고도 (m 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var location = API.JSCamera.getLocation();
```
{% endtab %}
{% endtabs %}

### getMapZoomLevel() -> long

> 카메라 Zoom Level 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * long: 현재 카메라의 zoom level
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var ZoomLevel= API.JSCamera.getMapZoomLevel();
```
{% endtab %}
{% endtabs %}

### getMoveMode() -> boolean

> 카메라의 회전 모드 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 현재 카메라의 회전 모드.
    * True : 1인칭 시점 회전 모드.
    * False : 3인칭 시점 회전 모드.
  * False: 엔진이 초기화되지 않아 실패한 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().getMoveMode();
```
{% endtab %}
{% endtabs %}

### getTilt() -> number

> 카메라의 현재 tilt 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number: 현재 카메라 각도의 tilt 값 반환 (Degree 단위).
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var currentTilt = API.JSCamera.getTilt();
```
{% endtab %}
{% endtabs %}

### MapRender()

> 지도 렌더링 화면 갱신.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getViewCamera().MapRender();
```
{% endtab %}
{% endtabs %}

### move(location, tilt, direct, speed)

> 카메라를 지정한 경위도 기반 위치로 이동시킨 후 카메라 각도(tilt, Direct) 및 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description                                                        |
| -------- | ----------------------------------- | ------------------------------------------------------------------ |
| location | [JSVector3D](../core/jsvector3d.md) | <p>카메라 위치 (경도, 위도, 고도).<br>경도, 위도는 Degree 단위. 고도는 m 단위.<br></p>    |
| tilt     | number                              | 이동 후 설정할 카메라 tilt.                                                 |
| direct   | number                              | 이동 후 설정할 카메라 Direct.                                               |
| speed    | long                                | <p>카메라 이동 속도.<br>속도는 정수 1 이상의 값을 가지며 단위가 커질 수록 이동 속도가 빨라짐.<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var vTargetPos = new Module.JSVector3D(longitude, latitude, altitude);
API.JSCamera.move(vTargetPos, 45.0, 90.0, 1);
```
{% endtab %}
{% endtabs %}

### moveDist(location, tilt, direct, dist, speed)

> 카메라를 지정한 경위도 기반 위치로 이동시킨 후 카메라 각도(tilt, Direct), 거리 및 속도 설정.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description                                                        |
| -------- | ----------------------------------- | ------------------------------------------------------------------ |
| location | [JSVector3D](../core/jsvector3d.md) | <p>카메라 위치 (경도, 위도, 고도).<br>경도, 위도는 Degree 단위. 고도는 m 단위.<br></p>    |
| tilt     | number                              | 이동 후 설정할 카메라 tilt.                                                 |
| direct   | number                              | 이동 후 설정할 카메라 Direct.                                               |
| dist     | number                              | 이동 후 설정할 카메라 거리(현재 미적용).                                           |
| speed    | long                                | <p>카메라 이동 속도.<br>속도는 정수 1 이상의 값을 가지며 단위가 커질 수록 이동 속도가 빨라짐.<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var vTargetPos = new Module.JSVector3D(longitude, latitude, altitude);
API.JSCamera.moveDist(vTargetPos, 45.0, 90.0, 1, 0.0);
```
{% endtab %}
{% endtabs %}

### MoveDown()

> 카메라를 후방으로 이동.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.moveDown();
```
{% endtab %}
{% endtabs %}

### MoveLeft()

> 카메라를 측면(왼쪽) 방향으로 이동.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.moveLeft();
```
{% endtab %}
{% endtabs %}

### moveLonLat(longitude, latitude)

> 지정한 경위도 기반 위치로 카메라 이동.

{% tabs %}
{% tab title="Information" %}
| Name      | Type   | Description              |
| --------- | ------ | ------------------------ |
| longitude | number | 이동하는 위치의 경도 (Degree 단위). |
| latitude  | number | 이동하는 위치의 위도 (Degree 단위). |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.moveLonLat(127.0273188, 37.4977981);
```
{% endtab %}
{% endtabs %}

### moveLonLatAlt(longitude, latitude, altitude, smooth)

> 지정한 고도, 경위도 기반 위치로 카메라 이동.

{% tabs %}
{% tab title="Information" %}
| Name      | Type    | Description                                                                        |
| --------- | ------- | ---------------------------------------------------------------------------------- |
| longitude | number  | 이동하는 위치의 경도 (Degree 단위).                                                           |
| latitude  | number  | 이동하는 위치의 위도 (Degree 단위).                                                           |
| altitude  | number  | 이동하는 위치의 고도 (m 단위).                                                                |
| smooth    | boolean | <p>카메라 이동 애니메이션 적용 여부.<br>True: 이동 애니메이션 적용.<br><br>False: 애니메이션 없이 바로 이동.<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.moveLonLatAlt(127.0273188, 37.4977981, 500.0, true);
```
{% endtab %}
{% endtabs %}

### moveLonLatAltOval(longitude, latitude, altitude, speed)

> 카메라가 지정한 고도, 경위도 기반 위치로 이동하며, 이동 시 줌 인/아웃 애니메이션 적용.

{% tabs %}
{% tab title="Information" %}
| Name      | Type   | Description                                                        |
| --------- | ------ | ------------------------------------------------------------------ |
| longitude | number | 이동하는 위치의 경도 (Degree 단위).                                           |
| latitude  | number | 이동하는 위치의 위도 (Degree 단위).                                           |
| altitude  | number | 이동하는 위치의 고도 (m 단위).                                                |
| speed     | long   | <p>카메라 이동 속도.<br>속도는 정수 1 이상의 값을 가지며 단위가 커질 수록 이동 속도가 빨라짐.<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.moveLonLatAltOval(127.0273188, 37.4977981, 500.0, 1);
```
{% endtab %}
{% endtabs %}

### moveLonLatOval(longitude, latitude, speed)

> 카메라가 지정한 고도, 경위도 기반 위치로 이동하며, 이동 시 줌 인/아웃 애니메이션 적용.

{% tabs %}
{% tab title="Information" %}
| Name      | Type   | Description                                                        |
| --------- | ------ | ------------------------------------------------------------------ |
| longitude | number | 이동하는 위치의 경도 (Degree 단위).                                           |
| latitude  | number | 이동하는 위치의 위도 (Degree 단위).                                           |
| speed     | long   | <p>카메라 이동 속도.<br>속도는 정수 1 이상의 값을 가지며 단위가 커질 수록 이동 속도가 빨라짐.<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.moveLonLatOval(127.0273188, 37.4977981, 1);
```
{% endtab %}
{% endtabs %}

### moveOval(location, tilt, Direct, speed)

> 카메라가 지정한 경위도 기반 위치로 이동한 후 카메라 틸트와 방향을 설정하며, 이동 시 줌 인/아웃 애니메이션 적용.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description                                                        |
| -------- | ----------------------------------- | ------------------------------------------------------------------ |
| location | [JSVector3D](../core/jsvector3d.md) | <p>카메라 위치 (경도, 위도, 고도).<br>경도, 위도는 Degree 단위. 고도는 m 단위.<br></p>    |
| tilt     | number                              | 이동 후 설정할 카메라 tilt.                                                 |
| Direct   | number                              | 이동 후 설정할 카메라 Direct.                                               |
| speed    | long                                | <p>카메라 이동 속도.<br>속도는 정수 1 이상의 값을 가지며 단위가 커질 수록 이동 속도가 빨라짐.<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var vTargetPos = new Module.JSVector3D(longitude, latitude, altitude);
API.JSCamera.moveOval(vTargetPos, 45.0, 90.0, 1);
```
{% endtab %}
{% endtabs %}

### moveOvalDist(location, tilt, Direct, speed)

> 카메라가 지정한 경위도 기반 위치로 이동한 후 카메라 틸트와 방향, 거리를 설정하며, 이동 시 줌 인/아웃 애니메이션 적용.

{% tabs %}
{% tab title="Information" %}
| Name     | Type                                | Description                                                        |
| -------- | ----------------------------------- | ------------------------------------------------------------------ |
| location | [JSVector3D](../core/jsvector3d.md) | <p>카메라 위치 (경도, 위도, 고도).<br>경도, 위도는 Degree 단위. 고도는 m 단위.<br></p>    |
| tilt     | number                              | 이동 후 설정할 카메라 tilt.                                                 |
| Direct   | number                              | 이동 후 설정할 카메라 Direct.                                               |
| speed    | long                                | <p>카메라 이동 속도.<br>속도는 정수 1 이상의 값을 가지며 단위가 커질 수록 이동 속도가 빨라짐.<br></p> |
{% endtab %}

{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var vTargetPos = new Module.JSVector3D(longitude, latitude, altitude);
API.JSCamera.moveOvalDist(vTargetPos, 45.0, 90.0, 0.0, 1);
```
{% endtab %}
{% endtabs %}

### MoveRight()

> 카메라를 측면(오른쪽) 방향으로 이동.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.moveRight();
```
{% endtab %}
{% endtabs %}

### MoveUp()

> 카메라를 전방으로 이동.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.moveUp();
```
{% endtab %}
{% endtabs %}

### pauseAutoMove(pause) -> boolean

> 카메라 자동이동을 잠시 멈춤.

{% tabs %}
{% tab title="Information" %}
| Name  | Type    | Description                                           |
| ----- | ------- | ----------------------------------------------------- |
| pause | boolean | <p>자동이동 설정.<br>True: 멈춤.<br><br>False: 다시 재생.<br></p> |

* Return
  * True : 설정에 성공할 경우.
  * False : 설정에 실패할 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().pauseAutoMove(true);
```
{% endtab %}
{% endtabs %}

### reset()

> 카메라의 위치, 거리 속성을초기 상태로 설정.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getViewCamera().reset();
```
{% endtab %}
{% endtabs %}

### rotateLeft()

> 카메라가 시야 왼쪽 방향으로 회전.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.rotateLeft();
```
{% endtab %}
{% endtabs %}

### rotateRight()

> 카메라가 시야 오른쪽 방향으로 회전.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.rotateRight();
```
{% endtab %}
{% endtabs %}

### setDistance(Dist)

> 카메라의 시점-위치 간 거리 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type   | Description  |
| ---- | ------ | ------------ |
| Dist | number | 설정 거리(m 단위). |
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getViewCamera().setDistance(500.0);
```
{% endtab %}
{% endtabs %}

### viewNorth()

> 카메라가 정북 방향을 바라보도록 회전.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.viewNorth();
```
{% endtab %}
{% endtabs %}

### ZoomIn()

> 화면 중심 위치를 기준으로 카메라 zoom In 실행.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.ZoomIn();
```
{% endtab %}
{% endtabs %}

### ZoomOut()

> 화면 중심 위치를 기준으로 카메라 zoom Out 실행.

{% tabs %}
{% tab title="Template" %}
```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.ZoomOut();
```
{% endtab %}
{% endtabs %}
