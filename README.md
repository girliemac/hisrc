HiSRC
=====

### A simple jQuery plugin for adaptive images in responsive web design

A twist on the old school [`LOWSRC` `IMG` attribute](http://www.w3.org/TR/html5/obsolete.html#attr-img-lowsrc), which would render a lower file size image first while a larger file size image would appears in its place later. 

Back to the future, we set in the markup and leave the lower file size image.

However, if the HiSRC plugin detects fast network or high resolution, then a high resolution image takes the image's place.

How the HiSRC jQuery Plugin Works
=====

The browser loads the low-resolution image first with an old-fashion `IMG` `SRC` attribute.

Then the HiSRC jQuery plugin checks the resolution of the browser. 

If the browser resolution is wider than the default 640 pixels width, then the plugin overwrites the low-resolution image for the higher resolution image.

If the device pixel ratio is set, instead of the width, the plugin overwrites the image with the high resolution image. For example, if you set the mindpr: 2, the high-resolution image is displayed for the high pixel density screen with the pixel ratio of 2, such as Retina display.

However, if mobile bandwidth is detected (like 3G), the low-resolutions stay in place. 

Setting up
=====

Associate jQuery to your web document as well as the HiSRC plugin as well.

In this code example, jQuery is link to Google's CDN and the HiSRC plugin is in the same directory as the web document:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1/jquery.js"></script>
<script src="hisrc.js"></script>
```

Use basic jQuery to pick out which images should be HiSRC'd:

```html
$(document).ready(function(){
  $(".hisrc img").hisrc();
  $(".hisrc img+img").hisrc({ minwidth: 800 });
})
```

Or you can also set the mindpr (device ratio) for the high pixel density screens:
```html
$(document).ready(function(){
  $(".hisrc img").hisrc();
  $(".hisrc img+img").hisrc({ mindpr: 2 });
})
```

When you define the mindpr instead of width, any minwidth setting is ignored.




The high-resolution image links should be placed as the value of `data-hisrc` in the markup of your web page:



```html
<h1>HiSRC Images</h1>	
	<div class="hisrc">
		<img src="http://placehold.it/400x200.png" data-hisrc="http://placehold.it/640x200.png">
		<img src="http://placehold.it/400x200.png" data-hisrc="http://placehold.it/800x200.png">
	</div>

<h2>Regular images</h2>	
	<img src="http://placehold.it/400x200.png">
	<img src="http://placehold.it/400x200.png">
```

More Resources
=====

* Place images in background of HTML elements and set [`background-size: auto;`](http://caniuse.com/#search=background-size) to have them scale as the element resizes. 
* Use [vector based images](http://caniuse.com/#search=svg) for truly resizable images. 
* [Flashpix](http://en.wikipedia.org/wiki/FlashPix) image format that stores multiple resolution versions. 
* Do you need a more robust, server-side solution? Try 
[Responsive Images](https://github.com/filamentgroup/Responsive-Images). Requires PHP and editing `.htaccess` files

