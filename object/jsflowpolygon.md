---
description: 물 흐름 효과 폴리곤 객체 생성 및 수정 기능 API.
---

# JSFlowPolygon

> Module.createFlowPolygon API 생성.
> 생성 후 JSFlowPolygon.create API를 사용하여 초기화.
> 
> [샌드박스_JSFlowPolygon(물 흐름 효과)](https://sandbox.dtwincloud.com/code/main.do?id=object_flowpolygon)

```javascript
let flowPolygon = Module.createFlowPolygon("flow");
// 매개변수 정보 생략.
flowPolygon.create({
    vertex : geometry,
    flowpath : flowPathList,
    normaltexture : _flowNoiseTexture,
    imagetextyre : _polygonImageTexture,
});
```

| 변수명    | 자료형    | 프로퍼티 역할 |
| ------ | ------ | ------- |
| vertex  | JSVec3Array | 폴리곤 형상. 별도로 로드하는 JSON 데이터에서 불러옴.      |
| flowpath | number | 흐름 방향. 별도로 로드하는 JSON 데이터에서 불러옴.     |
| normaltexture  | number | 강 흐름 노이즈 텍스쳐.      |
| imagetexture   | number | 강 표면 이미지 텍스쳐. |

## Properties

| Name                    | Type    | Description                                      |
| ----------------------- | ------- | ------------------------------------------------ |
| opacity           | number  | 투명도. |
| fluid_activity    | number  | 유체 출렁임 정도.             |
| flow_speed        | number  | 흐름 속도.        |
| image_type        | number  | 표면 이미지 표출 타입.<br>0일 경우 지정한 이미지로 표시.</br><br>1일 경우, 물 흐름 방향 범례를 색상으로 표시.</br><br>3일 경우, 지형 텍스처 버퍼로 표시.</br><br>그 외에는 color로 지정한 색상으로 표시.</br>                              |
| position_offset   | JSVector3D | 위치 추가 offset.                         |
| color             | JSColor  | 범례 색상 표시 모드일 경우, 색상 설정.                    |
| coordinates       | JSVec3Array  | 객체의 위치(get만 가능).             |

## Function

### setCullMode(type) → boolean

> 폴리곤 컬링 옵션 설정.
>
> type 입력 값에 따른 컬링 옵션은 0(양면), 1(양면), 2(CW) 3(CCW).
>
> 컬링 옵션 초기 설정 3.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ---- | -------- |
| type | number  | 폴리곤 컬링모드. |

* Return
  * true : 객체 옵션 설정 성공.
  * false : 객체 옵션 설정 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
polygon.setCullMode(3);
```
{% endtab %}
{% endtabs %}

### Type Definitions

#### JSFlow.FlowDataOption

> 바람 데이터 파라메터.

| Name   | Type                                                                             | Attributes | Default | Description |
| ------ | -------------------------------------------------------------------------------- | ---------- | ------- | ----------- |
| data   | [JSFlow.FlowDataOption.dataParam](jsflow.md#jsflow.flowdataoption.dataparam)     |            |         | 구성 데이터 필드   |
| option | [JSFlow.FlowDataOption.optionParam](jsflow.md#jsflow.flowdataoption.optionparam) | optional   |         | 초기 데이터 설정   |
| legend | [JSFlow.FlowDataOption.legendParam](jsflow.md#jsflow.flowdataoption.legendparam) | optional   |         | 범례 표현       |
