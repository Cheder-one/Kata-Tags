Запретить отображение `console.log` в режиме production

```
if (process.env.NODE_ENV === 'production') {
  console.log = function() {};
}
```

