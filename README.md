# it-interview
## 为了工作面试而准备的学习仓库，内容包含学习打卡及其他内容
8/23/2022

# 打卡第一天 
```
#算法
Top1两数之和
#eg：nums = [2,7,11,15] target = 9 输出[0,1]
##java
class Solution{
        public int[] twoSum(int[] sums,int target){
          int n = nums.length;
          for(int i=0;i<n;++i){
            for(int j=i+1;j<n;++j){
              if(nums[i]+nums[j]==target)
              return new int[]{i,j};
            }
          }
          return new int[0];
        }
}
```
24/8/2022
```
#回文数
class Solution{
        public boolean ispalindrome(int x){
                if(x<0 || x%10==0 && x!=0){    
                        return false;
                }
                int a = 0; //回文数
                while(x>a){
                        a = a * 10 + x%10;
                        x/=10;
                }
                return x == a || x == a/10;
                }
        }
```
```
#Romance to int
class Solution {
    public int romanToInt(String s) {
        s = s.replace("IV","a");
		s = s.replace("IX","b");
		s = s.replace("XL","c");
		s = s.replace("XC","d");
		s = s.replace("CD","e");
		s = s.replace("CM","f");

        int result  = 0;
		for(int i = 0;i<s.length();i++){
			result += which(s.charAt(i));
		}
		return result;
	}
	public int which(char ch){
		switch(ch){
			case 'I': return 1;
			case 'V': return 5;
			case 'X': return 10;
			case 'L': return 50;
			case 'C': return 100;
			case 'D': return 500;
			case 'M': return 1000;
			case 'a': return 4;
			case 'b': return 9;
			case 'c': return 40;
			case 'd': return 90;
			case 'e': return 400;
			case 'f': return 900;
		}
		return 0;
    }
}

```


# 八股文 目前暂无动力 I dont like it.

# 8/25/2022 学习状态不佳，在挑选八股文内容


```
#最长公共前缀
class Solution{
	public String longestCommonPrefix(String[] strs){
		if(strs.length == 0)
			return "";
			String ans = strs[0];
			for(int i = 1;i<strs.length;i++){
				int j = 0;
				for(;j<ans.length() && j < strs[i].length();j++){
                    if(ans.charAt(j) != strs[i].charAt(j))
					break;
				}
				ans = ans.substring(0,j);
				if(ans.equals(""))
					return ans;
			}
			return ans;
	}
}

```

```
#8/30/2022
#给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。
class Solution {
    public boolean isValid(String s) {
        int length = s.length() / 2;
		for (int i = 0; i < length; i++) {
			s = s.replace("()", "").replace("{}", "").replace("[]", "");
		}

		return s.length() == 0;
    }
}

#合并两个有序列表，并按升序排列
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if(list1 == null){
            return list2;
        }
        if(list2 == null){
            return list1;
        }
        if(list1.val < list2.val){
            list1.next = mergeTwoLists(list1.next,list2);
            return list1;
        }else{
            list2.next = mergeTwoLists(list1,list2.next);
            return list2;
        }
    }
}
```



# 1.从输入url到展示页面的过程
通过DNS解析获得网址的对应IP地址 
浏览器与远程web服务器 通过TCP三次握手协商来建立一个 TCP/IP 连接 
浏览器 通过TCP/IP连接 向web服务器 发送一个 HTTP 请求 
服务器的永久重定向响应 
浏览器跟踪重定向地址 
服务器处理请求 
服务器返回一个 HTTP 响应 
浏览器渲染:解析HTML、解析CSS、解析JS、Render树

# 2.三次握手和四次挥手
## 【三次握手】
第一次握手，发送端首先发送一个带SYN（synchronize）标志的数据包给接收方，第一次的seq序列号是随机产生的，这样是为了网络安全，如果不是随机产生初始序列号，黑客将会以很容易的方式获取到你与其他主机之间的初始化序列号，并且伪造序列号进行攻击  
第二次握手，接收端收到后，回传一个带有SYN/ACK（acknowledgement）标志的数据包以示传达确认信息SYN 是为了告诉发送端，发送方到接收方的通道没问题；ACK 用来验证接收方到发送方的通道没问题  
第三次握手，发送端再回传一个带ACK标志的数据包，代表握手结束，若在握手某个过程中某个阶段莫名中断，TCP协议会再次以相同的顺序发送相同的数据包
## 【四次挥手】
客户端发送一个 FIN，用来关闭服务端到客户端的数据传送  
服务端收到这个 FIN，它发回一 个 ACK，确认序号为收到的序号加1 。和 SYN 一样，一个 FIN 将占用一个序号  
服务端关闭与客户端的连接，发送一个FIN给客户端  
客户端发回 ACK 报文确认，并将确认序号设置为收到序号加1

# HTTP和HTTPS
## HTTP:
不安全；协议对客户端没有状态存储；每次请求需要TCP三次握手四次挥手，和服务器重新建立连接；
基本的特性，由客户端发起请求，服务端响应；简单快速、灵活；使用明文、请求和响应不进行确认

