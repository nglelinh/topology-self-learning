---
layout: post
title: "Lecture 07.04: Cohomology - Introduction"
lang: vi
lang-ref: lecture-07-04
chapter: 7
lecture: 4
categories: [chapter07]
tags: [cohomology, cup-product, ring-structure, poincare-duality]
description: "Cohomology Hⁿ(X): dual của homology, cup product ∪, ring structure, Universal Coefficient Theorem"
---

**$H^n(X)$ — Lý thuyết đối ngẫu với cấu trúc vành**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Hãy tưởng tượng bạn có hai không gian tô-pô kỳ lạ: mặt phẳng xạ ảnh phức $$\mathbb{C}P^2$$ và bó cầu $$S^2 \vee S^4$$ (một mặt cầu 2 chiều chạm một mặt cầu 4 chiều tại đúng một điểm). Nếu bạn dùng toàn bộ cỗ máy đồng điều của các bài trước để đo hai không gian này, máy đo sẽ trả về **cùng một kết quả y hệt nhau** ở mọi bậc: $$H_0 \cong \mathbb{Z},\; H_2 \cong \mathbb{Z},\; H_4 \cong \mathbb{Z}$$ và bằng $$0$$ ở các bậc khác! Liệu đồng điều đã bó tay? Không — chỉ cần **lấy đối ngẫu** sang **đối đồng điều $$H^n(X)$$**, một phép nhân kỳ diệu gọi là **tích cup ($$\cup$$)** lập tức hiện ra và phân biệt hai không gian ấy chỉ trong một dòng!

Các nhóm đồng điều $H_n(X)$ cung cấp một hệ bất biến nhóm Abel hữu ích để đo lường các lỗ của không gian tô-pô. Tuy nhiên, nếu chỉ xét từng nhóm riêng lẻ, ta vẫn bỏ sót nhiều thông tin hình học. **Đối đồng điều $H^n(X)$** (cohomology), được xây dựng bằng cách đối ngẫu hóa phức xích đồng điều, mang thêm cấu trúc đại số mà đồng điều không có:

✅ **Tích cup ($\cup$):** Phép nhân giữa các lớp đối đồng điều $H^p(X) \times H^q(X) \to H^{p+q}(X)$.

✅ **Cấu trúc vành phân bậc:** Tổng trực tiếp $H^*(X) = \bigoplus_{n=0}^\infty H^n(X)$ lập thành một vành giao hoán phân bậc, cho bất biến chặt chẽ hơn so với các nhóm đơn thuần.

✅ **Tính phản biến (contravariance):** Ánh xạ liên tục $f: X \to Y$ cảm sinh đồng cấu theo chiều ngược lại $f^*: H^n(Y) \to H^n(X)$.

✅ **Khả năng phân biệt tinh tế hơn:** Vành đối đồng điều phân biệt được những không gian có cùng nhóm đồng điều.

✅ **Đối ngẫu Poincaré:** Liên hệ trực tiếp $H^k(M)$ và $H_{n-k}(M)$ trên các đa tạp đóng định hướng được.

![Cohomology cup product](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Cup_product.svg/400px-Cup_product.svg.png)  
*Minh họa tích cup - Nguồn concept*

Trong bài học này, ta sẽ lần lượt tìm hiểu phức đối xích và toán tử đối biên, nhóm đối đồng điều $H^n(X; G)$, tích cup và cấu trúc vành $H^*(X)$, Định lý Hệ số Phổ quát (Universal Coefficient Theorem), Đối ngẫu Poincaré cùng các ví dụ chuẩn (điểm, mặt cầu, hình xuyến, $\mathbb{R}P^2$) và ứng dụng trong lý thuyết chướng ngại cũng như các lớp đặc trưng.

---

## 🗺️ Kiến thức cần nhớ: Đối đồng điều là gì và nghiên cứu những gì?

Nếu bạn tốt nghiệp đại học ngành toán, lý hoặc kỹ thuật, bạn đã từng quen với **không gian đối ngẫu** $$V^* = \operatorname{Hom}(V, \mathbb{R})$$ trong đại số tuyến tính và toán tử vi phân ngoài $$d$$ trong giải tích vectơ. Đối đồng điều chính là cầu nối tự nhiên đưa hai ý tưởng đó vào tô-pô học.

### 1. Từ Xích sang Đối xích: Nghệ thuật đo đạc bằng hàm tuyến tính
- **Bản chất:** Đồng điều $$H_n(X)$$ nghiên cứu trực tiếp các mảnh hình học ($$n$$-xích: điểm, cạnh, tam giác). Đối đồng điều $$H^n(X; G)$$ chuyển sang nghiên cứu các **hàm tuyến tính** ($$n$$-đối xích) gắn một con số hoặc phần tử nhóm $$G$$ lên mỗi mảnh hình học đó — hệt như cách trường lực hay dạng vi phân đo đạc dọc theo đường cong và mặt cong.
- **Tính phản biến:** Một ánh xạ liên tục $$f: X \to Y$$ đẩy các mảnh hình học xuôi chiều ($$f_*: H_n(X) \to H_n(Y)$$), nhưng kéo ngược các hàm đo đạc theo chiều ngược lại ($$f^*: H^n(Y) \to H^n(X)$$).

