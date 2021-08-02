---
description: 폴리곤 오브젝트 설정 및 반환 API를 제공합니다.
---

# JSPolygon

Module createPolygon API로 생성할 수 있습니다.

```text
var object = Module.createPolygon("newObject");
```

## loadFile\(object options\) → boolean

> 지정한 url과 옵션 값으로 3DS 파일을 로드합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| options | object | 모델 파일 로드 옵션 |

* Detail
  * options
    * url\(필수\) : 모델 파일 url
    * positionmode \(boolean\)
      * true : 좌표가 있는 모델 파일 \(projectioncode 속성으로 좌표계 지정 필수\)
      * false : 좌표가 없는 모델 파일 \(position 속성으로 위치 지정 필수\)
    * projectioncode \(number\) : positionmode가 true일 때 모델의 좌표계 번호
      * EPSG\:4326 → 13
      * EPSG\:5186 → 20
      * EPSG\:5174 → 23
    * position \([JSVector3D](jsvector3d.md)\) : positionmode가 false 일 때 모델 위치
    * align : position 지정 시 중심 정렬 위치
      * 0 : 중앙 정렬
      * 1 : 바닥 정렬
      * 2 : 윗면 정렬
    * texture \(string\) : texture 이미지 URL
* Return
  * 성공 : true
  * 실패 : false
    * positionmode=true 일 때 projectioncode가 설정되지 않음
    * positionmode=false 일 때 position이 지정되지 않음
    * url 이 지정되지 않음
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_file\_3ds](http://sandbox.dtwincloud.com/code/main.do?id=object_file_3ds)
{% endtab %}
{% endtabs %}

## loadTexture\(string texture\_name, string texture\_url\) → boolean

> 폴리곤에 사용할 텍스쳐 이미지를 등록합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| texture\_name | string | 텍스쳐 이름\(key\) |
| textureURL | string | 텍스쳐 이미지 URL |

* Detail
  * texture\_name
    * 텍스쳐는 texture\_name 로 구분되며, setFaceTexture API로 텍스쳐를 적용할 때 텍스쳐를 구분하는 용도로 사용됩니다.
* Return
  * 성공 : true
  * 실패 : false
    * 이미 동일한 texture\_name의 텍스쳐가 있음
    * texture\_name이나 texture\_url 이 빈 문자열
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_rtt\_image\_changing](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_rtt_image_changing)
{% endtab %}
{% endtabs %}

## setCircle\([JSVector3D](jsvector3d.md) position, number radius, number segment\) → boolean

> 중심 좌표와 반경, 버텍스 수로 원 모양의 평면 좌표를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| position | [JSVector3D](jsvector3d.md) | 원 중심점 |
| radius | number | 반경 |
| segment | number | 버텍스 수 |

* Detail
  * radius : 0이상의 값으로 입력, 단위는 미터 단위 입니다.
  * segment : 3이상의 값으로 입력. 값이 커질 수록 원에 가까운 형태가 됩니다.
* Return
  * 성공 : true
  * 실패 : false
    * radius 값이 0
    * segment 값이 3 미만
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_circle](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_circle)
{% endtab %}
{% endtabs %}

## setCoordinates\([Collection](collection.md) vertex\_list\)

> Polygon 평면을 구성하는 좌표 리스트를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| vertex\_list | [Collection](collection.md) | 폴리곤 좌표 리스트 |

* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=camera\_set\_viewrect](http://sandbox.dtwincloud.com/code/main.do?id=camera_set_viewrect)
{% endtab %}
{% endtabs %}

## setFaceTexture\(number face\_index, string texture\_name\) → boolean

> 중심 좌표와 반경, 버텍스 수로 원 모양의 평면 좌표를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| face\_index | number | 텍스쳐를 사용할 폴리곤 face index |
| texture\_name | string | loadTexture API로 지정한 텍스쳐 이름 |

* Return
  * 성공 : true
  * 실패 : false
    * 지정한 텍스쳐 이름이 없음
    * 지정한 index의 폴리곤 face가 존재하지 않음
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_rtt\_image\_changing](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_rtt_image_changing)
{% endtab %}
{% endtabs %}

## setFireEffect\(boolean effect\_set\) → boolean

> 폴리곤 표면에 불 효과를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| effect\_set | boolean | 효과 on\(true\), off\(false\) |

