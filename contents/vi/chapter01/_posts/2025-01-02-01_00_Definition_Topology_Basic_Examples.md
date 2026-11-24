---
layout: post
title: "Lecture 01.00: Definition of Topology and Basic Examples"
lang: vi
lang-ref: lecture-01-00
chapter: 1
lecture: 0
categories: [chapter01]
tags: [topology-definition, examples, trivial-topology, discrete-topology]
description: "Định nghĩa chính thức của topology, các axioms, và các ví dụ cơ bản"
---

**Định nghĩa Tô-pô và các Ví dụ cơ bản**

---

## 📖 Tổng quan

Năm 1914, trong cuốn sách kinh điển *Grundzüge der Mengenlehre*, Felix Hausdorff đặt ra một câu hỏi táo bạo: nếu ta vứt bỏ hoàn toàn thước đo khoảng cách $$d(x, y)$$, vứt bỏ tọa độ và phép cộng vectơ, **thứ tối giản nhất còn sót lại để định nghĩa "lân cận" và "hàm liên tục" là gì?** Câu trả lời gói gọn trong đúng **ba tiên đề** về một họ các tập con được gọi tên là **tập mở** — và từ ba tiên đề tưởng chừng giản dị ấy, cả tòa lâu đài Tô-pô học hiện đại mọc lên.

Bài giảng này là bước ngoặt chính thức mở đầu Chương 01: ta sẽ xây dựng định nghĩa hình thức của **không gian tô-pô**, khám phá phổ các ví dụ nền tảng (từ tô-pô tầm thường nghèo nàn nhất đến tô-pô rời rạc giàu có nhất, cùng tô-pô Euclid, đồng hữu hạn, đồng đếm được), học cách so sánh tô-pô "thô hơn" và "mịn hơn", và nhìn thấy cách các khái niệm tập đóng, phần trong, bao đóng, biên đều nảy sinh thuần túy từ tập mở.

**Mạch bài học:** Bản đồ kiến thức nền (tại sao là 3 tiên đề tập mở, phổ tô-pô thô–mịn & đối ngẫu mở–đóng) → Khung giải thích chậm: cầm tay kiểm tra 3 tiên đề tô-pô trên tập 3 phần tử $$\{a,b,c\}$$ và phản ví dụ giao vô hạn trên $$\mathbb{R}$$ → Trực giác & Định nghĩa hình thức → Bài tập & Tóm tắt.

---

## Bản đồ kiến thức nền: Không gian Tô-pô là gì và vì sao ba tiên đề lại có hình dạng như vậy?

### 1. Vì sao hợp *tùy ý* nhưng chỉ giao *hữu hạn*?

Đây là câu hỏi đầu tiên mọi sinh viên tốt nghiệp đại học đều thắc mắc khi nhìn 3 tiên đề tô-pô: (i) $$\emptyset, X \in \tau$$; (ii) hợp tùy ý của các tập mở là mở; (iii) giao **hữu hạn** của các tập mở là mở. Lý do xuất phát trực tiếp từ không gian Euclid $$\mathbb{R}$$: nếu ta cho phép giao *vô hạn* các khoảng mở, ta sẽ thu được $$\bigcap_{n=1}^\infty \left(-\frac{1}{n}, \frac{1}{n}\right) = \{0\}$$, tức điểm đơn lẻ $$\{0\}$$ cũng trở thành tập mở — kéo theo mọi tập con của $$\mathbb{R}$$ đều mở và cấu trúc liên tục của trục số sụp đổ hoàn toàn thành tô-pô rời rạc!

### 2. Phổ các tô-pô trên cùng một tập hợp $$X$$: Thô (Coarse) vs. Mịn (Fine)

Trên cùng một tập điểm $$X$$ có thể tồn tại nhiều tô-pô khác nhau. Nếu $$\tau_1 \subseteq \tau_2$$, ta nói $$\tau_2$$ **mịn hơn** (có nhiều tập mở hơn, dễ phân tách điểm hơn) và $$\tau_1$$ **thô hơn**. Hai cực trị luôn tồn tại là **tô-pô tầm thường** $$\{\emptyset, X\}$$ (thô nhất, mọi điểm dính vào nhau) và **tô-pô rời rạc** $$\mathcal{P}(X)$$ (mịn nhất, mỗi điểm là một hòn đảo mở riêng biệt).

