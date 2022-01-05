# CodeIgniter: Homework 1 - Hint

Add colums phone_number to table user. Update screens Create and Edit, allow input phone number when create or update user. Phone number only accept digits.

## Hint 1
- You need to update table `users` by add new column `phone_number`, max length of phone number is 15 digits as global standard https://en.wikipedia.org/wiki/Telephone_number
- In `View`, you need to update forms for creating and updating user to included `phone_number` in these forms.
- In User `model`, you need to update method `create_user` and `update_user` to include `phone_number`
- In User `controller`, you need to update method `create` and `update` to include `phone_number`

## Hint 2.
- In order to update form for creating user, open file `application/views/users/create.php`, add field for inputing `phone_number`.
- In order to update form for updating user, open file `application/views/users/update.php`, add field for inputing `phone_number`.
- Update User model by open file `application/models/Users_model.php`, in method `create_user` and `update_user`, add add email `'email' => $this->input->post('email')` to `$data`
- Update User controller by open file `application/controllers/Users.php`, in method `create` and `update`, update validation for `phone_number` to only accept digits, you can check validation at https://www.codeigniter.com/userguide3/libraries/form_validation.html

## Hint 3

### Add Phone Number to screen Create User

#### Update View: Add phone number to form for creating user

Open file `application/views/users/create.php`, below field `Email`, add field `Phone Number`:

```html
<div class="form-group">
    <label for="phone_number">Phone Number</label>
    <input type="text" class="form-control" name="phone_number" id="phone_number" placeholder="Enter your phone number">
</div>
```

#### Update User Model

Open file `application/models/Users_model.php` and update method `create_user`

```php
<?php
public function create_user()
{
    $this->load->helper('url');

    $data = array(
        'first_name' => $this->input->post('first_name'),
        'last_name' => $this->input->post('last_name'),
        'email' => $this->input->post('email'),
        'phone_number' => $this->input->post('phone_number')
    );

    return $this->db->insert('users', $data);
}
```

#### Update User Controller

Open User Controller, add `$this->form_validation->set_rules('phone_number', 'Phone Number', 'numeric');` to method `create` for validation phone number (only accept numbers).

```php
<?php
public function create()
{
    $this->load->helper('form');
    $this->load->library('form_validation');
    $this->load->helper('url');

    $data["page_title"] = "Create New User";
    $this->form_validation->set_rules('first_name', 'First name', 'required');
    $this->form_validation->set_rules('last_name', 'Last name', 'required');
    $this->form_validation->set_rules('email', 'Email', array('required','valid_email'));
    $this->form_validation->set_rules('phone_number', 'Phone Number', 'numeric');
    if ($this->form_validation->run() === FALSE) {
        $this->load->view('header', $data); 
        $this->load->view('users/create', $data);
        $this->load->view('footer');
    } else {
        $this->users_model->create_user();
        redirect(base_url('/'));
    }
}
```


### Add Phone Number to screen Update User

#### Update View: Add phone number to form for creating user

Open file `application/views/users/update.php`, below field `Email`, add field `Phone Number`:

```php
<div class="form-group">
    <label for="phone_number">Email</label>
    <input type="text" class="form-control" name="phone_number" id="phone_number" value="<?php echo $user->phone_number; ?>">
</div>
```

#### Update User Model

Open file `application/models/Users_model.php` and update method `update_user`

```php
<?php
public function create_user()
{
    $this->load->helper('url');

    $data = array(
        'first_name' => $this->input->post('first_name'),
        'last_name' => $this->input->post('last_name'),
        'email' => $this->input->post('email'),
        'phone_number' => $this->input->post('phone_number')
    );

    return $this->db->insert('users', $data);
}
```

#### Update User Controller

Open User Controller, add `$this->form_validation->set_rules('phone_number', 'Phone Number', 'numeric');` to method `update` for validation phone number (only accept numbers).

```php
<?php
public function update($user_id)
{
    $this->load->helper('form');
    $this->load->library('form_validation');

    $data["user"] = $this->users_model->get_user($user_id);

    $data["page_title"] = "Update User";
    $this->form_validation->set_rules('first_name', 'First name', 'required');
    $this->form_validation->set_rules('last_name', 'Last name', 'required');
    $this->form_validation->set_rules('email', 'Email', array('required','valid_email'));
    $this->form_validation->set_rules('phone_number', 'Phone Number', 'numeric');
    if ($this->form_validation->run() === FALSE) {
        $this->load->view('header', $data); 
        $this->load->view('users/update', $data);
        $this->load->view('footer');
    } else {
        $this->users_model->update_user($user_id);
        redirect(base_url('/'));
    }
}
```

