# vue-plain

Get plain object from vue getter/setter object.

## Install

- #### NPM

  npm install --save `vue-plain`

- #### CommonJS

  ``` js
  var plain = require('vue-plain')
  Vue.use(plain);
  ```

- #### `<script>` Include

  include `vue-plain.js` after `Vue.js`.

## Usage

``` js
let vm = new Vue({
    data: {
        a: {
            a1: 2,
            fn: function(){}
        },
        c: [1, 2, 3]
    }
});

console.log( Vue.plain(vm.a) );  
// { a: { a1: 2 } } 
// The function will be lose, but in general, you should not add function in Vue data

console.log( Vue.plain(vm.c) );  
// [1, 2, 3]
```

with prop.coerce

``` js
childComponent = {
    props: {
        obj: {
            type: Object, // or Array
            coerce (value) {
                return Vue.plain(value);
            }
        }
    },
    created () {
        // this change does not affect parentComponent.obj
        this.obj.a = 1;
    }
}
```