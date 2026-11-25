---
layout: post
title: "Lecture 04.00: Metric Spaces - Fundamentals"
lang: vi
lang-ref: lecture-04-00
chapter: 4
lecture: 0
categories: [chapter04]
tags: [metric-spaces, distance, isometry, completeness, cauchy-sequences]
description: "Không gian metric: định nghĩa, ví dụ, isometries, và tính chất cơ bản"
---

**Không gian metric – Các khái niệm cơ bản**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu bạn đang đứng ở ngã tư trung tâm quận 1 (TP.HCM) hay khu bàn cờ Manhattan (New York) và muốn đi bộ sang một tòa nhà cách đó 3 dãy nhà về phía Đông và 4 dãy nhà về phía Bắc, chim bay mất **5** đơn vị (đường chim bay Euclid), nhưng bạn không thể đi xuyên tường — bạn phải đi đúng **$$3 + 4 = 7$$** đơn vị! Còn nếu bạn là một quân Vua trên bàn cờ vua, bạn chỉ cần đúng **$$\max(3, 4) = 4$$** nước đi! Cả ba cách đo đó đều hợp lệ tuyệt đối và dẫn đến khái niệm **không gian metric** — cầu nối hoàn hảo giữa giải tích đo đạc và tô-pô học trừu tượng!

Sau khi nghiên cứu không gian tô-pô ở mức độ tổng quát, chúng ta chuyển sang một lớp không gian đặc biệt quan trọng: **không gian metric** — những không gian được trang bị khái niệm khoảng cách (distance).

Không gian metric sở hữu nhiều tính chất thuận lợi mà không gian tô-pô tổng quát không nhất thiết có. Trước hết, khoảng cách cho phép định lượng mức độ xa gần giữa hai điểm thay vì chỉ xét quan hệ lân cận. Thứ hai, các dãy điểm đủ để mô tả cấu trúc tô-pô mà không cần dùng đến lưới (net) hay bộ lọc (filter) tổng quát. Thứ ba, tính đầy đủ (completeness) — tức mọi dãy Cauchy đều hội tụ — mở ra nhiều công cụ giải tích hữu ích. Ngoài ra, phần lớn các đối tượng quen thuộc trong giải tích như $\mathbb{R}^n$, không gian hàm $C([0,1])$ hay các không gian xác suất đều mang cấu trúc metric.

![Metric space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Metric_space_illustration.svg/500px-Metric_space_illustration.svg.png)  
*Minh họa không gian metric với hàm khoảng cách – Nguồn: Wikimedia Commons*

Mối liên hệ giữa không gian metric và không gian tô-pô có tính một chiều. Mọi metric đều sinh ra một tô-pô tự nhiên thông qua các quả cầu mở, nên mọi không gian metric đều là không gian tô-pô. Tuy nhiên, chiều ngược lại không đúng: không phải mọi không gian tô-pô đều sinh bởi một metric (các không gian *metric hóa được* – metrizable – chỉ là một lớp con thực sự). Định lý metric hóa Urysohn đưa ra tiêu chuẩn đặc trưng cho lớp không gian này và sẽ được xem xét trong các bài sau.

Trong bài học này, chúng ta xây dựng một cách hệ thống các khái niệm nền tảng của không gian metric: định nghĩa metric qua ba tiên đề, các ví dụ tiêu chuẩn (metric Euclid $d_2$, metric Manhattan $d_1$, metric cực đại $d_\infty$, metric rời rạc, metric trên không gian hàm và họ metric $L^p$), tô-pô sinh bởi metric qua các quả cầu mở, sự hội tụ, dãy Cauchy, tính đầy đủ, phép đẳng cự (isometry) và tập bị chặn.

Không gian metric là nền tảng trực tiếp của giải tích thực (giới hạn, tính liên tục, đạo hàm), đồng thời kết nối tô-pô với hình học. Cấu trúc metric xuất hiện rộng rãi trong giải tích hàm (không gian vô hạn chiều), hình học vi phân (metric Riemann), lý thuyết xác suất, cũng như trong khoa học dữ liệu và học máy (phân cụm, phân loại, giảm chiều dữ liệu).

---

## 🗺️ Kiến thức cần nhớ: Không gian Metric là gì và nghiên cứu những gì?

