---
description: ARGB 색상을 정의합니다.
---

# JSColor

> new Module.Color API 생성.
> 
> JSColor 생성 시 기본값 ARGB(255, 255, 255, 255) 설정.

```javascript
var color = new Module.JSColor(255, 100, 100, 0); // ARGB

var color = new Module.JSColor(100, 100, 0);	// RGB

var color = new Module.JSColor();
```

## properties

| Name | Type | Description |
| :--- | :--- | :--- |
| a | number | alpha 색상 값 |
| r | number | red 색상 값 |
| g | number | green 색상 값 |
| b | number | blue 색상 값 |