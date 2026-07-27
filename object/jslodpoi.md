---
description: 카메라 거리(LOD)에 따라 헤드/타겟 아이콘과 연결선을 표시하는 POI 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSLODPOI

> Module.createLODPOI() API를 생성합니다.

```javascript
var lodPoi = Module.createLODPOI("ID");
```

## Function

### createPOI(position, x, y, z, lineStyle, lineColor, lineWidth, lineDistance) → boolean

> LOD POI 객체를 생성합니다. 기준 좌표(position)와 상대 오프셋(x, y, z)으로 대상 지점을 지정하고, 그 사이를 잇는 연결선의 스타일을 함께 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type                                | Description                    |
| :----------- | -------------------------------------- | ----------------------------------- |
| position     | [JSVector3D](../core/jsvector3d.md)  | 기준 좌표(경도, 위도, 고도).       |
| x            | number                                  | 대상 지점 상대 오프셋 X.           |
| y            | number                                  | 대상 지점 상대 오프셋 Y.           |
| z            | number                                  | 대상 지점 상대 오프셋 Z.           |
| lineStyle    | number                                  | 연결선 스타일.                     |
| lineColor    | [JSColor](../core/jscolor.md)        | 연결선 색상.                       |
| lineWidth    | number                                  | 연결선 두께.                       |
| lineDistance | number                                  | 연결선 표시 거리 기준값.           |

-   Return
    -   true: 생성 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var lodPoi = Module.createLODPOI("LODPOI_1");
lodPoi.createPOI(
    new Module.JSVector3D(127.0, 37.5, 0.0),
    0, 0, 100,
    0,
    new Module.JSColor(255, 255, 255, 255),
    2.0,
    5000.0
);
```

{% endtab %}
{% endtabs %}

### setHeadIcon(icon) → boolean

> 기준 지점(Head)에 표시할 아이콘을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                          | Description |
| :--- | ----------------------------- | ----------- |
| icon | [JSIcon](jsicon.md)           | 헤드 아이콘. |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.setHeadIcon(Module.getSymbol().getIcon("head_icon"));
```

{% endtab %}
{% endtabs %}

### setTarIcon(icon) → boolean

> 대상 지점(Target)에 표시할 아이콘을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type                 | Description  |
| :--- | ---------------------- | ------------------ |
| icon | [JSIcon](jsicon.md)  | 타겟(대상) 아이콘. |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.setTarIcon(Module.getSymbol().getIcon("target_icon"));
```

{% endtab %}
{% endtabs %}

### setLineColor(color) → boolean

> 헤드-타겟 연결선의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description |
| :---- | ----------------------------- | ----------- |
| color | [JSColor](../core/jscolor.md) | 연결선 색상. |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.setLineColor(new Module.JSColor(255, 0, 255, 0));
```

{% endtab %}
{% endtabs %}

### setLineStyle(style) → boolean

> 헤드-타겟 연결선의 스타일을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | ------ | ------------------ |
| style | number | 연결선 스타일(내부 정의값). |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.setLineStyle(1);
```

{% endtab %}
{% endtabs %}

### setLineDist(distance) → boolean

> 헤드-타겟 연결선이 표시되는 거리 기준값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description       |
| :------- | ------ | ---------------------- |
| distance | number | 연결선 표시 거리 기준값. |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.setLineDist(3000.0);
```

{% endtab %}
{% endtabs %}

### setLineWidth(width) → boolean

> 헤드-타겟 연결선의 두께를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description  |
| :---- | ------ | ----------------- |
| width | number | 연결선 두께.       |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.setLineWidth(1.5);
```

{% endtab %}
{% endtabs %}

### setText(text) → boolean

> POI 객체에 표시할 문자열을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| :--- | ------ | ----------------- |
| text | string | 표시할 문자열(유니코드 지원). |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.setText("표시 문구");
```

{% endtab %}
{% endtabs %}

### setFontStyle(fontName, fontSize, fontWeight, fontColor, outlineColor) → boolean

> [setText()](jslodpoi.md#settexttext-boolean)로 표시되는 문자열의 폰트 스타일을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type                          | Description   |
| :----------- | ----------------------------- | ------------------ |
| fontName     | string                         | 폰트 이름.         |
| fontSize     | number                         | 폰트 크기.         |
| fontWeight   | number                         | 폰트 굵기.         |
| fontColor    | [JSColor](../core/jscolor.md) | 폰트 색상.         |
| outlineColor | [JSColor](../core/jscolor.md) | 폰트 외곽선 색상.  |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.setFontStyle(
    "Arial", 20, 10,
    new Module.JSColor(255, 255, 255, 255),
    new Module.JSColor(255, 0, 0, 0)
);
```

{% endtab %}
{% endtabs %}

### set3DMode(set) → boolean

> POI 객체의 3D 표시 모드(화면 고정 여부) 사용 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                     |
| :--- | ------- | ---------------------------------------------------- |
| set  | boolean | <p>true: 3D 모드 사용.<br>false: 3D 모드 미사용.</p>  |

-   Return
    -   true: 설정 성공.
    -   false: 월드 또는 객체가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
lodPoi.set3DMode(true);
```

{% endtab %}
{% endtabs %}
