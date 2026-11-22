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

**Bài tùy chọn.** Ba tiên đề metric, tính đầy đủ và sự tương đương metric của Chapter 04 vẫn giữ nguyên; ở đây ta xem cách chúng được mở rộng để đo *khoảng cách giữa các không gian* chứ không chỉ giữa các điểm.

---

## 📖 Tổng quan

Một metric trên $X$ đo khoảng cách giữa từng cặp điểm. Trong khoa học dữ liệu hiện đại, ta thường cần thêm một tầng trừu tượng: đo khoảng cách giữa hai **không gian**. Khoảng cách Gromov–Hausdorff, khoảng cách bottleneck, khoảng cách Wasserstein trên biểu đồ bền vững (persistence diagram) và khoảng cách xen kẽ (interleaving distance) trên module bền vững là những metric ở cấp độ không gian, được nghiên cứu rộng rãi trong các công trình giai đoạn 2023–2026.

![Khoảng cách Hausdorff](https://upload.wikimedia.org/wikipedia/commons/2/21/Hausdorff_distance_sample.svg)
*Khoảng cách Hausdorff giữa hai tập trong cùng một không gian — bước đệm trước khi định nghĩa Gromov–Hausdorff. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_distance_sample.svg)*

---

## 🎯 Trực giác

Khoảng cách Hausdorff $d_H(A,B)$ đo xem mỗi điểm của $A$ gần tập $B$ đến mức nào và ngược lại. Khoảng cách Gromov–Hausdorff ($d_{GH}$) bỏ điều kiện $A$ và $B$ phải nằm chung trong một không gian cố định: ta được phép nhúng đẳng cự $A$ và $B$ vào cùng một không gian metric trung gian sao cho $d_H$ giữa hai ảnh là nhỏ nhất có thể. Đây là sự mở rộng tự nhiên của ý tưởng so sánh cấu trúc metric ở bài 04.02 lên cấp độ không gian.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Tính ổn định Gromov–Hausdorff cho tập dữ liệu có nhãn và landscape tổng quát

Fu và cộng sự (2025) chứng minh tính ổn định theo khoảng cách Gromov–Hausdorff cho đồng điều bền vững (persistent homology) của các tập dữ liệu có nhãn, đồng thời xây dựng khái niệm landscape tổng quát. Về bản chất, đây là tính đầy đủ và tính liên tục ở cấp độ không gian: một dãy Cauchy các đám mây điểm tương ứng với một dãy Cauchy các barcode.

- Yaoying Fu, Evgeniya Lagoda, Shiying Li, Tom Needham, Lander Ver Hoef, *Persistent Homology for Labeled Datasets: Gromov–Hausdorff Stability and Generalized Landscapes*, arXiv:2512.08794 (2025).

### 2. Metric Gromov–Hausdorff cho dữ liệu có màu và phân tử

Wee, Gong, Tuschmann và Xia (2024) sử dụng một metric kiểu Gromov–Hausdorff trên đối đồng điều (cohomology) để định lượng mức độ tương đồng phân tử. Draganov, Rosenmeier và Zava (2025) định nghĩa khoảng cách Gromov–Hausdorff giữa các *cặp metric có màu* và chứng minh tính ổn định cho các bất biến "six-pack". Ở đây metric không còn giới hạn ở khoảng cách Euclid trên $\mathbb{R}^d$, phù hợp với tinh thần "nhiều metric, một tô-pô" của Chapter 04.

- JunJie Wee, Xue Gong, Wilderich Tuschmann, Kelin Xia, *A cohomology-based Gromov–Hausdorff metric approach for quantifying molecular similarity*, arXiv:2411.13887 (2024).
- Ondřej Draganov, Sophie Rosenmeier, Nicolò Zava, *Gromov–Hausdorff distance between chromatic metric pairs and stability of the six-pack*, arXiv:2507.17994 (2025).

### 3. Khoảng cách xen kẽ (Interleaving): metric trên module thay vì chỉ trên biểu đồ

