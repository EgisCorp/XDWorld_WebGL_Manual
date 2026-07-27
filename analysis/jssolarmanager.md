---
description: 태양광 패널 배치 및 분석을 위한 JSSolarManager API 문서입니다.
---

# JSSolarManager

> 태양광 패널 배치, 설정, 분석 등을 위한 주요 인터페이스를 제공하는 클래스입니다. 건물 또는 지형 기반의 설치를 모두 지원하며, 다양한 파라미터 설정 및 결과 조회가 가능합니다.

## Methods

### setActive(isActive) → void

> 태양광 모듈 편집을 활성화 또는 비활성화합니다.

{% tabs %}
{% tab title="Information" %}
- Parameters
  - `isActive` (`boolean`): true 시 태양광 배치 활성화
{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setActive(true);
```
{% endtab %}
{% endtabs %}

### setModuleAngle(useDefault, angle) → void

> 태양광 패널의 각도를 설정합니다.

{% tabs %}
{% tab title="Information" %}
- Parameters
  - `useDefault` (`boolean`): 기본값 사용 여부
  - `angle` (`number`): 기울기 각도 (degrees)
{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setModuleAngle(true, 30.0);
```
{% endtab %}
{% endtabs %}

### setModuleImage(imageData, width, height) → boolean

> 사용자 정의 이미지를 태양광 패널 텍스처로 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type        | Description                 |
|------------|-------------|-----------------------------|
| imageData  | array       | 이미지 픽셀 데이터 (RGBA).   |
| width      | number      | 이미지의 너비 (pixels).     |
| height     | number      | 이미지의 높이 (pixels).     |

- Return  
  - true: 설정 성공.  
  - false: 설정 실패.  
  - 실패 조건  
    - imageData가 null이거나 비어 있는 경우  
    - width 또는 height가 0 이하인 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let image = new Uint8Array([
  255, 0, 0, 255,     // 빨강
  0, 255, 0, 255,     // 초록
  0, 0, 255, 255,     // 파랑
  255, 255, 255, 255  // 흰색
]);
let result = Module.getSolar().setModuleImage(image, 2, 2);
```
{% endtab %}
{% endtabs %}

### setProviderMode(isProvider) → void

> 태양광 Provider Mode를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type    | Description                          |
|-------------|---------|--------------------------------------|
| isProvider  | boolean | true: 공급자 모드, false: 소비자 모드 |

- Return  
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setProviderMode(true);
```
{% endtab %}
{% endtabs %}

### setModuleMargin(include, exclude, moduleSide, moduleTopDown, arraySide, arrayTopDown) → void

> 태양광 모듈 및 어레이 배치 간격을 설정합니다.  
> 음수 값은 자동으로 0으로 처리됩니다.

{% tabs %}
{% tab title="Information" %}

| Name           | Type    | Description                             |
|----------------|---------|-----------------------------------------|
| include        | number  | 전체 배치 경계 포함 여백 (meters)       |
| exclude        | number  | 전체 배치 경계 제외 여백 (meters)       |
| moduleSide     | number  | 모듈 간 좌우 간격 (meters)              |
| moduleTopDown  | number  | 모듈 간 상하 간격 (meters)              |
| arraySide      | number  | 어레이 간 좌우 간격 (meters)            |
| arrayTopDown   | number  | 어레이 간 상하 간격 (meters)            |

- Return  
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setModuleMargin(1.0, 0.5, 0.1, 0.1, 0.2, 0.2);
```
{% endtab %}
{% endtabs %}

### setDownScale(enable, length) → void

> 태양광 모듈 배치 시 일정 길이 간격으로 스케일 조정 기능을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description                            |
|---------|---------|----------------------------------------|
| enable  | boolean | true 시 다운스케일 기능 활성화         |
| length  | number  | 스케일 조정 기준 길이 (양수, meters 단위) |

- Return  
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setDownScale(true, 3.0);
```
{% endtab %}
{% endtabs %}

### getModuleCount() → number

> 현재 활성화된 객체 내에 배치된 태양광 모듈의 총 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return  
  - `number`: 배치된 모듈 수  
  - `0`: 유효한 객체가 없거나 모듈이 배치되지 않은 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let count = Module.getSolar().getModuleCount();
```
{% endtab %}
{% endtabs %}

### setSouthDeploy(enable) → void

> 남향 일괄 배치를 설정합니다. 해당 설정이 활성화되면 하나의 섹션으로 모든 모듈이 남향으로 배치됩니다.

{% tabs %}
{% tab title="Information" %}

- Parameters
  - `enable` (`boolean`): true 시 남향 일괄 배치 적용

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setSouthDeploy(true);
```
{% endtab %}
{% endtabs %}

### clearPreview() → void

> 모든 태양광 패널의 미리보기 상태를 초기화합니다.  
> `m_bPreview` 값이 false로 설정되어, 화면에서 미리보기 모듈이 제거됩니다.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getSolar().clearPreview();
```
{% endtab %}
{% endtabs %}

### selectRoofByObject(layerName, objectKey) → boolean

> 지정한 레이어와 객체 키를 기반으로 해당 지붕을 선택합니다.  
> 선택된 지붕 정보는 이후 태양광 패널 배치 등의 작업에 사용됩니다.

{% tabs %}
{% tab title="Information" %}

- Parameters
  - `layerName` (`string`): 대상 객체가 속한 레이어 이름
  - `objectKey` (`string`): 대상 객체의 고유 키

- Return
  - `true`: 지붕 선택 성공
  - `false`: 지붕 선택 실패

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().selectRoofByObject("building_layer", "object_001");
```
{% endtab %}
{% endtabs %}

### getAreaPointsOnTerrain() → JSVec3Array

> 지형에 설정된 태양광 설치 영역의 경계 좌표들을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `JSVec3Array`: 지형에 지정된 영역의 3D 좌표 배열

{% endtab %}
{% tab title="Template" %}
```javascript
let areaPoints = Module.getSolar().getAreaPointsOnTerrain();
```
{% endtab %}
{% endtabs %}

### getModuleSetWidthGapOnTerrain() → number

> 지형에 배치된 태양광 모듈 배열 간의 가로 간격(m)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 모듈 배열 간 가로 간격 (meters)

{% endtab %}
{% tab title="Template" %}
```javascript
let widthGap = Module.getSolar().getModuleSetWidthGapOnTerrain();
```
{% endtab %}
{% endtabs %}

### getModuleSetHeightGapOnTerrain() → number

> 지형에 배치된 태양광 모듈 배열 간의 세로 간격(m)을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 모듈 배열 간 세로 간격 (meters)

{% endtab %}
{% tab title="Template" %}
```javascript
let heightGap = Module.getSolar().getModuleSetHeightGapOnTerrain();
```
{% endtab %}
{% endtabs %}

### setDirectionOfModuleOnTerrain(isSpecific, direction) → void

> 지형에 배치된 태양광 모듈의 방향 각도를 설정합니다.  
> `_isSpecific`이 true인 경우 입력한 각도(`direction`)를 적용하며, false인 경우 자동 방향을 사용합니다.

{% tabs %}
{% tab title="Information" %}

- Parameters
  - `isSpecific` (`boolean`): true 시 사용자가 지정한 각도를 적용
  - `direction` (`number`): 모듈 설치 방향 각도 (0~360도, degrees)

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setDirectionOfModuleOnTerrain(true, 180.0);
```
{% endtab %}
{% endtabs %}

### rebuildModuleOnTerrain() → void

> 지형에 배치된 태양광 모듈을 현재 설정값에 따라 다시 배치합니다.  
> 방향, 간격, 여백 등의 변경사항이 반영됩니다.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getSolar().rebuildModuleOnTerrain();
```
{% endtab %}
{% endtabs %}

### setModuleSetWidthGapOnTerrain(gap) → void

> 지형에 배치되는 태양광 모듈 세트 간의 가로 간격을 설정합니다.

{% tabs %}
{% tab title="Information" %}

- Parameters
  - `gap` (`number`): 세트 간 가로 간격 (meters). 0보다 작은 값은 자동으로 0으로 보정됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setModuleSetWidthGapOnTerrain(1.5);
```
{% endtab %}
{% endtabs %}

### setModuleSetHeightGapOnTerrain(gap) → void

> 지형에 배치되는 태양광 모듈 세트 간의 세로 간격을 설정합니다.

{% tabs %}
{% tab title="Information" %}

- Parameters
  - `gap` (`number`): 세트 간 세로 간격 (meters). 0보다 작은 값은 자동으로 0으로 보정됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setModuleSetHeightGapOnTerrain(1.0);
```
{% endtab %}
{% endtabs %}

### getAlignAreaAngleOnTerrain() → number

> 지형에 설정된 배치 영역의 정렬 각도를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 정렬 각도 (degrees 단위). 0 ~ 360 사이의 값이 반환됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
let angle = Module.getSolar().getAlignAreaAngleOnTerrain();
```
{% endtab %}
{% endtabs %}

### getCenterOfMassOnTerrain() → [CJSVector3D](../core/jsvector3d.md)

> 지형 위에 배치된 태양광 패널의 질량 중심 위치를 반환합니다.
>
> 반환되는 값은 경도, 위도, 고도 순서의 좌표입니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - [`CJSVector3D`](../core/jsvector3d.md): 질량 중심 위치 (longitude, latitude, altitude)

{% endtab %}
{% tab title="Template" %}
```javascript
let center = Module.getSolar().getCenterOfMassOnTerrain();
console.log(center.lon, center.lat, center.alt);
```
{% endtab %}
{% endtabs %}

### getTerrainModuleCount() → number

> 지형에 설치된 태양광 모듈의 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 설치된 모듈 수

{% endtab %}
{% tab title="Template" %}
```javascript
let count = Module.getSolar().getTerrainModuleCount();
console.log("Terrain Module Count:", count);
```
{% endtab %}
{% endtabs %}

### clearModuleOnTerrain() → void

> 지형에 설치된 모든 태양광 모듈을 제거합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().clearModuleOnTerrain();
```
{% endtab %}
{% endtabs %}

### getLayerPannelInfo(layerName) → string

> 지정한 레이어 내 태양광 패널 객체들의 정보를 JSON 문자열 형태로 반환합니다.  
> 패널 위치(위도/경도/고도), 크기, 방향, 각도 등의 상세 정보가 포함됩니다.

{% tabs %}
{% tab title="Information" %}

- Parameters
  - `layerName` (`string`): 대상 레이어 이름

- Return
  - `string`: JSON 문자열
    ```json
    [
      {
        "Pos": [경도, 위도, 고도],
        "MWidth": 패널가로길이,
        "MHeight": 패널세로길이,
        "Thickness": 패널두께,
        "MAngle": 수직각,
        "MDirection": 방향각
      },
      ...
    ]
    ```

{% endtab %}
{% tab title="Template" %}
```javascript
let jsonInfo = Module.getSolar().getLayerPannelInfo("BuildingLayer");
let data = JSON.parse(jsonInfo);
console.log(data);
```
{% endtab %}
{% endtabs %}

### SetModuleArray(nSection, nSectionCount, nSectionSet) → boolean

> 태양광 모듈의 배열 구성 정보를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name           | Type  | Description |
|----------------|-------|-------------|
| nSection       | int   | 단일 배열당 섹션 수 |
| nSectionCount  | int   | 배열 전체의 섹션 개수 |
| nSectionSet    | int   | 배열 세트 수 |

- Return  
  - `true`: 설정 성공 및 모듈 재배치 완료  
  - `false`: 설정 실패 (엔진 미초기화 또는 내부 오류)

- Description  
  - 태양광 시스템 내 모듈 배열 구성을 설정합니다.  

{% endtab %}
{% tab title="Template" %}

```javascript
var API = {
    JSSolarManager : Module.getSolarManager()
};

// 예: 각 배열당 5개 섹션, 섹션 총 20개, 세트 2개 구성
var result = API.JSSolarManager.SetModuleArray(5, 20, 2);

if (!result) {
    console.error("모듈 배열 설정 실패");
}
```
{% endtab %}
{% endtabs %}

### saveEditModule(save) → void

> 지붕 모듈 편집 결과를 저장할지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description               |
|-------|---------|---------------------------|
| save  | boolean | true 시 편집한 모듈 저장 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().saveEditModule(true);
```
{% endtab %}
{% endtabs %}

### setEditMode(set) → void

> 태양광 지붕 편집 모드를 설정합니다. `setActive(true)`로 활성화된 상태에서만 적용되며, 마우스 상태를 이동/드래그(`MML_MOVE_GRAB`) 모드로 전환합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description             |
|------|---------|--------------------------|
| set  | boolean | true 시 편집 모드 활성화 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setActive(true);
Module.getSolar().setEditMode(true);
```
{% endtab %}
{% endtabs %}

### setSimpleMode(set) → void

> 태양광 모듈을 단순화된(Simple) 형태로 표시할지 여부를 설정합니다. `setActive(true)`로 활성화된 상태에서만 적용됩니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                 |
|------|---------|------------------------------|
| set  | boolean | true 시 단순 모드로 표시     |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setSimpleMode(true);
```
{% endtab %}
{% endtabs %}

### setEditStatus(status) → void

> 지붕 편집 상태(그리기 모드)를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description |
|--------|--------|--------------|
| status | number | 편집 상태 값. `SolarEditMode` 열거값 사용: `0`(SEM_NONE, 편집 없음), `1`(SEM_ADD_POLYGON, 다각형 영역 추가), `2`(SEM_ADD_RECT, 사각형 영역 추가), `3`(SEM_ADD_CIRCLE, 원형 영역 추가) |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
// 사각형 영역 추가 모드로 전환
Module.getSolar().setEditStatus(2);
```
{% endtab %}
{% endtabs %}

### setDrawRadiation(draw) → void

> 일사량 렌더링(음영/그라데이션 표시) 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description               |
|------|---------|----------------------------|
| draw | boolean | true 시 일사량 렌더링 활성화 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setDrawRadiation(true);
```
{% endtab %}
{% endtabs %}

### setSolarServer(url) → void

> 태양광 분석에 사용할 서버 주소를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description       |
|------|--------|--------------------|
| url  | string | 태양광 서버 URL   |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setSolarServer("http://106.255.249.50:8081");
```
{% endtab %}
{% endtabs %}

### setMaxRoofAngle(angle) → void

> 지붕으로 인식할 수 있는 최대 경사각을 설정합니다. 이 값보다 경사가 큰 면은 지붕으로 취급되지 않습니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
|-------|--------|---------------------|
| angle | number | 최대 지붕 각도 (degrees) |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setMaxRoofAngle(45.0);
```
{% endtab %}
{% endtabs %}

### setMaxSlopeAngle(angle) → void

> 경사 지붕으로 인식할 수 있는 최대 경사각을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description        |
|-------|--------|---------------------|
| angle | number | 최대 경사 각도 (degrees) |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setMaxSlopeAngle(30.0);
```
{% endtab %}
{% endtabs %}

### initialize() → void

> 태양광 매니저를 초기화합니다. 배치된 모듈, 선택 상태 등 내부 데이터를 초기 상태로 되돌립니다.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getSolar().initialize();
```
{% endtab %}
{% endtabs %}

### initPreview() → void

> 현재 활성화된 객체에 속한 모든 지붕/모듈세트의 미리보기 상태를 false로 초기화합니다.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getSolar().initPreview();
```
{% endtab %}
{% endtabs %}

### getFormulaNPV(fileName) → void

> 현재 활성 객체의 지붕별 NPV(순현재가치) 계산 결과를 텍스트로 정리하여 로컬 파일로 저장합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description        |
|----------|--------|----------------------|
| fileName | string | 저장할 파일 이름   |

- Return
  - 없음
  - 활성 객체(`m_pActiveObject`)가 없으면 빈 헤더 내용만 저장됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().getFormulaNPV("npv_result.txt");
```
{% endtab %}
{% endtabs %}

### getFormulaTotalPower(fileName) → void

> 전체 배치된 모듈 기준의 총 발전 용량 계산 결과를 텍스트로 정리하여 로컬 파일로 저장합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description      |
|----------|--------|--------------------|
| fileName | string | 저장할 파일 이름 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().getFormulaTotalPower("total_power.txt");
```
{% endtab %}
{% endtabs %}

### getFormulaAverageSolarRadiation(fileName) → void

> 지붕별 월간(12개월) 평균 전일사량 계산 결과를 텍스트로 정리하여 로컬 파일로 저장합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description      |
|----------|--------|--------------------|
| fileName | string | 저장할 파일 이름 |

- Return
  - 없음
  - 활성 객체가 없으면 빈 헤더 내용만 저장됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().getFormulaAverageSolarRadiation("avg_radiation.txt");
```
{% endtab %}
{% endtabs %}

### getFormulaAverageBeamSolarRadiation(fileName) → void

> 지붕별 월간 평균 직달일사량 계산 결과를 텍스트로 정리하여 로컬 파일로 저장합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description      |
|----------|--------|--------------------|
| fileName | string | 저장할 파일 이름 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().getFormulaAverageBeamSolarRadiation("avg_beam_radiation.txt");
```
{% endtab %}
{% endtabs %}

### getFormulaAverageDiffuseSolarRadiation(fileName) → void

> 지붕별 월간 평균 산란일사량 계산 결과를 텍스트로 정리하여 로컬 파일로 저장합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description      |
|----------|--------|--------------------|
| fileName | string | 저장할 파일 이름 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().getFormulaAverageDiffuseSolarRadiation("avg_diffuse_radiation.txt");
```
{% endtab %}
{% endtabs %}

### getFormulaUnitAreaPowerMap(fileName) → void

> 단위 면적당 연간 발전량 맵 데이터를 그대로 로컬 파일로 저장합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description      |
|----------|--------|--------------------|
| fileName | string | 저장할 파일 이름 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().getFormulaUnitAreaPowerMap("power_map.txt");
```
{% endtab %}
{% endtabs %}

### getFormulaTotalSolarRadiation(fileName) → void

> 전천 일사량 데이터를 그대로 로컬 파일로 저장합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type   | Description      |
|----------|--------|--------------------|
| fileName | string | 저장할 파일 이름 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().getFormulaTotalSolarRadiation("total_radiation.txt");
```
{% endtab %}
{% endtabs %}

### getRadiationPNG() → void

> 현재 활성화된 지붕들에 대해 일사량 분포를 나타내는 PNG 이미지를 생성합니다.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getSolar().getRadiationPNG();
```
{% endtab %}
{% endtabs %}

### getRadiationBeamData() → void

> 현재 활성화된 지붕들에 대해 직달일사 데이터를 생성/추출합니다.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getSolar().getRadiationBeamData();
```
{% endtab %}
{% endtabs %}

### getRadiationDiffuseData() → void

> 현재 활성화된 지붕들에 대해 산란일사 데이터를 생성/추출합니다.

{% tabs %}
{% tab title="Template" %}
```javascript
Module.getSolar().getRadiationDiffuseData();
```
{% endtab %}
{% endtabs %}

### getPanelVisible(), setPanelVisible(visible) → boolean, void

> 태양광 패널의 표시 여부를 조회하거나 설정합니다. `setPanelVisible(true)` 호출 시, 변경 사항이 있고 편집이 활성화된 상태라면 모듈을 즉시 재배치합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description             |
|---------|---------|--------------------------|
| visible | boolean | true 시 패널을 화면에 표시 |

- Return
  - `getPanelVisible()`: `boolean` - 현재 패널 표시 여부. 엔진이 준비되지 않았거나 SolarManager가 없으면 `false`

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setPanelVisible(true);
let visible = Module.getSolar().getPanelVisible();
```
{% endtab %}
{% endtabs %}

### setPanelWidth(width, apply), getPanelWidth() → void, number

> 태양광 패널의 가로 폭을 설정하거나 조회합니다. `apply`가 true이면 즉시 모듈을 재배치합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type    | Description                    |
|-------|---------|----------------------------------|
| width | number  | 패널 가로 폭 (meters)           |
| apply | boolean | true 시 변경 사항을 즉시 재배치 |

- Return
  - `getPanelWidth()`: `number` - 현재 패널 가로 폭. 엔진이 준비되지 않은 경우 `0.0`, SolarManager가 없는 경우 `-1.0` (두 실패 조건의 반환값이 다르므로 주의)

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setPanelWidth(1.0, true);
let width = Module.getSolar().getPanelWidth();
```
{% endtab %}
{% endtabs %}

### setPanelLength(length, apply), getPanelLength() → void, number

> 태양광 패널의 세로 길이를 설정하거나 조회합니다. `apply`가 true이면 즉시 모듈을 재배치합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type    | Description                    |
|--------|---------|----------------------------------|
| length | number  | 패널 세로 길이 (meters)         |
| apply  | boolean | true 시 변경 사항을 즉시 재배치 |

- Return
  - `getPanelLength()`: `number` - 현재 패널 세로 길이. 엔진이 준비되지 않은 경우 `0.0`, SolarManager가 없는 경우 `-1.0` (두 실패 조건의 반환값이 다르므로 주의)

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setPanelLength(1.6, true);
let length = Module.getSolar().getPanelLength();
```
{% endtab %}
{% endtabs %}

### setModuleArrayEX(section, sectionCount, sectionSet, deployAngle) → boolean

> `setModuleArray()`와 동일하게 모듈 배열 구성을 설정하되, 배치 각도를 직접 지정할 수 있습니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type   | Description             |
|--------------|--------|--------------------------|
| section      | number | 단일 배열당 섹션 수     |
| sectionCount | number | 배열 전체의 섹션 개수   |
| sectionSet   | number | 배열 세트 수            |
| deployAngle  | number | 배치 각도 (degrees)     |

- Return
  - `true`: 설정 성공 및 모듈 재배치 완료
  - `false`: 설정 실패 (엔진 미초기화 또는 내부 오류)

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().setModuleArrayEX(5, 20, 2, 15.0);
```
{% endtab %}
{% endtabs %}

### setModuleSwitch(set) → void

> 모듈 배치의 온/오프 스위치 상태를 설정하고, 즉시 모듈을 재배치합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description        |
|------|---------|----------------------|
| set  | boolean | 스위치 On/Off 여부 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setModuleSwitch(true);
```
{% endtab %}
{% endtabs %}

### setDeployBottomHeight(height) → void

> 모듈 배치 영역의 하단 높이 기준값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description         |
|--------|--------|------------------------|
| height | number | 하단 높이 기준값 (meters) |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setDeployBottomHeight(0.3);
```
{% endtab %}
{% endtabs %}

### setDeployTopHeight(height) → void

> 모듈 배치 영역의 상단 높이 기준값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description         |
|--------|--------|------------------------|
| height | number | 상단 높이 기준값 (meters) |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setDeployTopHeight(1.2);
```
{% endtab %}
{% endtabs %}

### getDeployBottomHeight(height) → void

> 모듈 배치 영역의 하단 높이 기준값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - 하단 높이 기준값 (meters)

{% endtab %}
{% tab title="Template" %}
```javascript
let bottomHeight = Module.getSolar().getDeployBottomHeight();
```
{% endtab %}
{% endtabs %}

### getDeployTopHeight(height) → void

> 모듈 배치 영역의 상단 높이 기준값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - 상단 높이 기준값 (meters)

{% endtab %}
{% tab title="Template" %}
```javascript
let topHeight = Module.getSolar().setDeployTopHeight();
```
{% endtab %}
{% endtabs %}

### setMaxKWP(maxKWP) → void

> 배치 가능한 최대 발전 용량(kWp)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description       |
|--------|--------|--------------------|
| maxKWP | number | 최대 발전 용량 (kWp) |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setMaxKWP(100.0);
```
{% endtab %}
{% endtabs %}

### getModuleAngle() → number

> 현재 활성화된 지붕들 중 첫 번째로 활성 상태인 지붕의 모듈 설치 각도를 반환합니다. 활성 지붕이 없으면 전역 옵션값을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 모듈 설치 각도 (degrees)

{% endtab %}
{% tab title="Template" %}
```javascript
let angle = Module.getSolar().getModuleAngle();
```
{% endtab %}
{% endtabs %}

### getAngle() → string

> 현재 활성화된 지붕들 중 첫 번째로 활성 상태인 지붕의 지형 기준각과 남향 기준각을 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `string`: `"Terrain : {지형 기준각},\nSouth : {남향 기준각}\n"` 형식의 문자열
  - 활성 지붕이 없으면 빈 문자열(`""`)을 반환합니다.

{% endtab %}
{% tab title="Template" %}
```javascript
let angleInfo = Module.getSolar().getAngle();
console.log(angleInfo);
```
{% endtab %}
{% endtabs %}

### getSelectedRoofInfo(), setSelectedRoofInfo(info) → string, void

> 현재 선택된 지붕의 정보를 문자열로 조회하거나, 문자열로부터 지붕 정보를 복원합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description        |
|------|--------|----------------------|
| info | string | 지붕 정보 문자열   |

- Return
  - `getSelectedRoofInfo()`: `string` - 선택된 지붕 정보. SolarManager가 없으면 빈 문자열

{% endtab %}
{% tab title="Template" %}
```javascript
let info = Module.getSolar().getSelectedRoofInfo();
Module.getSolar().setSelectedRoofInfo(info);
```
{% endtab %}
{% endtabs %}

### selectRoofByArea(points) → boolean

> 지정한 좌표 목록(경도, 위도)으로 둘러싸인 영역 내의 지붕을 선택합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                        | Description                        |
|--------|----------------------------------------------|-------------------------------------|
| points | [CJSVec3Array](../core/jsvec3array.md)      | 선택 영역 경계 좌표 목록 (경도, 위도, 고도) |

- Return
  - `boolean`: 항상 `true`를 반환합니다.

{% endtab %}
{% tab title="Template" %}
```javascript
let points = new Module.JSVec3Array();
points.pushLonLatAlt(127.0, 37.5, 0.0);
points.pushLonLatAlt(127.001, 37.5, 0.0);
points.pushLonLatAlt(127.001, 37.501, 0.0);
points.pushLonLatAlt(127.0, 37.501, 0.0);

let result = Module.getSolar().selectRoofByArea(points);
```
{% endtab %}
{% endtabs %}

### getSelectedRoofCenter() → [CJSVector3D](../core/jsvector3d.md)

> 현재 선택된 지붕의 중심 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - [`CJSVector3D`](../core/jsvector3d.md): 지붕 중심 위치 (longitude, latitude, altitude)
  - SolarManager가 없거나 활성 객체가 없으면 기본값(0,0,0) `CJSVector3D`를 반환합니다.

{% endtab %}
{% tab title="Template" %}
```javascript
let center = Module.getSolar().getSelectedRoofCenter();
console.log(center.lon, center.lat, center.alt);
```
{% endtab %}
{% endtabs %}

### getSelectedRoofArea() → number

> 현재 선택된 지붕의 면적을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 지붕 면적 (제곱미터)
  - SolarManager가 없거나 활성 객체가 없으면 `0.0`

{% endtab %}
{% tab title="Template" %}
```javascript
let area = Module.getSolar().getSelectedRoofArea();
```
{% endtab %}
{% endtabs %}

### getRoofCount() → number

> 현재 활성화된 객체 내에서 활성 상태인 지붕의 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 활성 지붕 개수
  - 엔진 미초기화, SolarManager 없음, 활성 객체 없음일 경우 `0`

{% endtab %}
{% tab title="Template" %}
```javascript
let count = Module.getSolar().getRoofCount();
```
{% endtab %}
{% endtabs %}

### getRoofedStructureCount() → number

> 태양광 패널이 설치(분석)된 건물(구조물)의 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 분석된 구조물 개수
  - 엔진이 준비되지 않았거나 SolarManager가 없으면 `-1`

{% endtab %}
{% tab title="Template" %}
```javascript
let count = Module.getSolar().getRoofedStructureCount();
```
{% endtab %}
{% endtabs %}

### getRoofedStructure(structureIndex) → [CJSSolarStructure](../etc/jssolarstructure.md)

> 지붕에 패널이 설치된 건물 정보를 인덱스로 조회합니다.

{% tabs %}
{% tab title="Information" %}

| Name           | Type   | Description                          |
|----------------|--------|----------------------------------------|
| structureIndex | number | 조회할 구조물의 인덱스 (0 기반, unsigned int) |

- Return
  - [`CJSSolarStructure`](../etc/jssolarstructure.md): 구조물 정보 객체 (문서 없음, 추후 B그룹에서 작성 예정)
  - `null`: 엔진 미초기화, SolarManager가 없거나, `structureIndex`가 구조물 개수 범위를 벗어난 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let count = Module.getSolar().getRoofedStructureCount();
for (let i = 0; i < count; i++) {
    let structure = Module.getSolar().getRoofedStructure(i);
}
```
{% endtab %}
{% endtabs %}

### getModuleSection(), getModuleSectionCount(), getModuleSectionSet() → number

> 현재 설정된 모듈 배열 구성값(`setModuleArray()`로 설정한 값)을 각각 조회합니다.
>
> - `getModuleSection()`: 단일 배열당 섹션 수
> - `getModuleSectionCount()`: 배열 전체의 섹션 개수
> - `getModuleSectionSet()`: 배열 세트 수

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 각 배열 구성값. 엔진이 준비되지 않은 경우 `0`

{% endtab %}
{% tab title="Template" %}
```javascript
let section = Module.getSolar().getModuleSection();
let sectionCount = Module.getSolar().getModuleSectionCount();
let sectionSet = Module.getSolar().getModuleSectionSet();
```
{% endtab %}
{% endtabs %}

### getRoofExtent(index) → number

> 현재 활성화된 객체의 바운딩 박스 대각선 길이(extent)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description |
|-------|--------|--------------|
| index | number | (사용되지 않음) |

- Return
  - `number`: 활성 객체의 바운딩 박스 대각선 길이
  - 엔진 미초기화 또는 SolarManager가 없으면 `0.0`

{% endtab %}
{% tab title="Template" %}
```javascript
let extent = Module.getSolar().getRoofExtent(0);
```
{% endtab %}
{% endtabs %}

### setColorResultPolygon(polyColor, holeColor) → void

> 태양광 분석 결과 폴리곤과 홀(구멍) 영역의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                              | Description        |
|-----------|-------------------------------------|-----------------------|
| polyColor | [JSColor](../core/jscolor.md)      | 결과 폴리곤 색상    |
| holeColor | [JSColor](../core/jscolor.md)      | 홀(구멍) 영역 색상  |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
let polyColor = new Module.JSColor(0, 255, 0, 128);
let holeColor = new Module.JSColor(255, 0, 0, 128);
Module.getSolar().setColorResultPolygon(polyColor, holeColor);
```
{% endtab %}
{% endtabs %}

### setColorSimpleObject(color) → void

> 단순(Simple) 모드에서 표시되는 모듈 오브젝트의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                           | Description       |
|-------|-----------------------------------|----------------------|
| color | [JSColor](../core/jscolor.md)    | 단순 오브젝트 색상 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
let color = new Module.JSColor(0, 128, 255, 255);
Module.getSolar().setColorSimpleObject(color);
```
{% endtab %}
{% endtabs %}

### setColorSimpleLine(color) → void

> 단순(Simple) 모드에서 표시되는 모듈 외곽선의 색상을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type                           | Description      |
|-------|-----------------------------------|---------------------|
| color | [JSColor](../core/jscolor.md)    | 단순 라인 색상    |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
let color = new Module.JSColor(0, 0, 0, 255);
Module.getSolar().setColorSimpleLine(color);
```
{% endtab %}
{% endtabs %}

### setDrawResultPolygon(draw) → void

> 태양광 분석 결과 폴리곤을 화면에 그릴지 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description                |
|------|---------|-------------------------------|
| draw | boolean | true 시 결과 폴리곤 렌더링 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setDrawResultPolygon(true);
```
{% endtab %}
{% endtabs %}

### getTotalPower() → number

> 배치된 전체 태양광 모듈의 총 발전 용량을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 총 발전 용량 (kWp)

{% endtab %}
{% tab title="Template" %}
```javascript
let totalPower = Module.getSolar().getTotalPower();
```
{% endtab %}
{% endtabs %}

### getTotalNPV() → number

> 배치된 전체 태양광 모듈 기준의 총 NPV(순현재가치)를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 총 NPV

{% endtab %}
{% tab title="Template" %}
```javascript
let totalNPV = Module.getSolar().getTotalNPV();
```
{% endtab %}
{% endtabs %}

### getModulesPosition() → [CJSVec3Array](../core/jsvec3array.md)

> 현재 활성화된 객체에 배치된 모든 태양광 모듈의 중심 좌표 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - [`CJSVec3Array`](../core/jsvec3array.md): 각 모듈의 중심 좌표 (경도, 위도, 고도) 목록. 활성 객체가 없으면 빈 배열

{% endtab %}
{% tab title="Template" %}
```javascript
let positions = Module.getSolar().getModulesPosition();
```
{% endtab %}
{% endtabs %}

### setDeployType(deployType) → void

> 모듈 배치 방식을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name       | Type   | Description                                                                 |
|------------|--------|-------------------------------------------------------------------------------|
| deployType | number | 배치 타입. `0`: 기존 방법(북쪽부터 시작), `1`: 경사 지붕에 통배치, `2`: 기존 방법에서 좌하단부터 시작 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setDeployType(1);
```
{% endtab %}
{% endtabs %}

### inputModuleModel(model), inputModuleMarker(maker), inputModuleCellType(cellType) → void

> 태양광 모듈(패널) 사양 중 모델명/제조사/셀 타입 문자열 정보를 설정합니다. 발전량 계산(XML) 입력값으로 사용됩니다.

{% tabs %}
{% tab title="Information" %}

| Function             | Parameter  | Type   | 저장 필드                       |
|----------------------|------------|--------|----------------------------------|
| inputModuleModel     | model      | string | `m_Module.m_strName`            |
| inputModuleMarker    | maker      | string | `m_Module.m_strMaker`           |
| inputModuleCellType  | cellType   | string | `m_Module.m_strCellType`        |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputModuleModel("Model-X");
Module.getSolar().inputModuleMarker("Egis Solar");
Module.getSolar().inputModuleCellType("Mono-crystalline");
```
{% endtab %}
{% endtabs %}

### inputModulePower(power), inputModuleNOCT(noct), inputModuleWeight(weight), inputModuleEfficiency(efficiency), inputModuleCoefficient(coefficient) → void

> 태양광 모듈 사양 중 정격 출력, NOCT(공칭 태양전지 동작온도), 무게, 효율, 온도계수를 설정합니다. `inputModulePower()`는 값 설정 후 총 발전 용량을 즉시 재계산합니다.

{% tabs %}
{% tab title="Information" %}

| Function                  | Parameter    | Type   | 저장 필드                    |
|---------------------------|--------------|--------|--------------------------------|
| inputModulePower           | power        | number | `m_Module.m_dPower`           |
| inputModuleNOCT            | noct         | number | `m_Module.m_dNOCT`            |
| inputModuleWeight          | weight       | number | `m_Module.m_dWeight`          |
| inputModuleEfficiency      | efficiency   | number | `m_Module.m_dEfficiency`      |
| inputModuleCoefficient     | coefficient  | number | `m_Module.m_dCoefficient`     |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputModulePower(400.0);
Module.getSolar().inputModuleNOCT(45.0);
Module.getSolar().inputModuleWeight(22.5);
Module.getSolar().inputModuleEfficiency(20.5);
Module.getSolar().inputModuleCoefficient(-0.35);
```
{% endtab %}
{% endtabs %}

### inputModuleLength(length), inputModuleHeight(height), inputModuleDepth(depth) → void

> 태양광 모듈의 규격(가로/세로/두께)을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Function           | Parameter | Type   | 저장 필드            | 비고                    |
|---------------------|-----------|--------|------------------------|--------------------------|
| inputModuleLength    | length    | number | `m_Module.m_dLength`   | 입력값(mm)을 1000으로 나누어 meter 단위로 저장 |
| inputModuleHeight    | height    | number | `m_Module.m_dHeight`   | 입력값(mm)을 1000으로 나누어 meter 단위로 저장 |
| inputModuleDepth     | depth     | number | `m_Module.m_dDepth`    | 입력값을 그대로 저장 (단위 변환 없음) |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputModuleLength(1650);  // mm 단위 입력 → 1.65m로 저장
Module.getSolar().inputModuleHeight(992);   // mm 단위 입력 → 0.992m로 저장
Module.getSolar().inputModuleDepth(40);
```
{% endtab %}
{% endtabs %}

### inputInverterEfficiency(efficiency), inputInverterPower(power) → void

> 인버터의 효율과 정격 출력을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Function                  | Parameter   | Type   | 저장 필드                    |
|---------------------------|-------------|--------|--------------------------------|
| inputInverterEfficiency    | efficiency  | number | `m_Inverter.m_dEfficiency`    |
| inputInverterPower         | power       | number | `m_Inverter.m_dPower`         |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputInverterEfficiency(98.0);
Module.getSolar().inputInverterPower(3000.0);
```
{% endtab %}
{% endtabs %}

### inputGenerationOptionLoss(loss), inputGenerationOptionAngle(angle) → void

> 발전량 계산 시 적용할 손실률과 기본 설치 각도를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Function                     | Parameter | Type   | 저장 필드          |
|-------------------------------|-----------|--------|----------------------|
| inputGenerationOptionLoss      | loss      | number | `m_Option.m_dLoss`   |
| inputGenerationOptionAngle     | angle     | number | `m_Option.m_dAngle`  |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputGenerationOptionLoss(14.0);
Module.getSolar().inputGenerationOptionAngle(30.0);
```
{% endtab %}
{% endtabs %}

### inputInitInvestA(value) ~ inputInitInvestL(value) → void

> 초기 투자비 계산에 사용되는 항목 A~L(12개)의 값을 설정합니다. 각 항목이 실제로 의미하는 세부 항목(공사비, 설계비 등)은 이 파일에서는 정의되어 있지 않으며, XML 스펙/UI 쪽에서 정의됩니다.

{% tabs %}
{% tab title="Information" %}

| Function            | Parameter | Type   | 저장 필드              |
|----------------------|-----------|--------|--------------------------|
| inputInitInvestA      | value     | number | `m_InitInvest.m_A`      |
| inputInitInvestB      | value     | number | `m_InitInvest.m_B`      |
| inputInitInvestC      | value     | number | `m_InitInvest.m_C`      |
| inputInitInvestD      | value     | number | `m_InitInvest.m_D`      |
| inputInitInvestE      | value     | number | `m_InitInvest.m_E`      |
| inputInitInvestF      | value     | number | `m_InitInvest.m_F`      |
| inputInitInvestG      | value     | number | `m_InitInvest.m_G`      |
| inputInitInvestH      | value     | number | `m_InitInvest.m_H`      |
| inputInitInvestI      | value     | number | `m_InitInvest.m_I`      |
| inputInitInvestJ      | value     | number | `m_InitInvest.m_J`      |
| inputInitInvestK      | value     | number | `m_InitInvest.m_K`      |
| inputInitInvestL      | value     | number | `m_InitInvest.m_L`      |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputInitInvestA(1000000);
Module.getSolar().inputInitInvestB(200000);
// ... inputInitInvestC ~ inputInitInvestL 도 동일한 방식으로 호출
```
{% endtab %}
{% endtabs %}

### inputOperationA(value) ~ inputOperationF(value) → void

> 운영비 계산에 사용되는 항목 A~F(6개)의 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Function         | Parameter | Type   | 저장 필드            |
|-------------------|-----------|--------|------------------------|
| inputOperationA    | value     | number | `m_Operation.m_A`     |
| inputOperationB    | value     | number | `m_Operation.m_B`     |
| inputOperationC    | value     | number | `m_Operation.m_C`     |
| inputOperationD    | value     | number | `m_Operation.m_D`     |
| inputOperationE    | value     | number | `m_Operation.m_E`     |
| inputOperationF    | value     | number | `m_Operation.m_F`     |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputOperationA(50000);
Module.getSolar().inputOperationB(10000);
// ... inputOperationC ~ inputOperationF 도 동일한 방식으로 호출
```
{% endtab %}
{% endtabs %}

### inputSalesA(value) ~ inputSalesD(value) → void

> 판매 수익 계산에 사용되는 항목 A~D(4개)의 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Function     | Parameter | Type   | 저장 필드         |
|---------------|-----------|--------|---------------------|
| inputSalesA    | value     | number | `m_Sales.m_A`      |
| inputSalesB    | value     | number | `m_Sales.m_B`      |
| inputSalesC    | value     | number | `m_Sales.m_C`      |
| inputSalesD    | value     | number | `m_Sales.m_D`      |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputSalesA(120.5);
Module.getSolar().inputSalesB(3.5);
// ... inputSalesC ~ inputSalesD 도 동일한 방식으로 호출
```
{% endtab %}
{% endtabs %}

### inputFinanceA(value), inputFinanceB(value), inputFinanceC(years), inputFinanceD(years) → void

> 금융(대출) 관련 조건을 설정합니다. A/B는 비율(대출 비율, 대출 이자율), C/D는 기간(년) 값입니다.

{% tabs %}
{% tab title="Information" %}

| Function       | Parameter | Type   | 저장 필드                          |
|-----------------|-----------|--------|---------------------------------------|
| inputFinanceA    | value     | number | `m_Finance.m_dLoanRatio` (대출 비율)      |
| inputFinanceB    | value     | number | `m_Finance.m_dLoanInterestRatio` (대출 이자율) |
| inputFinanceC    | years     | number | `m_Finance.m_nDeferPeriod` (거치 기간, int)   |
| inputFinanceD    | years     | number | `m_Finance.m_nRefundPeriod` (상환 기간, int)  |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputFinanceA(70.0);   // 대출 비율(%)
Module.getSolar().inputFinanceB(3.5);    // 대출 이자율(%)
Module.getSolar().inputFinanceC(3);      // 거치 기간(년)
Module.getSolar().inputFinanceD(10);     // 상환 기간(년)
```
{% endtab %}
{% endtabs %}

### inputRentalA(value), inputRentalB(value), inputRentalC(value) → void

> 임대 관련 계산 항목 A~C(3개)의 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Function       | Parameter | Type   | 저장 필드          |
|-----------------|-----------|--------|----------------------|
| inputRentalA     | value     | number | `m_Rental.m_A`      |
| inputRentalB     | value     | number | `m_Rental.m_B`      |
| inputRentalC     | value     | number | `m_Rental.m_C`      |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputRentalA(1000000);
Module.getSolar().inputRentalB(5.0);
Module.getSolar().inputRentalC(10);
```
{% endtab %}
{% endtabs %}

### inputSupportA(value), inputSupportB(value) → void

> 정부/지자체 지원금 관련 계산 항목 A, B(2개)의 값을 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Function       | Parameter | Type   | 저장 필드            |
|-----------------|-----------|--------|------------------------|
| inputSupportA    | value     | number | `m_Support.m_A`       |
| inputSupportB    | value     | number | `m_Support.m_B`       |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().inputSupportA(500000);
Module.getSolar().inputSupportB(2.0);
```
{% endtab %}
{% endtabs %}

### redeploy() → string

> 현재 활성 객체의 모든 활성 지붕에 대해 모듈을 일괄 재배치(추가/삭제)합니다. 전체 배치(`IsTotalDeploy()`)가 설정된 경우에만 실제로 추가/삭제가 수행됩니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `string`: `"{추가된 모듈 수}#{삭제된 모듈 수}"` 형식의 문자열
  - 엔진 미준비 또는 활성 객체가 없으면 `"0#0"`

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().redeploy();
let [added, deleted] = result.split("#").map(Number);
```
{% endtab %}
{% endtabs %}

### redeployAdd() → number

> 현재 활성 객체의 모든 활성 지붕에 대해 추가 가능한 모듈을 재배치(추가)합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 추가된 모듈 수. `0`: 실패 또는 추가된 모듈 없음, `1` 이상: 재배치(추가)된 모듈 수

{% endtab %}
{% tab title="Template" %}
```javascript
let addedCount = Module.getSolar().redeployAdd();
```
{% endtab %}
{% endtabs %}

### redeployDelete() → number

> 현재 활성 객체의 모든 활성 지붕에 대해 배치 조건에 맞지 않는 모듈을 재배치(삭제)합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 삭제된 모듈 수. `0`: 실패 또는 삭제된 모듈 없음, `1` 이상: 재배치(삭제)된 모듈 수

{% endtab %}
{% tab title="Template" %}
```javascript
let deletedCount = Module.getSolar().redeployDelete();
```
{% endtab %}
{% endtabs %}

### setModulePreview(imageData, imageWidth, imageHeight, width, height, thickness, angle) → boolean

> 벽면 설치용 모듈 미리보기 정보(텍스처, 규격)를 생성합니다. 기존 미리보기 정보는 해제 후 새로 생성됩니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type   | Description                          |
|-------------|--------|----------------------------------------|
| imageData   | array  | 텍스처 픽셀 데이터 (RGBA)              |
| imageWidth  | number | 이미지 너비 (pixels)                   |
| imageHeight | number | 이미지 높이 (pixels)                   |
| width       | number | 모듈 가로 폭 (meters)                  |
| height      | number | 모듈 세로 길이 (meters)                |
| thickness   | number | 모듈 두께 (meters)                     |
| angle       | number | 모듈 설치 각도 (degrees)               |

- Return
  - `true`: 생성 성공
  - `false`: `imageData`의 길이가 1 이하인 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let image = new Uint8Array([255, 0, 0, 255, 0, 255, 0, 255, 0, 0, 255, 255, 255, 255, 255, 255]);
let result = Module.getSolar().setModulePreview(image, 2, 2, 1.0, 1.6, 0.04, 30.0);
```
{% endtab %}
{% endtabs %}

### updateModuleOption(width, height, thickness, angle) → boolean

> 현재 선택(select)된 벽면 설치형 태양광 패널 오브젝트들의 규격(폭/높이/두께/각도)을 갱신합니다. 마우스 상태가 벽면 패널 편집 모드(`MML_SELECT_EDIT_WALL_PANEL`)일 때만 동작합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                                   |
|-----------|--------|-------------------------------------------------|
| width     | number | 모듈 가로 폭 (meters). 최소 0.1로 보정          |
| height    | number | 모듈 세로 길이 (meters). 최소 0.1로 보정        |
| thickness | number | 모듈 두께 (meters). 최소 0.1로 보정             |
| angle     | number | 모듈 설치 각도 (degrees). 0.1 ~ 90.0 범위로 보정 |

- Return
  - `true`: 하나 이상의 선택된 패널에 적용 성공
  - `false`: 편집 모드가 아니거나 선택된 패널이 없는 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().updateModuleOption(1.0, 1.6, 0.04, 30.0);
```
{% endtab %}
{% endtabs %}

### updateModuleUp(value) → boolean

> 현재 선택된 벽면 설치형 패널을 법선(normal) 방향으로 `value`만큼 이동시킵니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description               |
|-------|--------|------------------------------|
| value | number | 법선 방향 이동 거리 (meters) |

- Return
  - `true`: 하나 이상의 선택된 패널에 적용 성공
  - `false`: 편집 모드가 아니거나 선택된 패널이 없는 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().updateModuleUp(0.1);
```
{% endtab %}
{% endtabs %}

### updateModuleRight(value) → boolean

> 현재 선택된 벽면 설치형 패널을 표면상의 오른쪽(가로) 방향으로 `value`만큼 이동시킵니다.

{% tabs %}
{% tab title="Information" %}

| Name  | Type   | Description                  |
|-------|--------|---------------------------------|
| value | number | 오른쪽 방향 이동 거리 (meters) |

- Return
  - `true`: 하나 이상의 선택된 패널에 적용 성공
  - `false`: 편집 모드가 아니거나 선택된 패널이 없는 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().updateModuleRight(0.1);
```
{% endtab %}
{% endtabs %}

### updateModuleOptionByKey(layerName, objectKey, width, height, thickness, angle) → boolean

> 레이어 이름과 객체 키로 지정한 특정 벽면 설치형 패널 하나의 규격을 갱신합니다. (선택 상태와 무관하게 동작)

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                     |
|-----------|--------|-------------------------------------|
| layerName | string | 대상 객체가 속한 레이어 이름       |
| objectKey | string | 대상 객체의 고유 키                |
| width     | number | 모듈 가로 폭 (meters)              |
| height    | number | 모듈 세로 길이 (meters)            |
| thickness | number | 모듈 두께 (meters)                 |
| angle     | number | 모듈 설치 각도 (degrees)           |

- Return
  - `true`: 적용 성공
  - `false`: 레이어/객체를 찾지 못했거나 태양광 패널 오브젝트가 아닌 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().updateModuleOptionByKey("wall_layer", "panel_001", 1.0, 1.6, 0.04, 30.0);
```
{% endtab %}
{% endtabs %}

### updateModuleOptionByLayer(layerName, width, height, thickness, angle) → boolean

> 지정한 레이어에 속한 모든 벽면 설치형 패널 오브젝트의 규격을 일괄 갱신합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                     |
|-----------|--------|-------------------------------------|
| layerName | string | 대상 레이어 이름                    |
| width     | number | 모듈 가로 폭 (meters)              |
| height    | number | 모듈 세로 길이 (meters)            |
| thickness | number | 모듈 두께 (meters)                 |
| angle     | number | 모듈 설치 각도 (degrees)           |

- Return
  - `true`: 하나 이상의 패널에 적용 성공
  - `false`: 레이어를 찾지 못했거나 적용된 패널이 없는 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().updateModuleOptionByLayer("wall_layer", 1.0, 1.6, 0.04, 30.0);
```
{% endtab %}
{% endtabs %}

### updateModuleUpByKey(layerName, objectKey, value) → boolean

> 레이어 이름과 객체 키로 지정한 특정 벽면 설치형 패널 하나를 법선 방향으로 `value`만큼 이동시킵니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                     |
|-----------|--------|-------------------------------------|
| layerName | string | 대상 객체가 속한 레이어 이름       |
| objectKey | string | 대상 객체의 고유 키                |
| value     | number | 법선 방향 이동 거리 (meters)       |

- Return
  - `true`: 적용 성공
  - `false`: 레이어/객체를 찾지 못했거나 태양광 패널 오브젝트가 아닌 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().updateModuleUpByKey("wall_layer", "panel_001", 0.1);
```
{% endtab %}
{% endtabs %}

### updateModuleRightByKey(layerName, objectKey, value) → boolean

> 레이어 이름과 객체 키로 지정한 특정 벽면 설치형 패널 하나를 표면상의 오른쪽(가로) 방향으로 `value`만큼 이동시킵니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                     |
|-----------|--------|-------------------------------------|
| layerName | string | 대상 객체가 속한 레이어 이름       |
| objectKey | string | 대상 객체의 고유 키                |
| value     | number | 오른쪽 방향 이동 거리 (meters)     |

- Return
  - `true`: 적용 성공
  - `false`: 레이어/객체를 찾지 못했거나 태양광 패널 오브젝트가 아닌 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().updateModuleRightByKey("wall_layer", "panel_001", 0.1);
```
{% endtab %}
{% endtabs %}

### buildModuleOnTerrain(section, sectionCount, sectionSet, moduleAngle, deployAngle) → boolean

> 지형(터레인) 위에 설정된 영역(`setAreaOnTerrain()`으로 지정)을 기준으로 태양광 모듈을 배치합니다.

{% tabs %}
{% tab title="Information" %}

| Name         | Type   | Description             |
|--------------|--------|--------------------------|
| section      | number | 단일 배열당 섹션 수     |
| sectionCount | number | 배열 전체의 섹션 개수   |
| sectionSet   | number | 배열 세트 수            |
| moduleAngle  | number | 모듈 설치 각도 (degrees) |
| deployAngle  | number | 배치(방향) 각도 (degrees) |

- Return
  - `true`: 배치 성공
  - `false`: 배치 실패 (설정된 영역이 없는 등 내부 오류)

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().buildModuleOnTerrain(5, 20, 2, 30.0, 0.0);
```
{% endtab %}
{% endtabs %}

### setModuleSizeOnTerrain(width, height) → void

> 지형에 배치되는 태양광 모듈 하나의 가로/세로 크기를 설정하고, 즉시 재배치합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description        |
|--------|--------|----------------------|
| width  | number | 모듈 가로 폭 (meters) |
| height | number | 모듈 세로 길이 (meters) |

- Return
  - 없음
  - 지형 객체(`m_pSolarTerrain`)가 생성되어 있지 않으면 아무 동작도 하지 않습니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setModuleSizeOnTerrain(1.0, 1.6);
```
{% endtab %}
{% endtabs %}

### setVisibleAreaOnTerrain(visible) → void

> 지형에 설정된 태양광 설치 영역의 표시 여부를 설정합니다.

{% tabs %}
{% tab title="Information" %}

| Name    | Type    | Description             |
|---------|---------|--------------------------|
| visible | boolean | true 시 영역을 화면에 표시 |

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setVisibleAreaOnTerrain(true);
```
{% endtab %}
{% endtabs %}

### setAreaOnTerrain(points, buffer, fillColor, lineColor) → boolean

> 지형 위에 태양광 설치 영역(다각형)을 추가합니다. 좌표별 지형 고도값을 자동으로 조회하여 반영합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                    | Description                    |
|-----------|-------------------------------------------|-----------------------------------|
| points    | [CJSVec2Array](../core/jsvec2array.md)   | 영역 경계 좌표 목록 (경도, 위도)   |
| buffer    | number                                     | 영역 여백 버퍼 (meters)          |
| fillColor | [JSColor](../core/jscolor.md)            | 영역 채우기 색상                 |
| lineColor | [JSColor](../core/jscolor.md)            | 영역 외곽선 색상                 |

- Return
  - `boolean`: 항상 `true`를 반환합니다.

{% endtab %}
{% tab title="Template" %}
```javascript
let points = new Module.JSVec2Array();
points.push(127.0, 37.5);
points.push(127.002, 37.5);
points.push(127.002, 37.502);
points.push(127.0, 37.502);

let fillColor = new Module.JSColor(0, 200, 0, 128);
let lineColor = new Module.JSColor(0, 0, 0, 255);

let result = Module.getSolar().setAreaOnTerrain(points, 0.0, fillColor, lineColor);
```
{% endtab %}
{% endtabs %}

### getAreaOnTerrain() → number

> 지형에 설정된 태양광 설치 영역의 면적을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 설치 영역 면적 (제곱미터)

{% endtab %}
{% tab title="Template" %}
```javascript
let area = Module.getSolar().getAreaOnTerrain();
```
{% endtab %}
{% endtabs %}

### getModulesPositionOnTerrain() → [CJSVec3Array](../core/jsvec3array.md)

> 지형에 배치된 모든 태양광 모듈의 중심 좌표 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - [`CJSVec3Array`](../core/jsvec3array.md): 각 모듈의 중심 좌표 (경도, 위도, 고도) 목록

{% endtab %}
{% tab title="Template" %}
```javascript
let positions = Module.getSolar().getModulesPositionOnTerrain();
```
{% endtab %}
{% endtabs %}

### getArrayGapH() → number

> 태양광 모듈 배열 간의 세로 간격 값(`m_dGapArrayH`)을 반환합니다. (건물/지붕 설치 기준)

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 배열 간 세로 간격 (meters)

{% endtab %}
{% tab title="Template" %}
```javascript
let gap = Module.getSolar().getArrayGapH();
```
{% endtab %}
{% endtabs %}

### addObject3DS(layerName, objectKey, uri, position, scaleX, scaleY, scaleZ, rotation, color) → boolean

> 지정한 3DS 파일을 로드하여 라이브러리 오브젝트로 배치합니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                     | Description                    |
|-----------|--------------------------------------------|-----------------------------------|
| layerName | string                                      | 오브젝트를 생성할 레이어 이름     |
| objectKey | string                                      | 생성할 오브젝트의 고유 키         |
| uri       | string                                      | 3DS 파일 경로(URI)                |
| position  | [CJSVector3D](../core/jsvector3d.md)      | 배치 위치 (경도, 위도, 고도)       |
| scaleX    | number                                      | X축 스케일                        |
| scaleY    | number                                      | Y축 스케일                        |
| scaleZ    | number                                      | Z축 스케일                        |
| rotation  | number                                      | 회전 각도 (degrees)               |
| color     | [JSColor](../core/jscolor.md)             | 오브젝트 색상                     |

- Return
  - `true`: 파일 로드 및 배치 성공
  - `false`: 파일 로드 실패
  - 엔진이 준비되지 않은 경우 `false`

{% endtab %}
{% tab title="Template" %}
```javascript
let position = new Module.JSVector3D(127.0, 37.5, 0.0);
let color = new Module.JSColor(255, 255, 255, 255);
let result = Module.getSolar().addObject3DS("3ds_layer", "obj_001", "models/panel.3ds", position, 1.0, 1.0, 1.0, 0.0, color);
```
{% endtab %}
{% endtabs %}

### addObjectByCoordinates(layerName, objectKey, coordinates, color, height) → boolean

> 지정한 좌표 목록(다각형)을 밑면으로 하는 높이를 가진 3D 건물 오브젝트를 생성합니다.

{% tabs %}
{% tab title="Information" %}

| Name        | Type                                      | Description                         |
|-------------|----------------------------------------------|----------------------------------------|
| layerName   | string                                        | 오브젝트를 생성할 레이어 이름          |
| objectKey   | string                                        | 생성할 오브젝트의 고유 키              |
| coordinates | [CJSVec3Array](../core/jsvec3array.md)      | 건물 밑면 다각형 좌표 목록 (3개 이상)  |
| color       | [JSColor](../core/jscolor.md)               | 오브젝트 색상                          |
| height      | number                                        | 건물 높이 (meters)                    |

- Return
  - `true`: 생성 성공
  - `false`: 좌표 개수가 3개 미만이거나 엔진이 준비되지 않은 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let coords = new Module.JSVec3Array();
coords.pushLonLatAlt(127.0, 37.5, 0.0);
coords.pushLonLatAlt(127.001, 37.5, 0.0);
coords.pushLonLatAlt(127.001, 37.501, 0.0);
coords.pushLonLatAlt(127.0, 37.501, 0.0);

let color = new Module.JSColor(200, 200, 200, 255);
let result = Module.getSolar().addObjectByCoordinates("building_layer", "bldg_001", coords, color, 10.0);
```
{% endtab %}
{% endtabs %}

### setModuleSideMargin(margin), getModuleSideMargin() → void, number

> 모듈 간 좌우(측면) 여백을 설정하거나 조회합니다. (`setModuleMargin()`의 개별 필드 버전)

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description        |
|--------|--------|-----------------------|
| margin | number | 모듈 좌우 여백 (meters) |

- Return
  - `getModuleSideMargin()`: `number` - 현재 모듈 좌우 여백

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setModuleSideMargin(0.1);
let margin = Module.getSolar().getModuleSideMargin();
```
{% endtab %}
{% endtabs %}

### setModuleTopDownMargin(margin), getModuleTopDownMargin() → void, number

> 모듈 간 상하 여백을 설정하거나 조회합니다. (`setModuleMargin()`의 개별 필드 버전)

{% tabs %}
{% tab title="Information" %}

| Name   | Type   | Description        |
|--------|--------|-----------------------|
| margin | number | 모듈 상하 여백 (meters) |

- Return
  - `getModuleTopDownMargin()`: `number` - 현재 모듈 상하 여백

{% endtab %}
{% tab title="Template" %}
```javascript
Module.getSolar().setModuleTopDownMargin(0.1);
let margin = Module.getSolar().getModuleTopDownMargin();
```
{% endtab %}
{% endtabs %}

### addPlannelObject(layerName, lon, lat, alt, width, height, thickness, angle, direction) → boolean

> 지정한 좌표에 태양광 패널 오브젝트 하나를 직접 생성하여 레이어에 추가합니다. (지붕/지형 분석 절차 없이 단일 패널을 직접 배치할 때 사용)

{% tabs %}
{% tab title="Information" %}

| Name      | Type   | Description                     |
|-----------|--------|-------------------------------------|
| layerName | string | 오브젝트를 추가할 레이어 이름       |
| lon       | number | 경도                                |
| lat       | number | 위도                                |
| alt       | number | 고도 (meters)                       |
| width     | number | 패널 가로 폭 (meters)               |
| height    | number | 패널 세로 길이 (meters)             |
| thickness | number | 패널 두께 (meters)                  |
| angle     | number | 패널 수직 각도 (degrees)            |
| direction | number | 패널 방향 각도 (degrees)            |

- Return
  - `true`: 생성 성공
  - `false`: 지정한 레이어를 찾지 못한 경우

{% endtab %}
{% tab title="Template" %}
```javascript
let result = Module.getSolar().addPlannelObject("BuildingLayer", 127.0, 37.5, 12.0, 1.0, 1.6, 0.04, 30.0, 180.0);
```
{% endtab %}
{% endtabs %}