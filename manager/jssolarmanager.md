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

### getCenterOfMassOnTerrain() → [JSVector3D](../core/jsvector3d.md)

> 지형 위에 배치된 태양광 패널의 질량 중심 위치를 반환합니다.
>
> 반환되는 값은 경도, 위도, 고도 순서의 좌표입니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - [`JSVector3D`](../core/jsvector3d.md): 질량 중심 위치 (longitude, latitude, altitude)

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

### progressModuleArray(callback) → string

> 비동기 모듈 배치([startModuleArrayAsync](#startmodulearrayasync-section-sectioncount-sectionset-string))의 진행률 콜백을 등록합니다.
>
> 대문자로 시작하는 `ProgressModuleArray()`도 동일하게 동작합니다 (cpp에서 같은 구현부에 바인딩된 별칭).

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description                                                                 |
|----------|----------|-----------------------------------------------------------------------------|
| callback | function | 진행률 콜백. 인자로 진행률(`number`, 0 ~ 100, 정수 단위 %)이 전달됩니다. |

- Return
  - `string`: 항상 `"success"`
  - 이미 등록된 콜백이 있으면 새 콜백으로 교체됩니다. 등록한 콜백은 배치가 끝나도 해제되지 않으므로 이후 배치에도 계속 호출됩니다.
  - 진행률은 모듈 세트 단위로 1% 이상 변할 때마다 호출되며, 워커 내부 계산 구간에 대한 진행률입니다. 완료 시점의 패널 객체 생성은 이 값에 포함되지 않습니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().progressModuleArray(function (percent) {
    console.log("배치 진행률: " + percent + "%");
});
```
{% endtab %}
{% endtabs %}

### completeModuleArray(callback) → string

> 비동기 모듈 배치([startModuleArrayAsync](#startmodulearrayasync-section-sectioncount-sectionset-string))의 완료 콜백을 등록합니다.
>
> 대문자로 시작하는 `CompleteModuleArray()`도 동일하게 동작합니다 (cpp에서 같은 구현부에 바인딩된 별칭).

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description                                                              |
|----------|----------|--------------------------------------------------------------------------|
| callback | function | 완료 콜백. 인자로 설치된 패널 수(`number`)가 전달됩니다. |

- Return
  - `string`: 항상 `"success"`
  - 이미 등록된 콜백이 있으면 새 콜백으로 교체됩니다. 등록한 콜백은 배치가 끝나도 해제되지 않습니다.
  - 콜백 인자는 [getModuleCount()](#getmodulecount-number)와 같은 기준의 설치된 패널 수입니다. 배치를 요청한 뒤 다른 옥상을 다시 선택한 경우 결과가 폐기되고 `0`이 전달됩니다.
  - 콜백은 패널 객체 생성과 `EventSolarUpdate` 이벤트 발생이 끝난 뒤에 호출됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().completeModuleArray(function (panelCount) {
    console.log("설치된 패널 수: " + panelCount);
});
```
{% endtab %}
{% endtabs %}

### startModuleArrayAsync(section, sectionCount, sectionSet) → string

> 선택된 옥상에 태양광 모듈을 비동기(Web Worker)로 배치합니다. `setModuleArray()`와 같은 배치 조건을 사용하지만, 레이캐스트가 집중된 배치 계산을 워커에서 처리하므로 패널이 많아도 화면이 멈추지 않습니다.
>
> 대문자로 시작하는 `StartModuleArrayAsync()`도 동일하게 동작합니다 (cpp에서 같은 구현부에 바인딩된 별칭).

{% tabs %}
{% tab title="Information" %}

**사용 흐름**

1. `Module.initialize()`의 `worker` 옵션을 켭니다 (`worker.use: true`, `worker.path`). 워커가 꺼져 있으면 동기 폴백 없이 오류 문자열을 반환합니다.
2. [selectRoofByObject()](#selectroofbyobject-layername-objectkey-boolean) 등으로 옥상을 선택합니다.
3. [progressModuleArray()](#progressmodulearray-callback-string), [completeModuleArray()](#completemodulearray-callback-string)로 콜백을 등록합니다.
4. `startModuleArrayAsync()`를 호출합니다. 반환값이 `"success"`이면 즉시 반환되고 계산은 워커에서 진행됩니다.
5. 진행률 콜백이 반복 호출되고, 마지막에 완료 콜백이 설치된 패널 수와 함께 1회 호출됩니다.
6. 완료 시점에 주변 지물(그림자를 만드는 건물 등)이 자동으로 일조분석용 저장소에 캡처되므로, 이어서 [startPanelSunshine()](#startpanelsunshine-starttime-endtime-interval-string)을 바로 실행할 수 있습니다.

| Name         | Type   | Description             |
|--------------|--------|--------------------------|
| section      | number | 단일 배열당 섹션 수     |
| sectionCount | number | 배열 전체의 섹션 개수   |
| sectionSet   | number | 배열 세트 수            |

- Return
  - `string`: 시작 결과. 성공 시 `"success"`, 실패 시 아래 사유 문자열
  
  | 반환값 | 의미 |
  |--------|------|
  | `"success"` | 워커에 배치를 요청함 |
  | `"error map load"` | 엔진 또는 SolarManager가 준비되지 않음 |
  | `"already running"` | 이전 비동기 배치가 아직 진행 중 |
  | `"web worker is disabled - set Module.initialize({worker:{use:true, path:...}})"` | web worker 미사용 또는 경로 미설정 |
  | `"no selected roof"` | 선택된 옥상이 없음 |
  | `"redeploy mode is not supported on the async path"` | 재배치(redeploy) 진행 중 |
  | `"no pickable object - the selected building is not loaded now, move the camera back to it"` | 선택한 건물의 메쉬가 현재 로드/표시되어 있지 않음 (카메라를 건물로 되돌려야 함) |
  | `"no roof to deploy"` | 배치할 수 있는 지붕이 없음 (비활성 지붕, 모듈 높이 조건 불충족, 배치 계획 없음 등) |
  | `"failed to create web worker"` | 워커 생성 실패 |

- 동작 참고
  - 배치 각도 지정(`setModuleArrayEX()`의 `deployAngle`)은 지원하지 않으며, 항상 자동 각도로 배치합니다.
  - `"no pickable object"`, `"no roof to deploy"` 반환 시점에는 배열 옵션(`section`, `sectionCount`, `sectionSet`)이 이미 반영되어 있고, 처리된 지붕의 기존 패널은 이미 제거된 상태일 수 있습니다.
  - 요청에 성공하면 이전 일조분석 결과([getPanelSunshineResult()](#getpanelsunshineresult-string))가 초기화됩니다.
  - 패널을 올릴 대상 객체의 삼각형은 객체 유형(다면체, 3DS, 3D 피규어, glTF, 고스트 심볼 등)에 맞게 변환해 워커로 전달합니다. 예전에는 glTF(GLB) 객체의 삼각형이 비어 있어 지붕에 패널이 배치되지 않았는데, 이제 glTF 지붕에도 배치됩니다.
  - 워커가 빈 응답을 돌려주는 오류가 발생하면 진행 상태만 해제되고 완료 콜백은 호출되지 않습니다.

{% endtab %}
{% tab title="Template" %}
```javascript
var solar = Module.GetSolarManager();

solar.progressModuleArray(function (percent) {
    console.log("배치 진행률: " + percent + "%");
});

solar.completeModuleArray(function (panelCount) {
    console.log("설치된 패널 수: " + panelCount);
});

// 옥상 선택 후 비동기 배치 시작 (각 배열당 5개 섹션, 섹션 총 20개, 세트 2개)
solar.selectRoofByObject("building_layer", "object_001");
var result = solar.startModuleArrayAsync(5, 20, 2);
if (result !== "success") {
    console.error("비동기 배치 시작 실패: " + result);
}
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

### clearSelectedRoof() → void

> 선택된 옥상(지붕) 상태를 완전히 초기화합니다. 미리보기 모듈세트 해제, 선택된 지붕과 설치된 옥상 패널 삭제, 활성 객체 해제까지 수행합니다.
>
> `initialize()`와 달리 활성 객체까지 정리하므로, 호출 후 `getModuleCount()` 등이 이미 정리된 객체를 참조하지 않습니다. 대문자로 시작하는 `ClearSelectedRoof()`도 동일하게 동작합니다 (cpp에서 같은 구현부에 바인딩된 별칭).

{% tabs %}
{% tab title="Information" %}

- Return
  - 없음
  - 엔진 또는 SolarManager가 준비되지 않았으면 아무 동작도 하지 않습니다.
  - 선택된 옥상이 이미 없더라도 호출은 안전하며, 이 경우 옥상 선택/패널 정리는 생략됩니다.
  - 일조분석 결과([getPanelSunshineResult()](#getpanelsunshineresult-string))의 패널 목록과 분석 구간 정보도 함께 초기화됩니다. 지형/벽면 패널에 이미 칠해진 일조 색은 되돌리지 않으므로, 색까지 되돌리려면 [clearPanelSunshine()](#clearpanelsunshine-void)을 사용합니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().clearSelectedRoof();
```
{% endtab %}
{% endtabs %}

### selectRoofByArea(points) → boolean

> 지정한 좌표 목록(경도, 위도)으로 둘러싸인 영역 내의 지붕을 선택합니다.

{% tabs %}
{% tab title="Information" %}

| Name   | Type                                        | Description                        |
|--------|----------------------------------------------|-------------------------------------|
| points | [JSVec3Array](../core/jsvec3array.md)      | 선택 영역 경계 좌표 목록 (경도, 위도, 고도) |

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

### getSelectedRoofCenter() → [JSVector3D](../core/jsvector3d.md)

> 현재 선택된 지붕의 중심 좌표를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - [`JSVector3D`](../core/jsvector3d.md): 지붕 중심 위치 (longitude, latitude, altitude)
  - SolarManager가 없거나 활성 객체가 없으면 기본값(0,0,0) `JSVector3D`를 반환합니다.

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

### getRoofedStructure(structureIndex) → [JSSolarStructure](../etc/jssolarstructure.md)

> 지붕에 패널이 설치된 건물 정보를 인덱스로 조회합니다.

{% tabs %}
{% tab title="Information" %}

| Name           | Type   | Description                          |
|----------------|--------|----------------------------------------|
| structureIndex | number | 조회할 구조물의 인덱스 (0 기반, unsigned int) |

- Return
  - [`JSSolarStructure`](../etc/jssolarstructure.md): 구조물 정보 객체 (문서 없음, 추후 B그룹에서 작성 예정)
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

### getModulesPosition() → [JSVec3Array](../core/jsvec3array.md)

> 현재 활성화된 객체에 배치된 모든 태양광 모듈의 중심 좌표 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - [`JSVec3Array`](../core/jsvec3array.md): 각 모듈의 중심 좌표 (경도, 위도, 고도) 목록. 활성 객체가 없으면 빈 배열

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
| points    | [JSVec2Array](../core/jsvec2array.md)   | 영역 경계 좌표 목록 (경도, 위도)   |
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

### getModulesPositionOnTerrain() → [JSVec3Array](../core/jsvec3array.md)

> 지형에 배치된 모든 태양광 모듈의 중심 좌표 목록을 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - [`JSVec3Array`](../core/jsvec3array.md): 각 모듈의 중심 좌표 (경도, 위도, 고도) 목록

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
| position  | [JSVector3D](../core/jsvector3d.md)      | 배치 위치 (경도, 위도, 고도)       |
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
| coordinates | [JSVec3Array](../core/jsvec3array.md)      | 건물 밑면 다각형 좌표 목록 (3개 이상)  |
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

## Panel Sunshine Analysis

> 설치된 태양광 패널의 일조 시간을 분석하는 API 묶음입니다. 분석 계산은 Web Worker에서 비동기로 수행되므로 분석 중에도 지도를 조작할 수 있습니다.
>
> 아래 함수들은 모두 소문자로 시작하는 이름과 대문자로 시작하는 이름(예: `startPanelSunshine` / `StartPanelSunshine`)이 같은 기능으로 바인딩되어 있습니다.

**분석 대상 패널**

다음 패널이 모두 한 번에 분석 대상이 됩니다. 분석 대상이 하나도 없으면 시작할 수 없습니다.

| kind | 대상 | id 형식 |
|------|------|---------|
| `roof` | 선택된 옥상에 설치된 패널 (활성 지붕, 사용 중인 모듈세트만) | `roof_{지붕}_{세트}_{모듈}` |
| `terrain` | 지형에 설치된 패널 ([buildModuleOnTerrain()](#buildmoduleonterrain-section-sectioncount-sectionset-moduleangle-deployangle-boolean)) | `terrain_{세트}_{모듈}` |
| `wall` | 벽면/베란다 패널 (레이어에 등록된 태양광 패널 객체) | `wall_{레이어명}_{객체키}` |

**사용 흐름**

1. `Module.initialize()`의 `worker` 옵션을 켭니다 (`worker.use: true`, `worker.path`). 워커가 꺼져 있으면 동기 폴백 없이 오류 문자열을 반환합니다.
2. 패널을 설치합니다 ([startModuleArrayAsync()](#startmodulearrayasync-section-sectioncount-sectionset-string) 등). 옥상 패널은 비동기 배치가 끝나는 시점에 주변 지물이 자동으로 캡처됩니다.
3. (선택) 옵션을 설정합니다: [setPanelSunshineStrict()](#setpanelsunshinestrict-mode-void), [setPanelSunshineSelfShadow()](#setpanelsunshineselfshadow-use-void), [setPanelSunshineColoring()](#setpanelsunshinecoloring-use-void).
4. (선택) 건물이 로드되어 있는 상태에서 [capturePanelSunshineCasters()](#capturepanelsunshinecasters-string)를 호출해 그림자를 만드는 주변 지물을 저장해 둡니다. 카메라가 멀어져 건물 타일이 언로드되어도 저장된 지물은 계속 분석에 반영됩니다.
5. [progressPanelSunshine()](#progresspanelsunshine-callback-string), [completePanelSunshine()](#completepanelsunshine-callback-string)로 콜백을 등록합니다.
6. [startPanelSunshine()](#startpanelsunshine-starttime-endtime-interval-string)으로 분석을 시작합니다. `"success"`이면 즉시 반환됩니다.
7. 진행률 콜백이 반복 호출되고, 마지막에 완료 콜백이 호출됩니다. 옵션이 켜져 있으면 이때 패널이 일조율에 따라 색칠됩니다.
8. 완료 콜백에서 [getPanelSunshineResult()](#getpanelsunshineresult-string)로 결과 JSON을 읽습니다.
9. 결과와 색을 지우려면 [clearPanelSunshine()](#clearpanelsunshine-void)을 호출합니다.

### capturePanelSunshineCasters() → string

> 현재 메모리에 로드되어 있는 주변 지물(그림자를 만드는 건물 등)의 삼각형을 일조분석용 저장소에 담습니다. 이미 저장된 지물은 최신 지오메트리로 갱신하고, 없는 지물은 추가합니다.
>
> 타일 레이어 건물은 카메라가 멀어지면 언로드되어 삼각형이 사라지므로, 건물이 로드되어 있는 동안 저장해 두어야 나중에 어디서 분석을 실행해도 같은 결과가 나옵니다. `startPanelSunshine()`을 호출할 때도 자동으로 한 번 캡처합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `string`: 캡처 결과 `"captured {이번에 담은 지물 수}, stored {저장소 전체 지물 수}"`
  - 설치된 패널이 하나도 없으면 `"no installed panel"`
  - 지물은 `(레이어명|객체키)`로 관리되며, 객체 키가 없는 지물과 그림자 생성 대상이 아닌 지물은 제외됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
var info = Module.GetSolarManager().capturePanelSunshineCasters();
console.log(info); // 예: "captured 128, stored 128"
```
{% endtab %}
{% endtabs %}

### clearPanelSunshineCasters() → void

> 일조분석용 주변 지물 저장소를 비웁니다.
>
> [clearPanelSunshine()](#clearpanelsunshine-void)은 저장소를 지우지 않으므로, 저장된 지물을 버리려면 이 함수를 호출해야 합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - 없음

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().clearPanelSunshineCasters();
```
{% endtab %}
{% endtabs %}

### getPanelSunshineCasterCount() → number

> 일조분석용 저장소에 담긴 주변 지물의 개수를 반환합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `number`: 저장소에 담긴 지물 수. 아무것도 저장하지 않았으면 `0`

{% endtab %}
{% tab title="Template" %}
```javascript
var count = Module.GetSolarManager().getPanelSunshineCasterCount();
```
{% endtab %}
{% endtabs %}

### setPanelSunshineStrict(mode) → void

> 패널의 일조 판정 기준을 설정합니다. 기본값은 `301`(NORMAL)입니다.
>
> 각 패널은 중점 1개와 모서리 4개, 총 5개의 검사점으로 판정합니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type   | Description |
|------|--------|-------------|
| mode | number | 판정 기준. `300`: BRIEF (중점 1개만 검사), `301`: NORMAL (검사점 5개 중 절반 이상, 즉 3개 이상이 일조일 때 일조), `302`: DETAIL (검사점 5개 모두가 일조일 때만 일조) |

- Return
  - 없음
  - `300`, `301`, `302` 이외의 값은 무시되며 기존 설정이 유지됩니다.
  - 값 정의는 [Shadow Analysis Type List](../etc/type-list.md#shadow-analysis-type-list)와 같습니다. 해당 표는 격자 기준 설명이고, 패널에서는 위와 같이 적용됩니다.
  - 분석을 시작할 때의 설정이 사용됩니다. 진행 중인 분석에는 영향을 주지 않습니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().setPanelSunshineStrict(301);
```
{% endtab %}
{% endtabs %}

### setPanelSunshineSelfShadow(use) → void

> 패널끼리 서로 만드는 그림자(앞줄 패널이 뒷줄 패널을 가리는 효과)를 분석에 포함할지 설정합니다. 기본값은 `true`입니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description |
|------|---------|-------------|
| use  | boolean | `true`: 패널 상호 그림자 포함, `false`: 주변 지물의 그림자만 반영 |

- Return
  - 없음
  - 분석을 시작할 때의 설정이 사용됩니다. 진행 중인 분석에는 영향을 주지 않습니다.
  - 자기 자신이 만드는 그림자는 어느 경우에도 자신의 판정에 영향을 주지 않습니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().setPanelSunshineSelfShadow(true);
```
{% endtab %}
{% endtabs %}

### setPanelSunshineColoring(use) → void

> 분석이 끝났을 때 결과를 패널 색으로 표시할지 설정합니다. 기본값은 `true`입니다.
>
> 색은 패널 텍스처에 곱해지며, 일조율(`ratio`)에 따라 아래 표와 같이 칠해집니다.

{% tabs %}
{% tab title="Information" %}

| Name | Type    | Description |
|------|---------|-------------|
| use  | boolean | `true`: 완료 시 패널을 일조율 색으로 표시, `false`: 색을 바꾸지 않음 |

| 일조율 (ratio) | 등급 | 색상 (R, G, B) |
|----------------|------|----------------|
| 0.8 이상 | 매우 양호 | 255, 214, 40 |
| 0.6 이상 ~ 0.8 미만 | 양호 | 255, 170, 45 |
| 0.4 이상 ~ 0.6 미만 | 보통 | 245, 120, 60 |
| 0.2 이상 ~ 0.4 미만 | 불량 | 150, 110, 180 |
| 0.2 미만 | 매우 불량 | 70, 95, 150 |

- Return
  - 없음
  - 칠해진 색은 [clearPanelSunshine()](#clearpanelsunshine-void)으로 원래대로(흰색) 되돌립니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().setPanelSunshineColoring(true);
```
{% endtab %}
{% endtabs %}

### progressPanelSunshine(callback) → string

> 패널 일조분석의 진행률 콜백을 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description                                                                 |
|----------|----------|-----------------------------------------------------------------------------|
| callback | function | 진행률 콜백. 인자로 진행률(`number`, %)이 전달됩니다. |

- Return
  - `string`: 항상 `"success"`
  - 이미 등록된 콜백이 있으면 새 콜백으로 교체됩니다. 등록한 콜백은 분석이 끝나도 해제되지 않습니다.
  - 진행률은 분석 종료 시각의 시/분/초 대비 현재 분석 시각의 시/분/초 비율(%)로 계산되므로, 분석 구간이 하루를 넘으면 단조 증가하지 않을 수 있고 마지막 단계에서 `100`을 넘을 수 있습니다. 대략적인 표시용으로 사용하십시오.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().progressPanelSunshine(function (percent) {
    console.log("일조분석 진행률: " + Math.min(100, percent).toFixed(0) + "%");
});
```
{% endtab %}
{% endtabs %}

### completePanelSunshine(callback) → string

> 패널 일조분석의 완료 콜백을 등록합니다.

{% tabs %}
{% tab title="Information" %}

| Name     | Type     | Description                                                              |
|----------|----------|--------------------------------------------------------------------------|
| callback | function | 완료 콜백. 인자로 결과 패널 수(`number`)가 전달됩니다. |

- Return
  - `string`: 항상 `"success"`
  - 이미 등록된 콜백이 있으면 새 콜백으로 교체됩니다. 등록한 콜백은 분석이 끝나도 해제되지 않습니다.
  - 콜백은 결과 반영과 패널 색칠([setPanelSunshineColoring()](#setpanelsunshinecoloring-use-void))이 끝난 뒤에 호출되므로, 콜백 안에서 `getPanelSunshineResult()`로 완성된 결과를 읽을 수 있습니다.
  - 분석 도중 `clearPanelSunshine()`이 호출되면 결과 목록이 비어 있으므로 인자로 `0`이 전달됩니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().completePanelSunshine(function (panelCount) {
    console.log("분석 완료: 패널 " + panelCount + "개");
});
```
{% endtab %}
{% endtabs %}

### startPanelSunshine(startTime, endTime, interval) → string

> 설치된 패널의 일조분석을 비동기(Web Worker)로 시작합니다. 지정한 시간 구간을 `interval`분 간격으로 나누어 각 시각에 태양이 패널을 비추는지 판정합니다.
>
> 시작 시점에 주변 지물이 자동으로 한 번 캡처되어 저장소에 합쳐지며, 분석은 항상 저장소의 지물을 기준으로 수행됩니다.

{% tabs %}
{% tab title="Information" %}

| Name      | Type                                | Description                              |
|-----------|-------------------------------------|------------------------------------------|
| startTime | [JSDateTime](../core/jsdatetime.md) | 분석 시작 시각                           |
| endTime   | [JSDateTime](../core/jsdatetime.md) | 분석 종료 시각. `startTime`보다 늦어야 함 |
| interval  | number                              | 분석 시간 간격 (분 단위, 1 이상의 정수)  |

- Return
  - `string`: 시작 결과. 성공 시 `"success"`, 실패 시 아래 사유 문자열

  | 반환값 | 의미 |
  |--------|------|
  | `"success"` | 워커에 분석을 요청함 |
  | `"error map load"` | 엔진 또는 SolarManager가 준비되지 않음 |
  | `"already running"` | 이전 일조분석이 아직 진행 중 |
  | `"interval must be greater than 0"` | `interval`이 0 이하 |
  | `"web worker is disabled - set Module.initialize({worker:{use:true, path:...}})"` | web worker 미사용 또는 경로 미설정 |
  | `"no installed panel"` | 분석할 패널이 없음 |
  | `"end time must be later than start time"` | `endTime`이 `startTime`보다 늦지 않음 |
  | `"failed to create web worker"` | 워커 생성 실패 |

- 동작 참고
  - 시작 직후부터 `getPanelSunshineResult()`로 패널 목록과 위치를 조회할 수 있으며, 완료 전까지 일조 값은 `0`입니다. 이때 `running`은 `true`입니다.
  - 태양 위치는 패널 자신의 위치 기준으로 계산하며, 야간이거나 태양 고도 제한([SetLimitSunAngle()](../analysis/jsanalysis.md#setlimitsunangle-enable-angle), 기본 꺼짐)에 걸리는 시각은 미일조로 처리됩니다.
  - 워커가 빈 응답을 돌려주는 오류가 발생하면 진행 상태만 해제되고 완료 콜백은 호출되지 않습니다.
  - 일조 판정 기준은 [setPanelSunshineStrict()](#setpanelsunshinestrict-mode-void), 패널 상호 그림자는 [setPanelSunshineSelfShadow()](#setpanelsunshineselfshadow-use-void)에 따릅니다.

{% endtab %}
{% tab title="Template" %}
```javascript
var solar = Module.GetSolarManager();

// 1. 옵션 (선택)
solar.setPanelSunshineStrict(301);
solar.setPanelSunshineSelfShadow(true);
solar.setPanelSunshineColoring(true);

// 2. 주변 건물이 로드되어 있을 때 지물 저장 (선택)
console.log(solar.capturePanelSunshineCasters());

// 3. 콜백 등록
solar.progressPanelSunshine(function (percent) {
    console.log("진행률: " + Math.min(100, percent).toFixed(0) + "%");
});

solar.completePanelSunshine(function (panelCount) {
    // 5. 결과 조회
    var result = JSON.parse(solar.getPanelSunshineResult());
    console.log("패널 " + result.count + "개, 평균 일조 " + result.summary.averageSunMinutes + "분");
});

// 4. 분석 시작 (06:00 ~ 19:00, 30분 간격)
var startTime = new Module.JSDateTime(2026, 6, 21, 6, 0, 0);
var endTime = new Module.JSDateTime(2026, 6, 21, 19, 0, 0);
var ret = solar.startPanelSunshine(startTime, endTime, 30);
if (ret !== "success") {
    console.error("일조분석 시작 실패: " + ret);
}
```
{% endtab %}
{% endtabs %}

### getPanelSunshineResult() → string

> 패널 일조분석 결과를 JSON 문자열로 반환합니다. 분석 진행 중에도 호출할 수 있으며, 분석을 한 번도 하지 않았거나 `clearPanelSunshine()` 이후에는 패널 목록이 비어 있습니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - `string`: 아래 구조의 JSON 문자열 (`JSON.parse()`로 변환하여 사용)

**최상위 객체**

| Field | Type | Description |
|-------|------|-------------|
| running | boolean | 분석 진행 중 여부 |
| interval | number | 마지막으로 요청한 분석 간격 (분). 분석을 시작한 적이 없으면 `30` |
| totalMinutes | number | 분석 구간 전체 길이 (분) = (종료 시각 - 시작 시각). 결과가 없으면 `0` |
| strict | number | 현재 설정된 판정 기준 (`300`, `301`, `302`) |
| selfShadow | boolean | 현재 설정된 패널 상호 그림자 포함 여부 |
| casterCount | number | 마지막 분석에서 실제로 사용한 그림자 객체 수 (주변 지물 + 패널 자신) |
| casterSceneCount | number | 위 중 주변 지물(건물 등)의 수 |
| casterStored | number | 현재 저장소에 캡처된 지물 수 |
| count | number | 결과 패널 수 |
| summary | object | 전체 요약 (아래 표) |
| panels | array | 패널별 결과 (아래 표) |

**summary**

| Field | Type | Description |
|-------|------|-------------|
| averageSunMinutes | number | 패널 평균 일조 시간 (분) |
| averageDirectMinutes | number | 패널 평균 직달 가중 일조 시간 (분) |
| minSunMinutes | number | 최소 일조 시간 (분) |
| maxSunMinutes | number | 최대 일조 시간 (분) |

**panels 항목**

| Field | Type | Description |
|-------|------|-------------|
| id | string | 패널 식별자 (`roof_...`, `terrain_...`, `wall_...`) |
| kind | string | 패널 종류. `"roof"`, `"terrain"`, `"wall"` (벽면/베란다 공용) |
| sunMinutes | number | 일조 시간 (분). 일조로 판정된 시각마다 `interval`을 누적한 값 |
| continueMinutes | number | 최대 연속 일조 시간 (분) |
| directMinutes | number | 직달 가중 일조 시간 (분). 일조 시각마다 (패널 상면 법선과 태양 방향의 코사인, 음수는 0) x `interval`을 누적한 값 |
| ratio | number | 일조율 = `sunMinutes` / `totalMinutes`. 분석 구간이 `interval`로 나누어떨어지지 않으면 `1`을 넘을 수 있음 |
| position | object | 패널 중점 위치 `{ lon, lat, alt }` (경도, 위도, 고도 meters) |
| samples | array | 시각별 판정 목록 `[{ time, sunrise }]`. `time`은 `"HH:MM"` 형식의 현지 시각 문자열이고, `sunrise`는 해당 시각의 일조 여부(`true`/`false`)입니다. 필드 이름과 달리 일출이 아니라 일조 여부를 의미합니다. |

```json
{
  "running": false,
  "interval": 30,
  "totalMinutes": 780,
  "strict": 301,
  "selfShadow": true,
  "casterCount": 215,
  "casterSceneCount": 128,
  "casterStored": 128,
  "count": 1,
  "summary": {
    "averageSunMinutes": 420.0,
    "averageDirectMinutes": 310.5,
    "minSunMinutes": 420,
    "maxSunMinutes": 420
  },
  "panels": [
    {
      "id": "roof_0_0_0",
      "kind": "roof",
      "sunMinutes": 420,
      "continueMinutes": 300,
      "directMinutes": 310.5,
      "ratio": 0.538,
      "position": { "lon": 127.0012, "lat": 37.5003, "alt": 32.1 },
      "samples": [
        { "time": "06:00", "sunrise": false },
        { "time": "06:30", "sunrise": true }
      ]
    }
  ]
}
```

{% endtab %}
{% tab title="Template" %}
```javascript
var result = JSON.parse(Module.GetSolarManager().getPanelSunshineResult());

result.panels.forEach(function (panel) {
    console.log(panel.id, panel.sunMinutes + "분", (panel.ratio * 100).toFixed(1) + "%");
});
```
{% endtab %}
{% endtabs %}

### clearPanelSunshine() → void

> 패널 일조분석 결과를 지우고 패널 색을 원래(흰색)로 되돌립니다.
>
> 주변 지물 저장소는 지우지 않으므로 다시 분석할 때 재사용됩니다. 저장소를 비우려면 [clearPanelSunshineCasters()](#clearpanelsunshinecasters-void)를 호출합니다.

{% tabs %}
{% tab title="Information" %}

- Return
  - 없음
  - 분석 진행 중에 호출하면 진행 상태가 해제되고 결과가 지워지지만, 워커의 계산 자체를 취소하지는 않습니다. 이후 도착하는 응답은 결과에 반영되지 않으며 완료 콜백만 패널 수 `0`으로 호출될 수 있습니다.

{% endtab %}
{% tab title="Template" %}
```javascript
Module.GetSolarManager().clearPanelSunshine();
```
{% endtab %}
{% endtabs %}