Khoảng cách xen kẽ so sánh hai module bền vững bằng cách dịch chuyển chúng dọc theo trục tỉ lệ. Các công trình năm 2026 vừa cải tiến thuật toán tính toán (Aoki; Farahbakhsh Touli–Hotz–Masood; Althaf–Chattopadhyay–Saeki), vừa xây dựng vùng tin cậy cho đồ thị Reeb (Pegoraro–Conforti–Carrière). Về mặt hình thức:
$$
d_I(M,N)=\inf\{\varepsilon\ge 0: M,N\text{ là }\varepsilon\text{-interleaved}\}.
$$
Đây là một metric mở rộng trên một phạm trù; tính đầy đủ và bài toán tính toán hiệu quả của nó hiện vẫn đang được nghiên cứu.

- Matteo Pegoraro, Alberto Conforti, Mathieu Carrière, *Building confidence regions for Reeb graphs using the interleaving distance*, arXiv:2607.08458 (2026).
- Elena Farahbakhsh Touli, Ingrid Hotz, Talha Bin Masood, *Towards Computing Average Merge Tree Based on the Interleaving Distance*, arXiv:2603.00783 (2026).

### 4. Khoảng cách Gromov–Hausdorff trong không gian tiềm ẩn của mạng nơ-ron

Borde, Arroyo, Morales, Posner và Dong (2023) dùng khoảng cách Gromov–Hausdorff để suy luận cấu trúc tích các đa tạp mô hình cho hình học tiềm ẩn (Neural Latent Geometry Search). Không gian metric ở đây không chỉ là dữ liệu đầu vào mà còn đóng vai trò giả thuyết về không gian ẩn mà mạng đang học.

- Haitz Sáez de Ocáriz Borde et al., *Neural Latent Geometry Search: Product Manifold Inference via Gromov–Hausdorff-Informed Bayesian Optimization*, arXiv:2309.04810 (2023).

---

## 🧠 Tài liệu

- Munkres, *Topology*, Ch. 7 (không gian metric đầy đủ).
- Burago–Burago–Ivanov, *A Course in Metric Geometry* (nền tảng về Gromov–Hausdorff).
- Các bài báo arXiv liệt kê ở trên.

## 🔗 Ứng dụng

Việc so sánh hai cấu trúc protein không nằm trong cùng một hệ quy chiếu của $\mathbb{R}^3$ (khác phép căn chỉnh) đòi hỏi khoảng cách Gromov–Hausdorff hoặc một metric bất biến với phép dời hình — minh họa trực tiếp lý do Chapter 04 tách khái niệm metric khỏi hệ tọa độ cụ thể.

## Video tham khảo

- **xem trước** [An introduction to the Gromov-Hausdorff distance](https://www.youtube.com/watch?v=tvbkSt_QxnE) — Applied Algebraic Topology Network, tiếng Anh. Giới thiệu khoảng cách Gromov–Hausdorff giữa các hình dạng, đúng chủ đề chính của bài.
- [What is the distance between two sets of points? | Hausdorff Distance](https://www.youtube.com/watch?v=zGKfU91-hU0) — CHALK, tiếng Anh. Giải thích khoảng cách Hausdorff giữa hai tập điểm, bước nền tảng của khoảng cách Gromov–Hausdorff.
- [Week 6 Lecture 6C Interleaving Distance](https://www.youtube.com/watch?v=rXrLVH04FnA) — Vidit Nanda, tiếng Anh. Giới thiệu khoảng cách xen kẽ trên module bền vững.

## 🧩 Bài tập

1. Tính $d_H$ giữa $\{0,1\}$ và $\{0,1,2\}$ trong $\mathbb{R}$.
2. Giải thích bằng lời sự khác nhau giữa $d_H$ và $d_{GH}$ cho hai tam giác đều cạnh $1$ nằm trong hai mặt phẳng khác nhau.
3. Vì sao định nghĩa $d_I$ cần dùng $\inf$ thay vì $\min$? Liên hệ với tính đầy đủ.
