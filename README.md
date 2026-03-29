# 服装商品智能客服系统

一个基于RAG（检索增强生成）技术的智能客服系统，专为服装商品领域设计，提供尺码推荐、洗涤养护、颜色选择等专业知识咨询服务。

## 功能特性

### 智能客服聊天
- 基于通义千问大模型的智能对话功能
- 支持上下文理解和多轮对话
- 提供专业的服装商品知识解答
- 实时流式响应，提升用户体验

### 知识库管理
- 支持TXT文件上传更新知识库
- 自动文本分割和向量化存储
- 基于Chroma向量数据库的高效检索
- 支持尺码推荐、洗涤养护、颜色选择等领域知识

### 技术架构
- **前端**: Streamlit - 提供简洁直观的Web界面
- **后端**: Python
- **大模型**: 通义千问 (qwen3-max)
- **向量嵌入**: DashScope (text-embedding-v4)
- **向量数据库**: Chroma
- **框架**: LangChain

## 项目结构

```
服装商品智能客服/
├── app_qa.py              # 智能客服聊天应用
├── app_file_uploader.py    # 知识库更新服务
├── rag.py                  # RAG服务核心实现
├── knowledge_base.py       # 知识库管理服务
├── vector_stores.py        # 向量存储服务
├── file_history_store.py   # 对话历史存储
├── config_data.py          # 配置文件
├── data/                   # 初始知识库数据
│   ├── 尺码推荐.txt
│   ├── 洗涤养护.txt
│   └── 颜色选择.txt
├── chroma_db/              # Chroma向量数据库
└── chat_history/           # 对话历史记录
```

## 安装步骤

### 环境要求
- Python 3.8+
- pip包管理器

### 安装依赖
```bash
pip install streamlit langchain langchain-community chromadb
```

### 配置要求
1. 需要配置阿里云DashScope API密钥（用于嵌入模型和大模型）
2. 在环境变量中设置API密钥：
   ```bash
   export DASHSCOPE_API_KEY=your_api_key
   ```

## 使用说明

### 启动智能客服
```bash
streamlit run app_qa.py
```

### 启动知识库更新服务
```bash
streamlit run app_file_uploader.py
```

### 使用流程
1. **智能客服**:
   - 访问 http://localhost:8501
   - 在聊天界面输入问题，如"针织毛衣如何保养？"
   - AI会基于知识库提供专业回答

2. **更新知识库**:
   - 访问 http://localhost:8502
   - 上传TXT格式的知识库文件
   - 系统自动处理并更新向量数据库

## 知识库内容

系统内置了以下领域的专业知识：
- **尺码推荐**: 不同体型的服装尺码选择指南
- **洗涤养护**: 各类面料的正确洗涤和保养方法
- **颜色选择**: 基于肤色、场合的颜色搭配建议

## 配置说明

主要配置参数位于 `config_data.py` 文件中：

- `chunk_size`: 文本分割大小（默认1000）
- `chunk_overlap`: 文本重叠大小（默认100）
- `similarity_threshold`: 检索返回文档数量（默认1）
- `embedding_model_name`: 嵌入模型名称（text-embedding-v4）
- `chat_model_name`: 大模型名称（qwen3-max）

## 技术亮点

1. **RAG技术**: 结合检索和生成，提供准确的专业知识回答
2. **流式响应**: 实时显示AI思考过程，提升用户体验
3. **上下文理解**: 支持多轮对话，理解用户意图
4. **高效检索**: 基于向量相似度的快速检索
5. **易于扩展**: 模块化设计，便于添加新功能和知识领域

## 未来规划

- [ ] 支持更多文件格式（PDF, DOCX等）
- [ ] 添加用户认证和多用户支持
- [ ] 集成图像识别功能，支持服装款式识别
- [ ] 添加多语言支持
- [ ] 优化检索算法，提升回答准确性



