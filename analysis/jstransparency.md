---
description: 터파기 분석 기능 설정 API.
---

# JSTransparency

> Module.getTransparency API 생성.

```javascript
var transparency = Module.getTransparency();
```

## create(coordinates) → number

> 입력 좌표를 받아 터파기 객체를 생성
> 
> coordinates 입력값은 ([JSVector3D](../core/jsvector3d.md), [JSVector3D](../core/jsvector3d.md), ...) 영역 좌표 목록.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec3Array](../core/jsvec3aray.md) | 터파기 영역 좌표 리스트 |

* Return
  * 설정 성공 (좌표 리스트 크기 반환) 혹은 실패 (-1)
  
* Sample
  * function 참조.
  * [샌드박스\_터파기 생성](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_create)
{% endtab %}
{% endtabs %}

## setAutoMove(coordinates, waitframe) → boolean

> 자동으로 이동하는 원형 터파기의 이동 경로 및 속도를 설정합니다.
> 
> coordinates 입력값은 ([JSVector2D](../core/jsvector2d.md), [JSVector2D](../core/jsvector2d.md), ...) 이동경로 좌표 목록.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec2Array](../core/jsvec2aray.md) | 터파기 이동경로 좌표 리스트 |
| waitframe | number | 터파기 위치 갱신 프레임 수 |
  
* Return
  * true : 설정 성공.
  * false : 설정 실패.
  
* Sample
  * function 참조.
  * [샌드박스\_터파기 이동](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}
{% endtabs %}

## setDepth(depth)

> 터파기 깊이를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| depth | number | 지면으로부터 터파기 깊이 (단위 : 미터) |

* Sample
  * function 참조.
  * [샌드박스\_터파기 깊이 설정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_depth)
{% endtab %}
{% endtabs %}

## setRadius(radius)

> 원형 터파기 반경을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| radius | number | 원형 터파기 반경 (단우 : 미터) |

* Sample
  * function 참조.
  * [샌드박스\_터파기 반경 설정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_radius)
{% endtab %}
{% endtabs %}

## setTexture(imageData, width, height, type) → boolean

> 터파기 표면 텍스쳐 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| imageData | object | 이미지 Byte Array |
| width | number | 이미지 가로 크기 |
| height | number | 이미지 세로 크기 |
| type | boolean | <p>true인 경우 옆면 텍스쳐로 설정.<br>false인 경우 바닥면 텍스쳐로 설정.</p> |
  
* Return
  * true : 설정 성공.
  * false : 설정 실패.
  
* Sample
  * function 참조.
  * [샌드박스\_터파기 텍스쳐](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_texture)
{% endtab %}
{% endtabs %}

## startAutoMove() → boolean

> 사전에 지정된 경로를 따라 터파기 자동 이동을 시작합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  
* Sample
  * function 참조.
  * [샌드박스\_터파기 이동](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}
{% endtabs %}

## stopAutoMove() → boolean

> 사전에 지정된 경로를 따라 터파기 자동 이동을 종료합니다.

{% tabs %}
{% tab title="Information" %}

* Return
  * true : 설정 성공.
  * false : 설정 실패.
  
* Sample
  * function 참조.
  * [샌드박스\_터파기 이동](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}
{% endtabs %}