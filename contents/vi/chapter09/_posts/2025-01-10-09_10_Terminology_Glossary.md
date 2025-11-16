---
layout: post
title: "Bài 09.10: Từ Điển Thuật Ngữ Toán Học - Tổng Hợp Toàn Khóa"
lang: vi
lang-ref: lecture-09-10
chapter: 9
lecture: 10
categories: [chapter09]
tags: [glossary, terminology, dictionary, reference]
description: "Tổng hợp tất cả các thuật ngữ toán học đã được sử dụng trong toàn bộ khóa học topology, trình bày dưới dạng bảng có tổ chức"
---

**Từ Điển Thuật Ngữ Toán Học - Tổng Hợp Toàn Khóa**

---

**Lưu ý về hiển thị công thức toán học:** Tất cả các công thức toán học trong bảng được viết bằng LaTeX và sẽ được hiển thị đúng khi MathJax được load. Nếu công thức không hiển thị, vui lòng đảm bảo rằng MathJax đã được cấu hình đúng trong trang web.

---

## 📖 Tổng quan

Bài học này là một **từ điển toàn diện** tổng hợp tất cả các thuật ngữ toán học đã được sử dụng trong toàn bộ khóa học topology. Đây là một tài liệu tham khảo hữu ích để tra cứu nhanh các định nghĩa, ký hiệu, và khái niệm quan trọng.

**Cách sử dụng:**

- **Tra cứu nhanh:** Sử dụng để tìm định nghĩa của một thuật ngữ cụ thể
- **Ôn tập:** Xem lại các khái niệm đã học theo từng chương
- **Tham khảo:** Sử dụng khi đọc các bài học khác để hiểu các thuật ngữ

**Cấu trúc:**

Các thuật ngữ được sắp xếp theo các chương và chủ đề chính, với bảng trình bày rõ ràng bao gồm:
- **Thuật ngữ** (tiếng Việt và tiếng Anh)
- **Ký hiệu toán học** (nếu có)
- **Định nghĩa ngắn gọn**
- **Chương xuất hiện**

---

## 📚 Chapter 00: Foundations and Set-Theoretic Topology

### Lý Thuyết Tập Hợp

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tập hợp** (Set) | $A$, $B$, $X$ | Một collection các đối tượng phân biệt | 00.00 |
| **Phần tử** (Element) | $x \in A$ | Một đối tượng thuộc tập hợp | 00.00 |
| **Tập con** (Subset) | $A \subseteq B$ | Mọi phần tử của $A$ đều thuộc $B$ | 00.00 |
| **Tập rỗng** (Empty Set) | $\emptyset$ | Tập hợp không có phần tử nào | 00.00 |
| **Hợp** (Union) | $A \cup B$ | Tập tất cả phần tử thuộc $A$ hoặc $B$ | 00.00 |
| **Giao** (Intersection) | $A \cap B$ | Tập tất cả phần tử thuộc cả $A$ và $B$ | 00.00 |
| **Hiệu** (Difference) | $A \setminus B$ | Tập các phần tử thuộc $A$ nhưng không thuộc $B$ | 00.00 |
| **Phần bù** (Complement) | $A^c$ | Tập tất cả phần tử không thuộc $A$ | 00.00 |
| **Tích Descartes** (Cartesian Product) | $A \times B$ | Tập các cặp có thứ tự $(a,b)$ với $a \in A$, $b \in B$ | 00.01 |
| **Lực lượng** (Cardinality) | $|A|$, $\mathrm{card}(A)$ | Số lượng phần tử của tập hợp | 00.00 |
| **Đếm được** (Countable) | $\aleph_0$ | Có thể đặt tương ứng 1-1 với $\mathbb{N}$ | 00.00 |
| **Không đếm được** (Uncountable) | $2^{\aleph_0}$ | Không thể đặt tương ứng với $\mathbb{N}$ | 00.00 |

### Hàm Số và Quan Hệ

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Hàm số** (Function) | $f: A \to B$ | Ánh xạ từ tập $A$ vào tập $B$ | 00.00 |
| **Đơn ánh** (Injective) | $f$ injective | $f(a_1) = f(a_2) \Rightarrow a_1 = a_2$ | 00.00 |
| **Toàn ánh** (Surjective) | $f$ surjective | Mọi $b \in B$ đều có $a \in A$ sao cho $f(a) = b$ | 00.00 |
| **Song ánh** (Bijective) | $f$ bijective | Vừa đơn ánh vừa toàn ánh | 00.00 |
| **Hàm ngược** (Inverse Function) | $f^{-1}$ | Hàm ngược của song ánh | 00.00 |
| **Quan hệ tương đương** (Equivalence Relation) | $\sim$ | Quan hệ phản xạ, đối xứng, bắc cầu | 00.00 |
| **Lớp tương đương** (Equivalence Class) | $[a]$ | Tập tất cả phần tử tương đương với $a$ | 00.00 |
| **Phân hoạch** (Partition) | - | Phân chia tập hợp thành các lớp tương đương | 00.00 |

