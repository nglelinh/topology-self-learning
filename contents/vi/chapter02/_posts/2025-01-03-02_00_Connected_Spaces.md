---
layout: post
title: "Lecture 02.00: Connected Spaces"
lang: vi
lang-ref: lecture-02-00
chapter: 2
lecture: 0
categories: [chapter02]
tags: [connected-spaces, path-connected, components, disconnected]
description: "Không gian liên thông, path-connectedness, và connected components"
---

**Không gian Liên thông**

---

## 📖 Tổng quan

Bạn có thể kéo giãn một đoạn dây thun $$[0, 1]$$ thành dài gấp trăm lần, uốn cong nó thành chữ S hay hình xoắn ốc — nhưng nếu không dùng kéo cắt đứt, bạn **không bao giờ** biến một mảnh liền thành hai mảnh rời nhau được. Bước sang Chương 02, ta gặp bất biến tô-pô đầu tiên biến trực giác "liền một mảnh" ấy thành vũ khí chứng minh cực kỳ sắc bén: **tính liên thông (connectedness)**.

Điều bất ngờ là chỉ từ định nghĩa *"không thể tách $$X$$ thành hai tập mở rời nhau khác rỗng"*, ta không chỉ chứng minh được **Định lý Giá trị Trung gian** nổi tiếng của giải tích trong vài dòng, mà còn phân biệt được một cách dễ dàng những hình dạng tưởng chừng rất giống nhau — như đoạn thẳng $$[0, 1]$$, đường tròn $$S^1$$ và chữ số 8!

![Connected vs Disconnected](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Connected_and_disconnected_spaces.svg/500px-Connected_and_disconnected_spaces.svg.png)  
*Không gian liên thông (trái) và không liên thông (phải) - Nguồn minh họa khái niệm*

**Mạch bài học:** Kiến thức cần nhớ (liên thông qua tập vừa đóng vừa mở, liên thông đường vs. liên thông thường & bất biến "bỏ 1 điểm") → Giải thích: cầm tay chứng minh đoạn $$[0, 1]$$ không đồng phôi với đường tròn $$S^1$$ bằng kỹ thuật bỏ 1 điểm → Trực giác & Định nghĩa hình thức → Định lý Giá trị Trung gian & Thành phần liên thông → Bài tập & Tóm tắt.

---

## Kiến thức cần nhớ: Tính liên thông và Liên thông đường nghiên cứu những gì?

### 1. Liên thông (Connectedness): không có tập con "vừa đóng vừa mở" không tầm thường

Một không gian $$X$$ bị **không liên thông** khi ta viết được $$X = U \cup V$$ với $$U, V$$ mở, rời nhau và đều khác rỗng. Điều này tương đương hoàn toàn với sự tồn tại một tập con $$U \neq \emptyset, X$$ **vừa mở vừa đóng (clopen)**, hoặc một ánh xạ liên tục toàn ánh $$f: X \to \{0, 1\}$$ (với tô-pô rời rạc).

### 2. Liên thông đường (Path-Connectedness): mạnh hơn liên thông thông thường!

