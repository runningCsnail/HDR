# 帮助说明
`GPUhelp`文件说明了GPU的连接和使用方法。

`论文参考` 包含参考过的论文原文，论文复现记录。

`env`是本地`virtualenv`环境。

`pytorch笔记`是从pytorch官方文档里摘录的参考。

# 项目进度书

HDR-NTIRE2021

赛事链接：https://data.vision.ee.ethz.ch/cvl/ntire21/

任务：

1. Track 1 Single Frame
2. Track 2 Multiple Frames

# **1、任务时间节点**

- 2020.01.20发布训练数据(输入与输出)和验证数据（仅输入）
- 2020.01.21验证服务器在线
- **2020.03.01最终测试数据发布（inputs only）**
- **2020.03.08测试结果提交期限**
- **2020.03.09简介/代码/模型提交截止日期**
- 2020.03.11测试初步分数发布给参与者
- **2020.03.28参赛论文提交截止**
- 2020.06.15成果颁奖

# **2、任务描述**

从受噪声，量化误差和噪声影响的一幅或多幅输入低动态范围（LDR）图像中恢复HDR图像。目的是获得一种网络设计/解决方案，该解决方案能够产生高质量的结果，具有最佳的**相似度（保真度）。**

# **3、评价指标**

- 标准的峰值信噪比（PSNR）

由输出图像（标准化为ground-truth HDR图像的最大值）和mu-law色调映射图像(标准化为ground-truth HDR图像99%)计算真实图像，并以 tanh 函数为边界，以避免过度的亮度压缩。

- 排名的主要指标将是mu-PSNR

排名最高的解决方案也有望实现高于平均的PSNR，明显高于中等曝光输入图像的PSNR

- 数据脚本 scoring_program.zip 中提供了 metrics.py, evaluation.py 两个脚本，用来实现上述评价。也可参考其他PSNR的实现方法。

请注意在排行榜中：muPSNR被错误地命名为SSIM，而PSNR是标准PSNR

# **4、作品要求**

1. 处理：

- 针对Track 1:

处理medium exposed input LDR images 保证输出image_id与输入相同，例如：输入图像是["0013_medium.png"]，那么输出也应该是 ["0013.png", "0013_alignexposure.npy"]

- 针对Track 2:

处理input LDR images(short, medium and long)，保证输出image_id与输入相同，例如：输入图像 ["0013_short.png","0013_medium.png", "0013_long.png"]， 输出图像 ["0013.png", "0013_alignexposure.npy"]



输出图像以  uint16 png  格式保存，与输入图像大小一致，且无损压缩成一个单独的文件alignment_ratio（请使用提供的data_io.py中提供的写入功能）。



1. 建立一个ZIP，包含上述输出图像、一个 readme.txt 。该ZIP文件中不要包含文件夹。
2. readme.txt 文件包含：

- 每张图的程序运行时间(单位：秒)；
- 若使用CPU，标记1；若使用GPU，标记0。
- 若使用其他数据，标记1；否则0。

例如：

```
runtime per image [s] : 10.43 
CPU[1] / GPU[0] : 1
Extra Data [1] / No Extra Data [0] : 1
Other description : Solution based on A+ of Timofte et al. ACCV 2014. We have a Matlab/C++ implementation, and report single core CPU runtime. The method was trained on Train 91 of Yang et al. and BSDS 200 of the Berkeley segmentation dataset. 
```

readme.txt 文件最后包含代码描述(依赖、链接、脚本等)

- 参赛者最终要提供图像结果、代码或可执行文件。

排名前三的参赛者：从OSI批准的流行许可证（http://opensource.org/licenses）中获取许可证，公开发布代码或可执行文件。代码或可执行文件保留至少一年(一年可访问)，填写一份简短描述其方法的调查（情况说明书）

# **5、 项目备份**

参考论文查找地址：

https://openaccess.thecvf.com/menu

https://openreview.net/group?id=ICLR.cc/2020/Conference#accepted-oral-papers

https://papers.nips.cc/paper/2020

项目备份地址：

陈呈的github: https://github.com/runningCsnail/HDR



# **每日进展与反馈：**

2021/1/29：



2021/1/30：



2021/1/31：