---
layout: post
title: "Lecture 01.02: Closed Sets, Closure, and Interior"
lang: vi
lang-ref: lecture-01-02
chapter: 1
lecture: 2
categories: [chapter01]
tags: [closed-sets, closure, interior, boundary, limit-points]
description: "Tập đóng, closure operator, interior, boundary, và limit points"
---

**Tập đóng, Bao đóng và Phần trong**

---

## 📖 Tổng quan

Hai bài trước tập trung vào **tập mở** — khái niệm nguyên thủy của tô-pô. Tuy nhiên, cấu trúc tô-pô mang tính đối ngẫu rõ rệt: song hành với tập mở là **tập đóng** (*closed set*). Từ cặp khái niệm này hình thành ba toán tử quan trọng tác động lên mọi tập con: **phần trong** ($\text{int}$) lấy phần nằm hoàn toàn bên trong, **bao đóng** ($\text{cl}$) bổ sung thêm phần biên, và **biên** ($\partial$) xác định ranh giới giữa trong và ngoài.

Các toán tử này xuất hiện xuyên suốt toàn bộ tô-pô học. Tính **trù mật** (*density*) được định nghĩa bằng điều kiện $\text{cl}(A) = X$; tính **liên tục** có đặc trưng tương đương qua nghịch ảnh tập đóng hoặc qua toán tử bao đóng; và việc phân loại vị trí của điểm so với một tập hợp (điểm trong, điểm biên, điểm tụ, điểm cô lập) đều dựa trực tiếp vào chúng.

Bài giảng này xây dựng có hệ thống các tiên đề của tập đóng, các tính chất của toán tử bao đóng (hệ tiên đề Kuratowski), điểm tụ và điểm cô lập, toán tử phần trong cùng quan hệ đối ngẫu với bao đóng, khái niệm biên, tập trù mật và tập không đâu trù mật.

---

## 🎯 Từ trực giác đến hình thức

### Hình ảnh vùng đất và ranh giới

Hãy hình dung một vùng đất $A$ trên bản đồ. Mọi điểm trên bản đồ rơi vào một trong ba vị trí so với $A$:
- **Phần trong (Interior):** Các điểm nằm hoàn toàn bên trong $A$ — di chuyển một khoảng đủ nhỏ theo bất kỳ hướng nào vẫn ở trong $A$.
- **Biên (Boundary):** Đường viền ngăn cách — mọi vùng nhỏ quanh điểm biên đều chứa cả điểm trong $A$ lẫn điểm ngoài $A$.
- **Phần ngoài (Exterior):** Các điểm nằm hoàn toàn bên ngoài $A$.
- **Bao đóng (Closure):** Gồm toàn bộ $A$ cộng thêm các điểm biên của nó.

![Interior, Boundary, Exterior](https://upload.wikimedia.org/wikipedia/commons/thumb/0/04/Interior_Boundary_Exterior.svg/500px-Interior_Boundary_Exterior.svg.png)  
*Phần trong (xanh), Biên (đỏ), Phần ngoài (trắng) - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Interior_Boundary_Exterior.svg)*

**Ví dụ cụ thể trong $\mathbb{R}$:** Xét nửa khoảng $A = [0, 1)$.
- **Phần trong:** $\text{int}(A) = (0, 1)$, vì mọi điểm trong $(0, 1)$ đều có một khoảng mở nhỏ nằm trọn trong $A$, còn điểm $0$ thì không (mọi khoảng mở chứa $0$ đều chứa số âm không thuộc $A$).
- **Biên:** $\partial A = \{0, 1\}$, vì mọi lân cận của $0$ hoặc $1$ đều giao với cả $A$ lẫn $\mathbb{R} \setminus A$.
- **Bao đóng:** $\text{cl}(A) = [0, 1]$, thu được bằng cách bổ sung điểm biên $1$ vào $A$.

