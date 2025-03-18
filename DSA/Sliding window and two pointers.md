[3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

#Slidingwindow
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