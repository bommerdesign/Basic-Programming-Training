# Hint for Algorithm Homework

## Homework 1

### Hint 1

Use quicksort to sort array and you can find the pair quickly.

---

### Hint 2

After sorted (ascending), sum of two last elements is biggest.

---

### Hint 3

Full source code.

```php
<?php
// Re-use quicksort source code
function partition(&$array, $left, $right) {
    $pivot = $array[$right];
    $i = $left -1;
    for ($j = $left; $j < $right; $j++) {
          if(($array[$j] < $pivot)){
            $i++;
            $temp = $array[$i];
            $array[$i] = $array[$j];
            $array[$j] = $temp;
          }
    }
    $temp = $array[$i + 1];
    $array[$i + 1] = $array[$right];
    $array[$right] = $temp;
    return ($i + 1);
}

function quicksort(&$array, $left, $right) {
    if($left < $right) {
        $pivotIndex = partition($array, $left, $right);
        quicksort($array,$left,$pivotIndex -1 );
        quicksort($array,$pivotIndex, $right);
    }
}

$a = [0, 2, 1, 9, 7];
$n = count($a);

// Sort array
quicksort($a, 0, $n-1);

// sum of 2 latest element
$sum = $a[$n-1] + $a[$n-2];
echo $sum;
?>
```

## Homework 2

### Hint 1

1. Find all pairs and store their sums.
2. Then sort pairs according to sum

### Hint 2

```php
<?php

$array1 = [9, 4, 2];
$array2 = [7, 11, 1, 3];
$k = 3;

// Sorting array input 1
quicksort($array1, 0, count($array1) - 1);

// Sorting array input 2
quicksort($array2, 0, count($array2) - 1);

findSmallestPair($array1, $array2, $k);

function findSmallestPair($array1, $array2, $k) {
    // Posible pairs can create is equal count($array1)*count($array2)
    if ($k > count($array1)*count($array2)) {
        echo "k pairs does not exist";
        return;        
    }

    // All indexes of array2 for every element of array1.
    // Iniitial with all values is 0.
    $index2 = array_fill(0, count($array1), 0);

    while ($k > 0) {
        // Initial min sum as maximum of integer
        $minSum = PHP_INT_MAX;
        $minIndex = 0;

        // Traverse for all elemetns in array1
        // Each elements in array1, find corresponding elements in array2
        // then store the minimun value of this pair.
        foreach ($array1 as $i => $value1) {
            // Check current index of array2 is smaller than lenght of array2
            // and sum of element in array1 with current element in array2 is
            // smaller than minSum
            if ($index2[$i] < count($array2) && ($value1 + $array2[$index2[$i]] < $minSum)) {
                // Store new minIndex
                $minIndex = $i;
                // Update minimum of sum
                $minSum = $value1 + $array2[$index2[$i]];
            }
        }
        // Print the pair
        echo "[{$array1[$minIndex]}, {$array2[$index2[$minIndex]]}] ";
        // Moving next element of array2
        $index2[$minIndex]++;

        // Decreasing k
        $k--;
    }
}

 
function partition(&$array, $left, $right) {
    $pivot = $array[($right + $left) / 2];
    $i = $left;
    $j = $right;
    while ($i <= $j) {
        while ($array[$i] < $pivot) $i++;
        while ($array[$j] > $pivot) $j--;
        
        if ($i <= $j) {
            $temp = $array[$i];
            $array[$i] = $array[$j];
            $array[$j] = $temp;
            $i++;
            $j--;
        }
    }
 
    return $i;
}
 
function quicksort(&$array, $left, $right) {
    if($left < $right) {
        $pivotIndex = partition($array, $left, $right);
        quicksort($array,$left,$pivotIndex -1 );
        quicksort($array,$pivotIndex, $right);
    }
}
```
