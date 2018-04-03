# @doc
* title nenb example - using vue as a package
* bodyTitle
* icon ../images/nenb-icon.png

[source file](../src/examples/using-vue-package.nenb.md)

Below is a data block, in toml format.  It will be used as the data used to
create the Vue object.  The `name` attribute is set to `myVueData`.

# @comment =====================================================================
# @comment data block in toml, to be used in the vue block below

```toml
message = "this message was generated by data"
```
* name myVueData
* showAll

Below is an `html` block with a `render` attribute set to `vue`, and a `data`
attribute set to `myVueData`.

* the `render` attribute specifies that this block should not be rendered by the
usual `html` renderer, but by the renderer `vue-ssr`, which will perform
server-side rendering with [vue server-side rendering](https://ssr.vuejs.org/en/).

* the `data` attribute specifies the name of the data to be used when creating
the Vue object

# @comment =====================================================================
# @comment vue block

```html
<div id="my-vue-app">
  You're going to love this: {{ message }}
</div>
```
* name myVueTemplate
* dataOnly
* showAll

```js
// const Vue = require('vue')
const Vue = require('vue/dist/vue.common.js')

Vue.config.devtools = true

var app = new Vue({
  el: '#my-vue-target-element',
  data: data.myVueData,
  template: data.myVueTemplate
})
```
* module
* showAll

```html
<div id="my-vue-target-element"></div>
```
* showAll

We've also embedded a `css` block to make the `div` pretty.

# @comment =====================================================================
# @comment some nice css

```css
#my-vue-app {
  font-size: 200%;
  margin: 1em;
  border: thin solid #DDD;
  border-radius: 1em;
  padding: 1em;
  background-color: #DFD;
}
```
* showAll