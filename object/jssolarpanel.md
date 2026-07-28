---
description: 지도 내 태양광 패널 3차원 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSSolarPanel

> Module.createSolarPanel() API를 생성합니다.

```javascript
var panel = Module.createSolarPanel("ID");
```

## Function

### create(position, width, height, thickness, panelAngle, direction) → boolean

> 단일 태양광 패널 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type                                | Description                     |
| :--------- | -------------------------------------- | ------------------------------------- |
| position   | [JSVector3D](../core/jsvector3d.md)  | 패널 중심 좌표(경도, 위도, 고도).      |
| width      | number                                  | 패널 너비.                            |
| height     | number                                  | 패널 높이.                            |
| thickness  | number                                  | 패널 두께.                            |
| panelAngle | number                                  | 패널 기울기 각도(degrees).            |
| direction  | number                                  | 패널 방위각(degrees).                 |

-   Return
    -   true: 생성 성공.
    -   false: 객체가 없는 경우.
-   Note
    -   [setTexture()](jssolarpanel.md#settexture-imagedata-imagewidth-imageheight-boolean)로 미리 텍스처를 설정한 경우 해당 텍스처가 패널에 적용됩니다.

{% endtab %}
{% tab title="Template" %}

```javascript
var panel = Module.createSolarPanel("Panel_1");
panel.create(
    new Module.JSVector3D(127.0, 37.5, 30.0),
    1.0, 1.6, 0.05, 30.0, 180.0
);
```

{% endtab %}
{% endtabs %}

### createMergePanel(positions, width, height, thickness, panelAngle, direction) → boolean

> 여러 개의 좌표에 대해 동일한 규격의 태양광 패널을 하나의 병합된 객체로 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type                                    | Description                     |
| :--------- | ------------------------------------------ | ------------------------------------- |
| positions  | [JSVec3Array](../core/jsvec3array.md)   | 패널 중심 좌표 목록.                   |
| width      | number                                      | 패널 너비.                            |
| height     | number                                      | 패널 높이.                            |
| thickness  | number                                      | 패널 두께.                            |
| panelAngle | number                                      | 패널 기울기 각도(degrees).            |
| direction  | number                                      | 패널 방위각(degrees).                 |

-   Return
    -   true: 생성 성공.
    -   false: 객체가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var panel = Module.createSolarPanel("Panel_Merged");
var positions = new Module.JSVec3Array();
positions.push(new Module.JSVector3D(127.0, 37.5, 30.0));
positions.push(new Module.JSVector3D(127.0001, 37.5, 30.0));
panel.createMergePanel(positions, 1.0, 1.6, 0.05, 30.0, 180.0);
```

{% endtab %}
{% endtabs %}

### setTexture(imageData, imageWidth, imageHeight) → boolean

> 패널 표면에 적용할 텍스처를 픽셀 데이터로 설정합니다. [create()](jssolarpanel.md#create-position-width-height-thickness-panelangle-direction-boolean) 또는 [createMergePanel()](jssolarpanel.md#createmergepanel-positions-width-height-thickness-panelangle-direction-boolean) 호출 이전에 설정해야 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type          | Description                     |
| :---------- | ------------- | ------------------------------------ |
| imageData   | array(number) | 이미지 픽셀 데이터(ARGB byte 배열).  |
| imageWidth  | number        | 이미지 너비.                         |
| imageHeight | number        | 이미지 높이.                         |

-   Return
    -   true: 설정 성공.
    -   false: imageData 길이가 1 이하인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var panel = Module.createSolarPanel("Panel_1");
panel.setTexture(pixelArray, 64, 64);
panel.create(new Module.JSVector3D(127.0, 37.5, 30.0), 1.0, 1.6, 0.05, 30.0, 180.0);
```

{% endtab %}
{% endtabs %}
