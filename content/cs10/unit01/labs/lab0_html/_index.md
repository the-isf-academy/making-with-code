---
title: "0: HTML"
weight: 10
# draft: false
---

# HTML Lab

In this lab, you will start learning to write `HTML` code! HTML defines the content and the structural elements of a web site.

{{< figure src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/HTML5_logo_and_wordmark.svg/800px-HTML5_logo_and_wordmark.svg.png" width="15%" >}}


---

## [0] Set up

We are now in the **Web Design** unit, so you'll need to make a new folder. 

{{< code-action  >}} **In the Terminal, go into your `making_with_code/cs10` folder, create a `unit04_webdesign` folder, `cd` into it.**

```shell
cd ~/desktop/making_with_code
mkdir unit04_webdesign
cd unit04_webdesign
```


{{< code-action >}} **Then, clone your starter code and `cd` into the lab**
Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_html_yourgithubusername
cd lab_html_yourgithubusername
```


{{< aside "No need for the Poetry shell" >}}

In this unit we will not be using Python, and so **we will NOT use the Poetry shell**.

Don't worry, we'll return to Python in the next unit - Web Apps :)

{{< /aside>}}



---

## [1] Your First Webpage


💻 **Let's start by openning `index.html` in your web browser:** `open index.html`. It should automatically open in your system's default web browser. 
> `index.html` is the most common name for the start page of a web site.

{{< figure src="images/courses/cs10/unit01/00_html_0.png" width="50%" >}}


💻 **Now let's look at the code, open the `lab_html` folder in your code editor**: `code .`

📄 **This repository has the following files:**
- `index.html` - you will write `HTML` here
- `assets/blackout_cake.jpeg` - this photo will go on your page
- `cake_recipe.txt` - recipe content information
-  `styles.css` - `CSS` style sheet 

💻 **It is up to you to create a webpage for a cake recipe, by using the information in `cake_recipe.txt`.** Be sure to include all of the key information to make the cake, but feel free to rearrange it or eliminate unnecessary words.

> It will be helpful to have the `index.html` and `cake_recipe.txt` files open side by side. Then you can easily copy specific recipe lines to the `html` file.

{{< figure src="images/courses/cs10/unit01/00_html_1.png" width="75%" >}}


💻 **Your `index.html` must include at least 1 instance of each structural HTML element.** You can find information on HTML elements/tags [HERE](https://www.w3schools.com/html/).

- [ ] div
- [ ] heading (h2, h3, or h4,)
- [ ] paragraph text
- [ ] image
- [ ] link
- [ ] italic text
- [ ] bold text
- [ ] ordered bullet points 
- [ ] unordered bullet points 

> 🔍 Google will be your best friend this unit! You can Google `html div` (or replace div with any other element) to quickly find relevant resources. 


💻 **As you edit `index.html`, **save** `⌘+s` the file and **refresh** `⌘+r`  the web browser.** This will allow you to see updates as you edit the code!
> Use `⌘+tab` to easily switch between VS Code and your web browser. This will save you a ton of time :)

{{< figure src="images/courses/cs10/unit01/00_html_2.png" width="75%" >}}





## [2] Deliverables

{{< deliverables "Once you've successfully completed the lab:" >}}  


☑️  **Fill out [this Google form](https://forms.gle/Xhyi9nk9E3GxJqmx6)**

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

--- 

## [3] Extension: CSS 

💻 **Add custom styling to your page by editing `styles.css`** - a few ideas:
- change the color of the sub-headings
- change the color of the link when you hover over it 
- use multiple fonts throughout the page (e.g. a different font for the title)
- add a roudned border box around a section of the page

📖 **Here are a few helpful resources for CSS.** *Though again, Google is often the most helpful for `html` and `css`*.
- [css styling for text color](https://www.w3schools.com/css/css_text.asp)
- [css styling for fonts](https://www.w3schools.com/css/css_font.asp)
- [css styling for links](https://www.w3schools.com/css/css_link.asp)
- [css styling for backgrounds](https://www.w3schools.com/css/css_background.asp)


---

#### CSS Layout 

CSS can be also be used to apply layout designs to your webpage. Can you get the image to be next to the intro text?


💻 **Add custom layout to your page by incorporating a `flexbox` layout.** 
- [Overview of `flexbox` styling](https://css-tricks.com/snippets/css/a-guide-to-flexbox/).
- [Guide of `flexbox` grid layout](https://css-tricks.com/dont-overthink-flexbox-grids/)


{{< figure src="images/courses/cs10/unit01/00_html_3.png" width="100%" >}}


