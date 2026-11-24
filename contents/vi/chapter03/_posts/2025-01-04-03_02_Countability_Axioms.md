---
layout: post
title: "Lecture 03.02: Countability Axioms"
lang: vi
lang-ref: lecture-03-02
chapter: 3
lecture: 2
categories: [chapter03]
tags: [first-countable, second-countable, separable, lindelof, countability]
description: "First countable, second countable, separable, và Lindelöf spaces"
---

**Các Tiên đề Đếm được**

---

## 📖 Tổng quan

Trong giải tích, ta quen dùng **dãy số** $$(x_n)$$ để kiểm tra điểm tụ, bao đóng và tính liên tục. Nhưng khi bước sang tô-pô đại cương, có những không gian "quá cồng kềnh" đến mức dãy số bất lực hoàn toàn — một điểm nằm trong bao đóng của $$A$$ nhưng lại **không có dãy nào trong $$A$$ hội tụ về nó**! Điều gì kiểm soát "kích thước" của hệ thống tập mở để dãy số còn hoạt động tốt, hay để toàn bộ không gian được xấp xỉ bởi một tập con đếm được?

Câu trả lời nằm ở bốn **tiên đề đếm được (countability axioms)**:
1. **Đếm được thứ nhất (First countable):** Mỗi điểm có một cơ sở lân cận đếm được.
2. **Đếm được thứ hai (Second countable):** Toàn bộ tô-pô có một cơ sở đếm được.
3. **Khả ly (Separable):** Tồn tại tập con trù mật đếm được.
4. **Lindelöf:** Mọi phủ mở đều có phủ con đếm được.

![Countability hierarchy](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/Separation_and_countability.svg/500px-Separation_and_countability.svg.png)  
*Quan hệ giữa các tính chất đếm được - Nguồn minh họa khái niệm*

**Mạch bài học:** Bản đồ kiến thức nền (vì sao cần 4 mức đếm được, mối liên hệ với dãy số & sự trùng khớp trong không gian mê-tric) → Khung giải thích chậm: cầm tay dựng cơ sở đếm được của $$\mathbb{R}$$ và chứng minh đường thẳng Sorgenfrey khả ly nhưng không đếm được thứ hai → Định nghĩa hình thức & Quan hệ bao hàm → Bài tập & Tóm tắt.

---

## Bản đồ kiến thức nền: Các Tiên đề Đếm được nghiên cứu những gì?

### 1. Đếm được thứ nhất ($$C_1$$): ranh giới để dãy số còn đủ sức đặc trưng tô-pô

Mọi không gian mê-tric đều đếm được thứ nhất vì quanh mỗi điểm $$x$$ có họ đếm được các hình cầu mở $$B(x, 1/n)$$ ($$n \in \mathbb{N}^*$$). Trong mọi không gian $$C_1$$, ta được phép dùng dãy như trong giải tích: $$x \in \operatorname{cl}(A) \iff$$ tồn tại dãy $$(x_n) \subset A$$ hội tụ về $$x$$, và $$f$$ liên tục $$\iff f$$ bảo toàn giới hạn dãy!

### 2. Đếm được thứ hai ($$C_2$$): điều kiện mạnh nhất kéo theo cả ba điều kiện còn lại

Nếu toàn bộ tô-pô sinh bởi chỉ một cơ sở đếm được $$\mathcal{B} = \{B_1, B_2, \dots\}$$, thì không gian tự động vừa đếm được thứ nhất, vừa **khả ly** (chọn mỗi $$B_n \neq \emptyset$$ một điểm là được tập trù mật đếm được!), vừa **Lindelöf**. Hơn nữa, $$C_2$$ kết hợp với $$T_3$$ chính là giả thiết của Định lý mê-tric hóa Urysohn!

### 3. Trong không gian mê-tric, ba khái niệm $$C_2$$, Khả ly và Lindelöf nhập làm một!

