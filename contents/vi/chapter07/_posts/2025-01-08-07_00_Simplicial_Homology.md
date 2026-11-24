---
layout: post
title: "Lecture 07.00: Simplicial Homology - Foundations"
lang: vi
lang-ref: lecture-07-00
chapter: 7
lecture: 0
categories: [chapter07]
tags: [simplicial-homology, chain-complex, boundary-operator, betti-numbers]
description: "Simplicial homology: simplices, chain complexes, boundary operator, và homology groups - second algebraic invariant"
---

**$H_n(X)$ — Phát hiện các lỗ ở mọi chiều**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Ở Chương 06, nhóm cơ bản $$\pi_1$$ đã chứng tỏ sức mạnh tuyệt vời — nhưng nó chỉ nhìn thấy các lỗ 1 chiều và thường không giao hoán (khó tính toán bằng đại số tuyến tính!). Vậy làm sao đếm lỗ 2 chiều (khoang rỗng trong quả bóng $$S^2$$), lỗ 3 chiều, hay lỗ 10 chiều một cách **hệ thống, tự động hóa được bằng ma trận**? Henri Poincaré đã mở ra câu trả lời thiên tài: **cắt không gian thành các tam giác/tứ diện phẳng (phức đơn hình)**, biến biên hình học thành **ma trận số nguyên $$\partial_n$$**, rồi tính nhóm thương **$$H_n = \ker \partial_n / \operatorname{im} \partial_{n+1}$$** — khai sinh ra **Đồng điều Đơn hình**!

Ở chương trước, ta đã tìm hiểu **nhóm cơ bản $\pi_1(X)$** (fundamental group), bất biến đại số đầu tiên dùng để phát hiện các "lỗ một chiều" thông qua các vòng khép kín. Tuy nhiên, nhóm cơ bản không đủ để nhận diện các lỗ ở chiều cao hơn: chẳng hạn, mặt cầu $S^2$ bao quanh một khoảng rỗng hai chiều nhưng lại có $\pi_1(S^2) = 0$. Để phát hiện các lỗ ở mọi chiều, ta cần một công cụ tổng quát hơn là các **nhóm đồng điều $H_n(X)$** (homology groups).

Lý thuyết đồng điều mang lại các tính chất cơ bản sau:

- **Định nghĩa $H_n(X)$ cho mọi $n \geq 0$:** Phát hiện các lỗ $n$-chiều, mở rộng ý tưởng của nhóm cơ bản lên mọi số chiều.
- **Thuận lợi hơn cho tính toán so với $\pi_1$:** Các nhóm đồng điều luôn là nhóm Abel (abelian groups), cho phép áp dụng các kỹ thuật đại số tuyến tính và thuật toán để tính toán có hệ thống.
- **Tính hàm tử (functoriality):** Mỗi ánh xạ liên tục $f: X \to Y$ cảm sinh một đồng cấu nhóm $f_*: H_n(X) \to H_n(Y)$, xác định một hàm tử từ phạm trù các không gian tô-pô sang phạm trù các nhóm Abel.
- **Bất biến đồng luân (homotopy invariance):** Nếu $X \simeq Y$ thì $H_n(X) \cong H_n(Y)$, tức là các nhóm đồng điều chỉ phụ thuộc vào kiểu đồng luân của không gian.

![Homology detecting holes](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Simplicial_complex_example.svg/500px-Simplicial_complex_example.svg.png)  
*Cấu trúc phức đơn hình - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplicial_complex_example.svg)*

Có hai cách tiếp cận chính đối với đồng điều:

1. **Đồng điều đơn hình (simplicial homology)** (bài học này): Đòi hỏi phép chia tam giác (triangulation) không gian thành các đơn hình; đây là cách tiếp cận cổ điển và trực quan.
2. **Đồng điều kỳ dị (singular homology)** (bài học tiếp theo): Áp dụng được cho mọi không gian tô-pô mà không cần phép chia tam giác.

Trong bài học này, ta sẽ xây dựng đồng điều đơn hình theo trình tự: định nghĩa các đơn hình (simplices) và phức đơn hình (simplicial complexes), xây dựng các nhóm xích $C_n$ (chain groups) và toán tử biên $\partial$ (boundary operator), thiết lập phức xích $\cdots \to C_n \to C_{n-1} \to \cdots$, định nghĩa các nhóm đồng điều $H_n = \ker(\partial_n) / \text{im}(\partial_{n+1})$, và cuối cùng là các số Betti $\beta_n = \text{rank}(H_n)$ đếm số lỗ $n$-chiều. Bên cạnh vai trò nền tảng trong tô-pô đại số, đồng điều còn có tính thuật toán rõ ràng và được ứng dụng trong phân tích dữ liệu tô-pô (TDA), vật lý và sinh học.

---

