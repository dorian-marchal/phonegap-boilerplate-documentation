# Active state of interactive elements

Phonegap Boilerplate provide a way to add a *clicked* state on interactive
elements via the __data-clickable__ attribute.

When a user click on a clickable element, this element state become "clicked".

This state is useful to show a user that their action has been taken into account.

### Usage

Add the data-clickable attribute to your element

```html
<a href="" data-clickable="" src="http://source.tld">My link</a>
```

And style the "clicked" state

```css
a[data-clickable="clicked"] {
    color: red;
}
```

Later, you can remove the clicked state with jQuery

```js
$('a[data-clickable="clicked"]').attr('data-clickable', '');
```

Alternately, you can use data-clickable=auto.
This way, the "clicked" state will stay for a while (less than a second) and then
be removed.

```html
<a href="" data-clickable="auto" src="http://source.tld">My link</a>
```
