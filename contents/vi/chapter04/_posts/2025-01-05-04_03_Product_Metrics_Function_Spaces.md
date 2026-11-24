---
layout: post
title: "Lecture 04.03: Product Metrics and Function Spaces"
lang: vi
lang-ref: lecture-04-03
chapter: 4
lecture: 3
categories: [chapter04]
tags: [product-metrics, function-spaces, uniform-convergence, pointwise-convergence, banach-spaces]
description: "Product metrics, function spaces, uniform vs pointwise convergence, và Banach spaces"
---

**Metric tích và Không gian hàm**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Thế kỷ XIX, các nhà giải tích từng đinh ninh rằng: *nếu một dãy hàm liên tục $$f_n(x)$$ hội tụ tại từng điểm $$x$$ về một hàm $$f(x)$$, thì hàm giới hạn $$f(x)$$ ắt phải liên tục!* Thế nhưng ví dụ đơn giản $$f_n(x) = x^n$$ trên $$[0,1]$$ đã đánh sập trực giác đó: mỗi $$x^n$$ trơn tru hoàn hảo, nhưng giới hạn của chúng lại **gãy bậc thang** tại $$x = 1$$! Cú sốc đó đã khai sinh ra **không gian hàm $$C(X, Y)$$ với metric hội tụ đều $$d_\infty$$** — nơi mỗi **hàm số** trở thành một **điểm** trong một không gian metric vô hạn chiều!

Các bài học trước tập trung chủ yếu vào những không gian metric hữu hạn chiều như $\mathbb{R}^n$. Tuy nhiên, trong giải tích và toán ứng dụng, ta thường xuyên làm việc với các **không gian vô hạn chiều**, đặc biệt là **không gian hàm** (function spaces) — những không gian mà mỗi "điểm" là một hàm số hoặc một dãy số. Các ví dụ tiêu biểu gồm không gian các hàm liên tục $C([0,1])$, không gian các hàm khả tích bậc $p$ ký hiệu $L^p([0,1])$, và không gian các dãy số $\ell^p$.

Việc trang bị metric trên không gian hàm cho phép định nghĩa sự hội tụ của dãy hàm số, phục vụ trực tiếp cho nghiên cứu phương trình vi phân đạo hàm riêng (PDE), giải tích hàm (không gian Banach, không gian Hilbert), cơ học lượng tử và xử lý tín hiệu.

![Function space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Uniform_convergence.gif/400px-Uniform_convergence.gif)  
*Minh họa sự hội tụ đều của dãy hàm*

Trong bài học này, chúng ta sẽ tìm hiểu cách xây dựng metric trên tích hữu hạn và tích vô hạn đếm được của các không gian metric, khảo sát các metric quan trọng trên không gian hàm (metric đều và metric $L^1$), phân biệt hội tụ đều với hội tụ từng điểm, đồng thời giới thiệu các không gian dãy $\ell^p$, không gian hàm $L^p$, không gian Banach và không gian Hilbert.

---

## 🗺️ Bản đồ kiến thức nền: Không gian Tích & Không gian Hàm là gì?

### 1. Metric Tích: Từ Hữu hạn đến Vô hạn Đếm được
- **Tích hữu hạn $$X_1 \times \cdots \times X_n$$:** Ba công thức $$d_1 = \sum d_i$$, $$d_2 = \sqrt{\sum d_i^2}$$, $$d_\infty = \max d_i$$ đều tương đương mạnh và sinh đúng tô-pô tích.
- **Tích đếm được $$\prod_{n=1}^\infty X_n$$:** Không thể cộng thẳng vô hạn số! Ta chặn mỗi thành phần về $$\le 1$$ (dùng $$\bar{d}_n = \min(d_n, 1)$$) rồi gán trọng số giảm nhanh $$2^{-n}$$: $$D(x,y) = \sum_{n=1}^\infty \frac{\bar{d}_n(x_n, y_n)}{2^n}$$ — và kỳ diệu thay, metric này sinh ra chính xác **tô-pô tích**!

### 2. Không gian Hàm $$C(X, Y)$$ & Hội tụ Từng điểm vs. Hội tụ Đều
- **Bản chất:** Khi xem mỗi hàm liên tục $$f: X \to Y$$ là một *điểm*, có hai cách đo "hai hàm gần nhau":
  - **Hội tụ từng điểm:** $$f_n(x) \to f(x)$$ riêng lẻ tại từng $$x$$ (quá yếu — không bảo toàn tính liên tục hay tích phân!).
  - **Metric đều (supremum metric):** $$d_\infty(f, g) = \sup_{x \in X} d_Y(f(x), g(x))$$ (đo khe hở lớn nhất trên toàn miền — bảo toàn hoàn hảo tính liên tục, tính đầy đủ và tích phân!).

