### Установка
`npm i -g typescript tslint`

### Инициализация
Typescript: `tsc --init`

Линтер: `tslint --init`

### Правила tslint
Пример: разрешение логгирования в консоли:
```json
// tslint.json
{
   "defaultSeverity": "error",
   "extends": [
      "tslint:recommended"
   ],
   "jsRules": {
   },
   "rules": {
      "no-console": [false]
   },
   "rulesDirectory": []
}
```

### Установка необходимых зависимостей в проект
`npm install ts-node tslint typescript typescript-eslint-parser @types/node rimraf nodemon --save-dev`

### Компиляция es6
```json
// tsconfig.json
{
   "compilerOptions": {
      "target": "es6",
      "module": "commonjs",
      "outDir": "dist",
      "sourceMap": false,
      "declaration": true,
      "lib": [
        "es2017.object",
        "es2015",
        "es2017"
      ]
   },
   "files": [
      "./node_modules/@types/node/index.d.ts"
   ],
   "include": [
      "src/**/*.ts"
   ],
   "exclude": [
      "node_modules"
   ]
}
```

### Настройка nodemon
```json
// nodemon.json
{
  "watch": ["src"],
  "ext": "ts",
  "ignore": ["src/**/*.spec.ts"],
  "exec": "ts-node ./src/index.ts"
}
```





