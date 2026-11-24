---
layout: post
title: "Lecture 02.01: Compact Spaces"
lang: vi
lang-ref: lecture-02-01
chapter: 2
lecture: 1
categories: [chapter02]
tags: [compact-spaces, heine-borel, sequential-compactness, limit-point-compactness]
description: "Không gian compact, Heine-Borel theorem, và các characterizations"
---

**Không gian Compact**

---

## 📖 Tổng quan

Trong toàn bộ môn Tô-pô đại cương, **tính compact** có lẽ là khái niệm khiến người mới học cảm thấy "kỳ lạ" nhất lúc đầu — rồi lại trở thành công cụ được yêu thích nhất khi đã hiểu bản chất. Nếu tập hữu hạn là thứ dễ kiểm soát nhất trong toán học (mọi hàm trên tập hữu hạn đều đạt giá trị lớn nhất và nhỏ nhất), thì **không gian compact chính là "điều tốt thứ nhì sau tính hữu hạn"** trong thế giới vô hạn: nó cho phép ta rút gọn những bài toán vô hạn bước về đúng **một số hữu hạn bước**!

Trong $$\mathbb{R}^n$$, Định lý Heine–Borel cho ta cách nhận diện nhanh: compact $$\iff$$ đóng và bị chặn. Nhưng trên không gian tô-pô tổng quát không có thước đo khoảng cách, định nghĩa phải viết thuần túy qua tập mở:

> **Một không gian tô-pô là compact nếu mọi phủ mở của nó đều có một phủ con hữu hạn.**

![Open cover illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Compact_space.svg/400px-Compact_space.svg.png)  
*Không gian compact: mọi phủ mở đều trích ra được phủ con hữu hạn - Nguồn minh họa khái niệm*

**Mạch bài học:** Bản đồ kiến thức nền (trực giác "phủ mở – phủ con hữu hạn", Heine–Borel vs. không gian vô hạn chiều & bộ ba định lý vàng của compact) → Khung giải thích chậm: cầm tay dựng phủ mở cụ thể chứng minh $$(0, 1]$$ và $$\mathbb{R}$$ không compact → Trực giác & Định nghĩa hình thức → Compact dãy, số Lebesgue & Tychonoff → Bài tập & Tóm tắt.

---

## Bản đồ kiến thức nền: Không gian Compact là gì và vì sao nó quyền năng đến vậy?

### 1. Phủ mở và phủ con hữu hạn: "lọc vô hạn thành hữu hạn"

Hãy hình dung bạn cần thắp sáng một con đường bằng vô hạn ngọn đèn (mỗi ngọn đèn chiếu sáng một tập mở $$U_\alpha$$). Không gian là **compact** nếu *dù ai đó bố trí hệ thống đèn oái oăm đến đâu* (miễn là cả con đường đều được chiếu sáng), bạn luôn có thể tắt bớt và chỉ giữ lại **hữu hạn ngọn đèn** mà con đường vẫn sáng trưng! Chú ý chữ **"mọi phủ mở"** — chỉ cần tồn tại *một* phủ mở không rút gọn được là không gian mất tính compact ngay lập tức.

### 2. Heine–Borel trong $$\mathbb{R}^n$$ và cú sốc ở không gian vô hạn chiều

Trong $$\mathbb{R}^n$$, $$K$$ compact $$\iff K$$ đóng và bị chặn. Nhưng đừng bao giờ đồng nhất hai khái niệm này ngoài $$\mathbb{R}^n$$! Trong không gian mê-tric rời rạc vô hạn $$\mathbb{N}$$ (với $$d(m,n)=1$$ khi $$m \neq n$$), hay hình cầu đơn vị đóng trong không gian Hilbert vô hạn chiều $$\ell^2$$, tập hợp **vừa đóng vừa bị chặn nhưng KHÔNG compact**!

### 3. Bộ ba định lý vàng khiến tính compact trở nên không thể thiếu

- **Ảnh liên tục của tập compact là compact** → kéo theo ngay **Định lý Giá trị Cực trị Weierstrass** (mọi hàm thực liên tục trên không gian compact đều đạt $$\max$$ và $$\min$$!).
- **Song ánh liên tục từ không gian compact sang không gian Hausdorff tự động là phép đồng phôi** (không cần chứng minh $$f^{-1}$$ liên tục nữa!).
- **Định lý Tychonoff:** tích tùy ý (kể cả vô hạn không đếm được!) của các không gian compact vẫn là compact.

