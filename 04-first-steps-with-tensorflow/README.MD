## 使用 TensorFlow 的起始步骤

预计用时：1 分钟

### 学习目标

- 了解如何在 TensorFlow 中创建和修改张量。
- 了解 Pandas 的基础知识。
- 使用 TensorFlow 的一种高级 API 开发线性回归代码。
- 尝试不同的学习速率。

### TensorFlow API 层次结构

TensorFlow 是一种基于图表的通用计算框架，可用来编写您能想出的任何东西。

![tf][p-tf1]

包含

- [TensorFlow Estimators][estimators]
- [tf.layers][layers]
- [tf.losses][losses]
- [tf.metrics][metrics]

### 快速了解 tf.estimator API

```python
import tensorflow as tf

# Set up a linear classifier.
classifier = tf.estimator.LinearClassifier()

# Train the model on some example data.
classifier.train(input_fn=train_input_fn, steps=2000)

# Use it to predict.
predictions = classifier.predict(input_fn=predict_input_fn)
```

### 更多

- [TensorFlow Toolkit](A-toolkit.md)
- [Programming exercises](B-programming-exercises.md)

[p-tf1]: ../image/04-A-tf-1.png
[estimators]: https://www.tensorflow.org/programmers_guide/estimators
[layers]: https://www.tensorflow.org/api_docs/python/tf/layers
[losses]: https://www.tensorflow.org/api_docs/python/tf/losses
[metrics]: https://www.tensorflow.org/api_docs/python/tf/metrics