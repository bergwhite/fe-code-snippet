> 导入库

```

from PIL import Image, ImageFilter

```

> 打开图片

```

img = Image.open('1.jpg')

```

> 获取尺寸

```

imgSize = img.size
imgMode = img.mode
(w,h) = imgSize

```

> 开始缩放

```

imgThumbnail = img.thumbnail((w/4, h/4))
img.save('imgThumbnail.jpg', 'JPEG')
print(imgThumbnail)

```

> 滤镜模糊

```

imgFilterBlur = img.filter(ImageFilter.BLUR)
imgFilterBlur.save('imgFilterBlur.jpg', 'JPEG')

```

> 保存图片

```

img.save('img.jpg', 'JPEG')

```

> 显示图片

```

img.show()

```

> 图片过滤

```

imgFilter = img.filter(ImageFilter.SHARPEN)

```

> 再次保存

```

imgFilter.save('imgFilter.jpg', 'JPEG')

```