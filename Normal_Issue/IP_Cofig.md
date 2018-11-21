# 使用Vimba viewer配置相机IP
## 1. 进入IP配置界面 
#### 右键相机列表上的相机，会弹出一个菜单，如下图所示：
IP1
##### 如果相机IP配置不对，则只显示“Open CONFIG”，如果相机被占用，则只有“Open READ ONLY”
#### 选择“Open CONFIG”,进入IP配置界面
IP2
## 2. 配置IP
### 2.1 点击“IP Configuration Mode”的“Value”区域，在弹出的菜单中选择“Persistent”（固定IP）
ip3
### 2.2 点击“Persistent IP Address”的“Value”区域，在弹出的输入框中输入正确的IP（要与本地连接IP设置在同一网段）
ip4
### 2.3 改好后先按回车键，再关闭输入框

## 3.保存IP
### 3.1 点击“IP Configuration Apply”的“Value”区域，点击弹出的“Execute”, IP设置就保存好了

Ip5

### 如果本地连接是自动获取IP模式，相机可以配置成自动获取模式，只需在"2.1"选择“DHCP”后直接执行3，但我们建议配置成固定模式，尤其是多相机的情况下
## 通过配置模式设置的相机IP是非易失性的，断电重启后依然有效，无需保存在用户设置里
