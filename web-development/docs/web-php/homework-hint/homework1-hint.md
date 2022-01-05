# Web Programing with PHP: Homework1 Hint 

## Hint 1
- Use `session_destroy()` to destroy login session

### Hint 2

- Create new page `Logout`. At this page, we will destroy login session by using `session_destroy()
` that you leanred at [Cookie and Session](./cookie-session.md), after destroyed session, redirect to homepage.
- Add link to logout page at the text `Logout`

### Hint 3

Full source code:

- Update `modules/partials/header.php`by replacing `<li><a href="javascript:void(0)">Logout</a></li>` to <li><a href="index.php?m=logout">Logout</a></li>

- Create new files `logout.php` under the folder `modules`, and add below source code to the file

```php
<?php
// File modules/logout.php
session_destroy();

// Redirect to home page after logout
header('Location: index.php');
?>
```


