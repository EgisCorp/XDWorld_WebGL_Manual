---
description: Fire_이벤트 정리
---

# EVENT

## 기본 Event

> HTML Canvas 이벤트 등록으로 엔진과 연동되는 이벤트

```javascript
var canvas = document.createElement('canvas');
canvas.id = "canvas";
	
canvas.addEventListener("Fire_~~~~", function(e){
		// 기능 구현
});
```

| Index | Name                      | Description       |
| ----- | ------------------------- | ----------------- |
| 0     | Fire\_EventSelectedObject | 객체 선택 시 이벤트       |
| 1     | Fire\_EventRotateCompass  | 나침반 회전 시 이벤트      |
| 2     | Fire\_EventCameraMoveEnd  | 카메라 이동 종료 시 이벤트   |
| 3     | Fire\_JSEventResize       | 캔버스 리사이즈 시 이벤트    |
| 4     | Fire\_EventAddRadius      | 수직 평면 반경 생성 시 이벤트 |

## Gost Symbol Event

> 고스트 심볼 이벤트 등록으로 엔진과 연동되는 이벤트

```javascript
var canvas = document.createElement('canvas');
canvas.id = "canvas";
canvas.addEventListener("Fire__GhostSymbolRegistComplete", function(e){
		// 기능 구현
});

~
Module.getGhostSymbolMap().addGhostSymbolBy3DS()
~
	
```

| Index | Name                            | Description     |
| ----- | ------------------------------- | --------------- |
| 0     | Fire\_GhostSymbolRegistComplete | 고스트 심볼 등록 시 이벤트 |
