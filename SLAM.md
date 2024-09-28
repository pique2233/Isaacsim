# 如何在 Isaac Sim 中进行 SLAM 建图

## 必要条件
- 仅支持 ROS2 humble 和 foxy
- 需要安装 `nav2` 包

## Step 1: 生成 Occupancy Map

1. **加载场景**
   - 前往 `Isaac Examples -> ROS2 -> Navigation -> Carter Navigation`，加载该场景，或加载你自己创建的场景。

2. **视角调整**
   - 在视口的左上角，单击“相机”图标。从下拉菜单中选择“顶部视角”，以便更好地观察整个场景。

3. **打开占用地图工具**
   - 前往 `Isaac Utils -> 占用地图`，打开占用地图扩展。

4. **设置原点和边界**
   - 在占用地图扩展中，确保原点设置为 `X: 0.0, Y: 0.0, Z: 0.0`。
   - 下界设为 `Z: 0.1`，上限设置为 `Z: 0.62`，这个 Z 上限是为了匹配 Carter 机器人上激光雷达与地面的垂直距离。

5. **选择地图边界**
   - 在场景中选择 `warehouse_with_forklift` 升降机 prim。
   - 在占用地图扩展中，单击 “BOUND SELECTION”。这样会自动更新占用地图的边界，以包含 `warehouse_with_forklift`。

6. **生成占用地图**
   - 设置完成后，单击 “计算”，然后单击 “可视化图像”。
   - 将出现可视化弹窗，选择图像旋转角度为 `180 度`，坐标类型选择 `ROS 占用地图参数文件 (YAML)`。
   - 单击 “重新生成图像”，因为 ROS 和 Isaac Sim 的相机坐标不同。

7. **创建 YAML 文件**
   - 为占用地图参数创建一个名为 `carter_warehouse_navigation.yaml` 的文件，将其放在 `maps` 目录中，该目录位于示例 `carter_navigation` ROS2 包 (`carter_navigation/maps/carter_warehouse_navigation.yaml`) 中。

8. **插入地图参数**
   - 将之前生成的地图参数插入到 `carter_warehouse_navigation.yaml` 文件中。

9. **保存地图图像**
   - 回到 Omniverse Isaac Sim 的可视化选项卡，单击 “保存图像”。
   - 将图像命名为 `carter_warehouse_navigation.png`，并保存在与 YAML 文件相同的目录中。

### 最终生成一个 `.png` 格式的占用地图图像。

## Step 2: 运行 Nav2

1. **启动导航**
   - 打开终端并运行以下命令：
     ```bash
     ros2 launch carter_navigation carter_navigation.launch.py
     ```

2. **在 Rviz2 中导航**
   - 在 Rviz2 中可以加载并查看导航路径，使用 Nav2 进行导航。

