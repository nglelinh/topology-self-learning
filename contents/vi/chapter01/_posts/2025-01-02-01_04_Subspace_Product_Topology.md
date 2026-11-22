---
layout: post
title: "Lecture 01.04: Subspace and Product Topology"
lang: vi
lang-ref: lecture-01-04
chapter: 1
lecture: 4
categories: [chapter01]
tags: [subspace-topology, product-topology, projections, tychonoff]
description: "Subspace topology, product topology, và Tychonoff's theorem (statement)"
---

**Tô-pô con và Tô-pô tích**

---

## 📖 Tổng quan

Một nguyên tắc quen thuộc trong toán học là xây dựng các đối tượng phức tạp từ những đối tượng đơn giản hơn. Trong tô-pô học, hai phép xây dựng cơ bản nhất là:
1. **Tô-pô con (Subspace topology):** Trang bị tô-pô cho một tập con của không gian cho trước.
2. **Tô-pô tích (Product topology):** Trang bị tô-pô cho tích Đề-các của hai hay nhiều không gian.

Về mặt trực quan, đường tròn $S^1$ nằm trong mặt phẳng $\mathbb{R}^2$ nhận tô-pô con tự nhiên từ $\mathbb{R}^2$; trong khi đó mặt phẳng $\mathbb{R}^2 = \mathbb{R} \times \mathbb{R}$, mặt trụ $S^1 \times [0, 1]$ và hình xuyến $T^2 = S^1 \times S^1$ đều là các không gian tích. Trong vật lý và hình học, các mặt nhúng trong $\mathbb{R}^3$, không gian cấu hình của hệ nhiều hạt, hay không gian hàm số (tích vô hạn) đều sử dụng hai cấu trúc này.

Bài giảng này trình bày định nghĩa và tính chất của **tô-pô con**, **tô-pô tích hữu hạn** cùng tính chất phổ dụng của các ánh xạ chiếu, **tô-pô tích vô hạn** (so sánh với tô-pô hộp), và phát biểu **Định lý Tychonoff** — một trong những kết quả quan trọng nhất của tô-pô đại cương.

---

## 🎯 Từ trực giác đến hình thức

### Tô-pô con: Nguyên tắc kế thừa

Khi $A \subseteq X$, ta muốn $A$ kế thừa cấu trúc tô-pô từ không gian bao $X$. Chẳng hạn với $A = [0, 1] \subset \mathbb{R}$, nửa khoảng $[0, 0{,}5)$ không phải là tập mở trong $\mathbb{R}$, nhưng lại có dạng giao của một tập mở trong $\mathbb{R}$ với $A$: $[0, 0{,}5) = (-\infty, 0{,}5) \cap [0, 1]$. Vì vậy, $[0, 0{,}5)$ được xem là "tập mở tương đối" trong $[0, 1]$.

**Nguyên tắc chung:**
> **$U$ mở trong $A \iff U = V \cap A$ với một tập mở $V$ nào đó trong $X$.**

![Subspace topology illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Subspace_topology.svg/400px-Subspace_topology.svg.png)  
*Tô-pô con: $U$ mở trong $A$ khi $U = V \cap A$ - Nguồn minh họa khái niệm*

---

### Tô-pô tích: Hệ tọa độ

Trong $\mathbb{R}^2$, mỗi điểm có hai tọa độ $(x, y)$. Một hình chữ nhật mở $(a, b) \times (c, d)$ chiếu xuống trục hoành thành khoảng mở $(a, b)$ và chiếu xuống trục tung thành khoảng mở $(c, d)$. Nguyên tắc định nghĩa tô-pô tích là chọn **tô-pô thô nhất** trên tích Đề-các sao cho mọi ánh xạ chiếu lên từng thành phần đều liên tục.

![Product topology visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Cartesian-coordinate-system.svg/400px-Cartesian-coordinate-system.svg.png)  
*Không gian tích với các phép chiếu tọa độ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cartesian-coordinate-system.svg)*

---

## 📐 Định nghĩa hình thức

