---
layout: post
title: "Lecture 03.01: Regular and Normal Spaces - Urysohn's Lemma"
lang: vi
lang-ref: lecture-03-01
chapter: 3
lecture: 1
categories: [chapter03]
tags: [regular-spaces, normal-spaces, urysohn-lemma, tietze-extension, T3, T4]
description: "T₃ (Regular) và T₄ (Normal) spaces, Urysohn's Lemma, Tietze Extension Theorem"
---

**Không gian Chính quy, Chuẩn tắc và Bổ đề Urysohn**

---

## 📖 Tổng quan

Tiên đề Hausdorff ($$T_2$$) giúp ta tách rời hai *điểm* phân biệt bằng hai tập mở. Nhưng trong giải tích và hình học, ta thường cần làm nhiều hơn thế: làm sao tách một điểm khỏi một *tập đóng* lớn, hay tách hẳn *hai tập đóng rời nhau* $$A$$ và $$B$$ — thậm chí dựng được một **hàm liên tục thực** bằng đúng $$0$$ trên toàn bộ $$A$$ và bằng đúng $$1$$ trên toàn bộ $$B$$?

Đó chính là bước nhảy vọt kỳ diệu của bài giảng này: từ các điều kiện thuần túy tập hợp (**chính quy $$T_3$$**, **chuẩn tắc $$T_4$$**) bỗng nhiên **sinh ra được hàm số liên tục**! Hai đỉnh cao của chương — **Bổ đề Urysohn** và **Định lý mở rộng Tietze** — chính là chiếc cầu nối biến tô-pô trừu tượng thành giải tích thực sự.

$$
T_4 \subset T_{3.5} \subset T_3 \subset T_2
$$

![Regular and Normal spaces](https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/Normal_space.svg/500px-Normal_space.svg.png)  
*Không gian chuẩn tắc: hai tập đóng rời nhau có hai lân cận mở rời nhau - Nguồn minh họa khái niệm*

**Mạch bài học:** Kiến thức cần nhớ (từ tách điểm sang tách tập đóng $$T_3, T_{3.5}, T_4$$, ý nghĩa của Bổ đề Urysohn & Định lý mở rộng Tietze) → Giải thích: cầm tay dựng hàm Urysohn tường minh trên $$\mathbb{R}$$ tách $$(-\infty, 0]$$ và $$[2, +\infty)$$ → Định nghĩa hình thức & Chứng minh → Bài tập & Tóm tắt.

---

## Kiến thức cần nhớ: Không gian Chính quy, Chuẩn tắc và Bổ đề Urysohn nghiên cứu những gì?

### 1. Bộ ba $$T_3, T_{3.5}, T_4$$: tăng dần sức mạnh phân tách tập đóng

- **$$T_3$$ (Chính quy + $$T_1$$):** Tách một điểm $$x$$ và một tập đóng $$F \not\ni x$$ bằng hai tập mở rời nhau.
- **$$T_{3.5}$$ (Hoàn toàn chính quy / Tychonoff):** Tách $$x$$ và $$F \not\ni x$$ bằng một **hàm liên tục** $$f: X \to [0, 1]$$ sao cho $$f(x) = 0$$ và $$f(F) \subseteq \{1\}$$ (lớp không gian chính xác có compact hóa Stone–Čech!).
- **$$T_4$$ (Chuẩn tắc + $$T_1$$):** Tách *hai tập đóng rời nhau bất kỳ* $$A, B$$ bằng hai tập mở rời nhau $$U \supseteq A,\; V \supseteq B$$. Mọi không gian mê-tric và mọi không gian compact Hausdorff đều là $$T_4$$!

### 2. Bổ đề Urysohn: "điều kỳ diệu tạo hàm liên tục từ hư không"

Trong một không gian $$T_4$$ bất kỳ, ta chưa hề có thước đo khoảng cách hay tọa độ — vậy mà Pavel Urysohn (1925) chứng minh được bằng phép xây dựng lồng tập mở theo các phân số nhị phân $$p/2^n$$ rằng: **$$X$$ chuẩn tắc $$\iff$$ mọi cặp tập đóng rời nhau $$A, B$$ đều tách được bởi một hàm liên tục $$f: X \to [0, 1]$$** ($$f\vert_A = 0, f\vert_B = 1$$)!

