# Recursive function

## What is recursive function?

Recursive Function is a function that calls itself until `base case` is reached. `Base case` is the case, when function reach this case, it will finish calling itself and break the function.
In general terms, a recursive function works like this:

1. The calling code calls the recursive function.
2. The function does any processing or calculations required.
3. If the base case has not yet been reached, the function calls itself to continue the recursion. This creates a new instance of the function.
4. If the base case is reached, the function just returns control to the code that called it, thereby ending the recursion.

The format of Recursive Function will be like:

```php
function myRecursiveFunction() {

    // (do the required processing...)

    if ( baseCaseReached ) {

        // end the recursion
        return;

    } else {

        // continue the recursion
        myRecursiveFunction();
    }
}
```

## Example Recursive Functiton

Write a recursive function to calculate the factorial for a given number, n

Example, Factorial of 5:
```
n! = 5 x 4 x 3 x 2 x 1 = 120
```

**Solution**

Most important of Recursive Function is `Base Case`, if there is no `Base Case` (or `Base Case` is nerver reached), Recursive Function will be a infinitive loop. So that, with factorial of a number, we can see that `Base Case` is `1!`

Now, let implement the function

```php
function factorialNumber($n) {
    // Base case: if $n is 1, return 1!= 1
    if ($n == 1) {
        return 1;
    }

    // Recursive: call function itself
    $result = $n * factorialNumber($n-1);
    return $result;
}

factorialNumber(5);
// Ouput is 120
```

Easier to understand, when you call `factorialNumber(5)`, the function will be excute like below:

```php
factorialNumber(5) 
    factorialNumber(4) 
        factorialNumber(3) 
            factorialNumber(2) 
                factorialNumber(1) 
                return 1 
            return 2*1 = 2 
        return 3*2 = 6 
    return 4*6 = 24 
return 5*24 = 120
```
