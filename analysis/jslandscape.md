---
description: 지정한 관측 지점들을 순회하며 조망(경관)을 감상하는 조망 분석(둘러보기) 기능을 위한 API 입니다.
---

# JSLandScape

> Module.JSLandScape() API를 생성합니다.

```javascript
var landscape = new Module.JSLandScape();
```

## Getter / Setter

### eyePosition (property), setEyePosition(position) → [JSVector3D](../core/jsvector3d.md)

> 조망 시작 시점(카메라 위치)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                  |
| :------- | :------------------------------------ | :--------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 시점 좌표(경도, 위도, 고도). |

{% endtab %}
{% tab title="Template" %}

```javascript
landscape.eyePosition = new Module.JSVector3D(127.0, 37.5, 0.0);
```

{% endtab %}
{% endtabs %}

### viewPoints (property), setViewPoints(points) → [JSVec3Array](../core/jsvec3array.md)

> 순회할 조망 지점(경유지) 목록을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                   | Description               |
| :----- | ---------------------------------------- | ---------------------------- |
| points | [JSVec3Array](../core/jsvec3array.md)  | 조망 지점 좌표 목록.        |

{% endtab %}
{% tab title="Template" %}

```javascript
var points = new Module.JSVec3Array();
points.push(new Module.JSVector3D(127.01, 37.51, 50.0));
points.push(new Module.JSVector3D(127.02, 37.52, 60.0));
landscape.viewPoints = points;
```

{% endtab %}
{% endtabs %}

### interVal (property), setInterval(interval) → number

> 조망 지점 간 이동 간격을 설정합니다. 기본값 100.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description |
| :------- | :----- | :---------- |
| interval | number | 이동 간격(기본값 100). |

{% endtab %}
{% tab title="Template" %}

```javascript
landscape.interVal = 100;
```

{% endtab %}
{% endtabs %}

### viewSpeed (property), setViewSpeed(speed) → number

> 조망 이동 속도를 설정합니다. 기본값 100.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description |
| :---- | :----- | :---------- |
| speed | number | 이동 속도(기본값 100). |

{% endtab %}
{% tab title="Template" %}

```javascript
landscape.viewSpeed = 100;
```

{% endtab %}
{% endtabs %}

## Function

### startViewPoints() → boolean

> [eyePosition](jslandscape.md#eyeposition-property-seteyepositionposition-jsvector3d-md), [viewPoints](jslandscape.md#viewpoints-property-setviewpointspoints-jsvec3array-md)로 설정된 값을 기준으로 조망(둘러보기)을 시작합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   (실제 동작) 항상 false.
    -   (의도된 동작으로 추정) true: 조망 시작 성공. false: 조망 지점이 없거나 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
landscape.eyePosition = new Module.JSVector3D(127.0, 37.5, 0.0);

var points = new Module.JSVec3Array();
points.push(new Module.JSVector3D(127.01, 37.51, 50.0));
points.push(new Module.JSVector3D(127.02, 37.52, 60.0));
landscape.viewPoints = points;

landscape.startViewPoints();
```

{% endtab %}
{% endtabs %}

### endViewPoints() → boolean

> 진행 중인 조망(둘러보기)을 종료합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 종료 성공.
    -   false: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
landscape.endViewPoints();
```

{% endtab %}
{% endtabs %}

### setEyeToViewPoint(eye, view) → boolean

> 재생(애니메이션) 없이, 카메라를 즉시 지정한 시점과 바라보는 방향으로 이동시킵니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                                  | Description                     |
| :--- | ---------------------------------------- | -------------------------------- |
| eye  | [JSVector3D](../core/jsvector3d.md)   | 카메라 위치 좌표(경도, 위도, 고도). |
| view | [JSVector3D](../core/jsvector3d.md)   | 바라볼 대상 좌표(경도, 위도, 고도). |

-   Return
    -   true: 설정 성공.
    -   false: 월드가 초기화되지 않은 경우.
-   Note
    -   호출 시 기존 카메라 상태를 백업하며, [releaseEyeToViewPoint()](jslandscape.md#releaseeyetoviewpoint-boolean)로 복원할 수 있습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
landscape.setEyeToViewPoint(
    new Module.JSVector3D(127.0, 37.5, 50.0),
    new Module.JSVector3D(127.01, 37.51, 0.0)
);
```

{% endtab %}
{% endtabs %}

### releaseEyeToViewPoint() → boolean

> [setEyeToViewPoint()](jslandscape.md#seteyetoviewpointeye-view-boolean) 호출 이전의 카메라 상태로 복원합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 항상 true 반환.

{% endtab %}
{% tab title="Template" %}

```javascript
landscape.releaseEyeToViewPoint();
```

{% endtab %}
{% endtabs %}
