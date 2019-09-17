##python中with的用法：

摘自：https://blog.csdn.net/ego_bai/article/details/80873242

有一些任务，需要提前做一些设置，完成任务后需要清理掉。python中的with提供了一种非常方便的处理方式。其中一个很好的例子是文件处理，<font color=red>你需要获取一个文件句柄，从文件中读取数据，然后关闭文件句柄。</font>

```python
file = open("a.txt")
data = file.read()
file.close()
```

这里有两个问题。一是可能忘记关闭文件句柄；二是文件读取数据发生异常，没有进行任何处理。下面是处理异常的加强版本：

```python
file = open("/tmp/foo.txt")
try:
    data = file.read()
finally:
    file.close()
```

这段代码运行良好，但是太冗长。这时候with便体现出了优势。 除了有更优雅的语法，with还可以很好的处理上下文环境产生的异常。下面是with版本的代码：

```python
with open("/tmp/foo.txt") as file:
    data = file.read()
```

### with的语法格式：

摘自：https://www.ibm.com/developerworks/cn/opensource/os-cn-pythonwith/

**with 语句的语法格式**

```python
with context_expression [as target(s)]:
	with-body
```

这里 context_expression 要返回一个上下文管理器对象，该对象并不赋值给 as 子句中的 target(s) ，如果指定了 as 子句的话，会将上下文管理器的 **\__enter__() 方法的返回值**赋值给 **target(s)**。target(s) 可以是单个变量，或者由“()”括起来的元组（不能是仅仅由“,”分隔的变量列表，必须加“()”）。

Python 对一些内建对象进行改进，加入了对上下文管理器的支持，可以用于 with 语句中，比如可以自动关闭文件、线程锁的自动获取和释放等。假设要对一个文件进行操作，使用 with 语句可以有如下代码： 2. 使用 with 语句操作文件对象

```python
with open(r'somefileName') as somefile:
    for line in somefile:
        print line
        # ...more code
```

这里使用了 with 语句，不管在处理文件过程中是否发生异常，都能保证 with 语句执行完毕后已经关闭了打开的文件句柄。

###with 语句执行过程

```python
context_manager = context_expression
exit = type(context_manager).__exit__  
value = type(context_manager).__enter__(context_manager)
exc = True   # True 表示正常执行，即便有异常也忽略；False 表示重新抛出异常，需要对异常进行处理
try:
    try:
        target = value  # 如果使用了 as 子句
        with-body     # 执行 with-body
    except:
        # 执行过程中有异常发生
        exc = False
        # 如果 __exit__ 返回 True，则异常被忽略；如果返回 False，则重新抛出异常
        # 由外层代码对异常进行处理
        if not exit(context_manager, *sys.exc_info()):
            raise
finally:
    # 正常退出，或者通过 statement-body 中的 break/continue/return 语句退出
    # 或者忽略异常退出
    if exc:
        exit(context_manager, None, None, None) 
    # 缺省返回 None，None 在布尔上下文中看做是 False
```

1. 执行 context_expression，生成上下文管理器 context_manager
2. 调用上下文管理器的 \__enter__() 方法；如果使用了 as 子句，则将 \__enter__() 方法的返回值赋值给 as 子句中的 target(s)
3. 执行语句体 with-body
4. 不管是否执行过程中是否发生了异常，执行上下文管理器的 \__exit\__() 方法，\__exit__() 方法负责执行“清理”工作，如释放资源等。如果执行过程中没有出现异常，或者语句体中执行了语句 break/continue/return，则以 None 作为参数调用 \__exit__(None, None, None) ；如果执行过程中出现异常，则使用 sys.exc_info 得到的异常信息为参数调用 \__exit\__(exc_type, exc_value, exc_traceback)
5. 出现异常时，如果\__exit__(type, value, traceback) 返回 False，则会重新抛出异常，让with 之外的语句逻辑来处理异常，这也是通用做法；如果返回 True，则忽略异常，不再对异常进行处理

### 文件读取

open函数用于打开一个文件，创建一个file对象。

grammar：

```python
open(name[,mode[,buffering]])
```

name：文件名称，路径

mode：默认是只读（r）

buffering：可以设置缓冲区大小

| 模式 | 描述                                                         |
| :--- | :----------------------------------------------------------- |
| r    | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。 |
| rb   | 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。 |
| r+   | 打开一个文件用于读写。文件指针将会放在文件的开头。           |
| rb+  | 以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。 |
| w    | 打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
| wb   | 以二进制格式打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
| w+   | 打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
| wb+  | 以二进制格式打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
| a    | 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| ab   | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| a+   | 打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。 |
| ab+  | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。 |

### file 对象方法

- **file.read([size])**：size 未指定则返回整个文件，如果文件大小 >2 倍内存则有问题，f.read()读到文件尾时返回""(空字串)。
- **file.readline()**：返回一行。
- **file.readlines([size])** ：返回包含size行的列表, size 未指定则返回全部行。
- **for line in f: print line** ：通过迭代器访问。
- **f.write("hello\n")**：如果要写入字符串以外的数据,先将他转换为字符串。
- **f.tell()**：返回一个整数,表示当前文件指针的位置(就是到文件头的比特数)。
- **f.seek(偏移量,[起始位置])**：用来移动文件指针。
  - 偏移量: 单位为比特，可正可负
  - 起始位置: 0 - 文件头, 默认值; 1 - 当前位置; 2 - 文件尾
- **f.close()** 关闭文件