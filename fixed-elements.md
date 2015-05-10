# Fixed positioned elements

Elements in fixed position can be tricky with page sliding transitions.

To avoid flickering on transition when a page is scrolled, you need to make sure
of two things :

1. Using `PageSlider.js`

   Based on [PageSlider](https://github.com/ccoenraets/PageSlider),
   [PageSlider.js][page-slider] ensure that pages is always at 100% height so that
   scrolling don't produce jumps on page transitions.

   In order to allow scrolling in your pages with PageSlider.js, you must allow
   overflow scrolling on your child.

2. Using `data-fixed` attribute

   When the pages are sliding, children elements in fixed position don't follow
   their page. To prevent that, the trick is to set them in absolute positioning.

   The `data-fixed` attribute works just like that : add  `data-fixed="absolute"`
   on your fixed elements and they will follow their parent.

[page-slider]: https://github.com/dorian-marchal/page-slider
