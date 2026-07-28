---
description: 타일 기반 레이어의 개별 타일을 조회 및 설정하기 위한 API 입니다.
---

# JSTile

> [JSLayer.addTileInObject()](jslayer.md#addtileinobject-tileinfo-object-boolean) 등에서 사용되는 타일 정보 객체로, 직접 생성하지 않으며 지구본 타일 기반 레이어의 내부 타일에 대응됩니다.

```javascript
// 타일 정보 객체는 레이어 내부 타일 탐색 API를 통해 얻게 됩니다(예시).
var tile = layer.findTile(level, idx, idy);
```

## Properties

| Name  | Type                                 | Description                          |
| ----- | --------------------------------------- | ---------------------------------------- |
| center | [JSVector2D](../core/jsvector2d.md)  | 타일 중심 좌표(경도, 위도, 읽기 전용). |
| idx    | number                               | 타일 X 인덱스(읽기 전용). 타일이 없으면 -1. |
| idy    | number                               | 타일 Y 인덱스(읽기 전용). 타일이 없으면 -1. |
| level  | number                               | 타일 레벨(읽기 전용). 타일이 없으면 -1.     |

## Function

### addObject(object) → boolean

> 타일에 객체를 직접 삽입합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                              | Description |
| :----- | ---------------------------------- | ----------- |
| object | [JSObject](../object/jsobject3d.md) | 삽입할 객체. |

-   Return
    -   true: 삽입 성공.
    -   false: 삽입 실패.
    -   실패 조건
        -   타일이 없는 경우.
        -   object가 준비되지 않은 경우.
        -   타일이 속한 레이어가 없는 경우.
        -   레이어에 객체 삽입이 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
tile.addObject(object);
```

{% endtab %}
{% endtabs %}

### setFileRequestState(state) → boolean

> 타일의 파일(데이터) 요청 상태 플래그를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                                              |
| :---- | ------- | -------------------------------------------------------------- |
| state | boolean | 파일 요청 상태(true: 요청 중/요청 필요, false: 요청 완료/불필요). |

-   Return
    -   true: 설정 성공.
    -   false: 타일이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
tile.setFileRequestState(false);
```

{% endtab %}
{% endtabs %}