### 1. Tiên đề hóa Khoảng cách: Từ Euclid đến Mọi Thế giới
- **Bản chất:** Một **metric** $$d: X \times X \to [0, \infty)$$ chắt lọc đúng 3 tính chất cốt lõi của khoảng cách: xác định dương ($$d(x,y)=0 \iff x=y$$), đối xứng ($$d(x,y)=d(y,x)$$), và **bất đẳng thức tam giác** ($$d(x,z) \le d(x,y) + d(y,z)$$ — đi vòng không bao giờ ngắn hơn đi thẳng!).
- **Lĩnh vực nghiên cứu:** Không chỉ đo điểm trong $$\mathbb{R}^n$$, metric còn đo khoảng cách giữa hai **chuỗi DNA** (khoảng cách Hamming/Levenshtein), hai **hàm số** ($$L^2, L^\infty$$), hai **xác suất** (Wasserstein) hay hai **hình dạng** (Gromov–Hausdorff).

### 2. Quả cầu mở & Tô-pô sinh bởi Metric
- **Bản chất:** Khi đã có thước đo $$d$$, ta lập tức định nghĩa **quả cầu mở** $$B_d(x, r) = \{y \in X : d(x, y) < r\}$$. Họ các hợp tùy ý của những quả cầu mở tạo thành **tô-pô metric** $$\tau_d$$ — tự động thỏa mãn tính chất tách rất đẹp (mọi không gian metric đều là Hausdorff, chuẩn tắc và đếm được thứ nhất!).

### 3. Giới hạn dãy & Sự khác biệt với Tô-pô tổng quát
- **Bản chất:** Trong không gian metric, mọi khái niệm tô-pô (tập đóng, bao đóng, hàm liên tục, tính compact) đều **tương đương hoàn toàn với ngôn ngữ dãy số**! Đây là đặc ân lớn của không gian metric mà tô-pô tổng quát không luôn có.

---

## 🧮 Ví dụ tính tay làm từng bước

### Ví dụ 1: Ba hình dáng khác nhau của "Hình tròn đơn vị" $$B(0, 1)$$ trong $$\mathbb{R}^2$$
Trên $$\mathbb{R}^2$$, xét ba metric kinh điển đo khoảng cách từ điểm $$p = (x, y)$$ tới gốc $$O = (0, 0)$$:
- **Metric Manhattan ($$d_1$$):** $$d_1(p, O) = \lvert x\rvert + \lvert y\rvert$$.
- **Metric Euclid ($$d_2$$):** $$d_2(p, O) = \sqrt{x^2 + y^2}$$.
- **Metric Chebyshev ($$d_\infty$$):** $$d_\infty(p, O) = \max(\lvert x\rvert, \lvert y\rvert)$$.

Hãy kiểm tra trực tiếp bằng tay xem điểm **$$p = (0.6,\; 0.6)$$** có nằm trong quả cầu mở đơn vị $$B(O, 1)$$ không:
1. Với $$d_1$$: $$d_1(p, O) = 0.6 + 0.6 = 1.2 > 1 \implies p \notin B_{d_1}(O, 1)$$ (quả cầu $$d_1$$ là **hình thoi** xoay $$45^\circ$$!).
2. Với $$d_2$$: $$d_2(p, O) = \sqrt{0.36 + 0.36} = \sqrt{0.72} \approx 0.849 < 1 \implies p \in B_{d_2}(O, 1)$$ (quả cầu $$d_2$$ là **hình tròn**!).
3. Với $$d_\infty$$: $$d_\infty(p, O) = \max(0.6, 0.6) = 0.6 < 1 \implies p \in B_{d_\infty}(O, 1)$$ (quả cầu $$d_\infty$$ là **hình vuông** $$[-1,1]^2$$!).

Dù ba quả cầu có hình dáng khác hẳn nhau (thoi, tròn, vuông), bất kỳ hình tròn nào cũng lồng được vào trong hình vuông và chứa được một hình thoi nhỏ hơn — nên cả ba metric **sinh ra cùng một tô-pô duy nhất trên $$\mathbb{R}^2$$**!

