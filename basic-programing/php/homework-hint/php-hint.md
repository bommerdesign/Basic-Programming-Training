# Suggestion For PHP Homework

## Homework 1

### Hint 1

Use a variable like `$sum` to store sum of the odd numbers value. Use `for` to loop from 1 to 50, check if element is odd, add the element to `$sum`

----------

### Hint 2

Use operator `%` to check if the number is odd. Odd numbers that the numbers divided by 2, leave a remainder of 1. ($x%$y: Remainder of $x divided by $y)

---------

### Hint 3

Following below step:

1. Define a variable `$sum` to store sum of odd numbers value.
2. Use `for` to loop from 1 to 50: `for($i = 0; $i < 50; $i++)`
3. Inside of `for`, check the number is odd, add the number to the sum `$sum`: `if ($i%2 === 1) {$sum += $i}`
4. After the loop ended, output sum value to screen: `echo $sum`

Complete source code:

```php
<?php
$sum = 0;
for ($i = 0; $i < 50; $i++) {
    if ($i%2 === 1) {
        $sum += $i;
    }
}

echo $sum;
?>
```

## Homework 2

### Hint 1

1. Define a variable `$result=1` (because fatorial of 0 is 1), 
2. Define a varibale `$i`, increse `$i` from 2 to `n`.
3. Multiply `$result` with `$i`

------

### Hint 2

Please follow pseudocode to implment function `factorialOfNumber` in the homework.

```pre
result = 1

for i from 2 to n:
    result = result * i

print result
```

-------

### Hint 3

This is full source code for the homework

```php
<?php
function factorialOfNumber($n)
{
    $result = 1;
    for ($i = 2; $i <= $n; $i++) {
        $result *= $i;
    }
    return $result;
}

echo factorialOfNumber(10);
?>
```

## Homework 3

### Hint 1

1. Zero and 1 are not considered prime numbers. 
2. The only even prime number is 2. All other even numbers can be divided by 2.
3. Check if the number can devided by any number from 2 to `number/2`, it is not prime number.

----

### Hint 2

1. Check if a number is 0 or 1, return false, because they are not prime number.
2. Check if a number is 2, return true, because 2 is a prime number.
3. Loop `$i` from 2 to `n/2`, check if `$n` can be devided by `$i`, return `false`.
4. After break the loop at step 2, return `true`

-----

### Hint 3

Full solution and example

```php
<?php
function isPrimeNumber($n) {
    // Because 0 and 1 are not prime numbers
    if ($n == 0 || $n == 1) {
        return false;
    }

    // 2 is a prime number
    if ($n == 2) {
        return true;
    }

    $m = $n/2;
    for ($i = 2; $i <= $m; $i++) {
        // if can devided by another number (not 1 and itself), not prime number
        if ($n%$i == 0) {
            return false;
        }
    }

    return true;
}

// Try to check a number is prime number or not
if (isPrimeNumber(7)) {
    echo "7 is prime number\n";   
} else {
    echo "7 is not prime number\n"; 
}

if (isPrimeNumber(6)) {
    echo "6 is prime number\n";   
} else {
    echo "6 is not prime number\n"; 
}
```

## Homework 4

### Hint 1

1. Loop from 1 to `n` and re-use the function `isPrimeNumber` at `homework 3` to check if a number is prime number

---

### Hint 2
1. Define an array to store the prime numbers
2. Implement a function, this function takes an argument `n`, inside the function, loop `$i` from 1 to n, check if `$i` is prime number, append it to the array.
3. Return the Array.

----

### Hint 3

Full source code

```php
<?php
// reuse the function at step 3
function isPrimeNumber($n) {
    // Because 0 and 1 are not prime numbers
    if ($n == 0 || $n == 1) {
        return false;
    }

    // 2 is a prime number
    if ($n == 2) {
        return true;
    }

    $m = $n/2;
    for ($i = 2; $i <= $m; $i++) {
        // if can devided by another number (not 1 and itself), not prime number
        if ($n%$i == 0) {
            return false;
        }
    }

    return true;
}

function getPrimeNumbers($tn) {
    $result = [];
    for ($i = 1; $i <= $tn; $i++) {
        if (isPrimeNumber($i)) {
            array_push($result, $i);
        }
    }

    return $result;
}

// Try to check the function
print_r(getPrimeNumbers(10));

?>


