```js
slide.addText('Hola Mundo!', { x: 77.76, y: 400, font_size: 24, color: '000', font_face: 'Calibri'  })
```

#### Font properties:
- `font_face`
- `font_size` (in points)
- `bold`: true
- `underline`: true
- `char_spacing`: floating point number (kerning)
- `baseline`: percent (of font size). Used for superscript and subscript.
#### Text alignment properties
- `align` - can be either 'left' (default), 'right', 'center' or 'justify'.
- `indentLevel` - indent level (number: 0+, default = 0).

### More Examples

```js
// Change the background color:
slide.back = '000000';

// Declare the default color to use on this slide (default is black):
slide.color = 'ffffff';

// Basic way to add text string:
slide.addText('This is a test');
slide.addText('Fast position', 0, 20);
slide.addText('Full line', 0, 40, '100%', 20);

// Add text box with multi colors and fonts:
slide.addText([
  {text: 'Hello ', options: {font_size: 56}},
  {text: 'World!', options: {font_size: 56, font_face: 'Arial', color: 'ffff00'}}
  ], {cx: '75%', cy: 66, y: 150});
// Please note that you can pass object as the text parameter to addText.

slide.addText('Office generator', {
  y: 66, x: 'c', cx: '50%', cy: 60, font_size: 48,
  color: '0000ff' } );

slide.addText('Big Red', {
  y: 250, x: 10, cx: '70%',
  font_face: 'Wide Latin', font_size: 54,
  color: 'cc0000', bold: true, underline: true } );
```