# Fine-tuning DeepSeek-OCR với Dataset Tiếng Việt

## 1. Giới thiệu bài toán
Bài toán tập trung vào việc nhận dạng chữ viết tay tiếng Việt (Handwriting OCR), một trong những thách thức lớn trong lĩnh vực Xử lý ngôn ngữ tự nhiên và Thị giác máy tính do tính đa dạng trong nét chữ, độ nghiêng và các dấu thanh đặc trưng của tiếng Việt. Mục tiêu của đồ án là thực hiện tinh chỉnh (fine-tuning) mô hình DeepSeek-OCR để cải thiện khả năng trích xuất văn bản từ hình ảnh chữ viết tay một cách chính xác và hiệu quả.

## 2. Giới thiệu Dataset
[cite_start]Dữ liệu sử dụng trong bài toán là **UIT-HWDB**, một bộ dữ liệu chuẩn dành cho việc đánh giá nhận dạng chữ viết tay tiếng Việt trong điều kiện không ràng buộc.  
**Link dataset:** [UIT-HWDB](https://github.com/nghiangh/UIT-HWDB-dataset)


## 3. Fine-tuning Model DeepSeek-OCR
Quá trình huấn luyện được thực hiện dựa trên mô hình nền tảng DeepSeek-OCR với kỹ thuật QLoRA (Quantized Low-Rank Adaptation) để tối ưu hóa tài nguyên phần cứng, và tăng tốc qua thư viện [Unsloth](https://unsloth.ai/docs/models/tutorials/deepseek-ocr-how-to-run-and-fine-tune), giúp tiết kiệm bộ nhớ và đẩy nhanh tốc độ huấn luyện gấp 2 lần.

## 4. Thông tin sinh viên

| Họ và Tên | MSSV | Email |
| :--- | :--- | :--- |
| Trần Phụng Đình | 23127527 | tpdinh23@clc.fitus.edu.vn |