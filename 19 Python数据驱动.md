# 十九、Python数据驱动
## （一）数据驱动简介
### 1.概念：
数据驱动就是数据的改变从而驱动自动化测试的执行，最终引起测试结果的改变。简单来说，就是参数化的应用。数据量小的测试用例可以使用代码的参数化来实现数据驱动，数据量大的情况下建议大家使用一种结构化的文件（例如yaml，json等）来对数据进行存储，然后在测试用例中读取这些数据。

### 2.应用场景

#### 1）App、Web、接口自动化
- 测试步骤的数据驱动
- 测试数据的数据驱动
- 配置的数据驱动

示例：

1.首先建立一个env.yaml文件，内容为：
```
test : 192.168.125.124
```

2.调用该文件：
```python
import pytest
import yaml
class TestCs():
    @pytest.mark.parametrize("env",yaml.safe_load(open("./env.yaml")))
    def test_cs(self,env):
        if "test" in env:
            print("这是测试环境")
            print(env)
        if "dev" in env:
            print("这是正式环境")
```
3.出现一个文件，打印env时只显示了“test”，没有显示后面的ip地址，原因是如果yaml文件中是字典格式，则只打印key值，只有列表格式才可以全部打印，所以需要修改yaml文件：
```
-
  test : 192.168.125.124
```

优化代码：
```python
import pytest
import yaml
class TestCs():
    @pytest.mark.parametrize("env",yaml.safe_load(open("./env.yaml")))
    def test_cs(self,env):
        if "test" in env:
            print("这是测试环境")
            print("测试环境的IP地址是：",env["test"])
        if "dev" in env:
            print("这是正式环境")

```
