### Image Width with sizes

What if the image won't be displayed at the full viewport width? Then you need something more than srcset, which assumes the image will be full viewport width.

Add a sizes attribute to the image with a media query and a vw value. srcset and sizes together tell the browser the natural width of the image, and how wide the image will be displayed relative to viewport width. Knowing the display width of the image and the widths of the image files available to it, the browser has the information it needs to download the image with the right resolution for its needs that is as small as possible. And it can make this choice early in the page load while the HTML is still being parsed.

### srcset with sizes Syntax

Here's an example:

```
<img  src="images/great_pic_800.jpg"
      sizes="(max-width: 400px) 100vw, (min-width: 401px) 50vw"
      srcset="images/great_pic_400.jpg 400w, images/great_pic_800.jpg 800w"
      alt="great picture">
```
      
sizes consists of comma separated mediaQuery width pairs. sizes tells the browser early in the load process that the image will be displayed at some width when the mediaQuery is hit.

In fact, if sizes is missing, the browser defaults sizes to 100vw, meaning that it expects the image will display at the full viewport width.

sizes gives the browser one more piece of information to ensure that it downloads the right image file based on the eventual display width of the image. Just to be clear, it does not actually resize the image - that's what CSS does.

In this example, the browser knows that the image will be full viewport width if the browser's viewport is 400px wide or less, and half viewport width if greater than 400px. It knows that it has two image options - one with a natural width of 400px and the other 800px.
