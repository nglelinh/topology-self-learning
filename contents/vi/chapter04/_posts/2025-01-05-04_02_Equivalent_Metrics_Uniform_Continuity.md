---
layout: post
title: "Lecture 04.02: Equivalent Metrics and Uniform Continuity"
lang: vi
lang-ref: lecture-04-02
chapter: 4
lecture: 2
categories: [chapter04]
tags: [equivalent-metrics, uniform-continuity, lipschitz, contraction]
description: "Equivalent metrics, uniform continuity, Lipschitz maps, và contraction mappings"
---

**Các metric tương đương và Tính liên tục đều**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Hai người bạn cùng đo khoảng cách trên mặt phẳng $$\mathbb{R}^2$$ — một người dùng thước dây Euclid ($$d_2$$), người kia dùng lộ trình đường phố Manhattan ($$d_1$$). Họ có cho ra các con số khác nhau không? Có! Nhưng liệu họ có bao giờ bất đồng về việc một dãy điểm có hội tụ hay một tập hợp có mở không? **Không bao giờ!** Tuy nhiên, nếu bạn đổi thước đo từ $$d(x,y) = \lvert x-y\rvert$$ sang $$d'(x,y) = \lvert \arctan x - \arctan y\rvert$$ trên $$\mathbb{R}$$, hai thước đo vẫn cho cùng tập mở (tương đương tô-pô), nhưng $$d'$$ lại biến $$\mathbb{R}$$ thành không gian **không đầy đủ**! Bài học này phân định rạch ròi ba tầng tương đương của metric và bản chất của **tính liên tục đều**.

Trên cùng một tập hợp có thể tồn tại nhiều metric khác nhau nhưng lại sinh ra cùng một tô-pô. Những metric như vậy gọi là **tương đương tô-pô** (equivalent metrics): dù cách đo khoảng cách khác nhau, chúng có chung họ tập mở, chung các dãy hội tụ và chung lớp hàm liên tục.

**Tính liên tục đều** (uniform continuity) là điều kiện mạnh hơn tính liên tục thông thường: hằng số $\delta$ chỉ phụ thuộc vào $\varepsilon$, không phụ thuộc vào điểm $x$ đang xét. Nhờ đó, ta kiểm soát được độ biến thiên của hàm một cách đồng nhất trên toàn miền xác định, cho phép thác triển hàm từ một tập con trù mật hoặc tận dụng tính compact qua định lý Heine–Cantor.

![Uniform continuity visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Nonuniform_continuity.svg/500px-Nonuniform_continuity.svg.png)  
*Minh họa hàm liên tục nhưng không liên tục đều – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Nonuniform_continuity.svg)*

Một lớp đặc biệt của hàm liên tục đều là hàm **Lipschitz** và **ánh xạ co** (contraction mapping). Định lý điểm bất động Banach khẳng định mọi ánh xạ co trên một không gian metric đầy đủ đều có duy nhất một điểm bất động, và dãy lặp xuất phát từ bất kỳ điểm nào cũng hội tụ về điểm bất động đó.

Trong bài học này, chúng ta sẽ khảo sát các tiêu chuẩn nhận biết metric tương đương, metric tương đương mạnh, tính liên tục đều, định lý Heine–Cantor, định lý thác triển, tính liên tục Lipschitz, ánh xạ co và định lý điểm bất động Banach cùng một số ứng dụng trong giải phương trình và phương trình vi phân.

---

## 🗺️ Kiến thức cần nhớ: Phân tầng Tương đương Metric & Tính Liên tục Đều

### 1. Ba tầng Tương đương giữa hai Metric $$d_1, d_2$$ trên cùng tập $$X$$
- **Tương đương mạnh (Lipschitz):** Tồn tại hằng số $$c, C > 0$$ sao cho $$c\,d_1(x,y) \le d_2(x,y) \le C\,d_1(x,y)$$ với mọi $$x, y$$. Bảo toàn **tất cả**: tập mở, dãy Cauchy, tính đầy đủ và liên tục đều!
- **Tương đương đều (Uniformly equivalent):** Ánh xạ đồng nhất liên tục đều hai chiều — bảo toàn tính đầy đủ và liên tục đều, nhưng không nhất thiết có hằng số Lipschitz toàn cục.
- **Tương đương tô-pô (Topologically equivalent):** Sinh cùng họ tập mở $$\tau_{d_1} = \tau_{d_2}$$ — bảo toàn hội tụ và liên tục, nhưng có thể **phá vỡ tính đầy đủ**!

### 2. Liên tục tại điểm vs. Liên tục Đều (Uniform Continuity)
- **Bản chất:** Ở tính liên tục thường, bán kính $$\delta$$ phụ thuộc vào cả $$\varepsilon$$ **lẫn vị trí điểm $$x$$** (nơi hàm dốc đứng, $$\delta$$ phải co nhỏ xíu!). Ở **liên tục đều**, chỉ cần **một $$\delta(\varepsilon)$$ duy nhất** dùng chung cho *toàn bộ* không gian $$X$$!

