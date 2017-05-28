# Лайфхаки
## Строка,как название класса
В отличие от JS в Ruby строку перед использованием нужно преобразовать
```ruby
class User
end

Object.const_get("User") == User	# true
```