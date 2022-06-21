---
title: 'CSS Tricks'
description: 'CSS Common Tricks and New Features'
date: '2022-05-10'
slug: 'css-tricks'
categories:
  - Front-end Development
tags:
  - front-end development
---

## Responsive Web Design

### @media

@media is not a new feature, since Chrome supports it in the first version. It is especially useful for displaying different layouts on devices with different screen sizes. As it uses hardware information from devices, it raises security concerns about identifying a device. Browser may choose to return default values rather than actual information when users activate no-tracking mode.

```css
@media screen and (min-width: 900px) {
  .element {
    padding: 1rem;
  }
}
```

### flex

Sometimes fixed width and height are not the optimal solution for different devices, because their screen widths and heights are different. Therefore, let the browser decide will be a better option. To do this, we can set up max width, min width, [flex basis](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis), [flex grow](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow) and [flex shrink](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink). (Note that flex basis, flex grow and flex basis can be defined with [flex](https://developer.mozilla.org/en-US/docs/Web/CSS/flex) as a short-hand css property)

```css
.element {
  flex: 1 0 0px;
}
```

### Displaying Units

Generally, there are two catagories of displaying units, absolute units and relative units. The most commonly used absolute unit is px in web design and development. In relative units, vw / vh, em and rem are more popular. em is based on the font size of its parent and rem is based on the root font size. vw / vh is based on the viewport size. [Read More](https://elementor.com/help/whats-the-difference-between-px-em-rem-vw-and-vh/).  
They are useful for different scenarios, but it is recommended to use only one or two of them in the entire project to remain consistent.

## Mobile Device Adaption

### Consistent Experience on Different Devices

Using viewport width and viewport height is better than px because iOS devices and high-resolution Android Devices tend to have higher px width and px height, but the design process of the blueprint is for viewport. We can use PostCSS Plugins, to set up a basic device and then CSS px properties will be automatically converted to the viewport units.

### Displaying Color with Alpha Channel Properly

Android doesn't support 8-digit hex color, so it will simply omit the color property. CSS minimizers like esbuild minimizes the color to an 8-digit hex, and thus this is where they are in conflict. The solution I found is to set the minify syntax for CSS to false on esbuild.
