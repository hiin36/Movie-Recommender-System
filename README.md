# 🎬 Xây dựng Hệ thống Gợi ý Phim dựa trên Sở thích và Hành vi Người dùng
### Movie Recommender System Based on User Preferences and Behaviors

> **Trường Đại học Mỏ - Địa chất** — Khoa Công nghệ Thông tin
> **Cán bộ hướng dẫn:** TS. Trần Thị Hòa

---

##  Thông tin nhóm

| Họ và tên | MSV | Lớp | Vai trò |
|-----------|-----|-----|---------|
| Trần Hải Yến | 2121050840 | DCCTDH67A | Trưởng nhóm |
| Nguyễn Thế Trung | 2121050002 | DCCTDH67A | Thành viên |
| Nguyễn Mạnh Định | 2121050003 | DCCTDH67A | Thành viên |
| Nguyễn Trung Hiếu | 2121050004 | DCCTDH67A | Thành viên |

---

## Mục tiêu đề tài

Xây dựng hệ thống gợi ý phim kết hợp hai phương pháp chính:
1. **Content-Based Filtering (CBF):** Gợi ý phim dựa trên độ tương đồng nội dung (TF-IDF + Cosine Similarity) từ metadata phim (thể loại, từ khóa, diễn viên, đạo diễn, mô tả).
2. **Collaborative Filtering (CF):** Gợi ý phim dựa trên hành vi đánh giá của người dùng (phân rã ma trận SVD).
3. **Hybrid Recommender:** Kết hợp hai phương pháp trên bằng hàm trọng số tuyến tính α để tận dụng ưu điểm và bù đắp nhược điểm của từng phương pháp.

##  Cấu trúc thư mục

```
Movie-Recommender-System/
├── data/
│   ├── raw/                    # Dữ liệu thô từ Kaggle
│   ├── processed/              # Dữ liệu đã tiền xử lý
│   └── external/               # Dữ liệu từ TMDB API
├── notebooks/                  # Jupyter Notebook thực nghiệm
├── src/
│   ├── models/                 # Mô hình ML (CBF, CF, Hybrid)
│   ├── preprocessing/          # Module tiền xử lý
│   ├── evaluation/             # Module đánh giá (RMSE, Precision@K...)
│   ├── api/                    # Kết nối TMDB API
│   └── utils/                  # Hàm tiện ích
├── web/                        # Giao diện Streamlit
├── reports/                    # Báo cáo tiến độ theo tuần
├── docs/                       # Tài liệu kỹ thuật & kiến trúc
├── tests/                      # Unit test
├── models/                     # Mô hình đã huấn luyện (.pkl)
├── figures/                    # Hình ảnh, biểu đồ
├── requirements.txt
└── README.md
```

##  Bộ dữ liệu

Sử dụng bộ dữ liệu **The Movies Dataset** (Kaggle - Rounak Banik):
- `ratings_small.csv` — 100.004 lượt đánh giá từ 671 người dùng trên 9.125 phim
- `movies_metadata.csv` — Siêu dữ liệu 45.000+ phim (genres, overview, budget...)
- `credits.csv` — Thông tin diễn viên và đoàn làm phim
- `keywords.csv` — Từ khóa cốt truyện
- `links_small.csv` — Ánh xạ movieId ↔ imdbId ↔ tmdbId
  
---
*Hà Nội, Năm 2026*