## HTTPS
安全；HTTP安全版本，通过SSL或TSL提供加密处理数据、验证对方身份以及数据完整性保护；
采用混合加密技术，传输过程无法直接查看明文内容；通过证书认证客户端访问的是自己的服务器；
传输过程防止被篡改。

# 跨域的解决方案
JSONP、PostMessage、document.domain、Websocket、CORS、Nginx反向代理、Node中间件代理

# 01服务器返回code的意义
100 继续请求  
101 切换协议  
200 请求成功  
201 创建成功  
202 接受请求  
203 非授权信息  
204 没有内容  
205 内容重置  
206 部分内容  
300 多种选择  
301 永久移动  
302 临时移动  
303 访问其他位置  
304 未修改  
305 使用代理  
307 临时重定向  
400 请求错误  
401 未授权  
403 拒绝请求  
404 未找到  
405 方法禁用  
406 无法请求  
407 缺少代理权  
408 请求超时  
409 存在冲突  
410 已删除  
411 标头字段无效  
412 条件未满足  
413 请求体超标  
414 URI超标  
416 不存在请求范围  
417 请求头未满足条件  
500 服务器内部错误  
501 未完成请求  
502 网关错误  
503 服务器不可使用  
504 网关超时  
505 HTTP协议不支持  

# 9/6/2022
## HTML
### 1.语义化标签有哪些
header    头部  
nav       导航栏   
section   区块  
main      主要区域   
article   主要内容  
aside     侧边栏  
footer    底部 

### 2.简单说一下拖曳过程  
dragstart  // 拖放事件，开始拖放时触发。  

darg       // 拖放事件，正在拖放触发。  

dragenter  // 目标事件，拖放进入目标时触发。  

dragover   // 目标事件，拖放目标内移动时触发。  

dragleave  // 目标事件，拖放移出目标时触发。  

drop       // 目标事件，目标接受被拖放时触发。  

dragend    // 拖放事件，拖放操作结束时触发。

### 3.严格模式与混杂模式
严格模式： 浏览器支持的最高标准运行  
混杂模式： 向下兼容的方式显示，模拟低版本浏览器的行为

### 4.iframe的优缺点有哪些
优点：  
iframe能够原封不动地把嵌入的网页展示出来；  
提高页面代码的复用性；  
解决加载缓慢的第三方内容，如图标和广告等的加载问题；  
在处理上传或局部刷新时，避免了页面整体刷新；  
iframe解决部分跨域问题；

缺点：  
iframe会阻塞主页面的 onload 事件；  
无法被一些搜索引擎索引到；  
页面会增加服务器的http请求；  
会产生很多页面，不便于管理；  
很多移动设备无法完全显示框架，设备兼容性差；  
会出现区域的上下、左右滚动条，滚动条会挤占页面空间；  
使用框架时，要保证正确的使用导航链接，容易造成链接死循环；


## CSS
### 1.盒模型
盒模型构成：content + padding + border + margin  
W3C标准盒模型：width表示content（主内容）的宽度  
IE盒子模型：width表示content（主内容）+padding（内边距）+border（边框）这三个部分的宽度

切换盒模型：
box-sizing:content-box  //W3C盒子模型
box-sizing:border-box  //IE盒子模型

### 3.伪类和伪元素
常用的伪类：
```
a:link      // 未访问
a:hover     //  悬停
a:visited   // 已访问
a:active    // 已选择
```

常用的伪元素：
```
span::before {  // 内容前面插入新内容
    content:'';
}
span::after{  // 内容之后插入新内容
    content:'';
}
```

### 4.居中div的方案
水平垂直居中：
```
div{
    position:absolute;
    left:50%;
    top:50%;
    transform:translate(-50%,-50%);
}
```
### 5.绝对定位和相对定位
position属性的绝对定位：absolute和fixed统称为绝对定位  
position属性的相对定位:relative  

### 6.CSS3特性
border-radius  //圆角  
text-shadow    //文字阴影  
transition     //动画过渡  
animation      //动画  
box-shadow     //盒子阴影  
border-image   //图片边框  
background-clip//背景绘制  
color:rgba(0,0,0,0.1)  //透明度设置  
flex           //布局  

### 7.清除浮动的方法
```
<div style="clear:both" />
<br clear:"all"/>
//父元素使用overflow:hidden、auto
//使用伪元素清除浮动
```

### 8.CSS优化
尽量避免使用@import  
多个图片背景尽量使用精灵图  
减少重绘和重排的属性使用（如color，background，visibility等属性）  
有重复命名时，选择器添加父节点方便快捷查找

# 9/7/2022
## JavaScript
### 1.数据类型
基础数据类型：Undefined、Null、Boolean、Number、String、Symbol【ES6】、Bigint【ES10】  
复杂数据类型(三大引用类型)：Object、Array、Function【Array和Function都属于Object类型】
```
var obj = new Object()
obj.name = 'zhangsan';

var arr = new Array();
ar.push(1);

var func = function(){
	return 1;
}

console.log(obj,arr,func);  //{name:'zhangsan'},{1},1
```

