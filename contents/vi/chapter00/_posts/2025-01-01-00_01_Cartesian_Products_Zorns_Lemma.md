---
layout: post
title: "Lecture 00.01: Cartesian Products and Zorn's Lemma"
lang: vi
lang-ref: lecture-00-01
chapter: 0
lecture: 1
categories: [chapter00]
tags: [cartesian-product, axiom-of-choice, zorns-lemma, well-ordering]
description: "Tích Cartesian, Tiên đề Lựa chọn, Bổ đề Zorn và ứng dụng trong topology"
---

**Tích Đề-các và Bổ đề Zorn**

---

## 📖 Tổng quan

Triết gia kiêm nhà toán học Bertrand Russell từng kể một câu chuyện nổi tiếng để giải thích tiên đề kỳ lạ nhất của toán học hiện đại: giả sử bạn có **vô hạn đôi giày** và muốn chọn ra mỗi đôi một chiếc — chẳng cần phép màu nào cả, chỉ cần ra quy tắc *"luôn chọn chiếc bên trái"*. Nhưng nếu thay bằng **vô hạn đôi tất giống hệt nhau** (không có trái–phải để phân biệt), làm sao bạn viết ra một quy tắc chọn đúng một chiếc từ mỗi đôi? Câu hỏi tưởng như đùa cợt ấy lại dẫn thẳng tới **Tiên đề Lựa chọn (Axiom of Choice — AC)** và người anh em quyền năng của nó: **Bổ đề Zorn**.

Trong bài này, ta đi từ phép xây dựng quen thuộc nhất — **tích Đề-các** (nơi đường thẳng $$\mathbb{R}$$ nhân với chính nó tạo ra mặt phẳng $$\mathbb{R}^2$$, hay hai đường tròn $$S^1 \times S^1$$ dệt nên hình xuyến $$T^2$$) — sang thế giới của **tích vô hạn**, nơi chỉ riêng câu hỏi *"tích vô hạn của các tập khác rỗng có khác rỗng không?"* cũng đã tương đương hoàn toàn với Tiên đề Lựa chọn.

**Mạch bài học:** Bản đồ kiến thức nền (tích vô hạn như không gian hàm, Tiên đề Lựa chọn & Bổ đề Zorn) → Khung giải thích chậm: cầm tay phân biệt phần tử cực đại và phần tử lớn nhất trên một tập sắp thứ tự bộ phận hữu hạn → Trực giác & Định nghĩa hình thức → Ứng dụng trong tô-pô (Định lý Tychonoff) → Bài tập & Tóm tắt.

---

## Bản đồ kiến thức nền: Tích vô hạn, Tiên đề Lựa chọn và Bổ đề Zorn nghiên cứu những gì?

### 1. Tích Đề-các vô hạn như một không gian hàm số

Với hai tập $$A, B$$, phần tử của $$A \times B$$ là cặp $$(a, b)$$. Nhưng với một họ vô hạn tùy ý $$\{X_\alpha\}_{\alpha \in I}$$, ta không thể viết thành bộ hữu hạn; thay vào đó, mỗi phần tử của $$\prod_{\alpha \in I} X_\alpha$$ được định nghĩa là một **hàm lựa chọn** $$f: I \to \bigcup_{\alpha \in I} X_\alpha$$ sao cho $$f(\alpha) \in X_\alpha$$ với mọi $$\alpha \in I$$. Cách nhìn này biến không gian dãy số $$\mathbb{R}^\mathbb{N}$$ hay không gian hàm số $$\mathbb{R}^{[0,1]}$$ thành những tích Đề-các đích thực.

### 2. Tiên đề Lựa chọn (AC) và ranh giới giữa xây dựng được và tồn tại thuần túy

Tiên đề Lựa chọn khẳng định tích Đề-các của mọi họ tập khác rỗng đều khác rỗng. AC không cho ta công thức cụ thể để chọn, mà chỉ bảo đảm sự **tồn tại**. Dù từng gây tranh cãi (vì nó kéo theo nghịch lý Banach–Tarski), ngày nay AC là trụ cột không thể thiếu trong giải tích hàm (Định lý Hahn–Banach) và tô-pô đại cương (Định lý Tychonoff).