### 3. Định lý Heine–Cantor & Mở rộng Hàm Liên tục Đều
- **Bản chất:** Trên miền **compact**, liên tục tự động kéo theo liên tục đều (Heine–Cantor). Quan trọng hơn: hàm liên tục đều **biến dãy Cauchy thành dãy Cauchy**, cho phép thác triển duy nhất một hàm từ tập trù mật (như $$\mathbb{Q}$$) lên toàn bộ không gian đầy đủ (như $$\mathbb{R}$$)!

---

## 🧮 Ví dụ tính tay làm từng bước

### Ví dụ 1: Kiểm tra tương đương mạnh trên $$\mathbb{R}^2$$ giữa $$d_1, d_2, d_\infty$$
Với mọi $$x = (x_1, x_2),\; y = (y_1, y_2) \in \mathbb{R}^2$$, đặt $$a = \lvert x_1 - y_1\rvert \ge 0,\; b = \lvert x_2 - y_2\rvert \ge 0$$. Ta kiểm tra chuỗi bất đẳng thức bằng tay:
1. $$\max(a, b) = \sqrt{\max(a^2, b^2)} \le \sqrt{a^2 + b^2} \implies d_\infty \le d_2$$.
2. $$a^2 + b^2 \le a^2 + 2ab + b^2 = (a+b)^2 \implies d_2 \le d_1$$.
3. $$a + b \le 2\max(a, b) \implies d_1 \le 2\,d_\infty$$.
Gộp lại:
$$
d_\infty(x,y) \le d_2(x,y) \le d_1(x,y) \le 2\,d_\infty(x,y)!
$$
Vậy $$d_1, d_2, d_\infty$$ **tương đương mạnh** với nhau — mọi tính chất tô-pô, dãy Cauchy và tính đầy đủ đều giống hệt nhau!

### Ví dụ 2: Kiểm chứng $$f(x) = x^2$$ KHÔNG liên tục đều trên $$\mathbb{R}$$, còn $$g(x) = \sqrt{x}$$ THÌ CÓ trên $$[0, \infty)$$
- **Với $$f(x) = x^2$$ trên $$\mathbb{R}$$:** Chọn hai dãy tiến sát nhau $$x_n = n$$ và $$y_n = n + \frac{1}{n}$$.
  - Khoảng cách đầu vào: $$\lvert x_n - y_n\rvert = \frac{1}{n} \longrightarrow 0$$.
  - Khoảng cách đầu ra: $$\lvert f(y_n) - f(x_n)\rvert = \left(n + \frac{1}{n}\right)^2 - n^2 = 2 + \frac{1}{n^2} > 2$$ với mọi $$n$$!
  Không tồn tại bất kỳ $$\delta > 0$$ nào ứng với $$\varepsilon = 1$$ dùng chung cho mọi $$x \in \mathbb{R}$$ $$\implies$$ **không liên tục đều**!
- **Với $$g(x) = \sqrt{x}$$ trên $$[0, \infty)$$:** Giả sử $$x \ge y \ge 0$$. Bình phương hai vế của $$\sqrt{x} - \sqrt{y} \le \sqrt{x - y}$$:
  $$
  (\sqrt{x} - \sqrt{y})^2 = x + y - 2\sqrt{xy} \le x + y - 2y = x - y \quad (\text{vì } x \ge y \implies \sqrt{xy} \ge y)!
  $$
  Vậy $$\lvert \sqrt{x} - \sqrt{y}\rvert \le \sqrt{\lvert x - y\rvert}$$ mọi nơi! Chỉ cần chọn $$\delta = \varepsilon^2$$ (không hề phụ thuộc $$x$$!), suy ra $$\sqrt{x}$$ **liên tục đều trên toàn bộ $$[0, \infty)$$** dù đạo hàm tiến ra $$+\infty$$ tại $$0$$!

### Giải thích: Bản chất của 3 mức tương đương và vai trò của Liên tục Đều

#### Bước 1: Phân biệt "cùng tập mở" với "cùng dãy Cauchy"
Metric bị chặn $$d'(x,y) = \frac{\lvert x-y\rvert}{1 + \lvert x-y\rvert}$$ hay $$\lvert \arctan x - \arctan y\rvert$$ giữ nguyên tập mở của $$\mathbb{R}$$, nhưng ở vùng $$x \to +\infty$$ nó nén khoảng cách lại quá mạnh khiến dãy $$x_n = n$$ đột nhiên trở thành dãy Cauchy không hội tụ!

#### Bước 2: Dùng hằng số Lipschitz để kiểm tra nhanh tương đương mạnh
Chỉ cần kẹp được $$c\,d_1 \le d_2 \le C\,d_1$$ (như Ví dụ 1) là bạn yên tâm 100%: không những tập mở mà cả tính đầy đủ và tính liên tục đều cũng bất biến.

#### Bước 3: Nhìn tính liên tục đều qua lăng kính "bảo toàn dãy Cauchy"
Hàm $$f(x) = 1/x$$ liên tục trên $$(0, 1)$$ nhưng đưa dãy Cauchy $$x_n = 1/n$$ thành dãy phân kỳ $$f(x_n) = n$$ — nên nó **không** liên tục đều. Ngược lại, mọi hàm liên tục đều luôn đưa dãy Cauchy thành dãy Cauchy!

