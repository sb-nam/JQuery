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
# 제이쿼리 배열 관련 메소드

## $.map() / $.grep() 메소드

```
$.map(Array,function(매개변수1, 매개변수2) {
   return 데이터;
});


$.grep(Array,function(매개변수1, 매개변수2) {
   return [true | false];
});
<script src="jquery.js"></script>
<script>
$(function() {
	var arr1 = [{
		area:"서울",
		name:"무대리"
	}, {
		area:"부산",
		name:"홍과장"
	},{
		area:"서울",
		name:"빅마마"
	}]
	
	var arr2 = $.map(arr1,function(a,b){
		if(a.area == "서울") {
			return a;
		} 		
	});
	
	console.log(arr2);
	console.log("========== first End =========");
	
	var arr3 = $.grep(arr1,function(a,b){
		if(a.area == "서울") {
			return true;
		} else {
			return false;
		}
	});
	
	console.log(arr3);
	console.log("========== second End =========");
});

</script>
```

## $.inArray() / $.isArray() / $.merge() 메소드
```
<script src="jquery.js"></script>
<script>
$(function() {
	var arr1 = ["서울","대전","부산","전주"];
	var arr2 = ["한국","미국","일본","중국"];
	var obj = {
			name:"정부장",
			area:"서울"
	}
	
	var idxNum = $.inArray("부산",arr1);     //배열에 저장된 데이터를 인덱스 오름차순으로 찾아 먼저 찾은
	console.log(idxNum);                     //데이터의 인덱스 값을 반환함.
	
	var okArray1 = $.isArray(arr1);          // 지정한 객체가 배열이면 true
	var okArray2 = $.isArray(obj);           // 객체가 아니면 false
	console.log(okArray1);
	console.log(okArray2);
	
	$.merge(arr2,arr1);                     // 두 배열 객체를 하나의 배열 객체로 묶는다.
	console.log(arr2);
});

</script>
```

## 속성 탐색자
```

<script src="jquery.js"></script>
<script>
	$(function() {
		$("#wrap a[target]")          // target 속성을 포함하는 요소 선택
		.css({"color":"#f00"});      
		
		$("#wrap a[href^=https]")     // href 속성값이 https로 시작하는 요소 선택
		.css({"color":"#0f0"});       
		
		$("#wrap a[href$=net]")       // href 속성값이 net으로 끝나는 요소 선택
		.css({"color":"#00f"});
		
		$("#wrap a[href*=google]")    // href 속성값에 google이 포함된 요소 선택
		.css({"color":"#000"});
		
		$("#member_f :text")          // input 요소중 type이 "text"인 요소 선택
		.css({"background-color":"#ff0"});
		
		$("#member_f :password")      // input 요소중 type이 "password"인 요소 선택
		.css({"background-color":"#0ff"});
	});
</script>
</head>
<body>
	<div id="wrap">
		<p>
			<a href="http://easyspub.co.kr" target="_blank">EasysPub</a>
		</p>
		
		<p>
			<a href="https://naver.com">Naver</a>
		</p>
		
		<p>
			<a href="https://google.co.kr">Google</a>
		</p>
		
		<p>
			<a href="https://daum.net">Daum</a>
		</p>
		
	</div>
	<form action="#" method="get" id="member_f">
		<p>
			<label for="user_id">아이디</label><input type="text" name="user_id"
				id="user_id">
		</p>
		<p>
			<label for="user_pw">비밀번호</label><input type="password"
				name="user_pw" id="user_pw">
		</p>
	</form>
</body>
</html>
```

