```
const chars = [ 'a', 'a', 'b', 'b', 'c', 'c', 'd', 'e' ]

const uniqCharts = new Set(chars)
/=/ Set { 'a', 'b', 'c', 'd', 'e' }

const uniqCharts = [...new Set(chars)]
/=/ [ 'a', 'b', 'c', 'd', 'e' ]
```

