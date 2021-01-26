## 颜色

你能设置颜色在guizero 使用:

- 颜色的名字 - `white`
- 一个#rgb hex值 - `#ffffff`
- 一组rgb值 - `(255,255,255)`

颜色能够被作为开始的参数, 例如:

```python
app = App(bg = "red")
app = App(bg = "#ff0000")
app = App(bg = (255, 0, 0))
```

或者作为属性, 例如:

```python
text = Text(app, text = "hi")
text.text_color = "green"
text.text_color = "#00ff00"
text.text_color = (0, 255, 0)
```

如果一个颜色被设置为一组rbg值 (`(255,255,255)`) 它将被返回一个#rgb hex值(`#ffffff`)

### 颜色名称

一些颜色的名字能被作为字符, 例如

- `white`
- `black`
- `red`
- `green`
- `blue`
- `yellow`

一组完整的可用颜色名字在这里 [wiki.tcl.tk/37701](https://wiki.tcl.tk/37701)

### rgb hex 值

一个 rgb 颜色值以 `#` 开始和接着6个字符, 每两个为红, 绿和蓝值用 hex. 每个值为 `00` - `ff`. 这是一些例子:

- white = `#ffffff`
- black = `#000000`
- red = `#ff0000`
- green = `#00ff00`
- blue = `#0000ff`
- yellow = `#ffff00`

你能混合你拥有的颜色通过改变红,绿和蓝值.

这是一个 RGB 计算程序在 [https://www.w3schools.com/colors/colors_rgb.asp](https://www.w3schools.com/colors/colors_rgb.asp) 在在在在这里你能创造拥有的颜色和得到 `#rrggbb` 值.

### rgb list

这组 `(red, green, blue)` 颜色必须顺序包含三个元素红,绿,蓝,每个值必须为 0 - 255. 这是一些例子:

- white = (255, 255, 255)
- black = (0, 0, 0)
- red = (255, 0, 0)
- green = (0, 255, 0)
- blue = (0, 0, 255)
- yellow = (255, 255, 0)
