---
layout: post
title: "Lecture 07.02: Homology Computations"
lang: vi
lang-ref: lecture-07-02
chapter: 7
lecture: 2
categories: [chapter07]
tags: [homology-computations, euler-characteristic, betti-numbers]
description: "Computing H_n: systematic examples (Sⁿ, surfaces, CW complexes), Euler characteristic, cellular homology"
---

**Các phương pháp hệ thống và ví dụ chuẩn**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu bạn chải mượt một quả bóng dừa đầy lông (mặt cầu $$S^2$$), kiểu gì cũng sẽ mọc ra ít nhất một cái **xoáy tóc** đứng dựng lên — bạn không bao giờ chải phẳng được toàn bộ mặt cầu mà không có điểm xoáy! Thế nhưng trên một chiếc bánh donut (hình xuyến $$T^2$$), hay trên mặt cầu **3 chiều $$S^3$$**, bạn lại chải mượt hoàn toàn được không sót một sợi lông nào! Bí mật ẩn sau hiện tượng kỳ diệu ấy nằm gọn trong một con số nguyên duy nhất của bài học này: **bậc đồng điều $$\deg(f)$$** của ánh xạ giữa các mặt cầu $$S^n \to S^n$$!

Việc tính trực tiếp $H_n(X)$ từ định nghĩa đồng điều kỳ dị thường không khả thi vì nhóm xích kỳ dị có vô số phần tử sinh. Do đó, ta cần các công cụ tính toán hiệu quả hơn:

1. **Tương đương đồng luân:** Nếu $X \simeq Y$ thì $H_n(X) \cong H_n(Y)$, giúp rút gọn không gian trước khi tính.
2. **Phức CW và đồng điều tế bào (cellular homology):** Đưa bài toán về các nhóm xích hữu hạn sinh.
3. **Dãy Mayer–Vietoris:** Chia không gian thành các phần đơn giản hơn rồi ghép thông tin đồng điều.
4. **Các dãy khớp dài:** Dãy khớp dài của cặp $(X, A)$ hoặc của phân thớ.
5. **Dãy phổ (spectral sequences):** Công cụ nâng cao cho các bài toán phức tạp hơn.

Bài học này tập trung vào các ví dụ kinh điển (điểm, không gian co rút được, mặt cầu $S^n$, hình xuyến $T^2$, mặt định hướng $\Sigma_g$), đồng điều tế bào trên phức CW, đặc trưng Euler và các số Betti.

![CW complex structure](https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/CW-komplex-1.svg/400px-CW-komplex-1.svg.png)  
*Phức CW xây dựng từ các tế bào - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:CW-komplex-1.svg)*

Nắm vững các ví dụ chuẩn và thuật toán đồng điều tế bào giúp nhận diện cấu trúc lỗ của các không gian quen thuộc, đồng thời xây dựng nền tảng cho các công cụ tính toán tổng quát hơn ở các bài tiếp theo.

---

## 🗺️ Kiến thức cần nhớ: Tính toán Đồng điều & Lý thuyết Bậc Ánh xạ

### 1. Đồng điều Rút gọn $$\tilde{H}_n(X)$$ & Mặt cầu $$S^k$$
- **Bản chất:** Đồng điều rút gọn $$\tilde{H}_n(X)$$ chỉ chỉnh nhẹ bậc $$0$$ ($$\tilde{H}_0(X) \oplus \mathbb{Z} \cong H_0(X)$$) để không gian 1 điểm có $$\tilde{H}_n(\{\text{pt}\}) = 0$$ ở **mọi** bậc $$n$$. Nhờ đó công thức mặt cầu trở nên tuyệt đẹp: $$\tilde{H}_n(S^k) \cong \mathbb{Z}$$ khi $$n = k$$ và bằng $$0$$ khi $$n \neq k$$!

### 2. Bậc (Degree) của Ánh xạ $$f: S^n \to S^n$$
- **Bản chất:** Vì $$H_n(S^n) \cong \mathbb{Z}$$, mọi đồng cấu nhóm $$f_*: \mathbb{Z} \to \mathbb{Z}$$ đều chỉ là phép nhân với **một số nguyên duy nhất $$d$$** — gọi là **bậc của $$f$$** ($$\deg(f) = d$$):
  - $$\deg(\operatorname{id}_{S^n}) = +1$$; $$\deg(\text{ánh xạ hằng}) = 0$$.
  - $$\deg(f \circ g) = \deg(f)\cdot\deg(g)$$ và $$f \simeq g \implies \deg(f) = \deg(g)$$.
  - Mỗi phép phản xạ qua một siêu phẳng trong $$\mathbb{R}^{n+1}$$ có bậc bằng **$$-1$$**!

