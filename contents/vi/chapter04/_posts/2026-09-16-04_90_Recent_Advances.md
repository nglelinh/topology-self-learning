---
layout: post
title: "Lecture 04.90: Tiến bộ gần đây (2022–2026) — Metric giữa các hình dạng"
lang: vi
lang-ref: lecture-04-90
chapter: 4
lecture: 90
order: 90
lesson_type: optional
categories: [chapter04]
tags: [optional, recent-advances, metric, gromov-hausdorff, bottleneck, interleaving]
description: "Bài tùy chọn: metric spaces gặp GH, bottleneck, interleaving, và hình học tiềm ẩn. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Ba tiên đề metric, completeness, và tương đương metric của Chapter 04 giữ nguyên. Ta xem chúng đo *khoảng cách giữa các không gian* chứ không chỉ giữa các điểm.

---

## 📖 Tổng quan

Một metric trên $X$ đo cặp điểm. Khoa học dữ liệu hiện đại cần thêm một tầng: đo cặp **không gian**. Gromov–Hausdorff, bottleneck, Wasserstein trên diagram, và interleaving trên persistence module là những metric “không gian-cấp” — và chúng bùng nổ trong các bài 2023–2026.

![Khoảng cách Hausdorff](https://upload.wikimedia.org/wikipedia/commons/2/21/Hausdorff_distance_sample.svg)
*Hausdorff giữa hai tập trong cùng một không gian — bước đầu trước Gromov–Hausdorff. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_distance_sample.svg)*

---

## 🎯 Trực giác

Hausdorff $d_H(A,B)$ hỏi: mỗi điểm của $A$ có điểm của $B$ gần tới mức nào (và ngược lại)? Gromov–Hausdorff bỏ yêu cầu $A,B$ nằm chung một không gian: ta được phép *chọn cách đặt* chúng cạnh nhau trước khi đo $d_H$. Đó là “tương đương metric” của bài 04.02, nâng lên một tầng.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Ổn định GH cho tập có nhãn và landscape tổng quát

Fu et al. (2025) chứng minh persistent homology của tập có nhãn ổn định theo Gromov–Hausdorff, và đưa ra landscape tổng quát. Đây là completeness + continuity ở cấp không gian: một Cauchy sequence của đám mây điểm cho Cauchy sequence của barcode.

- Yaoying Fu, Evgeniya Lagoda, Shiying Li, Tom Needham, Lander Ver Hoef, *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 2. Metric GH cho dữ liệu có màu / phân tử

Wee, Gong, Tuschmann và Xia (2024) dùng một metric kiểu Gromov–Hausdorff trên đối cohomology để đo độ giống phân tử. Draganov, Rosenmeier và Zava (2025) định nghĩa khoảng cách GH giữa các *cặp metric có màu* và chứng minh ổn định cho “six-pack” invariants. Metric không còn là Euclidean trên $\mathbb{R}^d$ — đúng tinh thần “nhiều metric, một topology” của Chapter 04.

- JunJie Wee, Xue Gong, Wilderich Tuschmann, Kelin Xia, *A cohomology-based Gromov–Hausdorff metric approach for quantifying molecular similarity*, arXiv:2411.13887 (2024).
- Ondřej Draganov, Sophie Rosenmeier, Nicolò Zava, *Gromov–Hausdorff distance between chromatic metric pairs and stability of the six-pack*, arXiv:2507.17994 (2025).

### 3. Interleaving: metric trên module, không chỉ trên diagram

Interleaving distance so sánh hai persistence module bằng cách “trượt” chúng trên trục tỉ lệ. Các bài 2026 vừa đẩy thuật toán (Aoki; Farahbakhsh Touli–Hotz–Masood; Althaf–Chattopadhyay–Saeki) vừa xây vùng tin cậy cho Reeb graph (Pegoraro–Conforti–Carrière). Về formal:
$$
d_I(M,N)=\inf\{\varepsilon\ge 0: M,N\text{ là }\varepsilon\text{-interleaved}\}.
$$
Đây là một metric (mở rộng) trên một phạm trù — completeness và tính toán là câu hỏi đang mở, đúng phong cách Chapter 04.

- Matteo Pegoraro, Alberto Conforti, Mathieu Carrière, *Building confidence regions for Reeb graphs using the interleaving distance*, arXiv:2607.08458 (2026).
- Elena Farahbakhsh Touli, Ingrid Hotz, Talha Bin Masood, *Towards Computing Average Merge Tree Based on the Interleaving Distance*, arXiv:2603.00783 (2026).

### 4. GH trong không gian tiềm ẩn của mạng

Borde, Arroyo, Morales, Posner và Dong (2023) dùng GH để *suy* tích các đa tạp mô hình cho latent geometry — Neural Latent Geometry Search. Metric spaces không chỉ là input: chúng là giả thuyết về không gian ẩn mà mạng đang học.

- Haitz Sáez de Ocáriz Borde et al., *Neural Latent Geometry Search: Product Manifold Inference via Gromov–Hausdorff-Informed Bayesian Optimization*, arXiv:2309.04810 (2023).

---

## 🧠 Tài liệu

- Munkres, *Topology*, Ch. 7 (complete metric spaces).
- Burago–Burago–Ivanov, *A Course in Metric Geometry* (GH nền).
- Các arXiv trên.

## 🔗 Ứng dụng

So sánh hai protein không nằm trong cùng $\mathbb{R}^3$ (khác căn chỉnh) đòi hỏi GH hoặc một metric bất biến căn chỉnh — đúng lý do Chapter 04 tách “metric” khỏi “tọa độ”.

## 🧩 Bài tập

1. Tính $d_H$ giữa $\{0,1\}$ và $\{0,1,2\}$ trong $\mathbb{R}$.
2. Giải thích bằng lời sự khác giữa $d_H$ và $d_{GH}$ cho hai tam giác đều cạnh $1$ ở hai mặt phẳng khác nhau.
3. Vì sao $d_I$ cần $\inf$ chứ không phải $\min$? Liên hệ completeness.