### 1. Tô-pô con (Subspace Topology)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tô-pô con):**  
Cho $(X, \tau)$ là một không gian tô-pô và $A \subseteq X$. **Tô-pô con** (*subspace topology* hay *tô-pô cảm sinh*) trên $A$ là:

$$
\tau_A = \{U \cap A : U \in \tau\}
$$
</div>

Cặp $(A, \tau_A)$ gọi là một **không gian con** (*subspace*) của $X$.

**Ví dụ 1: Đoạn đóng trong $\mathbb{R}$**  
Với $A = [0, 2] \subset \mathbb{R}$ (tô-pô Euclid), các tập sau đều mở trong $A$: $[0, 1) = (-1, 1) \cap [0, 2]$, $(1, 2] = (1, 3) \cap [0, 2]$, $(0{,}5, 1{,}5) = (0{,}5, 1{,}5) \cap [0, 2]$, $[0, 2] = \mathbb{R} \cap [0, 2]$ và $\emptyset$. Lưu ý rằng $[0, 1)$ mở trong $[0, 2]$ nhưng không mở trong $\mathbb{R}$.

**Ví dụ 2: Đường tròn trong $\mathbb{R}^2$**  
Với $S^1 = \{(x, y) : x^2 + y^2 = 1\} \subset \mathbb{R}^2$, mỗi "cung mở" trên $S^1$ là giao của một đĩa mở trong $\mathbb{R}^2$ với $S^1$.

<div class="textbook-theorem" markdown="1">
**Định lý:**  
$\tau_A$ thỏa mãn cả ba tiên đề tô-pô trên $A$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**
</div>

- **(T1):** $\emptyset = \emptyset \cap A \in \tau_A$ và $A = X \cap A \in \tau_A$.
- **(T2):** Với mọi họ $\{U_\alpha \cap A\}$ ($U_\alpha \in \tau$), ta có $\bigcup (U_\alpha \cap A) = \left(\bigcup U_\alpha\right) \cap A \in \tau_A$.
- **(T3):** $(U_1 \cap A) \cap (U_2 \cap A) = (U_1 \cap U_2) \cap A \in \tau_A$.

<div class="textbook-theorem" markdown="1">
**Định lý (Tính liên tục của ánh xạ bao hàm):**  
Ánh xạ bao hàm $i: A \to X$, $i(a) = a$ luôn liên tục đối với tô-pô con $\tau_A$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Với mọi $U \in \tau$, ta có $i^{-1}(U) = U \cap A \in \tau_A$ theo đúng định nghĩa tô-pô con.
</div>

---

### 2. Cơ sở của tô-pô con

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Nếu $\mathcal{B}$ là một cơ sở cho $\tau$ trên $X$, thì:

$$
\mathcal{B}_A = \{B \cap A : B \in \mathcal{B}\}
$$
</div>
là một cơ sở cho tô-pô con $\tau_A$ trên $A$. Ví dụ, từ cơ sở $\{(a, b)\}$ của $\mathbb{R}$, ta thu được cơ sở $\{(a, b) \cap [0, 1]\}$ của $[0, 1]$.

---

### 3. Tính chất của không gian con

<div class="textbook-theorem" markdown="1">
**Định lý (Bao đóng tương đối):**  
Cho $A \subseteq X$ và $B \subseteq A$. Bao đóng của $B$ trong không gian con $A$ thỏa mãn:

$$
\text{cl}_A(B) = \text{cl}_X(B) \cap A
$$
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Dành làm bài tập (sử dụng định nghĩa tập đóng tương đối và bao đóng).
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Tính bắc cầu của không gian con):**  
Nếu $A \subseteq B \subseteq X$, thì tô-pô con trên $A$ cảm sinh từ $(B, \tau_B)$ trùng với tô-pô con trên $A$ cảm sinh trực tiếp từ $(X, \tau_X)$.
</div>

---

### 4. Tô-pô tích hữu hạn (Finite Product Topology)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tô-pô tích của hai không gian):**  
Cho $(X, \tau_X)$ và $(Y, \tau_Y)$. Trên $X \times Y$, **tô-pô tích** (*product topology*) là tô-pô sinh bởi cơ sở:

$$
\mathcal{B} = \{U \times V : U \in \tau_X, V \in \tau_Y\}
$$
</div>

Mỗi phần tử cơ sở có dạng "hình chữ nhật mở" $U \times V$.

**Ví dụ 1 ($\mathbb{R} \times \mathbb{R} = \mathbb{R}^2$):** Cơ sở gồm các hình chữ nhật mở $(a, b) \times (c, d)$, sinh ra đúng tô-pô Euclid trên $\mathbb{R}^2$.

**Ví dụ 2 ($S^1 \times [0, 1]$ — Mặt trụ):** Cơ sở gồm các tích của một cung mở trên $S^1$ với một khoảng mở tương đối trong $[0, 1]$.

![Cylinder as product](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Cylinder_geometry.svg/300px-Cylinder_geometry.svg.png)  
*Mặt trụ $S^1 \times [0, 1]$ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cylinder_geometry.svg)*

**Ví dụ 3 ($S^1 \times S^1$ — Hình xuyến):** Cơ sở gồm các tích của hai cung mở trên $S^1$.

![Torus as product](https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Torus.png/300px-Torus.png)  
*Hình xuyến $T^2 = S^1 \times S^1$ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus.png)*

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Họ $\mathcal{B} = \{U \times V : U \in \tau_X, V \in \tau_Y\}$ là một cơ sở cho một tô-pô trên $X \times Y$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Kiểm tra tiêu chuẩn cơ sở:
- (B1): $X \times Y \in \mathcal{B}$ phủ toàn bộ $X \times Y$.
- (B2): $(U_1 \times V_1) \cap (U_2 \times V_2) = (U_1 \cap U_2) \times (V_1 \cap V_2) \in \mathcal{B}$.
</div>

---

### 5. Các ánh xạ chiếu và tính chất phổ dụng

<div class="textbook-definition" markdown="1">
**Định nghĩa (Ánh xạ chiếu — Projection Maps):**

$$
\pi_X: X \times Y \to X, \quad \pi_X(x,y) = x
$$
$$
\pi_Y: X \times Y \to Y, \quad \pi_Y(x,y) = y
$$
</div>

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Các ánh xạ chiếu $\pi_X$ và $\pi_Y$ luôn liên tục đối với tô-pô tích.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Với mọi $U \in \tau_X$, ta có $\pi_X^{-1}(U) = U \times Y \in \mathcal{B} \subseteq \tau_{X \times Y}$. Tương tự cho $\pi_Y$.
</div>

**Tính chất phổ dụng:** Tô-pô tích là **tô-pô thô nhất** trên $X \times Y$ làm cho cả $\pi_X$ và $\pi_Y$ liên tục.

<div class="textbook-theorem" markdown="1">
**Định lý (Tiêu chuẩn liên tục vào không gian tích):**  
Ánh xạ $f: Z \to X \times Y$ liên tục khi và chỉ khi hai ánh xạ tọa độ $\pi_X \circ f$ và $\pi_Y \circ f$ đều liên tục.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh ($\Leftarrow$):**  
Chỉ cần kiểm tra trên các phần tử cơ sở $U \times V$. Ta có:
$f^{-1}(U \times V) = f^{-1}(\pi_X^{-1}(U) \cap \pi_Y^{-1}(V)) = (\pi_X \circ f)^{-1}(U) \cap (\pi_Y \circ f)^{-1}(V) \in \tau_Z$.
</div>

Nhờ định lý này, để kiểm tra tính liên tục của một ánh xạ vào không gian tích, ta chỉ cần kiểm tra tính liên tục của từng hàm tọa độ.

---

### 6. Tích hữu hạn nhiều không gian

