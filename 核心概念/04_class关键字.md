****
### class关键字实现面向对象、继承新形式

```js
class Persons(name,age){
    this.name = name
    this.age=age

    person.prototype.sing=()=>{
        console.log('sing' )
    }
    person.info='123' //挂载载原型对象
}
var pt = new Persons('za',19)
console.log(person.info)
        
```


**区别**
  * 每个`class`内部都有一个constructor构造器,就好比`class Persons(name,age){}`
  作用是每当`new`的时候，就优先调用`constructor(){}`

  * 关联性更强

```js
class Persons{
    constructor(name,age){
         console.log(3)
         this.name = name
         this.age=age
     }
     //实例方法必须通过new对象调用
     say(){
        console.log('sing' )
     }
      static info='123'  //挂载在构造器
}
var pt = new Persons('za',19)
console.log(pt.say())
```

**继承**

```js  
class Persons{
    constructor(name,age){
         this.name = name
         this.age=age
     }
     //实例方法必须通过new对象调用
     say(){
        console.log('fu-sing' )
     }
}
class Chinese extends Person{
    constructor(color,lac){
         console.log(1)
         super(name,age)       //super表示父类中contructor引用
         this.color = color
         this.lac=lac
         console.log(2)
     }
}
var pt = new Persons('za',19)
console.log(pt)
var ct = new  Chinese('za',19,'pink','dd')
console.log(ct)
```

**真正面向对象语言是由三部分组成  封装、继承、多态**

多态和接口，虚拟方法有关，定义一个动物类,直接来个叫声，喵喵叫，不可能每个动物喵喵叫，小猫小狗继承动物类,动物类定义个叫声方法，但具体怎么叫看子类，
```js

class Animal {
    say(){

    }
}
class cats extends Animal {
    say(){
      console.log('miaomaio')
  
    }
}
```

当子类继承父类以后，必然要继承父类中的方法，但是，发现父类中的方法空有其壳，如果子类想要调用这个方法，必须自己实现这个方法