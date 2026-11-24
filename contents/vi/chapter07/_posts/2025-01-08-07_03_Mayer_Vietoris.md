---
layout: post
title: "Lecture 07.03: Mayer-Vietoris Sequence"
lang: vi
lang-ref: lecture-07-03
chapter: 7
lecture: 3
categories: [chapter07]
tags: [mayer-vietoris, exact-sequence, homology-computations]
description: "Mayer-Vietoris Sequence: powerful computational tool via decomposition, long exact sequences, connecting homomorphisms"
---

**Phương pháp chia để trị cho đồng điều**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu Định lý Seifert–van Kampen (bài 06.04) là chiếc rìu "chia để trị" cho nhóm cơ bản $$\pi_1$$, thì **Dãy khớp dài Mayer–Vietoris** chính là phiên bản **mạnh mẽ hơn, tổng quát hơn và dễ dùng hơn rất nhiều** dành cho nhóm đồng điều $$H_n$$! Không chỉ hoạt động ở mọi bậc $$n = 0, 1, 2, \dots$$, Mayer–Vietoris thậm chí **không đòi hỏi phần giao $$U \cap V$$ phải liên thông đường** — cho phép bạn tính trọn vẹn đồng điều của mọi mặt cầu $$S^n$$, hình xuyến $$T^2$$, chai Klein và tổng liên thông các mặt chỉ bằng những phép đuổi biểu đồ đại số gọn gàng!

Trước đây, ta đã có định lý Seifert–van Kampen để tính nhóm cơ bản $\pi_1(X)$ từ phép phân rã $X = A \cup B$, và đồng điều tế bào để tính đồng điều cho các phức CW. Để tính đồng điều của những không gian tổng quát mà không cần cấu trúc phức CW, ta sử dụng **dãy Mayer–Vietoris** — công cụ đóng vai trò tương tự định lý van Kampen trong lý thuyết đồng điều.

Khi phân rã không gian thành hợp của hai tập mở $X = A \cup B$, dãy khớp dài Mayer–Vietoris liên hệ trực tiếp các nhóm đồng điều của phần giao $H_n(A \cap B)$, tổng trực tiếp của hai mảnh $H_n(A) \oplus H_n(B)$, và toàn bộ không gian $H_n(X)$:

- **Tính tổng quát:** Áp dụng được cho mọi không gian tô-pô và mọi phép phủ mở $X = A \cup B$ (tổng quát hơn là khi phần trong của $A$ và $B$ phủ $X$).
- **Giảm độ phức tạp:** Quy việc tính đồng điều của không gian phức tạp $X$ về các mảnh đơn giản hơn.
- **Tính hệ thống và quy nạp:** Thông qua đồng cấu nối $\partial$, ta có thể tính $H_n$ quy nạp theo $H_{n-1}$.

![Mayer-Vietoris decomposition](https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Mayer-Vietoris.svg/500px-Mayer-Vietoris.svg.png)  
*Phân rã không gian cho dãy Mayer–Vietoris - Nguồn concept*

Trong bài học này, ta sẽ ôn lại khái niệm dãy khớp, phát biểu định lý Mayer–Vietoris, tìm hiểu ý nghĩa hình học của đồng cấu nối $\partial$, áp dụng vào các ví dụ kinh điển ($S^2$, $S^n$, $T^2$, $\mathbb{R}P^2$) và phác thảo chứng minh qua Bổ đề con rắn (Snake Lemma). Dãy Mayer–Vietoris bổ sung cho đồng điều tế bào, giúp chứng minh nhiều định lý tổng quát và là bước đệm sang dãy phổ (spectral sequences).

---

## 🗺️ Bản đồ kiến thức nền: Dãy khớp & Định lý Mayer–Vietoris là gì?

