###  
前端动画可以通过CSS3的过渡（transition）和关键帧动画（@keyframes）、JavaScript的动画库（如GreenSock Animation Platform）、HTML5的canvas元素、SVG（可缩放矢量图形）以及其他前端技术来实现。这些动画可以是简单的渐变，也可以是复杂的交互式3D效果

### 1. 常用的css变换
1. 呼吸态效果
```css
    .box {
        width: 200px;
        height: 200px;
        background-color: blueviolet;
        border-radius: 15px;
    }
    
    .box-animation1 {
        animation: testAnimation 0.5s alternate infinite;
    }

    @keyframes testAnimation {
        0% {
            transform: scale(0.8);
        }

        100% {
            transform: scale(1);
        }
    }
    /* 或者 */
    
    .box-animation1 {
        animation: testAnimation1 1s infinite;
    }
    @keyframes testAnimation1 {
        0% {
            transform: scale(0.8);
        }

        50% {
            transform: scale(1);
        }

        100% {
            transform: scale(0.8);
        }
    }
  
```
2. 淡入淡出效果
```css
    .box1 {
        width: 200px;
        height: 200px;
        background-color: blueviolet;
        border-radius: 15px;
    }

    .box1-animation {
        animation: box1tAnimation 2s linear infinite;
    }

    @keyframes box1tAnimation {
        0% {
            opacity: 0;
            transform: translateX(-120px);
        }

        25% {
            opacity: 0.25;
            transform: translateX(-90px);
        }


        50% {
            opacity: 0.5;
            transform: translateX(-60px);
        }

        75% {
            opacity: 0.75;
            transform: translateX(-30px);
        }

        100% {
            opacity: 1;
            transform: translateX(0px);
        }
    }

```
3. 鼠标悬停效果
```css

    .button {
        width: 200px;
        height: 30px;
        border-radius: 20px;
        background: darkcyan;
    }

    .button:hover {
        transform: scale(1.1);
        transition: all 0.5s linear;
    }

```
4. loading效果
```html
  <div class="box">
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
  </div>
```
```css
    html,
    body {
      margin: 0;
      padding: 0;
    }

    .box {
      width: 300px;
      height: 300px;
      margin: 200px auto 0;
      display: flex;
    }

    .box1 {
      width: 10px;
      height: 10px;
      background-color: rgb(255, 0, 0);
      border-radius: 50%;
      margin-right: 10px;
      animation: boxma 1s 0.2s infinite alternate;
    }

    .box2 {
      width: 10px;
      height: 10px;
      background-color: rgb(10, 241, 125);
      border-radius: 50%;
      margin-right: 10px;
      animation: boxma 1s 0.5s infinite alternate;
    }

    .box3 {
      width: 10px;
      height: 10px;
      background-color: rgb(28, 3, 250);
      border-radius: 50%;
      margin-right: 10px;
      animation: boxma 1s 0.8s infinite alternate;
    }

    @keyframes boxma {
      0% {
        opacity: 0;
      }

      100% {
        opacity: 1;
      }
    }

```

