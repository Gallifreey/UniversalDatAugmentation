# UniversalDataAugmentation
一套庞大的数据增强方法。超过50种方法，而且还在增加。UDA（通用数据增强）是您所需要的一切！！！
# TODO

# 安装
如果你使用的是pip：
```
pip install universal-data-augmentation
```
或者使用的是conda：
```
conda install universal-data-augmentation
```
# 方法
## 1. 旋转(Rotation)
### 描述: 将图片以随机的角度旋转。
## 2. 平移(Translation)
### 描述: 将图片以特定方向平移(x方向、y方向或者两者均有)。
## 3. 错切(Shear)
### 描述: 将图片的一部分向一个方向拉伸，另一部分以相反的方向拉伸。
## 4. 翻转(Flip)
### 描述: 将图片水平或者垂直翻转(或者随机)。
## 5. 裁剪(Clip)
### 描述: 
## 6. 噪声(Noise)
### 描述: 为图片添加噪声。(支持椒盐噪声、高斯噪声、瑞利噪声、伽马噪声、指数噪声、均匀噪声)
## 7. 
### 描述: 
## 8. 扰动(Disturbance)
### 描述: 改变图像的亮度、对比度、饱和度及色调。
## 9. 核过滤(Kernal filter)
### 描述: 
## 10. Cutout
### 描述: 用随机颜色的像素填充图片的随机区域。
## 11. HAS
### 描述: 将图片分成$S×S(S≥5)$个网格，之后用随机颜色的像素填充随机数量的网格。
## 12. 网格掩码(Grid mask)
### 描述: 生成一个随机大小的$S×S(S≥3)$网格，每个网格之间有随机但固定的间隔，将此网格掩码与图像组合。
## 13. Local Augment
### 描述: 从所提供的数据增强操作列表中随机选择随机数目的操作来对输入的图像进行增强。
## 14. Self Augmentaion
### 描述: 
## 15. YOCO
### 描述:
## 16. Cut-Thumbnial
### 描述:
## 17. Mixup
### 描述:
## 18. CutMix
### 描述:
## 19. PuzzleMix
### 描述:
## 20. Fmix
### 描述:
## 21. Random Mix
### 描述:
## 22. RICAP
### 描述:
## 23. Cut Blur
### 描述:
## 24. CDA
### 描述:
## 更多数据增强方法正在不断添加。
# 自定义你的操作
你的操作必须继承```Operator```类。然后重载```process```函数。以下是一个例子。
## 例子(以图像翻转[Flip]为例)
```python
class Flip(Operator):
    def __init__(self):
        super().__init__()

    def process(self, img, process_type=0, p=0.5):
        img = img["image"]
        a = process_type
        if a == -1:
            a = np.random.choice([0, 1, 2], p=[p, 1 - p])
        if a:
            img = img[:, ::-1, :]
        else:
            img = img[::-1, :, :]
        out = {"image": img}
        return out
```
之后你就可以使用你自定义的操作。
# 快速查询
你可以使用下面的代码：
```python
import UniversalDataAugmentation as uda
print(uda.details())
```
以获得当前版本的所有支持的数据增强操作。
