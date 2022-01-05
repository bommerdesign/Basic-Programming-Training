# Web Programing with PHP: Homework 4 Hint

## Hint 1
- Same with homework 3, we already have varibale `$user` defined in header, you can user this variable to check and show user information on My Profile page, or redirect to Login page

## Hint 2

Update `modules/register.php` following

```php
<?php
if ($user == false) {
    header('Location: index.php?m=login');
    exit;
}
?>
<div id="main">
    <div id="main-content">
        <h3>My profile.</h3>
        <p>ID: <?php echo $user['id']; ?></p>
        <p>Full name: <?php echo $user['fullname']; ?></p>
        <p>Username: <?php echo $user['username']; ?></p>
        <p>Email: <?php echo $user['email']; ?></p>
    </div>
    <!-- embed sidbar.php -->
    <?php require __DIR__. '/partials/sidebar.php'; ?>
</div>
```