$$X$$ gọi là **liên thông đường** nếu mọi cặp điểm $$x, y \in X$$ đều nối được bằng một đường cong liên tục $$\gamma: [0, 1] \to X$$ ($$\gamma(0) = x, \gamma(1) = y$$). Mọi không gian liên thông đường đều liên thông, nhưng chiều ngược lại **không đúng** — phản ví dụ kinh điển là **đường cong sin của nhà tô-pô (topologist's sine curve)** $$S = \{(x, \sin(1/x)) : x \in (0, 1]\} \cup (\{0\} \times [-1, 1])$$, liền thành một mảnh (vì là bao đóng của tập liên thông) nhưng không có đường cong liên tục nào chạy từ nhánh dao động sang đoạn trục tung!

### 3. Bất biến tô-pô cực mạnh: đếm số thành phần liên thông khi bỏ đi một điểm

Ảnh liên tục của không gian liên thông luôn liên thông. Nhờ đó, nếu $$f: X \to Y$$ là phép đồng phôi, thì khi bỏ đi một điểm $$p \in X$$ và ảnh $$f(p) \in Y$$, hai phần còn lại $$X \setminus \{p\}$$ và $$Y \setminus \{f(p)\}$$ **phải có cùng số thành phần liên thông**! Đây là công cụ nhanh nhất để phân biệt các không gian 1 chiều.

---

### Giải thích: Cầm tay chứng minh $$[0, 1] \not\cong S^1$$ bằng kỹ thuật "bỏ 1 điểm"

Giả sử phản chứng rằng tồn tại một phép đồng phôi $$f: [0, 1] \to S^1$$. Hãy tự tay kiểm tra điều gì xảy ra khi ta rút một điểm duy nhất ra khỏi hai không gian:

1. **Chọn điểm cắt bên miền nguồn:** Lấy điểm giữa $$p = \frac{1}{2} \in [0, 1]$$ và gọi ảnh của nó là $$q = f\!\left(\frac{1}{2}\right) \in S^1$$.
2. **Thu hẹp phép đồng phôi:** Khi bỏ $$p$$ và $$q$$, ánh xạ thu hẹp
   $$
   \tilde{f}: [0, 1] \setminus \Bigl\{\frac{1}{2}\Bigr\} \longrightarrow S^1 \setminus \{q\}
   $$
   vẫn là một **phép đồng phôi** (song ánh liên tục hai chiều theo tô-pô con).
3. **Đếm số thành phần liên thông ở vế trái:**
   $$
   [0, 1] \setminus \Bigl\{\frac{1}{2}\Bigr\} = \Bigl[0, \frac{1}{2}\Bigr) \;\cup\; \Bigl(\frac{1}{2}, 1\Bigr].
   $$
   Hai tập $$U = \bigl[0, \tfrac{1}{2}\bigr)$$ và $$V = \bigl(\tfrac{1}{2}, 1\bigr]$$ đều mở trong không gian con, rời nhau và khác rỗng → vế trái **KHÔNG liên thông** (có đúng **2 thành phần liên thông**).
4. **Đếm số thành phần liên thông ở vế phải:** Bỏ bất kỳ 1 điểm $$q = (\cos \theta_0, \sin \theta_0)$$ nào khỏi đường tròn $$S^1$$, phần còn lại đồng phôi với khoảng mở $$(\theta_0, \theta_0 + 2\pi) \subset \mathbb{R}$$ qua ánh xạ $$\theta \mapsto (\cos \theta, \sin \theta)$$ → vế phải **LIÊN THÔNG** (chỉ có **1 thành phần liên thông**)!
5. **Mâu thuẫn!** Một không gian không liên thông không thể đồng phôi với một không gian liên thông → kết luận chặt chẽ: **$$[0, 1] \not\cong S^1$$**! (Với đúng chiêu này, thử bỏ 1 điểm cũng chứng minh ngay $$[0, 1] \not\cong (0, 1)$$ vì bỏ đầu mút $$0$$ của $$[0,1]$$ vẫn liên thông, còn bỏ *bất kỳ* điểm nào của $$(0,1)$$ đều tách đôi!)

---

## 🎯 Từ trực giác đến hình thức

### Ý tưởng chia cắt không gian

Một sợi dây liền là một vật thể liên thông; muốn làm nó mất liên thông, ta phải cắt nó thành hai đoạn tách rời. Trong ngôn ngữ tô-pô, "chia cắt" một không gian $X$ nghĩa là tìm được hai tập mở $U, V$ sao cho:
- $U \neq \emptyset$ và $V \neq \emptyset$;
- $U \cap V = \emptyset$;
- $U \cup V = X$.

Nếu tồn tại một cặp $(U, V)$ như vậy thì $X$ **không liên thông**; ngược lại, nếu không tồn tại thì $X$ **liên thông**. Chẳng hạn với $X = [0, 1] \cup [2, 3]$, hai tập $U = (-1, 1{,}5) \cap X = [0, 1]$ và $V = (1{,}5, 4) \cap X = [2, 3]$ đều mở trong tô-pô con, khác rỗng, rời nhau và có hợp bằng $X$, nên $X$ không liên thông. Trái lại, đoạn $[0, 2]$ không thể phân tách theo cách này nên nó liên thông.

---

## 📐 Định nghĩa hình thức

### 1. Không gian liên thông (Connected Spaces)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không liên thông — Disconnected):**  
Không gian tô-pô $X$ là **không liên thông** nếu tồn tại hai tập mở $U, V \in \tau$ sao cho:
1. $U \neq \emptyset$ và $V \neq \emptyset$;
2. $U \cap V = \emptyset$;
3. $U \cup V = X$.
</div>

Khi đó cặp $\{U, V\}$ được gọi là một **phép phân ly** (*separation*) của $X$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Liên thông — Connected):**  
Không gian $X$ là **liên thông** nếu nó không tồn tại bất kỳ phép phân ly nào.
</div>