### 3. Bổ đề Zorn và nghệ thuật tìm "đối tượng cực đại"

Trong thực hành chứng minh, các nhà toán học hiếm khi dùng AC trực tiếp mà dùng dạng tương đương tiện lợi hơn là **Bổ đề Zorn**: *nếu trong một tập sắp thứ tự bộ phận (poset), mọi xích (tập con sắp thứ tự toàn phần) đều có chặn trên, thì tập đó có ít nhất một phần tử cực đại.* Nhờ Bổ đề Zorn, ta chứng minh gọn gàng sự tồn tại của cơ sở Hamel cho mọi không gian vector, i-đê-an cực đại trong đại số, và **siêu lọc (ultrafilter)** trong tô-pô.

---

### Khung giải thích (nên đọc chậm): Cầm tay kiểm tra xích, chặn trên và phần tử cực đại trên một Poset hữu hạn

Để không bao giờ nhầm giữa **phần tử cực đại (maximal element)** và **phần tử lớn nhất (maximum)** khi áp dụng Bổ đề Zorn, hãy tự tay kiểm tra trên tập sắp thứ tự bộ phận gồm 5 tập con của $$\{1, 2, 3\}$$:
$$
P = \bigl\{\emptyset,\; \{1\},\; \{2\},\; \{1, 2\},\; \{1, 3\}\bigr\}
$$
với quan hệ thứ tự là phép bao hàm $$\subseteq$$:

1. **Liệt kê các xích tối đa (tập con sắp thứ tự toàn phần) trong $$P$$:**
   - Xích 1: $$\emptyset \subset \{1\} \subset \{1, 2\}$$ → có chặn trên trong $$P$$ là $$\{1, 2\}$$.
   - Xích 2: $$\emptyset \subset \{1\} \subset \{1, 3\}$$ → có chặn trên trong $$P$$ là $$\{1, 3\}$$.
   - Xích 3: $$\emptyset \subset \{2\} \subset \{1, 2\}$$ → có chặn trên trong $$P$$ là $$\{1, 2\}$$.
2. **Tìm các phần tử cực đại:**
   - Có phần tử nào trong $$P$$ lớn hơn hẳn $$\{1, 2\}$$ không? **Không** (vì $$\{1,2,3\} \notin P$$) → $$\{1, 2\}$$ là **phần tử cực đại**.
   - Có phần tử nào trong $$P$$ lớn hơn hẳn $$\{1, 3\}$$ không? **Không** → $$\{1, 3\}$$ cũng là **phần tử cực đại**!
3. **Kiểm tra phần tử lớn nhất:** Không có phần tử nào chứa đồng thời cả $$\{1, 2\}$$ và $$\{1, 3\}$$, nên $$P$$ **không có phần tử lớn nhất**, dù có tới **hai phần tử cực đại**! Bổ đề Zorn chỉ bảo đảm tồn tại *ít nhất một* phần tử cực đại (chứ không duy nhất và không phải lớn nhất) — đó là lý do một không gian vector có vô số cơ sở Hamel khác nhau.

---

## 🎯 Từ trực giác đến hình thức

### Khái niệm tích Đề-các

Xét một ví dụ quen thuộc: giả sử bạn thiết kế áo thun với tập màu sắc $C = \{\text{đỏ}, \text{xanh}, \text{vàng}\}$ và tập kích cỡ $S = \{\text{nhỏ}, \text{vừa}, \text{lớn}\}$. Tập hợp tất cả các cách ghép một màu với một kích cỡ chính là tích Đề-các: $C \times S = \{(\text{đỏ}, \text{nhỏ}), (\text{đỏ}, \text{vừa}), (\text{đỏ}, \text{lớn}), (\text{xanh}, \text{nhỏ}), \dots\}$, gồm tất cả $|C \times S| = 3 \times 3 = 9$ cặp.

Về mặt hình học, nếu đặt $C$ trên trục hoành và $S$ trên trục tung, thì $C \times S$ tương ứng với toàn bộ các điểm nút của một lưới $3 \times 3$. Mặt phẳng $\mathbb{R}^2$ cũng được xây dựng theo đúng cách này từ hai đường thẳng $\mathbb{R}$: mỗi điểm $(x, y)$ là một cặp có thứ tự với hoành độ $x$ thuộc trục thứ nhất và tung độ $y$ thuộc trục thứ hai.