### 1. Dãy khớp (Exact Sequence): Ngôn ngữ "ống dẫn" của Đại số Đồng điều
- **Bản chất:** Một dãy các nhóm Abel và đồng cấu $$\cdots \to A \xrightarrow{f} B \xrightarrow{g} C \to \cdots$$ gọi là **khớp tại $$B$$** nếu $$\operatorname{im}(f) = \ker(g)$$.
- **Hai trường hợp vàng gặp mọi lúc:**
  - $$0 \to A \xrightarrow{f} B \to 0$$ khớp $$\iff f$$ là **đẳng cấu**!
  - $$0 \to A \xrightarrow{f} B \xrightarrow{g} C \to 0$$ khớp (dãy khớp ngắn) $$\iff f$$ đơn ánh, $$g$$ toàn ánh và $$C \cong B/f(A)$$!

### 2. Dãy khớp dài Mayer–Vietoris (Phiên bản Đồng điều của Nguyên lý Bù–Trừ)
- **Bản chất:** Khi $$X = \operatorname{int}(A) \cup \operatorname{int}(B)$$, ta muốn đếm số lỗ của $$A \cup B$$ bằng cách cộng lỗ của $$A$$ với lỗ của $$B$$ rồi trừ phần bị đếm lặp trong $$A \cap B$$ — cộng thêm hiệu ứng tinh tế: **hai đường mở hở trong $$A$$ và $$B$$ nối chung biên trong $$A \cap B$$ có thể khép lại thành một lỗ MỚI ở bậc cao hơn** (chính là ánh xạ biên nối $$\partial_*: H_n(X) \to H_{n-1}(A \cap B)$$!):
  $$
  \cdots \to H_n(A \cap B) \xrightarrow{\Phi} H_n(A) \oplus H_n(B) \xrightarrow{\Psi} H_n(X) \xrightarrow{\partial_*} H_{n-1}(A \cap B) \to \cdots
  $$

### 3. Quy nạp theo Số chiều & Tính Cộng của Đặc trưng Euler
- **Bản chất:** Mayer–Vietoris cho ngay quy nạp $$\tilde{H}_k(S^n) \cong \tilde{H}_{k-1}(S^{n-1})$$ trong 3 dòng, đồng thời suy ra công thức bù–trừ huyền thoại cho đặc trưng Euler:
  $$
  \chi(A \cup B) = \chi(A) + \chi(B) - \chi(A \cap B)!
  $$

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc: Quy nạp tính $$\tilde{H}_k(S^n)$$ trong 4 dòng bằng Mayer–Vietoris

Hãy phủ mặt cầu $$S^n$$ ($$n \ge 1$$) bởi hai chỏm cầu mở lớn:
- $$U = S^n \setminus \{N\} \cong \mathbb{R}^n$$ (co rút được $$\implies \tilde{H}_k(U) = 0$$ với **mọi** $$k$$!).
- $$V = S^n \setminus \{S\} \cong \mathbb{R}^n$$ (co rút được $$\implies \tilde{H}_k(V) = 0$$ với **mọi** $$k$$!).
- Phần giao $$U \cap V = S^n \setminus \{N, S\} \cong S^{n-1} \times (-1, 1) \simeq S^{n-1}$$!

Bây giờ viết một đoạn bất kỳ của **dãy khớp dài Mayer–Vietoris rút gọn** cho $$(U, V)$$:
$$
\underbrace{\tilde{H}_k(U) \oplus \tilde{H}_k(V)}_{=\,0}
\longrightarrow
\tilde{H}_k(S^n)
\xrightarrow{\;\partial_*\;}
\tilde{H}_{k-1}(S^{n-1})
\longrightarrow
\underbrace{\tilde{H}_{k-1}(U) \oplus \tilde{H}_{k-1}(V)}_{=\,0}.
$$
Vì cả hai đầu trái và phải đều bằng $$0$$, tính khớp ép ánh xạ nối $$\partial_*$$ ở giữa phải là **đẳng cấu** với mọi $$k$$ và mọi $$n \ge 1$$:
$$
\tilde{H}_k(S^n) \cong \tilde{H}_{k-1}(S^{n-1}) \cong \tilde{H}_{k-2}(S^{n-2}) \cong \cdots \cong \tilde{H}_{k-n}(S^0)!
$$
Mà $$S^0 = \{-1, +1\}$$ gồm đúng **2 điểm rời nhau** nên $$\tilde{H}_0(S^0) \cong \mathbb{Z}$$ và $$\tilde{H}_m(S^0) = 0$$ với mọi $$m \neq 0$$! Thay vào ta thu ngay công thức tổng quát cho **MỌI** mặt cầu $$S^n$$:
$$
\tilde{H}_k(S^n) \cong \begin{cases} \mathbb{Z} & \text{nếu } k = n, \\ 0 & \text{nếu } k \neq n! \end{cases}
$$
*(Hãy chiêm ngưỡng vẻ đẹp của bước $$n=1$$: với $$S^1$$, $$U \cap V \simeq S^0$$ KHÔNG liên thông đường nên Seifert–van Kampen bó tay, nhưng Mayer–Vietoris rút gọn lại dùng chính $$\tilde{H}_0(S^0) \cong \mathbb{Z}$$ để đẩy lên $$H_1(S^1) \cong \mathbb{Z}$$ gọn gàng trong đúng 1 dòng!)*

