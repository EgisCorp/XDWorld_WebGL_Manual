---
description: JSEnum.cpp에 등록된 Module 전역 상수(Enum) 목록입니다.
---

# Enum / Constants List

> 이 문서는 `JSObject/JSEnum.cpp`에서 `constant("이름", 값)` 형태로 `Module` 객체에 직접 등록되는 전역 상수 목록을 카테고리별로 정리한 참고 문서입니다.
>
> 아래 상수들은 모두 `Module.상수이름` 형태로 접근합니다(예: `Module.JS_KEYBOARD_UP`).
>
> 이미 이름과 함께 정리되어 있는 카테고리(레이어 타입, 타일 레이어 타입, 네비게이션 위치/가시화 옵션, 마우스 모드, JSFigure 타입, 좌표계 타입, 그림자 분석 타입)는 [Type List](type-list.md) 문서를 참고하십시오.

## Keyboard Control Mask (JS_KEYBOARD_\*)

> 키보드 이동 방향/동작을 나타내는 비트마스크 값입니다.

| Name                     | Description             |
| ------------------------ | ------------------------ |
| JS_KEYBOARD_MASK         | 값 마스크(내부 비트 연산용). |
| JS_KEYBOARD_UP           | 위쪽 이동.                |
| JS_KEYBOARD_DOWN         | 아래쪽 이동.              |
| JS_KEYBOARD_LEFT         | 왼쪽 이동.                |
| JS_KEYBOARD_RIGHT        | 오른쪽 이동.              |
| JS_KEYBOARD_ZOOMIN       | 확대.                    |
| JS_KEYBOARD_ZOOMOUT      | 축소.                    |
| JS_KEYBOARD_TILTUP       | 카메라 틸트 위로.          |
| JS_KEYBOARD_TILTDOWN     | 카메라 틸트 아래로.        |
| JS_KEYBOARD_ROTATELEFT   | 왼쪽으로 회전.            |
| JS_KEYBOARD_ROTATERIGHT  | 오른쪽으로 회전.          |

## Selectable Option (JS_SELECTABLE_\*)

| Name                | Description        |
| -------------------- | ------------------ |
| JS_SELECTABLE_MASK   | 값 마스크(내부 비트 연산용). |
| JS_SELECTABLE_OFF    | 선택 불가.          |
| JS_SELECTABLE_ON     | 선택 가능.          |
| JS_SELECTABLE_ERROR  | 오류 값.            |

## Editable Option (JS_EDITABLE_\*)

| Name              | Description   |
| ------------------ | ------------------ |
| JS_EDITABLE_MASK   | 값 마스크(내부 비트 연산용). |
| JS_EDITABLE_OFF    | 편집 불가.          |
| JS_EDITABLE_ON     | 편집 가능.          |

## Option Quality (JS_OPTION_\*)

> 품질/옵션 등급을 나타내는 비트마스크 값입니다.

| Name              | Description  |
| ------------------ | ----------------- |
| JS_OPTION_MASK     | 값 마스크(내부 비트 연산용). |
| JS_OPTION_DISABLE  | 비활성화.          |
| JS_OPTION_MIDDLE   | 중간 품질/등급.     |
| JS_OPTION_HIGH     | 높은 품질/등급.     |

## Object Type (JS_OBJECT_\*)

> 객체의 대분류 타입 값입니다.

| Name                 | Description   |
| --------------------- | ------------------ |
| JS_OBJECT_MASK        | 값 마스크(내부 비트 연산용). |
| JS_OBJECT_POINT       | 포인트 객체.       |
| JS_OBJECT_LINESTRING  | 선(라인) 객체.     |
| JS_OBJECT_POLYGON     | 평면(폴리곤) 객체.  |
| JS_OBJECT_MODEL       | 모델(3D) 객체.     |
| JS_OBJECT_SYMBOL      | 심볼 객체.         |

## Text Style Edge (JS_TEXTSTYLE_EDGE_\*)

> 문자(텍스트) 스타일의 외곽선 표현 방식입니다.

