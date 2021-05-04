# Sort-Algorithm

Bubble Sort
============

* 코드
```java
public class BubbleSort {
    static void bubbleSort(int[] arr) {
        int n = arr.length;
        int temp = 0;
        for(int i=0; i < n; i++){
            for(int j=1; j < (n-i); j++){
                if(arr[j-1] > arr[j]){
                    temp = arr[j-1];
                    arr[j-1] = arr[j];
                    arr[j] = temp;
                }

            }
        }

    }
    public static void main(String[] args) {
        int arr[] ={5,7,10,4,1,15,17,13};

        System.out.println("정렬 전");
        for(int i=0; i < arr.length; i++){
            System.out.print(arr[i] + " ");
        }
        System.out.println();

        bubbleSort(arr);

        System.out.println("정렬 후");
        for(int i=0; i < arr.length; i++){
            System.out.print(arr[i] + " ");
        }

    }
}
```
* 결과

![image](https://user-images.githubusercontent.com/80373177/116963919-1f723a00-ace5-11eb-9bc0-baaac9bbc601.png)

* 성능 분석

N개의 원소를 비교하는 시간은 (n-1) + (n-2) + ~ + 2 + 1 = n(n-1)/2 이다. 따라서 BubbleSort 알고리즘의 시간복잡도는  O(n^2) 이다.


Selection Sort 
===============

* 코드
```java
public class SelectionSort {
    public static void main(String[] args) {
        int[] a = {13, 8, 4, 26, 14, 51, 1, 81, 9, 29};
        int i,p,temp;
        for(i=0;i<10;i++)
        {
            p = minimum(a, 10, i);
            temp = a[i];
            a[i]=a[p];
            a[p] = temp;
        }
        System.out.print("\n선택 정렬 후\n");
        for(i=0;i<10;i++)
        {
            System.out.println(a[i]);
        }
    }
    public static int minimum(int a[], int n, int i)
    {
        int min,p,j;
        min = a[i];
        p = i;
        for(j=i+1;j<10;j++)
        {
            if(a[j]<min)
            {
                min = a[j];
                p=j;
            }
        }
        return p;
    }
}
```
* 결과

![image](https://user-images.githubusercontent.com/80373177/116966651-9f9b9e00-aceb-11eb-8f91-0ec8cbfc5cdc.png)

* 성능 분석

N개의 원소를 비교하는 총 횟수는 (n-1) + (n-2) + ~ + 2 + 1 = n(n-1)/2 이다. 따라서 시간복잡도는 마찬가지로 O(n^2) 이다.


Insertion Sort
===============

* 코드
```java
public class InsertionSort {
    public static void insertion(int a[]) {
        int n = a.length;
        for (int j = 1; j < n; j++) {
            int key = a[j];
            int i = j-1;
            while ( (i > -1) && ( a [i] > key ) ) {
                a [i+1] = a [i];
                i--;
            }
            a[i+1] = key;
        }
    }

    public static void main(String[] args){
        int[] a = {40,60,70,50,15,29,31,24};
        System.out.println("삽입 정렬 전");
        for(int m :a) {
            System.out.print(m+" ");
        }
        System.out.println();

        insertion(a);

        System.out.println("삽입 정렬 후");
        for(int i:a){
            System.out.print(i+" ");
        }
    }
}
```
* 결과

![image](https://user-images.githubusercontent.com/80373177/116969338-125b4800-acf1-11eb-9932-3804b556a7af.png)

* 성능 분석

N개의 원소인 배열을 정렬할 때 비교에 걸리는 수행 시간을 T'(n)이라고 한다. 내부 반복문에서 비교에 걸리는 시간을 S(n)이라고 하면 S(n) = n-1이다.
T'(n) = S(2) + S(3) + … + S(n) = 1 + 2 + 3 + … +(n-1) 이고, 따라서 삽입 정렬의 비교에 걸리는 시간은 O(n^2)이다.


Shell Sort
===========

* 코드
```java
import java.util.*;
public class ShellSort {
    static void shell(int[] arr, int num)
    {
        int i, j, k, tmp;
        for (i = num / 2; i> 0; i = i / 2)
        {
            for (j = i; j<num; j++)
            {
                for(k = j - i; k>= 0; k = k - i)
                {
                    if (arr[k+i] >= arr[k])
                        break;
                    else
                    {
                        tmp = arr[k];
                        arr[k] = arr[k+i];
                        arr[k+i] = tmp;
                    }
                }
            }
        }
    }
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        int arr[]= new int[30];
        int k,  num;
        System.out.print("원소의 개수 : ");
        num = sc.nextInt();
        System.out.print("배열 입력 : ");
        for (k =  0 ; k<num; k++)
        {
            arr[k]=sc.nextInt();
        }
        shell(arr, num);
        System.out.println("정렬된 배열 : ");
        for (k = 0; k<num; k++)
            System.out.println(arr[k]);
    }
}
```
* 결과

![image](https://user-images.githubusercontent.com/80373177/116971785-096c7580-acf5-11eb-96d5-9ccd9b4d4ef6.png)

* 성능 분석

Shell Sort의 시간복잡도는 최선인 경우엔 O(nlogn)가 나오고, 평균은 O(n^1.5), 최악의 경우엔 O(n^2)이 나오기 때문에 전체 시간복잡도는 최악의 경우를 반영하여 O(n^2)이다.