### Khung giải thích: Quy trình 4 bước "đuổi biểu đồ" với Mayer–Vietoris (nên đọc chậm)

#### Bước 1: Chọn hai mảnh $$A, B$$ có phần trong phủ kín $$X$$ và dễ tính đồng điều nhất
Lý tưởng nhất là chọn $$A, B$$ co rút được (như hai bán cầu mở của $$S^n$$) hoặc co rút về vòng tròn/hình số 8 (như cắt hình xuyến $$T^2$$ thành hai hình trụ mở $$A, B \simeq S^1$$ giao nhau trên hai vòng tròn rời $$A \cap B \simeq S^1 \sqcup S^1$$!).

#### Bước 2: Dùng phiên bản rút gọn $$\tilde{H}_*$$ khi $$A \cap B \neq \emptyset$$
Phiên bản rút gọn triệt tiêu ngay nhiều số hạng $$\mathbb{Z}$$ thừa ở bậc $$0$$, giúp đoạn dãy khớp trở nên ngắn và trong suốt hơn hẳn.

#### Bước 3: Đọc cấu trúc dãy khớp từ những chỗ có số $$0$$
Bất cứ đoạn nào có dạng $$0 \to G \to H \to 0$$ cho ngay đẳng cấu $$G \cong H$$. Nếu có đoạn $$0 \to \mathbb{Z} \xrightarrow{\times 2} \mathbb{Z} \to H_1(\mathbb{R}P^2) \to 0$$ (khi dán đĩa $$D^2$$ vào dải Möbius!), ta đọc ra ngay phần xoắn $$H_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$$!

#### Bước 4: Hiểu ý nghĩa hình học của ánh xạ nối $$\partial_*$$
Ánh xạ nối $$\partial_*: H_n(X) \to H_{n-1}(A \cap B)$$ làm đúng một việc tự nhiên: lấy một chu trình $$z$$ nằm trong $$X$$, xẻ đôi thành $$z = x + y$$ (với $$x \in C_n(A),\; y \in C_n(B)$$), rồi lấy biên $$\partial x$$ — biên đó bắt buộc nằm gọn trong $$A \cap B$$!

$$
X = \operatorname{int}(A) \cup \operatorname{int}(B)
\;\xrightarrow{\;\text{Mayer–Vietoris}\;}\;
\cdots \to H_n(A\cap B) \to H_n(A)\oplus H_n(B) \to H_n(X) \xrightarrow{\partial_*} H_{n-1}(A\cap B) \to \cdots
$$

---

## 🔗 Ôn tập về Dãy khớp

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa (Dãy khớp):**  
Một dãy các nhóm Abel và các đồng cấu:

$$
\cdots \to A_{n+1} \xrightarrow{f_{n+1}} A_n \xrightarrow{f_n} A_{n-1} \to \cdots
$$

được gọi là **dãy khớp** (exact sequence) nếu tại mọi vị trí $n$, ảnh của ánh xạ trước trùng với hạt nhân của ánh xạ sau:

$$
\text{im}(f_{n+1}) = \ker(f_n) \quad \forall n
$$
</div>

**Dãy khớp ngắn (short exact sequence)** có dạng:

$$
0 \to A \xrightarrow{f} B \xrightarrow{g} C \to 0
$$

