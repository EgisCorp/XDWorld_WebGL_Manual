---
description: Module 객체 초기화 및 XDWorld 초기화.
---

# Initialize

```javascript
initialize() {
    Module.initialize({
        container: document.querySelector('#map'),
        terrain: {
            dem: {
                url: globals.xdserver.url,
                name: 'dem_yw_1m',
                servername: 'XDServer',
            },
            image: {
                url: globals.xdserver.url,
                name: 'tile_yw_10cm',
                servername: 'XDServer',
            },
        },
    });
}
```

> 맵 생성 정보를 매개변수로 전달.
> 성공시 메인 루프 실행.

{% tabs %}
{% tab title="Information" %}

| Name | Type | Description |
| :--- | :--- | :--- |
| container | HTML Container Element |  |  | 컨테이너 엘리먼트. |
| terrain | [Module.Initialize.Terrain](initialize.md#module.initialize.terrain) | Map 생성 정보. |

* Return
  * 생성 정보 반환.

  | Name | Type | Description(Content) |
  | --------- | ---- | -------- |
  | result | number | 성공 유무.<br>성공시 1. 실패시 0.</br> |
  | name | string | API 명칭.<br>"Module.Initialize" 고정.</br> |
  | return | string | 성공시 "success" 문자열 반환.<br>실패시 오류 메시지를 string으로 반환(자세한 사항은 메시지 참조).</br> |
{% endtab %}
{% endtabs %}

### Type Definitions

#### Module.Initialize.Terrain
| Name | Type | Description |
| --- | --- | --- |
| dem    | [Module.Initialize.Terrain.DEM](initialize.md#module.initialize.terrain.dem) | 지형 데이터. |
| image    | [Module.Initialize.Terrain.Image](initialize.md#module.initialize.terrain.image) | 영상 데이터. |

#### Module.Initialize.Terrain.DEM
| Name | Type | Description |
| --- | --- | --- |
| url    | string | 지형 데이터 url. |
| name    | string | 지형 레이어 이름. |
| servername    | string  | 사용자가 설정한 서버 이름. |
| encoding    | boolean | DEM 암호화 데이터 인식 여부.<br>true인 경우 암호화 되어 있음.</br><br>false인 경우 암호화 되어 있지 않음.</br> |

#### Module.Initialize.Terrain.Image
| Name | Type | Description |
| --- | --- | --- |
| url    | string | 영상 데이터 url. |
| name    | string | 영상 레이어 이름. |
| servername    | string | 사용자가 설정한 서버 이름. |
