# Stock_predict

<details open>
<summary>目次</summary>

* [概要](#概要)
* [内容](#内容)
  * [Trainee_EDA.jpynb](#trainee_edajpynb)
  * [training.jpynb](#trainingjpynb)
</details>

## 概要

このプロジェクトは、株価の時系列データをLSTMを用いて予測するシステムです。Jupyter Notebook (`*.ipynb`) で記述されており、上から順に実行してください。

* **`Trainee_EDA.jpynb`**: データの探索的データ分析 (EDA) と前処理を行い、学習に使用するデータを作成します。
* **`training.jpynb`**: LSTMモデルを用いて時系列分割交差検証を行い、ハイパーパラメータチューニングと学習、予測を行います。評価指標はAUC (Area Under the ROC Curve) です。

## 内容

### Trainee_EDA.jpynb

このNotebookでは、以下の処理を行います。

1. **データの確認と前処理:**
    * DataFrameの内容（データ長、欠損値、統計量など）を確認します。
    * 出来高の分布を確認し、対数変換を行います。
2. **特徴量エンジニアリング:**
    * 曜日情報を数値化 (0: 月曜日 ~ 4: 金曜日)
    * 変動幅を計算 (高値 - 安値)
3. **データの可視化と分析:**
    * 終値と変動幅のボックスプロットを作成し、外れ値を確認します。
    * 変動幅と変化率の分布を可視化します。
    * 終値の平均を年、月、曜日ごとに折れ線プロットで描画し、傾向を分析します。 (通年平均、1990年から10年ごと、2020年から毎年の3通り)
    * 目的変数の候補となる終値と変化率のコレログラムを表示します。
    * 変化率の均衡性を確認します。

### training_EDA.jpynb

このNotebookでは以下の処理を行います
1. **データの前処理:**
   * 目的変数の設定(翌日の変化率)を行い、二値分類問題とします。
   * 予測に利用する特徴量を決定します
     
2. **モデルの定義**
   * Pytorchを用いたLSTMモデルを設計します
   * 時系列分割交差検証でハイパーパラメータチューニングを行う関数を設計します(指標はAUC)
   * 学習データで訓練し、テストデータを検証します。また、ROC曲線を描画します
     
3. **学習、テスト**
   *

