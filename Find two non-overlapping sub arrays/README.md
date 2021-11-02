
Given an array of integers arr and an integer target.

You have to find two non-overlapping sub-arrays of arr each with a sum equal target. There can be multiple answers so you have to find an answer where the sum of the lengths of the two sub-arrays is minimum.

Return the minimum sum of the lengths of the two required sub-arrays, or return -1 if you cannot find such two sub-arrays.

 

**Example 1:**

Input: arr = [3,2,2,4,3], target = 3
Output: 2
Explanation: Only two sub-arrays have sum = 3 ([3] and [3]). The sum of their lengths is 2.


**solution:**

class Solution

{

public:

    int minSumOfLengths(vector<int>& arr, int target) 
    
    {
       
    int start=0;
    
    int len=INT_MAX;
   
    int n=arr.size();
   
    int sum=0;
    
    int res=INT_MAX;
   
    vector<int> dp(n,INT_MAX);
   
    for(int end=0;end<n;end++)
                               
    {
                               
        sum+=arr[end];
                               
       
        while(sum>target)
  
        {
            sum-=arr[start];
  
            start++;
  
        }
       
        if(sum==target)
  
        {
            int curlen=end-start+1;
  
           
            if(start>0  &&   dp[start-1]!=INT_MAX)
  
            {
  
                res=min(curlen+dp[start-1],res);
  
            }
           
            len=min(curlen,len);
        }
       
        dp[end]=len;
       
    }
   
    if(res==INT_MAX)
  
        return -1;
   
   
    return res;
   
}
  
};
