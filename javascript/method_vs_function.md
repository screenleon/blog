# Method vs Function
================================

**Author**: Lien Chen  **Date**: 2020-08-24

* It's semantics and has to do with what you are trying to express.
* In JavaScript every function is an object. ***An object is a collection of key:value pairs.*** If a value is a primitive (number, string, boolean), or another object, the value is considered a property. **If a value is a function, it is called a 'method'.**
* A function is usually in the top level (global) namespace, a method belongs to a class/object namespace and has to be called with that receiver.

#### Result
* Method is a function when object is associated with it.
* When no object is associated with it , it comes to function.

[reference](https://stackoverflow.com/questions/15285293/method-vs-functions-and-other-questions)