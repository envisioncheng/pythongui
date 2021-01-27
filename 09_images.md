## 图像

像 [Picture](picture.md) 和 [PushButton](pushbutton.md) 的组件允许你使用图象在GUI.

```python
from guizero import App, Picture
app = App()
picture = Picture(app, image="test.gif")
app.display()
```

这些类型的图像 (GIF, JPG, PNG, etc) 被支持取决你安在计算机安装的 [installed guizero](index.md).

### 支持的文件类型

所有的系统支持 `GIF` 文件类型.

Windows 和 Linux 全部支持 `PNG` 文件.

如果你使用`pip` [安装附加的图形特性](index.md#additional-features-install),它将跟随安装 `PIL` (Python 图形库),然后你将能够使用主流的图像类型.

guizero 将告诉你什么类型的文件类型被支持在你的电脑使用下边的代码:

```python
from guizero import system_config
print(system_config.supported_image_types)
```

| 操作系统         | PIL 不可用         | PIL 可用                              |
|------------------|-------------------|--------------------------------------------|
| Windows          | GIF, PNG          | GIF, Animated GIF, BMP, ICO, PNG, JPG, TIF |
| MacOS            | GIF               | GIF, Animated GIF, BMP, ICO, PNG, JPG, TIF |
| Linux            | GIF, PNG          | GIF, Animated GIF, BMP, ICO, PNG, JPG, TIF |
| Raspbian         | GIF, PNG          | GIF, Animated GIF, BMP, ICO, PNG, JPG, TIF |

### 变形

当组件的尺寸改变图像的尺寸也改变适应组件. 如果附加图像特性被安装,且 `PIL` 可用, 图像将被伸缩正确, 如果没有图像将被裁剪.

### 动画 GIFs

如果 `PIL` 被安装在 guizero 将支持显示 GIFs, 如果没有安装, GIF 图像将显示为静态图像.
