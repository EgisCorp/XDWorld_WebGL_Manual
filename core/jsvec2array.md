---
description: 2차원 좌표 배열 객체 입니다.
---

# JSVec2Array

> new Module.JSVec2Array API 생성.

```javascript
var vec_array = new Module.JSVec2Array();
```

### clear()

> 벡터 리스트를 초기화.

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec2Array();
vectorList.clear();
```
{% endtab %}

### count() → number

> 벡터 리스트의 벡터 개수를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number : 벡터 리스트의 벡터 개수.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec2Array();
vectorList.count();
```
{% endtab %}
{% endtabs %}

### get(index) → JSVector2D

> 인덱스에 해당하는 벡터 객체를 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| index | number | 반환할 벡터의 인덱스. |

* Return
  * 유효한 벡터 오브젝트(JSVector2D) : 해당 인덱스 벡터 반환 성공.
  * 초기화 상태의 오브젝트(JSVector2D) : 인덱스가 벡터 리스트 크기를 넘어설 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec2Array();
var vector = vectorList.get(2);
```
{% endtab %}
{% endtabs %}

### pop() → JSVector2D

> 벡터 리스트의 마지막 순서 벡터를 반환.
> 
> 반환 후 마지막 벡터는 벡터 리스트에서 삭제됨.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 벡터 오브젝트(JSVector2D) : 마지막 벡터 반환 성공.
  * 초기화 상태의 오브젝트(JSVector2D) : 벡터 리스트가 비어있을 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### push(element) → number

> 배열에 새로운 데이터를 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| element | [JSVector2D](../core/jsvector2d.md) | 새로 추가하는 데이터. |

* Return
  * 새 데이터 추가 후 배열의 총 데이터 수.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### pushXY(dX, dY) → number

> x, y 값을 활용하여 새 벡터 객체를 추가.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| dX | number | 새 벡터 프로퍼티 X. |
| dY | number | 새 벡터 프로퍼티 Y. |

* Return
  * 새 데이터 추가 후 배열의 총 데이터 수.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec2Array();
vectorList.pushXY(100.0, 120.0);
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
| vec | JSVector2D | 설정할 벡터 객체. |
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec2Array();
//...
var newVector = new Module.JSVector2D(130.22, 149.3);
vectorList.set(5, newVector);
```
{% endtab %}
{% endtabs %}

### setXY(index, dX, dY)

> x, y 값을 활용하여 인덱스에 해당하는 벡터 값을 재설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| index | number | 설정할 벡터의 인덱스. |
| dX | number | 설정할 벡터 값 X. |
| dY | number | 설정할 벡터 값 Y. |
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec2Array();
//...
vectorList.setXY(5, 130.22, 149.3);
```
{% endtab %}
{% endtabs %}

### shift()

> 벡터 리스트의 첫 번째 벡터를 반환하고 두 번째 인덱스 벡터부터 순서를 한 칸 앞으로 이동.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 벡터 오브젝트(JSVector2D) : 첫 번째 벡터 반환 성공.
  * 초기화 상태의 오브젝트(JSVector2D) : 벡터 리스트가 비어있을 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var vectorList = new Module.JSVec2Array();
//...
var lastVector = vectorList.shift();
```
{% endtab %}
{% endtabs %}
