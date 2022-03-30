---
description: 
---

# JSPipe

Module createPipe API로 생성할 수 있습니다.

```javascript
var object = Module.createPipe("ID");
```

## create\([Collection](../core/collection.md) _vArray, [JSColor](../core/jscolor.md) _startColor, _[JSColor](../core/jscolor.md) _endColor, number _segment, number _radius, number _dSimpleLineWidth\) → boolean

> 3D 파이프 형태를 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _vArray | [Collection](../core/collection.md) | 좌표 리스트 |
| _startColor | [JSColor](../core/jscolor.md) | 시작 지점 색상 |
| _endColor | [JSColor](../core/jscolor.md) | 끝 지점 색상 |
| _segment | number | 단면의 다각수 (정수형) |
| _radius | number | 반지름 |
| _dSimpleLineWidth | number | 라인 표현에서 라인 두께 |

* Detail
  * _vArray : [JSVector3D](JSVector3D.md) 클래스 객체 컬랙션으로 좌표리스트
  * _segment : 3이상의 정수
  * _radius : 0보다 큰 수치 필수, 단위 미터
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_pipe
{% endtab %}
{% endtabs %}

## getPositions\(\) → [JSVec3Array](JSVec3Array.md)

> 3D 파이프의 중심선 좌표를 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * [JSVec3Array](JSVec3Array.md) 관로 중심선 경위도 및 고도 좌표를 반환
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getRadius\(\) → number

> 3D 파이프의 반지름 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * number : 파이프 반지름, 단위 미터
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setFlow\([JSColor](../core/jscolor.md) _startColor, [JSColor](../core/jscolor.md) _endColor, number _nColorSegment, number _dFlowInterval\) → boolean

> 3D 파이프의 내부 흐름 표현 형태를 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _startColor | [JSColor](../core/jscolor.md) | 흐름 시작 색상 |
| _endColor | [JSColor](../core/jscolor.md) | 흐름 끝 색상 |
| _nColorSegment | number | 흐름 구성을 위한 점의 수 (정수형) |
| _dFlowInterval | number | 흐름 표현 화살표의 간격 |

* Detail
  * _nColorSegment : 3이상의 정수
  * _dFlowInterval : 0보다는 큰 실수, 단위 미터
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setFlowDisplay\(boolean _bDisplay\) → boolean

> 3D 파이프의 내부 흐름 표현을 보기 / 보이지 않기 상태를 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _bDisplay | boolean | 흐름 표현 설정 |

* Detail
  * _bDisplay : true - 흐름을 화면에 표현
  * _bDisplay : false - 흐름을 화면에 표현하지 않음
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setFlowWaitFrame\(number _nFarme\) → boolean

> 3D 파이프의 내부 흐름의 갱신 프레임 수 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _nFarme | number | 갱실할 프레임 수 (정수형) |

* Detail
  * _nFarme : 0보다 큰 정수형, 수치가 클수록 애니메이션 속도가 느려진다
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## moveVertically\(number _dAltitude\) → boolean

> 3D 파이프의 높이 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _dAltitude | number | 높이 재설정 값 |

* Detail
  * _dAltitude : 최소값 -1000.0, 해발고도, 단위 미터
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setSimplifyRange\(number _fRange\) → boolean

> 3D 파이프의 간소화 표현 거리 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _fRange | number | 간소화 표현 최소 시야거리 |

* Detail
  * _fRange : 0이상의 값으로 입력, 단위는 미터 단위.
  * 간소화 표현은 3D 파이프의 물리적 형상이 아닌 먼거리에서는 두께 있는 라인으로 파이프 궤적만 표현, 간소화 표현중에는 흐름 표현도 생략
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}

## getExtent\(\) → number

> 3D 파이프의 바운더리 박스의 장축 거리를 반환

{% tabs %}
{% tab title="Information" %}

* Detail
  * 
  
* Return
  * 3차원(x,y,z) 바운더리 박스의 장축(최소점에서 최대점까지 벡터)의 거리 반환, 단위 미터
  
* Code
  * 
{% endtab %}
{% endtabs %}

## setColor\([JSColor](../core/jscolor.md) _starColor, [JSColor](../core/jscolor.md) _endColor\) → boolean

> 3D 파이프의 시작, 끝 지점의 색상 설정

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| _starColor | [JSColor](../core/jscolor.md) | 시작 지점 색상 |
| _endColor | [JSColor](../core/jscolor.md) | 끝 지점 색상 |

* Detail
  * 
  
* Return
  * 설정 성공 (true) 혹은 실패 (false)
  
* Code
  * 
{% endtab %}
{% endtabs %}