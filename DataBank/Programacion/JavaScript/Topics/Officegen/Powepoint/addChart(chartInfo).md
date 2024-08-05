### Create

```js
slide.addChart(chartInfo)
```

### Values

Where `chartInfo` object is an object that takes the following attributes:

- `data` - an array of data, see examples below
- `renderType` - specifies base chart type, may be one of `"bar", "pie", "group-bar", "column", "stacked-column", "line"`
- `title` - chart title (default: none)
- `valAxisTitle` - value axis title (default: none)
- `catAxisTitle` - category axis title (default: none)
- `valAxisMinValue` - value axis min (default: none)
- `valAxisMaxValue` - vlaue axis max value (default: none)
- `valAxisNumFmt` - value axis format, e.g `"$0"` or `"0%"` (default: none)
- `valAxisMajorGridlines` - true|false (false)
- `valAxisMinorGridlines` - true|false (false)
- `valAxisCrossAtMaxCategory` - true|false (false)
- `catAxisReverseOrder` - true|false (false)
- `fontSize` - text size for chart, e.g. "1200" for 12pt type
- `xml` - optional XML overrides to `<c:chart>` as a Javascript object that is mixed in

### xml

Also, the overall chart and each data series take an an optional `xml` attribute, which specifies XML overrides to the `<c:series>` attribute.

- The `xml` argument for the `chartInfo` is mixed in to the `c:chartSpace` attribute.
- The `xml` argument for the `data` series is mixed into the `c:ser` attribute.

For instance, to specify the overall text size, you can specify the following on the `chartInfo` object. The snippet below is what happens under the scenes when you specify `fontSize: 1200`

```js
chartInfo = {
 // ....
 "xml": {
      "c:txPr": {
        "a:bodyPr": {},
        "a:listStyle": {},
        "a:p": {
          "a:pPr": {
            "a:defRPr": {
              "@sz": "1200"
            }
          },
          "a:endParaRPr": {
            "@lang": "en-US"
          }
        }
      }
    }
```

### Examples

#### Column chart

```js
slide = pptx.makeNewSlide();
slide.name = 'Chart slide';
slide.back = 'ffffff';
slide.addChart(
  {   title: 'Column chart',
          renderType: 'column',
          valAxisTitle: 'Costs/Revenues ($)',
          catAxisTitle: 'Category',
          valAxisNumFmt: '$0',
                valAxisMaxValue: 24,
    data:  [ // each item is one serie
    {
      name: 'Income',
      labels: ['2005', '2006', '2007', '2008', '2009'],
      values: [23.5, 26.2, 30.1, 29.5, 24.6],
      color: 'ff0000' // optional
    },
    {
      name: 'Expense',
      labels: ['2005', '2006', '2007', '2008', '2009'],
      values: [18.1, 22.8, 23.9, 25.1, 25],
      color: '00ff00' // optional
    }]
  }
)
```

#### Pie chart

```js
slide = pptx.makeNewSlide();
slide.name = 'Pie Chart slide';
slide.back = 'ffff00';
slide.addChart(
  {   title: 'My production',
      renderType: 'pie',
    data:  [ // each item is one serie
    {
      name: 'Oil',
      labels: ['Czech Republic', 'Ireland', 'Germany', 'Australia', 'Austria', 'UK', 'Belgium'],
      values: [301, 201, 165, 139, 128,  99, 60],
      colors: ['ff0000', '00ff00', '0000ff', 'ffff00', 'ff00ff', '00ffff', '000000'] // optional
    }]
  }
)
```

#### Bar chart

```js
slide = pptx.makeNewSlide();
slide.name = 'Bar Chart slide';
slide.back = 'ff00ff';
slide.addChart(
  { title: 'Sample bar chart',
    renderType: 'bar',
      data:  [ // each item is one serie
      {
        name: 'europe',
        labels: ['Y2003', 'Y2004', 'Y2005'],
        values: [2.5, 2.6, 2.8],
        color: 'ff0000' // optional
      },
      {
        name: 'namerica',
        labels: ['Y2003', 'Y2004', 'Y2005'],
        values: [2.5, 2.7, 2.9],
        color: '00ff00' // optional
      },
      {
        name: 'asia',
        labels: ['Y2003', 'Y2004', 'Y2005'],
        values: [2.1, 2.2, 2.4],
        color: '0000ff' // optional
      },
      {
        name: 'lamerica',
        labels: ['Y2003', 'Y2004', 'Y2005'],
        values: [0.3, 0.3, 0.3],
        color: 'ffff00' // optional
      },
      {
        name: 'meast',
        labels: ['Y2003', 'Y2004', 'Y2005'],
        values: [0.2, 0.3, 0.3],
        color: 'ff00ff' // optional
      },
      {
        name: 'africa',
        labels: ['Y2003', 'Y2004', 'Y2005'],
        values: [0.1, 0.1, 0.1],
        color: '00ffff' // optional
      }

    ]
  }
)
```

#### Line chart

```js
slide = pptx.makeNewSlide();
slide.name = 'Line Chart slide';
slide.back = 'ff00ff';
slide.addChart(
  { title: 'Sample line chart',
    renderType: 'line',
      data:  [ // each item is one serie
      {
        name: 'europe',
        labels: ['Y2003', 'Y2004', 'Y2005', 'Y2006'],
        values: [2.5, 2.6, 2.8, 2.4],
        color: 'ff0000' // optional
      },
      {
        name: 'namerica',
        labels: ['Y2003', 'Y2004', 'Y2005', 'Y2006'],
        values: [2.5, 2.7, 2.9, 3.2],
        color: '00ff00' // optional
      },
      {
        name: 'asia',
        labels: ['Y2003', 'Y2004', 'Y2005', 'Y2006'],
        values: [2.1, 2.2, 2.4, 2.2],
        color: '0000ff' // optional
      }
    ]
  }
)
```