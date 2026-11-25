---
layout: post
title: "Lecture 00.03: Real Numbers and Euclidean Space"
lang: vi
lang-ref: lecture-00-03
chapter: 0
lecture: 3
categories: [chapter00]
tags: [real-numbers, euclidean-space, metric, completeness]
description: "Số thực, không gian Euclid, metric topology, và các tính chất nền tảng"
---

**Số thực và Không gian Euclid**

---

## 📖 Tổng quan

Hơn hai nghìn năm trước, các môn đồ trường phái Pythagoras đã bàng hoàng khi phát hiện đường chéo của hình vuông cạnh $$1$$ — tức $$\sqrt{2}$$ — không thể viết dưới dạng tỉ số của hai số nguyên nào. Điều đó có nghĩa là trục số hữu tỉ $$\mathbb{Q}$$, dù dày đặc đến đâu, thực ra lại **chi chít những lỗ thủng vô hình**! Để vá kín toàn bộ các lỗ thủng ấy, toán học thế kỷ XIX xây dựng nên tập số thực $$\mathbb{R}$$ đầy đủ, rồi mở rộng ra không gian Euclid $$\mathbb{R}^n$$ và khái niệm tổng quát hơn là **không gian mê-tric**.

Nhưng điều bất ngờ nhất chỉ đến ở bước cuối cùng của bài giảng này: khi bạn thay chiếc thước đo Euclid quen thuộc bằng thước đo "đường phố Manhattan" ($$d_1$$) hay thước đo cực đại ($$d_\infty$$), hình dạng quả cầu đổi từ hình tròn sang hình thoi rồi hình vuông — **vậy mà họ các tập mở sinh ra vẫn giống hệt nhau!** Chính phát hiện sâu sắc đó đã mở cánh cửa bước từ Giải tích sang Tô-pô học.

**Mạch bài học:** Kiến thức cần nhớ (tính đầy đủ của $$\mathbb{R}$$, không gian mê-tric & sự tương đương tô-pô giữa các mê-tric) → Giải thích: cầm tay so sánh 3 hình cầu đơn vị $$d_1, d_2, d_\infty$$ trên $$\mathbb{R}^2$$ tại điểm $$(0.6, 0.6)$$ → Xây dựng $$\mathbb{R}$$, mê-tric và hội tụ → Bài tập & Tóm tắt.

---

## Kiến thức cần nhớ: Số thực, Không gian Mê-tric và Tô-pô Mê-tric nghiên cứu những gì?

### 1. Tính đầy đủ của $$\mathbb{R}$$ — "vá kín" mọi dãy Cauchy

Một tập số có thể trù mật (giữa hai số hữu tỉ bất kỳ luôn có số hữu tỉ khác) mà vẫn "thủng lỗ chỗ" như $$\mathbb{Q}$$. **Tiên đề đầy đủ** (mọi tập khác rỗng bị chặn trên đều có cận trên đúng $$\sup$$, hay tương đương: mọi dãy Cauchy đều hội tụ trong $$\mathbb{R}$$) chính là thứ giúp định lý giá trị trung gian, định lý Bolzano–Weierstrass và phép tính giới hạn vận hành trơn tru.

### 2. Không gian mê-tric: trừu tượng hóa khái niệm khoảng cách

Maurice Fréchet (1906) nhận ra nhiều định lý giải tích không cần tọa độ hay phép cộng vectơ, mà chỉ cần một hàm khoảng cách $$d(x, y)$$ thỏa 3 tiên đề: không âm & xác định dương, đối xứng, và **bất đẳng thức tam giác** $$d(x, z) \le d(x, y) + d(y, z)$$. Từ đó ta có thể đo khoảng cách giữa hai hàm liên tục, hai chuỗi DNA, hay hai bức ảnh!

### 3. Tô-pô mê-tric: khi "khoảng cách cụ thể" nhường chỗ cho "họ tập mở"

Mỗi mê-tric $$d$$ sinh ra một họ tập mở thông qua các hình cầu mở $$B_d(x, r) = \{y : d(x, y) < r\}$$. Hai mê-tric khác nhau hoàn toàn về con số đo được vẫn có thể sinh ra **cùng một tô-pô** (cùng họ tập mở, cùng các dãy hội tụ, cùng các hàm liên tục) nếu các hình cầu của mê-tric này luôn lồng được vào trong hình cầu của mê-tric kia.

---

### Giải thích: Cầm tay so sánh 3 thước đo $$d_1, d_2, d_\infty$$ trên mặt phẳng $$\mathbb{R}^2$$

