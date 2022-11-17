Copyright (c) 2022 Enflame Authors. All Rights Reserved.

## 简介
在GCU设备上应用DBNET网络，基于[PaddleOCR](README_ch.md)。

**近期更新**
- 2022.11.15 新增代码。

## 源码基线
- 基线源码仓库: https://gitee.com/paddlepaddle/PaddleOCR
- 分支: origin/static
- 基线 commit id: 69d78ddba36a9fed96588167e28edcfe4b313d80

## 重要修改
- 新增GCU使能开关，默认打开；
- DataLoader单独提供数据遍历，不作为main_program的一部分；
- 分布式适配：
  - 分布式初始化与优化器包装；
  - 训练集图片按照卡数随机划分到不同的卡上。

## 快速体验
### 安装依赖
```shell
# 在PaddleOCR路径下
cd PaddleOCR
python3.6 -m pip install -r requirements.txt
```

### 安装GCU环境
```shell
1. 安装GCU开发套件；
2. 安装paddle-with-gcu。
```

### 数据准备
以icdar2015数据集为例，参考[数据准备](./doc/doc_ch/detection.md#数据准备)。

## 启动训练
```shell
# 已默认开启GCU
python3.6 tools/train.py -c configs/det/det_mv3_db.yml &> train.log &
```