### 3. Định lý Arzelà–Ascoli: Tiêu chuẩn Compact trong Không gian Hàm
- **Bản chất:** Trong $$\mathbb{R}^n$$, đóng và bị chặn là đủ để compact (Heine–Borel). Trong không gian vô hạn chiều $$C[0,1]$$, đóng và bị chặn là **chưa đủ**! Định lý **Arzelà–Ascoli** bổ sung đúng mảnh ghép còn thiếu: **tính đồng liên tục (equicontinuity)** (các hàm trong họ không được dao động ngày càng dựng đứng!).

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc: Vì sao $$f_n(x) = x^n$$ hội tụ từng điểm nhưng KHÔNG hội tụ đều?

Xét dãy hàm liên tục $$f_n(x) = x^n$$ trên đoạn đóng $$[0, 1]$$:
1. **Hội tụ từng điểm:**
   - Nếu $$0 \le x < 1$$: $$x^n \to 0$$ khi $$n \to \infty$$.
   - Nếu $$x = 1$$: $$1^n = 1 \to 1$$.
   Vậy hàm giới hạn từng điểm là $$f(x) = \begin{cases} 0 & \text{nếu } 0 \le x < 1, \\ 1 & \text{nếu } x = 1 \end{cases}$$ — **bị gián đoạn tại $$x = 1$$**!
2. **Kiểm tra khoảng cách metric đều $$d_\infty(f_n, f)$$:**
   $$
   d_\infty(f_n, f) = \sup_{x \in [0, 1]} \lvert f_n(x) - f(x)\rvert = \sup_{x \in [0, 1)} x^n = 1 \quad \text{với MỌI } n \ge 1!
   $$
   Khoảng cách $$d_\infty(f_n, f)$$ đứng yên ở $$1 \not\to 0$$! (Ngược lại, nếu thu hẹp miền về $$[0, 0.9]$$, thì $$d_\infty(f_n, 0) = (0.9)^n \to 0$$ — hội tụ đều êm ái về hàm hằng liên tục $$0$$!)

3. **Thử kiểm tra Arzelà–Ascoli trên chính dãy $$\{x^n\}$$ trên $$[0, 1]$$:**
   - Họ $$\{x^n\}$$ bị chặn đều bởi $$1$$ ($$\lvert x^n\rvert \le 1$$).
   - Nhưng tại điểm $$x = 1$$, độ dốc $$f_n'(1) = n \to +\infty$$! Họ **không đồng liên tục** tại $$1$$, nên không có dãy con nào hội tụ đều trong $$C[0, 1]$$!

### Khung giải thích: Chuyển tư duy từ "điểm trong $$\mathbb{R}^n$$" sang "hàm là điểm" (nên đọc chậm)

#### Bước 1: Mỗi hàm số là một điểm trong không gian vô hạn chiều
Tưởng tượng ống lân cận bán kính $$\varepsilon$$ quanh đồ thị hàm $$f$$: quả cầu mở $$B_{d_\infty}(f, \varepsilon)$$ trong $$C[0,1]$$ gồm toàn bộ các hàm $$g$$ có đồ thị nằm lọt thỏm bên trong dải băng $$(f(x) - \varepsilon,\; f(x) + \varepsilon)$$!

#### Bước 2: Hội tụ trong $$d_\infty$$ chính là hội tụ đều
Khi $$d_\infty(f_n, f) \to 0$$, đồ thị $$f_n$$ bị kẹp chặt đồng loạt vào ống $$\varepsilon$$ quanh $$f$$ — lập tức bảo toàn tính liên tục và cho phép đổi chỗ $$\lim$$ với $$\int$$!

#### Bước 3: Tính đầy đủ của $$C(X, Y)$$ kế thừa từ không gian đích $$Y$$
Nếu $$Y$$ là không gian metric đầy đủ (như $$\mathbb{R}$$), thì $$C_b(X, Y)$$ trang bị metric $$d_\infty$$ cũng là một **không gian đầy đủ** (không gian Banach) — biến không gian hàm thành sân chơi lý tưởng cho Định lý điểm bất động Banach!

#### Bước 4: Đóng gói bằng Arzelà–Ascoli cho bài toán biến phân & PDE
Muốn chứng minh một phương trình vi phân hay bài toán tối ưu hàm có nghiệm, ta dựng dãy nghiệm xấp xỉ $$f_n$$ bị chặn đều và đồng liên tục, rồi dùng Arzelà–Ascoli trích ngay ra một dãy con hội tụ đều!

$$
\text{Họ hàm }\{f_n\} \subset C(K, \mathbb{R})
\;\xrightarrow{\;d_\infty(f,g) = \sup \lvert f-g\rvert\;}\;
\text{Không gian Banach đầy đủ}
\;\xrightarrow{\;\text{Bị chặn đều + Đồng liên tục}\;}\;
\text{Compact (Arzelà–Ascoli)}.
$$

