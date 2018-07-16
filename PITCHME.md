# Wacker#29 Google Colaboratoryで覚える初めての（？）機械学習（Deep Learning）

---

## AIと機械学習とDeep Learning

参考：人工知能学会 What's AI : [http://www.ai-gakkai.or.jp/whatsai/AIresearch.html](http://www.ai-gakkai.or.jp/whatsai/AIresearch.html)

###  強いAIと弱いAI
   - 強いAI = 人間の知能そのものをもつ機械を作ろうとする立場
   - 弱いAI = 人間が知能を使ってすることを機械にさせようとする立場

--

### 研究分野

![研究分野](./img/overview.jpg)

参照：人工知能学会 What's AIより

--

### 機械学習の技術マップと・Deep Learning立ち位置

- 機械学習によって、人が行う学習と推論によって、分類と推測を行う

--

1.  教師なし
    - クラスタリング
    - データ構造の発見
    - K平均法
    - https://colab.research.google.com/drive/1yLfjHo0axYXLqfI4tEIqWK4_qu3z_lVU

--

1.  教師あり
    1.  線形回帰
    1. パーセプトロン
    1. 決定木
    1.  ランダムフォレスト
    1.  ニューラルネットワーク
    1.  畳込みニューラルネットワーク

--

1. 強化学習
    1.  Q学習

--

- ニューロンとパーセプトロン
- 活性化関数
- 学習則（Learning Rulu)
-


- Deep Learningは何をするものか？
- GAN（Generative Adversarial Network）

 ### プログラミングにおける機械学習のフレームワーク

- 今回使うフレームワーク
  -  [TensorFlow](https://www.tensorflow.org/?hl=ja):Google,Python
  -  [Keras](https://keras.io/ja/):Python

- その他、主なフレームワーク
  -  [CNTK](https://docs.microsoft.com/ja-jp/cognitive-toolkit/):MS,C++,Python
  -  [Chainer](https://chainer.org/):Preferred Networks,Python
  -  [Pytorch](https://pytorch.org/):FB + NVIDIA,Python,ChainerのForkでCaffe2とマージ

- 主なデータセット
  - Kaggle

## チュートリアル：MNIST

### 説明

https://www.kaggle.com/c/skoltech-cats-vs-dogs/data



### 説明
- 60,000点の訓練データ(mnist.train)と10,000点のテストデータ(minist.test)

### コード

``` python

!pip install -q keras

import keras

```

``` python

# coding: utf-8

# MNISTサンプル



# Kerasをインポート

import keras



# MINISTのデータの他、必要なモジュールをインポート

from keras.datasets import mnist

from keras.models import Sequential

from keras.layers.core import Dense, Dropout, Activation

from keras.optimizers import RMSprop

from keras.callbacks import EarlyStopping, CSVLogger

import matplotlib.pyplot as plt



# バッチサイズ、クラス数、エポック数を定義

batch_size = 128

num_classes = 10

epochs = 20



# MNISTデータを読込

(x_train, y_train), (x_test, y_test) = mnist.load_data()



# MNISTデータのうち10枚だけ表示

for i in  range(10):

plt.subplot(2, 5, i+1)

plt.title("M_%d" % i)

plt.axis("off")

plt.imshow(x_train[i].reshape(28, 28), cmap=None)

plt.show()



# 画像サイズを正規化

x_train = x_train.reshape(60000, 784).astype('float32')

x_test = x_test.reshape(10000, 784).astype('float32')

x_train /= 255

x_test /= 255

y_train = keras.utils.to_categorical(y_train, num_classes)

y_test = keras.utils.to_categorical(y_test, num_classes)



# 確認のために表示

print(x_train.shape)

print(y_train.shape)

print(x_test.shape)

print(y_test.shape)



# モデルを作成

model = Sequential()

model.add(Dense(512, input_shape=(784, )))

model.add(Activation('relu'))

model.add(Dropout(0.2))

model.add(Dense(512))

model.add(Activation('relu'))

model.add(Dropout(0.2))

model.add(Dense(10))

model.add(Activation('softmax'))



# サマリーを出力

model.summary()



# モデルのコンパイル

model.compile(loss='categorical_crossentropy',

optimizer=RMSprop(),

metrics=['accuracy'])



es = EarlyStopping(monitor='val_loss', patience=2)

csv_logger = CSVLogger('training.log')

hist = model.fit(x_train, y_train,

batch_size=batch_size,

epochs=epochs,

verbose=1,

validation_split=0.1,

callbacks=[es, csv_logger])



# 学習を実行

score = model.evaluate(x_test, y_test, verbose=0)

print('test loss:', score[0])

print('test acc:', score[1])




# 学習結果を表示

loss = hist.history['loss']

val_loss = hist.history['val_loss']

epochs = len(loss)

plt.plot(range(epochs), loss, marker='.', label='loss(training data)')

plt.plot(range(epochs), val_loss, marker='.', label='val_loss(evaluationdata)')

plt.legend(loc='best')

plt.grid()

plt.xlabel('epoch')

plt.ylabel('loss')

plt.show()

```




## ハンズオン



## 参考情報



- DataSet

- https://ai-kenkyujo.com/2017/10/18/free-dataset/

- kaggle https://www.codexa.net/what-is-kaggle/

- その他

- IBM:AIを「Artificial Intelligence（人工知能）」ではなく、「Augmented Intelligence （拡張知能）」



https://www.slideshare.net/masa_s/gan-83975514

https://elix-tech.github.io/ja/2017/02/06/gan.html

