# Hint For OOP Homework

## Homework 1

### Hint 1
Because both `rectangle` and `triangle` have properties `width` and `height`, so that we can define a Abstract class `Shape` with these properties and the constructor to set value for `width` and `height`.

-----

### Hint 2

Implement 2 classes `Rectangle` and `Triangle`, extend from the class `Shape`. Inside class `Rectangle`, implement method `area()` to calulate area for `Rectangle`, and Inside class `Triangle`, implement method `area()` to calulate area for `Triangle`

----

### Hint 3

Full implementation

```php
<?php

// Define class Shape following hint 1
abstract class Shape {
    protected $width;
    protected $height;

    public function __construct($width, $height) {
        $this->width = $width;
        $this->height = $height;
    }
}

// Define Rectangle class following hint 2
class Rectangle extends Shape {
    public function area() {
        return ($this->width * $this->height);
    }
}

// Define Triangle class following hint 2
class Triangle extends Shape {
    public function area() {
        return ($this->width * ($this->height/2));
    }
}

// Try to calculate area of a Rectangle
$rectangle = new Rectangle(1,2);
echo $rectangle->area();

// Try to calculate area of a Triangle
$triangle = new Triangle(1,2);
echo $triangle->area();

?>

```

## Homework 2

### Hint 1

For first take a look on the source 
```php
$sgEmailer = new SendGrid("youremail@yourdomain.com");
$sgEmailer->addRecipients("emailID@domain.com")->setSubject("Just a Test")->setBody("Hi Name, How are you?")->sendEmail();
```

We can see that if `$sgEmailer->addRecipients("emailID@domain.com")` return an instance of SendGrid, we can call `setSubject` after calling `addRecipients`, it is same idea with the method `setBody`.

---

### Hint 2

From hint 1, what we have to do is that just return current instance (object), in PHP, we can return current instance by `return $this` at end of method.

---

### Hint 3

As Hint 1 and Hint 2, we implement the class as below:

```php
abstract class Emailer {
  // Declare properties
  protected $sender;
  protected $recipients;
  protected $subject;
  protected $body;

  // Use Constructor to initialize sender and recipients
  function __construct($sender)
  {
    $this->sender = $sender;
    $this->recipients = array(); 
  }

  public function addRecipients($recipient)
  {
    array_push($this->recipients, $recipient);
    // Return current object
    return $this;
  }

  public function setSubject($subject)
  {
    $this->subject = $subject;
    return $this;
  }

  public function setBody($body)
  {
    $this->body = $body;
    return $this;
  }
}
```
