---
layout: post
---

# Estimator 模式初探

## Estimator 优点

* 多平台运行,而不需要更改参数
* 方便的在开发者之间共享,(相当于把模型封装了,屏蔽底层的代码),更快的原型系统
* 便于调试,包括,失败创建检查点,Graph,初始化,Tensorboard使用,能让用户向使用Sk-learn那样使用TensorFlow
* 与之了常用的一些分类模型,例如

TensorFlow文档[链接](https://www.tensorflow.org/guide/estimators#advantages_of_estimators)

## Estimator 流程

[流程文档](https://www.tensorflow.org/guide/estimators#structure_of_a_pre-made_estimators_program)这个章节说出了机器学习的精髓,主要包括四大步骤:

1. 数据导入函数
2. 定义特征列
3. 实例化相应的 Estimator
4. 调用训练,评估,推论等

这个步骤,也大致遵循机器学习 sklearn 的流程,深度学习

## Estimator 实验