### 2. Tích Cup & Cấu trúc Vành phân bậc $$H^*(X)$$
- **Bản chất:** Giống như hai hàm số $$\alpha(x), \beta(x)$$ có thể nhân với nhau thành hàm $$(\alpha\cdot\beta)(x)$$, hai đối xích bậc $$p$$ và $$q$$ có thể nhân với nhau bằng **tích cup** $$\alpha \cup \beta$$ để tạo thành đối xích bậc $$p+q$$.
- **Lĩnh vực nghiên cứu:** Biến hệ bất biến tô-pô từ những nhóm Abel rời rạc thành một **vành đại số phân bậc** $$H^*(X)$$, đủ sức phân biệt các không gian có nhóm đồng điều y hệt nhau và mã hóa cách các mặt con giao nhau bên trong đa tạp.

### 3. Đối ngẫu Poincaré & Lớp đặc trưng
- **Bản chất:** Trên một đa tạp đóng định hướng được $$n$$ chiều $$M$$, Đối ngẫu Poincaré khẳng định $$H^k(M) \cong H_{n-k}(M)$$ — một đối xứng gương sâu sắc giữa các lỗ chiều $$k$$ và chiều $$n-k$$.
- **Ứng dụng:** Đối đồng điều là ngôn ngữ chuẩn của đối đồng điều de Rham (trường điện từ, định lý Stokes), lý thuyết chướng ngại, bó vectơ (lớp Chern, Stiefel–Whitney) và hình học đại số hiện đại.

---

## 🧮 Ví dụ tính tay làm từng bước

### Ví dụ 1: Tính toán tử đối biên $$\delta$$ trên tam giác $$S^1$$ (3 đỉnh, 3 cạnh)
Hãy chia đường tròn $$S^1$$ thành một tam giác gồm 3 đỉnh $$v_0, v_1, v_2$$ và 3 cạnh có hướng $$e_0 = [v_0, v_1],\; e_1 = [v_1, v_2],\; e_2 = [v_2, v_0]$$. Nhớ rằng biên của cạnh là $$\partial [v_i, v_j] = v_j - v_i$$.

1. **Xét một $$0$$-đối xích** (hàm gán số nguyên cho mỗi đỉnh): chọn $$\phi(v_0) = 1,\; \phi(v_1) = 3,\; \phi(v_2) = 0$$. Tính đối biên $$\delta\phi \in C^1(S^1; \mathbb{Z})$$ trên từng cạnh bằng công thức $$(\delta\phi)(e) = \phi(\partial e)$$:
   $$
   (\delta\phi)(e_0) = \phi(v_1) - \phi(v_0) = 3 - 1 = 2,
   \qquad
   (\delta\phi)(e_1) = \phi(v_2) - \phi(v_1) = 0 - 3 = -3,
   \qquad
   (\delta\phi)(e_2) = \phi(v_0) - \phi(v_2) = 1 - 0 = 1.
   $$
   Cộng 3 giá trị vòng quanh tam giác: $$2 + (-3) + 1 = 0$$! Điều này không phải ngẫu nhiên: **mọi $$1$$-đối biên $$\delta\phi$$ đều có tổng giá trị dọc theo vòng khép kín bằng $$0$$** (chính là phiên bản rời rạc của tích phân trường bảo toàn $$\oint \nabla\phi \cdot dr = 0$$!).

2. **Xét một $$1$$-đối xích không phải đối biên:** Chọn $$\alpha(e_0) = 1,\; \alpha(e_1) = 0,\; \alpha(e_2) = 0$$. Vì không có $$2$$-đơn hình nào nên $$\delta\alpha = 0$$ ($$\alpha$$ là đối chu trình). Nhưng tổng của $$\alpha$$ quanh vòng tròn là $$1 + 0 + 0 = 1 \neq 0$$, nên $$\alpha$$ **không thể** viết dưới dạng $$\delta\phi$$! Vậy $$[\alpha]$$ sinh ra lớp khác không trong $$H^1(S^1; \mathbb{Z}) \cong \mathbb{Z}$$.

