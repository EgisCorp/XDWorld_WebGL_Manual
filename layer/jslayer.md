---
description: 지도 내 레이어 설정 API를 제공합니다.
---

# JSLayer

## 생성자 \*\*Constructor -&gt; JSLayer

> 인스턴스 JSLayer 생성

{% tabs %}
{% tab title="Infomation" %}
| No. | API | Contents |
| :--- | :--- | :--- |
| 1 | JSLayer\(\) | 사용자 레이어 반환 |

* Code

```javascript
  let layerList = new Module.JSLayerList( true );
  let layer = layerList.createLayer( layername );
```
{% endtab %}
{% endtabs %}

## addObject\( object, level \)

> 해당 사용자 레이어 오브젝트 추가.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| object | JSObject | 생성 된 오브젝트 추가 |
| ~~level~~ | number | 0 값으로 사용 |

* Code

```javascript
  let layername = "objectlayer"
  let layerList = new Module.JSLayerList( true );
  let layer = layerList.createLayer( layername );
  // object 생성 과정
  layer.addObject(object, 0);
```
{% endtab %}
{% endtabs %}

## indexAtKey\( index \)  -&gt; string

> 해당 사용자 레이어에서 오브젝트 ID 반환.
>
> 해당 사용자 레이어 오브젝트는 리스트로 관리하며 리스트 index 해당되는 오브젝트 ID 반환.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| index | number | 목표 오브젝트 인덱스. |

* Return
  * 문자열 : 인덱스 해당 오브젝트 ID 반환 성공
  * 빈 문자열 : 인덱스 해당 오브젝트 ID 반환 실패
    * ID 반환 실패 조건
      * index가 오브젝트 리스트 범위를 초과한 경우 \(0보다 작거나 오브젝트 리스트 수 보다 큰 경우\)
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## indexAtObject\( index \) -&gt; **\(** JSObject **\)**

> 해당 사용자 레이어에서 오브젝트 반환.
>
> 해당 사용자 레이어 오브젝트는 리스트로 관리하며 리스트 index 해당되는 오브젝트 반환.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| index | number | 목표 오브젝트 인덱스. |

* Return
  * JSObject : 비교 ID와 동일한 오브젝트 반환 성공
  * null : 비교 ID와 동일한 오브젝트 반환 실패
    * ID 반환 실패 조건
      * index가 오브젝트 리스트 범위를 초과한 경우 \(0보다 작거나 오브젝트 리스트 수 보다 큰 경우\)
      * 해당 레이어 객체 수가 0인 경우
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## keyAtObject\( objectid \) -&gt; **\(** JSObject **\)**

> 해당 사용자 레이어에서 오브젝트 반환.
>
> 해당 사용자 레이어 오브젝트는 리스트로 관리하며 순차적으로 오브젝트 ID와 objectid 비교 후 조건에 만족하는 오브젝트 반환.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| objectid | string | 목표 오브젝트 ID. |

* Return
  * JSObject : 비교 ID와 동일한 오브젝트 반환 성공
  * NULL : 비교 ID와 동일한 오브젝트 반환 실패
    * ID 반환 실패 조건
      * ID와 동일한 오브젝트가 없을 경우
      * objectid 빈공백 일 경우
      * 해당 레이어 객체 수가 0인 경우
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## removeAtIndex\( index \) -&gt; boolean

> 해당 사용자 레이어에서 오브젝트 삭제.
>
> 해당 사용자 레이어 오브젝트는 리스트로 관리하며 리스트 index 해당되는 오브젝트 삭제.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| index | number | 삭제 오브젝트 인덱스 |

* Return
  * TRUE : 오브젝트 삭제 성공
  * FALSE : 오브젝트 삭제 실패
    * 삭제 실패 조건
      * index가 오브젝트 리스트 범위를 초과한 경우 \(0보다 작거나 오브젝트 리스트 수 보다 큰 경우\)
      * 해당 레이어 객체 수가 0인 경우
      * 서비스 레이어 경우\(서비스 레이어는 tile 기반으로 오브젝트는 tile에 종속 된다.\)
      * 외부 서버를 통해 로드된 데이터인 경우\(Ex. WMS, WFS\)
