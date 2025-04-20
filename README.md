# Emergency CNN Classification with Dropout Comparison

針對 CNN 模型進行 Dropout 正則化的實驗，探討其對於緊急事件圖片分類的影響。

##  專案目的                                                                                                                            
比較 CNN 模型在有無dropout(隨機失活)的形況下對模型的影響。

##  資料集                                                                                                                                            
- 來源：Kaggle 緊急影像分類比賽資料集（如 hp-2020）
- 訓練資料：1646 張                                                                                                                                            
- 測試資料：706 張                                                                                                                                            
- 圖片大小：28x28x3                                                                                                                                            

##  模型設計                                                                                                                                            
- 模型 A：Baseline CNN
- 模型 B：CNN + Dropout(0.25)
- 優化器：RMSprop                                                                                                                                            
- 損失函數：categorical_crossentropy

##  實驗結果摘要                                                                                                                                            

| 模型 | 訓練正確率 | 測試正確率 | 備註 |
|------|-------------|-------------|------|
| A    | 約 83%      | 約 76%      | 無 Dropout，易過擬合 |
| B    | 約 81%      | 約 76%      | 加入 Dropout，測試穩定 |

##  結論                                                                                                                                            
Dropout 雖稍微降低訓練準確率，但可有效降低過擬合、提升測試穩定性。

##  執行方式                                                                                                                                            
```bash                                                                                                                                            
pip install -r requirements.txt
python model/model_no_dropout.py
python model/model_with_dropout.py