* Return
  * 성공 : true
  * 실패 : false
    * 폴리곤 좌표가 설정되지 않음
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=effect\_fire](http://sandbox.dtwincloud.com/code/main.do?id=effect_fire)
{% endtab %}
{% endtabs %}

## setHeight\(number height\) → boolean

> 좌표가 설정 된 폴리곤의 높이를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| height | number | 폴리곤 높이 |

* Detail
  * height : 0이상의 값으로 입력, 단위는 미터 단위 입니다.
* Return
  * 성공 : true
  * 실패 : false
    * 폴리곤 좌표가 설정되지 않음
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_height](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_height)
{% endtab %}
{% endtabs %}

## setPartCoordinates\([JSVec3Array](jsvec3array.md) vertex\_list, [Collection](collection.md) part\_list\) → boolean

> 폴리곤 좌표\(vertex, part\)를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| vertex\_list | [JSVec3Array](jsvec3array.md) | 폴리곤 Vertex\(경도, 위도, 고도\) 리스트 |
| part\_list | [Collection](collection.md) | 폴리곤 Part 리스트 |

* Detail
  * part\_list : 파트를 이루는 버텍스 갯수의 리스트를 입력합니다.
* Return
  * 성공 : true
  * 실패 : false
    * vertex\_list 좌표가 3개 미만
    * part\_list 리스트 수가 1개 미만
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_height](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_height)
{% endtab %}
{% endtabs %}

## setPartCoordinatesUV\([JSVec3Array](jsvec3array.md) vertex\_list, [Collection](collection.md) part\_list, [JSVec2Array](jsvec2array.md) uv\_list, boolean is\_rtt\) → boolean

> 텍스쳐 uv를 포함한 폴리곤 좌표\(vertex, part, uv\)를 지정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| vertex\_list | [JSVec3Array](jsvec3array.md) | 폴리곤 Vertex\(경도, 위도, 고도\) 리스트 |
| part\_list | [Collection](collection.md) | 폴리곤 Part 리스트 |
| uv\_list | [JSVec2Array](jsvec2array.md) | 폴리곤 uv 좌표 리스트 |
| is\_rtt | boolean | 폴리곤 Part 리스트 |

* Detail
  * part\_list : 파트를 이루는 버텍스 갯수의 리스트를 입력합니다.
* Return
  * 성공 : true
  * 실패 : false
    * vertex\_list 좌표가 3개 미만
    * part\_list 리스트 수가 1개 미만
    * uv\_list 좌표가 3개 미만
    * vertex\_list 좌표와 uv\_list 좌표 수가 동일하지 않음
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_rtt\_image\_changing](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_rtt_image_changing)
{% endtab %}
{% endtabs %}

## setStyle\([JSPolygonStyle](jspolygonstyle.md) style\)

> 폴리곤 스타일을 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| style | [JSPolygonStyle](jspolygonstyle.md) | 오브젝트 스타일 설정 객체 |

* Detail
  * 설정 가능한 스타일
    * 폴리곤 채움 색상, 투명도
    * 폴리곤 외곽 라인 색상, 투명도
    * 폴리곤 외곽 라인 두께
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_polygon\_color](http://sandbox.dtwincloud.com/code/main.do?id=object_polygon_color)
{% endtab %}
{% endtabs %}

## videoTexturebyJSON\(object options\) → string

> 비디오를 재생 기반 텍스쳐를 설정합니다.

{% tabs %}
{% tab title="Information" %}
| Parameter | Type | Contents |
| :--- | :--- | :--- |
| options | object | 비디오 텍스쳐 설정 옵션 |

* Detail
  * options : 비디오 텍스쳐 설정을 위한 속성 객체입니다.
    * imagedata \(array\) : 비디오 이미지 데이터
    * size
      * width \(number\) : 비디오 엘리먼트 가로 크기
      * height \(number\) : 비디오 엘리먼트 세로 크기
    * position
      * min \([JSVector2D](jsvector2d.md)\) : 영역 최소 좌표 
      * max \([JSVector2D](jsvector2d.md)\) : 영역 최대 좌표 [JSVector2D](jsvector2d.md)
    * init \(boolean\) : position min, max 좌표를 이용한 폴리곤 형상 초기화 여부
    * complete\(function\) : 텍스쳐 갱신 완료 후 발생하는 CallBack
* Return
  * 설정 결과 문자열
    * "success" : 정상
    * "fail" : 실패
    * 이 외 예외처리에 대한 문자열 메시지 반환
* Code
  * [http://sandbox.dtwincloud.com/code/main.do?id=object\_video\_texture](http://sandbox.dtwincloud.com/code/main.do?id=object_video_texture)
{% endtab %}
{% endtabs %}

