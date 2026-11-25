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

**Từ điển thuật ngữ toán học — Tổng hợp toàn khóa**

---

**Lưu ý hiển thị công thức:** Các công thức trong bảng được viết bằng LaTeX và hiển thị qua MathJax. Nếu công thức chưa hiển thị đúng, hãy kiểm tra cấu hình tải MathJax của trình duyệt hoặc trang web.

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu ví toàn bộ khóa học tô-pô từ Chương 00 đến Chương 09 như một chuyến thám hiểm qua nhiều vùng đất — từ tập mở, compact, nhóm cơ bản đến đồng điều, bó thớ và đa tạp — thì bài **09.10** chính là **cuốn la bàn và từ điển song ngữ** giúp bạn không bao giờ lạc đường giữa hàng trăm thuật ngữ Anh–Việt. Thay vì học thuộc lòng rời rạc từng dòng, hãy xem **Bản đồ 3 tầng ngôn ngữ** và **Ví dụ kiểm tra toàn khóa trên hình xuyến $$T^2$$** dưới đây để thấy mọi thuật ngữ trong bảng thực ra ăn khớp với nhau chặt chẽ như một cỗ máy đồng hồ!

Bài học này tổng hợp các thuật ngữ và ký hiệu toán học cốt lõi đã xuất hiện trong toàn bộ khóa học tô-pô, được phân nhóm theo từng chương và chủ đề để thuận tiện tra cứu nhanh, ôn tập và đối chiếu song ngữ Anh – Việt.

Mỗi bảng gồm bốn cột:
- **Thuật ngữ** (tiếng Việt và tiếng Anh tương ứng).
- **Ký hiệu toán học** (nếu có).
- **Định nghĩa ngắn gọn.**
- **Bài học xuất hiện.**

---

## 🗺️ Kiến thức cần nhớ: Kiến trúc 3 tầng của hệ thuật ngữ Tô-pô toàn khóa

Toàn bộ các bảng thuật ngữ bên dưới được tổ chức theo đúng 3 tầng xây dựng của tô-pô học hiện đại:

### 1. Tầng 1 — Tô-pô Tập hợp (Chương 00–04): Ngôn ngữ của Lân cận và Hội tụ
- **Khái niệm cốt lõi:** Tập mở $$\tau$$, tập đóng, phần trong, bao đóng, hàm liên tục, phép đồng phôi, tô-pô tích, tô-pô thương, các tiên đề tách ($$T_0 \dots T_4$$, Hausdorff), tính liên thông và tính compact.
- **Vai trò:** Thiết lập nền móng chặt chẽ để nói về "gần nhau" và "biến dạng liên tục" mà không cần đến khoảng cách Euclid.

### 2. Tầng 2 — Tô-pô Đại số (Chương 05–08): Dịch Hình học sang Đại số
- **Khái niệm cốt lõi:** Đồng luân, nhóm cơ bản $$\pi_1(X)$$, không gian phủ, phức CW, nhóm đồng điều $$H_n(X)$$, đối đồng điều $$H^n(X)$$ với tích cup $$\cup$$, và nhóm đồng luân bậc cao $$\pi_n(X)$$.
- **Vai trò:** Biến bài toán khó "hai không gian có đồng phôi không?" thành bài toán đại số kiểm tra được "hai nhóm/vành có đẳng cấu không?".

### 3. Tầng 3 — Tô-pô Hình học & Vi phân (Chương 08–09): Đa tạp, Bó thớ, Morse và Nút
- **Khái niệm cốt lõi:** Đa tạp tô-pô/trơn, tập bản đồ (atlas), bó thớ, bó vectơ, lớp đặc trưng, hàm Morse, lý thuyết nút và đặc trưng Euler $$\chi$$.
- **Vai trò:** Kết nối trực tiếp tô-pô với hình học vi phân, vật lý lý thuyết, sinh học DNA và khoa học dữ liệu (TDA/TDL).

---

## 🧮 Ví dụ tính tay làm từng bước: "Khám sức khỏe" toàn bộ 3 tầng thuật ngữ trên Hình xuyến $$T^2 = S^1 \times S^1$$

Để thực hành tra cứu từ điển hiệu quả nhất, hãy chọn đúng **một** không gian quen thuộc là **hình xuyến $$T^2 = S^1 \times S^1$$** và tự kiểm chứng 6 nhãn thuật ngữ đại diện cho cả 3 tầng:

1. **Tô-pô tập hợp (Chương 01–04):** Vì $$S^1$$ là tập đóng, bị chặn trong $$\mathbb{R}^2$$ nên $$S^1$$ **Hausdorff**, **compact** và **liên thông**. Theo định lý Tychonoff và tính bảo toàn tích hữu hạn, $$T^2 = S^1 \times S^1$$ lập tức kế thừa cả 3 tính chất: **Hausdorff, compact, liên thông**!
2. **Tô-pô thương (Chương 02):** $$T^2 \cong [0,1]^2 / \sim$$ với $$(0,y)\sim(1,y)$$ và $$(x,0)\sim(x,1)$$ (1 đỉnh $$V=1$$, 2 cạnh $$E=2$$, 1 mặt $$F=1$$).
3. **Nhóm cơ bản (Chương 05):** $$\pi_1(T^2) \cong \pi_1(S^1) \times \pi_1(S^1) \cong \mathbb{Z} \times \mathbb{Z}$$ (giao hoán, khác $$0 \implies$$ **không đơn liên**!).
4. **Đồng điều & Số Betti (Chương 07):** $$H_0(T^2) \cong \mathbb{Z},\; H_1(T^2) \cong \mathbb{Z}^2,\; H_2(T^2) \cong \mathbb{Z}$$ ($$\beta_0=1, \beta_1=2, \beta_2=1$$), cho đặc trưng Euler $$\chi(T^2) = 1 - 2 + 1 = 0$$ (khớp y hệt $$V - E + F = 1 - 2 + 1 = 0$$!).
5. **Đối đồng điều & Tích cup (Chương 07.04):** Hai phần tử sinh $$\alpha, \beta \in H^1(T^2)$$ có $$\alpha \cup \beta \neq 0 \in H^2(T^2)$$ — chứng minh ngay $$T^2 \not\simeq S^1 \vee S^1 \vee S^2$$ dù có cùng mọi nhóm đồng điều!
6. **Đa tạp & Morse (Chương 08):** $$T^2$$ là **đa tạp trơn 2 chiều đóng định hướng được**; hàm chiều cao chuẩn có đúng 4 điểm tới hạn chỉ số $$(0, 1, 1, 2)$$ khớp tuyệt đối các số Betti!

