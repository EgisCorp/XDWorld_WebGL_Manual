---
description: 지도 내 레이어를 관리하는 API를 제공합니다
---

# JSLayerList

## 생성자 **Constructor -&gt; \( JSLayerList \)**

> 인스턴스 JSLayerList 생성

{% tabs %}
{% tab title="Infomation" %}
| No. | API | Contents |
| :--- | :--- | :--- |
| 1 | JSLayerList\(\) | 사용자 레이어 리스트 반환 |
| 2 | JSLayerList\(boolean\) | 레이어 리스트 반환 |

* Detail
  * TRUE : 사용자 레이어 리스트 설정.
  * FALSE : 서비스 레이어 리스트 설정.
* Return
  * JSLayerList : 반환 성공.
  * null : 반환 실패.
* Code

  ```javascript
  let userlayer = new Module.JSLayerList(true);
  let serverlayer = new Module.JSLayerList(false);
  ```
{% endtab %}
{% endtabs %}

## createLayer\(string \_layername, number \_layertype\) -&gt; **\(** [**JSLayer**](jslayer.md) **\)**

> 설정한 레이어 타입을 가지는 새 레이어 생성.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layername | string | 생성 레이어 명칭. |
| \_layertype | number | [레이어 타입.](../etc/type-list.md#layer-type-list) |

* Return
  * [JSLayer ](jslayer.md) : 반환 성공.
  * null : 반환 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  let layer = layerList.createLayer(“NewLayer”, Module.ELT_POLYHEDRON);
  ```
{% endtab %}
{% endtabs %}

## createWMSLayer\(string \_layername\) -&gt; **\(** [**JSLayer**](jslayer.md) **\)**

> WMS 레이어 생성
>
> Web Map Server로 가시화 된 Tile 영역에 해당되는 지형 영상 이미지 요청
>
> WMS 서비스 레이어로 new Module.JSLayerList\( false \) 사용

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layername | string | 생성 레이어 명칭. |

* Return
  * [JSLayer ](jslayer.md) : 반환 성공.
  * null : 반환 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList( false );
  let wmslayer = layerList.createWMSLayer( “WMS” );
  ```
{% endtab %}
{% endtabs %}

## createWFSLayer\(string \_layername, number \_layertype\) -&gt; **\(** [**JSLayer**](jslayer.md) **\)**

> WFS 레이어 생성
>
> Web Feature Server로 가시화 된 Tile 영역에 해당되는 오브젝트 요청
>
> WFS 서비스 레이어로 new Module.JSLayerList\( false \) 사용

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layername | string | 생성 레이어 명칭. |
| \_layertype | number | [WFS 레이어 타입.](../etc/type-list.md#wfs-type-list) |

* Return
  * [JSLayer ](jslayer.md) : 반환 성공.
  * null : 반환 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList( false );    // WFS는 서비스 레이어
  let wfslayer = layerList.createWFSLayer( “WFS" , 0);
  ```
{% endtab %}
{% endtabs %}

## nameAtLayer\(string \_layername\) -&gt; **\(** [**JSLayer**](jslayer.md) **\)**

> 생성 된 레이어 반환
>
> 동일한 명칭을 가진 레이어 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layername | string | 반환 레이어 명칭. |

* Return
  * [JSLayer ](jslayer.md) : 반환 성공.
  * null : 반환 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList( false );
  // ... 레이어 생성 과정
  let layer = layerList.nameAtLayer(“HybridLoad”);
  ```
{% endtab %}
{% endtabs %}

## getVisible\(string \_layername\) -&gt; **\(** number **\)**

> 레이어 가시화 옵션 정보 반환
>
> 레이어 투명/반투명 상태 정보 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layername | string | 목표 레이어 명칭. |

* Return
  * 0 : 투명 상태.
  * 1 : 가시화 상태.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(false);
  // ... 레이어 생성 과정
  let visible = layerList.getVisible(“HybridLoad”);
  ```
{% endtab %}
{% endtabs %}

## setVisible\(string \_layername, boolean \_visible\)

> 레이어 가시화 옵션 설정
>
> 레이어 투명/반투명 상태 설정
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layername | string | 목표 레이어 명칭. |
| \_visible | boolean | 레이어 가시화 설정. |

* Detail
  * \_visible
    * TRUE : 가시화 설정.
    * FALSE : 투명 설정.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(false);
  // ... 레이어 생성 과정
  layerList.setVisible(“HybridLoad”, true);   // HybridLoad 레이어 가시화 상태.
  layerList.setVisible(“HybridLoad”, false);  // HybridLoad 레이어 투영화 상태.
  ```
{% endtab %}
{% endtabs %}

## delLayerAtFirst\(\) -&gt; **\(** boolean **\)**

> 레이어 삭제
>
> 레이어 리스트 첫 순서에 해당되는 레이어 삭제
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
* Return
  * TRUE : 첫 순서 레이어 삭제 성공.
  * FALSE : 첫 순서 레이어 삭제 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
  layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
  // firstlayer 레이어 삭제
  let check = layerList.delLayerAtFirst();
  // 결과 출력
  console.log(check);
  ```
{% endtab %}
{% endtabs %}

## delLayerAtLast\(\) -&gt; \( boolean \)

> 레이어 삭제
>
> 레이어 리스트 끝 순서에 해당되는 레이어 삭제
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
* Return
  * TRUE : 끝 순서 레이어 삭제 성공.
  * FALSE : 끝 순서 레이어 삭제 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
  layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
  // endlayer 레이어 삭제
  let check = layerList.delLayerAtLast();
  // 결과 출력
  console.log(check);
  ```
{% endtab %}
{% endtabs %}

## delLayerAtName\(string \_layername\) -&gt; \( boolean \)

> 레이어 삭제
>
> 해당 명칭 레이어 삭제
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layername | string | 목표 레이어 명칭. |

* Return
  * TRUE : 목표 레이어 삭제 성공.
  * FALSE : 목표 레이어 삭제 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
  layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
  // firstlayer 레이어 삭제
  let check = layerList.delLayerAtName(“firstlayer”);
  console.log(check);
  // endlayer 레이어 삭제
  check = layerList.delLayerAtName(“endlayer”);
  console.log(check);
  ```
{% endtab %}
{% endtabs %}

## delLayerAtIndex\(number \_index\) -&gt; \( boolean \)

> 레이어 삭제
>
> 해당 인덱스 레이어 삭제
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_index | number | 목표 레이어 인덱스. |

* Return
  * TRUE : 목표 인덱스 레이어 삭제 성공.
  * FALSE : 목표 인덱스 레이어 삭제 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);    // 인덱스 0 설정
  layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);    // 인덱스 1 설정
  // firstlayer 레이어 삭제
  let check = layerList.delLayerAtIndex(0);
  console.log(check);
  // endlayer 레이어 삭제
  // firstlayer 레이어 삭제로 endlayer 레이어 인덱스는 0으로 변경
  check = layerList.delLayerAtName(0);
  console.log(check);
  ```
{% endtab %}
{% endtabs %}

## count\(\) -&gt; \( number\)

> 전체 레이어 갯수 반환
>
> 사용자, 서비스 레이어 전체 갯수

{% tabs %}
{% tab title="Infomation" %}
* Return
  * 전체 레이어 갯수 
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
  layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
  let count = layerList.count();
  console.log(count);    // 2출력
  ```
{% endtab %}
{% endtabs %}

## layerAtIndex\(JSLayer \_layer\) -&gt; \( number \)

> 해당 레이어 인덱스 확인
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layer | JSLayer | 인덱스 확인 레이어. |

* Return
  * -1 : 레이어 리스트에 존재 하지 않는 레이어.
  * result&gt;0 : 확인 레이어 인덱스 번호.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
  let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
  let count = layerList.layerAtIndex(first);
  console.log(count);    // 0 출력
  count = layerList.layerAtIndex(end);
  console.log(count);    // 1 출력
  ```
{% endtab %}
{% endtabs %}

## firstAtLayer\(\) -&gt; \( JSLayer \)

> 레이어 반환
>
> 레이어 리스트 첫 순서에 해당되는 레이어 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
* Return
  * [JSLayer ](jslayer.md) : 반환 성공.
  * null : 반환 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
  let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
  let result = layerList.firstAtLayer();
  // result == first 같은 레이어
  ```
{% endtab %}
{% endtabs %}

## lastAtLayer\(\) -&gt; \( JSLayer \)

> 레이어 반환
>
> 레이어 리스트 끝 순서에 해당되는 레이어 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
* Return
  * [JSLayer ](jslayer.md) : 반환 성공.
  * null : 반환 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);
  let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);
  let result = layerList.lastAtLayer();
  // result == end는 같은 레이어
  ```
{% endtab %}
{% endtabs %}

## indexAtLayer\(number \_index\) -&gt; \( JSLayer \)

> 레이어 반환
>
> 해당 인덱스 레이어 반환
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_index | number | 목표 레이어 인덱스. |

* Return
  * [JSLayer ](jslayer.md) : 반환 성공.
  * null : 반환 실패.
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);    // 인덱스 0
  let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);        // 인덱스 1
  let result = layerList.indexAtLayer(0);
  // result == first 같은 레이어
  result = layerList.indexAtLayer(1);
  // result == end 같은 레이어
  ```
{% endtab %}
{% endtabs %}

## setLayerMove\(JSLayer \_layer, boolean \_move\) -&gt; \( boolean \)

> 레이어 순서 변경
>
> 해당 레이어 인덱스 순서를 \_move 조건으로 변경
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layer | JSLayer | 목표 레이어. |
| \_move | boolean | 인덱스 변경 옵션. |

* Detail
  * \_move Type
    * TRUE : 한 단계 위로 올림.
    * FALSE : 한 단계 아래로 내림.
* Return
  * TRUE : 순서 변경 성공.
  * FALSE: 순서 변경 실패.
    * 순서 변경 실패 조건
      * 레이어 리스트 2개 미만
      * 끝 순서 해당 레이어를 한단계 내린 경우
      * 첫 순서 해당 레이어를 한단계 올린 경우
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);    // 인덱스 0
  let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);        // 인덱스 1
  let check =  layerList.setLayerMove(end, true);    // first 인덱스 1, end 인덱스 0
  ```
{% endtab %}
{% endtabs %}

## setLayerTopNBottom\(JSLayer \_layer, boolean \_extreme\) -&gt; \( boolean \)

> 레이어 순서 변경
>
> 해당 레이어 인덱스 순서를 \_extreme 조건으로 최상단, 최하단으로 변경
>
> 사용자, 서비스 레이어 모두 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| \_layer | JSLayer | 목표 레이어. |
| \_extreme | boolean | 인덱스 변경 옵션. |

* Detail
  * \_extreme Type
    * TRUE : 최상단으로 올림.
    * FALSE : 최하단으로 내림.
* Return
  * TRUE : 순서 변경 성공.
  * FALSE: 순서 변경 실패.
    * 순서 변경 실패 조건
      * 레이어 리스트 2개 미만
      * 끝 순서 해당 레이어를 한단계 내린 경우
      * 첫 순서 해당 레이어를 한단계 올린 경우
* Code

  ```javascript
  let layerList = new Module.JSLayerList(true);
  // 레이어 생성
  let first = layerList.createLayer(“firstlayer”, Module.ELT_POLYHEDRON);    // 인덱스 0
  let second = layerList.createLayer(“secondlayer”, Module.ELT_POLYHEDRON); // 인덱스 1
  let end = layerList.createLayer(“endlayer”, Module.ELT_POLYHEDRON);        // 인덱스 2
  let check =  layerList.setLayerMove(first, true);    // first 인덱스 2, second 인덱스 0 end 인덱스 1
  ```
{% endtab %}
{% endtabs %}

