## API 변경 내용

### 삭제 예정 API(2023년 01월 01일 까지 지원)

> -   SetPlanetImageryType
> -   changeBaseMap
> -   clearBaseMap
> -   setBaseMapOption
> -   getBaseMapOption

### 삭제 API 대체 API

> -   Module.GoogleMap();
> -   Module.ArcMap();
> -   Module.BingMap();
> -   Module.DaumMap();
> -   Module.MapBox();
> -   Module.NaverMap();
> -   Module.OpenStreetMap();
> -   Module.SKYMap();
> -   Module.WMTS();

### 대체 API 참소 소스

> -   [샌드박스\_배경지도설정](http://sandbox.dtwincloud.com/code/main.do?id=layer_basemap)
> -   [샌드박스\_WMTS](http://sandbox.dtwincloud.com/code/main.do?id=layer_wmts)

### 2022년 7월 05일

> -   리소스 URL 설정 API 추가
> -   맵컨트롤을 사용하기 위해서는 리소스 다운로드 해주시기 바랍니다.
> -   리소스 설정 샘플 샌드박스\_맵컨트롤
> -   입력된 영역과 객체의 영역 충돌 체크 API 추가

### 2022년 6월 29일

> -   XDO 포맷 파일 기반 고스트심볼 import 및 export API 추가

### 2022년 6월 20일

> -   Tile LOD Object 프로토콜 예외처리 추가

### 2022년 6월 8일

> -   포인트 클라우드 실시간 높이 조절 기능 구현(Tile LOD Object와 동일)
> -   Tile LOD Object 가시화 모듈 수정

### 2022년 5월 19일

> -   배경지도 변경 오류 수정
> -   선택 기능 추가
> -   JSMap addSelectObject 기능추가

### 2022년 4월 27일

> -   JSLibraryObject, JSBuildingManager 클래스 API 삭제

### 2022년 4월 22일

> -   WMTS, 배경지도 오류 수정
> -   WMTS 하이브리드 기능 추가

### 2022년 4월 21일

> -   Real3D 객체 페이스 색상 가시화 모듈 수정
> -   JSLineString 좌표 반환 기능 오류 수정

### 2022년 4월 15일

> -   Real3D 3DS export 시 메시 방향 지정 오류 수정