### Ví dụ 2: Dùng tích cup phân biệt $$\mathbb{C}P^2$$ và $$S^2 \vee S^4$$ trong 2 dòng
Cả $$X = \mathbb{C}P^2$$ và $$Y = S^2 \vee S^4$$ đều có nhóm đối đồng điều giống hệt nhau:
$$
H^0 \cong \mathbb{Z},\quad H^1 = 0,\quad H^2 \cong \mathbb{Z},\quad H^3 = 0,\quad H^4 \cong \mathbb{Z}.
$$
Hãy kiểm tra bình phương tích cup của phần tử sinh $$a \in H^2$$:
- Trong $$\mathbb{C}P^2$$, hai đường thẳng xạ ảnh $$\mathbb{C}P^1 \cong S^2$$ cắt nhau tại đúng **1 điểm**, phản ánh qua tích cup là $$a \cup a = b \neq 0$$ (sinh ra toàn bộ $$H^4(\mathbb{C}P^2) \cong \mathbb{Z}$$). Do đó $$H^*(\mathbb{C}P^2; \mathbb{Z}) \cong \mathbb{Z}[a]/(a^3)$$.
- Trong $$S^2 \vee S^4$$, lớp $$a \in H^2$$ hoàn toàn sống trên thành phần $$S^2$$ (không chạm gì vào $$S^4$$); vì $$H^4(S^2) = 0$$ nên phép kéo ngược ép $$a \cup a = 0$$!
- Hai vành $$H^*(\mathbb{C}P^2)$$ và $$H^*(S^2 \vee S^4)$$ **không đẳng cấu** $$\implies \mathbb{C}P^2 \not\simeq S^2 \vee S^4$$!

### Giải thích: Vì sao lấy đối ngẫu lại sinh ra cấu trúc vành?

#### Bước 1: Chuyển từ "vẽ hình" sang "đo hàm trên hình"
Đồng điều $$H_n(X)$$ làm việc trực tiếp với các tổ hợp đơn hình. Khi lấy đối ngẫu $$C^n(X; G) = \operatorname{Hom}(C_n(X), G)$$, ta biến mỗi đơn hình thành "đầu vào" của một phép đo. Toán tử đối biên $$(\delta\phi)(c) = \phi(\partial c)$$ tự động kế thừa $$\delta^2 = 0$$ từ $$\partial^2 = 0$$.

#### Bước 2: Biến phép chiếu chéo thành phép nhân tích cup
Một điểm kỳ diệu của không gian tô-pô là luôn có **ánh xạ đường chéo** $$\Delta: X \to X \times X,\; x \mapsto (x, x)$$. Trên đối đồng điều phản biến, $$\Delta^*$$ đi theo chiều thuận từ $$H^p(X) \otimes H^q(X) \to H^{p+q}(X \times X) \xrightarrow{\Delta^*} H^{p+q}(X)$$ — chính là **tích cup $$\alpha \cup \beta$$**! (Trong đồng điều hiệp biến, mũi tên đi ngược chiều nên chỉ cho phép "tách" chứ không cho phép "nhân"!)

#### Bước 3: Kiểm chứng qua Định lý Hệ số Phổ quát (UCT)
Nếu bạn chỉ nhìn vào *từng nhóm riêng lẻ*, UCT cho thấy $$H^n(X; \mathbb{Z})$$ được xác định gần như hoàn toàn từ $$H_n(X)$$ và phần xoắn của $$H_{n-1}(X)$$ (chuyển dịch bậc của phần xoắn lên 1 nấc). Sức mạnh vượt trội thực sự của đối đồng điều nằm ở **cấu trúc vành $$\cup$$** và **tính tự nhiên của $$f^*$$**.

#### Bước 4: Hợp nhất với giải tích và hình học
Trên đa tạp trơn, đối đồng điều đơn hình/kỳ dị trùng khớp với **đối đồng điều de Rham** ($$\delta$$ trở thành vi phân ngoài $$d$$, tích cup trở thành tích ngoài $$\wedge$$ của dạng vi phân!), và Đối ngẫu Poincaré nối trực tiếp tích cup với **số giao điểm** của các đa tạp con.

$$
\text{Phức xích }(C_n, \partial)
\;\xrightarrow{\;\operatorname{Hom}(-, G)\;}\;
\text{Phức đối xích }(C^n, \delta)
\;\xrightarrow{\;\Delta^*\text{ (tích cup)}\;}\;
\text{Vành phân bậc }H^*(X)
\;\xrightarrow{\;\text{Poincaré}\;}\;
\text{Số giao \& dạng vi phân}.
$$

---

## 🔗 Đối xích và Toán tử đối biên

### 1. Nhóm đối xích

Xuất phát từ phức xích $C_n(X)$ với toán tử biên $\partial: C_n \to C_{n-1}$, ta lấy đối ngẫu bằng cách cố định một nhóm Abel hệ số $G$ (thường chọn $G = \mathbb{Z}$).

<div class="textbook-definition" markdown="1">
**Định nghĩa (Nhóm đối xích):**

$$
C^n(X; G) = \text{Hom}(C_n(X), G)
$$
</div>

Mỗi phần tử $\phi \in C^n(X; G)$, gọi là một **$n$-đối xích** ($n$-cochain), là một đồng cấu nhóm $\phi: C_n(X) \to G$.

Về mặt trực giác, nếu các xích là các đối tượng hình học (tổ hợp hình thức các đơn hình) thì các đối xích là các hàm gán giá trị thuộc $G$ cho từng đơn hình. Chẳng hạn, một $1$-xích là tổng hình thức của các cạnh, còn một $1$-đối xích là hàm gán một phần tử của $G$ cho mỗi cạnh.

---

### 2. Toán tử đối biên

