---
description: 라인 오브젝트 설정 및 반환 API를 제공합니다.
---

# JSLineString

Module createLineString API로 생성할 수 있습니다.

```text
var object = Module.createLineString("newObject");
```

## createbyJson\(object options\) → string
> 지정한 옵션으로 라인을 생성합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| options | object | 라인 생성 옵션 |
* Detail
  * options : 라인을 생성하는 옵션 정보 객체.
    - style (string) : 라인 버텍스 배열 포맷. style 속성에 맞춰 coordinates 배열 포맷을 맞춰 입력합니다.
        - style="XY" → [[x, y], [x, y], ...]
        - style="XYZ" → [[x, y, z], [x, y, z], ...]
        - style="XYZARRAY" → [x, y, z, x, y, z], ...]
        - style="JSVector3D" → [JSVector3D, JSVector3D, ...]
    - coordinates : 라인 구성 버텍스. 포맷은 style 속성에 맞춰 적용합니다.
    - union (boolean) : 지형 결합 (RTT) 설정
    - depth (boolean) : Depth 설정
    - type (number) : 라인 타입
        - 0 : 일반 실선
        - 3 : 화살표
        - 4 : 점선
        - 5 : 애니메이션 라인
    - skip (number) : 애니메이션 라인 적용시, 스킵할 버텍스 단위를 설정합니다. 값이 커질수록 건너뛰는 버텍스 수가 많아지므로 애니메이션 속도가 빨라집니다.
    - width (number) : 라인 두께
    - dash (number) : 점선 간격
    - speed (number) : 애니메이션 속도
    - color ([JSColor[](JSColor.md)) : 라인 색상
* Return
  * 성공 : "success"
  * 실패
    - "error map load" : 오브젝트가 초기화 되지 않음
    - "error variable undefined NULL" : options 객체가 없음
    - 이 외 오류 원인을 포함한 에러 메시지
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_Json
{% endtab %}
{% endtabs %}

## setCoordinates\([Collection](Collection.md) vertex_list\)
> 라인 좌표\(vertex, part, uv\)를 지정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| vertex_list | [Collection](Collection.md) | 폴리곤 Vertex\(경도, 위도, 고도\) 리스트 |
* Detail
  * vertex_list : 버텍스 수는 중복된 위치 없이 3점 이상 입력합니다.
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance
{% endtab %}
{% endtabs %}

## SetDashType\(number dash_size\) → boolean
> 라인이 지정한 간격의 점선이 되도록 설정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| dash_size | number | 점선 간격 |
* Return
  * 성공 : true
  * 실패 : false
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_Json
{% endtab %}
{% endtabs %}

## setPartCoordinates\([JSVec3Array](JSVec3Array.md) vertex_list, [Collection](Collection.md) part_list\)
> 라인 좌표\(vertex, part\)를 지정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| vertex_list | [JSVec3Array](JSVec3Array.md) | 라인 Vertex\(경도, 위도, 고도\) 리스트 |
| part_list | [Collection](Collection.md) | 라인 Part 리스트 |
* Detail
  * part_list : 파트를 이루는 버텍스 갯수의 리스트를 입력합니다.
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_buffering
{% endtab %}
{% endtabs %}

## setStyle\([JSPolyLineStyle](JSPolyLineStyle.md) style\)
> 텍스쳐 uv를 포함한 폴리곤 좌표\(vertex, part, uv\)를 지정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| style | [JSPolyLineStyle](JSPolyLineStyle.md) | 라인 스타일 설정 객체 |
* Detail
  * 설정 가능한 스타일
    - 라인 색상, 투명도
    - 라인 두께
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=object_line_buffering
{% endtab %}
{% endtabs %}

## setUnionMode\(boolean is_union)
> 라인 지형 결합 (RTT) 여부를 설정합니다.
{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| boolean | is_union | 라인 지형 결합 (RTT) 여부 |
* Code
  * http://sandbox.dtwincloud.com/code/main.do?id=analysis_line_path_distance
{% endtab %}
{% endtabs %}