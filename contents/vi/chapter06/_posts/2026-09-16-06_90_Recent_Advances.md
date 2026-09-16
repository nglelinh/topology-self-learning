---
layout: post
title: "Lecture 06.90: Tiến bộ gần đây (2022–2026) — Homotopy của mạng nơ-ron và mode connectivity"
lang: vi
lang-ref: lecture-06-90
chapter: 6
lecture: 90
order: 90
lesson_type: optional
categories: [chapter06]
tags: [optional, recent-advances, homotopy, mode-connectivity, neural-networks]
description: "Bài tùy chọn: π₁ và homotopy gặp topology của mạng nơ-ron và mode connectivity. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Homotopy, $\pi_1$, và không gian phủ giữ nguyên. Ta chỉ đổi không gian: $X$ bây giờ là cảnh quan mất mát, tập kích hoạt, hoặc không gian dữ liệu sau từng lớp.

---

## 📖 Tổng quan

Một homotopy là một biến dạng liên tục của ánh xạ. Trong học sâu, hai bộ trọng số $w_0,w_1$ là “cùng mode” nếu có một đường $\gamma$ sao cho $L(\gamma(t))$ không vượt rào — tức là một path-homotopy trong siêu mức. Khảo sát Ballester–Casacuberta–Escalera (2023) và các bài mode connectivity 2025–2026 biến Chapter 06 thành công cụ đọc paper thực nghiệm.

![Mạng nơ-ron](https://upload.wikimedia.org/wikipedia/commons/4/46/Colored_neural_network.svg)
*Một mạng feedforward là một ánh xạ $f:X\to Y$ ghép từ các lớp — đối tượng của homotopy. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Colored_neural_network.svg)*

![Phủ vòng tròn](https://upload.wikimedia.org/wikipedia/commons/5/54/Covering_map.png)
*Ánh xạ phủ $\mathbb{R}\to S^1$: mô hình cho “nhiều preimage, một vòng”. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Covering_map.png)*

---

## 🎯 Trực giác

$\pi_1(S^1)=\mathbb{Z}$ đếm số vòng. Naitzat, Zhitnikov và Lim (2020) — bài vẫn được trích dẫn dày đặc sau 2022 — chỉ ra rằng một mạng sâu *đơn giản hóa topology của dữ liệu*: Betti numbers của tập theo lớp giảm dần, như thể mỗi lớp là một homotopy về phía không gian co được. Mode connectivity là câu hỏi đối ngẫu: không gian *tham số* có co được trên siêu mức thấp không?

---

## 📐 Bốn tiến bộ cụ thể

### 1. TDA cho phân tích mạng nơ-ron (khảo sát)

Ballester, Casacuberta và Escalera (2023/24) tổng hợp cách $\pi_1$, Mapper, và persistent homology được dùng trên (i) dữ liệu, (ii) kích hoạt, (iii) không gian trọng số. Đây là bản đồ Chapter 06 → ML.

- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *Topological Data Analysis for Neural Network Analysis: A Comprehensive Survey*, arXiv:2312.05840 (2023).
- Gregory Naitzat, Andrey Zhitnikov, Lek-Heng Lim, *Topology of deep neural networks*, *JMLR* (2020), arXiv:2004.06093 — nền vẫn định hình các bài 2022–2026.

### 2. Mode connectivity ngoài bộ phân loại

Yao, Zhang và Tian (2026) tìm bằng chứng mode connectivity ở mô hình sinh và contrastive — homotopy trong $S_c=\{L\le c\}$ không còn là chuyện riêng của softmax. Cheng–Amiri (2026) dùng cùng ngôn ngữ path để hiểu unlearning: xóa một điểm dữ liệu có cắt đường nối hai minimizer không?

- Chengzheyi Yao, Yongzhao Zhang, Yongding Tian, *Mode Connectivity Beyond Classifiers*, arXiv:2608.30366 (2026).
- Jiali Cheng, Hadi Amiri, *Understanding Machine Unlearning Through the Lens of Mode Connectivity*, arXiv:2607.23970 (2026).

### 3. Linear mode connectivity và trộn mô hình

Nếu đoạn thẳng giữa hai minimizer nằm trong $S_c$, ta có một homotopy *tuyến tính* của mạng. Li–Shen (2026) kéo tính chất này tới transformer tỷ tham số; Tran et al. (2025–26) phân tích MoE và attention. Về formal, đây là câu hỏi $\pi_0(S_c)$: siêu mức có một hay nhiều thành phần?

$$
[\gamma]\in\pi_0\bigl(\{w:L(w)\le c\}\bigr).
$$
(Thành phần đường; $\pi_1$ của $S_c$ vẫn gần như chưa được đo ở quy mô lớn.)

- Tianyi Li, Zhiqiang Shen, *Scaling Linear Mode Connectivity and Merging to Billion Parameter Pretrained Transformers*, arXiv:2606.23607 (2026).
- Viet-Hoang Tran, Van Hoan Trinh, Khanh Vinh Bui, Tan M. Nguyen, *On Linear Mode Connectivity of Mixture-of-Experts Architectures*, arXiv:2509.11348 (2025).

### 4. Homotopy như bất biến của dữ liệu sau lớp

Su et al. (2025) nhấn mạnh TDA *vượt* persistent homology: homotopy và phức tế bào bắt đầu được dùng làm đặc trưng. Trong ngôn ngữ Chapter 06, mỗi lớp $f_\ell$ cảm ứng $(f_\ell)_*$ trên $\pi_1$ — và người ta bắt đầu đo kernel/cokernel đó trên dữ liệu thật.

- Zhe Su et al., *Topological Data Analysis and Topological Deep Learning Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

---

## 🧠 Tài liệu

- Hatcher, *Algebraic Topology*, Ch. 1.
- Munkres, *Topology*, Ch. 9, 13.
- Các arXiv trên.

## 🔗 Ứng dụng

Model soup / weight averaging chạy được chỉ khi đoạn thẳng giữa các checkpoint là một homotopy mất mát thấp. Chapter 06 cho đúng tên gọi.

## 🧩 Bài tập

1. Với $L(x)=(x^2-1)^2$, tính $\pi_0(S_c)$ theo $c$.
2. Giải thích vì sao linear mode connectivity mạnh hơn path-connectedness thường.
3. Phác họa một phủ 2-tờ của $S^1$ và nói một câu về “hai minimizer phủ một minimizer trên không gian thương”.