---

## 🔢 Metric tích (Product Metrics)

### 1. Tích hữu hạn

Cho hai không gian metric $(X_1, d_1)$ và $(X_2, d_2)$. Để định nghĩa metric trên tích Descartes $X_1 \times X_2$, có ba cách tự nhiên:

**(1) Metric cực đại:**
$$
d_\infty((x_1, x_2), (y_1, y_2)) = \max\{d_1(x_1, y_1), d_2(x_2, y_2)\}
$$

**(2) Metric tổng:**
$$
d_1((x_1, x_2), (y_1, y_2)) = d_1(x_1, y_1) + d_2(x_2, y_2)
$$

**(3) Metric Euclid:**
$$
d_2((x_1, x_2), (y_1, y_2)) = \sqrt{d_1(x_1, y_1)^2 + d_2(x_2, y_2)^2}
$$

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Cả ba hàm trên đều là metric trên $X_1 \times X_2$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Kiểm tra trực tiếp ba tiên đề metric (xem phần bài tập).
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Tính tương đương):**  
Các metric $d_1, d_2, d_\infty$ tương đương mạnh với nhau trên tích hữu hạn $X_1 \times X_2$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Ta có $d_\infty \leq d_2 \leq d_1 \leq 2 \cdot d_\infty$.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Quan hệ với tô-pô tích):**  
Mỗi metric tích $d_1, d_2, d_\infty$ đều sinh ra đúng **tô-pô tích** $\tau_{X_1} \times \tau_{X_2}$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Cơ sở của tô-pô tích gồm các tập dạng $U_1 \times U_2$ với $U_i$ mở trong $X_i$. Trong metric $d_\infty$, quả cầu mở $B_{d_\infty}((x_1, x_2), r)$ chính là tích $B_{d_1}(x_1, r) \times B_{d_2}(x_2, r)$, nên tô-pô sinh bởi $d_\infty$ (và do đó cả $d_1, d_2$) trùng với tô-pô tích.
</div>

**Ví dụ:** Với $\mathbb{R}^n = \mathbb{R} \times \cdots \times \mathbb{R}$, các metric tích $d_1, d_2, d_\infty$ tương đương nhau và đều sinh ra tô-pô chuẩn của $\mathbb{R}^n$.

---

### 2. Tích vô hạn đếm được

Cho dãy không gian metric $(X_n, d_n)$ với $n = 1, 2, 3, \ldots$. Khi mở rộng lên tích vô hạn $\prod_{n=1}^\infty X_n$, việc lấy tổng $\sum d_n$ có thể phân kỳ và $\sup_n d_n$ có thể bằng $\infty$. Để khắc phục, ta chuẩn hóa các metric (chẳng hạn thay $d_n$ bởi $\min(d_n, 1)$) sao cho $d_n \leq 1$.

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Metric đều trên tích vô hạn):**  
Giả sử $d_n \leq 1$ với mọi $n$. Định nghĩa:

$$
d((x_n), (y_n)) = \sup_n d_n(x_n, y_n)
$$
</div>

<div class="textbook-theorem" markdown="1">
**Định lý:** Nếu $d_n \leq 1$ với mọi $n$, thì $d$ là một metric trên $\prod_{n=1}^\infty X_n$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Kiểm tra trực tiếp ba tiên đề metric.
</div>

---

**Metric có trọng số (Weighted Metric):**

$$
d((x_n), (y_n)) = \sum_{n=1}^\infty \frac{1}{2^n} d_n(x_n, y_n)
$$

(vẫn giả sử $d_n \leq 1$ để chuỗi hội tụ).

<div class="textbook-theorem" markdown="1">
**Định lý:** Metric có trọng số trên là một metric và sinh ra đúng tô-pô tích trên $\prod_{n=1}^\infty X_n$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Mang tính kỹ thuật; xem Munkres, §20.
</div>

---

**Lưu ý quan trọng:** Trên tích vô hạn, các metric khác nhau có thể **không tương đương**. Cụ thể, metric có trọng số sinh ra **tô-pô tích**, còn metric đều $\sup_n d_n$ sinh ra **tô-pô đều** (uniform topology), vốn mịn hơn thực sự so với tô-pô tích (nên hai metric này không tương đương nhau trên tích vô hạn).

---

### 3. Tính đầy đủ của không gian tích