Ta luôn có chuỗi bao hàm $\text{int}(A) \subseteq A \subseteq \text{cl}(A)$, trong đó $\text{int}(A)$ là tập mở lớn nhất chứa trong $A$, còn $\text{cl}(A)$ là tập đóng nhỏ nhất chứa $A$. Hơn nữa:
- $A$ mở $\iff A = \text{int}(A)$;
- $A$ đóng $\iff A = \text{cl}(A)$;
- $\partial A = \text{cl}(A) \setminus \text{int}(A)$.

---

## 📐 Định nghĩa hình thức

### 1. Tập đóng (Closed Sets)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập đóng):**  
Trong không gian tô-pô $(X, \tau)$, tập con $F \subseteq X$ là **tập đóng** (*closed*) nếu phần bù của nó là tập mở:

$$
F \text{ closed} \iff X \setminus F \in \tau
$$
</div>

**Ví dụ trong $\mathbb{R}$ (tô-pô Euclid):** Các đoạn $[a, b]$, tập đơn điểm $\{x\}$, tập số tự nhiên $\mathbb{N}$ và tập Cantor đều là các tập đóng.

**Hệ tiên đề đối ngẫu cho tập đóng:**

<div class="textbook-theorem" markdown="1">
**Định lý:** Họ tất cả các tập đóng trong $(X, \tau)$ thỏa mãn:
</div>

**(C1)** $\emptyset$ và $X$ là các tập đóng.

**(C2)** **Giao tùy ý** của các tập đóng là tập đóng:
$$
\{F_\alpha\}_{\alpha \in I} \text{ closed} \implies \bigcap_{\alpha \in I} F_\alpha \text{ closed}
$$

**(C3)** **Hợp hữu hạn** của các tập đóng là tập đóng:
$$
F_1, \ldots, F_n \text{ closed} \implies F_1 \cup \cdots \cup F_n \text{ closed}
$$

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:** Sử dụng công thức De Morgan:
- $X \setminus \left(\bigcap F_\alpha\right) = \bigcup (X \setminus F_\alpha) \in \tau$ (hợp tùy ý các tập mở là tập mở).
- $X \setminus (F_1 \cup \cdots \cup F_n) = (X \setminus F_1) \cap \cdots \cap (X \setminus F_n) \in \tau$ (giao hữu hạn các tập mở là tập mở). ∎
</div>

**So sánh đối ngẫu giữa tập mở và tập đóng:**

| Tập mở | Tập đóng |
|-----------|-------------|
| $\emptyset, X$ mở | $\emptyset, X$ đóng |
| Đóng với hợp tùy ý | Đóng với **giao tùy ý** |
| Đóng với giao hữu hạn | Đóng với **hợp hữu hạn** |

**Lưu ý:** "Không mở" không đồng nghĩa với "đóng", và "không đóng" không đồng nghĩa với "mở". Một tập có thể vừa mở vừa đóng (gọi là tập *vừa đóng vừa mở*, tiếng Anh: *clopen*), hoặc không mở cũng không đóng (như $[0, 1)$ trong $\mathbb{R}$).

---

### 2. Toán tử bao đóng (Closure Operator)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Bao đóng):**  
Cho $A \subseteq X$. **Bao đóng** (*closure*) của $A$ là giao của tất cả các tập đóng chứa $A$:

$$
\overline{A} = \text{cl}(A) = \bigcap \{F : F \text{ closed}, A \subseteq F\}
$$
</div>

Về trực giác, $\text{cl}(A)$ là **tập đóng nhỏ nhất** chứa $A$.

**Ví dụ trong $\mathbb{R}$:** $\text{cl}((0, 1)) = [0, 1]$; $\text{cl}([0, 1]) = [0, 1]$; $\text{cl}(\mathbb{Q}) = \mathbb{R}$; và $\text{cl}(\{1/n : n \in \mathbb{N}\}) = \{1/n : n \in \mathbb{N}\} \cup \{0\}$.

<div class="textbook-theorem" markdown="1">
**Định lý (Các tính chất của bao đóng):**

Toán tử bao đóng thỏa mãn bốn **tiên đề bao đóng Kuratowski**:
</div>

**(K1) Tính mở rộng (Extensivity):**
$$
A \subseteq \overline{A}
$$

