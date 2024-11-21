*一 为什么需要Deepspeed
分布式计算环境中，主节点负责协调其他节点和进程的工作
pytorch官方提供的分布式训练工具Accelerate只支持nvlink，而T4，3090这类显卡是PIX ，检测方式：nvidia-smi topo -m；deepspeed支持更大规模的模型训练
混合精度训练
ZeRO可以减少内存占用，优化大模型训练，将模型参数分成了三个部分：Optimizer States、Gradient 和 Model Parameter。在使用 ZeRO 进行分布式训练时，可以选择 ZeRO-Offload 和 ZeRO-Stage3 等不同的优化技术。
大模型（LLM）在训练时往往需要大量内存来存储中间激活、权重等参数，百亿模型甚至无法在单个 GPU上进行训练，使得模型训练在某些情况下非常低效和不可能。这就需要进行多卡，或者多节点分布式训练。
在大规模深度学习模型训练中有个主要范式：
数据并行
模型并行
目前训练超大规模语言模型技术路线：GPU + PyTorch + Megatron-LM + DeepSpeed
————————————————
                            本文为摩登都市天空博主原创文章，未经博主允许不得转载。
原文链接：https://blog.csdn.net/zwqjoy/article/details/130732601*