# Hint for Stack Homework

## Homework 1

### Hint 1

Use an array to store the worlds. Loop in the array and push it into a Stack.

### Hint 2

Following step.

1. Define an array to store the worlds of string and a Stack
2. Loop through the array
    - Check if the current string is same as the string at the top of the stack
        - If yes, pop the string from top
        - If not, push the string into the Stack
3. Return size of Stack by add a method to return size of the Stack


### Hint 3

Full source code.

Re-use the class `Stack` in the lession, and add below method to get size of Stack

```php
<?php
public function size()
{
    return sizeof($this->elements);
}
```

```php
<?php
function removeCoupleOfWords($worlds)
{
    $stack = new Stack();
  
    // Loop through the array
    for ($i = 0; $i < count($worlds); $i++) {
        // Push the current string if the stack is empty
        if ($stack->isEmpty())
            $stack->push($worlds[$i]);
        else
        {
            $str = $stack->top();
  
            // compare the current string with stack top if equal, pop the top
            if ($worlds[$i] == $str) {
                $stack->pop();
            } else { // otherwise push the current string
                $stack->push($worlds[$i]);
            }
        }
    }
  
    // Return stack size
    return $stack->size();
}

//try it
$worlds = ["ab", "aa", "aa", "bcd", "ab"];
echo removeCoupleOfWords($worlds);

```