**(K2) Tính lũy đẳng (Idempotence):**
$$
\overline{\overline{A}} = \overline{A}
$$

**(K3) Bảo toàn phép hợp hữu hạn:**
$$
\overline{A \cup B} = \overline{A} \cup \overline{B}
$$

**(K4) Bảo toàn tập rỗng:**
$$
\overline{\emptyset} = \emptyset
$$

<div class="textbook-proof" markdown="1">
**Chứng minh:**
</div>

- **(K1):** $\text{cl}(A)$ là giao của các tập chứa $A$, nên $A \subseteq \text{cl}(A)$.
- **(K2):** Vì $\text{cl}(A)$ là tập đóng, tập đóng nhỏ nhất chứa nó là chính nó: $\text{cl}(\text{cl}(A)) = \text{cl}(A)$.
- **(K3):** Vì $\text{cl}(A) \cup \text{cl}(B)$ là tập đóng chứa $A \cup B$, ta có $\text{cl}(A \cup B) \subseteq \text{cl}(A) \cup \text{cl}(B)$. Ngược lại, từ $A \subseteq A \cup B$ và $B \subseteq A \cup B$ suy ra $\text{cl}(A) \subseteq \text{cl}(A \cup B)$ và $\text{cl}(B) \subseteq \text{cl}(A \cup B)$, dẫn đến $\text{cl}(A) \cup \text{cl}(B) \subseteq \text{cl}(A \cup B)$.
- **(K4):** Vì $\emptyset$ đóng nên $\text{cl}(\emptyset) = \emptyset$.

**Kết quả của Kuratowski:** Ngược lại, bất kỳ toán tử $\text{cl}: \mathcal{P}(X) \to \mathcal{P}(X)$ nào thỏa mãn (K1)–(K4) đều xác định duy nhất một tô-pô trên $X$ bằng quy tắc: $F$ đóng $\iff F = \text{cl}(F)$.

---

### 3. Điểm tụ (Limit Points)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Điểm tụ):**  
Điểm $x \in X$ là **điểm tụ** (*limit point* hay *accumulation point*) của $A \subseteq X$ nếu:

$$
\forall U \in \tau, x \in U: (U \cap A) \setminus \{x\} \neq \emptyset
$$
</div>

Nói bằng lời, mọi lân cận mở của $x$ đều chứa ít nhất một điểm của $A$ **khác $x$**.

**Ví dụ trong $\mathbb{R}$:**
1. Với $A = (0, 1)$, mọi điểm $x \in [0, 1]$ đều là điểm tụ của $A$ (kể cả $0$ và $1$, vì mọi khoảng mở quanh $0$ đều chứa điểm thuộc $(0, 1)$); các điểm ngoài $[0, 1]$ không phải điểm tụ.
2. Với $A = \{1/n : n \in \mathbb{N}\}$, $0$ là điểm tụ duy nhất của $A$; mọi điểm $1/n$ đều không phải điểm tụ vì đều có khoảng mở đủ nhỏ chỉ chứa duy nhất điểm đó của $A$.

![Limit points visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7a/Limit_point_illustration.svg/400px-Limit_point_illustration.svg.png)  
*Điểm tụ của một tập hợp - Nguồn minh họa khái niệm*

<div class="textbook-definition" markdown="1">
**Định nghĩa (Điểm cô lập — Isolated Point):**  
Điểm $x \in A$ là **điểm cô lập** nếu $x$ không phải là điểm tụ của $A$, tức tồn tại lân cận mở $U$ của $x$ sao cho $U \cap A = \{x\}$.
</div>

Chẳng hạn, trong $A = \{1/n : n \in \mathbb{N}\}$ mọi phần tử đều là điểm cô lập; trong $(0, 1)$ không có điểm cô lập nào; còn trong $\{0\} \cup (1, 2)$ thì $0$ là điểm cô lập.

Ký hiệu $A'$ là tập tất cả các điểm tụ của $A$ (gọi là *tập dẫn xuất*, *derived set*).

<div class="textbook-theorem" markdown="1">
**Định lý (Biểu diễn bao đóng qua điểm tụ):**
$$
\overline{A} = A \cup A'
$$
</div>

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:**
</div>

