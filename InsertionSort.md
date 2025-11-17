``` # heading 1
public class InsertionSort {
    public static void main(String [] args){
        int[] list = {33, 22, 32, 1, 17, 19, 21}; 
        
        System.out.println("before sort"); //print before 
        for(int i = 0; i< list.length; i++){
            System.out.print(list[i] + " ");
        }
        
        insertSort(list);
        
        System.out.println("\nafter sort"); //print after
        for(int i = 0; i < list.length; i++){
        System.out.print(list[i] + " ");
        }
    }
    
public static void insertSort(int [] list){
        int compares = 0; // values to be added on
        int swaps = 0;
    
    for(int i = 1; i < list.length; i++){ // @index 1 loops through numbers
            int currentElement = list[i]; //number being inserted
            int k;
            
            for(k = i - 1; k>= 0 && list[k] > currentElement; k--){ //if # left is bigger
                list[k + 1] = list[k]; // moves it to the right 
            }
            
            list[k + 1] = currentElement; //moves number to empty spot
            swaps++; //values at end
            compares++;
        }
    System.out.println("\ncomparisons" + compares); 
    System.out.println("swaps" + swaps);
    }
}
```