### 3. Tập mở định đoạt mọi khái niệm còn lại

Không cần thêm bất kỳ dữ kiện nào khác: một tập là **đóng** khi phần bù của nó mở; **phần trong** là tập mở lớn nhất nằm trong nó; **bao đóng** là tập đóng nhỏ nhất chứa nó. Chỉ cần thay họ $$\tau$$, cùng một tập con $$A$$ có thể từ mở biến thành đóng hoặc ngược lại!

---

### Khung giải thích (nên đọc chậm): Cầm tay kiểm tra 3 tiên đề tô-pô trên $$X = \{a, b, c\}$$

Hãy tự tay kiểm tra ba họ tập con trên tập 3 phần tử $$X = \{a, b, c\}$$ để cảm nhận rõ ràng từng tiên đề:

1. **Họ $$\tau_1 = \bigl\{\emptyset,\; \{a\},\; \{a, b\},\; X\bigr\}$$ — CÓ phải tô-pô không?**
   - Tiên đề 1: Có cả $$\emptyset$$ và $$X$$. (Đạt!)
   - Tiên đề 2 (hợp tùy ý): $$\{a\} \cup \{a, b\} = \{a, b\} \in \tau_1$$; mọi hợp với $$\emptyset$$ hay $$X$$ đều nằm trong $$\tau_1$$. (Đạt!)
   - Tiên đề 3 (giao hữu hạn): $$\{a\} \cap \{a, b\} = \{a\} \in \tau_1$$. (Đạt!)
   - **Kết luận:** $$\tau_1$$ **là một tô-pô**! (Các tập đóng tương ứng — lấy phần bù trong $$X$$ — là $$X,\; \{b, c\},\; \{c\},\; \emptyset$$.)
2. **Họ $$\tau_2 = \bigl\{\emptyset,\; \{a\},\; \{b\},\; X\bigr\}$$ — CÓ phải tô-pô không?**
   - Kiểm tra hợp: $$\{a\} \in \tau_2$$ và $$\{b\} \in \tau_2$$, nhưng $$\{a\} \cup \{b\} = \{a, b\} \notin \tau_2$$!
   - **Kết luận:** **KHÔNG phải tô-pô** (vi phạm tiên đề hợp). Để sửa thành tô-pô, ta phải bổ sung $$\{a, b\}$$ vào.
3. **Họ $$\tau_3 = \bigl\{\emptyset,\; \{a, b\},\; \{b, c\},\; X\bigr\}$$ — CÓ phải tô-pô không?**
   - Kiểm tra giao: $$\{a, b\} \cap \{b, c\} = \{b\} \notin \tau_3$$!
   - **Kết luận:** **KHÔNG phải tô-pô** (vi phạm tiên đề giao hữu hạn).
4. **Kiểm tra nhanh giao vô hạn trên $$\mathbb{R}$$:** Với $$U_n = \left(-\frac{1}{n}, \frac{1}{n}\right)$$ mở trong $$\mathbb{R}$$, mọi giao hữu hạn $$\bigcap_{n=1}^N U_n = \left(-\frac{1}{N}, \frac{1}{N}\right)$$ vẫn mở, nhưng giao vô hạn $$\bigcap_{n=1}^\infty U_n = \{0\}$$ không chứa khoảng mở $$(-\varepsilon, \varepsilon)$$ nào nên **không mở**!

---

## 🎯 Từ trực giác đến hình thức

### Quá trình trừu tượng hóa

Nhắc lại rằng trong $\mathbb{R}$ với mê-tric Euclid, một tập $U$ là tập mở nếu quanh mỗi điểm $x \in U$ đều có một khoảng mở chứa $x$ và nằm trọn trong $U$. Họ các tập mở trong $\mathbb{R}$ thỏa mãn ba tính chất sau:
1. $\emptyset$ và $\mathbb{R}$ đều là tập mở.
2. **Hợp tùy ý** của các tập mở là tập mở (ví dụ $(0, 1) \cup (2, 3) \cup (4, 5) \cup \dots$ là tập mở).
3. **Giao hữu hạn** của các tập mở là tập mở (ví dụ $(0, 2) \cap (1, 3) = (1, 2)$ là tập mở).

