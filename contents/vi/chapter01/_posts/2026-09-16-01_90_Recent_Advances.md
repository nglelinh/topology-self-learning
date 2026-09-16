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

**Bài tùy chọn.** Các định nghĩa open set, basis, closure, liên tục của Chapter 01 giữ nguyên. Ở đây ta chỉ xem chúng xuất hiện lại như thế nào khi $X$ là một đám mây điểm.

---

## 📖 Tổng quan

Một topology trên $X$ là cách nói “điểm nào đứng cạnh điểm nào” mà không cần metric. Phân cụm là cùng một câu hỏi, viết bằng thuật toán: thành phần nào của dữ liệu là một “mảnh mở” tự nhiên? Từ 2022 đến 2026, các phương pháp clustering tô-pô không còn là chú thích ở cuối sách TDA — chúng trở thành thuật toán đa tỉ lệ, đa tham số, có định lý ổn định.

![Phân cụm](https://upload.wikimedia.org/wikipedia/commons/c/c8/Cluster-2.svg)
*Hai cụm trong mặt phẳng: phiên bản rời rạc của “không liên thông”. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cluster-2.svg)*

---

## 🎯 Trực giác

Hãy nhớ định nghĩa tập mở: nếu $x\in U$ thì cả một “vùng quanh $x$” nằm trong $U$. Trong dữ liệu, “vùng quanh $x$” thường là $k$ láng giềng hoặc một quả cầu bán kính $\varepsilon$. Khi $\varepsilon$ nhỏ, mỗi điểm là một cụm; khi $\varepsilon$ lớn, mọi thứ dính thành một. **Persistent clustering** theo dõi các cụm qua $\varepsilon$ — đúng tinh thần basis và so sánh topology (thô hơn / mịn hơn) của bài 01.01.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Phân cụm mật độ đa tỉ lệ bền vững

Bot, McInnes và Aerts (2025) đề xuất *Persistent Multiscale Density-based Clustering*: thay vì chọn một ngưỡng mật độ, họ theo dõi thành phần liên thông của siêu mức mật độ như một filtration. Đây là Chapter 01 viết thành thuật toán: họ open set $\{x:\rho(x)>\lambda\}$ thay đổi theo $\lambda$, và topology thay đổi có kiểm soát.

- Daniël Bot, Leland McInnes, Jan Aerts, *Persistent Multiscale Density-based Clustering*, arXiv:2512.16558 (2025).

### 2. ToMATo tái xuất: clustering tô-pô đa tham số

Dòng ToMATo (Topological Mode Analysis Tool) kết hợp chế độ mật độ với $0$-dimensional persistence. Martineau, Pouzat và Geffray (2025) đưa ToMATo vào dữ liệu chiều cao (spike sorting). Andrianirina và Carrière (2026) mở rộng thành ToMAToMP — clustering đa tham số ổn định. “Mode” ở đây là đỉnh của hàm mật độ; “thung lũng” là nơi các cụm gặp nhau — một bức tranh closure/boundary rất point-set.

- Louise Martineau, Christophe Pouzat, Ségolen Geffray, *ToMATo: an efficient and robust clustering algorithm for high dimensional datasets*, arXiv:2509.17499 (2025).
- Ludo Andrianirina, Mathieu Carrière, *ToMAToMP: Robust and Multi-Parameter Topological Clustering*, arXiv:2605.14824 (2026).

### 3. Ánh xạ liên tục và homeomorphism trong giảm chiều

UMAP tự nhận là bảo toàn topology địa phương. Dalmia và Sia (2021, ảnh hưởng kéo dài 2022–2026) chỉ ra rằng **tính liên thông** của đồ thị láng giềng quyết định chất lượng cụm sau UMAP: mất cạnh là mất thành phần. Đó là bài 01.03 ở dạng thực nghiệm: một ánh xạ “gần liên tục” có thể phá homeomorphism kiểu và gộp/tách cụm.

- Ayush Dalmia, Suzanna Sia, *Clustering with UMAP: Why and How Connectivity Matters*, arXiv:2108.05525 (2021).

### 4. Tô-pô của mạng nơ-ron như không gian dữ liệu

Ballester, Casacuberta và Escalera (2023/24) khảo sát TDA trên mạng nơ-ron: tập trọng số, tập kích hoạt, và tập dữ liệu đều được xem là không gian tô-pô. Continuous maps giữa chúng (forward pass) là đúng định nghĩa Chapter 01, chỉ khác là $X$ có hàng triệu điểm.

- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *Topological Data Analysis for Neural Network Analysis: A Comprehensive Survey*, arXiv:2312.05840 (2023).

**Nhắc formal:** nếu $f:X\to Y$ liên tục và $U\subset Y$ mở thì $f^{-1}(U)$ mở. Trong một encoder, “mở” thường được xấp xỉ bằng quả cầu trong không gian tiềm ẩn. Khi encoder không liên tục theo nghĩa này, các cụm bị xé.

---

## 🧠 Tài liệu

- Munkres, *Topology*, Ch. 2 (topology, basis, continuity).
- Adams & Franzosa, *Introduction to Topology: Pure and Applied*, Ch. 1.
- Các arXiv trên.

## 🔗 Ứng dụng

Phân nhóm tế bào đơn (single-cell) dùng UMAP + clustering mật độ. Bài tùy chọn này cho phép đọc các paper 2025–2026 mà không rời Chapter 01.

## 🧩 Bài tập

1. Vẽ hai topology trên cùng 5 điểm: một tách thành 2 cụm, một dính 1 cụm. Topology nào mịn hơn?
2. Giải thích vì sao tăng $k$ trong $k$-NN giống như chuyển sang topology thô hơn.
3. Lấy một hàm mật độ trên $\mathbb{R}^2$ với hai đỉnh. Phác họa filtration $\{\rho>\lambda\}$ khi $\lambda$ giảm.