<div class="textbook-theorem" markdown="1">
**Định lý (Tính kết hợp):**  
$(X \times Y) \times Z \cong X \times (Y \times Z) \cong X \times Y \times Z$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tích $n$ không gian):**  
$$
X_1 \times X_2 \times \cdots \times X_n
$$
</div>
có cơ sở gồm các tập dạng $B_1 \times B_2 \times \cdots \times B_n$, trong đó $B_i$ là phần tử cơ sở (hoặc tập mở) trong $X_i$. Với $X_i = \mathbb{R}$, ta thu được $\mathbb{R}^n$ cùng cơ sở là các hình hộp mở $(a_1, b_1) \times \cdots \times (a_n, b_n)$.

---

### 7. Tích vô hạn (Infinite Products)

Khi tập chỉ số $I$ là **vô hạn**, có hai cách tự nhiên để định nghĩa tô-pô trên $\prod_{i \in I} X_i$:

- **Tô-pô hộp (Box Topology):** Lấy cơ sở gồm tất cả các tích $\prod_{i \in I} U_i$ với $U_i$ mở trong $X_i$. Trong tô-pô hộp, các ánh xạ chiếu $\pi_i$ vẫn liên tục, nhưng tô-pô này quá mịn nên làm hỏng nhiều định lý quan trọng: tính chất phổ dụng bị mất (một ánh xạ có mọi tọa độ liên tục vẫn có thể không liên tục, ví dụ $t \mapsto (t, t, t, \dots)$ từ $\mathbb{R}$ vào $\mathbb{R}^{\mathbb{N}}$) và Định lý Tychonoff không còn đúng.
- **Tô-pô tích (Product Topology):** Chỉ cho phép khác toàn không gian $X_i$ ở **hữu hạn** tọa độ.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tô-pô tích vô hạn):**

$$
\mathcal{B} = \left\{\prod_{i \in I} U_i : U_i \in \tau_i, U_i = X_i \text{ for all but finitely many } i\right\}
$$
</div>

Ví dụ, trong $\mathbb{R}^{\mathbb{N}} = \mathbb{R} \times \mathbb{R} \times \cdots$, một phần tử cơ sở có dạng $(a_1, b_1) \times \cdots \times (a_n, b_n) \times \mathbb{R} \times \mathbb{R} \times \cdots$ (hoặc giới hạn trên hữu hạn chỉ số bất kỳ).

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Tô-pô tích là tô-pô thô nhất trên $\prod_{i \in I} X_i$ sao cho mọi ánh xạ chiếu $\pi_j: \prod_{i \in I} X_i \to X_j$ đều liên tục; đồng thời một ánh xạ $f: Z \to \prod_{i \in I} X_i$ liên tục khi và chỉ khi mọi tọa độ $\pi_j \circ f$ đều liên tục.
</div>

---

### 8. Định lý Tychonoff

**Định lý Tychonoff:**

> **Tích tùy ý của các không gian compact là một không gian compact** (đối với tô-pô tích).

$$
\forall i \in I: X_i \text{ compact} \implies \prod_{i \in I} X_i \text{ compact}
$$

Định lý này khẳng định tính compact được bảo toàn qua tích Đề-các (kể cả tích không đếm được). Chứng minh của nó sử dụng Tiên đề Lựa chọn (thông qua bổ đề siêu lọc hoặc định lý tiền cơ sở Alexander), và trong ZF định lý Tychonoff tương đương với Tiên đề Lựa chọn.

Chẳng hạn, vì $[0, 1]$ compact nên khối lập phương Hilbert $[0, 1]^{\mathbb{N}}$ cũng compact trong tô-pô tích. Định lý Tychonoff là công cụ nền tảng cho nhiều kết quả lớn như định lý Banach–Alaoglu trong giải tích hàm. Ngược lại, trong **tô-pô hộp**, $[0, 1]^{\mathbb{N}}$ không còn compact.

<div class="textbook-proof" markdown="1">
**Ghi chú về chứng minh:**  
Chứng minh đầy đủ sử dụng bổ đề siêu lọc (*ultrafilter lemma*) hoặc định lý tiền cơ sở Alexander (sẽ gặp ở mức độ nâng cao).
</div>

---

### 9. Một số ví dụ quan trọng

