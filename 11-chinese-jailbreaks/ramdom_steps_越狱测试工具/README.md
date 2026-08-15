# Prompt Security Tester - AI提示注入安全测试工具

<div align="center">

![Version](https://img.shields.io/badge/version-1.2.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![React](https://img.shields.io/badge/React-18.2-61dafb)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue)

一款专业的AI提示注入安全测试Web应用，用于评估大语言模型对各类越狱技术的防御能力。

</div>

## ✨ 功能特性

### 核心功能
- 🔐 **模板管理系统** - 50+预置专业测试模板，支持自定义创建
- 🚀 **批量测试执行** - 多模板并发测试，高效评估安全性
- 📊 **结果分析仪表板** - 实时展示测试结果，支持漏洞标记
- 🔧 **智能变量系统** - 自动分类管理公共/私有变量
- 💾 **本地数据存储** - IndexedDB持久化，保护用户隐私
- 🔄 **数据导入导出** - 完整数据备份恢复，防止数据丢失
- 🎯 **自动化管理** - 变量自动分析、清理和分类

### 技术架构
- **前端框架**: React 18.2 + TypeScript 5.0
- **构建工具**: Vite 5.0
- **样式方案**: Tailwind CSS (暗色主题)
- **数据存储**: IndexedDB (Dexie.js)
- **数据可视化**: Recharts
- **状态管理**: React Hooks + Context

## 🚀 快速开始

### 环境要求
- Node.js >= 16.0
- npm >= 8.0 或 yarn >= 1.22
- 现代浏览器（Chrome/Firefox/Safari/Edge）

### 安装步骤

```bash
# 克隆项目
git clone https://github.com/channely/ramdom_steps.git
cd prompt-security-tester

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

访问 http://localhost:5173 开始使用

### 生产构建

```bash
# 构建生产版本
npm run build

# 预览生产构建
npm run preview
```

## 📖 使用指南

### 1. 配置API
首次使用需要配置API密钥：
1. 进入"设置"页面
2. 选择API提供商（默认支持Moonshot Kimi）
3. 输入API密钥
4. 点击"测试连接"确保配置正确

### 2. 模板管理
#### 浏览模板
- 在"模板"页面查看所有可用模板
- 使用筛选器按风险等级、攻击类型分类
- 点击模板卡片查看详细信息

#### 创建自定义模板
- 点击"新建模板"按钮
- 填写模板基本信息
- 使用变量系统增强模板动态性
- 保存并测试模板

### 3. 变量管理
系统提供智能变量管理功能：
- **自动分类**: 根据使用情况自动分类变量
- **公共变量**: 被2个及以上模板使用
- **私有变量**: 仅被单个模板使用
- **自动清理**: 未使用的变量自动删除

### 4. 执行测试
1. 在"测试"页面选择目标模板（支持多选）
2. 配置测试参数（可选）
3. 点击"开始测试"
4. 实时查看测试进度和结果
5. 标记漏洞并添加分析说明

### 5. 结果分析
- **实时统计**: 查看成功率、漏洞分布
- **历史记录**: 回顾所有测试会话
- **详细报告**: 查看每个测试的具体响应
- **导出功能**: 导出测试结果为JSON格式

### 6. 数据管理
- **导出备份**: 一键导出所有数据
- **导入恢复**: 从备份文件恢复
- **清空数据**: 清理所有本地数据（谨慎操作）

## 🎯 预置模板类别

### 基础测试模板（25个）
1. **角色扮演类** - DAN变体、专家模拟、虚构场景
2. **指令注入类** - 系统覆盖、优先级劫持、嵌套指令
3. **编码混淆类** - Base64编码、语言混合、字符替换
4. **上下文操纵** - 虚假前提、渐进诱导、认知锚定
5. **输出格式利用** - JSON绕过、代码伪装、Markdown注入

### 高级测试模板（25个）
1. **DAN 13.0系列** - 最新DAN变体技术
2. **多层嵌套攻击** - 复杂的嵌套指令结构
3. **认知偏差利用** - 紧急情况、道德困境
4. **混合编码技术** - 多种编码方式组合
5. **社会工程学** - 信任建立、权威伪装

## 🔒 安全说明

### 使用须知
⚠️ **重要提醒**：
- 本工具仅供授权的安全测试使用
- 严禁用于非法或恶意目的
- 测试前请获得相关授权
- 遵守当地法律法规
- 妥善保管API密钥

### 数据安全
- ✅ 所有数据存储在本地浏览器
- ✅ 不会上传任何数据到服务器
- ✅ API密钥加密存储
- ✅ 支持数据导出备份
- ⚠️ 清除浏览器数据会删除所有内容

## ⚙️ API配置

### Moonshot Kimi配置示例
```javascript
{
  name: "Kimi K2 API",
  provider: "moonshot",
  endpoint: "https://api.moonshot.cn/v1/chat/completions",
  apiKey: "sk-YOUR_API_KEY",
  model: "kimi-k2-0711-preview",
  maxTokens: 4096,
  temperature: 0.7
}
```

### 支持的模型
- Moonshot Kimi K2
- 更多模型支持开发中...

## 📂 项目结构

```
prompt-security-tester/
├── src/
│   ├── components/       # UI组件
│   │   ├── ui/          # 基础组件
│   │   └── ...
│   ├── data/            # 静态数据
│   ├── lib/             # 核心库
│   ├── pages/           # 页面组件
│   ├── services/        # 业务服务
│   ├── types/           # TypeScript类型
│   └── utils/           # 工具函数
├── public/              # 静态资源
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

## 🐛 故障排除

### 常见问题
1. **API连接失败**
   - 检查API密钥是否正确
   - 确认网络连接正常
   - 验证API额度是否充足

2. **数据导入失败**
   - 确保导入文件格式正确（JSON）
   - 检查文件是否损坏
   - 尝试使用较小的数据文件

3. **模板变量不显示**
   - 刷新页面重新加载
   - 检查变量管理页面
   - 确认变量格式正确

### 调试步骤
1. 打开浏览器开发者工具（F12）
2. 查看控制台错误信息
3. 检查网络请求状态
4. 在"数据管理"页面尝试重置应用

## 🔄 更新日志

### v1.2.0 (2024-01)
- ✨ 新增智能变量管理系统
- 🔧 修复数据导入重复问题
- 📝 完善项目文档
- 🎨 优化UI交互体验

### v1.1.0 (2024-01)
- ✨ 添加25个高级越狱模板
- 🔧 修复JSON格式识别问题
- 🚀 性能优化

### v1.0.0 (2024-01)
- 🎉 初始版本发布
- ✨ 实现核心功能

## 🤝 贡献指南

欢迎贡献代码和建议！

### 开发流程
1. Fork本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 提交Pull Request

### 代码规范
- 使用ESLint进行代码检查
- 遵循TypeScript严格模式
- 组件使用函数式写法
- 保持代码简洁清晰

## 📄 许可证

本项目采用MIT许可证 - 详见[LICENSE](LICENSE)文件

## 📮 联系方式

- 项目地址：[https://github.com/channely/ramdom_steps](https://github.com/channely/ramdom_steps)
- Issue反馈：[GitHub Issues](https://github.com/channely/ramdom_steps/issues)

## 🙏 致谢

感谢所有为本项目做出贡献的开发者和安全研究人员！

---

<div align="center">
Made with ❤️ for Security Research
</div>
