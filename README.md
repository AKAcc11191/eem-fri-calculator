# EEM-FRI 荧光数据处理工具

三维荧光光谱 (EEM) 数据处理与荧光区域积分 (FRI) 计算的纯前端 Web 应用。

基于 Chen et al. (2003) 方法，实现从原始 TXT 数据到 FRI 五区域百分比的完整处理流程。

## 功能

- **TXT 文件解析**：支持 Hitachi F-4600 FD3 格式（UTF-8/GBK 编码）
- **空白扣除**：逐点扣除空白信号，负值归零
- **Raman 归一化**：基于空白 Ex=350nm / Em=371-428nm 的拉曼峰面积
- **散射去除**：一阶/二阶瑞利散射，参数可调
- **FRI 五区域积分**：二维梯形积分，乘积因子校正
- **EEM 等高线预览**：Canvas 绘制的热力图
- **XLSX 导出**：三个工作表（百分比、荧光体积、乘积因子）

## 部署到 GitHub Pages

### 方式一：直接部署

1. 在 GitHub 上创建一个新仓库（如 `eem-fri-tool`）
2. 将 `index.html` 上传到仓库根目录
3. 进入仓库 **Settings → Pages**
4. Source 选择 **Deploy from a branch**，Branch 选择 **main**，文件夹选 **/ (root)**
5. 保存后等待 1-2 分钟，访问 `https://<username>.github.io/eem-fri-tool/`

### 方式二：命令行部署

```bash
cd eem-fri-webapp
git init
git add index.html README.md
git commit -m "EEM-FRI webapp"
git branch -M main
git remote add origin https://github.com/<username>/eem-fri-tool.git
git push -u origin main
```

然后在 GitHub 仓库的 Settings → Pages 中启用 GitHub Pages。

## 技术细节

- 单 HTML 文件，所有 CSS/JS 内嵌
- SheetJS (xlsx) 通过 CDN 加载
- 纯客户端计算，数据不离开浏览器
- 兼容 Chrome / Edge / Firefox，支持移动端

## 参考文献

Chen, W., Westerhoff, P., Leenheer, J.A., Booksh, K. (2003). Fluorescence Excitation−Emission Matrix Regional Integration to Quantify Spectra for Dissolved Organic Matter. *Environmental Science & Technology*, 37(24), 5701-5710.
