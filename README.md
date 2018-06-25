# VerificationCode
# verification code by python

# chech_dode.py
import random
from PIL import Image, ImageDraw, ImageFont
# 创建画布
width = 400
height = 100
img = Image.new(mode = 'RGB', size =(width, height), color = (255, 255, 255))
# 创建画笔
draw = ImageDraw.Draw(img, mode = 'RGB')
font1 = ImageFont.truetype('Phetsarath_OT.ttf', 98)

code = [0] * 5
for i in range(5):
    char1 = random.choice([chr(random.randint(65, 90)), str(random.randint(0, 9))])
    code[i] = char1
    color1 = (random.randint(0, 255), random.randint(0, 255), random.randint(0, 255))
    draw.text([i * (width/len(code)), 0], char1, color1, font = font1)
   # 圆的半径
    radio = random.randint(3, 8) 
   # 画随机10个点，10条线
    for i in range(10):
        c1, c2 = (random.randint(radio, width-radio), random.randint(radio, height-radio))
   # 画点
        draw.ellipse((c1 - radio, c2 - radio, c1 + radio, c2 + radio), fill = color1, outline = color1) 
   # 画线
        draw.line((random.randint(0, 400), random.randint(0, 100), random.randint(0, 400), random.randint(0, 100)), fill = color1) 

print(code)
with open('pic.bmp', 'wb') as f:
    img.save(f, format = 'bmp')
img.show()