5. 加载动画
```html
        <div class="process-box">
            <div class="process-content" id="content"></div>
        </div>

```
```css
 
    .process-box {
        width: 350px;
        height: 20px;
        border-radius: 20px;
        position: relative;
        border: 1px solid red;
        transition: all linear;
    }

    .process-content {
        height: 100%;
        border-radius: 20px;
        background-color: aqua;
    }
```
```js
        const content = document.getElementById('content')
        let timer = null
        let width = 0
        function process() {
            timer = setInterval(() => {
                if (width >= 100) {
                    clearInterval(timer);
                } else {
                    width += 12;
                    if (width > 100) {
                        width = 100
                    }
                    content.style.width = width + '%';
                }
            }, 200)
        }

        process()

```
6. 有趣的动画
```html
<div class="test1 openUpRight">
```
```css

    .test1 {
        width: 200px;
        height: 200px;
        background-color: aqua;
        border-radius: 15px;
    }
    .openUpRight {
        animation: openUpRight 2s alternate infinite;
    }

    @keyframes openUpRight {
        0% {
            transform-origin: top right;
            transform: rotate(0deg);
        }

        100% {
            transform-origin: top right;
            transform: rotate(-110deg);
        }
    }

```
2.关于animation与transtion实现动画
```html
Transition（过渡）：
  适用场景：transition 主要用于实现简单的过渡效果，例如鼠标悬停时的颜色或大小变化、链接的颜色渐变等。它非常适合在状态变化时添加平滑的转换效果。
Animation（动画）:
  适用场景：animation 更为灵活，适用于复杂的、循环的、多步骤的动画效果，可以控制关键帧、延迟、持续时间、重复次数等各个方面。它适用于需要更高度自定义和控制的动画场
```
### 3. 浅谈一下3D变换
1. 翻书效果
```html
        <div class="perspective">
            <div class="perspective-left">

            </div>
            <div class="test2 perspectiveRight">
            </div>
        </div>
```
```css

    .perspective {
        position: relative;
    }

    .perspective-left {
        width: 200px;
        height: 200px;
        background-color: forestgreen;
        border-radius: 15px;
    }
    
    .test2 {
        top: 0;
        position: absolute;
        width: 200px;
        height: 200px;
        background-color: rebeccapurple;
        border-radius: 15px;
    }
    .perspectiveRight {
        animation: perspectiveRight 2s alternate infinite;
    }

    @keyframes perspectiveRight {
        0% {
            transform-origin: 100% 0;
            transform: perspective(800px) rotateY(0deg);
        }

        100% {
            transform-origin: 100% 0;
            transform: perspective(800px) rotateY(180deg);
        }
    }
```
2. 3D翻转
```html

    <div class="test4 test4-animation"></div>

```
```css

    .test4 {
        width: 200px;
        height: 200px;
        background-color: blueviolet;
        border-radius: 15px;
    }

    .test4-animation {
        /* transition: all 1s ease-in-out; */
        animation: test4animation 2s alternate infinite;
        /* animation: test4animation 1s cubic-bezier(0.455, 0.030, 0.515, 0.955) both */
            /* transform-style: preserve-3d; */
    }

    @keyframes test4animation {

        /* 0% {
            transform-origin: 100% 0;
            transform: perspective(800px) rotateY(0);
        }

        100% {
            transform-origin: 100% 0;
            transform: perspective(800px) rotateY(180deg);
        } */
        /* 0% {
            transform: perspective(800px) rotate3d(0, 1, 0, 0deg);
        }

        100% {
            transform: perspective(800px) rotate3d(0, 1, 0, 180deg);
        } */
        0% {
            transform: perspective(800px) rotateX(0);
        }

        100% {
            transform: perspective(800px) rotateX(180deg);
        }
    }

```
3. 其他3D变换
```html
    <div class="rotate">
        <div class="rotate-left">

        </div>
        <div class="test2 rotateLeft">
        </div>
    </div>
```
```css

    .test2 {
        top: 0;
        position: absolute;
        width: 200px;
        height: 200px;
        background-color: rebeccapurple;
        border-radius: 15px;
    }
    .rotate {
        position: relative;
        margin-left: 300px;
    }

    .rotate-left {
        width: 200px;
        height: 200px;
        background-color: forestgreen;
        border-radius: 15px;
    }
    .rotateLeft {
        animation: rotateLeft 2s alternate infinite;
    }

    @keyframes rotateLeft {
        0% {
            opacity: 1;
            transform-origin: 0 0;
            transform: perspective(800px) rotateY(0deg) translateZ(0px);
        }

        100% {
            opacity: 0;
            transform-origin: 50% 0;
            transform: perspective(800px) rotateY(-180deg) translateZ(300px);
        }
    }
```



