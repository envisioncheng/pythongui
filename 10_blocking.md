## 循环和睡眠

你过去可能写程序使用循环或使用 `sleep()` 命令, 但你试图使用这些时 guizero 促使你的 GUI 冻结. 这是因为 guizero (大多数 GUIs 都是这样) 操作作为 **事件驱动** 是一个不同于你熟悉的程序模型.

你的第一个 guizero 程序可能像这样:

```python
from guizero import App
app = App("Hello world")
app.display()
```

这一行代码 `app.display()` 不仅仅显示app - 它进入一个 **无限事件循环** 观察和等待GUI事件的发生. 事件包含像用户点击按钮,移动边栏,输入在文本框. 这一行后没有写代码将不会执行，因为事件循环是无限的.

### 例子

假设您希望GUI上的计数器开始以每秒1的速度递增。您可能很想编写这样的程序:

```python
from guizero import App, Text
from time import sleep

app = App("Hello world")
text = Text(app, text="1")
while True:
    text.value = int(text.value) + 1
    sleep(1)
app.display()
```

如果你运行这个程序，你会发现这并没有达到预期的效果——你的程序崩溃了!这是因为您用两种方式阻止了GUI的更新

1. 这个 `sleep()` 命令 - 同时你的程序睡眠, 这个 GUI 将不更新而你不能够点击任何东西.

2. 这个 `while` 循环 - 一旦进入这个循环, 你的 GUI 将不在更新将可能崩溃.


### 解决方案

**这个行为不是一个guizero 或者 tkinter 的bug.**

你必须用另外一种方法写 GUI 基本程序. 如果你想重复性能一个操作你应该像下边这样做I:

1. 编写一个执行所需操作的函数 (这是一个例子 `counter()`)

2. 设置一个 **callback** 为这个函数. 您可以调度相同的回调在给定的毫秒数之后重复发生 (在这个例子 `1000`), 或者调度一次.

```python
from guizero import App, Text

# Action you would like to perform
def counter():
    text.value = int(text.value) + 1

app = App("Hello world")
text = Text(app, text="1")
text.repeat(1000, counter)  # Schedule call to counter() every 1000ms
app.display()
```
