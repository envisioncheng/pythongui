# 安装,有3种方法

guizero是为初学者快速且容易创造图形界面程序而设计的

1. 你可以直接下载压缩文件,进行简易安装 - **无需超级管理员权限**
2. 如果你拥有操作系统的超级管理员权限且能联网,可以通过 pip 安装和更新 guizero(推荐)
3. windows用户可以使用安装包直接安装

## 方法一:简易方法安装
1. 打开[guizero repository](https://github.com/lawsie/guizero) on GitHub.

2. 点绿色的按钮"Code",然后点"Download ZIP"

    ![Download the zip](https://image.csmicrobit.club/guizero/01_00.png)

3. 解压zip文件

4. 打开 `guizero-master` 文件夹,然后拷贝`guizero` 文件夹,粘贴到你的用户home目录

    + Windows

     ![Copy the guizero folder in windows](https://image.csmicrobit.club/guizero/01_01.png)

    + macOs

     ![Copy the guizero folder in macos](https://image.csmicrobit.club/guizero/01_02.png)

5. 就这是全部! 当你写guizero代码,确保存在你的home目录.

## 方法二:使用pip安装

你可以使用命令行和 `pip`安装为以下平台guizero:

+ [Windows](#windows)
+ [macOS](#macos)
+ [Raspberry Pi](#raspberry-pi)
+ [Linux](#linux)

### Windows

1. 打开命令行,点 **开始** > **系统** > **命令行**, 或者输入'command'在开始菜单的搜索栏

    ![windows command prompt](https://image.csmicrobit.club/guizero/01_03.png)

2. 输入以下的命令,按回车键:

    ```
    pip3 install guizero
    ```

![windows pip install](https://image.csmicrobit.club/guizero/01_04.gif)

如果你以pip不熟,可以参考这个教程 [_Using pip on Windows_](https://projects.raspberrypi.org/en/projects/using-pip-on-windows).



### macOS

1. 点击 **Applications** > **Utilities** > **Terminal**打开终端, 输入 'terminal' 在桌面搜索栏.

    ![Mac terminal](https://image.csmicrobit.club/guizero/01_05.png)

2. 输入以下命令并回车

    ```
    pip3 install guizero
    ```

    ![mac pip install](https://image.csmicrobit.club/guizero/01_06.gif)

### Raspberry Pi

1. 点击**Menu** > **Accessories** > **Terminal**打开终端.

    ![pi terminal](https://image.csmicrobit.club/guizero/01_07.png)

2. 输入以下命令并回车:

    ```
    sudo pip3 install guizero
    ```

    ![run pip install guizero](https://image.csmicrobit.club/guizero/01_08.gif)

### Linux

1. 打开终端
2. 安装 `tkinter` 使用发行版的包管理工具, e.g. `sudo apt install python3-tk`
3. 安装 guizero 使用 pip 输入 `pip3 install guizero` or `sudo pip3 install guizero` if you don't have superuser rights

    ![linux pip install](https://image.csmicrobit.club/guizero/01_09.gif)

**Note:** 如果你用Debian, 你也可以选择通过apt安装guzero
`sudo apt-get install python-guizero`

### 安装附加功能

使用guizero 像 [image features](images.md) 此类的附加功能:

- JPG image support
- scaling images
- animated gifs

... 你需要安装guizero使用pip命令:

- Windows / macOS

    ```
    pip3 install guizero[images]
    ```

- Linux / Raspberry Pi

    ```
    sudo pip3 install guizero[images]
    ```

附加功能 image 不可以使用通过第一种简易安装的方法.

### 更新 guizero

如果你使用pip安装guizero, 你可以使用pip命令更新guizero:

- Windows / macOS

    ```
    pip3 install guizero --upgrade
    ```

- Linux / Raspberry Pi

    ```
    sudo pip3 install guizero --upgrade
    ```

如果你通过简易方法安装installed, 你应该按简易方法的安装步聚去下载最新版本guizero,然后删除旧版本,并用新的版本进行取代.

## 方法三:Windows安装包安装(Windows MSI installer)

如果你使用Windows,你可通过下载和运行windows MSI 安装包安装guizero.

1. 下载 [64位 guizero 安装包](https://github.com/lawsie/guizero/releases/latest/download/guizero-1.1.1.amd64.msi) 或者 [32位 guizero 安装包](https://github.com/lawsie/guizero/releases/latest/download/guizero-1.1.1.win32.msi) 取决你安装python的版本.

    **注意:** 如果你不能确定你正在使用哪一个版本的python, 在python里使用以下的程序, 将会输出 `32` 或 `64`:

        import struct
        print(struct.calcsize("P") * 8)

2. 运行guizero安装包和先择guizero是否被安装 ***为所有人*** or ***仅自已*** 然后点 **下一步**.

    ![windows msi installer step 1](https://image.csmicrobit.club/guizero/01_10.png)

3. 选择使用哪一个版本python安装guizero,然后点 **下一步**.

    ![windows msi installer step 2](https://image.csmicrobit.club/guizero/01_11.png)

    **注意:** 对于大多数人, 只有一个版本的Python,你可以安全的选择默认的选项.

4. 你将被问到 *"您希望允许来自未知发行者的应用程序对您的设备进行更改吗?"* - 点 **确定**.

5. 等待guizero安装完成.

    ![windows msi installer step 3](https://image.csmicrobit.club/guizero/01_12.png)

6. 当安装完成后,点 **完成**.

    ![windows msi installer step 4](https://image.csmicrobit.club/guizero/01_13.png)