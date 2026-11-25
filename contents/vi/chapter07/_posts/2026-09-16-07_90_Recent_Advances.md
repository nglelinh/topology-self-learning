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

> **Câu chuyện mở đầu:** Trong toán học thuần túy, một đường tròn hay một hình xuyến được cho sẵn dưới dạng phương trình trơn tru. Nhưng trong thế giới thực — một đám mây tọa độ nguyên tử protein, một lát cắt não 3D, hay dữ liệu cảm biến rung động — bạn **chỉ có một tập hữu hạn các điểm rời rạc đầy nhiễu**! Nếu nối các điểm quá gần nhau, mọi thứ vỡ vụn thành bụi; nếu nối quá xa, tất cả dính bết thành một khối đặc không còn lỗ nào. **Đồng điều bền vững (Persistent Homology)** giải quyết bài toán chọn ngưỡng đó bằng một ý tưởng thiên tài: *đừng chọn một ngưỡng duy nhất — hãy quét qua MỌI ngưỡng $$\varepsilon$$ và ghi lại lỗ nào sống dai nhất!*

Đồng điều đếm các lỗ của một không gian cố định, còn **đồng điều bền vững** (persistent homology — PH) theo dõi sự xuất hiện và biến mất của các lỗ dọc theo **một họ không gian lồng nhau**. Về bản chất, đó vẫn là công thức $H_n=\ker\partial_n/\operatorname{im}\partial_{n+1}$ được tính lặp lại trên từng mức $X_{\varepsilon}$. Ba trụ cột thực hành giai đoạn 2021–2026 gồm: thuật toán Ripser (cùng các biến thể cho phức hình hộp và tính toán phân tán), thư viện giotto-tda, và các phương pháp vectơ hóa (vectorization) ổn định để đưa biểu đồ vạch (barcode) vào mô hình học máy. Các bài khảo sát năm 2025 cũng đặt PH vào bối cảnh rộng hơn: phân tích dữ liệu tô-pô (TDA) hiện nay không còn chỉ đồng nhất với việc tính $H_n$.

