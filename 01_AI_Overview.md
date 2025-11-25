1. Tổng quan AI
  AI (Artificial Intelligence): hệ thống mô phỏng trí tuệ con người.
  -> tổng quát nhất, bất kỳ gì cho máy suy nghĩ đều thuộc AI.
  
  ML (Machine Learning): Phương pháp để AI tự học từ dữ liệu.
  -> AI = cái tổng, ML = một nhánh trong AI
  
  DL (Deep Learning): Một nhánh của ML sử dụng mạng nơ-ron sâu nhiều tầng
  -> Hiệu quả vượt trội khi có dữ liệu lớn + GPU
    DL có 3 kiểu học chính:
      - Supervised Learning (Học có giám sát): có label (nhãn), dự đoán giá nhà, phân loại email spam, nhận diện hình ảnh(dog/cat) - Mục tiêu Input -> Output
      - Unsupervised Learning (Học không giám sát): không label, phân loại nhóm khách hàng, giảm chiều dữ liệu (PCA) - Mục tiêu khám phá cấu trúc ẩn trong dữ liệu.
      - Reinforcement Learning (Học tăng cường): Agent học bằng thưởng - phạt, game, alphaGo, Robot, điều khiển tự động - Mục tiêu tối đa hóa tổng thưởng theo thời gian.
    Neural Network: gồm 3 phần chính
      - Input layer
          + Nhận dữ liệu đầu vào (pixel ảnh, số, text embedding...)
      - Hidden layers
          + Mỗi lớp có nhiều neurons
          + neurons học pattern bằng cách điều chỉnh weights
      - Output layer
          + Cho ra kết quả: 0/1, multi-class, giá trị dự đoán.
      - Cơ chế hoạt động cốt lõi: 
          + Forward pass: Input -> qua nhiều layers -> output dự đoán
          + Backward pass: So sánh dự đoán với sự thật -> tính lỗi -> điều chỉnh weights -> lập lại
          + Tối ưu bằng Gradient Descent
  
  Quan hệ 3 tầng:
  AI > ML > DL

2. ML/DL hoạt động thế nào
   Cốt lõi: máy học từ dữ liệu, rút ra pattern, dự đoán kết quả mới.

3. Pipeline chuẩn của AI/ML/DL
   Pipeline tiêu chuẩn cần nhơ:
    - Thu thập dữ liệu
        + file csv, hình ảnh, video, log, text, vv.
    - Xử lý - làm sạch - chuẩn hóa
        + Loại trùng, điền giá trị thiếu
        + chuẩn hóa số (standardization)
        + chuyển văn bản -> số (tokenization)
    - Tách dữ liệu
        + Train/Validation/Test
    - Huấn luyện mô hình
        + ML: random forest, SVM, XGBoost
        + DL: CNN, RNN, Transformers
    - Đánh giá mô hình
        + Accuracy, Precision, Recall
        + Confusion Matrix
    - Tối ưu
        + Hyperparameter tuning
        + Regularization
        + Early stopping
    - Triển khai (Deploy)
        + API, server, cloud, mobile
     
4. 3 ứng dụng muốn phát triển:
     - phát hiện mặt qua camera
     - xây dựng ứng dụng dự báo doanh thu, doanh số, xổ số.
     - tổng hợp phân tích dữ liệu báo cáo, trình bày dạng bảng, biểu đồ, sơ đồ.
     - automation xây dựng, phát triển quản bá sản phẩm kỹ thuật số video kênh tự động hoàn toàn.
