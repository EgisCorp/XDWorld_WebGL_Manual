---
description: 바람 흐름 생성 및 설정 기능 API.
---

# JSFlow

> Module.getFlow API 호출 후, JSFigure.SetFlowVisible API를 사용하여 가시화.
> 가시화 후 JSFigure.setJSON API에 파라메터를 전달하여 바람장 생성.
> 
> [샌드박스_JSFlow(바람 표현)](https://sandbox.dtwincloud.com/code/main.do?id=effect_wind_path)
>
> 파라메터는 [JSFlow.FlowDataOption](jsflow.md#jsflow.flowdataoption) 참고

```javascript
let flow = Module.getFlow();
Module.GetFlowVisible(true);

// 파라메터 생략. 샌드박스의 setWindLegendLoad()/setWindBandLoad()에서 확인
let flowParam = ...
flow.setJSON(flowParam);
```

### Type Definitions

#### JSFlow.FlowDataOption

> 흐름 데이터 요청 파라메터

| Name | Type | Attributes | Default | Description |
| --------- | --- | --- | --- | --- |
| kind      | string | | | 격자 데이터 그룹명 |
| timeIndex |number | | | 격자데이터 시게열 인덱스 번호 (정수형) |
| timeRange | number | | | 격자데이터 시계열 총수 (정수형) |
| callback  | function | optional | | 격자데이터가 모두 로딩되면 발생하는 콜백 함수 |
| cols | number | | | 격자의 가로 셀 총수 (정수형) |
| rows | number | | | 격자의 세로 셀 총수 (정수형) |
| size | number | | | 격자의 셀 가로,세로 크기 (단위 : 미터)  |
