```python
>>> assert True     # 条件为 true 正常执行
>>> assert False    # 条件为 false 触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError
>>> assert 1==1    # 条件为 true 正常执行
>>> assert 1==2    # 条件为 false 触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError

>>> assert 1==2, '1 不等于 2'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError: 1 不等于 2
>>>
```

assertions断言语法：

```python
assert expression[,arguments]
# 相当于
if not expression:
    raise AssertionError(arguments)
```

```python
try:
<语句>        #运行别的代码
except <名字>：
<语句>        #如果在try部份引发了'name'异常
except <名字>，<数据>:
# except(Exception1[, Exception2[,...ExceptionN]]]):
<语句>        #如果引发了'name'异常，获得附加的数据
else:
<语句>        #如果没有异常发生
```

- 以上是try except异常处理的用法

- except后可以不指定异常名，也可以带多种异常类型

- try-finally语句

  ```python
  try:
  <语句>
  finally:
  <语句>    #退出try时总会执行
  raise
  ```

- raise 自己触发异常

  raise语法格式如下：

  ```python
  raise [Exception [, args [, traceback]]]
  ```

