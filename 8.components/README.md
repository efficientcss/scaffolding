# Components

Pretty much what standard components are thought to be, albeit with a narrower focus.

Should contain content and structure. Should be autonomous and standalone. `with-style`, `as-forms` utilities should not be used on components. State based classes are accepted.

All child classes must be prefixed like `__container`. These kinds of classes are always namespaced, never global so they can be used anywhere without worrying about leaks.

For example, a `.card` should or could display titles, links, images, etc. A certain structure for these elements is expected. This structure should be enforced and reinforced, notably by using it in CSS. That way, changes to its HTML structure won't be made on whiff.

Following in this line of thinking, CSS should be as close as possible to the components main file. We therefore strongly encourage the use of `<link>` tags inside components as loading mechanism and straight path to associated CSS.

For example:

```html

<div class="as-grid with-broad-gutter and-large-padding">
    <article class="card">
        <link rel="stylesheet" href="/assets/ecss/8.components/card.css">
        <header class="as-content-over-image">
            <h1>Vive ECSS !</h1>
            <img src="image.webp" alt="An example image">
        </header>
        <div>
            <small class="tag">Nouvelles</small>
            <p>Ipsum quibusdam culpa deserunt provident libero Quis quisquam eius enim.</p>
            <a class="button" href="#">Plus !</a>
        </div>
    </article>
    ...
</div>

```

The advantages a numerous.

- Drastically reduce the possibility of growing unused CSS being shipped to the browser.
- Render performance increased by the JIT nature of the approach.
- One build step less.
- Optimized for HTTP/3
- Clearer & simpler debugging in the devtools.
