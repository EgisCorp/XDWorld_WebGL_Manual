---
description: 지도 내 시간 경과에 따라 회전하는 원기둥형 애니메이션 객체를 생성하기 위한 API 입니다.
---

# JSAnimationObject

> Module.createAnimationObject() API를 생성합니다.

```javascript
var object = Module.createAnimationObject("ID");
```

## Function

### createbyJson(option) → object

> JSON 형태의 파라미터로 애니메이션 객체(원기둥 형태)를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name             | Type                                | Description                                                    |
| :--------------- | ------------------------------------- | ------------------------------------------------------------------ |
| position         | [JSVector3D](../core/jsvector3d.md) | 중심 좌표(경도, 위도, 고도, 필수).                                |
| number           | number(optional, 기본값 0)          | 텍스처 매핑에 사용되는 번호(imagelist의 각 이미지 번호와 대응).   |
| type             | number(optional, 기본값 0)          | 애니메이션 타입.                                                  |
| segment          | number(optional, 기본값 36)         | 원기둥 둘레 분할 세그먼트 수(2 미만 입력 시 3으로 보정).          |
| color            | [JSColor](../core/jscolor.md)(optional, 기본값 흰색) | 이미지가 없을 때 사용할 색상.                        |
| image            | object(optional)                    | 단일 이미지 정보(그룹 이미지 파싱 규칙에 따름, number 위치에 매핑됨). |
| imagelist        | array(object)(optional)             | 다중 이미지 목록. 각 항목은 image와 동일한 형식에 `number` 필드를 포함.|

-   Return
    -   .result: API 성공 유무 상태(1: 성공, 0: 실패).
    -   .name: 동작 API 명칭("JSAnimationObject.createbyJson").
    -   .return: API 반환 정보(문자열: 실패 에러 코드).
    -   실패 조건
        -   월드가 로드되지 않은 경우.
        -   position이 없는 경우.
        -   내부 오브젝트 생성(AddTimeCylinderObject)에 실패한 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var object = Module.createAnimationObject("Anim_1");
var result = object.createbyJson({
    position: new Module.JSVector3D(127.0, 37.5, 50.0),
    type: 0,
    segment: 36,
    color: new Module.JSColor(255, 255, 255, 255)
});
```

{% endtab %}
{% endtabs %}