![Cartesian product visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Cartesian_Product_qtl1.svg/400px-Cartesian_Product_qtl1.svg.png)  
*Tích Đề-các của hai tập hợp - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cartesian_Product_qtl1.svg)*

### Từ hữu hạn đến vô hạn

Nếu có **vô hạn** tập hợp $\{A_1, A_2, A_3, \dots\}$, ta định nghĩa tích của chúng như thế nào? Câu hỏi này đưa ta đến trực tiếp vai trò của **Tiên đề Lựa chọn**.

---

## 📐 Định nghĩa hình thức

### 1. Cặp có thứ tự và tích Đề-các

<div class="textbook-definition" markdown="1">
**Định nghĩa (Cặp có thứ tự — Ordered Pair):**  
Cặp có thứ tự $(a, b)$ được định nghĩa theo Kuratowski là:

$$
(a, b) := \{\{a\}, \{a, b\}\}
$$
</div>

**Tính chất đặc trưng:**
$$
(a, b) = (c, d) \iff (a = c) \land (b = d)
$$

**Trực giác:** Thứ tự các thành phần đóng vai trò quyết định, chẳng hạn $(1, 2) \neq (2, 1)$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tích Đề-các — Cartesian Product):**  
Với hai tập $A$ và $B$, tích Đề-các của chúng là:

$$
A \times B = \{(a, b) : a \in A, b \in B\}
$$
</div>

**Ví dụ cụ thể:** $\mathbb{R} \times \mathbb{R} = \mathbb{R}^2$ là mặt phẳng tọa độ; $\mathbb{R} \times \mathbb{R} \times \mathbb{R} = \mathbb{R}^3$ là không gian ba chiều; và $\{0, 1\} \times \{0, 1\} = \{(0, 0), (0, 1), (1, 0), (1, 1)\}$ là tập gồm $4$ cặp nhị phân.

**Một số tính chất cơ bản:** Thứ nhất, tích Đề-các không giao hoán: $A \times B \neq B \times A$ (trừ khi $A = B$ hoặc một trong hai tập rỗng) vì $(a, b) \neq (b, a)$ khi $a \neq b$. Thứ hai, lực lượng của tích bằng tích các lực lượng: $|A \times B| = |A| \cdot |B|$ với tập hữu hạn (và mở rộng sang trường hợp vô hạn theo phép nhân lực lượng). Thứ ba, tích với tập rỗng luôn rỗng: $A \times \emptyset = \emptyset$, vì không thể lập được cặp có thứ tự nào khi một thành phần không có phần tử.

---

### 2. Tích tùy ý (Arbitrary Products)

Làm thế nào để định nghĩa tích của một họ gồm vô hạn tập hợp $\{A_i : i \in I\}$, với $I$ là tập chỉ số (*index set*)? Theo trực giác, mỗi phần tử của tích ứng với một cách chọn một phần tử từ mỗi tập $A_i$. Để diễn đạt chính xác điều này, ta định nghĩa tích bằng ngôn ngữ ánh xạ:

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tích của một họ tập hợp có chỉ số):**  
Tích Đề-các của họ $\{A_i\}_{i \in I}$ là:

$$
\prod_{i \in I} A_i = \left\{ f: I \to \bigcup_{i \in I} A_i \; \middle| \; \forall i \in I: f(i) \in A_i \right\}
$$
</div>

**Trực giác:** Mỗi phần tử của tích là một **hàm lựa chọn** (*choice function*) gán cho mỗi chỉ số $i \in I$ một phần tử thuộc $A_i$.

**Ví dụ về tích vô hạn:** $\mathbb{R}^{\mathbb{N}}$ (tích của đếm được bản sao của $\mathbb{R}$) là tập tất cả các dãy số thực vô hạn — mỗi dãy $(x_1, x_2, x_3, \dots)$ là một ánh xạ chọn $x_i \in \mathbb{R}$ ứng với mỗi chỉ số $i \in \mathbb{N}$. Tương tự, $\{0, 1\}^{\mathbb{N}}$ là tập tất cả các dãy nhị phân vô hạn, một đối tượng cơ bản trong tô-pô được gọi là không gian Cantor.