### Giải thích: Cách dùng từ điển thuật ngữ để tự học hiệu quả

#### Bước 1: Luôn đọc thuật ngữ theo cặp song ngữ Việt – Anh
Phần lớn tài liệu nghiên cứu và sách kinh điển (Munkres, Hatcher, Lee, Milnor) viết bằng tiếng Anh; ghi nhớ song song (ví dụ *homeomorphism* = đồng phôi, *homotopy* = đồng luân, *covering space* = không gian phủ) giúp bạn đọc thẳng giáo trình gốc không bị vấp.

#### Bước 2: Gắn mỗi thuật ngữ với 1 ví dụ đúng và 1 phản ví dụ
Ví dụ: nhắc đến *Hausdorff* nhớ ngay $$\mathbb{R}$$ (đúng) vs. *đường thẳng hai gốc* (sai); nhắc đến *compact* nhớ ngay $$[0,1]$$ (đúng) vs. $$(0,1)$$ (sai).

#### Bước 3: Phân biệt các cặp thuật ngữ dễ nhầm lẫn
Kiểm tra kỹ các cặp kinh điển trong bảng: *tập mở* vs. *tập đóng* (không loại trừ nhau!), *đồng phôi* vs. *đồng luân*, *liên thông* vs. *liên thông đường*, *đồng điều* vs. *đối đồng điều*.

#### Bước 4: Tra ngược về bài học gốc qua cột "Chương"
Cột ngoài cùng bên phải của mỗi bảng chỉ chính xác số bài học nơi khái niệm ra đời — hãy dùng nó như mục lục ngược mỗi khi gặp lại một ký hiệu lạ!

---

## 📚 Chương 00: Nền tảng và Tô-pô tập hợp

### Lý thuyết tập hợp

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tập hợp** (Set) | $A$, $B$, $X$ | Một tập hợp các đối tượng phân biệt | 00.00 |
| **Phần tử** (Element) | $x \in A$ | Một đối tượng thuộc tập hợp | 00.00 |
| **Tập con** (Subset) | $A \subseteq B$ | Mọi phần tử của $A$ đều thuộc $B$ | 00.00 |
| **Tập rỗng** (Empty Set) | $\emptyset$ | Tập hợp không chứa phần tử nào | 00.00 |
| **Hợp** (Union) | $A \cup B$ | Tập tất cả phần tử thuộc $A$ hoặc thuộc $B$ | 00.00 |
| **Giao** (Intersection) | $A \cap B$ | Tập tất cả phần tử thuộc cả $A$ và $B$ | 00.00 |
| **Hiệu** (Difference) | $A \setminus B$ | Tập các phần tử thuộc $A$ nhưng không thuộc $B$ | 00.00 |
| **Phần bù** (Complement) | $A^c$ | Tập tất cả phần tử không thuộc $A$ | 00.00 |
| **Tích Descartes** (Cartesian Product) | $A \times B$ | Tập các cặp có thứ tự $(a,b)$ với $a \in A$, $b \in B$ | 00.01 |
| **Lực lượng** (Cardinality) | $|A|$, $\mathrm{card}(A)$ | Quy mô (số lượng phần tử) của tập hợp | 00.00 |
| **Đếm được** (Countable) | $\aleph_0$ | Hữu hạn hoặc có thể đặt tương ứng 1-1 với $\mathbb{N}$ (vô hạn đếm được có lực lượng $\aleph_0$) | 00.00 |
| **Không đếm được** (Uncountable) | $2^{\aleph_0}$ | Vô hạn và không thể đặt tương ứng 1-1 với $\mathbb{N}$ (ví dụ $|\mathbb{R}| = 2^{\aleph_0}$) | 00.00 |

### Hàm số và quan hệ

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Hàm số / Ánh xạ** (Function) | $f: A \to B$ | Quy tắc gán mỗi phần tử của $A$ với đúng một phần tử của $B$ | 00.00 |
| **Đơn ánh** (Injective) | $f$ injective | $f(a_1) = f(a_2) \Rightarrow a_1 = a_2$ | 00.00 |
| **Toàn ánh** (Surjective) | $f$ surjective | Mọi $b \in B$ đều tồn tại $a \in A$ sao cho $f(a) = b$ | 00.00 |
| **Song ánh** (Bijective) | $f$ bijective | Ánh xạ vừa đơn ánh vừa toàn ánh | 00.00 |
| **Hàm ngược** (Inverse Function) | $f^{-1}$ | Ánh xạ ngược của một song ánh | 00.00 |
| **Quan hệ tương đương** (Equivalence Relation) | $\sim$ | Quan hệ thỏa mãn tính phản xạ, đối xứng và bắc cầu | 00.00 |
| **Lớp tương đương** (Equivalence Class) | $[a]$ | Tập tất cả phần tử tương đương với $a$ | 00.00 |
| **Phân hoạch** (Partition) | - | Sự chia tập hợp thành các tập con khác rỗng, đôi một rời nhau | 00.00 |

