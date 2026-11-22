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

**Bài tùy chọn.** Các nội dung về đồng điều đơn hình/kỳ dị, dãy Mayer–Vietoris và đối đồng điều không thay đổi; bài này bổ sung khái niệm *lọc* (filtration) cùng các phần mềm tính $H_n$ trực tiếp trên dữ liệu.

---

## 📖 Tổng quan

Đồng điều đếm các lỗ của một không gian cố định, còn **đồng điều bền vững** (persistent homology — PH) theo dõi sự xuất hiện và biến mất của các lỗ dọc theo **một họ không gian lồng nhau**. Về bản chất, đó vẫn là công thức $H_n=\ker\partial_n/\operatorname{im}\partial_{n+1}$ được tính lặp lại trên từng mức $X_{\varepsilon}$. Ba trụ cột thực hành giai đoạn 2021–2026 gồm: thuật toán Ripser (cùng các biến thể cho phức hình hộp và tính toán phân tán), thư viện giotto-tda, và các phương pháp vectơ hóa (vectorization) ổn định để đưa biểu đồ vạch (barcode) vào mô hình học máy. Các bài khảo sát năm 2025 cũng đặt PH vào bối cảnh rộng hơn: phân tích dữ liệu tô-pô (TDA) hiện nay không còn chỉ đồng nhất với việc tính $H_n$.

![Phức simplicial](https://upload.wikimedia.org/wikipedia/commons/5/50/Simplicial_complex_example.svg)
*Phức đơn hình: đối tượng tính $H_n$, đồng thời là $X_{\varepsilon}$ trong một phép lọc Vietoris–Rips. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

![Torus lấy mẫu](https://upload.wikimedia.org/wikipedia/commons/4/4c/Point_cloud_torus.gif)
*Một hình xuyến rời rạc: các lớp $H_1$ thật cần tồn tại lâu hơn nhiễu. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Point_cloud_torus.gif)*

---

## 🎯 Trực giác

Khi tham số $\varepsilon$ nhỏ, phức chỉ là tập các điểm rời nhau nên $H_0$ có hạng lớn và $H_1 = 0$. Khi $\varepsilon$ tăng đến ngưỡng thích hợp, các vòng thật của dữ liệu hình thành. Khi $\varepsilon$ đủ lớn, toàn bộ các lỗ bị lấp kín. **Barcode** ghi lại khoảng tồn tại $[\varepsilon_{\mathrm{birth}}, \varepsilon_{\mathrm{death}})$ của từng lớp đồng điều: các khoảng ngắn thường phản ánh nhiễu, còn các khoảng dài tương ứng với cấu trúc lỗ thực sự. Đây chính là đồng điều của Chương 07 mở rộng thêm một tham số tỉ lệ.

---

## 📐 Bốn tiến bộ cụ thể

### 1. Ripser và các biến thể tính toán

Bauer (công bố trên *JACOT* năm 2021, tiếp tục là chuẩn thực hành giai đoạn 2022–2026) tính đồng điều bền vững Vietoris–Rips bằng biểu diễn ẩn của toán tử đối biên, nhờ đó tránh phải lưu trữ tường minh toàn bộ phức. Guillou–Vidal–Tierny (2022) và Le Guillou–Fortin–Tierny (2025) phát triển *Discrete Morse Sandwich* — dùng lý thuyết Morse rời rạc để rút gọn phức trước khi tính biểu đồ bền vững — mở rộng khả năng xử lý lên các tập dữ liệu quy mô rất lớn và tính toán phân tán.

$$
\mathrm{VR}_{\varepsilon}(X)=\{\sigma\subseteq X:\mathrm{diam}(\sigma)\le\varepsilon\}.
$$

- Ulrich Bauer, *Ripser: efficient computation of Vietoris–Rips persistence barcodes*, *Journal of Applied and Computational Topology* (2021), arXiv:1908.02518.
- Pierre Guillou, Jules Vidal, Julien Tierny, *Discrete Morse Sandwich: Fast Computation of Persistence Diagrams for Scalar Data*, arXiv:2206.13932 (2022).
- Eve Le Guillou, Pierre Fortin, Julien Tierny, *Distributed Discrete Morse Sandwich*, arXiv:2505.21266 (2025).

### 2. giotto-tda: đưa đồng điều vào pipeline scikit-learn

Tauzin, Lupo, Tunstall, Hess và cộng sự (*JMLR* 2021; giao diện lập trình vẫn được dùng rộng rãi giai đoạn 2022–2026) tích hợp Ripser và GUDHI vào quy trình chuẩn của scikit-learn theo chuỗi: đám mây điểm $\to$ phức $\to$ barcode $\to$ vectơ đặc trưng. Công cụ này giúp áp dụng trực tiếp lý thuyết của Chương 07 trong mã nguồn mà không cần tự cài đặt toán tử biên $\partial$.

- Guillaume Tauzin et al., *giotto-tda: A Topological Data Analysis Toolkit for Machine Learning and Data Exploration*, *JMLR* 22(39) (2021), arXiv:2004.02551.

### 3. Vectơ hóa ổn định — bao gồm đa tham số

Biểu đồ bền vững tự thân không phải là một vectơ trong không gian Euclid. Loiseaux–Scoccola–Carrière–Botnan (2023) vectơ hóa đồng điều bền vững đa tham số bằng khái niệm barcode có dấu dưới dạng độ đo (signed barcode-as-measure); Xin–Mukherjee–Samaga–Dey (2023) đề xuất GRIL; Luchinsky–Islambekov (2024) đóng gói thư viện TDAvec. Bước chuyển đổi này là điều kiện cần để đưa thông tin từ $H_n$ vào các thuật toán tối ưu hóa bằng đạo hàm như gradient descent.

- David Loiseaux et al., *Stable Vectorization of Multiparameter Persistent Homology using Signed Barcodes as Measures*, arXiv:2306.03801 (2023).
- Cheng Xin, Soham Mukherjee, Shreyas N. Samaga, Tamal K. Dey, *GRIL: A 2-parameter Persistence Based Vectorization for Machine Learning*, arXiv:2304.04970 (2023).

### 4. Đồng điều bền vững không còn là toàn bộ TDA

Su, Liu, Bou Hamdan, Maroulas, Wu, Carlsson và Wei (2025) công bố bài tổng quan mở rộng "vượt ra ngoài đồng điều bền vững", bao gồm đồng luân, bó (sheaf), phức tế bào và học sâu tô-pô (TDL). Wee–Jiang (2025) thực hiện khảo sát tương tự cho lĩnh vực khoa học phân tử. Đồng điều của Chương 07 vẫn là công cụ cốt lõi, nhưng TDA hiện nay đã mở rộng sang nhiều cấu trúc tô-pô khác.

- Zhe Su et al., *TDA and TDL Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).
- JunJie Wee, Jian Jiang, *A review of TDA and TDL in molecular sciences*, arXiv:2509.16877 (2025).

