# RSelect
import java.util.Scanner;

public class Main {

    public static final String ANSI_GREEN = " ";

    public static void main(String[] args) {
        int[] in = {-14, 25,15 , 0, 45, 67 ,13, -11, 12, -45, -56};
        System.out.println("Main array");
            for (int i = 0; i < in.length; i++) {
                System.out.print(in[i] + " "); }
        Scanner zxc = new Scanner(System.in);
        System.out.print(ANSI_GREEN +"\nEnter element N:");
        int n = zxc.nextInt();
            in[n - 1] = Randomselect(in, 0, 10, n - 1);
            System.out.print(n +" Element: " + in[n - 1]);
    }
    public static int SH1(int[] arr, int left, int right, int zINdex) {
        int pivotValue = arr[zINdex];
        Change(arr, zINdex, right);
        int sIndex = left;
        for (int i = left; i <= right; i++) {
            if (arr[i] < pivotValue) {
                Change(arr, sIndex, i);
                sIndex++;
            } }
        Change(arr, right, sIndex);
        return sIndex;
    }
    public static void Change(int[] arr, int leftI, int rightI) {
        int temp = arr[leftI];
        arr[leftI] = arr[rightI];
        arr[rightI] = temp;
    }public static int random(int left, int right) {
        right -= left;
        return (int) (Math.random() * ++right) + left;
    }public static int Randomselect(int[] arr, int left, int right, int k) {
        int windex = random(left, right);
        windex = SH1(arr, left, right, windex);
        if (k == windex) return arr[windex];
        else if (k > windex) return Randomselect(arr, windex + 1, right, k);
        else return Randomselect(arr, left, windex - 1, k);
    }
}
