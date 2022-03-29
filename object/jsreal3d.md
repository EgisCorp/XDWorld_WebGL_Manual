---
description: 
---

# JSReal3D

Module createReal3D API로 생성할 수 있습니다.

```javascript
var object = Module.createReal3D("ID");
```

## setFillColor\(boolean _bSimpleColorMode, [JSColor](../core/jscolor.md) _color\) → boolean

> 3D 모델에 면의 체움색을 설정한다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _bSimpleColorMode | boolean | 색상 변경 모드  |
| _color | [JSColor](../core/jscolor.md) | 체움 색상 |

* Detail
  * _bSimpleColorMode : false - 일반 면의 색상 설정
  * _bSimpleColorMode : true - 심플렌더링 모드에서 면의 색상 설정
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getFillColor\(\) → [JSColor](../core/jscolor.md)

> 3D 모델에 면의 체움색을 반환한다.

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * [JSColor](../core/jscolor.md) 면의 색상
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getPosition\(\) → [JSVector3D](../core/jsvector3d.md)

> 3D 모델의 바닥면 중심좌표를 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * [JSVector3D](../core/jsvector3d.md) 모델의 바닥면 중심 (경위도)좌표  
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getHeight\(\) → number

> 3D 모델 자체 높이 값을 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * number 3D 모델의 높이 값 (단위 미터)
  
* Code
  * 
{% endtab %}
{% endtabs %}