### 3. Bốn Hệ quả Kinh điển ở MỌI số chiều $$n$$
- **Điểm bất động Brouwer tổng quát:** Mọi $$f: D^n \to D^n$$ liên tục đều có điểm bất động (dùng $$H_{n-1}(S^{n-1}) \cong \mathbb{Z}$$!).
- **Bất biến Số chiều (Invariance of Dimension):** $$\mathbb{R}^m \cong \mathbb{R}^n \iff m = n$$ (xóa 1 điểm rồi so sánh $$H_k(\mathbb{R}^m\setminus\{0\}) \cong H_k(S^{m-1})$$!).
- **Định lý Quả bóng có lông:** $$S^n$$ có trường vectơ tiếp tuyến khác không ở mọi điểm $$\iff n$$ **lẻ**!

---

## 🧮 Ví dụ tính tay làm từng bước: Tính $$\deg(\text{đối tâm})$$ và Chứng minh Quả bóng có lông trong 4 dòng

### 1. Tính bậc của ánh xạ đối tâm $$a: S^n \to S^n,\; a(x_1, \dots, x_{n+1}) = (-x_1, \dots, -x_{n+1})$$
Viết $$a$$ thành hợp của $$n+1$$ phép phản xạ sơ cấp $$r_k$$ (chỉ đổi dấu tọa độ thứ $$k$$):
$$
a = r_1 \circ r_2 \circ \cdots \circ r_{n+1}.
$$
Mỗi phép phản xạ $$r_k$$ đổi hướng mặt cầu nên có $$\deg(r_k) = -1$$. Nhờ tính nhân của bậc:
$$
\deg(a) = \deg(r_1)\cdots\deg(r_{n+1}) = (-1)^{n+1}!
$$
- Trên $$S^1$$ ($$n=1$$ lẻ): $$\deg(a) = (-1)^2 = +1$$ (quay $$180^\circ$$ đồng luân với đồng nhất!).
- Trên $$S^2$$ ($$n=2$$ chẵn): $$\deg(a) = (-1)^3 = -1$$ (không thể biến dạng liên tục phép đối tâm thành đồng nhất!).

### 2. Chứng minh Định lý Quả bóng có lông cho $$S^{2k}$$ bằng tay
Giả sử tồn tại một trường vectơ tiếp tuyến liên tục $$v(x) \neq 0$$ tại mọi $$x \in S^n$$ (vuông góc với $$x$$). Chuẩn hóa $$u(x) = v(x)/\|v(x)\|$$ (nên $$\|u(x)\|=1$$ và $$x \cdot u(x) = 0$$). Xét đường đi cung tròn đẩy mỗi điểm $$x$$ dọc theo $$u(x)$$ tới đúng điểm đối tâm $$-x$$:
$$
H(x, t) = \cos(\pi t)\,x + \sin(\pi t)\,u(x), \qquad t \in [0, 1].
$$
1. **Kiểm tra nằm trên $$S^n$$:** $$\|H(x,t)\|^2 = \cos^2(\pi t)\|x\|^2 + \sin^2(\pi t)\|u(x)\|^2 = 1$$! ✓
2. **Hai đầu mút:** $$H(x, 0) = x = \operatorname{id}(x)$$ và $$H(x, 1) = -x = a(x) \implies \operatorname{id}_{S^n} \simeq a$$!
3. **So sánh bậc hai vế:** $$+1 = \deg(\operatorname{id}_{S^n}) = \deg(a) = (-1)^{n+1} \implies n + 1$$ phải **chẵn**, tức **$$n$$ bắt buộc LẺ**!
Vậy trên $$S^2, S^4, S^6, \dots$$ **không bao giờ tồn tại** trường vectơ tiếp tuyến không triệt tiêu! (Còn trên $$S^{2m-1}$$, trường $$v(x_1, y_1, \dots, x_m, y_m) = (-y_1, x_1, \dots, -y_m, x_m)$$ thỏa $$v\cdot x = 0$$ và $$\|v\|=1$$ everywhere — chải mượt hoàn hảo!)