* Code

```javascript
    let layername = "objectlayer"
    let layerList = new Module.JSLayerList(true);
    let    layerList.createLayer(layername );

    // object 생성 과정

    layer.addObject(object, 0);
    layer.removeAtIndex(0);
```
{% endtab %}
{% endtabs %}

## removeAtKey\( objectid \) -&gt; boolean

> 해당 사용자 레이어에서 오브젝트 삭제.
>
> 해당 사용자 레이어 오브젝트는 리스트로 관리하며 순차적으로 오브젝트 ID와 objectid 비교 후 조건에 만족하는 오브젝트 삭제.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| objectid | string | 목표 오브젝트 ID. |

* Return
  * TRUE : 오브젝트 삭제 성공
  * FALSE : 오브젝트 삭제 실패
    * 삭제 실패 조건
      * objectid가 동일한 오브젝트가 없을 경우
      * objectid 빈공백 일 경우
      * 해당 레이어 객체 수가 0인 경우
      * 서비스 레이어 경우\(서비스 레이어는 tile 기반으로 오브젝트는 tile에 종속 된다.\)
      * 외부 서버를 통해 로드된 데이터인 경우\(Ex. WMS, WFS\)
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## removeAtObject\( object \) -&gt; boolean

> 해당 사용자 레이어에서 오브젝트 삭제.
>
> 해당 사용자 레이어 오브젝트는 리스트로 관리하며 순차적으로 오브젝트와 object 비교 후 조건에 만족하는 오브젝트 삭제.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| object | JSObject | 목표 오브젝트. |

* Return
  * TRUE : 오브젝트 삭제 성공
  * FALSE : 오브젝트 삭제 실패
    * 삭제 실패 조건
      * object와 동일한 오브젝트가 없을 경우.
      * 해당 레이어 객체 수가 0인 경우.
      * 서비스 레이어 경우\(서비스 레이어는 tile 기반으로 오브젝트는 tile에 종속 된다.\).
      * 외부 서버를 통해 로드된 데이터인 경우\(Ex. WMS, WFS\).
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## removeAll\( \) -&gt; boolean

> 해당 사용자 레이어에서 오브젝트 삭제.
>
> 해당 레이어 오브젝트 리스트 전체 삭제.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
* Return
  * TRUE : 오브젝트 삭제 성공.
  * FALSE : 오브젝트 삭제 실패.
    * 삭제 실패 조건
      * 해당 레이어 객체 수가 0인 경우.
      * 서비스 레이어 인 경우\( 서비스 레이어에서 오브젝트는 tile에 종속.\).
      * 외부 서버를 통해 로드된 데이터인 경우\(Ex. WMS, WFS\).
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## getObjectCount\( \) -&gt; number

> 해당 레이어 오브젝트 리스트 갯수 반환.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
* Return
  * result&gt;0 : 해당 레이어 오브젝트 갯수.
  * -1 : 해당 레이어에 오브젝트가 존재 하지 않는 경우.
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## getObjectKeyList\( \) -&gt; string

> 해당 레이어에서 오브젝트 ID 반환.
>
> 해당 사용자 레이어 오브젝트는 리스트로 관리하며 모든 리스트 오브젝트 ID 반환
>
> 사용자 레이어에서 사용 가능

{% tabs %}
{% tab title="Infomation" %}
* Return
  * 문자열 : 오브젝트 ID 반환 성공\(구분자 ","\)
  * 빈 문자열 : 오브젝트 ID 반환 실패  
  * "" : 오브젝트 ID 반환 실패
    * ID 반환 실패 조건
      * 해당 레이어 객체 수가 0인 경우.
      * 서비스 레이어 인 경우\( 서비스 레이어에서 오브젝트는 tile에 종속.\).
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## setEditable\( edit \) -&gt; boolean

> 해당 레이어에서 편집 레이어 설정.
>
> 엔진 내부에서 생성되는 객체를 관리하는 레이어.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| edit | boolean | 편집레이어 설정 유무. |