#### Bước 4: Đóng gói bằng Heine–Cantor
Trên miền compact (như đoạn đóng $$[a, b]$$ hay mặt cầu $$S^n$$), không có "vùng vô cực" hay "lỗ thủng biên" để độ dốc chạy trốn — vì thế mọi hàm liên tục đều tự động trở thành liên tục đều!

$$
\text{Tương đương mạnh } (c\,d_1 \le d_2 \le C\,d_1)
\;\Longrightarrow\;
\text{Tương đương đều}
\;\Longrightarrow\;
\text{Tương đương tô-pô }(\tau_{d_1} = \tau_{d_2}).
$$

---

## 🎯 Các metric tương đương

### 1. Định nghĩa và các đặc trưng

<div class="textbook-definition" markdown="1">
**Định nghĩa (Metric tương đương):**  
Hai metric $d_1, d_2$ trên tập $X$ được gọi là **tương đương** (hay **tương đương tô-pô**) nếu chúng sinh ra cùng một tô-pô:

$$
\tau_{d_1} = \tau_{d_2}
$$
</div>

Ký hiệu: $d_1 \sim d_2$. Khi đó $(X, d_1)$ và $(X, d_2)$ có cùng các tập mở, cùng các dãy hội tụ và cùng các hàm liên tục.

---

<div class="textbook-theorem" markdown="1">
**Mệnh đề (Đặc trưng qua ánh xạ đồng nhất):**  
$d_1 \sim d_2$ khi và chỉ khi ánh xạ đồng nhất $\operatorname{id}: (X, d_1) \to (X, d_2)$ là một phép đồng phôi.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Ánh xạ $\operatorname{id}$ là phép đồng phôi $\iff$ cả $\operatorname{id}$ và $\operatorname{id}^{-1}$ đều liên tục $\iff \tau_{d_1} = \tau_{d_2}$.
</div>

---

<div class="textbook-theorem" markdown="1">
**Mệnh đề (Đặc trưng qua sự hội tụ của dãy):**  
$d_1 \sim d_2$ khi và chỉ khi với mọi dãy $(x_n)$ và mọi $x \in X$:

$$
x_n \xrightarrow{d_1} x \iff x_n \xrightarrow{d_2} x
$$
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh ($\Rightarrow$):**  
Vì $\tau_{d_1} = \tau_{d_2}$ nên hai không gian có cùng họ tập mở, do đó có cùng các dãy hội tụ.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh ($\Leftarrow$):**  
Trong không gian metric (thỏa mãn tiên đề đếm được thứ nhất), sự hội tụ của dãy đặc trưng hoàn toàn cho các tập đóng, nên hai metric có cùng các tập đóng và do đó sinh ra cùng một tô-pô.
</div>

---

<div class="textbook-theorem" markdown="1">
**Mệnh đề (Đặc trưng qua quả cầu mở):**  
$d_1 \sim d_2$ khi và chỉ khi với mọi $x \in X$ và mọi $r_1 > 0$, tồn tại $r_2 > 0$ sao cho $B_{d_2}(x, r_2) \subseteq B_{d_1}(x, r_1)$, và ngược lại (với vai trò $d_1, d_2$ đổi chỗ cho nhau).
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Suy trực tiếp từ tiêu chuẩn so sánh hai cơ sở sinh ra cùng một tô-pô.
</div>

Trong thực hành, tiêu chuẩn lồng quả cầu này thường là cách trực tiếp nhất để kiểm tra tính tương đương của hai metric.

---

### 2. Các ví dụ trên $\mathbb{R}^n$

<div class="textbook-theorem" markdown="1">
**Định lý (Tương đương metric trên $\mathbb{R}^n$):**  
Trên $\mathbb{R}^n$, ba metric sau tương đương với nhau:
</div>

1. **Metric Euclid:** $d_2(x,y) = \left(\sum_{i=1}^n (x_i - y_i)^2\right)^{1/2}$
2. **Metric Manhattan:** $d_1(x,y) = \sum_{i=1}^n |x_i - y_i|$
3. **Metric cực đại:** $d_\infty(x,y) = \max_{1 \le i \le n} |x_i - y_i|$

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Ta chứng minh chuỗi bất đẳng thức $d_\infty \leq d_2 \leq d_1 \leq n \cdot d_\infty$.
</div>

- **Bước 1 ($d_\infty \leq d_2$):** Với mọi $i$, $|x_i - y_i| \leq \left(\sum_{j=1}^n (x_j - y_j)^2\right)^{1/2}$, nên lấy cực đại theo $i$ cho $d_\infty \leq d_2$.
- **Bước 2 ($d_2 \leq d_1$):** Bình phương hai vế ta thấy $\sum_{i=1}^n (x_i - y_i)^2 \leq \left(\sum_{i=1}^n |x_i - y_i|\right)^2$, nên $d_2 \leq d_1$.
- **Bước 3 ($d_1 \leq n \cdot d_\infty$):** Mỗi số hạng thỏa mãn $|x_i - y_i| \leq d_\infty(x,y)$, cộng $n$ số hạng cho $d_1 \leq n \cdot d_\infty$.