Điểm mấu chốt là ba tính chất này chỉ liên quan đến cấu trúc tập hợp của họ các tập mở, không cần nhắc tới công thức khoảng cách. Năm 1914, Felix Hausdorff đã phát triển ý tưởng chọn trực tiếp một họ tập con thỏa mãn các tiên đề thích hợp để định nghĩa không gian tô-pô mà không cần xuất phát từ mê-tric.

![Felix Hausdorff](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Hausdorff_1913.jpg/300px-Hausdorff_1913.jpg)  
*Felix Hausdorff (1868–1942) - Một trong những người đặt nền móng cho tô-pô đại cương - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_1913.jpg)*

---

## 📐 Định nghĩa hình thức

### 1. Không gian tô-pô (Topological Space)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tô-pô):**  
Cho $X$ là một tập hợp. Một **tô-pô** (*topology*) trên $X$ là một họ $\tau$ các tập con của $X$ (mỗi phần tử của $\tau$ gọi là một **tập mở**) thỏa mãn ba tiên đề sau:
</div>

**(T1) Chứa tập rỗng và toàn không gian:**
$$
\emptyset \in \tau \quad \text{và} \quad X \in \tau
$$

**(T2) Đóng với phép hợp tùy ý:**
$$
\{U_\alpha\}_{\alpha \in I} \subseteq \tau \implies \bigcup_{\alpha \in I} U_\alpha \in \tau
$$
(Hợp của một họ bất kỳ — hữu hạn, đếm được hay không đếm được — các tập mở là tập mở.)

**(T3) Đóng với phép giao hữu hạn:**
$$
U_1, U_2, \ldots, U_n \in \tau \implies U_1 \cap U_2 \cap \cdots \cap U_n \in \tau
$$
(Giao của hữu hạn tập mở là tập mở.)

**Ký hiệu:** Cặp $(X, \tau)$ được gọi là một **không gian tô-pô** (*topological space*).

**Lưu ý quan trọng:** Phép hợp trong (T2) là tùy ý, nhưng phép giao trong (T3) chỉ áp dụng cho **hữu hạn** tập mở. Lý do là giao vô hạn của các tập mở không nhất thiết mở; chẳng hạn trong $\mathbb{R}$, $\bigcap_{n=1}^{\infty} (-1/n, 1/n) = \{0\}$, nhưng $\{0\}$ không phải tập mở trong tô-pô Euclid.

---

### 2. Các ví dụ cơ bản

#### Ví dụ 1: Tô-pô tầm thường (Trivial / Indiscrete Topology)

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
Tô-pô **thô nhất** (*coarsest*) trên $X$ là:
$$
\tau_{\text{trivial}} = \{\emptyset, X\}
$$
</div>

Ở đây chỉ có $\emptyset$ và $X$ là tập mở. Ba tiên đề (T1), (T2), (T3) hiển nhiên thỏa mãn vì $\emptyset \cup X = X$ và $\emptyset \cap X = \emptyset$. Về trực giác, tô-pô này không tách được bất kỳ hai điểm nào của $X$. Chẳng hạn với $X = \{a, b, c\}$, ta có $\tau = \{\emptyset, \{a, b, c\}\}$.

---

#### Ví dụ 2: Tô-pô rời rạc (Discrete Topology)

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
Tô-pô **mịn nhất** (*finest*) trên $X$ là:
$$
\tau_{\text{discrete}} = \mathcal{P}(X) = \text{tất cả tập con của } X
$$
</div>

Mọi tập con của $X$ đều là tập mở, nên (T1), (T2), (T3) tự động thỏa mãn. Về trực giác, mọi điểm đều "cô lập" khỏi các điểm còn lại. Ví dụ với $X = \{a, b\}$, ta có $\tau = \{\emptyset, \{a\}, \{b\}, \{a, b\}\}$. Tô-pô rời rạc chính là tô-pô cảm sinh bởi mê-tric rời rạc.

![Discrete vs Trivial topology](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Topological_structures.svg/500px-Topological_structures.svg.png)  
*So sánh các cấu trúc tô-pô - Nguồn minh họa khái niệm*

