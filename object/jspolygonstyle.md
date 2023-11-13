---
description: 폴리곤 스타일 객체 생성 및 수정 기능 API.
---

# JSPolygonStyle

### JSPolygonStyle() → JSPolygonStyle

> 폴리곤 형 오브젝트의 스타일을 지정하는 JSPolygonStyle 오브젝트를 생성.
> 
> JSPolygonStyle 객체를 통해 여러 폴리곤 형 오브젝트 스타일의 일괄 지정이 가능.

```javascript
var objectStyle = new Module.JSPolygonStyle();
```

## Getter / Setter

### getFill() → boolean

> 오브젝트의 채움 색상 적용 여부를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 채움 색상 적용.
  * false : 채움 색상 적용하지 않음.
{% endtab %}

{% tab title="Template" %}
```javascript
var bOutlineUsed = polygon.getStyle().getFill();
```
{% endtab %}
{% endtabs %}

### setFill(fill)

> 오브젝트의 채움 색상 적용 여부를 설정.
> 
> 설정하지 않았을 경우, 적용되어 있음(true).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| fill | boolean | 오브젝트의 채움 색상 적용 여부.<br>true일 경우 색상 적용.</br><br>false일 경우 적용하지 않음.</br> |
{% tab title="Template" %}

```javascript
var figure = new Module.JSFigure();
//...
var polyStyle = figure.getStyle();
polyStyle.setFill(true);
```

{% endtab %}
{% endtabs %}

### getFillColor() → JSColor

> 오브젝트의 스타일의 채움 색상을 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * JSColor : 설정하고자 하는 색상 오브젝트.
{% endtab %}

{% tab title="Template" %}
```javascript
var figure = new Module.JSFigure();
//...
var polyStyle = figure.getStyle();
var fillColor = polyStyle.getFillColor();
```
{% endtab %}
{% endtabs %}

### setFillColor(color)

> 오브젝트의 스타일의 채움 색상을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| color | JSColor | 설정하고자 하는 색상 오브젝트. |
{% tab title="Template" %}

```javascript
var polyStyle = figure.getStyle();
var fillColor = new Module.JSColor(255, 255, 100, 0);
polyStyle.setFillColor(fillColor);
```

{% endtab %}
{% endtabs %}

### getOutLine() → boolean

> 오브젝트의 외곽 라인 색상 적용 여부를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 외곽 라인 색상 적용.
  * false : 외곽 라인 색상 적용하지 않음.
{% endtab %}

{% tab title="Template" %}
```javascript
var bOutlineUsed = polygon.getStyle().getOutLine();
```
{% endtab %}
{% endtabs %}

### setOutLine(set)

> 오브젝트의 외곽 라인 색상 적용 여부를 설정.
> 
> 설정하지 않았을 경우, 적용되어 있음(true).

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| set | boolean | 외곽 라인 색상 적용 여부.<br>true일 경우 색상 적용.</br><br>false일 경우 적용하지 않음.</br> |
{% tab title="Template" %}

```javascript
var figure = new Module.JSFigure();
//...
var polyStyle = figure.getStyle();
polyStyle.setOutLine(false);
```

{% endtab %}
{% endtabs %}

### getOutLineColor() → JSColor

> 오브젝트의 스타일의 외곽 라인 색상을 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * JSColor : 설정한 외곽 라인 색상.
{% endtab %}

{% tab title="Template" %}
```javascript
var figure = new Module.JSFigure();
//...
var polyStyle = figure.getStyle();
var outlineColor = polyStyle.getOutLineColor();
```
{% endtab %}
{% endtabs %}

### settOutLineColor(color)

> 오브젝트의 스타일의 외곽 라인 색상을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| color | JSColor | 설정하고자 하는 색상 오브젝트. |
{% tab title="Template" %}

```javascript
var figure = new Module.JSFigure();
//...
var polyStyle = figure.getStyle();
var outlineColor = new Module.JSColor(255, 255, 0, 0);
polyStyle.setOutLineColor(outlineColor);
```

{% endtab %}
{% endtabs %}
