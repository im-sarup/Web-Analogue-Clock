var canvas = document.getElementById("canvas"); /* Creating a canvas object that apply in HTML file*/
var ctx = canvas.getContext("2d"); /*Creating a 2D drawing object*/
var redius = canvas.height / 2; /*Calculate the height of the clock radius by clock height*/
ctx.translate(redius, redius); /*clock position or remap, i.e., x and y positioning value of the clock drawing in web page*/
redius = redius * 0.90;
// drawClock();
setInterval(drawClock, 1000);

function drawClock() {  
    drawFace(ctx, redius);  /*declear function for display clock face */
    drawNumber(ctx, redius);    /*declear function for display clock numbers */
    drawTime(ctx, redius);    /*declear function for display clock hands and timing settings */
    drawHand(ctx, pos, length, width);
}

function drawFace(ctx, redius) {
    var grad;
    ctx.beginPath();
    ctx.arc(0,0,redius,0,2*Math.PI);    /*context.arc describe the arc or curve of the clock or circle curve, Math.PI describe the ration of circumference of the circle for the diameter*/
    ctx.fillStyle = "White";    /* face of the clock fill by white*/
    ctx.fill(); /* this method fill the default colour in black*/

    grad = ctx.createRadialGradient(0,0,redius*0.95, 0,0,redius*1.05); /*Creading a radialGradient, which is 95% and 105% of original clock redius */
    grad.addColorStop(0, '#333');   /*inner edge arc and color*/ 
    grad.addColorStop(0.5, 'white');    /*middle edge arc and color*/
    grad.addColorStop(1, '#333');   /*outer edge arc and color*/

    ctx.strokeStyle = grad;  /*define gradient as a strokeStyle object */
    ctx.lineWidth = redius * 0.1; /*line width of the drawing object which is 10% of the redius */
    ctx.stroke(); /* stroke method to draw the circle */
    
    /*actual center for the clock */
    ctx.beginPath();
    ctx.arc(0, 0, redius*0.1, 0, 2*Math.PI);    /*context.arc describe the arc or curve of the clock or circle curve, Math.PI describe the ration of circumference of the circle for the diameter*/
    ctx.fillStyle = "#333";    /* face of the clock fill by white*/
    ctx.fill(); /* this method fill the default colour in black*/ /* */
}

function drawNumber(ctx, redius) {
    var ang;
    var num;

    ctx.font = redius*0.15 + "px arial";
    ctx.textBaseline = "middle";
    ctx.textAlign = "center";

    for(num=1; num<13; num++){
        ang = num * Math.PI/6;
        ctx.rotate(ang);
        ctx.translate(0, -redius*0.85);
        ctx.rotate(-ang);
        ctx.fillText(num.toString(), 0, 0);
        ctx.rotate(ang);
        ctx.translate(0, redius*0.85);
        ctx.rotate(-ang);
    }
}

function drawTime(ctx, redius){
    var now = new Date;
    var hour = now.getHours();
    var minute = now.getMinutes();
    var second = now.getSeconds();
    
    //hour 
    hour = hour%12;
    hour = (hour * Math.PI/6) + (minute * Math.PI/(6*60)) + (second * Math.PI/(60*360)) ;
    drawHand(ctx, hour, redius*0.5, redius*0.07);

    //minute
    minute = (minute * Math.PI/30) + (second * Math.PI/(30*60));
    drawHand(ctx, minute, redius*0.8, redius*0.07);

    //second
    second = (second * Math.PI/30);
    drawHand(ctx, second, redius*0.9, redius*0.02);
}

function drawHand(ctx, pos, length, width){
    ctx.beginPath();
    ctx.lineWidth = width;
    ctx.lineCap = "round";
    ctx.moveTo(0, 0);
    ctx.rotate(pos);
    ctx.lineTo(0, -length);
    ctx.stroke();
    ctx.rotate(-pos);
}

