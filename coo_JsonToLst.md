```{.python .input}
import json  
import mxnet as mx  
from skimage import io 
```

```{.python .input}
jsonName = 'ownset.json' #当前文件夹的某一类的标签文件
#directory = 'ownSet/'  
directory ='/media/qy/My Passport/coco_dataset/ownSet/'#提取的某一类的图片集
with open(jsonName, 'r') as f:  
    DataSet = json.load(f)  #读取标签文件
  
print(DataSet['DataSet'][0]['img_name'])  #答应第一张图片的name
```

```{.python .input}
#查看第一张图片的标签
print(DataSet['DataSet'][0])  
```

```{.python .input}
#查看数据的类型
print(DataSet['DataSet'][0]['bbox'])
print(type(DataSet['DataSet'][0]['height']))
print(type(DataSet['DataSet'][0]['bbox']))
print(type(int(DataSet['DataSet'][0]['height'])))#整型使用整型强制转换之后还是整型
```

```{.python .input}
#查看图片的数量
j=0
for i in range(len(DataSet['DataSet'])):
    j=j+1
    k=i
print(j,k)
```

```{.python .input}
img_idx=0
#with open('ownSet.lst', 'w+') as f:
with open('./ownSet.lst', 'w+') as f:  
    for Data in DataSet['DataSet']:  

        x_min = Data['bbox'][0]  
        y_min = Data['bbox'][1]  
        x_max = Data['bbox'][0]+ Data['bbox'][2]  
        y_max = Data['bbox'][1]+ Data['bbox'][3] 
        f.write(  
                str(img_idx) + '\t' +  # idx  
                str(4) + '\t' + str(5) + '\t' +  # width of header and width of each object.  
                #str(int(Data['height'])) + '\t' + str(Data['width']) + '\t' +  # (width, height)
                str(int(Data['width'])) + '\t' + str(Data['height']) + '\t' +  # (width, height)
                str(1) + '\t' +  # class  
                str(x_min) + '\t' + str(y_min) + '\t' + str(x_max) + '\t' + str(y_max) + '\t' +  # xmin, ymin, xmax, ymax  
                str(Data['img_name'])+'\n')  
        img_idx += 1
```

```{.python .input}
print(img_idx)#查看图片的数量
```
