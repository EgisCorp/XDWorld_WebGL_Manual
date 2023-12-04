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

### createGrid(options) → error

> 그리드 객체 생성.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ---- | -------- |
| options | [JSFlowPolygon.GridDataOption](jsflowpolygon.md#jsflowpolygon.griddataoption) | 그리드 정보 설정값.   |

* Return
  * "result" 속성이 추가된 object : 객체 생성 성공.
  * "error" 속성이 추가된 object : 객체 생성 실패.
    * options에 "vertex" 속성이 없을 경우.
    * options에 "index" 속성이 없을 경우.
    * options에 "normaltexture" 속성이 없거나 해당 텍스처 이미지가 유효하지 않을 경우.
    * 그리드 객체 생성에 실패했을 경우.
    * "waterlevel" 속성 설정에 실패했을 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### createWall(options) → error

> 수직 벽면 폴리곤 객체 생성.
>
> options 변수로 객체 설정.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Description |
| --------- | ---- | -------- |
| options | [JSFlowPolygon.WallDataOption](jsflowpolygon.md#jsflowpolygon.walldataoption) | 벽면 정보 설정값.   |

* Return
  * "result" 속성이 추가된 object : 객체 생성 성공.
  * "error" 속성이 추가된 object : 객체 생성 실패.
    * options에 "vertex" 속성이 없을 경우.
    * options에 "normaltexture" 속성이 없거나 해당 텍스처 이미지가 유효하지 않을 경우.
{% endtab %}

{% tab title="Template" %}
```javascript
```
{% endtab %}
{% endtabs %}

### setCullMode(type) → boolean

> 수직 벽면 폴리곤 컬링 옵션 설정.
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

#### JSFlowPolygon.GridDataOption

> 그리드 정보 파라메터.

| Name | Type | Attributes | Default | Description |
| --- | --- | --- | --- | --- |
| vertex | array(JSVector3D) |  |  | 그리드를 이루는 점들의 좌표 목록. |
| index | array(number) |  |  | 그리드를 이루는 점들의 인덱스 좌표 목록. |
| normaltexture | JSIcon |            |         | 재질 노말 텍스처. |
| flowtexture | JSIcon | optional |         | flow map(텍스처 직접 전달). |
| flowpath | 2차원 array(JSVector2D) | optional |         | flow map(path 전달). |
| imagetexture | JSIcon | optional |         | 표면 이미지 텍스처. |
| waterlevel | number | optional | 0.0 | 수위. |
| positionoffset | [JSFlowPolygon.positionOffset](jsflowpolygon.md#jsflowpolygon.positionoffset) | optional | (0.0, 0.0, 0.0) | 위치 offset. |

#### JSFlowPolygon.WallDataOption

> 벽면 정보 파라메터.

| Name | Type | Attributes | Default | Description |
| --- | --- | --- | --- | --- |
| vertex | array(JSVector3D) |  |  | 벽면을 이루는 점들의 좌표 목록. |
| normaltexture | JSIcon |            |         | 재질 노말 텍스처. |
| imagetexture | JSIcon | optional |         | 표면 이미지 텍스처. |
| height | number | optional | 10.0 | 벽 높이. |
| positionoffset | [JSFlowPolygon.positionOffset](jsflowpolygon.md#jsflowpolygon.positionoffset) | optional | (0.0, 0.0, 0.0) | 위치 offset. |

#### JSFlowPolygon.positionOffset
| Name | Type | Default | Description |
| --- | --- | --- | --- | --- |
| longitude | number | 0.0 | 경도. |
| latitude | number | 0.0 | 위도. |
| altitude | number | 0.0 | 고도. |
