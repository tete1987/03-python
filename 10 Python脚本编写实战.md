# 十、Python脚本编写实战
## 1.大纲：
1）使用面向对象方法实现编写一个简单的回合制小游戏

2）使用面向对象的继承改造游戏

3）加入模块化、异常优化代码

## 2.游戏解读：
1）一个回合制游戏，每个角色都有hp 和power ，hp代表血量，power代表攻击力，hp的初始值为1000，power 的初始值为200.

2）定义一个fight 方法：
- final_hp = hp - enemy_power
- enemy_final_hp = enemy_hp - power
 
两个hp 进行对比，血量剩余多的人获胜
```
#定义game 类
class Game:
    def __init__(self,hp,power):
        self.hp =hp
        self.power = power

    def fight(self,enemy_hp,enemy_power):
        final_hp = self.hp - enemy_power
        enemy_final_hp = enemy_hp - self.power
        if final_hp > enemy_final_hp:
            print("我赢了")
        elif final_hp < enemy_final_hp:
            print("对方赢了")
        else:
            print("平局")

#对hp 和power 进行初始化定义
hp = 1000
power = 200

#实例化类
game = Game(hp,power)
#调用方法
game.fight(3000,400)
```

3）增加第二个角色，他叫后裔，后裔继承了角色的hp和power ，并多了护甲属性。
```
houyi_hp = hp +defense-enemy_power
示例：
class Game:
     def __init__(self,hp,power):
 
         self.hp =hp
         self.power = power
 
class HouYi(Game):
     def __init__(self):
         super().__init__(1000,200)
         self.defense = 100
 
     def houyi_fight(self,enemy_hp,enemy_power):
         final_hp = self.hp +self.defense - enemy_power
         enemy_final_hp = enemy_hp - self.power
         if final_hp > enemy_final_hp:
             print("我赢了")
         elif final_hp < enemy_final_hp:
             print("对方赢了")
         else:
            print("平局")
 
 
# 实例化类
houyi = HouYi()
 
# 调用方法
houyi.houyi_fight(200,100)

```
3）代码优化2：
- 加入模块的改造：将类houyi 与类角色通过两个文件夹的文件管理
- 加入异常的改造：当平局时，抛出一个异常

![python模块导入](https://github.com/tete1987/picture_resource/blob/master/python%E6%A8%A1%E5%9D%97%E5%AF%BC%E5%85%A5.png)

```
import lessons
from lessons.game.game import  Game

class HouYi(Game):
    def __init__(self):
        super().__init__(1000,200)
        self.defense = 100

    def houyi_fight(self,enemy_hp,enemy_power):
        final_hp = self.hp +self.defense - enemy_power
        enemy_final_hp = enemy_hp - self.power
        if final_hp > enemy_final_hp:
            print("我赢了")
        elif final_hp < enemy_final_hp:
            print("对方赢了")
        else:
            print("平局")

```

优化游戏，更改为循环模式：
```
import lessons
from lessons.game.game import  Game

class HouYi(Game):
    def __init__(self):
        super().__init__(1000,200)
        self.defense = 100

    def houyi_fight(self,enemy_hp,enemy_power):
        final_hp = self.hp +self.defense - enemy_power
        enemy_final_hp = enemy_hp - self.power
        if final_hp > enemy_final_hp:
            print("我赢了")
        elif final_hp < enemy_final_hp:
            print("对方赢了")
        else:
             print("没有平局")


平局时抛出异常：
import lessons
from lessons.game.game import  Game

class HouYi(Game):
    def __init__(self):
        super().__init__(1000,200)
        self.defense = 100

    def houyi_fight(self,enemy_hp,enemy_power):
        final_hp = self.hp +self.defense - enemy_power
        enemy_final_hp = enemy_hp - self.power
        if final_hp > enemy_final_hp:
            print("我赢了")
        elif final_hp < enemy_final_hp:
            print("对方赢了")
        else:
            raise Exception("没有平局")
```

增加braek
```
class HouYi(Game):
    def __init__(self):
        super().__init__(1000,200)
        self.defense = 100

    def houyi_fight(self,enemy_hp,enemy_power):
        while True:
            self.hp = self.hp +self.defense - enemy_power
            enemy_hp = enemy_hp - self.power
            print(self.hp)
            if self.hp <=0:
                print("我输了")
                break
            elif enemy_hp <= 0:
                print("敌人输了")
                break

enemy_hp = 8000
enemy_power = 500

houyi = HouYi()
houyi.houyi_fight(enemy_hp,enemy_power)

```
