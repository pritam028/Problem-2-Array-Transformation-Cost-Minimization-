# Problem-2-Array-Transformation-Cost-Minimization-
import java.util.*;

public class Main {

   public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }
        int k = sc.nextInt();
        if (k == 0) {
            boolean same = true;
            for (int i = 1; i < n; i++) {
                if (arr[i] != arr[0]) {
                    same = false;
                    break;
                }
            }
            System.out.println(same ? 0 : -1);
            return;
        }
        int remainder = arr[0] % k;
        for (int i = 1; i < n; i++) {
            if (arr[i] % k != remainder) {
                System.out.println(-1);
                return;
            }
        }
        Arrays.sort(arr);
        int median = arr[n / 2];
        long operations = 0;
        for (int i = 0; i < n; i++) {
            operations += Math.abs(arr[i] - median) / k;
        }
       System.out.println(operations);
    }
}