<div class="textbook-theorem" markdown="1">
**Định lý (Tích hữu hạn):**  
Nếu $(X_1, d_1)$ và $(X_2, d_2)$ đầy đủ, thì $(X_1 \times X_2, d)$ cũng đầy đủ (với bất kỳ metric tích chuẩn nào).
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Nếu $(x_1^{(k)}, x_2^{(k)})$ là dãy Cauchy trong $X_1 \times X_2$, thì $(x_1^{(k)})$ là dãy Cauchy trong $X_1$ và $(x_2^{(k)})$ là dãy Cauchy trong $X_2$. Do $X_1, X_2$ đầy đủ nên $x_1^{(k)} \to x_1 \in X_1$ và $x_2^{(k)} \to x_2 \in X_2$, suy ra $(x_1^{(k)}, x_2^{(k)}) \to (x_1, x_2)$.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Tích vô hạn với metric có trọng số):**  
Nếu $(X_n, d_n)$ đầy đủ với mọi $n$ (và $d_n \le 1$ hoặc dùng metric cắt cụt $\min(d_n, 1)$), thì $\left(\prod_{n=1}^\infty X_n, d_{\text{weighted}}\right)$ đầy đủ.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Dãy Cauchy theo metric có trọng số kéo theo từng tọa độ là dãy Cauchy trong $X_n$, nên hội tụ theo từng tọa độ, và do đuôi chuỗi $\sum_{n > N} 2^{-n}$ nhỏ tùy ý nên dãy hội tụ theo metric có trọng số.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** $\mathbb{R}^\infty = \mathbb{R} \times \mathbb{R} \times \cdots$ đầy đủ với metric có trọng số (dùng metric cắt cụt trên từng nhân tử).
</div>

---

## 📊 Không gian hàm (Function Spaces)

### 1. Không gian các hàm liên tục $C([0,1])$

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
$C([0,1]) = \{f: [0,1] \to \mathbb{R} : f \text{ liên tục}\}$.
</div>

Đây là một không gian vector với phép cộng và nhân vô hướng xác định từng điểm: $(f + g)(x) = f(x) + g(x)$ và $(\lambda f)(x) = \lambda f(x)$.

---

**Metric 1: Metric đều (Supremum Metric)**

$$
d_\infty(f, g) = \sup_{x \in [0,1]} |f(x) - g(x)|
$$

Còn gọi là chuẩn supremum hay chuẩn đều, ký hiệu $\|f - g\|_\infty = d_\infty(f,g)$.

<div class="textbook-theorem" markdown="1">
**Định lý:** $d_\infty$ là một metric trên $C([0,1])$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**
- (M1): $\sup |f - g| \geq 0$, và bằng $0$ khi và chỉ khi $f = g$.
- (M2): Đối xứng hiển nhiên.
- (M3): $\sup |f - h| \leq \sup |f - g| + \sup |g - h|$.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Tính đầy đủ):**  
$(C([0,1]), d_\infty)$ là không gian metric đầy đủ.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Nếu $(f_n)$ là dãy Cauchy theo $d_\infty$, thì $(f_n)$ là dãy Cauchy đều. Với mỗi $x \in [0,1]$, dãy số thực $(f_n(x))$ là dãy Cauchy nên tồn tại giới hạn $f(x) = \lim_{n \to \infty} f_n(x)$. Hơn nữa, $f_n \to f$ đều trên $[0,1]$. Theo định lý cơ bản của giải tích, giới hạn đều của dãy hàm liên tục là hàm liên tục, nên $f \in C([0,1])$ và $d_\infty(f_n, f) \to 0$.
</div>

---

**Metric 2: Metric $L^1$ (Metric tích phân)**

$$
d_1(f,g) = \int_0^1 |f(x) - g(x)| \, dx
$$

<div class="textbook-theorem" markdown="1">
**Định lý:** $d_1$ là một metric trên $C([0,1])$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Kiểm tra các tiên đề metric dựa trên tính chất tuyến tính, không âm của tích phân và tính liên tục của $|f - g|$.
</div>

<div class="textbook-theorem" markdown="1">
**Định lý:** $d_1 \nsim d_\infty$ trên $C([0,1])$.
</div>

**Chứng minh (Phản ví dụ):**  
Xét dãy $f_n(x) = x^n$:
- $d_1(f_n, 0) = \int_0^1 x^n\,dx = \frac{1}{n+1} \to 0$,
- $d_\infty(f_n, 0) = \sup_{x \in [0,1]} x^n = 1 \neq 0$.

Do sự hội tụ khác nhau nên hai metric không tương đương.

---

<div class="textbook-theorem" markdown="1">
**Định lý (Không đầy đủ):**  
$(C([0,1]), d_1)$ **không** đầy đủ.
</div>

**Ý tưởng chứng minh:**  
Xây dựng một dãy hàm liên tục tuyến tính từng khúc $(f_n)$ xấp xỉ một hàm bậc thang gián đoạn. Dãy $(f_n)$ là dãy Cauchy theo metric $d_1$, nhưng giới hạn của nó là hàm bậc thang không thuộc $C([0,1])$. Điều này một lần nữa minh họa rằng tính đầy đủ phụ thuộc vào metric được chọn.

---

### 2. Hội tụ đều và hội tụ từng điểm

