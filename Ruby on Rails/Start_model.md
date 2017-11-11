#  Rails
## Быстрый старт

После генерации приложения, если в нем есть какие-либо сущности, надо сгенерировать модели для каждой сущности с указанием параметров. Название модели с большой буквы.
```console
rails g model #Modelname# #attr1#:string #attr2#:text
```

Выполнить миграцию 
```console
rake db:migrate
```
Сгенерировать контроллер для модели 
```console
rails g controller #ModelnameS#
```
это сразу создаст **view** (вместе со стилями и js)

затем в контроллере надо прописывать функции и для них создавать представления
 
миграциями добавляем поля и устанавливаем вторичные ключи и связи сущностей см.

https://github.com/NEWESTERS/hacknote/blob/master/Ruby%20on%20Rails/Database.md