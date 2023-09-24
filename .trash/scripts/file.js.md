````js
// in vault at scripts/coolString.js
class CoolString {
    coolify(s) {
        return `😎 ${s} 😎`
    }
}


// dataviewjs block in *.md
```dataviewjs
const {CoolString} = customJS
dv.list(dv.pages().file.name.map(n => CoolString.coolify(n)))
```

// templater template
<%*
const {CoolString} = customJS;
tR += CoolString.coolify(tp.file.title);
%>
````