Xét gốc tọa độ $$O = (0, 0)$$ và điểm $$P = (0.6,\; 0.6) \in \mathbb{R}^2$$. Hãy tính khoảng cách từ $$O$$ tới $$P$$ theo 3 mê-tric kinh điển trên $$\mathbb{R}^2$$:

1. **Tính cụ thể tại $$P = (0.6,\; 0.6)$$:**
   - **Mê-tric cực đại** $$d_\infty(O, P) = \max(\lvert 0.6 \rvert, \lvert 0.6 \rvert) = \mathbf{0.6} < 1 \implies P \in B_{d_\infty}(O, 1)$$ (hình vuông mở $$(-1,1)^2$$).
   - **Mê-tric Euclid** $$d_2(O, P) = \sqrt{0.6^2 + 0.6^2} = \sqrt{0.72} \approx \mathbf{0.849} < 1 \implies P \in B_{d_2}(O, 1)$$ (hình tròn mở bán kính $$1$$).
   - **Mê-tric Manhattan** $$d_1(O, P) = \lvert 0.6 \rvert + \lvert 0.6 \rvert = \mathbf{1.2} > 1 \implies P \notin B_{d_1}(O, 1)$$ (hình thoi mở với 4 đỉnh $$(\pm 1, 0), (0, \pm 1)$$).
2. **Chuỗi bất đẳng thức lồng nhau cho mọi $$x = (x_1, x_2) \in \mathbb{R}^2$$:**
   $$
   d_\infty(O, x) \;\le\; d_2(O, x) \;\le\; d_1(O, x) \;\le\; 2\,d_\infty(O, x).
   $$
   Thay thử $$P = (0.6, 0.6)$$: $$0.6 \le 0.849 \le 1.2 \le 2 \times 0.6 = 1.2$$ — khớp chính xác!
3. **Hệ quả hình học (tại sao cả 3 sinh cùng một tô-pô?):** Với mọi bán kính $$r > 0$$, chuỗi bất đẳng thức trên tương đương với việc lồng hình cầu:
   $$
   B_{d_1}(O, r) \;\subset\; B_{d_2}(O, r) \;\subset\; B_{d_\infty}(O, r) \;\subset\; B_{d_1}(O, 2r).
   $$
   Nghĩa là quanh bất kỳ điểm nào nằm trong một hình tròn mở, bạn luôn nhét gọn được một hình vuông mở nhỏ hơn và một hình thoi mở nhỏ hơn nữa — do đó một tập hợp là mở theo $$d_1$$ khi và chỉ khi nó mở theo $$d_2$$ và theo $$d_\infty$$!

---

## 🎯 Từ trực giác đến hình thức

### Vì sao cần tập số thực?

Ta đã quen thuộc với các tập số cơ bản:
- **$\mathbb{N} = \{1, 2, 3, \dots\}$:** Tập số tự nhiên, dùng để đếm.
- **$\mathbb{Z} = \{\dots, -2, -1, 0, 1, 2, \dots\}$:** Tập số nguyên, đóng với phép trừ.
- **$\mathbb{Q} = \{p/q : p, q \in \mathbb{Z}, q \neq 0\}$:** Tập số hữu tỉ, đóng với phép chia (cho số khác $0$).

Tuy nhiên, $\mathbb{Q}$ vẫn chưa đủ vì những số như $\sqrt{2}$ không thuộc $\mathbb{Q}$. Nói một cách chính xác hơn, trục số hữu tỉ $\mathbb{Q}$ tồn tại các "lỗ hổng" (*gaps*). Chẳng hạn, xét tập $A = \{x \in \mathbb{Q} : x^2 < 2\}$: với mọi $x \in A$, luôn tìm được $y \in \mathbb{Q}$ sao cho $x < y$ và $y^2 < 2$, do đó $A$ không có cận trên nhỏ nhất (*supremum*) trong $\mathbb{Q}$. Để lấp đầy các lỗ hổng này, ta cần một hệ số đầy đủ hơn là tập số thực **$\mathbb{R}$**.

![Number line with gaps](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d7/Real_number_line.svg/500px-Real_number_line.svg.png)  
*Trục số thực - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Real_number_line.svg)*

---

## 📐 Định nghĩa hình thức

### 1. Xây dựng tập số thực $\mathbb{R}$

Có hai cách kinh điển để xây dựng $\mathbb{R}$ từ $\mathbb{Q}$:

#### Cách 1: Lát cắt Dedekind (Dedekind Cuts)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Lát cắt Dedekind):**  
Một **lát cắt Dedekind** là một cặp $(A, B)$ với $A, B \subseteq \mathbb{Q}$ sao cho:
1. $A \cup B = \mathbb{Q}$, $A \cap B = \emptyset$, $A \neq \emptyset$, $B \neq \emptyset$.
2. $\forall a \in A, \forall b \in B: a < b$.
3. $A$ không có phần tử lớn nhất.
</div>

**Trực giác:** Mỗi lát cắt chia $\mathbb{Q}$ thành hai phần: tập các số hữu tỉ "nhỏ hơn" và tập các số hữu tỉ "lớn hơn hoặc bằng" một số thực xác định.

**Ví dụ:**
- **$\sqrt{2}$:** $A = \{x \in \mathbb{Q} : x < 0 \text{ hoặc } x^2 < 2\}$, $B = \{x \in \mathbb{Q} : x > 0 \text{ và } x^2 \ge 2\}$.
- **$\pi$:** $A = \{x \in \mathbb{Q} : x < \pi\}$, $B = \{x \in \mathbb{Q} : x \ge \pi\}$.

<div class="textbook-definition" markdown="1">
**Định nghĩa:** $\mathbb{R}$ là tập hợp tất cả các lát cắt Dedekind của $\mathbb{Q}$.
</div>

#### Cách 2: Dãy Cauchy (Cauchy Sequences)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Dãy Cauchy trong $\mathbb{Q}$):**  
Dãy $(x_n)$ trong $\mathbb{Q}$ là **dãy Cauchy** nếu:
$$
\forall \varepsilon > 0 \; \exists N \in \mathbb{N} \; \forall m,n \geq N: |x_m - x_n| < \varepsilon
$$
</div>

**Trực giác:** Các số hạng của dãy ngày càng tiến sát lại gần nhau khi $n \to \infty$. Tuy nhiên, một dãy Cauchy trong $\mathbb{Q}$ có thể không hội tụ đến một số hữu tỉ. Chẳng hạn, dãy $x_n = 1 + \frac{1}{1!} + \frac{1}{2!} + \frac{1}{3!} + \dots + \frac{1}{n!}$ là dãy Cauchy trong $\mathbb{Q}$, nhưng hội tụ về $e \approx 2{,}718\dots \notin \mathbb{Q}$.

**Cách xây dựng:** Ta định nghĩa $\mathbb{R}$ là tập các lớp tương đương của các dãy Cauchy trong $\mathbb{Q}$, trong đó hai dãy $(x_n)$ và $(y_n)$ tương đương nếu $|x_n - y_n| \to 0$ khi $n \to \infty$.

---

### 2. Tiên đề đầy đủ (Completeness Axiom)

Thay vì xây dựng tường minh, trong giải tích và tô-pô ta thường tiên đề hóa $\mathbb{R}$ bằng **Tính chất cận trên nhỏ nhất** (*Least Upper Bound Property — LUB*):

> **Mọi tập con khác rỗng và bị chặn trên của $\mathbb{R}$ đều có cận trên nhỏ nhất (*supremum*) trong $\mathbb{R}$.**

$$
\forall A \subseteq \mathbb{R}: (A \neq \emptyset \land A \text{ bounded above}) \implies \exists \sup A \in \mathbb{R}
$$

<div class="textbook-definition" markdown="1">
**Định nghĩa (Supremum):**  
Số $s = \sup A$ nếu:
1. $s$ là cận trên của $A$: $\forall a \in A: a \le s$.
2. $s$ là cận trên nhỏ nhất: nếu $t$ là một cận trên bất kỳ của $A$, thì $s \le t$.
</div>

Tương tự, cận dưới lớn nhất (*Greatest Lower Bound — GLB*) được gọi là **infimum**, ký hiệu $\inf A$.

**Ví dụ:**
- $A = (0, 1)$: $\sup A = 1$ (lưu ý $1 \notin A$).
- $B = \{1 - 1/n : n \in \mathbb{N}\}$: $\sup B = 1$.
- $C = \mathbb{Q} \cap [0, \sqrt{2}]$: $\sup C = \sqrt{2}$ (tồn tại trong $\mathbb{R}$, không tồn tại trong $\mathbb{Q}$).

**Hai hệ quả quan trọng:**

- **Tính chất Archimedes:** Với mọi $x, y \in \mathbb{R}$ mà $y > 0$, luôn tồn tại $n \in \mathbb{N}$ sao cho $ny > x$. Về trực giác, trong $\mathbb{R}$ không tồn tại đại lượng dương "vô cùng nhỏ" thực sự.
- **Tính trù mật của $\mathbb{Q}$ trong $\mathbb{R}$:** Giữa hai số thực phân biệt bất kỳ luôn có ít nhất một số hữu tỉ:

$$
\forall x, y \in \mathbb{R}: (x < y) \implies \exists r \in \mathbb{Q}: x < r < y
$$

---

### 3. Không gian mê-tric (Metric Spaces)

Để mở rộng khái niệm liên tục từ $\mathbb{R}$ sang các tập hợp tổng quát hơn, bước trung gian tự nhiên là hình thức hóa khái niệm "khoảng cách" thông qua **mê-tric**.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Mê-tric):**  
Một **mê-tric** (*metric*) trên tập $X$ là ánh xạ $d: X \times X \to \mathbb{R}$ thỏa mãn với mọi $x, y, z \in X$:

1. **Tính không âm và xác định:** $d(x, y) \ge 0$, và $d(x, y) = 0 \iff x = y$.
2. **Tính đối xứng:** $d(x, y) = d(y, x)$.
3. **Bất đẳng thức tam giác:** $d(x, z) \le d(x, y) + d(y, z)$.
</div>

**Trực giác:** Giá trị $d(x, y)$ đóng vai trò khoảng cách giữa hai điểm $x$ và $y$.

![Triangle inequality visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/Triangle_inequality.svg/400px-Triangle_inequality.svg.png)  
*Bất đẳng thức tam giác - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Triangle_inequality.svg)*

**Các ví dụ quan trọng:**

**1. Mê-tric Euclid trên $\mathbb{R}$:**
$$
d(x, y) = |x - y|
$$

**2. Mê-tric Euclid trên $\mathbb{R}^n$:**
$$
d(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^n (x_i - y_i)²}
$$

**3. Mê-tric Manhattan (Taxicab) trên $\mathbb{R}^2$:**
$$
d_1((x_1, y_1), (x_2, y_2)) = |x_1 - x_2| + |y_1 - y_2|
$$
Tên gọi này xuất phát từ quãng đường di chuyển dọc theo lưới đường phố vuông góc ở Manhattan.

**4. Mê-tric cực đại (Chebyshev) trên $\mathbb{R}^n$:**
$$
d_\infty(\mathbf{x}, \mathbf{y}) = \max_{i=1,\ldots,n} |x_i - y_i|
$$

**5. Mê-tric rời rạc (Discrete metric) trên tập $X$ bất kỳ:**
$$
d(x, y) = \begin{cases} 0 & \text{if } x = y \\ 1 & \text{if } x \neq y \end{cases}
$$

![Different metrics on R2](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Manhattan_distance.svg/400px-Manhattan_distance.svg.png)  
*So sánh khoảng cách Euclid và khoảng cách Manhattan - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Manhattan_distance.svg)*

---

### 4. Tô-pô mê-tric (Metric Topology)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Hình cầu mở — Open Ball):**  
Với $x \in X$ và $r > 0$, **hình cầu mở** tâm $x$ bán kính $r$ là:
$$
B(x, r) = \{y \in X : d(x, y) < r\}
$$
</div>

Cụ thể, trong $\mathbb{R}$, $B(a, r) = (a - r, a + r)$ là một khoảng mở; trong $\mathbb{R}^2$, $B(p, r)$ là đĩa tròn mở tâm $p$ bán kính $r$; và trong $\mathbb{R}^3$, $B(p, r)$ là khối cầu mở tâm $p$ bán kính $r$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập mở trong không gian mê-tric):**  
Tập con $U \subseteq X$ được gọi là **tập mở** (*open set*) nếu:
$$
\forall x \in U: \exists r > 0: B(x, r) \subseteq U
$$
</div>

**Trực giác:** Xung quanh mỗi điểm thuộc $U$ đều có một vùng lân cận nhỏ nằm trọn bên trong $U$.

![Open set visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Open_set_-_example.svg/400px-Open_set_-_example.svg.png)  
*Tập mở trong mặt phẳng - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Open_set_-_example.svg)*

**Ví dụ trong $\mathbb{R}$:** Khoảng mở $(a, b)$ là tập mở; đoạn đóng $[a, b]$ không mở (vì không có khoảng mở nào chứa đầu mút $a$ mà nằm trọn trong $[a, b]$); toàn bộ $\mathbb{R}$ là tập mở; và tập rỗng $\emptyset$ cũng là tập mở (theo chân lý rỗng).

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Họ tất cả các tập mở trong không gian mê-tric $(X, d)$ tạo thành một **tô-pô** trên $X$.
</div>

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:**  
Ta kiểm tra ba tiên đề của tô-pô:
1. $\emptyset$ và $X$ là các tập mở.
2. Hợp tùy ý của các tập mở là tập mở.
3. Giao hữu hạn của các tập mở là tập mở.
</div>

