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
    - Observation 1: If parent is static, height corresponds to viewport height but width is bound by parents width!
    - But if the parent position type is "relative" and this element is "aboslute", it is bound by the *entire area of the parent element*.
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
