# Vimba C++ API 三种拍照模式编程实例
Allied Vision工业相机一般可以使用三种模式进行拍照:
1. 自由采集(Free Run)
2. 软件触发拍照(Software Trigger)
3. 硬件触发拍照(Hardware Trigger)


## Vimba C++ 例子程序介绍
Allied Vision Vimba SDK 2.1.3 C++ 代码移植示例。


## 例子代码
请访问：https://github.com/avtcn/vimba_cpp_example_port 

## 需要软件
* Visual Studio Community 2017 (http://www.visualstudio.com/) 或者类似版本
* Vimba SDK 2.1.3 (https://www.alliedvision.com/en/products/software.html) 或者类似版本

## 使用方法
可以使用Beyond Compare或者WinMerg(http://winmerge.org/) 比较两个下面两个目录：
* vimba_cpp_port-blank: Visual C++ 空白对话框工程
* vimba_cpp_port-works：在以上Visual C++工程中加入Vimba SDK代码调用的例子
![改动文件对比](beyond-compare-list.png)


## 修改提示
1. 从vimba C++ 例子程序中复制辅助代码：ApiController.h/cpp, Bitmap.h/cpp到自己的工程.
2. 修改项目包含的头文件及库文件目录以包含Vimba C++用到的头文件及库，具体可以查看vimbacppex.vcxproj和vimbacppex.vcxproj.filters中的修改.
3. 在wimbacppexDlg.h中增加唯一的Vimba SDK实例 ApiController.
4. 测试如下Vimba C++代码是否能够成功运行：
```cpp
void CvimbacppexDlg::OnBnClickedButtonVimbaVersion()
{
	apiController.StartUp();
	  
	std::string strVersion = apiController.GetVersion();
	AVT::VmbAPI::CameraPtrVector ptrCameras = apiController.GetCameraList();	
	std::string strver2 = strVersion;
	apiController.ShutDown();
	
	std::string strver3 = strVersion;
	MessageBox(CString("Vimba version is ") + CString(strVersion.c_str()));
}
```


## 其它信息
联系 support@alliedvision.com 获取更多帮助。



2018-11-23 14:55:29
by Joe Ge

