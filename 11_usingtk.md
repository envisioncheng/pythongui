## 使用tkinter

如果你是一个先进的使用者, 你能使用tkinter当使用guizero.

你能结合无缝使用 `guizero` 和 `tkinter` 在一个程序里 , 拿guizero简单先进的语法的同时依然能进入tkinter的全部函数如果你需要它.

### 使用tkinter组件在guizero里

你能增加tk组件进入 guizero app 使用 `add_tk_widget` 方法在 `App`, `Window` and `Box`.

在这个例子, 我们增加 tkinter 组件 `Spinbox` 在 guizero `App`:

```python
from guizero import App, Text
from tkinter import Spinbox

app = App()
text = Text(app, text="A Spinbox widget")

spinbox = Spinbox(from_=0, to=10)
app.add_tk_widget(spinbox)

app.display()
```

当增加一个tk组件 `Box` 或者 `Window` 你需要指定 `tk` 属性当创建tk组件时.

```python
box = Box(app)
spinbox = Spinbox(box.tk, from_=0, to=10)
box.add_tk_widget(spinbox)
```

### 使用tkinter方法在guizero对像

每个guizero组件它自已包含一个tk组件 - 你能发现哪一个像guizero组件在guizero文档. 例如, 一个 guizero `TextBox` 包含 tkinter `Entry` 对象. 你能进入内部对像使用语法 `<object_name>.tk`.

在这个例子, 我有一个e guizero `App` 和 `TextBox` 组件使用tk组件 `config` 方法去改变鼠标当经过 `TextBox` 时.

```python
from guizero import App, TextBox
app = App()
name = TextBox(app, text="Laura")
name.tk.config(cursor="target")
app.display()
```