### 3. Định lý mở rộng Tietze: kéo dài hàm liên tục từ tập đóng ra toàn không gian

Nếu $$X$$ là không gian chuẩn tắc và $$A \subseteq X$$ là tập đóng, mọi hàm liên tục $$f: A \to [a, b]$$ (hoặc $$\mathbb{R}$$) đều mở rộng được thành một hàm liên tục $$\tilde{f}: X \to [a, b]$$ trên toàn không gian! Điều kiện $$A$$ **đóng** là bắt buộc: hàm $$f(x) = \frac{1}{x}$$ liên tục trên tập mở $$(0, 1)$$ không thể mở rộng liên tục lên $$[0, 1]$$!

---

### Giải thích: Cầm tay xây dựng và kiểm tra hàm Urysohn trên $$\mathbb{R}$$

Trên một không gian mê-tric $$(X, d)$$, ta không cần dùng phép xây dựng nhị phân dài dòng của Urysohn mà có ngay công thức tường minh tuyệt đẹp để tách hai tập đóng rời nhau khác rỗng $$A$$ và $$B$$:
$$
f(x) = \frac{d(x, A)}{d(x, A) + d(x, B)}, \qquad \text{với } d(x, A) = \inf_{a \in A} d(x, a).
$$
Hãy tự tay kiểm tra công thức này trên $$\mathbb{R}$$ với $$A = (-\infty, 0]$$ và $$B = [2, +\infty)$$:

1. **Vì sao mẫu số không bao giờ bằng $$0$$?** Vì $$A$$ đóng nên $$d(x, A) = 0 \iff x \in A$$; tương tự $$d(x, B) = 0 \iff x \in B$$. Do $$A \cap B = \emptyset$$, không điểm $$x$$ nào làm cả hai số hạng cùng bằng $$0$$ → mẫu số luôn **dương chặt**, nên $$f$$ liên tục khắp $$\mathbb{R}$$!
2. **Thay 4 điểm cụ thể để kiểm tra bằng tay:**
   - Tại $$x = -3 \in A$$: $$d(-3, A) = 0$$, $$d(-3, B) = \lvert -3 - 2 \rvert = 5 \implies f(-3) = \frac{0}{0 + 5} = \mathbf{0}$$.
   - Tại $$x = 0.5$$: $$d(0.5, A) = 0.5$$, $$d(0.5, B) = 1.5 \implies f(0.5) = \frac{0.5}{0.5 + 1.5} = \mathbf{0.25}$$.
   - Tại $$x = 1$$ (trung điểm): $$d(1, A) = 1$$, $$d(1, B) = 1 \implies f(1) = \frac{1}{1 + 1} = \mathbf{0.5}$$.
   - Tại $$x = 4 \in B$$: $$d(4, A) = 4$$, $$d(4, B) = 0 \implies f(4) = \frac{4}{4 + 0} = \mathbf{1}$$.
3. **Suy ngược ra hai tập mở tách $$A$$ và $$B$$:** Lấy $$U = f^{-1}\bigl([0, \tfrac{1}{2})\bigr) = (-\infty, 1)$$ và $$V = f^{-1}\bigl((\tfrac{1}{2}, 1]\bigr) = (1, +\infty)$$ — hiển nhiên $$U \supseteq A$$, $$V \supseteq B$$ và $$U \cap V = \emptyset$$!

---

## 📐 Định nghĩa hình thức

### 1. Không gian $T_3$ (Chính quy — Regular)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian chính quy — Regular Space):**  
Không gian $X$ là **chính quy** (*regular*) nếu với mọi điểm $x \in X$ và mọi tập đóng $F$ không chứa $x$, tồn tại hai tập mở rời nhau tách $x$ và $F$:

$$
\forall x \in X, \forall F \text{ closed}: x \notin F \implies \exists U, V \in \tau: x \in U, F \subseteq V, U \cap V = \emptyset
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian $T_3$):**  
Theo quy ước phổ biến trong giáo trình (như Munkres), $X$ là **$T_3$** nếu $X$ vừa **chính quy** vừa **$T_1$**.
</div>

