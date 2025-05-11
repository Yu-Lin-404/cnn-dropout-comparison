# Emergency Image Classification with CNN: Dropout Comparison

本專案針對卷積神經網路(CNN)模型進行Dropout正則化(為了避免模型過度擬合)的實驗，探討其在緊急事件圖片分類任務中的效果，分析有無Dropout對訓練與測試準確率的影響。

---

## 專案目的

比較CNN模型在有無Dropout(隨機失活)情況下的訓練與驗證表現，了解其對過擬合的影響。

---

## 資料集資訊

- 資料來源：[Kaggle - Emergency vs Non-Emergency](https://www.kaggle.com/code/trinadhsingaladevi/computer-vision-cnn)
- 訓練資料：1,646 張圖像  
- 測試資料：706 張圖像  
- 圖像大小：28 × 28 × 3（已標準化）

---

## 模型架構與訓練設定

| 模型 | Dropout 使用 | 優化器 | 損失函數 | 訓練週期 (Epochs) |
|------|--------------|--------|-----------|------------------|
| A    | ❌ 無         | RMSprop | categorical_crossentropy | 30 |
| B    | ✅ 是 (0.25)  | RMSprop | categorical_crossentropy | 30 |

---

## 實驗結果摘要

| 模型 | 訓練正確率 | 測試正確率 | 備註 |
|------|-------------|-------------|------|
| A (無 Dropout) | 約 83%      | 約 76%      | 易過擬合，驗證波動較大 |
| B (含 Dropout) | 約 81%      | 約 76%      | 訓練穩定，測試表現略好 |

---

## 結論

- Dropout 可略降低訓練準確率，但有助於減少過擬合。
- 在驗證集上表現更穩定，適合實務部署。

---

## 專案結構

```plaintext
.
├── computer-vision-cnn(with dropout).ipynb     # 含 Dropout 的模型訓練程式
├── computer-vision-cnn(without dropout).ipynb  # 無 Dropout 的模型訓練程式
├── CNN.pdf                                     # 實驗報告文件(內含"訓練準確率"與"驗證準確率"之變化圖)
└── README.md
