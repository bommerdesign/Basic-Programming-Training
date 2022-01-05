# CodeIgniter: Homework 3 - Hint

## Hint 1
You can follow below step:
- Add checkbox in each row, the name of checkbox is array, example `<input type="checkbox" name="ids[]" />`
- Make button `Delete`, when user click on this button, submit form to a page and process multi users at this page.

## Hint 2.

- You make new controller by add a method `delete_multi()` in User controller, in this method, you can receive User IDs that you want to delete like `$userIds = $_GET['ids'];`. `$userIds` is an array corresponsding with checked checkboxes.
- After received User IDs need to delete, add a method `delete_users($userIDs)` in User model (not that `$userIds` is an array). And you can execute query to delete user.


## Hint 3.

- Full source code.

### Add checkbox and delete button to Users List page

Open `application/views/users/index.php` and update

```html
<main role="main" class="flex-shrink-0">
  <div class="container">
      <h1>List of User</h1>
      <?php echo form_open('users/delete_multi'); ?>
      <table class="table table-striped table-hover">
          <thead>
              <tr>
              <th scope="col"><input type="checkbox" name="select-all" id="select-all" /></th>
              <th scope="col">#</th>
              <th scope="col">First Name</th>
              <th scope="col">Last Name</th>
              <th scope="col">Action</th>
              </tr>
          </thead>
          <tbody>
              <?php foreach ($users as $user): ?>
                  <tr>
                  <th scope="row"><input type="checkbox" name="ids[]" value="<?php echo $user['id']; ?>" /></th>
                  <th scope="row"><?php echo $user["id"]; ?></th>
                  <td><?php echo $user["first_name"]; ?></td>
                  <td><?php echo $user["last_name"]; ?></td>
                  <td>
                      <a href="#"><button class="btn btn-primary btn-sm">View</button></a>
                      <a href="<?php echo site_url("users/update/$user[id]"); ?>"><button class="btn btn-outline-primary btn-sm">Edit</button></a>
                      <a onclick="return confirm('Are you sure to delete this user?')" href="<?php echo site_url("users/delete/$user[id]"); ?>"><button class="btn btn-sm">Delete</button></a>
                  </td>
                  </tr>
              <?php endforeach; ?>
          </tbody>
      </table>
      <button type="submit" class="btn btn-danger">Delete</button>
      <?php echo form_close(); ?>
  </div>
</main>
```

### Add method to User Model to delete multiple Users.

Open User model `application/models/Users_model.php` and add method to delete multiple users

```php
<?php
public function delete_users($user_ids)
{
    return $this->db->where_in('id', $user_ids)->delete('users');
}
```

`$this->db->where_in('id', $user_ids)->delete('users');` will execute a query like `DELETE FROM users WHERE id IN (1,2...)`. You can check the query builder again at https://codeigniter.com/userguide3/database/query_builder.html


### Add method to User controller to delete multiple Users

Open `application/controllers/Users.php` and and add a method to delete multiple User

```php
<?php
public function delete_multi()
{
    $user_ids = $this->input->post('ids');
    if ($user_ids !== null) {
        $this->users_model->delete_users($user_ids);
    }
    redirect(base_url('/'));
}
?>
```


