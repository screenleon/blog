# Self vs This
================================

**Author**: Lien Chen  **Date**: 2020-08-26

#### Summary
* Use `$this` to refer to the current object
    * use `$this->member` for non-static members
* Use `self` to refer to the current class
    * use `self::$member` for static members
* `self` is used with the scope resolution operator `::` to refer to the current class
* it's perfectly legal to use `$this` to call static methods (but not to reference fields).

[reference](https://stackoverflow.com/questions/151969/when-to-use-self-over-this)