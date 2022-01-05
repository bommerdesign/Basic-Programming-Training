# Hint for Homework 2 (HTML-CSS-JS)

## Hint 1
- Use css `tr:nth-child(even)`: you can make style for `even rows` in the table (Example: 2nd row, 4th row... are `even` row)

### Hint 2

Add Table HTML to main content.

```HTML
<table>
    <tr>
        <th>ID</th>
        <th>Fullname</th>
        <th>Username</th>
        <th>Email</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Doloremque Laudantium</td>
        <td>doloremque</td>
        <td>doloremque@example.com</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Nemo enim</td>
        <td>nemo</td>
        <td>nemo@example.com</td>
    </tr>
    <tr>
        <td>3</td>
        <td>Adipisci Velit</td>
        <td>adipisci</td>
        <td>adipisci velit@example.com</td>
    </tr>
</table>
```

- Add CSS for the table:

```CSS
table {
    font-family: arial, sans-serif;
    border-collapse: collapse;
    width: 100%;
}

td, th {
    border: 1px solid #dddddd;
    text-align: left;
    padding: 8px;
}

tr:nth-child(even) {
    background-color: #dddddd;
}
```

### Hint 3

Please check full source code [here](../../docs/src/exercises-3)
