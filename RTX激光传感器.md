# RTX激光雷达传感器

## 目的
将传感器消息发布到 ROS2，并在 Rviz2 中实现可视化。

## 准备条件
- 机器人的 URDF 文件
- ROS2 的准备

## 步骤

### Step 1: 添加传感器 ROS2 桥
为 RTX 激光雷达传感器添加 ROS2 通信桥，以便与 ROS2 系统进行交互。

### Step 2: 将 RTX Lidar 传感器添加到机器人上
将 RTX Lidar 传感器正确地安装到机器人模型上，确保传感器的位置、方向和其他参数设置正确。

### Step 3: 进行 Omnigraph 可视化
使用 Omnigraph 进行可视化，RTX Lidar 应该能够发送 `LaserScan` 和 `PointCloud2` 消息，并且可以在 RViZ 中进行可视化展示。

### Step 4: 在 RVIZ 中可视化并运行
启动 RVIZ 进行可视化操作，并确认 RTX Lidar 传感器的输出消息成功显示在 RVIZ 中。