![Infinite product visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/9/92/Binary_tree_structure.svg/400px-Binary_tree_structure.svg.png)  
*Cây nhị phân biểu diễn $\{0,1\}^{\mathbb{N}}$ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Binary_tree_structure.svg)*

---

### 3. Tiên đề Lựa chọn (Axiom of Choice — AC)

**Phát biểu trực quan:**  
Cho một họ các tập hợp khác rỗng $\{A_i\}_{i \in I}$. Luôn tồn tại một hàm lựa chọn lấy đúng một phần tử từ mỗi tập $A_i$.

**Phát biểu hình thức:**

$$
\forall \mathcal{F}: \left(\emptyset \notin \mathcal{F}\right) \implies \exists f: \mathcal{F} \to \bigcup \mathcal{F} \text{ sao cho } \forall A \in \mathcal{F}: f(A) \in A
$$

**Ví dụ minh họa của Bertrand Russell:** Giả sử bạn có vô hạn đôi giày; ta có thể chọn một chiếc từ mỗi đôi mà không cần Tiên đề Lựa chọn nhờ một quy tắc tường minh: "luôn chọn chiếc bên trái". Nhưng nếu thay bằng vô hạn đôi tất hoàn toàn giống nhau (không phân biệt trái phải), ta không có quy tắc rõ ràng nào để chọn một chiếc từ mỗi đôi. Khi đó, ta cần Tiên đề Lựa chọn để khẳng định rằng một hàm lựa chọn như vậy vẫn tồn tại, dù tiên đề này không chỉ ra cách xây dựng cụ thể hàm đó.

**Hệ quả tương đương:**

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mệnh đề "Với mọi họ khác rỗng $\{A_i\}_{i \in I}$ gồm các tập khác rỗng ($A_i \neq \emptyset$ với mọi $i \in I$), tích $\prod_{i \in I} A_i$ khác rỗng" tương đương với Tiên đề Lựa chọn:

$$
\prod_{i \in I} A_i \neq \emptyset \iff \text{Axiom of Choice}
$$
</div>

**Vai trò của Tiên đề Lựa chọn trong tô-pô:** Nhiều kết quả cốt lõi của tô-pô phụ thuộc trực tiếp vào AC. **Định lý Tychonoff** khẳng định tích tùy ý các không gian compact là compact — kết quả này thậm chí tương đương với AC trong hệ ZF. Trong đại số tuyến tính, định lý khẳng định mọi không gian vector đều có cơ sở (cơ sở Hamel) cũng cần AC trong trường hợp vô hạn chiều. Trong tô-pô, sự tồn tại của **compact hóa Stone–Čech** cho mọi không gian hoàn toàn chính quy (Tychonoff) cũng dựa trên AC.

---

### 4. Bổ đề Zorn (Zorn's Lemma)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập sắp thứ tự bộ phận — Poset):**  
Một **tập sắp thứ tự bộ phận** (*partially ordered set*, viết tắt *poset*) $(A, \le)$ là tập $A$ cùng với quan hệ $\le$ thỏa mãn:
1. **Phản xạ (Reflexive):** $a \le a$
2. **Phản đối xứng (Antisymmetric):** $(a \le b) \land (b \le a) \Rightarrow (a = b)$
3. **Bắc cầu (Transitive):** $(a \le b) \land (b \le c) \Rightarrow (a \le c)$
</div>

**Ví dụ về poset:** Tập số thực với thứ tự thông thường $(\mathbb{R}, \le)$ là một poset. Tập lũy thừa $\mathcal{P}(X)$ với quan hệ bao hàm $(\mathcal{P}(X), \subseteq)$ cũng là một poset, vì $A \subseteq B$ và $B \subseteq A$ kéo theo $A = B$. Trong tô-pô, họ tất cả các tô-pô trên một tập cố định $X$ sắp thứ tự theo quan hệ bao hàm tạo thành một poset: $\tau_1 \subseteq \tau_2$ nghĩa là $\tau_1$ thô hơn (*coarser*, ít tập mở hơn) $\tau_2$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Xích — Chain):**  
Một **xích** (*chain*, hay tập con sắp thứ tự toàn phần) trong poset $(A, \le)$ là tập con $C \subseteq A$ sao cho mọi $a, b \in C$ đều so sánh được với nhau: $a \le b$ hoặc $b \le a$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Cận trên — Upper Bound):**  
Phần tử $u \in A$ là **cận trên** (*upper bound*) của $C$ nếu $\forall c \in C: c \le u$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phần tử cực đại — Maximal Element):**  
Phần tử $m \in A$ là **phần tử cực đại** (*maximal element*) nếu không tồn tại $a \in A$ sao cho $m < a$.
</div>

