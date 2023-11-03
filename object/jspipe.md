---
description: 파이프 객체 생성 및 수정 기능 API.
---

# JSPipe

> Module.createPipe API 생성.

```javascript
var object = Module.createPipe("ID");
```

### create(coordinates, startColor, endColor, segment, radius, width) → boolean

> 3D 파이프 객체 생성.
>
> parameter 변수로 객체 설정.
> 
> segment 입력값&gt;3 필수 설정.
> 
> radius 입력값&gt;0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [Collection](../core/collection.md) | 파이프 경위도 좌표 목록. |
| startColor | [JSColor](../core/jscolor.md) | 시작 지점 색상. |
| endColor | [JSColor](../core/jscolor.md) | 끝 지점 색상. |
| segment | number | 단면의 다각수 (정수형). |
| radius | number | 반지름. |
| width | number | 라인 표현에서 라인 두께. |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
  
* Sample
  * function createUndergroundFacility 참조.
  * [샌드박스\_터파기 생성](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_create)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getExtent() → number

> 3D 파이프의 바운더리 박스의 장축 거리를 반환

{% tabs %}
{% tab title="Information" %}

* Return
  * 3차원(x,y,z) 바운더리 박스의 장축(최소점에서 최대점까지 벡터)의 거리 반환, 단위 미터.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getId() → string

> 오브젝트의 Key를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   유효한 문자열(string) : 오브젝트의 Key 반환 성공.
    -   빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}
{% tab title="Template" %}

```javascript
var strKey = object.getId();
```

{% endtab %}
{% endtabs %}

### getPositions() → [JSVec3Array](../core/jsvec3array.md)

> 3D 파이프의 중심선 좌표를 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * [JSVec3Array](../core/jsvec3array.md) : 관로 중심선 경위도 고도 좌표 반환 성공.
  * null : 좌표 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### getRadius() → number

> 3D 파이프의 반지름 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * 파이프 반지름(미터).
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### moveVertically(altitude) → boolean

> 3D 파이프의 높이 설정.
> 
> altitude 최소 -1000 보다 큰 값 입력(해발고도 기준).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| altitude | number | 높이 재설정 값. |
  
* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setColor(starColor, endColor) → boolean

> 3D 파이프의 시작, 끝 지점의 색상 설정

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| starColor | [JSColor](../core/jscolor.md) | 시작 지점 색상 |
| endColor | [JSColor](../core/jscolor.md) | 끝 지점 색상 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFlow(startColor, endColor, segment, interval) → boolean

> 3D 파이프의 내부 흐름 표현 형태를 설정.
> 
> segment(정수) 입력값&gt;3 필수 설정.
> 
> interval(실수) 입력값&gt;0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| startColor | [JSColor](../core/jscolor.md) | 흐름 시작 색상. |
| endColor | [JSColor](../core/jscolor.md) | 흐름 끝 색상. |
| segment | number | 흐름 구성을 위한 점의 수 (정수형). |
| interval | number | 흐름 표현 화살표의 간격. |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createUndergroundFacility 참조.
  * [샌드박스\_터파기 생성](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_create)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFlowDisplay(type) → boolean

> 3D 파이프의 내부 흐름 표현을 보기 가시화 유무 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| type | boolean | <p>true인 경우 흐름 가시화<br>false인 경우 기본 가시화.</p> |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createUndergroundFacility 참조.
  * [샌드박스\_터파기 생성](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_create)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setFlowWaitFrame(farme) → boolean

> 3D 파이프의 내부 흐름의 갱신 프레임 수 설정.
> 
> farme(정수) 구성 요소 개수&gt;0 필수 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| farme | number | 갱신할 프레임 수 (정수형). |
  
* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createUndergroundFacility 참조.
  * [샌드박스\_터파기 생성](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_create)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setSimplifyRange(range) → boolean

> 3D 파이프의 간소화 표현 거리 설정.
> 
> range 입력값&gt;0 필수 설정.
> 
> 간소화 표현 중 흐름 표현 생략.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| range | number | 간소화 표현 최소 시야거리 |

* Return
  * true : 객체 설정 성공.
  * false : 객체 설정 실패.
  
* Sample
  * function createPipe 참조.
  * [샌드박스\_파이프](http://sandbox.dtwincloud.com/code/main.do?id=object_pipe)
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

## Getter / Setter

### getDescription() → string

> 오브젝트의 설명에 대한 내용을 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   유효한 문자열(string) : 오브젝트 설명 문자열 반환 성공.
    -   빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}
{% tab title="Template" %}

```javascript
var strDesc = object.getDescription();
```

{% endtab %}
{% endtabs %}

### setDescription(desc)

> 오브젝트의 설명에 대한 설명을 저장.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| desc | string | 오브젝트 설명 문자열. |
{% endtab %}
{% tab title="Template" %}

```javascript
object.setDescription('First Object.');
```

{% endtab %}
{% endtabs %}

### getName() → string

> 오브젝트의 이름을 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    -   유효한 문자열(string) : 오브젝트의 이름 반환 성공.
    -   빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
```

{% endtab %}
{% endtabs %}

### setName(name)

> 오브젝트의 이름을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | 설정할 오브젝트 이름. |
{% endtab %}
{% tab title="Template" %}

```javascript
object.setName('MyObject');
```

{% endtab %}
{% endtabs %}

### getVisible() → number

> 오브젝트의 보기/숨김 여부를 반환.

{% tabs %}
{% tab title="Information" %}
-   Return
    - [옵션 설정 상수](../etc/type-list.md#navigation-visible-type-list) 반환
    보기 : Module.JS_VISIBLE_ON
    숨김 : Module.JS_VISIBLE_OFF
    에러 발생 : Module.JS_SELECTABLE_ERROR(오브젝트가 NULL인 경우)
{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
```

{% endtab %}
{% endtabs %}

### setVisible(visible)

> 오브젝트의 보기/숨김 여부를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| visible | number | [옵션 설정 상수](../etc/type-list.md#navigation-visible-type-list).<br>보기 : Module.JS_VISIBLE_ON</br><br>숨김 : Module.JS_VISIBLE_OFF</br> |
{% endtab %}

{% tab title="Template" %}

```javascript
object.setVisible(Module.JS_VISIBLE_ON);
```

{% endtab %}
{% endtabs %}