Như vậy, mọi không gian mê-tric đều tự nhiên mang một cấu trúc không gian tô-pô.

---

### 5. Không gian Euclid $\mathbb{R}^n$

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
**Không gian Euclid $n$ chiều** là tập $\mathbb{R}^n = \mathbb{R} \times \mathbb{R} \times \cdots \times \mathbb{R}$ ($n$ lần) trang bị mê-tric Euclid:
$$
d(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^n (x_i - y_i)²}
$$
</div>

Các trường hợp đặc biệt quen thuộc gồm đường thẳng $\mathbb{R}^1 = \mathbb{R}$, mặt phẳng $\mathbb{R}^2$, không gian ba chiều $\mathbb{R}^3$ và không gian bốn chiều $\mathbb{R}^4$.

**Cơ sở chuẩn (Standard Basis):** Tô-pô của $\mathbb{R}^n$ sinh bởi họ tất cả các hình cầu mở, nhưng ta cũng có thể dùng một cơ sở gọn hơn là các "hình hộp mở":

<div class="textbook-theorem" markdown="1">
**Định lý (Cơ sở chuẩn của $\mathbb{R}^n$):**  
Họ tất cả các hình hộp mở (tích Đề-các của $n$ khoảng mở) tạo thành một cơ sở cho tô-pô Euclid của $\mathbb{R}^n$:
$$
\mathcal{B} = \{(a_1, b_1) \times (a_2, b_2) \times \cdots \times (a_n, b_n)\}
$$
</div>

**Ví dụ trong $\mathbb{R}^2$:** Một hình chữ nhật mở có dạng $(1, 3) \times (2, 5) = \{(x, y) : 1 < x < 3, \; 2 < y < 5\}$.

![Open rectangle in R2](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Open_rectangle.svg/300px-Open_rectangle.svg.png)  
*Hình chữ nhật mở làm phần tử cơ sở - Nguồn: Minh họa khái niệm*

**Các tính chất tô-pô quan trọng của $\mathbb{R}^n$:**
- **Khả ly (Separable):** Chứa tập con trù mật đếm được là $\mathbb{Q}^n$.
- **Đếm được thứ hai (Second countable):** Có cơ sở đếm được.
- **Hausdorff:** Hai điểm phân biệt bất kỳ đều có các lân cận mở rời nhau.
- **Đầy đủ (Complete):** Mọi dãy Cauchy trong $\mathbb{R}^n$ đều hội tụ trong $\mathbb{R}^n$.
- **Compact địa phương (Locally compact):** Mọi điểm đều có lân cận compact.
- **Liên thông (Connected):** Không thể phân tách thành hợp của hai tập mở khác rỗng rời nhau.

---

### 6. Sự hội tụ trong không gian mê-tric

<div class="textbook-definition" markdown="1">
**Định nghĩa (Sự hội tụ — Convergence):**  
Dãy $(x_n)$ trong không gian mê-tric $(X, d)$ **hội tụ** về $x \in X$ nếu:
$$
\forall \varepsilon > 0 \; \exists N \in \mathbb{N} \; \forall n \geq N: d(x_n, x) < \varepsilon
$$
</div>

Ký hiệu: $x_n \to x$ hoặc $\lim_{n \to \infty} x_n = x$. Về trực giác, khoảng cách $d(x_n, x)$ tiến về $0$ khi $n \to \infty$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Dãy Cauchy trong không gian mê-tric):**  
Dãy $(x_n)$ là **dãy Cauchy** nếu:
$$
\forall \varepsilon > 0 \; \exists N \in \mathbb{N} \; \forall m,n \geq N: d(x_m, x_n) < \varepsilon
$$
</div>

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi dãy hội tụ trong không gian mê-tric đều là dãy Cauchy.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:** Giả sử $x_n \to x$. Với mọi $\varepsilon > 0$, chọn $N \in \mathbb{N}$ sao cho $\forall n \ge N: d(x_n, x) < \varepsilon / 2$.  
Khi đó với mọi $m, n \ge N$:
$$
d(x_m, x_n) \leq d(x_m, x) + d(x, x_n) < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
$$
∎
</div>

Chiều ngược lại không đúng nói chung, trừ khi không gian có tính đầy đủ.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian mê-tric đầy đủ — Complete Metric Space):**  
Không gian mê-tric $(X, d)$ được gọi là **đầy đủ** (*complete*) nếu mọi dãy Cauchy trong $X$ đều hội tụ về một điểm thuộc $X$.
</div>