**Ví dụ 1: Khối lập phương Hilbert (Hilbert Cube)**
$$
H = [0,1]^\mathbb{N} = \prod_{n=1}^\infty [0,1]
$$
$H$ là không gian compact (theo định lý Tychonoff), mê-tric hóa được, và có tính phổ dụng: mọi không gian mê-tric khả ly đều nhúng được vào $H$.

**Ví dụ 2: Không gian Cantor**
$$
\mathcal{C} = \{0,1\}^\mathbb{N}
$$
(với $\{0, 1\}$ mang tô-pô rời rạc). $\mathcal{C}$ hoàn toàn không liên thông, không có điểm cô lập (tập hoàn hảo) và đồng phôi với tập Cantor chuẩn trong $[0, 1]$.

**Ví dụ 3: Không gian hàm số**
$$
\mathbb{R}^X = \{f: X \to \mathbb{R}\}
$$
Tô-pô tích trên $\mathbb{R}^X$ chính là **tô-pô hội tụ từng điểm** (*pointwise convergence*): $f_n \to f$ trong $\mathbb{R}^X \iff f_n(x) \to f(x)$ với mọi $x \in X$.

**Phản ví dụ: $[0, 1]^{\mathbb{N}}$ với tô-pô hộp**  
Trong tô-pô hộp, mọi ánh xạ chiếu vẫn liên tục nhưng không gian không còn compact (định lý Tychonoff sai).

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Andrey Tychonoff** - *"Über die topologische Erweiterung von Räumen"* (1930)  
   *Chứng minh định lý Tychonoff.*

2. **Marshall Stone** - *"Applications of Boolean Rings to Topology"* (1937)  
   *Compact hóa Stone–Čech, ứng dụng định lý Tychonoff.*

3. **John Kelley** - *"The Tychonoff Product Theorem Implies the Axiom of Choice"* (1950)  
   *Chứng minh định lý Tychonoff tương đương với Tiên đề Lựa chọn.*

### Giáo trình

4. **James R. Munkres** - *Topology*, 2nd Ed., **§16–19, §37**  
   *Tài liệu tham khảo chuẩn.*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 7–8**  
   *Trình bày dễ tiếp cận.*

6. **Stephen Willard** - *General Topology*, **Chapter 8**  
   *Trình bày đầy đủ.*

7. **John L. Kelley** - *General Topology*, **Chapter 5**  
   *Trình bày nâng cao theo hướng bộ lọc.*

---

## 🔗 Ứng dụng và liên hệ

### Vật lý — Không gian cấu hình
Trong cơ học cổ điển, không gian cấu hình của $n$ hạt chuyển động trong $\mathbb{R}^3$ là không gian tích $(\mathbb{R}^3)^n$, quyết định cấu trúc các quỹ đạo có thể có của hệ.

### Giải tích hàm — Tô-pô yếu*
Tô-pô yếu* (*weak-* topology*) trên không gian đối ngẫu của không gian Banach là tô-pô con của một tô-pô tích cảm sinh bởi các phiếm hàm đánh giá; định lý Tychonoff dẫn trực tiếp đến định lý Banach–Alaoglu.

### Xác suất — Không gian tích vô hạn
Không gian mẫu của dãy vô hạn lần tung đồng xu $\{H, T\}^{\mathbb{N}}$ mang tô-pô tích (đồng phôi không gian Cantor), là bối cảnh cho độ đo tích và định lý mở rộng Kolmogorov.

### Khoa học máy tính — Lý thuyết kiểu
Kiểu tích $A \times B$ trong các ngôn ngữ lập trình đi kèm hai phép chiếu `fst`, `snd` thỏa mãn tính chất phổ dụng tương tự tích trong phạm trù các không gian tô-pô.

---

## Video tham khảo

