---
description: '다양한 형식의 배열 데이터를 정의하고 각 배열 원소를 추가, 삭제, 관리하는 API를 제공합니다.'
---

# Collection

> new Module.Collection API 생성.

```javascript
var data_array = new Module.Collection();
```

## properties

| Name | Type | Description |
| :--- | :--- | :--- |
| count | number | 배열 원소 수 |

### add(element) → number

> 배열에 새로운 데이터 추가.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| element | object | 추가 할 데이터(0부터 순서대로 정렬). |

* Return
  * 추가 후 총 데이터 수.
{% endtab %}

{% tab title="Template" %}
```javascript
var movePosition = new Module.Collection();
movePosition.add(new Module.JSVector3D(126.77599416643791, 35.02714918251881, 34.293371013365686));
movePosition.add(new Module.JSVector3D(126.78374897355015, 35.03318059967435, 35.54886215366423));
movePosition.add(new Module.JSVector3D(126.79212321528658, 35.03203801070689, 25.686076117679477));
movePosition.add(new Module.JSVector3D(126.79408620811664, 35.019259090964134, 29.999966450035572));
```
{% endtab %}
{% endtabs %}

### clear()

> 배열의 모든 데이터를 삭제.

{% tabs %}
{% tab title="Infomation" %}

* Return
  * 추가 후 총 데이터 수.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### item(index) → object

> 인덱스 번호에 해당하는 데이터를 반환.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| index | number | 반환하는 데이터 인덱스. |

* Return
  * 인덱스 번호에 해당하는 데이터.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

