---
description: 지도 내 비디오 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSVideoObject

> Module.createVideoObject() API를 생성합니다.

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

> 비디오 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                   |
| :------- | :---------------------------------- | :---------------------------- |
| url      | string                              | 미디어 URL 경로.              |
| position | [JSVector3D](../core/jsvector3d.md) | 중심 좌표 (경도, 위도, 고도). |
| pan      | number                              | 바라보는 방향.                |
| tilt     | number                              | 바라보는 각도.                |
| far      | number                              | 최대 가시거리.                |
| bank     | number                              | 비디오 기울기.                |
| zoom     | number                              | 비디오 배율.                  |
| fov      | number                              | 비디오 화각 설정.             |
| render   | function                            | render callback 함수 설정.    |
| xaxis    | boolean                             | 좌우 반전 설정.               |
| yaxis    | boolean                             | 상하 반전 설정.               |

-   Return
    -   success : 텍스쳐 생성 성공.
    -   실패 조건
        -   null : 생성된 객체가 없을 경우.
        -   url tag isn't exist : url 태그가 없을 경우.
        -   position tag isn't exist : position 태그가 없을 경우.
        -   pan tag isn't exist : pan 태그가 없을 경우.
        -   tilt tag isn't exist : tilt 태그가 없을 경우.
        -   far tag isn't exist : far 태그가 없을 경우.
        -   fov tag isn't exist : fov 태그가 없을 경우.
-   Sample
    -   function createVideoFrustum 참조.
    -   [Sandbox_Video Object](https://sandbox.egiscloud.com/code/main.do?id=object_video)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### setTexture(option) → string

> 비디오 객체의 표현 중인 이미지를 변경합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type    | Description                        |
| :------------ | :------ | :--------------------------------- |
| size          | number  | Video size (width, height).        |
| data          | array   | Array of video frame pixel values. |
| objectmapping | boolean | Whether to visualize on buildings. |

-   Return

    -   success : 생성 성공.
    -   실패 조건
        -   null : 생성된 객체가 없을 경우.
        -   object is null : 객체가 등록되지 않았을 경우.
        -   size tag isn't exist. : size 태그가 없을 경우.
        -   imagedata tag isn't exist. : imagedata 태그가 없을 경우.
        -   texture is't exist : 텍스쳐가 정상적으로 생성되지 않을 경우.

-   Sample
    -   function createVideos 참조.
    -   [Sandbox_Video Object](https://sandbox.egiscloud.com/code/main.do?id=object_video)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### clearTexture() → boolean

> 비디오 객체를 초기화 합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   true : 초기화 성공.
    -   false : 초기화 실패.
    -   실패 조건
        -   생성된 객체가 없을 경우.
        -   비디오 데이터가 없을 경우.
        -   비디오 경로가 없을 경우.
-   Sample
    -   function clearCCTV 참조.
    -   [Sandbox_Video Object](https://sandbox.egiscloud.com/code/main.do?id=object_video)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}
