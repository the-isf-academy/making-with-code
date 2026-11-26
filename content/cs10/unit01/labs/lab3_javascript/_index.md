---
title: "3: Javascript"
weight: 10
# draft: true
---

# Javascript

**In this lab, it is up to you to recreate our website!** Through the process you will practice HTML/CSS and learn a bit of Javascript. 

{{< figure src="images/courses/cs10/unit01/03_js_1.png" width="100%" >}}


---

## [0] Set up



{{< code-action "Start by cloning your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
cd ~/desktop/making_with_code/unit04_webdesign
git clone https://github.com/the-isf-academy/lab_javascript_yourgithubusername
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_javascript_yourgithubusername
```


{{< code-action >}} **Start by openning the repo in VS code and running the live server on the `index.html` page.**
```shell
code .
```

---

## [0] Structure of Website

💻 **Start by creating the layout of the site.** It should have:
- header banner with "Making with Code"
- sidebar with links
- main content 
- footer `<footer>`

At this stage, it should just be able the layout, focusing on the placement of content and creating the 2 main columns. 

{{< figure src="images/courses/cs10/unit01/03_js_5.png" width="50%" >}}


{{< expand "If you want a hint, here is the start HTML and CSS for the basic layout" >}}

```html
<div class="header">
      <h1><a href="/">Making with Code</a></h1>
    </div>

    <div class="main">
      <div class="sidebar">
        <a>Link 0</a>
        <a>Link 1</a>
      </div>

      <div class="content">
        <h1>Content Header</h1>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam posuere velit ac commodo blandit. Nulla facilisi. Sed egestas suscipit lectus, et suscipit mi faucibus et. Nunc commodo dolor ante, vel facilisis nisl placerat sed. Maecenas efficitur, mauris non faucibus vehicula, nulla magna viverra diam, eget pulvinar velit enim ut urna. Quisque lacinia tortor libero, at auctor urna gravida non. Quisque ornare nec ante ac rutrum. Aliquam aliquet vehicula erat in volutpat. Aenean quis suscipit nulla, eu scelerisque odio. Nulla id justo vitae libero tempor imperdiet id nec nunc. Mauris ornare, sapien et efficitur iaculis, sem lorem lobortis enim, quis euismod est arcu vitae ligula. Donec malesuada porttitor purus id gravida. Donec porta, elit sit amet condimentum tincidunt, lacus dolor feugiat diam, vel lacinia diam nisi eu mauris.</p>
      </div>


    </div>

    <footer><p>Created by you!</p></footer>
```

```css
a, p, h1, h2{
    margin: 0;
    text-decoration: none;
}

.main{
    display: flex;
    flex: 1
}
```
{{< /expand >}}


💻 **Create the functionality of the navigation bar and link it to a new page.** To create a new page, just create a new `html` file. The `href` should just point to the new filename. 

---


## [1] Re-usable HTML Elements

Now that you have a working site and two pages, you may be realizing that there's components of the page that are re-used. Like the header banner, side navigation bar, and the footer. 

**We can use `javascript` to create custom HTML elements, so we don't have to copy/paste code.**

📖 **Here is an example of creating a custom HTML element in `script.js`**

```javascript{linenos=table}
class SiteHeader extends HTMLElement {
  connectedCallback() {
    this.innerHTML = `
      <div class="header">
        <h1><a href="/">Making with Code</a></h1>
      </div>
    `;
  }
}

customElements.define('site-header', SiteHeader);
```

You do NOT need to understand each line. Just understand these pieces:
- `line 1 and 11` - `SiteHeader` is the custom name in Javascript. It should have a capital first letter.  
- `lines 4-7` - the string inside `this.innerHTML` is where you define your custom element 
- `line 11` - defines a new HTML element `site-header`. It must be all lowercase.

📖 **You can then use your `site-header` element in the HTML files.**
```html
<site-header></site-header>
```


💻 **Create new Javascript Classes for the Header, Footer, and Navigation Sidebar.** Then, add them to your 2 pages. 


---

### Navigation Highlighting

A common feature of websites is to highlight the current page in the navigation.

💻 **Add this code snippet within your `class SiteNavbar` in `script.js`**

```javascript
const currentPath = window.location.pathname;
    this.querySelectorAll('a').forEach((link) => {
        if (link.getAttribute('href') === currentPath) {
            link.classList.add('active');
      }
    });
```

Let's unpack what the different parts of it mean using the javascript console. 
**Just like in Python, it is super useful to print out information in Javascript. For that, we use `console.log()`.**

For example:
```javascript
console.log(currentPath)
```

💻 **To open the log, right click the site and select `Inspect` > `Console`.**


💻 **Refresh the page and look at the log.** This is the path of the page you are on. Try going to another page. What is in the log?

```shell
/index.html
```

💻 **Use `console.log()` to understand how the loop is working.** Where should you put these commands? 
```javascript
console.log(link)
console.log(link.getAttribute('href'))
```

💻 **As you click around different pages, look at the `Inspect` > `Elements` and look at how the `active` class gets applied to the current link within the navigation.**

{{< figure src="images/courses/cs10/unit01/03_js_0.png" width="75%" >}}


💻 **Add a new CSS rule for the `active` class in `styles.css`, so you can tell which page is active.**


{{< figure src="images/courses/cs10/unit01/03_js_2.png" width="25%" >}}

---

## [2] Button Functions

A common use of functions in Javascript is to trigger effects after a button press. On class website, we have use this for our expand boxes. We are going to recreate it!

{{< expand "Example Expand Box" >}}

Reveled text. 

{{< /expand >}}

💻 **Copy & Paste this `button` into `index.html`.** HTML buttons have a built in attribute `onclick` to trigger Javscript functions.
```html
<button onclick="expand()">⬇️ Click to open</button>
```


💻 **Copy & Paste this `div` into `index.html`.** This will be shown or hidden when the button is clicked.
```html
<div class="expand-div">
    <p>Here is the expanded text.</p>
</div>
```

💻 **Copy & Paste the start of the `expand()` function into `script.js`.**

```javascript{linenos=table}
function expand() {
    const expandDiv = document.querySelector(".expand-div");
    const expandedDivStyle = window.getComputedStyle(expandDiv);

    console.log(expandedDivStyle.display) 
}
```
- `const` is a type of Javascript variable 
- `line 2` - creates a variable that stores the HTML element with the class `expand-div`. 
- `line 3` - creates a variable that stores its CSS style with `window.getComputedStyle()`
- `line 5` - prints to the console the element's display 


💻 **Reference this is an example of conditional statements in javascript to create the toggle behavior.**

```javascript
const isLoggedIn = false;

if (isLoggedIn == true) {
  console.log("Welcome back!");
} else {
  console.log("Please log in.");
}
```

💻 **Change the text of the button based on the status.** Reference the below example to change the text of the button. You will need to consider how you get the button.
```javascript
button.textContent = "⬇️ Click to open"
```


💻 **Style is nicely in `styles.css`** 

{{< figure src="images/courses/cs10/unit01/03_js_3.png" width="100%" >}}

{{< figure src="images/courses/cs10/unit01/03_js_4.png" width="100%" >}}


---


## [3] Deliverables

{{< deliverables "Once you've successfully completed the lab:" >}}  


{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---

## [4] Extensions

Add in other features from our site. For each of these, you should create a custom class so you can easily re-use them.

### Aside 

{{< aside "Aside" >}}
Text goes inside. 
There is a left darker boarder. 

Notice, the "deliverables" block is similar, but with different colors. Try creating custom `#ids` for different color schemes.
{{< /aside >}}

### Code Blocks

```shell
// code blocks
The background is darker. There is a rounded edge. The font changes. 
```

### Dark Mode

Click a button to toggle the color scheme from light mode to dark mode. 