**Ví dụ 1: Đoạn $[0, 1]$ liên thông trong $\mathbb{R}$**

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Phác thảo chứng minh:** Giả sử phản chứng tồn tại phép phân ly $\{U, V\}$ của $[0, 1]$. Không mất tính tổng quát, giả sử $0 \in U$. Vì $V \neq \emptyset$, chọn một điểm $b \in V$ ($0 < b \le 1$) và đặt $s = \sup(U \cap [0, b]) \in [0, b]$.
- Nếu $s \in U$, thì $s < b$ (vì $b \in V$ rời với $U$). Do $U$ mở trong $[0, 1]$, tồn tại $\varepsilon > 0$ sao cho $[s, s + \varepsilon) \subseteq U \cap [0, b]$, mâu thuẫn với định nghĩa $s = \sup(U \cap [0, b])$.
- Nếu $s \in V$, thì $s > 0$ (vì $0 \in U$). Do $V$ mở trong $[0, 1]$, tồn tại $\varepsilon > 0$ sao cho $(s - \varepsilon, s] \subseteq V$, suy ra $U \cap [0, b]$ không chứa điểm nào trong $(s - \varepsilon, s]$, mâu thuẫn với $s = \sup(U \cap [0, b])$.
- Nếu $s \notin U \cup V$, mâu thuẫn với $U \cup V = [0, 1]$. ∎
</div>

**Ví dụ 2: Tập số hữu tỉ $\mathbb{Q}$ không liên thông trong $\mathbb{R}$**

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Hai tập $U = \mathbb{Q} \cap (-\infty, \sqrt{2})$ và $V = \mathbb{Q} \cap (\sqrt{2}, \infty)$ đều mở trong tô-pô con của $\mathbb{Q}$, khác rỗng, rời nhau và có hợp bằng $\mathbb{Q}$, nên $\{U, V\}$ là một phép phân ly của $\mathbb{Q}$.
</div>

**Ví dụ 3: Tô-pô rời rạc**  
Mọi không gian có nhiều hơn $1$ điểm với tô-pô rời rạc đều không liên thông.

<div class="textbook-proof" markdown="1">
**Chứng minh:** Chọn $x \in X$; khi đó $U = \{x\}$ và $V = X \setminus \{x\}$ tạo thành một phép phân ly của $X$.
</div>

**Ví dụ 4: Tô-pô tầm thường**  
Mọi không gian với tô-pô tầm thường đều liên thông.

<div class="textbook-proof" markdown="1">
**Chứng minh:** Vì chỉ có $\emptyset$ và $X$ là tập mở nên không thể tồn tại hai tập mở khác rỗng rời nhau.
</div>

---

### 2. Các đặc trưng tương đương

<div class="textbook-theorem" markdown="1">
**Định lý (Các đặc trưng tương đương của tính liên thông):**  
Với không gian tô-pô $X$, bốn mệnh đề sau **tương đương**:
</div>

**(1)** $X$ liên thông.

**(2)** Chỉ có $\emptyset$ và $X$ là các tập vừa mở vừa đóng (*clopen*) trong $X$.

**(3)** Không tồn tại toàn ánh liên tục $f: X \to \{0, 1\}$ (với $\{0, 1\}$ mang tô-pô rời rạc).

**(4)** Mọi ánh xạ liên tục $f: X \to \{0, 1\}$ đều là ánh xạ hằng.

<div class="textbook-proof" markdown="1">
**Chứng minh:**
</div>