## 🗺️ Bản đồ kiến thức nền: Đồng điều Đơn hình là gì và tính toán như thế nào?

### 1. Phức Đơn hình & Nhóm Xích $$C_n(K)$$
- **Bản chất:** Một **$$n$$-đơn hình** là bao lồi của $$n+1$$ điểm độc lập ($$0$$-đơn hình là đỉnh, $$1$$-đơn hình là cạnh, $$2$$-đơn hình là tam giác đặc, $$3$$-đơn hình là tứ diện đặc). **Nhóm xích $$C_n(K)$$** là nhóm Abel tự do sinh bởi tất cả các $$n$$-đơn hình có hướng của phức $$K$$.

### 2. Toán tử Biên $$\partial_n$$ & Quy luật Vàng $$\partial_{n-1} \circ \partial_n = 0$$
- **Bản chất:** Toán tử biên lấy mặt ngoài có dấu của mỗi đơn hình: $$\partial [v_0, \dots, v_n] = \sum_{i=0}^n (-1)^i [v_0, \dots, \hat{v}_i, \dots, v_n]$$.
- **Định luật cốt lõi ("Biên của một biên luôn bằng 0"):** $$\partial^2 = 0$$ bảo đảm mọi **biên** ($$B_n = \operatorname{im}\partial_{n+1}$$) đều tự động là một **chu trình** ($$Z_n = \ker\partial_n$$), tức $$B_n \subseteq Z_n$$!

### 3. Nhóm Đồng điều $$H_n(K) = Z_n / B_n$$ & Số Betti $$\beta_n$$
- **Bản chất:** Một chu trình $$n$$ chiều (không có biên, như một vòng khép kín hay vỏ cầu rỗng) nhưng **không phải là biên của bất kỳ khối $$(n+1)$$ chiều nào** chính là một **lỗ $$n$$ chiều thực sự**! Thương $$H_n(K) = \ker\partial_n / \operatorname{im}\partial_{n+1}$$ đo chính xác số lượng (số Betti $$\beta_n$$) và độ xoắn của các lỗ đó!

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc: Tam giác Rỗng $$K$$ vs. Tam giác Đặc $$\overline{K}$$

Xét 3 đỉnh $$v_0, v_1, v_2$$ và 3 cạnh có hướng $$e_0 = [v_0, v_1],\; e_1 = [v_1, v_2],\; e_2 = [v_2, v_0]$$.

1. **Tính toán tử biên $$\partial_1: C_1 \to C_0$$:**
   $$
   \partial_1(e_0) = v_1 - v_0, \qquad \partial_1(e_1) = v_2 - v_1, \qquad \partial_1(e_2) = v_0 - v_2.
   $$
   Tìm các **1-chu trình** $$z = a e_0 + b e_1 + c e_2 \in \ker \partial_1$$:
   $$
   \partial_1(z) = (c - a)v_0 + (a - b)v_1 + (b - c)v_2 = 0 \iff a = b = c!
   $$
   Vậy $$Z_1 = \ker \partial_1 = \mathbb{Z}\cdot(e_0 + e_1 + e_2) \cong \mathbb{Z}$$ (đúng 1 vòng khép kín quanh tam giác!).

2. **Trường hợp A — Tam giác Rỗng $$K$$ (KHÔNG có mặt tam giác $$\sigma$$):**
   Vì $$C_2(K) = 0$$ nên $$B_1(K) = \operatorname{im}\partial_2 = 0$$. Do đó:
   $$
   H_1(K) = \frac{Z_1(K)}{B_1(K)} = \frac{\mathbb{Z}}{0} \cong \mathbb{Z} \quad (\beta_1 = 1: \text{ phát hiện đúng 1 lỗ tròn!}).
   $$

3. **Trường hợp B — Tam giác Đặc $$\overline{K}$$ (THÊM $$2$$-đơn hình $$\sigma = [v_0, v_1, v_2]$$):**
   Tính biên $$\partial_2(\sigma) = [v_1, v_2] - [v_0, v_2] + [v_0, v_1] = e_1 + e_2 + e_0$$ (vì $-[v_0, v_2] = +[v_2, v_0] = e_2$).
   - Kiểm tra nhanh $$\partial_1(\partial_2 \sigma) = (v_2-v_1) + (v_0-v_2) + (v_1-v_0) = 0$$! ✓
   - Lúc này $$B_1(\overline{K}) = \operatorname{im}\partial_2 = \mathbb{Z}\cdot(e_0 + e_1 + e_2) = Z_1(\overline{K})$$! Do đó:
     $$
     H_1(\overline{K}) = \frac{Z_1(\overline{K})}{B_1(\overline{K})} = \frac{\mathbb{Z}}{\mathbb{Z}} = 0 \quad (\beta_1 = 0: \text{ lỗ đã bị lấp kín!}).
     $$