3. 关于perspective

   ![图片](https://i7x7p5b7.stackpathcdn.com/codrops/wp-content/uploads/2014/12/perspective-distance.png?x67760)
   
   ```html
   
    <div class="box-container">
        <div class="box perspective">
        </div>
    </div>

    <div class="container">
        <div class="cube pers250">
            <div class="face front">1</div>
            <div class="face back">2</div>
            <div class="face right">3</div>
            <div class="face left">4</div>
            <div class="face top">5</div>
            <div class="face bottom">6</div>
        </div>
    </div>

   ```
   ```css
    html,
        body {
            padding: 0;
            margin: 0;
        }

        .box {
            width: 200px;
            height: 200px;
            overflow: hidden;
            background-color: #f34e23;
            margin: 0 auto;
            margin-top: 200px;
            display: flex;
        }

        /* 必须放父级才生效 */
        .box-container {
            perspective: 800px;
        }

        .perspective {
            transform: translateZ(300px);
            transform-style: preserve-3d;
        }

        /* Shorthand classes for different perspective values */
        .pers250 {
            perspective: 250px;
        }

        /* Define the container div, the cube div, and a generic face */
        .container {
            width: 200px;
            height: 200px;
            margin: 150px auto 0;
            border: none;
        }

        .cube {
            width: 100%;
            height: 100%;
            backface-visibility: visible;
            perspective-origin: 150% 150%;
            transform-style: preserve-3d;
        }

        .face {
            display: block;
            position: absolute;
            width: 100px;
            height: 100px;
            border: none;
            line-height: 100px;
            font-family: sans-serif;
            font-size: 60px;
            color: white;
            text-align: center;
        }

        /* Define each face based on direction */
        .front {
            background: rgba(0, 0, 0, 0.3);
            transform: translateZ(50px);
        }

        .back {
            background: rgba(0, 255, 0, 1);
            color: black;
            transform: rotateY(180deg) translateZ(50px);
        }

        .right {
            background: rgba(196, 0, 0, 0.7);
            transform: rotateY(90deg) translateZ(50px);
        }

        .left {
            background: rgba(0, 0, 196, 0.7);
            transform: rotateY(-90deg) translateZ(50px);
        }

        .top {
            background: rgba(196, 196, 0, 0.7);
            transform: rotateX(90deg) translateZ(50px);
        }

        .bottom {
            background: rgba(196, 0, 196, 0.7);
            transform: rotateX(-90deg) translateZ(50px);
        }
   ```
4. 关于translate旋转

 ![图片](https://images2015.cnblogs.com/blog/744482/201610/744482-20161019161435529-1814249230.png)

4. 旋转角度问题
```html
    <div class="rotate">
        <div class="rotate-left">
        </div>
    </div>
```
```css
        html,
        body {
            padding: 0;
            margin: 0;
        }

        .rotate-left {
            margin-top: 200px;
            margin-left: 100px;
            width: 200px;
            height: 200px;
            background-color: forestgreen;
            border-radius: 15px;
            transition: all linear 0.3s;
        }
```
```js 
        let startPosX, startPosY;
        let eleX, eleY;
        let rotateDeg = 0;
        let flag = false
        const rotate = document.querySelector('.rotate-left')
        // 获取元素点击原始坐标
        rotate.addEventListener('mousedown', (e) => {
            flag = true
            startPosX = e.pageX
            startPosY = e.pageY
        }, false)
        // 获取元素中心点坐标
        const boundClient = rotate.getBoundingClientRect()
        eleX = boundClient.width / 2 + boundClient.x
        eleY = boundClient.height / 2 + boundClient.y
        console.log(boundClient, eleX, eleY)

        rotate.addEventListener('mousemove', (e) => {
            if (flag) {
                const center2Start = calculateDistance(eleX, eleY, startPosX, startPosY)
                const center2End = calculateDistance(eleX, eleY, e.pageX, e.pageY)
                const start2end = calculateDistance(startPosX, startPosY, e.pageX, e.pageY)
                const isClockwise = calculateAngle(
                    { x: startPosX, y: startPosY },
                    { x: e.pageX, y: e.pageY }
                )
                if (isClockwise) {
                    rotateDeg += getRotate(center2End, center2Start, start2end)
                } else {
                    rotateDeg -= getRotate(center2End, center2Start, start2end)
                }
                rotate.style.transform = `rotate(${rotateDeg}deg)`;
                startPosY = e.pageY
                startPosX = e.pageX
            }
        }, false)
        rotate.addEventListener('mouseup', (e) => {
            flag = false
        }, false)
        function calculateDistance(x1, y1, x2, y2) {
            const deltaX = x2 - x1;
            const deltaY = y2 - y1;

            // 使用 Math.sqrt 函数计算平方根
            const distance = Math.sqrt(deltaX * deltaX + deltaY * deltaY);

            return distance;
        }

        function getRotate(a, b, c) {
            // 计算余弦值
            const cosTheta = (a * a + b * b - c * c) / (2 * a * b);

            // 使用反余弦函数计算角度（弧度）
            const radians = Math.acos(cosTheta);

            // 将弧度转换为度数
            const degrees = (radians * 180) / Math.PI;

            return degrees
        }
        function calculateAngle(A, B) {
            // 计算向量CA和CB
            var vectorCA = { x: A.x - eleX, y: A.y - eleY };
            var vectorCB = { x: B.x - eleX, y: B.y - eleY };

            // 计算向量叉积
            var crossProduct = vectorCA.x * vectorCB.y - vectorCA.y * vectorCB.x;

            // 如果叉积为正，夹角是逆时针形成；如果为负，夹角是顺时针形成
            if (crossProduct > 0) {
                console.log("顺时针");
                return true
            } else {
                console.log("逆时针");
                return false
            }
        }

```

4. 轮播图或pick组件的滑动（这两种滑动一般不使用自带的滑动即高度一定设置overflow：auto，而是使用transform：translate（）这种兼容性更好）

```html
    <div class="box">
        <div class="box1-left item">
        </div>
        <div class="box1-middle item">
        </div>
        <div class="box1-right item"></div>
    </div>

```
```css
        html,
        body {
            padding: 0;
            margin: 0;
        }

        .box {
            width: 200px;
            height: 200px;
            overflow: hidden;
            margin: 0 auto;
            margin-top: 200px;
            display: flex;
            user-select: none;
        }

        .box1-left {
            width: 200px;
            height: 200px;
            background-color: forestgreen;
            border-radius: 15px;
        }

        .box1-middle {
            width: 200px;
            height: 200px;
            background-color: rgb(114, 22, 83);
            border-radius: 15px;
        }

        .box1-right {
            width: 200px;
            height: 200px;
            background-color: rgb(204, 207, 24);
            border-radius: 15px;
        }

        .item {
            transition: all linear 0.4s;
            flex-shrink: 0;
        }

```
```js
        let startX = 0;
        let translateX = 0;
        let flag = false
        const box = document.querySelector('.box')
        const items = document.querySelectorAll('.item')
        const itemWidth = document.querySelector('.item').clientWidth
        document.addEventListener('mousedown', (e) => {
            flag = true
            startX = e.pageX
        }, false)
        document.addEventListener('mousemove', (e) => {
            if (flag) {
                translateX += e.pageX - startX
                console.log(translateX, itemWidth * 2)
                if (translateX <= -itemWidth * 2) {
                    translateX = -itemWidth * 2
                } else if (translateX > 0) {
                    translateX = 0
                }
                items.forEach((item) => {
                    item.style.transform = `translateX(${translateX}px)`
                })
                startX = e.pageX
            }
        }, false)
        document.addEventListener('mouseup', (e) => {
            flag = false
        }, false)

```

### 3. svg动画(https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Getting_Started)


### 4. 一些常用的动画库
1. GreenSock Animation Platform (https://greensock.com/)
2. animejs(https://animejs.com/documentation/)Anime.js是一个轻量级的JavaScript动画库，专注于Web动画的创建。它易于使用，支持各种动画类型，包括CSS属性、变换、颜色等。
3. Popmotion(https://popmotion.io/) Popmotion是一个用于创建流畅的Web动画和交互的库。它支持各种特性，包括弹簧动画、物理模拟等
4. CreateJS(https://createjs.com/) CreateJS是一组库，包括EaselJS、TweenJS、SoundJS等，专注于HTML5游戏和交互式内容的创建。EaselJS用于绘制和呈现图形，TweenJS用于动画，SoundJS用于音频处理