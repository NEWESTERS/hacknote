# Теги в Rails
## Select tag
**Select tag** создаётся следующим образом:
```ruby
<%= select_tag 'name', options_for_select( Model.all.collect{ |u| [u.name, u.id] } ) %>
```
Этот Rails-тег создаст следующий **select**:
```html
<select id="name" name="name">
  <option value="1">Brad</option>
  <option value="2">Angie</option>
  <option value="3">Jenny</option>
</select>
```
И обращаться к нему в контроллере можно будет следующим образом:
```ruby
params[:name].to_i
```
