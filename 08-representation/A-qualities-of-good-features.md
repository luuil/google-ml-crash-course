## 表示 (Representation)：良好特征的特点

预计用时：10 分钟

我们探索了将原始数据映射到合适特征矢量的方法，但这只是工作的一部分。现在，我们必须探索什么样的值才算这些特征矢量中良好的特征。

### 避免很少使用的离散特征值

良好的特征值应该在数据集中出现大约 5 次以上。这样一来，模型就可以学习该特征值与标签是如何关联的。也就是说，大量离散值相同的样本可让模型有机会了解不同设置中的特征，从而判断何时可以对标签很好地做出预测。例如，`house_type` 特征可能包含大量样本，其中它的值为 `victorian`：

```
✔This is a good example:

house_type: victorian
```

相反，如果某个特征的值仅出现一次或者很少出现，则模型就无法根据该特征进行预测。例如，`unique_house_id` 就不适合作为特征，因为每个值只使用一次，模型无法从中学习任何规律：

```
✘The following is an example of a unique value. This should be avoided.

unique_house_id: 8SK982ZZ1242Z
```

### 最好具有清晰明确的含义

每个特征对于项目中的任何人来说都应该具有清晰明确的含义。例如，下面的房龄适合作为特征，可立即识别为年龄：

```
✔The following is a good example of a clear value.

house_age: 27
```

相反，对于下方特征值的含义，除了它的建筑师，其他人恐怕辨识不出：

```
✘The following is an example of a value that is unclear. This should be avoided:

house_age: 851472000
```

在某些情况下，混乱的数据（而不是糟糕的工程选择）会导致含义不清晰的值。例如，以下 `user_age`的来源没有检查值恰当与否：

```
✘The following is an example of noisy/bad data. This should be avoided.

user_age: 277
```

### 不要将“神奇”的值与实际数据混为一谈

良好的浮点特征不包含超出范围的异常断点或“神奇”的值。例如，假设一个特征具有 0 到 1 之间的浮点值。那么，如下值是可以接受的：

```
✔The following is a good example:

quality_rating: 0.82
quality_rating: 0.37
```

不过，如果用户没有输入 `quality_rating`，则数据集可能使用如下神奇值来表示不存在该值：

```
✘The following is an example of a magic value. This should be avoided.

quality_rating: -1
```

为解决神奇值的问题，需将该特征转换为两个特征：

- 一个特征只存储质量评分，不含神奇值。
- 一个特征存储布尔值，表示是否提供了 `quality_rating`。为该布尔值特征指定一个名称，例如 `is_quality_rating_defined`。

### 考虑上游不稳定性

特征的定义不应随时间发生变化。例如，下列值是有用的，因为城市名称一般不会改变。（注意，我们仍然需要将`br/sao_paulo`这样的字符串转换为one-hot矢量。）

```
✔This is a good example:

city_id: "br/sao_paulo"
```

但收集由其他模型推理的值会产生额外成本。可能值“219”目前代表圣保罗，但这种表示在未来运行其他模型时可能轻易发生变化：

```
✘The following is an example of a value that could change. This should be avoided.

inferred_city_cluster: "219"
```