# 시작하기

엔진 파일을 받은 후 구동하기까지 과정을 자세히 소개합니다.

최신 엔진 파일은 아래 깃허브에서 다운로드 받으실 수 있습니다.

{% embed url="https://github.com/EgisCorp/XDWorld" %}

### 엔진 파일 구성

깃허브에서는 엔진 파일 / 실행 스크립트 / 기본 HTML 페이지를 함께 배포합니다.

![](<../.gitbook/assets/image (1).png>)

엔진 파일은

* XDWorldEM.js
* XDWorldEM.asm.js
* XDWorldEM.html.mem

&#x20;엔진 파일은 세 가지 파일로 구성되어 있으며 다운로드 한 파일의 폴더 XDWorld-main/Release/(버전명)/js에서 찾을 수 있습니다.

&#x20;엔진을 구동할 때 세 파일이 순차적으로 로드되어야 하며,&#x20;

1. XDWorldEM.asm.js
2. XDWorld.html.mem
3. XDWorldEM.js

&#x20;파일 순으로 로드합니다.

![다음 단계에서 각 파일의 로드 과정에 대해 소개합니다.](<../.gitbook/assets/image (2).png>)

다음 단계에서 각 파일의 로드 과정에 대해 소개합니다.



### 엔진 파일 로드
