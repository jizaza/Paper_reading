# Prompt-SID: Learning Structural Representation Prompt via Latent Diffusion for Single-Image Denoising
论文网址：[https://arxiv.org/pdf/2401.14966](https://arxiv.org/pdf/2502.06432)  
论文代码：[https://github.com/krennic999/MPI](https://github.com/huaqlili/Prompt-SID?tab=readme-ov-file)  
论文PowerPoint：  
自定的关键词：structural & semantic


## 主要目标/创新点
感觉写得还蛮清晰的，传统方法缺少对结构和语义的关注，于是我们就重点关注结构，并且将其转化为prompt嵌入
🌟最重要的应该是那个尺度回放策略

## 方法
整体思路是训练和推理分别得到一组采样恢复的图片，目标是要利用diffusion在特征层面对齐+利用在后面的SPIformer在图像层面对齐
![image](https://github.com/user-attachments/assets/b52d353f-51ce-44c4-a901-20046c2efca4)


## 实验
- 实验需求：一块3090
- 评估指标：PSNR
- 高斯+真实世界+荧光图像


## 优缺点（自我反思）


## 补充的知识
自监督的去噪：  
- noise2void
  - AP-BSN
- noise2noise

