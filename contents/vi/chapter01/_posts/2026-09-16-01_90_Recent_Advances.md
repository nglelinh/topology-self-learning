---
layout: post
title: "Lecture 01.90: Tiến bộ gần đây (2022–2026) — Tô-pô của dữ liệu và phân cụm"
lang: vi
lang-ref: lecture-01-90
chapter: 1
lecture: 90
order: 90
lesson_type: optional
categories: [chapter01]
tags: [optional, recent-advances, clustering, topology-of-data, tda]
description: "Bài tùy chọn: point-set topology gặp clustering và TDA (2022–2026). Không viết lại lý thuyết."
---

**Bài tùy chọn.** Các định nghĩa về tập mở, cơ sở, bao đóng và ánh xạ liên tục của Chương 01 vẫn giữ nguyên. Bài này chỉ trình bày cách các khái niệm đó xuất hiện trong bài toán phân cụm và phân tích dữ liệu khi $X$ là một đám mây điểm.

---

## 📖 Tổng quan

Một tô-pô trên $X$ cho biết cấu trúc lân cận giữa các điểm mà không cần cố định một mê-tric. Phân cụm (*clustering*) cũng đặt ra câu hỏi tương tự dưới dạng thuật toán: đâu là những nhóm điểm gắn kết tự nhiên trong dữ liệu? Trong giai đoạn 2022–2026, các phương pháp phân cụm tô-pô đã phát triển thành những thuật toán đa tỉ lệ, đa tham số đi kèm định lý ổn định chặt chẽ.

![Phân cụm](https://upload.wikimedia.org/wikipedia/commons/c/c8/Cluster-2.svg)
*Hai cụm trong mặt phẳng: phiên bản rời rạc của tính không liên thông. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cluster-2.svg)*

---

## 🎯 Trực giác

Theo định nghĩa tập mở, nếu $x \in U$ thì cả một vùng lân cận quanh $x$ cũng nằm trong $U$. Với dữ liệu thực tế, lân cận quanh $x$ thường được xấp xỉ bởi $k$ láng giềng gần nhất hoặc hình cầu bán kính $\varepsilon$. Khi $\varepsilon$ rất nhỏ, mỗi điểm tách thành một cụm riêng; khi $\varepsilon$ đủ lớn, toàn bộ dữ liệu gộp làm một. **Phân cụm bền vững** (*persistent clustering*) theo dõi sự xuất hiện và hợp nhất của các cụm khi thay đổi $\varepsilon$ — tương ứng trực tiếp với việc so sánh các tô-pô thô hơn và mịn hơn ở Bài 01.01.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Phân cụm mật độ đa tỉ lệ bền vững

Bot, McInnes và Aerts (2025) đề xuất *Persistent Multiscale Density-based Clustering*: thay vì chọn cố định một ngưỡng mật độ duy nhất, thuật toán theo dõi các thành phần liên thông của các tập siêu mức mật độ theo một phép lọc. Cách tiếp cận này chuyển trực tiếp khái niệm Chương 01 thành thuật toán: họ tập mở $\{x : \rho(x) > \lambda\}$ biến thiên theo $\lambda$ với sự thay đổi cấu trúc tô-pô được kiểm soát.

- Daniël Bot, Leland McInnes, Jan Aerts, *Persistent Multiscale Density-based Clustering*, arXiv:2512.16558 (2025).

### 2. ToMATo và phân cụm tô-pô đa tham số

Dòng thuật toán ToMATo (*Topological Mode Analysis Tool*) kết hợp các cực đại mật độ với homology bền vững $0$-chiều. Martineau, Pouzat và Geffray (2025) mở rộng ToMATo cho dữ liệu chiều cao (như phân loại tín hiệu thần kinh *spike sorting*). Andrianirina và Carrière (2026) tiếp tục phát triển thành ToMAToMP — thuật toán phân cụm đa tham số có tính ổn định. Về mặt hình học, mỗi "mode" tương ứng với đỉnh của hàm mật độ, còn các "thung lũng" là biên ngăn cách giữa các cụm — đúng với trực giác bao đóng và biên của tô-pô đại cương.

- Louise Martineau, Christophe Pouzat, Ségolen Geffray, *ToMATo: an efficient and robust clustering algorithm for high dimensional datasets*, arXiv:2509.17499 (2025).
- Ludo Andrianirina, Mathieu Carrière, *ToMAToMP: Robust and Multi-Parameter Topological Clustering*, arXiv:2605.14824 (2026).

