### Create

```js
var rows = [];
  for (var i = 0; i < 12; i++) {
    var row = [];
    for (var j = 0; j < 5; j++) {
      row.push("[" + i + "," + j + "]");
    }
    rows.push(row);
  }
  slide.addTable(rows, {});
```

### Values
Specific options for tables (in addition to standard : x, y, cx, cy, etc.) :

- `columnWidth` : width of all columns (same size for all columns). Must be a number (~1 000 000)
- `columnWidths` : list of width for each columns (custom size per column). Must be array of number. This param will overwrite columnWidth if both are given
### Example

```js
var rows = [];
rows.push([
	{
		val: "Category",
        	opts: {
          		font_face   : "Arial",
          		align       : "l",
          		bold        : 0
        	}
      },
      {
        	val  :"Average Score",
        	opts: {
          		font_face   : "Arial",
          		align       : "r",
          		bold        : 1,
          		font_color  : "000000",
          		fill_color  : "f5f5f5"
        	}
      }
]);
slide.addTable(rows, {});
```