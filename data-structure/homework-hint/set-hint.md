# Hint for Set

## Homework 1

### Hint 1

Use class `Set` in exercise, loop through each element in array and add the elemen to the set.

-----

### Hint 2

Following pseudocode

1. Define a set from `Set` class in exercise: `$mySet = new Set()`
2. Loop through each elemeent in the array : `foreach($a as $elm)`
3. Add the element to the set: `$mySet->add($elm)`

---

### Hint 3

Full source code

Re-use class `Set` from the exercise

```php
class Set {
    /** @var array */
    private $elements;

    /**
    * constructor
    */
    public function __construct()
    {
        $this->elements = array();
    }

    /**
    * add element to set
    * @param int $ele
    */
    public function add($ele)
    {
        if (!$this->isExist($ele)) { // we have to check if element is existed before adding
            $this->elements[] = $ele; // because the order is any so we can add to the end or beginning
        }
    }

    /**
    * get set
    * @return array
    */
    public function get()
    {
        return $this->elements;
    }


    /**
    * check if element is exist in set
    * @param int $ele
    * @return bool
    */
    public function isExist($ele)
    {
        return in_array($ele, $this->elements); // In php, in_array use to check an element is in array or not
    }
}

```

Add elements of array to a set

```php
<?php
$a = [1, 2, 3, 4, 5, 2, -1, 5, 2, 7, 11, 11, -5];
$mySet = new Set();
foreach ($a as $elm) {
    $mySet->add($elm);
}

// Output the set to screen
print_r($mySet->get());
?>
```

## Homework 2

### Hint 1

It is almost same with the Homework 1, make a Set to contain words that you learned.

-----

### Hint 1

1. Define a Set for dictionary to contain learned words. Because Set only contains `unique values`, therefore it only contain `unique words`.

----

### Hint 2

1. Define a set to contain learned words `$dict = new Set();`
2. Put learned words in each day into arrays.
3. Put all array in step 2 into an 2-dimentional array.
3. Loop through arrays and add words to defined set.

### Hint 3

Full source code

```php
<?php
// Re-use class Set above.

// Define a set to contain dictionary
$dict = new Set();

// Put learned words in each day into arrays.
$day1Words = ["Hello", "Hi", "Good morning", "Good night"];
$day2Words = ["Hi", "Name", "Age"];
$day3Words = ["Good morning", "How are you", "Fine", "Thank"];

$allDays = [$day1Words, $day2Words, $day3Words];

// Loop through each words
foreach ($allDays as $day) {
    foreach($day as $word) {
        $dict->add($word);
    }
}

print_r($dict->get())
?>