Từ $d_\infty \leq d_2 \leq d_1 \leq n \cdot d_\infty$, ta suy ra ba metric tương đương (hơn nữa là tương đương mạnh; hằng số $n$ phụ thuộc vào số chiều nhưng cố định với $n$ cho trước).

---

<div class="textbook-theorem" markdown="1">
**Hệ quả:**  
Mọi metric $L^p$ trên $\mathbb{R}^n$ (với $p \geq 1$) đều tương đương với nhau.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Sử dụng các bất đẳng thức so sánh tương tự giữa $d_\infty$, $d_p$ và $d_1$.
</div>

Hệ quả quan trọng là tô-pô chuẩn của $\mathbb{R}^n$ được xác định hoàn toàn độc lập với việc chọn metric nào trong họ $L^p$.

---

### 3. Các ví dụ về metric không tương đương

**Ví dụ 1: Metric rời rạc và metric Euclid trên $\mathbb{R}$**

Xét metric rời rạc:
$$
d_{\text{disc}}(x,y) = \begin{cases}
0 & x = y \\
1 & x \neq y
\end{cases}
$$

Ta có $d_{\text{disc}} \nsim d_{\text{Euclidean}}$ trên $\mathbb{R}$.

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Tập đơn điểm $\{x\}$ mở trong $(\mathbb{R}, d_{\text{disc}})$ (vì $\{x\} = B_{d_{\text{disc}}}(x, 1/2)$) nhưng không mở trong $(\mathbb{R}, d_{\text{Euclidean}})$.
</div>

---

**Ví dụ 2: Hai metric khác nhau trên không gian hàm $C([0,1])$**

Trên $C([0,1])$, xét:
1. **Metric đều:** $d_\infty(f,g) = \sup_{x \in [0,1]} |f(x) - g(x)|$
2. **Metric $L^1$:** $d_1(f,g) = \int_0^1 |f(x) - g(x)|\,dx$

Ta có $d_\infty \nsim d_1$.

**Chứng minh:**  
Xét dãy hàm $f_n(x) = x^n$ trên $[0,1]$:
- $d_1(f_n, 0) = \int_0^1 x^n\,dx = \frac{1}{n+1} \to 0$, nên $f_n \to 0$ theo $d_1$.
- $d_\infty(f_n, 0) = \sup_{x \in [0,1]} x^n = 1$ với mọi $n$, nên $f_n$ không hội tụ về $0$ theo $d_\infty$.

Vì sự hội tụ khác nhau nên hai metric sinh ra hai tô-pô khác nhau.

---

### 4. Metric tương đương mạnh (Strongly Equivalent Metrics)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tương đương mạnh):**  
Hai metric $d_1, d_2$ trên $X$ được gọi là **tương đương mạnh** (hay **tương đương đều**) nếu tồn tại các hằng số $c_1, c_2 > 0$ sao cho:

$$
c_1 d_1(x,y) \leq d_2(x,y) \leq c_2 d_1(x,y) \quad \forall x,y
$$
</div>

Ký hiệu: $d_1 \approx d_2$. Hai metric tương đương mạnh chỉ sai khác nhau tối đa một hệ số nhân cố định.

---

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Nếu $d_1 \approx d_2$ thì $d_1 \sim d_2$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Từ bất đẳng thức trên, với mọi $x$ và $r > 0$, ta có $B_{d_2}(x, c_1 r) \subseteq B_{d_1}(x, r)$ và $B_{d_1}(x, r/c_2) \subseteq B_{d_2}(x, r)$.
</div>

**Chiều ngược lại không đúng.** Chẳng hạn, trên $\mathbb{R}$, hai metric $d(x,y) = |x - y|$ và $d'(x,y) = \min(|x - y|, 1)$ tương đương tô-pô nhưng không tương đương mạnh (vì $d$ không bị chặn còn $d'$ bị chặn bởi $1$).

---

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Nếu $d_1 \approx d_2$, thì hai metric có cùng các dãy Cauchy và cùng tính đầy đủ.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Các bất đẳng thức với hằng số dương $c_1, c_2$ bảo toàn trực tiếp điều kiện Cauchy.
</div>

**Lưu ý:** Hai metric chỉ tương đương tô-pô có thể **khác nhau về tính đầy đủ**. Chẳng hạn trên $\mathbb{R}$, metric Euclid $d(x,y) = |x-y|$ là đầy đủ, trong khi metric tương đương tô-pô $d''(x,y) = |\arctan x - \arctan y|$ không đầy đủ (dãy $x_n = n$ là dãy Cauchy theo $d''$ nhưng không hội tụ trong $\mathbb{R}$). Trong khi đó, metric cắt cụt $d' = \min(d, 1)$ vẫn giữ nguyên tính đầy đủ của $d$ vì với mọi $\varepsilon \in (0,1)$, $d(x,y) < \varepsilon \iff d'(x,y) < \varepsilon$.

---

## 🔄 Tính liên tục đều (Uniform Continuity)

### 1. Định nghĩa và động lực

