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
| Name | Type | Description |
| ---- | ---- | ---- |
| from | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 (경도, 위도, 고도). |
| to | [JSVector3D](../core/jsvector3d.md) | 카메라가 바라보는 위치 (경도, 위도, 고도). |

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
| Name | Type | Description |
| ---- | ---- | ---- |
| position | [JSVector3D](../core/jsvector3d.md) | 카메라 경위도 좌표 위치. |
| tilt | number | 카메라 tilt. |
| direct | number | 카메라 direct. |
| speed | number | 카메라 speed. |

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

### moveLonLatBoundarybyJson(parameter) → string

> min, max boundary를 이용한 카메라 이동.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ---- | ---- |
| parameter | object | 카메라 min, max boundary. |

* Return
  * true : 설정 성공.
  * false : 설정 실패.
    * 엔진이 정상적으로 load되지 않았을 경우.
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

### moveLonLatAlt(Longitude, Latitude, Altitude, smooth)

> 카메라를 지정한 고도, 경위도 위치로 이동.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ---- | ---- |
| Longitude | number | 카메라 경도. |
| Latitude | number | 카메라 위도. |
| Altitude | number | 카메라 고도. |
| smooth | boolean | 카메라 이동 애니메이션 적용 여부. |

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
| Name | Type | Description |
| ---- | ---- | ---- |
| position | [JSVector3D](../core/jsvector3d.md) | 카메라 위치 (경도, 위도, 고도). |
| tilt | number | 카메라 tilt. |
| direct | number | 카메라 direct. |
| speed | number | 카메라 speed. |

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
| Name | Type | Description |
| ---- | ---- | ---- |
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
| Name | Type | Description |
| ---- | ---- | ---- |
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
| Name | Type | Description |
| ---- | ---- | ---- |
| tilt | number | 카메라 tilt. |

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
| Name | Type | Description |
| ---- | ---- | ---- |
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
| Name | Type | Description |
| ---- | ---- | ---- |
| alt | number | 카메라 고도. |

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
| Name | Type | Description |
| ---- | ---- | ---- |
| fov | number | 카메라 fov. |

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
| Name | Type | Description |
| ---- | ---- | ---- |
| type | boolean | 카메라 시점. |

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
| Name | Type | Description |
| ---- | ---- | ---- |
| alt | number | 제한하고자하는 고도(m 단위). |

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
| Name | Type | Description |
| ---- | ---- | ---- |
| speed | number | 카메라 이동 속도(1.0 ~ 10.0 사이 값). |

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

### setAutoMovePosition([JSVec3Array](../core/jsvec3array.md) positionList) → boolean

> 카메라 자동이동 좌표 리스트 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ---- | ---- |
| positionList | [JSVec3Array](../core/jsvec3array.md) | 자동이동 경로 좌표 리스트. |

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
| Name | Type | Description |
| ---- | ---- | ---- |
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

### setAutoMoveRoundPositions(center, distanceFromCenter, cameraAltitude, roundStartAngle, roundEndAngle, clockWise) → boolean

> 카메라 원형 경로 이동 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ---- | ---- |
| center | [JSVector3D](../core/jsvector3d.md) | 카메라가 바라보는 지점 (경도, 위도, 고도) |
| distanceFromCenter | number | 중심점과 카메라의 거리 |
| cameraAltitude | number | 카메라 고도 |
| roundStartAngle | number | 시작 방향 |
| roundEndAngle | number | 종료 방향 |
| clockWise | boolean | 방향 설정(true: 반시계방향, false: 시계방향) |

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
| Name | Type | Description |
| ---- | ---- | ---- |
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

### SetCameraShakeStrength(strength) → boolean

> 카메라 흔들림 효과 강도 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ---- | ---- |
| strength | number | 카메라 흔들림 효과 강도 (1 ~ 100) |

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

### setPermitUnderGround(permit)

> 카메라 지형 아래 이동 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| ---- | ---- | ---- |
| permit | boolean | 카메라 지형 아래 위치 허용 여부 |
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

##### JSCamera.MoveBoundaryOption

> 영역 정보를 기준으로 카메라 이동 옵션.