<div class="textbook-definition" markdown="1">
**Định nghĩa (Toán tử đối biên):**  
Toán tử biên $\partial: C_{n+1} \to C_n$ cảm sinh **toán tử đối biên** (coboundary operator) $\delta: C^n \to C^{n+1}$, xác định với mọi $\phi \in C^n$ và $c \in C_{n+1}$ bởi:

$$
(\delta \phi)(c) = \phi(\partial c), \quad c \in C_{n+1}
$$
</div>

Nói cách khác, $\delta\phi = \phi \circ \partial$ là phép hợp trước với toán tử biên, đẩy số chiều của đối xích tăng thêm $1$:

```
C_{n+1} --∂--> C_n
   |           |
   ↓           ↓
   G <--δφ--- G
```

---

### 3. Tính chất cốt lõi: $\delta^2 = 0$

<div class="textbook-theorem" markdown="1">
**Định lý:** $\delta^{n+1} \circ \delta^n = 0$.
</div>

**Chứng minh:** Với mọi $\phi \in C^n$ và $c \in C_{n+2}$, ta có:
$$(\delta^2\phi)(c) = (\delta\phi)(\partial c) = \phi(\partial^2 c) = \phi(0) = 0$$
kết quả suy trực tiếp từ tính chất $\partial^2 = 0$ của toán tử biên. ✓

---

### 4. Phức đối xích

Dãy các nhóm đối xích và toán tử đối biên lập thành **phức đối xích** (cochain complex), với các mũi tên tăng dần theo chiều:

$$
0 \to C^0(X) \xrightarrow{\delta^0} C^1(X) \xrightarrow{\delta^1} C^2(X) \to \cdots
$$

- **Đối chu trình (cocycles):** $Z^n = \ker(\delta^n)$ (các đối xích thỏa mãn $\delta\phi = 0$).
- **Đối biên (coboundaries):** $B^n = \text{im}(\delta^{n-1})$ (các đối xích có dạng $\delta\psi$).

<div class="textbook-lemma" markdown="1">
**Bổ đề:** $B^n \subseteq Z^n$ (suy trực tiếp từ $\delta^2 = 0$).
</div>

---

## 📊 Nhóm đối đồng điều

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa (Nhóm đối đồng điều):**

$$
H^n(X; G) = \frac{Z^n(X; G)}{B^n(X; G)} = \frac{\ker(\delta^n)}{\text{im}(\delta^{n-1})}
$$
</div>

$H^n(X; G)$ là nhóm thương của các đối chu trình theo các đối biên, có cấu trúc đại số tương tự như đồng điều.

---

### 2. Tính chất

- **Tính Abel:** $H^n(X; G)$ luôn là nhóm Abel.
- **Tính hàm tử phản biến (contravariant):** Mỗi ánh xạ liên tục $f: X \to Y$ cảm sinh đồng cấu theo chiều ngược lại:

$$
f^* : H^n(Y) \to H^n(X)
$$

Cách xây dựng: với mỗi đối xích $\phi: C_n(Y) \to G$, đặt $f^\#(\phi) = \phi \circ f_\#$ (hợp với ánh xạ xích $f_\#: C_n(X) \to C_n(Y)$). Ánh xạ cảm sinh $f^*$ trên đối đồng điều thỏa mãn:
- $(f \circ g)^* = g^* \circ f^*$,
- $\text{id}^* = \text{id}$.

Đây là hành vi hàm tử ngược chiều so với đồng điều.

---

### 3. Bất biến đồng luân

<div class="textbook-theorem" markdown="1">
**Định lý:** Nếu $X \simeq Y$ thì $H^n(X) \cong H^n(Y)$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Đối ngẫu hóa phép đồng luân xích từ chứng minh bất biến đồng luân của đồng điều. ✓
</div>

---

## ⭐ Tích cup

### 1. Định nghĩa

Điểm khác biệt lớn nhất của đối đồng điều là sự tồn tại của phép nhân gọi là **tích cup** (cup product), khi hệ số lấy trong một vành $R$ (như $\mathbb{Z}$ hoặc $\mathbb{Z}/2\mathbb{Z}$).

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tích cup):**

$$
\cup : H^p(X) \times H^q(X) \to H^{p+q}(X)
$$

là một phép toán song tuyến tính và kết hợp trên đối đồng điều.
</div>

**Phác thảo xây dựng:** Với $\phi \in C^p(X)$ và $\psi \in C^q(X)$, định nghĩa đối xích $\phi \cup \psi \in C^{p+q}(X)$ trên mỗi $(p+q)$-đơn hình kỳ dị $\sigma$ bằng cách tính $\phi$ trên mặt trước $[v_0, \ldots, v_p]$, tính $\psi$ trên mặt sau $[v_p, \ldots, v_{p+q}]$ rồi nhân hai giá trị lại:

$$
(\phi \cup \psi)(\sigma) = \phi(\sigma|_{[v_0, \ldots, v_p]}) \cdot \psi(\sigma|_{[v_p, \ldots, v_{p+q}]})
$$

