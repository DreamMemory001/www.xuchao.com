# 解决方案一

因为在gradle 3.0.0中AAPT2是默认打开的，
所以在项目的gradle.properties中添加android.enableAapt2=false，sync后就编译通过了。
这只是暂时的解决方案



# 解决方案二

如果你在 AndroidStudio3.0之后出现Aapt2 错误：
![错误展示]（https://img-blog.csdn.net/20180317210125709）
类似上述问题 
一般是在用户目录下，C:\Users\用户名\.gradle）中含有中文名称。
那么最好的解决问题的方法就是把.gradle进行迁移
迁移到一个没有中文路径下的文件夹下

[迁移gradle](https://blog.csdn.net/Jeff_YaoJie/article/details/80499278)


