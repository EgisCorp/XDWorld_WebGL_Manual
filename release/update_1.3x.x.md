# - API 변경 내용 -

### 삭제 예정 API

### 삭제 API 대체 API

### 대체 API 참소 소스

# - 업데이트 내역 -

### Version_1.3. (2022년 월 일)

> -

### Version_1.3. (2022년 월 일)

> -

### Version_1.3. (2022년 월 일)

> -

### Version_1.3. (2022년 월 일)

> -

### Version_1.3. (2022년 월 일)

> -

### Version_1.3. (2022년 월 일)

> -

### Version_1.37.29 (2022년 09월 23일)

> -   메뉴얼 업데이트 JSTerrain, JSMath
> -   Module.getTerrain().makeTerrainElevationCellData("parameter") 추가
>     -   그리드 생성 기능
> -   Module.getMath().calculationSlopeAnalysis("parameter") 추가
>     -   [3 * 3] 배열값을 통한 경사 분석 기능
> -   Module.getMap().ScreenToMapPointEX API 실행 시 피킹점이 없는 경우 null 반환하도록 루틴 추가([이슈#211](https://github.com/EgisCorp/XDWorld/issues/211))

### Version_1.37.28 (2022년 09월 22일)

> -   비디오 텍스쳐 Zoom In/Out 기능 추가
> -   버텍스 및 인덱스가 활용 된 JSColorPolygon의 마우스 피킹 기능 수정
> -   3D POI 텍스트의 문자 셋 지정 프로퍼티 추가

```javascript
var layerList = new Module.JSLayerList(false);
var layer = layerList.nameAtLayer("POI 텍스트 타일 레이어 이름");
layer.text_character_set = "EUC-KR"; // 디폴트 셋은 UTF-8
```

### Version_1.37.27 (2022년 09월 14일)

> -   JSColorPolygon의 마우스 피킹 기능 추가

### Version_1.37.26 (2022년 09월 02일)

> -   ([이슈#203](https://github.com/EgisCorp/XDWorld/issues/203)) 해결

### Version_1.37.23 (2022년 08월 24일)

> -   비디오 텍스쳐 메모리 누수 관련 오류 수정
> -   ([비디오텍스쳐](http://sandbox.dtwincloud.com/code/main.do?id=object_video_texture))
> -   ([전광판](http://sandbox.dtwincloud.com/code/main.do?id=object_ledboard))

### Version_1.37.22 (2022년 08월 23일)

> -   터치 이동/회전/줌인&아웃 사용 설정 프로퍼티 추가([이슈 200](https://github.com/EgisCorp/XDWorld/issues/200))

```javascript
// 터치 이동 활성화(true), 비활성화(false)
Module.getControl().touchPanEnable = true;

// 터치 회전 활성화(true), 비활성화(false)
Module.getControl().touchRotateEnable = true;

// 터치 줌 인&아웃 활성화(true), 비활성화(false)
Module.getControl().touchZoomEnable = true;
```

### Version_1.37.21 (2022년 08월 19일)

> -   setDescription, getDescription uft16 지원([이슈 197](https://github.com/EgisCorp/XDWorld/issues/197))

### Version_1.37.20 (2022년 08월 04일)

> -   고스트심볼(JSGhostSymbol) z버퍼 off 프로퍼티 추가([이슈 194](https://github.com/EgisCorp/XDWorld/issues/194))

```javascript
var object = Module.createGhostSymbol("MY_OBJECT");
object.zBufferOff = true;
```

### Version_1.37.19 (2022년 08월 04일)

> -   건물 객첵 key List 기반 색상 변경 API 추가

### Version_1.37.18 (2022년 08월 02일)

> -   실시간 cctv 관제 편집기능 추가

### Version_1.37.17 (2022년 07월 26일)

> -   가시권 분석 이슈 처리([이슈 189](https://github.com/EgisCorp/XDWorld/issues/189))

### Version_1.37.16 (2022년 07월 19일)

> -   입력된 영역과 객체의 영역 충돌 체크 조건 추가 (완전 포함, 조금이라도 포함)
> -   라이브맵 1차
> -   JSMap의 setSimpleMode API 오류 수정

### Version_1.37.15 (2022년 07월 13일)

> -   레이어 별로 건물 심플 모드 설정이 가능한 JSLayer 프로퍼티 simple_real3d 추가

```javascript
var layerList = new Module.JSLayerList(false);
layer = layerList.nameAtLayer("building_layer_name");
layer.simple_real3d = true;
```

### Version_1.37.14 (2022년 07월 08일)

> -   입력된 영역과 객체의 영역 충돌 체크 오류 수정

### Version_1.37.13 (2022년 07월 07일)

> -   텍스쳐가 없는 Real3d의 색상 변경 API SetDefineMeshColorByObjectKey 미적용 오류 수정
> -   JSGhostSymbol의 API exportFileFormat에 XDO 텍스쳐 이미지 파일 지정 기능 추가

### Version_1.37.12 (2022년 07월 06일)

> -   입력된 영역과 객체의 영역 충돌 체크 오류 수정
> -   그림자 분석, 비디오 텍스쳐 기능 오류 수정
