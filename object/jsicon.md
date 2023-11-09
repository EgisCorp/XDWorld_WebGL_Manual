---
description: >-
  텍스쳐로 활용되는 아이콘 객체. JSSymbol 클래스 객체에 등록하여 사용하며 각 아이콘은 등록 시 이름을 설정합니다. 아이콘 이름은
  중복하여 등록할 수 없습니다.
---

# JSIcon

> Module.JSIcon API 생성.

```javascript
```

### getId() → string

> 오브젝트의 Key를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * 유효한 문자열(string) : 오브젝트의 Key 반환 성공.
  * 빈 문자열(string) : 오브젝트가 null인 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var strKey = object.getId();
```
{% endtab %}
{% endtabs %}

### getReferenceCount() → number

> 아이콘을 참조 중인 오브젝트 수를 반환.

{% tabs %}
{% tab title="Information" %}
* Return
  * number(0 ~ ) : 참조 오브젝트 수 반환 성공.
  * -1 : 해당 이름으로 등록된 아이콘의 텍스쳐가 존재하지 않는 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
var icon = Module.getSymbol().getIcon("mapIcon");
var refCount = icon.getReferenceCount();
```
{% endtab %}
{% endtabs %}
