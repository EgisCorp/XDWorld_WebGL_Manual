---
description: 멀티 POI 생성 및 수정 기능 API.
---

# JSMultiPoint

> Module.createMultiPoint API 생성.

```javascript
var object = Module.createMultiPoint("ID");
```

### setMainPoint(id, position, icon) → boolean

> 멀티 포인트 객체 생성.
> 
> 중심 좌표로 가시화 메인 POI 생성.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| id | string | 멀티 POI 객체 명칭. |
| position | [JSVector3D](../core/jsvector3d.md) | 멀티 POI 경위도 위치. |
| icon | JSIcon | 객체의 표출 아이콘. |
  
* Return
  * true : 객체 생성 성공.
  * false : 객체 생성 실패.
  
* Sample
  * function initPage 참조.
  * [샌드박스\_멀티포인트](http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint)  
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insertSubPoint(id, icon) → boolean

> 멀티 포인트 객체 추가.
> 
> 중신 좌표를 기준으로 시계 방향 순으로 자동 배치 되는 POI 추가.
>
> 객체의 키구성은 (메인 POI 명칭)#(입력받는 id)로 구성

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| id | string | 멀티 POI 객체 명칭. |
| icon | JSIcon | 객체의 표출 아이콘. |
  
* Return
  * true : 객체 추가 성공.
  * false : 객체 추가 실패.
  
* Sample
  * function createSubPoints 참조.
  * [샌드박스\_멀티포인트](http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint)  
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setBar(color, altitude, width) → boolean

> 메인 POI 위치로 부터 지형을 연결하는 라인 생성.
> 
> altitude, width 단위는 미터.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| color | [JSColor](../core/jscolor.md) | 직선 가시화 색상 |
| altitude | number | 기둥의 시작 높이 |
| width | number | 기둥의 두께 |

* Return
  * true : 객체 추가 성공.
  * false : 객체 추가 실패.
  
* Sample
  * function createMultiPoint 참조.
  * [샌드박스\_멀티포인트](http://sandbox.dtwincloud.com/code/main.do?id=object_multipoint)  
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}