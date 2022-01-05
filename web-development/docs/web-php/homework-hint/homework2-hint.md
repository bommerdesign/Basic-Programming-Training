# Web Programing with PHP: Homework 2 Hint 

## Hint 1

- Remember that there is defined variable `$user`in header. We use can hide or show menu by checking if `$user` exists or not.

## Hint 2
- Condition to show menu:
  - If: $user is `false`, show menu Register
  - Else:  show menu My Profile


## Hint 3

Open `modules/partials/header.php` and update menu:

```php
<nav>
    <ul>
        <li><a href="./index.php">Home</a></li>
        <?php if ($user == false) { ?>
        <li><a href="./index.php?m=register">Register</a></li>
        <?php } else { ?>
        <li><a href="./index.php?m=profile">My Profile</a></li>
        <?php } ?>
    </ul>
</nav>
```