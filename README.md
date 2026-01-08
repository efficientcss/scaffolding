# Scaffolding — ECSS Documentation

Every CSS in root directory has general application over following indexed files and directories.

A major objective here is to make the CSS clear & intelligible. We try to attain this objective by creating a class vocabulary akin to sentences. ECSS abstractions commit to this by using prefixes and general guidelines for naming.

For example, this block of ECSS styled HTML :

```html

<div class="as-grid with-broad-gutter and-large-padding">
    <article data-component="card">
        <header class="as-overlay">
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

Any item in here can & should use the custom properties provided by preceding ones. Notably language properties must be used for any visual task. If a needed property is absent it should be added.

Only from 3.language and down should modifications be made.

Every filename not beginning with a digit or `x-` is expected to namespace selectors, meaning every declaration block must begin with an exact reference to its filename. Classes, tags or attributes selectors are allowed.

For example, in `card.css` selectors are

`.card h1`
`.card p`
`[data-component="card"]`


## Guides

Use nesting where it conveys meaning. when two rules, even if inside child elements, are condition for one or the other don't use separate blocks, use nesting instead.

Design tokens inside language.css are not to be used with factors, or only exceptionally.

## Abstractions

Compositions

styles touching the main interface regions but in a mutual way. they touch multiple regions at the same time. layout only. Their names should be explicit about their purpose.

Some examples

- side-nav-main-pile 
- bottom-nav-sliding-content

Regions

Unique zones of the main interface. They should be simply named as we assume the « main » by it being a region. They layout their insides, without theming styles. Child selectors must be scoped and should be anonymous or ad hoc, without any reference to any outside abstraction, be it a utility or a component, for instance. 

Here are some simple and likely regions

- body
- main
- footer
- header
- aside

Components

Components should only be created after all other concepts have failed to (efficiently) render a particular interface piece. A component designs content from a data model, as opposed to compositions or utilities who mostly lay out slots for anonymous matter. A component should scarcely include other components. A component should be able to accommodate varying combinations of content. For instance, `card` should try to encompass alterations or variants via expressive selection and `._modifier` or child `.__classes`. Components themselves should not make use of utilities. But their children can.

```
.card {
    &._artist {
    }

    &.__container {
    }
}
```

Prefer content combination to the creation of modifiers and child classes. The objective is to limit code drift and pattern duplication.

Elements

Single or mostly flat tag elements and interface controls (buttons, inputs, etc.). Highly reusable but tightly coupled. Elements share lots of styles so prefer having them all in one file. If some element styles become complex (buttons and variants, for instance), they can get their own file.
