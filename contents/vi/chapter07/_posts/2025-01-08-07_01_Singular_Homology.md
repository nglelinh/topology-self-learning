---
layout: post
title: "Lecture 07.01: Singular Homology"
lang: vi
lang-ref: lecture-07-01
chapter: 7
lecture: 1
categories: [chapter07]
tags: [singular-homology, singular-simplices, functoriality]
description: "Singular homology: definition cho arbitrary spaces, functoriality, homotopy invariance - universal homology theory"
---

**Đồng điều cho mọi không gian — Tính hàm tử và Bất biến đồng luân**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Đồng điều đơn hình ở bài 07.00 cực kỳ dễ tính, nhưng lại vướng hai câu hỏi hóc búa: (1) *Nếu không gian $$X$$ không thể chia thành tam giác phẳng thì sao?* và (2) *Nếu hai người chia cùng một mặt cầu theo hai cách tam giác hóa khác hẳn nhau, ai bảo đảm hai cách tính cho ra cùng một nhóm $$H_n$$?* **Đồng điều Kỳ dị (Singular Homology)** giải quyết dứt điểm cả hai vấn đề bằng một cú xoay góc nhìn ngoạn mục: *thay vì cắt không gian $$X$$ thành tam giác, hãy giữ nguyên $$X$$ và xét **TẤT CẢ mọi ánh xạ liên tục** từ tam giác chuẩn $$\Delta^n$$ vào trong $$X$$!*

Đồng điều đơn hình trực quan và dễ tính toán nhưng có một hạn chế lớn:

> **Đòi hỏi phép chia tam giác (triangulation).**

Nhiều không gian tô-pô không có cấu trúc phức đơn hình, chẳng hạn các tập con tùy ý của $\mathbb{R}^n$, các không gian hàm, các không gian vô hạn chiều hay các không gian có cấu trúc bệnh lý ("wild").

**Đồng điều kỳ dị (singular homology)** khắc phục hạn chế này:

> **$H_n(X)$ được định nghĩa cho mọi không gian tô-pô $X$.**

Thay vì chia $X$ thành các đơn hình, ta xét **tất cả các ánh xạ liên tục** từ đơn hình chuẩn $\Delta^n$ vào $X$. Cách tiếp cận này có các ưu điểm chính sau:

- **Tính phổ quát:** Áp dụng được cho mọi không gian tô-pô mà không cần phép chia tam giác.
- **Tính hàm tử (functoriality):** Mọi ánh xạ liên tục $f: X \to Y$ đều cảm sinh một đồng cấu $f_*: H_n(X) \to H_n(Y)$.
- **Bất biến đồng luân (homotopy invariance):** Nếu $X \simeq Y$ thì $H_n(X) \cong H_n(Y)$.
- **Tương thích với đồng điều đơn hình:** Trên các phức đơn hình, đồng điều kỳ dị đẳng cấu với đồng điều đơn hình.
- **Tính chuẩn mực:** Là định nghĩa tiêu chuẩn dùng cho hầu hết các định lý lớn trong tô-pô đại số hiện đại và có thể tính toán thông qua phức CW.

![Singular simplices](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Singular_simplex.svg/400px-Singular_simplex.svg.png)  
*Các đơn hình kỳ dị ánh xạ vào không gian - Nguồn concept*

Trong bài học này, ta sẽ lần lượt tìm hiểu đơn hình chuẩn $\Delta^n$ và các ánh xạ mặt, đơn hình kỳ dị $\sigma: \Delta^n \to X$, nhóm xích kỳ dị $C_n(X)$, toán tử biên $\partial$, nhóm đồng điều kỳ dị $H_n(X)$, tính hàm tử và tính bất biến đồng luân.

---

## 🗺️ Bản đồ kiến thức nền: Đồng điều Kỳ dị là gì và tại sao nó là "bất biến tô-pô tự động"?