### Ví dụ 2: Kiểm tra Metric rời rạc trên tập bất kỳ $$X$$
Định nghĩa $$d_{\text{rời}}(x, y) = 0$$ nếu $$x = y$$ và $$d_{\text{rời}}(x, y) = 1$$ nếu $$x \neq y$$.
- **Bất đẳng thức tam giác:** Nếu $$x = z$$ thì vế trái $$= 0 \le$$ vế phải. Nếu $$x \neq z$$ thì vế trái $$= 1$$; với mọi $$y$$, không thể đồng thời $$x = y$$ và $$y = z$$ nên ít nhất một trong $$d(x,y), d(y,z)$$ bằng $$1$$, suy ra tổng $$\ge 1$$!
- **Quả cầu mở bán kính $$r = \tfrac{1}{2}$$:** $$B(x, \tfrac{1}{2}) = \{x\}$$ — mọi điểm đơn lẻ đều là tập mở, sinh ra đúng **tô-pô rời rạc**!

### Giải thích: Vì sao tô-pô học vẫn cần không gian Metric?

#### Bước 1: Định lượng khái niệm "gần nhau"
Tô-pô tập hợp chỉ nói điểm $$y$$ nằm trong lân cận $$U$$ của $$x$$. Metric cho bạn một con số cụ thể $$d(x, y) < \varepsilon$$, mở khóa các công cụ định lượng: dãy Cauchy, tính đầy đủ, liên tục đều và nguyên lý ánh xạ co.

#### Bước 2: Dùng quả cầu mở làm cơ sở sinh tô-pô
Tập $$U \subseteq X$$ gọi là mở nếu quanh mỗi $$x \in U$$ ta đặt lọt một quả cầu $$B(x, r) \subseteq U$$. Nhờ bất đẳng thức tam giác, bản thân mỗi quả cầu mở $$B(x, r)$$ cũng là một tập mở!

#### Bước 3: Hưởng trọn đặc quyền "dãy số quyết định tất cả"
Trong không gian metric: $$x \in \overline{A} \iff \exists (a_n) \subset A,\; a_n \to x$$; hàm $$f$$ liên tục $$\iff$$ bảo toàn giới hạn dãy; tập $$K$$ compact $$\iff$$ mọi dãy đều có dãy con hội tụ (compact dãy).

#### Bước 4: Ranh giới giữa Metric và Tô-pô (Định lý Mêtric hóa)
Không phải không gian tô-pô nào cũng có metric sinh ra nó (ví dụ không gian không Hausdorff không bao giờ mêtric hóa được!). Ngược lại, **nhiều metric khác nhau** (như $$d_1, d_2, d_\infty$$) có thể sinh cùng một tô-pô.

$$
\text{Hàm khoảng cách }d
\;\xrightarrow{\;B_d(x,r)\;}\;
\text{Tô-pô metric }\tau_d
\;\xrightarrow{\;\text{Đặc quyền dãy số}\;}\;
\text{Liên tục, Đầy đủ \& Compact dãy}.
$$

---

## 📐 Định nghĩa và các tiên đề

### 1. Không gian metric

<div class="textbook-definition" markdown="1">
**Định nghĩa (Metric):**  
Cho $X$ là một tập hợp. Một **metric** (hay **hàm khoảng cách**) trên $X$ là một ánh xạ

$$
d: X \times X \to \mathbb{R}
$$
</div>

thỏa mãn ba tiên đề sau với mọi $x, y, z \in X$:

**(M1) Tính xác định dương (Positive Definiteness):**
$$
d(x,y) \geq 0, \quad d(x,y) = 0 \iff x = y
$$

**(M2) Tính đối xứng (Symmetry):**
$$
d(x,y) = d(y,x)
$$

**(M3) Bất đẳng thức tam giác (Triangle Inequality):**
$$
d(x,z) \leq d(x,y) + d(y,z)
$$

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian metric):**  
Cặp $(X, d)$ được gọi là một **không gian metric** (metric space).
</div>

**Ý nghĩa trực quan của ba tiên đề:**
- **(M1):** Khoảng cách luôn không âm và chỉ bằng $0$ khi hai điểm trùng nhau.
- **(M2):** Khoảng cách từ $x$ đến $y$ bằng khoảng cách từ $y$ đến $x$.
- **(M3):** Độ dài đường đi trực tiếp không vượt quá độ dài đường đi qua một điểm trung gian.

![Triangle inequality](https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/Triangle_inequality.svg/400px-Triangle_inequality.svg.png)  
*Bất đẳng thức tam giác: $d(x,z) \le d(x,y) + d(y,z)$ – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Triangle_inequality.svg)*

---

### 2. Các ví dụ tiêu chuẩn

**Ví dụ 1: Metric Euclid trên $\mathbb{R}^n$**

$$
d_2(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}
$$

