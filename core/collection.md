---
description: '다양한 형식의 배열 데이터를 정의하고 각 배열 원소를 추가, 삭제, 관리하는 API를 제공합니다.'
---

# Collection

new Module.Collection\(\) 로 생성합니다.

```text
var data_array = new Module.Collection();
```

## properties

| name | Type | Contents |
| :--- | :--- | :--- |
| count | number | 배열 원소 수 |

## new Module.Collection\(\) → [Collection](collection.md)

> 데이터 배열을 생성합니다.

{% tabs %}
{% tab title="Information" %}
* Return : 데이터 배열 객체 [Collection](collection.md)
{% endtab %}
{% endtabs %}

## add\(boolean/number/object new\_element\) → number

> 배열에 새로운 데이터를 추가합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| new\_element | boolean/number/object | 새로 추가하는 데이터 |

* Return : 새 데이터 추가 후 배열의 총 데이터 수
{% endtab %}
{% endtabs %}

## clear\(object options\)

> 배열의 모든 데이터를 삭제합니다.

## item\(number index\) → boolean/number/object

> 인덱스 번호에 해당하는 데이터를 반환합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| index | number | 반환하는 데이터 인덱스 |

* Detail
  * index : 데이터 인덱스는 입력한 순서대로 정렬되며 0부터 시작합니다.
* Return : 인덱스 번호에 해당하는 데이터
{% endtab %}
{% endtabs %}

