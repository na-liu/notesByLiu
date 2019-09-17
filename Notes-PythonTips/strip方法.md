## python中strip()方法

des：用于<font color=red>删除</font>字符串<font color=red>**头尾指定字符**</font>或者字符序列。<font color=red></font>

grammar：

```python
str.strip([chars])
```

instances：

```python
str = '   d0d0d000ddsdfsdf0     '
print(str.strip())
# 结果：d0d0d000ddsdfsdf0【删去首尾的空格】
str = '0000000d0d0d000ddsdfsd000000'
print(str.strip('0'))
# 结果：d0d0d000ddsdfsd【删去首尾的字符0】
str = 'abbaabaad0d0ddabababsabb'
print(str.strip('ab'))
# 结果：0d0ddabababs【删去首尾的字符a和字符b】
```

rstrip()

lstrip()

分别对应删除右边和左边相应的指定元素