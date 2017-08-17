# 质量规范 Vue

* **使用单文件组件 (single-file-components)**

```html
<template>
  <div>This is ok</div>
</template>

<script>
export default {

}
</script>
```

* **采用自闭合风格的标签 (self-closed)**

```html
<!-- Bad -->
<foo></foo>

<!-- Bad -->
<foo>

<!-- Bad -->
<foo/>

<!-- Good -->
<foo />
```

* **模板内组件名和属性使用短横线风格 (kebab-case)**

```html
<!-- Bad -->
<MyComponent myProps="foo" />

<!-- Good -->
<my-component my-props="foo" />
```

* **多属性标签风格 (multi-props-styles)**

```html
<!-- bad -->
<foo foo="a" bar="b"/>

<!-- bad -->
<foo foo="a"
  bar="b" />

<!-- ok -->
<foo foo="a" bar="b" />

<!-- ok -->
<foo
  foo="a"
  bar="b"
/>

<!-- best -->
<foo
  foo="a"
  bar="b" />

<!-- bad -->
<foo
  foo="a"
  bar="b">text
</foo>

<!-- bad -->
<foo
  foo="a"
  bar="b">
text</foo>

<!-- ok -->
<foo
  foo="a"
  bar="b"
>text</foo>

<!-- ok -->
<foo
  foo="a"
  bar="b"
>
  text
</foo>

<!-- best -->
<foo
  foo="a"
  bar="b">
  text
</foo>
```

* **模板绑定的 {{ }} 与变量间有空格 (space-between-brackets-and-var)**
```html
<!-- Bad -->
<div>{{data}}</div>

<!-- Good -->
<div>{{ data }}</div>
```

* **不使用js的字符串模板拼接动态数据 (no-js-template)**
```html
<!-- Bad -->
<div>
  {{ `pay for ${price}` }}
</div>

<!-- Good -->
<div>
  pay for {{ price }}
</div>
```

* **v-for属性 (v-for)**
```html
<!-- Bad -->
<foo v-for="item in list" />

<!-- Bad -->
<foo
  v-for="item in list"
  v-if="showList" />

<!-- Good -->
<template v-if="showList">
  <foo
    v-for="item in list"
    :key="item.id" />
</template>
```

* **属性顺序 (order-of-props)**
```html
<!-- recommended -->
<!-- '|' means you can only use one of them -->
<!-- '/' means you can order them as you like -->
<foo
  v-for | v-if | v-else
  @click
  key
  ref
  v-*
  class / style
  value-props / handler-props
/>

```

* **不在模板中使用this (no-this-in-template)**
```html
<!-- Bad -->
<foo :name="this.name" />

<!-- Good -->
<foo :name="name" />

<script>
export default {
  data() {
    return { name: 'bar' }
  }
}
</script>
```

* **不宜直接将整个对象传入组件 (config-destruction)**
```html
<!-- Bad -->
<foo :obj="obj" />

<!-- Good -->
<foo
  :id="obj.id"
  :name="obj.name"
  :value="obj.value" />
```

* **给组件的属性赋予初始值 (props-default-value)**
```html
<template>
  <div>Hello, {{ name }}</div>
</template>
<script>
export default {
  props: {
    name: {
      type: String,
      default() { return 'Guest' },
    },
  },
}

</script>
```

* **尽量避免使用this.$refs与this.$parent实现组件通信 (avoid-refs-and-parent)**

```javascript
// bad
export default {
  methods: {
    this.$refs.modal.open()
  },
}
```


* **组件内属性的顺序 (order-in-components)**
```javascript
// just recommend
export default {
  name: 'Component',

  components: {},

  props: {},
  mixins: {},
  extends: {},


  data() {},
  computed: {},
  filters: {},

  methods: {},
  watch: {},

  mounted() {},
  destroyed() {},
}


// and you can put some lifecycle hooks before the 'data', because of logical reasons, like:
export default {
  mounted() {},
  // because we are extremely concerned about what the component will do when mounted

  data() {},
  computed: {},

  destroyed() {},
}

```

* **不在模板中引入复杂逻辑 (simple-logic-in -template)**
```html
<!-- Bad -->
<template>
  <div>
    Time is {{ hour }}:{{ minute }}:{{ second }}
  </div>
</template>

<!-- Good -->
<template>
  <div>
    Time is {{ time }}
  </div>
</template>

<script>
export default {
  computed: {
    time() {
      return `${hour}:${minute}:${second}`
    },
  },
}
</script>
```

* **不要混用 filter、computed、methods (good-use-of-fcm)**
```javascript
// filter: The data is ready to show, but it won't be shown to UI by raw, may be formatted.

// computed: Computing data for avoiding describing complex logic repeatedly (especially complex logic in template).

// methods: Other functions and handlers, and params-needed 'computed'.
```

### 参考

* [vuelint-guide](https://github.com/seraphimrose/vuelint-guide)
