# UniversalDataAugmentation
A giant set of data augmentation methods. More than 50+ methods and increasing. UDA(Universal Data Augmentation) is ALL YOU NEED!!!
# TODO List

# Installation
If you use pip:
```
pip install universal-data-augmentation
```
Or use conda:
```
conda install universal-data-augmentation
```
# Method
## 1. Rotation
### Info: Rotate the image to a random angle.
## 2. Translation
### Info: Translate the image in a specific direction(x axis, y axis or both).
## 3. Shear
### Info: Move one part of the image in one direction and the other part in the opposite direction.
## 4. Flip
### Info: Flip the image horizontally or vertically(Or randomly).
## 5. Clip
### Info: 
## 6. Noise
### Info: Add noise for image.(Support salt noise, gaussian noise, rayleigh noise, gamma noise, exponential noise, uniform noise)
## 7. 
### Info: 
## 8. Disturbance
### Info: Change the brightness, contrast, saturation, and hue of an image.
## 9. Kernal filter
### Info: 
## 10. Cutout
### Info: Randomly fill the randomly sized area of an image.
## 11. HAS
### Info: Divide the image into $S×S(S≥5)$ grids, randomly filling a random number of grids with (random) pixels.
## 12. Grid mask
### Info: Generate a randomly sized $S×S(S≥3)$ grids, with random but fixed intervals between each grid, combine this mask with the image.
## 13. Local Augment
### Info: Randomly select a random number of operations from the provided data augmentation operation list to augument the same image.
## 14. Self Augmentaion
### Info: 
## 15. YOCO
### Info:
## 16. Cut-Thumbnial
### Info:
## 17. Mixup
### Info:
## 18. CutMix
### Info:
## 19. PuzzleMix
### Info:
## 20. Fmix
### Info:
## 21. Random Mix
### Info:
## 22. RICAP
### Info:
## 23. Cut Blur
### Info:
## 24. CDA
### Info:
## More operations will come.
# Customize your operation
Your operation must inherit the class ```Operator```. Then override the funtion ```process```. Here is a example.
## Example(Flip)
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
Then you can use your operation as we provided. 
# Quick Query
You can use the command:
```python
import UniversalDataAugmentation as uda
print(uda.details())
```
to obtain all supported data augmentation operations for the current version.