---

### Khung giải thích (nên đọc chậm): Cầm tay kiểm chứng tại sao $$(0, 1]$$ và $$\mathbb{R}$$ KHÔNG compact

Để nắm chắc cách phủ định định nghĩa compact (*"tồn tại một phủ mở không có phủ con hữu hạn"*), hãy tự tay kiểm tra hai ví dụ kinh điển:

1. **Chứng minh $$(0, 1]$$ không compact (bị hở ở đầu mút $$0$$):**
   - Chọn họ tập mở trong $$\mathbb{R}$$ (giao với $$(0, 1]$$):
     $$
     \mathcal{U} = \left\{ U_n = \left(\frac{1}{n},\; 2\right) : n \in \mathbb{N}^* \right\}.
     $$
   - **Kiểm tra tính phủ:** Lấy bất kỳ $$x \in (0, 1]$$. Vì $$x > 0$$, theo tính chất Archimedes tồn tại số nguyên dương $$n > \frac{1}{x} \implies \frac{1}{n} < x \le 1 < 2 \implies x \in U_n$$. Vậy $$\bigcup_{n=1}^\infty U_n \supseteq (0, 1]$$.
   - **Kiểm tra không có phủ con hữu hạn:** Giả sử ta chọn bất kỳ $$k$$ tập hữu hạn $$U_{n_1}, U_{n_2}, \dots, U_{n_k}$$. Đặt $$M = \max(n_1, \dots, n_k)$$. Vì các tập lồng nhau $$U_1 \subset U_2 \subset \dots \subset U_M$$, hợp của $$k$$ tập này chỉ bằng đúng:
     $$
     U_{n_1} \cup \dots \cup U_{n_k} = U_M = \left(\frac{1}{M},\; 2\right).
     $$
     Lấy ngay điểm $$x_0 = \frac{1}{2M} \in (0, 1]$$: rõ ràng $$0 < \frac{1}{2M} < \frac{1}{M}$$, nên $$x_0 \notin U_M$$! Mọi phủ con hữu hạn đều **bỏ sót** đoạn $$\left(0, \frac{1}{M}\right]$$ → $$(0, 1]$$ **không compact**!
2. **Chứng minh $$\mathbb{R}$$ không compact (không bị chặn):**
   - Chọn phủ mở $$\mathcal{V} = \{(-n, n) : n \in \mathbb{N}^*\}$$. Với mọi tập con hữu hạn có chỉ số lớn nhất $$M$$, hợp của chúng là $$(-M, M)$$, luôn bỏ sót điểm $$x = M + 1 \in \mathbb{R}$$ → $$\mathbb{R}$$ **không compact**!

---

## 🎯 Từ trực giác đến hình thức

### Phép ẩn dụ phủ mở

Hãy tưởng tượng một tập hợp các phòng được phủ bởi nhiều "khu vực phục vụ" (tương ứng với các tập mở). Không gian là **compact** nếu dù ta có một họ vô hạn các tập mở phủ kín toàn bộ không gian, ta vẫn luôn chọn ra được **hữu hạn** tập trong họ đó mà vẫn đủ phủ hết không gian.

Chẳng hạn, xét $\mathbb{N}$ với tô-pô rời rạc và họ phủ mở $U_n = \{1, 2, \dots, n\}$ ($n \in \mathbb{N}$): hợp $\bigcup_{n=1}^{\infty} U_n = \mathbb{N}$, nhưng bất kỳ họ con hữu hạn nào cũng chỉ phủ được đến chỉ số lớn nhất $N$ chứ không phủ hết $\mathbb{N}$, do đó $\mathbb{N}$ không compact. Trái lại, đoạn đóng $[0, 1]$ là không gian compact.

---

## 📐 Định nghĩa hình thức

### 1. Không gian compact (Compact Spaces)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phủ mở — Open Cover):**  
Họ các tập mở $\{U_\alpha\}_{\alpha \in I} \subseteq \tau$ là một **phủ mở** của $X$ nếu:

$$
X = \bigcup_{\alpha \in I} U_\alpha
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phủ con — Subcover):**  
Họ con $\{U_\beta\}_{\beta \in J}$ (với $J \subseteq I$) là một **phủ con** nếu nó vẫn phủ toàn bộ $X$:

$$
X = \bigcup_{\beta \in J} U_\beta, \quad J \subseteq I
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian compact — Compact Space):**  
Không gian $X$ là **compact** nếu mọi phủ mở của $X$ đều có ít nhất một **phủ con hữu hạn**:

$$
\forall \{U_\alpha\}_{\alpha \in I} \text{ open cover}: \exists \text{ finite } J \subseteq I: X = \bigcup_{\alpha \in J} U_\alpha
$$
</div>

**Các ví dụ cơ bản:**
1. **Không gian hữu hạn:** Mọi không gian hữu hạn với tô-pô bất kỳ đều compact vì chỉ có hữu hạn tập con (nên mọi phủ mở đều hữu hạn).
2. **Đoạn $[0, 1]$:** Compact theo Định lý Heine–Borel (chứng minh ở mục 3).
3. **$\mathbb{N}$ với tô-pô rời rạc:** Không compact, vì phủ mở $\{\{n\} : n \in \mathbb{N}\}$ không có phủ con hữu hạn.
4. **Khoảng mở $(0, 1)$:** Không compact, vì phủ mở $U_n = (1/n, 1)$ ($n \ge 2$) phủ kín $(0, 1)$ nhưng mọi hợp hữu hạn $U_{n_1} \cup \dots \cup U_{n_k} = (1/N, 1)$ (với $N = \max n_i$) đều bỏ sót $(0, 1/N]$.

---

### 2. Các tính chất của không gian compact

<div class="textbook-theorem" markdown="1">
**Định lý (Tập con compact trong không gian Hausdorff):**  
Nếu $K \subseteq X$ compact và $X$ là không gian Hausdorff, thì $K$ là **tập đóng** trong $X$.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Phác thảo chứng minh:**  
Lấy điểm bất kỳ $x \notin K$. Với mỗi $y \in K$, do $X$ Hausdorff nên tồn tại hai tập mở rời nhau $U_y \ni x$ và $V_y \ni y$. Họ $\{V_y\}_{y \in K}$ là phủ mở của $K$ nên trích ra được phủ con hữu hạn $V_{y_1}, \dots, V_{y_n}$. Khi đó $U = U_{y_1} \cap \dots \cap U_{y_n}$ là một tập mở chứa $x$ và rời với $K$. Do đó $X \setminus K$ mở, tức $K$ đóng. ∎
</div>

*(Lưu ý: giả thiết Hausdorff là thiết yếu; trong tô-pô tầm thường, mọi tập con đều compact nhưng không nhất thiết đóng.)*

---

<div class="textbook-theorem" markdown="1">
**Định lý (Tập con đóng của không gian compact):**  
Nếu $X$ compact và $F \subseteq X$ đóng, thì $F$ (với tô-pô con) là **compact**.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Cho $\{U_\alpha\}$ là một phủ của $F$ bởi các tập mở trong $X$. Bổ sung thêm tập mở $X \setminus F$, ta thu được phủ mở $\{U_\alpha\} \cup \{X \setminus F\}$ của $X$. Vì $X$ compact nên tồn tại phủ con hữu hạn; bỏ $X \setminus F$ (nếu có mặt) ta còn lại phủ con hữu hạn của $F$. ∎
</div>

<div class="textbook-theorem" markdown="1">
**Nhận xét:** Trong không gian Hausdorff $X$, mọi tập con compact đều đóng; nếu $X$ là không gian mê-tric thì mọi tập con compact đều đóng và bị chặn (chiều đảo chỉ đúng trong những không gian đặc biệt như $\mathbb{R}^n$, theo Định lý Heine–Borel).
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Ảnh liên tục của không gian compact):**  
Nếu $f: X \to Y$ liên tục và $X$ compact, thì ảnh **$f(X)$ compact**.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Cho $\{V_\alpha\}$ là một phủ của $f(X)$ bởi các tập mở trong $Y$. Do $f$ liên tục, $\{f^{-1}(V_\alpha)\}$ là phủ mở của $X$, nên có phủ con hữu hạn $f^{-1}(V_{\alpha_1}), \dots, f^{-1}(V_{\alpha_n})$. Suy ra $f(X) \subseteq V_{\alpha_1} \cup \dots \cup V_{\alpha_n}$. ∎
</div>

