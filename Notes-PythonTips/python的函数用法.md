https://www.cnblogs.com/LearningOnline/p/8512041.html

### 如何定义一个类

```python
class A:
    v = 0 # 类变量（静态变量），通过类名来调用
    def __init__(self,name,age): # 在类对象被实例化时执行
        self.value = [] # 对象变量，由对象调用
        self.name = name
        self.age = age
        
    def fun(self,a): # 动态属性（方法）
        print("执行")
```

### 如何实例化一个对象

```python
obj = A('Rachel',21) # 创建一个对象，会自动触发__init__方法
print(obj.__dict__['name']) # 使用__dict__可以打印变量值
print(obj.name) # 一般如下写法
print(obj) # 打印的是对象的内存地址
```

类可以嵌套使用，即在一个类中定义另一个类的实例对象

```
类名.__name__``# 类的名字(字符串)
类名.__doc__``# 类的文档字符串
类名.__base__``# 类的第一个父类(在讲继承时会讲)
类名.__bases__``# 类所有父类构成的元组(在讲继承时会讲)
类名.__dict__``# 类的字典属性，key为属性名，value为属性值
类名.__module__``# 类定义所在的模块
类名.__class__``# 实例对应的类 
```

###python内继承分为单继承和多继承，基本形式：

```python
class Parent1:  # 定义父类
    pass

class Parent2:  # 定义父类
    pass

class Son1(Parent1):  # 单继承，基类（父类，超类）是Parent1，派生类（子类）是Son
    pass

class Son2(Parent1, Parent2):  # 多继承，用逗号分隔开多个继承的类
    pass
 
print(Son1.__bases__)   # (<class '__main__.Parent1'>,)
print(Son2.__bases__)   #查看所有继承的父类 (<class '__main__.Parent1'>, <class '__main__.Parent2'>)
print(Parent1.__base__)  # 查看单个继承的父类<class 'object'>

# 在python3中，所有的类都会默认继承object类
# 继承了object类的所有类都是新式类
# 如果一个类没有继承任何父类，那么__base__就会显示<class 'object'>
```

**继承中的派生：子类在继承父类的属性基础下，也可以重新定义一些属性，如果重新定义的属性（或方法）与父类的相同，则会覆盖父类的属性（或方法），优先执行自己定义的。**

 super().__init__(name, hp, ad)

```python
`class` `Animal:``    ``def` `__init__(``self``, name, hp, ad):``        ``self``.name ``=` `name    ``# 三个属性``        ``self``.hp ``=` `hp  ``# 血量``        ``self``.ad ``=` `ad  ``# 攻击力` `    ``def` `eat(``self``):   ``# 方法``        ``print``(``'eating in Animal'``)``        ``self``.hp ``+``=` `20` `class` `Person(Animal):``    ``def` `__init__(``self``, name, hp, ad, sex):``        ``# Animal.__init__(self, name, hp, ad) ``        ``#super(Person, self).__init__(name, hp, ad)``        ``# 在单继承中，super负责找到当前类所在的父类，这个时候就不需要再手动传self``        ``super``().__init__(name, hp, ad)    ``# 这个比较常用``        ``self``.sex ``=` `sex     ``# 派生属性``        ``self``.money ``=` `100`   `# 给属性中再增添一个新技能``    ` `    ``def` `attack(``self``, dog):   ``# 派生方法``        ``print``(``"%s攻击了%s"` `%` `(``self``.name, dog.name))``        ` `    ``def` `eat(``self``):     ``# 重写``        ``# super().eat()``        ``# 在类内使用super()方法找父类的方法,这样调用子类时可以同时实现父类eat方法``        ``print``(``'eating in Person'``)``        ``self``.money ``-``=` `50`
```

**@property（实现了将方法伪装成属性）**

```python
a = A('alex')
print(a.__dict__)  # {'name': 'alex'}
setattr(a, 'age', 18)  # 给a对象新增一个属性
print(a.__dict__)  # {'age': 18, 'name': 'alex'}
setattr(a, 'name', 'egon')
print(a.__dict__)  # {'age': 18, 'name': 'egon'}
delattr(a, 'age')
print(a.__dict__)  # {'name': 'egon'}
```

输入：varia = input('>>>')

