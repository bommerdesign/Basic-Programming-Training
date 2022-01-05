# Object-Oriented Programming

## Index
- [Java Encapsulation](https://www.w3schools.com/java/java_encapsulation.asp)
- [Java Inheritance](https://www.w3schools.com/java/java_inheritance.asp)
- [Java Polymorphism](https://www.w3schools.com/java/java_polymorphism.asp)
- [Java Abstraction](https://www.w3schools.com/java/java_abstract.asp)

## Exercise

### Problem

We need a system to send emails to users. And we can use other services for sending email such as SendGrid, MailChimp... Apply OOP to implement classes for email system. (Only simulate sending email)

### Solution.

Because any sending email need sender, receivers, email subject, email body. Therefore we can use Abstract class to implement this actions, it can be re-use in other email services, and in each email service, we only need to implement Sending email by extending Abstract class.

### Source code.

```java
import java.util.ArrayList;
import java.util.List;

abstract class Emailer {
    // Declare properties
    protected String sender;
    protected List<String> recipients;
    protected String subject;
    protected String body;

    // Use Constructor to initialize sender and recipients
    public Emailer(String sender) {
        this.sender = sender;
        this.recipients = new ArrayList<String>(); 
    }

    public void addRecipients(String recipient) {
        this.recipients.add(recipient);
    }

    public void setSubject(String subject) {
        this.subject = subject;
    }

    public void setBody(String body) {
        this.body = body;
    }

    /**
    * abstract method
    */
    public abstract void send();
}

// Implement method send for SendGrid and MailChimp

class SendGrid extends Emailer {
  public SendGrid(String sender) {
    super(sender);
  }
  
  public void send() {
    for (String recipient : this.recipients) {
      System.out.println("SendGrid successfully sent to " + recipient);
      System.out.println("Sender: " + this.sender);
      System.out.println("Subject: " + this.subject);
      System.out.println("Content: " + this.body);
    }
  }
}

class MailChimp extends Emailer {
  public MailChimp(String sender) {
    super(sender);
  }

  public void send() {
    for (String recipient : this.recipients) {
      System.out.println("MailChimp successfully sent to " + recipient);
      System.out.println("Sender: " + this.sender);
      System.out.println("Subject: " + this.subject);
      System.out.println("Content: " + this.body);
    }
  }
}

```

And send email by SendGrid or MailChimp

```java
public class Main {
    public static void main(String[] args) {
        // SendGrid
        SendGrid sgEmailer = new SendGrid("youremail@yourdomain.com");
        sgEmailer.addRecipients("emailID@domain.com");
        sgEmailer.setSubject("Just a Test");
        sgEmailer.setBody("Hi Name, How are you?");
        sgEmailer.send();


        // MailChimp
        MailChimp mcEmailer = new MailChimp("youremail@yourdomain.com");
        mcEmailer.addRecipients("emailID@domain.com");
        mcEmailer.setSubject("Just a Test");
        mcEmailer.setBody("Hi Name, How are you?");
        mcEmailer.send();
    }
}

```
[Check it](https://repl.it/join/rybufxnz-ohralathe)
## Homework

1. Write a program that defines a shape class with a constructor that gives value to width and height. The define two sub-classes triangle and rectangle, that calculate the area of the shape area(). After that, define two variables: a triangle and a rectangle and then call the area() function in this two varibles.

2. Look at exercise above, we are using the syntax below to send email:

```java
// SendGrid
SendGrid sgEmailer = new SendGrid("youremail@yourdomain.com");
sgEmailer.addRecipients("emailID@domain.com");
sgEmailer.setSubject("Just a Test");
sgEmailer.setBody("Hi Name, How are you?");
sgEmailer.send();


// MailChimp
MailChimp mcEmailer = new MailChimp("youremail@yourdomain.com");
mcEmailer.addRecipients("emailID@domain.com");
mcEmailer.setSubject("Just a Test");
mcEmailer.setBody("Hi Name, How are you?");
mcEmailer.send();
```

Let refactor the source code on the exercise to use syntax below to send email

```java
// SendGrid
SendGrid sgEmailer = new SendGrid("youremail@yourdomain.com");
sgEmailer.addRecipients("emailID@domain.com")
         .setSubject("Just a Test")
         .setBody("Hi Name, How are you?")
         .send();


// MailChimp
MailChimp mcEmailer = new MailChimp("youremail@yourdomain.com");
mcEmailer.addRecipients("emailID@domain.com")
        .setSubject("Just a Test")
        .setBody("Hi Name, How are you?")
        .send();
```
