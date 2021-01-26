## 尺寸

你能设置guizero组件的 `width` 和 `height`.

组件的尺寸或者像素或尺寸被设置成像素或字符取决于组件所在的容器.

一些组件的尺寸能够被设置为 `"fill"` where it will use up all of the available space.

``` python
from guizero import App, PushButton, Slider, ListBox

app = App()

# A PushButton's size is noted in characters
button = PushButton(app, width=30, height=5)

# A Slider's size is noted in pixels
slider = Slider(app, width=300, height=30)

# Some widgets such as ListBox can also be told to fill all the available space
listbox = ListBox(app, width="fill", height="fill")

app.display()
```

| 组件                                    | 字符或像素 | 填充 | 注意事项                                                                  |
|----------------------------------------|----------------------|------|------------------------------------------------------------------------|
| [Box](box.md)                          | Pixels               | Yes  | 如果盒子的尺寸为像素, 长和宽都要设定.  |
| [ButtonGroup](buttongroup.md)          | Characters           | Yes  | ButtonGroup 的高度除以buttons 高度必须整除 |
| [CheckBox](checkbox.md)                | Characters           | Yes  |                                                                        |
| [Combo](combo.md)                      | Characters           | Yes  |                                                                        |
| [ListBox](listbox.md)                  | Pixels               | Yes  |                                                                        |
| [Picture](picture.md)                  | Pixels               | No   | 看更 [Images](images.md) 多的信息                           |
| [PushButton](pushbutton.md)            | Characters           | Yes  |                                                                        |
| [PushButton](pushbutton.md) with image | Pixels               | No   | PushButton's 有图像被设置为像素                     |
| [Slider](slider.md)                    | Pixels               | Yes  |                                                                        |
| [Text](text.md)                        | Characters           | Yes  |                                                                        |
| [TextBox](textbox.md)                  | Characters           | Yes  | 仅 TextBox's 宽度被设置                                    |
| [Waffle](waffle.md)                    | Pixels               | No   |                                                                        |
