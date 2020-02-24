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

## 상위 요소 선택자

```
<script src="jquery.js"></script>
<script>
	$(function() {

		$(".txt1").parents().css({           // .txt1의 모든 부모 선택
			"border" : "2px dashed #00f"
		});

		$(".txt2").parents("div").css({      //  .txt2의 부모 중에서 div만 선택
			"border" : "2px solid #f00"
		});
		
		$(".txt1").closest("div").css({      // .txt1을 기준으로 가장 가까운 div선택 *
			"border" : "2px solid #f00"
		});

	});
</script>
</head>
<body>
	<h1 class="title">선택자</h1>
	<section>
	     <div>
		<div>                                // .txt1을 기준으로 가장 가까운 div  *
			<p class="txt1">내용</p>
		</div>
	     </div>
	</section>
	<section>
		<div>
			<p class="txt2">내용</p>
		</div>
	</section>
</body>
</html>
```

# 제이쿼리 탐색 선택자

## first , last 선택자

```
<script src="jquery.js"></script>
<script>
	$(function() {

		$("#menu li:first").css({            // 첫번째 요소 선택
			"background-color" : "#ff0"
		});

		$("#menu li:last").css({             // 마지막 요소 선택
			"background-color" : "#0ff"
		});
		
		$("#menu li:even").css({             // 짝수 번호 요소 선택
			"background-color" : "#ff0"
		});

		$("#menu li:odd").css({              // 홀수 번호 요소 선택
			"background-color" : "#0ff"
		});
		
		$("#menu li:eq(2)").css({            // 해당 인덱스 2 에만 적용
			"background-color" : "#ff0"
		});

		$("#menu li:lt(2)").css({           // (lt, Less Than) 해당 인덱스 2 보다 작은 인덱스에 적용
			"background-color" : "#0ff"
		});
		
		$("#menu li:gt(2)").css({           // (gt, Greater Than) 해당 인덱스 2보다 큰 인덱스에 적용
			"background-color" : "#f0f"
		});

	});
</script>
</head>
<body>
	<h1>탐색 선택자</h1>
	<ul id="menu">
		<li>내용1</li>
		<li>내용2</li>
		<li>내용3</li>
		<li>내용4</li>
		<li>내용5</li>
	</ul>
</body>
</html>
```

## first-of-type , last-of-type

```
<script src="jquery.js"></script>
<script>
	$(function() {

		$("li:first-of-type").css({           // 모든 li 중 첫 번째 요소에 적용
			"background-color" : "#ff0"
		});

		$("li:last-of-type").css({            // 모든 li 중 마지막 번째 요소에 적용
			"background-color" : "#0ff"
		});
		
		$("#menu1 li:nth-child(1)").css({     // #menu1의 자식 중에서 1번째 요소에 적용
			"background-color" : "#ff0"
		});

		$("#menu1 li:nth-child(2n)").css({    // #menu1의 자식 중에서 2의 배수 요소에 적용
			"border" : "2px dashed #f00"
		});

		$("#menu2 li:nth-last-child(2)").css({   // #menu2의 자식 중에서 마지막에서 2번째 요소에 적용
			"background-color" : "#0ff"
		});
		
		$("#menu1 li").slice(1,3).css({       // #menu1의 li 중에서 1 초과 3 이하 적용
			"background-color":"#ff0"
		});
		
		$("li:only-child").css({              // 부모중 li가 1개만 있는 요소에 적용 
			"background-color":"#0ff"
		});


	});
</script>
</head>
<body>
	<h1>탐색 선택자</h1>
	<ul id="menu1">
		<li>내용1-1</li>
		<li>내용1-2</li>
		<li>내용1-3</li>
		<li>내용1-4</li>
	</ul>
	<ul id="menu2">
		<li>내용2-1</li>
		<li>내용2-2</li>
		<li>내용2-3</li>
		<li>내용2-4</li>
	</ul>
</body>
</html>
```