- **Chiều ($\subseteq$):** Lấy $x \in \text{cl}(A)$. Nếu $x \in A$ thì xong. Nếu $x \notin A$, giả sử phản chứng $x \notin A'$; khi đó tồn tại tập mở $U \ni x$ sao cho $U \cap A = \emptyset$, suy ra $A \subseteq X \setminus U$ (tập đóng), dẫn đến $\text{cl}(A) \subseteq X \setminus U$ nên $x \notin \text{cl}(A)$, mâu thuẫn.
- **Chiều ($\supseteq$):** Hiển nhiên $A \subseteq \text{cl}(A)$. Với mọi $x \in A'$ và mọi tập đóng $F \supseteq A$, nếu $x \notin F$ thì $U = X \setminus F$ là tập mở chứa $x$ thỏa $U \cap A = \emptyset$, trái với $x \in A'$. Vậy $x \in F$ với mọi tập đóng $F \supseteq A$, tức $x \in \text{cl}(A)$. ∎

---

### 4. Toán tử phần trong (Interior Operator)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phần trong):**  
**Phần trong** (*interior*) của $A$ là hợp của tất cả các tập mở chứa trong $A$:

$$
A° = \text{int}(A) = \bigcup \{U \in \tau : U \subseteq A\}
$$
</div>

Về trực giác, $\text{int}(A)$ là **tập mở lớn nhất** nằm trong $A$. Trong $\mathbb{R}$, ta có $\text{int}([0, 1]) = (0, 1)$, $\text{int}((0, 1)) = (0, 1)$, $\text{int}(\mathbb{Q}) = \emptyset$ và $\text{int}(\{x\}) = \emptyset$.

<div class="textbook-theorem" markdown="1">
**Định lý (Các tính chất của phần trong):**
</div>

**(I1) Tính thu hẹp:**
$$
\text{int}(A) \subseteq A
$$

**(I2) Tính lũy đẳng:**
$$
\text{int}(\text{int}(A)) = \text{int}(A)
$$

**(I3) Bảo toàn phép giao hữu hạn:**
$$
\text{int}(A \cap B) = \text{int}(A) \cap \text{int}(B)
$$

**(I4) Bảo toàn không gian:**
$$
\text{int}(X) = X
$$

**Quan hệ đối ngẫu với bao đóng:**

<div class="textbook-theorem" markdown="1">
**Định lý:**
$$
\text{int}(A) = X \setminus \overline{X \setminus A}
$$

$$
\overline{A} = X \setminus \text{int}(X \setminus A)
$$
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
$\text{int}(A)$ là tập mở lớn nhất chứa trong $A$, nên phần bù của nó là tập đóng nhỏ nhất chứa $X \setminus A$, tức $\overline{X \setminus A}$. Do đó $\text{int}(A) = X \setminus \overline{X \setminus A}$. Thay $A$ bằng $X \setminus A$ ta thu được đẳng thức thứ hai.
</div>

---

### 5. Biên (Boundary)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Biên):**  
**Biên** (*boundary* hay *frontier*) của $A$ là:

$$
\partial A = \overline{A} \setminus \text{int}(A)
$$
</div>

**Biểu diễn tương đương:**
$$
\partial A = \overline{A} \cap \overline{X \setminus A}
$$

Như vậy, $x \in \partial A$ khi và chỉ khi mọi lân cận của $x$ đều giao với cả $A$ lẫn $X \setminus A$. Trong $\mathbb{R}$, ta có $\partial([0, 1]) = \partial((0, 1)) = \{0, 1\}$, $\partial(\mathbb{Q}) = \mathbb{R}$ và $\partial(\emptyset) = \emptyset$.

