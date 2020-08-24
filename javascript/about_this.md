# About This
> **Lien Chen** *2020-08-24*

* The JavaScript **this** keyword refers to the object it belongs to.
    * In a method, `this` refers to the **owner object**.
    * Alone, `this` refers to the **global object**.
    * In a function, `this` refers to the **global object**.
    * In a function, in strict mode, `this` is `undefined`.
    * In an event, `this` refers to the **element** that received the event.
    * Methods like `call()`, and `apply()` can refer `this` to **any object**.

[reference](https://www.w3schools.com/js/js_this.asp)