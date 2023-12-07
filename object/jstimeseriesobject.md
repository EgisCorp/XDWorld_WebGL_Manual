---
description: 시계열 오브젝트 생성 및 수정 API.
---

# JSTimeSeriesObject

> Module.createTimeSeriesObject API 생성.
> 생성 후 JSTimeSeriesObject.create() 혹은 JSTimeSeriesObject.createbyJson() API에 파라메터를 전달하여 시계열 데이터 초기화.

```javascript
let object = Module.createTimeSeriesObject("timeSeriesObject");

// 자세한 파라메터는 API 참고
object.create(/*parameter*/);
object.createJSON(/*parameter*/);
```

### create(parameter) → error

> 시계열 객체 생성.
>
> parameter 변수로 전체 데이터(이미지, 경위도 기준점, 객체 크기, 객체 형태) 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| parameter | [JSTimeSeriesObject.createParameter](jstimeobject.md#jstimeobject.createparameter) | 전체 데이터. |

* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSTimeSeriesPolygon.create" 고정.</br> |
  | return | string | (실패시)오류 메시지를 string으로 반환(자세한 사항은 메시지 참조). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %} 
