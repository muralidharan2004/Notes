
[3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Set<Character> freq= new HashSet<>();
        int end=0,start=0,maxlen=0;
        while(end<s.length()){
            while(freq.contains(s.charAt(end))){
                freq.remove(s.charAt(start));
                start++;
            }
            freq.add(s.charAt(end));
            
            maxlen=Math.max(maxlen,end-start+1);
            end++;
        }
        return maxlen;
    }
}
```


[1004. Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)

```java
class Solution {
    public int longestOnes(int[] nums, int k) {
        int start=0,maxcount=0,zerocount=0;
        for(int end=0;end<nums.length;end++){
            if(nums[end]==0)
            zerocount++;
            while(zerocount>k){
                if(nums[start]==0)
                zerocount--;
                start++;
            }
            maxcount=Math.max(maxcount,end-start+1);
        }
        return maxcount;
    }
}
```


[Find length of the longest subarray containing at most two distinct integers](https://www.geeksforgeeks.org/problems/fruit-into-baskets-1663137462/1)

```java
lass Solution {
    public static int totalElements(Integer[] arr) {
        int l=0,r=0,len=0,count=0,maxlen=0;
        Map<Integer,Integer> freq=new HashMap<>();
        while(r<arr.length){
            freq.put(arr[r],freq.getOrDefault(arr[r],0)+1);
            while(freq.size()>2){
                freq.put(arr[l],freq.get(arr[l])-1);
                if(freq.get(arr[l])==0){
                    freq.remove(arr[l]);
                }
                l++;
            }
             maxlen=Math.max(maxlen,r-l+1);
            r++;
        }
            
           
        
        return maxlen;
    }
}
```


[424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

```java
class Solution {
    public int characterReplacement(String s, int k) {
          int l=0,r=0,maxlen=0,maxfreq=0;
          int[] hash=new int[26];
          while(r<s.length()){
            hash[s.charAt(r)-'A']++;
            maxfreq=Math.max(maxfreq,hash[s.charAt(r)-'A']);
            if((r-l+1)-maxfreq<=k){
                maxlen=Math.max(maxlen,r-l+1);
                r++;
            }else{
                hash[s.charAt(l)-'A']--;
                l++;
                r++;
            }
          }
          return maxlen;
    }
}
```


[930. Binary Subarrays With Sum](https://leetcode.com/problems/binary-subarrays-with-sum/)

```java
class Solution {
    public int numSubarraysWithSum(int[] nums, int goal) {
        int l=0,r=0,count=0,prefixsum=0;
        Map<Integer,Integer> prefixmap=new HashMap<>();
        prefixmap.put(0,1);
        for(int num:nums){
            prefixsum+=num;
            if(prefixmap.containsKey(prefixsum-goal)){
                count+=prefixmap.get(prefixsum-goal);
            }
            prefixmap.put(prefixsum,prefixmap.getOrDefault(prefixsum,0)+1);
        }
        return count;
    }
}
```


[1248. Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)

```java
class Solution {
    public int numberOfSubarrays(int[] nums, int k) {
        for(int i=0;i<nums.length;i++){
            if(nums[i]%2==0) nums[i]=0;
            else nums[i]=1;
        }
        int prefixsum=0,count=0;
        Map<Integer,Integer> prefixmap=new HashMap<>();
        prefixmap.put(0,1);
        for(int num:nums){
            prefixsum+=num;
            if(prefixmap.containsKey(prefixsum-k))
            count+=prefixmap.get(prefixsum-k);
            prefixmap.put(prefixsum,prefixmap.getOrDefault(prefixsum,0)+1);
        }
        return count;
    }
}
```


[1358. Number of Substrings Containing All Three Characters](https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/)

```java
class Solution {
    public int numberOfSubstrings(String s) {
        int[] hash=new int[3];
        Arrays.fill(hash,-1);
        int count=0;
        for(int i=0;i<s.length();i++){
            hash[s.charAt(i)-'a']=i;
            if(hash[0]!=-1&&hash[1]!=-1&&hash[2]!=-1){
                count+=(1+Math.min(hash[0],Math.min(hash[1],hash[2])));
            }
        }return count;
    }
}
```


[1423. Maximum Points You Can Obtain from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)

```java
class Solution {
    public int maxScore(int[] cardPoints, int k) {
        int rsum=0,lsum=0;
        for(int i=0;i<k;i++){
            lsum+=cardPoints[i];
        }
       int  n=cardPoints.length-1;
        int maxsum=lsum;
        for(int i=k-1;i>=0;i--){
            lsum-=cardPoints[i];
            rsum+=cardPoints[n];
            n--;
            maxsum=Math.max(maxsum,lsum+rsum);
        }
        return maxsum;
    }
}
```


[992. Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/)

```java
class Solution {
    public int validSubArray(int [] nums,int k){
        int l=0,r=0,count=0;
        Map<Integer,Integer> map=new HashMap<>();
        while(r<nums.length){
            map.put(nums[r],map.getOrDefault(nums[r],0)+1);
            while(map.size()>k){
                map.put(nums[l],map.get(nums[l])-1);
                if(map.get(nums[l])==0){
                map.remove(nums[l]);
                }
                l++;
            }
            
            count+=(r-l+1);
            r++;
        }
        return count;
    }
    public int subarraysWithKDistinct(int[] nums, int k) {
        return validSubArray(nums,k)-validSubArray(nums,k-1);
    }
}
```