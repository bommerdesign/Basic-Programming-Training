# Web Programing with PHP: Homework 5 Hint 

## Hint 1
- Use variable `$user` defined in header to check:
   - If user is not logged in, show the message.
   - If user is logged-in, query data and show on home page.

## Hint 2
- In order to query data, you can refer to the lession [PHP and MySQL](./php-mysql.md). You can read source code at `example/mysql_query.php`

## Hint 3

Update `modules/home.php`

```php
<!-- MAIN content -->
<div id="main">
    <div id="main-content">
    <?php if ($user === false) { ?>
        <h3>This is home page.</h3>
    <?php } else { ?>
        <!-- Get and show Users List -->
        <h3>Users List </h3>
        <?php
            try {
                $result = $mysql->query($sql);
            } catch (Exception $e) {
                echo "<p>Error: $e->getMessage()</p>";
            }
        ?>
        <table>
        <tr>
            <th>ID</th>
            <th>Fullname</th>
            <th>Username</th>
            <th>Email</th>
        </tr>
        <?php
        while($row = $result->fetch_array()) { ?>
            <tr>
                <td><?php echo $row['id'] ?></td>
                <td><?php echo $row['fullname'] ?></td>
                <td><?php echo $row['username'] ?></td>
                <td><?php echo $row['email'] ?></td>
            </tr>
        <?php } // end while ?>
        </table>    
    <?php } // end if ?>
    </div>
    <!-- embed sidbar.php -->
    <?php require __DIR__. '/partials/sidebar.php' ?>
</div>
```