---

#### Ví dụ 3: Tô-pô Euclid trên $\mathbb{R}$

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
$\tau = \{U \subseteq \mathbb{R} : U \text{ là hợp của các khoảng mở}\}$ (bao gồm hợp rỗng cho tập $\emptyset$).
</div>

Một số ví dụ về tập mở trong tô-pô Euclid trên $\mathbb{R}$ là $(a, b)$, $(0, 1) \cup (2, 3)$ và $\mathbb{R} \setminus \{0, 1, 2, \dots\}$. Ngược lại, $\mathbb{Q}$ không mở trong $\mathbb{R}$. Đây chính là tô-pô thông thường cảm sinh từ mê-tric Euclid $d(x, y) = |x - y|$.

---

#### Ví dụ 4: Tô-pô đồng hữu hạn (Cofinite Topology)

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
Trên tập $X$, tô-pô đồng hữu hạn là:
$$
\tau_{\text{cofinite}} = \{U \subseteq X : X \setminus U \text{ hữu hạn hoặc } U = \emptyset\}
$$
</div>

Nói cách khác, một tập con $U$ là mở khi và chỉ khi $U = \emptyset$ hoặc phần bù $X \setminus U$ hữu hạn.

**Kiểm tra các tiên đề:**
- **(T1):** $\emptyset \in \tau_{\text{cofinite}}$ theo định nghĩa, và $X \in \tau_{\text{cofinite}}$ vì $X \setminus X = \emptyset$ là tập hữu hạn.
- **(T2):** Cho họ $\{U_\alpha\} \subseteq \tau_{\text{cofinite}}$. Nếu mọi $U_\alpha = \emptyset$ thì $\bigcup U_\alpha = \emptyset \in \tau_{\text{cofinite}}$. Nếu tồn tại $U_{\alpha_0} \neq \emptyset$, thì $X \setminus \bigcup U_\alpha = \bigcap (X \setminus U_\alpha) \subseteq X \setminus U_{\alpha_0}$ là tập con của một tập hữu hạn nên hữu hạn; suy ra $\bigcup U_\alpha \in \tau_{\text{cofinite}}$.
- **(T3):** Cho $U_1, \dots, U_n \in \tau_{\text{cofinite}}$. Nếu có một $U_i = \emptyset$ thì giao bằng $\emptyset$. Nếu mọi $U_i \neq \emptyset$, thì $X \setminus \bigcap_{i=1}^n U_i = \bigcup_{i=1}^n (X \setminus U_i)$ là hợp hữu hạn các tập hữu hạn nên hữu hạn.

**Ví dụ cụ thể ($X = \mathbb{Z}$):** Các tập mở khác rỗng có dạng $\mathbb{Z} \setminus F$ với $F$ hữu hạn (như $\mathbb{Z}$, $\mathbb{Z} \setminus \{0\}$, $\mathbb{Z} \setminus \{1, 2\}$), còn các tập đóng là $\mathbb{Z}$ và mọi tập con hữu hạn của $\mathbb{Z}$. Nếu $X$ hữu hạn thì tô-pô đồng hữu hạn trùng với tô-pô rời rạc; nếu $X$ vô hạn thì nó thô hơn nghiêm ngặt so với tô-pô rời rạc.

---

#### Ví dụ 5: Tô-pô đồng đếm được (Cocountable Topology)

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
Trên tập $X$ (thường xét $X$ không đếm được), tô-pô đồng đếm được là:
$$
\tau_{\text{cocountable}} = \{U \subseteq X : X \setminus U \text{ đếm được (kể cả hữu hạn) hoặc } U = \emptyset\}
$$
</div>

Trên $\mathbb{R}$, các tập mở khác rỗng là phần bù của các tập đếm được (chẳng hạn $\mathbb{R}$, $\mathbb{R} \setminus \mathbb{Q}$, $\mathbb{R} \setminus \{x_1, x_2, \dots\}$), còn các tập đóng là $\mathbb{R}$ và mọi tập con đếm được (hoặc hữu hạn).

---

