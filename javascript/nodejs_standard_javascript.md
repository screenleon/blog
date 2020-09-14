# Nodejs Standard Javascript
> **Lien Chen** *2020-09-14*

* Nodejs javascript version is not the standard javascript, so it cant fit the javascript using in website.
* We need to translate node package to standard javascript to use in website.
* I choose browserify to translate.

```
browserify [src file] -s [require name] > [dist file]
```
* RUN above code then include to your html, you now can use node package with you set require name in script