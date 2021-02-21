# tianchi_nlp
热身赛二: 中文预训练模型泛化能力挑战赛

比赛地址：https://tianchi.aliyun.com/competition/entrance/531865/introduction



##### **一些有用的资料**

该赛涉及到用docker提交预测结果，这里采用的是WSL2，并在Ubuntu中安装docker

- windows10安装WSL可参考：https://docs.microsoft.com/zh-cn/windows/wsl/install-win10
- 在WSL2中安装和使用docker可参考：https://www.cnblogs.com/yunfeifei/p/13158845.html
- 有关WSL2中Windows和Linux之间的文件操作可参考：https://blog.csdn.net/caoyang_he/article/details/107898883
- 天池镜像服务及结果提交可参考：https://tianchi.aliyun.com/competition/entrance/231759/tab/174?spm=5176.12586973.0.0.51948f15ygPa4K
- （该赛题提交result.zip后即可进行评测，因此镜像中的run.sh可以不填写任何内容，但文件必须有）



##### **数据说明**

- **OCNLI**：是第一个非翻译的、使用原生汉语的大型中文自然语言推理数据集；
- **OCEMOTION**：是包含7个分类的细粒度情感性分析数据集；
- **TNEWS**：来源于今日头条的新闻版块，共包含15个类别的新闻；



##### **赛题及baseline分析**

该赛题是一个多任务多分类问题



##### **baseline提交结果**

![](https://github.com/LiuXiangYuan/tianchi_nlp/tree/main/pictures)

