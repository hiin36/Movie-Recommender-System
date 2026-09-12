# KHUNG MỤC LỤC BÁO CÁO ĐỒ ÁN 2

> **Đề tài:** Xây dựng Hệ thống Gợi ý Phim dựa trên Sở thích và Hành vi Người dùng
> *(Movie Recommender System Based on User Preferences and Behaviors)*
>
> **Trường:** Đại học Mỏ - Địa Chất | **Khoa:** Công nghệ Thông tin
> **GVHD:** TS. Trần Thị Hòa
> **Xây dựng khung mục lục:** Trần Hải Yến (Trưởng nhóm)

---

## MỤC LỤC CHI TIẾT

### PHẦN MỞ ĐẦU
- Lời cam đoan
- Lời cảm ơn
- Danh mục từ viết tắt
- Danh mục bảng biểu
- Danh mục hình ảnh
- Mục lục

---

### CHƯƠNG 1: TỔNG QUAN ĐỀ TÀI VÀ BÀI TOÁN LỌC THÔNG TIN
> **Phụ trách chính:** Trần Hải Yến (Trưởng nhóm)

1.1. Đặt vấn đề
    - Sự bùng nổ nội dung số và bài toán quá tải thông tin (Information Overload)
    - Vai trò của hệ thống gợi ý trong các nền tảng giải trí (Netflix, Spotify, YouTube)

1.2. Mục tiêu đề tài
    - Mục tiêu tổng quát
    - Mục tiêu cụ thể (6 mục tiêu)

1.3. Phạm vi nghiên cứu
    - Phạm vi về dữ liệu (The Movies Dataset - Kaggle)
    - Phạm vi về phương pháp (CBF, CF, Hybrid)
    - Phạm vi về công nghệ (Python, Streamlit, Surprise)
    - Giới hạn phạm vi (ngoài đề tài)

1.4. Phương pháp nghiên cứu
    - Nghiên cứu lý thuyết
    - Thực nghiệm và đánh giá
    - Thiết kế hệ thống phần mềm

1.5. Bố cục báo cáo
    - Tóm tắt nội dung 5 chương

---

### CHƯƠNG 2: CƠ SỞ LÝ THUYẾT
> **Phụ trách chính:**
> - Phần Content-Based: Nguyễn Trung Hiếu
> - Phần Collaborative Filtering: Nguyễn Thế Trung

2.1. Tổng quan về Hệ thống Gợi ý (Recommender Systems)
    - Định nghĩa và phân loại
    - Lịch sử phát triển

2.2. Phương pháp Lọc theo Nội dung (Content-Based Filtering)
    2.2.1. Nguyên lý hoạt động
    2.2.2. Thuật toán TF-IDF (Term Frequency - Inverse Document Frequency)
        - Công thức TF-IDF: w(t,d) = TF(t,d) × log(N / DF(t))
    2.2.3. Độ đo tương đồng Cosine Similarity
        - Công thức: sim(u, v) = (u · v) / (||u|| × ||v||)
    2.2.4. Ưu điểm và nhược điểm

2.3. Phương pháp Lọc Cộng tác (Collaborative Filtering)
    2.3.1. Nguyên lý hoạt động
    2.3.2. Phương pháp Memory-based: User-based k-NN và Item-based k-NN
    2.3.3. Phương pháp Model-based: Phân rã ma trận SVD
        - Công thức dự đoán: r̂(u,i) = μ + b_u + b_i + p_u^T · q_i
        - Hàm mất mát với điều chuẩn L2
        - Giải thuật tối ưu SGD (Stochastic Gradient Descent)
    2.3.4. Ưu điểm và nhược điểm

2.4. Phương pháp Lai ghép (Hybrid Recommender System)
    2.4.1. Các chiến lược kết hợp (Weighted, Switching, Feature Combination...)
    2.4.2. Công thức kết hợp trọng số tuyến tính
        - Hybrid_Score = α × CBF_Score + (1 − α) × CF_Score

2.5. Bài toán Khởi đầu lạnh (Cold-Start Problem)
    - Người dùng mới (New User)
    - Sản phẩm mới (New Item)
    - Giải pháp: Top Trending + Genre-based

2.6. Các chỉ số đánh giá hệ thống gợi ý
    2.6.1. Chỉ số sai số dự đoán: RMSE, MAE
    2.6.2. Chỉ số chất lượng xếp hạng: Precision@K, Recall@K
    2.6.3. Chỉ số xếp hạng tích lũy: NDCG@K, MAP

---

### CHƯƠNG 3: THIẾT KẾ KIẾN TRÚC HỆ THỐNG GỢI Ý
> **Phụ trách chính:** Trần Hải Yến (Trưởng nhóm)

3.1. Kiến trúc tổng thể hệ thống
    - Sơ đồ Data Pipeline Flowchart 5 tầng

3.2. Tầng 1: Thu nạp Dữ liệu (Data Ingestion)
    - Nguồn dữ liệu Kaggle (ratings, metadata, credits, keywords)
    - Kết nối TMDB REST API

3.3. Tầng 2: Tiền xử lý và Trích xuất Đặc trưng (Preprocessing)
    3.3.1. Nhánh Content-Based: Làm sạch text → Metadata Soup
    3.3.2. Nhánh Collaborative: Ma trận tương tác → Lọc k-core → CSR

