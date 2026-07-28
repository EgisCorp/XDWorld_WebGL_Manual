---
description: 지도 내 경로 기능을 관리하기 위한 API 입니다.
---

# JSTraceTarget

> Module.createTraceTarget() API를 생성합니다.

```javascript
let trace = Module.createTraceTarget("ID");
```

## Properties

| Name      | Type   | Description   |
| --------- | ------ | -------------- |
| direction | number | 방향값 (degrees 단위). |
| tilt      | number | 기울기 값 (카메라 최소 기울기 각도 미만으로는 설정되지 않음). |
| distance  | number | 대상과의 거리값. |

## Function

### move(front, right, up)

> 객체를 이동합니다.
>
> 입력 변수값(front, right)으로 이동합니다.
>
> 입력 변수값(up)의 타입에 따라 동작이 달라집니다: boolean이면 상하 이동 없이 지형 곡면률 적용 유무만 결정하고, number이면 해당 값만큼 상하로 이동합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type              | Description                                                                                        |
| :---- | :---------------- | :--------------------------------------------------------------------------------------------------- |
| front | number            | 전후 이동 값(in meters).                                                                            |
| right | number            | 좌우 이동 값(in meters).                                                                            |
| up    | boolean \| number | <p>boolean - true: 이동 후 지형 곡면률 적용, false: 미적용.<br>number: 상하 이동 값(in meters).</p> |

{% endtab %}

{% tab title="Template" %}

```javascript
// Omission of traceTarget creation and connection process.
traceTarget.move(1.0, 1.0, true);
// ... or ...
traceTarget.move(1.0, 1.0, 0.5); // 0.5m 상승 이동
```

{% endtab %}
{% endtabs %}

### moveTarget(options)

> 객체를 이동합니다.
>
> [move](jstracetarget.md#movefront-right-up)와 달리, 6방향(전,후,좌,우,상,하)으로 이동합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                                                        | Description |
| :-------- | :-------------------------------------------------------------------------- | :---------- |
| parameter | [JSTraceTarget.moveParameter](jstracetarget.md#jstracetarget.moveparameter) | 속성 정보.  |

{% endtab %}

{% tab title="Template" %}

```javascript
var move_front = 0.0;
var move_back = 0.0;
var move_left = 0.0;
var move_right = 0.0;
var move_up = 0.0;
var move_down = 0.0;

if (GLOBAL["KEY_PRESS_w"]) {
    move_front = 1.0;
} else if (GLOBAL["KEY_PRESS_s"]) {
    move_back = 1.0;
} else;

if (GLOBAL["KEY_PRESS_a"]) {
    move_left = 1.0;
} else if (GLOBAL["KEY_PRESS_d"]) {
    move_right = 1.0;
} else;

if (GLOBAL["KEY_PRESS_q"]) {
    move_down = 1.0;
} else if (GLOBAL["KEY_PRESS_e"]) {
    move_up = 1.0;
} else;

GLOBAL.TRACE_TARGET.moveTarget({
    front: move_front,
    back: move_back,
    left: move_left,
    right: move_right,
    down: move_down,
    up: move_up,
});
```

{% endtab %}
{% endtabs %}

### ReleaseObject() → boolean

> 연결된 객체를 해제 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true: 해제 성공.
    -   false: 해제 실패.

{% endtab %}

{% tab title="Template" %}

```javascript
// Omission of traceTarget creation and connection process.
traceTarget.ReleaseObject();
```

{% endtab %}
{% endtabs %}

### set(options)

> 대상 객체와 카메라 상태(기울기, 방향, 거리)를 한 번에 재설정합니다.
>
> options.object는 [JSGhostSymbol](jsghostsymbol.md), [JSPoint](jspoint.md), [JSPolygon](jspolygon.md)만 지원합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                                                          | Description        |
| :-------- | :------------------------------------------------------------------------------ | :------------------- |
| object    | [JSGhostSymbol](jsghostsymbol.md) \| [JSPoint](jspoint.md) \| [JSPolygon](jspolygon.md) | 대상 객체. (optional) |
| tilt      | number                                                                        | 기울기. (optional)  |
| direction | number                                                                        | 방향값. (optional)  |
| distance  | number                                                                        | 거리값. (optional)  |

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### unionTargetToTerrain()

> 객체 이동시 지형 곡면률 적용 합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
// Omission of traceTarget creation and connection process.
traceTarget.unionTargetToTerrain();
```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getObject(), setObject(object) → [JSObject](./jsobject.md)

> 연결된 객체를 입력 변수값(object) 객체로 변경합니다.
>
> setObject() 자체는 객체 타입을 제한하지 않으나(내부적으로 해당 객체의 오브젝트를 그대로 연결), 옵션 기반의 [set(options)](jstracetarget.md#setoptions)에서는 JSGhostSymbol, JSPoint, JSPolygon만 지원합니다.
>
> 입력 변수값(object) 객체가 null이면 동작하지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                      | Description |
| ------ | ------------------------- | ----------- |
| object | [JSObject](./jsobject.md) | 객체.       |

-   Return
    -   [JSObject](jsobject.md): returned successfully.
    -   null : returned failed.

{% endtab %}
{% tab title="Template" %}

```javascript
// Omission of traceTarget creation and connection process.
traceTarget.getObject();
// ... or ...
// Omission of traceTarget creation and connection process.
traceTarget.setObject(object);
```

{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTraceTarget.moveParameter

| Name  | Type   | Attributes | Default | Description              |
| ----- | ------ | ---------- | ------- | ------------------------ |
| front | number | optional   | 0.0     | 전방 이동값 (in meters). |
| back  | number | optional   | 0.0     | 후방 이동값 (in meters). |
| left  | number | optional   | 0.0     | 좌측 이동값 (in meters). |
| right | number | optional   | 0.0     | 우측 이동값 (in meters). |
| up    | number | optional   | 0.0     | 상승 이동값 (in meters). |
| down  | number | optional   | 0.0     | 하향 이동값 (in meters). |
