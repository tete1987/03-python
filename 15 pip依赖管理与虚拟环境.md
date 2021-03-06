# 十五、pip依赖管理与虚拟环境
## （一）pip介绍
- pip是python中的标准管理器。它允许你安装和管理不输入python标准库的其他软件包。
- python3的3.4版本及python2的2.7.9版本开始，pip被直接包括在python的安装包内。
- pypi托管了大量非常流行的库（www.pypi.org）。

1.安装包

pip install 报名==版本号

```
例：
pip install selenium==2.39.0
```

pip install i 镜像地址 --trusted-host 镜像地址对应的host

```
例：
pip3 install jupyter -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com
```


国内的pip源：
- 阿里云：http://mirrors.aliyun.com/pypi/simple
- 清华：https://pypi.tuna.tsinghua.edu.cn/simple
- 豆瓣：http://pypi.douban.com/simple

2.pip使用介绍
- pip help：帮助
- pip install：安装
- pip install -U 包名：升级包
- pip unistall：卸载
- pip list：列出所有的包文件
- pip download：下载包
- pip search requeset：搜索包

3.创建一个干净的虚拟环境

3.1 在cmd中创建的方法：
```
python -m venv tutorial-env
```

注：tutorial-env 是虚拟环境名称

- https://docs.python.org/3/tutorial/index.html
- https://docs.python.org/3/tutorial/venv.html

启动创建完成之后，启动的方法：

1）Windows环境：
```
tutorial-env\Scripts\activate.bat
```
2）Unix或 Mac环境：
```
source tutorial-env/bin/activate
```

![pip1](https://github.com/tete1987/picture_resource/blob/master/python%E5%9B%BE/pip1.png)

3）启动环境之后，可以使用pip list查看该环境下安装的包

4）退出该虚拟环境可在命令行中直接输入：deactivate

3.2在pycharm中创建新项目时选择 New environment using选项即可创建一个干净的环境：

![pip2](https://github.com/tete1987/picture_resource/blob/master/python%E5%9B%BE/pip2.png)