Tính khớp tương đương với ba điều kiện: $f$ là đơn ánh ($\ker f = 0$), $g$ là toàn ánh ($\text{im}\,g = C$), và $\text{im}\,f = \ker g$. Về mặt đại số, $B$ là một mở rộng kết hợp $A$ (nhúng vào $B$) và $C$ (nhóm thương $B/f(A)$).

**Dãy khớp tách (split exact sequence):** Nếu tồn tại đồng cấu lát cắt (section) $s: C \to B$ sao cho $g \circ s = \text{id}_C$, thì dãy khớp tách và ta có $B \cong A \oplus C$.

---

### 2. Dãy khớp dài trong đồng điều

Cho một dãy khớp ngắn các phức xích $0 \to A_\bullet \to B_\bullet \to C_\bullet \to 0$. Khi đó nó cảm sinh một **dãy khớp dài trong đồng điều**:

$$
\cdots \to H_n(A) \to H_n(B) \to H_n(C) \xrightarrow{\partial} H_{n-1}(A) \to \cdots
$$

trong đó $\partial$ là **đồng cấu nối** (connecting homomorphism) hạ số chiều đi một bậc.

---

## 🎯 Định lý Mayer–Vietoris

### 1. Phát biểu

<div class="textbook-theorem" markdown="1">
**Định lý (Mayer–Vietoris):**  
Cho $X$ là một không gian tô-pô, $A$ và $B$ là hai tập con mở của $X$ sao cho $X = A \cup B$. Khi đó tồn tại dãy khớp dài:

$$
\cdots \to H_n(A \cap B) \xrightarrow{\phi_n} H_n(A) \oplus H_n(B) \xrightarrow{\psi_n} H_n(X) \xrightarrow{\partial_n} H_{n-1}(A \cap B) \to \cdots
$$
</div>

Các ánh xạ trong dãy được xác định như sau:
- **$\phi_n([c]) = ([c], -[c])$:** Nhúng lớp đồng điều từ $A \cap B$ vào tổng trực tiếp $H_n(A) \oplus H_n(B)$ với dấu ngược nhau để bảo đảm $\psi_n \circ \phi_n = 0$.
- **$\psi_n([a], [b]) = [a] + [b]$:** Cộng hai lớp đồng điều từ $A$ và $B$ trong $X$.
- **$\partial_n$:** Đồng cấu nối liên hệ $H_n(X)$ với $H_{n-1}(A \cap B)$.

Tính khớp tại mọi vị trí giúp liên kết đồng điều của phần giao $A \cap B$, hai mảnh $A, B$, và không gian tổng thể $X = A \cup B$.

---

### 2. Đồng cấu nối $\partial$

Cách xây dựng hình học của $\partial_n: H_n(X) \to H_{n-1}(A \cap B)$ gồm bốn bước cho một lớp $[\alpha] \in H_n(X)$:

1. Chọn một chu trình đại diện $\alpha \in Z_n(X)$.
2. Chia nhỏ (subdivide) xích $\alpha$ để viết $\alpha = a + b$, trong đó $a \in C_n(A)$ và $b \in C_n(B)$. Dù $\alpha$ khép kín ($\partial\alpha = 0$), bản thân $a$ và $b$ nói chung không phải là chu trình.
3. Vì $\partial a + \partial b = \partial(a+b) = 0$, ta có $\partial a = -\partial b$. Xích này vừa nằm trong $A$ vừa nằm trong $B$, nên nằm trong $C_{n-1}(A \cap B)$ và là một $(n-1)$-chu trình.
4. Định nghĩa $\partial_n([\alpha]) = [\partial a] \in H_{n-1}(A \cap B)$.

Về trực giác, $\partial$ đo lường mức độ mà các mảnh $a, b$ của chu trình $\alpha$ không tự đóng kín trong từng phần $A, B$, nhưng biên của chúng lại khớp nhau trên phần giao $A \cap B$.

---

## 🧮 Các ví dụ

### Ví dụ 1: Tính $H_n(S^2)$