### 3. So sánh các tô-pô (Comparing Topologies)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Thô hơn / Mịn hơn):**  
Cho $\tau_1, \tau_2$ là hai tô-pô trên cùng một tập $X$.
</div>

- $\tau_1$ **thô hơn** (*coarser*) $\tau_2$ nếu $\tau_1 \subseteq \tau_2$ (ít tập mở hơn).
- $\tau_2$ **mịn hơn** (*finer*) $\tau_1$ nếu $\tau_2 \supseteq \tau_1$ (nhiều tập mở hơn).

**Ví dụ trên $X = \{a, b, c\}$:**
1. $\tau_1 = \{\emptyset, X\}$ (tầm thường)
2. $\tau_2 = \{\emptyset, \{a\}, X\}$
3. $\tau_3 = \{\emptyset, \{a\}, \{b\}, \{a, b\}, X\}$
4. $\tau_4 = \mathcal{P}(X)$ (rời rạc)

Ta có chuỗi bao hàm $\tau_1 \subseteq \tau_2 \subseteq \tau_3 \subseteq \tau_4$. Tô-pô tầm thường luôn là tô-pô thô nhất, còn tô-pô rời rạc luôn là tô-pô mịn nhất trên mọi tập $X$.

**So sánh các tô-pô trên $\mathbb{R}$:**
$$
\tau_{\text{trivial}} \subseteq \tau_{\text{cofinite}} \subseteq \tau_{\text{Euclidean}} \subseteq \tau_{\text{discrete}}
$$
Đồng thời $\tau_{\text{cofinite}} \subseteq \tau_{\text{cocountable}} \subseteq \tau_{\text{discrete}}$. Lưu ý rằng $\tau_{\text{cocountable}}$ và $\tau_{\text{Euclidean}}$ **không so sánh được với nhau**: $\mathbb{R} \setminus \mathbb{Q}$ mở trong $\tau_{\text{cocountable}}$ nhưng không mở trong $\tau_{\text{Euclidean}}$, còn $(0, 1)$ mở trong $\tau_{\text{Euclidean}}$ nhưng không mở trong $\tau_{\text{cocountable}}$.

---

### 4. Tập đóng (Closed Sets)

<div class="textbook-definition" markdown="1">
**Định nghĩa:**  
Trong không gian tô-pô $(X, \tau)$, tập con $F \subseteq X$ được gọi là **tập đóng** (*closed*) nếu:
$$
X \setminus F \in \tau
$$
</div>

Nói cách khác, $F$ đóng khi và chỉ khi phần bù của $F$ là tập mở. Trong $\mathbb{R}$ với tô-pô Euclid, các đoạn $[a, b]$, tập đơn điểm $\{x\}$ và $\mathbb{N}$ đều đóng, còn $\mathbb{Q}$ không đóng vì $\mathbb{R} \setminus \mathbb{Q}$ không mở.

**Tính chất đối ngẫu của tập đóng:**
1. $\emptyset$ và $X$ là các tập đóng.
2. **Giao tùy ý** của các tập đóng là tập đóng.
3. **Hợp hữu hạn** của các tập đóng là tập đóng.

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:** Áp dụng công thức De Morgan cùng các tiên đề (T1)–(T3) của tập mở.
</div>

**Lưu ý:** Một tập có thể vừa mở vừa đóng (ví dụ $\emptyset$ và $X$), và cũng có thể không mở cũng không đóng (ví dụ $[0, 1)$ trong $\mathbb{R}$).

![Open vs Closed sets](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Open_closed_sets.svg/500px-Open_closed_sets.svg.png)  
*Phân biệt tập mở và tập đóng - Nguồn minh họa khái niệm*

---

### 5. Phần trong, bao đóng và biên

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phần trong — Interior):**  
**Phần trong** của $A \subseteq X$ là hợp của tất cả các tập mở chứa trong $A$:
$$
\text{int}(A) = A° = \bigcup \{U \in \tau : U \subseteq A\}
$$
</div>

Trong $\mathbb{R}$: $\text{int}([0, 1]) = (0, 1)$, $\text{int}(\mathbb{Q}) = \emptyset$ và $\text{int}((0, 1)) = (0, 1)$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Bao đóng — Closure):**  
**Bao đóng** của $A \subseteq X$ là giao của tất cả các tập đóng chứa $A$:
$$
\overline{A} = \text{cl}(A) = \bigcap \{F : F \text{ closed}, A \subseteq F\}
$$
</div>

