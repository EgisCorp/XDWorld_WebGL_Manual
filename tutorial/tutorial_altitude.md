# 높이 측정하기

마우스 모드를 높이측정 모드로 변경한 후 클릭지점 높이를 측정합니다. 측정결과값을 이벤트로 반환받아 POI로 가시화합니다.

## Global 변수
```
var GLOBAL = {
	Symbol : null,		// 아이콘 관리 심볼 객체
	Layer : null,		// POI 저장 레이어
	nIndex : 0			// POI, Icon 생성 인덱스
};
```

## step 1. 레이어 생성

높이측정 Icon 및 높이값을 가시화할 레이어를 생성합니다.

레이어 타입에 대한 설명은 [여기](../etc/type-list.md)를 참조해 주십시오.

```
var layerList = new Module.JSLayerList(true);

GLOBAL.Layer = layerList.createLayer("MEASURE_POI", Module.ELT_3DPOINT);
GLOBAL.Layer.setMaxDistance(20000.0);
GLOBAL.Layer.setSelectable(false);
```

## step 2. 이벤트 등록

엔진 내부에서 계산된 높이을 반환받기 위해 이벤트를 등록합니다.

```
function initEvent(canvas) {
	canvas.addEventListener("Fire_EventAddAltitudePoint", function(e){

		createPOI( new Module.JSVector3D(e.dLon, e.dLat, e.dAlt),
				   "rgba(10, 10, 0, 0.5)",
				   e.dGroundAltitude, e.dObjectAltitude );
	});
}
```

## step 3. 마우스모드 변경

높이측정을 위해서 마우스 모드를 변경합니다.

마우스 모드에 대한 설명은 [여기](../etc/type-list.md)를 참조해 주십시오.

```javascript
Module.XDSetMouseState(Module.MML_ANALYS_ALTITUDE);
```

## step 4 - 1. 높이 Icon 생성

반환 받은 높이값을 랜더링하기 위해 Icon을 생성합니다.

```
function drawIcon(_canvas, _color, _value, _subValue) {

	// 컨텍스트 반환 및 배경 초기화
	var ctx = _canvas.getContext('2d'),
		width = _canvas.width,
		height = _canvas.height
		;
	ctx.clearRect(0, 0, width, height);

	// 배경과 높이 값 텍스트 그리기
	if (_subValue == -1) {
		drawRoundRect(ctx, 50, 20, 100, 20, 5, _color);		// 오브젝트 높이 값이 유효하지 않는 경우

	} else {
		drawRoundRect(ctx, 50, 5, 100, 35, 5, _color);		// 오브젝트 높이 값이 유효한 경우
		setText(ctx, width*0.5, height*0.2, '지면고도 : ' + setKilloUnit(_subValue, 0.001, 0));
	}
	setText(ctx, width*0.5, height*0.2+15, '해발고도 : '+ setKilloUnit(_value, 0.001, 0));

	// 위치 표시 점 그리기
	drawDot(ctx, width, height);

	return ctx.getImageData(0, 0, _canvas.width, _canvas.height).data;
}
```

## step 4 - 2. 높이 Point Icon 생성

높이측정한 위치를 가시화하기위한 Point Icon을 생성합니다.

```
function drawDot(ctx, width, height) {

	ctx.beginPath();
    ctx.lineWidth = 6;
    ctx.arc(width*0.5, height*0.5, 2, 0, 2*Math.PI, false);
	ctx.closePath();

	ctx.fillStyle = 'rgba(255, 0, 0, 0.8)';
	ctx.fill();
	ctx.lineWidth = 8;
	ctx.strokeStyle = "rgba(255, 255, 0, 0.8)";
	ctx.stroke();
}
```

## step 4 - 3. 높이 사각형 Icon 생성

반환 받은 높이값을 가시화하기 위해 사각형 Icon을 생성합니다.

```
function drawRoundRect(ctx,
					   x, y,
					   width, height, radius,
					   color) {

	if (width < 2 * radius) 	radius = width * 0.5;
	if (height < 2 * radius) 	radius = height * 0.5;

	ctx.beginPath();
	ctx.moveTo(x+radius, y);
	ctx.arcTo(x+width, 	y, 	 		x+width, 	y+height, 	radius);
	ctx.arcTo(x+width, 	y+height, 	x,		 	y+height, 	radius);
	ctx.arcTo(x, 	 	y+height, 	x,   		y,   		radius);
	ctx.arcTo(x,	   	y,   	 	x+width, 	y,   		radius);
	ctx.closePath();

	// 사각형 그리기
	ctx.fillStyle = color;
    ctx.fill();

	return ctx;
}
```

## step 4 - 4. 높이 측정결과값 Icon 생성

반환 받은 높이값을 사각형 Icon에 생성합니다.

```
function setText(_ctx, _posX, _posY, _strText) {

	_ctx.font = "bold 12px sans-serif";
    _ctx.textAlign = "center";

	_ctx.fillStyle = "rgb(255, 255, 255)";
    _ctx.fillText(_strText, _posX, _posY);
}
```

## step 4 - 5. 높이 측정결과값 m/km 텍스트로 변환

반환 받은 높이값을 m/km 텍스트로 변환합니다.

```
function setKilloUnit(_text, _meterToKilloRate, _decimalSize){

	if (_decimalSize < 0){
		_decimalSize = 0;
	}
	if (typeof _text == "number") {
		if (_text < 1.0/(_meterToKilloRate*Math.pow(10,_decimalSize))) {
			_text = _text.toFixed(1).toString()+'m';
		} else {
			_text = (_text*_meterToKilloRate).toFixed(2).toString()+'㎞';
		}
	}
	return _text;
}
```

## step 5. 높이 객체 생성

생성한 Icon으로 객체를 만들고 레이어에 추가합니다.

```
function createPOI(_position, _color, _value, _subValue) {

	// POI 아이콘 이미지를 그릴 Canvas 생성
	var drawCanvas = document.createElement('canvas');
    drawCanvas.width = 200;
    drawCanvas.height = 100;

	// 아이콘 이미지 데이터 반환
	var imageData = drawIcon(drawCanvas, _color, _value, _subValue),
		nIndex = GLOBAL.nIndex
		;

	// 심볼에 아이콘 이미지 등록
	if (GLOBAL.Symbol.insertIcon("Icon"+nIndex, imageData, drawCanvas.width, drawCanvas.height)) {

		// 등록한 아이콘 객체 반환
		var icon = GLOBAL.Symbol.getIcon("Icon"+nIndex);

		// JSPoint 객체 생성
		var count = GLOBAL.Layer.getObjectCount(),
			poi = Module.createPoint("POI"+nIndex)
			;

		poi.setPosition(_position);		// 위치 설정
		poi.setIcon(icon);				// 아이콘 설정

		// 레이어에 오브젝트 추가
		GLOBAL.Layer.addObject(poi, 0);

		// 인덱스 값 상승
		GLOBAL.nIndex++;
	}
}
```

