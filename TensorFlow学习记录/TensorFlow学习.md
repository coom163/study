# TensorFlow学习

## 0、前言

目前在学习TensorFlow，用的书籍是TensorFlow实战Google深度学习框架，把学习过程中的代码和遇到的问题记录下来，鼓励自己逐步成长。

## 1、TensorFlow学习

### 1.1 变量的更新

```python
import tensorflow as tf
state = tf.Variable(1, name="counter")
add_one = tf.add(state, tf.constant(1))
update = tf.assign(state, add_one)

with tf.Session() as sess:
    sess.run(tf.global_variables_initializer())
    sess.run(state)
    for _ in range(3):
        sess.run(update)
        print(sess.run(state))
```

### 1.2 出现的错误

#### 1.2.1 TypeError: __init__() got an unexpected keyword argument 'shapes'

使用tensorflow是0.9.0版本，而在最新的tensorflow中有很多改动，文章最后会附上这些改动以供参考查看。这里的错误是因为新版tf.zeros_initializer和tf.ones_initializer后面需要加括号，将v = tf.get_variable(“v”,initializer=tf.zeros_initializer(shape=[1]))改为v = tf.get_variable(“v”,initializer=tf.zeros_initializer( )(shape=[1]))就可以了，下面的一样。



#### 1.2.2 IndentationError: expected an indented block

python需要按照格式，一般出现错误的原因是不恰当的缩进（少输入了Tab键）。

 