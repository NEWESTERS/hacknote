# Добавляем поля в Users
## Изменение структуры базы данных
Создать миграцию терминальной командой:
```
$ rails g migration AddFieldsToUsers birthday:date name:string

```
В **routes.rb**
```ruby
devise_for :users, controllers: {
	sessions: 'users/sessions'
	}
```
3) В **registrations_controller.rb**
```ruby
before_filter :configure_permitted_parameters
# ...
def configure_permitted_parameters
	devise_parameter_sanitizer.for(:sign_up) do |u|
		u.permit(:name, :birthday, :email, :password, :password_confirmation)
	end
end
```
4) Выполняю миграцию

5) Добавляю поля **name** и **birthday** во вьюхи девайса (регистрация и редактор)

6) Хочу построить таблицу юзеров

7) Создал контроллер **users_controller** и прописал там функцию **index**
```ruby
def index
  	@users = User.all.order("created_at DESC")
end
```
8) Рукаааааааами создаю вьюху **index.html.erb** и прописываю вывод полей в сгенеренной папке **users**

9) Прописываю в рутах
```ruby
match '/users', to: 'users#index', via: 'get'

```
10) Таблица создана, проблема с выводом сгенеренных полей