Trên không gian tô-pô tổng quát, $$C_2 \implies \text{Khả ly}$$ và $$C_2 \implies \text{Lindelöf}$$ nhưng chiều ngược lại đều **sai** (như đường thẳng Sorgenfrey dưới đây!). Tuy nhiên, riêng trên **không gian mê-tric**, cả ba tính chất này hoàn toàn **tương đương nhau**!

---

### Khung giải thích (nên đọc chậm): Cầm tay kiểm chứng $$\mathbb{R}$$ là $$C_2$$ còn đường thẳng Sorgenfrey $$\mathbb{R}_l$$ thì KHÔNG

**Ví dụ 1 — Vì sao $$\mathbb{R}$$ (tô-pô Euclid) đếm được thứ hai ($$C_2$$)?**
Xét họ các khoảng mở có **hai đầu mút hữu tỉ**:
$$
\mathcal{B}_{\mathbb{Q}} = \bigl\{(p, q) : p, q \in \mathbb{Q},\; p < q\bigr\}.
$$
- **Kiểm tra tính đếm được:** Mỗi phần tử ứng với một cặp $$(p, q) \in \mathbb{Q} \times \mathbb{Q}$$, mà tích hai tập đếm được là **đếm được**.
- **Kiểm tra tính cơ sở bằng ví dụ cụ thể:** Lấy khoảng mở vô tỉ $$(\sqrt{2}, \pi)$$ và điểm $$x = 2 \in (\sqrt{2}, \pi)$$. Vì $$\mathbb{Q}$$ trù mật trong $$\mathbb{R}$$, ta chọn ngay $$p = 1.5 \in \mathbb{Q}$$ và $$q = 3 \in \mathbb{Q}$$ → thu được $$2 \in (1.5, 3) \subseteq (\sqrt{2}, \pi)$$! Vậy $$\mathcal{B}_{\mathbb{Q}}$$ là cơ sở đếm được của $$\mathbb{R}$$.

**Ví dụ 2 — Đường thẳng Sorgenfrey $$\mathbb{R}_l$$ (cơ sở $$[a, b)$$) khả ly nhưng KHÔNG $$C_2$$:**
- **Khả ly:** Mọi khoảng nửa mở $$[a, b)$$ (với $$a < b$$) đều chứa ít nhất một số hữu tỉ, nên $$\mathbb{Q}$$ là tập trù mật đếm được của $$\mathbb{R}_l$$!
- **Không đếm được thứ hai:** Giả sử $$\mathcal{B}$$ là một cơ sở bất kỳ của $$\mathbb{R}_l$$. Với **mỗi số thực $$x \in \mathbb{R}$$**, vì $$[x, x+1)$$ mở và chứa $$x$$, phải tồn tại một tập cơ sở $$B_x \in \mathcal{B}$$ sao cho:
  $$
  x \in B_x \subseteq [x, x + 1).
  $$
  Từ đây suy ra phần tử nhỏ nhất của $$B_x$$ chính là $$\min B_x = x$$! Vậy nếu $$x \neq y$$ thì $$\min B_x = x \neq y = \min B_y \implies B_x \neq B_y$$! Điều đó buộc $$\mathcal{B}$$ phải có ít nhất $$\lvert \mathbb{R} \rvert = \mathfrak{c}$$ phần tử (**không đếm được**) → $$\mathbb{R}_l$$ **không $$C_2$$**!

---

## 📐 Định nghĩa hình thức

### 1. Không gian đếm được thứ nhất (First Countable Spaces)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Cơ sở lân cận):**  
Họ $\{B_n\}$ các lân cận của điểm $x$ là một **cơ sở lân cận** tại $x$ nếu với mọi lân cận $N$ của $x$, tồn tại $B_n \subseteq N$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đếm được thứ nhất — First Countable):**  
Không gian $X$ thỏa mãn **tiên đề đếm được thứ nhất** nếu mọi điểm $x \in X$ đều có một **cơ sở lân cận đếm được** (hữu hạn hoặc vô hạn đếm được):

