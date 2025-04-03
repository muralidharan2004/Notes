
1.Sum of first n natural numbers

```java
import java.util.Scanner;
public class recursion {
    public static int natural(int i,int sum){
        if(i<1) {
            return sum;
        }
        return natural(i-1,sum+i);
               
    }
    public static void main(String[] args) {
        Scanner scan=new Scanner(System.in);
        int n=scan.nextInt();       
        scan.close();
        int sum=0;
        System.out.println(natural(n,sum));
    }
}

```
