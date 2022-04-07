---
description: 전파 범위 3차원 모델 오브젝트 생성 및 설정 API.
---

# JSAntenna

> Module.CreateAntenna API 생성.

```javascript
var object = Module.CreateAntenna("ID");
```

### CreateCoverageCone(position, height, radius, angle, fov_x, segment) → boolean

>  전파 범위 3차원 모델 오브젝트 생성.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| position | [JSVector3D](JSVector3D.md) | 전파 시작 경위도 |
| height | number | 전파 시작 경위도에서 전파 모델링 높이 설정 |
| radius | number | 전파 모델링 반경 설정(radius&gt;0 입력) |
| angle | number | 전파 모델링 파형 각도 설정(angle&gt;-90, angle&lt;90 입력) |
| fov_x | number | 전파 모델링 파형 화각 너비 설정 |
| segment | number | 전파 모델링 정밀도 설정(segment&gt;3 입력) |

* Return
  * TRUE : 오브젝트 생성 성공
  * FALSE : 오브젝트 생성 실패
    * 오브젝트 생성 실패 조건
	  * effect_radius&lt;0 값이 설졍 된 경우
	  * effect_angle&lt;-90, effect_angle&gt;90 값이 설정된 경우
      * effect_radius&lt;3 값이 설졍 된 경우
	  
* Sample
  * function create 참조
  * [샌드박스\_전파 범위](http://sandbox.dtwincloud.com/code/main.do?id=object_antenna)
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### SetCoverageDistance(radius) → boolean

> 전파 범위 모델 반경 변경.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| radius | number | 전파 모델링 반경 설정(radius&gt;0 입력) |

* Return
  * TRUE : 반경 설정 성공
  * FALSE : 반경 설정 실패
    * 오브젝트 생성 실패 조건
	  * radius&lt;0 값이 설졍 된 경우

* Sample
  * function SetCoverageDistance 참조
  * [샌드박스\_전파 범위](http://sandbox.dtwincloud.com/code/main.do?id=object_antenna)
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}