$$
\forall x \in X: \exists \{B_n\}_{n=1}^\infty \text{ neighborhoods of } x: \forall N \ni x: \exists n: B_n \subseteq N
$$
</div>

**Ví dụ 1: Không gian mê-tric**

<div class="textbook-theorem" markdown="1">
**Định lý:** Mọi không gian mê-tric đều thỏa mãn tiên đề đếm được thứ nhất.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Tại mỗi $x \in X$, họ $\{B(x, 1/n)\}_{n=1}^{\infty}$ là một cơ sở lân cận đếm được: với mọi lân cận $N$ của $x$, tồn tại $\varepsilon > 0$ sao cho $B(x, \varepsilon) \subseteq N$; chọn $n > 1/\varepsilon$ ta có $B(x, 1/n) \subseteq N$.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** $\mathbb{R}^n$ thỏa mãn tiên đề đếm được thứ nhất.
</div>

**Ví dụ 2:** Mọi không gian rời rạc đều đếm được thứ nhất (với cơ sở lân cận $\{\{x\}\}$ tại $x$).

**Phản ví dụ — Tô-pô đồng đếm được trên tập không đếm được:**

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Giả sử $\{B_n\}$ là cơ sở lân cận mở đếm được tại $x$. Khi đó mỗi phần bù $C_n = X \setminus B_n$ đều đếm được, nên $C = \bigcup_n C_n$ cũng đếm được và $C \not\ni x$. Vì $X$ không đếm được, chọn $y \in X \setminus (C \cup \{x\})$ và xét lân cận mở $N = X \setminus \{y\}$ của $x$ (hoặc đặt trực tiếp $C' = C \cup \{y\}$). Khi đó $y \in B_n$ với mọi $n$, nên không có $B_n$ nào nằm trong $N$ — mâu thuẫn.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Đặc trưng bao đóng bằng dãy):**  
Trong không gian đếm được thứ nhất, $\overline{A} = \{x \in X : \exists \text{ dãy } (x_n) \text{ trong } A \text{ hội tụ về } x\}$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
- **($\supseteq$):** Luôn đúng trong mọi không gian tô-pô.
- **($\subseteq$):** Cho $x \in \overline{A}$ và $\{B_n\}$ là cơ sở lân cận đếm được tại $x$. Đặt $V_n = B_1 \cap \dots \cap B_n$ (dãy lân cận giảm dần). Vì $x \in \overline{A}$ nên $V_n \cap A \neq \emptyset$; chọn $x_n \in V_n \cap A$ ta được dãy $(x_n)$ trong $A$ hội tụ về $x$.
</div>

Nhờ tính chất này, trong không gian đếm được thứ nhất ta có thể dùng dãy thay cho lưới (*nets*) để khảo sát bao đóng và tính liên tục.

---

### 2. Không gian đếm được thứ hai (Second Countable Spaces)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đếm được thứ hai — Second Countable):**  
Không gian $X$ thỏa mãn **tiên đề đếm được thứ hai** nếu tô-pô của nó có một **cơ sở đếm được**:

$$
\exists \{B_n\}_{n=1}^\infty \text{ basis}: \forall U \in \tau: U = \bigcup_{n \in I} B_n, I \subseteq \mathbb{N}
$$
</div>

**Ví dụ 1: $\mathbb{R}$ và $\mathbb{R}^n$ (tô-pô Euclid)**

<div class="textbook-theorem" markdown="1">
**Định lý:** $\mathbb{R}$ (và tổng quát $\mathbb{R}^n$) thỏa mãn tiên đề đếm được thứ hai.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Họ $\mathcal{B} = \{(a, b) : a, b \in \mathbb{Q}, a < b\}$ là một cơ sở đếm được cho $\mathbb{R}$ (tương tự, họ các hình hộp mở với tọa độ đỉnh hữu tỉ là cơ sở đếm được cho $\mathbb{R}^n$).
</div>

**Ví dụ 2: Không gian hữu hạn và không gian rời rạc đếm được**  
Mọi không gian hữu hạn với tô-pô bất kỳ, cũng như mọi tập đếm được với tô-pô rời rạc (cơ sở $\{\{x\} : x \in X\}$), đều đếm được thứ hai. *(Lưu ý: một tập vô hạn đếm được với tô-pô tùy ý chưa chắc đếm được thứ hai, vì $\mathcal{P}(X)$ không đếm được.)*

**Phản ví dụ 1:** Tập không đếm được với tô-pô rời rạc không đếm được thứ hai, vì mọi cơ sở đều phải chứa mọi tập đơn điểm $\{x\}$.

**Phản ví dụ 2:** Đường thẳng Sorgenfrey $\mathbb{R}_\ell$ (cơ sở $\{[a, b)\}$) không đếm được thứ hai vì với mỗi $x \in \mathbb{R}$, bất kỳ cơ sở nào cũng phải chứa một phần tử có dạng $B_x \subseteq [x, x+1)$ nhận $x$ làm phần tử nhỏ nhất, dẫn đến cơ sở có lực lượng ít nhất bằng $|\mathbb{R}|$.

---

<div class="textbook-theorem" markdown="1">
**Định lý (Đếm được thứ hai $\Rightarrow$ Đếm được thứ nhất):**  
Mọi không gian đếm được thứ hai đều đếm được thứ nhất.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Nếu $\{B_n\}$ là cơ sở đếm được của $X$, thì tại mỗi $x \in X$, họ $\{B_n : x \in B_n\}$ là cơ sở lân cận đếm được.
</div>

Chiều ngược lại không đúng (ví dụ tập không đếm được với tô-pô rời rạc).

---

### 3. Không gian khả ly (Separable Spaces)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập trù mật):**  
$D \subseteq X$ là **trù mật** (*dense*) trong $X$ nếu $\overline{D} = X$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Khả ly — Separable):**  
$X$ là **không gian khả ly** nếu tồn tại tập con trù mật đếm được:

$$
\exists D \subseteq X: |D| \leq \aleph_0 \land \overline{D} = X
$$
</div>

**Ví dụ:** $\mathbb{R}$ khả ly (nhờ $\mathbb{Q}$), $\mathbb{R}^n$ khả ly (nhờ $\mathbb{Q}^n$), và không gian Hilbert $\ell^2$ khả ly (nhờ tập các dãy có hữu hạn tọa độ hữu tỉ khác $0$). Ngược lại, tập không đếm được với tô-pô rời rạc không khả ly (vì mọi tập con đều đóng, nên chỉ có chính $X$ mới trù mật).

<div class="textbook-theorem" markdown="1">
**Định lý (Đếm được thứ hai $\Rightarrow$ Khả ly):**  
Mọi không gian đếm được thứ hai đều khả ly.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Cho $\{B_n\}$ là cơ sở đếm được gồm các tập khác rỗng. Chọn $x_n \in B_n$ cho mỗi $n$ và đặt $D = \{x_n\}$. Mọi tập mở khác rỗng $U$ đều chứa một $B_n$ nào đó nên chứa $x_n \in D$; suy ra $\overline{D} = X$.
</div>

Chiều ngược lại sai trong không gian tô-pô tổng quát (ví dụ đường thẳng Sorgenfrey $\mathbb{R}_\ell$ khả ly nhờ $\mathbb{Q}$, nhưng không đếm được thứ hai).

---

### 4. Không gian Lindelöf (Lindelöf Spaces)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Lindelöf):**  
$X$ là **không gian Lindelöf** nếu mọi phủ mở của $X$ đều có một **phủ con đếm được**:

