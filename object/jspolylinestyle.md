---
description: PolyLine 스타일 객체 생성 및 수정 기능 API.
---

# JSPolyLineStyle

### JSPolyLineStyle() → JSPolyLineStyle

> PolyLine 형 오브젝트의 스타일을 지정하는 JSPolyLineStyle 객체를 생성.
> 
> JSPolyLineStyle 객체를 통해 여러 폴리곤 형 오브젝트 스타일의 일괄 지정이 가능.

{% tabs %}
{% tab title="Template" %}
```javascript
var objectStyle = new Module.JSPolyLineStyle();
```
{% endtab %}
{% endtabs %}

## Getter / Setter

### _getColor() → JSColor

> 라인의 색상을 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * JSColor : 라인 색상.
{% endtab %}

{% tab title="Template" %}
```javascript
var color = polyline.getStyle().getColor();
```
{% endtab %}
{% endtabs %}

### _setColor(color)

> 라인의 색상을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| color | JSColor | 라인 색상. |
{% tab title="Template" %}

```javascript
polyline.getStyle().setColor(new Module.JSColor(255, 255, 255, 255));
```

{% endtab %}
{% endtabs %}

### _getWidth() → double

> 라인의 두께를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * double : 라인 두께.
{% endtab %}

{% tab title="Template" %}
```javascript
var width = polyline.getStyle().getWidth();
```
{% endtab %}
{% endtabs %}

### _setWidth(width)

> 라인의 두께를 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| width | double | 라인 두께. |
{% tab title="Template" %}

```javascript
polyline.getStyle().setWidth(10.0);
```

{% endtab %}
{% endtabs %}
