# Passport can't find req.user
> **Lien Chen** *2020-07-16*

Need to enable session by 
```javascript=
app.use(session());
app.use(passport.initialize());
app.use(passport.session());
```

`app.use(session())` need to put before passport use, then you can add req.user successfully.