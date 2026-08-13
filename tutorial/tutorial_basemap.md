# 배경 지도 설정

Google, BingMap, OpenStreetMap, ArcMap, MapBox, 네이버, 다음, SKYMap 지도를 배경지도로 설정할 수 있습니다.

## 1. GoogleMap 설정하기

nomal, terrain, vectorhybrid, satellitehybrid, satellite 레이어를 지원합니다.

```javascript
var google = Module.GoogleMap();
google.apikey = {API KEY};
google.layername = "satellitehybrid";
```

### 옵션 설정하기

```javascript
// 레이어 변경
google.layername = "satellitehybrid";

// API Key 입력
google.apikey = {API KEY};

// 이미지 품질 변경
google.quality = "middle";

// 이미지 LOD 변경
google.zerolevelOffset = 1;
```

## 2. BingMap 설정하기

nomal, satellitehybrid, satellite 레이어를 지원합니다.

```javascript
var bing = Module.BingMap();
bing.apikey = {API KEY};
bing.layername = "satellitehybrid";
```

### 옵션 설정하기

```javascript
// 레이어 변경
bing.layername = "satellitehybrid";

// API Key 입력
bing.apikey = {API KEY};

// 이미지 품질 변경
bing.quality = "middle";

// 이미지 LOD 변경
bing.zerolevelOffset = 1;
```

## 3. OpenStreetMap 설정하기

nomal, terrain 레이어를 지원합니다.

```javascript
var osm = Module.OpenStreetMap();
```

### 옵션 설정하기

```javascript
// 레이어 변경
osm.layername = "terrain";

// 이미지 품질 변경
osm.quality = "middle";

// 이미지 LOD 변경
osm.zerolevelOffset = 1;
```

## 4. ArcMap 설정하기

nomal, terrain, vectorhybrid, satellite 레이어를 지원합니다.

```javascript
var arc = Module.ArcMap();
arc.apikey = {API KEY};
```

### 옵션 설정하기

```javascript
// 레이어 변경
arc.layername = "vectorhybrid";

// API Key 입력
arc.apikey = {API KEY};

// 이미지 품질 변경
arc.quality = "middle";

// 이미지 LOD 변경
arc.zerolevelOffset = 1;
```

## 5. MapBox 설정하기

satellite 레이어를 지원합니다.

```javascript
var mapbox = Module.MapBox();
mapbox.apikey = {API KEY};
```

### 옵션 설정하기

```javascript
// 레이어 변경
mapbox.layername = "satellite";

// API Key 입력
mapbox.apikey = {API KEY};

// 이미지 품질 변경
mapbox.quality = "middle";

// 이미j지 LOD 변경
mapbox.zerolevelOffset = 1;
```

## 9. 레이어 타입 명칭

> .layername Tag 설정 명칭 목록.

| Name            | Type   | Description  |
| --------------- | ------ | ------------ |
| nomal           | string | 일반 지도.       |
| terrain         | string | 지형 등고선 지도.   |
| vectorhybrid    | string | 벡터 하이브리드 지도. |
| satellitehybrid | string | 영상 하이브리드 지도. |
| satellite       | string | 영상 지도.       |