---

## 🧠 Tài liệu

- Hatcher, *Algebraic Topology*, Ch. 2.
- Edelsbrunner–Harer, *Computational Topology*.
- Các bài báo arXiv và JMLR nêu trên.

## 🔗 Ứng dụng

Một lời gọi `VietorisRipsPersistence` trong giotto-tda trên đám mây điểm tọa độ nguyên tử của protein sẽ trả về barcode cho $H_1$ và $H_2$ — vẫn là các nhóm đồng điều của bài 07.00, nhưng phép tính toán tử biên $\partial$ được thực thi tối ưu trong C++.

## Video tham khảo

- **xem trước** [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, tiếng Anh. Từ đồng điều hữu hạn tới đồng điều bền vững, đúng bước mở rộng của bài này.
- [Applied topology 15: Introduction to a software tutorial for persistent homology and Ripser](https://www.youtube.com/watch?v=jgVr4FIySw4) — Applied Algebraic Topology Network, tiếng Anh. Giới thiệu Ripser và hướng dẫn tính barcode, sát phần mềm được đề cập trong bài.

## 🧩 Bài tập

1. Với 4 đỉnh của hình vuông đơn vị, hãy ước lượng giá trị $\varepsilon$ tại thời điểm lớp $H_1$ sinh ra và biến mất trong phức Vietoris–Rips.
2. Phân biệt barcode và số Betti tĩnh: đối tượng nào thể hiện tính hàm tử theo tham số $\varepsilon$?
3. Vì sao phương pháp Discrete Morse Sandwich giúp tính $H_n$ trên ảnh 3D kích thước lớn hiệu quả hơn so với Ripser thuần túy?