**Hệ quả:** Tính compact là một **bất biến tô-pô**.

---

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý Giá trị Cực trị — Extreme Value Theorem, EVT):**  
Nếu $X$ compact khác rỗng và $f: X \to \mathbb{R}$ liên tục, thì $f$ đạt **giá trị lớn nhất và giá trị nhỏ nhất** trên $X$:

$$
\exists x_{\max}, x_{\min} \in X: \forall x \in X: f(x_{\min}) \leq f(x) \leq f(x_{\max})
$$
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Vì $X$ compact và $f$ liên tục nên $f(X) \subseteq \mathbb{R}$ compact, suy ra $f(X)$ đóng và bị chặn (theo Heine–Borel). Do bị chặn và khác rỗng nên $\sup f(X)$ và $\inf f(X)$ tồn tại hữu hạn; do $f(X)$ đóng nên hai giá trị này thuộc $f(X)$.
</div>

![Extreme Value Theorem](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Extreme_value_theorem.svg/400px-Extreme_value_theorem.svg.png)  
*Định lý Giá trị Cực trị: hàm liên tục trên không gian compact đạt cực đại và cực tiểu - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Extreme_value_theorem.svg)*

---

### 3. Định lý Heine–Borel

**Định lý Heine–Borel:**  
Trong **$\mathbb{R}^n$** với tô-pô Euclid, một tập con $K \subseteq \mathbb{R}^n$ là compact khi và chỉ khi $K$ **đóng và bị chặn**.

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh trong $\mathbb{R}$:**
</div>

**Chiều thuận ($\Rightarrow$):** Nếu $K$ compact, thì vì $\mathbb{R}$ Hausdorff nên $K$ đóng. Hơn nữa họ $\{(-n, n)\}_{n \in \mathbb{N}}$ là phủ mở của $K$, nên tồn tại phủ con hữu hạn và do đó $K \subseteq (-N, N)$ (bị chặn).

**Chiều đảo ($\Leftarrow$):** Nếu $K$ đóng và bị chặn, thì $K$ là tập con đóng của một đoạn đóng $[a, b]$ nào đó; do đó chỉ cần chứng minh $[a, b]$ compact.  
Giả sử phản chứng $[a, b]$ có phủ mở $\{U_\alpha\}$ không có phủ con hữu hạn. Chia đôi $[a, b]$ thành $[a, m]$ và $[m, b]$ với $m = (a + b)/2$: ít nhất một nửa cũng không có phủ con hữu hạn, gọi là $[a_1, b_1]$. Lặp lại quy trình chia đôi, ta thu được dãy đoạn lồng nhau $[a, b] \supseteq [a_1, b_1] \supseteq [a_2, b_2] \supseteq \dots$ với độ dài $b_n - a_n = (b - a)/2^n \to 0$. Theo tính đầy đủ của $\mathbb{R}$, tồn tại điểm chung $x \in \bigcap_n [a_n, b_n]$. Vì $x \in [a, b]$, có một tập mở $U_{\alpha_0}$ chứa $x$, nên tồn tại $\varepsilon > 0$ sao cho $(x - \varepsilon, x + \varepsilon) \subseteq U_{\alpha_0}$. Chọn $n$ đủ lớn để $b_n - a_n < \varepsilon$, khi đó $[a_n, b_n] \subseteq U_{\alpha_0}$, mâu thuẫn với việc $[a_n, b_n]$ không có phủ con hữu hạn. ∎

<div class="textbook-theorem" markdown="1">
**Hệ quả:** Các đoạn đóng $[a, b]$ trong $\mathbb{R}$ và các hình cầu đóng trong $\mathbb{R}^n$ đều compact.
</div>

Ngược lại, các tập $(a, b)$, $[a, b)$, $(a, b]$, $\mathbb{R}$ và $\mathbb{N}$ đều không compact (vì không đóng hoặc không bị chặn).

---

### 4. Tính compact dãy (Sequential Compactness)

Trong không gian mê-tric, tính compact có thêm các đặc trưng tương đương qua dãy và điểm tụ.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Compact dãy — Sequentially Compact):**  
Không gian $X$ là **compact dãy** nếu mọi dãy trong $X$ đều chứa một **dãy con hội tụ** trong $X$:

$$
\forall (x_n) \text{ sequence}: \exists \text{ subsequence } (x_{n_k}), \exists x \in X: x_{n_k} \to x
$$
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Trong không gian mê-tric):**  
Đối với một không gian mê-tric $(X, d)$, ba tính chất sau **tương đương**:
1. Compact (theo phủ mở).
2. Compact dãy.
3. Compact điểm tụ (*limit point compact*: mọi tập con vô hạn đều có điểm tụ trong $X$).
</div>

<div class="textbook-proof" markdown="1">
**Ghi chú chứng minh:** Chứng minh đầy đủ sử dụng bổ đề số Lebesgue và tính hoàn toàn bị chặn.
</div>

Trường hợp riêng cho đoạn $[0, 1]$ chính là Định lý Bolzano–Weierstrass. Lưu ý rằng trong không gian tô-pô tổng quát (không mê-tric), ba tính chất này không còn tương đương.

---

### 5. Không gian compact địa phương (Locally Compact Spaces)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Compact địa phương):**  
Không gian $X$ là **compact địa phương** (*locally compact*) nếu mỗi điểm $x \in X$ đều có ít nhất một lân cận compact.
</div>

Ví dụ: $\mathbb{R}^n$ là không gian compact địa phương (vì quanh mỗi $x$ có khối hộp đóng $[x - 1, x + 1]^n$ compact). Ngược lại, không gian Hilbert vô hạn chiều và tập số hữu tỉ $\mathbb{Q}$ không compact địa phương.

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi không gian Hausdorff compact địa phương (không compact) đều có một **compact hóa một điểm** (*one-point compactification*), chẳng hạn $\mathbb{R}^n \cup \{\infty\} \cong S^n$.
</div>

---

### 6. Không gian mê-tric compact

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Không gian mê-tric $(X, d)$ là compact khi và chỉ khi nó **đầy đủ và hoàn toàn bị chặn**.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Hoàn toàn bị chặn — Totally Bounded):**  
Với mọi $\varepsilon > 0$, không gian $X$ có thể phủ được bởi hữu hạn hình cầu mở bán kính $\varepsilon$.
</div>

Chẳng hạn, $[0, 1]$ đầy đủ và hoàn toàn bị chặn nên compact; $\mathbb{R}$ đầy đủ nhưng không hoàn toàn bị chặn; còn $(0, 1)$ hoàn toàn bị chặn nhưng không đầy đủ.

**Bổ đề số Lebesgue (Lebesgue Number Lemma):**  
Nếu $(X, d)$ là không gian mê-tric compact và $\{U_\alpha\}$ là một phủ mở của $X$, thì tồn tại số $\delta > 0$ (gọi là *số Lebesgue* của phủ mở) sao cho mọi tập con có đường kính nhỏ hơn $\delta$ đều nằm trọn trong ít nhất một tập của phủ mở:

$$
\forall A \subseteq X: \text{diam}(A) < \delta \implies \exists \alpha: A \subseteq U_\alpha
$$

---

### 7. Định lý Tychonoff (Phát biểu)

**Định lý Tychonoff:**

> **Tích tùy ý của các không gian compact là compact** (đối với tô-pô tích).

$$
\forall i \in I: X_i \text{ compact} \implies \prod_{i \in I} X_i \text{ compact}
$$

Định lý Tychonoff tương đương với Tiên đề Lựa chọn trong ZF và không còn đúng đối với tô-pô hộp. Chẳng hạn, khối lập phương Hilbert $[0, 1]^{\mathbb{N}}$ là compact. Định lý này là nền tảng cho định lý Banach–Alaoglu trong giải tích hàm và lý thuyết compact hóa.

<div class="textbook-proof" markdown="1">
**Ghi chú chứng minh:** Chứng minh thường dùng định lý tiền cơ sở Alexander hoặc bổ đề siêu lọc.
</div>

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Eduard Heine** - *"Über trigonometrische Reihen"* (1872)  
   *Tính liên tục đều trên các đoạn đóng bị chặn.*

2. **Émile Borel** - *"Sur quelques points de la théorie des fonctions"* (1895)  
   *Tính chất phủ con hữu hạn.*

3. **Andrey Tychonoff** - *"Über die topologische Erweiterung von Räumen"* (1930)  
   *Chứng minh định lý Tychonoff.*

