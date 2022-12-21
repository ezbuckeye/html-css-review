# HTML&CSS Review

This repo contains my study notes and learning projects contained in the course [Build Responsive Real-World Websites with HTML and CSS](https://www.udemy.com/course/design-and-develop-a-killer-website-with-html5-and-css3/).

## HTML Notes

#### Dec 18 2022

- `<strong>` and ~~`<b>`~~ are both used to make texts bold. However, `<strong>` label is more recommended since it has its semantics.

- `<em>` and ~~`<i>`~~ are both used to make texts italics. However, `<em>` label, which stands for emphasize, is more recommended.

- We could add target="\_blank" as an attribute-value pair inside the `<a>` label so that the link would be opened in new tab.

- `<header>`(header of the html doc/smaller units), `<nav>`(for navigation links), `<article>`, `<footer>`(e.g., copyright), `<aside>`(for secondary info) are container labels for structuring html documents. They would be helpful for semantics HTML as well as CSS styling.

- useful VScode extension: auto rename tag(automatically change the closing tags when the openning tags were changed), prettier(formatter), color hightlight(for css), image preview(`<img>`), live server

## CSS Notes

#### Dec 19 2022

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

#### Dec 21 2022

- **CSS Theory1: conlicting selectors**
  - declarations marked `!important` > inline styles > ID selector > class/psudeo-class selector > element selector > universal selector
  - if there are multiple conflicts of the same level, the last selector in code will apply