![Phức simplicial](https://upload.wikimedia.org/wikipedia/commons/5/50/Simplicial_complex_example.svg)
*Phức đơn hình: đối tượng tính $H_n$, đồng thời là $X_{\varepsilon}$ trong một phép lọc Vietoris–Rips. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

![Torus lấy mẫu](https://upload.wikimedia.org/wikipedia/commons/4/4c/Point_cloud_torus.gif)
*Một hình xuyến rời rạc: các lớp $H_1$ thật cần tồn tại lâu hơn nhiễu. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Point_cloud_torus.gif)*

---

## 🎯 Trực giác

Khi tham số $\varepsilon$ nhỏ, phức chỉ là tập các điểm rời nhau nên $H_0$ có hạng lớn và $H_1 = 0$. Khi $\varepsilon$ tăng đến ngưỡng thích hợp, các vòng thật của dữ liệu hình thành. Khi $\varepsilon$ đủ lớn, toàn bộ các lỗ bị lấp kín. **Barcode** ghi lại khoảng tồn tại $[\varepsilon_{\mathrm{birth}}, \varepsilon_{\mathrm{death}})$ của từng lớp đồng điều: các khoảng ngắn thường phản ánh nhiễu, còn các khoảng dài tương ứng với cấu trúc lỗ thực sự. Đây chính là đồng điều của Chương 07 mở rộng thêm một tham số tỉ lệ.

---

## 🗺️ Kiến thức cần nhớ: Đồng điều bền vững là gì và nghiên cứu những gì?

### 1. Phức Vietoris–Rips & Phép lọc (Filtration)
- **Bản chất:** Cho một tập hữu hạn điểm $$X$$ với khoảng cách giữa từng cặp điểm, tại mỗi bán kính $$\varepsilon \ge 0$$ ta nối hai điểm bằng một cạnh nếu khoảng cách $$\le \varepsilon$$, lấp tam giác nếu cả 3 cạnh $$\le \varepsilon$$, v.v. Kết quả là một **dãy phức đơn hình lồng nhau** $$\mathrm{VR}_{\varepsilon_1}(X) \subseteq \mathrm{VR}_{\varepsilon_2}(X) \subseteq \cdots$$.
- **Lĩnh vực nghiên cứu:** Theo dõi cách ánh xạ bao hàm $$\iota: \mathrm{VR}_{\varepsilon_1} \hookrightarrow \mathrm{VR}_{\varepsilon_2}$$ cảm sinh đồng cấu giữa các nhóm đồng điều $$H_n(\mathrm{VR}_{\varepsilon_1}) \to H_n(\mathrm{VR}_{\varepsilon_2})$$.

### 2. Barcode & Biểu đồ bền vững (Persistence Diagram)
- **Bản chất:** Mỗi lỗ (thành phần liên thông $$H_0$$, vòng khép kín $$H_1$$, khoang rỗng $$H_2$$) ra đời tại một ngưỡng $$\varepsilon_{\text{birth}}$$ và bị lấp kín tại ngưỡng $$\varepsilon_{\text{death}}$$. Tập các khoảng $$[\varepsilon_{\text{birth}}, \varepsilon_{\text{death}})$$ tạo thành **barcode**.
- **Định lý Ổn định (Stability Theorem):** Nếu dữ liệu bị nhiễu nhẹ một lượng $$\eta$$, các điểm trên biểu đồ bền vững dịch chuyển không quá $$\eta$$ theo khoảng cách bottleneck — bảo chứng toán học khiến TDA chống nhiễu cực tốt!

### 3. Thuật toán tăng tốc & Vectơ hóa cho Học máy (2021–2026)
- **Bản chất:** Số lượng đơn hình trong phức Vietoris–Rips bùng nổ theo tổ hợp $$\binom{N}{k+1}$$. Các công cụ hiện đại như **Ripser** (dùng đối đồng điều ẩn), **Discrete Morse Sandwich** (rút gọn phức bằng lý thuyết Morse rời rạc) và các phương pháp **vectơ hóa** biến barcode thành đặc trưng khả vi đưa thẳng vào mạng nơ-ron.

---

## 🧮 Ví dụ tính tay làm từng bước: Barcode của 4 đỉnh hình vuông đơn vị

Lấy 4 điểm nằm ở 4 góc của hình vuông cạnh $$1$$ trong $$\mathbb{R}^2$$:
$$
A(0,0),\quad B(1,0),\quad C(1,1),\quad D(0,1).
$$
Khoảng cách giữa các cặp điểm chỉ có hai giá trị: **4 cạnh dài $$1$$** và **2 đường chéo dài $$\sqrt{2} \approx 1.414$$**. Hãy tăng dần ngưỡng $$\varepsilon$$ từ $$0$$ lên $$2$$ và tính từng nhóm đồng điều bằng tay:

1. **Khi $$0 \le \varepsilon < 1$$:** Chưa có cạnh nào được nối. Ta có 4 đỉnh rời rạc:
   $$
   \beta_0 = 4, \qquad \beta_1 = 0.
   $$
   Cả 4 thành phần liên thông đều ra đời tại $$\varepsilon = 0$$.

2. **Khi $$1 \le \varepsilon < \sqrt{2}$$:** Cả 4 cạnh $$AB, BC, CD, DA$$ đồng loạt xuất hiện, nhưng hai đường chéo $$AC, BD$$ (dài $$\sqrt{2}$$) **chưa** xuất hiện nên chưa có tam giác nào! Hình thu được là đúng một chu trình hình vuông rỗng:
   - 4 thành phần liên thông gộp thành 1 $$\implies$$ **3 thanh của $$H_0$$ chết tại $$\varepsilon = 1$$** (cho 3 khoảng $$[0, 1)$$ và 1 khoảng bất tử $$[0, \infty)$$).
   - **1 vòng khép kín $$H_1$$ ra đời tại $$\varepsilon_{\text{birth}} = 1$$** ($$\beta_1 = 1$$)!

3. **Khi $$\varepsilon \ge \sqrt{2}$$:** Hai đường chéo $$AC, BD$$ xuất hiện, kéo theo cả 4 tam giác (và tứ diện $$ABCD$$) lập tức lấp kín hoàn toàn lỗ giữa hình vuông!
   - **Lớp $$H_1$$ chết tại $$\varepsilon_{\text{death}} = \sqrt{2}$$** ($$\beta_1$$ trở về $$0$$).

**Kết quả Barcode chính xác:**
- $$H_0$$: $$[0, 1),\; [0, 1),\; [0, 1),\; [0, \infty)$$.
- $$H_1$$: duy nhất một thanh $$[1, \sqrt{2})$$ với độ bền (persistence) bằng $$\sqrt{2} - 1 \approx 0.414$$!

### Giải thích: Từ lý thuyết đồng điều Chương 07 đến phần mềm Ripser

#### Bước 1: Thay không gian tĩnh bằng một "bộ phim" không gian lồng nhau
Thay vì hỏi "hình này có bao nhiêu lỗ?", ta hỏi "khi phóng to dần bán kính nối điểm $$\varepsilon$$, những lỗ nào xuất hiện và tồn tại đủ lâu?". Lỗ có khoảng $$\varepsilon_{\text{death}} - \varepsilon_{\text{birth}}$$ lớn là cấu trúc hình học thật; khoảng ngắn sát đường chéo là nhiễu.

#### Bước 2: Dùng tính hàm tử để ghép cặp sinh–tử
Nhờ tính hàm tử của đồng điều, mỗi phép bao hàm $$X_{\varepsilon_1} \hookrightarrow X_{\varepsilon_2}$$ tạo ra ánh xạ tuyến tính giữa các không gian vectơ $$H_n(X_{\varepsilon_1}; \mathbb{F}_2) \to H_n(X_{\varepsilon_2}; \mathbb{F}_2)$$. Định lý phân tích mô-đun bền vững bảo đảm chuỗi không gian vectơ đó luôn phân tích duy nhất thành tổng các thanh barcode $$[b_i, d_i)$$.

#### Bước 3: Tối ưu tính toán bằng đối đồng điều ẩn (Ripser) và Morse rời rạc
Tính khử Gauss trên ma trận biên $$\partial$$ trực tiếp rất tốn bộ nhớ. **Ripser** phát hiện rằng chuyển sang ma trận **đối biên $$\delta$$** (bài 07.04!) kết hợp thủ thuật "xóa cột" (clearing optimization) và sinh ma trận theo kiểu lười giúp giảm bộ nhớ và thời gian tính hàng trăm lần!

#### Bước 4: Vectơ hóa barcode để kết nối với Học máy
Vì tập hợp các thanh barcode không cộng trừ như vectơ thông thường, các phương pháp hiện đại (Persistence Images, Landscapes, Signed Barcodes, GRIL) ánh xạ barcode thành vectơ trong không gian Hilbert mà vẫn bảo toàn tính ổn định — sẵn sàng đưa vào `scikit-learn` hay mạng nơ-ron sâu.

$$
\text{Đám mây điểm }X
\;\xrightarrow{\;\mathrm{VR}_\varepsilon(X)\;}\;
\text{Phép lọc đơn hình}
\;\xrightarrow{\;\text{Ripser (đối biên }\delta)\;}\;
\text{Barcode }[b_i, d_i)
\;\xrightarrow{\;\text{Vectơ hóa ổn định}\;}\;
\text{Đặc trưng cho AI / Khoa học dữ liệu}.
$$

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
