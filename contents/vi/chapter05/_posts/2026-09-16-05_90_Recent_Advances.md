---
layout: post
title: "Lecture 05.90: Tiến bộ gần đây (2022–2026) — Mapper, UMAP, và hình thương của dữ liệu"
lang: vi
lang-ref: lecture-05-90
chapter: 5
lecture: 90
order: 90
lesson_type: optional
categories: [chapter05]
tags: [optional, recent-advances, mapper, umap, quotient, manifolds]
description: "Bài tùy chọn: quotient/surfaces gặp Mapper, phê bình UMAP, và đồ thị phủ dữ liệu. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Tô-pô thương, phân loại mặt, phức CW và tác động nhóm của Chapter 05 vẫn giữ nguyên nền tảng; ở đây ta xem cách chúng được ứng dụng trong thuật toán Mapper và so sánh với phương pháp giảm chiều UMAP.

---

## 📖 Tổng quan

Thuật toán Mapper (ra đời năm 2007) mang bản chất của một phép lấy thương: chọn một hàm lọc (filter) $f:X\to\mathbb{R}^k$, phủ miền giá trị bằng các tập mở có chồng lấn, lấy các thành phần liên thông (hoặc cụm) trong từng nghịch ảnh, rồi dán chúng thành một đồ thị (hay phức đơn hình). Đây chính là ý tưởng "dán theo sợi" của Chapter 05 áp dụng cho dữ liệu hữu hạn. Giai đoạn 2022–2026 ghi nhận các khảo sát tổng hợp về Mapper, các khung đánh giá độ ổn định, cùng nhiều phân tích chỉ rõ rằng các phương pháp giảm chiều phổ biến như UMAP *không* phải là ánh xạ thương tô-pô.

![Torus](https://upload.wikimedia.org/wikipedia/commons/1/17/Torus.png)
*Hình xuyến là thương của hình vuông sau khi dán cạnh — hình mẫu trực quan cho phép dán trong Mapper. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus.png)*

---

## 🎯 Trực giác

Tương tự phép dán $S^1=[0,1]/\{0\sim 1\}$, Mapper xử lý một đám mây điểm bằng cách vẽ cạnh nối hai cụm địa phương nếu chúng có điểm chung nằm trong phần giao của hai tập lọc chồng lấn — tức thao tác *dán*. UMAP cũng xây dựng một đồ thị láng giềng rồi nhúng xuống $\mathbb{R}^2$, nhưng bước nhúng này không còn mang tính chất của ánh xạ thương. Phân biệt rõ hai cơ chế này là một bài học hữu ích từ Chapter 05 cho khoa học dữ liệu.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Khảo sát tổng hợp về Mapper (2007–2025)

Madukpe, Ugoala và Zulkepli (2025) thực hiện tổng quan có hệ thống về thuật toán Mapper và các ứng dụng liên ngành. Dưới góc nhìn của bài 05.00, mỗi biến thể của Mapper tương ứng với một cách chọn phủ mở và một cách gom cụm thành phần khác nhau, từ đó tạo ra một không gian thương khác nhau.

- Vine Nwabuisi Madukpe, Bright Chukwuma Ugoala, Nur Fariha Syaqina Zulkepli, *A Comprehensive Review of the Mapper Algorithm … (2007–2025)*, arXiv:2504.09042 (2025).

### 2. Độ ổn định và đánh giá thuật toán Mapper

Sen, Singh và Tiwari (2026) đề xuất khung đánh giá ba trục cho các thuật toán Mapper, đồng thời giới thiệu biến thể GK-Mapper dựa trên kỹ thuật phân cụm Gustafson–Kessel. Ahsan, Das và Mukhopadhyay (2026) đề xuất chọn phủ theo dữ liệu (MAPLE) nhằm giảm sự phụ thuộc vào tham số thủ công — giải quyết vấn đề cố hữu của phép lấy thương là thay đổi phủ có thể làm thay đổi đáng kể không gian thương thu được.

- Annesha Sen, Shivam Singh, S. P. Tiwari, *A Three Axis Evaluation Framework for Mapper Algorithms*, arXiv:2606.21688 (2026).
- Md Moinul Ahsan, Priyam Das, Nitai D. Mukhopadhyay, *MAPLE: Mapper Based Localized Prediction with Data Driven Cover Selection*, arXiv:2607.06797 (2026).