![Regular space illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Regular_space.svg/400px-Regular_space.svg.png)  
*Không gian chính quy: tách điểm và tập đóng bằng hai tập mở rời nhau - Nguồn minh họa khái niệm*

**Ví dụ 1: Không gian mê-tric**

<div class="textbook-theorem" markdown="1">
**Định lý:** Mọi không gian mê-tric đều là không gian chính quy (và do đó $T_3$).
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Cho $x \notin F$ ($F$ đóng khác rỗng). Đặt $d = d(x, F) = \inf\{d(x, y) : y \in F\} > 0$ (vì $F$ đóng và $x \notin F$). Khi đó $U = B(x, d/2)$ và $V = \bigcup_{y \in F} B(y, d/2)$ là hai tập mở rời nhau (theo bất đẳng thức tam giác) tách $x$ và $F$.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** $\mathbb{R}^n$ với tô-pô Euclid là không gian $T_3$.
</div>

**Ví dụ 2: Không gian compact Hausdorff**

<div class="textbook-theorem" markdown="1">
**Định lý:** Mọi không gian compact Hausdorff đều là không gian chính quy.
</div>

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:**  
Cho $x \notin F$ ($F$ đóng, suy ra $F$ compact). Với mỗi $y \in F$, do $X$ Hausdorff nên có hai tập mở rời nhau $U_y \ni x$ và $V_y \ni y$. Họ $\{V_y\}_{y \in F}$ phủ $F$ nên có phủ con hữu hạn $V_{y_1}, \dots, V_{y_n}$. Khi đó $U = \bigcap_{i=1}^n U_{y_i}$ và $V = \bigcup_{i=1}^n V_{y_i}$ là hai tập mở rời nhau tách $x$ và $F$.
</div>

**Phản ví dụ:** Tập không đếm được với tô-pô đồng đếm được không chính quy (thậm chí không Hausdorff): với $x \neq y$, tập $F = \{y\}$ đóng nhưng mọi cặp tập mở khác rỗng đều giao nhau.

---

### 2. Không gian $T_4$ (Chuẩn tắc — Normal)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian chuẩn tắc — Normal Space):**  
Không gian $X$ là **chuẩn tắc** (*normal*) nếu với mọi hai tập đóng rời nhau $A, B$, tồn tại hai tập mở rời nhau $U, V$ chứa chúng:

$$
\forall A, B \text{ closed}: A \cap B = \emptyset \implies \exists U, V \in \tau: A \subseteq U, B \subseteq V, U \cap V = \emptyset
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian $T_4$):**  
$X$ là **$T_4$** nếu $X$ vừa **chuẩn tắc** vừa **$T_1$**.
</div>

![Normal space illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/T4_space.svg/400px-T4_space.svg.png)  
*Không gian chuẩn tắc: hai tập đóng rời nhau có hai lân cận mở rời nhau - Nguồn minh họa khái niệm*

**Ví dụ 1: Không gian mê-tric**

<div class="textbook-theorem" markdown="1">
**Định lý:** Mọi không gian mê-tric đều là không gian chuẩn tắc (và do đó $T_4$).
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Cho $A, B$ là hai tập đóng rời nhau khác rỗng. Đặt $d_A(x) = \inf\{d(x, a) : a \in A\}$ và $d_B(x) = \inf\{d(x, b) : b \in B\}$ (hai hàm liên tục). Hai tập $U = \{x : d_A(x) < d_B(x)\}$ và $V = \{x : d_B(x) < d_A(x)\}$ đều mở, rời nhau và thỏa $A \subseteq U, B \subseteq V$.
</div>

**Ví dụ 2: Không gian compact Hausdorff**

<div class="textbook-theorem" markdown="1">
**Định lý:** Mọi không gian compact Hausdorff đều là không gian chuẩn tắc.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Tương tự trường hợp chính quy: trước hết tách từng điểm $a \in A$ với tập đóng $B$ (nhờ tính chính quy), rồi dùng tính compact của $A$ để trích ra hữu hạn tập mở.
</div>

