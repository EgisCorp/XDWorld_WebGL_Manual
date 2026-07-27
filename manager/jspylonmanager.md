---
description: 송전탑(철탑)과 전선(Wire)을 생성 및 관리하기 위한 API 입니다.
---

# JSPylonManager

> Module.JSPylonManager() API를 생성합니다.
>
> 철탑(Pylon) 객체 목록 구성, 전선(Wire) 연결, 철탑 부속 구조물, 울타리(Fence) 등을 생성하는 전력 설비 특화 기능을 제공합니다. 대부분의 API에서 좌표/좌표 목록은 콤마(,)와 샵(#)으로 구분된 문자열로 주고받습니다.

```javascript
var pylonManager = new Module.JSPylonManager();
```

## Function

### refSetPos(x, y, z)

> 이후 [pylonAddToList()](jspylonmanager.md#pylonaddtolistkey-volt-type-height-ajindex-pipe-label-boolean), [pylonAddStructure()](jspylonmanager.md#pylonaddstructurelayername-key-upper-boolean)로 생성할 철탑/구조물에 적용할 기준 좌표를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| :--- | :----- | ----------------- |
| x    | number | 경도(degrees).     |
| y    | number | 위도(degrees).     |
| z    | number | 고도(meters).      |

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.refSetPos(127.0, 37.5, 50.0);
```

{% endtab %}
{% endtabs %}

### refSetColor(alpha, red, green, blue)

> 이후 생성할 철탑/전선/울타리에 적용할 기준(주) 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| :---- | :----- | ---------------------- |
| alpha | number | 투명도(0~255).         |
| red   | number | 색상 R 값(0~255).      |
| green | number | 색상 G 값(0~255).      |
| blue  | number | 색상 B 값(0~255).      |

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.refSetColor(255, 200, 200, 200);
```

{% endtab %}
{% endtabs %}

### refSetSecondColor(alpha, red, green, blue)

> 이후 생성할 철탑/전선/울타리에 적용할 보조(2차) 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| :---- | :----- | ---------------------- |
| alpha | number | 투명도(0~255).         |
| red   | number | 색상 R 값(0~255).      |
| green | number | 색상 G 값(0~255).      |
| blue  | number | 색상 B 값(0~255).      |

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.refSetSecondColor(255, 150, 150, 150);
```

{% endtab %}
{% endtabs %}

### pylonListClear()

> 철탑 생성 목록(대기열)을 초기화합니다.

{% tabs %}
{% tab title="Information" %}

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.pylonListClear();
```

{% endtab %}
{% endtabs %}

### pylonAddToList(key, volt, type, height, ajIndex, pipe, label) → boolean

> 철탑 생성 목록에 철탑 정보를 추가합니다.
>
> [refSetPos()](jspylonmanager.md#refsetposx-y-z), [refSetColor()](jspylonmanager.md#refsetcoloralpha-red-green-blue), [refSetSecondColor()](jspylonmanager.md#refsetsecondcoloralpha-red-green-blue)로 설정된 값을 기준으로 추가되며, 실제 생성은 [pylonBuildPylonList()](jspylonmanager.md#pylonbuildpylonlistlayername-boolean) 호출 시 이루어집니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                      |
| :------ | ------- | -------------------------------------- |
| key     | string  | 철탑 고유 명칭.                        |
| volt    | string  | 전압 종류(철탑 형태 결정에 사용).       |
| type    | string  | 철탑 타입 문자열.                       |
| height  | number  | 철탑 높이.                             |
| ajIndex | number  | 애자(절연체) 배치 인덱스.               |
| pipe    | boolean | 파이프 형태 여부.                       |
| label   | string  | 철탑 라벨 문자열.                       |

-   Return
    -   true: 추가 성공.
    -   false: 추가 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.refSetPos(127.0, 37.5, 0.0);
pylonManager.refSetColor(255, 200, 200, 200);
pylonManager.pylonAddToList("Pylon_1", "154kV", "type1", 30.0, 0, false, "1호");
```

{% endtab %}
{% endtabs %}

### pylonBuildPylonList(layerName) → boolean

> [pylonAddToList()](jspylonmanager.md#pylonaddtolistkey-volt-type-height-ajindex-pipe-label-boolean)로 추가된 철탑 목록을 실제로 지정한 레이어에 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| :-------- | :----- | ---------------------- |
| layerName | string | 생성 대상 레이어 명칭. |

-   Return
    -   true: 생성 성공.
    -   false: 월드/맵이 초기화되지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.pylonBuildPylonList("PylonLayer");
```

{% endtab %}
{% endtabs %}

### pylonBuildWire(layerName, wireKey, pylonKey1, pylonKey2, param, option) → boolean

> 두 철탑 사이를 연결하는 전선(Wire) 객체를 편집 레이어에 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                    |
| :-------- | ------ | ----------------------------------- |
| layerName | string | 대상 철탑이 속한 레이어 명칭.       |
| wireKey   | string | 생성할 전선 객체 고유 명칭.         |
| pylonKey1 | string | 시작 철탑 객체 키.                  |
| pylonKey2 | string | 끝 철탑 객체 키.                    |
| param     | number | 전선 처짐/형태 파라미터.            |
| option    | number | 추가 옵션 값(현재 내부적으로 미사용). |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   레이어가 없거나, pylonKey1/pylonKey2에 해당하는 객체가 없는 경우.
        -   두 객체가 철탑(Pylon) 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.pylonBuildWire("PylonLayer", "Wire_1", "Pylon_1", "Pylon_2", 0, 0);
```

{% endtab %}
{% endtabs %}

### pylonCreateOneWire(layerName, wireKey, pylonKey1, left1, part1, seq1, pylonKey2, left2, part2, seq2, param) → boolean

> 철탑의 특정 애자(절연체) 위치를 지정하여 두 철탑 사이에 전선 한 가닥을 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                              |
| :-------- | ------ | -------------------------------------------------------------- |
| layerName | string | 대상 철탑이 속한 레이어 명칭.                                  |
| wireKey   | string | 생성할 전선 객체 고유 명칭(이미 존재하면 실패).                |
| pylonKey1 | string | 시작 철탑 객체 키.                                             |
| left1     | number | 시작 철탑 좌/우 구분(1: 좌, 그 외: 우).                         |
| part1     | number | 시작 철탑 배치 파트 번호.                                       |
| seq1      | string | 시작 철탑 회선 구분 문자열("GR": 지상선, 그 외: 상별 코드).     |
| pylonKey2 | string | 끝 철탑 객체 키.                                               |
| left2     | number | 끝 철탑 좌/우 구분(1: 좌, 그 외: 우).                           |
| part2     | number | 끝 철탑 배치 파트 번호.                                         |
| seq2      | string | 끝 철탑 회선 구분 문자열.                                       |
| param     | number | 전선 처짐/형태 파라미터.                                        |

-   Return
    -   true: 생성 성공(seq1, seq2가 모두 "GR"이 아닌 경우).
    -   false: 대상 레이어/철탑을 찾지 못했거나, wireKey가 이미 존재하는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.pylonCreateOneWire("PylonLayer", "Wire_1a", "Pylon_1", 1, 0, "A1", "Pylon_2", 1, 0, "A1", 0);
```

{% endtab %}
{% endtabs %}

### pylonCreateFence(objectKey, pointInfo, height) → boolean

> 다각형 좌표 정보를 기반으로 울타리(펜스) 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                                                                  |
| :-------- | ------ | -------------------------------------------------------------------------------------------------- |
| objectKey | string | 생성할 울타리 객체 고유 명칭(이미 존재하면 실패).                                                  |
| pointInfo | string | 좌표 문자열. 파트는 `#`으로, 좌표는 `,`로 구분(`lon,lat,alt,lon,lat,alt,...#lon,lat,alt,...`).       |
| height    | number | 울타리 높이.                                                                                        |

-   Return
    -   true: 생성 성공.
    -   false: 생성 실패.
    -   실패 조건
        -   pointInfo가 비어있는 경우.
        -   objectKey가 이미 존재하는 경우.
        -   내부 폴리곤 울타리 생성에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.pylonCreateFence("Fence_1", "127.0,37.5,0,127.001,37.5,0,127.001,37.501,0", 3.0);
```

{% endtab %}
{% endtabs %}

### pylonGetWirePointNum(layerName, pylonKey) → number

> 철탑에 배치된 애자(절연체) 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| :-------- | ------ | ---------------------- |
| layerName | string | 대상 레이어 명칭.       |
| pylonKey  | string | 철탑 객체 키.           |

-   Return
    -   number: 애자 개수.
    -   0: 레이어/객체를 찾지 못했거나 철탑 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = pylonManager.pylonGetWirePointNum("PylonLayer", "Pylon_1");
```

{% endtab %}
{% endtabs %}

### pylonGetHeight(layerName, pylonKey) → number

> 철탑의 높이를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| :-------- | ------ | ---------------------- |
| layerName | string | 대상 레이어 명칭.       |
| pylonKey  | string | 철탑 객체 키.           |

-   Return
    -   number: 철탑 높이(meters).
    -   0.0: 레이어/객체를 찾지 못했거나 철탑 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var height = pylonManager.pylonGetHeight("PylonLayer", "Pylon_1");
```

{% endtab %}
{% endtabs %}

### pylonGetWirePoints(layerName, pylonKeyA, indexA, pylonKeyB, indexB, param) → string

> 두 철탑의 지정한 애자 인덱스 사이를 잇는 전선의 좌표 목록을 계산하여 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                          |
| :-------- | ------ | ------------------------------------------ |
| layerName | string | 대상 레이어 명칭.                            |
| pylonKeyA | string | 시작 철탑 객체 키.                           |
| indexA    | number | 시작 철탑 애자 인덱스.                       |
| pylonKeyB | string | 끝 철탑 객체 키.                             |
| indexB    | number | 끝 철탑 애자 인덱스.                         |
| param     | number | 전선 처짐/형태 파라미터.                     |

-   Return
    -   string: `lon,lat,alt,lon,lat,alt,...` 형식의 좌표 목록 문자열.
    -   "": 레이어/객체를 찾지 못했거나 철탑 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var points = pylonManager.pylonGetWirePoints("PylonLayer", "Pylon_1", 0, "Pylon_2", 0, 0);
```

{% endtab %}
{% endtabs %}

### pylonGetAejaCount(layerName, objectKey) → number

> 철탑에 배치된 애자(절연체) 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| :-------- | ------ | ---------------------- |
| layerName | string | 대상 레이어 명칭.       |
| objectKey | string | 철탑 객체 키.           |

-   Return
    -   number: 애자 개수.
    -   0: 레이어/객체를 찾지 못했거나 철탑 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var count = pylonManager.pylonGetAejaCount("PylonLayer", "Pylon_1");
```

{% endtab %}
{% endtabs %}

### pylonGetAejaPos(layerName, objectKey, index) → string

> 철탑의 지정한 애자(절연체) 위치 좌표를 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| :-------- | ------ | ---------------------- |
| layerName | string | 대상 레이어 명칭.       |
| objectKey | string | 철탑 객체 키.           |
| index     | number | 조회할 애자 인덱스.     |

-   Return
    -   string: `lon,lat,alt` 형식의 좌표 문자열.
    -   "": 레이어/객체를 찾지 못했거나, 철탑 타입이 아니거나, index가 범위를 벗어난 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var pos = pylonManager.pylonGetAejaPos("PylonLayer", "Pylon_1", 0);
```

{% endtab %}
{% endtabs %}

### pylonAddStructure(layerName, key, upper) → boolean

> [refSetPos()](jspylonmanager.md#refsetposx-y-z), [refSetColor()](jspylonmanager.md#refsetcoloralpha-red-green-blue)로 설정된 위치/색상을 기준으로 철탑 부속 구조물을 추가합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description                              |
| :-------- | ------- | ---------------------------------------------- |
| layerName | string  | 대상 레이어 명칭(현재 구현상 직접 사용되지는 않음). |
| key       | string  | 구조물 고유 명칭.                               |
| upper     | boolean | 상부 구조물 여부.                               |

-   Return
    -   true: 추가 성공.
    -   false: 추가 실패.

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.refSetPos(127.0, 37.5, 30.0);
pylonManager.refSetColor(255, 200, 200, 200);
pylonManager.pylonAddStructure("PylonLayer", "Structure_1", true);
```

{% endtab %}
{% endtabs %}

### getLineBufferPoints(pointCount, pointArray, segment, radius) → string

> 입력 좌표(경로)를 기준으로 지정한 반경만큼 버퍼링(폭 확장)된 폴리곤 좌표를 계산하여 반환합니다. 계산된 좌표의 고도는 지형 고도로 자동 보정됩니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                                                     |
| :--------- | ------ | ---------------------------------------------------------------------- |
| pointCount | number | 입력 좌표 개수.                                                        |
| pointArray | string | 입력 좌표 문자열(`lon,lat,alt,lon,lat,alt,...`).                        |
| segment    | number | 버퍼 모서리 처리 세그먼트 수.                                          |
| radius     | number | 버퍼링 반경.                                                            |

-   Return
    -   string: 버퍼링된 좌표 목록 문자열(파트는 `#`, 좌표는 `,`로 구분).
    -   "": 입력 좌표 문자열이 비어있는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var buffered = pylonManager.getLineBufferPoints(3, "127.0,37.5,0,127.001,37.5,0,127.002,37.501,0", 8, 10.0);
```

{% endtab %}
{% endtabs %}

### getTowerBox(layerName, objectKey) → array

> 철탑 객체의 바운딩 박스를 구성하는 8개 꼭짓점 좌표 배열을 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description       |
| :-------- | ------ | ---------------------- |
| layerName | string | 대상 레이어 명칭.       |
| objectKey | string | 철탑 객체 키.           |

-   Return
    -   array(number): 8개 꼭짓점 좌표를 `[lon, lat, alt, lon, lat, alt, ...]` 순서로 이어붙인 배열(총 24개 값).
    -   null: 레이어/객체를 찾지 못했거나 철탑 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var box = pylonManager.getTowerBox("PylonLayer", "Pylon_1");
```

{% endtab %}
{% endtabs %}

### setPylonVisible(layerName, objectKey, visible) → boolean

> 철탑 객체 개별 가시화 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type    | Description                              |
| :-------- | ------- | ---------------------------------------------- |
| layerName | string  | 대상 레이어 명칭.                               |
| objectKey | string  | 철탑 객체 키.                                   |
| visible   | boolean | <p>true: 가시화.<br>false: 비가시화.</p>       |

-   Return
    -   true: 설정 성공.
    -   false: 레이어/객체를 찾지 못했거나 철탑 타입이 아닌 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.setPylonVisible("PylonLayer", "Pylon_1", false);
```

{% endtab %}
{% endtabs %}

### setPreBuildPylonAngle(key, angle) → boolean

> [pylonBuildPylonList()](jspylonmanager.md#pylonbuildpylonlistlayername-boolean)로 생성되기 전 철탑의 회전 각도를 수동으로 지정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description       |
| :---- | ------ | ---------------------- |
| key   | string | 철탑 고유 명칭.         |
| angle | number | 회전 각도(degrees).    |

-   Return
    -   true: 설정 성공.
    -   false: 설정 실패(대상 키를 찾지 못한 경우).

{% endtab %}
{% tab title="Template" %}

```javascript
pylonManager.setPreBuildPylonAngle("Pylon_1", 45.0);
```

{% endtab %}
{% endtabs %}
