---
description: 도로 기하구조 분석의 종단면(Profile) 결과를 조회하기 위한 API 입니다.
---

# JSRoadAnlProfile

> [JSRoadAnalysis.getProfile()](jsroadanalysis.md#getprofile-jsroadanlprofile)의 반환 객체로 생성됩니다.
>
> 직접 생성해서 사용하지는 않으며, 도로 종단면(진행 방향 고도 변화) 분석 결과를 조회하는 용도로 사용됩니다.

```javascript
var roadAnalysis = new Module.JSRoadAnalysis();
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