<div class="textbook-definition" markdown="1">
**Định nghĩa (Hội tụ đều):**  
Dãy hàm $(f_n)$ **hội tụ đều** về $f$ (ký hiệu $f_n \rightrightarrows f$) nếu:

$$
\sup_x |f_n(x) - f(x)| \to 0
$$
</div>

Trong ngôn ngữ không gian metric, $f_n \rightrightarrows f$ chính là $f_n \to f$ trong $(C([0,1]), d_\infty)$.

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Hội tụ từng điểm):**  
Dãy hàm $(f_n)$ **hội tụ từng điểm** về $f$ nếu:

$$
\forall x: f_n(x) \to f(x)
$$
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Hội tụ đều $\Rightarrow$ hội tụ từng điểm.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Với mọi $x$, $|f_n(x) - f(x)| \le \sup_t |f_n(t) - f(t)| \to 0$.
</div>

**Chiều ngược lại không đúng.** Xét $f_n(x) = x^n$ trên $[0,1]$:
- Hội tụ từng điểm về hàm $f(x) = 0$ với $x < 1$ và $f(1) = 1$.
- Không hội tụ đều vì $\sup_{x \in [0,1]} |f_n(x) - f(x)| = 1$ với mọi $n$.

---

<div class="textbook-theorem" markdown="1">
**Định lý (Bảo toàn tính liên tục):**
- Giới hạn đều của một dãy hàm liên tục là hàm liên tục.
- Giới hạn từng điểm của một dãy hàm liên tục có thể gián đoạn (như ví dụ $f_n(x) = x^n$ ở trên).
</div>

---

### 3. Không gian dãy $\ell^p$

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
Với $1 \leq p < \infty$, đặt $\ell^p = \left\{(x_n) : \sum_{n=1}^\infty |x_n|^p < \infty\right\}$.
</div>

**Metric trên $\ell^p$:**
$$
d_p((x_n), (y_n)) = \left(\sum_{n=1}^\infty |x_n - y_n|^p\right)^{1/p}
$$

<div class="textbook-theorem" markdown="1">
**Định lý:** $d_p$ là một metric trên $\ell^p$ (chứng minh dùng bất đẳng thức Minkowski).
</div>

<div class="textbook-theorem" markdown="1">
**Định lý:** Không gian $\ell^p$ đầy đủ với mọi $p \geq 1$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Dùng tính hội tụ theo tọa độ kết hợp với định lý hội tụ bị chặn (hoặc bổ đề Fatou).
</div>

---

**Trường hợp đặc biệt: $\ell^2$**

$\ell^2 = \left\{(x_n) : \sum_{n=1}^\infty x_n^2 < \infty\right\}$ là một **không gian Hilbert** với tích vô hướng:
$$
\langle (x_n), (y_n) \rangle = \sum_{n=1}^\infty x_n y_n
$$

Chuẩn tương ứng là $\|x\| = \sqrt{\langle x,x \rangle}$ và metric là $d(x,y) = \|x - y\|$. Không gian $\ell^2$ xuất hiện trong cơ học lượng tử, xử lý tín hiệu (chuỗi Fourier) và thống kê (biến ngẫu nhiên khả tích bình phương).

---

**Không gian $\ell^\infty$:**

$\ell^\infty$ là không gian các dãy bị chặn $(x_n)$ với metric:
$$
d_\infty((x_n), (y_n)) = \sup_n |x_n - y_n|
$$

<div class="textbook-theorem" markdown="1">
**Định lý:** $\ell^\infty$ là không gian metric đầy đủ.
</div>

---

### 4. Không gian hàm $L^p$

<div class="textbook-definition" markdown="1">
**Định nghĩa (mô tả sơ lược):**  
$L^p([0,1])$ là tập các lớp tương đương (bằng nhau hầu khắp nơi) của các hàm đo được $f$ thỏa mãn $\int_0^1 |f(x)|^p\,dx < \infty$.
</div>

**Metric:**
$$
d_p(f,g) = \left(\int_0^1 |f(x) - g(x)|^p \, dx\right)^{1/p}
$$

<div class="textbook-theorem" markdown="1">
**Định lý (Riesz–Fischer):** Không gian $L^p([0,1])$ đầy đủ với mọi $1 \le p \le \infty$.
</div>

**Mối liên hệ với $C([0,1])$:**
- $C([0,1]) \subsetneq L^p([0,1])$ (mọi hàm liên tục trên $[0,1]$ đều khả tích bậc $p$),
- $C([0,1])$ trù mật trong $L^p([0,1])$ (với $1 \le p < \infty$),
- Đầy đủ hóa của $(C([0,1]), d_p)$ chính là $L^p([0,1])$.

---

**Không gian $L^2$:**

$L^2([0,1])$ là một không gian Hilbert với tích vô hướng:
$$
\langle f, g \rangle = \int_0^1 f(x)g(x) \, dx
$$

