# Hint for LinkedList Homework

## Homework 1.

## Hint 1

- Re-use the method *deleteFirst* on Exercise
- Don't stop method until loop to end of linked list

## Hint 2
- Be carefully checking duplicated data on head node. so loop check head data util not match with input data

```
$input = [4, 4, 5];
```

## Hint 3

Please check the source code

```
public function deleteAll($data)
    {
        if ($this->head == null) { // linked list is empty
            echo "List is empty.";
            return;
        }
        while ($this->head->getData() == $data) {
            $this->head = $this->head->getNext();
        }

        $current = $this->head;

        while ($current->getNext() != null)
        {
            if ($current->getNext()->getData() == $data)
            {
                $current->setNext($current->getNext()->getNext());
            }
            else
            {
                $current = $current->getNext();
            }
        }
    }
```

## Homework 2.

## Hint 1

- Way-1: Use recursion
- Way-2: Without recursion, reversing linked list before print all elements

## Hint 2
Using recursion is so easy way, so we can keep this solution.

Following pseudocode without recursion

### Iterative Method 

```
1. Initialize three pointers prev as NULL, curr as head and next as NULL.
2. Iterate through the linked list. In loop, do following. 
	// Before changing next of current, 
	// store next node 
	next = curr->next
	// Now change next of current 
	// This is where actual reversing happens 
	curr->next = prev 
	// Move prev and curr one step forward 
	prev = curr 
	curr = next
```

### For example

Input

```
1 -> 2 -> 3 -> NULL
```
Step 1: Initialize three pointers prev as NULL, curr as head and next as NULL.

```
NULL->1 -> 2 -> 3 -> NULL
```

Step 2:

Loop fisrt Node 1. Remove next pointer to Node 2 and then make a pointer to prevous Node (NULL)
```
NULL<-1  2 -> 3 -> NULL
```

Step 3:

Loop next Node 2. Remove next pointer to Node 3 and then make a pointer to prevous Node (Node 1)
```
NULL <-1 <- 2 3 -> NULL
```

Step 4:

Loop next Node 3. Remove next pointer to Node Last(NULL) and then make a pointer to prevous Node (Node 2)
```
NULL <-1 <- 2 <- 3 NULL
```
Step 5: Visit and show all elements

## Hint 3

```
 public function reverse()
    {
		$preNode = null;
        $currNode = $this->head;
		$nextNode = null;

        echo "Linked List: ";

        while ($currNode != null) { //stop when node is NULL
            $nextNode = $currNode->getNext(); 
            $currNode->setNext($preNode);
            $preNode = $currNode;
            $currNode = $nextNode;
        }
		$this->head =$preNode;
    }
```

## Homework 3.

## Hint 1

1. Traverse the list from start to end.
2. If the head node of second list lies in between two node of the first list, insert it there and make the next node of second list as the head. Continue this until there is no node left in both lists, i.e. both the lists are traversed.
3. If the first list has reached end while traversing, point the next node to the head of second list.

## Hint 2

Make sure can get head Node by setting modify access or create getter method.

```
class LinkedList { 
    /** @var Node  head node */
    public $head;
	...
}
```


```
/**
* Merges two given lists in-place. This function
* mainly compares head nodes and calls mergeUtil()
* @param LinkedList
*/
public function merge($h1, $h2)
{
	if ($h1->head == null)
		return $h2;
	if ($h2->head == null)
		return $h1;

	// start with the linked list
	// whose head data is the least
	if ($h1->head->getData() < $h2->head->getData())
		return $this->mergeUtil($h1, $h2);
	else
		return $this->mergeUtil($h2, $h1);
}
```

```
/**
* Merges two lists with headers as h1 and h2.
* It assumes that h1's data is smaller than
* or equal to h2's data.
* @param LinkedList
*/
public function mergeUtil($h1, $h2)
{
	// if only one node in first list
	// simply point its head to second list
	if ($h1->head->getNext() == null) {
		$h1->head->setNext($h2);
		return $h1;
	}

	// Initialize current and next pointers of
	// both lists
	$curr1 = $h1->head;
	$next1 = $h1->head->getNext();
	$curr2 = $h2->head;
	$next2 = $h2->head->getNext();

	while ($next1 != null && $curr2 != null) {
		// if curr2 lies in between curr1 and next1
		// then do curr1->curr2->next1
		if (($curr2->getData()) >= ($curr1->getData()) && ($curr2->getData()) <= ($next1->getData())) {
			$next2 = $curr2->getNext();
			$curr1->setNext($curr2);
			$curr2->setNext($next1);

			// now let curr1 and curr2 to point
			// to their immediate next pointers
			$curr1 = $curr2;
			$curr2 = $next2;
		}
		else {
			// if more nodes in first list
			if ($next1->getNext() != null) {
				$next1 = $next1->getNext();
				$curr1 = $curr1->getNext();
			}

			// else point the last node of first list
			// to the remaining nodes of second list
			else {
				$next1->setNext($curr2);
				return $h1;
			}
		}
	}
	return $h1;
}
```

For example:

```
$list = new LinkedList(); 
$list->insert(1); 
$list->insert(3); // (1) -> (3)
$list->insert(10); // (1) -> (3) -> (10)

$list1 = new LinkedList(); // 
$list1->insert(2); //
$list1->insert(4); // (2) -> (4)
$list1->insert(5); // (2) -> (4) -> (5)

$list2 = $list->merge($list, $list1);
$list2->visit();
```