Phân rã $S^2 = U \cup V$, trong đó:
- $U$ là bán cầu bắc mở rộng qua xích đạo ($U \simeq D^2$, co rút được);
- $V$ là bán cầu nam mở rộng qua xích đạo ($V \simeq D^2$, co rút được);
- $U \cap V$ là một dải mở quanh xích đạo ($U \cap V \simeq S^1$).

Ta đã biết $H_0(U) = H_0(V) = \mathbb{Z}$, $H_n(U) = H_n(V) = 0$ với $n > 0$; và $H_n(U \cap V) = H_n(S^1)$ bằng $\mathbb{Z}$ khi $n = 0, 1$ và bằng $0$ ở các bậc khác.

**Tính $H_2(S^2)$:** Xét đoạn dãy Mayer–Vietoris quanh bậc $2$:

$$
H_2(U) \oplus H_2(V) \to H_2(S^2) \xrightarrow{\partial} H_1(U \cap V) \to H_1(U) \oplus H_1(V)
$$

Thay các nhóm đã biết vào:

$$
0 \to H_2(S^2) \xrightarrow{\partial} \mathbb{Z} \to 0
$$

Từ tính khớp tại $H_2(S^2)$ ta có $\ker\partial = 0$ ($\partial$ đơn ánh), và từ tính khớp tại $\mathbb{Z}$ ta có $\text{im}\,\partial = \mathbb{Z}$ ($\partial$ toàn ánh). Do đó $\partial$ là đẳng cấu và $H_2(S^2) \cong \mathbb{Z}$. ✓

**Tính $H_1(S^2)$:** Xét đoạn dãy quanh bậc $1$:

$$
H_1(U) \oplus H_1(V) \to H_1(S^2) \to H_0(U \cap V) \xrightarrow{\phi_0} H_0(U) \oplus H_0(V)
$$

Thay các nhóm đã biết vào:

$$
0 \to H_1(S^2) \to \mathbb{Z} \xrightarrow{\phi_0} \mathbb{Z} \oplus \mathbb{Z}
$$

Vì $U, V$ và $U \cap V$ đều liên thông đường, ánh xạ $\phi_0(1) = (1, -1)$ là đơn ánh, nên $\ker\phi_0 = 0$. Theo tính khớp, ánh xạ $H_1(S^2) \to \mathbb{Z}$ vừa đơn ánh vừa có ảnh bằng $0$, suy ra $H_1(S^2) = 0$. ✓

Kết luận: $H_0(S^2) = \mathbb{Z}$, $H_1(S^2) = 0$, $H_2(S^2) = \mathbb{Z}$ và $H_n(S^2) = 0$ với $n \geq 3$. ✓

---

### Ví dụ 2: Tính $H_n(S^n)$ bằng quy nạp

Ta đã biết trường hợp cơ sở $H_*(S^0)$ (và $H_*(S^1)$). Giả sử đã biết $H_*(S^{n-1})$. Phân rã $S^n = U \cup V$ thành hai bán cầu mở rộng co rút được sao cho $U \cap V \simeq S^{n-1}$. Với $k \geq 2$, dãy Mayer–Vietoris cho $0 \to H_k(S^n) \xrightarrow{\partial} H_{k-1}(S^{n-1}) \to 0$, suy ra $H_k(S^n) \cong H_{k-1}(S^{n-1})$. Phân tích thêm bậc $k = 1$ tương tự trường hợp $S^2$ cho kết quả $H_n(S^n) \cong \mathbb{Z}$ và $H_k(S^n) = 0$ với $0 < k < n$. ✓

---

### Ví dụ 3: Hình xuyến $T^2$

Viết $T^2 = S^1 \times S^1$ và phủ đường tròn thứ hai $S^1 = U \cup V$ bởi hai cung mở co rút được có giao gồm hai đoạn rời nhau. Đặt $A = S^1 \times U$ và $B = S^1 \times V$. Khi đó $A$ và $B$ là hai hình trụ mở đều co rút biến dạng về $S^1$, còn $A \cap B \simeq S^1 \sqcup S^1$ gồm hai đường tròn rời nhau, nên $H_1(A \cap B) \cong \mathbb{Z}^2$.