- **xem trước** [[Tôpô đại cương] Bài 7.  Không gian tôpô con (phần 1)](https://www.youtube.com/watch?v=WhuwOeKqXaY) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Tô-pô con: tập mở tương đối, đúng nửa đầu của bài.
- [Tô-pô tích](https://www.youtube.com/watch?v=uSQ7J4tpAWI) — Cuong Nguyen, tiếng Việt. Tô-pô tích, nửa sau của bài, bằng tiếng Việt.
- [Topology Lecture 12: Product Spaces](https://www.youtube.com/watch?v=iwUzTAhwdh8) — Marius Furter, tiếng Anh. Không gian tích nói chậm bằng tiếng Anh, để đối chiếu với bài giảng tiếng Việt.

## 🧩 Bài tập

### Tô-pô con

1. **Kiểm tra tập mở trong không gian con:**  
   Cho $X = \mathbb{R}$ và $A = [0, 1]$ với tô-pô con. Các tập sau có phải là tập mở trong $A$ không?
   - a) $(0, 0{,}5)$
   - b) $[0, 0{,}5)$
   - c) $\{0{,}25\}$

2. **Tập mở tương đối:**  
   Trong $\mathbb{R}$, xét $A = [0, 2]$.
   - a) $[0, 1)$ có mở trong $A$ không?
   - b) $(0, 1)$ có mở trong $A$ không?
   - c) $[0, 1)$ có mở trong $\mathbb{R}$ không?

3. **Không gian con đường tròn:**  
   Với $S^1 \subset \mathbb{R}^2$ (tô-pô con), mô tả hình dạng một "cung mở" $U \subset S^1$ và vẽ hình minh họa.

### Tô-pô tích

4. **Phần tử cơ sở:**  
   Trong $\mathbb{R} \times \mathbb{R} = \mathbb{R}^2$ với cơ sở hình chữ nhật mở, các tập sau có phải phần tử cơ sở không?
   - a) $(0, 1) \times (0, 1)$
   - b) Đĩa mở $B((0, 0), 1)$
   - c) $\{(x, y) : x^2 + y^2 < 1\}$

5. **Tập mở trong không gian tích:**  
   Chứng minh đĩa mở trong $\mathbb{R}^2$ là tập mở trong tô-pô tích. (*Gợi ý:* Biểu diễn nó như hợp của các hình chữ nhật mở.)

6. **Kiểm tra liên tục bằng tọa độ:**  
   Chứng minh $f: \mathbb{R} \to \mathbb{R}^2$, $f(t) = (\cos t, \sin t)$ là ánh xạ liên tục bằng cách kiểm tra hai hàm tọa độ.

### Ánh xạ chiếu

7. **Tính chất của phép chiếu:**  
   Xét $\pi_1: \mathbb{R}^2 \to \mathbb{R}$, $\pi_1(x, y) = x$.
   - a) Chứng minh $\pi_1$ liên tục.
   - b) $\pi_1$ có phải là ánh xạ mở (ảnh của mọi tập mở là tập mở) không?
   - c) $\pi_1$ có phải là ánh xạ đóng (ảnh của mọi tập đóng là tập đóng) không?

8. **Tính chất phổ dụng:**  
   Áp dụng tiêu chuẩn liên tục vào không gian tích để kiểm tra tính liên tục của $g: \mathbb{R} \to \mathbb{R}^2$, $g(t) = (t^2, t^3)$.

### Tích vô hạn

9. **Khối lập phương Hilbert:**  
   Xét $H = [0, 1]^{\mathbb{N}}$ với tô-pô tích.
   - a) Mô tả một phần tử cơ sở của $H$.
   - b) $H$ có compact không?
   - c) $H$ có cơ sở đếm được không?

10. **Không gian Cantor:**  
    Xét $\mathcal{C} = \{0, 1\}^{\mathbb{N}}$ với tô-pô tích.
    - a) Tính lực lượng $|\mathcal{C}|$.
    - b) $\mathcal{C}$ có compact không?
    - c) $\mathcal{C}$ có liên thông không?

11. **Tô-pô hộp và tô-pô tích:**  
    So sánh $\mathbb{R}^{\mathbb{N}}$ với tô-pô hộp và tô-pô tích:
    - a) Mô tả một phần tử cơ sở trong tô-pô hộp.
    - b) Mô tả một phần tử cơ sở trong tô-pô tích.
    - c) Tô-pô nào mịn hơn?

