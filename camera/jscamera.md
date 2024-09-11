---
description: 지도 카메라 설정을 위한 API입니다.
---

# JSCamera

> Module.getViewCamera API를 생성합니다.

```javascript
var camera = Module.getViewCamera();
```

## Properties

| Name     				| Type                                	| Description                   |
| --------------------- | ------------------------------------- | ----------------------------- |
| videoStreaming     	| boolean                              	| 비디오 스트리밍 여부.               	|
| videoFar     			| number                              	| 비디오 최대 가시거리.              	|
| videoFovX      		| number                              	| 화각 넓이.               			|
| videoFovY     		| number                              	| 화각 높이.               			|
| videoAlpha     		| number                              	| 비디오 투명값.                   	|
| videoAxisX     		| boolean                              	| 좌우 반전.                   		|
| videoAxisY    		| boolean                              	| 상하 반전.               			|
| videoZoom    			| number                             	| 비디오 배율.                   	|
| videoFarPlane    		| boolean                             	| 비디오 뒷배경 여부.                  |
| videoResolution 		| number 								| 비디오 해상도.  					|
| videoObjectMapping   	| boolean                              	| 건물 매핑 여부.                 	|
| videoIsplayer 		| boolean                            	| 비디오 재생 여부.        			|

## Function

### AltitudeDown()

> 카메라의 고도를 낮춥니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라의 고도를 높입니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라의 기울기 각도를 낮춥니다.
>
> 회전을 지원하지 않는 평면 모드에서는 작동하지 않습니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라의 기울기 각도를 높입니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라의 FOV를 줄입니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().FOVDecrease();
```

{% endtab %}
{% endtabs %}

### FOVIncrease()

> 카메라의 FOV를 높입니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().FOVIncrease();
```

{% endtab %}
{% endtabs %}

### getMapZoomLevel() -> number

> 카메라 고도에서 가시화 된 지형 정밀 레벨 정보를 반환합니다.

{% tabs %}

{% tab title="Information" %}

-   Return
    -   number: 현재 가시화 지형 레벨.

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

### look(from, to) → boolean

> 두 점을 사용하여 카메라를 이동합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                                | Description                                     |
| ---- | ----------------------------------- | ----------------------------------------------- |
| from | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 좌표 (경도, 위도, 고도).            |
| to   | [JSVector3D](../core/jsvector3d.md) | 카메라가 보고 있는 위치 좌표(경도, 위도, 고도). |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   function init 참조.
    -   [Sandbox_Circular Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_round_path)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().look(new Module.JSVector3D(129.128265, 35.171834, 500.0), new Module.JSVector3D(129.128265, 35.161834, 10.0));
```

{% endtab %}
{% endtabs %}

### MapRender()

> 3D 지도 화면을 갱신합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().MapRender();
```

{% endtab %}
{% endtabs %}

### move(position, tilt, direct, speed)

> 카메라를 지정된 위치, 기울기, 방향을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                          |
| -------- | ----------------------------------- | ------------------------------------ |
| position | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 좌표 (경도, 위도, 고도). |
| tilt     | number                              | 카메라 기울기.                       |
| direct   | number                              | 카메라 좌우 회전.                    |
| speed    | number                              | 카메라 이동 속도 (1.0 ~ 10.0).       |

-   Sample
    -   function init 참조.
    -   [Sandbox_Position Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_position)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().move(new Module.JSVector3D(129.128265, 35.171834, 500.0), 70, 0, 0);
