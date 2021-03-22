Vimba CPP 参数设置
---

## 相机参数列表
* GigE参数列表: https://www.alliedvision.com/fileadmin/content/documents/products/cameras/various/features/GigE_Features_Reference.pdf
* USB3参数列表: https://cdn.alliedvision.com/fileadmin/content/documents/products/cameras/various/features/Alvium_Features_Reference.pdf


### 曝光时间参数设置方法

下面的代码使用如下参数对相机进行曝光时间设置：
* GigE: ExposureTimeAbs 
* Alvium USB3: ExposureTime

```CPP
VmbErrorType ApiController::AcquireSingleImage( const std::string &rStrCameraID, FramePtr &rpFrame )
{
    // Open the desired camera by its ID
    VmbErrorType res = m_system.OpenCameraByID( rStrCameraID.c_str(), VmbAccessModeFull, m_pCamera );
    if ( VmbErrorSuccess == res )
    {
        // Set the GeV packet size to the highest possible value
        // (In this example we do not test whether this cam actually is a GigE cam)
        FeaturePtr pCommandFeature;
        if ( VmbErrorSuccess == m_pCamera->GetFeatureByName( "GVSPAdjustPacketSize", pCommandFeature ))
        {
            if ( VmbErrorSuccess == pCommandFeature->RunCommand() )
            {
                bool bIsCommandDone = false;
                do
                {
                    if ( VmbErrorSuccess != pCommandFeature->IsCommandDone( bIsCommandDone ))
                    {
                        break;
                    }
                } while ( false == bIsCommandDone );
            }
        }
        FeaturePtr pFormatFeature;
        // Set pixel format. For the sake of simplicity we only support Mono and BGR in this example.
        res = m_pCamera->GetFeatureByName( "PixelFormat", pFormatFeature );
        if ( VmbErrorSuccess == res )
        {
            // Try to set BGR
            res = pFormatFeature->SetValue( VmbPixelFormatRgb8 );
            if ( VmbErrorSuccess != res )
            {
                // Fall back to Mono
                res = pFormatFeature->SetValue( VmbPixelFormatMono8 );
            }

            // Try to set exposure time: GigE: ExposureTimeAbs; Alvium USB3: ExposureTime
            FeaturePtr pExposureFeature;
            res = m_pCamera->GetFeatureByName("ExposureTimeAbs", pExposureFeature);
            if ( VmbErrorSuccess != res ) { // try USB3 feature name
                res = m_pCamera->GetFeatureByName("ExposureTime", pExposureFeature);
                if (VmbErrorSuccess == res) {
                    res = pExposureFeature->SetValue(15000.0f); // in us, 15000.0us = 15ms
                }
            }

            if ( VmbErrorSuccess == res )
            {
                // Acquire
                res = m_pCamera->AcquireSingleImage( rpFrame, 5000 );
            }
        }

        m_pCamera->Close();
    }

    return res;
}
```