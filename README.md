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
- 可参考的提交教程：https://github.com/datawhalechina/team-learning-cv/blob/master/DefectDetection/docker%E6%8F%90%E4%BA%A4%E6%95%99%E7%A8%8B.pdf



##### **数据说明**

- **OCNLI**：是第一个非翻译的、使用原生汉语的大型中文自然语言推理数据集；
- **OCEMOTION**：是包含7个分类的细粒度情感性分析数据集；
- **TNEWS**：来源于今日头条的新闻版块，共包含15个类别的新闻；



##### **赛题及baseline分析**

该赛题是一个多任务多分类问题，在baseline中采用bert对输入的序列进行encoder，并在bert层后添加了一层attention层，该attention层在三个任务间共享，通过训练后能够对不同的任务有较为均衡的关注点（与之相对应的还可以对不同任务分别设置各自的attention，如 https://github.com/HuipengXu/tianchi-multi-task 中所设计的），最后每个任务都有各自的分类器。

在loss上，baseline中并没有简单的将多个任务的loss直接求和，而是在生成数据部分，计算数据集中样本标签的数量，从而根据设定的公式计算出每个标签的权重，以解决数据集中样本不平衡而带来的训练偏差，同时在训练的过程中，根据batch中不同任务占有的数据，动态得调整任务的loss比例。有关多任务loss的相关资料可以参考https://zhuanlan.zhihu.com/p/299648421



##### **可以改进的方案**

1. 对数据进行清洗
2. 采用交叉验证集进行训练
3. 修改网络结构



##### **提交结果**

- bert-base-chinese(baseline)，4轮即可跑到最佳

![](https://github.com/LiuXiangYuan/tianchi_nlp/blob/main/pictures/bert_base_result.png)

- ernie，2轮即可跑到最佳

![](https://github.com/LiuXiangYuan/tianchi_nlp/blob/main/pictures/ernie_result.png)