### 3. UMAP không phải phép nhúng đa tạp và không phải Mapper

Yang (2026) chỉ ra rằng UMAP thông dụng tương đương với phân cụm phổ (spectral clustering) trên đồ thị láng giềng mờ. Li và Zhang (2026) đề xuất bổ sung thông tin tiên nghiệm hình học và tô-pô để khắc phục hạn chế này (thuật toán JORC-UMAP). Về mặt khái niệm, dù UMAP tạo ra hình ảnh trông giống bản đồ của một đa tạp (các bài 05.01–05.03), nó không thỏa mãn tính chất phổ dụng của không gian thương và không tạo ra thần kinh (nerve) của một phủ mở như Mapper.

- Yang Yang, *UMAP Is Spectral Clustering on the Fuzzy Nearest-Neighbor Graph*, arXiv:2602.11662 (2026).
- Xiaobin Li, Run Zhang, *Understanding and Improving UMAP with Geometric and Topological Priors: The JORC-UMAP Algorithm*, arXiv:2601.16552 (2026).

### 4. Mapper trong phân tích sống còn và học có cấu trúc

Kibisi, Abawonse và Woukeng (2026) áp dụng Mapper vào phân tích sống còn ở bệnh nhân ung thư vú, sử dụng đồ thị thương như đặc trưng lâm sàng. Babus và Nasrin (2026) nghiên cứu học có cấu trúc trực tiếp trên biểu diễn Mapper, lấy không gian thương làm không gian nền cho mô hình học máy.

Nếu $f:X\to\mathbb{R}$ là hàm lọc và $\mathcal{U}=\{U_i\}$ là một phủ của $f(X)$, thì thần kinh (nerve)
$$
N(\{C:C\text{ thành phần của }f^{-1}(U_i)\})
$$
là một phức CW (thường là một đồ thị), kết nối trực tiếp với ngôn ngữ của bài 05.02.

- Emmanuel Kibisi, Olakunle Abawonse, Donald Woukeng, *Topology-Informed Survival Analysis of Breast Cancer Patients Using the Mapper Algorithm*, arXiv:2607.15022 (2026).
- George Babus, Farzana Nasrin, *Structured Learning on Mapper Representations*, arXiv:2608.22044 (2026).

---

## 🧠 Tài liệu

- Munkres, *Topology*, Ch. 2 §22 (tô-pô thương), Ch. 12 (các mặt, trong một số ấn bản).
- Hatcher, *Algebraic Topology*, Ch. 0 (phức CW và minh họa thương).
- Các bài báo arXiv liệt kê ở trên.

## 🔗 Ứng dụng

Trong phân tích dữ liệu đơn bào (single-cell), Mapper đôi khi giữ được các nhánh phân hóa tế bào mà phép nhúng UMAP làm phẳng đi. Lý thuyết Chapter 05 giải thích điều này: phép lấy thương bảo toàn cấu trúc sợi của hàm lọc, còn phép nhúng phổ không đảm bảo tính chất đó.

## Video tham khảo

- **xem trước** [The Mapper Algorithm | Overview & Python Example Code](https://www.youtube.com/watch?v=NlMrvCYlOOQ) — Shaw Talebi, tiếng Anh. Trình bày thuật toán Mapper (phủ, thương và đồ thị dữ liệu), bám sát nội dung bài.
- [UMAP Dimension Reduction, Main Ideas!!!](https://www.youtube.com/watch?v=eN0wFzBA4Sc) — StatQuest with Josh Starmer, tiếng Anh. Giải thích ý tưởng chính của UMAP để đối chiếu với Mapper.

## 🧩 Bài tập

1. Với $X=S^1$ và $f$ là hàm chiều cao, phác họa đồ thị Mapper khi phủ miền giá trị bằng $3$ khoảng mở chồng lấn.
2. Chỉ ra một phủ làm cho đồ thị Mapper của hình số $8$ suy biến thành một cạnh duy nhất (mất vòng khép kín).
3. Viết một câu ngắn gọn phân biệt ánh xạ thương và phép nhúng UMAP.
