---
description: 지도 내 레이어를 관리하는 API를 제공합니다
---

# JSLayerList

> Module.createTypoon API 생성.

```javascript
let userlayer = new Module.JSLayerList(true);		// 사용자 레이어 반환

let serverlayer = new Module.JSLayerList(false);	// 서비스 레이어 반환
```

### createLayer(name, type) → JSLayer

> 설정한 레이어 타입을 가지는 새 레이어 생성.

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| name | string | 생성 레이어 명칭. |
| type | number | [레이어 타입.](../etc/type-list.md#layer-type-list) |

* Return
  * JSLayer : 레이어 반환 성공.
  * null : 레이어 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let layer = layerList.createLayer(“NewLayer”, Module.ELT_POLYHEDRON);
```
{% endtab %}
{% endtabs %}

### createWMSLayer( name ) → JSLayer

> WMS 레이어 생성
>
> Web Map Server로 가시화 된 Tile 영역에 해당되는 지형 영상 이미지 요청
>
> WMS 서비스 레이어로 new Module.JSLayerList( false ) 사용

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| name | string | 생성 레이어 명칭. |

* Return
  * JSLayer : 레이어 반환 성공.
  * null : 레이어 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList( false );
let wmslayer = layerList.createWMSLayer( “WMS” );
```
{% endtab %}
{% endtabs %}

### createWFSLayer(name, type) → JSLayer

> WFS 레이어 생성
>
> Web Feature Server로 가시화 된 Tile 영역에 해당되는 오브젝트 요청
>
> WFS 서비스 레이어로 new Module.JSLayerList( false ) 사용

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| name | string | 생성 레이어 명칭. |
| type | number | [WFS 레이어 타입.](../etc/type-list.md#wfs-type-list) |

* Return
  * JSLayer : 반환 성공.
  * null : 반환 실패.
{% endtab %}

{% tab title="Template" %}
  ```javascript
  let layerList = new Module.JSLayerList( false );
  let wfslayer = layerList.createWFSLayer( “WFS" , 0);
  ```
{% endtab %}
{% endtabs %}

### nameAtLayer(name) → JSLayer

> 생성 된 레이어 반환
>
> 동일한 명칭을 가진 레이어 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| name | string | 반환 레이어 명칭. |

* Return
  * JSLayer : 반환 성공.
  * null : 반환 실패.
{% endtab %}
{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList( false );
let layer = layerList.nameAtLayer(“HybridLoad”);
```
{% endtab %}
{% endtabs %}

### getVisible(name) → number

> 레이어 가시화 옵션 정보 반환
>
> 레이어 투명/반투명 상태 정보 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| name | string | 목표 레이어 명칭. |

* Return
  * 0 : 투명 상태.
  * 1 : 가시화 상태.
{% endtab %}
{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
let visible = layerList.getVisible(“HybridLoad”);
```
{% endtab %}
{% endtabs %}

### setVisible(name, type)

> 레이어 가시화 옵션 설정
>
> 레이어 투명/반투명 상태 설정
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| name | string | 목표 레이어 명칭. |
| type | boolean | <p>true인 경우 레이어 가시화.<br>false인 레이어 숨김.</p> |
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(false);
layerList.setVisible(“HybridLoad”, true); 
layerList.setVisible(“HybridLoad”, false); 
```
{% endtab %}
{% endtabs %}

### delLayerAtFirst()  → boolean

> 레이어 삭제
>
> 레이어 리스트 첫 순서에 해당되는 레이어 삭제
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 첫 순서 레이어 삭제 성공.
  * false : 첫 순서 레이어 삭제 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
let check = layerList.delLayerAtFirst();
console.log(check);
```
{% endtab %}
{% endtabs %}

### delLayerAtLast() → boolean

> 레이어 삭제
>
> 레이어 리스트 끝 순서에 해당되는 레이어 삭제
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
* Return
  * true : 끝 순서 레이어 삭제 성공.
  * false : 끝 순서 레이어 삭제 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
let check = layerList.delLayerAtLast();
console.log(check);
```
{% endtab %}
{% endtabs %}

### delLayerAtName(name) → boolean

> 레이어 삭제
>
> 해당 명칭 레이어 삭제
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| name | string | 목표 레이어 명칭. |

* Return
  * true : 목표 레이어 삭제 성공.
  * false : 목표 레이어 삭제 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);

let check = layerList.delLayerAtName(“firstlayer”);
console.log(check);
check = layerList.delLayerAtName(“endlayer”);
console.log(check);
```
{% endtab %}
{% endtabs %}

### delLayerAtIndex(index) → boolean

> 레이어 삭제
>
> 해당 인덱스 레이어 삭제
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| index | number | 목표 레이어 인덱스. |

* Return
  * true : 목표 인덱스 레이어 삭제 성공.
  * false : 목표 인덱스 레이어 삭제 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);

let check = layerList.delLayerAtIndex(0);
check = layerList.delLayerAtName(0);
```
{% endtab %}
{% endtabs %}

### count() → number

> 전체 레이어 갯수 반환
>
> 사용자, 서비스 레이어 전체 갯수

{% tabs %}
{% tab title="Information" %}
* Return
  * 전체 레이어 갯수 
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
let count = layerList.count();
console.log(count);
```
{% endtab %}
{% endtabs %}

### layerAtIndex(layer) → number

> 해당 레이어 인덱스 확인
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| layer | JSLayer | 인덱스 확인 레이어. |

* Return
  * -1 : 레이어 리스트에 존재 하지 않는 레이어.
  * result&gt;0 : 확인 레이어 인덱스 번호.
  
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
let count = layerList.layerAtIndex(first);
console.log(count);
count = layerList.layerAtIndex(end);
console.log(count); 
```
{% endtab %}
{% endtabs %}

### firstAtLayer() → JSLayer

> 레이어 반환
>
> 레이어 리스트 첫 순서에 해당되는 레이어 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
* Return
  * JSLayer : 반환 성공.
  * null : 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
let result = layerList.firstAtLayer();
```
{% endtab %}
{% endtabs %}

### lastAtLayer() → JSLayer

> 레이어 반환
>
> 레이어 리스트 끝 순서에 해당되는 레이어 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
* Return
  * JSLayer : 반환 성공.
  * null : 반환 실패.
{% endtab %}

{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
let result = layerList.lastAtLayer();
```
{% endtab %}
{% endtabs %}

### indexAtLayer(index) → JSLayer

> 레이어 반환
>
> 해당 인덱스 레이어 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| index | number | 목표 레이어 인덱스. |

* Return
  * JSLayer : 반환 성공.
  * null : 반환 실패.
{% endtab %}

{% tab title="Template" %}
  ```javascript
  let layerList = new Module.JSLayerList(true);
  let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
  let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON); 
  let result = layerList.indexAtLayer(0);
  result = layerList.indexAtLayer(1);
  ```
{% endtab %}
{% endtabs %}

### setLayerMove(layer, move) → boolean

> 레이어 순서 변경
>
> 해당 레이어 인덱스 순서를 move 조건으로 변경
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| layer | JSLayer | 목표 레이어. |
| move | boolean | <p>true인 경우 인덱스 증가.<br>false인 경우 인덱스 감소.</p> |
* Return
  * true : 순서 변경 성공.
  * false: 순서 변경 실패.
    * 순서 변경 실패 조건
      * 레이어 리스트 2개 미만
      * 끝 순서 해당 레이어를 한단계 내린 경우
      * 첫 순서 해당 레이어를 한단계 올린 경우
{% endtab %}
{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
let check =  layerList.setLayerMove(end, true);
```
{% endtab %}
{% endtabs %}

### setLayerTopNBottom(layer, extreme) → boolean

> 레이어 순서 변경
>
> 해당 레이어 인덱스 순서를 extreme 조건으로 최상단, 최하단으로 변경
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Information" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| layer | JSLayer | 목표 레이어. |
| extreme | boolean | <p>true인 경우 인덱스 최상단으로 변경.<br>false인 경우 인덱스 최하단으로 변경.</p> |
* Return
  * true : 순서 변경 성공.
  * false: 순서 변경 실패.
    * 순서 변경 실패 조건.
      * 레이어 리스트 2개 미만.
      * 끝 순서 해당 레이어를 한단계 내린 경우.
      * 첫 순서 해당 레이어를 한단계 올린 경우.
{% endtab %}
{% tab title="Template" %}
```javascript
let layerList = new Module.JSLayerList(true);
let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
let second = layerList.createLayer(“secondlayer”, Module.ELT_POLYHEDRON); 
let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON); 
let check =  layerList.setLayerMove(first, true); 
```
{% endtab %}
{% endtabs %}