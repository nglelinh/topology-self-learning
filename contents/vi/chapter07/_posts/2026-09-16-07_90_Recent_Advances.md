---
layout: post
title: "Lecture 07.90: Tiến bộ gần đây (2022–2026) — Persistent homology, Ripser, giotto-tda"
lang: vi
lang-ref: lecture-07-90
chapter: 7
lecture: 90
order: 90
lesson_type: optional
categories: [chapter07]
tags: [optional, recent-advances, persistent-homology, ripser, giotto-tda]
description: "Bài tùy chọn: homology gặp persistent homology, Ripser, giotto-tda, và vectorization. Không viết lại lý thuyết."
---

**Bài tùy chọn.** Simplicial/singular homology, Mayer–Vietoris, và cohomology giữ nguyên. Ta chỉ thêm *filtration* và phần mềm tính $H_n$ trên dữ liệu.

---

## 📖 Tổng quan

Homology đếm lỗ. Persistent homology theo dõi lỗ **qua một họ không gian lồng nhau**. Đó là cùng $H_n=\ker\partial_n/\operatorname{im}\partial_{n+1}$, lặp lại cho mỗi $X_{\varepsilon}$. Ba trụ cột thực hành 2021–2026 là: thuật toán Ripser (và các hậu duệ cubical / distributed), thư viện giotto-tda, và lớp vectorization ổn định để đưa barcode vào học máy. Các khảo sát 2025 đặt PH vào một bức tranh lớn hơn — TDA không còn đồng nhất với $H_n$.

![Phức simplicial](https://upload.wikimedia.org/wikipedia/commons/5/50/Simplicial_complex_example.svg)
*Phức simplicial: đối tượng tính $H_n$, và cũng là $X_{\varepsilon}$ trong một Vietoris–Rips filtration. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

![Torus lấy mẫu](https://upload.wikimedia.org/wikipedia/commons/4/4c/Point_cloud_torus.gif)
*Một torus rời rạc: $H_1$ bền vững phải sống lâu hơn nhiễu. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Point_cloud_torus.gif)*

---

## 🎯 Trực giác

Ở $\varepsilon$ nhỏ, phức là đống điểm: $H_0$ lớn, $H_1=0$. Ở $\varepsilon$ vừa, các vòng thật xuất hiện. Ở $\varepsilon$ lớn, mọi thứ bị lấp. **Barcode** ghi khoảng $[\varepsilon_{\mathrm{birth}},\varepsilon_{\mathrm{death}})$ của mỗi lớp. Lớp ngắn là nhiễu; lớp dài là lỗ. Đây là Chapter 07 với một tham số thêm.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Ripser và các biến thể tính toán

Bauer (công bố JACOT 2021, vẫn là chuẩn vàng 2022–2026) tính Vietoris–Rips persistence bằng biểu diễn ẩn của coboundary, tránh xây phức tường minh. Guillou–Vidal–Tierny (2022) và Le Guillou–Fortin–Tierny (2025) đưa *Discrete Morse Sandwich* — Morse rời rạc để rút gọn phức trước khi tính diagram — lên dữ liệu vô cùng lớn, phân tán.

$$
\mathrm{VR}_{\varepsilon}(X)=\{\sigma\subseteq X:\mathrm{diam}(\sigma)\le\varepsilon\}.
$$

- Ulrich Bauer, *Ripser: efficient computation of Vietoris–Rips persistence barcodes*, *Journal of Applied and Computational Topology* (2021), arXiv:1908.02518.
- Pierre Guillou, Jules Vidal, Julien Tierny, *Discrete Morse Sandwich: Fast Computation of Persistence Diagrams for Scalar Data*, arXiv:2206.13932 (2022).
- Eve Le Guillou, Pierre Fortin, Julien Tierny, *Distributed Discrete Morse Sandwich*, arXiv:2505.21266 (2025).

### 2. giotto-tda: homology trong scikit-learn

Tauzin, Lupo, Tunstall, Hess và cộng sự (JMLR 2021; API vẫn là cổng vào 2022–2026) gói Ripser/GUDHI thành pipeline scikit-learn: đám mây điểm → phức → barcode → vector. Đây là chỗ Chapter 07 chạm code mà không cần viết $\partial$ bằng tay.

- Guillaume Tauzin et al., *giotto-tda: A Topological Data Analysis Toolkit for Machine Learning and Data Exploration*, *JMLR* 22(39) (2021), arXiv:2004.02551.

### 3. Vectorization ổn định — kể cả multiparameter

Một diagram không phải vector. Loiseaux–Scoccola–Carrière–Botnan (2023) vector hóa persistence đa tham số bằng signed barcode-as-measure; Xin–Mukherjee–Samaga–Dey (2023) đề xuất GRIL; Luchinsky–Islambekov (2024) đóng gói TDAvec. Không có bước này, $H_n$ không vào được gradient descent.

- David Loiseaux et al., *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Cheng Xin, Soham Mukherjee, Shreyas N. Samaga, Tamal K. Dey, *GRIL: A 2-parameter Persistence Based Vectorization for Machine Learning*, arXiv:2304.04970 (2023).

### 4. PH không còn là toàn bộ TDA

Su, Liu, Bou Hamdan, Maroulas, Wu, Carlsson và Wei (2025) viết review “beyond persistent homology”: homotopy, sheaf, phức tế bào, TDL. Wee–Jiang (2025) làm điều tương tự cho khoa học phân tử. Chapter 07 vẫn là động cơ — nhưng không còn là cả chiếc xe.

- Zhe Su et al., *TDA and TDL Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).
- JunJie Wee, Jian Jiang, *A review of TDA and TDL in molecular sciences*, arXiv:2509.16877 (2025).

---

## 🧠 Tài liệu

- Hatcher, *Algebraic Topology*, Ch. 2.
- Edelsbrunner–Harer, *Computational Topology*.
- Các arXiv/JMLR trên.

## 🔗 Ứng dụng

Một lệnh `VietorisRipsPersistence` trong giotto-tda trên đám mây điểm protein cho barcode $H_1,H_2$ — cùng nhóm $H_n$ của bài 07.00, chỉ khác là $\partial$ chạy trong C++.

## 🧩 Bài tập

1. Với 4 đỉnh của hình vuông đơn vị, ước lượng $\varepsilon$ khi $H_1$ sinh và khi nó chết trong VR.
2. Phân biệt barcode và Betti number tĩnh: cái nào là functor theo $\varepsilon$?
3. Vì sao Morse sandwich giúp tính $H_n$ trên ảnh 3D lớn hơn Ripser thuần?
