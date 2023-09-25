
1. Установка GitHub Pages
```
$ npm install gh-pages --save-dev
```
2. Добавление команды `deploy`
```
|> package.json

"scripts": {
	"dev": "npx webpack-dev-server --mode development",
	"build": "npx webpack --mode production",
	"deploy": "gh-pages -d dist"
},
```
3. Сборка проекта
```
$ npm run build
```
4. Разворачивание проекта на GitHub Pages
```
$ npm run deploy
```
5. Настройка  GitHub Pages в настройках репозитория
   После успешного выполнения предыдущей команды, перейдите в настройки вашего репозитория на GitHub. Прокрутите вниз до раздела GitHub Pages и выберите источник для развертывания. В большинстве случаев, вы должны выбрать `gh-pages branch`