Trong $\mathbb{R}$: $\text{cl}((0, 1)) = [0, 1]$, $\text{cl}(\mathbb{Q}) = \mathbb{R}$ ($\mathbb{Q}$ trù mật trong $\mathbb{R}$), và $\text{cl}(\{1/n : n \in \mathbb{N}\}) = \{1/n : n \in \mathbb{N}\} \cup \{0\}$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Biên — Boundary):**  
**Biên** của $A$ là:
$$
\partial A = \overline{A} \setminus A°
$$
</div>

Trong $\mathbb{R}$: $\partial((0, 1)) = \{0, 1\}$, $\partial([0, 1]) = \{0, 1\}$, và $\partial(\mathbb{Q}) = \mathbb{R}$.

**Các tính chất cơ bản:**
1. $\text{int}(A) \subseteq A \subseteq \text{cl}(A)$.
2. $A$ mở $\iff A = \text{int}(A)$.
3. $A$ đóng $\iff A = \text{cl}(A)$.
4. $\text{cl}(A) = A \cup \partial A$.

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình lịch sử

1. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Trình bày định nghĩa tiên đề hóa đầu tiên cho không gian tô-pô (không gian Hausdorff).*

2. **Kazimierz Kuratowski** - *"Sur l'opération A̅ de l'Analysis Situs"* (1922)  
   *Định nghĩa tô-pô thông qua toán tử bao đóng.*

3. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Đặt nền móng trực giác cho tô-pô học trước giai đoạn tiên đề hóa.*

4. **Pavel Alexandroff** - *"Über stetige Abbildungen kompakter Räume"* (1927)  
   *Đóng góp quan trọng cho lý thuyết tô-pô đại cương.*

### Giáo trình

5. **James R. Munkres** - *Topology*, 2nd Ed., **§12–13: Topological Spaces**  
   *Tài liệu chuẩn, trình bày mạch lạc.*

6. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 2**  
   *Giới thiệu nhẹ nhàng kèm nhiều ví dụ.*

7. **John L. Kelley** - *General Topology* (1955)  
   *Giáo trình cao học kinh điển và toàn diện.*

8. **Ryszard Engelking** - *General Topology* (1989)  
   *Tài liệu tra cứu chuyên sâu về tô-pô đại cương.*

---

## 🔗 Ứng dụng và liên hệ

### Khoa học máy tính — Tô-pô số (Digital Topology)
Trong xử lý ảnh số, lưới điểm ảnh (*pixel*) được nghiên cứu bằng các khái niệm liên thông và biên của tô-pô rời rạc; hai điểm ảnh trong ảnh 2D có thể xét lân cận theo cạnh ($4$-liên thông) hoặc cả góc ($8$-liên thông).

### Vật lý — Đa tạp
Trong thuyết tương đối rộng, không-thời gian được mô hình hóa bằng một đa tạp $4$ chiều — cục bộ giống $\mathbb{R}^4$ nhưng có thể mang cấu trúc tô-pô toàn cục phức tạp.

### Khoa học dữ liệu — Phân tích dữ liệu tô-pô (TDA)
Homology bền vững phân tích cấu trúc hình dạng của dữ liệu chiều cao nhằm phát hiện các cụm và "lỗ" dựa trên cấu trúc tô-pô qua nhiều tỉ lệ.

### Toán học — Tính liên tục tổng quát
Định nghĩa liên tục $\varepsilon$-$\delta$ trong giải tích chỉ là trường hợp riêng của định nghĩa tô-pô (nghịch ảnh của mọi tập mở là tập mở), vốn áp dụng được cho mọi không gian tô-pô.

### Ví dụ thực tế
Khi phóng to hay thu nhỏ bản đồ GPS, tỉ lệ khoảng cách thay đổi nhưng cấu trúc kết nối và ranh giới giữa các tuyến đường, khu vực vẫn giữ nguyên — đó là góc nhìn tô-pô.

---

## Video tham khảo

