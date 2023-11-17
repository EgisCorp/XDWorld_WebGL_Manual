---
description: 지형의 경사향, 경사도 분석 기능 API.
---

# JSSlope

> Module.getSlope API 반환.

```javascript
var Slope = Module.getSlope();
```

### clearAnalysisData()

> 분석 내용을 초기화.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getSlope().clearAnalysisData();
```
{% endtab %}
{% endtabs %}

### clearColorList() → boolean

> 등록한 범례 색상 리스트를 초기화.

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 초기화 성공.
  * false : 초기화 실패.
{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSlope().clearColorList();
```
{% endtab %}
{% endtabs %}

### getColorArea(key, index) → number

> 각 범례 인덱스 별 면적 값을 반환.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| key | string | 분석 대상 오브젝트 명칭. |
| index | number | 면적 값을 반환할 범례 인덱스. |
{% endtab %}
{% tab title="Information" %}
* Return
  * number(0 ~) : 범례에 해당하는 면적 반환 성공(제곱미터 단위).
  * -1 : index가 유효하지 않거나, key에 해당하는 오브젝트를 찾지 못한 경우.
{% endtab %}
{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}