### Nâng cao

12. **Mặt trụ và dải Möbius:**  
    Mặt trụ là không gian tích $S^1 \times [0, 1]$, còn dải Möbius không đồng phôi với $S^1 \times [0, 1]$ (được xây bằng phép dán/thương). Hãy giải thích sự khác biệt về mặt tô-pô giữa hai mặt này.

13. **Hình xuyến:**  
    Xét $T^2 = S^1 \times S^1$.
    - a) Vẽ hình minh họa.
    - b) $T^2$ có đồng phôi với mặt cầu $S^2$ không?
    - c) Tìm hiểu đặc trưng Euler của $T^2$ và $S^2$.

14. **Không gian hàm số:**  
    Trên $\mathbb{R}^{\mathbb{R}}$ với tô-pô tích, sự hội tụ $f_n \to f$ có ý nghĩa gì (hội tụ từng điểm)? So sánh với hội tụ đều.

15. **Áp dụng định lý Tychonoff:**  
    Chứng minh $[0, 1]^{[0, 1]}$ (tập tất cả các hàm $[0, 1] \to [0, 1]$ với tô-pô hội tụ từng điểm) là không gian compact.

### Câu hỏi suy ngẫm

16. **Vì sao dùng tô-pô tích thay vì tô-pô hộp?**  
    Liệt kê các lý do khiến tô-pô tích là lựa chọn tiêu chuẩn cho tích vô hạn (tính chất phổ dụng, định lý Tychonoff, tính liên thông).

17. **Không gian con và không gian tích:**  
    Nếu không gian con là phép "thu hẹp" và không gian tích là phép "nhân", hãy tìm hiểu phép xây dựng đối ngẫu với chúng là không gian thương (*quotient space*).

18. **Góc nhìn lý thuyết phạm trù:**  
    Tìm hiểu cách tính chất phổ dụng định nghĩa tích trong lý thuyết phạm trù và đối chiếu với tô-pô tích.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §16 (Subspace), §19 (Product), §37 (Tychonoff)
- **Morris, Topology Without Tears:** Chapters 7–8
- **Willard, General Topology:** Chapters 8–9
- **Bourbaki, General Topology:** Chapter I (Products)

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã học hai phép xây dựng không gian tô-pô cơ bản:

✅ **Tô-pô con:** $\tau_A = \{U \cap A : U \in \tau\}$, bảo đảm ánh xạ bao hàm $i: A \hookrightarrow X$ liên tục.  
✅ **Tô-pô tích hữu hạn:** Sinh bởi cơ sở các hình chữ nhật mở $\{U \times V\}$.  
✅ **Ánh xạ chiếu và tính chất phổ dụng:** Tô-pô tích là tô-pô thô nhất làm mọi phép chiếu liên tục; ánh xạ vào không gian tích liên tục khi và chỉ khi mọi hàm tọa độ liên tục.  
✅ **Tô-pô tích vô hạn:** Phần tử cơ sở chỉ giới hạn trên hữu hạn tọa độ (khác với tô-pô hộp).  
✅ **Định lý Tychonoff:** Tích tùy ý các không gian compact là compact trong tô-pô tích.

**Kết thúc Chương 01:** Chương 02 sẽ nghiên cứu hai tính chất tô-pô quan trọng bậc nhất là **Tính liên thông và Tính compact**.

---

*"The product topology is the topology of coordinatewise convergence."* — Standard wisdom

🎯 **Hãy vẽ minh họa mặt trụ, hình xuyến và các hình chữ nhật mở để củng cố trực giác về không gian tích.** 🎯

---

**Previous:** [Lecture 01.03: Continuous Functions](/contents/vi/topology-chapter01/01_03_Continuous_Functions_Homeomorphisms/)  
**Next Chapter:** [Chapter 02: Connectedness and Compactness](/contents/vi/topology-chapter02/)
