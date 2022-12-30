# dsq5import java.util.*;

public class a3q5 {

    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args)

    {

        int ch;

        do

        {

            System.out.println("\n1.Insertion Sort");

            System.out.println("\n2.Selection Sort");

            System.out.println("\n3.Bubble Sort");

            System.out.println("\n4.Quick Sort");

            System.out.println("\n5.Merge Sort");

            System.out.println("\n6.Exit");

            System.out.println("Enter Your Choice:- ");

            ch = sc.nextInt();

            

            switch(ch)

            {

                case 1:

                    String arr[] = insertarr();

                    insertion(arr);

                    System.out.println(Arrays.toString(arr));

                    break;

                   

                case 2:

                    String arr2[] = insertarr();

                    selectionsort(arr2);

                    System.out.println(Arrays.toString(arr2));

                    break;

                    

                case 3:

                    String arr3[] = insertarr();

                    bubblesort(arr3);

                    System.out.println(Arrays.toString(arr3));

                    break;

                

                case 4:

                    String arr4[] = insertarr();

                    int high = arr4.length-1;

                    quicksort(arr4, 0 , high);

                    System.out.println(Arrays.toString(arr4));

                    break;

                    

                case 5:

                    String arr5[] = insertarr();

                    String sortedarr[] = mergesort(arr5);

                    System.out.println(Arrays.toString(sortedarr));

                    break;

            }

        }while(ch!= 6);

    }

    

    static String[] insertarr()

    {

        int size;

        System.out.println("Enter The Size Of An Array");

        size = sc.nextInt();

        String arr[]=new String[size];

        System.out.println("Enter The data To Store In Array");

        for(int i = 0;i<size;i++)

        {

            arr[i] = sc.next();

        }

        return arr;

    }

    

    static void swap(String [] arr, int first,int second)

    {

        String temp = arr[first];

        arr[first] = arr[second];

        arr[second] = temp;

    }

    

    static int getmex(String [] arr,int start, int end)

    {

        int max = start;

        for(int i =0;i<=end;i++)

        { 

            if(arr[max].compareToIgnorecase(arr[i])<0)

            {

                max = i;

            }

        }

        return max;

    }

    

    static void insertion(String [] arr)

    {

        for(int i=0;i<arr.length-1;i++)

        {

            for(int j=i+1;j>0;j--)

            {

                if(arr[j].compareTo(arr[j-1])<0)

                {

                    swap(arr,j,j-1);

                }

                else

                {

                    break;

                }

            }

        }

    }

    

    static void selectionsort(String [] arr)

    {

        for(int i =0;i<arr.length;i++)

        {

            int last = arr.length-i-1;

            int max = getmex(arr,0,last);

            swap(arr,max,last);

        }

    }

    

    static void bubblesort(String[] arr)

    {

        boolean swapped;

        for(int i=0;i<arr.length;i++)

        {

            swapped = false;

            for(int j=1;j<arr.length-i;j++)

            {

                if(arr[j].compareTo(arr[j-1])<0)

                {

                    swap(arr,j,j-1);

                    swapped = true;

                }

            }

            if(!swapped) 

            {

                break;

            }

        }

    }

    

    static void quicksort(String [] arr, int low,int high)

    {

        if(low>=high)

        {

            return;

        }

        int s = low;

        int e = high;

        int m = s + (e-s)/2;

        String pivot = arr[m];

        

        while(s<=e)

        {

            while(arr[s].compareTo(pivot)<0)

            {

                s++;

            }

            while(arr[e].compareTo(pivot)>0)

            {

                e--;

            }

            if(s<=e)

            {

                swap(arr,s,e);

                s++;

                e--;

            }

        }

        

        quicksort(arr,low,e);

        quicksort(arr,s,high);

    }

    

    static int[] mergesort(String [] arr)

    {

        if(arr.length==1)

        {

            return arr;

        }

        int mid = arr.length/2;

        String [] left = mergesort(Arrays.copyOfRange(arr, 0,mid));

        String [] right = mergesort(Arrays.copyOfRange(arr, mid,arr.length));

        

        return merger(left,right);

    }

    

    private static int[] merger(String[] first,String[] second)

    {

        String [] mix = new String [first.length + second.length];

        int j=0;

        int i=0;

        int k=0;

        while(i<first.length && j < second.length)

        {

            if(first[i].compareTo(second[j])<0)

            {

                mix[k] = first[i];

                i++;

            }

            else

            {

                mix[k] = second[j];

                j++;

            }

            k++;

        }

        

        while(i<first.length)

        {

            mix[k] = first[i];

            i++;

            k++;

        }

        while(j<second.length)

        {

            mix[k] = second[j];

            j++;

            k++;

        }

        return mix;

    }

}