4. **Pavel Alexandroff & Pavel Urysohn** - *"Mémoire sur les espaces topologiques compacts"* (1929)  
   *Nghiên cứu có hệ thống về tính compact.*

### Giáo trình

5. **James R. Munkres** - *Topology*, 2nd Ed., **§26–27: Compact Spaces**  
   *Trình bày rõ ràng, chuẩn mực.*

6. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 10**  
   *Trình bày dễ tiếp cận.*

7. **Stephen Willard** - *General Topology*, **Chapter 5**  
   *Trình bày đầy đủ.*

8. **John L. Kelley** - *General Topology*, **Chapter 5**  
   *Trình bày nâng cao theo hướng lưới.*

---

## 🔗 Ứng dụng và liên hệ

### Giải tích — Tối ưu hóa
Định lý Giá trị Cực trị bảo đảm sự tồn tại cực đại và cực tiểu toàn cục của hàm liên tục trên miền compact.

### Giải tích hàm — Định lý Banach–Alaoglu
Hình cầu đơn vị đóng trong không gian đối ngẫu của một không gian định chuẩn là compact theo tô-pô yếu* (suy từ định lý Tychonoff), là công cụ cốt lõi trong lý thuyết phương trình đạo hàm riêng.

### Phương trình vi phân và lý thuyết trò chơi
Định lý tồn tại nghiệm Peano cho phương trình vi phân thường và định lý tồn tại cân bằng Nash cho trò chơi hữu hạn đều dựa vào tính compact để trích dãy con hội tụ hoặc áp dụng định lý điểm bất động.

---

## Video tham khảo

- **xem trước** [The Concept So Much of Modern Math is Built On | Compactness](https://www.youtube.com/watch?v=td7Nz9ATyWY) — Morphocular, tiếng Anh. Vì sao phủ mở và phủ con hữu hạn là cách đúng để nói một tập không bị loãng ra vô hạn.
- [Basic Topology 4 | Compact Sets](https://www.youtube.com/watch?v=pYli4-0hzSs) — The Bright Side of Mathematics, tiếng Anh. Định nghĩa compact và các tính chất đầu tiên, trong chuỗi Basic Topology.
- [Không gian tô-pô compact](https://www.youtube.com/watch?v=_o4E8YTaDk4) — Cuong Nguyen, tiếng Việt. Không gian compact nói bằng tiếng Việt, để nghe lại định nghĩa trong ngôn ngữ của bài.

## 🧩 Bài tập

### Định nghĩa tính compact

1. **Kiểm tra tính compact:**  
   Các không gian sau có compact không?
   - a) $\{1, 2, 3\}$ với tô-pô rời rạc
   - b) $\mathbb{N}$ với tô-pô rời rạc
   - c) $[0, 1]$
   - d) $(0, 1)$

2. **Tìm phủ mở:**  
   Tìm một phủ mở của $(0, 1) \subset \mathbb{R}$ không có phủ con hữu hạn.

3. **Không gian hữu hạn:**  
   Chứng minh mọi không gian hữu hạn với tô-pô bất kỳ đều compact.

### Định lý Heine–Borel

4. **Đóng và bị chặn trong $\mathbb{R}$:**  
   Các tập sau trong $\mathbb{R}$ có compact không?
   - a) $[0, 1] \cup [2, 3]$
   - b) $\{1/n : n \in \mathbb{N}\} \cup \{0\}$
   - c) $[0, \infty)$
   - d) Tập Cantor

5. **Ví dụ trong $\mathbb{R}^2$:**  
   Các tập sau trong $\mathbb{R}^2$ có compact không?
   - a) Đĩa đóng đơn vị $\{(x, y) : x^2 + y^2 \le 1\}$
   - b) Đĩa mở đơn vị $\{(x, y) : x^2 + y^2 < 1\}$
   - c) Đường tròn đơn vị $S^1$

### Tính chất

6. **Ảnh liên tục:**  
   Xét $f: [0, 1] \to \mathbb{R}$ cho bởi $f(x) = 1/x$ nếu $x > 0$ và $f(0) = 0$.
   - $f$ có liên tục không?
   - $f([0, 1])$ có compact không?
   - Vì sao điều này không mâu thuẫn với định lý ảnh liên tục?