### Tiên đề và logic

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tiên đề chọn** (Axiom of Choice) | AC | Có thể chọn đồng thời một phần tử từ mỗi tập hợp khác rỗng trong một họ bất kỳ | 00.01 |
| **Bổ đề Zorn** (Zorn's Lemma) | - | Nếu mọi xích trong tập sắp thứ tự bộ phận đều có chặn trên thì tập đó có phần tử tối đại | 00.01 |
| **Nguyên lý sắp thứ tự tốt** (Well-Ordering Principle) | - | Mọi tập hợp đều có thể trang bị một thứ tự tốt | 00.01 |
| **Quy nạp toán học** (Mathematical Induction) | - | Phương pháp chứng minh mệnh đề đúng với mọi số tự nhiên | 00.02 |
| **Phản chứng** (Proof by Contradiction) | - | Giả sử điều phủ định là đúng rồi suy ra mâu thuẫn | 00.02 |

### Số thực và không gian Euclid

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Số thực** (Real Numbers) | $\mathbb{R}$ | Tập hợp tất cả các số thực | 00.03 |
| **Không gian Euclid** (Euclidean Space) | $\mathbb{R}^n$ | Không gian $n$-chiều trang bị metric Euclid | 00.03 |
| **Tính đầy đủ** (Completeness) | - | Mọi dãy Cauchy đều hội tụ trong không gian | 00.03 |
| **Lát cắt Dedekind** (Dedekind Cut) | - | Phương pháp xây dựng $\mathbb{R}$ từ $\mathbb{Q}$ | 00.03 |

---

## 📚 Chương 01: Không gian tô-pô và hàm liên tục

### Không gian tô-pô

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Không gian tô-pô** (Topological Space) | $(X, \tau)$ | Tập hợp $X$ trang bị một tô-pô $\tau$ | 01.00 |
| **Tô-pô** (Topology) | $\tau$ | Họ các tập con mở của $X$ thỏa mãn ba tiên đề tô-pô | 01.00 |
| **Tập mở** (Open Set) | $U \in \tau$ | Một phần tử thuộc họ tô-pô $\tau$ | 01.00 |
| **Tập đóng** (Closed Set) | $A$ closed | Tập con có phần bù là tập mở | 01.02 |
| **Tô-pô tầm thường** (Trivial Topology) | $\{\emptyset, X\}$ | Tô-pô thô nhất trên $X$ | 01.00 |
| **Tô-pô rời rạc** (Discrete Topology) | $\mathcal{P}(X)$ | Tô-pô mịn nhất (mọi tập con của $X$ đều mở) | 01.00 |
| **Tô-pô đồng hữu hạn** (Cofinite Topology) | - | Tập mở là $\emptyset$ hoặc tập có phần bù hữu hạn | 01.00 |
| **Tô-pô đồng đếm được** (Cocountable Topology) | - | Tập mở là $\emptyset$ hoặc tập có phần bù đếm được | 01.00 |
| **Thô hơn** (Coarser) | $\tau_1 \subseteq \tau_2$ | Tô-pô chứa ít tập mở hơn | 01.00 |
| **Mịn hơn** (Finer) | $\tau_2 \supseteq \tau_1$ | Tô-pô chứa nhiều tập mở hơn | 01.00 |

### Cơ sở và tiền cơ sở

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Cơ sở** (Basis) | $\mathcal{B}$ | Họ tập mở mà mọi tập mở đều là hợp của các phần tử thuộc họ đó | 01.01 |
| **Tiền cơ sở** (Subbasis) | $\mathcal{S}$ | Họ tập hợp mà các giao hữu hạn của chúng tạo thành một cơ sở | 01.01 |
| **Cơ sở chuẩn** (Standard Basis) | - | Cơ sở các quả cầu mở sinh ra tô-pô chuẩn trên $\mathbb{R}^n$ | 01.01 |

### Bao đóng và phần trong

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Bao đóng** (Closure) | $\overline{A}$, $\mathrm{cl}(A)$ | Tập đóng nhỏ nhất chứa $A$ | 01.02 |
| **Phần trong** (Interior) | $A^\circ$, $\mathrm{int}(A)$ | Tập mở lớn nhất chứa trong $A$ | 01.02 |
| **Biên** (Boundary) | $\partial A$ | Tập hiệu $\overline{A} \setminus A^\circ$ | 01.02 |
| **Điểm tụ / Điểm giới hạn** (Limit Point) | - | Điểm mà mọi lân cận của nó đều chứa ít nhất một điểm khác của $A$ | 01.02 |
| **Điểm cô lập** (Isolated Point) | - | Điểm thuộc $A$ có một lân cận không chứa điểm nào khác của $A$ | 01.02 |

### Hàm liên tục và đồng phôi

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Hàm liên tục** (Continuous Function) | $f: X \to Y$ | Nghịch ảnh của mọi tập mở trong $Y$ là tập mở trong $X$ | 01.03 |
| **Đồng phôi** (Homeomorphism) | $f: X \cong Y$ | Song ánh liên tục có ánh xạ ngược liên tục | 01.03 |
| **Phép nhúng** (Embedding) | $f: X \hookrightarrow Y$ | Ánh xạ liên tục là đồng phôi từ $X$ lên ảnh $f(X)$ | 01.03 |
| **Tương đương đồng luân** (Homotopy Equivalence) | $X \simeq Y$ | Tồn tại hai ánh xạ liên tục có tích hợp thành đồng luân với ánh xạ đồng nhất | 06.00 |

### Tô-pô con và tô-pô tích

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tô-pô con** (Subspace Topology) | $Y \subseteq X$ | Tô-pô cảm sinh trên tập con $Y$ bằng cách giao với các tập mở của $X$ | 01.04 |
| **Tô-pô tích** (Product Topology) | $X \times Y$ | Tô-pô thô nhất trên tích Descartes làm các phép chiếu liên tục | 01.04 |
| **Ánh xạ chiếu** (Projection) | $\pi_i: X_1 \times X_2 \to X_i$ | Ánh xạ chiếu lên thành phần thứ $i$ | 01.04 |

---

## 📚 Chương 02: Tính liên thông và tính compact

### Tính liên thông

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Liên thông** (Connected) | - | Không thể biểu diễn thành hợp của hai tập mở khác rỗng, rời nhau | 02.00 |
| **Thành phần liên thông** (Connected Component) | - | Tập con liên thông lớn nhất chứa một điểm cho trước | 02.00 |
| **Liên thông đường** (Path-Connected) | - | Mọi cặp điểm đều nối được với nhau bằng một đường đi liên tục | 02.00 |
| **Thành phần liên thông đường** (Path Component) | - | Tập con liên thông đường lớn nhất chứa một điểm | 02.00 |
| **Đường đi** (Path) | $\gamma: [0,1] \to X$ | Ánh xạ liên tục từ đoạn $[0,1]$ vào không gian $X$ | 02.00 |
| **Vòng lặp** (Loop) | $\gamma: S^1 \to X$ | Đường đi khép kín có điểm đầu trùng điểm cuối | 06.01 |

### Tính compact

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Compact** | - | Mọi phủ mở đều trích ra được phủ con hữu hạn | 02.01 |
| **Phủ mở** (Open Cover) | $\{U_\alpha\}$ | Họ các tập mở có hợp chứa toàn bộ không gian | 02.01 |
| **Phủ con hữu hạn** (Finite Subcover) | - | Họ con hữu hạn vẫn phủ hết không gian | 02.01 |
| **Compact địa phương** (Locally Compact) | - | Mọi điểm đều có một lân cận compact | 02.02 |
| **Compact hóa** (Compactification) | $\hat{X}$ | Không gian compact chứa $X$ như một tập con trù mật | 02.02 |
| **Compact hóa một điểm** (One-Point Compactification) | $X^*$ | Bổ sung một điểm vô cực để tạo không gian compact | 02.02 |
| **Compact hóa Stone–Čech** (Stone–Čech Compactification) | $\beta X$ | Compact hóa Hausdorff lớn nhất (có tính phổ quát) | 02.02 |

---

## 📚 Chương 03: Các tiên đề tách

### Tiên đề tách

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Không gian $T_0$** (T0-space) | - | Với hai điểm phân biệt bất kỳ, có tập mở chứa điểm này nhưng không chứa điểm kia | 03.00 |
| **Không gian $T_1$** (T1-space) | - | Mọi tập đơn điểm đều là tập đóng | 03.00 |
| **Hausdorff** ($T_2$) | - | Mọi cặp điểm phân biệt đều có hai lân cận mở rời nhau | 03.00 |
| **Chính quy** (Regular / $T_3$) | - | Điểm và tập đóng không chứa nó luôn có hai lân cận mở rời nhau | 03.01 |
| **Chuẩn tắc** (Normal / $T_4$) | - | Mọi cặp tập đóng rời nhau đều có hai lân cận mở rời nhau | 03.01 |
| **Hoàn toàn chính quy** (Completely Regular) | $T_{3\frac{1}{2}}$ | $T_1$ và tách được điểm với tập đóng bằng hàm liên tục vào $[0,1]$ | 03.01 |

### Tiên đề đếm được

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đếm được thứ nhất** (First Countable) | - | Mọi điểm đều có một cơ sở lân cận đếm được | 03.02 |
| **Đếm được thứ hai** (Second Countable) | - | Không gian có một cơ sở tô-pô đếm được | 03.02 |
| **Tách được** (Separable) | - | Chứa một tập con đếm được trù mật | 03.02 |
| **Lindelöf** | - | Mọi phủ mở đều có phủ con đếm được | 03.02 |

### Định lý metric hóa

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Metric hóa được** (Metrizable) | - | Tồn tại một metric sinh ra đúng tô-pô của không gian | 03.03 |
| **Định lý metric hóa Urysohn** | - | Không gian chính quy ($T_3$) và đếm được thứ hai $\Rightarrow$ metric hóa được | 03.03 |
| **Bổ đề Urysohn** (Urysohn's Lemma) | - | Trong không gian chuẩn tắc, hai tập đóng rời nhau tách được bằng hàm liên tục | 03.01 |
| **Định lý mở rộng Tietze** | - | Hàm liên tục trên tập con đóng của không gian chuẩn tắc mở rộng được ra toàn không gian | 03.01 |

---

## 📚 Chương 04: Không gian metric

### Không gian metric

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Metric** (Khoảng cách) | $d: X \times X \to \mathbb{R}$ | Hàm khoảng cách thỏa mãn tính không âm–xác định, đối xứng và bất đẳng thức tam giác | 04.00 |
| **Không gian metric** (Metric Space) | $(X, d)$ | Tập hợp $X$ trang bị metric $d$ | 04.00 |
| **Quả cầu mở** (Open Ball) | $B(x, r)$ | $\{y : d(x,y) < r\}$ | 04.00 |
| **Quả cầu đóng** (Closed Ball) | $\overline{B}(x, r)$ | $\{y : d(x,y) \leq r\}$ | 04.00 |
| **Metric Euclid** (Euclidean Metric) | $d_2$ | $\sqrt{\sum (x_i - y_i)^2}$ | 04.00 |
| **Metric Manhattan** (Manhattan Metric) | $d_1$ | $\sum |x_i - y_i|$ | 04.00 |
| **Metric cực đại** (Maximum Metric) | $d_\infty$ | $\max |x_i - y_i|$ | 04.00 |
| **Metric rời rạc** (Discrete Metric) | $d_{\mathrm{disc}}$ | $d(x,y) = 1$ nếu $x \neq y$, bằng $0$ nếu $x = y$ | 04.00 |

### Tính đầy đủ và định lý Baire

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Dãy Cauchy** (Cauchy Sequence) | $(x_n)$ | $\forall \epsilon > 0, \exists N: m,n \geq N \Rightarrow d(x_m, x_n) < \epsilon$ | 04.01 |
| **Đầy đủ** (Complete) | - | Mọi dãy Cauchy đều hội tụ | 04.01 |
| **Hoàn thiện** (Completion) | $\hat{X}$ | Không gian metric đầy đủ chứa $X$ đẳng cự và trù mật | 04.01 |
| **Không đâu trù mật** (Nowhere Dense) | - | Tập con có phần trong của bao đóng bằng rỗng | 04.01 |
| **Tập gầy / Phạm trù thứ nhất** (Meager / First Category) | - | Hợp đếm được các tập không đâu trù mật | 04.01 |
| **Tập không gầy / Phạm trù thứ hai** (Nonmeager / Second Category) | - | Tập không phải tập gầy | 04.01 |
| **Định lý phạm trù Baire** (Baire Category Theorem) | - | Không gian metric đầy đủ khác rỗng thuộc phạm trù thứ hai | 04.01 |

### Tính liên tục đều

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Liên tục đều** (Uniformly Continuous) | - | $\forall \epsilon > 0, \exists \delta > 0: d(x,y) < \delta \Rightarrow d(f(x), f(y)) < \epsilon$ | 04.02 |
| **Ánh xạ Lipschitz** | - | $d(f(x), f(y)) \leq L \cdot d(x,y)$ | 04.02 |
| **Hằng số Lipschitz** (Lipschitz Constant) | $L$ | Hằng số chặn trên tỉ số khoảng cách trong điều kiện Lipschitz | 04.02 |
| **Ánh xạ co** (Contraction) | - | Ánh xạ Lipschitz với hằng số $L < 1$ | 04.02 |
| **Định lý điểm bất động Banach** | - | Mọi ánh xạ co trên không gian metric đầy đủ khác rỗng có đúng một điểm bất động | 04.02 |

### Metric tích và không gian hàm

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Metric tích** (Product Metric) | - | Metric cảm sinh trên tích các không gian metric | 04.03 |
| **Không gian hàm** (Function Space) | $C(X,Y)$ | Tập các ánh xạ liên tục từ $X$ vào $Y$ | 04.03 |
| **Metric đều** (Uniform Metric) | $d_\infty$ | $\sup_{x \in X} d(f(x), g(x))$ | 04.03 |
| **Hội tụ đều** (Uniform Convergence) | - | Sự hội tụ theo metric đều | 04.03 |
| **Hội tụ từng điểm** (Pointwise Convergence) | - | Sự hội tụ riêng lẻ tại mỗi điểm $x \in X$ | 04.03 |

---

## 📚 Chương 05: Không gian thương

### Tô-pô thương

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Quan hệ tương đương** (Equivalence Relation) | $\sim$ | Quan hệ phản xạ, đối xứng và bắc cầu | 05.00 |
| **Tập thương** (Quotient Set) | $X/\sim$ | Tập hợp các lớp tương đương của $X$ theo $\sim$ | 05.00 |
| **Tô-pô thương** (Quotient Topology) | - | Tô-pô mịn nhất trên $X/\sim$ làm ánh xạ chiếu liên tục | 05.00 |
| **Ánh xạ chiếu chính tắc** (Projection Map) | $\pi: X \to X/\sim$ | Ánh xạ gửi mỗi phần tử vào lớp tương đương của nó | 05.00 |
| **Ánh xạ thương** (Quotient Map) | $q: X \to Y$ | Toàn ánh thỏa mãn $U \subseteq Y$ mở $\iff q^{-1}(U)$ mở trong $X$ | 05.00 |

### Phân loại bề mặt

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Bề mặt** (Surface) | - | Đa tạp 2 chiều (thường xét trường hợp compact không biên) | 05.01 |
| **Định hướng được** (Orientable) | - | Có thể chọn định hướng liên tục và nhất quán trên toàn mặt | 05.01 |
| **Không định hướng được** (Non-orientable) | - | Không thể định hướng nhất quán trên toàn mặt | 05.01 |
| **Giống** (Genus) | $g$ | Số lỗ (tay cầm) của bề mặt đóng định hướng được | 05.01 |
| **Đặc trưng Euler** (Euler Characteristic) | $\chi$ | Bất biến $V - E + F$ | 05.01 |
| **Tổng liên thông** (Connected Sum) | $\#$ | Phép ghép hai bề mặt bằng cách khoét đĩa rồi dán dọc theo biên | 05.01 |
| **Đa giác cơ bản** (Fundamental Polygon) | - | Biểu diễn một bề mặt đóng bằng cách dán các cạnh của một đa giác | 05.01 |

### Phức CW

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Phức CW** (CW Complex) | - | Không gian xây dựng bằng cách gắn tuần tự các tế bào (cell) theo chiều tăng dần | 05.02 |
| **Tế bào $n$-chiều** ($n$-cell) | $e^n$ | Không gian đồng phôi với quả cầu mở $n$-chiều | 05.02 |
| **Khung $n$-chiều** ($n$-Skeleton) | $X^n$ | Phức con gồm toàn bộ các tế bào có chiều $\leq n$ | 05.02 |
| **Ánh xạ gắn** (Attaching Map) | $\phi: S^{n-1} \to X^{n-1}$ | Ánh xạ liên tục gắn biên của $n$-tế bào vào khung $(n-1)$-chiều | 05.02 |

### Tác động nhóm

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tác động nhóm** (Group Action) | $G \curvearrowright X$ | Ánh xạ $G \times X \to X$ thỏa mãn tiên đề kết hợp và phần tử đơn vị | 05.03 |
| **Quỹ đạo** (Orbit) | $G \cdot x$ | Tập $\{g \cdot x : g \in G\}$ | 05.03 |
| **Nhóm ổn định / Đẳng hướng** (Stabilizer) | $G_x$ | Nhóm con $\{g \in G : g \cdot x = x\}$ | 05.03 |
| **Không gian quỹ đạo** (Orbit Space) | $X/G$ | Tập các quỹ đạo trang bị tô-pô thương | 05.03 |

---

## 📚 Chương 06: Nhóm cơ bản

### Đồng luân

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đồng luân** (Homotopy) | $F: X \times [0,1] \to Y$ | Biến dạng liên tục từ ánh xạ này sang ánh xạ khác | 06.00 |
| **Đồng luân đường** (Path Homotopy) | $\gamma \simeq_p \delta$ | Đồng luân giữa hai đường đi giữ cố định hai đầu mút | 06.00 |
| **Lớp đồng luân** (Homotopy Class) | $[\gamma]$ | Tập các đường đi đồng luân đường với $\gamma$ | 06.00 |
| **Co được** (Contractible) | - | Tương đương đồng luân với một điểm | 06.00 |
| **Rút đồng luân** (Deformation Retract) | - | Phép đồng luân rút liên tục không gian về một không gian con | 06.00 |

### Nhóm cơ bản

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Nhóm cơ bản** (Fundamental Group) | $\pi_1(X, x_0)$ | Nhóm các lớp đồng luân của các vòng lặp tại điểm cơ sở $x_0$ | 06.01 |
| **Điểm cơ sở** (Basepoint) | $x_0$ | Điểm cố định làm đầu và cuối cho các vòng lặp | 06.01 |
| **Ghép nối đường** (Concatenation) | $\gamma \cdot \delta$ | Đi hết đường $\gamma$ rồi nối tiếp bằng đường $\delta$ | 06.01 |
| **Đường đi ngược** (Inverse Path) | $\gamma^{-1}$ | Đường đi ngược chiều từ cuối về đầu của $\gamma$ | 06.01 |
| **Vòng lặp hằng** (Constant Loop) | $e_{x_0}$ | Vòng lặp đứng yên tại $x_0$ (phần tử đơn vị của $\pi_1$) | 06.01 |
| **Chỉ số vòng quay** (Winding Number) | - | Số vòng quấn có hướng quanh một điểm | 06.02 |

### Không gian phủ

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Không gian phủ** (Covering Space) | $\tilde{X}$ | Không gian đi kèm một ánh xạ phủ lên $X$ | 06.03 |
| **Ánh xạ phủ** (Covering Map) | $p: \tilde{X} \to X$ | Toàn ánh liên tục phủ đều địa phương | 06.03 |
| **Nâng ánh xạ** (Lift) | $\tilde{f}$ | Ánh xạ lên $\tilde{X}$ sao cho $p \circ \tilde{f} = f$ | 06.03 |
| **Không gian phủ phổ quát** (Universal Cover) | - | Không gian phủ đơn liên | 06.03 |
| **Phép biến đổi tầng** (Deck Transformation) | - | Tự đồng phôi của $\tilde{X}$ giao hoán với ánh xạ phủ $p$ | 06.03 |

### Định lý Seifert–Van Kampen

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Tích tự do** (Free Product) | $G * H$ | Tích tự do của hai nhóm $G$ và $H$ | 06.04 |
| **Tích tự do hợp nhất** (Amalgamated Free Product) | $G *_K H$ | Tích tự do đồng nhất hóa hai bản sao của nhóm con $K$ | 06.04 |
| **Định lý Seifert–Van Kampen** | - | Công cụ tính $\pi_1$ của không gian từ hai mảnh mở phủ nó | 06.04 |
| **Tổng nêm** (Wedge Sum) | $X \vee Y$ | Ghép hai không gian có điểm cơ sở tại đúng một điểm chung | 06.04 |

---

## 📚 Chương 07: Lý thuyết đồng điều

### Đồng điều đơn hình

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **$n$-đơn hình** ($n$-Simplex) | $\sigma = [v_0, \ldots, v_n]$ | Bao lồi của $n+1$ điểm độc lập afin | 07.00 |
| **Mặt của đơn hình** (Face) | $\partial_i \sigma$ | Đơn hình con thu được khi bỏ đỉnh $v_i$ | 07.00 |
| **Phức đơn hình** (Simplicial Complex) | $K$ | Tập các đơn hình đóng với phép lấy mặt và giao theo mặt chung | 07.00 |
| **Thực hóa hình học** (Geometric Realization) | $|K|$ | Không gian tô-pô tương ứng với phức đơn hình $K$ | 07.00 |
| **Nhóm dây chuyền** (Chain Group) | $C_n(K)$ | Nhóm Abel tự do sinh bởi các $n$-đơn hình | 07.00 |
| **Toán tử biên** (Boundary Operator) | $\partial_n: C_n \to C_{n-1}$ | Đồng cấu ánh xạ mỗi $n$-đơn hình sang tổng có dấu các mặt của nó | 07.00 |
| **Phức dây chuyền** (Chain Complex) | $(C_*, \partial_*)$ | Dãy các nhóm và toán tử biên thỏa mãn $\partial_{n-1} \circ \partial_n = 0$ | 07.00 |
| **Chu trình** (Cycle) | $Z_n = \ker(\partial_n)$ | Dây chuyền có biên bằng 0 | 07.00 |
| **Biên** (Boundary) | $B_n = \mathrm{im}(\partial_{n+1})$ | Dây chuyền là biên của một dây chuyền chiều cao hơn | 07.00 |
| **Nhóm đồng điều** (Homology Group) | $H_n(K) = Z_n / B_n$ | Nhóm thương của chu trình theo biên | 07.00 |
| **Số Betti** (Betti Number) | $\beta_n = \mathrm{rank}(H_n)$ | Hạng của phần tự do trong nhóm đồng điều bậc $n$ | 07.00 |

### Đồng điều kỳ dị

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đơn hình chuẩn** (Standard Simplex) | $\Delta^n$ | $n$-đơn hình chuẩn trong $\mathbb{R}^{n+1}$ | 07.01 |
| **Tọa độ trọng tâm** (Barycentric Coordinates) | $(t_0, \ldots, t_n)$ | Bộ tọa độ không âm có tổng bằng 1 trong đơn hình | 07.01 |
| **Ánh xạ mặt** (Face Map) | $\delta_i: \Delta^{n-1} \to \Delta^n$ | Ánh xạ nhúng vào mặt đối diện đỉnh thứ $i$ | 07.01 |
| **Ánh xạ suy biến** (Degeneracy Map) | $s_i: \Delta^{n+1} \to \Delta^n$ | Ánh xạ chiếu gộp hai đỉnh liên tiếp | 07.01 |
| **$n$-đơn hình kỳ dị** (Singular $n$-Simplex) | $\sigma: \Delta^n \to X$ | Ánh xạ liên tục từ đơn hình chuẩn vào không gian $X$ | 07.01 |
| **Nhóm dây chuyền kỳ dị** (Singular Chain Group) | $C_n(X)$ | Nhóm Abel tự do sinh bởi các $n$-đơn hình kỳ dị | 07.01 |
| **Đồng điều kỳ dị** (Singular Homology) | $H_n(X)$ | Đồng điều của phức dây chuyền kỳ dị | 07.01 |

### Dãy Mayer–Vietoris

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Dãy khớp** (Exact Sequence) | - | Dãy đồng cấu thỏa mãn $\mathrm{im} = \ker$ tại mỗi bước | 07.03 |
| **Dãy khớp ngắn** (Short Exact Sequence) | $0 \to A \to B \to C \to 0$ | Dãy khớp gồm năm hạng tử với hai đầu bằng $0$ | 07.03 |
| **Dãy Mayer–Vietoris** | - | Dãy khớp dài liên hệ đồng điều của $A \cup B$ với $A$, $B$ và $A \cap B$ | 07.03 |
| **Đồng cấu nối** (Connecting Homomorphism) | $\partial_*$ | Đồng cấu chuyển từ bậc $n$ sang bậc $n-1$ trong dãy khớp dài | 07.03 |

### Đối đồng điều (Cohomology)

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đối đồng điều** (Cohomology) | $H^n(X)$ | Bất biến đại số đối ngẫu với đồng điều | 07.04 |
| **Nhóm đối dây chuyền** (Cochain Group) | $C^n(X)$ | Nhóm đồng cấu $\mathrm{Hom}(C_n(X), \mathbb{Z})$ | 07.04 |
| **Toán tử đối biên** (Coboundary Operator) | $\delta: C^n \to C^{n+1}$ | Toán tử đối ngẫu của toán tử biên | 07.04 |
| **Tích cốc / Tích cup** (Cup Product) | $\cup$ | Phép nhân phân bậc trên đối đồng điều | 07.04 |
| **Vành đối đồng điều** (Cohomology Ring) | $H^*(X)$ | Cấu trúc vành của đối đồng điều với phép tích cup | 07.04 |

---

## 📚 Chương 08: Các chủ đề nâng cao

### Nhóm đồng luân bậc cao

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Nhóm đồng luân bậc $n$** ($n$-th Homotopy Group) | $\pi_n(X, x_0)$ | Nhóm các lớp đồng luân của ánh xạ có điểm cơ sở $S^n \to X$ | 08.00 |
| **Bậc của ánh xạ** (Degree of a Map) | $\deg(f)$ | Số nguyên đặc trưng cho ánh xạ liên tục $S^n \to S^n$ | 08.00 |
| **Phân thớ Hopf** (Hopf Fibration) | $S^3 \to S^2$ | Phân thớ kinh điển của $S^3$ trên $S^2$ với thớ là $S^1$ | 08.00 |
| **Định lý treo Freudenthal** (Freudenthal Suspension Theorem) | - | Liên hệ giữa $\pi_n(X)$ và $\pi_{n+1}(\Sigma X)$ ở vùng ổn định | 08.00 |
| **Nhóm đồng luân ổn định** (Stable Homotopy Groups) | $\pi_k^s$ | Giới hạn ổn định của $\pi_{n+k}(S^n)$ khi $n$ đủ lớn | 08.00 |

### Phân thớ và bó vectơ

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Phân thớ / Bó sợi** (Fiber Bundle) | $E \to B$ | Không gian tầm thường địa phương có cấu trúc tích với thớ $F$ | 08.01 |
| **Không gian đáy** (Base Space) | $B$ | Không gian cơ sở của phân thớ | 08.01 |
| **Không gian toàn phần** (Total Space) | $E$ | Không gian tổng chứa toàn bộ các thớ | 08.01 |
| **Thớ / Sợi** (Fiber) | $F$ | Nghịch ảnh đồng phôi tại mỗi điểm trên đáy | 08.01 |
| **Tầm thường địa phương** (Locally Trivial) | - | Trên từng lân cận đủ nhỏ của đáy, phân thớ đồng phôi với tích $U \times F$ | 08.01 |
| **Hàm chuyển tiếp** (Transition Function) | - | Ánh xạ chuyển đổi tọa độ giữa hai tầm thường hóa địa phương chồng lấn | 08.01 |
| **Bó vectơ** (Vector Bundle) | - | Phân thớ mà mỗi thớ là một không gian vectơ | 08.01 |
| **Bó tiếp tuyến** (Tangent Bundle) | $TM$ | Bó vectơ gồm các không gian tiếp tuyến tại mọi điểm của đa tạp $M$ | 08.01 |
| **Bó pháp tuyến** (Normal Bundle) | $\nu(M)$ | Bó vectơ của các vectơ pháp tuyến với đa tạp con $M$ | 08.01 |
| **Bó chính** (Principal Bundle) | - | Phân thớ với thớ là một nhóm Lie tác động tự do và bắc cầu | 08.01 |

### Lý thuyết Morse

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Hàm Morse** (Morse Function) | $f: M \to \mathbb{R}$ | Hàm trơn có mọi điểm tới hạn đều không suy biến | 08.02 |
| **Điểm tới hạn** (Critical Point) | - | Điểm tại đó vi phân $df = 0$ | 08.02 |
| **Chỉ số Morse** (Index) | $\lambda$ | Số giá trị riêng âm của ma trận Hessian tại điểm tới hạn | 08.02 |
| **Tập mức dưới** (Sublevel Set) | $M^a$ | Tập $\{x \in M : f(x) \leq a\}$ | 08.02 |
| **Bổ đề Morse** (Morse Lemma) | - | Biểu diễn dạng toàn phương chuẩn của hàm Morse gần điểm tới hạn | 08.02 |
| **Bất đẳng thức Morse** (Morse Inequalities) | - | Liên hệ số điểm tới hạn chỉ số $k$ với số Betti: $c_k \geq \beta_k$ | 08.02 |

### Đa tạp tô-pô

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đa tạp tô-pô** (Topological Manifold) | $M$ | Không gian Hausdorff, đếm được thứ hai và địa phương Euclid | 08.03 |
| **Bản đồ tọa độ** (Chart) | $(U, \phi)$ | Tập mở $U$ đi kèm đồng phôi $\phi$ vào tập mở của $\mathbb{R}^n$ | 08.03 |
| **Atlas** | - | Họ các bản đồ tọa độ phủ toàn bộ đa tạp | 08.03 |
| **Đa tạp trơn** (Smooth Manifold) | - | Đa tạp có atlas với các ánh xạ chuyển tọa độ khả vi vô hạn | 08.03 |
| **Đa tạp có biên** (Manifold with Boundary) | - | Không gian địa phương đồng phôi với nửa không gian đóng $\mathbb{H}^n$ | 08.03 |
| **Mặt cầu kỳ dị** (Exotic Sphere) | - | Đa tạp trơn đồng phôi nhưng không vi phôi với mặt cầu chuẩn $S^n$ | 08.03 |

### Lý thuyết nút

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Nút** (Knot) | $K: S^1 \to \mathbb{R}^3$ | Phép nhúng đường tròn $S^1$ vào không gian ba chiều | 08.04 |
| **Nút tầm thường / Nút không** (Unknot) | - | Nút tương đương với một đường tròn phẳng đơn giản | 08.04 |
| **Tương đương nút** (Knot Equivalence) | - | Hai nút tương đương qua đẳng luân xung quanh (ambient isotopy) | 08.04 |
| **Biến đổi Reidemeister** (Reidemeister Move) | RI, RII, RIII | Ba phép biến đổi địa phương cơ bản trên biểu đồ nút | 08.04 |
| **Mặt Seifert** (Seifert Surface) | $\Sigma$ | Bề mặt compact, liên thông, định hướng được có biên là nút $K$ | 08.04 |
| **Giống của nút** (Knot Genus) | $g(K)$ | Giống nhỏ nhất trong mọi mặt Seifert của nút $K$ | 08.04 |
| **Nhóm nút** (Knot Group) | $\pi_1(S^3 \setminus K)$ | Nhóm cơ bản của phần bù nút trong $S^3$ | 08.04 |
| **Đa thức Alexander** (Alexander Polynomial) | $\Delta_K(t)$ | Đa thức bất biến cổ điển của nút | 08.04 |
| **Đa thức Conway** (Conway Polynomial) | $\nabla_K(z)$ | Phiên bản chuẩn hóa của đa thức Alexander qua hệ thức skein | 08.04 |
| **Đa thức Jones** (Jones Polynomial) | $V_K(t)$ | Đa thức bất biến lượng tử phân biệt được nhiều nút đối xứng gương | 08.04 |
| **Ký số / Chữ ký** (Signature) | $\sigma(K)$ | Số nguyên bất biến tính từ dạng Seifert của nút | 08.04 |
| **Nút lát cắt** (Slice Knot) | - | Nút trong $S^3$ là biên của một đĩa nhúng trơn trong $B^4$ | 08.04 |
| **Phần bù nút** (Knot Complement) | $S^3 \setminus K$ | Không gian thu được khi bỏ nút $K$ khỏi $S^3$ | 08.04 |
| **Phẫu thuật Dehn** (Dehn Surgery) | - | Kỹ thuật khoét lân cận ống của nút rồi dán lại để tạo đa tạp 3 chiều | 08.04 |

---

## 📚 Chương 09: Tô-pô đại chúng

### Khái niệm cơ bản và ứng dụng

| Thuật Ngữ | Ký Hiệu | Định Nghĩa | Chương |
|-----------|---------|------------|--------|
| **Đồng phôi** (Homeomorphism) | $X \cong Y$ | Song ánh liên tục có ánh xạ ngược liên tục | 09.01 |
| **Biến dạng liên tục** (Continuous Deformation) | - | Biến đổi kéo giãn, uốn cong không cắt rời hay dán dính | 09.01 |
| **Lỗ** (Hole) | - | Đặc trưng tô-pô giúp phân loại bề mặt (liên hệ với genus) | 09.01 |
| **Đồ thị** (Graph) | $G = (V, E)$ | Tập các đỉnh và các cạnh nối giữa chúng | 09.02 |
| **Đường đi Euler** (Euler Path) | - | Đường đi qua mỗi cạnh của đồ thị đúng một lần | 09.02 |
| **Dải Möbius** (Möbius Strip) | - | Bề mặt không định hướng được chỉ có một mặt và một biên | 09.03 |
| **Tính định hướng** (Orientability) | - | Khả năng xác định nhất quán hai phía của một bề mặt | 09.03 |
| **Đặc trưng Euler** (Euler Characteristic) | $\chi = V - E + F$ | Bất biến tô-pô của đa diện và bề mặt | 09.04 |
| **Định lý bốn màu** (Four Color Theorem) | - | Mọi bản đồ phẳng đều tô được bằng tối đa 4 màu | 09.05 |
| **Phân tích dữ liệu tô-pô** (TDA) | - | Phương pháp phân tích hình dạng tập dữ liệu bằng công cụ tô-pô | 09.90 |
| **Đồng điều bền vững** (Persistent Homology) | - | Theo dõi sự xuất hiện và biến mất của các đặc trưng đồng điều qua nhiều tỉ lệ | 09.90 |
| **Giả thuyết Poincaré** (Poincaré Conjecture) | - | Mọi đa tạp 3 chiều đóng, đơn liên đều đồng phôi với $S^3$ | 09.08 |

---

## 🎯 Ký hiệu toán học thường dùng

| Ký Hiệu | Ý Nghĩa | Ví Dụ |
|---------|---------|-------|
| $\mathbb{R}$ | Tập số thực | $\mathbb{R}^n$ — không gian Euclid $n$-chiều |
| $\mathbb{Z}$ | Tập số nguyên | $\pi_1(S^1) \cong \mathbb{Z}$ |
| $\mathbb{Q}$ | Tập số hữu tỉ | - |
| $\mathbb{N}$ | Tập số tự nhiên | - |
| $\emptyset$ | Tập rỗng | - |
| $\in$ | Thuộc về | $x \in A$ |
| $\subseteq$ | Tập con | $A \subseteq B$ |
| $\cup$ | Hợp | $A \cup B$ |
| $\cap$ | Giao | $A \cap B$ |
| $\setminus$ | Hiệu hai tập hợp | $A \setminus B$ |
| $\times$ | Tích Descartes | $X \times Y$ |
| $\cong$ | Đồng phôi hoặc đẳng cấu | $X \cong Y$ |
| $\simeq$ | Tương đương đồng luân | $X \simeq Y$ |
| $\to$ | Ánh xạ | $f: X \to Y$ |
| $\hookrightarrow$ | Phép nhúng | $X \hookrightarrow Y$ |
| $\partial$ | Biên hoặc toán tử biên | $\partial A$, $\partial_n$ |
| $\pi$ | Ánh xạ chiếu hoặc nhóm đồng luân | $\pi: X \to X/\sim$, $\pi_1(X)$ |
| $\sim$ | Quan hệ tương đương | $x \sim y$ |
| $S^n$ | Mặt cầu $n$-chiều | $S^1$ — đường tròn |
| $D^n$ | Đĩa / khối cầu đóng $n$-chiều | $D^2$ — đĩa đóng |
| $B^n$ | Quả cầu mở $n$-chiều | - |
| $T^n$ | Mặt xuyến (torus) $n$-chiều | $T^2$ — mặt xuyến 2 chiều |
| $\mathbb{R}P^n$ | Không gian xạ ảnh thực $n$-chiều | - |
| $\mathbb{C}P^n$ | Không gian xạ ảnh phức $n$-chiều | - |

---

## 📝 Ghi chú tra cứu

- Một số thuật ngữ xuất hiện ở nhiều chương với mức độ khái quát khác nhau.
- Các định nghĩa trong bảng được viết cô đọng để tra nhanh; hãy xem lại bài học tương ứng khi cần phát biểu đầy đủ và ví dụ chứng minh.
- Ký hiệu có thể thay đổi tùy giáo trình, nhưng trong bảng này đã được thống nhất theo toàn khóa học.

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

## Video tham khảo

- **xem trước** [This open problem taught me what topology is](https://www.youtube.com/watch?v=IQqtsm-bBRU) — 3Blue1Brown, tiếng Anh. Một vòng các từ cơ bản: biến dạng, lỗ, mặt, trước khi tra từng mục glossary.
- [[TÔPÔ ĐẠI CƯƠNG] Không gian Tô pô: Định nghĩa và ví dụ.](https://www.youtube.com/watch?v=1LiNBmWl-S8) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Định nghĩa không gian tô-pô bằng tiếng Việt, khớp các mục chương 01.
- [Algebraic topology: Introduction](https://www.youtube.com/watch?v=K4f-lk9CMz8) — Richard E Borcherds, tiếng Anh. Borcherds mở đầu tô-pô đại số, khớp các mục nhóm cơ bản và đồng điều ở cuối bảng.

## 🧩 Bài tập và suy ngẫm

### Gợi ý ôn tập

1. Chọn năm thuật ngữ bất kỳ trong bảng, tự phát biểu lại định nghĩa bằng lời của bạn và nêu một ví dụ cùng một phản ví dụ.
2. Phân nhóm các thuật ngữ của một chương thành ba loại: định nghĩa cơ sở, bất biến và định lý tính toán.
3. Chọn một cặp khái niệm dễ nhầm lẫn (như *đồng phôi* và *tương đương đồng luân*, hoặc *đồng điều* và *đối đồng điều*) rồi nêu rõ điểm khác biệt chính.

---

## 📚 Tóm tắt

Từ điển thuật ngữ này tổng hợp có hệ thống các khái niệm, ký hiệu và vị trí bài học tương ứng từ Chương 00 đến Chương 09, giúp bạn tra cứu nhanh và duy trì sự nhất quán thuật ngữ trong suốt quá trình tự học tô-pô.
