## 多窗体

一个guizero程序应该只有一个单一的[App](app.md)对象 - 这是主窗体控制你的程序.

如果你想创造2个或3个,4个,5个窗体,你的程序应该使用[Window](window.md)对像.

### 第二窗体

当你他创建第2个 `窗体Window` 你需要传递给 `App`, 就像你创建组件一样:

```python
from guizero import App, Window

app = App(title="Main window")
window = Window(app, title="Second window")

app.display()

```

添加组件到第二个窗体与添加组件到App一样. 您通过将窗体名称传递给窗体组件，以告知窗口组件将进入哪个窗体：

```python
from guizero import App, Window, Text

app = App(title="Main window")
window = Window(app, title="Second window")
text = Text(window, text="This text will show up in the second window")

app.display()

```

### 打开和关闭窗体

当窗体对创建马上显上在屏幕. 你能控制窗体是否显示或隐藏通过`show()` 和 `hide()` 方法.

下边的代码是点在`App` 的按钮按下创建一个窗体并显示和当在 `Window`.的按钮按下关闭

```python
from guizero import App, Window, PushButton

def open_window():
    window.show()

def close_window():
    window.hide()

app = App(title="Main window")

window = Window(app, title="Second window")
window.hide()

open_button = PushButton(app, text="Open", command=open_window)
close_button = PushButton(window, text="Close", command=close_window)

app.display()
```

### 模态窗体

当窗体使用 `show()` 打开,它与主窗体并排显示, 两个窗体能够被同时使用.

一个 "模态" 窗体阻止另一个窗体在程序内被使用直到它关闭. 创建模态窗体,你在`show`里边传一个可选参数`wait`为`True` .

这净压迫所有的窗体等待直到这个窗体被关闭,其它窗体才能被使用.

```python
def open_window():
    window.show(wait=True)
```
