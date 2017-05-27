# База данных
## Изменение структуры базы данных
Создать миграцию терминальной командой:
```
$ rails g migration migration_name
```
В сгенерированном фале миграций *(db/migrations/migration_name.rb)* прописать изменения в таблицах
```ruby
change_table :users do |t|
  t.remove :email	# удаляет из таблицы users поле с ключом email
  t.string :name 	# добавляет в таблицу users поле с ключом name и типом строка
end
```
## Создание связей в БД
У моделей не нужно создавать поля, являющиеся вторичными ключами, т.к. они создадутся автоматически при миграции БД

В модели необходимо прописать связи в виде:
```ruby
belongs_to :user
has_many :orders
```
Создать миграцию терминальной командой:
```
$ rails g migration AddUserToOrders user:references
```
Что создаст файл миграции со следующим содержимым:
```ruby
class AddUserToUploads < ActiveRecord::Migration[5.0]
  def change
    add_reference :orders, :user, foreign_key: true
  end
end
```
Команды в функцию **change** также можно добавлять вручную

Вместо **add_reference** можно написать:
```ruby
change_table :orders do |t|
  t.belongs_to :user, index: true
```
Далее неообходимо сделать миграцию базы данных командой
```
$ rake db:migrate
```
Удаление связи:
```ruby
remove_reference :orders, :user, index: true, foreign_key: true
```
Замечания:

* **has_many** в миграции писать не нужно

* можно прописать изменения для нескольких таблиц в одном файле
