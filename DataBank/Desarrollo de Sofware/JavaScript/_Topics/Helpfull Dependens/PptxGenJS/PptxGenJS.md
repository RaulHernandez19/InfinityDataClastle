Biblioteca que permite crear presentaciones de PowerPoint con JavaScript. Es compatible con todos los navegadores de escritorio y móviles modernos, se integra con Node, Angular, React y Electron, y es compatible con Microsoft PowerPoint, Apple Keynote y muchas otras aplicaciones.

```bash
npm install pptxgenjs
```

# Creating a presentation

```js
import pptxgen from "pptxgenjs";  
let pres = new pptxgen();

//Client web Browser
let pres = new PptxGenJS();

```
#### Values
```js
pptx.author = 'Brent Ely';  
pptx.company = 'S.T.A.R. Laboratories';  
pptx.revision = '15';  
pptx.subject = 'Annual Report';  
pptx.title = 'PptxGenJS Sample Presentation';
```

## Slide Layout Syntax 
```js
pptx.layout = 'LAYOUT_NAME';
```
### Standard Slide Layouts[​](https://gitbrent.github.io/PptxGenJS/docs/usage-pres-options/#standard-slide-layouts "Direct link to heading")

| Layout Name    | Default | Layout Slide Size |
| :------------- | :------ | :---------------- |
| `LAYOUT_16x9`  | Yes     | 10 x 5.625 inches |
| `LAYOUT_16x10` | No      | 10 x 6.25 inches  |
| `LAYOUT_4x3`   | No      | 10 x 7.5 inches   |
| `LAYOUT_WIDE`  | No      | 13.3 x 7.5 inches |
### Custom Slide Layout Example

```js
// Define new layout for the Presentation  
pptx.defineLayout({ name:'A3', width:16.5, height:11.7 });  
  
// Set presentation to use new layout  
pptx.layout = 'A3'
```

### Default font

```js
pptx.theme = { headFontFace: "Arial Light" };  
pptx.theme = { bodyFontFace: "Arial" };
```

# ⬜ [[_Slides]]

- ### [[Text]]
- ### [[Images]]
- ### [[Charts]]
- ### [[Tables]]
- ### [[Saving Presentations]]


📕[Documentation](https://gitbrent.github.io/PptxGenJS/docs/usage-pres-create/)