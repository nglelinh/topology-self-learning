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

**Bài tùy chọn.** Quotient topology, phân loại mặt, CW, và group actions giữ nguyên. Ta xem chúng được *vẽ lại* thành Mapper và bị UMAP bắt chước — rồi bị phê bình.

---

## 📖 Tổng quan

Mapper, ra đời 2007, là thuật toán quotient: chọn một hàm lọc $f:X\to\mathbb{R}^k$, phủ miền giá trị bằng các tập mở có chồng lấn, lấy thành phần liên thông của các nghịch ảnh, rồi dán chúng thành một đồ thị. Đó là đúng tinh thần Chapter 05 — “dán theo sợi” — viết cho dữ liệu hữu hạn. Giai đoạn 2022–2026 chứng kiến khảo sát toàn diện, khung ổn định, và một làn phê bình UMAP: giảm chiều phổ biến *không* phải là quotient tô-pô.

![Torus](https://upload.wikimedia.org/wikipedia/commons/1/17/Torus.png)
*Torus là thương của hình vuông sau khi dán cạnh — nguyên mẫu cho Mapper. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus.png)*

---

## 🎯 Trực giác

Hãy nhớ $S^1=[0,1]/\{0\sim 1\}$. Mapper làm điều tương tự với một đám mây điểm: nếu hai “cụm địa phương” sống trong hai tập lọc chồng nhau, ta vẽ một cạnh — tức là *dán*. UMAP cũng vẽ một đồ thị láng giềng rồi nhúng nó xuống $\mathbb{R}^2$, nhưng bước nhúng không còn là quotient map. Phân biệt hai thao tác này là bài học Chapter 05 cho khoa học dữ liệu.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Khảo sát Mapper 2007–2025

Madukpe, Ugoala và Zulkepli (2025) viết một tổng quan có hệ thống về Mapper và ứng dụng xuyên lĩnh vực. Đây là bản đồ đọc cho bất kỳ ai đã xong bài 05.00: mỗi biến thể Mapper là một cách chọn phủ và một cách chọn thành phần — tức là một quotient khác.

- Vine Nwabuisi Madukpe, Bright Chukwuma Ugoala, Nur Fariha Syaqina Zulkepli, *A Comprehensive Review of the Mapper Algorithm … (2007–2025)*, arXiv:2504.09042 (2025).

### 2. Ổn định và đánh giá Mapper

Sen, Singh và Tiwari (2026) đề xuất khung đánh giá ba trục cho thuật toán Mapper; cùng nhóm đưa ra GK-Mapper với ổn định kiểu Gustafson–Kessel. Ahsan, Das và Mukhopadhyay (2026) chọn phủ theo dữ liệu (MAPLE) để giảm phụ thuộc tham số — đúng nỗi đau của quotient: phủ khác thì thương khác.

- Annesha Sen, Shivam Singh, S. P. Tiwari, *A Three Axis Evaluation Framework for Mapper Algorithms*, arXiv:2606.21688 (2026).
- Md Moinul Ahsan, Priyam Das, Nitai D. Mukhopadhyay, *MAPLE: Mapper Based Localized Prediction with Data Driven Cover Selection*, arXiv:2607.06797 (2026).

### 3. UMAP không phải nhúng đa tạp — và không phải Mapper

Yang (2026) chứng minh UMAP thông dụng là spectral clustering trên đồ thị láng giềng mờ. Li–Zhang (2026) vá bằng prior tô-pô. Kết luận sư phạm: UMAP *trông* như một bản đồ của đa tạp (Chapter 05.01–05.03) nhưng không thỏa universal property của quotient, cũng không cho nerve của một phủ mở theo nghĩa Mapper.

- Yang Yang, *UMAP Is Spectral Clustering on the Fuzzy Nearest-Neighbor Graph*, arXiv:2602.11662 (2026).
- Xiaobin Li, Run Zhang, *Understanding and Improving UMAP with Geometric and Topological Priors: The JORC-UMAP Algorithm*, arXiv:2601.16552 (2026).

### 4. Mapper gặp bài toán sống còn và học có cấu trúc

Kibisi, Abawonse và Woukeng (2026) dùng Mapper cho phân tích sống còn trong ung thư vú — đồ thị thương trở thành đặc trưng lâm sàng. Babus và Nasrin (2026) học có cấu trúc *trên* biểu diễn Mapper, tức là lấy quotient làm không gian nền cho model.

Nếu $f:X\to\mathbb{R}$ là filter và $\mathcal{U}=\{U_i\}$ là phủ của $f(X)$, nerve
$$
N(\{C:C\text{ thành phần của }f^{-1}(U_i)\})
$$
là CW-phức (thường là đồ thị) — ngôn ngữ bài 05.02.

- Emmanuel Kibisi, Olakunle Abawonse, Donald Woukeng, *Topology-Informed Survival Analysis of Breast Cancer Patients Using the Mapper Algorithm*, arXiv:2607.15022 (2026).
- George Babus, Farzana Nasrin, *Structured Learning on Mapper Representations*, arXiv:2608.22044 (2026).

---

## 🧠 Tài liệu

- Munkres, *Topology*, Ch. 2 §22 (quotient), Ch. 12 (surfaces, trong một số lần xuất bản).
- Hatcher, *Algebraic Topology*, Ch. 0 (CW, quotient pictures).
- Các arXiv trên.

## 🔗 Ứng dụng

Trong single-cell, Mapper đôi khi lộ một “nhánh biệt hóa” mà UMAP làm phẳng. Chapter 05 giải thích: một thương giữ sợi của filter; một spectral embedding thì không cam kết điều đó.

## 🧩 Bài tập

1. Với $X=S^1$ và $f=$ chiều cao, phác họa Mapper graph (phủ 3 khoảng chồng).
2. Chỉ ra một phủ làm Mapper của hình số 8 trở thành một cạnh duy nhất (mất lỗ).
3. Viết một câu phân biệt quotient map và UMAP embedding.