Nếu $\phi, \psi$ là đối chu trình thì $\phi \cup \psi$ cũng là đối chu trình; hơn nữa tích của một đối chu trình với một đối biên là một đối biên. Do đó phép nhân cảm sinh tích cup xác định tốt trên đối đồng điều: $[\phi] \cup [\psi] = [\phi \cup \psi] \in H^{p+q}(X)$.

---

### 2. Tính chất

- **Song tuyến tính:** $(\alpha_1 + \alpha_2) \cup \beta = \alpha_1 \cup \beta + \alpha_2 \cup \beta$.
- **Kết hợp:** $(\alpha \cup \beta) \cup \gamma = \alpha \cup (\beta \cup \gamma)$.
- **Đơn vị:** Phần tử $1 \in H^0(X)$ là đơn vị: $1 \cup \alpha = \alpha \cup 1 = \alpha$.
- **Giao hoán phân bậc (graded commutativity):** Với $\alpha \in H^p(X)$ và $\beta \in H^q(X)$,

$$
\alpha \cup \beta = (-1)^{pq} \beta \cup \alpha
$$

---

### 3. Cấu trúc vành

<div class="textbook-definition" markdown="1">
**Định nghĩa (Vành đối đồng điều):**

$$
H^*(X) = \bigoplus_{n=0}^\infty H^n(X)
$$

cùng với tích cup $\cup$ lập thành **vành đối đồng điều** (cohomology ring), là một vành giao hoán phân bậc.
</div>

Chẳng hạn, với mặt cầu $S^2$, ta có $H^*(S^2) \cong \mathbb{Z}[\alpha]/(\alpha^2)$ với $\alpha \in H^2(S^2)$ — một vành đa thức bị cắt cụt.

---

## 🔄 Định lý Hệ số Phổ quát

### 1. Phát biểu

<div class="textbook-theorem" markdown="1">
**Định lý (Hệ số Phổ quát cho đối đồng điều):**  
Với mọi không gian $X$ và nhóm Abel $G$, tồn tại đẳng cấu (không tự nhiên):

$$
H^n(X; G) \cong \text{Hom}(H_n(X), G) \oplus \text{Ext}(H_{n-1}(X), G)
$$
</div>

Trong công thức trên, $\text{Hom}(A, G)$ là nhóm các đồng cấu từ $A$ vào $G$, còn $\text{Ext}(A, G)$ là nhóm mở rộng đo lường ảnh hưởng từ phần xoắn của $H_{n-1}(X)$.

**Trường hợp riêng:** Nếu $H_{n-1}(X)$ là nhóm tự do (không có phần xoắn) thì $\text{Ext}(H_{n-1}(X), G) = 0$, nên $H^n(X; G) \cong \text{Hom}(H_n(X), G)$. Đặc biệt, khi $H_n(X)$ hữu hạn sinh tự do thì:

$$
H^n(X; G) \cong \text{Hom}(H_n(X), G) \cong H_n(X) \otimes G
$$

và với $G = \mathbb{Z}$, ta có $H^n(X; \mathbb{Z}) \cong H_n(X)$.

---

### 2. Ví dụ

**$X = S^2$:** Vì $H_2(S^2) = \mathbb{Z}$ và $H_1(S^2) = 0$ đều tự do, ta có:

$$
H^2(S^2; \mathbb{Z}) \cong \text{Hom}(\mathbb{Z}, \mathbb{Z}) \oplus \text{Ext}(0, \mathbb{Z}) \cong \mathbb{Z}
$$

tức là $H^2(S^2) \cong H_2(S^2) \cong \mathbb{Z}$. ✓

**$X = \mathbb{R}P^2$:** Ta đã biết $H_0(\mathbb{R}P^2) = \mathbb{Z}$, $H_1(\mathbb{R}P^2) = \mathbb{Z}/2\mathbb{Z}$ và $H_2(\mathbb{R}P^2) = 0$. Áp dụng định lý ở bậc $1$:

$$
H^1(\mathbb{RP}^2; \mathbb{Z}) \cong \text{Hom}(\mathbb{Z}/2\mathbb{Z}, \mathbb{Z}) \oplus \text{Ext}(H_0, \mathbb{Z})
$$

$$
\cong 0 \oplus 0 = 0
$$

trong khi $H_1(\mathbb{R}P^2) = \mathbb{Z}/2\mathbb{Z} \neq 0$. Ở bậc $2$, phần xoắn của $H_1$ lại xuất hiện qua hạng tử $\text{Ext}$: $H^2(\mathbb{R}P^2; \mathbb{Z}) \cong \text{Hom}(0, \mathbb{Z}) \oplus \text{Ext}(\mathbb{Z}/2\mathbb{Z}, \mathbb{Z}) \cong \mathbb{Z}/2\mathbb{Z}$. Như vậy, phần xoắn làm cho $H^n$ và $H_n$ khác nhau (dịch lên một bậc trong đối đồng điều).

---

## 🧮 Ví dụ và Tính toán

### Ví dụ 1: Một điểm