Không gian này là môi trường tự nhiên cho chuỗi Fourier, nghiệm yếu của PDE và hàm sóng trong cơ học lượng tử.

---

## 🎓 Không gian Banach và không gian Hilbert

### 1. Không gian vector định chuẩn

<div class="textbook-definition" markdown="1">
**Định nghĩa (Chuẩn – Norm):**  
Cho $V$ là một không gian vector (trên $\mathbb{R}$ hoặc $\mathbb{C}$). Một **chuẩn** trên $V$ là hàm $\|\cdot\| : V \to \mathbb{R}$ thỏa mãn:
</div>

- **(N1) Xác định dương:** $\|x\| \geq 0$, và $\|x\| = 0 \iff x = 0$.
- **(N2) Thuần nhất:** $\|\lambda x\| = |\lambda| \cdot \|x\|$.
- **(N3) Bất đẳng thức tam giác:** $\|x + y\| \leq \|x\| + \|y\|$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian định chuẩn):** Cặp $(V, \|\cdot\|)$ được gọi là một **không gian vector định chuẩn**.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi chuẩn đều sinh ra một metric qua công thức $d(x,y) = \|x - y\|$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Kiểm tra trực tiếp ba tiên đề metric từ ba tiên đề chuẩn.
</div>

---

**Ví dụ:**
- **$\mathbb{R}^n$:** $\|x\|_1 = \sum |x_i|$, $\|x\|_2 = \left(\sum x_i^2\right)^{1/2}$, $\|x\|_\infty = \max_i |x_i|$.
- **$C([0,1])$:** $\|f\|_\infty = \sup_{x \in [0,1]} |f(x)|$.
- **$\ell^p$:** $\|(x_n)\|_p = \left(\sum |x_n|^p\right)^{1/p}$.
- **$L^p$:** $\|f\|_p = \left(\int |f|^p\right)^{1/p}$.

---

### 2. Không gian Banach

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian Banach):**  
Một không gian vector định chuẩn $(V, \|\cdot\|)$ đầy đủ (theo metric sinh bởi chuẩn) được gọi là một **không gian Banach**.
</div>

**Ví dụ về không gian Banach:**
- $\mathbb{R}^n$ với bất kỳ chuẩn nào,
- $C([0,1])$ với $\|\cdot\|_\infty$,
- $\ell^p$ với $1 \leq p \leq \infty$,
- $L^p([0,1])$ với $1 \leq p \leq \infty$.

**Phản ví dụ:** $C([0,1])$ với chuẩn $\|\cdot\|_1$ không phải là không gian Banach (vì không đầy đủ).

---

<div class="textbook-theorem" markdown="1">
**Định lý (Trường hợp hữu hạn chiều):**  
Mọi không gian vector định chuẩn hữu hạn chiều (trên $\mathbb{R}$ hoặc $\mathbb{C}$) đều là không gian Banach.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Mọi chuẩn trên không gian hữu hạn chiều đều tương đương với chuẩn Euclid trên $\mathbb{R}^n$ (hoặc $\mathbb{C}^n$), vốn đầy đủ.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** $\mathbb{R}^n$ với bất kỳ chuẩn nào cũng là không gian Banach.
</div>

---

### 3. Không gian Hilbert

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian có tích vô hướng):**  
Không gian vector $V$ trang bị **tích vô hướng** $\langle \cdot, \cdot \rangle$ thỏa mãn:
</div>

- **(IP1) Tính tuyến tính:** $\langle ax + by, z \rangle = a\langle x,z \rangle + b\langle y,z \rangle$.
- **(IP2) Tính đối xứng:** $\langle x,y \rangle = \langle y,x \rangle$ (hoặc liên hợp phức $\overline{\langle y,x \rangle}$ trên $\mathbb{C}$).
- **(IP3) Xác định dương:** $\langle x,x \rangle \geq 0$, và $\langle x,x \rangle = 0 \iff x = 0$.

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Tích vô hướng sinh ra một chuẩn qua công thức $\|x\| = \sqrt{\langle x,x \rangle}$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Kiểm tra các tiên đề chuẩn bằng bất đẳng thức Cauchy–Schwarz.
</div>

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian Hilbert):**  
Một không gian có tích vô hướng đầy đủ (theo metric sinh bởi chuẩn tương ứng) được gọi là một **không gian Hilbert**.
</div>

Nói cách khác, không gian Hilbert là không gian Banach mà chuẩn được sinh ra từ một tích vô hướng.

---

**Ví dụ về không gian Hilbert:**
- $\mathbb{R}^n$ với tích vô hướng chuẩn,
- $\ell^2$,
- $L^2([0,1])$.

**Lưu ý:** $\ell^1$ và $L^1$ là các không gian Banach nhưng không phải không gian Hilbert vì chuẩn của chúng không sinh từ tích vô hướng nào.