$$
\forall \{U_\alpha\}_{\alpha \in I} \text{ open cover}: \exists \text{ countable } J \subseteq I: X = \bigcup_{\alpha \in J} U_\alpha
$$
</div>

Mọi không gian compact đều là không gian Lindelöf (vì hữu hạn là trường hợp riêng của đếm được).

<div class="textbook-theorem" markdown="1">
**Định lý (Đếm được thứ hai $\Rightarrow$ Lindelöf):**  
Mọi không gian đếm được thứ hai đều là không gian Lindelöf.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Cho $\{B_n\}$ là cơ sở đếm được và $\{U_\alpha\}$ là một phủ mở của $X$. Với mỗi $x \in X$, chọn $U_{\alpha(x)} \ni x$ và chọn phần tử cơ sở $B_{n(x)}$ sao cho $x \in B_{n(x)} \subseteq U_{\alpha(x)}$. Tập các $B_{n(x)}$ thu được chỉ có tối đa đếm được phần tử; ứng với mỗi phần tử đó, chọn một $U_\alpha$ chứa nó ta được một phủ con đếm được của $X$.
</div>

Do đó $\mathbb{R}$ và $\mathbb{R}^n$ đều là không gian Lindelöf. Ngược lại, tập không đếm được với tô-pô rời rạc không phải Lindelöf (phủ mở $\{\{x\} : x \in X\}$ không có phủ con đếm được).

<div class="textbook-theorem" markdown="1">
**Định lý ($T_3$ + Lindelöf $\Rightarrow$ Chuẩn tắc):**  
Mọi không gian chính quy ($T_3$) và Lindelöf đều là không gian chuẩn tắc ($T_4$). (Hơn nữa, mọi không gian Hausdorff paracompact cũng chuẩn tắc.)
</div>

---

### 5. Quan hệ giữa các tính chất đếm được

```
Second Countable ⟹ Lindelöf
        ↓
First Countable    Separable
        ↘         ↙
     (không kéo theo nhau nói chung)
```

Trong trường hợp không gian mê-tric hóa được, ba tính chất toàn cục trở nên tương đương:

<div class="textbook-theorem" markdown="1">
**Định lý (Trong không gian mê-tric hóa được):**  
Đối với không gian mê-tric hóa được, ba điều kiện sau tương đương: **đếm được thứ hai $\iff$ khả ly $\iff$ Lindelöf**.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Dành làm bài tập (nếu $D$ trù mật đếm được, xét họ hình cầu mở $\{B(d, 1/n) : d \in D, n \in \mathbb{N}\}$).
</div>

**Bảng tổng hợp ví dụ:**

| Không gian | Đếm được thứ nhất | Đếm được thứ hai | Khả ly | Lindelöf |
|-------|-----------|-----------|-----------|----------|
| $\mathbb{R}^n$ (Euclid) | ✓ | ✓ | ✓ | ✓ |
| Rời rạc (đếm được) | ✓ | ✓ | ✓ | ✓ |
| Rời rạc (không đếm được) | ✓ | ✗ | ✗ | ✗ |
| Đồng đếm được (không đếm được) | ✗ | ✗ | ✗ | ✓ |
| $\mathbb{R}_\ell$ (Sorgenfrey) | ✓ | ✗ | ✓ | ✓ |
| $[0, 1]^{\mathbb{R}}$ (tô-pô tích) | ✗ | ✗ | ✓ | ✓ |

*(Lưu ý: trong tô-pô đồng đếm được trên tập không đếm được $X$, mọi tập đếm được đều đóng nên không tồn tại tập trù mật đếm được; còn $[0, 1]^{\mathbb{R}}$ với tô-pô tích thì compact nên Lindelöf, và khả ly theo định lý Hewitt–Marczewski–Pondiczery, nhưng không đếm được thứ nhất.)*

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Các khảo sát nền tảng về tiên đề đếm được.*

