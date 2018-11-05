

```python
import os
import jieba
from collections import Counter
import pandas as pd
text=[]
text_1=[]

path=r'C:\Users\lenovo\Desktop\data1\assignment0\text'
pathDir = os.listdir(r'C:\Users\lenovo\Desktop\data1\assignment0\text')
for item in pathDir:
    newDir=os.path.join(path,item)
    if os.path.isfile(newDir):
        if os.path.splitext(newDir)[1]==".txt":  #判断是否是txt
            contents = open(newDir,encoding="utf8") #打开文件，并把打开的内容赋值给contents
            text.append(contents.read()) #读取contents里面的内容，装到text列表中
#print(text)
        
file=open(r'C:\Users\lenovo\Desktop\data1\assignment0\text.txt','w')
for i in text:
    file.write(i)
file.close()

stopwords=['about','t','—','also','against','\n',',',')','(','?','.',':',' ','”','“','s','a','the','on','and','to','in','as','is','for','of','that','this','’','-','"','it','has','are','not','with','The','A','have','be','at','up','its','said','form','would','form','by','U','S','which','an', "'",'I','more','they','will','state','from']
words=list(jieba.cut(open(r"C:\Users\lenovo\Desktop\data1\assignment0\text.txt").read()))

for word in words:
    if word not in stopwords:
        text_1.append(word)

count_words=Counter(text_1)
list1=count_words.most_common(15)

output = open(r'C:\Users\lenovo\Desktop\data1\assignment0\Keywords.csv','w',encoding='utf8')
output.write('keyword,frequency\n')
for row in list1:
    rowtxt = '{},{}'.format(row[0],row[1])
    output.write(rowtxt)
    output.write('\n')
output.close()

```


```python

```
