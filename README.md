# 代码规范

## 目录
- [格式规范](#格式规范)
- [质量规范React](#质量规范react)
- [质量规范Vue](#质量规范vue)

## 格式规范

* **使用两个空格**进行缩进。

  eslint: [`indent`](http://eslint.org/docs/rules/indent)

  ```js
  function hello (name) {
    console.log('hi', name)
  }
  ```

* 除需要转义的情况外，**字符串统一使用单引号**。

  eslint: [`quotes`](http://eslint.org/docs/rules/quotes)

  ```js
  console.log('hello there')
  $("<div class='box'>")
  ```

* **不要定义未使用的变量**。

  eslint: [`no-unused-vars`](http://eslint.org/docs/rules/no-unused-vars)

  ```js
  function myFunction () {
    var result = something()   // ✗ avoid
  }
  ```

* **关键字后面加空格**。

  eslint: [`keyword-spacing`](http://eslint.org/docs/rules/keyword-spacing)

  ```js
  if (condition) { ... }   // ✓ ok
  if(condition) { ... }    // ✗ avoid
  ```

* **函数声明时括号与函数名间加空格**。

  eslint: [`space-before-function-paren`](http://eslint.org/docs/rules/space-before-function-paren)

  ```js
  function name (arg) { ... }   // ✓ ok
  function name(arg) { ... }    // ✗ avoid

  run(function () { ... })      // ✓ ok
  run(function() { ... })       // ✗ avoid
  ```

* **始终使用** `===` 替代 `==`。<br>
  例外： `obj == null` 可以用来检查 `null || undefined`。

  eslint: [`eqeqeq`](http://eslint.org/docs/rules/eqeqeq)

  ```js
  if (name === 'John')   // ✓ ok
  if (name == 'John')    // ✗ avoid
  ```

  ```js
  if (name !== 'John')   // ✓ ok
  if (name != 'John')    // ✗ avoid
  ```

* **字符串拼接操作符 (Infix operators)** 之间要留空格。

  eslint: [`space-infix-ops`](http://eslint.org/docs/rules/space-infix-ops)

  ```js
  // ✓ ok
  var x = 2
  var message = 'hello, ' + name + '!'
  ```

  ```js
  // ✗ avoid
  var x=2
  var message = 'hello, '+name+'!'
  ```

* **逗号后面加空格**。

  eslint: [`comma-spacing`](http://eslint.org/docs/rules/comma-spacing)

  ```js
  // ✓ ok
  var list = [1, 2, 3, 4]
  function greet (name, options) { ... }
  ```

  ```js
  // ✗ avoid
  var list = [1,2,3,4]
  function greet (name,options) { ... }
  ```

* **else 关键字要与花括号**保持在同一行。

  eslint: [`brace-style`](http://eslint.org/docs/rules/brace-style)

  ```js
  // ✓ ok
  if (condition) {
    // ...
  } else {
    // ...
  }
  ```

  ```js
  // ✗ avoid
  if (condition) {
    // ...
  }
  else {
    // ...
  }
  ```

* **多行 if 语句的**的括号不能省。

  eslint: [`curly`](http://eslint.org/docs/rules/curly)

  ```js
  // ✓ ok
  if (options.quiet !== true) console.log('done')
  ```

  ```js
  // ✓ ok
  if (options.quiet !== true) {
    console.log('done')
  }
  ```

  ```js
  // ✗ avoid
  if (options.quiet !== true)
    console.log('done')
  ```

* **不要丢掉**异常处理中`err`参数。

  eslint: [`handle-callback-err`](http://eslint.org/docs/rules/handle-callback-err)
  ```js
  // ✓ ok
  run(function (err) {
    if (err) throw err
    window.alert('done')
  })
  ```

  ```js
  // ✗ avoid
  run(function (err) {
    window.alert('done')
  })
  ```

* **使用浏览器全局变量时加上** `window.` 前缀。<br>
  Exceptions are: `document`, `console` and `navigator`.

  eslint: [`no-undef`](http://eslint.org/docs/rules/no-undef)

  ```js
  window.alert('hi')   // ✓ ok
  ```

* **不允许有连续多行空行**。

  eslint: [`no-multiple-empty-lines`](http://eslint.org/docs/rules/no-multiple-empty-lines)

  ```js
  // ✓ ok
  var value = 'hello world'
  console.log(value)
  ```

  ```js
  // ✗ avoid
  var value = 'hello world'
  console.log(value)
  ```

* **对于三元运算符** `?` 和 `:` 与他们所负责的代码处于同一行

  eslint: [`operator-linebreak`](http://eslint.org/docs/rules/operator-linebreak)

  ```js
  // ✓ ok
  var location = env.development ? 'localhost' : 'www.api.com'

  // ✓ ok
  var location = env.development
    ? 'localhost'
    : 'www.api.com'

  // ✗ avoid
  var location = env.development ?
    'localhost' :
    'www.api.com'
  ```

* **每个 var 关键字**单独声明一个变量。

  eslint: [`one-var`](http://eslint.org/docs/rules/one-var)

  ```js
  // ✓ ok
  var silent = true
  var verbose = true

  // ✗ avoid
  var silent = true, verbose = true

  // ✗ avoid
  var silent = true,
      verbose = true
  ```

* **条件语句中赋值语句**使用括号包起来。这样使得代码更加清晰可读，而不会认为是将条件判断语句的全等号（`===`）错写成了等号（`=`）。

  eslint: [`no-cond-assign`](http://eslint.org/docs/rules/no-cond-assign)

  ```js
  // ✓ ok
  while ((m = text.match(expr))) {
    // ...
  }

  // ✗ avoid
  while (m = text.match(expr)) {
    // ...
  }
  ```

* **单行代码块两边加空格**。

  eslint: [`block-spacing`](http://eslint.org/docs/rules/block-spacing)

  ```js
    function foo () {return true}    // ✗ avoid
    function foo () { return true }  // ✓ ok
  ```

* **对于变量和函数名统一使用驼峰命名法**。

  eslint: [`camelcase`](http://eslint.org/docs/rules/camelcase)

  ```js
    function my_function () { }    // ✗ avoid
    function myFunction () { }     // ✓ ok

    var my_var = 'hello'           // ✗ avoid
    var myVar = 'hello'            // ✓ ok
  ```

* **不允许有多余的行末逗号**。

  eslint: [`comma-dangle`](http://eslint.org/docs/rules/comma-dangle)

  ```js
    var obj = {
      message: 'hello',   // ✗ avoid
    }
  ```

* **始终将逗号置于行末**。

  eslint: [`comma-style`](http://eslint.org/docs/rules/comma-style)

  ```js
    var obj = {
      foo: 'foo'
      ,bar: 'bar'   // ✗ avoid
    }

    var obj = {
      foo: 'foo',
      bar: 'bar'   // ✓ ok
    }
  ```

* **点号操作符须与属性需在同一行**。

  eslint: [`dot-location`](http://eslint.org/docs/rules/dot-location)

  ```js
    console.
      log('hello')  // ✗ avoid

    console
      .log('hello') // ✓ ok
  ```

* **文件末尾留一空行**。

  elint: [`eol-last`](http://eslint.org/docs/rules/eol-last)

* **函数调用时标识符与括号间不留间隔**。

  eslint: [`func-call-spacing`](http://eslint.org/docs/rules/func-call-spacing)

  ```js
  console.log ('hello') // ✗ avoid
  console.log('hello')  // ✓ ok
  ```

* **键值对当中冒号与值之间要留空白**。

  eslint: [`key-spacing`](http://eslint.org/docs/rules/key-spacing)

  ```js
  var obj = { 'key' : 'value' }    // ✗ avoid
  var obj = { 'key' :'value' }     // ✗ avoid
  var obj = { 'key':'value' }      // ✗ avoid
  var obj = { 'key': 'value' }     // ✓ ok
  ```

* **构造函数要以大写字母开头**。

  eslint: [`new-cap`](http://eslint.org/docs/rules/new-cap)

  ```js
  function animal () {}
  var dog = new animal()    // ✗ avoid

  function Animal () {}
  var dog = new Animal()    // ✓ ok
  ```

* **无参的构造函数调用时要带上括号**。

  eslint: [`new-parens`](http://eslint.org/docs/rules/new-parens)

  ```js
  function Animal () {}
  var dog = new Animal    // ✗ avoid
  var dog = new Animal()  // ✓ ok
  ```

* **对象中定义了存值器，一定要对应的定义取值器**。

  eslint: [`accessor-pairs`](http://eslint.org/docs/rules/accessor-pairs)

  ```js
  var person = {
    set name (value) {    // ✗ avoid
      this.name = value
    }
  }

  var person = {
    set name (value) {
      this.name = value
    },
    get name () {         // ✓ ok
      return this.name
    }
  }
  ```

* **子类的构造器中一定要调用 `super`**

  eslint: [`constructor-super`](http://eslint.org/docs/rules/constructor-super)

  ```js
  class Dog {
    constructor () {
      super()   // ✗ avoid
    }
  }

  class Dog extends Mammal {
    constructor () {
      super()   // ✓ ok
    }
  }
  ```

* **使用数组字面量而不是构造器**。

  eslint: [`no-array-constructor`](http://eslint.org/docs/rules/no-array-constructor)

  ```js
  var nums = new Array(1, 2, 3)   // ✗ avoid
  var nums = [1, 2, 3]            // ✓ ok
  ```

* **避免使用 `arguments.callee` 和 `arguments.caller`**。

  eslint: [`no-caller`](http://eslint.org/docs/rules/no-caller)

  ```js
  function foo (n) {
    if (n <= 0) return

    arguments.callee(n - 1)   // ✗ avoid
  }

  function foo (n) {
    if (n <= 0) return

    foo(n - 1)
  }
  ```

* **避免对类名重新赋值**。

  eslint: [`no-class-assign`](http://eslint.org/docs/rules/no-class-assign)

  ```js
  class Dog {}
  Dog = 'Fido'    // ✗ avoid
  ```

* **避免修改使用 `const` 声明的变量**。

  eslint: [`no-const-assign`](http://eslint.org/docs/rules/no-const-assign)

  ```js
  const score = 100
  score = 125       // ✗ avoid
  ```

* **避免使用常量作为条件表达式的条件（循环语句除外）**。

  eslint: [`no-constant-condition`](http://eslint.org/docs/rules/no-constant-condition)

  ```js
  if (false) {    // ✗ avoid
    // ...
  }

  if (x === 0) {  // ✓ ok
    // ...
  }

  while (true) {  // ✓ ok
    // ...
  }
  ```

* **正则中不要使用控制符**。

  eslint: [`no-control-regex`](http://eslint.org/docs/rules/no-control-regex)

  ```js
  var pattern = /\x1f/    // ✗ avoid
  var pattern = /\x20/    // ✓ ok
  ```

* **不要使用 `debugger`**。

  eslint: [`no-debugger`](http://eslint.org/docs/rules/no-debugger)

  ```js
  function sum (a, b) {
    debugger      // ✗ avoid
    return a + b
  }
  ```

* **不要对变量使用 `delete` 操作**。

  eslint: [`no-delete-var`](http://eslint.org/docs/rules/no-delete-var)

  ```js
  var name
  delete name     // ✗ avoid
  ```

* **不要定义冗余的函数参数**。

  eslint: [`no-dupe-args`](http://eslint.org/docs/rules/no-dupe-args)

  ```js
  function sum (a, b, a) {  // ✗ avoid
    // ...
  }

  function sum (a, b, c) {  // ✓ ok
    // ...
  }
  ```

* **类中不要定义冗余的属性**。

  eslint: [`no-dupe-class-members`](http://eslint.org/docs/rules/no-dupe-class-members)

  ```js
  class Dog {
    bark () {}
    bark () {}    // ✗ avoid
  }
  ```

* **对象字面量中不要定义重复的属性**。

  eslint: [`no-dupe-keys`](http://eslint.org/docs/rules/no-dupe-keys)

  ```js
  var user = {
    name: 'Jane Doe',
    name: 'John Doe'    // ✗ avoid
  }
  ```

* **`switch` 语句中不要定义重复的 `case` 分支**。

  eslint: [`no-duplicate-case`](http://eslint.org/docs/rules/no-duplicate-case)

  ```js
  switch (id) {
    case 1:
      // ...
    case 1:     // ✗ avoid
  }
  ```

* **同一模块有多个导入时一次性写完**。

  eslint: [`no-duplicate-imports`](http://eslint.org/docs/rules/no-duplicate-imports)

  ```js
  import { myFunc1 } from 'module'
  import { myFunc2 } from 'module'          // ✗ avoid

  import { myFunc1, myFunc2 } from 'module' // ✓ ok
  ```

* **正则中不要使用空字符**。

  eslint: [`no-empty-character-class`](http://eslint.org/docs/rules/no-empty-character-class)

  ```js
  const myRegex = /^abc[]/      // ✗ avoid
  const myRegex = /^abc[a-z]/   // ✓ ok
  ```

* **不要解构空值**。

  eslint: [`no-empty-pattern`](http://eslint.org/docs/rules/no-empty-pattern)

  ```js
  const { a: {} } = foo         // ✗ avoid
  const { a: { b } } = foo      // ✓ ok
  ```

* **不要使用 `eval()`**。

  eslint: [`no-eval`](http://eslint.org/docs/rules/no-eval)

  ```js
  eval( "var result = user." + propName ) // ✗ avoid
  var result = user[propName]             // ✓ ok
  ```

* **`catch` 中不要对错误重新赋值**。

  eslint: [`no-ex-assign`](http://eslint.org/docs/rules/no-ex-assign)

  ```js
  try {
    // ...
  } catch (e) {
    e = 'new value'             // ✗ avoid
  }

  try {
    // ...
  } catch (e) {
    const newVal = 'new value'  // ✓ ok
  }
  ```

* **不要扩展原生对象**。

  eslint: [`no-extend-native`](http://eslint.org/docs/rules/no-extend-native)

  ```js
  Object.prototype.age = 21     // ✗ avoid
  ```

* **避免多余的函数上下文绑定**。

  eslint: [`no-extra-bind`](http://eslint.org/docs/rules/no-extra-bind)

  ```js
  const name = function () {
    getName()
  }.bind(user)    // ✗ avoid

  const name = function () {
    this.getName()
  }.bind(user)    // ✓ ok
  ```

* **避免不必要的布尔转换**。

  eslint: [`no-extra-boolean-cast`](http://eslint.org/docs/rules/no-extra-boolean-cast)

  ```js
  const result = true
  if (!!result) {   // ✗ avoid
    // ...
  }

  const result = true
  if (result) {     // ✓ ok
    // ...
  }
  ```

* **不要使用多余的括号包裹函数**。

  eslint: [`no-extra-parens`](http://eslint.org/docs/rules/no-extra-parens)

  ```js
  const myFunc = (function () { })   // ✗ avoid
  const myFunc = function () { }     // ✓ ok
  ```

* **`switch` 一定要使用 `break` 来将条件分支正常中断**。

  eslint: [`no-fallthrough`](http://eslint.org/docs/rules/no-fallthrough)

  ```js
  switch (filter) {
    case 1:
      doSomething()    // ✗ avoid
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
      doSomething()
      break           // ✓ ok
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
      doSomething()
      // fallthrough  // ✓ ok
    case 2:
      doSomethingElse()
  }
  ```

* **不要省去小数点前面的0**。

  eslint: [`no-floating-decimal`](http://eslint.org/docs/rules/no-floating-decimal)

  ```js
  const discount = .5      // ✗ avoid
  const discount = 0.5     // ✓ ok
  ```

* **避免对声明过的函数重新赋值**。

  eslint: [`no-func-assign`](http://eslint.org/docs/rules/no-func-assign)

  ```js
  function myFunc () { }
  myFunc = myOtherFunc    // ✗ avoid
  ```

* **不要对全局只读对象重新赋值**。

  eslint: [`no-global-assign`](http://eslint.org/docs/rules/no-global-assign)

  ```js
  window = {}     // ✗ avoid
  ```

* **注意隐式的 `eval()`**。

  eslint: [`no-implied-eval`](http://eslint.org/docs/rules/no-implied-eval)

  ```js
  setTimeout("alert('Hello world')")                   // ✗ avoid
  setTimeout(function () { alert('Hello world') })     // ✓ ok
  ```

* **嵌套的代码块中禁止再定义函数**。

  eslint: [`no-inner-declarations`](http://eslint.org/docs/rules/no-inner-declarations)

  ```js
  if (authenticated) {
    function setAuthUser () {}    // ✗ avoid
  }
  ```

* **不要向 `RegExp` 构造器传入非法的正则表达式**。

  eslint: [`no-invalid-regexp`](http://eslint.org/docs/rules/no-invalid-regexp)

  ```js
  RegExp('[a-z')    // ✗ avoid
  RegExp('[a-z]')   // ✓ ok
  ```

* **不要使用非法的空白符**。

  eslint: [`no-irregular-whitespace`](http://eslint.org/docs/rules/no-irregular-whitespace)

  ```js
  function myFunc () /*<NBSP>*/{}   // ✗ avoid
  ```

* **禁止使用 `__iterator__`**。

  eslint: [`no-iterator`](http://eslint.org/docs/rules/no-iterator)

  ```js
  Foo.prototype.__iterator__ = function () {}   // ✗ avoid
  ```

* **外部变量不要与对象属性重名**。

  eslint: [`no-label-var`](http://eslint.org/docs/rules/no-label-var)

  ```js
  var score = 100
  function game () {
    score: 50         // ✗ avoid
  }
  ```

* **不要使用标签语句**。

  eslint: [`no-labels`](http://eslint.org/docs/rules/no-labels)

  ```js
  label:
    while (true) {
      break label     // ✗ avoid
    }
  ```

* **不要书写不必要的嵌套代码块**。

  eslint: [`no-lone-blocks`](http://eslint.org/docs/rules/no-lone-blocks)

  ```js
  function myFunc () {
    {                   // ✗ avoid
      myOtherFunc()
    }
  }

  function myFunc () {
    myOtherFunc()       // ✓ ok
  }
  ```

* **不要混合使用空格与制表符作为缩进**。

  eslint: [`no-mixed-spaces-and-tabs`](http://eslint.org/docs/rules/no-mixed-spaces-and-tabs)

* **除了缩进，不要使用多个空格**。

  eslint: [`no-multi-spaces`](http://eslint.org/docs/rules/no-multi-spaces)

  ```js
  const id =    1234    // ✗ avoid
  const id = 1234       // ✓ ok
  ```

* **不要使用多行字符串**。

  eslint: [`no-multi-str`](http://eslint.org/docs/rules/no-multi-str)

  ```js
  const message = 'Hello \
                   world'     // ✗ avoid
  ```

* **`new` 创建对象实例后需要赋值给变量**。

  eslint: [`no-new`](http://eslint.org/docs/rules/no-new)

  ```js
  new Character()                     // ✗ avoid
  const character = new Character()   // ✓ ok
  ```

* **禁止使用 `Function` 构造器**。

  eslint: [`no-new-func`](http://eslint.org/docs/rules/no-new-func)

  ```js
  var sum = new Function('a', 'b', 'return a + b')    // ✗ avoid
  ```

* **禁止使用 `Object` 构造器**。

  eslint: [`no-new-object`](http://eslint.org/docs/rules/no-new-object)

  ```js
  let config = new Object()   // ✗ avoid
  ```

* **禁止使用 `new require`**。

  eslint: [`no-new-require`](http://eslint.org/docs/rules/no-new-require)

  ```js
  const myModule = new require('my-module')    // ✗ avoid
  ```

* **禁止使用 `Symbol` 构造器**。

  eslint: [`no-new-symbol`](http://eslint.org/docs/rules/no-new-symbol)

  ```js
  const foo = new Symbol('foo')   // ✗ avoid
  ```

* **禁止使用原始包装器**。

  eslint: [`no-new-wrappers`](http://eslint.org/docs/rules/no-new-wrappers)

  ```js
  const message = new String('hello')   // ✗ avoid
  ```

* **不要将全局对象的属性作为函数调用**。

  eslint: [`no-obj-calls`](http://eslint.org/docs/rules/no-obj-calls)

  ```js
  const math = Math()   // ✗ avoid
  ```

* **不要使用八进制字面量**。

  eslint: [`no-octal`](http://eslint.org/docs/rules/no-octal)

  ```js
  const num = 042     // ✗ avoid
  const num = '042'   // ✓ ok
  ```

* **字符串字面量中也不要使用八进制转义字符**。

  eslint: [`no-octal-escape`](http://eslint.org/docs/rules/no-octal-escape)

  ```js
  const copyright = 'Copyright \251'  // ✗ avoid
  ```

* **使用 `__dirname` 和 `__filename` 时尽量避免使用字符串拼接**。

  eslint: [`no-path-concat`](http://eslint.org/docs/rules/no-path-concat)

  ```js
  const pathToFile = __dirname + '/app.js'            // ✗ avoid
  const pathToFile = path.join(__dirname, 'app.js')   // ✓ ok
  ```

* 使用 `getPrototypeOf` 来替代 **`__proto__`**。

  eslint: [`no-proto`](http://eslint.org/docs/rules/no-proto)

  ```js
  const foo = obj.__proto__               // ✗ avoid
  const foo = Object.getPrototypeOf(obj)  // ✓ ok
  ```

* **不要重复声明变量**。

  eslint: [`no-redeclare`](http://eslint.org/docs/rules/no-redeclare)

  ```js
  let name = 'John'
  let name = 'Jane'     // ✗ avoid

  let name = 'John'
  name = 'Jane'         // ✓ ok
  ```

* **正则中避免使用多个空格**。

  eslint: [`no-regex-spaces`](http://eslint.org/docs/rules/no-regex-spaces)

  ```js
  const regexp = /test   value/   // ✗ avoid

  const regexp = /test {3}value/  // ✓ ok
  const regexp = /test value/     // ✓ ok
  ```

* **return 语句中的赋值必需有括号包裹**。

  eslint: [`no-return-assign`](http://eslint.org/docs/rules/no-return-assign)

  ```js
  function sum (a, b) {
    return result = a + b     // ✗ avoid
  }

  function sum (a, b) {
    return (result = a + b)   // ✓ ok
  }
  ```

* **避免将变量赋值给自己**。

  eslint: [`no-self-assign`](http://eslint.org/docs/rules/no-self-assign)

  ```js
  name = name   // ✗ avoid
  ```

* **避免将变量与自己进行比较操作**。

  esint: [`no-self-compare`](http://eslint.org/docs/rules/no-self-compare)

  ```js
  if (score === score) {}   // ✗ avoid
  ```

* **避免使用逗号操作符**。

  eslint: [`no-sequences`](http://eslint.org/docs/rules/no-sequences)

  ```js
  if (doSomething(), !!test) {}   // ✗ avoid
  ```

* **不要随意更改关键字的值**。

  eslint: [`no-shadow-restricted-names`](http://eslint.org/docs/rules/no-shadow-restricted-names)

  ```js
  let undefined = 'value'     // ✗ avoid
  ```

* **禁止使用稀疏数组（Sparse arrays）**。

  eslint: [`no-sparse-arrays`](http://eslint.org/docs/rules/no-sparse-arrays)

  ```js
  let fruits = ['apple',, 'orange']       // ✗ avoid
  ```

* **不要使用制表符**。

  eslint: [`no-tabs`](http://eslint.org/docs/rules/no-tabs)

* **正确使用 ES6 中的字符串模板**。

  eslint: [`no-template-curly-in-string`](http://eslint.org/docs/rules/no-template-curly-in-string)

  ```js
  const message = 'Hello ${name}'   // ✗ avoid
  const message = `Hello ${name}`   // ✓ ok
  ```

* **使用 `this` 前请确保 `super()` 已调用**。

  eslint: [`no-this-before-super`](http://eslint.org/docs/rules/no-this-before-super)

  ```js
  class Dog extends Animal {
    constructor () {
      this.legs = 4     // ✗ avoid
      super()
    }
  }
  ```

* **用 `throw` 抛错时，抛出 `Error` 对象而不是字符串**。

  eslint: [`no-throw-literal`](http://eslint.org/docs/rules/no-throw-literal)

  ```js
  throw 'error'               // ✗ avoid
  throw new Error('error')    // ✓ ok
  ```

* **行末不留空格**。

  eslint: [`no-trailing-spaces`](http://eslint.org/docs/rules/no-trailing-spaces)

* **不要使用 `undefined` 来初始化变量**。

  eslint: [`no-undef-init`](http://eslint.org/docs/rules/no-undef-init)

  ```js
  let name = undefined    // ✗ avoid

  let name
  name = 'value'          // ✓ ok
  ```

* **循环语句中注意更新循环变量**。

  eslint: [`no-unmodified-loop-condition`](http://eslint.org/docs/rules/no-unmodified-loop-condition)

  ```js
  for (let i = 0; i < items.length; j++) {...}    // ✗ avoid
  for (let i = 0; i < items.length; i++) {...}    // ✓ ok
  ```

* **如果有更好的实现，尽量不要使用三元表达式**。

  eslint: [`no-unneeded-ternary`](http://eslint.org/docs/rules/no-unneeded-ternary)

  ```js
  let score = val ? val : 0     // ✗ avoid
  let score = val || 0          // ✓ ok
  ```

* **`return`，`throw`，`continue` 和 `break` 后不要再跟代码**。

  eslint: [`no-unreachable`](http://eslint.org/docs/rules/no-unreachable)

  ```js
  function doSomething () {
    return true
    console.log('never called')     // ✗ avoid
  }
  ```

* **`finally` 代码块中不要再改变程序执行流程**。

  eslint: [`no-unsafe-finally`](http://eslint.org/docs/rules/no-unsafe-finally)

  ```js
  try {
    // ...
  } catch (e) {
    // ...
  } finally {
    return 42     // ✗ avoid
  }
  ```

* **关系运算符的左值不要做取反操作**。

  eslint: [`no-unsafe-negation`](http://eslint.org/docs/rules/no-unsafe-negation)

  ```js
  if (!key in obj) {}       // ✗ avoid
  ```

* **避免不必要的 `.call()` 和 `.apply()`**。

  eslint: [`no-useless-call`](http://eslint.org/docs/rules/no-useless-call)

  ```js
  sum.call(null, 1, 2, 3)   // ✗ avoid
  ```

* **避免使用不必要的计算值作对象属性**。

  eslint: [`no-useless-computed-key`](http://eslint.org/docs/rules/no-useless-computed-key)

  ```js
  const user = { ['name']: 'John Doe' }   // ✗ avoid
  const user = { name: 'John Doe' }       // ✓ ok
  ```

* **禁止多余的构造器**。

  eslint: [`no-useless-constructor`](http://eslint.org/docs/rules/no-useless-constructor)

  ```js
  class Car {
    constructor () {      // ✗ avoid
    }
  }
  ```

* **禁止不必要的转义**。

  eslint: [`no-useless-escape`](http://eslint.org/docs/rules/no-useless-escape)

  ```js
  let message = 'Hell\o'  // ✗ avoid
  ```

* **import, export 和解构操作中，禁止赋值到同名变量**。

  eslint: [`no-useless-rename`](http://eslint.org/docs/rules/no-useless-rename)

  ```js
  import { config as config } from './config'     // ✗ avoid
  import { config } from './config'               // ✓ ok
  ```

* **属性前面不要加空格**。

  eslint: [`no-whitespace-before-property`](http://eslint.org/docs/rules/no-whitespace-before-property)

  ```js
  user .name      // ✗ avoid
  user.name       // ✓ ok
  ```

* **禁止使用 `with`**。

  eslint: [`no-with`](http://eslint.org/docs/rules/no-with)

  ```js
  with (val) {...}    // ✗ avoid
  ```

* **对象属性换行时注意统一代码风格**。

  eslint: [`object-property-newline`](http://eslint.org/docs/rules/object-property-newline)

  ```js
  const user = {
    name: 'Jane Doe', age: 30,
    username: 'jdoe86'            // ✗ avoid
  }

  const user = { name: 'Jane Doe', age: 30, username: 'jdoe86' }    // ✓ ok

  const user = {
    name: 'Jane Doe',
    age: 30,
    username: 'jdoe86'
  }                                                                 // ✓ ok
  ```

* **代码块中避免多余留白**。

  eslint: [`padded-blocks`](http://eslint.org/docs/rules/padded-blocks)

  ```js
  if (user) {
                              // ✗ avoid
    const name = getName()

  }

  if (user) {
    const name = getName()    // ✓ ok
  }
  ```

* **展开运算符与它的表达式间不要留空白**。

  eslint: [`rest-spread-spacing`](http://eslint.org/docs/rules/rest-spread-spacing)

  ```js
  fn(... args)    // ✗ avoid
  fn(...args)     // ✓ ok
  ```

* **遇到分号时空格要后留前不留**。

  eslint: [`semi-spacing`](http://eslint.org/docs/rules/semi-spacing)

  ```js
  for (let i = 0 ;i < items.length ;i++) {...}    // ✗ avoid
  for (let i = 0; i < items.length; i++) {...}    // ✓ ok
  ```

* **代码块首尾留空格**。

  eslint: [`space-before-blocks`](http://eslint.org/docs/rules/space-before-blocks)

  ```js
  if (admin){...}     // ✗ avoid
  if (admin) {...}    // ✓ ok
  ```

* **圆括号间不留空格**。

  eslint: [`space-in-parens`](http://eslint.org/docs/rules/space-in-parens)

  ```js
  getName( name )     // ✗ avoid
  getName(name)       // ✓ ok
  ```

* **一元运算符后面跟一个空格**。

  eslint: [`space-unary-ops`](http://eslint.org/docs/rules/space-unary-ops)

  ```js
  typeof!admin        // ✗ avoid
  typeof !admin        // ✓ ok
  ```

* **注释首尾留空格**。

  eslint: [`spaced-comment`](http://eslint.org/docs/rules/spaced-comment)

  ```js
  //comment           // ✗ avoid
  // comment          // ✓ ok

  /*comment*/         // ✗ avoid
  /* comment */       // ✓ ok
  ```

* **模板字符串中变量前后不加空格**。

  eslint: [`template-curly-spacing`](http://eslint.org/docs/rules/template-curly-spacing)

  ```js
  const message = `Hello, ${ name }`    // ✗ avoid
  const message = `Hello, ${name}`      // ✓ ok
  ```

* **检查 `NaN` 的正确姿势是使用 `isNaN()`**。

  eslint: [`use-isnan`](http://eslint.org/docs/rules/use-isnan)

  ```js
  if (price === NaN) { }      // ✗ avoid
  if (isNaN(price)) { }       // ✓ ok
  ```

* **用合法的字符串跟 `typeof` 进行比较操作**。

  eslint: [`valid-typeof`](http://eslint.org/docs/rules/valid-typeof)

  ```js
  typeof name === 'undefimed'     // ✗ avoid
  typeof name === 'undefined'     // ✓ ok
  ```

* **自调用匿名函数 (IIFEs) 使用括号包裹**。

  eslint: [`wrap-iife`](http://eslint.org/docs/rules/wrap-iife)

  ```js
  const getName = function () { }()     // ✗ avoid

  const getName = (function () { }())   // ✓ ok
  const getName = (function () { })()   // ✓ ok
  ```

* **`yield *` 中的 `*` 前后都要有空格**。

  eslint: [`yield-star-spacing`](http://eslint.org/docs/rules/yield-star-spacing)

  ```js
  yield* increment()    // ✗ avoid
  yield * increment()   // ✓ ok
  ```

* **请书写优雅的条件语句（avoid Yoda conditions）**。

  eslint: [`yoda`](http://eslint.org/docs/rules/yoda)

  ```js
  if (42 === age) { }    // ✗ avoid
  if (age === 42) { }    // ✓ ok
  ```

## 质量规范React

* **组件声明**

  全面使用 ES6 class 声明，可不严格遵守该属性声明次序，但如有 propTypes 则必须写在顶部， lifecycle events 必须写到一起。

  * class
    * propTypes
    * defaultPropTypes
    * constructor
      * event handlers (如不使用[类属性](http://babeljs.io/docs/plugins/transform-class-properties/)语法可在此声明)
    * lifecycle events
    * event handlers
    * getters
    * render

  ```javascript
  class Person extends React.Component {
    static propTypes = {
      firstName: PropTypes.string.isRequired,
      lastName: PropTypes.string.isRequired
    }
    constructor (props) {
      super(props)

      this.state = { smiling: false }

      /* 若不能使用 babel-plugin-transform-class-properties
      this.handleClick = () => {
        this.setState({smiling: !this.state.smiling})
      }
      */
    }

    componentWillMount () {}

    componentDidMount () {}

    // ...

    handleClick = () => {
      this.setState({smiling: !this.state.smiling})
    }

    get fullName () {
      return this.props.firstName + this.props.lastName
    }

    render () {
      return (
        <div onClick={this.handleClick}>
          {this.fullName} {this.state.smiling ? 'is smiling.' : ''}
        </div>
      )
    }
  }
  ```

* **计算属性**

  使用 getters 封装 render 所需要的状态或条件的组合

  对于返回 boolean 的 getter 使用 is- 前缀命名

  ```javascript
    // bad
    render () {
      return (
        <div>
          {
            this.state.age > 18
              && (this.props.school === 'A'
                || this.props.school === 'B')
              ? <VipComponent />
              : <NormalComponent />
          }
        </div>
      )
    }

    // good
    get isVIP() {
      return
        this.state.age > 18
          && (this.props.school === 'A'
            || this.props.school === 'B')
    }
    render() {
      return (
        <div>
          {this.isVIP ? <VipComponent /> : <NormalComponent />}
        </div>
      )
    }
  ```

* **事件回调命名**

  Handler 命名风格:

  - 使用 `handle` 开头
  - 以事件类型作为结尾 (如 `Click`, `Change`)
  - 使用一般现在时

  ```javascript
  // bad
  closeAll = () => {},

  render () {
    return <div onClick={this.closeAll} />
  }
  ```

  ```javascript
  // good
  handleClick = () => {},

  render () {
    return <div onClick={this.handleClick} />
  }
  ```

  如果你需要区分同样事件类型的 handler（如 `handleNameChange` 和 `handleEmailChange`）时，可能这就是一个拆分组件的信号

* **组件化优于多层 render**

  当组件的 jsx 只写在一个 render 方法显得太臃肿时，很可能更适合拆分出一个组件，视情况采用 class component 或 stateless component

  ```javascript
  // bad
  renderItem ({name}) {
    return (
      <li>
      	{name}
      	{/* ... */}
      </li>
    )
  }

  render () {
    return (
      <div className="menu">
        <ul>
          {this.props.items.map(item => this.renderItem(item))}
        </ul>
      </div>
    )
  }
  ```

  ```javascript
  // good
  function Items ({name}) {
    return (
      <li>
      	{name}
      	{/* ... */}
      </li>
    )
  }

  render () {
    return (
      <div className="menu">
        <ul>
          {this.props.items.map(item => <Items {...item} />)}
        </ul>
      </div>
    )
  }
  ```

* **状态上移优于公共方法**

  一般组件不应提供公共方法，这样会破坏数据流只有一个方向的原则。

  再因为我们倾向于更细颗粒的组件化，状态应集中在远离渲染的地方处理（比如应用级别的状态就在 redux 的 store 里），也能使兄弟组件更方便地共享。

  ```javascript
  //bad
  class DropDownMenu extends Component {
    constructor (props) {
      super(props)
      this.state = {
        showMenu: false
      }
    }

    show () {
      this.setState({display: true})
    }

    hide () {
      this.setState({display: false})
    }

    render () {
      return this.state.display && (
        <div className="dropdown-menu">
          {/* ... */}
        </div>
      )
    }
  }

  class MyComponent extends Component {
    // ...
    showMenu () {
      this.refs.menu.show()
    }
    hideMenu () {
      this.refs.menu.hide()
    }
    render () {
      return <DropDownMenu ref="menu" />
    }
  }

  //good
  class DropDownMenu extends Component {
    static propsType = {
      display: PropTypes.boolean.isRequired
    }

    render () {
      return this.props.display && (
        <div className="dropdown-menu">
          {/* ... */}
        </div>
      )
    }
  }

  class MyComponent extends Component {
    constructor (props) {
      super(props)
      this.state = {
        showMenu: false
      }
    }

    // ...

    showMenu () {
      this.setState({showMenu: true})
    }

    hideMenu () {
      this.setState({showMenu: false})
    }

    render () {
      return <DropDownMenu display={this.state.showMenu} />
    }
  }
  ```

  更多阅读: [lifting-state-up](https://facebook.github.io/react/docs/lifting-state-up.html)

* **容器组件**

  一个容器组件主要负责维护状态和数据的计算，本身并没有界面逻辑，只把结果通过 props 传递下去。

  区分容器组件的目的就是可以把组件的状态和渲染解耦开来，改写界面时可不用关注数据的实现，顺便得到了可复用性。

  ```javascript
  // bad
  class MessageList extends Component {
    constructor (props) {
      super(props)
    	this.state = {
          onlyUnread: false,
          messages: []
    	}
    }

    componentDidMount () {
      $.ajax({
        url: "/api/messages",
      }).then(({messages}) => this.setState({messages}))
    }

    handleClick = () => this.setState({onlyUnread: !this.state.onlyUnread})

    render () {
      return (
        <div class="message">
          <ul>
            {
              this.state.messages
                .filter(msg => this.state.onlyUnread ? !msg.asRead : true)
                .map(({content, author}) => {
                  return <li>{content}—{author}</li>
                })
            }
          </ul>
          <button onClick={this.handleClick}>toggle unread</button>
        </div>
      )
    }
  }
  ```

  ```javascript
  // good
  class MessageContainer extends Component {
    constructor (props) {
      super(props)
    	this.state = {
          onlyUnread: false,
          messages: []
    	}
    }

    componentDidMount () {
      $.ajax({
        url: "/api/messages",
      }).then(({messages}) => this.setState({messages}))
    }

    handleClick = () => this.setState({onlyUnread: !this.state.onlyUnread})

    render () {
      return <MessageList
        messages={this.state.messages.filter(msg => this.state.onlyUnread ? !msg.asRead : true)}
        toggleUnread={this.handleClick}
      />
    }
  }

  function MessageList ({messages, toggleUnread}) {
    return (
      <div class="message">
        <ul>
          {
            messages
              .map(({content, author}) => {
                return <li>{content}—{author}</li>
              })
          }
        </ul>
        <button onClick={toggleUnread}>toggle unread</button>
      </div>
    )
  }
  MessageList.propTypes = {
    messages: propTypes.array.isRequired,
    toggleUnread: propTypes.func.isRequired
  }
  ```

  更多阅读:
  - [Presentational and Container Components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0#.sz7z538t6)
  - [React AJAX Best Practices](http://andrewhfarmer.com/react-ajax-best-practices/)


* **纯函数的 render**

  render 函数应该是一个纯函数（stateless component 当然也是），不依赖 this.state、this.props 以外的变量，也不改变外部状态

  ```javascript
  // bad
  render () {
    return <div>{window.navigator.userAgent}</div>
  }

  // good
  render () {
    return <div>{this.props.userAgent}</div>
  }
  ```

  更多阅读: [Return as soon as you know the answer](https://medium.com/@SimonRadionov/return-as-soon-as-you-know-the-answer-dec6369b9b67#.q67w8z60g)

* **始终声明 PropTypes**

  每一个组件都声明 PropTypes，非必须的 props 应提供默认值。

  对于非常广为人知的 props 如 children, dispatch 也不应该忽略。因为如果一个组件没有声明 dispatch 的 props，那么一眼就可以知道该组件没有修改 store 了。

  但如果在开发一系列会 dispatch 的组件时，可在这些组件的目录建立单独的 .eslintrc 来只忽略 dispatch。

  更多阅读: [Prop Validation](http://facebook.github.io/react/docs/reusable-components.html#prop-validation)

* **Props 非空检测**

  对于并非 `isRequired` 的 proptype，必须对应设置 defaultProps，避免再增加 if 分支带来的负担

  ```javascript
  // bad
  render () {
    if (this.props.person) {
      return <div>{this.props.person.firstName}</div>
    } else {
      return <div>Guest</div>
    }
  }
  ```

  ```javascript
  // good
  class MyComponent extends Component {
    render() {
      return <div>{this.props.person.firstName}</div>
    }
  }

  MyComponent.defaultProps = {
    person: {
      firstName: 'Guest'
    }
  }
  ```

  如有必要，使用 PropTypes.shape 明确指定需要的属性

* **使用 Props 初始化**

  除非 props 的命名明确指出了意图，否则不该使用 props 来初始化 state

  ```javascript
  // bad
  constructor (props) {
    this.state = {
      items: props.items
    }
  }
  ```

  ```javascript
  // good
  constructor (props) {
    this.state = {
      items: props.initialItems
    }
  }
  ```

  更多阅读: ["Props in getInitialState Is an Anti-Pattern"](http://facebook.github.io/react/tips/props-in-getInitialState-as-anti-pattern.html)

* **classnames**

  使用 [classNames](https://www.npmjs.com/package/classnames) 来组合条件结果.

  ```javascript
  // bad
  render () {
    return <div className={'menu ' + this.props.display ? 'active' : ''} />
  }
  ```

  ```javascript
  // good
  render () {
    let classes = {
      menu: true,
      active: this.props.display
    }

    return <div className={classnames(classes)} />
  }
  ```

  Read: [Class Name Manipulation](https://github.com/JedWatson/classnames/blob/master/README.md)
  
## 质量规范Vue

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
