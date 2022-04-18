# 汉语音频文本对齐（Forced Alignment）-MFA
​
音素对齐在语音识别，语音合成等领域都可能会用的到。Montreal-Forced-Aligner（MFA）是个比较好用的工具，不仅支持汉语（普通话）还支持英语和一堆其他的语言（还可以自己训练声学模型），所以接下来主要写的是MFA的用法。

1、第一件事是把MFA安装好，Installation — Montreal Forced Aligner 2.0.0 documentation，Mac，Linux，Windows都可以用。

2、安装预训练模型：

mfa model download acoustic mandarin

若上述指令安装失败，可在与训练模型找到普通话（Mandarin），链接在这里Pretrained acoustic models — Montreal Forced Aligner 2.0.0 documentation

![image](https://user-images.githubusercontent.com/49120307/163780314-7f918c8a-64a5-4641-b799-f704dbf84022.png)

3、安装字典：

mfa model download dictionary mandarin

若上述指令安装失败，可在GitHub上找一个现成的字典，链接如下https://github.com/Jackiexiao/MTTS/blob/master/misc/mandarin-for-montreal-forced-aligner-pre-trained-model.lexicon。 下载下来要将字典改成.txt等MFA支持的字典格式。

4、准备要处理的数据

一个音频文件对应一个文本文件（支持多种格式），文本文件里的内容是对应音频的拼音

![image](https://user-images.githubusercontent.com/49120307/163780373-1bb8ae6a-d9e8-4dcf-a5cd-e604c17cd4de.png)

5、运行音频文本对齐程序

mfa align ./data mandarin mandarin ./result

或

mfa align ./data mandarin-for-montreal-forced-aligner-pre-trained-model.txt mandarin.zip ./result

若模型与字典都通过mfa安装成功，则第一条命令即可实现音频文本对齐；若安装不成功都是通过手动下载的模型与字典，则通过第二条命令运行。

mfa align是运行命令，

./data指的是数据所在文件夹路径，

mandarin-for-montreal-forced-aligner-pre-trained-model.txt是前面步骤下载的字典，

mandarin.zip是前面下载的预训练模型（不要解压），

./result是输出路径。

正常运行的话大概会是这样：

![image](https://user-images.githubusercontent.com/49120307/163780437-b0d7baba-8bb9-4e3c-a677-74eb8dc6dfa2.png)

运行成功会生成对应名字的.TextGrid文件

![image](https://user-images.githubusercontent.com/49120307/163780457-7c309900-30c8-459f-8d2c-7e37c7953352.png)

6、查看结果

Item [1]是整个拼音的持续时间：

![image](https://user-images.githubusercontent.com/49120307/163780490-986556c2-55dc-4a93-9c9b-1c6b79ef307c.png)

Item [2] 是单个音素的持续时间:

![image](https://user-images.githubusercontent.com/49120307/163780515-7fffc6b9-840e-4ea8-82bc-c3c087eeae43.png)

​
