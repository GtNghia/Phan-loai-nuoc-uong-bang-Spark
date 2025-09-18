Dự đoán Chất lượng Nước (Water Quality Prediction)
Dự án này sử dụng các kỹ thuật học máy và học sâu với Apache Spark để dự đoán Chỉ số Chất lượng Nước (Water Quality Index – WQI) và phân loại trạng thái chất lượng nước dựa trên các thông số hóa lý.

I. Mục đích dự án
Nước là một tài nguyên thiết yếu nhưng đang bị đe dọa bởi ô nhiễm. Việc giám sát và đánh giá chất lượng nước một cách hiệu quả là rất quan trọng để bảo vệ sức khỏe cộng đồng và môi trường. Dự án này xây dựng các mô hình dự đoán nhằm tự động hóa quá trình đánh giá chất lượng nước, giúp đưa ra các cảnh báo sớm và hỗ trợ việc ra quyết định.

Dữ liệu:

Dự án sử dụng bộ dữ liệu về chất lượng nước của Ấn Độ, được lấy từ Kaggle.

Bộ dữ liệu chứa các thông số như nhiệt độ (TEMP), oxy hòa tan (DO), pH, độ dẫn điện (CONDUCTIVITY), nhu cầu oxy sinh hóa (BOD), nitrat và nitrit, và coliform.

II. Các bước thực hiện
Quy trình của dự án bao gồm các bước chính sau:

Tiền xử lý dữ liệu (Data Preprocessing):

Làm sạch dữ liệu bằng cách loại bỏ các hàng có giá trị rỗng (null) ở các cột quan trọng.

Chuyển đổi kiểu dữ liệu của các cột thông số từ chuỗi (string) sang số thực (float) để phục vụ cho việc tính toán.

Phân tích dữ liệu khám phá (Exploratory Data Analysis - EDA):

Trực quan hóa sự biến thiên của các thông số chính (DO, pH, BOD, NN) để hiểu rõ hơn về đặc điểm của dữ liệu.

Sử dụng GeoPandas để tạo bản đồ trực quan hóa chỉ số WQI trung bình theo từng tiểu bang của Ấn Độ.

Kỹ thuật tạo đặc trưng (Feature Engineering):

Tính toán các chỉ số chất lượng (qn) cho từng thông số (pH, DO, BOD,...) dựa trên các tiêu chuẩn về nước sạch.

Tính toán Chỉ số Chất lượng Nước (WQI) tổng hợp bằng công thức trọng số: WQI = ∑(qn * Wn).

Phân loại WQI thành các cấp độ chất lượng (ví dụ: Excellent, Good, Poor, Very Poor, Unsuitable) để tạo ra nhãn cho mô hình phân loại.

Xây dựng và Đánh giá Mô hình:

Dữ liệu được chia thành hai tập: 80% cho huấn luyện (training) và 20% cho kiểm tra (testing).

Ba mô hình khác nhau đã được xây dựng và đánh giá:

III. Kết quả các mô hình
1. Mô hình Hồi quy Tuyến tính (Linear Regression - Spark ML)
Mục tiêu: Dự đoán giá trị WQI (một số liên tục).

Kỹ thuật: Sử dụng VectorAssembler để gom các đặc trưng và Normalizer để chuẩn hóa dữ liệu trước khi đưa vào mô hình LinearRegression.

Kết quả: Mô hình đạt độ chính xác cao trong việc dự đoán WQI.

Hệ số xác định R² ≈ 0.982

2. Mô hình Hồi quy Tuyến tính (Deep Learning - Keras)
Mục tiêu: Dự đoán giá trị WQI bằng mạng neural nhân tạo.

Kiến trúc: Mạng neural tuần tự (Sequential) với 3 lớp ẩn (350 нейрон mỗi lớp, hàm kích hoạt relu) và 1 lớp đầu ra (hàm linear).

Kết quả: Mô hình cho thấy sự sụt giảm đáng kể của giá trị mất mát (loss) qua các epoch, chứng tỏ khả năng học tốt từ dữ liệu.

3. Mô hình Hồi quy Logistic (Logistic Regression - Spark ML)
Mục tiêu: Phân loại trạng thái chất lượng nước (ví dụ: Poor, Good,...).

Kỹ thuật: Sử dụng StringIndexer để chuyển đổi nhãn chuỗi thành số, sau đó áp dụng VectorAssembler, Normalizer và LogisticRegression.

Kết quả: Mô hình đạt độ chính xác rất cao trong việc phân loại.

Độ chính xác (Accuracy) ≈ 0.986

IV. Môi trường và Cài đặt
Dự án này được xây dựng trong môi trường Google Colab.

Yêu cầu quan trọng:

Java 8: PySpark yêu cầu phiên bản Java 8 để hoạt động ổn định. Notebook đã bao gồm các lệnh để gỡ bỏ phiên bản Java mặc định và cài đặt OpenJDK 8.

Thư viện chính:

pyspark

pandas

keras (với backend tensorflow)

geopandas

matplotlib & seaborn

numpy
