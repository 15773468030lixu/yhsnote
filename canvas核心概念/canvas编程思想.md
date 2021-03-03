### 像素化
canvas没有能力修改已经在画布上的内容，这就是canvas比较轻量的原因

图形移动按照清屏-更新-渲染的逻辑进行编程，总之就是再画一次

面向对象的课程中，动画这种思想清屏-更新-渲染当做canvas动画思想 

```js
//顺序很重要！！！
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
console.log(ctx)
ctx.fillStyle="#FF0000";
//信号量  canvas动画过程
var left =100
setInterval(function(){
//0,0代表从什么位置开始清除， 画布的高度宽度
ctx.clearRect(0,0,600,600);  //清除画布
left++;
ctx.fillRect(left,100,100,100);   x/y/width/height
},30)
```


### 连续动画的过程
每一次的静态画面叫一帧，定时器的间隔代表帧率，面向对象进行编程，利用当前状态进行canvas编程
```js
  <canvas id="myCanvas" width="600" height="600"
    style="border:1px solid #000000;">
    </canvas>
    <script>
    var c=document.getElementById("myCanvas");
    var ctx=c.getContext("2d");
    function Rect(x,y,w,h,color){
        this.x=x;
        this.y=y;
        this.w=w;
        this.h=h;
        this.color=color;
    };
    Rect.prototype.update=function(){
            this.x++
    }
    Rect.prototype.render=function(){
        ctx.fillStyle=this.color;
        ctx.fillRect(this.x,this.y,this.w,this.h);  
    }
    //实例化
    var r1 = new Rect(100,100,50,50,"purple")
    setInterval(function(){
    //0,0代表从什么位置开始清除， 画布的高度宽度
    ctx.clearRect(0,0,myCanvas.width,myCanvas.height);  //清除当前myCanvas画布大小
    r1.update()
    r1.render()
    },10)
    </script> 

```

### canvas绘制功能[矩形]

```js
//顺序很重要！！！
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
console.log(ctx)
//填充
ctx.fillStyle="#FF0000";
ctx.fillRect(0,100,100,100); 
//绘制边框
ctx.strokeStyle="#c000000";
ctx.strokeRect(x, y, width, height);
```

绘制路径闭合的，不规则的多边形状态，需要既定的步骤

```js
//顺序很重要！！！
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
console.log(ctx)
//需要设置路径的起点，
ctx.beginPath() //路径开始和闭合
//使用画图的命令、绘制命令，
ctx.moveTo(100,100) //设置绘制起点(moveTo)
ctx.lineTo(200,200)  //绘制直线(lineTo)
ctx.lineTo(400,180)
ctx.lineTo(380,50)
//封闭路径
ctx.closePath() //路径开始和闭合
//填充已经封闭路径的形状
ctx.strokeStyle="#c000000";
ctx.stroke();  //绘制的边框颜色和根据路径绘制线。路径只是草稿，真正绘制线必须执行stroke
ctx.fillStyle="#FF0000";
ctx.fill(); 
```