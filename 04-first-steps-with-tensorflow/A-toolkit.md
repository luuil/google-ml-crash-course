## 使用 TensorFlow 的起始步骤 (First Steps with TensorFlow)：工具包

预计用时：4 分钟

Tensorflow是构建机器学习模型的计算框架。 TensorFlow提供了各种不同的工具包，使您可以根据自己喜欢的抽象级别构建模型。通过定义一系列数学运算，您可以使用较低级别的API来构建模型。或者，您可以使用更高级别的API（如tf.estimator）来指定预定义的体系结构，例如线性回归器或神经网络。

下图显示了 TensorFlow 工具包的当前层次结构：

![tf1][p-tf1]

图 1. TensorFlow 工具包层次结构。

下表总结了不同层的用途：

| 工具包 | 说明 |
|-------|------|
| Estimator (tf.estimator) | 高级 OOP API |
| tf.layers/tf.losses/tf.metrics | 用于常见模型组件的库 |
| TensorFlow | 低级 API |

TensorFlow 由以下两个组件组成：

- [图协议缓冲区(graph protocol buffer)][protobuf]
- 执行（分布式）图的运行时

这两个组件类似于 Java 编译器和 JVM。正如 JVM 可以运行在多个硬件平台（CPU 和 GPU）上一样，TensorFlow 也是如此。

您应该使用哪个 API？您应该使用能够解决问题的最高级抽象层。较高级别的抽象层更易于使用，但（设计方面）不够灵活。我们建议您先从最高级 API 入手，让所有组件正常运作起来。如果您希望在某些特殊建模方面能够更加灵活一些，则可以降低一个级别。请注意，每个级别都是使用低级 API 构建的，因此降低层次结构级别应该比较直观。

### tf.estimator API

我们将使用 tf.estimator 来完成机器学习速成课程中的大部分练习。您在练习中所做的一切都可以在较低级别（原始）的 TensorFlow 中完成，但使用 tf.estimator 会大大减少代码行数。

tf.estimator 与 scikit-learn API 兼容。 [scikit-learn][sl] 是极其热门的 Python 开放源代码机器学习库，拥有超过 10 万名用户，其中包括许多 Google 员工。

概括而言，以下是在 tf.estimator 中实现的线性回归程序的格式：

```python
import tensorflow as tf

# Set up a linear classifier.
classifier = tf.estimator.LinearClassifier()

# Train the model on some example data.
classifier.train(input_fn=train_input_fn, steps=2000)

# Use it to predict.
predictions = classifier.predict(input_fn=predict_input_fn)
```

[p-tf1]: ../image/04-A-tf-1.png
[protobuf]: https://www.tensorflow.org/extend/tool_developers/#protocol_buffers
[sl]: http://scikit-learn.org/