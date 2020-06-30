## Pythonでできること  
## 【爆速ガイド付き】
Webをしていたピカピカ一年生の  
データエンジニアのPythonまとめ  
-まれにソースを添えて-

---

### お前、誰よ
<hr>
#### やっしー
- メンバーズデータアドベンチャー
- データアーキテクト・アナリスト
- Twitter @yasshi_dayooon

<hr>
Portfolio<br>
![Portfolio](qr20200630152708240.png)

---
### 注意
- Pythonの環境構築方法については、Anaconda,pyenv,パッケージ版,Colab等色々ありますが、戦争になるので、カバーしません

---

### Pythonでできること
<hr>
- **Web**、スマホ開発
- **データ分析、機械学習**
- **数値計算**
- クラウド
- API

---?image=https://images.sftcdn.net/images/t_app-cover-l,f_auto/p/1790a008-96d6-11e6-8047-00163ed833e7/669733406/python-screenshot.png&position=right&size=20% 40%

### [Python](https://www.python.org/)とは
<hr>
みんな大好き   
- Simple is better than complex
- Complex is better than complicated
- Flat is better than nested

[The Zen of Python](https://www.pythonic-exam.com/pythonic)より一部抜粋

---

### これから各工程に共通する作業

```bash
python -m venv [仮想環境名]
cd [仮想環境名]
source bin/activate
pip install --upgrade pip
```

---

### Web,スマホ開発
- **[Django](https://www.djangoproject.com/)**(多機能・安全性)
- **[Flask](https://a2c.bitbucket.io/flask/)**(シンプル・拡張性・機械学習API)
- [Flutter](https://flutter.dev/)(マルチプラットフォーム)

+++

@snap[west span-45]
## [Django](https://www.djangoproject.com/)
@snapend

@snap[north-east span-60]
```bash
pip install django
django-admin startproject [PROJECT_NAME] .
cd [PROJECT_NAME]
python manage.py migrate
python manage.py runserver
```
@snapend

+++

@snap[west span-45]
## [Flask](https://a2c.bitbucket.io/flask/)
@snapend

@snap[north-east span-60]
インストール▼
```bash
pip install Flask
```
app.py作成▼
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello():
    name = "Hello World"
    return name

if __name__ == "__main__":
    app.run(debug=True)
```
サーバー構築▼
```
python app.py
```
@snapend

+++

---

### データ分析、機械学習
- [pandas](https://pandas.pydata.org/)(データ整備、鳥瞰)
- [scikit-learn](https://scikit-learn.org/stable/)(モデリング・回帰,分類)
- [Tensorflow](https://www.tensorflow.org/),[Keras](https://keras.io/ja/),[PyTorch](https://pytorch.org/)(ディープラーニング)
- [Matplotlib](https://matplotlib.org/),[Plotly](https://plotly.com/python/),[Dash](https://dash.plotly.com/),[Streamlit](https://www.streamlit.io/),[pyDeck](https://deckgl.readthedocs.io/en/stable/)(可視化)

+++

### Tips

+++

#### [pandas-profiling](https://github.com/pandas-profiling/pandas-profiling)

```
pip install plotly
pip install pandas
pip install pandas-profiling
```

```python
import pandas as pd
import pandas_profiling as pdp

import plotly.express as px

gapminder_df = px.data.gapminder()
pdp.ProfileReport(gapminder_df).to_file("output.html")
```

+++

![Image1](1.png)

+++

![Image2](2.png)

+++

![Image3](3.png)

+++

![Image4](4.png)

+++

![Image5](5.png)

+++

![Image6](6.png)

+++

#### プロットライブラリについて
|ライブラリ\インタラクティブ|低い|普通|高い|
|:--:|:--:|:--:|:--:|
|Matplotlib (&seaborn)|○|||
|Plotly||○||
|Dash,Streamlit|||○|

<hr>

pyDeck・・・圧倒的に上記ライブラリより地図描画が優れている

+++

### 数値計算
- [SciPy](https://www.scipy.org/)
  - フーリエ変換
  - LU分解
  - 信号処理
- [Numpy](https://numpy.org/)
　- Numpy配列もはや国際条例
 - Pure Pythonより計算が高速

+++

#### 数値計算の例

@snap[west span-45]
### 大きさNの正方行列の
### 行列行列積
インポート系は割愛

@snapend

@snap[north-east span-60]

C言語

```c
double a = [N][N]
double b = [N][N]
double c = [N][N]

for(int i=0;i<N;i++) {
  for(int j=0;j<N;j++) {
    a[i][j] = rand() % 10
    b[i][j] = rand() % 10
  }
}

for(int i=0;i<N;i++){
  for(int j=0;j<N;j++){
    for(int k=0;k<N;k++){
      c[i][j] += a[i][k] * b[k][j]
    }
  }
}

```

Python

```python
a = np.array([1, 2])
b = np.array([4, 3])
np.dot(a, b) # まずは２次元ベクトル同士の内積から。
```
@snapend

+++

### いかにPythonがシンプルさを追求しているか
ちなみにC言語もmkl cblasというライブラリを使えば高速に演算できますが、低レベルに近い言語という特性上そこそこのコード量になります。[参考](https://www.xlsoft.com/jp/products/intel/perflib/mkl/11.2/mkl_tutorial_c/GUID-36BFBCE9-EB0A-43B0-ADAF-2B65275726EA.htm)

+++

---
