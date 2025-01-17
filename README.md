# HTML&CSS Review

This repo contains my study notes and learning projects contained in the course [Build Responsive Real-World Websites with HTML and CSS](https://www.udemy.com/course/design-and-develop-a-killer-website-with-html5-and-css3/).

## HTML Notes

- `<strong>` and ~~`<b>`~~ are both used to make texts bold. However, `<strong>` label is more recommended since it has its semantics.

- `<em>` and ~~`<i>`~~ are both used to make texts italics. However, `<em>` label, which stands for emphasize, is more recommended.

- We could add `target="\_blank"` as an attribute-value pair inside the `<a>` label so that the link would be opened in new tab.

- `<header>`(header of the html doc/smaller units),  
  `<nav>`(for navigation links),  
  `<menu>`,  
  `<main>`,  
  `<article>`,  
  `<section>`,  
  `<aside>`(for secondary info),  
  `<blockquote>`,  
  `<figure>`,  
  `<footer>`(e.g., copyright),  
  are container labels for structuring html documents. They would be helpful for semantics HTML as well as CSS styling.

- `<div>` and `<span>` labels both are non-semantic html. The former is a _block_ label, while the latter is a _inline_ label.

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
  - adjacent sibling selector `h3 + p {}`

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

- **psuedo-elements**

  - first letter: `h1::first-letter {}`
  - first line: `h3 + p::first-line {}`
  - create an element(inline) as the first(`before`)/last(`after`) child of the selected element`h2::after {content: "TOP";}`

- **transform property**

  - `transform: translate(-50%, -50%);`  
    useful for aligning absolute positioned elements.
  - `transform: scale(1.5);`  
    useful for making images larger than its containers.

- **CSS Theory1: conlicting selectors**
  - declarations marked `!important` > inline styles > ID selector > class/psudeo-class selector > element selector > universal selector
  - if there are multiple conflicts of the same level, the last selector in code will apply
- **CSS Theory2: Inheritance and the Universal Selector**
  - The children html elements would inherit the styles of their parents elements. (not all the styles would be inherited, it's mostly ones related to text)
  - universal selector applies the specified styles(including those that couldn't be inherited) to all elements, which doesn't use the mechanism of inheritance.
- **CSS Theory3: The CSS Box Model**
  - global reset:  
     `* {margin: 0; padding: 0; box-sizing: border-box; /* the default is content-box */}`
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

## Layouts

- **Float**
  - `float: left;` `float: right;`
  - element is removed from the normal flow
  - text and inline elements will wrap around the floated element
  - the container will not adjust its height to the element  
    => collapsing height
    - clearfix hack  
      `.clearfix::after{content: ""; display: "block"; clear: both;}`  
      Clearfix only works when the selected element is a block element.  
      `after` pseudo-element only works when the content has been specified.
    - alternative way  
      Add an empty block element as the next sibling element(e.g., `<div class="clear"></div>`).  
      And then do `.clear {clear: both;}` in the corresponding CSS file.
- **Flexbox**
  - `display: flex;`
  - terminology:  
    ![flexbox-terms](image/flexbox.png)
  - properties for
    - flex container
      - 🦍`gap: 0;` | `<length>`  
        To create space between items, without using margin
      - 🦍`justify-content: flex-start;` | `flex-end` | `center` | `space-between` | `space-around` | `space-evenly`  
        To align items along main axis (horizontally)
      - 🦍`align-items: stretch;` | `flex-start` | `flex-end` | `center` | `baseline`  
        To align items along cross axis (vertically)
      - `flex-direction: row;` | `row-reverse` | `column` | `column-reverse`  
        To define which is the main axis
      - `flex-wrap: nowrap;` | `wrap` | `wrap-reverse`  
        To allow items to wrap into a new line if they are too large
      - `align-content: strech;` | `flex-start` | `flex-end` | `center` | `space-between` | `space-around`  
        Only applies when there are multiple lines(`flex-wrap: wrap;`)
    - flex items
      - 🦍`align-self: auto;` | `stretch` | `flex-start` | `flex-end` | `center` | `baseline`  
        To overwrite align-items for individual flex items
      - `flex-grow: 0;` | `<integer>`  
        To allow an element to grow(0 means no, 1+ means yes)
      - `flex-shrink: 1;` | `<integer>`  
        To allow an element to shrink when the container is not big enough(0 means no, 1+ means yes)
      - `flex-basis: auto;` | `<length>`  
        To define an item's width, instead of the width property
      - 🦍`flex: 0 1 auto;` | `<int> <int> <len>`  
        **Recommended** shorthand for flex-grow, -shrink, -basis
      - 🦍`order: 0` | `integer`  
        Controls order of items. -1 makes item first, 1 makes it last.
- **Grid**
  - `display: grid;`
  - terminology: cssgrid  
    ![cssgrid-terms](image/cssgrid.png)
  - properties for
    - grid container
      - 🦍`grid-template-rows: <track size>*`  
        `grid-template-columns: <track size>*`  
        To establish the grid row and column tracks.
        - **px**: only use the specified space.(fixed)
        - **fr**: similar to flex-grow, would use all the remaining space of the grid container. The higher the fr is for the column/row, the more space the column/row would fill.(proportionally)
        - **auto**: only use the minimum space of neccesity.
      - 🦍`row-gap: 0;` | `<length>`  
        `column-gap: 0;` | `<length>`  
        `gap: 0;` | `<length>`  
        To create empty space between tracks.
      - 🦍`justify-items: stretch;` | `start` | `center` | `end`  
        `align-items: stretch;` | `start` | `center` | `end`  
        To align items inside rows/columns (horizontally / vertically)
      - 🦍`justify-content: start;` | `center` | `end` | `...`  
        `align-content: start;` | `center` | `end` | `...`  
        To align entire grid inside grid container.  
        Only applies if container is larger than the grid.
    - grid items
      - 🦍`grid-column: <start line> / <end line>` | `span <number>`  
        `grid-row: <start line> / <end line>` | `span <number>`  
        To place a grid item into a specific cell, based on line numbers.  
        _span_ keyword can be used to span an item across more cells.  
        **examples:**
        1. `grid-column: 1 / 3;` == `grid-column: 1 / span 2;`
        2. `grid-column: 1 / 2;` == `grid-column: 1 / span 1;` == `grid-column: 1;`
      - 🦍`justify-self: stretch;` | `start` | `center` | `end`  
        `align-self: stretch;` | `start` | `center` | `end`  
        To overwrite justify-items/align-items for single items.

## Web Design Rules and Framework

- Inspirational Website

  - [land-book](https://land-book.com/)
  - [onepagelove](https://onepagelove.com/)
  - [awwwards](https://www.awwwards.com/)
  - [screenlane](https://screenlane.com/) => for components

- Helpful Systems

  - Font-size System
  - Font-weight System
  - Color System
  - Whitespace System

- **Rules #1: Typography**
  - tool box
    - [Google Fonts](https://fonts.google.com)  
      provide different kinds of fonts
    - [Type scale](https://type-scale.com/)  
      provide different font-size systems
  - serif vs sans-serif  
    ![serif_vs_sans-serif](image/serif_sansserif.png)
    - serif
      - traditional / classic look and feel
      - conveys trustworthiness
      - good for long text
    - sans-serif
      - modern look and feel
      - clean and simple
      - easier to fit the vibe
  - guidelines
    - typface
      - It's okay to use just one typeface per page! If you want more, limit to 2 typefaces.
    - `font-size` & `font-weight`
      - For "normal" text, use a font size between 16px and 32px for "normal" text.  
        for long text(like a blog post), try a size of 20px or even bigger
      - For headlines, you can go really big(50px+) and bold(600+), depending on personality
      - For any text, don't use a font weight under 400(regular)
    - reading experience
      - Use less than 75 characters per line
      - `line-height`
        - For normal-sized text, use a line height between 1.5 and 2.
        - For big text, go below 1.5
        - _The smaller or longer the text, the larger the line height needs to be_
      - `letter-spacing`  
        For headlines, decrease letter spacing if it looks unnatural.
      - Experiment with all caps for short titles.  
        Make them small and bold and increase letter-spacing.
- **Rules #2: Colors**
  - tool box
    - [Open Color](https://yeun.github.io/open-color/)
    - [tailwindcss]()
    - [Flat UI Colors]()
  - guidelines
    - color types
      - You need at least two types of colors in your color palette: a main color and a grey color  
        main color: draw attention to the most important elements on the page
        grey color: background & texts
      - With more experience, you can add more colors: accent colors(use a tool) => could use tools like [palleton]() or [coolors]()  
        Use accent colors to make entire components or sections stand out
      - For diversity, create lighter and darker "versions" (tints and shades)
        => could use tools like [Tine & Shade Generator]()
    - the relationship between colors
      - On dark colored backgrounds, try to use a tint of the background for text
      - Text should usually not be completely balck.
- **Rule #3: Images and Illustrations**
  - types  
    product photos, storytelling photos, illustrations, patterns
  - toolbox
    - [Unsplash]()
    - [Pexels]()
    - [DrawKit]()
    - [unDraw]()
  - guidelines
    - handling text on images
      - Method #1: Darker or brighter image(completely/partially, using a gradient)
      - Method #2: Position text into neutral image area
      - Method #3: Put text in a box
      - Method #4: Add showdows to text
    - technical details
      - compress images for lower file size with [Squoosh]()
- **Rule #4: Icons**
  - toolbox
    - [Phosphor icons]()
    - [heroicons]()
    - [ionicons]()
    - [ICONS8]()
  - guidelines
    - Use SVG icons or icon fonts(vector-based).  
      Don't use bitmap image foramts(.jpg / .png)
    - Use icons
      - to provide visual assistance to text
      - for product feature blocks
      - associated with actions
      - as bullet points
  - copy the `<svg>` label from the tool website, color them with `stroke` property / `fill` property.
- **Rule #5: Shadows**
  - add shadow to text  
    `text-shadow: <horizontal-length> <vertical-length> <blur> <color>`  
    e.g., `text-shadow: 0 5px 3px rgba(0, 0, 0, 0.2);`
  - add shadow to block  
    `box-shadow: <horizontal-length> <vertical-length> <blur> <spread> <color>`  
    e.g., `box-shadow: 0 20px 30px 0px rgba(0, 0, 0, 0.07);`
  - guidelines
    - small/medium-sized shadows => images, cards, sections
    - large shadows => modular, hover-menu
    - changing shadows on mouse interaction (click and hover)
- **Rule #6: Border-Radius**
  - `border-radius: 50%;` (maximum)  
    `border-radius: 16px;` (maximum if the min(w, h) is 32px)
  - `border-bottom-left-radius: 10px;`
  - guidlines
    - could use border-radius on
      - buttons, icons
      - images, cards, standout sections
      - modular, hover-menu
- **Rule #7: Whitespace**  
  implies invisible relationships between the elements of layout
  - guidelines
    - Use tons of whitespace between sections  
      Use a lot of whitespace between groups of elements  
      Use whitespace between elements
    - **Law of Proximity**: The more some elements belong together, the closer they should be
- **Rule #8: Visual Hierachy**
  - guidelines
    - Position important elements closer to the top of the page, where they get more attention.
    - Use images mindfully, as they draw a lot of attention.(larger images get more attention)
    - For text elements, use font size, font weight, color, and whitespace to convey importance.
    - For important component, use background color, shadow, or border to ephasize.
- **Rule #9: User Experience(UX)**
  - guidelines
    - Use patterns that users konw
    - Make your CALL-TO-ACTION the most prominent element, and make the text descriptive

## Components and Layout Patterns

- **Rule #10: Part1: Elements and Components**

  - Components
    - Accordion
    - Carousel
    - Table
      - _HTML_
      ```
        <table>
          <tr>
            <th>Chair</th>
            <th>Chair A</th>
            <th>Chair B</th>
          </tr>
          <tr>
            <th>Width</th>
            <td>80 cm</td>
            <td>120 cm</td>
          </tr>
          <tr>
            <th>Height</th>
            <td>100 cm</td>
            <td>200 cm</td>
          </tr>
        </table>
      ```
      - _CSS_
        - border related
          - `border-collapse: collapse;`  
            (should be applied on tables)
            1. when there is border, the border between cells & the border between cells&tables would be collapsed as one line
            2. when there is no border, the "invisible" border between cells would disappear when filling them with background color
          - `border: 1px solid #000;`  
            could be applied on tables/cells
          - Utilizing pseudo-class  
            `tbody tr:nth-child(odd){background-color: #f8f9fa;`  
            `tbody tr:nth-child(even){background-color: #e9ecef;}`
      - Pagination

- **Rule #10: Part2: Layout Patterns**

  - Section Components

    - Navigation Bar
    - Hero Section

      - viewport height  
        `height: 100vh;`
      - background-image (de-highlighted)

        ```
        background-image: linear-gradient(
            rgba(34, 34, 34, 0.6),
            rgba(34, 34, 34, 0.6)
          ),
          url(hero.jpg);
        background-size: cover;
        ```

    - Footer Section
    - Call-To-Action Section
    - Feature Rows

  - Layout Patterns

    - repeating boxes/cards
      - in Row
      - in Grid
    - repeating feature rows
      - Z-Pattern
      - F-Pattern
    - overall content
      - single column
      - sidebar
      - multi-column / Magzine
      - asymmetry / experimental

  - _take-aways from the example: a fake email application_
    - in flexbox, if we want to push a flex-item all the way to the right, we could do
      ```
      flex-item:last-child{
        margin-left: auto;
      }
      ```
    - `overflow: scroll;`  
      defines how elements that don't fit into container appear