### Khung giải thích: Quy trình 4 bước tính Đồng điều Đơn hình bằng tay (nên đọc chậm)

#### Bước 1: Liệt kê các đơn hình có hướng theo từng bậc $$0, 1, 2, \dots$$
Viết rõ cơ sở cho từng nhóm xích $$C_0, C_1, C_2, \dots$$ (mỗi $$C_n \cong \mathbb{Z}^{c_n}$$).

#### Bước 2: Viết ma trận nguyên cho từng toán tử biên $$\partial_n$$
Mỗi cột của ma trận $$\partial_n$$ ghi biên của một $$n$$-đơn hình dưới dạng tổ hợp tuyến tính (chỉ gồm $$0, +1, -1$$) của các $$(n-1)$$-đơn hình. Luôn kiểm tra nhanh tích ma trận $$\partial_{n-1}\partial_n = 0$$ để chống nhầm dấu!

#### Bước 3: Tìm hạt nhân $$Z_n = \ker \partial_n$$ và ảnh $$B_n = \operatorname{im} \partial_{n+1}$$
Với hệ số thực $$\mathbb{R}$$, bạn chỉ cần tính hạng ma trận ($$\beta_n = \dim\ker\partial_n - \operatorname{rank}\partial_{n+1}$$). Với hệ số nguyên $$\mathbb{Z}$$, dạng chuẩn Smith (Smith Normal Form) cho ra cả phần tự do lẫn phần xoắn (như $$\mathbb{Z}/2\mathbb{Z}$$ trên $$\mathbb{R}P^2$$!).

#### Bước 4: Kiểm tra chéo bằng Công thức Euler–Poincaré
Luôn kiểm tra lại kết quả bằng đẳng thức vàng: $$\sum (-1)^n c_n = \sum (-1)^n \beta_n = \chi(K)$$ — nếu hai vế khớp nhau, phép tính của bạn gần như chắc chắn đúng!

$$
\text{Phức đơn hình }K
\;\xrightarrow{\;\partial_n,\; \partial^2=0\;}\;
Z_n = \ker\partial_n,\; B_n = \operatorname{im}\partial_{n+1}
\;\xrightarrow{\;Z_n/B_n\;}\;
H_n(K) \;\&\; \chi(K) = \sum (-1)^n \beta_n.
$$

---

## 🔺 Đơn hình và Phức đơn hình

### 1. Đơn hình hình học

<div class="textbook-definition" markdown="1">
**Định nghĩa ($n$-đơn hình):**  
Cho $v_0, v_1, \ldots, v_n \in \mathbb{R}^N$ là các điểm **độc lập affine** (affinely independent), nghĩa là không có điểm $v_i$ nào nằm trong bao affine của các điểm còn lại. Khi đó, **$n$-đơn hình** ($n$-simplex) $\sigma = [v_0, v_1, \ldots, v_n]$ là bao lồi của các điểm này:

$$
\sigma = \left\{\sum_{i=0}^n t_i v_i : t_i \geq 0, \sum t_i = 1\right\}
$$
</div>

Các điểm $v_0, \ldots, v_n$ được gọi là các **đỉnh** (vertices) của $\sigma$ (gồm $n+1$ đỉnh), và số chiều của đơn hình là $\dim(\sigma) = n$. Điều kiện độc lập affine đảm bảo các đỉnh không cùng nằm trên một siêu phẳng chiều thấp hơn.

**Các ví dụ:**

- **$0$-đơn hình:** Một điểm duy nhất $[v_0]$ (một đỉnh).
- **$1$-đơn hình:** $[v_0, v_1]$ là đoạn thẳng nối hai đỉnh (một cạnh).
- **$2$-đơn hình:** $[v_0, v_1, v_2]$ là tam giác đặc (bao gồm cả phần bên trong).
- **$3$-đơn hình:** $[v_0, v_1, v_2, v_3]$ là tứ diện đặc (bao gồm cả phần thể tích bên trong).
- **$n$-đơn hình:** Dạng tổng quát của tam giác đặc trong không gian $n$-chiều.

![Simplices](https://upload.wikimedia.org/wikipedia/commons/thumb/6/60/Simplexes.svg/500px-Simplexes.svg.png)  
*Các đơn hình chiều 0, 1, 2, 3 - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Simplexes.svg)*

---

### 2. Mặt của đơn hình

<div class="textbook-definition" markdown="1">
**Định nghĩa (Mặt):**  
Mỗi tập con khác rỗng của tập các đỉnh của $\sigma$ xác định một **mặt** (face) của $\sigma$.
</div>

**Mặt thứ $i$** của $\sigma$ thu được bằng cách bỏ đi đỉnh $v_i$:

$$
\partial_i \sigma = [v_0, \ldots, \hat{v}_i, \ldots, v_n]
$$