* Detail
  * edit
    * TRUE : 편집 레이어 설정\(기존 편집 레이어는 일반레이어로 변경\).
    * FALSE : 일반 레이어 설정.
* Return
  * TRUE : 편집 레이어 설정 성공.
  * FALSE : 편집 레이어 설정 실패.
    * 편집 레이어 설정 실패 조건
      * 서비스 레이어 인 경우\( 서비스 레이어에서 오브젝트는 tile에 종속.\).
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_figure](http://sandbox.dtwincloud.com/code/main.do?id=object_figure)
{% endtab %}
{% endtabs %}

## setLODRatio\( ratio \)

> 해당 레이어 가시화 범위 설정
>
> 해당 서비스 레이어 LOD 변경으로 오브젝트 가시화 조절.
>
> 서비스 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| ratio | number | LOD 단계 설정\(높을수록 가시화 범위 증가\). |

* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_line\_arc](http://sandbox.dtwincloud.com/code/main.do?id=object_line_arc)
{% endtab %}
{% endtabs %}

## setSelectable\( select \)

> 해당 레이어 선택 설정.
>
> 해당 레이어를 구성하는 오브젝트 선택 이벤트 설정.
>
> 사용자, 서비스 레이어에서 사용 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| select | boolean | 해당 레이어 오브젝트 선택 이벤트 설정 |

* Detail
  * edit
    * TRUE : 선택 이벤트 동작.
    * FALSE : 선택 이벤트 미동작.
* Code

```javascript

```
{% endtab %}
{% endtabs %}

## setUseRecoverHsv\( use \) -&gt; boolean

> 해당 서비스 레이어 색상 표현 설정.
>
> HSV 색상 채널을 적용한 오브젝트 표현 설정.
>
> 건물, 드론 LOD 레이어만 적용.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| use | boolean | HSV 채널 설정 유무. |

* Detail
  * use
    * TRUE : HSV 채널 가시화 설정.
    * FALSE : 일반 가시화 설정.
* Return
  * TRUE : HSV 채널 가시화 설정 성공.
  * FALSE : HSV 채널 가시화 설정 실패.
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=layer\_color\_tone](http://sandbox.dtwincloud.com/code/main.do?id=layer_color_tone)
{% endtab %}
{% endtabs %}

## setRecoverHsvValue\( hue, saturation, value \) -&gt; boolean

> 해당 서비스 레이어 HSV 색상 채널 설정.
>
> 색상\(hue\), 채도\(saturation\), 명도\(value\) 입력 값으로 오브젝트 HSV 채널 가시화 설정.
>
> 건물, 드론 LOD 레이어만 적용.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| hue | number | HSV 채널\(명도\). |
| saturation | number | HSV 채널\(채도\). |
| value | number | HSV 채널\(명도\). |

* Return
  * TRUE : HSV 채널 설정 성공.
  * FALSE : HSV 채널 설정 실패.
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=layer\_color\_tone](http://sandbox.dtwincloud.com/code/main.do?id=layer_color_tone)
{% endtab %}
{% endtabs %}

## setTileAltitudeOffset\( offset \) -&gt; boolean

> 해당 서비스 초기 설정 고도값 설정\(기본 0\)
>
> 오브젝트가 로딩 시 초기 설정된 고도\(offset\)을 기준으로 높이 설정\(가시화 된 오브젝트 높이 변경 안됨\).
>
> 포인트 클라우드 레이어만 적용.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| offset | number | 포인트 클라우드 고도 설정. |

* Detail
  * altitude
    * offset &lt; 0 : 원본 고도에서 높이를 높인다.
    * offset == 0 : 원본 고도값.
    * offset &gt; 1 : 원본 고도에서 높이를 내린다.
	
* Return
  * TRUE : 높이 설정 성공.
  * FALSE : 높이 설정 실패.
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=layer\_pointcloud\_point\_size](http://sandbox.dtwincloud.com/code/main.do?id=layer_pointcloud_point_size)
{% endtab %}
{% endtabs %}

## setMinDistance\( distance \) -&gt; boolean

> 레이어 가시 범위 설정
>
> 레이어 최소 가시범위 거리를 설정.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| distance | number | 레이어 최소 가시범위 거리\(m단위\). |

* Return
  * TRUE : 최소 가시 범위 설정 성공.
  * FALSE : 최소 가시 범위 설정 실패.
    * 최소 가시 범위 실패 조건.
      * 최소 가시 범위가 최대 가시 범위보다 큰 경우.
      * 서비스 레이어 일 경우 setLODRatio 사용.
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d)
{% endtab %}
{% endtabs %}