2. **Ernst Lindelöf** - *"Sur quelques points de la théorie des ensembles"* (1903)  
   *Tính chất phủ con đếm được (Lindelöf).*

3. **René-Maurice Fréchet** - *"Sur quelques points du calcul fonctionnel"* (1906)  
   *Nghiên cứu không gian hội tụ bằng dãy.*

### Giáo trình

4. **James R. Munkres** - *Topology*, 2nd Ed., **§30: Countability Axioms**  
   *Trình bày hệ thống, rõ ràng.*

5. **Stephen Willard** - *General Topology*, **Chapter 4**  
   *Trình bày đầy đủ.*

6. **Ryszard Engelking** - *General Topology*, **Chapter 1.2**  
   *Trình bày chuyên sâu.*

---

## 🔗 Ứng dụng và liên hệ

- **Lý thuyết xấp xỉ:** Không gian hàm liên tục $C([0, 1])$ khả ly nhờ định lý xấp xỉ Weierstrass (đa thức với hệ số hữu tỉ trù mật).
- **Giải tích hàm:** Các không gian Hilbert khả ly ($\ell^2, L^2$) đều có cơ sở trực chuẩn đếm được.
- **Lý thuyết mê-tric hóa:** Tiên đề đếm được thứ hai là điều kiện then chốt trong Định lý mê-tric hóa Urysohn (Bài 03.03).
- **Compact hóa Stone–Čech:** $\beta\mathbb{N}$ không đếm được thứ nhất tại mọi điểm thuộc phần dư $\beta\mathbb{N} \setminus \mathbb{N}$.

---

## Video tham khảo

