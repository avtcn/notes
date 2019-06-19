## NET环境下AVT相机常用格式转换（Frame转Bmp）
        ```CPP
                private Image ConvertFrame1(Frame frame)
        {
            if (null == frame)
            {
                throw new ArgumentNullException("frame");
            }

            //Check if the image is valid
            if (VmbFrameStatusType.VmbFrameStatusComplete != frame.ReceiveStatus)
            {
                throw new Exception("Invalid frame received. Reason: " + frame.ReceiveStatus.ToString());
            }
            // m_Cam.QueueFrame(frame);

            //Convert raw frame data into image (for image display)
            Image image = null;
            switch (frame.PixelFormat)
            {
                case VmbPixelFormatType.VmbPixelFormatMono8:
                    {
                        Bitmap bitmap = null;
                        //bitmap = new Bitmap((int)frame.Width, (int)frame.Height, PixelFormat.Format24bppRgb);
                        //frame.Fill(ref bitmap);
                        //image = bitmap;
                        bitmap = new Bitmap((int)frame.Width, (int)frame.Height, PixelFormat.Format8bppIndexed);

                        //Set greyscale palette
                        ColorPalette palette = bitmap.Palette;
                        for (int i = 0; i < palette.Entries.Length; i++)
                        {
                            palette.Entries[i] = Color.FromArgb(i, i, i);
                        }
                        bitmap.Palette = palette;

                        //Copy image data
                        BitmapData bitmapData = bitmap.LockBits(new Rectangle(0, 0, (int)frame.Width, (int)frame.Height), ImageLockMode.WriteOnly, PixelFormat.Format8bppIndexed);
                        try
                        {
                            //Copy image data line by line
                            for (int y = 0; y < (int)frame.Height; y++)
                            {
                                System.Runtime.InteropServices.Marshal.Copy(frame.Buffer, y * (int)frame.Width, new IntPtr(bitmapData.Scan0.ToInt64() + y * bitmapData.Stride), (int)frame.Width);
                            }
                        }
                        finally
                        {
                            bitmap.UnlockBits(bitmapData);
                        }

                        image = bitmap;

                    }
                    break;

                case VmbPixelFormatType.VmbPixelFormatBgr8:
                case VmbPixelFormatType.VmbPixelFormatRgb8:
                case VmbPixelFormatType.VmbPixelFormatBayerRG8:
                case VmbPixelFormatType.VmbPixelFormatBayerGR8:
                    {
                        Bitmap bitmap = new Bitmap((int)frame.Width, (int)frame.Height, PixelFormat.Format24bppRgb);
                        frame.Fill(ref bitmap);
                        image = bitmap;
                    }
                    break;

                default:
                    throw new Exception("Current pixel format is not supported by this example (only Mono8 and BRG8Packed are supported).");
            }

            return image;
        }
         ```
