# Ember-sidebars

This addon makes it easy to manage sidebars, toolbars, or any piece of DOM that you want to lift outside your normal route hiearchy.

It is similar to [ember-wormhole](https://github.com/yapplabs/ember-wormhole), but is more suitable when your target is your own Ember component (as opposed to arbitrary, potentially foreign DOM).

The best documentation is the sample application in `tests/dummy`, which is also running at [http://ef4.github.io/ember-sidebars/](http://ef4.github.io/ember-sidebars/).

## Components

Create a sidebar named "my-right-sidebar":

```hbs
{{show-sidebar name="my-right-sidebar"}}
```

From elsewhere, declare which component should render in the sidebar -- complete with bound inputs and actions:


```hbs
{{in-sidebar name="my-right-sidebar" show=(component "cool-thing" model=model launch=(action "launchIt") }}
```

For fancier behaviors, you can use `{{#with-sidebar}}` instead of `{{show-sidebar}}` which gives you an opportunity to extend the sidebar's behavior in arbitrary ways. For example, this lets your sidebar animate as its content changes:

```hbs
{{#with-sidebar name="my-right-sidebar" as |sidebar|}}
  <div class="topbar">
    {{#liquid-bind sidebar as |currentSidebar|}}
      {{component currentSidebar}}
    {{/liquid-bind}}
  </div>
{{/with-sidebar}}
```


## Installation

* `git clone` this repository
* `npm install`
* `bower install`

## Running

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `npm test` (Runs `ember try:testall` to test your addon against multiple Ember versions)
* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://www.ember-cli.com/](http://www.ember-cli.com/).
