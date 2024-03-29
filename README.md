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
    - NOTE: In absolute position, the element is detached from the body and hence will not add to the body height value!

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
	- In Flexbox, all it's child elements will be placed in a row called "Main Axis" next to each other.
	- It also contains what is called a "Cross Axis" that grows vertically.
	- Flex values are comprised of 3 items:
		- Flex Grow
		- Flex Shrink & 
		- Flex Basis
	- Both Flex Grow & Flex Shrink are based on Flex Basis, so that is the first thing to be looked at.
		- Flex Basis:
			- It determines the minimum amount of flex container area that is to be reserved for an element.
			- It's value can be expressed using any parameters like px, inches, % etc that also applies to CSS "width" property.
			- If we set flex-basis as 0, it will not have any initial width set. Instead it just grows according to the need.
			- On the other hand, if flex-basis is set to 20%, it will cause this element to have a width of atleast 20%
		- Flex Grow
			- It determines if an element is allowed to grow to the remaining available container size
			- If set to 0, it will not grow.
			- If set to any +ve value, it grows. This +ve value will also act as a weighted value.
			- So if two elements have flex-grow set to 2 & 1, first element grow and occupy twice the size of 
			  the remainder container size than that occupied by the second element.
		- Flex Shrink
			- This is similar to Flex Grow, except it's value determines if it allows to shrink the content or let it overflow.
			- If set to 0, it will let it overflow.
			- Any +ve value, it will start shrinking that element. This +ve value will also act as a weighted value.
			- So if two elements have flex-shrink set to 2 & 1, first element shrink at twice the rate of second element.
		- By default Flex parameters take the order:
			flex-grow, flex-shrink, flex-basis
		  and have the default values {1, 1, 0%}
	- Flex Direction can be used to set the direction of element flow. 
			- We can use it to layout elements in row, row-reverse, column or column-reverse
			{
				flex-direction:row-reverse;
			}
	- In addition to these there are many other Flexbox properties such as align-self, order, justify-content, flex-flow etc.
			- They can all be used to control the flow of layout in a webpage.
			- Refer to Flexbox docs and books to learn more about these miscellaneous properties.
	
	- Flex-Flow: It is a shorthand property for Flex-Direction and Flex-Wrap properties.
	
	- Align-Self: This property specifies the alignment for the selected item inside a Flex container. 
			It overrides the default align-items property.

## CSS Grid

	- CSS Grid is another specification that can be used to create Grid layouts.
	- It is not a replacement for Flexbox, but work in conjunction with it.
	- CSS Grid is called by adding the CSS property:
		display: grid;
	- The number of rows and columns in a CSS grid is defined using the CSS properties:
		grid-template-columns: 1fr 1fr 1fr;
		grid-template-rows: 1fr 1fr;
		grid-gap: 0.5em
		
		where fr stands for "fraction".
	- Grid-column property will define the width of an element. An example of this:
		grid-column: 1/3;   /* Spans from vertical grid line 1 to grid line 3 */


## CSS Background
	- CSS background-clip property will define how far background image or color should stretch within an element.
	- CSS background-attachment property will specify if the background image is going to scroll along with the webpage or remains fixed.
	- CSS background-origin property will specify the origin position of the background image.

## CSS Borders
	- border-image-source: This property wil specify the image to be used for borders.
	
## CSS Hyphens
	- Specifies if hyphens are allowed. If yes, also specifies who does it.
	- Valid values: none, manual, auto, initial, inherit

## Responsive Design - Viewport
	- By adding meta viewport tag, we are telling the browser that our webpages will be rendered differently for mobile screen size.
	- So,the browser will not try to shrink the webpage but instead, it will focus only to a part of the desktop webpage upto which it can showcase.

## Align an image to the center of the div
	- Set the margin to be auto
	- Set image display type block

## Create responsive image
	- Set width to 100%
	- Set height to auto

## Remove bullets from ul
	- Set style property list-style-type=none

## Make the font wider
	- Use font-stretch property

## CSS Gap property
	- It sets the gap (gutter) between rows and columns in a Grid layout.

## CSS Transform property
	- It applies a 2D or 3D transformation on an element.
	- Eg: TranlsateX, TranlsateY, Rotate, Scale, Skew etc.

## CSS Top Property
	- Top property is used to alter the displacement of an element from it's normal y-axis.
	- A negative top value can be used to overflow an element beyond the viewport.

## CSS Opacity
	- It is used to control the opacity of an element.
	- 0 makes the element invisible and 1 makes it visible.

## CSS Background Repeat
	- It will control whether to repeat the background image or not if the size of the image is smaller than the viewport.	

## Justify content - space between
	- For a list of inline items, we can arrange them in equal spaces by calling the property:
	 	justify-content: space-between;

## CSS Cursor property
	- The CSS cursor property can be used to change the type of cursor displayed over the specified element.
	- Eg: cursor: move;

## CSS Linear Gradient
	- Creates a linear gradient image that can be used as a background image.
	- Eg: background-image: linear-gradient(red, yellow);
## CSS Radial Gradient
	- Creates a radial gradient that can be set as background image
	- The colors set as options moves from inside out in order.	
	- Eg: background-image: radial-gradient(red, yellow, green);

## CSS Add Shadow To Text
	- Eg: text-shadow: 2px 2px;
## CSS Add Box Shadow
	- Eg: box-shadow: 10px 10px;
## CSS Background Repeat
	- Repeats background image as tiles
	- Eg: background-repeat: repeat-x;