Kiểm tra các tiên đề:
- (M1): Hiển nhiên từ tính không âm của tổng bình phương.
- (M2): Suy trực tiếp từ $|x_i - y_i| = |y_i - x_i|$.
- (M3): Suy từ bất đẳng thức Minkowski trong đại số tuyến tính.

Đây là metric thông thường trên $\mathbb{R}^n$.

---

**Ví dụ 2: Metric Manhattan (Taxicab)**

$$
d_1(\mathbf{x}, \mathbf{y}) = \sum_{i=1}^n |x_i - y_i|
$$

Tên gọi xuất phát từ hình ảnh khoảng cách di chuyển dọc theo lưới đường vuông góc như ở khu Manhattan.

Chẳng hạn trong $\mathbb{R}^2$, ta có $d_1((0,0), (3,4)) = |3| + |4| = 7$, trong khi với metric Euclid thì $d_2((0,0), (3,4)) = 5$.

![Manhattan vs Euclidean](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Manhattan_distance.svg/400px-Manhattan_distance.svg.png)  
*Minh họa khoảng cách Manhattan – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Manhattan_distance.svg)*

---

**Ví dụ 3: Metric cực đại (Chebyshev)**

$$
d_\infty(\mathbf{x}, \mathbf{y}) = \max_{i=1,\ldots,n} |x_i - y_i|
$$

Chẳng hạn $d_\infty((0,0), (3,4)) = \max\{3, 4\} = 4$. Về mặt hình học trong $\mathbb{R}^2$, các quả cầu mở theo metric này là các hình vuông thay vì hình tròn.

---

**Ví dụ 4: Metric rời rạc (Discrete Metric)**

Trên **bất kỳ** tập hợp $X$ nào, ta có thể định nghĩa:

$$
d(x,y) = \begin{cases}
0 & \text{if } x = y \\
1 & \text{if } x \neq y
\end{cases}
$$

Kiểm tra các tiên đề:
- (M1) và (M2) thỏa mãn trực tiếp từ định nghĩa.
- (M3): Nếu $x = z$ thì $d(x,z) = 0 \le d(x,y) + d(y,z)$. Nếu $x \neq z$ thì với mọi $y$, ít nhất một trong hai điều kiện $x \neq y$ hoặc $y \neq z$ xảy ra, nên $d(x,y) + d(y,z) \ge 1 = d(x,z)$.

Tô-pô sinh bởi metric rời rạc chính là tô-pô rời rạc trên $X$.

---

**Ví dụ 5: Không gian hàm**

**Metric đều (uniform metric)** trên không gian các hàm liên tục $C([0,1], \mathbb{R})$ được định nghĩa bởi:

$$
d_\infty(f,g) = \sup_{x \in [0,1]} |f(x) - g(x)|
$$

Metric này gắn với chuẩn supremum, đo độ lệch lớn nhất giữa hai hàm trên toàn bộ đoạn $[0,1]$.

**Ví dụ 6: Họ metric $L^p$**

Trên $\mathbb{R}^n$ với $1 \leq p < \infty$:

$$
d_p(\mathbf{x}, \mathbf{y}) = \left(\sum_{i=1}^n |x_i - y_i|^p\right)^{1/p}
$$

Họ metric này gộp các ví dụ quen thuộc ở trên vào cùng một công thức tổng quát:
- $p = 1$: metric Manhattan,
- $p = 2$: metric Euclid,
- $p \to \infty$: metric cực đại.

---

### 3. Tô-pô sinh bởi metric

<div class="textbook-definition" markdown="1">
**Định nghĩa (Quả cầu mở – Open Ball):**  
Quả cầu mở tâm $x \in X$, bán kính $r > 0$ là tập hợp:

$$
B(x, r) = B_d(x, r) = \{y \in X : d(x,y) < r\}
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Quả cầu đóng – Closed Ball):**

$$
\overline{B}(x, r) = \{y \in X : d(x,y) \leq r\}
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Mặt cầu – Sphere):**

$$
S(x, r) = \{y \in X : d(x,y) = r\}
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tô-pô sinh bởi metric):**  
Tô-pô sinh bởi metric $d$ là họ tập hợp:

$$
\tau_d = \{U \subseteq X : \forall x \in U: \exists r > 0: B(x,r) \subseteq U\}
$$
</div>

