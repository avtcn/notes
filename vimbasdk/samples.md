# Section1.2

This is Section1.2

### AVT Vimba SDK 使用流程图
AVT Vimba SDK操作相机，需要进行初始化，然后打开相机，之后可以一直调用拍照API进行图像获取工作，可以一直保留Camera实例，直到上层软件不再需要为止。
只有当上层软件需要停止工作时，才需要进行相反的步骤：停止采集，关闭相机，销毁灭VimbaSystem实例。
可以参考下面的流程图：
  
```mermaid
sequenceDiagram
    participant Application
    participant SciAqAVT
    participant VimbaSDK
    Application->>VimbaSDK: Step1: VimbaSDK初始化
    loop VimbaSDK初始化
        VimbaSDK->VimbaSDK: VimbaSystem.Startup()
    end
    VimbaSDK-->>Application: Step1 OK

    Application->>SciAqAVT: Step2: 打开一个相机
    SciAqAVT->VimbaSDK: SciOpenCamera()
    loop 打开相机
        VimbaSDK->VimbaSDK: pCam->OpenCamera()
    end
    VimbaSDK-->>Application: Step2 OK

    Application->>VimbaSDK: Step3: 设置图像采集模式
    Note left of VimbaSDK: 设置相机图像采集模式：软件触发，硬件触发，自由采集
    VimbaSDK-->>Application: Step3 OK

    Application->>SciAqAVT: Step4: 准备采集SciStartAcquire()
    SciAqAVT->>VimbaSDK: pCam->StartAcquire()
    loop 准备采集图像
        VimbaSDK->VimbaSDK: pCam->StartContinuousImageAcquisition()
    end
    VimbaSDK-->>Application: Step4 OK
    
    Application->>SciAqAVT: Step5: 拍照SciGrabImage()
    SciAqAVT->>VimbaSDK: pCam->Shot(*image)
    loop 拍照
        VimbaSDK->VimbaSDK: m_ApiController.GetImage()
    end
    VimbaSDK-->>Application: Step5 OK

    activate Application
    Note over Application,VimbaSDK: 多次拍照时间
    Note over Application,VimbaSDK: 可以一直调用拍照SciGrabImage()
    Note over Application,VimbaSDK: 这个过程可以一直持续下去，直接上层应用不再需要相机拍照功能为止。
    Note over Application,VimbaSDK: ...
    deactivate Application

    Note left of Application: 如果用户准备退出整个软件时, 正好和以上流程相反

    Application->>SciAqAVT: Step6: SciStopAcquire()
    SciAqAVT->>VimbaSDK: ...
    Application->>SciAqAVT: Step7: SciCloseCamera()
    SciAqAVT->>VimbaSDK: ...
    Application->>SciAqAVT: Step8: VimbaSystem.Shutdown()
    SciAqAVT->>VimbaSDK: ...

    Note over Application,VimbaSDK: 到此为步Vimba SDK已经停止工作，可以进行程序其它模块的销毁工作...