Với $X = \{\text{pt}\}$, ta có $H_0(\text{pt}) = \mathbb{Z}$ và $H_n(\text{pt}) = 0$ ($n > 0$). Theo Định lý Hệ số Phổ quát:

$$
H^n(\text{pt}) \cong H_n(\text{pt}) \cong \begin{cases}
\mathbb{Z} & n = 0 \\
0 & n > 0
\end{cases}
$$

Vành đối đồng điều là $H^*(\text{pt}) = \mathbb{Z}$ với phép nhân tầm thường.

---

### Ví dụ 2: Mặt cầu $S^n$

Với $n \geq 1$, $H_k(S^n) = \mathbb{Z}$ khi $k = 0, n$ và bằng $0$ ở các bậc khác. Theo Định lý Hệ số Phổ quát:

$$
H^k(S^n) \cong \begin{cases}
\mathbb{Z} & k = 0, n \\
0 & \text{otherwise}
\end{cases}
$$

Vành đối đồng điều là:

$$
H^*(S^n) \cong \mathbb{Z}[x]/(x^2), \quad x \in H^n(S^n)
$$

trong đó $x^2 = 0$ (với $n$ lẻ điều này cũng suy ra từ tính giao hoán phân bậc; với mọi $n \geq 1$, $H^{2n}(S^n) = 0$ nên $x^2 = 0$).

---

### Ví dụ 3: Hình xuyến $T^2$

Vì $H_*(T^2) = (\mathbb{Z}, \mathbb{Z}^2, \mathbb{Z})$ không có phần xoắn, ta có $H^*(T^2) = (\mathbb{Z}, \mathbb{Z}^2, \mathbb{Z})$ ở các bậc $0, 1, 2$.

Gọi $a, b \in H^1(T^2)$ là hai phần tử sinh của $H^1(T^2)$ và $1 \in H^0(T^2)$. Do $a, b$ có bậc lẻ, tính giao hoán phân bậc cho $a \cup a = 0$, $b \cup b = 0$ và $a \cup b = -b \cup a$, trong đó $a \cup b$ sinh $H^2(T^2) \cong \mathbb{Z}$. Vì vậy $H^*(T^2)$ đẳng cấu với đại số ngoài (exterior algebra) trên hai phần tử sinh $a, b$:

$$
H^*(T^2) \cong \Lambda_{\mathbb{Z}}(a, b)
$$

---

### Ví dụ 4: Mặt phẳng xạ ảnh $\mathbb{R}P^2$

Với $H_*(\mathbb{R}P^2) = (\mathbb{Z}, \mathbb{Z}/2\mathbb{Z}, 0)$, áp dụng Định lý Hệ số Phổ quát với hệ số $\mathbb{Z}$ cho:

$$
H^0(\mathbb{RP}^2; \mathbb{Z}) = \mathbb{Z}, \quad H^1(\mathbb{RP}^2; \mathbb{Z}) = 0, \quad H^2(\mathbb{RP}^2; \mathbb{Z}) = \mathbb{Z}/2\mathbb{Z}
$$

(phần xoắn $\mathbb{Z}/2\mathbb{Z}$ từ $H_1$ dịch chuyển lên $H^2$ thông qua $\text{Ext}$).

Khi chuyển sang hệ số $\mathbb{Z}/2\mathbb{Z}$, cấu trúc vành thể hiện rõ ràng hơn:

$$
H^*(\mathbb{RP}^2; \mathbb{Z}/2\mathbb{Z}) = (\mathbb{Z}/2\mathbb{Z})[x]/(x^3), \quad x \in H^1
$$

Tích cup $x \cup x = x^2 \neq 0$ sinh $H^2(\mathbb{R}P^2; \mathbb{Z}/2\mathbb{Z}) \cong \mathbb{Z}/2\mathbb{Z}$, phản ánh tính không định hướng được của $\mathbb{R}P^2$.

---

## 🧠 Đối ngẫu Poincaré

### 1. Phát biểu

<div class="textbook-theorem" markdown="1">
**Định lý (Đối ngẫu Poincaré):**  
Nếu $M$ là một $n$-đa tạp compact, định hướng được và không có biên, thì với mọi $k$:

$$
H^k(M; \mathbb{Z}) \cong H_{n-k}(M; \mathbb{Z})
$$
</div>

Đẳng cấu đối ngẫu Poincaré $PD: H^k(M) \xrightarrow{\cong} H_{n-k}(M)$ liên kết đối đồng điều ở bậc thấp với đồng điều ở bậc bù $n - k$. Về mặt trực giác hình học, một $k$-chu trình trong $M$ ứng với một $(n-k)$-chu trình đối ngẫu có thể hình dung như "phần bù trực giao", và tích cup trong đối đồng điều tương ứng với phép giao (intersection pairing) của các chu trình.

---

### 2. Ví dụ: Mặt cầu $S^n$

