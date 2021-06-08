# Webpack Resolve dotenv Error
> **Lien Chen** *2021-06-08*

* Run dotenv on laravel might run out with error `Can't resolve 'fs'` and `Can't resolve 'path'`
* Add below code to webpack.mix.js

```javascript=
mix.webpackConfig({resolve: {fallback: {fs: false, path: false}}});
```

* Then you can fix this issue

---

[github](https://github.com/motdotla/dotenv/issues/233)
