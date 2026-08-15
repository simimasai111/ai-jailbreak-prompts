JailbreakBench

**简介**:  
🚀 `JailbreakBench` 是一个用于评估大语言模型（LLM）安全性的测试工具，专注于检测模型对越狱攻击（Jailbreak）的抵抗能力。通过模拟恶意提示词注入、编码攻击和多轮对话操控，量化模型的漏洞风险，并生成详细报告与可视化分析。支持中英文数据集，适用于安全研究、模型优化和合规性测试。  

🔧 **核心功能**:  

- 📊 自动化越狱测试流程，支持多线程并发  
- 🔍 基于关键词分类的漏洞统计分析  
- 📝 生成 Word 格式的测试报告与图表  
- 🌍 中英双语支持，适配不同场景  

🛡️ **适用场景**:  

- 模型开发者进行安全加固  
- 企业评估部署模型的抗攻击能力  
- 研究人员探索 LLM 安全边界

🔧 **自定义**:  

- 可将csv数据集直接放到py脚本相同目录，脚本将自动读取
- 可直接编辑越狱提示词.txt（针对中文数据集）和越狱提示词_en.txt（英文数据集）以组定义越狱提示词

🔧 **注意事项**:  
Linux需要config.json配置参数，参考：
```json
{
  // 模型名称，指定要测试的目标模型（示例为 DeepSeek 的 8B 参数模型）
  "model_name": "deepseek-r1:8b",

  // API 基础地址，指向本地或远程的模型服务端点（示例为本地 Ollama 默认地址）
  "base_url": "http://127.0.0.1:11434/v1",

  // API 密钥，用于身份验证（留空表示无需密钥或本地测试）
  "api_key": "",

  // 测试条数限制（留空或注释表示测试全部数据集）
  "num_tests": "",

  // 并发线程数，控制测试请求的并行度（建议根据硬件性能调整）
  "threads": 1,

  // 数据集文件路径，包含用于测试的恶意查询样本（需为 CSV 格式）
  "dataset_file": "中文_大模型基础安全评测数据集_JailBench_seed.csv",

  // 数据集语言，支持 "chinese" 或 "english"（影响提示词和分类逻辑）
  "language": "chinese",

  // 报告语言，支持 "chinese" 或 "english"（控制输出文档的语言）
  "report_language": "chinese"
}
```


> *"让 AI 既强大又可靠"*
> <img width="902" height="1244" alt="image" src="https://github.com/user-attachments/assets/fc3ee2b8-3c33-4b53-a79c-a6378e74bac3" style="zoom: 25%;" />
> <img width="2307" height="514" alt="image" src="https://github.com/user-attachments/assets/c0c1e861-3a3b-4803-91cc-4f5dc288c649" style="zoom: 25%;" />