Nhắc lại rằng ánh xạ $f: (X, d_X) \to (Y, d_Y)$ liên tục tại $x \in X$ nếu:

$$
\forall \varepsilon > 0: \exists \delta > 0: d_X(x, x') < \delta \Rightarrow d_Y(f(x), f(x')) < \varepsilon
$$

Ở đây, $\delta$ có thể phụ thuộc vào cả $\varepsilon$ lẫn điểm $x$.

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Liên tục đều):**  
Ánh xạ $f: (X, d_X) \to (Y, d_Y)$ được gọi là **liên tục đều** (uniformly continuous) nếu:

$$
\forall \varepsilon > 0: \exists \delta > 0: \forall x, x' \in X: d_X(x, x') < \delta \Rightarrow d_Y(f(x), f(x')) < \varepsilon
$$
</div>

Điểm khác biệt cốt lõi là $\delta$ chỉ phụ thuộc vào $\varepsilon$, dùng chung cho mọi cặp điểm $x, x' \in X$.

---

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi ánh xạ liên tục đều đều liên tục.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Hiển nhiên bằng cách chọn cùng $\delta$ cho mọi điểm $x$.
</div>

**Chiều ngược lại không đúng:** một hàm liên tục không nhất thiết liên tục đều.

---

**Ví dụ 1: $f(x) = x^2$ trên $\mathbb{R}$**

Hàm $f(x) = x^2$ liên tục nhưng không liên tục đều trên $\mathbb{R}$.

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Chọn $\varepsilon = 1$. Giả sử tồn tại $\delta > 0$ thỏa mãn định nghĩa liên tục đều. Xét $x = 1/\delta$ và $x' = x + \delta/2$. Khi đó $|x - x'| = \delta/2 < \delta$, nhưng:
$$
|f(x') - f(x)| = |(x + \delta/2)^2 - x^2| = |x\delta + (\delta/2)^2| \approx x\delta = 1/\delta \cdot \delta = 1
$$
Chính xác hơn, $|f(x') - f(x)| = 1 + \delta^2/4 > 1 = \varepsilon$, mâu thuẫn.
</div>

---

**Ví dụ 2: $f(x) = 1/x$ trên $(0,1)$**

Hàm $f(x) = 1/x$ liên tục nhưng không liên tục đều trên $(0,1)$.

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Xét hai dãy $x_n = \frac{1}{n}$ và $x'_n = \frac{1}{n+1}$ trong $(0,1)$ (với $n \ge 2$). Ta có $|x_n - x'_n| = \frac{1}{n(n+1)} \to 0$, nhưng $|f(x_n) - f(x'_n)| = |n - (n+1)| = 1$ với mọi $n$. Do đó $f$ không liên tục đều.
</div>

Ví dụ này cho thấy ngay cả trên miền bị chặn, một hàm không bị chặn vẫn có thể không liên tục đều.

---

### 2. Tính liên tục đều trên không gian compact

<div class="textbook-theorem" markdown="1">
**Định lý (Heine–Cantor):**  
Nếu $f: K \to Y$ là ánh xạ liên tục và $K$ là không gian metric compact, thì $f$ liên tục đều trên $K$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Cho $\varepsilon > 0$. Với mỗi $x \in K$, do $f$ liên tục tại $x$, tồn tại $\delta_x > 0$ sao cho $B(x, \delta_x) \subseteq f^{-1}(B(f(x), \varepsilon/2))$. Họ $\{B(x, \delta_x/2)\}_{x \in K}$ là một phủ mở của $K$. Vì $K$ compact, tồn tại phủ con hữu hạn ứng với các điểm $x_1, \ldots, x_n$. Đặt $\delta = \min_{1 \le i \le n} (\delta_{x_i}/2) > 0$.  
Với mọi $x, x' \in K$ thỏa $d_K(x, x') < \delta$, tồn tại $i$ sao cho $x \in B(x_i, \delta_{x_i}/2)$. Theo bất đẳng thức tam giác, $d_K(x', x_i) \le d_K(x', x) + d_K(x, x_i) < \delta + \delta_{x_i}/2 \le \delta_{x_i}$, nên $x' \in B(x_i, \delta_{x_i})$. Do đó cả $f(x)$ và $f(x')$ đều thuộc $B(f(x_i), \varepsilon/2)$, suy ra $d_Y(f(x), f(x')) < \varepsilon$.
</div>

**Hệ quả:** Mọi hàm liên tục trên đoạn đóng bị chặn $[a,b]$ đều liên tục đều.

---

### 3. Định lý thác triển (Extension Theorem)

<div class="textbook-theorem" markdown="1">
**Định lý (Thác triển ánh xạ liên tục đều):**  
Cho $A$ là tập con trù mật của không gian metric $X$, $Y$ là không gian metric đầy đủ, và $f: A \to Y$ là ánh xạ liên tục đều. Khi đó $f$ thác triển duy nhất thành một ánh xạ liên tục đều $\overline{f}: X \to Y$.
</div>

**Ý tưởng chứng minh:**  
Với mỗi $x \in X$, vì $A$ trù mật nên tồn tại dãy $(a_n)$ trong $A$ hội tụ đến $x$. Do $f$ liên tục đều, $(f(a_n))$ là dãy Cauchy trong $Y$, và vì $Y$ đầy đủ nên hội tụ. Ta đặt $\overline{f}(x) = \lim_{n \to \infty} f(a_n)$; giá trị này không phụ thuộc vào cách chọn dãy $(a_n)$, và $\overline{f}$ liên tục đều trên $X$ đồng thời trùng với $f$ trên $A$.

**Ứng dụng:** Thác triển các hàm liên tục đều từ $\mathbb{Q}$ lên $\mathbb{R}$.

---

## 📏 Tính liên tục Lipschitz

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa (Liên tục Lipschitz):**  
Ánh xạ $f: (X, d_X) \to (Y, d_Y)$ được gọi là **liên tục Lipschitz** với hằng số $L \ge 0$ (hay **$L$-Lipschitz**) nếu:

$$
d_Y(f(x), f(y)) \leq L \cdot d_X(x,y) \quad \forall x, y \in X
$$
</div>

Về mặt trực quan, $f$ không làm tăng khoảng cách giữa hai điểm bất kỳ quá $L$ lần.

---

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Liên tục Lipschitz $\Rightarrow$ liên tục đều $\Rightarrow$ liên tục.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Nếu $L = 0$ thì $f$ là hàm hằng nên hiển nhiên liên tục đều. Nếu $L > 0$, với mọi $\varepsilon > 0$, chọn $\delta = \varepsilon/L$: khi $d_X(x,y) < \delta$ ta có $d_Y(f(x), f(y)) \leq L \cdot d_X(x,y) < L \cdot \delta = \varepsilon$.
</div>

**Chiều ngược lại không đúng:** Hàm $f(x) = \sqrt{x}$ trên $[0,1]$ liên tục đều (theo định lý Heine–Cantor) nhưng không Lipschitz vì đạo hàm không bị chặn gần $0$.

---

### 2. Các ví dụ

- **Ví dụ 1:** $f(x) = 3x + 5$ trên $\mathbb{R}$ thỏa $|f(x) - f(y)| = 3|x - y|$, là hàm Lipschitz với $L = 3$.
- **Ví dụ 2:** $f(x) = \sin(x)$ trên $\mathbb{R}$ thỏa $|\sin(x) - \sin(y)| \leq |x - y|$ (theo định lý giá trị trung bình), là hàm Lipschitz với $L = 1$.
- **Ví dụ 3:** $f(x) = x^2$ trên $[0, M]$ thỏa $|f(x) - f(y)| = |x - y|\cdot |x + y| \leq 2M|x - y|$, là hàm Lipschitz với $L = 2M$ (nhưng không Lipschitz trên toàn bộ $\mathbb{R}$).

---

### 3. Ánh xạ co (Contraction Mappings)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Ánh xạ co):**  
Ánh xạ $f: X \to X$ được gọi là một **ánh xạ co** (contraction mapping) nếu tồn tại hằng số $k \in [0, 1)$ sao cho:

$$
d(f(x), f(y)) \leq k \cdot d(x,y) \quad \forall x,y \in X
$$
</div>

Nói cách khác, ánh xạ co là một ánh xạ Lipschitz từ $X$ vào chính nó với hằng số $k < 1$, tức luôn kéo các điểm lại gần nhau hơn sau mỗi lần tác động.

---

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý điểm bất động Banach):**  
Cho $(X, d)$ là không gian metric đầy đủ khác rỗng và $f: X \to X$ là một ánh xạ co. Khi đó tồn tại duy nhất một điểm $x^* \in X$ sao cho $f(x^*) = x^*$ (**điểm bất động**).
</div>

Hơn nữa, với mọi điểm xuất phát $x_0 \in X$, dãy lặp $x_{n+1} = f(x_n)$ hội tụ về $x^*$.

<div class="textbook-proof" markdown="1">
**Chứng minh:**
</div>

**Bước 1 (Xây dựng dãy lặp):** Chọn $x_0 \in X$ tùy ý và định nghĩa $x_{n+1} = f(x_n)$ với mọi $n \ge 0$.

**Bước 2 (Chứng minh $(x_n)$ là dãy Cauchy):**  
Bằng quy nạp, $d(x_{n+1}, x_n) = d(f(x_n), f(x_{n-1})) \leq k \cdot d(x_n, x_{n-1}) \leq \cdots \leq k^n d(x_1, x_0)$. Với mọi $m > n$:
$$
d(x_m, x_n) \leq d(x_m, x_{m-1}) + \cdots + d(x_{n+1}, x_n) \leq (k^{m-1} + \cdots + k^n) d(x_1, x_0)
$$
$$
\leq k^n \frac{1}{1-k} d(x_1, x_0) \to 0
$$
khi $n \to \infty$ (do $0 \le k < 1$). Vậy $(x_n)$ là dãy Cauchy.

**Bước 3 (Sự hội tụ):** Vì $X$ đầy đủ, tồn tại $x^* \in X$ sao cho $x_n \to x^*$.

**Bước 4 (Kiểm tra điểm bất động):** Vì $f$ liên tục, $f(x^*) = f(\lim x_n) = \lim f(x_n) = \lim x_{n+1} = x^*$.

**Bước 5 (Tính duy nhất):** Giả sử $f(y) = y$. Khi đó $d(x^*, y) = d(f(x^*), f(y)) \leq k \cdot d(x^*, y)$. Do $k < 1$, ta suy ra $d(x^*, y) = 0$, tức $x^* = y$.

---

<div class="textbook-theorem" markdown="1">
**Hệ quả (Tốc độ hội tụ):**

$$
d(x_n, x^*) \leq \frac{k^n}{1-k} d(x_1, x_0)
$$
</div>

Sai số giảm theo cấp số nhân theo số bước lặp $n$.

---

**Ứng dụng: Giải phương trình**

Để giải phương trình $g(x) = 0$, ta có thể viết lại dưới dạng bài toán tìm điểm bất động $x = f(x)$ (chẳng hạn $f(x) = x - g(x)$). Nếu $f$ là ánh xạ co trên một không gian metric đầy đủ, phương trình có nghiệm duy nhất.

**Ví dụ:** Giải phương trình $x = \cos(x)$ trên $[0,1]$. Xét $f(x) = \cos(x)$ ánh xạ $[0,1]$ vào $[0,1]$. Ta có $|f'(x)| = |\sin(x)| \leq \sin(1) < 1$ trên $[0,1]$, nên $f$ là ánh xạ co trên đoạn đóng $[0,1]$ và có duy nhất một điểm bất động $x^* \approx 0.739$.

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Stefan Banach** – *"Sur les opérations dans les ensembles abstraits"* (1922)  
   *Chứng minh Định lý điểm bất động Banach.*

2. **Eduard Heine** & **Georg Cantor** – *On uniform continuity* (thập niên 1870)  
   *Định lý Heine–Cantor.*

### Giáo trình

3. **James R. Munkres** – *Topology*, 2nd Ed., **§20, §43**

4. **Walter Rudin** – *Principles of Mathematical Analysis*, **Chapter 4**  
   *Tính liên tục đều.*

5. **Serge Lang** – *Real and Functional Analysis*, **Chapter 1**  
   *Định lý điểm bất động Banach.*

6. **Michael Reed & Barry Simon** – *Functional Analysis*, **Chapter 1**

---

## 🔗 Ứng dụng và liên kết

### Phương trình vi phân
**Định lý Picard–Lindelöf:** Chứng minh sự tồn tại và duy nhất nghiệm địa phương của phương trình vi phân thường nhờ Định lý điểm bất động Banach.

### Giải tích số
**Các phương pháp lặp:** Phương pháp Newton và hạ gradient (gradient descent) hội tụ khi ánh xạ lặp mang tính co cục bộ.

### Kinh tế học
**Cân bằng Nash:** Sử dụng Định lý điểm bất động Kakutani (mở rộng cho ánh xạ đa trị) để chứng minh sự tồn tại cân bằng.

### Xử lý ảnh
**Nén ảnh fractal:** Sử dụng hệ các ánh xạ co để mã hóa và tái tạo hình ảnh.

### Học máy
**Thuật toán huấn luyện:** Phân tích sự hội tụ của nhiều thuật toán tối ưu dựa trên tính chất co.

---

## Video tham khảo

- **xem trước** [Topology #11 Metric Equivalences](https://www.youtube.com/watch?v=odCnlzlpKZ0) — Daniel Firth, tiếng Anh. Hai metric tương đương khi chúng sinh ra cùng họ tập mở, bám sát nửa đầu bài học.
- [Uniform Continuity Explained | Real Analysis](https://www.youtube.com/watch?v=MmxtJwr3Kws) — Wrath of Math, tiếng Anh. Giải thích tính liên tục đều (hằng số $\delta$ không phụ thuộc vào điểm), ứng với nửa sau bài học.
- [Math 441 - 4.4 Uniform Continuity](https://www.youtube.com/watch?v=dQktXveD5bc) — Marc Renault, tiếng Anh. Một tiết giảng về tính liên tục đều kèm các chứng minh $\varepsilon$–$\delta$.

## 🧩 Bài tập

### Metric tương đương

1. **Kiểm tra tính tương đương:**  
   Chứng minh chi tiết $d_1, d_2, d_\infty$ tương đương nhau trên $\mathbb{R}^2$.

2. **Metric không tương đương:**  
   Chứng minh $d_{\text{disc}}$ và $d_{\text{Euclidean}}$ không tương đương trên $\mathbb{R}$ bằng cách chỉ ra một tập mở cụ thể.

3. **Tương đương mạnh:**  
   Hai metric $d(x,y)$ và $2d(x,y)$ có tương đương mạnh không? Kiểm chứng.

### Tính liên tục đều

4. **Khảo sát tính liên tục đều:**  
   Hàm $f(x) = x^3$ có liên tục đều trên $[-1, 1]$ không? Trên $\mathbb{R}$ thì sao?

5. **Định lý Heine–Cantor:**  
   Áp dụng định lý Heine–Cantor để kết luận $f(x) = 1/x$ liên tục đều trên $[1,2]$.

6. **Phản ví dụ:**  
   Tìm một hàm liên tục trên $(0,1)$ nhưng không liên tục đều.

### Tính liên tục Lipschitz

7. **Kiểm tra điều kiện Lipschitz:**  
   Chứng minh $f(x) = |x|$ liên tục Lipschitz trên $\mathbb{R}$ với $L = 1$.

8. **Không Lipschitz:**  
   Chứng minh $f(x) = x^2$ không liên tục Lipschitz trên $\mathbb{R}$.

9. **Đạo hàm bị chặn:**  
   Chứng minh nếu $f: [a,b] \to \mathbb{R}$ khả vi và $|f'(x)| \leq M$ với mọi $x \in [a,b]$, thì $f$ liên tục Lipschitz với hằng số $L = M$.

### Định lý điểm bất động Banach

10. **Áp dụng định lý Banach:**  
    Chứng minh $f(x) = (x + 2)/3$ là ánh xạ co trên $\mathbb{R}$ và tìm điểm bất động của nó.

11. **Giải phương trình:**  
    Dùng Định lý điểm bất động Banach chứng minh phương trình $x = e^{-x}$ có nghiệm duy nhất.

12. **Tốc độ hội tụ:**  
    Trong bài 11, lấy $x_0 = 0$, tính $x_1, x_2, x_3$ và ước lượng $x^*$.

### Ứng dụng

13. **Phương trình vi phân thường:**  
    Với bài toán $dy/dx = f(x,y)$, $y(0) = y_0$ và dãy lặp Picard $y_{n+1}(x) = y_0 + \int_0^x f(t, y_n(t))\,dt$, hãy phác thảo chứng minh sự hội tụ bằng định lý Banach.

14. **Phương pháp Newton:**  
    Với phép lặp $x_{n+1} = x_n - f(x_n)/f'(x_n)$, khi nào ánh xạ lặp là ánh xạ co?

15. **Fractal:**  
    Mô tả cách định nghĩa tam giác Sierpinski thông qua các ánh xạ co.

### Nâng cao

16. **Định lý thác triển:**  
    Cho $f: \mathbb{Q} \cap [0,1] \to \mathbb{R}$ xác định bởi $f(x) = x^2$. Hãy thác triển $f$ lên $[0,1]$.

17. **Định lý Kakutani:**  
    Tìm hiểu Định lý điểm bất động Kakutani cho ánh xạ đa trị.

18. **Định lý Brouwer:**  
    Tìm hiểu Định lý điểm bất động Brouwer (mọi ánh xạ liên tục $f: D^n \to D^n$ đều có điểm bất động) và so sánh với định lý Banach.

### Câu hỏi suy ngẫm

19. **Tại sao cần tính đầy đủ?:**  
    Định lý điểm bất động Banach yêu cầu không gian đầy đủ. Hãy tìm một ví dụ về ánh xạ co trên không gian không đầy đủ nhưng không có điểm bất động.

20. **Ứng dụng:**  
    Liệt kê $3$ ứng dụng của Định lý điểm bất động Banach trong các lĩnh vực khác nhau.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §20, §43
- **Rudin, PMA:** Chapter 4
- **Kreyszig:** *Introductory Functional Analysis* (Không gian Banach)
- **Granas & Dugundji:** *Fixed Point Theory*

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã nghiên cứu các metric tương đương, tính liên tục đều, tính liên tục Lipschitz và ánh xạ co. Hai metric tương đương tô-pô sinh ra cùng một họ tập mở, cùng các dãy hội tụ và cùng lớp hàm liên tục; trên $\mathbb{R}^n$, mọi metric $L^p$ (gồm $d_1, d_2, d_\infty$) đều tương đương mạnh với nhau. Metric tương đương mạnh bảo toàn cả tính chất Cauchy và tính đầy đủ, trong khi metric chỉ tương đương tô-pô có thể khác nhau về tính đầy đủ.

Tính liên tục đều kiểm soát sự biến thiên của hàm một cách đồng nhất trên toàn miền xác định; theo định lý Heine–Cantor, mọi hàm liên tục trên không gian metric compact đều liên tục đều. Tính liên tục Lipschitz kéo theo tính liên tục đều, và trường hợp đặc biệt với hằng số $k < 1$ là ánh xạ co. Định lý điểm bất động Banach đảm bảo mọi ánh xạ co trên không gian metric đầy đủ khác rỗng đều có duy nhất một điểm bất động và dãy lặp hội tụ về đó với tốc độ hàm mũ.

**Tiếp theo:** Lecture 04.03 về **Metric tích và Không gian hàm** — mở rộng cấu trúc metric lên các không gian vô hạn chiều.

---

*"Fixed points are where iteration comes to rest."*

---

**Previous:** [Lecture 04.01: Completeness and Baire Category](/contents/vi/topology-chapter04/04_01_Completeness_Baire_Category/)  
**Next:** [Lecture 04.03: Product Metrics and Function Spaces](/contents/vi/topology-chapter04/04_03_Product_Metrics_Function_Spaces/)
