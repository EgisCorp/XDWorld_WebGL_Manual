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

자세한 설명에 앞서, 기본 index.html 페이지와 엔진 파일 로드를 위한 init.js 파일의 코드는 다음과 같습니다.

(index.html 파일과 init.js 파일은 다운로드 엔진 폴더에 기본으로 첨부되어 있으므로 그대로 활용하실 수 있습니다.)

{% tabs %}
{% tab title="index.html" %}
```html
<!doctype html>
<html>
<head>
	<title>[EGIS] Init
</head>
<body>
	<script>
		var initScript = document.createElement('script');
		initScript.src = "./js/init.js";
		document.body.appendChild(initScript);
	</script>
</body>
</html>
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="init.js" %}
```javascript
// 엔진 로드 후 실행할 초기화 함수(Module.postRun)
function init() {

   // 엔진 초기화 API 호출(필수)
   Module.Start(window.innerWidth, window.innerHeight);
}

var Module = {
   TOTAL_MEMORY: 256*1024*1024,
   postRun: [init],
   canvas: (function() {
		
      // Canvas 엘리먼트 생성
      var canvas = document.createElement('canvas');
		
      // Canvas id, Width, height 설정
      canvas.id = "canvas";
      canvas.width="calc(100%)";
      canvas.height="100%";
		
      // Canvas 스타일 설정
      canvas.style.position = "fixed";
      canvas.style.top = "0px";
      canvas.style.left = "0px";

      // contextmenu disabled
      canvas.addEventListener("contextmenu", function(e){
         e.preventDefault();
      });
	
      // 생성한 Canvas 엘리먼트를 body에 추가합니다.
      document.body.appendChild(canvas);
      return canvas;
   })()
};

// 엔진 파일 로드
;(function(){   	

   // 1. XDWorldEM.asm.js 파일 로드
   var file = "./js/XDWorldEM.asm.js";
	
   var xhr = new XMLHttpRequest();
   xhr.open('GET', file, true);
   xhr.onload = function() {
	
      var script = document.createElement('script');
      script.innerHTML = xhr.responseText;
      document.body.appendChild(script);
		
      // 2. XDWorldEM.html.mem 파일 로드
      setTimeout(function() {
         (function() {
            var memoryInitializer = "./js/XDWorldEM.html.mem";
            var xhr = Module['memoryInitializerRequest'] = new XMLHttpRequest();
            xhr.open('GET', memoryInitializer, true);
               xhr.responseType = 'arraybuffer';
               xhr.onload =  function(){
						
                  // 3. XDWorldEM.js 파일 로드
                  var url = "./js/XDWorldEM.js";
                  var xhr = new XMLHttpRequest();
                  xhr.open('GET',url , true);
                  xhr.onload = function(){
                     var script = document.createElement('script');
                     script.innerHTML = xhr.responseText;
                     document.body.appendChild(script);
                  };
                  xhr.send(null);
               }
               xhr.send(null);
            })();
         }, 1);
      };
      xhr.send(null);
   }
)();

window.onresize = function() {
   if (typeof Module == "object") {
      Module.Resize(window.innerWidth, window.innerHeight);
      Module.XDRenderData();
   }
};
```
{% endtab %}
{% endtabs %}