Nói cách khác, $U$ là tập mở trong $\tau_d$ khi và chỉ khi $U$ là hợp của một họ các quả cầu mở.

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Họ $\tau_d$ thỏa mãn các tiên đề của một tô-pô trên $X$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Kiểm tra trực tiếp ba tiên đề tô-pô (xem phần bài tập).
</div>

---

**Cơ sở của tô-pô metric:**

<div class="textbook-theorem" markdown="1">
**Định lý:** Họ $\mathcal{B} = \{B(x,r) : x \in X, r > 0\}$ là một cơ sở (basis) của tô-pô $\tau_d$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Suy trực tiếp từ định nghĩa của $\tau_d$ và bất đẳng thức tam giác.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** Tô-pô metric thỏa mãn tiên đề đếm được thứ hai (second countable) khi và chỉ khi $X$ khả ly (separable).
</div>

---

### 4. Sự hội tụ trong không gian metric

<div class="textbook-definition" markdown="1">
**Định nghĩa (Sự hội tụ):**  
Dãy $(x_n)$ **hội tụ** đến $x \in X$ nếu:

$$
\forall \varepsilon > 0: \exists N: \forall n \geq N: d(x_n, x) < \varepsilon
$$
</div>

Ta ký hiệu $x_n \to x$ hoặc $\lim x_n = x$.

<div class="textbook-theorem" markdown="1">
**Định lý (Tính duy nhất của giới hạn):**  
Trong một không gian metric, giới hạn của một dãy hội tụ là duy nhất.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Mọi không gian metric đều là không gian Hausdorff (đã chứng minh ở chương trước), nên giới hạn của dãy là duy nhất.
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Đặc trưng bằng dãy):**  
Trong không gian metric $(X, d)$:
- $x \in \operatorname{cl}(A)$ khi và chỉ khi tồn tại một dãy trong $A$ hội tụ đến $x$.
- Ánh xạ $f$ liên tục tại $x$ khi và chỉ khi với mọi dãy $x_n \to x$, ta có $f(x_n) \to f(x)$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Suy từ việc mọi không gian metric đều thỏa mãn tiên đề đếm được thứ nhất (first countable).
</div>

---

### 5. Dãy Cauchy và tính đầy đủ

<div class="textbook-definition" markdown="1">
**Định nghĩa (Dãy Cauchy):**  
Dãy $(x_n)$ được gọi là **dãy Cauchy** nếu:

$$
\forall \varepsilon > 0: \exists N: \forall m,n \geq N: d(x_m, x_n) < \varepsilon
$$
</div>

Về mặt trực quan, các phần tử của dãy Cauchy tiến lại gần nhau tùy ý khi chỉ số đủ lớn.

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi dãy hội tụ đều là dãy Cauchy.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Giả sử $x_n \to x$. Với mọi $\varepsilon > 0$, tồn tại $N$ sao cho $d(x_n, x) < \varepsilon/2$ với mọi $n \geq N$. Khi đó, với mọi $m, n \geq N$:
$$
d(x_m, x_n) \leq d(x_m, x) + d(x, x_n) < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
$$
Do đó $(x_n)$ là dãy Cauchy.
</div>

**Chiều ngược lại không đúng trong trường hợp tổng quát.** Chẳng hạn, trong khoảng mở $(0,1)$ với metric Euclid, dãy $x_n = 1/n$ là dãy Cauchy nhưng giới hạn $0$ không thuộc $(0,1)$.

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian metric đầy đủ – Complete Metric Space):**  
Không gian metric $(X, d)$ được gọi là **đầy đủ** (complete) nếu mọi dãy Cauchy trong $X$ đều hội tụ đến một điểm thuộc $X$.
</div>

**Các ví dụ về không gian đầy đủ:**
- $\mathbb{R}^n$ với metric Euclid (từ tiên đề đầy đủ của $\mathbb{R}$),
- Đoạn đóng $[a, b] \subset \mathbb{R}$,
- $C([0,1])$ với metric đều $d_\infty$,
- Các không gian dãy $\ell^p$ với $p \geq 1$.

**Các ví dụ về không gian không đầy đủ:**
- Khoảng mở $(0, 1)$,
- Tập số hữu tỉ $\mathbb{Q}$ với metric Euclid,
- $C([0,1])$ với metric tích phân $L^1$.

Về trực quan, tính đầy đủ có nghĩa là không gian không bị "khuyết điểm": mọi dãy Cauchy đều có giới hạn nằm ngay trong không gian đó.

---

