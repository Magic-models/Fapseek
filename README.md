> [!TIPS]
> Github暂未上传模型，欲下载请前往https://modelscope.cn/models/Yuanbenxin/Fapseek
# Fapseek项目简介
Fapseek，是我们基于Qwen3-4B进行Lora指令微调得到的对话模型，在精心构建的数据集以及我们合理的训练之下，模型可以扮演一位名叫“赵发”的高中男老师。
## 重要说明
> [!IMPORTANT]
> 本项目使用阿里通义出品的Qwen3-4B作为基座模型展开微调，有关Qwen3-4B的更多信息，请[在此查看](),该模型以Apache License 2.0 协议开源。  
>Qwen3-4B 的版权声明及许可证请见 licenses/Qwen3-LICENSE 。
## 项目亮点
- 角色扮演能力出众，不易跑偏
- 适应多种日常对话场景
- 模型尺寸小，轻量高速
- 我们提供无损精度的原尺寸模型和对CPU推理更加友好的gguf格式量化（8bit/4bit量化）模型
- 详尽的操作指南，方便您在端侧进行部署
## 测试截图
>测试环境为8核CPU、RAM32GB，Ubuntu22.04-py311-torch2.3.1-1.29.0下的jupyter notebook
<img width="404" height="144" alt="image" src="https://github.com/user-attachments/assets/1ae073a7-cfd8-4c53-850e-89a59bf07396" />
<img width="468" height="123" alt="image" src="https://github.com/user-attachments/assets/ae9932a2-d554-4c70-bcb0-e378f1db3f6c" />
<img width="387" height="111" alt="image" src="https://github.com/user-attachments/assets/a69c2eb6-4db1-48ab-a28d-08481c46129b" />
## 训练过程和参数

### 采用Qwen3-4B的原因有二：

过小参数模型在此类任务中表现并不令人满意，如Qwen3-0.6B即使在日常对话中也会出现无尽重复，即使对推理参数进行调整，但它仍旧难以胜任  
受条件限制我们无法直接微调参数量过大模型，并且考虑到本地部署，我们最终选择了4B参数，它足够聪明，并且量化后可以在主流CPU上流畅运行
### 训练超参：

|参数名|值|
|---|---|
|学习率|1e-4|
|训练次数|5|
|输入序列分词后的最大长度|2048|
|数值精度|bf16|
|LoRA作用模块|all|
|LoRA秩|8|
|LoRA随机丢弃|0.1|
|LoRA缩放系数|16|

<img width="999" height="599" alt="image" src="https://github.com/user-attachments/assets/27de07e2-02d8-4f45-a000-1a0b13025fa4" />

## 最佳实践