trong đó dấu mũ $\hat{v}_i$ biểu thị việc loại bỏ đỉnh $v_i$. Đây là mặt $(n-1)$-chiều đối diện với đỉnh $v_i$. Một $n$-đơn hình có tổng cộng $2^{n+1} - 1$ mặt khác rỗng (hoặc $2^{n+1}$ nếu tính cả tập rỗng).

**Ví dụ:** Tam giác $[v_0, v_1, v_2]$ có $7$ mặt khác rỗng:
- 3 đỉnh ($0$-mặt): $[v_0]$, $[v_1]$, $[v_2]$;
- 3 cạnh ($1$-mặt): $[v_0,v_1]$, $[v_1,v_2]$, $[v_0,v_2]$;
- 1 mặt hai chiều (chính nó): $[v_0,v_1,v_2]$.

---

### 3. Phức đơn hình

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phức đơn hình):**  
Một **phức đơn hình** (simplicial complex) $K$ là một họ các đơn hình trong $\mathbb{R}^N$ thỏa mãn hai điều kiện:
1. **Đóng với phép lấy mặt:** Nếu $\sigma \in K$ và $\tau$ là một mặt của $\sigma$ thì $\tau \in K$.
2. **Giao đúng cách:** Nếu $\sigma, \tau \in K$ thì giao $\sigma \cap \tau$ là tập rỗng hoặc là một mặt chung của cả $\sigma$ và $\tau$.
</div>

Hợp của tất cả các đơn hình trong $K$, ký hiệu $|K|$, được gọi là **thể hiện hình học** (geometric realization) của $K$. Đây là một không gian tô-pô tạo thành bằng cách ghép các đơn hình theo các mặt chung của chúng.

**Các ví dụ:**

**Ví dụ 1: Biên của tam giác.** Gồm 3 đỉnh $v_0, v_1, v_2$ và 3 cạnh $[v_0,v_1], [v_1,v_2], [v_0,v_2]$, không chứa $2$-mặt ở bên trong. Đây là phức $1$-chiều đồng phôi với đường tròn $S^1$.

**Ví dụ 2: Tam giác đặc.** Gồm 3 đỉnh, 3 cạnh và 1 tam giác đặc $[v_0,v_1,v_2]$. Đây là phức $2$-chiều đồng phôi với đĩa đóng $D^2$.

**Ví dụ 3: Phép chia tam giác hình xuyến.** Ta chia một hình vuông thành các tam giác rồi đồng nhất các cạnh đối diện một cách thích hợp để thu được phức đơn hình $K$ với $|K| \cong T^2$.

---

## 🔗 Nhóm xích

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa (Nhóm xích):**  
Cho $K$ là một phức đơn hình. **Nhóm $n$-xích** ($n$-chain group) của $K$ là nhóm Abel tự do sinh bởi các $n$-đơn hình có định hướng của $K$:

$$
C_n(K) = \text{free abelian group generated by oriented n-simplices}
$$
</div>

Mỗi phần tử của $C_n(K)$, gọi là một **$n$-xích** ($n$-chain), là một tổng hình thức với hệ số nguyên:

$$
c = \sum_{i} n_i \sigma_i \quad (n_i \in \mathbb{Z}, \sigma_i \text{ là các } n\text{-đơn hình})
$$

Phép cộng được thực hiện theo từng thành phần bằng cách cộng các hệ số của cùng một đơn hình. Chẳng hạn, với hai $n$-đơn hình $\sigma_1, \sigma_2$, ta có $3\sigma_1 + 2\sigma_2 \in C_n(K)$, $\sigma_1 - \sigma_1 = 0$, và $-\sigma_1$ biểu thị đơn hình $\sigma_1$ lấy theo hướng ngược lại.

---

### 2. Định hướng

Các $n$-đơn hình cần được gán **định hướng** (orientation) thông qua thứ tự liệt kê các đỉnh $[v_0, \ldots, v_n]$:
- Một hoán vị chẵn các đỉnh giữ nguyên định hướng.
- Một hoán vị lẻ các đỉnh đảo ngược định hướng.

Chẳng hạn, $[v_0, v_1, v_2] = -[v_1, v_0, v_2]$. Việc gán định hướng là cần thiết để toán tử biên xác định được các dấu một cách nhất quán trên các mặt của đơn hình.

---

### 3. Tính chất

$C_n(K)$ là nhóm Abel tự do với tập sinh là toàn bộ các $n$-đơn hình có định hướng (mỗi đơn hình chọn một hướng đại diện), và hạng (rank) của nó bằng số lượng $n$-đơn hình trong $K$.

- Nếu $K$ là phức hữu hạn có $r$ đơn hình $n$-chiều thì $C_n(K) \cong \mathbb{Z}^r$.
- Nếu $n > \dim(K)$ thì không có $n$-đơn hình nào nên $C_n(K) = 0$.

