# Masked Pre-training Enables Universal Zero-shot Denoiser
论文网址：https://arxiv.org/pdf/2401.14966  
论文代码：https://github.com/krennic999/MPI  
自定的关键词：zero-shot、masked image modelling
![image](https://github.com/user-attachments/assets/49a9b897-d2eb-477e-a560-832bbe3e665f)

## 主要目标/创新点
~~最重要的好像是他预训练的masked image model~~  
update：  
- [ ] 他设计的mask model和别人有什么不一样？
- [ ] iterative filling是导致他快于别人的主要原因吗？

## 方法
先训练一个预训练模型，然后在推理阶段预测mask region;  
然后因为直接去噪可能对特定图片效果不太好，所以优化了一下加了个iterative fill。  
🤔看起来像是把inpainting的建模思路迁移过来了

把mask建模为原图上叠加的噪声
根据公式
$$\underset{\theta}{\arg \max } p(I \odot \hat{M} \mid I \odot M ; \theta)$$
可以得知，作者是想在随机遮盖的情况下恢复原图。  
:thinking:loss为什么不是
$$||\tilde{I}-\tilde{I}||_2$$
感觉现在这个像我在被遮住的地方和原图尽可能相似，而不是全图和原图尽可能相似


## 实验
- 实验需求：2块3090+48000张ImageNet(感觉应该所有算力需求都在预训练上）
- 评估指标：PSNR和SSIM

在高斯噪声、盲噪声和真实数据集上进行了测试，甚至在医学图像上进行了测试
## 优缺点（自我反思）
3.29 真是一场酣畅淋漓的没看懂呀！

## 补充的知识
在《Masked Image Training for Generalizable Deep Image Denoising》中提出了mask denoising  
主要观点是**模型靠识别噪声本身来去噪，对未见过的噪声模型表现不好**，而通过mask可以迫使模型去理解图像内容。  

DIP（2018）（https://openaccess.thecvf.com/content_cvpr_2018/papers/Ulyanov_Deep_Image_Prior_CVPR_2018_paper.pdf）  
很神奇的文章，maybe是one-shot的开端（？）  
证明的就是网络本身有隐含先验信息可以来恢复图像