```

{% endtab %}
{% endtabs %}

### moveDist(location, tilt, direct, dist, speed)

> 카메라를 지정된 위치, 기울기, 방향, 거리, 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                          |
| -------- | ----------------------------------- | ------------------------------------ |
| location | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 좌표 (경도, 위도, 고도). |
| tilt     | number                              | 카메라 기울기.                       |
| direct   | number                              | 카메라 좌우 회전.                    |
| dist     | number                              | (현재 미적용).                       |
| speed    | number                              | 카메라 이동속도 (기본 1).            |

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

> 카메라를 현재 위치에서 뒤로 이동합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라를 현재 위치에서 왼쪽으로 이동합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라를 지정된 위치(경도, 위도)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                           |
| --------- | ------ | ------------------------------------- |
| longitude | number | 카메라 위치 경도 좌표 (degrees 단위). |
| latitude  | number | 카메라 위치 위도 좌표 (degrees 단위). |

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

### moveLonLatAlt(x, y, z, type)

> 카메라를 지정된 위치(경도, 위도, 고도)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                           |
| ---- | ------- | ------------------------------------- |
| x    | number  | 카메라 위치 경도 좌표 (degrees 단위). |
| y    | number  | 카메라 위치 위도 좌표 (degrees 단위). |
| z    | number  | 카메라 위치 고도 좌표 (meter 단위).   |
| type | boolean | 카메라 이동 애니메이션 적용 유무.     |

-   Sample
    -   function init 참조.
    -   [Sandbox_Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

{% endtab %}
{% tab title="Template" %}

```javascript
var height = Module.getMap().getTerrHeight(126.92836647767662, 37.52439503321471);
```

{% endtab %}
{% endtabs %}

### moveLonLatAltOval(longitude, latitude, altitude, speed)

> 카메라를 지정된 위치(경도, 위도, 고도) 이동 시 확대/축소 애니메이션을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                           |
| --------- | ------ | ------------------------------------- |
| longitude | number | 카메라 위치 경도 좌표 (degrees 단위). |
| latitude  | number | 카메라 위치 위도 좌표 (degrees 단위). |
| altitude  | number | 카메라 위치 고도 좌표 (meter 단위).   |
| speed     | number | 카메라 이동속도 (기본 1).             |

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

### moveLonLatBoundarybyJson(option) → string

> 최소 좌표점, 최대 좌표점을 이용한 카메라 이동 및 완료 이벤트를 설정합니다..

{% tabs %}

{% tab title="Information" %}

| Name   | Type                                                                   | Description |
| ------ | ---------------------------------------------------------------------- | ----------- |
| option | [JSCamera.MoveBoundaryOption](jscamera.md#jscamera.moveboundaryoption) | 속성 정보.  |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   [JSCamera.MoveBoundaryOption](jscamera.md#jscamera.moveboundaryoption) 구성 태그가 누락된 경우.
-   Sample
    -   function moveTestArea 참조.
    -   [Sandbox_Camera Area Setting](https://sandbox.egiscloud.com/code/main.do?id=camera_set_viewrect)

{% endtab %}
{% tab title="Template" %}

```javascript
function complete(...args) {
    console.log(args);
}

let json = {
    boundary: {
        // Camera movement position
        min: new Module.JSVector2D(area_min_lon, area_min_lat), // Bottom left
        max: new Module.JSVector2D(area_max_lon, area_max_lat), // Top right
    },
    complete: complete, // Callback after movement completion
};
```

{% endtab %}
{% endtabs %}

### moveLonLatOval(longitude, latitude, speed)

> 카메라를 지정된 위치(경도, 위도) 이동 시 애니메이션 효과를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                           |
| --------- | ------ | ------------------------------------- |
| longitude | number | 카메라 위치 경도 좌표 (degrees 단위). |
| latitude  | number | 카메라 위치 위도 좌표 (degrees 단위). |
| speed     | number | 카메라 이동속도 (기본 1).             |

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

### moveOval(position, tilt, direct, speed)

> 카메라를 지정된 위치(경도, 위도, 고도) 이동 시 애니메이션 효과를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                          |
| -------- | ----------------------------------- | ------------------------------------ |
| position | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 좌표 (경도, 위도, 고도). |
| tilt     | number                              | 카메라 기울기.                       |
| direct   | number                              | 카메라 좌우 회전.                    |
| speed    | number                              | 카메라 이동 속도 (1.0 ~ 10.0).       |

-   Sample
    -   function initPage 참조.
    -   [Sandbox_Landscape View](https://sandbox.egiscloud.com/code/main.do?id=camera_landscape)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().moveOval(new Module.JSVector3D(129.128265, 35.171834, 500.0), 70, 0, 1);
```

{% endtab %}
{% endtabs %}

### moveOvalDist(location, tilt, Direct, speed)

> 카메라를 지정된 위치(경도, 위도, 고도)로 부터 기울기 방향을 기준으로 거리를 적용한 좌표를 설정한다.
>
> 카메라 이동시 확대/축소 애니메이션 효과 설정한다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                          |
| -------- | ----------------------------------- | ------------------------------------ |
| location | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 좌표 (경도, 위도, 고도). |
| tilt     | number                              | 카메라 기울기.                       |
| direct   | number                              | 카메라 좌우 회전.                    |
| speed    | number                              | 카메라 이동 속도 (1.0 ~ 10.0).       |

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