**Lưu ý:** Phần tử cực đại (*maximal*) khác với phần tử lớn nhất (*maximum*). Một poset có thể có nhiều phần tử cực đại mà không có phần tử lớn nhất.

**Bổ đề Zorn (Zorn's Lemma):**

> **Nếu mọi xích trong poset $(A, \le)$ đều có ít nhất một cận trên trong $A$, thì $A$ có ít nhất một phần tử cực đại.**

$$
\left(\forall \text{ chain } C \subseteq A: \exists u \in A: \forall c \in C: c \leq u\right) \implies \exists m \in A: m \text{ is maximal}
$$

![Zorn's Lemma visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Hasse_diagram_of_powerset_of_3.svg/300px-Hasse_diagram_of_powerset_of_3.svg.png)  
*Biểu đồ Hasse minh họa phần tử cực đại - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hasse_diagram_of_powerset_of_3.svg)*

**Trực giác:** Nếu dọc theo mọi con đường đi lên (xích) trong $A$ ta luôn tìm được một điểm chặn ở phía trên trong $A$, thì phải tồn tại ít nhất một "đỉnh" mà từ đó không thể đi cao hơn nữa.

---

### 5. Sự tương đương: AC $\iff$ Bổ đề Zorn $\iff$ Nguyên lý Sắp thứ tự tốt

Ba mệnh đề sau đây **tương đương nhau** trong hệ tiên đề ZF:

1. **Tiên đề Lựa chọn (Axiom of Choice — AC)**
2. **Bổ đề Zorn (Zorn's Lemma — ZL)**
3. **Nguyên lý Sắp thứ tự tốt (Well-Ordering Principle — WOP):** Mọi tập hợp đều có thể trang bị một quan hệ thứ tự tốt.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập sắp thứ tự tốt — Well-ordered set):**  
Một tập $A$ với quan hệ thứ tự toàn phần $\le$ là **sắp thứ tự tốt** (*well-ordered*) nếu mọi tập con khác rỗng của $A$ đều có phần tử nhỏ nhất.
</div>

**Ví dụ về thứ tự tốt:** Tập số tự nhiên $(\mathbb{N}, \le)$ được sắp thứ tự tốt — mọi tập con khác rỗng của $\mathbb{N}$ đều có phần tử nhỏ nhất, và đó là cơ sở của phép quy nạp toán học. Ngược lại, tập số nguyên $(\mathbb{Z}, \le)$ không sắp thứ tự tốt vì bản thân $\mathbb{Z}$ không có phần tử nhỏ nhất. Tương tự, $(\mathbb{R}, \le)$ không sắp thứ tự tốt vì khoảng mở $(0, 1)$ không có phần tử nhỏ nhất.

**Hệ quả của WOP:** Tồn tại một quan hệ thứ tự $\preceq$ trên $\mathbb{R}$ (khác thứ tự $\le$ thông thường) sao cho $(\mathbb{R}, \preceq)$ là tập sắp thứ tự tốt, dù không thể viết ra một cách tường minh.

**Nhận xét:** WOP thoạt nhìn rất xa lạ với trực giác, nhưng lại tương đương logic với AC — một tiên đề thường được chấp nhận khá tự nhiên.

---

### 6. Ứng dụng trong tô-pô

**Ứng dụng 1: Tồn tại họ cực đại có tính chất giao hữu hạn (siêu lọc / ultrafilter)**

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi họ tập con $\mathcal{F}_0$ của $X$ có tính chất giao hữu hạn (giao của hữu hạn phần tử bất kỳ đều khác rỗng) đều mở rộng được thành một họ cực đại $\mathcal{F}$ có tính chất giao hữu hạn.
</div>

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:** Xét poset gồm tất cả các họ tập con của $X$ chứa $\mathcal{F}_0$ và có tính chất giao hữu hạn, sắp thứ tự theo quan hệ bao hàm $\subseteq$. Hợp của một xích bất kỳ các họ như vậy vẫn có tính chất giao hữu hạn nên là một cận trên của xích. Theo Bổ đề Zorn, tồn tại một họ cực đại $\mathcal{F}$.
</div>

*(Lưu ý: Bản thân một không gian tô-pô $(X, \tau)$ luôn hiển nhiên có một cơ sở là chính $\tau$ mà không cần dùng Bổ đề Zorn; ngược lại, việc chứng minh mọi không gian vector vô hạn chiều có cơ sở Hamel hay sự tồn tại của siêu lọc mới thực sự cần Bổ đề Zorn.)*

**Ứng dụng 2: Định lý Tychonoff**

**Định lý Tychonoff:**  
Tích tùy ý của các không gian compact là một không gian compact (với tô-pô tích).

**Lưu ý:** Chứng minh định lý Tychonoff sử dụng trực tiếp Bổ đề Zorn (thông qua họ cực đại có tính chất giao hữu hạn ở Ứng dụng 1); hơn nữa, trong ZF, định lý Tychonoff tương đương với Tiên đề Lựa chọn.

**Ứng dụng 3: Nguyên lý cực đại Hausdorff**

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi xích trong một poset đều có thể mở rộng thành một xích cực đại.
</div>

**Ý nghĩa:** Nguyên lý này (cũng tương đương với Bổ đề Zorn) thường được dùng trong tô-pô để chứng minh sự tồn tại của các đối tượng cực đại như siêu lọc và các phép compact hóa.

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Bài báo kinh điển

1. **Ernst Zermelo** - *"Beweis, daß jede Menge wohlgeordnet werden kann"* (1904)  
   *Chứng minh đầu tiên của Định lý Sắp thứ tự tốt (sử dụng Tiên đề Lựa chọn).*

2. **Max Zorn** - *"A Remark on Method in Transfinite Algebra"* (1935)  
   *Trình bày "Bổ đề Zorn" như một công cụ thay thế tiện lợi cho quy nạp siêu hạn.*

3. **Kurt Gödel** - *"The Consistency of the Axiom of Choice"* (1938)  
   *Chứng minh AC nhất quán với ZF (nếu ZF nhất quán).*

4. **Paul Cohen** - *"The Independence of the Continuum Hypothesis"* (1963)  
   *Chứng minh AC độc lập với ZF (đoạt Huy chương Fields).*

### Giáo trình

5. **James R. Munkres** - *Topology*, 2nd Ed., **§9: Infinite Sets and Axiom of Choice**  
   *Trình bày rõ ràng về AC và tô-pô tích.*

6. **Thomas Jech** - *The Axiom of Choice* (1973)  
   *Chuyên khảo toàn diện về AC và các hệ quả.*

7. **John L. Kelley** - *General Topology* (1955), **Chapter 0**  
   *Cách trình bày kinh điển về các nguyên lý lựa chọn.*

---

## 🔗 Ứng dụng và liên hệ

### Vật lý — Cơ học lượng tử
**Không gian Fock:** Trong lý thuyết trường lượng tử, không gian Fock được xây dựng từ tổng trực tiếp các tích tensor; sự tồn tại cơ sở của các không gian vô hạn chiều liên quan chặt chẽ tới các nguyên lý lựa chọn.

### Giải tích hàm
**Định lý Hahn–Banach:** Một trong những định lý nền tảng của giải tích hàm, có chứng minh sử dụng Bổ đề Zorn (thực tế yếu hơn AC một chút nhưng không chứng minh được chỉ trong ZF).

### Đại số
**Cơ sở của không gian vector:** Mệnh đề "mọi không gian vector đều có cơ sở" được chứng minh nhờ Bổ đề Zorn; trong ZF không có AC, có thể tồn tại không gian vector không có cơ sở.

### Lý thuyết độ đo và hình học
**Nghịch lý Banach–Tarski:** Sử dụng Tiên đề Lựa chọn, có thể phân hoạch một hình cầu đặc trong $\mathbb{R}^3$ thành hữu hạn mảnh (chẳng hạn $5$ mảnh) rồi dùng phép dời hình lắp lại thành hai hình cầu đặc giống hệt hình cầu ban đầu. Điều này không xảy ra với vật thể vật lý vì các mảnh đó không đo được theo nghĩa Lebesgue.

### Ví dụ thực tế
**Phép nối bảng trong cơ sở dữ liệu (Database Joins):** Phép tích chéo (*cross join*) hai bảng dữ liệu thực hiện đúng tích Đề-các trên tập các bản ghi, với số hàng kết quả bằng tích số hàng của hai bảng. Tô-pô tích là phiên bản có cấu trúc tô-pô của phép xây dựng này.

---

## Video tham khảo

- **xem trước** [Cartesian Product -- Applications, 10a Essence of Set Theory](https://www.youtube.com/watch?v=9tbZJ2dwCts) — Mirek Olšák, tiếng Anh. Tích Descartes, trước hết hữu hạn rồi mới tới chỗ tiên đề chọn bắt đầu can thiệp.
- [11. Set Theory. Infinite Cartesian Products](https://www.youtube.com/watch?v=EySmEsfo9rY) — Antonio Montalban, tiếng Anh. Tích vô hạn trong lý thuyết tập hợp, đúng nửa đầu của bài.
- [Zorn's Lemma Demystified](https://www.youtube.com/watch?v=oRH-HTrAvxw) — sudgylacmoe, tiếng Anh. Phát biểu bổ đề Zorn và vì sao một thứ tự bộ phận có phần tử tối đại.

## 🧩 Bài tập

### Câu hỏi khái niệm

1. **Hình dung tích Đề-các:**  
   Vẽ hình minh họa $[0, 1] \times [0, 1]$ (hình vuông đơn vị) và $S^1 \times [0, 1]$ (mặt trụ).  
   - Mô tả hình học của các không gian này.
   - Không gian $S^1 \times S^1$ có hình dạng như thế nào? (*Gợi ý:* Hình xuyến / Torus.)

2. **Lực lượng của tích:**  
   Chứng minh rằng $|\mathbb{R} \times \mathbb{R}| = |\mathbb{R}|$ bằng cách xây dựng một song ánh (hoặc đơn ánh hai chiều và áp dụng định lý Cantor–Bernstein).  
   (*Gợi ý:* Kỹ thuật đan xen chữ số của Cantor.)

3. **Hàm lựa chọn:**  
   Cho họ tập hợp {% raw %}{{1}, {1,2}, {1,2,3}, ...}{% endraw %}.  
   - Viết tường minh một hàm lựa chọn cho họ này.
   - Việc chọn này có cần Tiên đề Lựa chọn không? Vì sao?

4. **Áp dụng Bổ đề Zorn:**  
   Xét poset $(\mathcal{P}(\mathbb{N}), \subseteq)$ gồm tất cả các tập con của $\mathbb{N}$.
   - Nêu một ví dụ về xích trong poset này.
   - Cận trên của xích đó là gì?
   - Các phần tử cực đại của poset này là gì?

5. **Thử thách về thứ tự tốt:**  
   Giả sử $(\mathbb{R}, \preceq)$ là một tập sắp thứ tự tốt.
   - Nếu $x_0$ là phần tử nhỏ nhất, ta có biết cụ thể $x_0$ là số thực nào không?
   - Phần tử kế tiếp ngay sau $x_0$ (nếu có) được xác định như thế nào?
   - Quan hệ thứ tự này có khớp với trực giác quen thuộc về trục số thực không?

### Bài tập nâng cao

6. **Tích đếm được của các tập có ít nhất hai phần tử:**  
   - Chứng minh: nếu mỗi $A_i$ có ít nhất $2$ phần tử, thì $\prod_{i=1}^{\infty} A_i$ là tập không đếm được.
   - Suy ra kết luận gì về $\{0, 1\}^{\mathbb{N}}$?

7. **Gợi mở về tô-pô tích:**  
   Trong $\mathbb{R}^2 = \mathbb{R} \times \mathbb{R}$, xét đĩa mở $U = \{(x, y) : x^2 + y^2 < 1\}$.
   - $U$ có thể viết dưới dạng $A \times B$ với $A, B \subseteq \mathbb{R}$ không?
   - Điều này gợi ý gì về cách định nghĩa các tập mở trong tô-pô tích?

8. **Tính độc lập của AC:**  
   Tìm hiểu về tập "hữu hạn Dedekind" (*Dedekind-finite set*) — tập hợp không có song ánh với bất kỳ tập con thực sự nào của chính nó.
   - Trong ZF (không có AC), có thể tồn tại tập vô hạn nhưng vẫn hữu hạn Dedekind.
   - Điều này có thể xảy ra nếu chấp nhận AC không?

### Câu hỏi suy ngẫm

9. **Tranh luận về tính xây dựng:**  
   Một số nhà toán học dè dặt với Tiên đề Lựa chọn vì nó mang tính "phi xây dựng" (*non-constructive*).  
   - Vì sao AC được gọi là phi xây dựng?
   - Theo bạn, vì sao phần lớn toán học hiện đại vẫn chấp nhận AC?

10. **So sánh ba mệnh đề tương đương:**  
    So sánh Tiên đề Lựa chọn, Bổ đề Zorn và Nguyên lý Sắp thứ tự tốt.  
    - Phát biểu nào gần với trực giác nhất?
    - Phát biểu nào thuận tiện nhất khi áp dụng trong chứng minh tô-pô?

---

## 📚 Đọc thêm

- **Munkres, Topology:** §9 (Infinite Sets and AC)
- **Kelley, General Topology:** Chapter 0 (Preliminaries on Set Theory)
- **Halmos, Naive Set Theory:** §15–16 (Axiom of Choice)
- **Jech, The Axiom of Choice:** Chapters 1–3 (Comprehensive treatment)
- **Herrlich, Axiom of Choice (Lecture Notes in Math):** Modern perspective

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã tìm hiểu các nội dung chính:

✅ **Tích Đề-các:** Cách xây dựng tập hợp và không gian mới từ các tập hợp cho trước.  
✅ **Tích vô hạn:** Được hình thức hóa thông qua các hàm lựa chọn.  
✅ **Tiên đề Lựa chọn (AC):** Khẳng định tích của một họ bất kỳ các tập khác rỗng là khác rỗng.  
✅ **Bổ đề Zorn:** Công cụ chứng minh sự tồn tại của các phần tử cực đại trong poset.  
✅ **Tính tương đương:** AC $\iff$ Bổ đề Zorn $\iff$ Nguyên lý Sắp thứ tự tốt.

**Điểm chính:**
- Tích Đề-các là cơ sở tập hợp của tô-pô tích.
- AC có phát biểu đơn giản nhưng kéo theo nhiều hệ quả sâu rộng.
- Bổ đề Zorn thường là dạng thuận tiện nhất để chứng minh sự tồn tại của các đối tượng cực đại.
- Ba phát biểu AC, Bổ đề Zorn và WOP tương đương nhau trong ZF, tùy bài toán mà chọn dạng phù hợp.

**Liên hệ với tô-pô:**
- Tô-pô tích cho các không gian như $\mathbb{R}^n$, hình xuyến $S^1 \times S^1$ và các không gian vô hạn chiều.
- Định lý Tychonoff: tích tùy ý của các không gian compact là compact.
- Sự tồn tại của siêu lọc và họ cực đại có tính chất giao hữu hạn.

**Tiếp theo:** Trong Bài 00.02, ta sẽ ôn tập về **Logic toán học và các kỹ thuật chứng minh** — nền tảng để đọc hiểu và tự viết các chứng minh tô-pô chặt chẽ.

---

*"The Axiom of Choice is obviously true, the Well-Ordering Principle obviously false, and who can tell about Zorn's Lemma?"* — Jerry Bona

🎯 **Hãy thử vẽ các tích Đề-các đơn giản và suy ngẫm về trường hợp vô hạn.** 🎯

---

**Previous:** [Lecture 00.00: Set Theory, Functions, and Relations](/contents/vi/topology-chapter00/00_00_Set_Theory_Functions_Relations/)  
**Next:** [Lecture 00.02: Logic and Mathematical Proofs](/contents/vi/topology-chapter00/00_02_Logic_Mathematical_Proofs/)
