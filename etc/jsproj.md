---
description: 좌표계 변환 계산 API를 제공합니다.
---

# JSProj

> Module.JSProj API 생성합니다.
>
> 입력값이 없다면 기본적으로 EPSG:4326으로 설정됩니다.

```javascript
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
let projection = new Module.JSProj("epsg 코드(epsg:4326)");
let projection = new Module.JSProj("proj4 코드(+proj=longlat +datum=WGS84 +no_defs +type=crs)");
```

## Function

### apply(code) → object

> Projection 재설정 합니다.
>
> 이전 Projection을 초기화 하고 입력값으로 Projection을 생성합니다.

{% tabs %}
{% tab title="infomation" %}
| Name | Type | Description |
| ---- | ------ | ------------------- |
| code | string | epsg, proj4 코드 입력값. |

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name : 동작 API 명칭.
    -   .return : API 결과 정보 반환( 실패 에러 코드 ).

{% endtab %}

{% tab title="Template" %}

```javascript
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
let result = projection.apply("epsg:5186");
console.log(result); // API 결과 정보 반환
```

{% endtab %}
{% endtabs %}

### find(epsg) → object

> 엔진에서 지원하는 Projection 목록 중 입력된 EPSG 존재 유무를 확인합니다.
>
> 입력된 EPSG 코드를 통해 해당 PROJ4를 반환합니다.
>
> 지원 EPSG 목록을 참조epsg 목록 참

{% tabs %}
{% tab title="infomation" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| epsg | string | epsg 코드 입력값. |

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name : 동작 API 명칭.
    -   .return : API 결과 정보 반환( proj4 문자열 : 정상적인 반환값, 문자열 : 실패 에러 코드 ).

{% endtab %}

{% tab title="Template" %}

```javascript
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
let result = projection.find("epsg:5186");
console.log(result); // API 결과 정보 반환
```

{% endtab %}
{% endtabs %}

### getProjCode() → string

> JSProj 변수에 적용된 Projection 구성요소인 proj4 코드를 반환합니다.

{% tabs %}
{% tab title="infomation" %}

-   Return
    -   API 결과 정보 반환( proj4 문자열 : 정상적인 반환값, 공백 : JSProj 초기화 상태 ).

{% endtab %}
{% tab title="Template" %}

```javascript
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
let result = projection.getProjCode();
console.log(result); // epsg:4326 proj4 코드 반환
// or
let projection = new Module.JSProj("epsg:5186"); // 기본값 epsg:4326으로 설정
let result = projection.getProjCode();
console.log(result); // epsg:5186 proj4 코드 반환
```

{% endtab %}
{% endtabs %}

### transform(option) → object

> 좌표 변환을 동작합니다.
>
> JSProj 변수에 적용된 Projection으로 입력된 좌표 정보를 변환합니다.

{% tabs %}
{% tab title="infomation" %}
| Name | Type | Description |
| ------ | ------ | ----------- |
| option | object | 좌표 변환 정보. |

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name : 동작 API 명칭.
    -   .return : API 결과 정보 반환( Array : 변환된 좌표 목록, 문자열 : 실패 에러 코드 ).

{% endtab %}

{% tab title="Template" %}

```javascript
// 단일 변환 지원
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
parameter = {
    source: "epsg:5186",
    coordinates: new Module.JSVector2D(200000.0, 378044.651253),
};

let result = projection.transform(parameter); // 5186 -> 4326으로 좌표 변환
// or
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
parameter = {
    source: "+proj=tmerc +lat_0=38 +lon_0=127 +k=1 +x_0=200000 +y_0=600000 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs",
    coordinates: new Module.JSVector3D(200000.0, 378044.651253, 10),
};
let result = projection.transform(parameter); // 5186 -> 4326으로 좌표 변환
// or
// Array 타입 지원
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
let coordinate = Array();
coordinate.push(new Module.JSVector3D(200000.0, 378044.651253, 10));
coordinate.push(new Module.JSVector3D(200000.0, 489012.95569100516, 10));
coordinate.push(new Module.JSVector3D(289012.929607278, 489480.463416938, 10));
parameter = {
    source: "epsg:5186",
    coordinates: coordinate,
};
let result = projection.transform(parameter); // 5186 -> 4326으로 좌표 변환
```

{% endtab %}
{% endtabs %}

## Class Function

### list() → object

> 엔진에서 지원하는 Projection 전체 목록을 사용자에게 제공합니다.
>
> 목록 정보는 epsg 코드로 구성된 number Type 입니다.

{% tabs %}
{% tab title="infomation" %}

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name : 동작 API 명칭.
    -   .return : API 결과 정보 반환( Array : epsg 코드 목록 ).

{% endtab %}

{% tab title="Template" %}

```javascript
let list = Module.JSProj.list();
```

{% endtab %}
{% endtabs %}

### find(epsg) → object

> 엔진에서 지원하는 Projection 목록 중 입력된 EPSG 존재 유무를 확인합니다.
>
> 입력된 EPSG 코드를 통해 해당 PROJ4를 반환합니다.
>
> 지원 EPSG 목록을 참조epsg 목록 참

{% tabs %}
{% tab title="infomation" %}
| Name | Type | Description |
| ---- | ------ | ------------ |
| epsg | string | epsg 코드 입력값. |

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name : 동작 API 명칭.
    -   .return : API 결과 정보 반환( proj4 문자열 : 정상적인 반환값, 문자열 : 실패 에러 코드 ).

{% endtab %}

{% tab title="Template" %}

```javascript
let list = Module.JSProj.find("epsg:5186");
console.log(result); // API 결과 정보 반환
```

{% endtab %}
{% endtabs %}

### transform(option) → object

> 좌표 변환을 동작합니다.
>
> JSProj 변수에 적용된 Projection으로 입력된 좌표 정보를 변환합니다.

{% tabs %}
{% tab title="infomation" %}
| Name | Type | Description |
| ------ | ------ | --------------- |
| option | object | 좌표 변환 정보. |

-   Return
    -   .result : API 성공 유무 상태 ( 1 : 성공, 0 : 실패 ).
    -   .name : 동작 API 명칭.
    -   .return : API 결과 정보 반환( Array : 변환된 좌표 목록, 문자열 : 실패 에러 코드 ).

{% endtab %}

{% tab title="Template" %}

```javascript
// 단일 변환 지원
parameter = {
    target: "epsg:4326"
    source: "epsg:5186",
    coordinates: new Module.JSVector2D(200000.0, 378044.651253),
};
let result = Module.JSProj.transform(parameter); // 5186 -> 4326으로 좌표 변환
// or
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
parameter = {
    target: "+proj=longlat +datum=WGS84 +no_defs"
    source: "+proj=tmerc +lat_0=38 +lon_0=127 +k=1 +x_0=200000 +y_0=600000 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs",
    coordinates: new Module.JSVector3D(200000.0, 378044.651253, 10),
};
let result = Module.JSProj.transform(parameter); // 5186 -> 4326으로 좌표 변환
// or
// Array 타입 지원
let projection = new Module.JSProj(); // 기본값 epsg:4326으로 설정
let coordinate = Array();
coordinate.push(new Module.JSVector3D(200000.0, 378044.651253, 10));
coordinate.push(new Module.JSVector3D(200000.0, 489012.95569100516, 10));
coordinate.push(new Module.JSVector3D(289012.929607278, 489480.463416938, 10));
parameter = {
    target: "epsg:4326"
    source: "epsg:5186",
    coordinates: coordinate,
};
let result = Module.JSProj.transform(parameter); // 5186 -> 4326으로 좌표 변환
```

{% endtab %}
{% endtabs %}