---

<div class="textbook-theorem" markdown="1">
**Định lý (Đẳng thức hình bình hành):**  
Một chuẩn được sinh bởi tích vô hướng khi và chỉ khi nó thỏa mãn:

$$
||x + y||^2 + ||x - y||^2 = 2(||x||^2 + ||y||^2)
$$
</div>

Đây là tiêu chuẩn trực tiếp để kiểm tra xem một chuẩn có đến từ tích vô hướng hay không. Chẳng hạn, chuẩn $\|\cdot\|_1$ trên $\mathbb{R}^2$ không thỏa mãn đẳng thức hình bình hành (thử với $x = (1,0), y = (0,1)$), nên không sinh bởi tích vô hướng nào.

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Stefan Banach** – *"Théorie des opérations linéaires"* (1932)  
   *Đặt nền móng cho lý thuyết không gian Banach.*

2. **David Hilbert** – *"Grundzüge einer allgemeinen Theorie der linearen Integralgleichungen"* (1912)  
   *Khởi nguồn lý thuyết không gian Hilbert.*

3. **Frigyes Riesz & Ernst Fischer** – *Định lý Riesz–Fischer* (1907)  
   *Tính đầy đủ của không gian $L^p$.*

### Giáo trình

4. **James R. Munkres** – *Topology*, 2nd Ed., **§20, §21, §43**

5. **Walter Rudin** – *Real and Complex Analysis*, **Chapters 3-4**  
   *Không gian $L^p$.*

6. **Walter Rudin** – *Functional Analysis*, 2nd Ed.

7. **Elias Stein & Rami Shakarchi** – *Functional Analysis*, **Chapters 1-2**

---

## 🔗 Ứng dụng và liên kết

### Giải tích hàm
Không gian Banach và không gian Hilbert là khung lý thuyết chính của giải tích hàm hiện đại.

### Cơ học lượng tử
Hàm sóng của hệ lượng tử thuộc không gian Hilbert $L^2(\mathbb{R}^3)$, trong đó tích vô hướng gắn với biên độ xác suất.

### Phương trình vi phân đạo hàm riêng (PDE)
Nghiệm yếu của nhiều lớp PDE được xét trong các không gian Sobolev (đầy đủ hóa của các không gian hàm trơn theo chuẩn chứa đạo hàm).

### Xử lý tín hiệu
Phân tích Fourier dựa trên hệ cơ sở trực chuẩn $\{e^{inx}\}$ trong không gian $L^2$.

### Học máy
Không gian Hilbert nhân tái tạo (RKHS) là nền tảng của các phương pháp nhân (kernel methods) và máy vector hỗ trợ (SVM).

---

## Video tham khảo

