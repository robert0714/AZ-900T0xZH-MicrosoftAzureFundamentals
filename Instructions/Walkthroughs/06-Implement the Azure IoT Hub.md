﻿---
wts:
    title: '06 - 实现 Azure IoT 中心'
    module: '模块 02 - 核心 Azure 服务'
---
# 06 - 实现 Azure IoT 中心

在本演练中，我们将在 Azure 门户中配置新的 Azure IoT 中心，并使用在线 Raspberry Pi 设备模拟器验证与 IoT 设备的连接。传感器数据和消息从 Raspberry Pi 模拟器传递到 Azure IoT 中心，你可以在 Azure 门户中查看消息传递活动的指标。

预计用时：30 分钟

# 任务 1：创建一个 IoT 中心 

在此任务中，我们将创建一个 IoT 中心。 

1. 登录至 [Azure 门户](https://portal.azure.com)。

2. 搜索并选择 **IoT 中心**，然后单击 **+ 添加**。

3. 使用以下详细信息填写字段。

	| 设置 | 值 |
	|--|--|
	| 订阅 | **选择你的订阅** |
	| 资源组 |  **myRGIoT** （新建）|
	| 区域 | **美国东部** |
	| IoT 中心名称 | **my-hub-group** |
    	| | |	

4. 移动至 **大小和缩放** 选项卡，使用下拉列表将 **定价和缩放级别** 设置为 **F1 - 免费层**。请注意，你每天将收到固定数量的消息。 

5. 单击 **审阅+创建** 按钮。

6. 单击 **创建** 按钮开始创建新的 Azure IoT 中心。

7. 等待资源部署完成。 

# 任务 2：添加 IoT 设备

在此任务中，我们将 IoT 设备添加到 IoT 中心。 

1. 部署完成后，从 **通知** 页面选择 **转到资源**。也可以搜索 **IoT 中心** 找到新资源。

	![此屏幕截图显示了 Azure 门户中正在进行部署和部署成功的通知。](../images/0601.png)

2. 如需添加新的 IoT 设备，请从 **IoT 中心导航** 工具中选择 **Explorers** > **IoT 设备**。然后，选择“**新建**”按钮。

	![此屏幕截图显示了“IoT 设备”窗格，该窗格在 Azure 门户中的“IoT 中心导航”边栏选项卡中突出显示。突出显示“新建”按钮以说明如何将新的 IoT 设备标识添加到 IoT 中心。](../images/0602.png)

3. 为新的 IoT 设备 **myRaspberryPi** 提供名称，然后单击 **保存** 按钮。这将在 Azure IoT 中心中创建新的 IoT 设备标识。

4. 如果看不到新设备，**请刷新** IoT 设备页面。 

5. 选择 **myRaspberryPi** 并复制 **主连接字符串** 值。你将在下一任务中使用此密钥来验证与 Raspberry Pi 模拟器的连接。

	![此屏幕截图显示了“主连接字符串”页面，其中突出显示了“复制”图标。](../images/0603.png)

# 任务 3：使用 Raspberry Pi 模拟器测试设备

在此任务中，我们将使用 Raspberry Pi 模拟器测试设备。 

1. 在 web 浏览器中，打开在线 [Raspberry PI 模拟程序](https://azure-samples.github.io/raspberry-pi-web-simulator/#Getstarted)。 

2. 了解有关 Raspberry Pi 模拟器的信息。如果存在“概述”弹出窗口，请选择 **X** 关闭该窗口。

3. 在右侧的编码区域中，找到带有“const connectionString =”的行。更改 DeviceId 并使用你的主连接字符串。

	DeviceId=**myRaspberryPi**

	SharedAccessKey=**primary connection string**

	![Raspberry Pi 模拟器中编码区域的屏幕截图。](../images/0604.png)

4. 选择 **运行** （底部窗格）以运行应用程序。控制台输出应显示从 Raspberry Pi 模拟器发送到 Azure IoT 中心的传感器数据和消息。每次Raspberry Pi模拟器LED闪烁时,都会发送数据和消息。 

	![Raspberry Pi 模拟器控制台的屏幕截图。  控制台输出显示了从 Raspberry Pi 模拟器发送到 Azure IoT 中心的传感器数据和消息。](../images/0605.png)

5. 选择 **停止** 以停止发送数据

6. 返回 Azure 门户和 IoT 中心。

7. 选择 IoT 中心 **概述** 边栏选项卡并向下滚动到 **IoT 中心使用情况** 信息。

	![此屏幕截图显示了 Azure 门户的 IoT 中心使用情况区域中的指标。](../images/0606.png)


恭喜！你已设置 Azure IoT 中心来从 IoT 设备收集传感器数据。

**注意**：为避免产生额外费用，你可以删除此资源组。搜索资源组，单击你的资源组，然后单击 **删除资源组**。验证资源组的名称，然后单击 **删除**。关注 **通知**，了解删除操作的进度。