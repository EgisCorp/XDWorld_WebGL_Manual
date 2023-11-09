---
description: ARGB 색상을 정의합니다.
---

# JSColor

> new Module.Color API 생성.
> 
> JSColor 생성 시 기본값 ARGB(255, 255, 255, 255) 설정.

```javascript
var color = new Module.JSColor(255, 100, 100, 0); // ARGB

var color = new Module.JSColor(100, 100, 0);	// RGB

var color = new Module.JSColor();
```

### getValue(index) → number

> 색상 값이 저장된 2진수 데이터를 10진수로 반환.
> 
> 색상은 ARGB 순서대로 8bit씩 저장되어 있음(총 32bit).

{% tabs %}
{% tab title="Information" %}
* Return
  * number : 10진수로 변환된 색상 데이터
{% endtab %}

{% tab title="Template" %}
```javascript
var color = new Module.JSColor(255, 4, 32, 100);
var value = color.getValue(); // value : 4278460516
// 10진수 4278460516은 2진수로 11111111000001000010000001100100
//  2진수 1111 1111 / 0000 0100 / 0010 0000 / 0110 0100
//   ARGB       255 /         4 /        32 /       100
```
{% endtab %}
{% endtabs %}

### setARGB(a, r, g, b)

> 색상 값을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| a | number | 색상 Alpha. |
| r | number | 색상 Red. |
| g | number | 색상 Green. |
| b | number | 색상 Blue. |
{% endtab %}

{% tab title="Template" %}
```javascript
var color = new Module.JSColor();
color.SetARGB(255, 255, 0, 200);
```
{% endtab %}
{% endtabs %}

### setHexCode(hexCode)

> Hex 코드로 색상 값을 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| hexCode | string | '#(00)(00)(00)(00)' 형태의 색상 코드.<br>숫자는 순서대로 Alpha, Red, Green, Blue 색상의 16진수 값.</br> |

- Return
    - true : 설정 성공
    - false : 문자열 '#' 시작하며 숫자 8자리 형식인 Hex Code 문자열이 아닌 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var color = new Module.JSColor();
color.setHexCode('#FF002442');
```
{% endtab %}
{% endtabs %}

## properties

| Name | Type | Description |
| :--- | :--- | :--- |
| a | number | alpha 색상 값 |
| r | number | red 색상 값 |
| g | number | green 색상 값 |
| b | number | blue 색상 값 |