Đoạn dãy Mayer–Vietoris ở bậc $2$ có dạng:

$$
H_2(A) \oplus H_2(B) \to H_2(T^2) \xrightarrow{\partial} H_1(A \cap B) \xrightarrow{\phi_1} H_1(A) \oplus H_1(B)
$$

$$
0 \to H_2(T^2) \xrightarrow{\partial} \mathbb{Z}^2 \xrightarrow{\phi_1} \mathbb{Z} \oplus \mathbb{Z}
$$

Ánh xạ $\phi_1$ gửi hai đường tròn giao vào cùng một phần tử sinh của $H_1(A)$ và $H_1(B)$ theo công thức $(m, n) \mapsto (m + n, -(m + n))$, nên $\ker\phi_1 \cong \mathbb{Z}$ (gồm các cặp $(m, -m)$). Theo tính khớp, $H_2(T^2) \cong \ker\phi_1 \cong \mathbb{Z}$. ✓ Tiếp tục phân tích đoạn dãy tại $H_1(T^2)$ cho $H_1(T^2) \cong \mathbb{Z}^2$. ✓

---

### Ví dụ 4: Mặt phẳng xạ ảnh $\mathbb{R}P^2$

Xem $\mathbb{R}P^2$ như đĩa $D^2$ đã đồng nhất các điểm đối cực trên biên. Chọn $A$ là một đĩa mở ở phần trong ($A \simeq \mathbb{R}^2$, co rút được) và $B$ là lân cận mở của biên ($B$ co rút biến dạng về đường tròn trung tâm của dải Möbius, tức $B \simeq S^1$), khi đó $A \cap B \simeq S^1$. Ánh xạ cảm sinh $H_1(A \cap B) \to H_1(B)$ là phép nhân với $2$ (do biên của dải Möbius quấn hai vòng quanh đường tròn trung tâm), và dãy Mayer–Vietoris cho ngay $H_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$ (phần xoắn) cùng $H_2(\mathbb{R}P^2) = 0$.

---

## 🔍 Phác thảo chứng minh

### 1. Dãy khớp ngắn của các phức xích

Xét các nhóm xích kỳ dị và dãy:

$$
0 \to C_n(A \cap B) \xrightarrow{\alpha} C_n(A) \oplus C_n(B) \xrightarrow{\beta} C_n(A + B) \to 0
$$

trong đó $C_n(A + B) \subseteq C_n(X)$ là nhóm con sinh bởi các đơn hình nằm trọn trong $A$ hoặc trong $B$, còn các đồng cấu được cho bởi:
- $\alpha(c) = (i_A(c), -i_B(c))$,
- $\beta(a, b) = j_A(a) + j_B(b)$.

Ta kiểm tra trực tiếp được dãy trên là khớp ngắn. Nhờ phép chia nhỏ trọng tâm (barycentric subdivision), phép nhúng $C_\bullet(A + B) \hookrightarrow C_\bullet(X)$ cảm sinh đẳng cấu trên đồng điều $H_n(A + B) \cong H_n(X)$.

---

### 2. Bổ đề con rắn (Snake Lemma)

Theo Bổ đề con rắn (hoặc bổ đề ngoằn ngoèo trong đại số đồng điều), mỗi dãy khớp ngắn của các phức xích đều cảm sinh một dãy khớp dài trên đồng điều kèm theo đồng cấu nối $\partial$, được xây dựng tường minh bằng kỹ thuật truy đuổi biểu đồ (diagram chasing).

---

### 3. Kết luận

Kết hợp dãy khớp dài của $0 \to C_\bullet(A\cap B) \to C_\bullet(A) \oplus C_\bullet(B) \to C_\bullet(A+B) \to 0$ với đẳng cấu $H_n(A+B) \cong H_n(X)$, ta thu được dãy khớp dài Mayer–Vietoris. ✓ Chứng minh đầy đủ có thể xem trong Hatcher §2.2 hoặc Bredon Chương IV.

---

## 🧠 Tài liệu kinh điển & Tham khảo

### Công trình kinh điển

