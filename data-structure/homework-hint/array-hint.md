# Hint for Array Homework

## Homework 1.

### Hint 1

Define variable to store sum, average, min, max (`$sum, $avg, $min, $max`).
Assign `$min and $max = first element`.

Loop though each elment in array, and calucate sum, average, min, max.
- Calulate sum: Add value of element to `$sum`
- Average: Average is calculated by `$sum/count(array)` 
- Min: check if `$min` is greater than current element, assign `$min = current element`
- Max: check if `$max` is less than current element, assign `$max = current element`

-----

### Hint 2

Following pseudocode 

```pre
min, max = a[0]
sum = 0
agv = 0

n = size_of(a)
for i from 0 to n-1:
    sum += a[i]
agv = sum/n
```

------

### Hint 3

Please check the source code

```php
<?php
$a = [5, 12, 17, 9, 3];
$min = $a[0];
$max = $a[0];
$sum = 0;
$avg = 0;
$n = count($a);

for ($i = 0; $i < $n; $i++) {
    // add element so tum
    $sum += $a[$i];

    // check min element
    if ($min > $a[$i]) {
        $min = $a[$i];
    }

    // check max element
    if ($max < $a[$i]) {
        $max = $a[$i];
    }
}

$avg = $sum/$n;
?>
```

## Homework 2

### Hint 1

Because number of elments in 2 array are same, so that use only one `for` to loop though 2 array.

------------

### Hint 2 

Define an array C, and assign C[i] = A[i] + B[i]

-------------

### Hint 3

Full source code for homework

```php
<?php
$a = [1, 2, 3, 4, 5];
$b = [4, 5, 3, 2, 10];
$c = [];

// because $a and $a have same number of element, use one varibale to store it
$count = count($a);

for ($i = 0; $i < $count; $i++) {
    $c[$i] = $a[$i] + $b[$i];
}

// output $c to screen
print_r($c);
?>
```

## Homework 3

### Hint 1

It's almost same with Homework 2, but it is 2-dementional array. So that we have to loop each row of array, then loop through each element in each row. And calculate min, max, sum, average same with Homework 1.

----

### Hint 2

1. Define `$min, $max, $sum, $avg` same with Homework 1.
2. Loop through the array : `foreach ($a as $row)`
3. Loop through the row: `foreach ($row as $elm)`.
4. Calculate `$min, $max, $sum, $avg` same with homework 1.

----

### Hint 3

Full source code

```php
<?php
// Define 2-dimentional array
$a = [[5, 12, 17, 9, 13], [13, 4, 8, 14, 1], [9, 5, 3, 17, 21]];
// Define $min, $max is first element of the array
$min = $a[0][0];
$max = $a[0][0];
$sum = 0;
$avg = 0;
$n = count($a);

// Loop through 2-dimention array
foreach ($a as $row) {
    // Loop through each row
    foreach ($row as $elm) {
        // add element so tum
        $sum += $elm;

        // check min element
        if ($min > $elm) {
            $min = $elm;
        }

        // check max element
        if ($max < $elm) {
            $max = $elm;
        }
    }
}

$avg = $sum/$n;
?>