### Giải thích: Chiến lược 4 bước chinh phục các bài toán tính Đồng điều

#### Bước 1: Dùng co rút biến dạng để đơn giản hóa không gian trước khi tính
Thay $$\mathbb{R}^n\setminus\{0\}$$ bằng $$S^{n-1}$$; thay dải Möbius hay hình trụ bằng $$S^1$$; thay mặt cầu thủng 1 điểm bằng 1 điểm!

#### Bước 2: Dùng công thức tách tổng rời và bó không gian (Wedge sum)
Đồng điều của hợp rời bằng tổng trực tiếp: $$H_n(\bigsqcup X_\alpha) \cong \bigoplus H_n(X_\alpha)$$. Với bó tại một điểm đẹp (như $$S^1 \vee S^1 \vee S^2$$): $$\tilde{H}_n(\bigvee X_\alpha) \cong \bigoplus \tilde{H}_n(X_\alpha)$$!

#### Bước 3: Dùng tính chất bậc $$\deg(f)$$ để giải các bài toán tồn tại nghiệm và trường vectơ
Bất kỳ bài toán nào hỏi "liệu có tồn tại ánh xạ không có điểm bất động / không có điểm đối tâm / trường vectơ khác không?" đều hãy thử dựng một đồng luân giữa $$\operatorname{id}_{S^n}$$ và ánh xạ đối tâm $$a$$ rồi đối chiếu bậc!

#### Bước 4: Đọc ngay các nhóm đồng điều của mặt đóng & không gian xạ ảnh
Nắm vững bảng chuẩn: $$H_*(S^k)$$, $$H_*(T^2) = (\mathbb{Z}, \mathbb{Z}^2, \mathbb{Z})$$, $$H_*(\mathbb{R}P^2) = (\mathbb{Z}, \mathbb{Z}/2\mathbb{Z}, 0)$$ và $$H_*(\mathbb{C}P^n)$$ ($$\mathbb{Z}$$ ở các bậc chẵn $$0, 2, \dots, 2n$$).

$$
H_n(S^n) \cong \mathbb{Z}
\;\xrightarrow{\;f_*(1) = \deg(f)\;}\;
\deg(a) = (-1)^{n+1}
\;\xrightarrow{\;\operatorname{id} \simeq a?\;}\;
\text{Brouwer, Bất biến chiều \& Quả bóng có lông}.
$$

---

## 🎯 Các tính toán cơ bản

### Ví dụ 1: Một điểm

Xét $X = \{\text{pt}\}$. Trong đồng điều kỳ dị, ở mỗi chiều $n \geq 0$ chỉ có một $n$-đơn hình duy nhất là ánh xạ hằng $\sigma_n: \Delta^n \to \{\text{pt}\}$, nên $C_n = \mathbb{Z}\langle\sigma_n\rangle \cong \mathbb{Z}$. Toán tử biên thỏa mãn $\partial_n(\sigma_n) = 0$ khi $n$ lẻ (hoặc $n = 0$) và $\partial_n(\sigma_n) = \sigma_{n-1}$ khi $n > 0$ chẵn, nên phức xích có dạng:
$$\cdots \xrightarrow{\text{id}} \mathbb{Z} \xrightarrow{0} \mathbb{Z} \xrightarrow{\text{id}} \mathbb{Z} \xrightarrow{0} \mathbb{Z} \to 0$$

Từ đó thu được:

$$
H_n(\text{pt}) = \begin{cases}
\mathbb{Z} & n = 0 \\
0 & n > 0
\end{cases}
$$

Một điểm có đúng một thành phần liên thông và không có lỗ ở các chiều dương.

---

### Ví dụ 2: Không gian co rút được

Nếu $X$ là không gian co rút được ($X \simeq \text{pt}$), theo tính bất biến đồng luân ta có:

$$
H_n(X) \cong H_n(\text{pt})
$$

Suy ra $H_0(X) = \mathbb{Z}$ và $H_n(X) = 0$ với mọi $n > 0$. Điều này đúng với không gian Euclid $\mathbb{R}^n$, đĩa $D^n$, các miền hình sao và hình nón $CX$ của mọi không gian $X$.

---

## 🔵 Mặt cầu $S^k$

### Định lý về $H_n(S^k)$

<div class="textbook-theorem" markdown="1">
**Định lý:** Với mọi $k \geq 1$,