3.4. Tầng 3: Lõi Mô hình (Model Core)
    3.4.1. TF-IDF Vectorizer + Cosine Similarity
    3.4.2. SVD Training Pipeline

3.5. Tầng 4: Động cơ Lai ghép (Hybrid Engine)
    - Chuẩn hóa Min-Max
    - Kết hợp trọng số α

3.6. Tầng 5: Tầng Hiển thị (Presentation Layer)
    - Giao diện Streamlit
    - Tích hợp TMDB API (Poster, Trailer)

3.7. Thiết kế cơ sở dữ liệu và cấu trúc file
    - Sơ đồ ER (Entity Relationship)
    - Cây thư mục dự án

---

### CHƯƠNG 4: CÀI ĐẶT VÀ THỰC NGHIỆM
> **Phụ trách chính:**
> - Tiền xử lý & API: Nguyễn Mạnh Định
> - Mô hình Content-Based: Nguyễn Trung Hiếu
> - Mô hình SVD & Đánh giá: Nguyễn Thế Trung

4.1. Môi trường thực nghiệm
    - Phần cứng, phần mềm, thư viện

4.2. Tiền xử lý dữ liệu
    4.2.1. Khám phá dữ liệu (EDA)
        - Phân bố điểm đánh giá
        - Hoạt động người dùng (User Activity)
        - Độ phổ biến phim (Movie Popularity)
    4.2.2. Xử lý giá trị khuyết và trùng lặp
    4.2.3. Trích xuất và ghép Metadata Soup
    4.2.4. Xây dựng ma trận thưa CSR

4.3. Mô hình Content-Based Filtering
    4.3.1. TF-IDF Vectorization
    4.3.2. Tính toán Cosine Similarity Matrix
    4.3.3. Truy vấn Top-K phim tương tự

4.4. Mô hình Collaborative Filtering
    4.4.1. Huấn luyện mô hình SVD (Surprise)
    4.4.2. Tối ưu siêu tham số (GridSearchCV)
    4.4.3. Đường cong hội tụ hàm mất mát

4.5. Mô hình Hybrid Recommender
    4.5.1. Chuẩn hóa và kết hợp điểm số
    4.5.2. Xử lý Cold-Start

4.6. Tích hợp TMDB API
    4.6.1. Lấy Poster và Trailer
    4.6.2. Cơ chế caching và retry

4.7. Giao diện Streamlit
    4.7.1. Thiết kế giao diện (Wireframe)
    4.7.2. Tính năng tìm kiếm phim tương tự
    4.7.3. Tính năng gợi ý cá nhân hóa
    4.7.4. Thanh trượt trọng số α

4.8. Đánh giá thực nghiệm
    4.8.1. So sánh RMSE, MAE giữa các mô hình
    4.8.2. So sánh Precision@K, Recall@K, NDCG@K
    4.8.3. Bảng Benchmark tổng hợp
    4.8.4. Biểu đồ so sánh trực quan

---

### CHƯƠNG 5: KẾT LUẬN VÀ HƯỚNG PHÁT TRIỂN
> **Phụ trách chính:** Trần Hải Yến (Trưởng nhóm) + Cả nhóm

5.1. Tổng kết kết quả đạt được
    - Đối chiếu với 6 mục tiêu đề ra
    - Trả lời 3 câu hỏi nghiên cứu (RQ1, RQ2, RQ3)

5.2. Đóng góp của đề tài
    - Đóng góp khoa học
    - Đóng góp thực tiễn

5.3. Hạn chế
    - Giới hạn dữ liệu
    - Giới hạn mô hình

5.4. Hướng phát triển trong tương lai
    - Deep Learning (NCF, Autoencoders)
    - Real-time Streaming
    - Triển khai Production

---

### PHẦN PHỤ LỤC
- Tài liệu tham khảo
- Phụ lục mã nguồn
- Phụ lục kết quả thực nghiệm chi tiết
- Phụ lục báo cáo sử dụng AI

---

## BẢNG PHÂN CÔNG VIẾT BÁO CÁO

| Chương | Nội dung | Người phụ trách chính | Người hỗ trợ |
|--------|----------|----------------------|--------------|
| Chương 1 | Tổng quan đề tài & Bài toán lọc thông tin | Trần Hải Yến | — |
| Chương 2 (CBF) | Cơ sở lý thuyết Content-Based | Nguyễn Trung Hiếu | — |
| Chương 2 (CF) | Cơ sở lý thuyết Collaborative Filtering | Nguyễn Thế Trung | — |
| Chương 3 | Thiết kế kiến trúc hệ thống | Trần Hải Yến | — |
| Chương 4 (Data) | Tiền xử lý & Tích hợp API | Nguyễn Mạnh Định | — |
| Chương 4 (CBF) | Mô hình Content-Based | Nguyễn Trung Hiếu | — |
| Chương 4 (CF) | Mô hình SVD & Đánh giá thực nghiệm | Nguyễn Thế Trung | — |
| Chương 5 | Kết luận & Hướng phát triển | Trần Hải Yến | Cả nhóm |

---

*Xây dựng khung mục lục: Trần Hải Yến — Tuần 2*
*Cập nhật lần cuối: 12/09/2026*