**Ví dụ:**
- **$\mathbb{R}$** đầy đủ (theo tiên đề đầy đủ).
- **$\mathbb{Q}$** không đầy đủ (dãy xấp xỉ thập phân của $\sqrt{2}$ là dãy Cauchy nhưng giới hạn $\sqrt{2} \notin \mathbb{Q}$).
- **$(0, 1)$** không đầy đủ (dãy $1/n$ là dãy Cauchy trong $(0, 1)$ nhưng hội tụ về $0 \notin (0, 1)$).
- **$[0, 1]$** đầy đủ.

**Định lý quan trọng:** Với mọi $n \ge 1$, không gian Euclid **$\mathbb{R}^n$** là một không gian mê-tric đầy đủ.

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Bài báo kinh điển

1. **Richard Dedekind** - *Stetigkeit und irrationale Zahlen* (1872)  
   *Xây dựng tập số thực $\mathbb{R}$ bằng lát cắt Dedekind.*

2. **Georg Cantor** - *Grundlagen einer allgemeinen Mannigfaltigkeitslehre* (1883)  
   *Xây dựng tập số thực $\mathbb{R}$ bằng dãy Cauchy.*

3. **Maurice Fréchet** - *Sur quelques points du calcul fonctionnel* (1906)  
   *Giới thiệu khái niệm không gian mê-tric.*

4. **Felix Hausdorff** - *Grundzüge der Mengenlehre* (1914)  
   *Đặt nền móng cho tô-pô đại cương và không gian mê-tric hiện đại.*

### Giáo trình

5. **Walter Rudin** - *Principles of Mathematical Analysis*, 3rd Ed., **Chapter 1**  
   *Xây dựng và các tính chất cơ bản của $\mathbb{R}$.*

6. **James R. Munkres** - *Topology*, 2nd Ed., **§20: Metric Topology**  
   *Trình bày không gian mê-tric trong bối cảnh tô-pô.*

7. **Kenneth A. Ross** - *Elementary Analysis: The Theory of Calculus* (2013)  
   *Cách tiếp cận dễ theo dõi về tập số thực $\mathbb{R}$.*

8. **Charles C. Pugh** - *Real Mathematical Analysis* (2002)  
   *Giáo trình giải tích hiện đại giàu trực giác hình học.*

---

## 🔗 Ứng dụng và liên hệ

### Vật lý — Thuyết tương đối
**Không gian Minkowski:** Trong thuyết tương đối hẹp, không-thời gian được mô hình hóa trên $\mathbb{R}^4$ với dạng toàn phương không Euclid:
$$
ds² = -c²dt² + dx² + dy² + dz²
$$
Dạng này không xác định dương nên không phải là mê-tric theo định nghĩa không gian mê-tric ở trên; cấu trúc tô-pô nền của không-thời gian Minkowski vẫn thường được xét là tô-pô Euclid trên $\mathbb{R}^4$.

### Đồ họa máy tính
**Kết xuất 3D (3D Rendering):** Các đối tượng hình học được mô hình hóa trong $\mathbb{R}^3$. Các phép biến đổi cứng như phép quay và phép tịnh tiến là những ánh xạ liên tục bảo toàn khoảng cách Euclid.

### Khoa học dữ liệu
**Không gian đặc trưng Euclid:** Mỗi điểm dữ liệu thường được biểu diễn dưới dạng vector trong $\mathbb{R}^n$, và các độ đo khoảng cách (Euclid, Manhattan, cosine) được dùng để đo mức độ tương đồng. Chẳng hạn, thuật toán $k$-láng giềng gần nhất (KNN) thường sử dụng mê-tric Euclid trên $\mathbb{R}^n$.

### Học máy
**Không gian tham số:** Mạng nơ-ron hoạt động trên các không gian Euclid chiều cao ($\mathbb{R}^n$ với $n$ lớn), nơi cấu trúc giải tích và tô-pô của $\mathbb{R}^n$ cho phép áp dụng các phương pháp tối ưu dựa trên gradient.

### Ví dụ thực tế
**Định vị GPS:** Vị trí trên bề mặt Trái Đất có thể biểu diễn bằng tọa độ cầu hoặc tọa độ trong $\mathbb{R}^3$; trên phạm vi hẹp, khoảng cách được xấp xỉ bởi mê-tric Euclid (trên phạm vi toàn cầu sử dụng hình học cầu).

---

## Video tham khảo