### 6. Phép đẳng cự (Isometries)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phép đẳng cự – Isometry):**  
Ánh xạ $f: (X, d_X) \to (Y, d_Y)$ được gọi là một **phép đẳng cự** nếu:

$$
d_Y(f(x), f(y)) = d_X(x, y) \quad \forall x, y \in X
$$
</div>

Nói cách khác, $f$ bảo toàn chính xác khoảng cách giữa mọi cặp điểm.

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi phép đẳng cự đều là đơn ánh và liên tục.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**
- **Tính đơn ánh:** Nếu $f(x) = f(y)$ thì $d_X(x,y) = d_Y(f(x), f(y)) = 0$, suy ra $x = y$.
- **Tính liên tục:** Với mọi $\varepsilon > 0$, chọn $\delta = \varepsilon$; khi đó $d_X(x,y) < \delta$ kéo theo $d_Y(f(x), f(y)) = d_X(x,y) < \varepsilon$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đẳng cự – Isometric):**  
Hai không gian metric $(X, d_X)$ và $(Y, d_Y)$ được gọi là **đẳng cự** với nhau nếu tồn tại một phép đẳng cự **toàn ánh** (song ánh) $f: X \to Y$.
</div>

Ký hiệu: $X \cong Y$ (với tư cách là không gian metric). Hai không gian đẳng cự có cùng cấu trúc metric, chỉ khác nhau ở cách đặt tên điểm.

**Ví dụ:** $[0, 1]$ và $[2, 3]$ đẳng cự với nhau qua phép tịnh tiến $f(x) = x + 2$ (lưu ý rằng $g(x) = 3x + 2$ biến $[0,1]$ lên $[2,5]$ là một phép đồng phôi nhưng không phải phép đẳng cự vì làm giãn khoảng cách $3$ lần).

**Lưu ý về mối quan hệ với đồng phôi:**
- Một phép đẳng cự **song ánh** luôn là một phép đồng phôi (còn phép đẳng cự nói chung là phép nhúng đẳng cự, tức đồng phôi lên ảnh của nó).
- Phép đồng phôi không nhất thiết là phép đẳng cự. Chẳng hạn, $[0,1]$ đồng phôi với $[0,2]$ qua $f(x) = 2x$, nhưng hai đoạn này không đẳng cự vì độ dài khác nhau.

---

### 7. Tập bị chặn và đường kính

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập bị chặn – Bounded Set):**  
Tập con $A \subseteq X$ được gọi là **bị chặn** nếu tồn tại $M \ge 0$ sao cho $d(x,y) \leq M$ với mọi $x, y \in A$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đường kính – Diameter):**

$$
\text{diam}(A) = \sup\{d(x,y) : x, y \in A\}
$$
</div>

**Ví dụ:**
- Đoạn $[0, 1]$ trong $\mathbb{R}$ có $\operatorname{diam}([0,1]) = 1$.
- Toàn bộ $\mathbb{R}$ có $\operatorname{diam}(\mathbb{R}) = \infty$ (không bị chặn).
- Mọi tập hữu hạn đều bị chặn.

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Nếu $A$ là tập compact trong một không gian metric thì $A$ bị chặn.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Cố định $x_0 \in X$. Họ các quả cầu mở $\{B(x_0, n)\}_{n=1}^\infty$ tạo thành một phủ mở của $A$. Vì $A$ compact nên tồn tại phủ con hữu hạn, suy ra $A \subseteq B(x_0, N)$ với $N$ đủ lớn, do đó $A$ bị chặn.
</div>

**Chiều ngược lại không đúng:** Khoảng $(0,1)$ bị chặn nhưng không compact.

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Maurice Fréchet** – *"Sur quelques points du calcul fonctionnel"* (1906)  
   *Giới thiệu khái niệm không gian metric trừu tượng.*

2. **Felix Hausdorff** – *"Grundzüge der Mengenlehre"* (1914)  
   *Trình bày có hệ thống về lý thuyết không gian metric và tô-pô.*

3. **Stefan Banach** – *"Sur les opérations dans les ensembles abstraits"* (1922)  
   *Nghiên cứu không gian metric đầy đủ và không gian Banach.*

### Giáo trình

4. **James R. Munkres** – *Topology*, 2nd Ed., **§20: Metric Topology**  
   *Tài liệu tham khảo tiêu chuẩn.*

