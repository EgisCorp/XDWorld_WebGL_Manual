# 레이어 설정

레이어는 객체를 담는 스케치북 입니다. 객체를 생성하고 랜더링하기 위해서는 레이어가 필요합니다. 객체를 생성하고 레이어에 삽입하지 않으면 해당 객체는 랜더링되지 않습니다. 또한 필요한 레이어만 랜더링하기 위해서 가시설정을 할 수 있습니다.

![](../.gitbook/assets/layer.png)

## Layer Type List

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
