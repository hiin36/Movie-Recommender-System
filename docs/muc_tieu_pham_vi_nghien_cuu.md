# MỤC TIÊU VÀ PHẠM VI NGHIÊN CỨU

> **Đề tài:** Xây dựng Hệ thống Gợi ý Phim dựa trên Sở thích và Hành vi Người dùng
> *(Movie Recommender System Based on User Preferences and Behaviors)*
>
> **Cán bộ hướng dẫn:** TS. Trần Thị Hòa — Khoa Công nghệ Thông tin
> **Trường:** Đại học Mỏ - Địa Chất
> **Soạn thảo:** Trần Hải Yến (Trưởng nhóm) — MSV: 2121050001

---

## 1. MỤC TIÊU ĐỀ TÀI

### 1.1. Mục tiêu tổng quát

Xây dựng một hệ thống gợi ý phim (Movie Recommender System) hoàn chỉnh, kết hợp hai
phương pháp lọc thông tin chính — **Lọc theo nội dung (Content-Based Filtering)** và
**Lọc cộng tác (Collaborative Filtering)** — thành một mô hình **lai ghép (Hybrid)**
nhằm cung cấp danh sách phim gợi ý phù hợp với sở thích và hành vi đánh giá của
từng người dùng cá nhân.

### 1.2. Mục tiêu cụ thể

| STT | Mục tiêu | Phương pháp / Công nghệ | Tiêu chí đo lường |
|-----|----------|------------------------|--------------------|
| 1   | Xây dựng phân hệ **Content-Based Filtering** gợi ý phim tương tự dựa trên nội dung metadata | TF-IDF Vectorization + Cosine Similarity | Kết quả gợi ý phù hợp về thể loại, diễn viên, đạo diễn |
| 2   | Xây dựng phân hệ **Collaborative Filtering** dự đoán điểm đánh giá dựa trên hành vi người dùng | Phân rã ma trận SVD (thư viện Surprise) | RMSE ≤ 0.88 trên tập test |
| 3   | Thiết kế mô hình **Hybrid Recommender** kết hợp hai phân hệ trên | Weighted Linear Combination với trọng số α | Precision@10 ≥ 0.25 |
| 4   | Xử lý bài toán **Cold-Start** cho người dùng mới chưa có lịch sử đánh giá | Top Trending + Genre-based Filtering | Đảm bảo gợi ý cho 100% người dùng |
| 5   | Xây dựng **giao diện web** trực quan hiển thị kết quả gợi ý | Streamlit + TMDB API (poster, trailer) | Thời gian phản hồi < 1 giây |
| 6   | Đánh giá thực nghiệm định lượng với nhiều chỉ số | RMSE, MAE, Precision@K, Recall@K, NDCG@K, MAP | Bảng benchmark so sánh đầy đủ |

### 1.3. Ý nghĩa khoa học và thực tiễn

- **Ý nghĩa khoa học:** Nghiên cứu, triển khai và so sánh hiệu quả của các thuật toán
  lọc thông tin kinh điển (TF-IDF, SVD) trong bài toán gợi ý phim; đánh giá lợi ích
  của phương pháp lai ghép so với từng phương pháp đơn lẻ.

- **Ý nghĩa thực tiễn:** Xây dựng một ứng dụng web hoàn chỉnh có thể demo và trải
  nghiệm trực tiếp; cung cấp nền tảng mở rộng cho các nghiên cứu về hệ thống gợi ý
  trong các lĩnh vực khác (sách, âm nhạc, thương mại điện tử).

---

## 2. PHẠM VI NGHIÊN CỨU

### 2.1. Phạm vi về dữ liệu

- **Bộ dữ liệu chính:** The Movies Dataset (Kaggle - Rounak Banik)
  - `ratings_small.csv`: 100.004 bản ghi đánh giá | 671 người dùng | 9.125 bộ phim
  - `movies_metadata.csv`: Siêu dữ liệu > 45.000 bộ phim (genres, overview, budget, revenue...)
  - `credits.csv`: Danh sách diễn viên (cast) và đoàn làm phim (crew)
  - `keywords.csv`: Từ khóa cốt truyện
  - `links_small.csv`: Bảng ánh xạ movieId ↔ imdbId ↔ tmdbId

- **API bổ sung:** TMDB REST API (The Movie Database) — lấy poster ảnh gốc, YouTube trailer key,
  thông tin diễn viên/đạo diễn theo thời gian thực.

### 2.2. Phạm vi về phương pháp và thuật toán

| Phương pháp | Thuật toán cụ thể | Phạm vi áp dụng |
|-------------|-------------------|------------------|
| Content-Based Filtering | TF-IDF + Cosine Similarity | Gợi ý phim tương tự dựa trên metadata (genres, keywords, cast, crew, overview) |
| Collaborative Filtering | SVD (Singular Value Decomposition) | Dự đoán điểm đánh giá dựa trên ma trận tương tác người dùng - phim |
| Hybrid | Weighted Linear Combination | Kết hợp điểm số từ CBF và CF bằng trọng số α ∈ [0, 1] |
| Xử lý Cold-Start | Top Trending + Genre-based | Gợi ý cho người dùng mới chưa có lịch sử |

### 2.3. Phạm vi về công nghệ và nền tảng

- **Ngôn ngữ lập trình:** Python 3.10+
- **Thư viện ML:** scikit-learn (TF-IDF, Cosine), scikit-surprise (SVD), scipy (ma trận thưa CSR)
- **Trực quan hóa:** matplotlib, seaborn
- **Giao diện:** Streamlit
- **Quản lý mã nguồn:** Git + GitHub
- **Phân tích dữ liệu:** Jupyter Notebook, Pandas

### 2.4. Giới hạn phạm vi (Ngoài phạm vi)

Đề tài **KHÔNG** bao gồm:
- Triển khai mô hình Deep Learning phức tạp (NCF, Autoencoders, Transformers)
- Xây dựng hệ thống đánh giá thời gian thực (Real-time streaming)
- Thu thập dữ liệu đánh giá mới từ người dùng thực tế
- Triển khai lên máy chủ sản xuất (Production deployment)
- Xử lý ngôn ngữ đa quốc gia (Multi-language NLP)

---

## 3. CÂU HỎI NGHIÊN CỨU

1. **RQ1:** Phương pháp Content-Based Filtering sử dụng TF-IDF và Cosine Similarity
   có khả năng gợi ý phim tương tự chính xác đến mức nào trên bộ dữ liệu The Movies Dataset?

2. **RQ2:** Mô hình phân rã ma trận SVD đạt được mức sai số dự đoán điểm đánh giá (RMSE)
   bao nhiêu trên tập kiểm thử, và hiệu quả so với các mô hình đường cơ sở (Baseline)?

3. **RQ3:** Phương pháp Hybrid kết hợp CBF và CF có cải thiện đáng kể chất lượng gợi ý
   (Precision@K, NDCG@K) so với từng phương pháp đơn lẻ hay không?

---

*Soạn thảo: Trần Hải Yến — Tuần 1*
*Cập nhật lần cuối: 12/09/2026*
