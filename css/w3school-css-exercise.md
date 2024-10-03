# W3School CSS Exercise Supplement
================================

**Author**: Lien Chen  **Date**: 2020-07-24

* [CSS Overflow](#css-overflow)
* [CSS Combinator](#css-combinator)
* [CSS Attribute](#css-attribute)
* [CSS Border Images](#css-border-images)
* [CSS Background](#css-background)

### CSS Overflow
[reference](https://www.w3schools.com/css/css_overflow.asp)

---
##### Overflow: scroll
Add a scrollbar both horizontally and vertically
**example**: `{ overflow: scroll; }`
[example](https://www.w3schools.com/css/tryit.asp?filename=trycss_overflow_scroll)

---
### CSS Combinator
[reference](https://www.w3schools.com/css/css_combinators.asp)

---

##### Adjacent Sibling Selector
**example**: `element + element2 {  background-color: yellow; }`

[example](https://www.w3schools.com/css/tryit.asp?filename=trycss_sel_element_pluss)


---
##### General Sibling Selector
**example**: `element ~ element2 {  background-color: yellow; }`

[example](https://www.w3schools.com/css/tryit.asp?filename=trycss_sel_element_tilde)

---
#### CSS Attribute
[reference](https://www.w3schools.com/css/css_attribute_selectors.asp)

---
##### Attribute containing specific word
**example**: `[title~="value"] { color: red; }`

[example](https://www.w3schools.com/css/tryit.asp?filename=trycss_sel_attribute_value2)

---
##### Attribute begins with a specified value
**example**: `[title^="value"] { color: red; }`

[example](https://www.w3schools.com/css/tryit.asp?filename=trycss_sel_attribute_start)

---
##### Attribute starting with the specified value
**example**: `[title|="value"] { color: red; }`

[example](https://www.w3schools.com/css/tryit.asp?filename=trycss_sel_attribute_hyphen)

---
##### Attribute ends with a specified value
**example**: `[title$="value"] { color: red; }`

[example](https://www.w3schools.com/css/tryit.asp?filename=trycss_sel_attribute_end)

---
##### Attribute value contains a specified value
**example**: `[title*="value"] { color: red; }`

[example](https://www.w3schools.com/css/tryit.asp?filename=trycss_sel_attribute_contain)

---
### CSS Border Images
[reference](https://www.w3schools.com/css/css3_border_images.asp)

---
##### CSS border-image
Allows you to specify an image to be used instead of the normal border around an element.
The element needs the border property set!
**example**: `{ border: 10px solid transparent;   padding: 15px; border-image: url(image.url) 30 round; }`

[example](https://www.w3schools.com/css/tryit.asp?filename=trycss3_border-image)

---
### CSS Background
#### CSS background-image
The background-image property sets one or **more** background images for an element.
**example**: `{ background-image: url(), url(); }`

[reference](https://www.w3schools.com/cssref/pr_background-image.asp)
---
#### CSS background-size
The background-size property specifies the size of the background images.
**cover**: Resize the background image to cover the entire container, even if it has to stretch the image or cut a little bit off one of the edges.
**auto**: Default value. The background image is displayed in its original size.
**contain**: Resize the background image to make sure the image is fully visible.

[reference](https://www.w3schools.com/csSref/css3_pr_background-size.asp)

---
#### CSS background-origin
The background-origin property specifies the origin position (the background positioning area) of a background image.
**padding-box**: Default value. The background image starts from the upper left corner of the padding edge	
**border-box**: The background image starts from the upper left corner of the border	
**content-box**: The background image starts from the upper left corner of the content

[reference](https://www.w3schools.com/csSref/css3_pr_background-origin.asp)

---
#### CSS background-clip
The background-clip property defines how far the background (color or image) should extend within an element.
**border-box**: Default value. The background extends behind the border	
**padding-box**: The background extends to the inside edge of the border	
**content-box**: The background extends to the edge of the content box

[reference](https://www.w3schools.com/csSref/css3_pr_background-clip.asp)

---
### CSS Web Fonts
#### CSS @font-face Rule
Web fonts allow Web designers to use fonts that are not installed on the user's computer.

[reference](https://www.w3schools.com/css/css3_fonts.asp)

---