**Phản ví dụ — Mặt phẳng Sorgenfrey:** Đường thẳng Sorgenfrey $\mathbb{R}_\ell$ (tô-pô giới hạn dưới với cơ sở $\{[a, b)\}$) là không gian chuẩn tắc, nhưng tích của nó — **mặt phẳng Sorgenfrey** $\mathbb{R}_\ell \times \mathbb{R}_\ell$ — **không chuẩn tắc**. Điều này cho thấy tính chuẩn tắc không được bảo toàn qua phép lấy tích Đề-các (kể cả tích hữu hạn).

<div class="textbook-proof" markdown="1">
**Ghi chú:** Phản ví dụ này dùng tính không đếm được của đường chéo phụ $y = -x$ kết hợp với tính khả ly của $\mathbb{R}_\ell \times \mathbb{R}_\ell$.
</div>

---

### 3. Bổ đề Urysohn (Urysohn's Lemma)

**Bổ đề Urysohn:**

> **Nếu $X$ là không gian chuẩn tắc và $A, B \subseteq X$ là hai tập đóng rời nhau, thì tồn tại hàm liên tục $f: X \to [0, 1]$ sao cho:**
> $$f(A) = \{0\}, \quad f(B) = \{1\}$$

![Urysohn Lemma visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Urysohn_function.svg/500px-Urysohn_function.svg.png)  
*Hàm Urysohn tách hai tập đóng rời nhau - Nguồn minh họa khái niệm*

Bổ đề Urysohn chuyển một tính chất thuần túy tập hợp (tách hai tập đóng bằng tập mở) thành sự tồn tại của hàm số liên tục, đóng vai trò then chốt trong định lý mở rộng Tietze và định lý mê-tric hóa Urysohn.

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh (Xây dựng dãy tập mở lồng nhau):**
</div>

Nhắc lại đặc trưng tương đương của tính chuẩn tắc: với mọi tập đóng $C$ và tập mở $W \supseteq C$, tồn tại tập mở $U$ sao cho $C \subseteq U \subseteq \text{cl}(U) \subseteq W$.

**Bước 1:** Đặt $U_1 = X \setminus B$ (tập mở chứa $A$). Áp dụng liên tiếp tính chuẩn tắc theo các số hữu tỉ nhị phân (hoặc toàn bộ $\mathbb{Q} \cap [0, 1]$), ta xây dựng họ tập mở $\{U_r\}_{r \in \mathbb{Q} \cap [0, 1]}$ sao cho:
- $A \subseteq U_0 \subseteq \text{cl}(U_0) \subseteq U_1 = X \setminus B$;
- Với mọi $r < s$ trong $\mathbb{Q} \cap [0, 1]$, ta có $\text{cl}(U_r) \subseteq U_s$ (chẳng hạn chọn $U_{1/2}$ sao cho $\text{cl}(U_0) \subseteq U_{1/2} \subseteq \text{cl}(U_{1/2}) \subseteq U_1$, rồi tiếp tục chia đôi).

**Bước 2:** Định nghĩa hàm $f: X \to [0, 1]$:
$$
f(x) = \begin{cases}
\inf\{r \in \mathbb{Q} \cap [0,1] : x \in U_r\} & \text{if } x \in U_1 \\
1 & \text{if } x \notin U_1
\end{cases}
$$

**Bước 3:** Kiểm tra:
- Với mọi $x \in A$, $x \in U_r$ với mọi $r \ge 0$, nên $f(x) = 0$.
- Với mọi $x \in B$, $x \notin U_1$, nên $f(x) = 1$.
- Tính liên tục suy từ các đẳng thức $f^{-1}([0, a)) = \bigcup_{r < a} U_r$ (mở) và $f^{-1}((a, 1]) = \bigcup_{s > a} (X \setminus \text{cl}(U_s))$ (mở).

---

### 4. Định lý mở rộng Tietze (Tietze Extension Theorem)

**Định lý mở rộng Tietze:**