### Tiên Đề và Logic

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tiên đề chọn** (Axiom of Choice) | AC | Có thể chọn một phần tử từ mỗi tập hợp | 00.01 |
| **Bổ đề Zorn** (Zorn's Lemma) | - | Mọi tập được sắp thứ tự bộ phận có phần tử tối đại | 00.01 |
| **Nguyên lý sắp thứ tự tốt** (Well-Ordering Principle) | - | Mọi tập hợp đều có thể sắp thứ tự tốt | 00.01 |
| **Quy nạp toán học** (Mathematical Induction) | - | Phương pháp chứng minh cho các số tự nhiên | 00.02 |
| **Phản chứng** (Proof by Contradiction) | - | Giả sử phủ định để dẫn đến mâu thuẫn | 00.02 |

### Số Thực và Không Gian Euclid

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Số thực** (Real Numbers) | $\mathbb{R}$ | Tập hợp tất cả số thực | 00.03 |
| **Không gian Euclid** (Euclidean Space) | $\mathbb{R}^n$ | Không gian $n$-chiều với metric Euclid | 00.03 |
| **Tính đầy đủ** (Completeness) | - | Mọi dãy Cauchy đều hội tụ | 00.03 |
| **Cắt Dedekind** (Dedekind Cut) | - | Cách xây dựng $\mathbb{R}$ từ $\mathbb{Q}$ | 00.03 |

---

## 📚 Chapter 01: Topological Spaces and Continuous Functions

### Không Gian Tô-pô

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Không gian tô-pô** (Topological Space) | $(X, \tau)$ | Tập hợp $X$ với topology $\tau$ | 01.00 |
| **Topology** | $\tau$ | Họ các tập mở thỏa mãn ba tiên đề | 01.00 |
| **Tập mở** (Open Set) | $U \in \tau$ | Phần tử của topology | 01.00 |
| **Tập đóng** (Closed Set) | $A$ closed | Phần bù của tập mở | 01.02 |
| **Topology tầm thường** (Trivial Topology) | $\{\emptyset, X\}$ | Topology nhỏ nhất | 01.00 |
| **Topology rời rạc** (Discrete Topology) | $\mathcal{P}(X)$ | Topology lớn nhất (mọi tập đều mở) | 01.00 |
| **Topology hữu hạn bù** (Cofinite Topology) | - | Tập mở là $\emptyset$ hoặc có phần bù hữu hạn | 01.00 |
| **Topology đếm được bù** (Cocountable Topology) | - | Tập mở là $\emptyset$ hoặc có phần bù đếm được | 01.00 |
| **Thô hơn** (Coarser) | $\tau_1 \subseteq \tau_2$ | Topology nhỏ hơn | 01.00 |
| **Mịn hơn** (Finer) | $\tau_2 \supseteq \tau_1$ | Topology lớn hơn | 01.00 |

### Cơ Sở và Tiền Cơ Sở

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Cơ sở** (Basis) | $\mathcal{B}$ | Họ tập mở sinh ra topology | 01.01 |
| **Tiền cơ sở** (Subbasis) | $\mathcal{S}$ | Họ tập hợp sinh ra basis | 01.01 |
| **Cơ sở chuẩn** (Standard Basis) | - | Cơ sở cho $\mathbb{R}^n$ | 01.01 |

### Bao Đóng và Phần Trong

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Bao đóng** (Closure) | $\overline{A}$, $\mathrm{cl}(A)$ | Tập đóng nhỏ nhất chứa $A$ | 01.02 |
| **Phần trong** (Interior) | $A^\circ$, $\mathrm{int}(A)$ | Tập mở lớn nhất chứa trong $A$ | 01.02 |
| **Biên** (Boundary) | $\partial A$ | $\overline{A} \setminus A^\circ$ | 01.02 |
| **Điểm giới hạn** (Limit Point) | - | Mọi lân cận đều chứa điểm khác của $A$ | 01.02 |
| **Điểm cô lập** (Isolated Point) | - | Có lân cận không chứa điểm khác của $A$ | 01.02 |

### Hàm Liên Tục và Đồng Phôi

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Hàm liên tục** (Continuous Function) | $f: X \to Y$ | Ảnh ngược của tập mở là tập mở | 01.03 |
| **Đồng phôi** (Homeomorphism) | $f: X \cong Y$ | Song ánh liên tục với hàm ngược liên tục | 01.03 |
| **Phép nhúng** (Embedding) | $f: X \hookrightarrow Y$ | Đồng phôi lên ảnh của nó | 01.03 |
| **Tương đương đồng luân** (Homotopy Equivalence) | $X \simeq Y$ | Tồn tại ánh xạ với đồng luân ngược | 06.00 |

### Topology Con và Tích

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Topology con** (Subspace Topology) | $Y \subseteq X$ | Topology cảm sinh trên tập con | 01.04 |
| **Topology tích** (Product Topology) | $X \times Y$ | Topology trên tích Descartes | 01.04 |
| **Hình chiếu** (Projection) | $\pi_i: X_1 \times X_2 \to X_i$ | Ánh xạ chiếu lên thành phần thứ $i$ | 01.04 |

---

## 📚 Chapter 02: Connectedness and Compactness

### Liên Thông

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Liên thông** (Connected) | - | Không thể phân thành hai tập mở rời nhau | 02.00 |
| **Thành phần liên thông** (Connected Component) | - | Tập liên thông lớn nhất chứa điểm | 02.00 |
| **Liên thông đường** (Path-Connected) | - | Mọi hai điểm đều nối được bằng đường đi | 02.00 |
| **Thành phần liên thông đường** (Path Component) | - | Tập liên thông đường lớn nhất | 02.00 |
| **Đường đi** (Path) | $\gamma: [0,1] \to X$ | Ánh xạ liên tục từ đoạn vào không gian | 02.00 |
| **Vòng lặp** (Loop) | $\gamma: S^1 \to X$ | Đường đi khép kín | 06.01 |

### Compact

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Compact** | - | Mọi phủ mở đều có phủ con hữu hạn | 02.01 |
| **Phủ mở** (Open Cover) | $\{U_\alpha\}$ | Họ tập mở có hợp chứa không gian | 02.01 |
| **Phủ con hữu hạn** (Finite Subcover) | - | Phủ con có số phần tử hữu hạn | 02.01 |
| **Liên compact** (Locally Compact) | - | Mọi điểm có lân cận compact | 02.02 |
| **Compact hóa** (Compactification) | $\hat{X}$ | Không gian compact chứa $X$ | 02.02 |
| **Compact hóa một điểm** (One-Point Compactification) | $X^*$ | Thêm điểm vô cực | 02.02 |
| **Compact hóa Stone-Čech** (Stone-Čech Compactification) | $\beta X$ | Compact hóa phổ quát | 02.02 |

---

## 📚 Chapter 03: Separation Axioms

### Tiên Đề Tách

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **T0-space** | - | Với mọi hai điểm, có tập mở chứa một điểm nhưng không chứa điểm kia | 03.00 |
| **T1-space** | - | Mọi điểm đơn đều đóng | 03.00 |
| **Hausdorff** (T2) | - | Mọi hai điểm đều có lân cận rời nhau | 03.00 |
| **Regular** (T3) | - | Tập đóng và điểm không thuộc có lân cận rời nhau | 03.01 |
| **Normal** (T4) | - | Mọi hai tập đóng rời nhau có lân cận rời nhau | 03.01 |
| **Hoàn toàn chính quy** (Completely Regular) | T3½ | Regular và có hàm liên tục tách điểm và tập đóng | 03.01 |

### Tiên Đề Đếm Được

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đếm được thứ nhất** (First Countable) | - | Mọi điểm có cơ sở lân cận đếm được | 03.02 |
| **Đếm được thứ hai** (Second Countable) | - | Có cơ sở đếm được | 03.02 |
| **Separable** | - | Có tập con đếm được trù mật | 03.02 |
| **Lindelöf** | - | Mọi phủ mở đều có phủ con đếm được | 03.02 |

### Định Lý Metrization

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Metrizable** | - | Có thể định nghĩa metric sinh ra topology | 03.03 |
| **Định lý Urysohn Metrization** | - | T3 + Second countable $\Rightarrow$ Metrizable | 03.03 |
| **Bổ đề Urysohn** (Urysohn's Lemma) | - | Tồn tại hàm liên tục tách tập đóng rời nhau | 03.01 |
| **Định lý Tietze Extension** | - | Hàm liên tục trên tập đóng có thể mở rộng | 03.01 |

---

## 📚 Chapter 04: Metric Spaces

### Không Gian Metric

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Metric** (Khoảng cách) | $d: X \times X \to \mathbb{R}$ | Hàm khoảng cách thỏa mãn ba tiên đề | 04.00 |
| **Không gian metric** (Metric Space) | $(X, d)$ | Tập hợp với metric | 04.00 |
| **Quả cầu mở** (Open Ball) | $B(x, r)$ | $\{y : d(x,y) < r\}$ | 04.00 |
| **Quả cầu đóng** (Closed Ball) | $\overline{B}(x, r)$ | $\{y : d(x,y) \leq r\}$ | 04.00 |
| **Metric Euclid** (Euclidean Metric) | $d_2$ | $\sqrt{\sum (x_i - y_i)^2}$ | 04.00 |
| **Metric Manhattan** (Manhattan Metric) | $d_1$ | $\sum |x_i - y_i|$ | 04.00 |
| **Metric Maximum** (Maximum Metric) | $d_\infty$ | $\max |x_i - y_i|$ | 04.00 |
| **Metric rời rạc** (Discrete Metric) | $d_{\mathrm{disc}}$ | $d(x,y) = 1$ nếu $x \neq y$ | 04.00 |

### Tính Đầy Đủ và Baire

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Dãy Cauchy** (Cauchy Sequence) | $(x_n)$ | $\forall \epsilon > 0, \exists N: m,n \geq N \Rightarrow d(x_m, x_n) < \epsilon$ | 04.01 |
| **Đầy đủ** (Complete) | - | Mọi dãy Cauchy đều hội tụ | 04.01 |
| **Hoàn thiện** (Completion) | $\hat{X}$ | Không gian đầy đủ chứa $X$ | 04.01 |
| **Tập không đâu trù mật** (Nowhere Dense) | - | Phần trong của bao đóng rỗng | 04.01 |
| **Tập meager** (Meager/First Category) | - | Hợp đếm được các tập không đâu trù mật | 04.01 |
| **Tập nonmeager** (Nonmeager/Second Category) | - | Không phải meager | 04.01 |
| **Định lý Baire Category** | - | Không gian đầy đủ là nonmeager | 04.01 |

### Tính Liên Tục Đều

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Liên tục đều** (Uniformly Continuous) | - | $\forall \epsilon > 0, \exists \delta > 0: d(x,y) < \delta \Rightarrow d(f(x), f(y)) < \epsilon$ | 04.02 |
| **Lipschitz** | - | $d(f(x), f(y)) \leq L \cdot d(x,y)$ | 04.02 |
| **Hệ số Lipschitz** (Lipschitz Constant) | $L$ | Hằng số trong điều kiện Lipschitz | 04.02 |
| **Co rút** (Contraction) | - | Lipschitz với $L < 1$ | 04.02 |
| **Định lý điểm cố định Banach** | - | Co rút trên không gian đầy đủ có điểm cố định duy nhất | 04.02 |

### Metric Tích và Không Gian Hàm

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Metric tích** (Product Metric) | - | Metric trên tích các không gian metric | 04.03 |
| **Không gian hàm** (Function Space) | $C(X,Y)$ | Tập các hàm liên tục | 04.03 |
| **Metric đều** (Uniform Metric) | $d_\infty$ | $\sup_{x \in X} d(f(x), g(x))$ | 04.03 |
| **Hội tụ đều** (Uniform Convergence) | - | Hội tụ theo metric đều | 04.03 |
| **Hội tụ điểm** (Pointwise Convergence) | - | Hội tụ tại mỗi điểm | 04.03 |

---

## 📚 Chapter 05: Quotient Spaces

### Topology Thương

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Quan hệ tương đương** (Equivalence Relation) | $\sim$ | Quan hệ phản xạ, đối xứng, bắc cầu | 05.00 |
| **Tập thương** (Quotient Set) | $X/\sim$ | Tập các lớp tương đương | 05.00 |
| **Topology thương** (Quotient Topology) | - | Topology lớn nhất làm ánh xạ chiếu liên tục | 05.00 |
| **Ánh xạ chiếu** (Projection Map) | $\pi: X \to X/\sim$ | Ánh xạ gửi phần tử vào lớp tương đương | 05.00 |
| **Ánh xạ thương** (Quotient Map) | $q: X \to Y$ | Ánh xạ liên tục, mở, và toàn ánh | 05.00 |

### Phân Loại Bề Mặt

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Bề mặt** (Surface) | - | 2-manifold compact | 05.01 |
| **Định hướng được** (Orientable) | - | Có thể định hướng nhất quán | 05.01 |
| **Không định hướng được** (Non-orientable) | - | Không thể định hướng | 05.01 |
| **Genus** | $g$ | Số lỗ trong bề mặt | 05.01 |
| **Đặc trưng Euler** (Euler Characteristic) | $\chi$ | $V - E + F$ | 05.01 |
| **Tổng liên thông** (Connected Sum) | $\#$ | Phép toán ghép hai bề mặt | 05.01 |
| **Đa giác cơ bản** (Fundamental Polygon) | - | Biểu diễn bề mặt bằng đa giác | 05.01 |

### Phức CW

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Phức CW** (CW Complex) | - | Không gian được xây dựng từ cells | 05.02 |
| **n-cell** | $e^n$ | Quả cầu mở $n$-chiều | 05.02 |
| **Skeleton** | $X^n$ | Phức con gồm các cells chiều $\leq n$ | 05.02 |
| **Ánh xạ gắn** (Attaching Map) | $\phi: S^{n-1} \to X^{n-1}$ | Ánh xạ gắn $n$-cell vào skeleton | 05.02 |

### Tác Động Nhóm

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tác động nhóm** (Group Action) | $G \curvearrowright X$ | Ánh xạ $G \times X \to X$ thỏa mãn tiên đề | 05.03 |
| **Quỹ đạo** (Orbit) | $G \cdot x$ | Tập $\{g \cdot x : g \in G\}$ | 05.03 |
| **Nhóm đẳng hướng** (Stabilizer) | $G_x$ | $\{g \in G : g \cdot x = x\}$ | 05.03 |
| **Không gian quỹ đạo** (Orbit Space) | $X/G$ | Tập các quỹ đạo với topology thương | 05.03 |

---

## 📚 Chapter 06: Fundamental Group

### Đồng Luân

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đồng luân** (Homotopy) | $F: X \times [0,1] \to Y$ | Biến dạng liên tục giữa hai ánh xạ | 06.00 |
| **Đồng luân đường** (Path Homotopy) | $\gamma \simeq_p \delta$ | Đồng luân giữa các đường đi | 06.00 |
| **Lớp đồng luân** (Homotopy Class) | $[\gamma]$ | Tập các đường đi đồng luân | 06.00 |
| **Co được** (Contractible) | - | Đồng luân với điểm | 06.00 |
| **Rút đồng luân** (Deformation Retract) | - | Rút liên tục về không gian con | 06.00 |

### Nhóm Cơ Bản

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Nhóm cơ bản** (Fundamental Group) | $\pi_1(X, x_0)$ | Nhóm các lớp đồng luân của loops tại $x_0$ | 06.01 |
| **Điểm cơ sở** (Basepoint) | $x_0$ | Điểm cố định cho loops | 06.01 |
| **Ghép nối** (Concatenation) | $\gamma \cdot \delta$ | Đi qua $\gamma$ rồi $\delta$ | 06.01 |
| **Đường đi ngược** (Inverse Path) | $\gamma^{-1}$ | Đi ngược lại đường đi | 06.01 |
| **Vòng lặp hằng** (Constant Loop) | $e_{x_0}$ | Vòng lặp không di chuyển | 06.01 |
| **Số vòng quay** (Winding Number) | - | Số lần vòng quanh điểm | 06.02 |

### Không Gian Phủ

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Không gian phủ** (Covering Space) | $\tilde{X}$ | Không gian phủ $X$ | 06.03 |
| **Ánh xạ phủ** (Covering Map) | $p: \tilde{X} \to X$ | Ánh xạ phủ địa phương | 06.03 |
| **Lift** | $\tilde{f}$ | Nâng ánh xạ lên không gian phủ | 06.03 |
| **Phủ phổ quát** (Universal Cover) | - | Phủ đơn liên | 06.03 |
| **Biến đổi Deck** (Deck Transformation) | - | Tự đẳng cấu của không gian phủ | 06.03 |

### Định Lý Van Kampen

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tích tự do** (Free Product) | $G * H$ | Tích tự do của hai nhóm | 06.04 |
| **Tích tự do ghép** (Amalgamated Free Product) | $G *_K H$ | Tích tự do ghép qua nhóm con | 06.04 |
| **Định lý Seifert-Van Kampen** | - | Tính toán $\pi_1$ từ các phần | 06.04 |
| **Tổng nêm** (Wedge Sum) | $X \vee Y$ | Ghép hai không gian tại một điểm | 06.04 |

---

## 📚 Chapter 07: Homology Theory

### Homology Đơn Hình

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **n-đơn hình** (n-Simplex) | $\sigma = [v_0, \ldots, v_n]$ | Convex hull của $n+1$ điểm độc lập | 07.00 |
| **Mặt** (Face) | $\partial_i \sigma$ | Simplex con loại bỏ vertex $v_i$ | 07.00 |
| **Phức đơn hình** (Simplicial Complex) | $K$ | Tập các simplices đóng với mặt | 07.00 |
| **Thực hóa hình học** (Geometric Realization) | $|K|$ | Không gian tô-pô của phức | 07.00 |
| **Nhóm chuỗi** (Chain Group) | $C_n(K)$ | Nhóm abel tự do sinh bởi $n$-simplices | 07.00 |
| **Toán tử biên** (Boundary Operator) | $\partial_n: C_n \to C_{n-1}$ | Toán tử tính biên của simplex | 07.00 |
| **Phức chuỗi** (Chain Complex) | $(C_*, \partial_*)$ | Dãy các nhóm và toán tử biên | 07.00 |
| **Chu trình** (Cycle) | $Z_n = \ker(\partial_n)$ | Phần tử có biên bằng 0 | 07.00 |
| **Biên** (Boundary) | $B_n = \mathrm{im}(\partial_{n+1})$ | Phần tử là biên của phần tử khác | 07.00 |
| **Nhóm đồng điều** (Homology Group) | $H_n(K) = Z_n / B_n$ | Chu trình modulo biên | 07.00 |
| **Số Betti** (Betti Number) | $\beta_n = \mathrm{rank}(H_n)$ | Hạng của nhóm đồng điều | 07.00 |

### Homology Kỳ Dị

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đơn hình chuẩn** (Standard Simplex) | $\Delta^n$ | Simplex chuẩn trong $\mathbb{R}^{n+1}$ | 07.01 |
| **Tọa độ barycentric** (Barycentric Coordinates) | $(t_0, \ldots, t_n)$ | Tọa độ trong simplex | 07.01 |
| **Ánh xạ mặt** (Face Map) | $\delta_i: \Delta^{n-1} \to \Delta^n$ | Ánh xạ vào mặt thứ $i$ | 07.01 |
| **Ánh xạ suy biến** (Degeneracy Map) | $s_i: \Delta^{n+1} \to \Delta^n$ | Ánh xạ suy biến | 07.01 |
| **n-đơn hình kỳ dị** (Singular n-Simplex) | $\sigma: \Delta^n \to X$ | Ánh xạ liên tục từ simplex chuẩn | 07.01 |
| **Nhóm chuỗi kỳ dị** (Singular Chain Group) | $C_n(X)$ | Nhóm abel tự do sinh bởi singular simplices | 07.01 |
| **Homology kỳ dị** (Singular Homology) | $H_n(X)$ | Homology của phức chuỗi kỳ dị | 07.01 |

### Dãy Mayer-Vietoris

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Dãy khớp** (Exact Sequence) | - | Dãy với $\mathrm{im} = \ker$ | 07.03 |
| **Dãy khớp ngắn** (Short Exact Sequence) | $0 \to A \to B \to C \to 0$ | Dãy khớp với 5 phần tử | 07.03 |
| **Dãy Mayer-Vietoris** | - | Dãy khớp dài tính $H_n$ từ các phần | 07.03 |
| **Ánh xạ nối** (Connecting Homomorphism) | $\partial_*$ | Ánh xạ nối trong dãy khớp | 07.03 |

### Đồng Điều

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đồng điều** (Cohomology) | $H^n(X)$ | Đối ngẫu của homology | 07.04 |
| **Nhóm đối chuỗi** (Cochain Group) | $C^n(X)$ | $\mathrm{Hom}(C_n(X), \mathbb{Z})$ | 07.04 |
| **Toán tử đối biên** (Coboundary Operator) | $\delta: C^n \to C^{n+1}$ | Đối ngẫu của toán tử biên | 07.04 |
| **Tích cúp** (Cup Product) | $\cup$ | Phép nhân trong cohomology | 07.04 |
| **Vành đồng điều** (Cohomology Ring) | $H^*(X)$ | Cohomology với tích cúp | 07.04 |

---

## 📚 Chapter 08: Advanced Topics

### Nhóm Đồng Luân Cao

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Nhóm đồng luân n** (n-th Homotopy Group) | $\pi_n(X, x_0)$ | Nhóm các lớp đồng luân của ánh xạ $S^n \to X$ | 08.00 |
| **Bậc của ánh xạ** (Degree of a Map) | $\deg(f)$ | Số nguyên đặc trưng ánh xạ $S^n \to S^n$ | 08.00 |
| **Fibration Hopf** (Hopf Fibration) | $S^3 \to S^2$ | Fibration quan trọng | 08.00 |
| **Định lý Freudenthal Suspension** | - | Liên hệ $\pi_n$ và $\pi_{n+1}$ | 08.00 |
| **Nhóm đồng luân ổn định** (Stable Homotopy Groups) | $\pi_k^s$ | Giới hạn của $\pi_{n+k}(S^n)$ | 08.00 |

### Bó Sợi và Bó Vectơ

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Bó sợi** (Fiber Bundle) | $E \to B$ | Không gian phủ địa phương với fiber | 08.01 |
| **Cơ sở** (Base Space) | $B$ | Không gian cơ sở | 08.01 |
| **Tổng** (Total Space) | $E$ | Không gian tổng | 08.01 |
| **Sợi** (Fiber) | $F$ | Không gian sợi | 08.01 |
| **Tầm thường địa phương** (Locally Trivial) | - | Địa phương giống tích | 08.01 |
| **Hàm chuyển tiếp** (Transition Function) | - | Hàm chuyển đổi giữa các biểu đồ | 08.01 |
| **Bó vectơ** (Vector Bundle) | - | Bó sợi với fiber là không gian vectơ | 08.01 |
| **Bó tiếp tuyến** (Tangent Bundle) | $TM$ | Bó vectơ của các vectơ tiếp tuyến | 08.01 |
| **Bó chuẩn** (Normal Bundle) | $\nu(M)$ | Bó vectơ của các vectơ pháp tuyến | 08.01 |
| **Bó chính** (Principal Bundle) | - | Bó sợi với fiber là nhóm Lie | 08.01 |

### Lý Thuyết Morse

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Hàm Morse** (Morse Function) | $f: M \to \mathbb{R}$ | Hàm với các điểm tới hạn không suy biến | 08.02 |
| **Điểm tới hạn** (Critical Point) | - | Điểm với $df = 0$ | 08.02 |
| **Chỉ số** (Index) | $\lambda$ | Số giá trị riêng âm của Hessian | 08.02 |
| **Tập mức dưới** (Sublevel Set) | $M^a$ | $\{x : f(x) \leq a\}$ | 08.02 |
| **Bổ đề Morse** (Morse Lemma) | - | Dạng chuẩn của hàm Morse tại điểm tới hạn | 08.02 |
| **Bất đẳng thức Morse** (Morse Inequalities) | - | $c_k \geq \beta_k$ | 08.02 |

### Đa Tạp Tô-pô

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đa tạp tô-pô** (Topological Manifold) | $M$ | Không gian Hausdorff, đếm được thứ hai, địa phương Euclid | 08.03 |
| **Biểu đồ** (Chart) | $(U, \phi)$ | Mở $U$ với homeomorphism vào $\mathbb{R}^n$ | 08.03 |
| **Atlas** | - | Tập các biểu đồ phủ đa tạp | 08.03 |
| **Đa tạp trơn** (Smooth Manifold) | - | Đa tạp với atlas trơn | 08.03 |
| **Đa tạp có biên** (Manifold with Boundary) | - | Đa tạp với biên | 08.03 |
| **Hình cầu kỳ lạ** (Exotic Sphere) | - | Đa tạp homeomorphic nhưng không diffeomorphic với $S^n$ | 08.03 |

### Lý Thuyết Nút

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Nút** (Knot) | $K: S^1 \to \mathbb{R}^3$ | Embedding của đường tròn vào không gian 3D | 08.04 |
| **Nút không** (Unknot) | - | Nút tầm thường (đường tròn) | 08.04 |
| **Tương đương nút** (Knot Equivalence) | - | Ambient isotopic | 08.04 |
| **Phép biến đổi Reidemeister** (Reidemeister Move) | RI, RII, RIII | Ba phép biến đổi cơ bản trên diagram | 08.04 |
| **Mặt Seifert** (Seifert Surface) | $\Sigma$ | Mặt có biên là nút | 08.04 |
| **Genus của nút** (Knot Genus) | $g(K)$ | Genus nhỏ nhất của Seifert surface | 08.04 |
| **Nhóm nút** (Knot Group) | $\pi_1(S^3 \setminus K)$ | Fundamental group của phần bù nút | 08.04 |
| **Đa thức Alexander** (Alexander Polynomial) | $\Delta_K(t)$ | Đa thức bất biến của nút | 08.04 |
| **Đa thức Conway** (Conway Polynomial) | $\nabla_K(z)$ | Đa thức với skein relation đơn giản | 08.04 |
| **Đa thức Jones** (Jones Polynomial) | $V_K(t)$ | Đa thức bất biến lượng tử | 08.04 |
| **Chữ ký** (Signature) | $\sigma(K)$ | Số nguyên bất biến của nút | 08.04 |
| **Nút slice** (Slice Knot) | - | Nút là biên của đĩa trong $B^4$ | 08.04 |
| **Phần bù nút** (Knot Complement) | $S^3 \setminus K$ | Không gian thu được bằng cách loại bỏ nút | 08.04 |
| **Phẫu thuật Dehn** (Dehn Surgery) | - | Phương pháp tạo 3-manifold từ nút | 08.04 |

---

## 📚 Chapter 09: Topology Đại Chúng

### Khái Niệm Cơ Bản

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đồng phôi** (Homeomorphism) | $X \cong Y$ | Song ánh liên tục với hàm ngược liên tục | 09.00 |
| **Biến dạng liên tục** (Continuous Deformation) | - | Biến đổi không cắt hoặc dán | 09.00 |
| **Lỗ** (Hole) | - | Đặc trưng topology của không gian | 09.00 |
| **Đồ thị** (Graph) | $G = (V, E)$ | Tập đỉnh và cạnh | 09.01 |
| **Đường Euler** (Euler Path) | - | Đường đi qua mỗi cạnh đúng một lần | 09.01 |
| **Mặt Möbius** (Möbius Strip) | - | Mặt không định hướng với một mặt | 09.02 |
| **Định hướng** (Orientability) | - | Tính chất có thể định hướng | 09.02 |
| **Đặc trưng Euler** (Euler Characteristic) | $\chi = V - E + F$ | Bất biến topology | 09.03 |
| **Định lý bốn màu** (Four Color Theorem) | - | Mọi bản đồ phẳng có thể tô bằng 4 màu | 09.04 |
| **Phân tích dữ liệu tô-pô** (TDA) | - | Phương pháp phân tích dữ liệu bằng topology | 09.07 |
| **Đồng điều bền vững** (Persistent Homology) | - | Homology theo tham số | 09.07 |
| **Giả thuyết Poincaré** (Poincaré Conjecture) | - | Định lý về 3-manifold đơn liên | 09.08 |

---

## 🎯 Ký Hiệu Toán Học Thường Dùng

| Ký Hiệu | Ý Nghĩa | Ví Dụ |
|---------|---------|-------|
| $\mathbb{R}$ | Số thực | $\mathbb{R}^n$ - không gian Euclid $n$-chiều |
| $\mathbb{Z}$ | Số nguyên | $\pi_1(S^1) \cong \mathbb{Z}$ |
| $\mathbb{Q}$ | Số hữu tỉ | - |
| $\mathbb{N}$ | Số tự nhiên | - |
| $\emptyset$ | Tập rỗng | - |
| $\in$ | Thuộc về | $x \in A$ |
| $\subseteq$ | Tập con | $A \subseteq B$ |
| $\cup$ | Hợp | $A \cup B$ |
| $\cap$ | Giao | $A \cap B$ |
| $\setminus$ | Hiệu | $A \setminus B$ |
| $\times$ | Tích Descartes | $X \times Y$ |
| $\cong$ | Đẳng cấu | $X \cong Y$ |
| $\simeq$ | Tương đương đồng luân | $X \simeq Y$ |
| $\to$ | Ánh xạ | $f: X \to Y$ |
| $\hookrightarrow$ | Nhúng | $X \hookrightarrow Y$ |
| $\partial$ | Biên | $\partial A$, $\partial_n$ |
| $\pi$ | Ánh xạ chiếu hoặc số pi | $\pi: X \to X/\sim$, $\pi_1(X)$ |
| $\sim$ | Quan hệ tương đương | $x \sim y$ |
| $S^n$ | Hình cầu $n$-chiều | $S^1$ - đường tròn |
| $D^n$ | Quả cầu đóng $n$-chiều | $D^2$ - đĩa |
| $B^n$ | Quả cầu mở $n$-chiều | - |
| $T^n$ | Torus $n$-chiều | $T^2$ - torus |
| $\mathbb{R}P^n$ | Không gian xạ ảnh thực $n$-chiều | - |
| $\mathbb{C}P^n$ | Không gian xạ ảnh phức $n$-chiều | - |

---

## 📝 Ghi Chú

**Cách sử dụng bảng:**

1. **Tra cứu theo chương:** Tìm thuật ngữ trong chương tương ứng
2. **Tra cứu theo ký hiệu:** Sử dụng bảng ký hiệu để tìm ý nghĩa
3. **Tra cứu theo tên:** Tìm kiếm theo tên tiếng Việt hoặc tiếng Anh

**Lưu ý:**

- Một số thuật ngữ xuất hiện ở nhiều chương khác nhau
- Các định nghĩa ở đây là ngắn gọn, chi tiết hơn xem trong các bài học cụ thể
- Ký hiệu có thể khác nhau tùy theo tài liệu, nhưng đã được chuẩn hóa trong khóa học này

---

## 🧠 Fundamental Papers & References

### Tài Liệu Tham Khảo Chính

1. **James R. Munkres** - *Topology*, 2nd Ed.  
   *Giáo trình kinh điển về topology*

2. **Sidney A. Morris** - *Topology without Tears*  
   *Giáo trình dễ tiếp cận*

3. **Colin Adams & Robert Franzosa** - *Introduction to Topology: Pure and Applied*  
   *Kết hợp lý thuyết và ứng dụng*

4. **Allen Hatcher** - *Algebraic Topology*  
   *Giáo trình về topology đại số*

5. **W.B. Raymond Lickorish** - *An Introduction to Knot Theory*  
   *Giáo trình về lý thuyết nút*

---

## 🔗 Applications and Connections

Từ điển này tổng hợp các thuật ngữ từ toàn bộ khóa học topology, từ các khái niệm cơ bản nhất về tập hợp và không gian tô-pô đến các chủ đề nâng cao như lý thuyết nút và topology đại số. Việc hiểu và sử dụng đúng các thuật ngữ này là nền tảng quan trọng để nghiên cứu sâu hơn về topology và các ứng dụng của nó.

---

## 🧩 Exercises and Reflections

### Câu hỏi suy ngẫm

1. **Tra cứu:** Hãy tìm định nghĩa của một thuật ngữ cụ thể mà bạn quan tâm.

2. **Phân loại:** Hãy phân loại các thuật ngữ theo các nhóm: định nghĩa cơ bản, định lý, kỹ thuật tính toán, ứng dụng.

3. **Liên kết:** Hãy tìm các thuật ngữ liên quan đến nhau và giải thích mối liên hệ giữa chúng.

4. **Mở rộng:** Hãy tìm hiểu thêm về các thuật ngữ mà bạn chưa hiểu rõ từ các bài học tương ứng.

### Thử nghiệm thực tế

1. **Tạo từ điển cá nhân:** Hãy tạo một từ điển riêng với các ví dụ và giải thích của bạn.

2. **Ôn tập:** Sử dụng từ điển này để ôn tập lại các khái niệm đã học.

3. **Tham khảo:** Sử dụng từ điển này khi đọc các bài học khác để hiểu các thuật ngữ mới.

---

## 📚 Tóm tắt

Từ điển này là một công cụ tham khảo quan trọng cho toàn bộ khóa học topology. Nó tổng hợp:

- **Hơn 200 thuật ngữ toán học** từ các chương khác nhau
- **Các ký hiệu toán học** thường dùng
- **Định nghĩa ngắn gọn** cho mỗi thuật ngữ
- **Tham chiếu chương** để tìm hiểu chi tiết hơn

Sử dụng từ điển này một cách hiệu quả sẽ giúp bạn nắm vững các khái niệm topology và áp dụng chúng trong nghiên cứu và ứng dụng thực tế!