$$
H_n(S^k) = \begin{cases}
\mathbb{Z} & n = 0 \\
\mathbb{Z} & n = k \\
0 & \text{otherwise}
\end{cases}
$$
</div>

Mặt cầu $S^k$ ($k \geq 1$) chỉ có hai nhóm đồng điều khác không: $H_0(S^k) = \mathbb{Z}$ (liên thông) và $H_k(S^k) = \mathbb{Z}$ (một lỗ $k$-chiều là khoảng rỗng bên trong).

---

### Phác thảo chứng minh (bằng phức CW)

Với $k \geq 1$, mặt cầu $S^k$ có cấu trúc phức CW tối giản gồm một $0$-tế bào $e^0$ và một $k$-tế bào $e^k$ được dán biên $S^{k-1}$ vào $e^0$. Khi $k \geq 2$, phức xích tế bào chỉ khác không ở bậc $0$ và bậc $k$:

$$
0 \to \mathbb{Z} \xrightarrow{\partial_k} \mathbb{Z} \to 0
$$

Với $k \geq 2$, không có $(k-1)$-tế bào nên $\partial_k = 0$ (còn khi $k = 1$, hai đầu mút của $1$-tế bào cùng dán vào $e^0$ nên $\partial_1(e^1) = e^0 - e^0 = 0$). Do mọi toán tử biên đều bằng $0$, ta suy ra $H_0(S^k) = \mathbb{Z}$, $H_k(S^k) = \mathbb{Z}$ và $H_n(S^k) = 0$ với các $n$ còn lại. ✓

---

### Các trường hợp cụ thể

- **$S^0$ (hai điểm rời nhau):** $H_0(S^0) = \mathbb{Z} \oplus \mathbb{Z}$ (hai thành phần liên thông) và $H_n(S^0) = 0$ với $n > 0$.
- **$S^1$ (đường tròn):** $H_0(S^1) = \mathbb{Z}$, $H_1(S^1) = \mathbb{Z}$, $H_n(S^1) = 0$ ($n \geq 2$).
- **$S^2$ (mặt cầu 2 chiều):** $H_0(S^2) = \mathbb{Z}$, $H_1(S^2) = 0$, $H_2(S^2) = \mathbb{Z}$.
- **$S^3$ (mặt cầu 3 chiều):** $H_0(S^3) = \mathbb{Z}$, $H_3(S^3) = \mathbb{Z}$, các bậc khác bằng $0$.

---

## 🍩 Hình xuyến $T^2$

### Cấu trúc CW

Hình xuyến $T^2 = S^1 \times S^1$ có cấu trúc phức CW gồm:
- 1 đỉnh ($0$-tế bào $e^0$);
- 2 cạnh ($1$-tế bào $a, b$) tạo thành hai vòng khép kín tại $e^0$;
- 1 ô vuông ($2$-tế bào $e^2$) dán vào $1$-khung theo từ biên $aba^{-1}b^{-1}$.

---

### Phức xích tế bào

Các nhóm xích tế bào là $C_0 = \mathbb{Z}$, $C_1 = \mathbb{Z}^2$ (sinh bởi $a, b$) và $C_2 = \mathbb{Z}$ (sinh bởi $e^2$), nối nhau bởi:

$$
C_2 \xrightarrow{\partial_2} C_1 \xrightarrow{\partial_1} C_0
$$

Do $a$ và $b$ là các vòng bắt đầu và kết thúc tại cùng đỉnh $e^0$, ta có $\partial_1(a) = \partial_1(b) = 0$. Trên $2$-tế bào $e^2$, biên có hướng của hình vuông là $\partial_2(e^2) = a + b - a - b = 0$ vì mỗi cạnh được đi qua hai lần theo hai chiều ngược nhau.

---

### Tính toán đồng điều

Vì cả $\partial_1$ và $\partial_2$ đều là ánh xạ không (và không có $3$-tế bào), ta thu được ngay:
- $H_0(T^2) = Z_0 / B_0 = \mathbb{Z} / \{0\} = \mathbb{Z}$ (liên thông);
- $H_1(T^2) = Z_1 / B_1 = \mathbb{Z}^2 / \{0\} = \mathbb{Z}^2$ (hai vòng độc lập theo kinh tuyến và vĩ tuyến);
- $H_2(T^2) = Z_2 / B_2 = \mathbb{Z} / \{0\} = \mathbb{Z}$ (khoảng rỗng hai chiều bên trong).

