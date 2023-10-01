- `npm install eslint --save-dev`
- `$ yarn global add eslint` - глобальная установка ESLint (чтобы не устанавливать для каждого проекта)

Установка и настройка файла конфигурации:
- `eslint --init`

Для того, чтобы наша проверка работала, нам нужно установить необходимые пакеты:
```
npm install --save-dev eslint eslint-plugin-prettier eslint-config-prettier babel-eslint
```

```
npm install --save-dev --save-exact prettier
```