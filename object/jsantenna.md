---
description: 지도 내 전파 범위 3차원 모델 객체를 생성 및 설정하기 위한 API 입니다.
---

# JSAntenna

> Module.CreateAntenna() API를 생성합니다.

```javascript
var object = Module.CreateAntenna("ID");
```

## Function

### CreateCoverageCone(position, height, radius, angle, x, segment) → boolean

> 전파 범위 3차원 모델 객체를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                                | Description                                           |
| :------- | :---------------------------------- | :---------------------------------------------------- |
| position | [JSVector3D](../core/jsvector3d.md) | 전파 시작 경위도.                                     |
| height   | number                              | 전파 시작 경위도에서 전파 모델링 높이 설정.           |
| radius   | number                              | 전파 모델링 반경 설정(radius>0 입력).                 |
| angle    | number                              | 전파 모델링 파형 각도 설정(angle>-90, angle<90 입력). |
| x        | number                              | 전파 모델링 파형 화각 너비 설정.                      |
| segment  | number                              | 전파 모델링 정밀도 설정(segment>3 입력).              |

-   Return
    -   true : 생성 성공.
    -   false : 생성 실패.
    -   실패 조건.
        -   effect_radius \< 0 값이 설졍 된 경우.
        -   effect_angle \< -90, effect_angle \> 90 값이 설정된 경우.
        -   effect_radius \< 3 값이 설졍 된 경우.
-   Sample
    -   the create function 참조.
    -   [Sandbox_Radio Coverage](https://sandbox.egiscloud.com/code/main.do?id=object_antenna)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### CreateCoverageCylinder(position, height, radius, roundSegment) → boolean

> 전파 범위를 원통(Cylinder) 형태의 3차원 모델로 생성합니다. 지형과의 충돌 검사는 수행하지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                | Description                                  |
| :---------- | :---------------------------------- | :-------------------------------------------- |
| position    | [JSVector3D](../core/jsvector3d.md) | 전파 시작 경위도.                             |
| height      | number                              | 전파 모델링 높이 설정.                        |
| radius      | number                              | 전파 모델링 반경 설정.                        |
| roundSegment| number                              | 원통 둘레 정밀도 설정(roundSegment>=3 입력).  |

-   Return
    -   true : 생성 성공.
    -   false : 생성 실패.
    -   실패 조건.
        -   roundSegment \< 3 값이 설정된 경우.
        -   height \< 0.001 값이 설정된 경우(내부적으로 heightInterval로 사용됨).

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### CreateCoverageCylinderWithCheckCollision(position, height, radius, roundSegment, heightInterval) → boolean

> 전파 범위를 원통(Cylinder) 형태의 3차원 모델로 생성합니다. `CreateCoverageCylinder`와 달리 지형(Planet)과의 충돌 검사를 수행하여 지형 굴곡에 맞춰 형태를 보정합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type                                | Description                                   |
| :----------- | :----------------------------------- | :--------------------------------------------- |
| position     | [JSVector3D](../core/jsvector3d.md)  | 전파 시작 경위도.                              |
| height       | number                               | 전파 모델링 높이 설정.                         |
| radius       | number                               | 전파 모델링 반경 설정.                         |
| roundSegment | number                               | 원통 둘레 정밀도 설정(roundSegment>=3 입력).   |
| heightInterval | number                              | 높이 방향 분할 간격 설정(heightInterval>0.001 입력). |

-   Return
    -   true : 생성 성공.
    -   false : 생성 실패.
    -   실패 조건.
        -   roundSegment \< 3 값이 설정된 경우.
        -   heightInterval \< 0.001 값이 설정된 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetAntenaScopeColor(faceType, color) → boolean

> 전파 범위(Coverage Cone) 모델의 특정 면(face)에 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type                          | Description                                                     |
| :------- | :----------------------------- | :---------------------------------------------------------------- |
| faceType | number                         | 색상을 지정할 면 종류(0: yFOV top, 1: yFOV gap, 2: yFOV bottom). |
| color    | [JSColor](../core/jscolor.md)  | 설정할 색상.                                                     |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건.
        -   `CreateCoverageCone`으로 생성된 Cone 모델이 없는 경우.
        -   faceType이 0보다 작거나 Cone의 면 개수보다 큰 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetAntenaPoleColor(color) → boolean

> 안테나 기둥(Pole) 모델의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                          | Description   |
| :---- | :----------------------------- | :------------- |
| color | [JSColor](../core/jscolor.md) | 설정할 색상.  |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건.
        -   안테나 기둥 모델이 생성되어 있지 않은 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetModel(model) → boolean

> 안테나 본체(기지국) 3차원 모델을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                                            | Description             |
| :---- | :------------------------------------------------ | :------------------------ |
| model | [JSGhostSymbol](jsghostsymbol.md)                | 안테나 본체로 사용할 모델 객체. |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건.
        -   model이 유효하지 않은(null) 객체인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetCoverageDepthTest(set) → boolean

> 전파 범위 원통(Cylinder) 모델의 Depth Test 사용 여부를 설정합니다. false로 설정 시 다른 객체에 가려지지 않고 항상 표시됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                                            |
| :--- | :------- | :------------------------------------------------------- |
| set  | boolean | true: Depth Test 사용.<br>false: Depth Test 미사용(항상 표시). |

-   Return
    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건.
        -   `CreateCoverageCylinder` 또는 `CreateCoverageCylinderWithCheckCollision`으로 생성된 원통 모델이 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

### SetCoverageDistance(radius) → boolean

> 전파 범위 모델 반경 변경.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description                             |
| :----- | :----- | :-------------------------------------- |
| radius | number | 전파 모델링 반경 설정(radius \> 0 입력) |

-   Return

    -   true : 설정 성공.
    -   false : 설정 실패.
    -   실패 조건
        -   radius \< 0 값이 설정된 경우.

-   Sample
    -   the SetCoverageDistance function 참조.
    -   [Sandbox_Radio Coverage](https://sandbox.egiscloud.com/code/main.do?id=object_antenna)

{% endtab %}
{% tab title="Template" %}

```javascript

```

{% endtab %}
{% endtabs %}

## Getter / Setter

### getDescription(), setDescription(desc) → string

> 객체에 대한 설명을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| desc | string | 설명 문자열. |

-   Return
    -   string: 객체 설명 문자열이 성공적으로 반환.
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var strDesc = object.getDescription();
// ... or ...
object.setDescription("First Object.");
```

{% endtab %}
{% endtabs %}

### getName(), setName(name) → string

> 객체 이름을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
| ---- | ------ | ----------- |
| name | string | 객체 이름.  |

-   Return
    -   string: 객체 이름을 성공적을 반환
    -   null: 객체가 null인 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setName("MyObject");
```

{% endtab %}
{% endtabs %}

### getVisible(), setVisible(visible) → boolean

> 객체의 가시화 유무를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                                        |
| ------- | ------- | -------------------------------------------------- |
| visible | boolean | <p>true: 객체 가시화.<br>false: 객체 비가시화.</p> |

-   Return
    -   true: 객체 가시화 상태.
    -   false: 객체 비가시화 상태.

{% endtab %}
{% tab title="Template" %}

```javascript
var objName = object.getName();
// ... or ...
object.setVisible(true);
```

{% endtab %}
{% endtabs %}
