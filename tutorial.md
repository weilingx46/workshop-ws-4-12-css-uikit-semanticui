# UIkit Workshop: Tutorial
### CS 52, Spring 2018
### 04/12/2018

## Grid

## Navbar, Customizer


## Adding an Image Slideshow with Navigation Buttons
Let's make the webpage look better by adding a slideshow!

To start, we need to link one CSS file and two JS files. Insert the following line into your `<head>`:
```html
<link rel="stylesheet" href="uikit/css/components/slideshow.css" />
```
and the following two lines at the end of your `<body>`:
```html
<script src="uikit/js/components/slideshow.min.js"></script>
<script src="uikit/js/components/slideshow-fx.min.js"></script>
```
`slideshow-fx.min.js` isn't strictly necessary, but it enables some nice transitions which make the slideshow look classier.

Now we're ready to start! We'll begin with a basic slideshow and add functionality as we go.

With UiKit, slideshows are  unordered lists with `class="uk-slideshow"`. Let's try making one by inserting the following snippet into your `<body>`:
```html
<ul class="uk-slideshow" data-uk-slideshow>
  <li> <img src="img/slide-1.jpg" alt="test" uk-cover> </li>
  <li> <img src="img/slide-2.jpg" alt="test" uk-cover> </li>
  <li> <img src="img/slide-3.jpg" alt="test" uk-cover> </li>
</ul>
```
Note that `data-uk-slideshow` must be included in order to load the necessary JavaScript.

Take a look! You should see a single image that isn't changing. Since we have no navigation buttons, there's also no way to change that image. Annoying.

![slideshow-bare](tutorial-screenshots/slideshow.png)

If you don't want to have any buttons, but want the slideshow to autoplay, replace `data-uk-slideshow` in the `<ul>` tag with `data-uk-slideshow="{autoplay:true}"`. Now, the slideshow should autoplay.

Navigation buttons would still be nice, though. To add navigation buttons, we'll need to create a `<div>` that holds both the slideshow `<ul>` and the buttons. We'll start by
adding previous and next image buttons. Modify your current slideshow HTML to look like the following:
```html
<div class="uk-slidenav-position" data-uk-slideshow="{autoplay:true}">
  <ul class="uk-slideshow">
    <li> <img src="img/slide-1.jpg" alt="test" uk-cover> </li>
    <li> <img src="img/slide-2.jpg" alt="test" uk-cover> </li>
    <li> <img src="img/slide-3.jpg" alt="test" uk-cover> </li>
  </ul>
  <a href="" class="uk-slidenav uk-slidenav-contrast uk-slidenav-previous" data-uk-slideshow-item="previous"></a>
  <a href="" class="uk-slidenav uk-slidenav-contrast uk-slidenav-next" data-uk-slideshow-item="next"></a>
</div>
```

Note that the `data-uk-slideshow` must be moved to the `<div>` tag because the JavaScript needs to be loaded for the buttons as well.

With UiKit, these navigation buttons are hyperlinks with `class="uk-slidenav uk-slidenav-contrast uk-slidenav-[previous | next]"`. There's no need to put an actual link inside the `href` term.

The page should look something like this:

![slideshow-arrows](tutorial-screenshots/slideshow-arrows.png)

Now, you'll be able to navigate back and forth between images. But what if we want to skip to a particular image? We can insert a dotnav component to add this functionality. The dotnav menu is an unordered list with `class="uk-dotnav"`. We recommend using `class="uk-dotnav uk-dotnav-contrast uk-position-bottom uk-flex-center"` as well to make it look better. Each dot is a `<li>` element, where `data-uk-slideshow-item` indicates which slideshow image the dot will link to. Note that the numbers for `data-uk-slideshow-item` are zero-indexed and correspond directly to the order in which the images appear in your original slideshow `<ul>`. You could play around with these indices if you wanted (e.g. set everything to reference image 0), but that doesn't seem very productive...
```html
<div class="uk-slidenav-position" data-uk-slideshow="{autoplay:true}">
  <ul class="uk-slideshow">
    <li> <img src="img/slide-1.jpg" alt="test" uk-cover> </li>
    <li> <img src="img/slide-2.jpg" alt="test" uk-cover> </li>
    <li> <img src="img/slide-3.jpg" alt="test" uk-cover> </li>
  </ul>
  <a href="" class="uk-slidenav uk-slidenav-contrast uk-slidenav-previous" data-uk-slideshow-item="previous"></a>
  <a href="" class="uk-slidenav uk-slidenav-contrast uk-slidenav-next" data-uk-slideshow-item="next"></a>
  <ul class="uk-dotnav uk-dotnav-contrast uk-position-bottom uk-flex-center">
    <li data-uk-slideshow-item="0"><a href=""></a></li>
    <li data-uk-slideshow-item="1"><a href=""></a></li>
    <li data-uk-slideshow-item="2"><a href=""></a></li>
  </ul>
</div>
```

You should get something that looks like this:
![slideshow-dots](tutorial-screenshots/slideshow-dots.png)

Hooray! You've created an image slideshow with elegant navigation buttons.
