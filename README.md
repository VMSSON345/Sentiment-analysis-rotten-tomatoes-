# Mô hình dựa trên ROBERTa với Pre-Attention và LSTM để phân loại cảm xúc cho bài đánh giá phim

Dự án này trình bày một kiến trúc mô hình lai để phân loại cảm xúc của các bài đánh giá phim, tận dụng sức mạnh của các mô hình Transformer được huấn luyện trước cùng với các cơ chế attention và mạng nơ-ron hồi quy.

## 📖 Tổng quan

Nhiệm vụ là phân loại các bài đánh giá phim từ bộ dữ liệu **Rotten Tomatoes** thành các loại cảm xúc **tích cực** hoặc **tiêu cực**.

Mô hình được đề xuất là một kiến trúc lai kết hợp các thành phần sau:

1.  **Bộ mã hóa ROBERTa**: Sử dụng mô hình `roberta-base` được huấn luyện trước để tạo ra các biểu diễn từ theo ngữ cảnh.
2. **Lớp Pre-Attention**: Áp dụng một cơ chế self-attention nhẹ lên các trạng thái ẩn của ROBERTa để làm nổi bật các token quan trọng nhất đối với việc phân tích cảm xúc.
3.  **Lớp Bi-directional LSTM (Bi-LSTM)**: Xử lý các biểu diễn đã được trọng số hóa bởi attention để nắm bắt các mẫu tuần tự và phụ thuộc xa trong văn bản.
4. **Đầu phân loại MLP**: Một mạng Perceptron đa lớp (MLP) nhỏ sẽ đưa ra dự đoán cảm xúc cuối cùng.

Kiến trúc này được thiết kế để vượt qua các phương pháp tinh chỉnh (fine-tuning) tiêu chuẩn bằng cách nắm bắt hiệu quả hơn các mẫu tuần tự và các tương tác token chi tiết.

## ⚙️ Kiến trúc mô hình

Sơ đồ tổng quan về kiến trúc của mô hình:

<img width="885" height="899" alt="image" src="https://github.com/user-attachments/assets/bd627378-06b6-4bf8-bcc9-570d9e32d584" />


## 🚀 Kết quả

Mô hình đạt được kết quả hiệu suất ấn tượng trên bộ dữ liệu thử nghiệm (test set):

  * **Độ chính xác (Accuracy)**: 87.15%
  * **F1-Score**: 0.8712
  * **Độ chính xác (Precision)**: 0.8746
  * **Độ thu hồi (Recall)**: 0.8715

Những kết quả này cho thấy mô hình vượt trội so với việc tinh chỉnh ROBERTa tiêu chuẩn và các biến thể chỉ sử dụng attention gần đây.Các nghiên cứu loại bỏ (ablation studies) cũng xác nhận rằng mỗi thành phần (pre-attention, LSTM, và MLP) đều đóng góp một cách có ý nghĩa vào hiệu suất cuối cùng.





