# LLM-fine-tuning

这个项目专注于使用LoRA（Low-Rank Adaptation）技术对大型语言模型（LLM）进行微调，特别针对医学领域的问答任务。项目包含了数据预处理、模型训练、模型评估和模型调用等完整流程。

## 项目结构

```
Lora/
├── Lora eval.ipynb          # 模型评估脚本
├── Lora train.ipynb          # 模型训练脚本
├── Lora train-Copy1.ipynb    # 模型训练脚本副本
├── call.ipynb                # 模型调用脚本
└── file process.ipynb        # 数据预处理脚本
```

## 功能介绍

### 1. 数据预处理 (file process.ipynb)

该脚本负责将PDF格式的医学文档转换为模型训练所需的JSONL格式数据。主要功能包括：

- 从PDF文件中提取文本内容
- 将长文本智能切分为适合模型处理的小块
- 使用大模型（如GPT-4）将文本转换为问答对格式
- 将数据集分割为训练集和验证集

### 2. 模型训练 (Lora train.ipynb)

该脚本使用QLoRA技术对Qwen3-1.7B模型进行微调，以适应医学问答任务。主要特点：

- 使用4-bit量化减少显存占用
- 应用LoRA适配器进行高效微调
- 支持多GPU训练
- 实时监控训练过程

### 3. 模型评估 (Lora eval.ipynb)

该脚本用于评估微调后的模型性能，并与基础模型进行对比。评估指标包括：

- ROUGE分数
- BERTScore
- 关键词匹配度
- 安全性评估

### 4. 模型调用 (call.ipynb)

该脚本提供了一个交互式界面，用于加载训练好的模型并进行医学问答。用户可以输入医学相关问题，模型将生成专业的医学报告。

## 使用方法

1. **数据预处理**
   - 修改`file process.ipynb`中的配置参数，指定PDF文件路径和输出路径
   - 运行脚本完成数据转换

2. **模型训练**
   - 确保已安装所有依赖库
   - 运行`Lora train.ipynb`开始训练
   - 训练过程中可实时查看训练状态

3. **模型评估**
   - 训练完成后，运行`Lora eval.ipynb`评估模型性能
   - 查看生成的评估报告和对比结果

4. **模型调用**
   - 运行`call.ipynb`
   - 根据提示输入医学问题
   - 查看模型生成的医学专家报告

## 依赖库

- transformers
- datasets
- torch
- pandas
- scikit-learn
- PyMuPDF
- openai
- trl
- peft
- bitsandbytes
- accelerate

## 注意事项

- 训练过程需要较大的GPU显存（推荐16GB以上）
- 数据预处理阶段需要访问大模型API（如OpenAI或国内替代服务）
- 模型评估可能需要较长时间，特别是BERTScore计算

## 运行代码

1. **数据预处理**
   ```bash
   jupyter notebook file\ process.ipynb
   ```
   在Jupyter Notebook中打开文件，按顺序运行各个代码块。

2. **模型训练**
   ```bash
   jupyter notebook Lora\ train.ipynb
   ```
   在Jupyter Notebook中打开文件，按顺序运行各个代码块。

3. **模型评估**
   ```bash
   jupyter notebook Lora\ eval.ipynb
   ```
   在Jupyter Notebook中打开文件，按顺序运行各个代码块。

4. **模型调用**
   ```bash
   jupyter notebook call.ipynb
   ```
   在Jupyter Notebook中打开文件，运行代码块后根据提示输入问题。