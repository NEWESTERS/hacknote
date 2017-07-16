# Devise
## Добавление полей в Users
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
В **registrations_controller.rb**
```ruby
before_filter :configure_permitted_parameters
# ...
def configure_permitted_parameters
  devise_parameter_sanitizer.for(:sign_up) do |u|
    u.permit(:name, :birthday, :email, :password, :password_confirmation)
  end
end
```
Выполнить миграцию
```
$ rake db:migrate
```

Добавить поля **name** и **birthday** в представления **registrations** и **edit**
