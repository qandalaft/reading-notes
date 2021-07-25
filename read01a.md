# HTML Tables
* intro

HTML tables allow web developers to arrange data into rows and columns.
## synx
The <table> tag defines an HTML table.

Each table row is defined with a <tr> tag. Each table header is defined with a <th> tag. Each table data/cell is defined with a <td> tag.

By default, the text in <th> elements are bold and centered.

By default, the text in <td> elements are regular and left-aligned.

 for Example:
```
<table style="width:100%">
  <tr>
    <th>Firstname</th>
    <th>Lastname</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>50</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>94</td>
  </tr>
</table>
```
- it will shown like this 
```
Firstname 	Lastname	Age
Jill	 Smith	50
Eve	Jackson	94
John	Doe	80

```
** To Add a Border**

To add a border to a table, use the CSS `border` property:
 * like below
 ```
 table, th, td {
  border: 1px solid black;
}
```


