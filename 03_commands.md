## 命令

在guzero中创建组件时，可以给它一个命令，在使用组件时，可以使用这个命令调用函数。

通过使用命令，您可以更改GUI，并在用户与GUI交互时采取行动，例如单击按钮、选择选项或输入消息。

### Example

当按钮被按下时，这段代码将显示` hello world `

```python
from guizero import App, Text, PushButton

def say_hello():
    text.value = "hello world"

app = App()
text = Text(app)
button = PushButton(app, command=say_hello)
app.display()
```
