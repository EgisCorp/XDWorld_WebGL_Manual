---
description: 지도 내 시간 설정 API.
---

# JSDateTime

> Module JSDateTime API 생성할 수 있습니다.

```javascript
var startTime = new Module.JSDateTime(2023, 4, 27, 8, 0, 0); // 년, 월, 일, 시간, 분, 초
```

## properties

| Name   | Type   | Description |
| :----- | :----- | :---------- |
| year   | number | 연도        |
| month  | number | 월          |
| day    | number | 일          |
| hour   | number | 시          |
| minute | number | 분          |
| second | number | 초          |

## Function

### setCurrentTime()

> 입력된 정보로 시간을 설정합니다.
>
> 입력된 정보가 없다면 로컬 시간으로 설정합니다.

{% tabs %}
{% tab title="Infomation" %}
{% endtab %}
{% tab title="Template" %}

```javascript
var startTime = new Module.JSDateTime();
startTime.setCurrentTime();
```

{% endtab %}
{% endtabs %}
