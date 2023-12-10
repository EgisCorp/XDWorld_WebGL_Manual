---
description: 시계열 오브젝트 생성 및 수정 API.
---

# JSTimeSeriesObject

> Module.createTimeSeriesObject API 생성.
> 
> 생성 후 create() 혹은 createbyJson() API에 파라메터를 전달하여 시계열 데이터 초기화.
> 
> 데이터 갱신이 필요할 경우, insert(), merge() 순으로 함수를 호출하여 데이터 갱신.

```javascript
let object = Module.createTimeSeriesObject("timeSeriesObject");

// 자세한 파라메터는 API 참고
object.create(/*parameter*/);
object.createJSON(/*parameter*/);

object.insert(/*parameter*/);
object.merge(/*parameter*/);
```

### create(parameter) → error

> 시계열 객체 생성.
>
> parameter 변수로 전체 데이터(이미지, 경위도 기준점, 객체 크기, 객체 형태) 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeobject.md#jstimeobject.objectdata) | 전체 데이터. |

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

### createbyJson(parameter) → error

> 시계열 객체 생성.
>
> parameter 변수로 전체 데이터(이미지, 경위도 기준점, 객체 크기, 객체 형태) 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeobject.md#jstimeobject.objectdata) | 전체 데이터. |

* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSTimeSeriesPolygon.createByJson" 고정.</br> |
  | return | string | (실패시)오류 메시지를 string으로 반환(자세한 사항은 메시지 참조). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### insert(parameter) → error

> 추가할 객체 정보 입력.
> 
> 이후 merge()를 호출하여 입력한 데이터를 기존 객체에 추가하는 작업 필요.
>
> parameter 변수로 전체 데이터(이미지, 경위도 기준점, 객체 크기, 객체 형태) 전달.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| parameter | [JSTimeSeriesObject.ObjectData](jstimeobject.md#jstimeobject.objectdata) | 전체 데이터. |

* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSTimeSeriesPolygon.insert" 고정.</br> |
  | return | string | (실패시)오류 메시지를 string으로 반환(자세한 사항은 메시지 참조). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### merge() → error

> insert()로 입력한 데이터를 기존 객체에 추가하는 함수.

{% tabs %}
{% tab title="Information" %}
* Return
  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"JSTimeSeriesPolygon.merge" 고정.</br> |
  | return | string | (실패시)오류 메시지를 string으로 반환(자세한 사항은 메시지 참조). |
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSTimeSeriesObject.ObjectData
| Name | Type | Default | Description |
| --- | --- | --- | --- |
|  |  |  |  |
