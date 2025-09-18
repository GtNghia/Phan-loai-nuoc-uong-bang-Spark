Dự đoán Chất lượng Nước (Water Quality Prediction)
Dự án này sử dụng các kỹ thuật học máy và học sâu với Apache Spark để dự đoán Chỉ số Chất lượng Nước (Water Quality Index – WQI) và phân loại trạng thái chất lượng nước dựa trên các thông số.

I. Mục đích dự án

  Nước là một tài nguyên thiết yếu nhưng đang bị đe dọa bởi ô nhiễm. Việc giám sát và đánh giá chất lượng nước là rất quan trọng để bảo vệ sức khỏe cộng đồng và môi trường. Dự án này xây dựng các mô hình dự đoán nhằm tự động đánh giá chất lượng nước, giúp đưa ra các cảnh báo và hỗ trợ việc ra quyết định.

Dữ liệu:

  Dự án sử dụng bộ dữ liệu về chất lượng nước của Ấn Độ, được lấy từ Kaggle.

  Bộ dữ liệu chứa các thông số như nhiệt độ (TEMP), oxy hòa tan (DO), pH, độ dẫn điện (CONDUCTIVITY), nhu cầu oxy sinh hóa (BOD), nitrat và nitrit, và coliform.



II. Kết quả các mô hình 

1. Mô hình Hồi quy Tuyến tính (Dự đoán chỉ số WQI)
Mục tiêu: Dự đoán chính xác chỉ số chất lượng nước (WQI) dưới dạng một con số.

Hệ số R² ≈ 0.982, nghĩa là các thông số đầu vào giải thích được 98.2% sự thay đổi của WQI.

2. Mô hình Học sâu - Keras (Dự đoán chỉ số WQI)
Mục tiêu: Dùng mạng нейрон nhân tạo để dự đoán chỉ số WQI.

3. Mô hình Hồi quy Logistic (Phân loại chất lượng nước)
Mục tiêu: Phân loại nước vào các nhóm như "Tốt", "Kém", hay "Rất Kém".

Độ chính xác (Accuracy) ≈ 0.986, nghĩa là mô hình gán nhãn đúng cho chất lượng nước tới 98.6% số trường hợp.