### 2.数据类型转换
可以相互转换的类型：Number、String、Boolean


### 3.原型和原型链
定义一个函数数据类型（普通函数、类）时候，都会自带一个prototype属性，这个属性指向函数的原型对象，并且这个属性是一个对象数据类型的值  
对象属性也自带一个属性_proto_，属性值是当前实例所属类的原型（prototype）。原型对象中有一个属性constructor，它指向函数对象  
原型链指的是通过prototype对象指向父类对象最后指向Object对象的过程【Object最后为null】

### 4.作用域和作用域链
作用域就是代码的执行环境，全局执行环境就是全局作用域，函数的执行环境就是私有作用域，它们都是栈内存  
当代码在一个环境中执行时，会创建变量对象的一个作用域链（作用域形成的链条)  
内部环境可以通过作用域链访问所有外部环境，但外部环境不能访问内部环境的任何变量和函数  
当在内部函数中，需要访问一个变量的时候，首先会访问函数本身的变量对象，是否有这个变量，如果没有，那么会继续沿作用域链往上查找，直到全局作用域。

### 5.深拷贝和浅拷贝的方法
浅拷贝就是可以将对象的基础类型复制，无法复制复杂数据类型  
深拷贝就是为了解决无法复制数据类型，对数据进行深程度拷贝
【浅拷贝】1.Object.assign 2.扩展运算符(...) 3.for...in

【深拷贝】1.JSON对象来实现深拷贝【缺点：函数无法拷贝，会显示undefined】 
2.lodash函数库实现深拷贝【需要引入lodash库】 3.递归

### 6.闭包
在javascript中，只有函数内部的子函数才能读取局部变量，所以闭包可以理解成“定义在一个函数内部的函数”  
在本质上，闭包是将函数内部和函数外部连接起来的桥梁

### 7.常用的创建对象的几种方式
工厂模式、构造函数模式、原型模式  
通过Object构造函数或对象字面量创造单个对象  
组合使用构造函数模式和原型模式  
动态原型模式  
寄生构造函数模式  
稳妥构造函数模式

### 8.继承的几种实现方法
构造继承、原型链继承、拷贝继承、实例继承、组合继承、寄生组合继承

### 9.this：call、apply、bind
this的指向受函数运行环境的影响（默认指向window）  
call方法可以修改this的指向（指向函数指向时所在的作用域），然后再执行函数
```
// function.prototype.call();

   function f(x, y){
     console.log(x + y);
   }

   f.call(null, 1, 1) // 2
   ```
   
  apply和call作用类似，唯一区别是apply接受组作为函数执行时的参数
  ```
  // function.prototype.apply();

function f(x, y){
  console.log(x + y);
}

f.apply(null, [1, 1]) // 2
  ```
 bind用于将函数体内的this绑定到某个对象，然后返回一个新函数
 ```
 // function.prototype.bind();

const add = function (x, y) {
    console.log(x, y);
    return x * this.a + y * this.b;
}

const newAdd = add.bind({a: 2, b: 3}, 5);  // 第二个参数为x值
newAdd(5) // 输入参数为y值  结果: 25

 ```

### 10.事件捕获和事件冒泡 
捕获型事件：事件从document对象开始触发，然后到目标事件  
冒泡型事件：目标事件到document对象的顺序触发

### 11.DOM操作
获取DOM
DOM事件

onclick--------点击事件  
onload---------进入时执行事件  
onunload-------离开时执行事件  
onmouseover----鼠标指针移入时执行事件  
onmouseout-----鼠标指针移出时执行事件  
onmousedown----鼠标摁下时执行事件  
onmouseup------鼠标松开时执行事件  

### 12.AJAX
AJAX是异步 JavaScript 和 XML。    
AJAX可以通过在后台与服务器进行少量数据交换,实现异步更新。  
AJAX的XmlHttpRequest使您可以使用JavaScript向服务器提出请求并处理响应，而不阻塞用户。  
AJAX通过XMLHttpRequest对象，Web开发人员可以在页面加载以后进行页面的局部更新。  
AJAX常用的方法：（新增）post,（获取）get,（删除）delete, （修改）put  
原生AJAX请求
```
//创建 XMLHttpRequest 对象
var ajax = new XMLHttpRequest();
//规定请求的类型、URL 以及是否异步处理请求。
ajax.open('GET',url,true);
//发送信息至服务器时内容编码类型
ajax.setRequestHeader("Content-type", "application/x-www-form-urlencoded"); 
//发送请求
ajax.send(null);  
//接受服务器响应数据
ajax.onreadystatechange = function () {};
```

## Git操作代码
git status                // 查看本地文件修改的状态  
git diff                  // 查看具体变更内容  
git add .                 // 将所有改动文件添加到暂存区  
git add 'file'            // 添加指定文件到暂存区  
git commit -m 'message'   // 本次提交的说明  
git pull                  // 拉取远程分支代码至本地分支  
git push                  // 当前代码合并至远程仓库  