---

### Kết quả

$$
H_*(T^2) = \mathbb{Z}, \mathbb{Z}^2, \mathbb{Z}, 0, 0, \ldots
$$

Từ đây ta có các số Betti $\beta_0 = 1, \beta_1 = 2, \beta_2 = 1$ và đặc trưng Euler $\chi(T^2) = 1 - 2 + 1 = 0$.

---

## 🏔️ Mặt đóng định hướng $\Sigma_g$

### Cấu trúc CW

![Genus surfaces](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Torus_cycles.png/400px-Torus_cycles.png)  
*Hình xuyến với các chu trình cơ bản - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus_cycles.png)*

Mặt đóng định hướng giống $g$ ($\Sigma_g$) có cấu trúc CW gồm:
- 1 đỉnh ($0$-tế bào);
- $2g$ cạnh ($1$-tế bào là các vòng $a_1, b_1, \ldots, a_g, b_g$);
- 1 mặt ($2$-tế bào là đa giác $4g$ cạnh dán theo quan hệ biên $\prod_{i=1}^g a_i b_i a_i^{-1} b_i^{-1}$).

---

### Đồng điều

Tương tự như hình xuyến, mọi toán tử biên tế bào đều bằng $0$, suy ra:
- $H_0(\Sigma_g) = \mathbb{Z}$ (liên thông);
- $H_1(\Sigma_g) = \mathbb{Z}^{2g}$ ($2g$ vòng độc lập);
- $H_2(\Sigma_g) = \mathbb{Z}$ (mặt đóng bao quanh vùng rỗng bên trong).

**Các trường hợp cụ thể:**
- $g = 0$ ($S^2$): $H_1 = 0$ (đơn liên).
- $g = 1$ ($T^2$): $H_1 = \mathbb{Z}^2$ (2 vòng độc lập).
- $g = 2$: $H_1 = \mathbb{Z}^4$ (4 vòng độc lập).

Tổng quát, hạng của $H_1(\Sigma_g)$ bằng $2g$, xác định hoàn toàn giống $g$ của mặt.

---

### Đặc trưng Euler

$$\chi(\Sigma_g) = 2 - 2g$$

Cụ thể: với $S^2$ ($g=0$) ta có $\chi = 2$; với $T^2$ ($g=1$) ta có $\chi = 0$; với mặt giống $2$ ta có $\chi = -2$. Đối với các mặt đóng định hướng, đặc trưng Euler xác định duy nhất giống $g$.

---

## 🏗️ Đồng điều tế bào

### 1. Ôn tập về phức CW

Một **phức CW** $X$ được xây dựng quy nạp: bắt đầu từ tập rời rạc các $0$-tế bào (đỉnh), sau đó lần lượt dán các $n$-tế bào $D^n$ dọc theo biên $S^{n-1}$ vào $(n-1)$-khung. Tập hợp tất cả các tế bào có chiều $\leq n$ gọi là **$n$-khung** $X^{(n)}$ ($n$-skeleton). Các mặt cầu, hình xuyến, mặt đóng và đa tạp quen thuộc đều có cấu trúc phức CW.

---

### 2. Phức xích tế bào

Các nhóm xích tế bào được định nghĩa qua đồng điều tương đối của các khung liên tiếp:

$$
C_n^{CW}(X) = H_n(X^{(n)}, X^{(n-1)})
$$

Nếu $X$ là phức CW hữu hạn, mỗi $C_n^{CW}(X)$ là nhóm Abel tự do có hạng đúng bằng số lượng $n$-tế bào. Toán tử biên $\partial_n$ được cảm sinh từ các phép nhúng và có thể tính tường minh thông qua bậc (degree) của các ánh xạ dán.

---

### 3. Định lý đồng điều tế bào

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Với mọi phức CW $X$, đồng điều tế bào đẳng cấu với đồng điều kỳ dị:

$$
H_n^{CW}(X) \cong H_n(X)
$$
</div>

Nhờ định lý này, với mọi phức CW hữu hạn ta chỉ cần làm việc trên các nhóm xích hữu hạn sinh thay vì vô số đơn hình kỳ dị, và bài toán tính $H_n(X)$ quy về các phép biến đổi đại số tuyến tính trên ma trận hữu hạn chiều.

---

### 4. Ví dụ: Mặt phẳng xạ ảnh $\mathbb{R}P^2$

