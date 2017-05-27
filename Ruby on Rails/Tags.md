# Теги в Rails
## Select tag
**Select** создаётся следующим образом:
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
## Datetime select tag
**Datetime select** создаётся следующим образом
```ruby
<%= datetime_select("date", "date") %>
```
Этот Rails-тег создаст следующий **select**:
```html
<select id="date_date_1i" name="date[date(1i)]">
	<option value="2012">2012</option>
	...
	<option value="2012">2022</option>
</select>
<select id="date_date_2i" name="date[date(2i)]">
	<option value="1">January</option>
	...
	<option value="12">December</option>
</select>
<select id="date_date_3i" name="date[date(3i)]">
	<option value="1">1</option>
	...
	<option value="31">31</option>
</select>
"—"
<select id="date_date_4i" name="date[date(4i)]">
	<option value="00">00</option>
	...
	<option value="23">23</option>
</select>
":"
<select id="date_date_5i" name="date[date(5i)]">
	<option value="00">00</option>
	...
	<option value="59">59</option>
</select>
```
Дату этот тег отправляет по частям, поэтому для удобства использования её нужно собрать воедино:
```ruby
event = params[:date]
date = Date.new event["date(1i)"].to_i, event["date(2i)"].to_i, event["date(3i)"].to_i
time = Time.new 2017, 5, 23, event["date(4i)"].to_i, event["date(5i)"].to_i
```
Получение даты и времени в виде форматированной строки:
```ruby
date.strftime("%d %B %Y")	# 26 May 2017
time.strftime("%H:%M")		# 21:00
```