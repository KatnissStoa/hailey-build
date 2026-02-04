# DouBook Insight

豆瓣书单抓取与AI阅读画像分析的Chrome插件。

## 功能特性

- 🔄 **一键抓取书单**: 自动抓取豆瓣「读过」和「想读」书单
- 💾 **本地缓存**: 24小时智能缓存，减少重复请求
- 📤 **数据导出**: 支持CSV和JSON格式导出，Excel完美兼容
- 🤖 **AI对话**: 基于个人书单的阅读画像分析和推荐
- 🎨 **侧边栏UI**: 优雅的侧边栏界面，支持拖拽调整宽度
- ⚙️ **灵活配置**: 支持自定义OpenAI API配置

## 安装步骤

### 1. 下载插件

下载或克隆此项目到本地：

```bash
git clone https://github.com/your-username/doubook-insight.git
cd doubook-insight
```

### 2. 添加图标文件

由于图标文件较大，需要手动添加。在 `icons` 文件夹中放入：
- `icon16.png` (16x16)
- `icon48.png` (48x48)
- `icon128.png` (128x128)

或者使用现有的图标文件。

### 3. 安装到Chrome

1. 打开Chrome浏览器
2. 访问 `chrome://extensions/`
3. 打开右上角的"开发者模式"
4. 点击"加载已解压的扩展程序"
5. 选择项目文件夹

## 使用说明

### 1. 配置API

首次使用需要配置OpenAI API：

1. 右键点击插件图标，选择"选项"
2. 在设置页面输入OpenAI API Key
3. 可选：修改API Base URL（支持第三方代理）
4. 保存设置

### 2. 抓取书单

1. 访问豆瓣个人读书主页（`https://book.douban.com/people/your-id/`）
2. 确保已登录豆瓣账号
3. 点击插件图标打开侧边栏
4. 点击"抓取书单"按钮

### 3. AI对话

在侧边栏对话框中，你可以：

- 询问阅读偏好："从我看过的书里，你觉得我是什么样的人？"
- 请求推荐："推荐一些我可能喜欢的书"
- 分析阅读趣味："我的阅读有什么特点？"

### 4. 数据导出

- 点击"导出CSV"获取Excel兼容的表格文件
- 点击"导出JSON"获取结构化数据文件
- 文件名格式：`douban_books_2024-01-01.csv`

## 项目结构

```
doubook-insight/
├── manifest.json       # 插件配置文件
├── background.js       # 后台服务脚本
├── content.js          # 内容脚本（主要功能）
├── content.css         # 样式文件
├── options.html        # 设置页面
├── options.js          # 设置页面脚本
├── icons/              # 图标文件夹
│   ├── icon16.png
│   ├── icon48.png
│   └── icon128.png
└── README.md           # 说明文档
```

## 技术特点

- **Manifest V3**: 使用最新的Chrome扩展API
- **Shadow DOM**: 避免样式冲突
- **智能缓存**: 24小时本地缓存机制
- **批量抓取**: 支持分页抓取大量书籍数据
- **错误处理**: 完善的异常处理和用户提示

## 数据格式

### 书籍数据结构

```json
{
  "title": "书名",
  "author": "作者",
  "rating": "评分",
  "tags": "标签",
  "date": "标记日期",
  "cover": "封面URL",
  "url": "书籍详情URL"
}
```

### CSV导出列

- title: 书名
- author: 作者
- rating: 评分
- tags: 标签
- date: 标记日期
- url: 详情链接

## 隐私说明

- ✅ 所有数据仅在本地存储
- ✅ 仅向配置的AI API发送匿名书单数据
- ✅ 不收集用户个人信息
- ✅ 不上传至任何第三方服务器

## 兼容性

- Chrome 110+
- 需要豆瓣账号登录
- 需要OpenAI API Key或兼容的API服务

## 故障排除

### 抓取失败
- 确保已登录豆瓣
- 检查网络连接
- 尝试刷新页面后重新抓取

### AI对话失败
- 验证API Key正确性
- 检查API配额是否充足
- 确认API Base URL设置正确

### 导出问题
- 检查浏览器下载权限
- 确保有足够的磁盘空间

## 开发者信息

如需自定义或扩展功能，请参考：

- Chrome Extension API文档
- OpenAI API文档
- 豆瓣页面结构分析

## 更新日志

### v0.1.0 (2024-01-01)
- 初始版本发布
- 支持书单抓取和AI对话
- 实现数据导出功能
- 添加设置页面

## 许可证

MIT License
