---
description: 경로 설정 객체 생성 및 수정 기능 API.
---

# JSTraceTarget

> 경위도 기반으로 경로 설정.
> 
> Module.createTraceTargetAPI 생성.
>
> 샌드박스[Trace Target](https://sandbox.dtwincloud.com/code/main.do?id=camera_trace) 참고.

```javascript
let trace = Module.createTraceTarget("NEW_PATH");
```

### move(front, right, terrainUnion)

> 객체 해당 방향으로 이동.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| front | number | 전방 이동 상수. |
| right | number | 우측 이동 상수. |
| terrainUnion | boolean | 오브젝트 지형 결합 여부.<br>true인 경우 지형과 결합.</br><br>false인 경우 결합하지 않음.</br> |
{% endtab %}

{% tab title="Template" %}
```javascript
// traceTarget의 생성 및 연결 과정 생략.
traceTarget.move(1.0, 1.0, true);
```
{% endtab %}
{% endtabs %}

### moveTarget(options)

> 객체 해당 방향으로 이동.
> 
> move()와 달리, 6방향(전/후/좌/우/상/하)의 이동을 매개변수로 전달함.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| parameter | [JSTraceTarget.moveParameter](jstracetarget.md#jstracetarget.moveparameter) | 이동 정보. |

{% endtab %}

{% tab title="Template" %}
- 샌드박스[Trace Target](https://sandbox.dtwincloud.com/code/main.do?id=camera_trace)의 `renewObjectMoving()`을 변형한 코드.
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
    front : move_front,
    back : move_back,
    left : move_left,
    right : move_right,
    down : move_down,
    up : move_up
})
```
{% endtab %}
{% endtabs %}

### ReleaseObject() → boolean

> 연결되어 있는 객체 해제.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 해제에 성공한 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
// traceTarget의 생성 및 연결 과정 생략.
traceTarget.ReleaseObject();
```
{% endtab %}
{% endtabs %}

### set(options)

> 대상 객체 및 카메라 상태 재설정.
> 
> 객체 및 상태를 파라메터로 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| object | [JSGhostSymbol](jsghostsymbol.md) or [JSPoint](jspoint.md) | 대상 객체. |
| tilt      | number | tilt 상수. |
| direction | number | direction 상수. |
| distance  | number | distance 상수. |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 해제에 성공한 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
// traceTarget의 생성 및 연결 과정 생략.
traceTarget.ReleaseObject();
```
{% endtab %}
{% endtabs %}



### unionTargetToTerrain()

> 오브젝트 지형 결합.

{% tabs %}
{% tab title="Template" %}
```javascript
// traceTarget의 생성 및 연결 과정 생략.
traceTarget.unionTargetToTerrain();
```
{% endtab %}
{% endtabs %}

## Getter / Setter

### getObject → JSObject

> 현재 연결되어 있는 대상 객체 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * [JSObject](jsobject.md) : 반환에 성공한 경우.
  * null : 연결된 객체가 없는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
// traceTarget의 생성 및 연결 과정 생략.
traceTarget.getObject();
```
{% endtab %}
{% endtabs %}

### setObject(object)

> 현재 연결되어 있는 대상 객체 변경.
> 
> object가 null인 경우, 동작하지 않음.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| object | [JSObject](jsobject.md) | 대상 객체 정보. |

{% endtab %}

{% tab title="Template" %}
```javascript
// traceTarget의 생성 및 연결 과정 생략.
traceTarget.setObject(object);
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTraceTarget.moveParameter
| Name   | Type | Attributes | Default | Description |
| --- | --- | --- | --- | --- |
| front | number | optional | 0.0 | 전방 이동 상수. |
| back  | number | optional | 0.0 | 후방 이동 상수. |
| left  | number | optional | 0.0 | 좌측 이동 상수. |
| right | number | optional | 0.0 | 우측 이동 상수. |
| up    | number | optional | 0.0 | 상측 이동 상수. |
| down  | number | optional | 0.0 | 하측 이동 상수. |
