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

> **Câu chuyện mở đầu:** Bạn có hai mô hình 3D của hai phân tử protein đo ở hai phòng thí nghiệm khác nhau — một cái xoay nghiêng $$37^\circ$$, cái kia đặt ở gốc tọa độ khác, thậm chí số lượng nguyên tử còn hơi lệch nhau. Làm sao đo xem **hai hình dạng đó giống nhau đến mức nào** khi chúng thậm chí không nằm chung trong cùng một không gian tọa độ? Chương 04 dạy bạn đo khoảng cách giữa hai *điểm*; bài đọc thêm 2022–2026 này nâng lên một tầng trừu tượng mới: **đo khoảng cách giữa hai không gian metric** bằng **khoảng cách Gromov–Hausdorff** và **khoảng cách xen kẽ (Interleaving)**!

Một metric trên $X$ đo khoảng cách giữa từng cặp điểm. Trong khoa học dữ liệu hiện đại, ta thường cần thêm một tầng trừu tượng: đo khoảng cách giữa hai **không gian**. Khoảng cách Gromov–Hausdorff, khoảng cách bottleneck, khoảng cách Wasserstein trên biểu đồ bền vững (persistence diagram) và khoảng cách xen kẽ (interleaving distance) trên module bền vững là những metric ở cấp độ không gian, được nghiên cứu rộng rãi trong các công trình giai đoạn 2023–2026.

![Khoảng cách Hausdorff](https://upload.wikimedia.org/wikipedia/commons/2/21/Hausdorff_distance_sample.svg)
*Khoảng cách Hausdorff giữa hai tập trong cùng một không gian — bước đệm trước khi định nghĩa Gromov–Hausdorff. Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_distance_sample.svg)*

---

## 🎯 Trực giác

Khoảng cách Hausdorff $d_H(A,B)$ đo xem mỗi điểm của $A$ gần tập $B$ đến mức nào và ngược lại. Khoảng cách Gromov–Hausdorff ($d_{GH}$) bỏ điều kiện $A$ và $B$ phải nằm chung trong một không gian cố định: ta được phép nhúng đẳng cự $A$ và $B$ vào cùng một không gian metric trung gian sao cho $d_H$ giữa hai ảnh là nhỏ nhất có thể. Đây là sự mở rộng tự nhiên của ý tưởng so sánh cấu trúc metric ở bài 04.02 lên cấp độ không gian.

---

## 🗺️ Kiến thức cần nhớ: Đo khoảng cách giữa các Hình dạng và Không gian

### 1. Khoảng cách Hausdorff $$d_H(A, B)$$ (trong cùng không gian mẹ $$Z$$)
- **Bản chất:** Đo độ lệch xấu nhất khi bạn cố gắng phủ tập $$A$$ bằng lân cận bán kính $$r$$ của $$B$$ và ngược lại:
  $$
  d_H(A, B) = \max\Bigl(\sup_{a \in A} d(a, B),\; \sup_{b \in B} d(b, A)\Bigr).
  $$

### 2. Khoảng cách Gromov–Hausdorff $$d_{GH}(X, Y)$$ (so sánh hai không gian ĐỘC LẬP)
- **Bản chất:** Khi $$X$$ và $$Y$$ không nằm chung không gian (hai đám mây điểm, hai đa tạp trừu tượng), ta thử **mọi** phép nhúng đẳng cự $$\varphi: X \hookrightarrow Z,\; \psi: Y \hookrightarrow Z$$ vào một không gian metric chung $$Z$$ rồi lấy cận dưới của $$d_H(\varphi(X), \psi(Y))$$! Kết quả là $$d_{GH}(X, Y) = 0$$ khi và chỉ khi $$X$$ và $$Y$$ **đẳng cự** với nhau!

### 3. Khoảng cách Xen kẽ (Interleaving Distance $$d_I$$) trên Module Bền vững
- **Bản chất:** Phiên bản đại số của khoảng cách metric cho hai bộ barcode / module bền vững $$M, N$$: đo độ dịch chuyển tỉ lệ $$\varepsilon$$ nhỏ nhất sao cho $$M$$ và $$N$$ có thể "xen kẽ" (nhúng qua lại) dọc theo trục tham số $$t$$.

---

## 🧮 Ví dụ tính tay làm từng bước: Tính $$d_H$$ và $$d_{GH}$$ trên tập 2–3 điểm