---

## ∂ Toán tử biên

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa (Toán tử biên):**  
**Toán tử biên** $\partial_n: C_n(K) \to C_{n-1}(K)$ được xác định trên mỗi $n$-đơn hình bằng công thức:

$$
\partial_n([v_0, \ldots, v_n]) = \sum_{i=0}^n (-1)^i [v_0, \ldots, \hat{v}_i, \ldots, v_n]
$$
</div>

Sau đó, ta mở rộng tuyến tính $\partial_n$ lên toàn bộ nhóm xích: với $c = \sum_i n_i \sigma_i$, đặt $\partial_n(c) = \sum_i n_i \partial_n(\sigma_i)$. Về mặt hình học, $\partial(\sigma)$ là biên có định hướng của $\sigma$, là tổng đan dấu các mặt $(n-1)$-chiều của nó.

**Ví dụ 1 (Cạnh):** Với cạnh có hướng $\sigma = [v_0, v_1]$ đi từ $v_0$ đến $v_1$, ta có:

$$
\partial([v_0, v_1]) = [v_1] - [v_0]
$$

Biên của cạnh là hiệu giữa đỉnh cuối (dấu dương) và đỉnh đầu (dấu âm).

**Ví dụ 2 (Tam giác):** Với tam giác $\sigma = [v_0, v_1, v_2]$ định hướng ngược chiều kim đồng hồ:

$$
\partial([v_0, v_1, v_2]) = [v_1, v_2] - [v_0, v_2] + [v_0, v_1]
$$

Đây là tổng ba cạnh của tam giác với định hướng cảm sinh phù hợp khi đi một vòng quanh chu vi.

![Triangle boundary](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Triangle_boundary.svg/300px-Triangle_boundary.svg.png)  
*Biên có định hướng của tam giác - Nguồn concept*

**Ví dụ 3 (Tứ diện):** Với tứ diện $\sigma = [v_0, v_1, v_2, v_3]$:

$$
\partial(\sigma) = [v_1, v_2, v_3] - [v_0, v_2, v_3] + [v_0, v_1, v_3] - [v_0, v_1, v_2]
$$

Biên của tứ diện gồm bốn mặt tam giác với dấu đan xen theo định hướng cảm sinh.

---

### 2. Tính chất cốt lõi: $\partial^2 = 0$

<div class="textbook-theorem" markdown="1">
**Định lý (Tính chất cơ bản):**  
Ánh xạ hợp $\partial_{n-1} \circ \partial_n = 0$ là đồng cấu không.
</div>

Ta thường viết gọn là $\partial^2 = 0$ hoặc $\partial\partial = 0$, nghĩa là **biên của một biên luôn bằng $0$**.

**Kiểm tra cho trường hợp tam giác:** Xét $\sigma = [v_0, v_1, v_2]$. Ta đã có $\partial(\sigma) = [v_1, v_2] - [v_0, v_2] + [v_0, v_1]$. Áp dụng $\partial$ lần thứ hai với $\partial([v_1, v_2]) = [v_2] - [v_1]$, $\partial([v_0, v_2]) = [v_2] - [v_0]$ và $\partial([v_0, v_1]) = [v_1] - [v_0]$, ta thu được:

$$
\partial^2(\sigma) = ([v_2] - [v_1]) - ([v_2] - [v_0]) + ([v_1] - [v_0]) = 0
$$

Mỗi đỉnh xuất hiện đúng hai lần với dấu trái nhau nên triệt tiêu hoàn toàn. Trong trường hợp tổng quát, chứng minh tổ hợp cũng cho kết quả tương tự vì các cặp mặt thu được khi bỏ lần lượt hai đỉnh $v_i, v_j$ luôn triệt tiêu theo cặp dấu.

Về mặt trực giác, biên của tam giác là ba cạnh tạo thành một vòng khép kín, còn biên của vòng khép kín thì các đầu mút triệt tiêu hết nên bằng $0$. Tính chất $\partial^2 = 0$ là điều kiện tiên quyết để xây dựng các nhóm đồng điều.

---

## 📊 Phức xích và Đồng điều

### 1. Phức xích

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phức xích):**  
Một **phức xích** (chain complex) là một dãy các nhóm Abel và các đồng cấu:

$$
\cdots \xrightarrow{\partial_{n+2}} C_{n+1} \xrightarrow{\partial_{n+1}} C_n \xrightarrow{\partial_n} C_{n-1} \xrightarrow{\partial_{n-1}} \cdots \xrightarrow{\partial_1} C_0 \xrightarrow{\partial_0} 0
$$

thỏa mãn $\partial^2 = 0$, tức là $\text{im}(\partial_{n+1}) \subseteq \ker(\partial_n)$ với mọi $n$.
</div>

