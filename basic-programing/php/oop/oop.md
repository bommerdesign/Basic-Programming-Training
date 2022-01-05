# Object-Oriented Programming

## Index

- [OOP Introduction](https://www.w3schools.com/php/php_oop_what_is.asp)
- [Classes/Objects](https://www.w3schools.com/php/php_oop_classes_objects.asp)
- [Constructor](https://www.w3schools.com/php/php_oop_constructor.asp)
- [Destructor](https://www.w3schools.com/php/php_oop_destructor.asp)
- [Access Modifiers](https://www.w3schools.com/php/php_oop_access_modifiers.asp)
- [Inheritance](https://www.w3schools.com/php/php_oop_inheritance.asp)
- [Static Methods](https://www.w3schools.com/php/php_oop_static_methods.asp)
- [Static Properties](https://www.w3schools.com/php/php_oop_static_properties.asp)
- [Abstract Classes](https://www.w3schools.com/php/php_oop_classes_abstract.asp)
- [Interfaces](./oop-interface.md)

## Summary

We have learned OOP program, below things are what you should remember after learned.

### Basic OOP Terms Need To Remember
- **Class:** [A Class](https://www.w3schools.com/php/php_oop_classes_objects.asp) is a template for an object. A class contains the code which defines how an object will behave and interact either with each other.
- **Property:** A property is a container inside the class which can retain some information. Unlike other languages, PHP doesn't check the type of property variable. A property could be accessible only in class itself, by its subclass, or by everyone. In essence, a property is a variable which is declared inside the class itself, but not inside any function in that class.
- **Method:** Methods are functions inside a class. Like properties, methods can also be accessible by those three types of users.
- **Encapsulation:** Encapsulation is the mechanism that binds together code and the data it manipulates, and keeps both safe from outside interference and misuse. The wrapping up of data and methods into a single unit (called [Class](https://www.w3schools.com/php/php_oop_classes_objects.asp)) is known as encapsulation. The benefifit of encapsulating is that it performs the task inside without making you worry.
- **Polymorphism:** simply understand that it allows multiple class with various functionalities to implement or share a common [Interface](./oop-interface.md).
- **[Inheritance](https://www.w3schools.com/php/php_oop_inheritance.asp):** The key process of deriving a new object by extending another object is called inheritance. When you inherit an object from another object, the subclass (which inherits) derives all the properties and methods of the superclass (which is inherited). A subclass can then process each method of superclass anyway (which is called overriding).
- **Subclass:** A very common term in OOP. When an object is derived from another object, the derived one is called the subclass of which it is derived from.
- **Superclass (Parent class):** when you extend a class, the class which you are extending is the superclass of a newly extended class.
- **Instance:** Whenever you create an object by calling its constructor, it will be called an instance. To simplify this, whenever you write some thing like this `$var = new ClassName();` you actually create an instance of class.

### Benefits of OOP
- **Reusability:** **a class** is an entity which has bundles of properties and methods and can interact with other objects. An object can be sufficient or it may have dependencies over other objects. But an object is usually developed to solve a specific set of problems. So when other developers suffer from the same set of problems, they can just incorporate your class to their project and use it without affecting their existing workflow. It prevents from DRY, which means Don't Repeat Yourself. In functional or modular programming, reusing is possible but complex.
- **Refactoring:** When you need to refactor your projects, OOP gives you the maximum benefit because all objects are small entities and contain its properties and methods as a part of itself. So refactoring is comparatively easier.
- **Extensible:** If you need to add features to your project, you can achieve best results from OOP. One of the core OOP features is extensibility. You can refactor your object to add the feature. While doing it, you can still maintain backward compatibility of this object so that it works fine with an old code base. Or you can extend the object and create a totally new object that retains all the necessary properties and methods of the parent object from which it has been derived, and then expose new features. This is termed "inheritance" and is a very important feature of OOP.
- **Maintenance:** Object oriented code is easier to maintain because it follows somewhat strict coding conventions and is written in a self explanatory format. For example, when a developer extends it, refactors it, or debugs it, they can easily find out the inner coding structure and maintain the code time after time. Moreover, whenever there is a team development environment in your project, OOP could be the best solution because you can distribute your code after splitting it into small parts. These small parts could be developed as a separate classes, so developers can develop them almost independently. Finally, it will be very easy to merge the code.


### Conclusion
The OOP program is most important in basic programing, the "keywords" `Class, Object, Constructor/Destructor, Access Modifiers, Inheritance, Static Methods/Properties, Abstract Class, Interface` are realy necessary for your task related to programing. You can't be a real Software Developer if you don't undertand this part clearly.

## Exercise

### Problem

We need a system to send emails to users. And we can use other services for sending email such as SendGrid, MailChimp... Apply OOP to implement classes for email system. (Only simulate sending email)

### Solution.

Because any sending email need sender, receivers, email subject, email body. Therefore we can use Abstract class to implement this actions, it can be re-use in other email services, and in each email service, we only need to implement Sending email by extending Abstract class.

### Source code.

```php
<?
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
  }

  public function setSubject($subject)
  {
    $this->subject = $subject;
  }

  public function setBody($body)
  {
    $this->body = $body;
  }
}

// Implement method sendEmail for SendGrid and MailChimp

class SendGrid extends Emailer {
  public function sendEmail()
  {
    foreach ($this->recipients as $recipient) {
      $result = mail($recipient, $this->subject, $this->body, "From: {$this->sender}\r\n");
      echo "SendGrid successfully sent to {$recipient}\n";
      echo "Sender: $this->sender\n";
      echo "Subject: $this->subject\n";
      echo "Content: $this->body\n";
    }
  }
}

class MailChimp extends Emailer {
  public function sendEmail()
  {
    foreach ($this->recipients as $recipient) {
      $result = mail($recipient, $this->subject, $this->body, "From: {$this->sender}\r\n");
      echo "MailChimp successfully sent to {$recipient}\n";
      echo "Sender: $this->sender\n";
      echo "Subject: $this->subject\n";
      echo "Content: $this->body\n";
    }
  }
}

?>
```

And send email by SendGrid or MailChimp

```php

// SendGrid
$sgEmailer = new SendGrid("youremail@yourdomain.com");
$sgEmailer->addRecipients("emailID@domain.com");
$sgEmailer->setSubject("Just a Test");
$sgEmailer->setBody("Hi Name, How are you?");
$sgEmailer->sendEmail();


// MailChimp
$sgEmailer = new MailChimp("youremail@yourdomain.com");
$sgEmailer->addRecipients("emailID@domain.com");
$sgEmailer->setSubject("Just a Test");
$sgEmailer->setBody("Hi Name, How are you?");
$sgEmailer->sendEmail();
```

## Homework

1. Write a program that defines a shape class with a constructor that gives value to width and height. The define two sub-classes triangle and rectangle, that calculate the area of the shape area(). After that, define two variables: a triangle and a rectangle and then call the area() function in this two varibles.

2. Look at exercise above, we are using the syntax below to send email:

```php
// SendGrid
$sgEmailer = new SendGrid("youremail@yourdomain.com");
$sgEmailer->addRecipients("emailID@domain.com");
$sgEmailer->setSubject("Just a Test");
$sgEmailer->setBody("Hi Name, How are you?");
$sgEmailer->sendEmail();


// MailChimp
$mcEmailer = new MailChimp("youremail@yourdomain.com");
$mcEmailer->addRecipients("emailID@domain.com");
$mcEmailer->setSubject("Just a Test");
$mcEmailer->setBody("Hi Name, How are you?");
$mcEmailer->sendEmail();
```

Let refactor the source code on the exercise to use syntax below to send email

```php
// SendGrid
$sgEmailer = new SendGrid("youremail@yourdomain.com");
$sgEmailer->addRecipients("emailID@domain.com")->setSubject("Just a Test")->setBody("Hi Name, How are you?")->sendEmail();


// MailChimp
$mcEmailer = new MailChimp("youremail@yourdomain.com");
$mcEmailer->addRecipients("emailID@domain.com")->setSubject("Just a Test")->setBody("Hi Name, How are you?")->sendEmail();
```