5. **Walter Rudin** – *Principles of Mathematical Analysis*, **Chapters 2-3**  
   *Tiếp cận từ góc độ giải tích.*

6. **Seymour Lipschutz** – *General Topology* (Schaum's)  
   *Trình bày ngắn gọn kèm nhiều ví dụ.*

---

## 🔗 Ứng dụng và liên kết

### Giải tích – Tính đầy đủ
**Các định lý điểm bất động:** Định lý điểm bất động Banach đòi hỏi tính đầy đủ của không gian metric và được ứng dụng trực tiếp để chứng minh sự tồn tại, duy nhất nghiệm của phương trình vi phân.

### Khoa học máy tính – Thuật toán
**Tìm láng giềng gần nhất (Nearest Neighbor):** Thuật toán $k$-NN sử dụng các metric khoảng cách (như Euclid, Manhattan) trong không gian đặc trưng.

### Khoa học dữ liệu – Phân cụm
**$k$-Means:** Sử dụng khoảng cách Euclid để phân cụm dữ liệu; việc lựa chọn metric ảnh hưởng trực tiếp đến kết quả phân cụm.

### Vật lý – Thuyết tương đối hẹp
**Metric Minkowski:** Không-thời gian sử dụng dạng song tuyến tính không xác định dương, thỏa mãn một phiên bản điều chỉnh của các tiên đề khoảng cách.

### Học máy – Biểu diễn nhúng (Embeddings)
**Word Embeddings:** Biểu diễn từ ngữ thành các vector trong $\mathbb{R}^n$, nơi khoảng cách hoặc góc giữa các vector phản ánh mức độ tương đồng ngữ nghĩa.

---

## Video tham khảo

- **xem trước** [Basic Topology 1 | Introduction and Open Sets in Metric Spaces](https://www.youtube.com/watch?v=D7ioHVbqWLA) — The Bright Side of Mathematics, tiếng Anh. Giới thiệu metric, quả cầu mở và tập mở sinh bởi chúng, bám sát phần mở đầu của bài.
- [[Không gian metric] I - Khái niệm, sự hội tụ, tập mở & tập đóng](https://www.youtube.com/watch?v=VTRHEyFDpA0) — Hatsune's Maticious, tiếng Việt. Trình bày các khái niệm cơ bản về hội tụ, tập mở và tập đóng bằng tiếng Việt.
- [Metric Spaces 1: Definition and Examples](https://www.youtube.com/watch?v=6LFIav3C_lY) — Math at Andrews University, tiếng Anh. Trình bày định nghĩa và một số ví dụ chuẩn để ôn lại từng tiên đề của metric.

## 🧩 Bài tập

### Định nghĩa metric

1. **Kiểm tra tiên đề:**  
   Với metric Manhattan $d_1$, hãy kiểm tra chi tiết cả ba tiên đề metric.

2. **Metric rời rạc:**  
   Chứng minh metric rời rạc thỏa mãn bất đẳng thức tam giác.

3. **Không phải metric:**  
   Xét $d(x,y) = (x - y)^2$ trên $\mathbb{R}$. Đây có phải là một metric không? Giải thích.

### Ví dụ

4. **Tính khoảng cách:**  
   Trong $\mathbb{R}^2$ với $x = (1,2)$ và $y = (4,6)$, hãy tính:
   - a) $d_2$ (Euclid)
   - b) $d_1$ (Manhattan)
   - c) $d_\infty$ (Cực đại)

5. **Không gian hàm:**  
   Trong $C([0,1])$, tính $d_\infty(f,g)$ với $f(x) = x$ và $g(x) = x^2$.

6. **Chuẩn $L^p$:**  
   Với $x = (1,2,3) \in \mathbb{R}^3$, tính $\|x\|_p$ với $p = 1, 2, \infty$.

### Tô-pô

7. **Quả cầu mở:**  
   Trong $\mathbb{R}^2$ với metric Manhattan, vẽ quả cầu mở $B((0,0), 1)$. Nó có hình dạng gì?

8. **Tô-pô sinh bởi metric:**  
   Metric rời rạc sinh ra tô-pô nào?

9. **Cơ sở:**  
   Chứng minh họ $\{B(x,r) : x \in X, r > 0\}$ là một cơ sở của tô-pô metric.

### Sự hội tụ

10. **Dãy số:**  
    Với dãy $x_n = 1/n$ trong $\mathbb{R}$, chứng minh $x_n \to 0$ theo định nghĩa $\varepsilon$-$N$.

11. **Dãy Cauchy:**  
    Chứng minh mọi dãy hội tụ đều là dãy Cauchy.

12. **Không gian không đầy đủ:**  
    Trong $(0,1)$, tìm một dãy Cauchy không hội tụ trong $(0,1)$.

### Phép đẳng cự

13. **Kiểm tra phép đẳng cự:**  
    Ánh xạ $f: \mathbb{R} \to \mathbb{R}$ xác định bởi $f(x) = 2x$ có phải là phép đẳng cự không?

14. **Đẳng cự giữa các đoạn:**  
    Với điều kiện nào thì $[0,1]$ và $[a,b]$ đẳng cự với nhau? Hãy xây dựng tường minh một phép đẳng cự trong trường hợp đó.

15. **Đồng phôi và đẳng cự:**  
    Tìm một phép đồng phôi $f: [0,1] \to [0,2]$ không phải là phép đẳng cự.

### Nâng cao

16. **Bất đẳng thức tam giác ngược:**  
    Từ bất đẳng thức tam giác, chứng minh $|d(x,z) - d(y,z)| \leq d(x,y)$.

17. **Metric tương đương:**  
    Hai metric $d_1, d_2$ gọi là tương đương nếu chúng sinh ra cùng một tô-pô. Chứng minh $d_1, d_2, d_\infty$ trên $\mathbb{R}^n$ tương đương với nhau.

18. **Đầy đủ hóa (Completion):**  
    Mọi không gian metric đều có một đầy đủ hóa (không gian metric đầy đủ chứa $X$ như một tập con trù mật). Ví dụ: đầy đủ hóa của $\mathbb{Q}$ là $\mathbb{R}$.

### Câu hỏi suy ngẫm

19. **Tại sao cần ba tiên đề?:**  
    Giải thích ý nghĩa hình học của từng tiên đề metric.

20. **Metric và tô-pô:**  
    Tô-pô chỉ cần khái niệm tập mở, trong khi metric bổ sung thêm khái niệm khoảng cách. Sự đánh đổi giữa tính tổng quát và độ phong phú của cấu trúc là gì?

---

## 📚 Đọc thêm

- **Munkres, Topology:** §20 (Metric Topology)
- **Rudin, PMA:** Chapters 2-3 (Metric Spaces)
- **Sutherland:** *Introduction to Metric and Topological Spaces*
- **Kolmogorov & Fomin:** *Introductory Real Analysis*

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã hệ thống hóa các khái niệm nền tảng của không gian metric. Một metric là hàm $d: X \times X \to \mathbb{R}$ thỏa mãn ba tiên đề: xác định dương, đối xứng và bất đẳng thức tam giác. Các ví dụ tiêu biểu gồm metric Euclid, metric Manhattan, metric cực đại, metric rời rạc và họ metric $L^p$. Các quả cầu mở tạo thành cơ sở cho tô-pô metric $\tau_d$. Trong không gian metric, sự hội tụ được đặc trưng qua định nghĩa $\varepsilon$-$N$ với giới hạn duy nhất; dãy Cauchy là dãy có các phần tử tiến gần nhau tùy ý, và không gian đầy đủ là không gian trong đó mọi dãy Cauchy đều hội tụ. Phép đẳng cự là ánh xạ bảo toàn chính xác khoảng cách.

Về mặt cấu trúc, mọi không gian metric đều tự động là Hausdorff, chính quy (regular), chuẩn tắc (normal) và thỏa mãn tiên đề đếm được thứ nhất. Tính đầy đủ là tính chất của bản thân metric chứ không chỉ của tô-pô sinh bởi nó. Các metric khác nhau trên cùng một tập hợp có thể tạo ra các tính chất hình học rất khác nhau, nên việc lựa chọn metric phù hợp đóng vai trò quan trọng trong cả lý thuyết lẫn ứng dụng.

**Tiếp theo:** Lecture 04.01 về **Tính đầy đủ và Định lý phạm trù Baire** — nghiên cứu sâu hơn về các không gian đầy đủ và các hệ quả của chúng.

---

*"A metric space is a topological space with a ruler."*

---

**Previous Chapter:** [Chapter 03: Separation Axioms](/contents/vi/topology-chapter03/)  
**Next:** [Lecture 04.01: Completeness and Baire Category](/contents/vi/topology-chapter04/04_01_Completeness_Baire_Category/)
