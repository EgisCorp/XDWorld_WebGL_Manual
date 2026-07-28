---
description: 태양광 패널이 설치된 건물(구조물) 정보를 조회하기 위한 API 입니다.
---

# JSSolarStructure

> [JSSolarManager.getRoofedStructure()](../manager/jssolarmanager.md#getroofedstructurestructureindex--cjssolarstructure)의 반환 객체로 생성됩니다.
>
> 직접 생성할 수 없으며, 태양광 패널이 설치된 건물 1개에 대한 정보를 조회하는 용도로 사용됩니다.

```javascript
var solarManager = Module.getSolarManager();
var structure = solarManager.getRoofedStructure(0);
```

## Function

### getStructureContainLayerName() → string

> 태양광 패널을 포함하는 건물이 소속된 레이어의 명칭을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 건물이 소속된 레이어 명칭.

{% endtab %}
{% tab title="Template" %}

```javascript
var layerName = structure.getStructureContainLayerName();
```

{% endtab %}
{% endtabs %}

### getStructureKey() → string

> 태양광 패널이 설치된 건물 객체의 고유 명칭(오브젝트 키)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 반환 성공.
    -   "": 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var objectKey = structure.getStructureKey();
```

{% endtab %}
{% endtabs %}

### getRoofCount() → number

> 건물에 포함된(태양광 패널이 설치된) 지붕의 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   number(0 이상): 지붕 개수.
    -   -1: 월드가 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var roofCount = structure.getRoofCount();
```

{% endtab %}
{% endtabs %}

### getSolarPanelPosition(roofIndex) → [JSVec3Array](../core/jsvec3array.md)

> 지정한 지붕 인덱스에 설치된 태양광 패널들의 중심 좌표 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| :-------- | :----- | :--------------------- |
| roofIndex | number | 조회할 지붕 인덱스([getRoofCount()](jssolarstructure.md#getroofcount--number) 범위 내). |

-   Return
    -   [JSVec3Array](../core/jsvec3array.md): 패널 중심 좌표(경도, 위도, 고도) 목록.
    -   빈 배열: 월드가 초기화되지 않았거나, roofIndex가 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var positions = structure.getSolarPanelPosition(0);
```

{% endtab %}
{% endtabs %}