- **(1 $\Rightarrow$ 2):** Nếu tồn tại tập vừa mở vừa đóng $A \subseteq X$ với $A \neq \emptyset, X$, thì $U = A$ và $V = X \setminus A$ tạo thành một phép phân ly của $X$, mâu thuẫn với (1).
- **(2 $\Rightarrow$ 3):** Nếu có toàn ánh liên tục $f: X \to \{0, 1\}$, thì $f^{-1}(\{0\})$ vừa mở vừa đóng (vì $\{0\}$ vừa mở vừa đóng trong $\{0, 1\}$) và khác $\emptyset, X$ (vì $f$ toàn ánh), mâu thuẫn với (2).
- **(3 $\Rightarrow$ 4):** Hiển nhiên (một ánh xạ vào $\{0, 1\}$ không toàn ánh thì chỉ nhận đúng một giá trị).
- **(4 $\Rightarrow$ 1):** Nếu $\{U, V\}$ là một phép phân ly của $X$, định nghĩa $f: X \to \{0, 1\}$ bởi $f(x) = 0$ với $x \in U$ và $f(x) = 1$ với $x \in V$. Khi đó $f$ liên tục nhưng không hằng, mâu thuẫn với (4). ∎

---

### 3. Các tính chất của không gian liên thông

<div class="textbook-theorem" markdown="1">
**Định lý (Ảnh liên tục của không gian liên thông):**  
Nếu $f: X \to Y$ liên tục và $X$ liên thông, thì ảnh $f(X)$ liên thông.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Giả sử phản chứng $f(X)$ có phép phân ly $\{U, V\}$ (mở trong $f(X)$). Khi đó $f^{-1}(U)$ và $f^{-1}(V)$ là hai tập mở trong $X$, rời nhau, khác rỗng (do $U, V \subseteq f(X)$ khác rỗng) và có hợp bằng $X$, tạo thành phép phân ly của $X$ — mâu thuẫn. ∎
</div>

**Hệ quả:** Tính liên thông là một **tính chất tô-pô** (bất biến qua phép đồng phôi).

---

<div class="textbook-theorem" markdown="1">
**Định lý (Hợp của các không gian con liên thông):**  
Cho $\{A_\alpha\}_{\alpha \in I}$ là một họ các không gian con liên thông của $X$. Nếu $\bigcap_{\alpha \in I} A_\alpha \neq \emptyset$, thì hợp $\bigcup_{\alpha \in I} A_\alpha$ là không gian liên thông.
</div>

![Union of connected spaces](https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Connected_union.svg/400px-Connected_union.svg.png)  
*Hợp của các tập liên thông có điểm chung - Nguồn minh họa khái niệm*

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Đặt $A = \bigcup_\alpha A_\alpha$ và chọn $x_0 \in \bigcap_\alpha A_\alpha$. Xét ánh xạ liên tục bất kỳ $f: A \to \{0, 1\}$, giả sử $f(x_0) = 0$. Với mỗi $\alpha$, ánh xạ thu hẹp $f|_{A_\alpha}$ liên tục trên không gian liên thông $A_\alpha$ nên là ánh xạ hằng, do đó $f|_{A_\alpha} \equiv f(x_0) = 0$. Suy ra $f \equiv 0$ trên toàn bộ $A$, nên $A$ liên thông. ∎
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:**  
Nếu $A$ liên thông và $A \subseteq B \subseteq \text{cl}(A)$, thì $B$ cũng liên thông. Đặc biệt, bao đóng $\text{cl}(A)$ của một tập liên thông là liên thông.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:** Giả sử $B = U \cup V$ là một phép phân ly của $B$ (với $U, V$ mở trong $B$). Vì $A \subseteq B$ liên thông nên $A$ nằm trọn trong $U$ hoặc $V$; giả sử $A \subseteq U$. Khi đó $V$ là tập mở trong $B$ rời với $A$, nên không điểm nào của $V$ thuộc $\text{cl}_B(A) = \text{cl}(A) \cap B = B$, suy ra $V = \emptyset$ — mâu thuẫn. ∎
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Tích của các không gian liên thông):**  
Nếu $X$ và $Y$ đều liên thông, thì không gian tích $X \times Y$ (với tô-pô tích) cũng liên thông.
</div>

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:**  
Cố định $x_0 \in X$. Các lát cắt $\{x_0\} \times Y \cong Y$ và $X \times \{y\} \cong X$ (với mọi $y \in Y$) đều liên thông. Với mỗi $y \in Y$, tập $T_y = (\{x_0\} \times Y) \cup (X \times \{y\})$ liên thông vì hai mảnh giao nhau tại $(x_0, y)$. Hơn nữa mọi $T_y$ đều chứa $\{x_0\} \times Y$, nên hợp $\bigcup_{y \in Y} T_y = X \times Y$ là tập liên thông.
</div>

