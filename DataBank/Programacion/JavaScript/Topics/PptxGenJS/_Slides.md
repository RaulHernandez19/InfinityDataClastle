# Add
```js
let slide = pptx.addSlide();
```

# Master slide

## Create
```js
pptx.defineSlideMaster({
        title: 'FIRST_SLIDE',
        bkgd: 'FFFFFF',
        objects: [
            { image: { w: '100%', h: '100%', path: "./.." } },
        ]
    });
```
## Using
```js
// Create a new Slide that will inherit properties from a pre-defined master page (margins, logos, text, background, etc.)  
let slide = pptx.addSlide("TITLE_SLIDE");
```

# Values

## Background-Color
```js
slide.background = { color: "F1F1F1" }; // Solid color  
slide.background = { color: "FF3399", transparency: 50 }; // hex fill color with transparency of 50%  
slide.background = { data: "image/png;base64,ABC[...]123" }; // image: base64 data  
slide.background = { path: "https://some.url/image.jpg" }; // image: url

// EX: Set slide default font color  
slide.color = "696969";
```

# Slide number

```js
// EX: Add a Slide Number at a given location  
slide.slideNumber = { x: 1.0, y: "90%" };  
  
// EX: Styled Slide Numbers  
slide.slideNumber = { x: 1.0, y: "95%", fontFace: "Courier", fontSize: 32, color: "CF0101" };
```

