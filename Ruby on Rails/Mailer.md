# Организация почтовой рассылки
## Настройка SMTP
В файле */config/enviroments/development.rb (production.rb)* включить **SMTP** и прописать данные для входа в почтовый ящик (на примере **gmail**):
```ruby
config.action_mailer.delivery_method = :smtp
config.action_mailer.smtp_settings = {
  address: 'smtp.gmail.com',
  port: 587,
  user_name: '<username>',
  password: '<password>',
  authentication: 'plain',
  enable_starttls_auto: true
}
```
В настройках **gmail** может потребоваться разрешить вход для "ненадёжных приложений"
## Отправка почты
Создать **mailer** терминальной командой:
```ruby
$ rails generate mailer SampleMailer
```
В получившемся файле */app/controllers/mailers/sample_mailer.rb* создать метод, отправляющий письма:
```ruby
class SampleMailer < ApplicationMailer
  default :from => "from@example.com"

  def send_email(user)
    @user = user	# переменная, которую можно будет использовать во view
    mail(:to => user.email, :subject => "Тема письма")
  end
end
```
Создать шаблон письма */app/views/sample_mailer/send_email.html.erb*:
```ruby
<!DOCTYPE html>
<html>
  <head>
    <meta content="text/html; charset=UTF-8" http-equiv="Content-Type" />
  </head>
  <body>
    <p>Здравствуйте, <b><%= @user.name %></b>,</p>
    <p>Съешьте ещё этих мягких французских булок, да выпейте чаю</p>
  </body>
</html>
```
Теперь письмо с созданным шаблоном можно отправить в любом контроллере методом:
```ruby
SampleMailer.send_email(@user).deliver_now   # deliver_now отправляет письмо сразу
```