---

### 4. Các không gian con liên thông của $\mathbb{R}$

<div class="textbook-theorem" markdown="1">
**Định lý (Đặc trưng tập liên thông trong $\mathbb{R}$):**  
Một tập con $A \subseteq \mathbb{R}$ là liên thông khi và chỉ khi $A$ là một **khoảng** (bao gồm khoảng bị chặn, không bị chặn, điểm đơn hoặc tập rỗng).
</div>

Các dạng khoảng có ít nhất hai điểm gồm $[a, b], (a, b), [a, b), (a, b], [a, \infty), (a, \infty), (-\infty, b], (-\infty, b)$ và $\mathbb{R}$.

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh ($\Leftarrow$):**  
Tương tự chứng minh cho $[0, 1]$ bằng tính đầy đủ của $\mathbb{R}$ (hoặc dùng thực tế mọi khoảng không suy biến đều là hợp tăng dần các đoạn đóng $[a_n, b_n]$ giao nhau).
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh ($\Rightarrow$):**  
Giả sử $A$ không phải là khoảng; khi đó tồn tại $a < c < b$ với $a, b \in A$ nhưng $c \notin A$. Hai tập $U = A \cap (-\infty, c)$ và $V = A \cap (c, \infty)$ tạo thành một phép phân ly của $A$, mâu thuẫn với tính liên thông của $A$. ∎
</div>

---

### 5. Định lý Giá trị Trung gian (Intermediate Value Theorem)

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý Giá trị Trung gian — IVT):**  
Cho $X$ là không gian liên thông và $f: X \to \mathbb{R}$ liên tục. Nếu $x, y \in X$ thỏa $f(x) < f(y)$, thì:

$$
\forall r \in (f(x), f(y)): \exists z \in X: f(z) = r
$$
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Vì $X$ liên thông và $f$ liên tục nên $f(X) \subseteq \mathbb{R}$ là một tập liên thông, do đó là một khoảng. Vì $f(x), f(y) \in f(X)$, toàn bộ khoảng $(f(x), f(y))$ phải nằm trong $f(X)$, suy ra với mọi $r \in (f(x), f(y))$ tồn tại $z \in X$ sao cho $f(z) = r$. ∎
</div>

![Intermediate Value Theorem](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/Intermediate_value_theorem.svg/400px-Intermediate_value_theorem.svg.png)  
*Minh họa Định lý Giá trị Trung gian - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Intermediate_value_theorem.svg)*

**Ví dụ áp dụng:** Phương trình $f(x) = x^3 - x + 1 = 0$ có nghiệm trong $(-2, 0)$ vì $f$ liên tục trên $[-2, 0]$, $f(-2) = -5 < 0$ và $f(0) = 1 > 0$.

---

### 6. Liên thông đường (Path-Connectedness)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đường đi — Path):**  
Một **đường đi** (*path*) trong $X$ từ $x$ đến $y$ là một ánh xạ liên tục:

$$
\gamma: [0,1] \to X \quad \text{với } \gamma(0) = x, \gamma(1) = y
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Liên thông đường — Path-Connected):**  
Không gian $X$ là **liên thông đường** nếu giữa hai điểm bất kỳ $x, y \in X$ luôn tồn tại một đường đi nối $x$ với $y$.
</div>

![Path connected space](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Path-connectedness.svg/400px-Path-connectedness.svg.png)  
*Không gian liên thông đường - Nguồn minh họa khái niệm*

**Ví dụ:** $\mathbb{R}^n$ liên thông đường qua đoạn thẳng $\gamma(t) = (1 - t)x + ty$; đường tròn $S^1$ liên thông đường qua các cung tròn; còn $[0, 1] \cup [2, 3]$ không liên thông đường.

<div class="textbook-theorem" markdown="1">
**Định lý (Liên thông đường $\Rightarrow$ Liên thông):**  
Mọi không gian liên thông đường đều liên thông.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Cố định $x_0 \in X$. Với mỗi $x \in X$, chọn một đường đi $\gamma_x: [0, 1] \to X$ từ $x_0$ đến $x$. Ảnh $\gamma_x([0, 1])$ là tập liên thông chứa $x_0$. Vì mọi tập $\gamma_x([0, 1])$ đều có điểm chung $x_0$, hợp của chúng $\bigcup_{x \in X} \gamma_x([0, 1]) = X$ là tập liên thông. ∎
</div>

