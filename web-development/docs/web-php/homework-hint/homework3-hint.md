# Web Programing with PHP: Homework 3 Hint

## Hint 1

- You can check an user is logged-in or not by varible `$user` defined in `header.php`. If `$user` is not `false`, mean that user is logged-in => redirect to home page.

## Hint 2

- From Hint 1: User function `header(...)` to redirect to Homepage.

## Hint 2

Add below source code to the top of `modules/register.php`

```php
// If $user is not false, mean that user is logged-in
if ($user != false) {
    // Redirect to home page
    header('Location: index.php');
}
```

