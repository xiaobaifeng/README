## js new关键字：
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
