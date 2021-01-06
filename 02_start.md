# 开始

在每一个guizero程序的开始, 从guizero库选择你要的组件,然后导入它:

```python
from guizero import App, PushButton, Slider
```

你仅需导入组件一次, 然后你就可以在你的程序多次使用,只要你愿意.

### Hello World

所有的guizero工程的开始主窗口叫 `App`. 在每一个程序的结尾,你必要让guizero程序显示你的app

让我们创造一个窗口标题为 "Hello world" 的 app:

```python
from guizero import App
app = App(title="Hello world")
app.display()
```

保存,然后运行代码 - 你已经完成创建第一个guizero app!

### 加放组件

组件是出现在图形界面(GUI)的一些东西, 像文本框(text boxes), 按钮(buttons), 边栏(sliders)和平面的一些文本.

**所有的组件** 应出在 `App` 和 `app.display()` 两行之间.

```python
from guizero import App, Text
app = App(title="Hello world")
message = Text(app, text="Welcome to the Hello world app!")
app.display()
```
![Hello world](images/hello-world.png)

看一看`Text`文本组件的更多详情:

```python
message = Text(app, text="Welcome to the Hello world app!")
```

- `message =` - `Text`对象有一个名字,就好像变量.
- `Text` - 一个*对象*创造一个些文字要界面.
- `app` – 告知`Text`的容器. 大多分情下你的组件将居住在app里边.
- `text="Welcome to the Hello world app!"` - 显示的文本

完成! 现在你可以看一下每一个组件文档,发现如何去使用他们.