Dãy các nhóm xích $C_n(K)$ cùng với các toán tử biên $\partial_n$ lập thành phức xích của phức đơn hình $K$.

---

### 2. Chu trình và Biên

<div class="textbook-definition" markdown="1">
**Định nghĩa ($n$-chu trình):**  
Nhóm các **$n$-chu trình** ($n$-cycles) là hạt nhân của $\partial_n$:

$$
Z_n(K) = \ker(\partial_n) = \{c \in C_n : \partial c = 0\}
$$
</div>

Một chu trình là một xích không có biên, tức là "khép kín". Ví dụ, một vòng khép kín trong đồ thị là một $1$-chu trình.

<div class="textbook-definition" markdown="1">
**Định nghĩa ($n$-biên):**  
Nhóm các **$n$-biên** ($n$-boundaries) là ảnh của $\partial_{n+1}$:

$$
B_n(K) = \text{im}(\partial_{n+1}) = \{\partial d : d \in C_{n+1}\}
$$
</div>

Một biên là một xích đồng thời là biên của một xích ở chiều cao hơn một bậc. Ví dụ, chu vi của một tam giác đặc là một $1$-biên.

<div class="textbook-lemma" markdown="1">
**Bổ đề:** $B_n \subseteq Z_n$ (mọi biên đều là chu trình).
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Nếu $c \in B_n$ thì tồn tại $d \in C_{n+1}$ sao cho $c = \partial d$. Khi đó $\partial c = \partial(\partial d) = \partial^2 d = 0$, suy ra $c \in Z_n$. ✓
</div>

Mọi biên đều là chu trình, nhưng điều ngược lại không nhất thiết đúng. Chính những chu trình không phải là biên mới phản ánh các lỗ của không gian.

---

### 3. Nhóm đồng điều

<div class="textbook-definition" markdown="1">
**Định nghĩa (Nhóm đồng điều):**

$$
H_n(K) = Z_n(K) / B_n(K) = \ker(\partial_n) / \text{im}(\partial_{n+1})
$$
</div>

$H_n(K)$ là nhóm thương của các $n$-chu trình theo các $n$-biên. Về mặt trực giác:
- **Chu trình ($Z_n$):** Các xích khép kín có thể bao quanh lỗ.
- **Biên ($B_n$):** Các chu trình bị "lấp đầy" bởi một xích chiều cao hơn, do đó không phải là lỗ thực sự.
- **Đồng điều ($H_n$):** Đo lường các chu trình không phải là biên, tức là các lỗ $n$-chiều thực sự.

Chẳng hạn, với mặt cầu rỗng $S^2$, bề mặt khép kín của nó tạo thành một $2$-chu trình nhưng không phải là biên của một $3$-xích nào (vì phần bên trong rỗng), dẫn đến một phần tử khác không trong $H_2(S^2) \cong \mathbb{Z}$.

---

### 4. Tính chất

- **Tính Abel:** $H_n(K)$ luôn là nhóm Abel (khác với $\pi_1$ có thể không giao hoán).
- **Hữu hạn sinh:** Nếu $K$ là phức đơn hình hữu hạn thì $H_n(K)$ là nhóm Abel hữu hạn sinh.
- **Định lý cấu trúc:** Mọi nhóm Abel hữu hạn sinh đều phân tích được thành $H_n(K) \cong \mathbb{Z}^r \oplus (\text{phần xoắn})$, trong đó phần xoắn (torsion) là tổng trực tiếp hữu hạn các nhóm cyclic hữu hạn.
- **Số Betti:** $\beta_n = \text{rank}(H_n)$ là số hạng tử $\mathbb{Z}$ trong phần tự do, dùng để đếm số lỗ $n$-chiều.
- **Phần xoắn (torsion):** Các nhóm cyclic hữu hạn phản ánh các đặc trưng tô-pô tinh tế hơn mà số Betti không ghi nhận hết.

---

## 🔢 Ví dụ

### Ví dụ 1: Một điểm

Xét phức $K$ chỉ gồm một đỉnh duy nhất.
- **Nhóm xích:** $C_0 = \mathbb{Z}$ (một đỉnh sinh), và $C_n = 0$ với mọi $n > 0$.
- **Chu trình và biên:** $Z_0 = \mathbb{Z}$, $Z_n = 0$ ($n > 0$), và $B_n = 0$ với mọi $n$.
- **Đồng điều:** $H_0 = \mathbb{Z}/0 = \mathbb{Z}$ và $H_n = 0$ với mọi $n > 0$.

Kết quả cho thấy một điểm có đúng một thành phần liên thông ($H_0 = \mathbb{Z}$) và không có lỗ nào ở chiều cao hơn.

---

### Ví dụ 2: Đường tròn $S^1$

