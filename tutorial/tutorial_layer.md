# 레이어 설정하기

레이어는 객체를 담는 스케치북 입니다. 객체를 생성하고 랜더링하기 위해서는 레이어가 필요합니다. 객체를 생성하고 레이어에 삽입하지 않으면 해당 객체는 랜더링되지 않습니다. 또한 필요한 레이어만 랜더링하기 위해서 가시설정을 할 수 있습니다.

![](../.gitbook/assets/layer.png)

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

```javascript
var userlayer = new Module.JSLayerList(true);
userlayer = layerList.createLayer(레이어 이름, 레이어 타입);
```

### step 2. 레이어 가시설정

step 1 에서 생성한 레이어의 가시설정을 합니다.
* true : 레이어의 모든 객체 랜더링
* false : 레이어의 모든 객체 랜더링하지 않음

```javascript
userlayer. setVisible(false);
```


### etc. 레이어 검색

레이어 생성 후 레이어 이름은 알고있지만 어느 변수에 저장했는지 모를경우 검색을 통해서 레이어를 반환받을 수 있습니다.

```javascript
var userlayer = new Module.JSLayerList(true);
userlayer = layerList.nameAtLayer(레이어 이름);
```