- **xem trước** [Product metrics (revised)](https://www.youtube.com/watch?v=jBe5jkrzsV4) — Andrew McCrady, tiếng Anh. Trình bày cách dựng metric tích, ứng với nửa đầu bài học.
- [MAST30026 Lecture 13: Metrics on function spaces (Part 2)](https://www.youtube.com/watch?v=t6B7UCHvz18) — metauni, tiếng Anh. Metric trên không gian hàm trong giáo trình MAST30026, ứng với nửa sau bài học.
- [Metric Spaces | Lecture 15 | Example of Norm on set of Continuous Functions](https://www.youtube.com/watch?v=10geqkzytCA) — Ranjan Khatu, tiếng Anh. Ví dụ cụ thể về chuẩn supremum trên không gian hàm liên tục.

## 🧩 Bài tập

### Metric tích

1. **Kiểm tra metric:**  
   Chứng minh $d_\infty((x_1,x_2), (y_1,y_2)) = \max\{d_1(x_1,y_1), d_2(x_2,y_2)\}$ thỏa mãn ba tiên đề metric.

2. **Tính tương đương:**  
   Chứng minh $d_1, d_2, d_\infty$ tương đương nhau trên $\mathbb{R} \times \mathbb{R}$.

3. **Tính đầy đủ:**  
   Chứng minh nếu $X$ và $Y$ đầy đủ thì $X \times Y$ đầy đủ.

### Không gian hàm

4. **Metric đều:**  
   Tính $d_\infty(f,g)$ với $f(x) = x$ và $g(x) = x^2$ trong $C([0,1])$.

5. **Metric $L^1$:**  
   Tính $d_1(f,g)$ với cùng cặp hàm $f, g$ ở bài 4.

6. **Không tương đương:**  
   Với $f_n(x) = x^n$, chứng minh $d_1(f_n, 0) \to 0$ nhưng $d_\infty(f_n, 0) \not\to 0$.

### Sự hội tụ

7. **Hội tụ từng điểm và hội tụ đều:**  
   Dãy $f_n(x) = x/n$ trên $[0,1]$ hội tụ từng điểm về hàm nào? Có hội tụ đều không?

8. **Kiểm tra hội tụ đều:**  
   Chứng minh $f_n(x) = \sin(x/n)$ hội tụ đều về $f(x) = 0$ trên $[0,1]$ bằng định nghĩa $\varepsilon$-$N$.

9. **Giới hạn của dãy hàm liên tục:**  
   Chứng minh chi tiết: nếu các hàm $f_n$ liên tục và $f_n \rightrightarrows f$, thì $f$ liên tục.

### Không gian $\ell^p$

10. **Kiểm tra phần tử:**  
    Dãy $(1, 1/2, 1/3, \ldots)$ có thuộc $\ell^2$ không? Có thuộc $\ell^1$ không?

11. **Tính chuẩn:**  
    Tính $\|(1, 1/2, 1/4, \ldots)\|_2$.

12. **Bất đẳng thức Cauchy–Schwarz:**  
    Kiểm chứng $|\langle x,y \rangle| \leq \|x\|_2 \cdot \|y\|_2$ trong $\ell^2$ với một cặp dãy $x, y$ cụ thể.

### Không gian Banach và Hilbert

13. **Kiểm tra chuẩn:**  
    Chứng minh $\|f\|_\infty = \sup |f(x)|$ thỏa mãn ba tiên đề chuẩn trên $C([0,1])$.

14. **Không sinh từ tích vô hướng:**  
    Kiểm chứng chuẩn $\|\cdot\|_1$ trên $\mathbb{R}^2$ không thỏa mãn đẳng thức hình bình hành.

15. **Tính đầy đủ của $\ell^2$:**  
    Phác thảo chứng minh $\ell^2$ đầy đủ.

### Nâng cao

16. **Không gian Sobolev:**  
    Tìm hiểu không gian $W^{1,2}([0,1]) = \{f : f, f' \in L^2\}$. Đây có phải là không gian Banach không?

17. **Không gian đối ngẫu (Dual Space):**  
    Không gian đối ngẫu của $\ell^p$ là $\ell^q$ với $1/p + 1/q = 1$ ($1 < p < \infty$); đặc biệt, đối ngẫu của $\ell^2$ là $\ell^2$.

18. **Chuẩn toán tử:**  
    Với toán tử tuyến tính liên tục $T: V \to W$, chứng minh $\|T\| = \sup\{\|Tx\| : \|x\| \leq 1\}$ thỏa mãn các tiên đề chuẩn.

### Câu hỏi suy ngẫm

19. **Vai trò của tính đầy đủ:**  
    Tại sao tính đầy đủ lại đóng vai trò thiết yếu trong giải tích hàm?

20. **Ứng dụng của $L^2$:**  
    Trình bày vai trò của không gian $L^2$ trong cơ học lượng tử hoặc xử lý tín hiệu.

---

## 📚 Đọc thêm

- **Rudin, Functional Analysis**
- **Reed & Simon, Vol. 1** (Góc nhìn vật lý toán)
- **Brezis, Functional Analysis** (Tiếp cận hiện đại)
- **Munkres, Topology:** §20–21 (Không gian metric)

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã mở rộng lý thuyết metric sang không gian tích và không gian hàm vô hạn chiều. Trên tích hữu hạn $X_1 \times X_2$, các metric $d_1, d_2, d_\infty$ tương đương nhau và đều sinh ra tô-pô tích; trên tích vô hạn đếm được, metric có trọng số sinh ra tô-pô tích trong khi metric đều sinh ra tô-pô mịn hơn.

Trên $C([0,1])$, metric đều $d_\infty$ là đầy đủ và gắn với sự hội tụ đều (bảo toàn tính liên tục), trong khi metric $L^1$ không đầy đủ (và đầy đủ hóa của nó là $L^1([0,1])$). Các không gian dãy $\ell^p$ và không gian hàm $L^p$ ($1 \le p \le \infty$) đều là không gian Banach, còn $\ell^2$ và $L^2$ là các không gian Hilbert nhờ có tích vô hướng.

**Hoàn thành Chapter 04.** Chúng ta đã đi qua các trụ cột của không gian metric: định nghĩa, tính đầy đủ, Định lý phạm trù Baire, metric tương đương, không gian hàm, không gian Banach và không gian Hilbert.

**Tiếp theo:** Chapter 05 về **Không gian thương và Mặt** — cấu trúc tô-pô của phép dán và đa tạp.

---

*"Infinite-dimensional spaces are where analysis truly lives."*

---

**Previous:** [Lecture 04.02: Equivalent Metrics and Uniform Continuity](/contents/vi/topology-chapter04/04_02_Equivalent_Metrics_Uniform_Continuity/)  
**Next Chapter:** [Chapter 05: Quotient Spaces and Surfaces](/contents/vi/topology-chapter05/)
