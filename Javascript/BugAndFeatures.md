# Bugs and Features

## Использование setTimeout внутри итератора выдает timer

Подобный код выдаст не ошибку, но неверный результат, так как в Promise.all() попадает массив чисел связанных с таймером вместо промисов

```javascript
await Promise.all(['default_branches', 'okopf', 'countries', 'employment_position']
    .map((item, i) => setTimeout(() =>
        new Promise(async (resolve) =>
            resolve(
                await loadDict(item))),
                100 * i
            )
    )
);
```

В этом случае следует использоать такой вариант для получения массива промисов

```javascript
await Promise.all(
    ['default_branches', 'okopf', 'countries', 'employment_position']
        .map((item, i) =>
            new Promise((resolve) =>
                setTimeout(async () => {
                    let res = await loadDict(item);
                    resolve(res);
                },
                100 * i)
            )
        )
);
```