**Chiều ngược lại không đúng:**

**Phản ví dụ (Đường cong sin của nhà tô-pô — Topologist's Sine Curve):**

$$
A = \{(x, \sin(1/x)) : 0 < x \leq 1\} \cup \{(0,0)\} \subseteq \mathbb{R}^2
$$

Đặt $S = \{(x, \sin(1/x)) : 0 < x \le 1\}$. Khi đó $S$ liên thông (là ảnh liên tục của $(0, 1]$) và $S \subseteq A \subseteq \text{cl}(S)$, nên $A$ **liên thông**. Tuy nhiên, $A$ **không liên thông đường** vì không có đường đi liên tục nào nối $(0, 0)$ với một điểm thuộc $S$.

![Topologist's sine curve](https://upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Topologist%27s_sine_curve.svg/400px-Topologist%27s_sine_curve.svg.png)  
*Đường cong sin của nhà tô-pô - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Topologist%27s_sine_curve.svg)*

---

### 7. Thành phần liên thông (Connected Components)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Thành phần liên thông):**  
**Thành phần liên thông** chứa điểm $x \in X$ là hợp của tất cả các không gian con liên thông của $X$ chứa $x$:

$$
C_x = \bigcup \{A \subseteq X : x \in A, A \text{ connected}\}
$$
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Tính chất của thành phần liên thông):**
1. $C_x$ là tập con liên thông cực đại chứa $x$.
2. $C_x$ luôn là tập đóng trong $X$.
3. Nếu $C_x \cap C_y \neq \emptyset$ thì $C_x = C_y$.
4. Các thành phần liên thông tạo thành một phân hoạch của $X$.
</div>

**Ví dụ:** Không gian $[0, 1] \cup [2, 3]$ có hai thành phần liên thông là $[0, 1]$ và $[2, 3]$. Ngược lại, trong $\mathbb{Q}$, mỗi thành phần liên thông chỉ là một tập đơn điểm $\{x\}$ (gọi là không gian *hoàn toàn không liên thông*, *totally disconnected*).

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Bernard Bolzano** - *"Rein analytischer Beweis..."* (1817)  
   *Phát biểu và chứng minh chặt chẽ đầu tiên cho Định lý Giá trị Trung gian.*

2. **Camille Jordan** - *"Cours d'analyse"* (1893)  
   *Định lý đường cong Jordan gắn liền với tính liên thông của mặt phẳng.*

3. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Hình thức hóa khái niệm tính liên thông trong tô-pô đại cương.*

### Giáo trình

4. **James R. Munkres** - *Topology*, 2nd Ed., **§23–24: Connected Spaces**  
   *Tài liệu tham khảo chuẩn.*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 9**  
   *Giàu ví dụ minh họa.*

6. **Stephen Willard** - *General Topology*, **Chapter 6**  
   *Trình bày đầy đủ và chặt chẽ.*

---

## 🔗 Ứng dụng và liên hệ

### Giải tích — Định lý điểm bất động
Định lý Giá trị Trung gian suy ra ngay định lý điểm bất động Brouwer trong $1$ chiều (mọi ánh xạ liên tục $[0, 1] \to [0, 1]$ đều có điểm bất động).

### Lý thuyết đồ thị — Tính liên thông
Một đồ thị liên thông theo nghĩa tổ hợp khi và chỉ khi biểu diễn hình học (không gian tô-pô $1$-chiều) của nó liên thông.

### Khoa học thần kinh và kinh tế học mạng lưới
Khái niệm thành phần liên thông được dùng để mô tả tính kết nối chức năng giữa các vùng não cũng như sự phân mảnh hay liên kết giữa các thị trường.

---

## Video tham khảo