> **Nếu $X$ là không gian chuẩn tắc, $A \subseteq X$ là tập con đóng và $f: A \to [a, b]$ là hàm liên tục, thì tồn tại hàm liên tục mở rộng $F: X \to [a, b]$ sao cho $F|_A = f$.**

```
A ---f---> [a,b]
|          
i|         
v          
X ---F---> [a,b]
```

*(Định lý cũng đúng khi thay $[a, b]$ bằng $\mathbb{R}$.)*

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:**
</div>

Không mất tính tổng quát, co giãn miền giá trị về $[-1, 1]$, tức $f: A \to [-1, 1]$.
1. Đặt $A_1 = f^{-1}([-1, -1/3])$ và $A_2 = f^{-1}([1/3, 1])$ (hai tập đóng rời nhau trong $A$, do đó đóng trong $X$). Áp dụng Bổ đề Urysohn (sau khi co giãn về $[-1/3, 1/3]$), tồn tại hàm liên tục $g_1: X \to [-1/3, 1/3]$ thỏa $g_1(A_1) = -1/3$ và $g_1(A_2) = 1/3$.
2. Đặt $f_1 = f - g_1|_A$; khi đó $|f_1(x)| \le 2/3$ với mọi $x \in A$.
3. Lặp lại quy trình, ta xây dựng dãy hàm liên tục $g_n: X \to \mathbb{R}$ thỏa $|g_n(x)| \le \frac{1}{3}\left(\frac{2}{3}\right)^{n-1}$ và $\left|f(x) - \sum_{k=1}^n g_k(x)\right| \le \left(\frac{2}{3}\right)^n$ trên $A$.
4. Chuỗi $F(x) = \sum_{n=1}^{\infty} g_n(x)$ hội tụ đều trên $X$ (theo tiêu chuẩn Weierstrass M-test) về một hàm liên tục $F: X \to [-1, 1]$ thỏa $F|_A = f$.

---

### 5. Không gian $T_{3.5}$ (Hoàn toàn chính quy / Tychonoff)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Hoàn toàn chính quy — Completely Regular):**  
Không gian $X$ là **hoàn toàn chính quy** nếu với mọi $x \in X$ và mọi tập đóng $F$ không chứa $x$ ($x \notin F$), tồn tại hàm liên tục $f: X \to [0, 1]$ sao cho $f(x) = 0$ và $f(F) = \{1\}$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian $T_{3.5}$ / Tychonoff):**  
$X$ là **không gian Tychonoff** ($T_{3.5}$) nếu $X$ vừa hoàn toàn chính quy vừa $T_1$.
</div>

Hệ phân tầng đầy đủ:
$$
T_4 \implies T_{3.5} \implies T_3 \implies T_2 \implies T_1 \implies T_0
$$

Mọi không gian mê-tric, mọi không gian compact Hausdorff và mọi không gian con của không gian Tychonoff đều là không gian Tychonoff.

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý nhúng Tychonoff):**  
$X$ là không gian Tychonoff $\iff X$ đồng phôi với một không gian con của tích $[0, 1]^I$ (với một tập chỉ số $I$ thích hợp).
</div>

<div class="textbook-proof" markdown="1">
**Ghi chú:** Phép nhúng được cho bởi ánh xạ đánh giá $x \mapsto (f(x))_{f \in C(X, [0, 1])}$ (cơ sở xây dựng compact hóa Stone–Čech).
</div>

---

### 6. Tổng hợp quan hệ và tính bảo toàn

```
                T₄ (Normal + T₁)
                      ↓
              T₃.₅ (Tychonoff)
                      ↓
              T₃ (Regular + T₁)
                      ↓
              T₂ (Hausdorff)
                      ↓
                  T₁ (Fréchet)
                      ↓
              T₀ (Kolmogorov)
```

<div class="textbook-theorem" markdown="1">
**Định lý (Tính bảo toàn):**
- Không gian con của không gian $T_3$ là $T_3$.
- Không gian con của không gian Tychonoff là Tychonoff.
- Tích tùy ý các không gian Tychonoff là Tychonoff.
- Tích (và không gian con bất kỳ) của không gian $T_4$ **không nhất thiết** là $T_4$ (ví dụ mặt phẳng Sorgenfrey).
</div>

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Pavel Urysohn** - *"Über die Mächtigkeit der zusammenhängenden Mengen"* (1925)  
   *Trình bày Bổ đề Urysohn.*