$\mathbb{R}P^2$ có cấu trúc CW gồm 1 đỉnh $e^0$, 1 cạnh $e^1$ (vòng khép kín) và 1 đĩa $e^2$ dán vào $e^1$ bằng phép đồng nhất các điểm đối cực. Do đó $C_0 = \mathbb{Z}$, $C_1 = \mathbb{Z}$, $C_2 = \mathbb{Z}$.

Khi dán $e^2$ theo phép đồng nhất đối cực, biên của đĩa quấn quanh $e^1$ đúng hai lần theo cùng chiều, nên $\partial_2(e^2) = 2e^1$, trong khi $\partial_1(e^1) = 0$. Từ đó:
- $H_0(\mathbb{R}P^2) = \mathbb{Z}$ (liên thông);
- $H_1(\mathbb{R}P^2) = \mathbb{Z}/2\mathbb{Z}$ (xuất hiện phần xoắn);
- $H_2(\mathbb{R}P^2) = \ker(\partial_2) = 0$ (vì $\partial_2: \mathbb{Z} \to \mathbb{Z}$ là phép nhân với $2$, nên đơn ánh).

Đây là ví dụ đầu tiên cho thấy nhóm đồng điều có thể chứa phần xoắn (torsion), phản ánh tính không định hướng được của $\mathbb{R}P^2$.

---

## 🔢 Đặc trưng Euler

### Định nghĩa

**Đặc trưng Euler** (Euler characteristic) của không gian $X$ được định nghĩa là tổng đan dấu các số Betti $\beta_n = \text{rank}(H_n(X))$:

$$
\chi(X) = \sum_{n=0}^\infty (-1)^n \beta_n
$$

---

### Định lý Euler–Poincaré

Đối với một phức CW hữu hạn $X$:

$$
\chi(X) = \sum_{n=0}^\infty (-1)^n (\text{số lượng các } n\text{-tế bào})
$$

Kết quả này cho thấy đặc trưng Euler có thể tính bằng hai cách cho cùng một giá trị: từ các nhóm đồng điều hoặc đếm trực tiếp số tế bào ở từng chiều. Với các khối đa diện trong $\mathbb{R}^3$, công thức quy về công thức cổ điển $V - E + F$.

---

### Các ví dụ

- **$S^2$:** $\chi = \beta_0 - \beta_1 + \beta_2 = 1 - 0 + 1 = 2$. Dùng cấu trúc CW gồm 2 đỉnh, 1 cạnh, 1 mặt cho $2 - 1 + 1 = 2$; hoặc dùng 1 đỉnh, 0 cạnh, 1 mặt cho $1 - 0 + 1 = 2$.
- **$T^2$:** $\chi = 1 - 2 + 1 = 0$.
- **$\Sigma_g$:** $\chi = 1 - 2g + 1 = 2 - 2g$.
- **$\mathbb{R}P^2$:** $\chi = 1 - 0 + 0 = 1$ (vì $H_1(\mathbb{R}P^2) = \mathbb{Z}/2\mathbb{Z}$ là nhóm xoắn nên $\beta_1 = 0$).

---

### Các tính chất

1. **Bất biến đồng luân:** Nếu $X \simeq Y$ thì $\chi(X) = \chi(Y)$.
2. **Tính nhân:** $\chi(X \times Y) = \chi(X) \cdot \chi(Y)$.
3. **Tính cộng:** $\chi(X \cup Y) = \chi(X) + \chi(Y) - \chi(X \cap Y)$ (với các giao thỏa mãn điều kiện phù hợp).

---

## 🧱 Đồng điều Tế bào (Cellular Homology) — Công cụ tính nhanh cho Phức CW

