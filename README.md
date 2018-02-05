# Code-Player
Interactive Web Compiler With HTML CSS JavaScript
@@ -0,0 +1,171 @@
<html>
	<head>
		<title> WebTester</title>
		<link href="jquery-ui/jquery-ui.css" rel="stylesheet">
		<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
		
		<style type="text/css">
			body{
			
				font-family: sans-serif;
				padding: 0;
				margin: 0;
			}
			
			#header{
				width: 100%;
				background-color: #EEEEEE;
				padding: 5px;
				height: 30px;
			}
		
			#buttonContainer{
				width: 233px;
				margin: 0 auto;
				
			}
			
			#logo{
				float:left;
				font-weight: bold;
				font-size: 120%;
				padding: 3px 5px;
			}
			.toggleButton{
				float: left;
				border: 1px solid grey;
				padding: 6px;
				border-right: none;
				font-size: 90%;
			
			}
			
			#html{
			
				border-top-left-radius: 4px;
				border-bottom-left-radius: 4px;
			}
			
			#output{
				border-top-right-radius: 4px;
				border-bottom-right-radius: 4px;
				border-right: 1px solid grey;
			}
			
			.active{
				background-color: #E8F2FF;
				
			}
			
			.highlightedButton{
			
				background-color: grey;
			}
			
			textarea{
				width: 50%;
				height: 100%;
				resize: none;
				border-top: none;
				border-color: grey;
			}
			.panel{
				float: left;
				width: 50%;
				left-border: none;
			
			}
			
			iframe{
			
				border: none;
			}
			
			.hidden{
			
				display: none;
			}
		
		</style>
	
	</head>
	
	<body>
			
			<div id="header">
				<div id="logo">
					WebTester by Hung Ngo
				</div>
				<div id="buttonContainer">
			
					<div class="toggleButton active" id="html"> HTML</div>
					<div class="toggleButton" id="css"> CSS </div>
					<div class="toggleButton" id="javascript"> JavaScript</div>
					<div class="toggleButton active" id="output"> Output </div>
				
				</div>
			</div>
			
			<div id="bodyContainer">
				<textarea id="htmlPanel" class="panel"> <p> Hello World <p>				<h1> What's Up </h1>
<h2> I'm good </h2> 				<p>Type Your Code Here</p>
				</textarea>
			
				<textarea id="cssPanel" class="panel hidden"> p{ color: green; }</textarea>
				<textarea id="javascriptPanel" class="panel hidden"> alert("WebTester Start! Type Your Code On Either Button, to Stop Display This Popup Click on JavaScript Button and Delete the Code");</textarea>
				
				
				<iframe id="outputPanel" class="panel">
				
				
				
				</iframe>
			
			
			</div>
			<script type="text/javascript">
			
			function updateInput(){
				$("iframe").contents().find("html").html("<html> <head> <style type='text/css'>" + $("#cssPanel").val() + "</style>" +
					"</head><body>" + $("#htmlPanel").val() + "</body>" +"</html>");
					
					document.getElementById("outputPanel").contentWindow.eval($("#javascriptPanel").val());
					
				
			}
			
				$(".toggleButton").hover(function() {
					$(this).addClass("highlightedButton");
				
				}, function(){
					$(this).removeClass("highlightedButton");
				});
			
				$(".toggleButton").click(function(){
					$(this).toggleClass("active");
					$(this).removeClass("highlightedButton");
					var panelId = $(this).attr("id") + "Panel";
					$("#" + panelId).toggleClass("hidden");
					
					var numberOfActivePanel = 4 - $(".hidden").length;
					
					$(".panel").width(($(window).width())/ numberOfActivePanel - 10);
					
					
				});
				
				$(".panel").width(($(window).width())/ 2 - 10);
				$(".panel").height($(window).height() - $("#header").height() - 15);
				
				$("iframe").contents().find("html").html($("#htmlPanel").val());
				updateInput();
				$("textarea").on('change keyup paste', function(){
					updateInput();
				
				});
				
			</script>
	
	</body>

</html>
