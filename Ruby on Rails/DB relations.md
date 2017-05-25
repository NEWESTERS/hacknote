# Rails
## Создание связей в БД
У моделей не нужно создавать поля, являющиеся вторичными ключами, т.к. они создадутся автоматически при миграции БД

В модели необходимо прописать связи в виде:
```
	belongs_to :model_name

	has_many :model_names
```
Создать миграцию терминальной командой:
```
	$ rails g migration migration_name
```
Для создания ключей в сгенерированном файле миграции прописать изменения в таблицах:
```
	change_table :table_name do |t|

	  t.belongs_to :model_name, index: true
```
Замечания:

* has_many в миграции писать не нужно

* можно прописать изменения для нескольких таблиц в одном файле

## Select in Rails  ---------->

при создании данного селекта имя тега селекта в html выглядит name=film[genre]

```
	###@film.map{|f|....

   	<%= f.select ###:genre, Genre.all.collect{ |c| [c.Name, c.id] } %>
```
 В значение value данного селекта передаётся id а в содержимое тегов выборки Name
 (пример:)
 
	 <select>
		<option value="c.id">c.Name</option>
		......
В параметр передается id извлекается следующим образом params[:film][:genre]
параметры всегда передаются как строки!!!
```
	@film.genre = Genre.all.select{ |x| x.id == params[:film][:genre].to_i }[0]
```	