<div class="textbook-theorem" markdown="1">
**Định lý (Phân hoạch không gian):**  
Với mọi $A \subseteq X$, không gian $X$ được phân hoạch thành ba tập rời nhau:
$$
X = \text{int}(A) \sqcup \partial A \sqcup \text{int}(X \setminus A)
$$
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Suy trực tiếp từ các định nghĩa (dành làm bài tập).
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Các tính chất của biên):**
1. $\partial A = \partial(X \setminus A)$ (tính đối xứng).
2. $\partial A = \emptyset \iff A$ vừa mở vừa đóng (*clopen*).
3. $A$ đóng $\iff \partial A \subseteq A$.
4. $A$ mở $\iff \partial A \subseteq X \setminus A$ (tức $A \cap \partial A = \emptyset$).
</div>

---

### 6. Tập trù mật (Dense Sets)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập trù mật):**  
Tập con $A \subseteq X$ được gọi là **trù mật** (*dense*) trong $X$ nếu:

$$
\overline{A} = X
$$
</div>

Điều này tương đương với việc mọi tập mở khác rỗng trong $X$ đều giao với $A$, hoặc mọi điểm của $X$ hoặc thuộc $A$ hoặc là điểm tụ của $A$.

**Ví dụ:** Trong $\mathbb{R}$, cả $\mathbb{Q}$ và tập số vô tỉ $\mathbb{R} \setminus \mathbb{Q}$ đều trù mật; $(0, 1)$ trù mật trong $[0, 1]$; còn $\{0, 1\}$ không trù mật trong $\mathbb{R}$ vì $\text{cl}(\{0, 1\}) = \{0, 1\} \neq \mathbb{R}$.

![Dense set illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/Dense_set_rationals.svg/400px-Dense_set_rationals.svg.png)  
*Tập số hữu tỉ $\mathbb{Q}$ trù mật trong $\mathbb{R}$ - Nguồn minh họa khái niệm*

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập không đâu trù mật — Nowhere Dense):**  
Tập $A$ được gọi là **không đâu trù mật** nếu $\text{int}(\text{cl}(A)) = \emptyset$.
</div>

Về trực giác, $A$ "mỏng" đến mức ngay cả bao đóng của nó cũng không chứa bất kỳ tập mở khác rỗng nào. Ví dụ trong $\mathbb{R}$ gồm $\mathbb{N}$, tập Cantor và $\{1/n : n \in \mathbb{N}\}$.

**Định lý phạm trù Baire (gợi mở):** Trong một không gian mê-tric đầy đủ, hợp đếm được các tập không đâu trù mật luôn có phần trong rỗng.

<div class="textbook-theorem" markdown="1">
**Hệ quả:** $\mathbb{R}$ không thể biểu diễn thành hợp đếm được của các tập không đâu trù mật.
</div>

---

### 7. Các đặc trưng tương đương của bao đóng

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Với $A \subseteq X$ và $x \in X$, bốn mệnh đề sau **tương đương**:

1. $x \in \text{cl}(A)$.
2. Mọi lân cận của $x$ đều giao với $A$.
3. Mọi tập mở chứa $x$ đều giao với $A$.
4. $x \in A$ hoặc $x$ là điểm tụ của $A$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**
</div>

- **(1 $\Rightarrow$ 2):** Giả sử phản chứng tồn tại lân cận $N$ của $x$ sao cho $N \cap A = \emptyset$. Khi đó tồn tại tập mở $U \in \tau$ với $x \in U \subseteq N$, nên $U \cap A = \emptyset$. Suy ra $X \setminus U$ là tập đóng chứa $A$, kéo theo $\text{cl}(A) \subseteq X \setminus U$, mâu thuẫn với $x \in \text{cl}(A) \cap U$.
- **(2 $\Rightarrow$ 3):** Hiển nhiên vì mọi tập mở chứa $x$ đều là lân cận của $x$.
- **(3 $\Rightarrow$ 4):** Nếu $x \in A$ thì đúng. Nếu $x \notin A$, thì với mọi tập mở $U \ni x$, ta có $U \cap A \neq \emptyset$ nên $(U \cap A) \setminus \{x\} \neq \emptyset$, tức $x$ là điểm tụ của $A$.
- **(4 $\Rightarrow$ 1):** Vì $\text{cl}(A) = A \cup A'$, ta có ngay $x \in \text{cl}(A)$. ∎

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Kazimierz Kuratowski** - *"Sur l'opération Ā de l'Analysis Situs"* (1922)  
   *Xây dựng hệ tiên đề Kuratowski cho toán tử bao đóng.*

2. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Phát triển lý thuyết điểm tụ và tập dẫn xuất.*

3. **René-Louis Baire** - *"Sur les fonctions de variables réelles"* (1899)  
   *Định lý phạm trù Baire và tập không đâu trù mật.*

### Giáo trình

4. **James R. Munkres** - *Topology*, 2nd Ed., **§17: Closed Sets and Limit Points**  
   *Tài liệu tham khảo chuẩn.*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 3**  
   *Trình bày rõ ràng kèm nhiều ví dụ.*

6. **John L. Kelley** - *General Topology*, **Chapter 2**  
   *Trình bày toàn diện.*

7. **Stephen Willard** - *General Topology*, **Chapter 2**  
   *Cách tiếp cận chặt chẽ.*

---

## 🔗 Ứng dụng và liên hệ

### Giải tích — Hội tụ và bao đóng
Trong không gian mê-tric, sự hội tụ của dãy liên hệ trực tiếp với bao đóng: một điểm $x$ thuộc $\overline{A}$ khi và chỉ khi tồn tại một dãy trong $A$ hội tụ về $x$.

### Giải tích số — Xấp xỉ hữu tỉ
Tính trù mật của $\mathbb{Q}$ trong $\mathbb{R}$ bảo đảm mọi số thực đều có thể xấp xỉ tùy ý gần bởi số hữu tỉ — cơ sở cho biểu diễn số dấu phẩy động trên máy tính.

### Khoa học dữ liệu — Phân cụm theo mật độ
Thuật toán DBSCAN phân loại điểm dữ liệu thành điểm lõi (*core points*, tương tự điểm trong), điểm biên (*border points*, tương tự điểm biên) và điểm nhiễu dựa trên mật độ lân cận.

### Xử lý ảnh — Phát hiện biên
Bài toán tìm đường viền vật thể trong xử lý ảnh tương ứng với việc xác định tập biên $\partial A$ của vùng ảnh, là động lực hình học cho các bộ lọc phát hiện cạnh như Canny.

### Ví dụ thực tế
Nghịch lý đường bờ biển cho thấy đường biên giữa đất liền và biển có thể mang cấu trúc hình học rất phức tạp (hình học fractal), dù về mặt tô-pô nó vẫn là tập biên giữa hai vùng.

---

## Video tham khảo

- **xem trước** [[Tôpô đại cương] Bài 11.  Bao đóng và phần trong: định nghĩa và ví dụ](https://www.youtube.com/watch?v=OYSX3KdXZ8c) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Bao đóng và phần trong bằng tiếng Việt, đúng hai khái niệm trung tâm của bài.
- [Basic Topology 3 | Closed Sets and Closure](https://www.youtube.com/watch?v=P-SPQLJTxJk) — The Bright Side of Mathematics, tiếng Anh. Tập đóng như phần bù của tập mở, rồi tới bao đóng, trong ngôn ngữ của Bright Side.
- [Topology Definitions: Closure, Boundary, Interior](https://www.youtube.com/watch?v=jhAI_irtA3M) — Mu Prime Math, tiếng Anh. Ba từ cạnh nhau: bao đóng, biên, phần trong. Xem để không trộn chúng.

## 🧩 Bài tập

### Tập đóng

1. **Kiểm tra tập đóng:**  
   Trong $\mathbb{R}$ với tô-pô Euclid, các tập sau có đóng không?
   - a) $[0, 1]$
   - b) $\{1/n : n \in \mathbb{N}\}$
   - c) $\mathbb{Q}$
   - d) $\{x \in \mathbb{R} : \sin(x) = 0\}$

2. **Tập vừa đóng vừa mở (Clopen):**  
   Tìm tất cả các tập vừa mở vừa đóng trong:
   - a) $\mathbb{R}$ với tô-pô Euclid
   - b) Không gian có tô-pô rời rạc
   - c) Không gian có tô-pô tầm thường