- **xem trước** [Construction of the Real Numbers](https://www.youtube.com/watch?v=ZWRnZhYv0G0) — Dr Peyam, tiếng Anh. Dựng ℝ từ ℚ, nền cho mặt phẳng và không gian Euclid ở nửa sau bài.
- [Dedekind Cuts: An Introduction](https://www.youtube.com/watch?v=q4FiZ3bsa6w) — Mike, the Mathematician, tiếng Anh. Lát cắt Dedekind, một cách cụ thể để nhìn thứ tự và tính đầy đủ của đường thẳng thực.

## 🧩 Bài tập

### Hiểu về $\mathbb{R}$

1. **Supremum và Infimum:**  
   Tìm $\sup A$ và $\inf A$ (nếu tồn tại):
   - a) $A = \{1/n : n \in \mathbb{N}\}$
   - b) $A = \{x \in \mathbb{Q} : x^2 < 3\}$
   - c) $A = \{x \in \mathbb{R} : \sin(x) = 1\}$

2. **Tính trù mật:**  
   Chứng minh rằng giữa hai số thực bất kỳ $a < b$ luôn tồn tại:
   - a) Một số hữu tỉ.
   - b) Một số vô tỉ.

3. **Tính chất Archimedes:**  
   Sử dụng tính chất Archimedes để chứng minh: $\forall \varepsilon > 0, \; \exists n \in \mathbb{N}: 1/n < \varepsilon$.

### Mê-tric

4. **Kiểm tra tiên đề mê-tric:**  
   Chứng minh mê-tric Manhattan $d_1$ trên $\mathbb{R}^2$ thỏa mãn bất đẳng thức tam giác.

5. **So sánh các mê-tric:**  
   Trên $\mathbb{R}^2$, vẽ hình cầu đơn vị $B(0, 1)$ ứng với ba mê-tric:
   - a) Euclid: $d_2(x, y) = \sqrt{\sum (x_i - y_i)^2}$
   - b) Manhattan: $d_1(x, y) = \sum |x_i - y_i|$
   - c) Cực đại: $d_\infty(x, y) = \max |x_i - y_i|$
   
   Hình dạng của ba hình cầu đơn vị này khác nhau như thế nào?

6. **Mê-tric rời rạc:**  
   Với mê-tric rời rạc trên $X$, mô tả tất cả các hình cầu mở. Những tập con nào của $X$ là tập mở?

### Tập mở

7. **Kiểm tra tập mở:**  
   Trong $\mathbb{R}$ với mê-tric Euclid, các tập sau có phải tập mở không? Giải thích lý do:
   - a) $(0, 1)$
   - b) $[0, 1]$
   - c) $(0, 1] \cup (2, 3)$
   - d) $\mathbb{N}$
   - e) $\mathbb{Q}$

8. **Hình cầu mở là tập mở:**  
   Trong $\mathbb{R}^2$ với mê-tric Euclid, chứng minh rằng $B((0, 0), 1)$ là một tập mở.

9. **Cơ sở của $\mathbb{R}$:**  
   Chứng minh rằng họ tất cả các khoảng mở $(a, b)$ tạo thành một cơ sở cho tô-pô Euclid trên $\mathbb{R}$.

### Sự hội tụ

10. **Ví dụ về hội tụ:**  
    Xác định các dãy sau có hội tụ trong $\mathbb{R}$ không:
    - a) $x_n = 1/n$
    - b) $x_n = (-1)^n$
    - c) $x_n = (n^2 + 1) / (n^2 + 2)$

11. **Dãy Cauchy không hội tụ:**  
    Tìm một dãy Cauchy trong $(0, 1)$ (với mê-tric Euclid) không hội tụ trong $(0, 1)$. Điều này cho thấy gì về tính đầy đủ của $(0, 1)$?

12. **Hội tụ trong $\mathbb{R}^2$:**  
    Chứng minh rằng trong $\mathbb{R}^2$ với mê-tric Euclid, $(x_n, y_n) \to (a, b) \iff x_n \to a$ và $y_n \to b$.

### Nâng cao

13. **Mê-tric tương đương:**  
    Hai mê-tric $d_1, d_2$ trên $X$ được gọi là **tương đương về tô-pô** nếu chúng cảm sinh cùng một tô-pô trên $X$. Chứng minh rằng trên $\mathbb{R}^n$, ba mê-tric sau tương đương nhau:
    - Mê-tric Euclid $d_2$
    - Mê-tric Manhattan $d_1$
    - Mê-tric cực đại $d_\infty$
    
    (*Gợi ý:* Chứng minh mọi hình cầu mở theo một mê-tric đều chứa một hình cầu mở đồng tâm theo mê-tric kia và ngược lại.)