Tính đồng điều kỳ dị trực tiếp từ định nghĩa gần như bất khả thi, nhưng với các không gian có cấu trúc **phức CW** (như $S^n, T^2, \Sigma_g, \mathbb{R}P^n, \mathbb{C}P^n$), ta chỉ cần đếm số $k$-tế bào và **bậc ánh xạ dán (cellular boundary degree)** — theo Chương 5.5 của [*Algebraic Topology* (L. Maxim)](https://people.math.wisc.edu/~lmaxim/topbookf.pdf):

![Phân rã tế bào CW của S^2 và T^2]({{ site.imgurl }}/chapter_img/chapter07/07_02_cellular_homology.png)

- Định nghĩa phức dây chuyền tế bào $C_k^{\mathrm{CW}}(X) = H_k(X^{(k)}, X^{(k-1)}) \cong \bigoplus_{\alpha} \mathbb{Z}$ (mỗi $k$-tế bào đóng góp một bản sao $\mathbb{Z}$).
- **Công thức biên tế bào:** Với $k$-tế bào $e^k_\alpha$ và $(k-1)$-tế bào $e^{k-1}_\beta$, hệ số biên $d_{\alpha\beta} = \deg(\Delta_{\alpha\beta})$ chính là **bậc (degree)** của ánh xạ hợp từ $S^{k-1} \xrightarrow{\varphi_\alpha} X^{(k-1)} \to S^{k-1}_\beta$.
- **Ví dụ tính tay cho $T^2$:** $T^2 = e^0 \cup (e^1_a \vee e^1_b) \cup e^2$. Khi dán $e^2$ dọc theo từ $aba^{-1}b^{-1}$, mỗi cạnh $a$ và $b$ đi qua một lần theo chiều dương và một lần theo chiều âm nên bậc tổng bằng $1 - 1 = 0$. Do đó mọi $\partial_k^{\mathrm{CW}} = 0$, suy ra ngay $H_0(T^2)=\mathbb{Z},\; H_1(T^2)=\mathbb{Z}^2,\; H_2(T^2)=\mathbb{Z}$!
- **Ví dụ $\mathbb{R}P^n$:** Có đúng một tế bào ở mỗi chiều $0 \le k \le n$, ánh xạ dán có bậc $1 + (-1)^k$ (luân phiên $0$ và $2$), cho kết quả kinh điển $H_k(\mathbb{R}P^n; \mathbb{Z}) = \mathbb{Z}/2\mathbb{Z}$ với $k$ lẻ ($0 < k < n$).

## 🧠 Tài liệu kinh điển & Tham khảo

### Công trình kinh điển

1. **Leonhard Euler** - *"Solutio problematis ad geometriam situs pertinentis"* (1736)  
   *Công thức $V - E + F$*

2. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Đồng điều và các số Betti*

3. **J.H.C. Whitehead** - *"Combinatorial homotopy"* (1949)  
   *Phức CW và đồng điều tế bào*

### Giáo trình

4. **Allen Hatcher** - *Algebraic Topology*, **§2.1-2.2**

5. **Glen E. Bredon** - *Topology and Geometry*, **Chapter IV**

6. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapter 2**

---

## 🔗 Ứng dụng

### Đồ họa máy tính — Xử lý lưới 3D
**Kiểm tra đặc trưng Euler:** Xác minh cấu trúc tô-pô của lưới 3D và phát hiện lỗi trong các mô hình quét.

### Robot học — Không gian cấu hình
**Tính toán đồng điều:** Phân tích tô-pô của không gian cấu hình phục vụ các thuật toán lập kế hoạch chuyển động.

### Khoa học dữ liệu — Phân tích hình dạng
**Đồng điều bền vững:** Theo dõi sự biến đổi của các số Betti qua các thang đo để phát hiện đặc trưng trong dữ liệu.

---

## Video tham khảo

- **xem trước** [Algebraic Topology 17: Degree and Cellular Homology](https://www.youtube.com/watch?v=CVcxgCm6qgg) — Math at Andrews University, tiếng Anh. Đồng điều tế bào và bậc ánh xạ, công cụ tính mà bài dùng cho mặt cầu và mặt.
- [19. Homology of Cell Complexes - Pierre Albin](https://www.youtube.com/watch?v=2tOLcrLaqOw) — Mat Neth, tiếng Anh. Pierre Albin tính đồng điều của phức tế bào, sát các ví dụ mặt cầu và hình xuyến.

## 🧩 Bài tập

### Tính toán cơ bản

1. **Hai điểm rời nhau:** Cho $X = \{\text{pt}_1, \text{pt}_2\}$ với tô-pô rời rạc. Tính $H_n(X)$.

2. **Đoạn thẳng:** Với $X = [0,1]$, sử dụng tính co rút được để tính $H_n(X)$.

3. **Hình số tám:** Tính $H_1(S^1 \vee S^1)$ (gợi ý: sử dụng tiên đề tổng bó — wedge axiom).

### Mặt cầu

4. **Kiểm chứng:** Tính $H_n(S^3)$ bằng phức CW gồm một $0$-tế bào và một $3$-tế bào.

5. **Phép treo (Suspension):** Với $\Sigma(S^n) = S^{n+1}$, kiểm tra sự tương thích của các nhóm đồng điều.

### Các mặt

6. **Chai Klein:** Sử dụng cấu trúc CW gồm 1 đỉnh, 2 cạnh, 1 mặt để tính $H_n$ của chai Klein. (Đáp số: $H_1 = \mathbb{Z} \oplus \mathbb{Z}/2\mathbb{Z}$.)

7. **Không gian xạ ảnh $\mathbb{R}P^3$:** Kiểm chứng $H_n(\mathbb{R}P^3) = \mathbb{Z}, \mathbb{Z}/2\mathbb{Z}, 0, \mathbb{Z}$ (với $n = 0,1,2,3$) bằng phức CW.

### Đặc trưng Euler

8. **Hình lập phương:** Với 8 đỉnh, 12 cạnh, 6 mặt, hãy tính $\chi$ và đối chiếu với $\chi(S^2) = 2$.

9. **Mặt giống 5:** Tính $\chi(\Sigma_5)$.

10. **Không gian tích:** Tính $\chi(S^2 \times S^2)$ bằng công thức $\chi(X \times Y) = \chi(X)\chi(Y)$.

### Phức CW

11. **Dán $2$-tế bào:** Bắt đầu từ $S^1$, dán đĩa $D^2$ theo ánh xạ bậc 2 rồi tính $H_n$ (thu được $\mathbb{R}P^2$).

12. **Tổng bó (Wedge):** Chứng minh $H_n(X \vee Y) \cong H_n(X) \oplus H_n(Y)$ với $n > 0$ (cho các phức CW).

### Đồng điều tế bào

13. **Tính trực tiếp:** Viết đầy đủ phức xích tế bào và tính $H_*(T^2)$.

14. **Mặt phẳng xạ ảnh $\mathbb{R}P^2$:** Kiểm chứng $H_1(\mathbb{R}P^2) = \mathbb{Z}/2\mathbb{Z}$ từ công thức biên tế bào $\partial_2(e^2) = 2e^1$.

### Nâng cao

15. **Tìm hiểu:** Xác định các nhóm đồng điều $H_n(\mathbb{C}P^2)$ của mặt phẳng xạ ảnh phức.

16. **Mặt cầu đồng điều (Homology Sphere):** Tìm hiểu về mặt cầu đồng điều Poincaré — một $3$-đa tạp có cùng nhóm đồng điều với $S^3$ nhưng không đồng phôi với $S^3$.

---

## 📚 Đọc thêm

- **Hatcher, §2.1-2.2:** Các ví dụ chi tiết và đồng điều tế bào.
- **Bredon, Chapter IV:** Trình bày toàn diện.
- **Munkres, Elements:** Các tính toán cẩn thận.

---

## 🎓 Tóm tắt

Các kết quả và công cụ tính toán đồng điều có hệ thống:

✅ **Không gian co rút được:** $H_0 = \mathbb{Z}$, các bậc cao hơn bằng $0$.  
✅ **Mặt cầu $S^n$ ($n \geq 1$):** $H_0 = H_n = \mathbb{Z}$, các bậc khác bằng $0$.  
✅ **Hình xuyến $T^2$:** $H_0 = \mathbb{Z}$, $H_1 = \mathbb{Z}^2$, $H_2 = \mathbb{Z}$.  
✅ **Mặt đóng định hướng $\Sigma_g$:** $H_1 = \mathbb{Z}^{2g}$ xác định giống $g$.  
✅ **Đồng điều tế bào:** Thuật toán hữu hạn thông qua phức CW.  
✅ **Đặc trưng Euler $\chi$:** Bất biến đồng luân, tính được qua số Betti hoặc số tế bào.  
✅ **Số Betti $\beta_n$:** Đếm số lỗ $n$-chiều.

**Tiếp theo:** Dãy Mayer–Vietoris — công cụ tính đồng điều bằng phương pháp phân rã không gian.

---

**Previous:** [Lecture 07.01: Singular Homology](/contents/vi/topology-chapter07/07_01_Singular_Homology/)  
**Next:** [Lecture 07.03: Mayer-Vietoris Sequence](/contents/vi/topology-chapter07/07_03_Mayer_Vietoris/)
