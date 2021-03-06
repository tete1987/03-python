# 一、python语言基础
## （一）Python历史

![python历史](https://github.com/tete1987/picture_resource/blob/master/python%E5%8E%86%E5%8F%B2.png)

## （二）Python的安装
1.官方地址下载python安装包：https://www.python.org

python安装文档（Windows系统）：https://testing-studio.com/t/topic/57/4

2.安装完成之后python会默认启动比较老的2.x版本，可使用更改链接的方式自动执行最新3.x版本。

在cmd中输入：

`ln -f /user/local/bin/python3.8 /user/local/bin/python`

![pyhton-软连接](https://github.com/tete1987/picture_resource/blob/master/pyhton-%E8%BD%AF%E8%BF%9E%E6%8E%A5.png)


3.mac或linux环境修改环境变量：
```
cd user/local/bin
PATH
vim ~/.bash_profile
```

在文件中增加：
export PATH=$PATH:/user/local/bin

4.IDE：Pycharm

1）官方地址下载pyhcharm安装包：https://www.jetbrains.com/pycharm/download

5.pip依赖管理

1）pip介绍：

- pip是python中的标准管理器。它允许你安装和管理不输入python标准库的其他软件包。

- python3的3.4版本及python2的2.7.9版本开始，pip被直接包括在python的安装包内。

- pypi托管了大量非常流行的库（www.pypi.org）。

2）安装包

pip install 报名==版本号

例：pip install selenium==2.39.0

![python-安装selenium](https://github.com/tete1987/picture_resource/blob/master/python-%E5%AE%89%E8%A3%85selenium.png)

pip install i 镜像地址 --trusted-host 镜像地址对应的host

例：

`pip3 install jupyter -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com`


国内的pip源：
- 阿里云：http://mirrors.aliyun.com/pypi/simple
- 清华：https://pypi.tuna.tsinghua.edu.cn/simple
- 豆瓣：http://pypi.douban.com/simple