## 속성에 따른 탐색 선택자
```
<script src="jquery.js"></script>
<script>
	$(function() {
		$("#wrap p:hidden")      //("요소선택: visible | hidden") 숨겨진 상태 or 보이는 상태의 요소만 선택
		.css({
			"display" : "block",
			"background":"#ff0"
		});
		
		var z1=$("#zone1 :selected").val();  //#zone1의 하위 요소 중 에서 selected된 요소만 선택
		console.log(z1);
		
		var z2=$("#zone2 :checked").val();   //#zone2의 하위 요소 중 에서 checked된 요소만 선택
		console.log(z2);

		var z3=$("#zone3 :checked").val();   // (":checked")는 radio, checkbox 요소만 선택한다.
		console.log(z3);
		
	});
</script>
</head>
<body>
	<div id="wrap">
		<p>내용1</p>
		<p style="display: none">내용2</p>
		<p>내용3</p>
	</div>
	<form action="#">
		<p id="zone1">
			<select name="course" id="course">
				<option value="opt1">옵션1</option>
				<option value="opt2" selected>옵션2</option>
				<option value="opt3">옵션3</option>
			</select>
		</p>
		<p id="zone2">
			<input type="checkbox" name="hobby1" value="독서">독서 
			<input type="checkbox" name="hobby2" value="자전거">자전거 
			<input type="checkbox" name="hobby3" value="등산" checked>등산
		</p>
		<p id="zone3">
			<input type="radio" name="gender" value="male">남성 
			<input type="radio" name="gender" value="female" checked>여성
		</p>
	</form>
</body>
</html>
```
## 콘텐츠 선택자
```
<script src="jquery.js"></script>
<script>
	$(function() {
		$("#inner_1 p:contains(내용1)").css({ // 선택한 p 중 내용1을 포함하는 요소만 선택
			"background-color" : "#ff0"
		});

		$("#inner_1 p:has(strong)").css({  // 선택한 p 중 strong을 포함하는 요소만 선택
			"background-color" : "#0ff"
		});

		$("#outer_wrap").contents().css({ //outer_wrap의 하위 요소의 텍스트,테그노드 선택
			"border" : "1px dashed #00f"
		});

		$("#inner_2 p").not(":first").css({ //inner_2의 하위 요소에서 첫번째 요소만 제외하고 선택
			"background-color" : "#0f0"
		});

		$("#inner_2 p").eq(2).end().css({
			"color" : "#f00"
		});
		
		$("inner_1 p").find("txt1").css({
			"background-color":"#ff0"
		});
		
		$("inner_1 p").filter("txt2").css({
			"background-color":"#0ff"
		});
		
		$("inner_1").filter(function({
			console.log(idx);
			return idx % 2==0;
		})
		.css({
			"background-color":"#0f0"
		});
	});
</script>
</head>
<body>
	<div id="outer_wrap">
		<h1>콘텐츠 탐색 선택자</h1>
		<section id="inner_1">
			<h1>contains(), contents(), has()</h1>
			<p>
				<span>내용1</span>
			</p>
			<p>
				<strong>내용2</strong>
			</p>
			<p>
				<span>내용3</span>
			</p>
		</section>
		<section id="inner_2">
			<h1>not(), end()</h1>
			<p>내용4</p>
			<p>내용5</p>
			<p>내용6</p>
		</section>
	</div>

</body>
</html>
```

# JQuery이벤트

## 단독 이벤트 등록 메서드
```
단독 이벤트 등록 메소드

$("이벤트 대상 선택").이벤트 등록 메서드(function(){
   자바스크립트 코드;
});

<script type="text/javascript">
	$(function() {
		$('#btn').click(function() {
			alert("click 이벤트 발생");
		});
	});
</script>

```

## 그룹 이벤트 등록 매소드
```
<script src="jquery.js">
	
</script>
<script type="text/javascript">
	$(function() {
		$(".btn1").click(function() {
			$(".btn1").parent().next()
			.css({
				"color":"#f00"
			});
		});
		
		$(".btn2").on({
			"mouseover focus":function(){
				$(".btn2").parent().next()
				.css({
					"color":"#0f0"
				});
			},
			"mouseout blur":function(){
				$(".btn2").parent().next()
				.css({
					"color":"#000"
				});
			}
		});
	});
</script>
</head>
<body>
	<p>
		<button class="btn1">버튼1</button>
	</p>
	<p>내용1</p>
	<p>
		<button class="btn2">버튼2</button>
	</p>
	<p>내용2</p>
</body>
```