3. **Giao tùy ý của các tập đóng:**  
   Cho $F_n = [1/n, 1]$ trong $\mathbb{R}$ ($n \in \mathbb{N}$).
   - a) Mỗi $F_n$ có đóng không?
   - b) Tính $\bigcap_{n=1}^{\infty} F_n$.
   - c) Giao này có đóng không?

### Bao đóng

4. **Tính bao đóng:**  
   Trong $\mathbb{R}$, tìm $\text{cl}(A)$:
   - a) $A = (0, 1) \cup \{2\}$
   - b) $A = \{1 + 1/n : n \in \mathbb{N}\}$
   - c) $A = \{x \in \mathbb{Q} : 0 < x < \sqrt{2}\}$
   - d) $A = \mathbb{Z}$

5. **Bao đóng của phép giao:**  
   Chứng minh rằng $\text{cl}(A \cap B) \subseteq \text{cl}(A) \cap \text{cl}(B)$, và nêu ví dụ khi bao hàm là nghiêm ngặt.

6. **Bao đóng trong tô-pô rời rạc:**  
   Trong không gian có tô-pô rời rạc, xác định $\text{cl}(A)$ với $A$ bất kỳ.

### Phần trong

7. **Tính phần trong:**  
   Trong $\mathbb{R}$, tìm $\text{int}(A)$:
   - a) $A = [0, 1]$
   - b) $A = \mathbb{Q}$
   - c) $A = [0, 1] \cup [2, 3]$
   - d) $A = \{1/n : n \in \mathbb{N}\}$

8. **Đối ngẫu phần trong — bao đóng:**  
   Chứng minh $\text{int}(A) = X \setminus \text{cl}(X \setminus A)$.

9. **Đặc trưng tập mở:**  
   Chứng minh $A$ mở $\iff A = \text{int}(A)$.

### Điểm tụ

10. **Tìm tập điểm tụ:**  
    Trong $\mathbb{R}$, tìm tập điểm tụ $A'$ của:
    - a) $A = (0, 1)$
    - b) $A = \{1/n : n \in \mathbb{N}\}$
    - c) $A = \mathbb{Q}$
    - d) $A$ là tập Cantor

11. **Tập chỉ gồm điểm cô lập:**  
    Xét tập $A \subseteq \mathbb{R}$ mà mọi điểm của $A$ đều là điểm cô lập.
    - a) Nêu một ví dụ với $A$ vô hạn.
    - b) $A$ có thể không đếm được không?

12. **Công thức bao đóng:**  
    Chứng minh $\text{cl}(A) = A \cup A'$.

### Biên

13. **Tính biên:**  
    Trong $\mathbb{R}$, tìm $\partial A$:
    - a) $A = [0, 1)$
    - b) $A = \mathbb{Q}$
    - c) $A = \{0\} \cup (1, 2)$
    - d) $A$ là tập Cantor

14. **Tính chất của biên:**  
    Chứng minh:
    - a) $\partial A = \partial(X \setminus A)$
    - b) $\partial A$ là tập đóng
    - c) $\partial(\partial A) \subseteq \partial A$

15. **Phân hoạch không gian:**  
    Chứng minh $X = \text{int}(A) \sqcup \partial A \sqcup \text{int}(X \setminus A)$.

### Tập trù mật

16. **Tính trù mật của $\mathbb{Q}$:**  
    Chứng minh $\mathbb{Q}$ trù mật trong $\mathbb{R}$. (*Gợi ý:* Dùng tính chất Archimedes để chỉ ra mọi khoảng $(a, b)$ đều chứa số hữu tỉ.)

17. **Tính trù mật của số vô tỉ:**  
    Chứng minh $\mathbb{R} \setminus \mathbb{Q}$ cũng trù mật trong $\mathbb{R}$.

18. **Không đâu trù mật:**  
    Chứng minh $\mathbb{N}$ không đâu trù mật trong $\mathbb{R}$.

### Nâng cao

19. **Tập Cantor:**  
    Biết tập Cantor $C \subset [0, 1]$ đóng và không đâu trù mật, chứng minh rằng $\partial C = C$.