1. **Leopold Vietoris** - *"Über den höheren Zusammenhang kompakter Räume"* (1927)  
   *Dạng phát biểu ban đầu*

2. **Walther Mayer** - *"Über abstrakte Topologie"* (1929)  
   *Phiên bản tổng quát*

3. **Solomon Eilenberg, Norman Steenrod** - *"Foundations of Algebraic Topology"* (1952)  
   *Hệ thống hóa hiện đại theo lối tiên đề*

### Giáo trình

4. **Allen Hatcher** - *Algebraic Topology*, **§2.2: Mayer-Vietoris Sequence**

5. **Glen E. Bredon** - *Topology and Geometry*, **Chapter IV**

6. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapter 4**

7. **Edwin H. Spanier** - *Algebraic Topology*, **Chapter 4**

---

## 🔗 Ứng dụng

### Tô-pô tính toán
**Thuật toán phân rã:** Chia không gian phức tạp thành các mảnh đơn giản rồi tính đồng điều quy nạp qua dãy Mayer–Vietoris.

### Robot học — Lập kế hoạch chuyển động
**Không gian cấu hình:** Phân rã không gian cấu hình phức tạp để tính đồng điều, từ đó phân tích tính liên thông, lỗ và các vật cản tô-pô.

### Khoa học dữ liệu — TDA
**Đồng điều bền vững:** Dãy Mayer–Vietoris hỗ trợ tính toán hiệu quả trên tập dữ liệu lớn bằng cách ghép đồng điều từ các mảnh cục bộ sang toàn cục.

---

## Video tham khảo

