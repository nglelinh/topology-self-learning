---
layout: post
title: "Lecture 03.90: Tiến bộ gần đây (2022–2026) — Phân ly, nhúng, và ổn định hình dạng"
lang: vi
lang-ref: lecture-03-90
chapter: 3
lecture: 90
order: 90
lesson_type: optional
categories: [chapter03]
tags: [optional, recent-advances, hausdorff, embedding, stability]
description: "Bài tùy chọn: tiên đề phân ly và metrization gặp ổn định TDA và phê bình UMAP. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Các tiên đề $T_0$–$T_4$, Urysohn, và metrization giữ nguyên. Ta chỉ hỏi: dữ liệu và các bất biến TDA “tách điểm” theo nghĩa nào?

---

## 📖 Tổng quan

Hausdorff nghĩa là hai điểm khác nhau có hai lân cận rời nhau — giới hạn, nếu tồn tại, là duy nhất. Trong học máy ta thường *giả* điều này khi vẽ UMAP: hai điểm khác nhau phải đứng ở hai chỗ. Các tiến bộ 2022–2026 cho thấy giả định đó vừa cần thiết (ổn định barcode) vừa dễ vỡ (UMAP không phải nhúng tô-pô).

![Khoảng cách Hausdorff](https://upload.wikimedia.org/wikipedia/commons/2/21/Hausdorff_distance_sample.svg)
*Khoảng cách Hausdorff giữa hai tập: ngôn ngữ $T_2$ đã được số hóa. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_distance_sample.svg)*

---

## 🎯 Trực giác

Urysohn’s lemma nói: nếu không gian đủ “hiền” (normal), hai tập đóng rời nhau bị một hàm liên tục $[0,1]$ tách. Mapper và UMAP là những nỗ lực *vẽ* hàm đó cho dữ liệu. Khi không gian không Hausdorff — thí dụ không gian Alexandroff hữu hạn của Kayacan (Chapter 00.90) — “tách điểm” thất bại và các thuật toán nhúng bắt đầu bịa ra khoảng cách.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Không gian diagram là Hausdorff — và đó là lý do ổn định có nghĩa

Metric bottleneck $d_B$ trên persistence diagrams thỏa
$$
d_B(\mathrm{Dgm}(X),\mathrm{Dgm}(Y))\le d_{GH}(X,Y)
$$
(trong các giả thiết compact). Không gian $(\mathrm{Dgm},d_B)$ là metric, nên $T_2$: hai barcode khác nhau bị tách bởi quả cầu. Fu et al. (2025) mở rộng ổn định Gromov–Hausdorff sang tập có nhãn — một định lý metrization *ứng dụng*: ta được phép coi barcode như điểm trong một không gian Hausdorff.

- Yaoying Fu et al., *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 2. Phê bình UMAP: không phải mọi “nhúng” đều là embedding

Yang (2026) chứng minh UMAP, ở dạng thông dụng, là **spectral clustering trên đồ thị láng giềng mờ** — không phải một embedding tô-pô của đa tạp ẩn. Li và Zhang (2026) thêm prior hình học/tô-pô (JORC-UMAP) để vá đúng chỗ UMAP phá $T_2$ địa phương. Bài học Chapter 03: “vẽ được trên $\mathbb{R}^2$” $\neq$ “tồn tại embedding”.

- Yang Yang, *UMAP Is Spectral Clustering on the Fuzzy Nearest-Neighbor Graph*, arXiv:2602.11662 (2026).
- Xiaobin Li, Run Zhang, *Understanding and Improving UMAP with Geometric and Topological Priors: The JORC-UMAP Algorithm*, arXiv:2601.16552 (2026).

### 3. $T_0$ hữu hạn như mô hình tính toán

Kayacan (2025) làm việc trên không gian hữu hạn $T_0$ không Hausdorff. Điều này không mâu thuẫn Chapter 03: nó giải thích vì sao pipeline TDA rời rạc *phải* đi qua một không gian không-$T_2$ trước khi barcode — hồ sơ Hausdorff — được xuất ra.

- Selçuk Kayacan, *Persistent Homology via Finite Topological Spaces*, arXiv:2512.23348 (2025).

### 4. Vectorization ổn định: Lipschitz thay cho chỉ liên tục

Một hàm liên tục trên không gian diagram chưa đủ cho học máy; ta cần Lipschitz để nhiễu nhỏ không nổ feature. Loiseaux et al. (2023) và Bravetti et al. (2024) xây các vectorization (kể cả multiparameter) với chứng minh ổn định — phiên bản định lượng của “hàm liên tục tách tập” trong Urysohn.

- David Loiseaux et al., *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Alessandro Bravetti, Martín Mijangos, Pablo Padilla, *New divergence measures between persistence diagrams and stability of vectorizations*, arXiv:2410.03910 (2024).

---

## 🧠 Tài liệu

- Munkres, *Topology*, Ch. 4–5 (separation, Urysohn, metrization).
- Willard, *General Topology*, Ch. 13–23.
- Các arXiv trên.

## 🔗 Ứng dụng

Khi một dashboard UMAP “tách” hai nhóm bệnh nhân, Chapter 03 buộc ta hỏi: đó là $T_2$ thật của dữ liệu, hay artifact của spectral clustering?

## 🧩 Bài tập

1. Chỉ ra một không gian $T_0$ không $T_1$ có 3 điểm. Nó có thể là output trung gian của một filtration không?
2. Vì sao bottleneck metric biến không gian diagram thành Hausdorff, trong khi union-find thô thì không?
3. Đọc abstract của Yang (2026) và viết một câu: UMAP bảo toàn thứ gì, không bảo toàn thứ gì.
