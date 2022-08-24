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


#八股文
