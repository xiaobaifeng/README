# js new运算符：

## mdn 描述
  [new](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind#Description)

## code
```bash
  function Person (name, age) {
   this.name = name
   this.age = age
  }
  console.log('new ...', new Person('cwb', 27))
  var peopleOne = {}
  peopleOne.newPerson = Person.bind(peopleOne, 'cwb', 27)
  peopleOne.newPerson()
  delete peopleOne.newPerson
  console.log(peopleOne)
```