20. **Phân tách $\mathbb{R}$:**  
    Ta có $\mathbb{R} = \mathbb{Q} \cup (\mathbb{R} \setminus \mathbb{Q})$ với cả hai tập đều trù mật. Có thể viết $\mathbb{R} = A \cup B$ với cả $A$ và $B$ đều **không** trù mật trong $\mathbb{R}$ không?

21. **Tách hai tập tách biệt trong không gian mê-tric:**  
    Trong một không gian mê-tric $(X, d)$, cho hai tập $A, B \subseteq X$ thỏa mãn $\text{cl}(A) \cap B = \emptyset$ và $A \cap \text{cl}(B) = \emptyset$. Chứng minh tồn tại hai tập mở rời nhau $U, V$ sao cho $A \subseteq U$ và $B \subseteq V$. (*Gợi ý:* Với mỗi $a \in A$, chọn $r_a > 0$ sao cho $B(a, r_a) \cap B = \emptyset$, rồi xét $U = \bigcup_{a \in A} B(a, r_a / 2)$ và tương tự cho $V$.)

### Câu hỏi suy ngẫm

22. **Tính đối ngẫu:**  
    Giải thích vì sao các cặp tập mở $\leftrightarrow$ tập đóng, phần trong $\leftrightarrow$ bao đóng, hợp $\leftrightarrow$ giao tạo thành quan hệ đối ngẫu qua phép lấy phần bù.

23. **Tái tạo tô-pô từ toán tử bao đóng:**  
    Nếu toán tử $\text{cl}: \mathcal{P}(X) \to \mathcal{P}(X)$ thỏa mãn bốn tiên đề Kuratowski (K1)–(K4), hãy mô tả cách khôi phục lại họ các tập mở của tô-pô tương ứng.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §17 (Closed Sets and Limit Points), §18 (Continuous Functions)
- **Morris, Topology Without Tears:** Chapter 3 (Limit Points)
- **Willard, General Topology:** Chapter 2 (Convergence and Closure)
- **Kuratowski, Topology Vol. I:** Chapter I (Closure and Interior)

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã xây dựng hệ thống các khái niệm và toán tử đối ngẫu với tập mở:

✅ **Tập đóng:** Phần bù của tập mở, thỏa mãn các tiên đề đối ngẫu (C1)–(C3).  
✅ **Bao đóng $\text{cl}(\cdot)$:** Tập đóng nhỏ nhất chứa $A$, thỏa mãn bốn tiên đề Kuratowski (K1)–(K4).  
✅ **Điểm tụ và điểm cô lập:** Công thức $\text{cl}(A) = A \cup A'$.  
✅ **Phần trong $\text{int}(\cdot)$:** Tập mở lớn nhất nằm trong $A$, đối ngẫu với bao đóng qua $\text{int}(A) = X \setminus \text{cl}(X \setminus A)$.  
✅ **Biên $\partial A$:** Tập $\text{cl}(A) \setminus \text{int}(A)$, phân hoạch $X = \text{int}(A) \sqcup \partial A \sqcup \text{int}(X \setminus A)$.  
✅ **Tập trù mật và không đâu trù mật:** $\text{cl}(A) = X$ và $\text{int}(\text{cl}(A)) = \emptyset$.

**Tiếp theo:** Trong Bài 01.03, ta sẽ tìm hiểu **Ánh xạ liên tục và Phép đồng phôi** — công cụ so sánh các không gian tô-pô và định nghĩa sự tương đương tô-pô.

---

*"Closure is the smallest closed set; interior is the largest open set. Between them lies the boundary."* — Topology wisdom

🎯 **Hãy rèn luyện việc tính bao đóng, phần trong và biên trên nhiều ví dụ khác nhau.** 🎯

---

**Previous:** [Lecture 01.01: Basis and Subbasis](/contents/vi/topology-chapter01/01_01_Basis_Subbasis/)  
**Next:** [Lecture 01.03: Continuous Functions and Homeomorphisms](/contents/vi/topology-chapter01/01_03_Continuous_Functions_Homeomorphisms/)
