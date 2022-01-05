### Problem:

Given an array `array = [6, 2, 5, 10, 11, 1, 17, 20];`, find minimum and maximum value of the array and ouput them to screen.

### Solution

1. Set default max and min value to first element of array.
2. Loop on array, check if current element value is less than current min value, set min value to current element. And check if current element value is greater than current max value, set max value to current element.

```java
public class Main {
    public static void main(String[] args) {
        int[] array = new int[] {6, 2, 5, 10, 11, 1, 17, 20};

        // Set default min and max value is first element of array
        int min = array[0];
        int max = array[0];

        // Loop array
        for (int elm : array) {
            // if min is less than current element, assign current element to $min
            if (elm < min) {
                min = elm;
            }

            if (elm > min) {
                max = elm;
            }
        }

        // Ouput min, max on screen
        System.out.printf("Min: %d, Max: %d", min, max);
    }
}

```

