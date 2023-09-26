---
description: 비디오 객체 생성 및 수정 기능 API.
---

# JSVideoObject

> Module.createVideoObject API 생성.

```javascript
var object = Module.createVideoObject("ID");
```

## Properties

| Name     | Type                                | Description                  |
| -------- | ----------------------------------- | ---------------------------- |
| isplayer | boolean                             | 현재 비디오 재생중인지 여부. |
| key      | string                              | 객체 키값.                   |
| tilt     | number                              | 바라보는 각도.               |
| far      | number                              | 최대 가시거리.               |
| pan      | number                              | 바라보는 방향.               |
| bank     | number                              | 비디오 기울기.               |
| fovX     | number                              | 화각 넓이.                   |
| fovY     | number                              | 화각 높이.                   |
| alpha    | number                              | 비디오 투명값.               |
| axisX    | boolean                             | 좌우 반전.                   |
| axisY    | boolean                             | 상하 반전.                   |
| position | [JSVector3D](../core/jsvector3d.md) | 객체 경도, 위도, 고도 위치.  |
| zoom     | number                              | 비디오 배율.                 |
| distance | number                              | 카메라와 객체의 거리.        |

## Function

### createVideo(option) → string

> 비디오 객체 생성.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| url | string | 미디어 URL 경로. |
| position | [JSVector3D](../core/jsvector3d.md) | 객체 경도, 위도, 고도 위치. |
| pan | number | 바라보는 방향. |
| tilt | number | 바라보는 각도. |
| far | number | 최대 가시거리. |
| bank | number | 비디오 기울기. |
| zoom | number | 비디오 배율. |
| fov | number | 비디오 화각 설정. |
| render | function | render callback 함수 설정. |
| xaxis | boolean | 좌우 반전 설정. |
| yaxis | boolean | 상하 반전 설정. |

-   Return
    -   success : 텍스쳐 생성 성공.
    -   객체 생성 실패일 경우
    -   null : 생성된 객체가 없을 경우.
    -   url tag isn't exist : url 태그가 없을 경우.
    -   position tag isn't exist : position 태그가 없을 경우.
    -   pan tag isn't exist : pan 태그가 없을 경우.
    -   tilt tag isn't exist : tilt 태그가 없을 경우.
    -   far tag isn't exist : far 태그가 없을 경우.
    -   fov tag isn't exist : fov 태그가 없을 경우.
-   Sample
    -   function createVideoFrustum 함수 참조.
    -   [샌드박스\_비디오 객체](http://sandbox.dtwincloud.com/code/main.do?id=object_video)
        {% endtab %}
        {% endtabs %}

### setTexture(option) → string

> 비디오 객체 텍스쳐 변경.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| size | number | 비디오 사이즈(width, height). |
| data | array | 비디오 프레임 픽셀 값 배열. |
| objectmapping | boolean | 건물 위에 가시화 여부. |

-   Return

    -   success : 텍스쳐 생성 성공.
    -   텍스쳐 생성 실패일 경우
    -   null : 생성된 객체가 없을 경우.
    -   object is null : 객체가 등록되지 않았을 경우.
    -   size tag isn't exist. : size 태그가 없을 경우.
    -   imagedata tag isn't exist. : imagedata 태그가 없을 경우.
    -   texture is't exist : 텍스쳐가 정상적으로 생성되지 않을 경우.

-   Sample
    -   function createVideos 함수 참조.
    -   [샌드박스\_비디오 객체](http://sandbox.dtwincloud.com/code/main.do?id=object_video)
        {% endtab %}
        {% endtabs %}

### clearTexture() → boolean

> 비디오 객체 초기화.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true : 초기화 성공.
    -   false : 초기화 실패.
    -   생성된 객체가 없을 경우.
    -   비디오 데이터가 없을 경우.
    -   비디오 경로가 없을 경우.
-   Sample
    -   function clearCCTV 함수 참조.
    -   [샌드박스\_비디오 객체](http://sandbox.dtwincloud.com/code/main.do?id=object_video)
        {% endtab %}
        {% endtabs %}
