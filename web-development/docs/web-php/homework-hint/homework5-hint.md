# Web Programing with PHP: Homework 5 Hint 

## Hint 1
Process page with below step:
- Use variable `$user` defined in header to check if not logged in, redirect to login.
- Check if `$user['password']` is not same with `current password`, show error.
- Check if `new password` is not same with `confirm password`, show error.
- If there is no error, process to update password.

## Hint 2
- You can create new page `Change Password` by add a new file `change_password.php` under the folder `modules` and process following Hint 1. At this page, you also should define and array to contains error messages, and loop though this array to output messages on screen.
- Create menu: you can check `if ($user !=== false)`, show menu and link to page `Change Password` (the link will be `index.php?m=change_password`).
- Set page title: open `header.php` and update `$page$pageTitles` to include the title of page `Change Password`.


## Hint 3

Full source code of `modules/change_password.php`

```php
<?php
if ($user == false) {
    header('Location: index.php?m=login');
    exit;
}

// Define an array to contain message
$messages = [];

// Receive form data
if (!empty($_POST)) {
    $currentPassword = md5($_POST['current_password']);
    $newPassword = md5($_POST['new_password']);
    $confirmPassword = md5($_POST['confirm_password']);

    /* If inputed new password is not same with current password,
     push error message to array $message for showing on UI */
    if ($currentPassword != $user['password']) {
        array_push($messages, "Current password is incorrect");
    }

    /*If inputed new password is not same with confirm password,
     push error message to array $message for showing on UI*/
    if ($newPassword != $confirmPassword) {
        array_push($messages, "Confirm password is not matched with New Password");
    }

    // If there is no error, process to update password
    if (empty($messages)) {
        $sql = "UPDATE users
        SET password = '$newPassword'
        WHERE id = " . $user['id'];

        try {
            $result = $mysql->query($sql);
            array_push($messages,"Your password is changed");
        } catch (Exception $e) {
            // if there is error, push the error message
            array_push($messages, $e->getMessage());
        }
    }
}
?>
<div id="main">
    <div id="main-content">
        <h3>Change Password</h3>
        <?php foreach($messages as $message) {
            echo "<p>$message</p>";
        } 
        ?>
        <form method="post" class="form-register">
            <p>
                <label>Current Password: </label>
                <input type="password" name="current_password" />
            </p>
            <p>
                <label>New Password: </label>
                <input type="password" name="new_password" />
            </p>
            <p>
                <label>Confirm Password: </label>
                <input type="password" name="confirm_password" />
            </p>
            <p><input type="submit" value="Change Password" /></p>
        </form>
    </div>
    <!-- embed sidbar.php -->
    <?php require __DIR__. '/partials/sidebar.php'; ?>
</div>
```

- Update page title by open `modules/partials/header.php` and modify `$pageTitles`

```php
<?php
$pageTitles = array(
    'home' => "Home",
    'login' => "Login",
    "profile" => "My Profile",
    "register" => "Regiser",
    "change_password" => "Change Password"
);
```

- At header, add menu link to page `Change Password`

```php
<nav>
    <ul>
        <li><a href="./index.php">Home</a></li>
        <?php if ($user == false) { ?>
        <li><a href="./index.php?m=register">Register</a></li>
        <?php } else { ?>
        <li><a href="./index.php?m=profile">My Profile</a></li>
        <li><a href="./index.php?m=change_password">Change Password</a></li>
        <?php } ?>
    </ul>
</nav>
```



