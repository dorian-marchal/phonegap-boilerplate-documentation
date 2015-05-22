# Routing

*__Note :__ if you want more informations on router configuration, see the [router documentation](router.md)*

---

Default routing works this way :

```
Router
|
|- Detect #hash change (or first #hash, at init)
|- Store `controller`, `action` and `params` in
     the `route` property of the `globals` singleton.
|- Pass the request to the proper controller/action with given parameters
    following this route pattern : #controller/action/param1/param2/...
    By default, the 'index' action is used
v

Controller
|
|- Associate the relevant `Page` with its layout
|- Notify the layout that it must be rendered
v

Layout
|
|- `Layout.defaultOptions` properties are overriden by
     `Page.layoutOptions` if needed
|- Render with its `Page` and `subviews` in <section class="content">
v

PageSlider / Layout
|
|- Slide the AppLayout rendered element as a new page
v

Layout / Page
|
|- The new page is slided in :
|  -> newPage.beforeLoad()
|  -> newPage.render() : *Render the newPage in the DOM*
|  -> newPage.afterRender()
|  -> oldPage.beforeLeave()
|  *Actual page sliding transition*
|  -> newPage.afterLoad()
```

__Exemple :__

1. The route `/#/contact/show/14` is called.

   ```js
   // In the router :
   uses: [
       ContactController,
   ],
   ```

   ```js
   // In the ContactController :
   name: 'contact', // used in the route

   // At Controller init, a new Layout instance will be added to the
   // "layouts" Controller property
   useLayouts: [
       require('app/views/Layout'),
   ],

   // At Controller init, a new Show instance will be added to the
   // "pages" Controller property
   usePages: [
       require('app/views/Show'),
   ],

   // Pages in "layoutForPages" are automatically associated with
   // their layout. For example, here, this action is created :
   // ContactController.show: function() {
   //     this._loadPage(this.layouts.layout, this.pages.contactShow);
   // }
   // (Note that "layout" is the Layout name, and "contactShow", the Page name)
   layoutForPages: {
       show: {
           page: 'contactShow',
           layout: 'layout',
       }
   },
   ```

2. The router calls the method `ContactController.show(14)`

   In this case, the action parameter ( `14`) is useless, but the route params are also available in the `route` property of the `globals` singleton.
   Since it has not been overriden, the action do the following :
   - Set the content view of the layout with `layout.setPage()`
   - Render the layout : `layout.render()`
   - Slide the layout element as a new page : `pageSlider.slidePage(layout.$el)`
   - Delegate the layout and page events

3. `page.beforeLoad`

   The page.beforeLoad method is called with an object containing the action
   arguments and a page history string in parameters.
   For example, the route #contact/show/14 could call the method.

   ```js
   contactForm.beforeLoad({
       actionArguments: 14,
       history: 'forward'
   });
   ```

   `history` can be :
   - 'first' if the page is the first one slided
   - 'forward' if the page come from the right
   - 'back' if the page come from the left

4. The layout is rendered

   The layout, its subviews and the Page are rendered and the page is added to the DOM.

   You can read the [layout documentation, here](layout.md)

5. `page.afterRender`

   Just after the page has been added to the DOM, this method is called.

6. `previousPage.beforeLeave`

   Just before the actual sliding transition, `beforeLeave` is called.
   It can be useful to free some ressources.

7. `page.afterLoad`

   Once the transition end (or immediatly, if this is the first loaded page), the `page.afterLoad` method is called.
   This method is useful to execute some code after the rendering, without interrupting the transition.
