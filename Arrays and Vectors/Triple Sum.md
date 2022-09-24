## Given an array containing N integers, and an number S denoting a target sum.

## Find all distinct integers that can add up to form target sum. The numbers in each triplet should be ordered in ascending order, and triplet should be ordered too. Return empty array if no such triplet exists.

```
Input
arr = [1,2,3,4,5,6,7,8,9,15]
target=18

Output
[[1,2,15]]
[3,7,8]
[4,6,8]
[5,6,7]

```










import java.util.*;

public class MyClass {
    public static void main(String args[]) {
        
        int[] arr = {1,2,3,4,5,6,7,8,9,15};
        int k=18;
        getResult(arr, k);
    }
    
    private static void getResult(int[] arr, int k){
        
        int[] res = {0,0,0};
        for(int i=0; i<arr.length; i++){
            int diff = k - arr[i];
            
            int[] otherTwo = findPair(arr, i+1, arr.length-1, diff);
            
            if(otherTwo[0] != -1 && otherTwo[1] != -1){
                
                System.out.println("[ "+arr[i]+", "+otherTwo[0]+", "+otherTwo[1]+" ]");
            }
        }
    }
    
    private static int[] findPair(int[] arr, int p1, int p2, int target){
        
        int[] res = {-1,-1};
        for(int i=p1; i<=p2; i++){
           if(arr[p1] + arr[p2] > target){
               p2--;
           }else if(arr[p1] + arr[p2] < target){
               p1++;
           }else{
               res[0] = arr[p1];
               res[1] = arr[p2];
               return res;
           }
        }
        return res;
    }
}
