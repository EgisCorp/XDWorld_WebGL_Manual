---
description : 3차원 좌표 배열 객체 입니다.
---

# JSVec3Array
new Module.JSVec3Array() 로 생성합니다.
```text
var vec_array = new Module.JSVec3Array();
```

## new Module.JSVec3Array\(\) → [JSVector3D](jsvector3d.md)
> 새로운 JSVector3D 배열 객체를 생성합니다.
{% tabs %}
{% tab title="Information" %}
* Return : JSVector2D 배열 객체 [JSVector3D](jsvector3d.md)
{% endtab %}
{% endtabs %}

## count\(\) → number
> 배열의 데이터 수를 반환합니다.
{% tabs %}
{% tab title="Information" %}
* Return : 배열의 데이터 수
{% endtab %}
{% endtabs %}

## get\(number index\) → [JSVector3D](jsvector3d.md)
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

## push\([JSVector3D](jsvector3d.md) new_element\) → number
> 배열에 새로운 데이터를 추가합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| new_element | [JSVector3D](jsvector3d.md) | 새로 추가하는 데이터 |
* Return : 새 데이터 추가 후 배열의 총 데이터 수
{% endtab %}
{% endtabs %}