- **xem trước** [Basic Topology 2 | Topological Spaces](https://www.youtube.com/watch?v=Wxa-pMaxd7Q) — The Bright Side of Mathematics, tiếng Anh. Ba tiên đề tập mở và bước từ metric sang không gian tô-pô, đúng định nghĩa của bài.
- [[TÔPÔ ĐẠI CƯƠNG] Không gian Tô pô: Định nghĩa và ví dụ.](https://www.youtube.com/watch?v=1LiNBmWl-S8) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Cùng định nghĩa và các ví dụ rời rạc, tầm thường, nói bằng tiếng Việt.
- [This open problem taught me what topology is](https://www.youtube.com/watch?v=IQqtsm-bBRU) — 3Blue1Brown, tiếng Anh. Vì sao người ta chịu khó trừu tượng hóa như vậy, trước khi quay lại các ví dụ cực đoan.

## 🧩 Bài tập

### Kiến thức cơ bản

1. **Kiểm tra tiên đề tô-pô:**  
   Cho $X = \{a, b, c\}$. Các họ sau có phải là tô-pô trên $X$ không? Giải thích lý do:
   - a) $\tau = \{\emptyset, \{a\}, \{a, b\}, X\}$
   - b) $\tau = \{\emptyset, \{a\}, \{b\}, \{a, b\}, X\}$
   - c) $\tau = \{\emptyset, \{a\}, \{b\}, \{c\}, X\}$

2. **Liệt kê tập mở và tập đóng:**  
   Với $X = \{1, 2, 3, 4\}$ trang bị tô-pô đồng hữu hạn, hãy liệt kê tất cả các tập mở và tập đóng.

3. **Tô-pô đồng hữu hạn trên $\mathbb{N}$:**  
   Trên $\mathbb{N}$ với tô-pô đồng hữu hạn, các tập sau là tập mở hay tập đóng?
   - a) $\{1, 2, 3, 4, 5\}$
   - b) $\{n \in \mathbb{N} : n > 100\}$
   - c) $\{2, 4, 6, 8, \dots\}$ (tập các số chẵn)

### Phần trong, bao đóng và biên

4. **Tính phần trong:**  
   Trong $\mathbb{R}$ với tô-pô Euclid, tìm $\text{int}(A)$:
   - a) $A = [0, 1] \cup \{2\}$
   - b) $A = \mathbb{Q} \cap [0, 1]$
   - c) $A = \{1/n : n \in \mathbb{N}\}$

5. **Tính bao đóng:**  
   Trong $\mathbb{R}$ với tô-pô Euclid, tìm $\text{cl}(A)$:
   - a) $A = (0, 1) \cup (2, 3)$
   - b) $A = \{1/n : n \in \mathbb{N}\}$
   - c) $A = \mathbb{Z}$

6. **Tính biên:**  
   Tìm $\partial A$ trong $\mathbb{R}$:
   - a) $A = (0, 1]$
   - b) $A = \mathbb{Q}$
   - c) $A$ là tập Cantor

### So sánh tô-pô

7. **Sắp xếp các tô-pô:**  
   Trên $X = \{a, b, c, d\}$, cho:
   - $\tau_1 = \{\emptyset, X\}$
   - $\tau_2 = \{\emptyset, \{a\}, X\}$
   - $\tau_3 = \{\emptyset, \{a\}, \{b, c\}, \{a, b, c\}, X\}$
   
   Sắp xếp các tô-pô trên theo thứ tự từ thô hơn đến mịn hơn.

8. **Euclid và rời rạc:**  
   Chứng minh tô-pô Euclid trên $\mathbb{R}$ thô hơn tô-pô rời rạc. Có tồn tại tô-pô nào nằm nghiêm ngặt giữa chúng không?

### Nâng cao

9. **Xây dựng tô-pô giới hạn dưới:**  
   Trên $\mathbb{R}$, định nghĩa $U$ là tập mở khi và chỉ khi $U$ là hợp của các nửa khoảng $[a, b)$. Chứng minh đây là một tô-pô trên $\mathbb{R}$ và kiểm tra xem nó có trùng với tô-pô Euclid không.

