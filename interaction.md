# Active state of interactive elements

Phonegap Boilerplate provide a way to add a *clicked* state on interactive
elements via the __data-clickable__ attribute.

When a user click on a clickable element, this element state become "clicked".

This state is useful to show to a user that an action has been taken into account.

### Usage

```html
<!-- Add the data-clickable attribute to your element -->
<a href="" data-clickable="" src="http://source.tld">My link</a>
```

```css
/* And style the "clicked" state */
a[data-clickable="clicked"] {
    color: red;
}
```

```js
// Later, you can remove the clicked state with jQuery
$('a[data-clickable="clicked"]').attr('data-clickable', '');
```
