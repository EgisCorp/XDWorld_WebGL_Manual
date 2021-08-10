---
description: 터파기 기능 설정 API를 제공합니다.
---

# JSTransparency

## create\( vertex \) → number

> 입력 좌표를 받아 터파기 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| vertex | [JSVec3Array](../core/jsvec3array.md) | 터파기 영역 좌표 리스트 |

* Detail
  * vertex : \([JSVector3D](../core/jsvector3d.md), [JSVector3D](../core/jsvector3d.md), ...\) 터파기 영역 좌표 리스트 배열
* Return
  * 설정 성공 \(좌표 리스트 크기 반환\) 혹은 실패 \(-1\)
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_transparency\_create](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_create)
{% endtab %}
{% endtabs %}

## setAutoMove\( position, waitframe \) → boolean

> 자동으로 이동하는 원형 터파기의 이동 경로 및 속도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector2D](../core/jsvector2d.md) | 터파기 이동경로 좌표 리스트 |
| waitframe | number | 터파기 위치 갱신 프레임 수 |

* Detail
  * vertex : \([JSVector2D](../core/jsvector2d.md), [JSVector2D](../core/jsvector2d.md), ...\) 터파기 이동경로 좌표 리스트 배열
  * waitframe : 터파기 위치 갱신 프레임 수
* Return
  * 설정 성공 \(true\) 혹은 실패 \(false\)
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_transparency\_move](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}
{% endtabs %}

## setDepth\( depth \)

> 터파기 깊이를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| depth | number | 터파기 깊이 \(m단위\) |

* Detail
  * depth : 지면으로부터 터파기 깊이 \(m단위\) 
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_transparency\_depth](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_depth)
{% endtab %}
{% endtabs %}

## setRadius\( radius \)

> 원형 터파기 반경을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| radius | number | 원형 터파기 반경 |

* Detail
  * depth : 원형 터파기 반경
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_transparency\_radius](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_radius)
{% endtab %}
{% endtabs %}

## setTexture\( imageData, width, height, type\) → boolean

> 터파기 표면 텍스쳐 이미지를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| imageData | object | 이미지 Byte Array |
| width | number | 이미지 가로 크기 |
| height | number | 이미지 세로 크기 |
| type | boolean | 설정 표면 타입 |

* Detail
  * type
    * false : 옆면 텍스쳐로 설정합니다.
    * true : 바닥면 텍스쳐로 설정합니다.
* Return
  * 설정 성공 \(true\) 혹은 실패 \(false\)
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_transparency\_texture](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_texture)
{% endtab %}
{% endtabs %}

## startAutoMove\(\) → boolean

> 사전에 지정된 경로를 따라 터파기 자동 이동을 시작합니다.

{% tabs %}
{% tab %}
* Return
  * 설정 성공 \(true\) 혹은 실패 \(false\)
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_transparency\_move](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}
{% endtabs %}

## stopAutoMove\(\) → boolean

> 사전에 지정된 경로를 따라 터파기 자동 이동을 종료합니다.

{% tabs %}
{% tab %}
* Return
  * 설정 성공 \(true\) 혹은 실패 \(false\)
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=analysis\_transparency\_move](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}
{% endtabs %}