> 카메라를 현재 위치에서 오른쪽으로 이동합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라를 현재 위치에서 앞으로 이동합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라 자동 이동 시 일시 중지를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                                           |
| ----- | ------- | ----------------------------------------------------- |
| pause | boolean | <p>자동 이동 설정.<br>true: 멈춤.<br>false: 시작.</p> |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function pauseCameraAutoMove 참조.
    -   [Sandbox_Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().pauseAutoMove(true);
```

{% endtab %}
{% endtabs %}

### reset()

> 카메라의 속성 정보를 초기화 상태로 설정합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().reset();
```

{% endtab %}
{% endtabs %}

### rotateLeft()

> 카메라를 현재 왼쪽으로 회전합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라를 현재 오른쪽으로 회전합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 카메라 시점, 위치 간의 거리를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                     |
| ---- | ------ | ------------------------------- |
| Dist | number | 카메라 시야 거리 (meters 단위). |

{% endtab %}

{% tab title="Template" %}

```javascript
Module.getViewCamera().setDistance(500.0);
```

{% endtab %}
{% endtabs %}

### setAltitude(alt)

> 카메라 고도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                         |
| ---- | ------ | ----------------------------------- |
| alt  | number | 카메라 위치 고도 좌표 (meter 단위). |

-   Sample
    -   function setAltitude 참조.
    -   [Sandbox_Camera Setting](https://sandbox.egiscloud.com/code/main.do?id=camera_set)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().setAltitude(1000);
```

{% endtab %}
{% endtabs %}

### setAutoMovePosition(coordinates) → boolean

> 카메라의 자동 이동 좌표 목록을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                  | Description                 |
| ----------- | ------------------------------------- | --------------------------- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 자동 이동 경로의 좌표 목록. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   function setAutoMovePosition 참조.
    -   [Sandbox_Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

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

> 카메라의 자동 이동 중 카메라의 이동 간격 발생 프레임을을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                            |
| ----- | ------ | -------------------------------------- |
| speed | number | 카메라 이동 애니메이션 발생 프레임 수. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   function setAutoMovePosition 참조.
    -   [Sandbox_Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().setAutoMoveWaitFrame(3);
```

{% endtab %}
{% endtabs %}

### setAutoMoveRoundPositions(center, distance, altitude, startAngle, endAngle, type) → boolean

> 카메라의 원형 이동 경로를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type                                | Description                                                 |
| ---------- | ----------------------------------- | ----------------------------------------------------------- |
| center     | [JSVector3D](../core/jsvector3d.md) | 카메라 회전 중심 좌표(경도, 위도, 고도)                     |
| distance   | number                              | 카메라 회전 반지름 거리 (meter 단위).                       |
| altitude   | number                              | 카메라 위치 고도 좌표 (meter 단위).                         |
| startAngle | number                              | 카메라 초기 시야 방향                                       |
| endAngle   | number                              | 카메라 종료 시야 방향                                       |
| type       | boolean                             | 카메라 이동 방향 설정 (true: 반시계 방향, false: 시계 방향) |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   function setAutoMovePosition 참조.
    -   [Sandbox_Circular Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_round_path)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().setAutoMoveRoundPositions(new Module.JSVector3D(129.12732457984308, 35.171000072302796, 4.0), 400.0, 350.0, -130.0, -160.0, true);
```

{% endtab %}
{% endtabs %}

### SetCameraShakeEffect(type) → boolean

> 카메라 흔들림 효과를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description              |
| ---- | ------- | ------------------------ |
| type | boolean | 카메라 흔들링 유무 설정. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   function ShakeCamera 참조.
    -   [Sandbox_Camera Shake](https://sandbox.egiscloud.com/code/main.do?id=camera_quake)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().SetCameraShakeEffect(true);
```

{% endtab %}
{% endtabs %}

### SetCameraShakeStrength(value) → boolean

> 카메라 흔들림 강도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                   |
| ----- | ------ | ----------------------------- |
| value | number | 카메라 흔들링 강도 (1 ~ 100). |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
-   Sample
    -   function SetShakeEffectStrength 참조.
    -   [Sandbox_Camera Shake](https://sandbox.egiscloud.com/code/main.do?id=camera_quake)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().SetCameraShakeStrength(50);
```

{% endtab %}
{% endtabs %}

### setPermitUnderGround(type)

> 지하에서 카메라 이동 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                               |
| ---- | ------- | --------------------------------------------------------- |
| type | boolean | <p>지하 이동<br>true: 이동 가능.<br>false: 이동 금지.</p> |

{% endtab %}

{% tab title="Template" %}

```javascript
Module.getViewCamera().setPermitUnderGround(true);
```

{% endtab %}
{% endtabs %}

### startAutoMove() → boolean

> 카메라 자동 이동을 시작합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function startCameraAutoMove 참조.
    -   [Sandbox_Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().startAutoMove();
```

{% endtab %}
{% endtabs %}

### stopAutoMove() → boolean

> 카메라 자동 이동을 종료합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function stopCameraAutoMove 참조.
    -   [Sandbox_Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().stopAutoMove();
```

{% endtab %}
{% endtabs %}

### viewNorth()

> 카메라가 정복 방향을 바라보도록 회전 합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 화면 중심 위치를 기준으로 카메라 확대를 실행합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
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

> 화면 중심 위치를 기준으로 카메라 축소를 실행합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
API.JSCamera.ZoomOut();
```

{% endtab %}
{% endtabs %}

### getLocation() -> JSVector3D

> 카메라 위치 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   [JSVector3D](../core/jsvector3d.md): 카메라 위치 좌표 (경도, 위도, 고도)를 성공적으로 반환.
    -   null: 카메라 위치 좌표 반환에 실패.

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

### setLocation(position) → boolean

> 카메라 위치 좌표를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                          |
| -------- | ----------------------------------- | ------------------------------------ |
| position | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 좌표 (경도, 위도, 고도). |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패.
-   Sample
    -   function setMove 참조.
    -   [Sandbox_Camera Setting](https://sandbox.egiscloud.com/code/main.do?id=camera_set)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().setLocation(new Module.JSVector3D(129.128265, 35.171834, 500.0));
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getAnimationSpeed(), setAnimationSpeed(speed) -> number

> 카메라 이동 애니메이션의 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                    |
| ----- | ------ | ------------------------------ |
| speed | number | 카메라 이동 속도 (1.0 ~ 10.0). |

-   Return
    -   number: 카메라 이동 애니메이션 적용 속도.
-   Sample
    -   function setEvent 참조.
    -   [Sandbox_Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

{% endtab %}
{% tab title="Template" %}

```javascript
var speed = Module.getViewCamera().getAnimationSpeed();
Module.getViewCamera().setAnimationSpeed(5);
```

{% endtab %}
{% endtabs %}

### getDirect(), setDirect(direct) -> number

> 카메라의 현재 방향 각도를 설정 및 반환합니다.
>
> 방향각도 값의 범위는 -180도 ~ 180도 사이 입니다.
>
> -   0도: 북쪽
> -   +90도: 동쪽
> -   180도 or -180도: 남쪽
> -   -90도: 서쪽

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description       |
| ------ | ------ | ----------------- |
| direct | number | 카메라 좌우 회전. |

-   Return
    -   number: 카메라 좌우 회전값 반환 (degree 단위).
-   Sample
    -   function setDirect 참조.
    -   [Sandbox_Camera Setting](https://sandbox.egiscloud.com/code/main.do?id=camera_set)

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var direct= API.JSCamera.getDirect();
Module.getViewCamera().setDirect(0);
```

{% endtab %}
{% endtabs %}

### getFov(), setFov(fov) -> number

> 카메라의 화각 설정 및 반환 합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| fov  | [JSVector2D](../core/jsvector2d.md) | 카메라 화각. |

-   Return
    -   number: 카메라 시야 화각 반환 (degree 단위).
-   Sample
    -   function setFOV 참조.
    -   [Sandbox_Camera Setting](https://sandbox.egiscloud.com/code/main.do?id=camera_set)

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var FOV= API.JSCamera.getFOV();
Module.getViewCamera().setFov(50);
```

{% endtab %}
{% endtabs %}

### getMoveMode(), setMoveMode(type) -> boolean

> 1인칭, 3인칭 카메라 회전 모드를 설정 및 반환 합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description       |
| ---- | ------- | ----------------- |
| type | boolean | 카메라 회전 모드. |

-   Return
    -   카메라 모드 반환.
        -   true: 1인칭 시점 회전 모드.
        -   false: 3인칭 시점 회전 모드.
-   Sample
    -   function setPerson 참조.
    -   [Sandbox_Camera Setting](https://sandbox.egiscloud.com/code/main.do?id=camera_set)

{% endtab %}
{% tab title="Template" %}

```javascript
Module.getViewCamera().getMoveMode();
Module.getViewCamera().setMoveMode(true);
```

{% endtab %}
{% endtabs %}

### getLimitAltitude(), setLimitAltitude(alt) -> number

> 카메라 제한 고도값을 설정 및 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                       |
| ---- | ------ | --------------------------------- |
| alt  | number | 카메라 제한 고도값 (meters 단위). |

-   Return
    -   number: 카메라 제한 고도값 반환 (meter 단위).
-   Sample
    -   function initPage 참조.
    -   [Sandbox_Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var limitAltitude = API.JSCamera.getLimitAltitude();
Module.getViewCamera().setLimitAltitude(3000);
```

{% endtab %}
{% endtabs %}

### getLimitTilt(), setLimitTilt(tilt) -> number

> 카메라 제한 기울기 각도를 설정 및 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                            |
| ---- | ------ | -------------------------------------- |
| tilt | number | 카메라 제한 기울기 각도 (degree 단위). |

-   Return
    -   number: 카메라 제한 기울기 각도를 반환합니다 (degree 단위).
-   Sample
    -   function initPage 참조.
    -   [Sandbox_Camera Path Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path)

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var limitTilt = API.JSCamera.getLimitTilt();
Module.getViewCamera().setLimitTilt(80);
```

{% endtab %}
{% endtabs %}

### getTilt(), setTilt(tilt) -> number

> 카메라 기울기 각도를 설정 및 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description                       |
| ---- | ------ | --------------------------------- |
| tilt | number | 카메라 기울기 각도 (degree 단위). |

-   Return
    -   number: 카메라 기울기 각도를 반환합니다 (degree 단위).
-   Sample
    -   See function setTilt.
    -   [Sandbox_Camera Setting](https://sandbox.egiscloud.com/code/main.do?id=camera_set)

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSCamera : Module.getViewCamera();
};
var currentTilt = API.JSCamera.getTilt();
Module.getViewCamera().setTilt(80);
```

{% endtab %}
{% endtabs %}

### setVideoInfo(option) -> number

> 비디오 텍스쳐를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name     		| Type                              | Description               |
| :------------ | :-------------------------------- | :------------------------ |
| url      		| string                            | 미디어 URL 경로.              	|
| dronemode 	| boolean | 중심 좌표 (경도, 위도, 고도). 	| 드론 모드 설정.				|
| streaming     | boolean                           | 비디오 스트리밍 설정.             |
| objectmapping | boolean                           | 건물 매핑 설정.               	|
| alpha      	| number                           	| 비디오 투명값 설정.              |
| zoom     		| number                            | 비디오 배율 설정.               |
| fov     		| [Size2D](../etc/tag-list.md#size2d-style-type)                            | 비디오 화각 설정.               |
| xaxis			| boolean                           | 비디오 좌우 반전 설정.           	|
| yaxis    		| boolean                           | 비디오 상하 반전 설정.            |
| resolution    | number                            | 비디오 해상도 설정.              |
| farplane    	| boolean                           | 뒷배경 설정.               	|

-   Return
    -   success : 텍스쳐 생성 성공.
    -   실패 조건
        -   url tag isn't exist : url 태그가 없을 경우.
        -   streaming tag isn't exist : streaming 태그가 없을 경우.
-   Sample
    -   function createCCTV, createCCTVDrone 참조.
    -   [Sandbox_Video Texture](https://sandbox.egiscloud.com/code/main.do?id=camera_video_texture)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearVideo() -> boolean

> 비디오 텍스쳐를 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true : 초기화 성공.
    -   false : 초기화 실패.
    -   실패 조건
        -   비디오 텍스쳐가 없을 경우.
        -   비디오 데이터가 없을 경우.
        -   비디오 경로가 없을 경우.
-   Sample
    -   See function setTilt.
    -   [Sandbox_Video Texture](https://sandbox.egiscloud.com/code/main.do?id=camera_video_texture)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSCamera.MoveBoundaryOption

> Options for moving the camera based on area information.

| Name     | Type                                           | Description            |
| -------- | ---------------------------------------------- | ---------------------- |
| boundary | [Rect2D](../etc/tag-list.md#rect2d-style-type) | 카메라 이동 경계 박스. |
| complete | function                                       | 이동 완료 콜백 함수.   |