### Ví dụ 1: Tính tay khoảng cách Hausdorff $$d_H(A, B)$$ trong $$\mathbb{R}$$
Cho $$A = \{0, 1\}$$ và $$B = \{0, 1, 2\}$$ nằm trong $$\mathbb{R}$$ với metric chuẩn:
- Từ mỗi điểm của $$A$$ đến $$B$$: $$d(0, B) = 0,\; d(1, B) = 0 \implies \sup_{a\in A} d(a, B) = 0$$.
- Từ mỗi điểm của $$B$$ đến $$A$$: $$d(0, A) = 0,\; d(1, A) = 0,\; d(2, A) = \min(\lvert 2-0\rvert, \lvert 2-1\rvert) = 1 \implies \sup_{b\in B} d(b, A) = 1$$.
- Lấy giá trị lớn nhất hai chiều:
  $$
  d_H(A, B) = \max(0, 1) = 1!
  $$

### Ví dụ 2: Tính tay khoảng cách Gromov–Hausdorff $$d_{GH}(X, P)$$ giữa đoạn 2 điểm và 1 điểm!
Cho $$X = \{a, b\}$$ với $$d_X(a, b) = 1$$ và $$P = \{p\}$$ (không gian 1 điểm duy nhất).
- **Chặn trên:** Nhúng đẳng cự $$X$$ vào $$\mathbb{R}$$ tại $$\{-\tfrac{1}{2}, +\tfrac{1}{2}\}$$ và nhúng $$P$$ vào đúng tâm $$\{0\}$$. Khi đó khoảng cách Hausdorff giữa $$\{-\tfrac{1}{2}, +\tfrac{1}{2}\}$$ và $$\{0\}$$ là đúng **$$\frac{1}{2}$$** $$\implies d_{GH}(X, P) \le \frac{1}{2}$$!
- **Chặn dưới:** Trong mọi phép nhúng đẳng cự vào bất kỳ không gian $$Z$$ nào, hai ảnh $$a', b'$$ cách nhau $$1$$; theo bất đẳng thức tam giác, $$1 = d_Z(a', b') \le d_Z(a', p') + d_Z(p', b') \implies \max(d_Z(a', p'), d_Z(b', p')) \ge \frac{1}{2}$$!
- Kết luận chính xác: **$$d_{GH}(X, P) = \frac{1}{2} = \frac{1}{2}\operatorname{diam}(X)$$**! (Và tổng quát, khoảng cách Gromov–Hausdorff từ bất kỳ không gian bị chặn $$X$$ nào đến 1 điểm luôn bằng đúng nửa đường kính của $$X$$!)

### Giải thích: Vì sao "Metric giữa các không gian" lại bùng nổ trong 2022–2026?

#### Bước 1: Thoát khỏi sự phụ thuộc vào hệ tọa độ
Hai đám mây điểm protein xoay khác góc có khoảng cách Euclid rất lớn dù thực chất là cùng một phân tử. $$d_{GH}$$ chỉ nhìn vào ma trận khoảng cách nội tại nên **bất biến hoàn toàn dưới phép xoay và tịnh tiến**.

#### Bước 2: Định lý Ổn định — Cầu nối Lipschitz từ Hình dạng sang Barcode
Một trong những định lý đẹp nhất của TDA khẳng định: khoảng cách bottleneck giữa hai biểu đồ bền vững bị chặn trên trực tiếp bởi $$2\,d_{GH}(X, Y)$$! Nghĩa là hai hình dạng gần nhau theo $$d_{GH}$$ chắc chắn có chữ ký tô-pô gần nhau!

#### Bước 3: Mở rộng sang dữ liệu có nhãn màu và không gian tiềm ẩn AI
Các công trình 2024–2026 mở rộng $$d_{GH}$$ cho dữ liệu hóa học có gán nhãn nguyên tử (chromatic metric pairs) và dùng $$d_{GH}$$ để kiểm tra xem không gian ẩn (latent space) của mạng nơ-ron có khớp với hình học cầu, phẳng hay hyperbolic hay không.

#### Bước 4: Đánh đổi tính toán — Từ NP-hard đến xấp xỉ thông minh
Tính chính xác $$d_{GH}$$ trên tập lớn là bài toán NP-hard; vì thế các thuật toán mới (như khoảng cách Gromov–Wasserstein và các cải tiến tính $$d_I$$ năm 2026) kết hợp tối ưu vận tải và lý thuyết đồ thị Reeb để chạy được trên dữ liệu thực!

$$
\text{Metric điểm }d(x,y)
\;\xrightarrow{\;\text{Tập con}\;}\;
d_H(A,B)
\;\xrightarrow{\;\text{Nhúng đẳng cự}\;}\;
d_{GH}(X,Y)
\;\xrightarrow{\;\text{Ổn định TDA}\;}\;
d_I(M,N) \le 2\,d_{GH}(X,Y).
$$

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
