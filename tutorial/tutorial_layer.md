# 레이어 설정하기

레이어는 객체를 담는 스케치북 입니다. 객체를 생성하고 랜더링하기 위해서는 레이어가 필요합니다. 객체를 생성하고 레이어에 삽입하지 않으면 해당 객체는 랜더링되지 않습니다. 또한 필요한 레이어만 랜더링하기 위해서 가시설정을 할 수 있습니다.

![](<../.gitbook/assets/layer.png>)

## Layer Type List

| Index | Name | Description |
| :--- | :--- | :--- |
| 0 | ELT_POLYHEDRON | 다면체 |
| 1 | ELT_PLANE | 평면 |
| 2 | ELT_PIPE | 관\(실린더\) |
| 3 | ELT_BILLBOARD | 빌보드 |
| 4 | ELT_3DLINE | 3차원 선 |
| 5 | ELT_3DPOINT | 심볼 텍스트 |
| 6 | ELT_3DS\_SYMBOL | 3차원 심볼 |
| 7 | ELT_GHOST\_3DSYMBOL | 유령 심볼 |
| 8 | ELT_TERRAIN | 지형 |
| 9 | ELT_MULTILPE | 다용도 |
| 10 | ELT_KML\_GROUND | KML |
| 11 | ELT_TERRAIN\_IMAGE | 지형 영상 |
| 12 | ELT_PICTOMETRY | 픽토 메트리 |
| 13 | ELT_WATER | Water 가시화 |
| 102 | ELT_SKY\_LINE | RTT 미적용 3차원 선 |
| 112 | ELT_TYPOON | 태풍 가시화 |
| 113 | ELT_GRAPH | 차트 가시화 |

### step 1. 레이어 생성

객체를 생성하고 랜더링하기 위해서는 레이어가 필요하기 때문에 레이어를 생성합니다.

레이어 타입에 대한 설명은 [여기](../etc/type-list.md)를 참조해 주십시오.

```javascript
var userlayer = new Module.JSLayerList(true);
userlayer = layerList.createLayer("layerName", Module.ELT_POLYHEDRON);
```

### step 2 - 1. 레이어 가시설정

step 1 에서 생성한 레이어의 가시설정을 합니다.
* true : 레이어의 모든 객체 랜더링
* false : 레이어의 모든 객체 랜더링하지 않음

```javascript
userlayer.setVisible(false);
```

### step 2 - 2. 레이어 가시 거리설정

step 1 에서 생성한 레이어의 가시 거리를 설정합니다.
* getMaxDistance : 최대 가시거리 반환
* setMaxDistance : 최대 가시거리 설정

* getMinDistance : 최소 가시거리 반환
* setMinDistance : 최소 가시거리 설정

```javascript
userlayer.setMaxDistance(10);
userlayer.setMaxDistance(2000);
```

### step 2 - 3. 레이어 선택 가능여부 설정

step 1 에서 생성한 레이어의 선택 가능여부를 설정합니다.
* setSelectable : 레이어 선택 가능여부 설정
* getSelectable : 레이어 선택 가능여부 반환

```javascript
userlayer.setSelectable(true);
```

### step 2 - 4. 레이어에 객체 추가

step 1 에서 생성한 레이어에 객체를 추가합니다.

```javascript
var object = 객체 생성;
userlayer.addObject(object, 0);	// (객체, 삽입할 레벨)
```