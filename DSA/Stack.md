[Implement stack using array](https://www.geeksforgeeks.org/problems/implement-stack-using-array/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=implement-stack-using-array)

```java
class MyStack {
    private int[] arr;
    private int top;

    public MyStack() {
        arr = new int[1000];
        top = -1;
    }

    public void push(int x) {
        if(top==arr.length-1){
        System.out.print("stack overflow");
        return;}
        top++;
        arr[top]=x;
    }

    public int pop() {
        if(top==-1) return -1;
        return arr[top--];
    }
}
```


[394. Decode String](https://leetcode.com/problems/decode-string/)

```java
class Solution {
    public String decodeString(String s) {
        Stack<Integer> numst=new Stack<>();
        Stack<StringBuilder> strst=new Stack<>();
        int n=0;
        StringBuilder ans =new StringBuilder();
        for(char c:s.toCharArray()){
            if(Character.isDigit(c)){
                n=(n*10)+(c-'0');
            }
            else if(c=='['){
                numst.push(n);
                n=0;
                strst.push(ans);
                ans=new StringBuilder();
            }else if(c==']'){
               String str=ans.toString();
               ans=new StringBuilder(str.repeat((numst.pop())));
               ans=strst.pop().append(ans);
            }
            else{
                ans.append(c);
            }
        }
        return ans.toString();
    }
}
```



