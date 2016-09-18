# Vue Pagination 2

Note: This package is for use with Vuejs 2.
For version 1 please use [v-pagination](https://www.npmjs.com/package/v-pagination) instead.

Simple, generic and non-intrusive pagination component for Vue.js version 2.
Presentation is based on bootstrap.

- [Dependencies](#dependencies)
- [Installation](#installation)
- [Usage](#usage)

# Dependencies

* Vue.js (>=2.0.0-rc.1). Required.
* Bootstrap (CSS). Optional.

# Installation

Compile the code using a module bundler, such as webpack or browserify, and the [vue jsx transform](https://github.com/vuejs/babel-plugin-transform-vue-jsx)

    npm install vue-pagination-2

import the script and the event bus:

    import VuePagination from 'vue-pagination-2';
    import bus from 'vue-pagination-2/src/bus'

# Usage

## Register the component(s)

    Vue.use(VuePagination)

HTML:

    <pagination for="some-entity" :records="500"></pagination>

props:

* `for` `string` `required` unique identifier for the component instance.
* `records` `number` `required` number of records
* `per-page` `number` `optional` records per page. Default: 25
* `chunk` `number` `optional` max pages per chunk. Default: 10
* `count-text` `string` `optional` total records text. Default: '{count} records'

When a page is selected an event will be dispatched, using the unique id for the component.
Listen to it on your bus and respond accordingly:

      bus.$on('vue-pagination::some-entity', function(page) {
          // display the relevant records using the page param
      });

# Programmatic Manipulation

To programmatically set the page apply a `ref` identifier to the component and use one of the following methods:

* `setPage(page)`
* `next()`
* `prev()`
* `nextChunk()`
* `prevChunk()`

All methods return `true` if the page is legal and was thus set, or `false` otherwise.

# Computed Properties

* `totalPages`
* `totalChunks`
* `currentChunk`