| Name                         | Description                     |
| ----------------------------- | -------------------------------- |
| JS_TEXTSTYLE_EDGE_MASK        | 값 마스크(내부 비트 연산용).      |
| JS_TEXTSTYLE_EDGE_NONE        | 외곽선 없음.                     |
| JS_TEXTSTYLE_EDGE_LINE        | 외곽선(라인)만 표시.              |
| JS_TEXTSTYLE_EDGE_FILL        | 채움만 표시.                      |
| JS_TEXTSTYLE_EDGE_LINEFILL    | 외곽선과 채움 모두 표시.          |

## Text Style Font (JS_TEXTSTYLE_FONT_\*)

| Name                        | Description  |
| ----------------------------- | ----------------- |
| JS_TEXTSTYLE_FONT_MASK        | 값 마스크(내부 비트 연산용). |
| JS_TEXTSTYLE_FONT_BOLD        | 굵게(Bold).        |
| JS_TEXTSTYLE_FONT_ITALIC      | 기울임(Italic).    |
| JS_TEXTSTYLE_FONT_UNDERLINE   | 밑줄(Underline).   |

## View Top/Down (JS_VIEW_TD_\*)

> 카메라 시점(하늘 뷰/지상 뷰 등)과 관련된 값입니다.

| Name              | Description        |
| ------------------ | ------------------------ |
| JS_VIEW_TD_MASK    | 값 마스크(내부 비트 연산용). |
| JS_VIEW_TD_SKY     | 하늘에서 내려다보는 시점.  |
| JS_VIEW_FT_GROUND  | 지상 기준 시점.           |
| JS_VIEW_FT_SKY     | 하늘 기준 시점.           |

## Frustum Face Type (FRUSTUM_FACE_TYPE_\*)