- **xem trước** [Second Countable Spaces, and the relation to First Countable Spaces](https://www.youtube.com/watch?v=Y6AILGjDoVA) — Andrew McCrady, tiếng Anh. Đếm được thứ nhất và thứ hai, và quan hệ giữa chúng.
- [1st/2nd countable and Lindelöf spaces --Topology Video 21](https://www.youtube.com/watch?v=7ZIrSxNan8o) — MathMajor, tiếng Anh. Thêm Lindelöf vào cùng bức tranh, đúng cụm tiên đề đếm được của bài.
- [Countability axioms | Part 2 | Topology](https://www.youtube.com/watch?v=oL06FkGQttM) — Problemathic, tiếng Anh. Một lối thứ hai, chậm hơn, nếu hai video trên còn đặc.

## 🧩 Bài tập

### Đếm được thứ nhất

1. **Không gian mê-tric:** Trình bày chứng minh chi tiết mọi không gian mê-tric đều đếm được thứ nhất.
2. **Đặc trưng tập đóng bằng dãy:** Trong không gian đếm được thứ nhất, chứng minh $A$ đóng $\iff A$ chứa giới hạn của mọi dãy hội tụ nằm trong $A$.
3. **Tích hữu hạn:** Chứng minh nếu $X, Y$ đếm được thứ nhất thì $X \times Y$ đếm được thứ nhất.

### Đếm được thứ hai

4. **$\mathbb{R}$ đếm được thứ hai:** Chứng minh $\{(a, b) : a, b \in \mathbb{Q}, a < b\}$ là cơ sở đếm được của $\mathbb{R}$.
5. **$\mathbb{R}^n$ đếm được thứ hai:** Mở rộng kết quả trên sang $\mathbb{R}^n$.
6. **Không gian con:** Chứng minh không gian con của không gian đếm được thứ hai là đếm được thứ hai.
7. **Rời rạc không đếm được:** Chứng minh tập không đếm được với tô-pô rời rạc không đếm được thứ hai.

### Không gian khả ly

8. **$\mathbb{Q}$ trù mật:** Chứng minh $\mathbb{Q}$ trù mật trong $\mathbb{R}$.
9. **$\ell^2$ khả ly:** Chứng minh không gian Hilbert $\ell^2 = \{(x_n) : \sum x_n^2 < \infty\}$ khả ly (*Gợi ý:* dùng các dãy có hữu hạn tọa độ hữu tỉ khác $0$).
10. **Tích của hai không gian khả ly:** Nếu $X, Y$ khả ly, chứng minh $X \times Y$ khả ly.

### Không gian Lindelöf

11. **Đếm được thứ hai $\Rightarrow$ Lindelöf:** Trình bày chứng minh chi tiết.
12. **$\mathbb{R}$ là Lindelöf:** Kiểm tra trực tiếp $\mathbb{R}$ thỏa tính chất Lindelöf.
13. **Compact $\Rightarrow$ Lindelöf:** Giải thích ngắn gọn vì sao mọi không gian compact đều Lindelöf.

### Quan hệ giữa các tính chất

14. **Khả ly $\not\Rightarrow$ Đếm được thứ hai:** Chứng minh đường thẳng Sorgenfrey $\mathbb{R}_\ell$ khả ly nhưng không đếm được thứ hai.
15. **Đếm được thứ nhất $\not\Rightarrow$ Đếm được thứ hai:** Kiểm tra ví dụ tập không đếm được với tô-pô rời rạc.
16. **Không gian mê-tric:** Chứng minh trong không gian mê-tric, khả ly $\iff$ đếm được thứ hai.

### Nâng cao

17. **Tô-pô đồng đếm được:** Trên tập không đếm được $X$ với tô-pô đồng đếm được, chứng minh $X$ không đếm được thứ nhất, không khả ly, nhưng là không gian Lindelöf.
18. **Không gian tích $[0, 1]^{\mathbb{R}}$:** Với tô-pô tích trên $[0, 1]^{\mathbb{R}}$, chứng minh không gian này là Lindelöf (nhờ compact) nhưng không đếm được thứ nhất và không đếm được thứ hai.
19. **Tích đếm được:** Chứng minh tích đếm được của các không gian đếm được thứ hai là đếm được thứ hai.

### Câu hỏi suy ngẫm

20. **Vai trò của tiên đề đếm được:** Tóm tắt vai trò của các tiên đề đếm được trong việc sử dụng dãy, lý thuyết xấp xỉ và bài toán mê-tric hóa.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §30 (Countability Axioms)
- **Willard, General Topology:** Chapter 4
- **Engelking, General Topology:** Chapter 1.2
- **Kelley, General Topology:** Chapter 5

---

## 🎓 Tóm tắt

✅ **Đếm được thứ nhất:** Mỗi điểm có cơ sở lân cận đếm được; cho phép dùng dãy để mô tả bao đóng.  
✅ **Đếm được thứ hai:** Toàn bộ tô-pô có cơ sở đếm được; kéo theo cả ba tính chất đếm được thứ nhất, khả ly và Lindelöf.  
✅ **Khả ly:** Tồn tại tập con trù mật đếm được.  
✅ **Lindelöf:** Mọi phủ mở đều có phủ con đếm được; kết hợp với $T_3$ suy ra $T_4$.  
✅ **Không gian mê-tric hóa được:** Đếm được thứ hai $\iff$ khả ly $\iff$ Lindelöf.

**Tiếp theo:** Bài 03.03 sẽ kết hợp tiên đề tách và tiên đề đếm được trong **Định lý Mê-tric hóa Urysohn**.

---

*"Second countability: the topology is not too large to describe."* — Topological intuition

🎯 **Hãy nắm vững bảng so sánh bốn tính chất đếm được qua các ví dụ chuẩn và phản ví dụ.** 🎯

---

**Previous:** [Lecture 03.01: Regular and Normal Spaces](/contents/vi/topology-chapter03/03_01_Regular_Normal_Spaces_Urysohn/)  
**Next:** [Lecture 03.03: Urysohn Metrization Theorem](/contents/vi/topology-chapter03/03_03_Urysohn_Metrization_Theorem/)