2. **Heinrich Tietze** - *"Über Funktionen, die auf einer abgeschlossenen Menge stetig sind"* (1915)  
   *Định lý mở rộng Tietze.*

3. **Andrey Tychonoff** - *"Über einen Funktionenraum"* (1935)  
   *Nghiên cứu không gian hoàn toàn chính quy.*

### Giáo trình

4. **James R. Munkres** - *Topology*, 2nd Ed., **§31–33: Normal Spaces**  
   *Chứng minh đầy đủ Bổ đề Urysohn và Định lý Tietze.*

5. **Stephen Willard** - *General Topology*, **Chapter 5**  
   *Trình bày nâng cao.*

6. **John L. Kelley** - *General Topology*, **Chapter 4**  
   *Cách tiếp cận kinh điển.*

---

## 🔗 Ứng dụng và liên hệ

- **Giải tích hàm:** Định lý mở rộng Tietze là tương tự tô-pô của định lý mở rộng Hahn–Banach.
- **Tô-pô vi phân:** Kết hợp kỹ thuật tách hàm liên tục và làm trơn để xây dựng phân hoạch đơn vị (*partition of unity*) trên đa tạp.
- **Lý thuyết đồng luân:** Bổ đề Urysohn và định lý Tietze được dùng rộng rãi để xây dựng phép đồng luân và mở rộng ánh xạ trên phức CW.
- **Mê-tric hóa:** Tiền đề trực tiếp cho Định lý mê-tric hóa Urysohn ở Bài 03.03.

---

## Video tham khảo

