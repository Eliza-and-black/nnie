1.依赖环境: opencv4.0 
  需要用海思的检查编译工具编译opencv4.0的库，然后替换掉third_party/opencv4

2.将nnie放在和海思nnie相同的路径下

3.切换到改目录下,make生成可执行文件

4.将可执行文件和模型以及测试图片考到板子上运行。

5.由于楼主精力有限，因此主要是针对yolov3的优化。后期会更新更多的模型。  

6.支持yolov3多标签预测，需要将util.h中single-label-prediction部分注释，并将@ymd_add的multiple-label-prediction部分取消注释。