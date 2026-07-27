---
description: 도로 기하구조 분석의 종단면(Profile) 결과를 조회하기 위한 독립형(Standalone) API 입니다.
---

# JSSRoadAnlProfile

> [JSSRoadAnalysis.getProfile()](jssroadanalysis.md#getprofile-jssroadanlprofile-jssroadanlprofilemd)의 반환 객체로 생성됩니다.
>
> [JSRoadAnlProfile](../analysis/jsroadanlprofile.md)와 API 구성 및 동작이 동일하나, [JSSRoadAnalysis](jssroadanalysis.md)의 전역 싱글턴 분석 데이터를 사용하는 독립형(Standalone) 버전입니다. 직접 생성해서 사용하지는 않습니다.

```javascript
var roadAnalysis = new Module.JSSRoadAnalysis();
// ...(setJsonData로 분석 수행)...
var profile = roadAnalysis.getProfile();
```

## Function

### getProfileJSON() → string

> 종단면 상세 정보(진행 방향 좌표 목록, 경사, 최대/최소 고도, 전체 길이)를 JSON 문자열로 반환합니다.

{% tabs %}
{% tab title="Information" %}

-   Return
    -   string: 종단면 정보 JSON 문자열(`type: "Profile Geometry Analisys Output"`).
    -   "": 내부 데이터가 없는 경우.

{% endtab %}
{% tab title="Template" %}

```javascript
var json = profile.getProfileJSON();
console.log(JSON.parse(json));
```

{% endtab %}
{% endtabs %}