- **xem trước** [Regular and Normal Spaces -- Topology Video 22](https://www.youtube.com/watch?v=sW-H4f5S5A8) — MathMajor, tiếng Anh. Thang regular rồi normal, trước khi bổ đề Urysohn biến tách tập thành một hàm liên tục.
- [MAST30026 Lecture 22: Urysohn's lemma](https://www.youtube.com/watch?v=UQas4Cu89D0) — metauni, tiếng Anh. Bổ đề Urysohn cho không gian normal, đúng phiên bản Munkres của bài này.
- [The most important lemma in Topology | Urysohn Lemma | Part 1](https://www.youtube.com/watch?v=z0qUPtaOmXs) — Problemathic, tiếng Anh. Phần mở đầu chứng minh Urysohn, xem sau khi phát biểu đã nằm yên.

## 🧩 Bài tập

### Không gian chính quy

1. **Không gian mê-tric:** Trình bày chứng minh chi tiết mọi không gian mê-tric đều chính quy.
2. **Compact Hausdorff:** Chứng minh mọi không gian compact Hausdorff đều chính quy.
3. **Không gian con:** Chứng minh nếu $X$ chính quy và $A \subseteq X$ thì không gian con $A$ cũng chính quy.

### Không gian chuẩn tắc

4. **Không gian mê-tric:** Chứng minh mọi không gian mê-tric đều chuẩn tắc.
5. **Compact Hausdorff:** Chứng minh mọi không gian compact Hausdorff đều chuẩn tắc.
6. **Mặt phẳng Sorgenfrey:** Tìm hiểu chứng minh vì sao $\mathbb{R}_\ell \times \mathbb{R}_\ell$ không chuẩn tắc.

### Bổ đề Urysohn

7. **Xây dựng tường minh:** Trên $X = \mathbb{R}$ với $A = \{0\}$ và $B = \{1\}$, viết công thức tường minh một hàm Urysohn $f: \mathbb{R} \to [0, 1]$ thỏa $f(A) = \{0\}, f(B) = \{1\}$.
8. **Tính không duy nhất:** Hàm Urysohn có duy nhất không? Giải thích.
9. **Chiều đảo:** Nếu trong $X$ mọi cặp tập đóng rời nhau đều tách được bởi một hàm liên tục $f: X \to [0, 1]$, chứng minh $X$ là không gian chuẩn tắc.

### Định lý mở rộng Tietze

10. **Áp dụng Tietze:** Cho $X = \mathbb{R}$, $A = [0, 1]$ và $f(x) = \sin(\pi x)$. Tìm một mở rộng liên tục $F: \mathbb{R} \to [-1, 1]$.
11. **Vai trò của giả thiết tập đóng:** Cho $X = \mathbb{R}$, $A = (0, 1)$ và $f(x) = \sin(1/x)$. Vì sao $f$ không mở rộng liên tục được lên toàn bộ $\mathbb{R}$, và điều này không mâu thuẫn với định lý Tietze?

### Nâng cao

12. **$T_4 \Rightarrow T_{3.5}$:** Dùng Bổ đề Urysohn chứng minh mọi không gian $T_4$ đều là không gian Tychonoff ($T_{3.5}$).
13. **Định lý nhúng:** Chứng minh mọi không gian Tychonoff đều nhúng được vào $[0, 1]^I$ với tập chỉ số $I$ thích hợp.
14. **Phản ví dụ:** Tìm một không gian $T_3$ (thậm chí $T_{3.5}$) nhưng không $T_4$ (*Gợi ý:* mặt phẳng Sorgenfrey).
15. **Gợi mở mê-tric hóa:** Nếu $X$ là $T_3$ và thỏa mãn tiên đề đếm được thứ hai, chứng minh tồn tại họ đếm được các hàm liên tục $f_n: X \to [0, 1]$ tách mọi điểm khỏi mọi tập đóng không chứa nó.

### Câu hỏi suy ngẫm

16. **Ý nghĩa của Bổ đề Urysohn:** Vì sao việc chứng minh tồn tại hàm liên tục chỉ từ tiên đề tập mở lại quan trọng trong tô-pô đại cương?
17. **Tính chuẩn tắc và tích Đề-các:** So sánh tính bảo toàn qua tích của các tính chất Hausdorff, chính quy, Tychonoff và chuẩn tắc.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §31–33 (Normal Spaces, Urysohn, Tietze)
- **Willard, General Topology:** Chapter 5 (Normal and Completely Regular Spaces)
- **Engelking, General Topology:** Chapter 1.5 (Separation)
- **Steen & Seebach:** *Counterexamples in Topology*

---

## 🎓 Tóm tắt

✅ **$T_3$ (Chính quy + $T_1$):** Tách điểm khỏi tập đóng bằng hai tập mở rời nhau.  
✅ **$T_4$ (Chuẩn tắc + $T_1$):** Tách hai tập đóng rời nhau bằng hai tập mở rời nhau.  
✅ **Bổ đề Urysohn:** Trong không gian chuẩn tắc, hai tập đóng rời nhau luôn tách được bằng một hàm liên tục nhận giá trị trong $[0, 1]$.  
✅ **Định lý mở rộng Tietze:** Mọi hàm liên tục từ tập con đóng của không gian chuẩn tắc vào $[a, b]$ (hoặc $\mathbb{R}$) đều mở rộng liên tục được ra toàn không gian.  
✅ **$T_{3.5}$ (Tychonoff):** Tách điểm và tập đóng bằng hàm liên tục; tương đương với việc nhúng được vào $[0, 1]^I$.

**Tiếp theo:** Bài 03.02 sẽ trình bày **Các tiên đề đếm được** (*Countability Axioms*) — đếm được thứ nhất, đếm được thứ hai, khả ly và Lindelöf.

---

*"Urysohn's Lemma: In normal spaces, closed sets can be separated not just by open sets, but by continuous functions."* — Topological wisdom

🎯 **Hãy nắm vững Bổ đề Urysohn và Định lý Tietze vì chúng là hai công cụ cốt lõi trong phần còn lại của tô-pô học.** 🎯

---

**Previous:** [Lecture 03.00: T₀, T₁, T₂ Spaces](/contents/vi/topology-chapter03/03_00_Separation_Axioms_T0_T1_T2/)  
**Next:** [Lecture 03.02: Countability Axioms](/contents/vi/topology-chapter03/03_02_Countability_Axioms/)
