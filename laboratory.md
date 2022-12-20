---
layout: page
title: Laboratory
permalink: /laboratory/
---
## 实验室
<p>
<script>
"use strict"
  document.write("浏览器支持并已启用 JavaScript。<br/>UserAgent: <code>"+navigator.userAgent+"</code>");
</script>
<noscript>
浏览器不支持或未启用 JavaScript
</noscript>
</p>
<script>
"use strict"
function sqrt()
{
    let begin,end;
    
    begin=new Date();
    let r;
    for(r=0.0;r<=1;r+=0.000000005)
    {
        Math.sqrt(r);
    }
    end=new Date();
    document.getElementById("sqrt-result").innerHTML=end.getTime()-begin.getTime()+"ms. 耗时越低越好";
}
</script>

<script>
"use strict"
let n,m,ans=0,x=[],rlock=[],slock=[],slockr=[];
function init()
{
    let timeBegin=new Date();
    
    n=13;
    m=n-1;

    for(let i=0;i<n;i++)
    {
        dfs(0,i);
    }
    
    let timeEnd=new Date();
    let timeTotal=timeEnd.getTime()-timeBegin.getTime();
    document.getElementById("nq-result").innerHTML=timeTotal+"ms. 耗时越低越好";
}

function dfs(line,row)
{
    if(rlock[row]===true || slock[line+row]===true || slockr[line-row+m]===true)
    return;

    x[line]=row;
    
    rlock[row]=true;
    slock[line+row]=true;
    slockr[line-row+m]=true;

    for(let i=0;i<n;i++)
    {
        dfs(line+1,i);
    }
    
    rlock[row]=false;
    slock[line+row]=false;
    slockr[line-row+m]=false;
}
</script>

<script>
"use strict"
  document.write('<h3>基准测试</h3><p>这只是个玩具。</p><h4>N皇后问题</h4><p>n=13，使用朴素的深度优先搜索算法。</p><button onclick="setTimeout(init,200)">开始测试</button><p id="nq-result">-----</p><h4>平方根求解</h4><button onclick="setTimeout(sqrt,200)">开始测试</button><p id="sqrt-result">-----</p>');
</script>

### 伏安特性曲线

学校实验室搬走了，想画电源伏安特性曲线怎么办？

[造个虚拟的出来。]({{site.url}}/res/c-v-characteristic/c-v-characteristic.html)

### 康威生命游戏

大一上学期结课，在C语言的课设上就用 ncurses 搓了个康威生命游戏，结果发现其他同学都在搞大工程，做围棋游戏、用 Qt 写图形程序、用 Unity 做 3D 游戏的都有，对我这种七百行代码、git 都没必要用的玩具简直就是降维打击。根本卷不过啊！

砹，砹，砹；砹，砹，砹。

课设的作品一点技术含量都没有，拿来水博客太尴尬，不如用 emscripten 编译成[网页]({{site.url}}/res/conway/conway.html)扔博客上。

构建时用了 [emcurses](https://github.com/rhaberkorn/emcurses) 库，同时用了 emcurses 演示文件里原装的 HTML。
