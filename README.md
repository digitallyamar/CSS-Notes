# CSS-Notes
A quick notes on the findings of how CSS works for different properties.

# Layout

## CSS Position Property

### Static

    - This is the default value for position property.
    - Here, the HTML element is placed in their default flow position.
    - This element will occupy the *entire area of the parent element*.

### Relative

    - Here, the HTML element is positioned relative to it's default position.
    - This element will occupy the *entire area of the parent element*.
    - So in other words, all its values are bounded for entire stretch of it's parent element.

### Absolute

    - Here, the HTML element is positioned relative to it's parent's position.
    - This element will occupy the *entire area of the viewport* if the 
    parent element is of the default position type "static".
    - But if tge parent position type is "relative" and this element is "aboslute", it is bound by the *entire area of the parent element*.
    - So in other words, all its values are bounded for entire stretch of the view port by default and bound by parent for parent position=relative.
    - So it can draw on top of and go beyond the parent element itself!

    - Eg: position.html
        
        - Open position.html file in a browser
        - Watch the size of each element in dev console as you hover over them.
        - Change innerbox's position values to notice the difference.
        - Notice how even if body width is at 300px, it is reflected only in outerbox element.

### Brief note on margins

    - When innerbox position is set to relative, you will notice that margin has no effect at the top.
    - So you will not see any margin at the top of innerbox and it attaches to outerbox.
    - This happens due to (margin collapsing)[https://www.smashingmagazine.com/2019/07/margins-in-css/]
    - You can avoid this by setting a border value around outerbox.
    - So add something like:

        .outerbox {
            /* position:static; The default value*/
            width: 200px;
            height: 200px;
            background-color: crimson;
            border: 1px solid crimson;
        }


## CSS property value - initial

	- By setting a value to initial will cause that property to reset it's value to default initial value. 

	- Now, this is different from setting the property value to auto.
		- In fact, auto is not a valid value for many properties like border-width, padding etc.

	- Declaring display:initial is the same as display:inline even if the element is of type block like <div>.
		This is because initial value for display is always "inline".

## CSS property value - inherit

	- Setting a value to inherit will causes that value to lose it's current value and inherit it from it's parent.

	- You can also use the inherit keyword to force inheritance of a property not normally inherited.
		For example - in cases of border or padding.

## CSS shorthand properties

	- They will set values to associated properties in bulk.
		Eg: font, border etc.

	- It is important to note that when using shorthand, non explicit values will also be set to default values!

	- The order of short hand can be lenient in some cases, but can be ambiguous in others.
		- So for many properties, we use use order something like: top, right, bottom & left (Clockwise).
		- But few properties like background-position , box-shadow , and text-shadow take only two values.
			- In this case the values are reversed as compared to that of properties that uses 4 values.
			- So background-position: 25% 75% specifies the horizontal right/left values first. 
				It is then followed by the vertical top/bottom values.
			- The reason for this is straightforward: the two values represent a Cartesian grid.
			- Cartesian grid measurements are typically given in the order x, y (horizontal and then vertical).

## CSS measuring units em, rem, vh & vw

	- em is measured with respect to it's parent's font size.
	- rem is measured with respect to the root element's font-size.
	- vh - 1/100th of the viewport height
	- vw - 1/100th of the viewport width
	- vmin - 1/100th of the smaller dimension, height or width (IE9 supports vm instead of vmin)
	- vmax - 1/100th of the larger dimension, height or width (not supported in IE)

## CSS remove anchor text default decoration

	- If you want to remove default text decoration done to anchor element (i.e. turn link blue and underline it), 
	then target that anchor element <a> and set:
		text-decoration: none

## CSS remove unordered list elements' default bullet styling
	- To do this, target <ul> element and set:
		list-style-type: none

## CSS Flexbox

	- The outer most div element will be having a display property of type:
		display: flex;
	- In Flexbox, all it's child elements will be placed in a row, next to each other.
