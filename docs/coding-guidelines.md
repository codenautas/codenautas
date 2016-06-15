## Draft of future coding conventions and guidelines for Codenautas projects

### Porpuose
This document collects de facto coding conventions used in current projects, starting with a simple list with little or no clasification.
Hopefully, subsecuent versions of this documents will evolve into a more consistent classification.

### Contents
* [Node projects](#node-projects)
* [JavaScript guidelines](#javascript-guidelines)

---

### Node projects
* New projects should be created using [qa-control command-line utility](https://github.com/codenautas/qa-control) that generates a template with the minimal
  required setup, for example:
  
  ``` mkdir myproject && cd myprojects && qa-control --init```
* Source code editor settings:
  * File encoding: UTF8 without BOM
  * Tabs according by file-type:

      ext | width
    ------|-------:
    css   |   2
    jade  |   2
    js    |   4
    md    |   2

  * Replace tabs with spaces
* Multi-language documentation should be written in github's style of markdown, starting in LEEME.md file, providing at least a description in english and spanish.
  * [multilang](https://github.com/codenautas/multilang) should be used to generate (from LEEME.md) README.md and other language files
  * Warning: README.md is required for npmjs.com publication
* [qa-control](https://github.com/codenautas/qa-control) can be used to check for various conventions including:
  * package.json format and dependencies
  * .gitignore, .travis, etc
  * jshint/eslint warnings and "use strict" declarations
  * "cucardas"
  * [multilang](https://github.com/codenautas/multilang) sincronization

---

### JavaScript guidelines
#### Style
* Variables should be named using camel-case:
```javascript
  var father;
  var childPeter;
  var fatherAndSon;
```

* Methods of classes should be declared verbatim to favor debugging (i.e. with Chrome):
```javascript
var myClass = {}
// correct
myClass.myMethod = function myMethod() {};
// incorrect
myClass.myMethod = function() {};

```

* Open braces in conditionals and loops should be in on the same line as the keyword:
```javascript
// correct
if(condition) {
  // ...
}
for(var i; i<max; ++i) {
}

// incorrect
if(condition)
{
  // ...
}
while(condition)
{
  // ...
}
```
* **else** should be in the same line of the braces:
```javascript
if(condition) {
  // ...
} else {
  // ...
}
```

* The space between the keyword and the brace is optional, but must be consistent in the file:
```javascript
// one way
if(condition) {
  // ...
} else {

// the other way
if(condition){
  // ...
}else{
```

* Objects should be defined using {} syntax (inline form) when posible
```javascript

function f1(obj) {
  return obj.first + obj.second;
}
// use
var result = f1({first:12, second:54});

// instead of
function Param(first, second) {
  this.first = first;
  this.second = second;
}
var result = f1(new Param{12, 54));

```

#### Performance
* String concatenation should be avoided, use array push() + join() instead:
```javascript
// wrong
var s="";
s += "one";
s += "two" + "three";
var result = s;
// right!
var s=[];
s.push("one");
s.push("two");
s.push("three");
var result = s.join('');
```
