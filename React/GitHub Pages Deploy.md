# Deploy React-приложения на GitHub Pages

Для начала нужно добавить в проект пакет "**gh-pages**":

```bash
npm install --save-dev gh-pages
```

Затем в секцию `"scripts"` файла *package.json* необходимо добавить следующие строки:

```json
"predeploy": "npm run build",
"deploy": "gh-pages -d build"
```

Также в корень *package.json* нужно добавить такую строку:

```json
"homepage": "http://username.github.io/<repo_name>"
```

Где `<repo_name>` — название репозитория

Теперь при выполнении команды `npm run deploy` приложение будет деплоиться в **GitHub Pages**

**Примечание**: для деплоя в репозитории будет создана специальная ветка "**gh-pages**"
