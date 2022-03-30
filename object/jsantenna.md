---
description: 전파 범위 3차원 모델 오브젝트 생성 및 설정 API.
---

# JSAntenna

Module CreateAntenna API로 생성할 수 있습니다.

```javascript
var object = Module.CreateAntenna("ID");
```

## CreateCoverageCone\([JSVector3D](JSVector3D.md) position, number effect_height, number effect_radius, number effect_angle, number effect_fov_x, number effect_segment\) → boolean

>  전파 범위 3차원 모델 오브젝트 생성.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector3D](JSVector3D.md) | 전파 시작 경위도 |
| effect_height | number | 전파 시작 경위도에서 전파 모델링 높이 설정 |
| effect_radius | number | 전파 모델링 반경 설정 |
| effect_angle | number | 전파 모델링 파형 각도 설정 |
| effect_fov_x | number | 전파 모델링 파형 화각 너비 설정 |
| effect_segment | number | 전파 모델링 정밀도 설정 |

* Detail
  * effect_radius : effect_radius&gt;0 입력 처리 가능.
  * effect_angle : effect_angle&gt;-90, effect_angle&lt;90 입력 처리 가능.
  * effect_segment : effect_radius&gt;3 입력 처리 가능.  
  
* Return
  * TRUE : 오브젝트 생성 성공
  * FALSE : 오브젝트 생성 실패
    * 오브젝트 생성 실패 조건
	  * effect_radius&lt;0 값이 설졍 된 경우
	  * effect_angle&lt;-90, effect_angle&gt;90 값이 설정된 경우
      * effect_radius&lt;3 값이 설졍 된 경우
	  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_antenna
{% endtab %}
{% endtabs %}

## SetCoverageDistance \(number effect_radius\) → boolean

> 전파 범위 모델 반경 변경.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| effect_radius | number | 전파 모델링 반경 설정 |

* Return
  * TRUE : 반경 설정 성공
  * FALSE : 반경 설정 실패
    * 오브젝트 생성 실패 조건
	  * effect_radius&lt;0 값이 설졍 된 경우

* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_antenna
{% endtab %}
{% endtabs %}
