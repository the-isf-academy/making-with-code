---
title: "HTML/CSS Tips" 
draft: true
---
<style>

/* FOR CSS INTRO */

h1.css_intro{
  color: pink;
  text-decoration: underline;
}



/* FOR FLEX BOX */

.centered_content{
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(200, 243, 203);
}

.flexbox-grid{
    display:flex;
    gap: 20px;
}

.column{
    background-color: rgb(255, 243, 203);
    padding: 0px 20px;
    flex: 1;
}


#col-large{
    background-color: rgb(255, 216, 216);
    flex-grow: 3; 
}



/* FOR MOBILE SCREEN SIZE */

@media only screen and (max-width: 768px) {


    .flexbox-grid {
        display: block;
      }

    .column{
        margin: 10px;
        padding: 10px 10px; 
    }

}
</style>

# HTML/CSS Tips

This page is dedicated to HTML and CSS tips. Let the teachers know if you would like us to add any content. 

---

## CSS Cheat Sheets


{{< figure src="https://miro.medium.com/v2/resize:fit:600/1*OFsc0SD55jhi8cjo7aCA4w.jpeg" width="40%" >}}

🔗 **Here are a few helpful links to reference CSS properties:**
- [CSS Properties Cheat Sheet](https://web.stanford.edu/group/csp/cs21/csscheatsheet.pdf)
- [CSS Interactive Cheat Sheet](https://htmlcheatsheet.com/css/)
- [Mozzila CSS Tutorials](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [w3 CSS wiki](https://www.w3schools.com/css/css_intro.asp)

---

## CSS Challenges

{{< figure src="https://upload.wikimedia.org/wikipedia/commons/9/9a/CodePen_logo.png" width="40%" >}}


🔗 **Here are solutions to the CSS Challenges on Codepen:**
- [challenge 1](https://codepen.io/eqbrown/pen/bGZEZap)
- [challenge 2](https://codepen.io/eqbrown/details/KKEzrYW)

---


## Flexbox Guide

💡 **The `display: flex` property is an incredibly useful `CSS` property to apply flexible and layouts.** It can be used to create responsive layouts and side-by-side content. 

📖 **Here are two helpful resources for using a `flexbox`**
- [flexbox guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [flexbox grid tutorial](https://kevinsguides.com/guides/webdev/css/creating-a-simple-flexbox-grid)

---

### [Centering Content Vertically]

**We often want content to be centered vertically and horizontally in a box.**
> 💻 *Try resizing the browser window - notice how the box is *responsive* and resizes depending on the screen size.*


<div class="centered_content">
    <p>Hello, World</p>
</div>

👀 **This is the `html` code for the columns above.** 
> *learn more about using a Class [here](https://blog.hubspot.com/website/what-is-css-class)*
```html
<div class="centered_content">
    <p>Hello, World</p>
</div>
```


👀 **This is the `css` for the two classes: `center_example-grid`.** 
> *learn more `flex` and `flexbox` properties [here](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)*
```css
.centered_content{
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(200, 243, 203);
}
```
> the `.` before the `centered_content` name, tell the CSS to select the HTML element with that `class` name

---

### [Equally Sized Columns]

**We often want content size-by-side in two equally sized columns.**

> 💻 *Try resizing the browser window - notice how the boxes are *responsive* and resize and rearrange depending on the screen size.*
>
> *The background color is not required - it is just used here to illustrate the different columns*

<div class="flexbox-grid" >
  <div class="column"">
    <h3>column</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
  </div>

  <div class="column" >
    <h3>column</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. </p>
  </div>
</div>


👀 **This is the `html` code for the columns above.** 

```html
<div class="flexbox-grid" >
  <div class="column"">
    <h3>column</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
  </div>

  <div class="column" >
    <h3>column</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. </p>
  </div>
</div>
```

👀 **This is the `css` for the two classes: `flexbox-grid` and `column` grid.** 

```css
.flexbox-grid{
    display: flex;
    gap: 20px; 
}

.column{
    background-color: rgb(255, 243, 203);
    padding: 0px 20px;
    flex: 1;
}
```

---


### [Unevenly Sized Columns]

**What if we want content size-by-side in two un-equally sized columns?**

> 💻 *Try resizing the browser window - notice how the boxes are *responsive* and maintain the relative size ratio. They also stack if the window is too small.*
>
> *The background colors are not required - it is just used here to illustrate the different columns*

<div class="flexbox-grid">
  <div class="column">
    <h3>column 1</h3>
    <p>Suspendisse luctus dapibus consequat.</p>
  </div>

  <div class="column" id="col-large">
    <h3>column 3</h3>
    <p>Vivamus pellentesque molestie odio, eu porttitor dui pharetra id. Nunc tempus tristique tortor, sit amet pellentesque magna accumsan sed. Nullam posuere nunc eu libero rutrum sodales. Duis congue scelerisque odio eu suscipit. Nunc at ligula non libero viverra dapibus. In sit amet lacinia odio.</p>
  </div>
</div>

👀 **This is the `html` code for the columns above.** 

```html
<div class="flexbox-grid">
  <div class="column">
    <h3>column 1</h3>
    <p>Suspendisse luctus dapibus consequat.</p>
  </div>

  <div class="column" id="col-large">
    <h3>column 2</h3>
    <p>Vivamus pellentesque molestie odio, eu porttitor dui pharetra id. Nunc tempus tristique tortor, sit amet pellentesque magna accumsan sed. Nullam posuere nunc eu libero rutrum sodales. Duis congue scelerisque odio eu suscipit. Nunc at ligula non libero viverra dapibus. In sit amet lacinia odio.</p>
  </div>
</div>
```

👀 **This is the `css` for the two classes: `flexbox-grid` and `column` grid.** *Notice, it uses two of the same `CSS classes`, `flexbox-grid` and `columns` and the example above.*

```css
.flexbox-grid{
    display:flex;
    gap: 20px; 
}

.column{
    background-color: rgb(255, 243, 203);
    padding: 0px 20px;
    flex: 1;
}

#col-large{
    background-color: rgb(255, 216, 216);
    flex-grow: 3; 
}
```
> - `#` - is used to apply rules to a `CSS ID`
> - **`flex-grow`** - this makes `col-2` 3x as big

<!-- 
---


### [Responsive Design: Mobile Friendly]

📱**It is important for websites to be viewable and readable on different sized screens - like on a phone**. 

👀 **This is the `css` applied to the `divs` in the two examples.** 

```css
/* FOR MOBILE SCREEN SIZE */

@media only screen and (max-width: 768px) {

    .flexbox-grid {
        display: block;
      }

    .column{
        margin: 10px;
        padding: 10px 10px; 
    }

}
```
> - **`@media only screen and (max-width: 768px)`** - this applies different `CSS` properties for the two classes, `flexbox-grid` and `column`, when the window is at a specific screen size
- `/* FOR MOBILE SCREEN SIZE */` - is a comment, just like the `#` for comments in Python 
  - You can learn more about `media queries` [HERE](https://www.w3schools.com/css/css_rwd_mediaqueries.asp). -->