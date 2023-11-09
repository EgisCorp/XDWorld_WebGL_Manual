---
description: 터파기 분석 기능 설정 API.
---

# JSTransparency

> Module.getTransparency API 생성.

```javascript
var transparency = Module.getTransparency();
```

### clear()

> 생성된 터파기를 모두 삭제.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getTransparency().clear();
```
{% endtab %}
{% endtabs %}

### create(coordinates) → number

> 입력 좌표를 받아 터파기 객체를 생성.
> 
> coordinates 입력값은 ([JSVector3D](../core/jsvector3d.md), [JSVector3D](../core/jsvector3d.md), ...) 영역 좌표 목록.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec3Array](../core/jsvec3array.md) | 터파기 영역 좌표 리스트. |

* Return
  * 설정 성공 (좌표 리스트 크기 반환) 혹은 실패 (-1)
  
* Sample
  * function createTransparency 참조.
  * [샌드박스\_터파기 생성](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_create)
{% endtab %}

{% tab title="Template" %}
```javascript
var AreaVertices = Module.getMap().getInputPoints();
var nIndex = Module.getTransparency().create(AreaVertices);
```
{% endtab %}
{% endtabs %}

### setAutoMove(coordinates, frame) → boolean

> 자동으로 이동하는 원형 터파기의 이동 경로 및 속도를 설정합니다.
> 
> coordinates 입력값은 ([JSVector2D](../core/jsvector2d.md), [JSVector2D](../core/jsvector2d.md), ...) 이동경로 좌표 목록.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| coordinates | [JSVec2Array](../core/jsvec2array.md) | 터파기 이동경로 좌표 목록. |
| frame | number | 터파기 위치 갱신 프레임 수. |
  
* Return
  * true : 설정 성공.
  * false : 설정 실패.
  
* Sample
  * function setTransparencyAutoMove 참조.
  * [샌드박스\_터파기 이동](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}

{% tab title="Template" %}
```javascript
var movePositionList = new Module.JSVec2Array();
movePositionList.push(new Module.JSVector2D(127.03691229708741, 37.509635136930626));
movePositionList.push(new Module.JSVector2D(127.03987097629198, 37.50932526196098));
movePositionList.push(new Module.JSVector2D(127.03695802409491, 37.50865005215346));
movePositionList.push(new Module.JSVector2D(127.03985503640686, 37.50816724210336));
movePositionList.push(new Module.JSVector2D(127.03711645791172, 37.50779863443866));
movePositionList.push(new Module.JSVector2D(127.03978095384555, 37.50738212410067));
// 터파기 자동 이동 설정
Module.getTransparency().setAutoMove(movePositionList, 5);
```
{% endtab %}
{% endtabs %}

### setDepth(depth)

> 터파기 깊이를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| depth | number | 지면으로부터 터파기 깊이 (단위 : 미터). |

* Sample
  * function createTransparency 참조.
  * [샌드박스\_터파기 깊이 설정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_depth)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getTransparency().setDepth(5.5);
```
{% endtab %}
{% endtabs %}

### setRadius(radius)

> 원형 터파기 반경을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| radius | number | 원형 터파기 반경 (단우 : 미터). |

* Sample
  * function setTransparencyRadius 참조.
  * [샌드박스\_터파기 반경 설정](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_radius)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getTransparency().setRadius(500.0);
```
{% endtab %}
{% endtabs %}

### setTexture(data, width, height, type) → boolean

> 터파기 표면 텍스쳐 이미지를 설정합니다.
> 
> data 변수는 Uint8Array 기반의 바이너리 배열 데이터.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| data | object | 이미지 Byte Array |
| width | number | 이미지 가로 크기 |
| height | number | 이미지 세로 크기 |
| type | boolean | <p>true인 경우 옆면 텍스쳐로 설정.<br>false인 경우 바닥면 텍스쳐로 설정.</p> |
  
* Return
  * true : 설정 성공.
  * false : 설정 실패.
  
* Sample
  * function setTransparencyTexture 참조.
  * [샌드박스\_터파기 텍스쳐](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_texture)
{% endtab %}

{% tab title="Template" %}
```javascript
var img = new Image();
// 텍스쳐 이미지 로드
img.onload = function(){
    var canvas = document.createElement('canvas');
    canvas.width = img.width;
    canvas.height = img.height;
    var ctx = canvas.getContext('2d');
    ctx.drawImage(img, 0, 0);
    var imageSize = new Module.JSSize2D(img.width, img.height);
    var imageData = ctx.getImageData(0, 0, canvas.width, canvas.height).data;
    // 터파기 텍스쳐 설정
    var transparency = Module.getTransparency();
    transparency.setTexture(imageData, canvas.width, canvas.height, true);  // 터파기 바닥면 텍스쳐
    transparency.setTexture(imageData, canvas.width, canvas.height, false); // 터파기 벽면 텍스쳐
}
img.src = "./image/FaceImage.jpg";
```
{% endtab %}
{% endtabs %}

### startAutoMove() → boolean

> 사전에 지정된 경로를 따라 터파기 자동 이동을 시작합니다.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 이동 시작 성공.
  * false : 이동 시작 실패.
  
* Sample
  * function startTransparencyAutoMove 참조.
  * [샌드박스\_터파기 이동](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getTransparency().startAutoMove();
```
{% endtab %}
{% endtabs %}

### stopAutoMove()

> 사전에 지정된 경로를 따라 터파기 자동 이동을 종료합니다.

{% tabs %}
{% tab title="Information" %}
* Sample
  * function stopTransparencyAutoMove 참조.
  * [샌드박스\_터파기 이동](http://sandbox.dtwincloud.com/code/main.do?id=analysis_transparency_move)
{% endtab %}

{% tab title="Template" %}
```javascript
Module.getTransparency().stopAutoMove();
```
{% endtab %}
{% endtabs %}