## 이벤트 적용시 이벤트 차단하기
```
<script src="jquery.js">
	
</script>
<script type="text/javascript">
	$(function() {

		$(".btn1").on("click",function(e){
			e.preventDefault();       // 링크 페이지로 이동 차단
			$(".txt1").css({
				"background-color":"#ff0"
			});
		});
		$(".btn2").on("click",function(e){        
			$(".txt2").css({
				"background-color":"#0ff"
			});
		});
		$(".btn3").on("dblclick",function(){        // 더블클릭시 적용
			$(".txt3").css({
				"background-color":"#0f0"
			});
		});
	});
</script>
</head>
<body>
	<p>
		<a href="http://www.easyspub.co.kr" class="btn1">버튼1</a>
	</p>
	<p class="txt1">내용1</p>
	<p>
		<a href="http://www.easyspub.co.kr" class="btn2">버튼2</a>
	</p>
	<p class="txt2">내용2</p>
	<p>
		<button class="btn3">버튼3</button>
	</p>
	<p class="txt3">내용3</p>
</body>
</html>
```
# 애니메이션
```
<script src="jquery.js">
	
</script>
<script type="text/javascript">
	$(function() {
		$(".btn2").hide();

		$(".btn1").on("click", function() {
			$(".box").slideUp(1000, "linear", function() {
				$(".btn1").hide();
				$(".btn2").show();
			});
		});

		$(".btn2").on("click", function() {
			$(".box").fadeIn(1000, "swing", function() {
				$(".btn2").hide();
				$(".btn1").show();
			});
		});

		$(".btn3").on("click", function() {
			$(".box").slideToggle(1000, "linear");
		});

		$(".btn4").on("click", function() {
			$(".box").fadeTo("fast", 0.3);
		});

		$(".btn5").on("click", function() {
			$(".box").fadeTo("fast", 1);
		});
	});
</script>
<style type="text/css">
.content{
  width: 400px;
  background-color: #eee;
}
</style>
</head>
<body>

	<p>
		<button class="btn1">slideUp</button>
		<button class="btn2">fadeIn</button>
	</p>
	<p>
		<button class="btn3">toggleSlide</button>
	</p>
	<p>
		<button class="btn4">fadeTo(0.3)</button>
		<button class="btn5">fadeTo(1)</button>
	</p>
	<div class="box">
		<div class="content">lorem</div>
	</div>
</body>
```
```
<script type="text/javascript">
	$(function() {
		$(".btn1").on("click", function() {
			$(".txt1").animate({
				marginLeft: "500px",
			    fontSize: "30px"
			},
			2000,"linear",function() {
				alert("모션완료!");
			});
		});
		
		$(".btn2").on("click", function() {
			$(".txt2").animate({
				marginLeft: "+=50px"
			},1000);			
		});
		
	});
</script>
<style type="text/css">
.txt1 {
	background-color: aqua;
}

.txt2 {
	background-color: pink;
}
</style>
</head>
<body>

	<p>
		<button class="btn1">버튼1</button>
	</p>
	<p>
		<span class="txt1">"500px" 이동</span>
	</p>
	<p>
		<button class="btn2">버튼2</button>
		<span class="txt2">"50px"씩 이동</span>
	</p>
	
</body>

</html>
```
## stop 메소드
```
$(function() {

		$(".txt1").animate({
			marginLeft : "300px"
		}, 1000);

		$(".txt2").delay(3000).animate({
			marginLeft : "300px"
		}, 1000);

		$(".btn1").on("click", moveElement);

		function moveElement() {
			$(".txt3").animate({
				marginLeft : "+=50px"
			}, 800);

			$(".txt4").animate({
				marginLeft : "+=50px"
			}, 800);
			$(".txt4").stop();

			$(".txt5").animate({
				marginLeft : "+=50px"
			}, 800);
			$(".txt5").stop(true,ture);
		}
	});
	
```	