Với $H^k(S^n) \cong H_{n-k}(S^n)$:
- $k = 0$: $H^0 = \mathbb{Z} \leftrightarrow H_n = \mathbb{Z}$ ✓
- $k = n$: $H^n = \mathbb{Z} \leftrightarrow H_0 = \mathbb{Z}$ ✓
- Các bậc khác: $0 \leftrightarrow 0$ ✓

---

### 3. Ví dụ: Hình xuyến $T^2$

Với $n = 2$:
- $H^0(T^2) = \mathbb{Z} \leftrightarrow H_2(T^2) = \mathbb{Z}$ ✓
- $H^1(T^2) = \mathbb{Z}^2 \leftrightarrow H_1(T^2) = \mathbb{Z}^2$ ✓ (tự đối ngẫu)
- $H^2(T^2) = \mathbb{Z} \leftrightarrow H_0(T^2) = \mathbb{Z}$ ✓

---

### 4. Trường hợp không định hướng được

Với đa tạp không định hướng được như $\mathbb{R}P^2$, Đối ngẫu Poincaré không còn đúng với hệ số $\mathbb{Z}$, nhưng vẫn đúng khi lấy hệ số trong $\mathbb{Z}/2\mathbb{Z}$.

---

## 🧠 Tài liệu kinh điển & Tham khảo

### Công trình kinh điển

1. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Giới thiệu đối ngẫu và các số Betti*

2. **Eduard Čech** - *"Théorie générale de l'homologie"* (1932)  
   *Phát triển lý thuyết đối đồng điều*

3. **Samuel Eilenberg, Norman Steenrod** - *"Foundations"* (1952)  
   *Hệ tiên đề cho đối đồng điều*

### Giáo trình

4. **Allen Hatcher** - *Algebraic Topology*, **§3.1: Cohomology**

5. **Glen E. Bredon** - *Topology and Geometry*, **Chapter V**

6. **Raoul Bott, Loring W. Tu** - *Differential Forms in Algebraic Topology*

7. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapter 5**

---

## 🔗 Ứng dụng và Liên kết

### Các lớp đặc trưng (Characteristic Classes)
Các lớp Chern, Stiefel–Whitney và Pontryagin là các phần tử trong đối đồng điều của không gian cơ sở, dùng để phân loại bó vectơ và phát hiện các chướng ngại tô-pô.

### Lý thuyết chướng ngại (Obstruction Theory)
Đối đồng điều và tích cup phát hiện các chướng ngại khi mở rộng ánh xạ liên tục hoặc tìm lát cắt của bó.

### Hình học đại số
Đối đồng điều bó (Sheaf Cohomology) là công cụ nền tảng để tính các bất biến hình học của đa tạp đại số.

### Lý thuyết dây (String Theory)
Các trường nền như B-field và RR-field được mô tả bởi các lớp đối đồng điều, cho thấy cấu trúc tô-pô ảnh hưởng trực tiếp đến mô hình vật lý.

### Đối đồng điều de Rham
Trên đa tạp trơn $M$, định lý de Rham cho đẳng cấu $H^n_{\text{dR}}(M) \cong H^n(M; \mathbb{R})$, nối tô-pô đại số với giải tích vi phân qua các dạng vi phân.

---

## Video tham khảo

