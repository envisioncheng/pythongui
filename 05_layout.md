## 布局

GUI的布局就是如何在窗口中安排组件.


组件能被安排进 "容器" (e.g. `App`, `Window`, `Box`) 使用下边两种层排布:

+ `auto` - 组件自动排列
+ `grid` - you specify where in a grid each widget should be positioned

层设置使用 `layout` 作为容器的参数, 例如:

```python
app = App(layout="auto")
app = App(layout="grid")
```

如果没有 `layout` 参数指定,默认使用 `auto` 局.

### 自动布局

 I当容器被创建时,`auto` 被当作默认布局使用. 所有的组件被顺序安排对齐居中当创建时. 例如, 下边的代码将创建两个 `Text` 组件,一个在另一个之上.

```python
from guizero import App, Text
app = App()
text_1 = Text(app, text="on top")
text_2 = Text(app, text="below")
app.display()
```

![Text on top and below](https://image.csmicrobit.club/guizero/05_00.png)

### 对齐方式

组件对齐方式有 `top`, `bottom`, `left` 或者 `right`, 使用 `align` 属性当创建时.

例如，对齐组件将导致它“卡住”在容器的那一侧:

```python
from guizero import App, Text
app = App()
top_text = Text(app, text="at the top", align="top")
bottom_text = Text(app, text="at the bottom", align="bottom")
left_text = Text(app, text="to the left", align="left")
right_text = Text(app, text="to the right", align="right")
app.display()
```

![Text aligned at each edge](https://image.csmicrobit.club/guizero/05_01.png)

通过将多个组件对齐到容器的同一侧，组件可以堆叠在一起:

```python
from guizero import App, Text, TextBox, PushButton
app = App()
text = Text(app, text="label", align="left")
text_box = TextBox(app, text="enter text", align="left")
button = PushButton(app, text="submit", align="left")
app.display()
```

![Widgets stacked at the side](https://image.csmicrobit.club/guizero/05_02.png)

组件将按照它们创建的顺序堆叠，因此首先创建的组件将在指定的方向上最接近边缘

###

组件也可以通过设置“宽度”和“高度”参数来“填充”所有可用的空间。以下是一些例子

一个 `TextBox` 可以跨越容器的整个宽度:

```python
from guizero import App, TextBox
app = App()
text_box = TextBox(app, text="enter text", width="fill")
app.display()
```

![A text box filling the width of the screen](https://image.csmicrobit.club/guizero/05_03.png))

或者一个 `ListBox` 可以用 `fill` 来填充“高度”和“对齐”到“左边”

```python
from guizero import App, ListBox
app = App()
list_box = ListBox(app, items=["a list"], height="fill", align="left")
app.display()
```

![List box spanning the whole left edge](https://image.csmicrobit.club/guizero/05_04.png)

将`fill`用作`width`和`height`将使组件使用所有可用空间：

```python
from guizero import App, PushButton
app = App()
button = PushButton(app, width="fill", height="fill")
app.display()
```

![Button filling the whole window](https://image.csmicrobit.club/guizero/05_05.png)

当多个组件使用 `fill` 时，窗口管理器（操作系统）将在所有要求填充它的窗口组件之间相应地分配空间

```python
from guizero import App, ListBox, PushButton
app = App()
list_box = ListBox(app, items=["a list", "of items", "yay"], height="fill", align="left")
button = PushButton(app, width="fill", height="fill", align="right")
app.display()
```

![Two widgets filling the space](https://image.csmicrobit.club/guizero/05_06.png)

**注意 :** 使用填充可能并不总能获得预期的效果，因为取决于操作系统分配屏幕空间。

## 网格布局

网格布局允许您将组件放置在虚拟网格中。

创建窗口组件时，您需要传递一个名为`grid`的额外参数，该参数是一个包含`[x，y]`坐标的列表，用于您希望窗口组件出现的位置，如下所示


```python
app = App(layout="grid")
text = Text(app, text="Hello world", grid=[0,1])
```
不需要指定您想要的网格的宽度或高度——它将根据您为每个组件提供的坐标展开。然而，不包含对象的网格单元格将没有高度或宽度

这在创建窗口组件排成一行的GUIs时非常有用

例如，您可以创建一个数字键盘：

![Number keypad with 10 buttons](https://image.csmicrobit.club/guizero/05_07.png)

```python
from guizero import App, PushButton

app = App(layout="grid")

button1 = PushButton(app, text="1", grid=[0,0])
button2 = PushButton(app, text="2", grid=[1,0])
button3  = PushButton(app, text="3", grid=[2,0])
button4  = PushButton(app, text="4", grid=[0,1])
button5  = PushButton(app, text="5", grid=[1,1])
button6  = PushButton(app, text="6", grid=[2,1])
button7  = PushButton(app, text="7", grid=[0,2])
button8  = PushButton(app, text="8", grid=[1,2])
button9  = PushButton(app, text="9", grid=[2,2])
button0  = PushButton(app, text="0", grid=[1,3])

app.display()
```

还可以在网格中对齐组件，这在创建表单时非常有用


![Form data entry layout](https://image.csmicrobit.club/guizero/05_08.png)

```python
from guizero import App, Text, TextBox

app = App(layout="grid")

name_label = Text(app, text="Name", grid=[0,0], align="left")
name = TextBox(app, grid=[1,0])
surname_label = Text(app, text="Surname", grid=[0,1], align="left")
surname = TextBox(app, grid=[1,1])
dob_label = Text(app, text="Date of Birth", grid=[0,2], align="left")
dob = TextBox(app, grid=[1,2])

app.display()
```

### 跨越列或行

通过在网格参数中指定跨度，可以使组件跨越多个列或行。它们是可选的，但如果指定了它们，则必须使用该格式包含它们 `[x,y,xspan,yspan]`.

下边的例子显示 `Text` 组件在 0,1 和跨越两列(x) 和一行 (y):

```python
text = Text(app, text="Hello world", grid=[0,1,2,1])
```

这种网络布局方法能够被用于包含不同尺寸的组件安排在一起.

```python
from guizero import App, Picture

app = App(layout="grid")

picture1 = Picture(app, image="std1.gif", grid=[0,0])
picture2 = Picture(app, image="std2.gif", grid=[1,0])
picture3 = Picture(app, image="tall1.gif", grid=[2,0,1,2])
picture4 = Picture(app, image="wide1.gif", grid=[0,1,2,1])

app.display()
```

![Images laid out on a grid with various spans](https://image.csmicrobit.club/guizero/05_09.png)

## Boxes

使用 `Box` 组件,你可以将GUI分割成不同的部分，从而可以以任何您想要的方式布置用户界面。

![Layout with multiple boxes](https://image.csmicrobit.club/guizero/05_10.png)

([Code for example above](https://github.com/lawsie/guizero/tree/master/examples/layout_boxes.py))


如果你想在你的GUI的左上角创建一个标题，你可以使用一个 `Box` 填充 `App` 的顶部，并在 `Text` 小部件内部对齐到  `left`。

```python
from guizero import App, Box, Text
app = App()

title_box = Box(app, width="fill", align="top")
title = Text(title_box, text="title", align="left")

app.display()
```

![Title at the top](https://image.csmicrobit.club/guizero/05_11.png)


如果你的盒子有边框，你可能会发现设计布局更容易,通过在 `Box` 设置`border` 参数为 `True`.


```python
title_box = Box(app, width="fill", align="top", border=True)
```

![Title at the top, in a box](https://image.csmicrobit.club/guizero/05_12.png)


一个相似的方法能够被使用把"确定"和"取消"按钮在界面的底右部.记注组件被堆叠在右按创建的顺序,所以取消按钮首先被创建.

```python
from guizero import App, Box, PushButton
app = App()

buttons_box = Box(app, width="fill", align="bottom")
cancel = PushButton(buttons_box, text="Cancel", align="right")
ok = PushButton(buttons_box, text="OK", align="right")

app.display()
```

![OK and Cancel buttons on the bottom right](https://image.csmicrobit.club/guizero/05_13.png)

**注意 :** 你能够把一个盒子放入另一个盒子, 允许你布局盒子和组件的位置.

**提示 :** 当创造一个界面你可能发现,先在纸上设计会容勿很多, 注意你的盒子将被放置的位置.

![hand drawn gui](https://image.csmicrobit.club/guizero/05_14.png)

不幸的是,但guizero不支持邮寄给你自己，也不支持用锤子砸它.