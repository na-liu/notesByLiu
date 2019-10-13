```python
# string，是一种区别于list的不可变类型，所以不能直接赋值改变某一位的值
# solve:可以直接string转为list

# string ---> list
list("12345") # 结果：['1', '2', '3', '4', '5']
# 下面的map函数可以将list的每一项映射成int类型
a = list(map(int, list("12345")))	# 结果：[1, 2, 3, 4, 5]

# list ---> string 
''.join(str(i) for i in a)
```