Ta chia tam giác $S^1$ theo cách tối giản gồm 3 đỉnh và 3 cạnh (biên của một tam giác).
- **Nhóm xích:** $C_0 = \mathbb{Z}^3$, $C_1 = \mathbb{Z}^3$, và $C_n = 0$ với $n \geq 2$.
- **Toán tử biên:** Biên của mỗi cạnh là hiệu hai đỉnh đầu mút. Tổng ba cạnh tạo thành vòng khép kín có biên bằng $0$, và đó là phần tử sinh của $Z_1 = \ker(\partial_1) \cong \mathbb{Z}$.
- **Kết quả:**
  - $H_0(S^1) = \mathbb{Z}$ (một thành phần liên thông);
  - $H_1(S^1) = \mathbb{Z}$ (một lỗ $1$-chiều tương ứng với vòng tròn);
  - $H_n(S^1) = 0$ với mọi $n \geq 2$.

Như vậy $\beta_0 = 1$ và $\beta_1 = 1$.

---

### Ví dụ 3: Mặt cầu $S^2$

Chia tam giác mặt cầu $S^2$ (chẳng hạn bằng mặt của một khối nhị thập diện đều — icosahedron). Tính toán đồng điều cho:
- $H_0(S^2) = \mathbb{Z}$ (một thành phần liên thông);
- $H_1(S^2) = 0$ (không có lỗ $1$-chiều);
- $H_2(S^2) = \mathbb{Z}$ (một lỗ $2$-chiều là khoảng rỗng bên trong);
- $H_n(S^2) = 0$ với mọi $n \geq 3$.

Trong khi nhóm cơ bản $\pi_1(S^2) = 0$ không phát hiện được khoảng rỗng bên trong mặt cầu, nhóm đồng điều $H_2(S^2) = \mathbb{Z}$ lại nhận diện chính xác đặc trưng này.

---

## 🧠 Tài liệu kinh điển & Tham khảo

### Công trình kinh điển

1. **Henri Poincaré** - *"Analysis Situs"* (1895-1904)  
   *Đặt nền móng cho khái niệm đồng điều*

2. **Emmy Noether** - *Group theory approach* (1920s)  
   *Xây dựng nền tảng đại số bằng lý thuyết nhóm*

3. **Leopold Vietoris** - *"Über den höheren Zusammenhang"* (1927)  
   *Hình thức hóa lý thuyết đồng điều*

### Giáo trình

4. **Allen Hatcher** - *Algebraic Topology*, **§2.1: Simplicial Homology**  
   *Cách trình bày hiện đại và trực quan*

5. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapters 1-2**  
   *Trình bày rõ ràng, chú trọng tính toán*

6. **Glen E. Bredon** - *Topology and Geometry*, **Chapter IV**

7. **Joseph J. Rotman** - *An Introduction to Algebraic Topology*, **Chapters 5-6**

---

## 🔗 Ứng dụng và Liên kết

### Phân tích dữ liệu tô-pô (TDA)
**Đồng điều bền vững (Persistent Homology):** Tính $H_n$ trên nhiều thang đo khác nhau để phát hiện các đặc trưng (lỗ) trong dữ liệu đám mây điểm, ứng dụng trong nhận dạng hình dạng, sinh học và mạng cảm biến.

### Tô-pô tính toán
**Thuật toán:** Sử dụng phép khử ma trận để tính $H_n$. Các thư viện phần mềm như CHomP, Dionysus, GUDHI được dùng trong đồ họa máy tính và robot học.

### Vật lý chất rắn
**Pha tô-pô:** Đồng điều được dùng để phân loại các chất cách điện tô-pô, với các số Betti đóng vai trò bất biến tô-pô.

### Sinh học cấu trúc protein
**Phân tích khoang rỗng:** Các khoang bên trong cấu trúc protein được mô tả thông qua $H_1, H_2$, hỗ trợ phát hiện các vị trí gắn kết thuốc.

### Mạng cảm biến
**Lỗ hổng vùng phủ:** $H_1$ giúp phát hiện các khoảng trống trong vùng phủ sóng cảm biến phục vụ tối ưu hóa mạng.

---

## Video tham khảo

