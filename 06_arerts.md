# Pop-ups

可以通过询问问题或提供信息来打断用户的弹出窗口。

![Alert popup](https://image.csmicrobit.club/guizero/06_00.png)

### 使用弹出窗口
弹出窗口能被 `App` 或者 `Window` 对象调用,例如:

```python
app.info("info", "this is a guizero app")
```

弹出窗口能被独立导入在程序的开头,例如:

```python
from guizero import info
info("info", "this is a guizero app")
```

### 用途
这些函数弹出窗口在屏幕显示消息或询问.有以下可用函数

* `warn(title, text)` - 弹出警告窗口
* `info(title, text)` - 弹出信息提示窗口
* `error(title, text)` - 弹出错误窗口
* `yesno(title, text)` - 弹出是否选项. 按 `是` 返回 `True` 和按 `否` 返回 `False`.
* `question(title, text, initial_value=None)` - 接收一个文本参数响应的询问窗口. 按 `确定` 返回输入的文字,按 `取消` 返  `None`.
* `select_file(title="Select file", folder=".", filetypes=[["All files", "*.*"]], save=False)` - 询问用户选择文件的弹出文件窗口.默认, 一个 *打开* 按钮显示, 设置 `保存` 为 `True` 将改变按扭显示为 *另存为*. 选择到的文件路径将被函数返回.
* `select_folder(title="Select folder", folder=".")` - 询问用户选择文件夹弹出窗口.选择到的文件夹路径将被函数返回.

所有的弹出窗口都是本地显示, 所以根据你的操作系统需显示不同的外观.

### 例子

**警告窗口**

这个警告窗的标题是T `"Uh oh!"` 和消息是 `"You are almost out of biscuits!"`.

```python
from guizero import App
app = App(title="Biscuit monitor")
app.warn("Uh oh!", "You are almost out of biscuits!")
app.display()
```
在windows上,窗口显示的样子如下:

![Warning popup](https://image.csmicrobit.club/guizero/06_01.png)

 `info` 和 `error` 窗口做一样的工作,但是显示不同的图标.

**是/否 窗**

当这个函数被调用返回一个**布尔** 值.

* 如果 `是` 被按下, 返回 `True`
* 如果 `否` 被按下, 返回 `False`

你能够存这个值在变量里和测试它:

```python
from guizero import App
app = App(title="Snowman")
build_a_snowman = app.yesno("A question...", "Do you want to build a snowman?")
if build_a_snowman == True:
    app.info("Snowman", "It doesn't have to be a snowman")
else:
    app.error("Snowman", "Okay bye...")
app.display()
```

这些代码将第一个显示是/否 窗口

![Yes No popup](https://image.csmicrobit.club/guizero/06_02.png)

如 `是` 按下, 一个信息窗将显示:

![Info popup](https://image.csmicrobit.club/guizero/06_03.png)

如 `否` 按下, 一个警告窗将显示

![Info popup](https://image.csmicrobit.club/guizero/06_04.png)

**列子: 使用一回调出窗**

你参使用这些函数在 *回调* (当你需要为其它的组件提供一个函数时). 这是一个  `PushButton` 的例子,当它被按下时弹出一个 `信息` 窗.

```python
from guizero import App, PushButton, info
app = App()
button = PushButton(app, command=app.info, args=["Info", "You pressed the button"])
app.display()
```

提供给 `PushButton` 的参数是:

* 哪里按钮被创建 (在 `app` 里)
* 调用函数的名字当按下 (`info`) 窗时
* 调用函数的一个list的参数 (函数`info`的参数 `title` 和 `message` 的值)

**例子: 你真的需要关闭吗?**

你能用 `yesno` 窗口去检查某人是否真正想退出你的程序. 如果他们点确定, 关闭程序, 如果点否, 什么也不做,然后他们继续做他们想做的.

```python
from guizero import App, Text

# Ask the user if they really want to close the window
def do_this_when_closed():
    if app.yesno("Close", "Do you want to quit?"):
        app.destroy()

app = App()

title = Text(app, text="blank app")

# When the user tries to close the window, run the function do_this_when_closed()
app.when_closed = do_this_when_closed

app.display()

```

**列子: 询问问题**

你能用 `question` 窗口去接收用户的信息. 在这个例子里,用户被要求输入他们的名字当按钮按下.

```python
from guizero import App, PushButton, Text

def button_pressed():
    name = app.question("Hello", "What's your name?")
    # If cancel is pressed, None is returned
    # so check a name was entered
    if name is not None:
        hello.value = "Hello " + name

app = App()
button = PushButton(app, command=button_pressed, text="Hello")
hello = Text(app)
app.display()
```

![question popu](https://image.csmicrobit.club/guizero/06_05.png)

** 例子: 取得一个文件名**

询问用户去选一个文件用 `select_file` 窗口.

```python
from guizero import App, PushButton, Text

def get_file():
    file_name.value = app.select_file()

app = App()

PushButton(app, command=get_file, text="Get file")
file_name = Text(app)

app.display()
```

![select file popup](https://image.csmicrobit.club/guizero/06_06.png)

你能用一个list改变文件描述和类型进行过虑.
```python
file_name.value = app.select_file(filetypes=[["All files", "*.*"], ["Text documents", "*.txt"]])
```

默认显示 *打开* 按钮,  设置 `save` 参数为 `True` 能改变为 *别存为* .

```python
file_name.value = app.select_file(save=True)
```

![select save file popup](https://image.csmicrobit.club/guizero/06_07.png)

** 例子: 取得文件夹名**

选择一个文件夹使用 `select_folder` 窗口.

```python
from guizero import App, PushButton, Text

def get_folder():
    path.value = app.select_folder()

app = App()

PushButton(app, command=get_folder, text="Get path")
path = Text(app)

app.display()
```

![select folder popup](https://image.csmicrobit.club/guizero/06_08.png)

你能传递一个路径参数到 `folder` 来初始化文件夹.

```python
file_name.value = app.select_file(folder="c:\users\lawsie")
```
