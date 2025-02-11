---
title: "2: Responsive Design"
weight: 10
---



# Responsive Design 

In this lab, you will learn how to differentiate CSS for mobile viewing and continue exploring CSS design properties. 

---

## [0] Set up



{{< code-action "Start by cloning your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
cd ~/desktop/making_with_code/cs10/unit01_webdesign
git clone https://github.com/the-isf-academy/lab_responsive_design_yourgithubusername
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_responsive_design_yourgithubusername
```

📄 **This repo contains the following:**
- `index.html`
- `styles.css`
- `assets/` - contains 1 images
- `README.md`

{{< code-action >}} **Start by openning the repo in VS code and opening the `index.html` page.**
```shell
code .
open index.html
```

{{< figure src="images/courses/cs10/unit01/02_responsive_8.png" width="75%" >}}


---

## [0] Mobile Queries

{{< code-action >}} **Let's start by resizing the window.** As you resize the window, the content on the site does not get adjusted for the phone. The buttons are no longer visible and some of the text is mis-aligned. 

{{< figure src="images/courses/cs10/unit01/02_responsive_10.png" width="25%" >}}



💻 **First, let's look at the media query at the bottom of the `styles.css` file.** 
> Media queries change the CSS properties for specific screen sizes 

- *learn more [here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)*

```css
/* FOR SCREEN SIZE SMALLER THAN 767 PX */

@media (max-width: 767px) {
    .container {
        display: block;
        margin-top: 0px;
    }
}
```
- by defining css rules inside the media query, you can overwrite specific properties
- by changing `display: block` to `display: flex`, this forces the items to stack on top of each other

💻 **Let's change our `display` property to `block` instead of `flex`, so the content to stack on top of each other, instead of side by side.** It's looking better!

{{< figure src="images/courses/cs10/unit01/02_responsive_11.png" width="25%" >}}


💻 **Now, it's up to you to edit the exisitng CSS rules and add more specific CSS rules in the media query!** Try to match the screenshots below. 
> *Don't forget to scroll to the bottom and check the 'back to the top' text*
- You must:
    - add additional properties to the `.container` rule
    - create new rules for html elements in the media query

{{< columns >}}
{{< figure src="images/courses/cs10/unit01/02_responsive_2.png" width="50%" >}}
<--->
{{< figure src="images/courses/cs10/unit01/02_responsive_4.png" width="75%" >}}

{{< /columns >}}


---

## [1] Customizing the Site

Now that the mobile looks better, let's improve the site!

---

### [Internal Links]

You can link to an internal part of your site by setting an `id` to an `HTML` element. 

💻 **Try clicking on the `about` link.** It jumps you to the about section of the page. But, the `contact me!` and `meow` buttons are broken. 

{{< figure src="images/courses/cs10/unit01/02_responsive_5.png" width="25%" >}}

📖 **This is the `HTML` code for the link. It's `href` points to the `id` of the about section.**

```html
<a class="border-box" href="#about">about</a>
```

📖 **This is the `HTML` code for the `<h2>` section heading.**

```html
<h2 id="about">about</h2>
```

💻 **Fix the links for the `contact me!` and `meow` buttons so they jump you to the correct part of the site.**

---

💻 **Try clicking on the `back to top` link.** It should jump you to top of the page, but it currently doesn't work.


{{< figure src="images/courses/cs10/unit01/02_responsive_9.png" width="25%" >}}

💻 **Fix the link by refering th reference link to `"#"`** The single hashtag represents the top of the page.


---

### [Gradients]

💻 **Experiment with CSS graidents at [cssgradient.io](https://cssgradient.io/)**


💻 **When you find one you like, copy the `linear-gradient`**

{{< figure src="images/courses/cs10/unit01/02_responsive_6.png" width="75%" >}}

💻 **Paste it into the top of your `styles.css` and replace the current `--bg-graident` value**
> *These are `CSS` variables, which allow you to more quickly retheme your site - learn more [here](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)*
```css
:root {
    --bg-gradient: radial-gradient(circle, rgba(44,55,111,1) 46%, rgba(87,26,70,1) 100%);
    --border-gradient: linear-gradient(to right, rgb(193, 193, 237), rgb(234, 193, 255)) 1;
    --color1: white;
    --color2: rgb(67, 77, 131);
    --color3: rgb(93, 102, 148);
}
```

💻 **Experiment with the other variables and change the theme to *light mode*.**

{{< figure src="images/courses/cs10/unit01/02_responsive_7.png" width="75%" >}}

---

### [Animations]

📖 **For simple animations, we will use the `Animate.css` library: [animate.style](https://animate.style/)**

You can see an example of an animation when you refresh the site, the `👋 Hi I'm a cat` flips in from the top of the screen.

```css
h1{
    animation: flipInX;
    animation-duration: 1s;
}
```

💻 **Customize your site by adding more animations!** When adding an animation to the CSs properties, it MUST include the `animation` and `animation-duration` properties.
- view the animation options by clicking the options at [animate.style](https://animate.style/)
- experiment with animations when you hover an element

---

## [2] Deliverables

{{< deliverables "Once you've successfully completed the lab:" >}}  


{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}





## [3] Extension: CSS  

💻 **Experiment with UX/UI design by customizing this site!** This is one of the last practice labs before your make your own site, so us this as opportunity to test ideas. 

