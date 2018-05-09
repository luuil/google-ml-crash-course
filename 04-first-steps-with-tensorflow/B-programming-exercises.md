## 使用 TensorFlow 的起始步骤 (First Steps with TensorFlow)：编程练习

预计用时：55 分钟

机器学习速成课程将引导您使用 tf.estimator（一种高级 TensorFlow API）对模型进行编码，以便您将学到的原则和技术应用于实践。

机器学习速成课程中的编程练习使用的是可将代码、输出和说明性文字合并到一个协作文档中的数据分析平台。

> 可使用 [Colaboratory][Colaboratory] 平台直接在浏览器中运行编程练习（无需设置！）。Colaboratory 支持大多数主流浏览器，并且在 Chrome 和 Firefox 的各个桌面版本上进行了最全面的测试。如果您想下载并离线运行这些练习，请参阅有关设置本地环境的[说明][colab-docker]。

请按照指定顺序运行以下三项练习：

- Pandas 简介([原版][pandas-intro]/[本地][pandas-intro-local])。 Pandas 是用于进行数据分析和建模的重要库，广泛应用于 TensorFlow 编码。该教程提供了您学习本课程所需的全部 Pandas 信息。如果您已了解 Pandas，则可以跳过此练习。
- 使用 TensorFlow 的起始步骤([原版][tensor_flow]/[本地][tensor_flow-local])。此练习介绍了线性回归。
- 合成特征和离群值([原版][synthetic]/[本地][synthetic-local])。此练习介绍了合成特征，以及输入离群值会造成的影响。

### 机器学习速成课程练习中的常用超参数

很多编码练习都包含以下超参数：

- **steps**：是指训练迭代的总次数。一步计算一批样本产生的损失，然后使用该值修改模型的权重一次。
- **batch size**：是指单步的样本数量（随机选择）。例如，SGD 的批量大小为 1。
以下公式成立：

```
total number of trained examples = batchsize∗steps
```

### 机器学习速成课程练习中的方便变量

有些练习中会出现以下方便变量：

- **periods**：控制报告的粒度。例如，如果 `periods` 设为 `7` 且 `steps` 设为 `70`，则练习将每 10 步（或 7 次）输出一次损失值。与超参数不同，我们不希望您修改 `periods` 的值。请注意，修改 `periods` 不会更改您的模型所学习的内容。
以下公式成立：

```
number of training examples in each period = batchsize∗steps / periods
```

[Colaboratory]: https://colab.research.google.com/
[colab-docker]: https://github.com/google/eng-edu/blob/master/ml/cc/README.md#with-docker
[pandas-intro]: https://colab.research.google.com/notebooks/mlcc/intro_to_pandas.ipynb?hl=zh-cn
[pandas-intro-local]: intro_to_pandas.py
[tensor_flow]: https://colab.research.google.com/notebooks/mlcc/first_steps_with_tensor_flow.ipynb?hl=zh-cn
[tensor_flow-local]: first_steps_with_tensor_flow.py
[synthetic]: https://colab.research.google.com/notebooks/mlcc/synthetic_features_and_outliers.ipynb?hl=zh-cn
[synthetic-local]: synthetic_features_and_outliers.py