14. **Tính đầy đủ của tập con đóng:**  
    Chứng minh rằng $[0, 1] \subset \mathbb{R}$ là một không gian mê-tric đầy đủ (với mê-tric cảm sinh từ $\mathbb{R}$).

15. **Mê-tric tích:**  
    Trên $\mathbb{R}^2 = \mathbb{R} \times \mathbb{R}$, định nghĩa:
    $$
    d((x_1, y_1), (x_2, y_2)) = \max\{|x_1 - x_2|, |y_1 - y_2|\}
    $$
    Chứng minh $d$ là một mê-tric và mô tả hình dạng các hình cầu mở của nó.

### Suy ngẫm

16. **Tính đầy đủ và tính compact:**  
    $(0, 1)$ không đầy đủ trong khi $[0, 1]$ đầy đủ. Sự khác biệt nào giữa hai tập này tạo nên tính chất đó? (*Gợi mở:* $[0, 1]$ còn có tính chất đặc biệt nào khác trong tô-pô?)

17. **Tô-pô từ mê-tric:**  
    Vì sao hình cầu mở là khái niệm tự nhiên để xây dựng tô-pô từ một mê-tric? Hãy liên hệ với trực giác về "lân cận" và "độ gần".

---

## 📚 Đọc thêm

- **Rudin, Principles of Mathematical Analysis:** Chapter 1 (The Real Number System)
- **Munkres, Topology:** §20 (Metric Topology), §27 (Compact Spaces in Metric Topology)
- **Kolmogorov & Fomin, Introductory Real Analysis:** Chapter 2 (Metric Spaces)
- **Sutherland, Introduction to Metric and Topological Spaces:** Chapters 1–3

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã hoàn thiện các nội dung nền tảng:

✅ **Số thực $\mathbb{R}$:** Xây dựng qua lát cắt Dedekind hoặc dãy Cauchy.  
✅ **Tính đầy đủ:** Tính chất cận trên nhỏ nhất, tính chất Archimedes và tính trù mật của $\mathbb{Q}$.  
✅ **Không gian mê-tric:** Tiên đề khoảng cách và các mê-tric thông dụng.  
✅ **Tô-pô mê-tric:** Từ hình cầu mở đến tập mở và cấu trúc tô-pô.  
✅ **Không gian Euclid $\mathbb{R}^n$:** Ví dụ trung tâm của giải tích và tô-pô.  
✅ **Hội tụ và tính đầy đủ:** Dãy hội tụ, dãy Cauchy và không gian mê-tric đầy đủ.

**Điểm chính:**
- $\mathbb{R}$ đầy đủ theo nghĩa mọi dãy Cauchy đều hội tụ trong $\mathbb{R}$.
- Mê-tric hình thức hóa khái niệm khoảng cách và tự động cảm sinh một tô-pô qua các hình cầu mở.
- $\mathbb{R}^n$ là mô hình chuẩn giúp hình dung hầu hết các khái niệm tô-pô cơ bản.

**Liên hệ với tô-pô:**
- Tô-pô học trừu tượng hóa các tính chất của $\mathbb{R}^n$ không phụ thuộc vào một mê-tric cụ thể.
- Tập mở trong tô-pô tổng quát hóa khái niệm hình cầu mở, còn tính liên tục tô-pô tổng quát hóa định nghĩa $\varepsilon$-$\delta$.

**Kết thúc Chương 00:** Ta đã xây dựng xong nền tảng gồm lý thuyết tập hợp, ánh xạ, quan hệ, Tiên đề Lựa chọn, Bổ đề Zorn, logic chứng minh, tập số thực và không gian mê-tric.

**Tiếp theo:** Chương 01 sẽ trình bày **Không gian tô-pô và Ánh xạ liên tục** — định nghĩa chính thức của tô-pô, cơ sở, hàm liên tục và các ví dụ vượt ra ngoài khuôn khổ không gian mê-tric.

---

*"In mathematics, you don't understand things. You just get used to them." — John von Neumann*

🎯 **Hoàn thành Chương 00 — bạn đã có đủ nền tảng để bước vào nội dung chính của Tô-pô học.** 🎯

---

**Previous:** [Lecture 00.02: Logic and Mathematical Proofs](/contents/vi/topology-chapter00/00_02_Logic_Mathematical_Proofs/)  
**Next Chapter:** [Chapter 01: Topological Spaces and Continuous Functions](/contents/vi/topology-chapter01/)
