# tiktak

<!DOCTYPE html>
<html>
<meta charset="utf-8">
<body>

<canvas id="canvas" width="690" height="690"
style="border:4px solid #c3c3c3;">

</canvas>




<p id="demo"></p>

<script>

var ctx = canvas.getContext("2d");
     

document.getElementById("canvas").addEventListener("click", function(event) {
  onClick(event);
});
var lastMove = 'x';
var BlocksOfGame = ['', '', '', '', '', '', '', '', ''];
function printState()

{
	alert(
	BlocksOfGame[0]+
	BlocksOfGame[1]+
	BlocksOfGame[2]+
	BlocksOfGame[3]+
	BlocksOfGame[4]+
	BlocksOfGame[5]+
	BlocksOfGame[6]+
	BlocksOfGame[7]+
	BlocksOfGame[8])
}
function calcBlockFromCoordinates(x, y) {
if (x < 235 && y < 235){
return 0;
}

else if (x > 465 && y < 235){
return 2;}

else{
(x > 235 && x < 465 && y < 235)
return 1;
}



if (x < 235 && y > 465){
return 6;
}

else if (x > 465 && y > 465){
return 8;
}

else{
(x > 235 && x < 465 && y < 465)
return 7;
}



if (x < 235 && y > 235 && y < 465){
return 3;
}

else if (x > 465 && y > 235 && y < 465){
return 5;
}

else{
(x > 235 && x < 465 && y > 235 && y < 465)
return 4;
}


}



function onClick(e) {
printState()
function drawX(x, y) {
ctx.beginPath();
ctx.moveTo(x + -35, y + -35);
ctx.lineTo(x + 35, y + 35);
ctx.moveTo(x + -35, y + 35);
ctx.lineTo(x + 35, y + -35);
ctx.stroke();
}

  
  function drawO(x, y, r) {
  ctx.beginPath();
  ctx.arc(x, y, r, 0, Math.PI * 2, true);
  ctx.stroke();
}
  
  var x = e.x - canvas.offsetLeft;
  var y = e.y - canvas.offsetTop;
  
   if (x < 235)
x = 115;
else if (x > 465)
x = 580;
else 
x = 350

  if (y < 230)
y = 115;
else if (y > 465)
y = 580;
else 
y = 350


 if (lastMove == 'x') {
lastMove = 'o';
drawO(x, y, 50)
} else {
lastMove = 'x';
drawX(x, y);
 
}
 

var block = calcBlockFromCoordinates(x, y);
BlocksOfGame[block] = lastMove;

}


ctx.beginPath();
ctx.moveTo(230, 0);
ctx.lineTo(230, 700);
ctx.moveTo(460, 0);
ctx.lineTo(460, 700);
ctx.moveTo(0, 230);
ctx.lineTo(690, 230);
ctx.moveTo(0, 460);
ctx.lineTo(690, 460);
ctx.stroke();


</script>
<button onclick="onClick()">Start game</button>
</body>
</html>
