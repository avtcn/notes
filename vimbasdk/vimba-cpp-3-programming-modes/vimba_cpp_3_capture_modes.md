# Vimba C++ API 三种拍照模式编程实例
Allied Vision工业相机一般可以使用三种模式进行拍照:
1. 自由采集(Free Run)
2. 软件触发拍照(Software Trigger)
3. 硬件触发拍照(Hardware Trigger)


![GitHub]( vimba-3-models.png "Allied Vision Vimba Viewer 3 photo capturing modes settings") 
上图中是Vimba Viewer中显示的一款相机支持的拍照模式：
* Freerun - 自由采集
* Line1 - 硬件触发1
* Line2 - 硬件触发2
* FixedRate - 固定帧率(自由采集)
* Software - 软件触发拍照  

其中FixedRate是Freerun的一种特殊模式-以确定的频率进行拍照，例如1fps代表一秒拍摄一张等； Line1和Line2表示相机有两根触发线，用户可以任选
其一来接外部触发信息源进行图像拍摄；Software模式是指相机处理待命状态，当通过以太网（例如GigE千兆网相机）连接相机时，可以通过 Vimba SDK的
相应API向相机发出拍照指令，然后获得一张相应的照片。


## Vimba C++ API 实例 - 三种拍照模式编程方法
以下是基于Allied Vision Vimba SDK 2.1.3 C++ API 进行相机拍摄模式编程的例子。

![GitHub]( Joe-Demo-Three-Modes-Vimba-CPlusPlus.png "Allied Vision Camera 3 photo capturing modes") 


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