- **xem trước** [The derivative isn't what you think it is.](https://www.youtube.com/watch?v=2ptFnIj71SM) — Aleph 0, tiếng Anh. Vì sao đối đồng điều đếm lỗ bằng hàm và dạng, xem trước các định nghĩa đối xích.
- [Algebraic Topology 20: Introduction to Cohomology](https://www.youtube.com/watch?v=ol-AJVVbkMs) — Math at Andrews University, tiếng Anh. Đối đồng điều kỳ dị từ đầu, sau khi đã có trực giác từ video trên.
- [Algebraic Topology 21: Cup Product](https://www.youtube.com/watch?v=uenkIqOKjng) — Math at Andrews University, tiếng Anh. Tích cup, cấu trúc vành mà bài giới thiệu sau các nhóm đối đồng điều.

## 🧩 Bài tập

### Đối xích

1. **Đối ngẫu:** Nếu $C_n = \mathbb{Z}^3$ thì $C^n = \text{Hom}(C_n, \mathbb{Z})$ là nhóm nào?

2. **Toán tử đối biên:** Kiểm chứng $\delta^2 = 0$ trực tiếp từ $\partial^2 = 0$.

### Nhóm đối đồng điều

3. **Một điểm:** Kiểm chứng $H^0(\text{pt}) = \mathbb{Z}$ và $H^n(\text{pt}) = 0$ với $n > 0$.

4. **Không gian co rút được:** Nếu $X$ co rút được thì $H^n(X)$ bằng gì?

### Tính phản biến

5. **Ánh xạ cảm sinh:** Cho ánh xạ $f: S^1 \to S^1$ có bậc $2$. Hãy xác định đồng cấu $f^*: H^1(S^1) \to H^1(S^1)$.

6. **Ánh xạ hợp:** Kiểm chứng $(f \circ g)^* = g^* \circ f^*$.

### Tích cup

7. **Hình xuyến:** Kiểm chứng $a \cup b \neq 0$ nhưng $a \cup a = 0$ trong $H^*(T^2)$.

8. **Giao hoán phân bậc:** Với $\alpha \in H^1(X)$ và $\beta \in H^2(X)$, so sánh $\alpha \cup \beta$ và $\beta \cup \alpha$.

### Cấu trúc vành

9. **Mặt cầu:** Kiểm chứng $H^*(S^2) \cong \mathbb{Z}[x]/(x^2)$.

10. **Không gian tích:** Xác định cấu trúc vành của $H^*(S^1 \times S^1)$.

### Định lý Hệ số Phổ quát

11. **Áp dụng:** Cho $X$ liên thông đường với $H_1(X) = \mathbb{Z}/3\mathbb{Z}$. Tính $H^1(X; \mathbb{Z})$.

12. **Phần xoắn:** Giải thích vì sao $H^1(\mathbb{R}P^2; \mathbb{Z}) = 0$ dù $H_1(\mathbb{R}P^2) = \mathbb{Z}/2\mathbb{Z}$, và xác định $H^2(\mathbb{R}P^2; \mathbb{Z})$.

### Đối ngẫu Poincaré

13. **Kiểm chứng:** Kiểm tra Đối ngẫu Poincaré một cách tường minh cho $S^3$.

14. **Mặt đóng:** Với mặt định hướng giống $g$ ($\Sigma_g$), kiểm chứng $H^1(\Sigma_g) \cong H_1(\Sigma_g)$ qua đối ngẫu Poincaré.

### Nâng cao

15. **Hệ số $\mathbb{Z}/2\mathbb{Z}$ cho $\mathbb{R}P^2$:** Tính $H^*(\mathbb{R}P^2; \mathbb{Z}/2\mathbb{Z})$ và kiểm chứng cấu trúc vành của nó.

16. **Mặt phẳng xạ ảnh phức $\mathbb{C}P^2$:** Tìm hiểu vành đối đồng điều $H^*(\mathbb{C}P^2)$. (Đáp số: $\mathbb{Z}[x]/(x^3)$ với $x \in H^2$.)

### Câu hỏi suy ngẫm

17. **Vì sao cần đối đồng điều?** Liệt kê các ưu điểm của đối đồng điều so với đồng điều.

18. **Sức mạnh của cấu trúc vành:** Nêu một ví dụ hai không gian có cùng các nhóm đồng điều nhưng có vành đối đồng điều không đẳng cấu.

19. **Tính phản biến:** Giải thích trực giác vì sao các ánh xạ cảm sinh trong đối đồng điều lại đảo chiều.

20. **Ý nghĩa hình học của tích cup:** Tìm hiểu mối liên hệ giữa tích cup và lý thuyết giao (intersection theory).

---

## 📚 Đọc thêm

- **Hatcher, §3:** Trình bày đầy đủ về lý thuyết đối đồng điều.
- **Bott & Tu:** Góc nhìn qua dạng vi phân.
- **Bredon, Chapter V:** Các chủ đề nâng cao.
- **Milnor & Stasheff:** *Characteristic Classes*.

---

## 🎓 Tóm tắt

Đối đồng điều là lý thuyết đối ngẫu của đồng điều với cấu trúc đại số vành phong phú:

✅ **Đối xích $C^n$:** $\text{Hom}(C_n, G)$.  
✅ **Toán tử đối biên $\delta$:** $C^n \to C^{n+1}$, thỏa mãn $\delta^2 = 0$.  
✅ **Đối đồng điều $H^n$:** $\ker(\delta) / \text{im}(\delta)$.  
✅ **Tính phản biến:** $f: X \to Y$ cảm sinh $f^*: H^n(Y) \to H^n(X)$.  
✅ **Tích cup $\cup$:** Phép nhân $H^p \times H^q \to H^{p+q}$ tạo thành vành giao hoán phân bậc $H^*(X)$.  
✅ **Định lý Hệ số Phổ quát:** Liên hệ $H^n$ với $H_n$ thông qua $\text{Hom}$ và $\text{Ext}$.  
✅ **Đối ngẫu Poincaré:** $H^k(M) \cong H_{n-k}(M)$ trên các đa tạp đóng định hướng được (và với hệ số $\mathbb{Z}/2\mathbb{Z}$ trên đa tạp không định hướng được).

Với bài học này, ta đã hoàn thành Chương 07 gồm đồng điều đơn hình, đồng điều kỳ dị, các phương pháp tính toán (tế bào và Mayer–Vietoris) và đối đồng điều.

**Tiếp theo:** Chương 08 về **Các chủ đề nâng cao** — nhóm đồng luân bậc cao, phân thớ, lý thuyết Morse và đa tạp.

---

*"Cohomology: where duality becomes multiplication, and topology becomes algebra."*

---

**Previous:** [Lecture 07.03: Mayer-Vietoris](/contents/vi/topology-chapter07/07_03_Mayer_Vietoris/)  
**Next Chapter:** [Chapter 08: Advanced Topics](/contents/vi/topology-chapter08/)
