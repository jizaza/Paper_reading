# Masked Pre-training Enables Universal Zero-shot Denoiser
论文网址：https://arxiv.org/pdf/2401.14966  
论文代码：https://github.com/krennic999/MPI  
自定的关键词：zero-shot、masked image modelling
![image](https://github.com/user-attachments/assets/49a9b897-d2eb-477e-a560-832bbe3e665f)

## 主要目标/创新点
最重要的好像是他预训练的masked image model

## 方法
先训练一个预训练模型，然后在推理阶段预测mask region;  
然后因为直接去噪可能对特定图片效果不太好，所以优化了一下加了个iterative fill。  

:thinking:看起来很像把mask建模为原图上叠加的噪声？也就是一个前提假设是加性噪声？那乘性噪声怎么办？


## 实验
- 实验需求：2块3090+48000张ImageNet(感觉应该所有算力需求都在预训练上）
- 评估指标：PSNR和SSIM

## 优缺点（自我反思）

## 需要补充的知识
DIP
blind-spot networks
参考文献22-23的方法
