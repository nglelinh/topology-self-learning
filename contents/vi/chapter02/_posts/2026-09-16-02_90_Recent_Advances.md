---
layout: post
title: "Lecture 02.90: Tiến bộ gần đây (2022–2026) — Liên thông, compact, và thành phần của dữ liệu"
lang: vi
lang-ref: lecture-02-90
chapter: 2
lecture: 90
order: 90
lesson_type: optional
categories: [chapter02]
tags: [optional, recent-advances, connectedness, compactness, mode-connectivity]
description: "Bài tùy chọn: connectedness/compactness gặp clustering, persistence 0-chiều, và mode connectivity. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Định nghĩa liên thông, path-connected, compact của Chapter 02 không đổi. Ta chỉ theo chúng vào dữ liệu và vào không gian tham số của mạng nơ-ron.

---

## 📖 Tổng quan

Hai tính chất “quan trọng nhất” của point-set — **không tách được** và **mọi phủ mở đều có phủ con hữu hạn** — là đúng ngôn ngữ của hai câu hỏi hiện đại: (1) dữ liệu có bao nhiêu mảnh? (2) một họ mô hình có thể đi từ cực tiểu này sang cực tiểu kia mà không vượt rào mất mát?

![Cà phê và torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)
*Path-connectedness trong không gian hình dạng: một đường liên tục các homeomorphism. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif)*

---

## 🎯 Trực giác

Một không gian liên thông không cho phép viết $X=U\cup V$ với $U,V$ mở, khác rỗng, rời nhau. Trong clustering, đó là định nghĩa của “một cụm” ở một tỉ lệ cố định. Persistence $H_0$ làm mịn định nghĩa này: hai điểm cùng thành phần ở bán kính $\varepsilon$ khi có một chuỗi điểm trung gian, mỗi bước dài $\le\varepsilon$. Compactness xuất hiện khi ta hỏi barcode có ổn định không: không gian các persistence diagram (với metric bottleneck) là **complete và locally compact trên các diagram hữu hạn** — “hữu hạn-giống” đúng nghĩa Heine–Borel.

---

## 📐 Bốn tiến bộ cụ thể

### 1. $H_0$ bền vững như lý thuyết thành phần

Bot–McInnes–Aerts (2025) và ToMATo 2025–2026 (xem Chapter 01.90) biến thành phần liên thông thành một **đối tượng đa tỉ lệ**. Về mặt hình thức, nếu
$$
X_{\varepsilon}=\bigsqcup_{\alpha} C_{\alpha}(\varepsilon)
$$
là phân hoạch thành các path-component của phức $\varepsilon$, thì một “cái chết” trong barcode $H_0$ là lúc hai $C_{\alpha}$ dính nhau. Đây không phải định lý mới của Munkres — đó là connectedness được lọc.

- Daniël Bot, Leland McInnes, Jan Aerts, *Persistent Multiscale Density-based Clustering*, arXiv:2512.16558 (2025).

### 2. Mode connectivity: path-connectedness của cảnh quan mất mát

Một mạng với tham số $w\in\mathbb{R}^N$ và hàm mất mát $L$ cho siêu mức
$$
S_c=\{w:L(w)\le c\}.
$$
**Mode connectivity** hỏi $S_c$ có path-connected không khi $c$ đủ lớn. Các công trình 2025–2026 đẩy câu hỏi này ra ngoài bộ phân loại cổ điển: Yao, Zhang và Tian (2026) tìm thấy đường nối mode ở mô hình sinh và contrastive; Cheng và Amiri (2026) đọc *machine unlearning* qua cùng thấu kính path-connectedness.

- Chengzheyi Yao, Yongzhao Zhang, Yongding Tian, *Mode Connectivity Beyond Classifiers: Evidence from Generative and Contrastive Models*, arXiv:2608.30366 (2026).
- Jiali Cheng, Hadi Amiri, *Understanding Machine Unlearning Through the Lens of Mode Connectivity*, arXiv:2607.23970 (2026).

### 3. Linear mode connectivity ở quy mô lớn

“Linear” mode connectivity nghĩa là đoạn thẳng $(1-t)w_0+tw_1$ nằm trọn trong $S_c$. Đó là path-connectedness với path rất nghèo — và vì thế mạnh hơn. Li và Shen (2026) kéo tính chất này tới transformer hàng tỷ tham số; Tran et al. (2026) phân tích tương đương hàm của attention như một lý do các mode nối được.

$$
\gamma(t)=(1-t)w_0+tw_1,\qquad t\in[0,1],\qquad L(\gamma(t))\le c.
$$

- Tianyi Li, Zhiqiang Shen, *Scaling Linear Mode Connectivity and Merging to Billion Parameter Pretrained Transformers*, arXiv:2606.23607 (2026).
- Viet-Hoang Tran et al., *Functional Equivalence in Attention: A Comprehensive Study with Applications to Linear Mode Connectivity*, arXiv:2606.17830 (2026).

### 4. Compactness như kiểm soát phủ trong TDA

Ổn định persistence (Cohen–Steiner–Edelsbrunner–Harer, vẫn là định lý nền) nói rằng map từ không gian compact metric tới không gian diagram là Lipschitz theo bottleneck. Các bài 2024–2025 về vectorization (Loiseaux et al. 2023; Bravetti–Mijangos–Padilla 2024) mở rộng: muốn đưa barcode vào mạng nơ-ron, cần một embedding Lipschitz — tức là không phá vỡ “hữu hạn-giống” của compact.

- David Loiseaux, Luis Scoccola, Mathieu Carrière, Magnus Bakke Botnan, *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Alessandro Bravetti, Martín Mijangos, Pablo Padilla, *New divergence measures between persistence diagrams and stability of vectorizations*, arXiv:2410.03910 (2024).

---

## 🧠 Tài liệu

- Munkres, *Topology*, Ch. 3 (connectedness, compactness).
- Morris, *Topology without Tears*, Ch. 12–13.
- Các arXiv trên.

## 🔗 Ứng dụng

Khi hai checkpoint của cùng một mô hình ngôn ngữ lớn nối được bằng đoạn thẳng mất mát thấp, người ta *trộn* trọng số thay vì ensemble. Đó là path-connectedness đang chạy trong production.

## 🧩 Bài tập

1. Vẽ $S_c$ cho $L(x,y)=(x^2-1)^2+y^2$. Với $c$ nào thì $S_c$ liên thông?
2. Phân biệt connected và path-connected bằng một đám mây điểm trên topologist’s sine curve (lấy mẫu).
3. Vì sao một barcode với vô hạn vạch dài không “compact” theo trực giác Heine–Borel?