### 1. Từ "Cắt không gian" sang "Dò không gian bằng ánh xạ liên tục"
- **Bản chất:** Một **$$n$$-đơn hình kỳ dị** trong $$X$$ đơn giản là một ánh xạ liên tục bất kỳ $$\sigma: \Delta^n \to X$$ (có thể bóp méo, gấp nếp, thậm chí co cả tam giác về 1 điểm — vì thế mới gọi là *kỳ dị*!).
- **Tự động là bất biến tô-pô:** Vì định nghĩa chỉ dùng ánh xạ liên tục mà không hề nhắc tới phép tam giác hóa nào, mọi ánh xạ liên tục $$f: X \to Y$$ lập tức đẩy đơn hình $$\sigma$$ thành $$f \circ \sigma$$, cảm sinh đồng cấu $$f_*: H_n(X) \to H_n(Y)$$!

### 2. Bất biến Đồng luân & Định lý Tách Thành phần Liên thông đường
- **Bản chất:** Hai ánh xạ đồng luân $$f \simeq g$$ cảm sinh **cùng một** đồng cấu $$f_* = g_*$$ trên đồng điều kỳ dị (nhờ xây dựng toán tử lăng trụ $$P: C_n(X) \to C_{n+1}(Y)$$ thỏa mãn $$\partial P + P\partial = g_\# - f_\#$$!).
- **Bậc 0:** $$H_0(X) \cong \bigoplus_{\alpha} \mathbb{Z}$$ (số bản sao $$\mathbb{Z}$$ đúng bằng số thành phần liên thông đường của $$X$$!).

### 3. Cầu nối Hurewicz & Đẳng cấu với Đồng điều Đơn hình
- **Bản chất:** Dù nhóm xích kỳ dị $$C_n(X)$$ khổng lồ vô hạn chiều, trên mọi phức đơn hình/CW, đồng điều kỳ dị **đẳng cấu hoàn toàn** với đồng điều đơn hình — vừa có tính bất biến tô-pô tuyệt đối của kỳ dị, vừa có tốc độ tính toán gọn nhẹ của đơn hình! Và ở bậc 1, $$H_1(X)$$ chính là **Abel hóa của $$\pi_1(X)$$**!

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc: Tính trọn vẹn Đồng điều Kỳ dị của Không gian 1 điểm $$X = \{p\}$$

Với không gian chỉ gồm đúng 1 điểm $$X = \{p\}$$, ở mỗi bậc $$n \ge 0$$ chỉ có **duy nhất 1 ánh xạ liên tục** $$\sigma_n: \Delta^n \to \{p\}$$ (ánh xạ hằng đưa mọi điểm về $$p$$). Do đó $$C_n(\{p\}) = \mathbb{Z}\cdot \sigma_n \cong \mathbb{Z}$$ với mọi $$n \ge 0$$!

Bây giờ hãy tính tường minh toán tử biên $$\partial_n(\sigma_n) = \sum_{i=0}^n (-1)^i (\sigma_n |_{[v_0, \dots, \hat{v}_i, \dots, v_n]})$$. Vì mọi mặt của ánh xạ hằng vẫn là ánh xạ hằng $$\sigma_{n-1}$$, ta có:
$$
\partial_n(\sigma_n) = \sum_{i=0}^{n} (-1)^i \sigma_{n-1} = \bigl(1 - 1 + 1 - 1 + \cdots + (-1)^n\bigr)\sigma_{n-1} = \begin{cases} 0 & \text{nếu } n \text{ lẻ}, \\ \sigma_{n-1} & \text{nếu } n \text{ chẵn } (n \ge 2)! \end{cases}
$$
Viết ra toàn bộ phức xích kỳ dị của $$\{p\}$$:
$$
\cdots \xrightarrow{\;0\;} \mathbb{Z} \xrightarrow{\;\times 1\;} \mathbb{Z} \xrightarrow{\;0\;} \mathbb{Z} \xrightarrow{\;\times 1\;} \mathbb{Z} \xrightarrow{\;0\;} \mathbb{Z} \longrightarrow 0.
$$
Đọc ngay từng nhóm đồng điều bằng mắt thường:
- **Bậc $$n = 0$$:** $$\ker \partial_0 = \mathbb{Z}$$, $$\operatorname{im} \partial_1 = 0 \implies H_0(\{p\}) = \mathbb{Z}/0 \cong \mathbb{Z}$$!
- **Bậc $$n \ge 1$$ lẻ:** $$\ker \partial_n = \mathbb{Z}$$, $$\operatorname{im} \partial_{n+1} = \mathbb{Z} \implies H_n(\{p\}) = \mathbb{Z}/\mathbb{Z} = 0$$!
- **Bậc $$n \ge 2$$ chẵn:** $$\ker \partial_n = 0$$, $$\operatorname{im} \partial_{n+1} = 0 \implies H_n(\{p\}) = 0/0 = 0$$!

Nhờ bất biến đồng luân, kết quả này lập tức cho đồng điều của **mọi không gian co rút được** ($$\mathbb{R}^k, D^k$$): $$H_0 \cong \mathbb{Z}$$ và $$H_n = 0$$ với mọi $$n \ge 1$$!

### Khung giải thích: Tại sao không gian xích khổng lồ $$C_n(X)$$ lại trở nên dễ chế ngự? (nên đọc chậm)

#### Bước 1: Chấp nhận $$C_n(X)$$ vô hạn chiều để đổi lấy tính tự nhiên tuyệt đối
Không cần chọn tam giác hóa, không cần lo tính độc lập cách chia lưới: $$H_n$$ tự động là một hàm tử từ $$\mathbf{Top}$$ sang $$\mathbf{Ab}$$ ngay từ định nghĩa!

#### Bước 2: Dùng Phép đồng luân xích (Chain Homotopy) để chứng minh bất biến đồng luân
Hai ánh xạ đồng luân $$f \simeq g$$ tạo ra một lăng trụ $$\Delta^n \times [0,1]$$; xẻ lăng trụ thành $$n+1$$ đơn hình chiều $$n+1$$ cho ta toán tử $$P$$ thỏa mãn $$\partial P + P\partial = g_\# - f_\#$$, lập tức ép $$f_* = g_*$$ trên $$H_n$$!

#### Bước 3: Mở rộng lên Đồng điều Tương đối $$H_n(X, A)$$ và Dãy khớp dài của cặp $$(X, A)$$
Lấy thương $$C_n(X)/C_n(A)$$ tạo ra đồng điều tương đối $$H_n(X, A)$$ cùng dãy khớp dài nối $$H_n(A) \to H_n(X) \to H_n(X, A) \to H_{n-1}(A)$$ — và **Định lý Cắt bỏ (Excision)** cho phép cắt vứt phần ruột thừa bên trong $$A$$ mà không đổi $$H_n(X, A)$$!

#### Bước 4: Đứng trên hệ tiên đề Eilenberg–Steenrod
Một khi có đủ tính hàm tử, bất biến đồng luân, dãy khớp dài và cắt bỏ (cùng Mayer–Vietoris ở bài 07.03), bạn hiếm khi phải động trực tiếp vào từng đơn hình kỳ dị nữa — mọi tính toán quy về đại số tinh gọn!

$$
\sigma: \Delta^n \to X
\;\xrightarrow{\;\partial_n\;}\;
H_n^{\text{sing}}(X)
\;\xrightarrow{\;\text{Đồng luân + Cắt bỏ}\;}\;
H_n^{\text{sing}}(K) \cong H_n^{\text{simp}}(K) \;\&\; H_1(X) \cong \pi_1(X)^{\text{ab}}.
$$

---

## 🔺 Đơn hình chuẩn

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa ($n$-đơn hình chuẩn):**

$$
\Delta^n = \left\{(t_0, \ldots, t_n) \in \mathbb{R}^{n+1} : t_i \geq 0, \sum_{i=0}^n t_i = 1\right\}
$$
</div>

Các **đỉnh** của $\Delta^n$ là các vectơ cơ sở chuẩn:
- $e_0 = (1, 0, \ldots, 0)$,
- $e_1 = (0, 1, 0, \ldots, 0)$,
- $\ldots$
- $e_n = (0, \ldots, 0, 1)$.

Bộ số $(t_0, \ldots, t_n)$ được gọi là **tọa độ trọng tâm** (barycentric coordinates), biểu diễn mỗi điểm của $\Delta^n$ như một tổ hợp lồi của các đỉnh.

**Các ví dụ:**
- **$\Delta^0$:** Một điểm duy nhất $\{(1)\} \subset \mathbb{R}^1$.
- **$\Delta^1$:** Đoạn thẳng $\{(t, 1-t) : t \in [0,1]\} \subset \mathbb{R}^2$ nối $e_0 = (1,0)$ và $e_1 = (0,1)$, đồng phôi với $[0,1]$.
- **$\Delta^2$:** Tam giác $\{(t_0,t_1,t_2) : t_i \geq 0, \sum t_i = 1\} \subset \mathbb{R}^3$ với các đỉnh $(1,0,0), (0,1,0), (0,0,1)$.
- **$\Delta^3$:** Tứ diện trong $\mathbb{R}^4$ với 4 đỉnh là các vectơ đơn vị.

---

### 2. Ánh xạ mặt

<div class="textbook-definition" markdown="1">
**Định nghĩa (Ánh xạ mặt thứ $i$):**

$$
\delta_i : \Delta^{n-1} \to \Delta^n
$$

được xác định bằng cách chèn số $0$ vào vị trí thứ $i$:

$$
\delta_i(t_0, \ldots, t_{n-1}) = (t_0, \ldots, t_{i-1}, 0, t_i, \ldots, t_{n-1})
$$
</div>

Về mặt hình học, $\delta_i$ nhúng $(n-1)$-đơn hình chuẩn vào mặt thứ $i$ của $\Delta^n$, tức là mặt đối diện với đỉnh $e_i$.

**Ví dụ ($n=2$):** Ba ánh xạ mặt $\Delta^1 \to \Delta^2$ tương ứng với ba cạnh của tam giác:
- $\delta_0$: $(t, 1-t) \mapsto (0, t, 1-t)$ (cạnh đối diện $e_0$);
- $\delta_1$: $(t, 1-t) \mapsto (t, 0, 1-t)$ (cạnh đối diện $e_1$);
- $\delta_2$: $(t, 1-t) \mapsto (t, 1-t, 0)$ (cạnh đối diện $e_2$).

---

### 3. Ánh xạ suy biến

Các **ánh xạ suy biến** (degeneracy maps) $s_i: \Delta^n \to \Delta^{n-1}$ co một cạnh lại và được sử dụng trong lý thuyết tập đơn hình (simplicial sets), nhưng không cần dùng đến khi xây dựng đồng điều kỳ dị cơ bản.

---

## 🔗 Đơn hình kỳ dị

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa ($n$-đơn hình kỳ dị):**  
Một **$n$-đơn hình kỳ dị** (singular $n$-simplex) trong không gian $X$ là một ánh xạ liên tục bất kỳ:

$$
\sigma : \Delta^n \to X
$$
</div>

Ánh xạ $\sigma$ không cần phải là phép nhúng hay đơn ánh; chỉ cần liên tục. Ta có thể hình dung $\sigma$ như cách "bọc" hoặc ánh xạ khuôn mẫu $\Delta^n$ vào không gian $X$.

**Các ví dụ:**

Với $X = S^1$, ta có vô số đơn hình kỳ dị, chẳng hạn:
- **Ánh xạ hằng:** Đưa toàn bộ $\Delta^n$ về một điểm duy nhất.
- **Quấn một vòng:** $\sigma: \Delta^1 \to S^1$ đi đúng một vòng quanh đường tròn.
- **Quấn hai vòng:** $\sigma$ đi hai vòng quanh đường tròn.
- **Đi ngược chiều:** $\sigma$ đi theo chiều kim đồng hồ.

Với $X = \mathbb{R}^n$, mọi đơn hình hình học $[v_0, \ldots, v_n] \subseteq \mathbb{R}^n$ đều xác định một đơn hình kỳ dị thông qua ánh xạ affine $\sigma(t_0, \ldots, t_n) = \sum t_i v_i$. Theo nghĩa này, đồng điều kỳ dị bao hàm cấu trúc của phức đơn hình như một trường hợp riêng.

---

### 2. So sánh đơn hình hình học và đơn hình kỳ dị

- **Đơn hình hình học (đồng điều đơn hình):** Là các tập con thực sự của $X$; đòi hỏi $X$ là phức đơn hình; có số lượng hữu hạn nếu phức là hữu hạn.
- **Đơn hình kỳ dị:** Là các ánh xạ liên tục $\Delta^n \to X$; áp dụng cho mọi không gian $X$; thường có vô số đơn hình kỳ dị ngay cả với các không gian đơn giản.

Dù có vô số đơn hình kỳ dị, mỗi xích chỉ là một tổng hữu hạn các đơn hình, và cấu trúc đại số thương $Z_n/B_n$ vẫn cho ra các nhóm đồng điều gọn gàng.

---

## 🔗 Phức xích kỳ dị

### 1. Nhóm xích kỳ dị

<div class="textbook-definition" markdown="1">
**Định nghĩa (Nhóm xích kỳ dị):**

$$
C_n(X) = \text{free abelian group on singular } n\text{-simplices in } X
$$
</div>

Mỗi phần tử của $C_n(X)$ là một tổng hình thức **hữu hạn** với hệ số nguyên:

$$
c = \sum_{i=1}^k m_i \sigma_i, \quad m_i \in \mathbb{Z}, \sigma_i : \Delta^n \to X
$$

Các tính chất cơ bản của $C_n(X)$:
- **Nhóm Abel tự do:** Toàn bộ các $n$-đơn hình kỳ dị tạo thành một cơ sở không có quan hệ ràng buộc nào giữa chúng.
- **Tính hàm tử:** Mỗi ánh xạ liên tục $f: X \to Y$ cảm sinh đồng cấu $C_n(f): C_n(X) \to C_n(Y)$.
- **Kích thước lớn:** Thường có vô số phần tử sinh, nhưng mọi phép tính vẫn thực hiện trên các tổng hữu hạn.

---

### 2. Toán tử biên

<div class="textbook-definition" markdown="1">
**Định nghĩa (Toán tử biên):**  
Cho $n$-đơn hình kỳ dị $\sigma: \Delta^n \to X$. Mặt thứ $i$ của $\sigma$ là ánh xạ hợp $\sigma \circ \delta_i: \Delta^{n-1} \to \Delta^n \to X$. Khi đó, biên của $\sigma$ được định nghĩa là tổng đan dấu các mặt:

$$
\partial_n \sigma = \sum_{i=0}^n (-1)^i (\sigma \circ \delta_i)
$$
</div>

Ta mở rộng tuyến tính lên toàn bộ $C_n(X)$ bởi $\partial(\sum m_i \sigma_i) = \sum m_i \partial\sigma_i$, nhờ đó $\partial_n: C_n(X) \to C_{n-1}(X)$ là một đồng cấu nhóm.

**Ví dụ ($n=1$):** Với $\sigma: \Delta^1 \to X$, ta có:

$$
\partial \sigma = \sigma \circ \delta_0 - \sigma \circ \delta_1
$$

Do $\Delta^0 = \{(1)\}$, ánh xạ mặt $\delta_0(1) = (0,1) = e_1$ (bỏ đỉnh $e_0$) và $\delta_1(1) = (1,0) = e_0$ (bỏ đỉnh $e_1$), nên:

$$
\partial \sigma = \sigma(e_1) - \sigma(e_0)
$$

Biên của một $1$-đơn hình kỳ dị (một đường đi) chính là hiệu giữa điểm cuối và điểm đầu, giống hệt trường hợp cạnh trong đồng điều đơn hình.

---

### 3. Tính chất cốt lõi: $\partial^2 = 0$

<div class="textbook-theorem" markdown="1">
**Định lý:** $\partial_{n-1} \circ \partial_n = 0$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Các ánh xạ mặt thỏa mãn đồng nhất thức:

$$
\delta_i \circ \delta_j = \delta_{j+1} \circ \delta_i \quad (i \leq j)
$$

Khi khai triển $\partial(\partial\sigma)$, mỗi ánh xạ hợp xuất hiện đúng hai lần với dấu trái nhau nên triệt tiêu hoàn toàn, suy ra $\partial^2 = 0$. ✓
</div>

Như vậy, đồng điều kỳ dị có cùng cấu trúc đại số cơ bản như đồng điều đơn hình.

---

## 📊 Nhóm đồng điều kỳ dị

### 1. Định nghĩa

Từ phức xích kỳ dị:

$$
\cdots \to C_n(X) \xrightarrow{\partial_n} C_{n-1}(X) \to \cdots \to C_0(X) \to 0
$$

ta định nghĩa nhóm chu trình $Z_n(X) = \ker(\partial_n)$, nhóm biên $B_n(X) = \text{im}(\partial_{n+1})$, và **nhóm đồng điều kỳ dị bậc $n$**:

$$
H_n(X) = \frac{Z_n(X)}{B_n(X)}
$$

Các tính chất cơ bản:
1. **Nhóm Abel:** $H_n(X)$ luôn là nhóm Abel.
2. **Bất biến đồng luân:** $X \simeq Y \Rightarrow H_n(X) \cong H_n(Y)$.
3. **Tính hàm tử:** $f: X \to Y$ cảm sinh $f_*: H_n(X) \to H_n(Y)$.
4. **Tiên đề chiều:** $H_0(\text{point}) = \mathbb{Z}$ và $H_n(\text{point}) = 0$ với $n > 0$.

---

### 2. Tính hàm tử

<div class="textbook-theorem" markdown="1">
**Định lý (Tính hàm tử):**  
Mỗi ánh xạ liên tục $f: X \to Y$ cảm sinh một đồng cấu nhóm:

$$
f_* : H_n(X) \to H_n(Y)
$$
</div>

**Cách xây dựng:** Với mỗi đơn hình kỳ dị $\sigma: \Delta^n \to X$, ta lập ánh xạ hợp $f \circ \sigma: \Delta^n \to Y$ và mở rộng tuyến tính thành ánh xạ xích $C_n(f)(\sigma) = f \circ \sigma$. Vì toán tử biên giao hoán với phép hợp ánh xạ, $\partial(f \circ \sigma) = f \circ (\partial\sigma)$, nên $C_n(f)$ đưa chu trình về chu trình và biên về biên. Nhờ đó, ánh xạ cảm sinh trên đồng điều $f_*[c] = [f(c)]$ được xác định tốt và thỏa mãn:
- $(f \circ g)_* = f_* \circ g_*$;
- $\text{id}_* = \text{id}$.

Theo ngôn ngữ lý thuyết phạm trù, $H_n: \mathbf{Top} \to \mathbf{Ab}$ là một hàm tử hiệp biến từ phạm trù các không gian tô-pô sang phạm trù các nhóm Abel.

---

### 3. Bất biến đồng luân

<div class="textbook-theorem" markdown="1">
**Định lý (Bất biến đồng luân):**  
Nếu hai ánh xạ liên tục $f, g: X \to Y$ đồng luân với nhau thì $f_* = g_*: H_n(X) \to H_n(Y)$.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** Nếu $X \simeq Y$ thì $H_n(X) \cong H_n(Y)$.
</div>

**Phác thảo chứng minh:** Cho $F: X \times [0,1] \to Y$ là một phép đồng luân từ $f$ đến $g$. Ta xây dựng một **đồng luân xích** (chain homotopy) $P: C_n(X) \to C_{n+1}(Y)$ thỏa mãn:

$$
\partial P + P \partial = g_\# - f_\#
$$

Với mọi chu trình $c \in Z_n(X)$, ta có $\partial c = 0$, do đó $g_\#(c) - f_\#(c) = \partial P(c)$ là một biên. Khi lấy lớp đồng điều trong $H_n(Y)$, hiệu $g_*[c] - f_*[c] = [\partial P(c)] = 0$, suy ra $f_* = g_*$. ✓

Tính chất này giúp quy bài toán tính đồng điều của nhiều không gian phức tạp về các không gian đơn giản hơn có cùng kiểu đồng luân.

---

## 🧮 Ví dụ và Tính toán

### Ví dụ 1: Một điểm

Xét $X = \{\text{pt}\}$. Ở mỗi chiều $n \geq 0$, chỉ có duy nhất một $n$-đơn hình kỳ dị là ánh xạ hằng $\sigma_n: \Delta^n \to \{\text{pt}\}$, nên $C_n(X) = \mathbb{Z}\langle\sigma_n\rangle \cong \mathbb{Z}$.

Áp dụng công thức toán tử biên:
$$\partial_n(\sigma_n) = \sum_{i=0}^n (-1)^i \sigma_{n-1} = \begin{cases} 0 & \text{nếu } n \text{ lẻ (hoặc } n = 0\text{)} \\ \sigma_{n-1} & \text{nếu } n > 0 \text{ chẵn} \end{cases}$$

Phức xích kỳ dị có dạng $\cdots \xrightarrow{\text{id}} \mathbb{Z} \xrightarrow{0} \mathbb{Z} \xrightarrow{\text{id}} \mathbb{Z} \xrightarrow{0} \mathbb{Z} \to 0$. Do đó:
- $H_0(\text{pt}) = \mathbb{Z}/0 = \mathbb{Z}$;
- $H_n(\text{pt}) = 0$ với mọi $n > 0$.

Một điểm là không gian liên thông và không có lỗ ở các chiều dương.

---

### Ví dụ 2: Không gian co rút được

Nếu $X$ co rút được (contractible) thì $X \simeq \text{pt}$. Theo tính bất biến đồng luân, $H_n(X) \cong H_n(\text{pt})$, suy ra $H_0(X) = \mathbb{Z}$ và $H_n(X) = 0$ với mọi $n > 0$. Kết quả này áp dụng cho $\mathbb{R}^n$, đĩa $D^n$ và mọi miền hình sao.

---

### Ví dụ 3: Mặt cầu $S^n$

Kết quả chuẩn (sẽ được chứng minh ở các bài sau) cho $n \geq 1$:

$$
H_k(S^n) = \begin{cases}
\mathbb{Z} & k = 0, n \\
0 & \text{otherwise}
\end{cases}
$$

Về mặt trực giác, $S^n$ có một thành phần liên thông ($H_0 = \mathbb{Z}$), một lỗ $n$-chiều ($H_n = \mathbb{Z}$) và không có lỗ ở các chiều khác.

---

### Ví dụ 4: Đường tròn $S^1$

$H_0(S^1) = \mathbb{Z}$ (liên thông), $H_1(S^1) = \mathbb{Z}$ (sinh bởi một vòng quấn đúng một lần quanh đường tròn), và $H_n(S^1) = 0$ với mọi $n \geq 2$.

---

## 🧠 Tài liệu kinh điển & Tham khảo

### Công trình kinh điển

1. **Henri Poincaré** - *"Analysis Situs"* (1895-1904)  
   *Giới thiệu các khái niệm mở đầu của đồng điều*

2. **Solomon Lefschetz** - *"Topology"* (1930)  
   *Phát triển đồng điều kỳ dị*

3. **Samuel Eilenberg** - *"Singular homology theory"* (1944)  
   *Xây dựng hệ thống chặt chẽ theo cách tiếp cận hiện đại*

### Giáo trình

4. **Allen Hatcher** - *Algebraic Topology*, **§2.1: Singular Homology**

5. **Glen E. Bredon** - *Topology and Geometry*, **Chapter IV**

6. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapter 4**

7. **Edwin H. Spanier** - *Algebraic Topology*, **Chapter 4**

---

## 🔗 Ứng dụng

### Phân tích dữ liệu tô-pô
**Đồng điều tính toán:** Các thuật toán tính đồng điều từ dữ liệu giúp phát hiện đặc trưng hình học, cụm điểm và khoang rỗng.

### Hình học đại số
**Đối đồng điều bó (Sheaf Cohomology):** Mở rộng tư tưởng đồng điều/đối đồng điều thông qua bó, là công cụ nền tảng trong hình học hiện đại.

### Vật lý lý thuyết trường
**Các lớp đặc trưng (Characteristic Classes):** Đồng điều và đối đồng điều được dùng để phân loại các trường chuẩn (gauge fields) và dị thường (anomalies).

---

## Video tham khảo

- **xem trước** [Algebraic Topology 12: Intro to Singular Homology](https://www.youtube.com/watch?v=GE1_Ntw7x6s) — Math at Andrews University, tiếng Anh. Đồng điều kỳ dị từ đơn hình chuẩn, không cần phép chia tam giác của không gian.
- [12. Singular Homology; Chain Homotopy - Pierre Albin](https://www.youtube.com/watch?v=I2GbdKDN9zg) — Mat Neth, tiếng Anh. Pierre Albin trình bày đồng điều kỳ dị và đồng luân xích, đúng phần kỹ thuật của bài.

## 🧩 Bài tập

### Đơn hình chuẩn

1. **Kiểm chứng:** Chỉ ra $\Delta^1 \cong [0,1]$ thông qua một phép biến đổi tọa độ tường minh.

2. **Ánh xạ mặt:** Tính tường minh $\delta_0, \delta_1, \delta_2: \Delta^1 \to \Delta^2$.

3. **Biên của $\Delta^2$:** Kiểm chứng rằng mỗi cạnh trong 3 mặt của $\Delta^2$ đều là ảnh của một ánh xạ $\delta_i$.

### Đơn hình kỳ dị

4. **Đếm số đơn hình:** Với $X = \{\text{pt}\}$, có bao nhiêu $n$-đơn hình kỳ dị phân biệt?

5. **Đường tròn:** Hãy cho một ví dụ tường minh về $1$-đơn hình kỳ dị $\sigma: \Delta^1 \to S^1$ quấn hai vòng quanh đường tròn.

6. **Ảnh của đơn hình kỳ dị:** Một đơn hình kỳ dị có thể là toàn ánh không? Hãy nêu ví dụ hoặc giải thích vì sao không.

### Toán tử biên

7. **Tính toán:** Cho $\sigma: \Delta^2 \to X$, hãy viết biểu thức tường minh của $\partial\sigma$ theo các ánh xạ $\delta_i$.

8. **Kiểm chứng $\partial^2 = 0$:** Với $\sigma: \Delta^2 \to X$, hãy tính từng bước để kiểm tra $\partial(\partial\sigma) = 0$.

### Tính hàm tử

9. **Ánh xạ cảm sinh:** Cho ánh xạ đồng nhất $f: S^1 \to S^1$. Đồng cấu $f_*: H_1(S^1) \to H_1(S^1)$ là gì?

10. **Ánh xạ hợp:** Kiểm chứng $(f \circ g)_* = f_* \circ g_*$ trên một ví dụ đơn giản.

### Bất biến đồng luân

11. **Không gian co rút được:** Xét $X = \mathbb{R}^2$. Dùng tính bất biến đồng luân để suy ra $H_n(\mathbb{R}^2)$.

12. **Hình trụ:** Từ $S^1 \times [0,1] \simeq S^1$, hãy tính $H_n(S^1 \times [0,1])$.

### So sánh

13. **Đơn hình và kỳ dị:** Với phức đơn hình $K$, hãy giải thích vì sao $H_n^{\text{simplicial}}(K) \cong H_n^{\text{singular}}(|K|)$.

### Nâng cao

14. **Tính khớp:** Tìm hiểu dãy khớp dài của một cặp không gian $(X, A)$.

15. **Đồng điều tương đối:** Tìm hiểu ý nghĩa của $H_n(X, A)$ trong việc đo lường "các lỗ trong $X$ không xuất phát từ $A$".

---

## 📚 Đọc thêm

- **Hatcher, §2:** Trình bày toàn diện về đồng điều kỳ dị.
- **Bredon, Chapter IV:** Góc nhìn nâng cao.
- **Spanier:** Tài liệu tra cứu hệ thống.

---

## 🎓 Tóm tắt

Đồng điều kỳ dị là lý thuyết đồng điều tổng quát áp dụng cho mọi không gian tô-pô:

✅ **Đơn hình kỳ dị:** Mọi ánh xạ liên tục $\sigma: \Delta^n \to X$.  
✅ **Nhóm xích $C_n(X)$:** Nhóm Abel tự do sinh bởi các $n$-đơn hình kỳ dị.  
✅ **Toán tử biên $\partial$:** Xác định qua các ánh xạ mặt, thỏa mãn $\partial^2 = 0$.  
✅ **Nhóm đồng điều $H_n(X)$:** $\ker(\partial) / \text{im}(\partial)$.  
✅ **Tính hàm tử:** $f: X \to Y$ cảm sinh $f_*$.  
✅ **Bất biến đồng luân:** $X \simeq Y \Rightarrow H_n(X) \cong H_n(Y)$.  
✅ **Tính phổ quát:** Áp dụng được cho mọi không gian tô-pô.

**Tiếp theo:** Các phương pháp tính toán đồng điều một cách có hệ thống.

---

**Previous:** [Lecture 07.00: Simplicial Homology](/contents/vi/topology-chapter07/07_00_Simplicial_Homology/)  
**Next:** [Lecture 07.02: Homology Computations](/contents/vi/topology-chapter07/07_02_Homology_Computations/)
