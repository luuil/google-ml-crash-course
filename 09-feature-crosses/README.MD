## 特征组合 (Feature Crosses)
特征组合是指两个或多个特征相乘形成的合成特征。特征的相乘组合可以提供超出这些特征单独能够提供的预测能力。

预计用时：5 分钟

### 学习目标

- 了解特征组合。
- 在 TensorFlow 中实施特征组合。

### 特征组合

- 定义 [A x B] 形式的模板
- 也可以比较复杂：[A x B x C x D x E]
- 当 A 和 B 表示布尔特征（例如分箱）时，所得到的组合可能会极其稀疏

### 特征组合：一些示例

- 房价预测器：
    ```
    [latitude X num_bedrooms]
    ```
- 井字游戏预测器：
    ```
    [pos1 x pos2 x ... x pos9]
    ```

### 特征组合：我们为什么要这么做？

- 线性学习器可以很好地扩展到大量数据，例如 vowpal-wabit、sofia-ml
- 不过，如果不使用特征组合，这些模型的表现度将受到限制
- 使用特征组合 + 大量数据是学习高度复杂模型的一种有效策略
    - 预示：神经网络可提供另一种策略


### 更多

- [Encoding nonlinearity](A-encoding-nonlinearity.md)
- [Crossing one-hot vectors](B-crossing-one-hot-vectors.md)

[p-fea-1]: ../image/08-A-feature-1.png
[p-fea-2]: ../image/08-A-feature-2.png
[p-fea-3]: ../image/08-A-feature-3.png