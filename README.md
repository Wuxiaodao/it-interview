# it-interview
为了工作面试而准备的学习仓库，内容包含学习打卡及其他内容
8/23/2022

#打卡第一天 
#算法
Top1两数之和
eg：nums = [2,7,11,15] target = 9 输出[0,1]
##java
```
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






#八股文
