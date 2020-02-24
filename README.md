# JQuery

## 선택자 사용하기
```
<script src="JS/jquery.js"></script>
<script>
$(document).ready(function(){	
  $('#title').css('color','red');
});        // - 1번

$(function(){
	$('#title').css('color','red');
});        // - 2번
</script>
<body>
 <h1 id="title">제목</h1>
</body>
```
## 그룹 선택자 사용하기
```
<script src="jquery.js"></script>
<script>
	$(function() {
		$('#title, h1').css("background-color", "#ff0")    // , 를 이용하여 여러 그룹 지정
		.css("border", "2px dashed #f00");

	});
</script>
</head>
<body>
	<h1>제이쿼리</h1>
	<h2 id="title">선택자</h2>
	<h3>직접 선택자</h3>
</body>
</html>
```

## 부모 요소 선택자 사용하기
```
<script src="jquery.js"></script>
<script>
	$(function() {
		$('#list_1').parent().css("border",  // #list_1의 부모 선택
				"2px dashed #f00");              // parents 선택시 모든상위 객체 선택

	});
</script>
</head>
<body>
	<h1>인접 관계 선택자</h1>
	<ul id="wrap">
		<li>
			<ul>
				<li id="list_1">리스트1-1</li>
				<li>리스트1-2</li>
			</ul>
		</li>
		<li>리스트1-3</li>
		<li>리스트1-4</li>
	</ul>
</body>
</html>
```

## 하위 요소 선택자 사용하기
```
<script>
	$(function() {
		$('#wrap h1').   // #wrap의 모든 h1 선택
		css({
			"background-color":"yellow",
			"border":"2px dashed #f00"
		});

	});
</script>
</head>
<body>
	<div id="wrap">
		<h1>인접 관계 선택자</h1>      
		<p>내용1</p>
		<section>
			<h1>하위 요소 선택자</h1>
			<p>내용2</p>
		</section>
	</div>
</body>
</html>
```

## 자식 요소 선택자 사용하기
```
<script src="jquery.js"></script>
<script>
	$(function() {
		$('#wrap > h1').css("border","2px dashed #f00");  // 자식 지정 
		
		$("#wrap > section").children()
		.css({
			"background-color":"yellow",
			"border":"2px solid #f00"
		});

	});
</script>
</head>
<body>
	<div id="wrap">
		<h1>인접 관계 선택자</h1>
		<p>내용1</p>
		<section>
			<h1>자식 요소 선택자</h1>
			<p>내용2</p>
		</section>
	</div>
</body>
</html>
```

## 형(이전) 동생(다음) 요소 선택자

```
<script src="jquery.js"></script>
<script>
	$(function() {
		var style_1 = {
			"background-color" : "#0ff",
			"border" : "2px solid #f00"
		}
		var style_2 = {
			"background-color" : "#ff0",
			"border" : "2px dashed #f00"
		}
		$(".txt").prev().css(style_1);   // 형(이전) 

		$(".txt + p").css(style_2);      // .txt 기준으로 바로 다음에 오는 p 선택

		$(".txt").next().next().css(style_2);  // .txt 기준으로 다음 다음 선택
    
    $(".txt").prevAll()   // .txt 기준으로 이전 요소 모두를 선택
		.css(style_1);
		
		$(".txt").nextAll()  // .txt 기준으로 다음 요소 모두 선택
		.css(style_2);
    
    $(".txt").siblings() // .txt 를 제외한 모든 형제 선택
		.css(style_1);
    
    $(".txt3").prevUntil("#title")  // .txt3과 #title 사이 이전 범위지정 (형)  
		.css(style_1);
		
		$(".txt3").nextUntil(".txt6")   // .txt3과 .txt6 사이 다음 범위지정  (동생) 
		.css(style_1);

	});
</script>
</head>
<body>
	<div id="wrap">
	  <h1 id="title">선택자</h1>
		<p>내용1</p>
		<p class="txt">내용2</p>
		<p class="txt3">내용3</p>
		<p>내용4</p>
		<p>내용5</p>
		<p class="txt6">내용6</p>

	</div>
</body>
</html>
```
