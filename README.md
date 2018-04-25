# PaddlePaddle

### 官网：

http://www.paddlepaddle.org/


###  快速上手：

```
mkdir ~/workspace
cd ~/workspace; touch housing.py
```

```
touch housing.py
```

```
import paddle.v2 as paddle

# Initialize PaddlePaddle.
paddle.init(use_gpu=False, trainer_count=1)

# Configure the neural network.
x = paddle.layer.data(name='x', type=paddle.data_type.dense_vector(13))
y_predict = paddle.layer.fc(input=x, size=1, act=paddle.activation.Linear())

with open('/workspace/fit_a_line.tar', 'r') as f:
    parameters = paddle.parameters.Parameters.from_tar(f)

# Infer using provided test data.
probs = paddle.infer(
     output_layer=y_predict, parameters=parameters,
     input=[item for item in paddle.dataset.uci_housing.test()()])

for i in xrange(len(probs)):
     print 'Predicted price: ${:,.2f}'.format(probs[i][0] * 1000)
        
```


```
docker run --rm -v ~/workspace:/workspace paddlepaddle/paddle:latest python /workspace/housing.py
```


### 文档：

http://www.paddlepaddle.org/docs/develop/documentation/zh/getstarted/index_cn.html




###  baidu技术学院

####  PaddlePaddle 深度学习实战介绍    

http://bit.baidu.com/course/datalist/column/117.html    




