- [Synergy](#synergy)
  * [Notices](#notices)
  * [Flexbox](#flexbox)
    + [Defining a box](#defining-a-box)
    + [Children](#children)
  * [Properties](#properties)
  * [Design guides](#design-guides)
    + [Two-element property guide:](#two-element-property-guide-)
    + [Three-element/four-element property guide:](#three-element-four-element-property-guide-)

# Synergy
Synergy is a flexbox-based CSS positioning library.  
It's very simple and easy for beginners.

## Notices
Synergy does not provide actual styles, and is just used for positioning and flexbox.

## Flexbox
*What is flexbox?*   
Flexbox is a modern way to align, scale, and organize HTML elements.  
Unfortunately, it's very hard to use, but Synergy simplifies this way further.

To actually use flexbox without Synergy, you can easily use this:

```css
.element {
  display: flex;
  flex-direction: row;
}
```

This will put every child of that element into a new column:
```element element element```

```css
.element {
  display: flex;
  flex-direction: column;
}
```

This will put every child of that element into a new row:
```
element
element
element
```

### Defining a box
There are two different directions that a flexbox can have.  
We support both directions: row, and column.

```css
flex-direction: row;
flex-direction: column;
```

Chrome usually interprets the row direction as displaying each child element in a column, and the column direction as displaying each child element in a row. This is why we switched the directions:
```html
<div class="flex-in-row"> <!-- Flexes each child in a row direction -->
</div>
<div class="flex-in-column"> <!-- Flexes each child in a column direction -->
</div>
```

Which applies these styles:

```css
.flex-in-row {
  display: flex;
  flex-direction: column;
}

.flex-in-column {
  display: flex;
  flex-direction: row;
}
```

### Children
The format for flexbox child styles (the elements inside of a flexbox) is like so:
```html
<div class="flex-in-row">
  <h1 class="child space-fit"></h1> <!-- Takes up as much space as the content -->
  <h1 class="child space-rest"></h1> <!-- Takes up the rest of the container's space -->
</div>
```

Which applies these styles:

```css
.child.space-fit {
  flex: 0 1 auto;
}

.child.space-rest {
  flex: 1;
}
```

This forces the first child to take up as much space as its contents, and the second child to take up the rest of the space in the flexbox.

You can also eliminate the default space applied to each child element with this class applied to the flexbox.

```html
<div class="flex-in-row children no-space">
  <p>No margin or padding</p>
  <p>One directly on top of the other.</p>
</div>
```

Which applies these styles:

```css
.children.no-space>* {
  margin: 0;
  padding: 0;
}
```

You can also align an element to the center by itself.

```html
<div class="flex-in-row">
  <p class="child align-center">Center aligned!</p> <!-- Aligns itself to the center of the container -->
</div>
```

Which applies these styles:

```css
.child.align-center {
  align-self: center;
}
```

## Properties
Width:
- w-all   : Width 100%
  - equal : Height 100%
- w-most  : Width 75%
  - equal : Height 75%
- w-half  : Width 50%
  - equal : Height 50%
- w-some  : Width 25%
  - equal : Height 25%

Height:
- h-all   : Height 100%
- h-most  : Height 75%
- h-half  : Height 50%
- h-some  : Height 25%

w- and h- properties can be used in combination.
Ex:
```html
<div class="w-most h-half"> <!-- 75% width but 50% height -->
</div>
```

## Design guides
*How do I use these design guides?*   
```w/h``` = width or height, abbreviated as w and h in Synergy. ```w/h-some``` can be used as either ```w-some``` or ```h-some```.   

```->``` = defines a match to the first property, for example ```75% -> 25%``` equals 100%. All of the matches in this guide add up to 100%.
### Two-element property guide:  
Common two-element design widths and heights.

- w/h-all -> 0% width (css)
- w/h-most -> w/h-some
- w/h-half -> w/h-half
- w/h-some -> w/h-most

### Three-element/four-element property guide:   
Common three or four element design widths and heights.

- w/h-half -> w/h-some -> w/h-some
- w/h-some -> w/h-some -> w/h-some -> w/h-some
- w/h-some -> w/h-half -> w/h-some

1: Focus is on the first element
2: Four elements, equal focus
3: Focus is on the second element.