### 3. Ánh xạ liên tục và phép đồng phôi trong giảm chiều

Thuật toán UMAP hướng tới việc bảo toàn cấu trúc tô-pô địa phương khi giảm chiều dữ liệu. Dalmia và Sia (2021, có ảnh hưởng kéo dài trong giai đoạn 2022–2026) chỉ ra rằng **tính liên thông** của đồ thị láng giềng quyết định trực tiếp chất lượng phân cụm sau khi chạy UMAP: mất cạnh nối có thể làm đứt thành phần liên thông. Đây là minh họa thực nghiệm cho Bài 01.03: một ánh xạ chỉ "gần liên tục" có thể phá vỡ tính đồng phôi và làm gộp hoặc tách nhầm các cụm.

- Ayush Dalmia, Suzanna Sia, *Clustering with UMAP: Why and How Connectivity Matters*, arXiv:2108.05525 (2021).

### 4. Tô-pô của mạng nơ-ron như không gian dữ liệu

Ballester, Casacuberta và Escalera (2023) khảo sát việc ứng dụng TDA để phân tích mạng nơ-ron: không gian trọng số, không gian kích hoạt và tập dữ liệu đều được xem như các không gian tô-pô, còn quá trình lan truyền tiến (*forward pass*) đóng vai trò ánh xạ liên tục giữa chúng — đúng theo khung lý thuyết của Chương 01 nhưng ở quy mô hàng triệu điểm.

- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *Topological Data Analysis for Neural Network Analysis: A Comprehensive Survey*, arXiv:2312.05840 (2023).

**Nhắc lại định nghĩa:** Nếu $f: X \to Y$ liên tục và $U \subset Y$ mở thì $f^{-1}(U)$ mở trong $X$. Trong một bộ mã hóa (*encoder*), tập mở thường được xấp xỉ bởi các hình cầu trong không gian tiềm ẩn; khi bộ mã hóa vi phạm tính liên tục theo nghĩa này, các cụm dữ liệu có thể bị xé rách.

---

## 🧠 Tài liệu tham khảo

- Munkres, *Topology*, Ch. 2 (tô-pô, cơ sở, tính liên tục).
- Adams & Franzosa, *Introduction to Topology: Pure and Applied*, Ch. 1.
- Các bài báo arXiv trích dẫn ở trên.

## 🔗 Ứng dụng

Phân nhóm dữ liệu tế bào đơn (*single-cell*) thường kết hợp giảm chiều UMAP với phân cụm dựa trên mật độ. Các khái niệm của Chương 01 giúp người học theo dõi trực tiếp các công trình nghiên cứu giai đoạn 2025–2026 trong lĩnh vực này.

## Video tham khảo

- **xem trước** [UMAP Dimension Reduction, Main Ideas!!!](https://www.youtube.com/watch?v=eN0wFzBA4Sc) — StatQuest with Josh Starmer, tiếng Anh. UMAP được giới thiệu như một phép giảm chiều. Bài này sẽ nói vì sao đó chưa phải là đồng phôi.
- [Henry Adams (5/3/22): Topology in Machine Learning](https://www.youtube.com/watch?v=kwYiQNa_pTc) — Applied Algebraic Topology Network, tiếng Anh. Tô-pô dùng như đặc trưng của dữ liệu và của phân cụm, sát các mục TDA của bài.
- [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, tiếng Anh. Thành phần liên thông và lỗ xuất hiện theo tỉ lệ, thứ mà thuật toán phân cụm đang cố thấy.

## 🧩 Bài tập

1. Xây dựng hai tô-pô trên cùng một tập gồm $5$ điểm: một tô-pô tách tập thành $2$ cụm mở rời nhau, tô-pô kia giữ cả $5$ điểm liên thông thành $1$ cụm. Trong hai tô-pô đó, tô-pô nào mịn hơn?
2. Giải thích vì sao việc tăng tham số $k$ trong đồ thị $k$-láng giềng gần nhất ($k$-NN) có tác dụng tương tự việc chuyển sang một cấu trúc thô hơn.
3. Xét một hàm mật độ $\rho$ trên $\mathbb{R}^2$ có hai đỉnh cực đại khác độ cao. Phác họa sự thay đổi của các tập siêu mức $\{\rho > \lambda\}$ khi $\lambda$ giảm dần.