- **xem trước** [Algebraic Topology 10: Simplicial Homology](https://www.youtube.com/watch?v=-bM8Gg6bOJo) — Math at Andrews University, tiếng Anh. Đơn hình, phức đơn hình và toán tử biên, đúng mạch dựng của bài.
- [11. ∆-Complexes; Simplicial Homology - Pierre Albin](https://www.youtube.com/watch?v=RGhaHydnk-Q) — Mat Neth, tiếng Anh. Pierre Albin trình bày $\Delta$-phức rồi đến đồng điều đơn hình trong một buổi học đầy đủ.

## 🧩 Bài tập

### Đơn hình

1. **Vẽ hình:** Phác thảo các $0$-, $1$-, $2$-, $3$-đơn hình và gắn nhãn các đỉnh.

2. **Mặt của đơn hình:** Liệt kê tất cả các mặt của $[v_0,v_1,v_2,v_3]$. Có bao nhiêu mặt ở mỗi chiều?

3. **Đếm số mặt:** Một $n$-đơn hình có bao nhiêu $k$-mặt? (Sử dụng hệ số nhị thức.)

### Nhóm xích

4. **Tính toán:** Với $K$ là biên của một tam giác, hãy xác định $C_0, C_1, C_2$.

5. **Định hướng:** Kiểm tra rằng quy ước $[v_0,v_1,v_2] = -[v_1,v_0,v_2]$ bảo toàn công thức toán tử biên.

### Toán tử biên

6. **Kiểm chứng $\partial^2 = 0$:** Với tứ diện $[v_0,v_1,v_2,v_3]$, tính tường minh $\partial^2(\sigma)$.

7. **Trực giác hình học:** Giải thích trực quan vì sao biên của một biên luôn bằng $0$.

### Tính nhóm đồng điều

8. **Một điểm:** Kiểm chứng $H_0(\text{point}) = \mathbb{Z}$ và $H_n = 0$ với $n > 0$.

9. **Hai điểm rời nhau:** Tính $H_0(v_0 \sqcup v_1) = \mathbb{Z} \oplus \mathbb{Z}$ (hai thành phần liên thông).

10. **Đường tròn:** Chia tam giác $S^1$ với 4 đỉnh rồi tính chi tiết $H_0, H_1$.

### Ví dụ mở rộng

11. **Đĩa $D^2$:** Chia tam giác $D^2$ và tính $H_0 = \mathbb{Z}$, $H_1 = H_2 = 0$.

12. **Hình xuyến $T^2$:** Phác thảo một phép chia tam giác của $T^2$ và dự đoán $H_0 = \mathbb{Z}$, $H_1 = \mathbb{Z}^2$, $H_2 = \mathbb{Z}$.

### Nâng cao

13. **Đặc trưng Euler:** Với công thức $\chi = \sum (-1)^n \beta_n$, hãy kiểm chứng cho $S^1, S^2, T^2$.

14. **Tổng liên thông:** Tìm hiểu công thức tính $H_*(\Sigma_g)$ cho mặt định hướng giống $g$.

15. **Mặt phẳng xạ ảnh $\mathbb{R}P^2$:** Tính $H_0 = \mathbb{Z}$, $H_1 = \mathbb{Z}/2\mathbb{Z}$, $H_2 = 0$ (mặt không định hướng được).

---

## 📚 Đọc thêm

- **Hatcher, §2.1:** Cách tiếp cận hiện đại và đầy đủ.
- **Munkres, Elements:** Tập trung vào kỹ thuật tính toán.
- **Rotman:** Các tính toán chi tiết.
- **Edelsbrunner & Harer:** *Computational Topology* (ứng dụng trong TDA).

---

## 🎓 Tóm tắt

Trong bài học này, ta đã xây dựng **đồng điều đơn hình** — nền tảng tính toán của lý thuyết đồng điều:

✅ **Đơn hình (Simplices):** Các khối xây dựng hình học từ đỉnh, cạnh, tam giác đến tứ diện và chiều cao hơn.  
✅ **Nhóm xích (Chain Groups):** $C_n$ là nhóm Abel tự do sinh bởi các $n$-đơn hình có định hướng.  
✅ **Toán tử biên (Boundary Operator):** $\partial_n: C_n \to C_{n-1}$ thỏa mãn $\partial^2 = 0$.  
✅ **Phức xích (Chain Complex):** Dãy $\cdots \to C_n \to C_{n-1} \to \cdots$.  
✅ **Nhóm đồng điều (Homology):** $H_n = \ker(\partial_n) / \text{im}(\partial_{n+1})$.  
✅ **Các ví dụ cơ bản:** $H_*(\text{point})$, $H_*(S^1)$, $H_*(S^2)$.

Các điểm cần ghi nhớ: đồng điều phát hiện lỗ ở mọi chiều thông qua thương của chu trình theo biên, dựa trên tính chất cốt lõi $\partial^2 = 0$; các nhóm đồng điều luôn là nhóm Abel và có thể tính bằng phép khử ma trận.

**Tiếp theo:** Lecture 07.01 về **Đồng điều kỳ dị (Singular Homology)** — định nghĩa đồng điều cho mọi không gian tô-pô.

---

*"Homology: where chains become algebra, and holes become numbers."*

---

**Previous Chapter:** [Chapter 06: Fundamental Group](/contents/vi/topology-chapter06/)  
**Next:** [Lecture 07.01: Singular Homology](/contents/vi/topology-chapter07/07_01_Singular_Homology/)