> [JSViewFrustum.getPlaneEdge()](../object/jsviewfrustum.md#getplaneedgeplanetype-jsvec3array-core-jsvec3arraymd)의 `planeType` 인자에 사용되는 절두체 평면 종류 값입니다.

| Name                        | Description  |
| ----------------------------- | ------------------ |
| FRUSTUM_FACE_TYPE_NEAR         | 근평면(Near).       |
| FRUSTUM_FACE_TYPE_FAR          | 원평면(Far).        |
| FRUSTUM_FACE_TYPE_RIGHT        | 오른쪽 평면.        |
| FRUSTUM_FACE_TYPE_TOP          | 위쪽 평면.          |
| FRUSTUM_FACE_TYPE_LEFT         | 왼쪽 평면.          |
| FRUSTUM_FACE_TYPE_BOTTOM       | 아래쪽 평면.        |

## WebGL Texture Wrap Mode (GL_\*)

> 표준 WebGL(OpenGL ES) 텍스처 래핑(Wrap) 모드 상수를 그대로 노출한 값입니다.

| Name                  | Description                                  |
| ----------------------- | --------------------------------------------- |
| GL_REPEAT               | 텍스처 좌표 범위를 벗어나면 반복.               |
| GL_MIRRORED_REPEAT      | 텍스처 좌표 범위를 벗어나면 대칭 반복.          |
| GL_CLAMP_TO_EDGE        | 텍스처 좌표 범위를 벗어나면 가장자리 픽셀로 고정. |

## Road Type (ROAD_\*)

> 도로 객체 생성 API의 도로 형태 옵션 값입니다.

| Name          | Description  |
| -------------- | ----------------- |
| ROAD_OVERPASS  | 고가도로(육교/고가). |
| ROAD_TUNNEL    | 터널.              |
| ROAD_UNDERPASS | 지하차도.          |
| ROAD_BRIDGE    | 교량.              |

## Line Effect Type

> [JSLineString.setLineType()](../object/jslinestring.md#setlinetypetype)에서 사용되는 라인 효과 타입 값입니다. 상세 설명은 해당 문서를 참고하십시오.

| Name    | Value | Description |
| ------- | ----- | ------------ |
| NORMAL  | 0     | 일반 실선.   |
| OUTLINE | 1     | 외곽선.      |
| GLOW    | 2     | 발광 효과.   |
| ARROW   | 3     | 화살표.      |
| DASH    | 4     | 점선.        |
| FIRE    | 5     | 불꽃 효과.   |
| TWINKLE | 6     | 반짝임 효과. |
| WARNING | 7     | 경고 표시.   |

## Colors (COLOR_\*)

> CSS 표준 색상 이름을 그대로 사용한 [JSColor](jscolor.md) 상수 목록입니다(약 140여 개). 값은 각각 R, G, B(알파 255 고정)로 구성됩니다.

| Name | RGB | Name | RGB | Name | RGB |
| --- | --- | --- | --- | --- | --- |
| COLOR_MAROON | 128,0,0 | COLOR_DARKRED | 139,0,0 | COLOR_BROWN | 165,42,42 |
| COLOR_FIREBRICK | 178,34,34 | COLOR_CRIMSON | 220,20,60 | COLOR_RED | 255,0,0 |
| COLOR_TOMATO | 255,99,71 | COLOR_CORAL | 255,127,80 | COLOR_INDIANRED | 205,92,92 |
| COLOR_LIGHTCORAL | 240,128,128 | COLOR_DARKSALMON | 233,150,122 | COLOR_SALMON | 250,128,114 |
| COLOR_LIGHTSALMON | 255,160,122 | COLOR_ORANGERED | 255,69,0 | COLOR_DARKORANGE | 255,140,0 |
| COLOR_ORANGE | 255,165,0 | COLOR_GOLD | 255,215,0 | COLOR_DARKGOLDENROD | 184,134,11 |
| COLOR_GOLDENROD | 218,165,32 | COLOR_PALEGOLDENROD | 238,232,170 | COLOR_DARKKHAKI | 189,183,107 |
| COLOR_KHAKI | 240,230,140 | COLOR_OLIVE | 128,128,0 | COLOR_YELLOW | 255,255,0 |
| COLOR_YELLOWGREEN | 154,205,50 | COLOR_DARKOLIVEGREEN | 85,107,47 | COLOR_OLIVEDRAB | 107,142,35 |
| COLOR_LAWNGREEN | 124,252,0 | COLOR_CHARTREUSE | 127,255,0 | COLOR_GREENYELLOW | 173,255,47 |
| COLOR_DARKGREEN | 0,100,0 | COLOR_GREEN | 0,128,0 | COLOR_FORESTGREEN | 34,139,34 |
| COLOR_LIME | 0,255,0 | COLOR_LIMEGREEN | 50,205,50 | COLOR_LIGHTGREEN | 144,238,144 |
| COLOR_PALEGREEN | 152,251,152 | COLOR_DARKSEAGREEN | 143,188,143 | COLOR_MEDIUMSPRINGGREEN | 0,250,154 |
| COLOR_SPRINGGREEN | 0,255,127 | COLOR_SEAGREEN | 46,139,87 | COLOR_MEDIUMAQUAMARINE | 102,205,170 |
| COLOR_MEDIUMSEAGREEN | 60,179,113 | COLOR_LIGHTSEAGREEN | 32,178,170 | COLOR_DARKSLATEGRAY | 47,79,79 |
| COLOR_TEAL | 0,128,128 | COLOR_DARKCYAN | 0,139,139 | COLOR_AQUA | 0,255,255 |
| COLOR_CYAN | 0,255,255 | COLOR_LIGHTCYAN | 224,255,255 | COLOR_DARKTURQUOISE | 0,206,209 |
| COLOR_TURQUOISE | 64,224,208 | COLOR_MEDIUMTURQUOISE | 72,209,204 | COLOR_PALETURQUOISE | 175,238,238 |
| COLOR_AQUAMARINE | 127,255,212 | COLOR_POWDERBLUE | 176,224,230 | COLOR_CADETBLUE | 95,158,160 |
| COLOR_STEELBLUE | 70,130,180 | COLOR_CORNFLOWERBLUE | 100,149,237 | COLOR_DEEPSKYBLUE | 0,191,255 |
| COLOR_DODGERBLUE | 30,144,255 | COLOR_LIGHTBLUE | 173,216,230 | COLOR_SKYBLUE | 135,206,235 |
| COLOR_LIGHTSKYBLUE | 135,206,250 | COLOR_MIDNIGHTBLUE | 25,25,112 | COLOR_NAVY | 0,0,128 |
| COLOR_DARKBLUE | 0,0,139 | COLOR_MEDIUMBLUE | 0,0,205 | COLOR_BLUE | 0,0,255 |
| COLOR_ROYALBLUE | 65,105,225 | COLOR_BLUEVIOLET | 138,43,226 | COLOR_INDIGO | 75,0,130 |
| COLOR_DARKSLATEBLUE | 72,61,139 | COLOR_SLATEBLUE | 106,90,205 | COLOR_MEDIUMSLATEBLUE | 123,104,238 |
| COLOR_MEDIUMPURPLE | 147,112,219 | COLOR_DARKMAGENTA | 139,0,139 | COLOR_DARKVIOLET | 148,0,211 |
| COLOR_DARKORCHID | 153,50,204 | COLOR_MEDIUMORCHID | 186,85,211 | COLOR_PURPLE | 128,0,128 |
| COLOR_THISTLE | 216,191,216 | COLOR_PLUM | 221,160,221 | COLOR_VIOLET | 238,130,238 |
| COLOR_FUCHSIA | 255,0,255 | COLOR_ORCHID | 218,112,214 | COLOR_MEDIUMVIOLETRED | 199,21,133 |
| COLOR_PALEVIOLETRED | 219,112,147 | COLOR_DEEPPINK | 255,20,147 | COLOR_HOTPINK | 255,105,180 |
| COLOR_LIGHTPINK | 255,182,193 | COLOR_PINK | 255,192,203 | COLOR_ANTIQUEWHITE | 250,235,215 |
| COLOR_BEIGE | 245,245,220 | COLOR_BISQUE | 255,228,196 | COLOR_BLANCHEDALMOND | 255,235,205 |
| COLOR_WHEAT | 245,222,179 | COLOR_CORNSILK | 255,248,220 | COLOR_LEMONCHIFFON | 255,250,205 |
| COLOR_LIGHTGOLDENRODYELLOW | 250,250,210 | COLOR_LIGHTYELLOW | 255,255,224 | COLOR_SADDLEBROWN | 139,69,19 |
| COLOR_SIENNA | 160,82,45 | COLOR_CHOCOLATE | 210,105,30 | COLOR_PERU | 205,133,63 |
| COLOR_SANDYBROWN | 244,164,96 | COLOR_BURLYWOOD | 222,184,135 | COLOR_TAN | 210,180,140 |
| COLOR_ROSYBROWN | 188,143,143 | COLOR_MOCCASIN | 255,228,181 | COLOR_NAVAJOWHITE | 255,222,173 |
| COLOR_PEACHPUFF | 255,218,185 | COLOR_MISTYROSE | 255,228,225 | COLOR_LAVENDERBLUSH | 255,240,245 |
| COLOR_LINEN | 250,240,230 | COLOR_OLDLACE | 253,245,230 | COLOR_PAPAYAWHIP | 255,239,213 |
| COLOR_SEASHELL | 255,245,238 | COLOR_MINTCREAM | 245,255,250 | COLOR_SLATEGRAY | 112,128,144 |
| COLOR_LIGHTSLATEGRAY | 119,136,153 | COLOR_LIGHTSTEELBLUE | 176,196,222 | COLOR_LAVENDER | 230,230,250 |
| COLOR_FLORALWHITE | 255,250,240 | COLOR_ALICEBLUE | 240,248,255 | COLOR_GHOSTWHITE | 248,248,255 |
| COLOR_HONEYDEW | 240,255,240 | COLOR_IVORY | 255,255,240 | COLOR_AZURE | 240,255,255 |
| COLOR_SNOW | 255,250,250 | COLOR_BLACK | 0,0,0 | COLOR_DIMGRAY | 105,105,105 |
| COLOR_GRAY | 128,128,128 | COLOR_DARKGRAY | 169,169,169 | COLOR_SILVER | 192,192,192 |
| COLOR_LIGHTGRAY | 211,211,211 | COLOR_GAINSBORO | 220,220,220 | COLOR_WHITESMOKE | 245,245,245 |
| COLOR_WHITE | 255,255,255 | | | | |

```javascript
var polygon = Module.createPolygon("Colored");
polygon.getStyle().setFillColor(Module.COLOR_DODGERBLUE);
```
