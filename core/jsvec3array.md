---
description: 3차원 좌표 배열 객체 입니다.
---

# JSVec3Array

> new Module.JSVec3Array API 생성.

```javascript
var vec_array = new Module.JSVec3Array();
```

### clear()

> 벡터 리스트를 초기화.

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
vectorList.clear();
```
{% endtab %}

### count() → number

> 배열의 데이터 수 반환.

{% tabs %}
{% tab title="Information" %}

* Return
  * number : 벡터 리스트의 벡터 개수.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
vectorList.count();
```
{% endtab %}
{% endtabs %}

### get(index) → [JSVector3D](../core/jsvector3d.md)

> 인덱스 번호에 해당하는 벡터 오브젝트를 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| index | number | 반환하는 데이터 인덱스(0부터 순서대로 정렬) |

* Return
  * 유효한 벡터 오브젝트(JSVector3D) : 해당 인덱스 벡터 반환 성공.
  * 초기화 상태의 오브젝트(JSVector3D) : 인덱스가 벡터 리스트 크기를 넘어설 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
//...
var vector = vectorList.get(2);
```
{% endtab %}
{% endtabs %}

### pop() → JSVector3D

> 벡터 리스트의 마지막 순서 벡터를 반환.
> 
> 반환 후 마지막 벡터는 벡터 리스트에서 삭제됨.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 벡터 오브젝트(JSVector3D) : 마지막 벡터 반환 성공.
  * 초기화 상태의 오브젝트(JSVector3D) : 벡터 리스트가 비어있을 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
//...
var lastVector = vectorList.pop();
```
{% endtab %}
{% endtabs %}

### push(element) → number

> 새 벡터(JSVector3D)를 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| element | [JSVector3D](../core/jsvector3d.md) | 새 3차원 벡터 객체. |

* Return
  * number : 벡터 추가 실행 후 리스트의 벡터 개수.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
var newVector = new Module.JSVector3d(100.0, 150.0, 15.0);
vectorList.push(newVector);
```
{% endtab %}
{% endtabs %}

### pushLonLatAlt(lon, lat, alt) → number

> 새 벡터를 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| lon | number | 새 벡터 경도. |
| lat | number | 새 벡터 위도. |
| alt | number | 새 벡터 고도. |
* Return
  * number : 벡터 추가 실행 후 리스트의 벡터 개수.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
vectorList.pushLonLatAlt(100.0, 120.0, 15.0);
```
{% endtab %}
{% endtabs %}

### set(index, vec)

> 인덱스에 해당하는 벡터 값을 재설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| index | number | 설정할 벡터의 인덱스. |
| vec | JSVector3D | 설정할 벡터 객체. |
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
//...
var newVector = new Module.JSVector3D(130.22, 149.3, 15.0);
vectorList.set(5, newVector);
```
{% endtab %}
{% endtabs %}

### setLonLatAlt(index, lon, lat, alt)

> 인덱스에 해당하는 벡터 값을 재설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| index | number | 설정할 벡터의 인덱스. |
| lon | number | 설정할 벡터 경도. |
| lat | number | 설정할 벡터 위도. |
| alt | number | 설정할 벡터 고도. |
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
//...
vectorList.setLonLatAlt(5, 130.22, 149.3, 15.0);
```
{% endtab %}
{% endtabs %}

### shift()

> 벡터 리스트의 첫 번째 벡터를 반환하고 두 번째 인덱스 벡터부터 순서를 한 칸 앞으로 이동.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 벡터 오브젝트(JSVector3D) : 첫 번째 벡터 반환 성공.
  * 초기화 상태의 오브젝트(JSVector3D) : 벡터 리스트가 비어있을 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec3Array();
//...
var lastVector = vectorList.shift();
```
{% endtab %}
{% endtabs %}