## setMaxDistance\( distance \) -&gt; boolean

> 레이어 가시 범위 설정
>
> 레이어 최대 가시범위 거리를 설정.
>
> 사용자 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| distance | number | 레이어 최대 가시범위 거리\(m단위\). |

* Return
  * TRUE : 최대 가시 범위 설정 성공.
  * FALSE : 최대 가시 범위 설정 실패.
    * 최대 가시 범위 실패 조건.
      * 최대 가시 범위가 최소 가시 범위보다 작은 경우.
      * 서비스 레이어 일 경우 setLODRatio 사용.
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_grid\_2d](http://sandbox.dtwincloud.com/code/main.do?id=object_grid_2d)
{% endtab %}
{% endtabs %}

## setWMSProvider\( option \) -&gt; string

> WMS 레이어 생성
>
> argument 변수로 WMS 서비스 레이어 생성

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| option | object | WMS 요청 속성 정보. |

* Detail
  * option

| Name | Type | Contents |
| :--- | :--- | :--- |
| url | string | 요청 지오서버 url. |
| layer | string | 요청 지오서버 레이어 명칭. |
| minmumLevel | number | 최소 가시화 레벨\[Default 0\]. |
| maxmumLevel | number | 최대 가시화 레벨\[Default 15\]. |
| tileSize | number | 요청 정사각형 이미지 크기\[Default 256\].|
| crs | string | 좌표 타입\[Default EPSG:4326\]. |
| parameters | Object | 스타일, 옵션 설정 속성정보.|

* Return
  * success : WMS 레이어 생성 성공.
  * 문자열 : WMS 레이어 생성 과정 에러 메시지.
  
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=layer_wms](http://sandbox.dtwincloud.com/code/main.do?id=layer_wms)
{% endtab %}
{% endtabs %}


## setBBoxOrder\( reverse \)

> WMS 서비스 레이어 옵션 설정.
>
> 지오 서버로 요청하는 좌표 정보 가시화 옵션 설정.
>
> WMS 레이어에서 사용 가능

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| reverse | boolean | 좌표 옵션 설정. |

* Detail
  * reverse
    * TRUE : X, Y 순서로 설정 Ex) BBOX=minx,miny,maxx,maxy
    * FALSE : Y, X 순서로 설정 Ex) BBOX=minY,minX,maxY,maxX
	
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=layer_wms](http://sandbox.dtwincloud.com/code/main.do?id=layer_wms)
  
{% endtab %}
{% endtabs %}

## setProxyRequest\( set \)

> 레이어 프록시 사용 설정.
>
> 오브젝트 통신 요청 시 프록시 사용 유무를 설정.
>
> 서비스 레이어만 가능.

{% tabs %}
{% tab title="Infomation" %}
| Name | Type | Contents |
| :--- | :--- | :--- |
| set | boolean | 프록시 사용 설정 유무. |

* Detail
  * altitude
    * offset &lt; 0 : 원본 고도에서 높이를 높인다.
    * offset == 0 : 원본 고도값.
    * offset &gt; 1 : 원본 고도에서 높이를 내린다.
	
* Return
  * TRUE : 프록시 설정 성공.
  * FALSE : 프록시 설정 실패.
    * 프록시 설정 실패 조건.
      * 사용자 레이어 인 경우
	  
* Code

```javascript

```
{% endtab %}
{% endtabs %}


