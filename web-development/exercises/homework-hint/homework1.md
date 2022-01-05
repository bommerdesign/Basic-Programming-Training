# Hint for Homework 1

## Hint 1
- Use css property: `posistion` to align the form at the top - right with the `px` you want
- Let the form showing when building the form & styling, after finish all, set `display: none` to hide it.
- Set even onlick on link `Login`, when user click on `Login`, set show Login form `display: block`

### Hint 2:

- Make HTML for form first, you can change HTML for search form to below

```HTML
<div id="form">
    <ul>
        <li>Hi <span>Guest</span></li>
        <!-- Add event onlick, when user click, show login form by calling function showLoginForm, we will make this function later -->
        <li><a href="javascript:void(0)" onclick="showLoginForm()">Login</a></li>
    </ul>
    
    <form id="login">
        <input type="text" name="username" placeholder="User name" />
        <input type="password" name="password" placeholder="Password"/>
        <label><input type="checkbox" name="rememberUsername" />Remember user name </label>
        <button type="submit" name="Login">Login</button>
    </form>
    <form method="GET" id="search">
        <input type="text" name="keyword" />
        <i class="material-icons">search</i>
    </form>
</div>
```

- Update CSS for the form

```CSS
#form {
    text-align: right;
}

#form ul {
    list-style: none;
}

#form ul li {
    display: inline-block;
    padding: 0 15px;
    color: #fff;
    letter-spacing: 1px;    
}

#form li span {
    font-weight: 700;
    color: #080;
}

#form a {
    color: #fff;
}


#login {
    position: absolute;
    z-index: 100;
    background-color: #fff;
    border: 1px solid #ccc;
    padding: 30px 0;
    display: none;
    width: 320px;
    top: 55px;
    right: 20px;
}

#login input {
    margin: 0 auto;
    display: block;
    width: 50%;
    background: #e6e6e6;
    border-radius: 10px;
    margin-bottom: 15px;
}

#login button {
    font-family: Montserrat-Bold;
    font-size: 15px;
    color: #fff;
    text-transform: uppercase;
    width: 68%;
    height: 50px;
    border-radius: 25px;
    background: #57b846;
    margin-right: 50px;
    margin-top: 20px;
    border: none;
}

#login button:hover {
    background: #333333;
}

#login label  {
    display: block;
    width: 100%;
    text-align: left;
    margin-left: 80px;
}

#login label input {
    display: inline-block;
    height: 20px;
    position: absolute;
    left: -20px;
}

#search {
    position: relative;
    margin-top: 30px;
}

/* #search input {
    /* padding: 6px; 
} */

#search i {
    position: absolute;
    right: 0px;
    top: 10px;
    color: green;
}
```

- Finally, Add javascrip function to show login form:

```javascript
function showLoginForm() {
    const form = document.getElementById('login');
    
    if (!form) { return; }
    
    form.style.display = form.style.display ? '' : 'block';
}
```

### Hint 3

Full source code [here](../../docs/src/html-css-js/exercises-2)

