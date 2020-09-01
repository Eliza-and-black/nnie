作者用C++重新封装了一下NNIE的代码。把sample里面大部分的那坨垃圾代码全部弃用了，主要贡献如下:

1.高度模块化，主要分三步，1.load_model；2.run_model，3.postprocess。1,2所有的模型共用，通过2可以得到output的tensor,每个模型只需写自己的后处理来解析output的Tensor即可。

2.代码量是sample代码的几十分之一，结构清晰简单易懂

3.yolov3后处理完全自己重写，速度非常快

4.遗弃sample中所有的全局变量，防止多线程跑多个模型时出现的线程安全问题。作者亲测，在多线程跑多个模型正常，互不影响，重构的C++代码是线程安全的。



编译:

1.依赖环境: opencv4.0 
  需要用海思的检查编译工具编译opencv4.0的库，然后替换掉third_party/opencv4

2.将nnie放在和海思nnie相同的路径下

3.切换到改目录下,make生成可执行文件

4.将可执行文件和模型以及测试图片考到板子上运行。

5.由于楼主精力有限，因此主要是针对yolov3的优化。后期会更新更多的模型。  

6.支持yolov3多标签预测，需要将util.h中single-label-prediction部分注释，并将@ymd_add的multiple-label-prediction部分取消注释。
