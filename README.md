# it-interview
##为了工作面试而准备的学习仓库，内容包含学习打卡及其他内容
8/23/2022

#打卡第一天 
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


#八股文 目前暂无动力 I dont like it.

#8/25/2022 学习状态不佳，在挑选八股文内容


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

```



1.从输入url到展示页面的过程
通过DNS解析获得网址的对应IP地址 
浏览器与远程web服务器 通过TCP三次握手协商来建立一个 TCP/IP 连接 
浏览器 通过TCP/IP连接 向web服务器 发送一个 HTTP 请求 
服务器的永久重定向响应 
浏览器跟踪重定向地址 
服务器处理请求 
服务器返回一个 HTTP 响应 
浏览器渲染:解析HTML、解析CSS、解析JS、Render树

2.三次握手和四次挥手
【三次握手】
第一次握手，发送端首先发送一个带SYN（synchronize）标志的数据包给接收方，第一次的seq序列号是随机产生的，这样是为了网络安全，如果不是随机产生初始序列号，黑客将会以很容易的方式获取到你与其他主机之间的初始化序列号，并且伪造序列号进行攻击
第二次握手，接收端收到后，回传一个带有SYN/ACK（acknowledgement）标志的数据包以示传达确认信息SYN 是为了告诉发送端，发送方到接收方的通道没问题；ACK 用来验证接收方到发送方的通道没问题
第三次握手，发送端再回传一个带ACK标志的数据包，代表握手结束，若在握手某个过程中某个阶段莫名中断，TCP协议会再次以相同的顺序发送相同的数据包
【四次挥手】
客户端发送一个 FIN，用来关闭服务端到客户端的数据传送
服务端收到这个 FIN，它发回一 个 ACK，确认序号为收到的序号加1 。和 SYN 一样，一个 FIN 将占用一个序号
服务端关闭与客户端的连接，发送一个FIN给客户端
客户端发回 ACK 报文确认，并将确认序号设置为收到序号加1
