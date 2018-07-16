## 機械学習の学習
Learning machine learning
<div style="text-align: right; font-size: 0.7em">2017. 10. 28 Ishizaki</div>

---

### 1. 機械学習って何？
What's machine learning?

---

コンピュータプログラムが経験によって<br>自動的に出力結果を改善していく仕組み

![whats_ml](img/whats_ml.png)


---

### 2. 何に使われているの？
What is it used for?

---

機械学習を利用したシステムは<br>生活にあふれている

![use_ai_1](img/use_for.png)

---

### 3. どうやって作るの？
How do we create ML?

---

##### 統計学系 / ディープラーニング

![whats_ml2](img/what_ml2.png)

---

### 4. Demo

ワインの品種を当てる

![wine](img/wine.jpg)

---

* 特徴ベクトル :  アルコール濃度, Mg量, 等13種類
* ラベル :  class0, class1, class2

---

##### ニューラルネットワーク

入力値から重みとバイアスを加えて<br>計算を繰り返し結果を算出

![NN](img/NN.png)

---

たった数行でワインの品種を高精度で予測

```py
model = Sequential()
model.add(Dense(64, activation='relu', input_dim=13))
model.add(Dropout(0.5))
model.add(Dense(3, activation='softmax'))

model.compile(optimizer='rmsprop',
              loss='categorical_crossentropy',
              metrics=['accuracy'])

model.fit(x, y, epochs=100, batch_size=100, verbose=1)
```

---

### 5. どうやって学習する？
How do you study ML?

---

##### おすすめの学習方法

* オンライン講座 :　coursera
* 書籍 :　仕事ではじめる機械学習
* 言語 :　Python
* ライブラリ :　scikit-learn, Keras, pandas
* データ分析力向上 :　kaggle

---

興味があったら機械学習エンジニアとして<br>
勉強してスキルアップしていきましょう
