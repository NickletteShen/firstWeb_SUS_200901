
# 学习总结

@(Nicklette)&nbsp;&nbsp;from[面经|文章|leecode]

**最近更新**&nbsp;&nbsp;21.04.07

- **JS** - 异步.
- **CSS** - 垂直水平居中.
- **网络** - 三次握手，四次挥手；状态码.   
- **React** - 生命周期. 
- **编程** - . 

学了几年，看什么书，红宝书看到什么程度；多读纸质书？

----------

[TOC]

## JS基础
### 闭包
> Markdown is a plain text formatting syntax designed to be converted to HTML. Markdown is popularly used as format for readme files, ... or in text editors for the quick creation of rich text documents.  - [Wikipedia](http://en.wikipedia.org/wiki/Markdown)

As showed in this manual, it uses hash(#) to identify headings, emphasizes some text to be **bold** or *italic*. You can insert a [link](http://www.example.com) , or a footnote[^demo]. Serveral advanced syntax are listed below, please press `Ctrl + /` to view Markdown cheatsheet.














## CSS世界

## 浏览器/网络

## 框架React


## 编程算法题
> **字节面试** 实现斐波拉契数列1,1,1,3,5,9...，从第4个开始每个数是前三个之和
``` JavaScript
function sum(n){
	if(n==1||n==2||n==3){return 1}
	else return sum(n-1)+sum(n-2)+sum(n-3)
}
```
但是求sum(50)会运算超时，原因是递归sum(n-2)会重复计算。我的想法是将上一次的纸存起来，结果没写出来...在面试官的提醒下：
``` JavaScript
let arr=[]
function sum(n){
	if(n==1||n==2||n==3){ arr[n]=1; return 1}
	else{
            if(!arr[n]){        //递归时看当前x计算过没有,如果没有，就算前三个之和
                arr[n]=sum(n-1)+sum(n-2)+sum(n-3)
            }     //如n=50，需要sum(49)，不用重新算sum(48)+sum(47)+sum(46)，只需要取arr[49]
        return arr[n]
        }
}
console.log(sum(6))
```
**普通递归** 时复O(2^N) 空复o(n)
**记忆化递归** 时复o(n) 空复o(n)
**动态规划** 时复o(n) 空复o(1)
因为动态规划没有存所有值，只记(n-1)和(n-2)的值，然后轮流覆盖
1&nbsp;&nbsp;1&nbsp;&nbsp;1&nbsp;&nbsp;3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5&nbsp;&nbsp;9...
a&nbsp;&nbsp;b&nbsp;&nbsp;c&nbsp;&nbsp;sum
&nbsp;&nbsp;&nbsp;&nbsp;a&nbsp;&nbsp;b&nbsp;&nbsp;&nbsp;&nbsp;c&nbsp;&nbsp;sum
``` JavaScript
function sum(n){
	if(n==1||n==2||n==3){ return 1}
	else{
            let a=1
            let b=1
            let c=1
            let temp1=0
            let temp2=0
            for(let i=3;i<n;i++){
                temp1=c
                c=a+b+c
                temp2=b
                b=temp1
                a=temp2
                
            }
            return c
    }
}
```
