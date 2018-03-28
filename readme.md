为了方便各位，已上传data和zhwiki

PS：请充分使用Fork再发邮件……

https://github.com/S-H-Y-GitHub/QA/network

https://github.com/S-H-Y-GitHub/QA/tree/dffec997dee8501586853cf1d6834bb46c95fcdf

# 基于LSTM的中文问答系统 #

本项目通过建立双向长短期记忆网络模型，实现了在多个句子中找到给定问题的答案所在的句子这一功能。**在使用了互联网第三方资源的前提下**，用training.data中的数据训练得到的模型对develop.data进行验证，MRR可达0.75以上

# 如何运行 #

## 环境依赖 ##

| 程序 | 版本 |
|---|---|
| python | 3.5.2 |
| TensorFlow | 1.2.1 |
| jieba | 0.38 |
| CUDA | 8.0(8.0.61.2) |
| cuDNN | 5.1 |

CUDA和cuDNN都是TensorFlow的依赖项，请查看TensorFlow官方文档获取安装方法。其余几项都可以使用`pip install`命令安装

## 第三方资源使用说明 ##

1. 在对中文文本进行分词时，使用了jieba分词
2. 在对分好的词语进行编码时，为了避免One-hot编码带来的性能损失，使用了word embedding编码。其词向量使用了通过中文维基百科离线资料训练得到的50维词向量文件

## 运行程序 ##

装好了依赖库之后，直接执行main.py即可。如果有已经训练好的模型，程序会提示您是直接加载这个模型，还是重新开始训练。

main.py不接收参数，如果需要修改配置，请直接修改代码。文件中有详细中文注释，据此修改即可

taevaluation.py是一个评估脚本，可以提供MRR，MAP，ACC@1的评估，由助教学姐编写。我在输入输出的格式上进行了一些修改


## 关于训练 ##

当你选择了不使用已经训练的模型，或者没有已经训练的模型，程序会利用training.data和develop.data中的数据对模型进行训练。当使用默认参数时，训练最多会消耗大约8G内存+2G显存，请事先保证计算机有充足的硬件资源，防止报错。在我的GTX 850M+i5 4210H条件下，完整的训练过程需要大约12小时。

另外，我在调参时发现，即使使用相同的参数，每次训练的结果使用MRR度量仍可能有最大0.03的波动，原因尚不明确。由于个人硬件和时间所限，只是进行了很粗糙的调参，绝大多数参数仍有进一步优化的空间，有意的话不妨尝试优化一下。