- **xem trước** [Algebraic Topology 18: Mayer-Vietoris](https://www.youtube.com/watch?v=LdJlbh7Tpls) — Math at Andrews University, tiếng Anh. Dãy Mayer–Vietoris: ghép đồng điều của hai mảnh và của phần giao.
- [20. Euler Characteristic; Mayer-Vietoris Sequence - Pierre Albin](https://www.youtube.com/watch?v=W1RVwbeQy48) — Mat Neth, tiếng Anh. Pierre Albin trình bày đặc trưng Euler rồi dãy Mayer–Vietoris, đúng cặp công cụ của chương.

## 🧩 Bài tập

### Dãy khớp

1. **Kiểm chứng tính khớp:** Kiểm tra tính khớp tại mỗi vị trí của dãy $0 \to \mathbb{Z} \xrightarrow{\times 2} \mathbb{Z} \xrightarrow{\bmod 2} \mathbb{Z}/2\mathbb{Z} \to 0$.

2. **Dãy khớp tách:** Khi nào dãy khớp ngắn $0 \to A \to B \to C \to 0$ tách? Hãy nêu một ví dụ tách và một phản ví dụ không tách.

### Dãy Mayer–Vietoris

3. **Mặt cầu $S^2$:** Kiểm chứng toàn bộ dãy Mayer–Vietoris cho phép phân rã $S^2 = U \cup V$ theo hai bán cầu và tính tất cả các $H_n(S^2)$.

4. **Mặt cầu $S^3$:** Phân rã $S^3$ tương tự như $S^2$ và tính $H_n(S^3) = \mathbb{Z}, 0, 0, \mathbb{Z}$.

### Tính toán

5. **Hình số tám:** Phân rã $X = S^1 \vee S^1$ và dùng Mayer–Vietoris để chứng minh $H_1(X) = \mathbb{Z}^2$.

6. **Mặt giống 2:** Tính $H_n(\Sigma_2)$ bằng dãy Mayer–Vietoris.

### Hình xuyến

7. **Cấu trúc tích:** Với $T^2 = S^1 \times S^1$, dùng phép phủ $T^2 = (S^1 \times U) \cup (S^1 \times V)$ (với hai cung mở $U, V$ phủ $S^1$) và dãy Mayer–Vietoris để tính $H_1(T^2) = \mathbb{Z}^2$.

### Nâng cao

8. **Chai Klein:** Tính $H_n$ của chai Klein bằng dãy Mayer–Vietoris. (Đáp số: $H_1 = \mathbb{Z} \oplus \mathbb{Z}/2\mathbb{Z}$.)

9. **Không gian xạ ảnh $\mathbb{R}P^3$:** Phân rã $\mathbb{R}P^3$ và tính $H_n(\mathbb{R}P^3)$.

10. **Phần bù của nút:** Với $X = S^3 \setminus K$ (nút $K$), dùng Mayer–Vietoris để liên hệ $H_n(X)$ với các tính chất tô-pô của nút.

### Đồng cấu nối

11. **Trực giác hình học:** Trong phép phân rã $S^2 = U \cup V$, hãy mô tả ý nghĩa hình học của $\partial: H_2(S^2) \to H_1(S^1)$.

12. **Tính tường minh:** Chọn một phần tử đại diện $[\alpha] \in H_2(S^2)$ và tính $\partial([\alpha])$ từng bước.

### Dãy khớp dài

13. **Quan hệ giữa các hạng:** Từ tính khớp tại $H_1(X)$ trong dãy Mayer–Vietoris, suy ra mối liên hệ giữa hạng của các nhóm đồng điều liên quan.

14. **Bất đẳng thức số Betti:** Dùng dãy Mayer–Vietoris để chứng minh $\beta_n(X) \leq \beta_n(A) + \beta_n(B) + \beta_{n-1}(A \cap B)$.

### Ứng dụng

15. **So sánh phương pháp:** Đối với $T^2$, hãy so sánh việc tính đồng điều bằng Mayer–Vietoris và bằng đồng điều tế bào. Cách nào gọn hơn?

16. **Hợp của hai hình xuyến đặc:** Cho $X$ là không gian thu được khi dán hai hình xuyến đặc dọc theo biên $T^2$ của chúng. Tính $H_n(X)$.

### Câu hỏi suy ngẫm

17. **Van Kampen và Mayer–Vietoris:** So sánh những điểm tương đồng và khác biệt giữa hai định lý.

18. **Vì sao dãy lại khớp?** Giải thích vì sao cấu trúc phép phủ tạo ra một dãy khớp thay vì chỉ các đồng cấu rời rạc.

19. **Đồng cấu nối $\partial$:** Vì sao $\partial$ luôn làm giảm số chiều đi $1$?

20. **Phạm vi áp dụng:** Nêu một ví dụ mà dãy Mayer–Vietoris tỏ ra thiết yếu khi khó xây dựng cấu trúc phức CW trực tiếp.

---

## 📚 Đọc thêm

- **Hatcher, §2.2:** Trình bày hiện đại cùng nhiều ví dụ chi tiết.
- **Bredon, Chapter IV:** Cách tiếp cận nâng cao và hệ thống.
- **Munkres, Elements:** Chứng minh chi tiết.
- **Spanier:** Tài liệu tra cứu đầy đủ.

---

## 🎓 Tóm tắt

Dãy Mayer–Vietoris là công cụ chủ lực để tính đồng điều bằng cách phân rã không gian:

✅ **Phân rã:** $X = A \cup B$ liên hệ đồng điều của $A, B, A \cap B$ và $X$.  
✅ **Dãy khớp dài:** $\cdots \to H_n(A \cap B) \to H_n(A) \oplus H_n(B) \to H_n(X) \to H_{n-1}(A \cap B) \to \cdots$.  
✅ **Đồng cấu nối $\partial$:** Đo lường cách các mảnh của chu trình khớp biên trên phần giao.  
✅ **Tính quy nạp:** Cho phép tính $H_n(S^n)$, hình xuyến và các mặt một cách hệ thống.  
✅ **Bổ sung cho đồng điều tế bào:** Không yêu cầu cấu trúc CW, đặc biệt hiệu quả khi chọn $A, B$ co rút được và kết hợp với tương đương đồng luân.

**Tiếp theo:** Đối đồng điều (Cohomology) — lý thuyết đối ngẫu với cấu trúc đại số vành phong phú hơn.

---

**Previous:** [Lecture 07.02: Homology Computations](/contents/vi/topology-chapter07/07_02_Homology_Computations/)  
**Next:** [Lecture 07.04: Cohomology Introduction](/contents/vi/topology-chapter07/07_04_Cohomology_Introduction/)
