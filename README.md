# LoveLetterForYou

有一个工科女友是怎么一种体验？

Decode the bin file,Get the love msg;

---

> GF扔来一个文件，文件名称：loveLetterForYou.bin
看来考验我的时候到了，先打开看看。。。
最方法记事本打开看看，哦，乱码。。。。
后缀是bin,看来是二进制文件，还好有winHex
哈哈，打开看看。。。要么00要么FF。。。

```
暂时无解
```
> 后告知是一幅图像，难道是把后缀强制改成了bin,嗯，改回bmp试试，读取文件头，图像宽，高，bitCount，都不对，其他字段也不对...
```
依旧无解
```
> 又告诉一个条件，图像宽和高都是512。

```
瞄了一眼文件大小512KB,嗯，不包括文件头的话，每个像素点
512*1024*8bit/(512*512)=16bit，哦，每个像素点是16位。
16位彩色下，每个像素是用一个字节来表示，一般有555或者
565来分别表示RGB值。然而然而，图像依然不对，十六进制查看下
文件由oo和FF组成，，没有传说中的LoveLetter啊啊啊
```

```
还是无解
```
> 谜底揭开，又告诉我图像是dcm格式标准，每个像素点由十六位，图像是灰度图像。。。。、、

```
(⊙o⊙)…，原来如此，0000就是黑色的，ffff位白色的，嗯，开辟一块
512*512*sizeof(short int)的内存，并把数据映射成图像，
哈哈，LoveLetter出来了。。。
```