7. **Tập con đóng:**  
   Cho $K \subseteq \mathbb{R}$ compact và $F \subseteq K$ đóng. Chứng minh $F$ compact.

8. **Giá trị cực trị:**  
   Áp dụng Định lý Giá trị Cực trị, tìm giá trị lớn nhất và nhỏ nhất của $f(x) = x^2 - 2x$ trên $[0, 3]$.

### Tính compact dãy

9. **Bolzano–Weierstrass:**  
   Đoạn $[-1, 1]$ là compact dãy. Giải thích vì sao dãy $x_n = \sin(n)$ trong $[-1, 1]$ có một dãy con hội tụ (không cần tìm công thức tường minh).

10. **Phản ví dụ:**  
    Tìm một dãy trong $\mathbb{N}$ (với tô-pô rời rạc) không có dãy con hội tụ.

### Nâng cao

11. **Tích hai đoạn đóng:**  
    Chứng minh $[0, 1] \times [0, 1]$ compact (dùng Định lý Heine–Borel trong $\mathbb{R}^2$ hoặc Định lý Tychonoff).

12. **Khối lập phương Hilbert:**  
    Giải thích vì sao $H = [0, 1]^{\mathbb{N}}$ compact theo tô-pô tích.

13. **Compact địa phương:**  
    Chứng minh $\mathbb{R}$ là không gian compact địa phương nhưng không compact.

14. **Compact hóa một điểm:**  
    Mô tả cấu trúc tô-pô trên $\mathbb{R} \cup \{\infty\}$ sao cho nó đồng phôi với đường tròn $S^1$.

15. **Số Lebesgue:**  
    Trên $[0, 1]$ với tô-pô Euclid, xét phủ mở $\{[0, 0{,}6), (0{,}4, 1]\}$. Tìm một số Lebesgue $\delta > 0$ cho phủ mở này.

### Câu hỏi suy ngẫm

16. **Compact và tập đóng:**  
    Vì sao trong không gian tô-pô tổng quát, tập con compact không nhất thiết là tập đóng nếu thiếu giả thiết Hausdorff?

17. **Compact dãy và compact theo phủ mở:**  
    Tìm hiểu vì sao hai khái niệm này tương đương trong không gian mê-tric nhưng không tương đương trong không gian tô-pô tổng quát.

18. **Ứng dụng:**  
    Liệt kê một số định lý quan trọng trong giải tích và tô-pô sử dụng trực tiếp giả thiết compact.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §26–28 (Compact Spaces, Products)
- **Morris, Topology Without Tears:** Chapter 10
- **Willard, General Topology:** Chapter 5
- **Kelley, General Topology:** Chapter 5 (Nets and Compactness)

---

## 🎓 Tóm tắt

✅ **Không gian compact:** Mọi phủ mở đều có phủ con hữu hạn.  
✅ **Định lý Heine–Borel:** Trong $\mathbb{R}^n$, compact $\iff$ đóng và bị chặn.  
✅ **Tập con đóng & Ảnh liên tục:** Tập con đóng của không gian compact là compact; ảnh liên tục của không gian compact là compact.  
✅ **Định lý Giá trị Cực trị:** Hàm thực liên tục trên không gian compact khác rỗng đạt giá trị lớn nhất và nhỏ nhất.  
✅ **Không gian mê-tric:** Compact $\iff$ compact dãy $\iff$ đầy đủ và hoàn toàn bị chặn.  
✅ **Định lý Tychonoff:** Tích tùy ý các không gian compact là compact trong tô-pô tích.

**Tiếp theo:** Bài 02.02 sẽ trình bày chi tiết về **Tính compact địa phương và Phép compact hóa** (*Local Compactness and Compactification*).

---

*"Compact spaces are to topology what finite sets are to set theory."* — Standard analogy

🎯 **Hãy thực hành nhận diện tập compact trong $\mathbb{R}^n$ bằng Định lý Heine–Borel và luyện tập kỹ thuật trích phủ con hữu hạn.** 🎯

---

**Previous:** [Lecture 02.00: Connected Spaces](/contents/vi/topology-chapter02/02_00_Connected_Spaces/)  
**Next:** [Lecture 02.02: Applications of Compactness](/contents/vi/topology-chapter02/02_02_Applications_Compactness/)
