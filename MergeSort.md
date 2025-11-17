``` # heading 1
public class MergeSort {
    static int compares =0; // values and they have to be static to be used everywhere 
    static int swaps =0; //regular gives error says to make static

    public static void mergeSort(int[] list) {
        if (list.length > 1) {
            int[] firstHalf = new int[list.length / 2];
            System.arraycopy(list, 0, firstHalf, 0, list.length / 2);
            mergeSort(firstHalf); // sort 1st half

            int secondHalfLength = list.length - list.length / 2;
            int[] secondHalf = new int[secondHalfLength];
            System.arraycopy(list, list.length / 2, secondHalf, 0, secondHalfLength);
            mergeSort(secondHalf); //sort 2nd half

            merge(firstHalf, secondHalf, list); //merge both
        }
    }

    public static void merge(int[] list1, int[] list2, int[] temp) { //merge 2 sorted lists
        int current1 = 0; // index 1,2,temp
        int current2 = 0; 
        int current3 = 0; 

        // merge while both lists still have elements
        while (current1 < list1.length && current2 < list2.length) {
            compares++; //compare count
            if (list1[current1] <= list2[current2]) {
                temp[current3++] = list1[current1++];
                swaps++; //swaps here
            } else {
                temp[current3++] = list2[current2++];
                swaps++; //swaps here
            }
        }

        // leftover 1
        while (current1 < list1.length) {
            temp[current3++] = list1[current1++];
            swaps++; //swaps here
        }

        // leftovers from2
        while (current2 < list2.length) {
            temp[current3++] = list2[current2++];
            swaps++; //swaps here
        }
    }

    public static void main(String[] args) {
        int[] list = {19, 18, 20, 21, 2, 5, 1};
        mergeSort(list);
        for (int i = 0; i < list.length; i++) {
            System.out.print(list[i] + " ");
        }
        System.out.println("\nComparisons " + compares);
        System.out.println("Swaps " + swaps);
    }
}
```
