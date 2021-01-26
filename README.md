# 说明  

This is public technical documents portal by AVTCN AE team.   
You can view content directory through link below:  
https://github.com/avtcn/notes/blob/master/SUMMARY.md



# Summary

This is a technical book for AVT cameras by AVTCN AE.

* [AVT相机选型](cameras/README.md)        	
	* [AVT相机选型指南](cameras/AVT相机选型指南.pdf)
	* [相机I/O线定义](cameras/AVT_cable_12pin.pdf)
	* [CCD到CMOS的转换](cameras/ccd2cmos.md)
	* [Firewire/1394 vs GigE千兆网](cameras/firewire2gige.md)
* [Vimba SDK](vimbasdk/README.md)
	* [Vimba SDK安装](vimbasdk/installation.md)
	* [Windows平台优化](vimbasdk/optimization.md)
	* [Vimba 例程介绍](vimbasdk/samples.md)
	* [VimbaC 采图 + MFC界面显示图片实例](vimbasdk/VimbaC/VimbaC.md)
	* [Vimba C++ API 移植方法](vimbasdk/vimbacppport/vimbacppport.md)
	* [Vimba C++例程移植实例](vimbasdk/VmbCPP/VmbCPP_Examples.md)
	* [MFC(VS2010)环境下调用VmbCPP API及复用例程代码实例](vimbasdk/VmbCPP/VmbAPI_CPP.md)
	* [Vimba C++ API标准接口：Open/Start/Capture/Stop/Close](vimbasdk/vimbacppport/vimbacppport.md)	
	* [Vimba.NET API 移植 + C#/VB.Net代码实例](vimbasdk//VimbaNet/VimbaAPINET.md)	
	* [Vimba C++ API 三种拍照模式编程实例-GUI](vimbasdk/vimba-cpp-3-programming-modes/vimba_cpp_3_capture_modes.md)
	* [Vimba C++ API 三种拍照模式编程实例-API Console](vimbasdk/vimba-cpp-3-programming-modes-api-console/vimba-cpp-3-programming-modes-api-console.md) 
	* [Vimba C++ API - SynchronousGrab同步方法单张取图-AcquireSingleImage()函数优化](vimbasdk/vimba-cpp-synchronous-grab-mfc-refine/cpp_synchronousgrab_quicker.md)
	* [Vimba API 如何读写相机参数](vimbasdk/vimba_api_read_write_features/vimba_features_rw.md)	
	* [使用Vimba编程方法进行连续拍照高速存储](vimbasdk/vimba_api_save_continous_photos/high_speed_save_photos.md)	
	* [Vimba C++ API 图像采集在ActiveX OCX控件中的应用](vimbasdk/vimbacpp-mfc-activex-ocx-implementation/VimbaCPP-ActiveX-OCX-Implementation.md)
	* [Vimba .NET 图像采集状态统计例程](https://github.com/avtcn/vmbnet_freerun_missing_frames_statistics/blob/master/README.md)
	* [Vimba.NET 用异步软触发的方式实现同步采图.减少耗时](vimbasdk//VimbaNet/AsySingleGrap.md)	
* [AVT相机使用技巧](skills/README.md)	
	* [AVT采图软件入门指南](skills/AVT采图软件入门指南.pdf)
	* [千兆网相机使用及优化](skills/gige.md)
	* [Camera Link](skills/section2.2.md)
	* [USB 3.0](skills/section2.3.md)
	* [CoaXPress](skills/section2.3.md)
	* [Halcon与AVT相机](skills/section2.3.md)
	* [Labview与AVT相机](skills/section2.3.md)
	* [外部触发使用技巧](Normal_Issue/mako-gige-external-trigger-strobe-circuits/external-trigger-circuit.md)
	* [AVT多相机IP配置工具 - AVT_IP_Config](skills/avt_ip_config/avt_ip_config.md)
	* [Manta相机的EdgeFilter参数](skills/avt_ip_config/avt_ip_config.md)
	* [LUT参数导入及模拟Gamma参数效果](Normal_Issue/avt-gamma-lut-operation/Manta-LUT-Test.md)
	
* [常见问题列表](Normal_Issue/ReadMe.md)
	* [相机误触发](Normal_Issue/TriggerIssue/Trigger_error.md)
	* [通过交换机连接多个相机](Normal_Issue/ConnectThroughSwitch/Connect_through_switch.md)
	* [安装/更新Intel原厂网卡驱动程序](Normal_Issue/Intel_Network_Adapter_AVT_Cameras/Reinstall_Intel_Network_Adapter_Driver.md)
	* [Win7 64位找不到相机或安装驱动报错](Normal_Issue/Win7_X64_Install.md)
	* [相机坏了如何维修](Normal_Issue/Repair.md)
	* [彩色相机白平衡设置方法](Normal_Issue/AdjustWhiteBalance/White_Balance.md)
	* [使用Vimba viewer配置相机IP - Vimba Viewer](Normal_Issue/IPConfigByVimbaViewer/IP_Cofig.md)
	* [修改并保存相机参数](Normal_Issue/SaveUserset/Save_Userset.md)
	* [恢复相机出厂设置/默认参数](Normal_Issue/LoadDefault/load_Default.md)
	* [如何升级/导入相机固件（Firmware_Upgrade）](Normal_Issue/FirmwareUpgrade/Firmware_Upgrade.md)
	* [相机坏点判定方法及坏点校正工具使用](Normal_Issue/DefectPixel/bad_pixels_tools.md)
	* [千兆网相机稳定性判断方法-Vimba Viewer查看软件](skills/how_to_check_gige_network_statbility.md)
	* [相机2D尺寸图、3D尺寸图](Normal_Issue/AVT-Cameras-2D-3D-Datasheets/AVT-Cameras-2d-3d-datasheets.md)
	* [在Matlab上使用AVT工业相机的注意事项](Normal_Issue/AVT-Cameras-2D-3D-Datasheets/AVT-Cameras-2d-3d-datasheets.md)
	
	
* [简明技术手册]()
	* [Alvium USB3 相机简明手册](vimbasdk/alvium_usb_camera_setup/README.md)
	* [GigE千兆网相机简明手册](vimbasdk/gige_camera_setup/README.md)
	* [Alvium MIPI 相机简明手册](vimbasdk/alvium_mipi_camera_setup/README.md)
	

## 其他  
[解决github无法访问或排版图片出错等问题](https://ayunnn.github.io/2019/05/17/20190517%E8%A7%A3%E5%86%B3github%E6%97%A0%E6%B3%95%E8%AE%BF%E9%97%AE%E6%88%96%E6%8E%92%E7%89%88%E5%9B%BE%E7%89%87%E5%87%BA%E9%94%99%E7%AD%89%E9%97%AE%E9%A2%98/)


## 联系方式  

support@alliedvision.com 
2021-1-26 11:24:42




