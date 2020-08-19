[top]

# 起步
#  anaconda promt 里创建环境
- 1. conda create -n duyi python=3.7
- 2. activate duyi

#  安装包安装(镜像：pip install -i https://pypi.douban.com/simple module)
#   美盾轮廓
- 1. pip install ... Pillow
- 2. 代码：
        from PIL import Image
        from PIL import ImageFilter
        im = Image.open('pika.jfif')
        contour = im.filter(ImageFilter.CONTOUR)
        contour.save('pika_1.jpg')
#   文字云
- 1. pip install ... wordcloud
- 2. 代码：        
        import wordcloud
        fp=open('test.txt')
        text=fp.read()
        WordCloud = wordcloud.WordCloud().generate(text)
        image_produce = WordCloud.to_image()
        image_produce.show()
# 人脸检测
  - 1. pip install ... cmake
- 2. pip install ... dlib
    安装此模块需注意几个步骤：
    1.python版本与dlib版本之间的兼容
    （步骤1 下载地址dlib-19.17.99-cp37-cp37m-win_amd64.whl文件
    链接：https://pan.baidu.com/s/1VrDssoHfcTbAGGB6cRIwBQ
    提取码：76u8

    步骤2 pip install... boost

    步骤3 在存放dlib-19.17.99-cp37-cp37m-win_amd64.whl的目录下
    pip install dlib-19.17.99-cp37-cp37m-win_amd64.whl(我的为 (duyi) C:\Users\14067 )
    ————————————————
    版权声明：本文为CSDN博主「丿一_一乚」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
    原文链接：https://blog.csdn.net/weixin_41453476/java/article/details/105854784
    ）
- 3. pip install ... face-recognition
- 4. pip install ... opencv-python
- 5. 代码：
    import face_recognition
    import cv2
    
    image = face_recognition.load_image_file("lyf.jpg")
    
    face_locations = face_recognition.face_locations(image)
    
    y0, x0, y1, x1 =face_locations[0]
    img =cv2.imread('lyf.jpg')
    #画矩阵框
    cv2.rectangle(img,(x0,y0),(x1,y1),(0,255,0),2)
    cv2.imwrite('01.jpg', img)
    cv2.imshow('image',img)
    cv2.waitKey()
    cv2.destroyAllwindows()
    
