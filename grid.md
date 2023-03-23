## CSS Grid
------------
CSS Grid Layout provides a two dimensional layout system, with rows and columns, making it easier to design responsive web applications or pages.

Grid is a layout method designed for two-dimensional content. That is, laying things out in rows and columns at the same time.

### Display Property
---------------------
An HTML element becomes a grid container when its display property is set to `grid` or `inline-grid`.

```html
The parent container with two direct children

<div class="parent-container">
  <div>A</div>
  <div>B</div>
</div>
```
```css
The parent container 
.parent-container {
  display: grid;
}
```

All direct children of the grid container automatically become grid items.

The following are the *parent properties*:-

### grid-template-columns
-------------------------	 
This specifies the size of the `columns`, and how many `columns` in a grid layout.
The value is a space-separated-list, where each value defines the width of the respective column.
If you want a grid layout to contain 4 columns, specify the width of the 4 columns, or "auto" if all columns should have the same width.
- Note: If you have more than 4 items in a 4 `columns` grid, the grid will automatically add a new row to put the items in.


```html
<div class="container">
  <div>A</div>
  <div>B</div>
</div>
```

```css
.container{
  display: grid;
  grid-template-columns: auto auto auto auto;
}
```

### grid-template-rows
----------------------	   
This specifies the size of the `rows`, and how many `rows` in a grid layout.
The value is a space-separated-list, where each value defines the height of the respective row:

```css
.container{
  display: grid;
  grid-template-rows: 90px 250px;
}
```


### grid-template
-----------------	     
`grid-template`	 is a shorthand property for the grid-template-rows, grid-template-columns and grid-areas properties

### Grid Gaps
-------------
The spaces between each column/row are called `gaps`.
You can adjust the gap size by using one of the following properties:

![grid columns](./grid-image/grid_gaps.png)

- `column-gap`
  
The `column-gap` property sets the `gap` between the columns:

- `row-gap`
  
The `row-gap` property sets the `gap` between the rows:

- `gap`

The `gap` property is a shorthand property for the `row-gap` and the `column-gap` properties:

The `gap` property can also be used to set both the `row gap` and the `column gap` in one value.

### justify-content 
--------------------
The `justify-content` property is used to align the whole grid inside the container.
Note: The grid's total width has to be less than the container's width for the 
justify-content property to have any effect.

```css
.grid-container {
  display: grid;
  justify-content: end;
  grid-template-columns: 50px 50px 50px; /*Make the grid smaller than the container*/
  gap: 10px;
  background-color: #2196F3;
  padding: 10px;
}
```
The justify-content values are: 
- space-evenly
- space-around
- space-between
- center
- start
- end

### align-content 
------------------
The `align-content` property is used to vertically align the whole grid inside the container. Note: The grid's total height has to be less than the container's height for the align-content property to have any effect.

```css
.grid-container {
  display: grid;
  height: 400px;
  align-content: center;
  grid-template-columns: auto auto auto;
}
```

The align-content values are: 
- center
- space-evenly
- space-around
- space-between
- start
- end


## CSS Grid Item(Child Elements (Items))
----------------------------------------
A grid container contains grid items.
By default, a container has one grid item for each column, in each row, but you can style the grid items so that they will span multiple columns and/or rows.

### Grid Columns
---------------
The vertical lines of grid items are called columns.

![grid columns](./grid-image/grid_columns.png)

The `grid-column` property defines on which column(s) to place an item.
You define where the item will start, and where the item will end.
The grid-column property is a shorthand property for the grid-column-start and the grid-column-end properties.

### Grid Rows
------------
The horizontal lines of grid items are called rows.

![grid columns](./grid-image/grid_rows.png)


### Grid Lines
--------------
The lines between columns are called `column lines`.

The lines between rows are called `row lines`.

![grid columns](./grid-image/grid_lines.png)



### Examples 
------------
- To place a grid item at column line 1, and let it end on column line 3:

```
.item1 {
  grid-column-start: 1;
  grid-column-end: 3;
}

.item1 {
   grid-column: 1 / 3;
}

.item1 {
  grid-column: 1 / span 3;
}
```
*Note: 
To place an item, you can refer to line numbers, or use the keyword "span" to define how many columns the item will span*


- To place a grid item at row line 1, and let it end on row line 3:

```
.item1 {
  grid-row-start: 1;
  grid-row-end: 2;
}

.item1 {
  grid-row: 1 / 2;
}

.item1 {
  grid-row: 1 / span 2;
}
```

### grid-template-areas
-----------------------	   
`grid-template-areas` specifies how to display `columns` and `rows`, using named grid items.

### grid Area
---------------
`grid-area `     either specifies a name for the grid item, It is also a shorthand property for `the grid-row-start`, `grid-column-start`, `grid-row-end`, and `grid-column-end` properties.


### Examples 
------------
Item-1 gets the name "myArea" and spans all five columns in a five columns grid layout:

```css
.grid-container {
  grid-template-areas: 'myArea myArea myArea myArea myArea';
}
.item-1 {
  grid-area: myArea;
}
```

### illustration
-----------------

```css
.item-1 { grid-area: header; }
.item-2 { grid-area: menu; }
.item-3 { grid-area: main; }
.item-4 { grid-area: right; }
.item-5 { grid-area: footer; }

.grid-container {
  grid-template-areas:
    'header header header header header header'
    'menu main main main right right'
    'menu footer footer footer footer footer';
}
```

### Examples 
------------
Make "item-8" start on row-line 1 and column-line 2, and end on row-line 5 and column line 6:

```html
<div class="container">
  <div class="item-1">A</div>
  <div class="item-2">B</div>
  <div class="item-3">A</div>
  <div class="item-4">B</div>
  <div class="item-5">A</div>
  <div class="item-6">B</div>
  <div class="item-8">A</div>
  <div class="item-9">B</div>
  <div class="item-10">B</div>
</div>
```

```css
.item-8 {
  grid-area: 1 / 2 / 5 / 6;
  grid-area: grid-row-start / grid-column-start / grid-row-end / grid-column-end
}
```

### Examples 
------------
Make "item8" start on row-line 2 and column-line 1, and span 2 rows and 3 columns:

```css
.item-8 {
  grid-area: 2 / 1 / span 2 / span 3;
}
```

### `The fr unit`
------------------
The fr unit, is a flexible length which describes a share of the available space in the `grid` container.
The fr unit works in a similar way to using `flex: auto` in flexbox. It distributes space after the items have been laid out. Therefore to have three `columns` which all get the same share of available space:

#### Example
-------------
```html
<div class="container">
  <div>A</div>
  <div>B</div>
  <div>C</div>
  <div>D</div>
</div>
```

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
```


### Functions
-------------

###  `repeat()`
The `repeat()` function can be used to repeat any section of your track listing. To create a 8 column track grid with equal columns, you could use the following CSS:

#### Example
-------------
```html
<div class="container">
  <div>A</div>
  <div>B</div>
  <div>C</div>
  <div>D</div>
  <div>E</div>
  <div>F</div>
  <div>G</div>
  <div>H</div>
  <div>I</div>
  <div>J</div>
  <div>K</div>
</div>
```

```css
.container {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
}
```
### The `minmax()`
-------------------
This is a function that can used to set a minimum and a maximum size for a track. It could be written out using minmax() as minmax(auto, 1fr). 


```css
.container {
    display: grid;
    grid-template-columns:
      minmax(0,1fr),
      minmax(0,1fr),
      minmax(0,1fr),
      minmax(0,1fr),
      minmax(0,1fr),
      minmax(0,1fr),
      minmax(0,1fr),
      minmax(0,1fr),
}
```

- With `repeat()` function, we have

```css
.container {
    display: grid;
    grid-template-columns: repeat(8, minmax(0,1fr));
}
```
