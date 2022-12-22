# HTML&CSS Review

This repo contains my study notes and learning projects contained in the course [Build Responsive Real-World Websites with HTML and CSS](https://www.udemy.com/course/design-and-develop-a-killer-website-with-html5-and-css3/).

## HTML Notes

- `<strong>` and ~~`<b>`~~ are both used to make texts bold. However, `<strong>` label is more recommended since it has its semantics.

- `<em>` and ~~`<i>`~~ are both used to make texts italics. However, `<em>` label, which stands for emphasize, is more recommended.

- We could add target="\_blank" as an attribute-value pair inside the `<a>` label so that the link would be opened in new tab.

- `<header>`(header of the html doc/smaller units), `<nav>`(for navigation links), `<article>`, `<footer>`(e.g., copyright), `<aside>`(for secondary info) are container labels for structuring html documents. They would be helpful for semantics HTML as well as CSS styling.

- useful VScode extension: auto rename tag(automatically change the closing tags when the openning tags were changed), prettier(formatter), color hightlight(for css), image preview(`<img>`), live server

## CSS Notes

- **styling text**

  - _font-size_: 26px;
  - _font-weight_: bold;
  - _font-family_: sans-serif;
  - _font-style_: italic;
  - _text-align_: center;
  - _text-transform_: uppercase;
  - _line-height_: 1.5; (1.5 times font size)

- **selector**

  - descendant selector `article header p {}`
  - list selector `h1, h2, h3, h4, p, li{}`
  - id selector `#author {}`
  - class selector `.related {}`

- **color**

  - text color => `color: #1098ad;`
  - background color of containers => `background-color: #f7f7f7;`
  - border color => `border(-top/left/right/bottom): 5px solid #1098ad;`

- **pseudo-classes**

  - `li:first-child {}`
  - `li:nth-child(odd) {}`
  - `article p:last-child {}` iff there is a `<p>` element as the last child of any `<article>` element.
  - **styling hyperlinks**
    - `a:link {}` (could use `text-decoration:none` to get rid of the default underline, we could also specify our own style, e.g., `text-decoration: underline wavy orangered`)
    - `a:visited {}`
    - `a:hover {}`
    - `a:active {}`

- **CSS Theory1: conlicting selectors**
  - declarations marked `!important` > inline styles > ID selector > class/psudeo-class selector > element selector > universal selector
  - if there are multiple conflicts of the same level, the last selector in code will apply
- **CSS Theory2: Inheritance and the Universal Selector**
  - The children html elements would inherit the styles of their parents elements. (not all the styles would be inherited, it's mostly ones related to text)
  - universal selector applies the specified styles(including those that couldn't be inherited) to all elements, which doesn't use the mechanism of inheritance.
- **CSS Theory3: The CSS Box Model**
  - global reset:
    `* {
  margin: 0;
  padding: 0;
}`
  - collapsing margins: the bigger margin between elements would be applied if both margins are specified
  - consistent with using margin-top/margin-bottom when trying to add vertical space between elements
  - `padding: 10px 20px` => the vertical paddings are 10 px and the horizontal paddings are 20px
  - a trick to center the content
    - add a div container around the content that we want to center
    - `.container{margin: 0 auto;}`
- **CSS Theory4: Types of Boxes**
  - BLOCK-LEVEL elements (`display: block;`)
    - 100% of parent's width => vertically, one after another
    - box-model could be applied
  - INLINE elements (`display: inline;`)
    - occupies only content's space => causes no line breaks
    - box-model is differently applied
      - hieghts and widths do not apply
      - paddings and margins only apply horizontally
  - INLINE-BLOCK elements (`display: inline-block;`)
    - Looks like inline from the outside(occupies only content's space)
    - Behaves like block-level on the inside(box-model applies as showed)
- **CSS Theory5: Absolute Positioning**
  - normal flow: elements are laid out according to their order in the HTML code
  - absolute positioning: no impact on surrounding elements, might overlap them
  - the way to use: Add `position: absolute;` for the element and set its top/bottom/left/right (e.g., `top: 5px;`). The element would be put based on these attributes relatively to its closest parent element with `position: relative` specified.
