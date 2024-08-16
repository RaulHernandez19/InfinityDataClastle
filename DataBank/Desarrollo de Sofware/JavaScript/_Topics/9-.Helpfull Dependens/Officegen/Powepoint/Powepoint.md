# <font color="#b2a2c7">Creating</font>

```js
let pptx = officegen('pptx')

//...OR...//

let pptx = officegen({
	type: 'pptx', // We want to create a Microsoft Powerpoint document.
	... // Extra options goes here.
})
```

# <font color="#b2a2c7">Change the theme</font>

```js
let pptx = officegen({
	type: 'pptx', // We want to create a Microsoft Powerpoint document.
	themeXml: '... theme xml goes here ...' // Just copy the theme xml code from existing office document (stored in ppt\theme\theme1.xml).
})
```

# <font color="#b2a2c7">Document object's settings:</font>

- author (string) - The document's author (part of the Document's Properties in Office).
- creator (string) - Alias. The document's author (part of the Document's Properties in Office).
- description (string) - The document's properties comments (part of the Document's Properties in Office).
- keywords (string) - The document's keywords (part of the Document's Properties in Office).
- orientation (string) - Either 'landscape' or 'portrait'. The default is 'portrait'.
- pageMargins (object) - Set document page margins. The default is { top: 1800, right: 1440, bottom: 1800, left: 1440 }
- subject (string) - The document's subject (part of the Document's Properties in Office).
- title (string) - The document's title (part of the Document's Properties in Office).

```js
pptx.setDocTitle('...')
pptx.setDocSubject('...')
pptx.setDocKeywords('...')
pptx.setDescription( '...')
pptx.setDocCategory('...')
pptx.setDocStatus('...')
```

## <font color="#92cddc">Setting slide size:</font>

```js
pptx.setSlideSize(cx, cy, type, cxSLD, cySLD)
```

#### <font color="#d99694">Arguments:</font>

- cx - width of the slide and notes (in pixels)
- cy - height of the slide and notes (in pixels)
- cxSLD - width of the slide (in pixels) only if it's not the same as the notes size
- cySLD - height of the slide (in pixels) only if it's not the same as the notes size
- Supported types: '35mm','A3','A4','B4ISO','B4JIS','B5ISO','B5JIS','banner', 'custom', 'hagakiCard', 'ledger', 'letter', 'overhead', 'screen16x10', 'screen16x9', 'screen4x3'.

>Notes:
>- cx, cy, cxSLD and cySLD are optional and you can pass 0 if you just want to use one of the >standard sizes (anything except for 'custom').
>- If you are taking the values for cx, cy, cxSLD and cySLD from existing document then do: sourceValue / 12700
>- cxSLD and cySLD only working in version 0.5.0 or later of officegen.
>- if you didn't set cxSLD and cySLD then officegen will use the values of cx and cy also for cxSLD and cySLD.
# ⬜ <font color="#b2a2c7">New slide</font>

## <font color="#92cddc">Creating slide</font>

```js
let slide = pptx.makeNewSlide();
```

## <font color="#92cddc">Make subTitles</font>

```js

let slide = pptx.makeNewSlide({
  userLayout: 'title'
});
slide.setTitle('The title');
slide.setSubTitle('Another text'); // For either 'title' and 'secHead' only.
// for 'obj' layout use slide.setObjData(...) to change the object element inside the slide.

//...OR...//

slide = pptx.makeNewSlide({
  userLayout: 'title'
});

// Both setTitle and setSubTitle excepting all the parameters that you can pass to slide.addText - see below:
slide.setTitle([
  // This array is like a paragraph and you can use any settings that you pass for creating a paragraph,
  // Each object here is like a call to addText:
  {
    text: 'Hello ',
    options: {font_size: 56}
  },
  {
    text: 'World!',
    options: {
      font_size: 56,
      font_face: 'Arial',
      color: 'ffff00'
    }
  }
]);

```

## <font color="#92cddc">Slide's propieties</font>

- `"name"` - name for this slide.
- `"back"` - the background color.
```js
slide.back = {type: 'solid', color: '008800'};
```
- `"color"` - the default font color to use.
```js
slide.color = 'ffffff';
```
- `"show"` - change this property to false if you want to disable this slide.

## <font color="#ccc1d9">Object's type's methods</font>

### [[addText (text, options)]]
###  [[addImage (image, options)]]
### [[addShape (shape, options)]]
### [[addChart(chartInfo)]]
### [[addTable(rowsSpec, options)]]
### Extra 
- getPageNumber - return the ID of this slide.
### Global propieties object:

- `x` - start horizontal position. Can be either number, percentage or 'c' to center this object (horizontal).
- `y` - start vertical position. Can be either number, percentage or 'c' to center this object (vertical).
- `cx` - the horizontal size of this object. Can be either number or percentage of the total horizontal size.
- `cy` - the vertical size of this object. Can be either number or percentage of the total vertical size.
- `id` - optional custom ID (must be unique number).
- `name` - optional custom name.
- `title` - optional custom title.
- `desc` - optional custom description.
- `hidden` - optional boolean flag. If true then this shape will be hidden.
- `color` - the font color for text.
- `fill` - the background color.
- `line` - border color / line color.
	- - '`line_size`' - line width in pixels.
	- '`line_head`' - the shape name of the line's head side (either: 'triangle', 'stealth', etc).
	- '`line_tail`' - the shape name of the line's tail side (either: 'triangle', 'stealth', etc).
- `flip_vertical`: true - flip the object vertical.
- `flip_horizontal`: true - flip the object horizontal
- `shape` - see below.
# Save PP

```js
var stream = fs.createWriteStream('Presentacion.pptx');
pptx.generate(stream);
```