---
description: 도로 객체에서 사용할 텍스처를 등록하기 위한 API 입니다.
---

# JSRoadManager

> Module.JSRoadManager() API를 생성합니다.

```javascript
var roadManager = new Module.JSRoadManager();
```

## Function

### addTexture(option)

> 도로 텍스처로 사용할 이미지를 픽셀 데이터로 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name          | Type          | Description                        |
| :------------ | ------------- | ---------------------------------------- |
| option        | object        | 텍스처 등록 옵션.                        |
| ↳ key         | string        | 텍스처 고유 명칭.                        |
| ↳ pixels      | array(number) | 이미지 픽셀 데이터(ARGB byte 배열).       |
| ↳ width       | number        | 이미지 너비.                             |
| ↳ height      | number        | 이미지 높이.                             |

-   Note
    -   option.pixels가 없거나 길이가 0인 경우, 또는 key/width/height 중 하나라도 없으면 아무 동작도 하지 않습니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var roadManager = new Module.JSRoadManager();
roadManager.addTexture({
    key: "road_texture_1",
    pixels: pixelArray,
    width: 256,
    height: 256
});
```

{% endtab %}
{% endtabs %}
