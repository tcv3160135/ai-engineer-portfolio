# 06 — Titanic Model Comparison Report

## 1. Kết quả so sánh

| Model         | Accuracy | F1-score |
|---------------|----------:|---------:|
| Logistic      | 0.798883  | 0.75000  |
| DecisionTree  | 0.798883  | 0.73913  |
| RandomForest  | 0.815642  | 0.77551  |

## 2. Nhận xét ngắn gọn
- **RandomForest** cho kết quả tốt nhất về cả *Accuracy* và *F1-score*, chứng tỏ ensemble học được các quan hệ phi tuyến và ổn định hơn.  
- **Decision Tree** có cùng *Accuracy* với Logistic nhưng *F1-score* thấp hơn → có thể do tree dự đoán phân bố nhãn khác (precision/recall trade-off) hoặc overfitting từng nhánh.  
- **Logistic** vẫn có hiệu năng tốt, cho thấy một phần quan hệ trong dữ liệu có tính tuyến tính; lợi thế là dễ giải thích và nhanh.

## 3. Giải thích chi tiết — Vì sao RandomForest tốt nhất
- RandomForest là ensemble của nhiều cây, tạo ra sự trung bình (bagging) giúp giảm variance so với một cây đơn.  
- Nhờ việc lấy mẫu cột và mẫu dòng ngẫu nhiên, RF ít bị ảnh hưởng bởi noise và biến quan trọng không chính xác.  
- Với Titanic (dữ liệu hỗn hợp numeric + categorical, mối quan hệ phi tuyến giữa các biến), RF thường bắt được tương tác tốt hơn Logistic.

## 4. Trade-offs (Lựa chọn mô hình dựa trên yêu cầu)
- **Giải thích (explainability):** Logistic > DecisionTree > RandomForest (RF khó giải thích toàn diện).  
- **Hiệu năng (accuracy/F1):** RandomForest > Logistic ≈ DecisionTree (tùy dataset).  
- **Tốc độ huấn luyện / dự đoán:** Logistic nhanh nhất, RF chậm nhất (tuỳ số cây).  
- **Nguy cơ overfit:** DecisionTree (cao) > RandomForest (thấp) > Logistic (thấp).

## 5. Cách cải thiện (kỹ thuật cụ thể)
1. **Hyperparameter tuning** cho RF & DT:
   - RandomizedSearchCV / GridSearchCV cho `n_estimators`, `max_depth`, `min_samples_leaf`, `max_features`.  
2. **Cross-validation (k-fold)** để có ước lượng ổn định hơn của Accuracy & F1.  
3. **Feature engineering**:
   - Thêm `family_size = SibSp + Parch`, `is_alone`, trích `title` từ tên, tương tác tuổi*fare, v.v.  
4. **Xử lý imbalance** (nếu cần): thử `class_weight='balanced'` hoặc oversampling (SMOTE) / undersampling.  
5. **Thử boosting models**: XGBoost / LightGBM thường mạnh hơn RF trên nhiều bài toán tabular khi được tune.  
6. **Calibration** nếu cần xác suất đầu ra chính xác (CalibratedClassifierCV).  
7. **Ensembling**: Stacking Logistic + RF + GBM có thể cải thiện thêm.

## 6. Ghi chú về kết quả hiện tại
- Hai mô hình Logistic và DecisionTree có cùng Accuracy nhưng F1 khác nhau → chỉ nhìn Accuracy có thể gây nhầm lẫn; nên ưu tiên metric phù hợp (Titanic thường dùng F1 khi cân bằng precision/recall quan trọng).  
- Đảm bảo bạn dùng cùng **X_test** và **y_test** cho tất cả mô hình (điều đó bạn đã làm đúng).

## 7. Kết luận (tóm tắt)
- **Chọn mô hình:** RandomForest là lựa chọn tốt nhất cho bài toán Titanic theo các chỉ số hiện tại (Accuracy 0.8156, F1 0.7755).  
- **Bước tiếp theo:** Tuning & feature engineering để cố gắng đẩy F1 lên cao hơn; nếu cần interpretability, cân nhắc dùng SHAP để giải thích RF.

---

## 8. Bài tập (5 dòng)
1. Mô hình tốt nhất là **RandomForest**.  
2. Vì RF là ensemble giúp giảm overfitting và bắt được mối quan hệ phi tuyến, nên Accuracy và F1 cao nhất.  
3. DecisionTree có thể overfit, dẫn đến F1 thấp hơn mặc dù Accuracy bằng Logistic.  
4. Logistic vẫn có lợi thế ở độ giải thích và tốc độ.  
5. Cải thiện bằng **tuning**, **feature engineering**, hoặc thử **XGBoost/LightGBM** và cross-validation.