- **xem trước** [Basic Topology 15 | Connected Spaces](https://www.youtube.com/watch?v=JEZ9Psscb18) — The Bright Side of Mathematics, tiếng Anh. Không gian liên thông qua tập vừa mở vừa đóng, đúng định nghĩa của bài.
- [[Tôpô đại cương] Bài 44. Không gian liên thông - Phần 1: Định nghĩa và Ví dụ](https://www.youtube.com/watch?v=d9E5MkJaQpg) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Cùng định nghĩa và ví dụ, bằng tiếng Việt.
- [Weird Topological Spaces  //  Connected vs Path Connected vs Simply Connected](https://www.youtube.com/watch?v=zzeADy0MSFA) — Dr. Trefor Bazett, tiếng Anh. Liên thông, liên thông đường, và đơn liên: ba mức mà bài cần tách bạch.

## 🧩 Bài tập

### Không gian liên thông

1. **Kiểm tra tính liên thông:**  
   Các không gian sau (với tô-pô con từ $\mathbb{R}$) có liên thông không?
   - a) $\mathbb{R}$
   - b) $\mathbb{Q}$
   - c) $[0, 1]$
   - d) $(0, 1) \cup (1, 2)$

2. **Tập vừa mở vừa đóng:**  
   Tìm tất cả các tập vừa mở vừa đóng trong:
   - a) $\mathbb{R}$
   - b) $[0, 1] \cup [2, 3]$
   - c) $\{1, 2, 3\}$ với tô-pô rời rạc

3. **Áp dụng Định lý Giá trị Trung gian:**  
   Chứng minh phương trình $x^5 + x = 1$ có nghiệm trong $(0, 1)$.

### Liên thông đường

4. **Kiểm tra liên thông đường:**  
   Các không gian sau có liên thông đường không?
   - a) $\mathbb{R}^n$
   - b) Đường tròn $S^1$
   - c) $[0, 1] \cup [2, 3]$

5. **Xây dựng đường đi:**  
   Chứng minh không gian $X = \mathbb{R}^2 \setminus \{(0, 0)\}$ liên thông đường.

6. **Đường cong sin của nhà tô-pô:**  
   Chứng minh $A = \{(x, \sin(1/x)) : 0 < x \le 1\} \cup \{(0, 0)\}$ liên thông nhưng không liên thông đường.

### Thành phần liên thông

7. **Tìm thành phần liên thông:**  
   Tìm tất cả các thành phần liên thông của:
   - a) $\mathbb{Q}$
   - b) $[0, 1] \cup [2, 3] \cup \{5\}$
   - c) $\mathbb{R} \setminus \mathbb{Z}$

8. **Tính đóng của thành phần liên thông:**  
   Chứng minh mọi thành phần liên thông của một không gian tô-pô đều là tập đóng.

### Nâng cao

9. **Tích của hai không gian liên thông:**  
   Trình bày chứng minh đầy đủ: nếu $X, Y$ liên thông thì $X \times Y$ liên thông.

10. **Ảnh liên tục:**  
    Cho $f: X \to Y$ liên tục và $X$ liên thông. Chứng minh $f(X)$ liên thông bằng đặc trưng tập vừa mở vừa đóng.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §23–25 (Connected Spaces, Components)
- **Morris, Topology Without Tears:** Chapter 9
- **Hatcher, Algebraic Topology:** §0 (Path-connectedness)

---

## 🎓 Tóm tắt

✅ **Liên thông:** Không tồn tại phép phân ly thành hai tập mở khác rỗng rời nhau.  
✅ **Đặc trưng tương đương:** Chỉ có $\emptyset$ và $X$ vừa mở vừa đóng; mọi ánh xạ liên tục vào $\{0, 1\}$ đều hằng.  
✅ **Ảnh liên tục:** Ảnh liên tục của không gian liên thông là liên thông, dẫn trực tiếp đến Định lý Giá trị Trung gian.  
✅ **Liên thông đường:** Điều kiện mạnh hơn tính liên thông (chiều đảo không đúng, phản ví dụ là đường cong sin của nhà tô-pô).  
✅ **Thành phần liên thông:** Các không gian con liên thông cực đại phân hoạch $X$ và luôn đóng.

**Tiếp theo:** Bài 02.01 sẽ nghiên cứu **Không gian Compact** — tính chất bất biến tô-pô cốt lõi thứ hai của Chương 02.

---

*"Connected spaces cannot be separated."* — Topology wisdom

🎯 **Hãy vẽ hình minh họa các đường đi, phép phân ly và thành phần liên thông để rèn luyện trực giác.** 🎯

---

**Previous:** [Chapter 01: Topological Spaces](/contents/vi/topology-chapter01/)  
**Next:** [Lecture 02.01: Applications of Connectedness](/contents/vi/topology-chapter02/02_01_Applications_Connectedness/)
