# Объектно-ориентированное программирование в Javascript
## Prototype
### Прототипное наследование
Одной из основных концепций ООП является наследование. В JS оно реализуется с помощью так называемых прототипов.
```javascript
// Создаём родительский конструктор
function Animal(name) {
  this.name = name
}

// Создаём дочерние конструкторы
function Fish(name, fins_number) {
  Animal.call(this, name) // Вызов родительского конструктора
  this.type = 'Рыба'
  this.fins_number = fins_number
}

function Cat(name) {
  Animal.call(this, name) // Вызов родительского конструктора
  this.type = 'Кот'
  this.paws_number = 4 // У котов всегда 4 лапы, поэтому значение будет по умолчанию
}

// Связываем дочерние конструкторы с родительскими
Fish.prototype = Object.create(Animal.prototype)
Cat.prototype = Object.create(Animal.prototype)

// Создаём экземпляры
var myFish = new Fish('Димон', 5)
var myCat = new Cat('Борис')

console.log(myFish.type + ' ' + myFish.name + ' имеет ' + myFish.fins_number + ' плавников')
console.log(myCat.type + ' ' + myCat.name + ' имеет ' + myCat.paws_number + ' лапы')

// Рыба Димон имеет 5 плавников
// Кот Борис имеет 4 лапы
```
### Определение методов
Допустим, имеется конструктор с публичными методами `getName` и `getMessage`:
```javascript
function MyObject(name, message) {
  this.name = name
  this.message = message

  this.getName = function() {
    return this.name
  };

  this.getMessage = function() {
    return this.message
  };
}
```
Для каждого экземпляра этого конструктора будут созданы свои экземпляры методов.

**Prototype** позволяет создать экземпляры методов один раз и наследовать их от прототипа:
```javascript
function MyObject(name, message) {
  this.name = name
  this.message = message
}

MyObject.prototype.getName = function() {
  return this.name
};

MyObject.prototype.getMessage = function() {
  return this.message
};
```
Для красоты можно обернуть определение методов в замыкание и вызвать на прототипе объекта с помощью метода `call`:
```javascript
function MyObject(name, message) {
    this.name = name
    this.message = message
}

(function() {
    this.getName = function() {
        return this.name
    };

    this.getMessage = function() {
        return this.message
    };
}).call(MyObject.prototype)
```