10. **Tính liên tục với tô-pô tầm thường ở miền đích:**  
    Cho $(X, \tau)$ là không gian tô-pô bất kỳ và $(Y, \tau_{\text{trivial}})$ mang tô-pô tầm thường. Chứng minh mọi ánh xạ $f: X \to Y$ đều liên tục (dùng định nghĩa nghịch ảnh của tập mở là tập mở).

11. **Tô-pô đồng hữu hạn trên $\mathbb{R}$:**  
    Trong $\mathbb{R}$ với tô-pô đồng hữu hạn:
    - a) $(0, 1)$ có mở không?
    - b) $\mathbb{R} \setminus \mathbb{N}$ có mở không?
    - c) So sánh tô-pô này với tô-pô Euclid.

12. **Tính chất của bao đóng:**  
    Chứng minh trong mọi không gian tô-pô:
    - a) $\text{cl}(\emptyset) = \emptyset$
    - b) $\text{cl}(A \cup B) = \text{cl}(A) \cup \text{cl}(B)$
    - c) $\text{cl}(\text{cl}(A)) = \text{cl}(A)$

### Câu hỏi suy ngẫm

13. **Ý nghĩa ba tiên đề:**  
    Giải thích vì sao ba tiên đề (T1), (T2), (T3) là tự nhiên khi tổng quát hóa khái niệm tập mở từ không gian mê-tric.

14. **Hợp vô hạn và giao hữu hạn:**  
    Vì sao (T2) cho phép hợp tùy ý nhưng (T3) chỉ cho phép giao hữu hạn? Nêu ví dụ minh họa điều gì xảy ra nếu yêu cầu đóng với giao vô hạn.

15. **Tập mở và tập đóng:**  
    Có thể định nghĩa một tô-pô bằng cách chọn trước họ các tập đóng thỏa mãn các tiên đề đối ngẫu rồi mới định nghĩa tập mở không?

---

## 📚 Đọc thêm

- **Munkres, Topology:** §12–13 (Topological Spaces, Basis)
- **Morris, Topology Without Tears:** Chapter 2 (Topological Spaces)
- **Willard, General Topology:** Chapter 1 (Topological Spaces)
- **Armstrong, Basic Topology:** Chapter 2 (Topological Spaces)

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã xây dựng định nghĩa cốt lõi của môn học:

✅ **Không gian tô-pô:** Cặp $(X, \tau)$ với $\tau$ thỏa mãn ba tiên đề (T1), (T2), (T3).  
✅ **Ba tiên đề tập mở:** Chứa $\emptyset, X$; đóng với hợp tùy ý; đóng với giao hữu hạn.  
✅ **Ví dụ cơ bản:** Tô-pô tầm thường, rời rạc, Euclid, đồng hữu hạn và đồng đếm được.  
✅ **So sánh tô-pô:** Quan hệ thô hơn ($\subseteq$) và mịn hơn ($\supseteq$).  
✅ **Tập đóng:** Khái niệm đối ngẫu định nghĩa qua phần bù của tập mở.  
✅ **Phần trong, bao đóng, biên:** Các toán tử dẫn xuất trực tiếp từ tập mở.

**Điểm chính:**
- Tô-pô cho phép mô tả cấu trúc không gian mà không cần mê-tric.
- Tập mở là khái niệm nguyên thủy; mọi khái niệm khác đều suy ra từ đó.
- Trên cùng một tập $X$ có thể trang bị nhiều cấu trúc tô-pô khác nhau.

**Tiếp theo:** Trong Bài 01.01, ta sẽ tìm hiểu **Cơ sở và Tiền cơ sở** (*Basis and Subbasis*) — cách mô tả và so sánh tô-pô gọn nhẹ hơn thông qua các họ tập sinh đơn giản.

---

*"Topology is the study of continuity in its most general form."* — Anonymous

🎯 **Hãy làm nhiều bài tập kiểm tra tiên đề và tính phần trong, bao đóng để quen với tư duy trừu tượng của tô-pô.** 🎯

---

**Previous Chapter:** [Chapter 00: Foundations](/contents/vi/topology-chapter00/)  
**Next:** [Lecture 01.01: Basis and Subbasis for a Topology](/contents/vi/topology-chapter01/01_01_Basis_Subbasis/)
