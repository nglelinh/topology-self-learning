---
layout: post
title: "Lecture 08.00: Higher Homotopy Groups πₙ(X)"
lang: vi
lang-ref: lecture-08-00
chapter: 8
lecture: 0
categories: [chapter08]
tags: [higher-homotopy-groups, πn, homotopy-spheres, whitehead-theorem]
description: "Higher homotopy groups π_n(X): definition, properties, examples, Whitehead Theorem, và computational challenges"
---

**$\pi_n(X, x_0)$ — Vượt ra ngoài nhóm cơ bản**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Năm 1931, Heinz Hopf khiến cả giới toán học sững sờ khi phát hiện ra một ánh xạ liên tục từ **mặt cầu 3 chiều $$S^3$$ xuống mặt cầu 2 chiều $$S^2$$** mà **không thể co rút về một điểm**! Trực giác thông thường mách bảo rằng một mặt cầu chiều cao hơn bọc lên mặt cầu chiều thấp hơn ắt phải tầm thường — giống như nhóm đồng điều luôn cho $$H_3(S^2) = 0$$. Thế nhưng **phân thớ Hopf** chứng minh **$$\pi_3(S^2) \cong \mathbb{Z}$$**! Đó là cánh cửa mở ra thế giới đầy mê hoặc nhưng cũng đầy thử thách của các **nhóm đồng luân bậc cao $$\pi_n(X)$$**.

Nhóm cơ bản $\pi_1(X, x_0)$ phát hiện các lỗ một chiều thông qua lớp đồng luân của các vòng khép kín (ánh xạ từ $S^1$ vào $X$). Một câu hỏi tự nhiên đặt ra là điều gì xảy ra khi thay $S^1$ bằng mặt cầu $n$-chiều $S^n$ ($n \geq 2$). Câu trả lời dẫn đến các **nhóm đồng luân bậc cao** (higher homotopy groups) $\pi_n(X, x_0)$, được định nghĩa là tập các lớp đồng luân của các ánh xạ liên tục từ $S^n$ vào $X$ bảo toàn điểm cơ sở.

Các nhóm đồng luân bậc cao có hai đặc điểm nổi bật:
- **Tính đầy đủ đối với phức CW (Định lý Whitehead):** Một ánh xạ liên tục $f: X \to Y$ giữa hai phức CW là tương đương đồng luân nếu và chỉ nếu nó cảm sinh đẳng cấu $f_*: \pi_n(X) \xrightarrow{\cong} \pi_n(Y)$ với mọi $n$ (và mọi điểm cơ sở). Trong khi đó, hai không gian có thể có cùng nhóm đồng điều nhưng không tương đương đồng luân.
- **Tính giao hoán khi $n \geq 2$:** Khác với $\pi_1$ có thể không giao hoán, $\pi_n(X, x_0)$ luôn là nhóm Abel với mọi $n \geq 2$. Về mặt hình học, trong không gian từ hai chiều trở lên có đủ "chỗ" để trượt hai vùng ánh xạ qua nhau một cách liên tục.

Bên cạnh vai trò nền tảng trong tô-pô đại số, các nhóm đồng luân bậc cao còn xuất hiện trong lý thuyết chướng ngại (kiểm soát khả năng mở rộng ánh xạ qua các khung của phức CW), lý thuyết bó vectơ (phân loại bó qua các không gian Grassmann), và lý thuyết đồng luân ổn định (liên hệ với lý thuyết cobordism và $K$-theory).

![Higher homotopy groups](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Hopf_Fibration.png/400px-Hopf_Fibration.png)  
*Phân thớ Hopf — ví dụ kinh điển cho thấy $\pi_3(S^2) = \mathbb{Z}$, minh họa rằng mặt cầu chiều cao hơn có thể ánh xạ không tầm thường vào mặt cầu chiều thấp hơn - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hopf_Fibration.png)*

Tuy nhiên, khác với đồng điều, việc tính toán $\pi_n(X)$ rất khó khăn: ngay cả các nhóm $\pi_n(S^m)$ của các mặt cầu vẫn chưa có công thức đóng tổng quát, và $\pi_n(S^m)$ có thể khác không ngay cả khi $n > m$ (chẳng hạn $\pi_3(S^2) = \mathbb{Z}$).

Trong bài học này, ta sẽ tìm hiểu định nghĩa và cấu trúc nhóm của $\pi_n(X, x_0)$, lý luận Eckmann–Hilton giải thích tính Abel khi $n \geq 2$, các ví dụ cơ bản (điểm, không gian co rút được, $\pi_n(S^m)$, $\pi_n(S^1)$), Định lý Whitehead, Định lý Hurewicz, dãy khớp dài của phân thớ (fibration), cùng các thách thức tính toán và dãy ổn định.

---

## 🗺️ Kiến thức cần nhớ: Lý thuyết đồng luân bậc cao là gì và nghiên cứu những gì?

### 1. Tổng quát hóa vòng tròn thành mặt cầu $$n$$ chiều
- **Bản chất:** Nếu nhóm cơ bản $$\pi_1(X)$$ thả những sợi dây thun 1 chiều ($$S^1$$) vào trong không gian $$X$$ để dò lỗ 1 chiều, thì $$\pi_n(X)$$ thả những **quả bóng $$n$$ chiều** ($$S^n$$) vào $$X$$ và phân loại chúng theo biến dạng liên tục (đồng luân).
- **Lĩnh vực nghiên cứu:** Đo lường cấu trúc lỗ và cách quấn bậc cao của không gian tô-pô; kiểm soát khả năng mở rộng ánh xạ qua từng tầng khung của phức CW (lý thuyết chướng ngại).

### 2. Lý luận Eckmann–Hilton & Cấu trúc Đại số
- **Bản chất:** Trong 1 chiều, hai hạt cườm trên một sợi dây không thể vượt qua nhau nên $$\pi_1$$ có thể không giao hoán. Từ 2 chiều trở lên, hai hình vuông con trong $$I^n$$ có thừa chỗ để trượt vòng qua nhau — buộc $$\pi_n(X)$$ luôn là **nhóm Abel** với mọi $$n \ge 2$$.

### 3. Dãy khớp dài phân thớ & Cầu nối Hurewicz–Whitehead
- **Bản chất:** Khác với đồng điều $$H_n$$ tính dễ dàng nhờ cắt dán (Mayer–Vietoris), nhóm đồng luân $$\pi_n$$ không có tính cắt bỏ đơn giản. Công cụ tính toán mạnh nhất là **dãy khớp dài của phân thớ** $$F \to E \to B$$, cùng hai định lý cầu nối: **Hurewicz** (liên hệ nhóm $$\pi_n$$ đầu tiên khác không với $$H_n$$) và **Whitehead** (chứng minh hệ $$\{\pi_n\}$$ nắm giữ toàn bộ kiểu đồng luân của phức CW).

---

## 🧮 Ví dụ tính tay làm từng bước

### Ví dụ 1: Kiểm tra bằng tay Phân thớ Hopf $$h: S^3 \to S^2$$ và suy ra $$\pi_3(S^2) \cong \mathbb{Z}$$
Xem mặt cầu 3 chiều là $$S^3 = \{(z_1, z_2) \in \mathbb{C}^2 : \lvert z_1\rvert^2 + \lvert z_2\rvert^2 = 1\}$$ và xét ánh xạ Hopf tường minh:
$$
h(z_1, z_2) = \Bigl(2\operatorname{Re}(z_1\bar{z}_2),\; 2\operatorname{Im}(z_1\bar{z}_2),\; \lvert z_1\rvert^2 - \lvert z_2\rvert^2\Bigr) \in \mathbb{R}^3.
$$
1. **Kiểm tra ảnh nằm đúng trên mặt cầu $$S^2$$:** Tính tổng bình phương 3 tọa độ bằng tay! Vì $$(2\operatorname{Re} w)^2 + (2\operatorname{Im} w)^2 = 4\lvert w\rvert^2$$, ta có:
   $$
   \|h(z_1, z_2)\|^2 = 4\lvert z_1\rvert^2\lvert z_2\rvert^2 + \bigl(\lvert z_1\rvert^2 - \lvert z_2\rvert^2\bigr)^2 = \bigl(\lvert z_1\rvert^2 + \lvert z_2\rvert^2\bigr)^2 = 1^2 = 1!
   $$
2. **Kiểm tra mỗi thớ là một đường tròn $$S^1$$:** Nhân đồng thời cả hai tọa độ với số phức đơn vị $$e^{i\theta}$$: $$(e^{i\theta}z_1)\overline{(e^{i\theta}z_2)} = z_1\bar{z}_2$$ và $$\lvert e^{i\theta}z_k\rvert^2 = \lvert z_k\rvert^2$$, nên $$h(e^{i\theta}z_1, e^{i\theta}z_2) = h(z_1, z_2)$$! Chẳng hạn, nghịch ảnh của cực Bắc $$(0,0,1)$$ là đúng đường tròn $$\{(e^{i\theta}, 0) : \theta \in [0, 2\pi)\} \cong S^1$$.
3. **Đọc ngay $$\pi_3(S^2)$$ từ dãy khớp dài phân thớ $$S^1 \to S^3 \to S^2$$:** Vì không gian phủ phổ dụng của $$S^1$$ là $$\mathbb{R}$$ (co rút được), nên $$\pi_k(S^1) = 0$$ với mọi $$k \ge 2$$. Cắt một đoạn của dãy khớp dài:
   $$
   0 = \pi_3(S^1) \longrightarrow \pi_3(S^3) \xrightarrow{\;h_*\;} \pi_3(S^2) \longrightarrow \pi_2(S^1) = 0.
   $$
   Vì hai đầu đều bằng $$0$$, ánh xạ ở giữa $$h_*$$ bắt buộc là **đẳng cấu**! Mà $$\pi_3(S^3) \cong \mathbb{Z}$$, suy ra ngay:
   $$
   \pi_3(S^2) \cong \mathbb{Z}!
   $$

### Ví dụ 2: Kiểm chứng đại số Lý luận Eckmann–Hilton trong 3 dòng
Giả sử tập $$M$$ có hai phép toán hai ngôi $$\cdot$$ và $$\circ$$ cùng chung phần tử đơn vị $$e$$ và thỏa mãn luật hoán đổi $$(a \cdot b) \circ (c \cdot d) = (a \circ c) \cdot (b \circ d)$$ (trên $$I^2$$, đó là việc chia hình vuông thành 4 ô con theo hàng trước hay cột trước đều như nhau!).
1. Đặt $$b = c = e$$: $$(a\cdot e)\circ(e\cdot d) = (a\circ e)\cdot(e\circ d) \implies a \circ d = a \cdot d$$ (hai phép toán **trùng nhau**!).
2. Đặt $$a = d = e$$: $$(e\cdot b)\circ(c\cdot e) = (e\circ c)\cdot(b\circ e) \implies b \circ c = c \cdot b$$!
3. Kết hợp (1) và (2): $$b \cdot c = c \cdot b$$ — phép toán bắt buộc **giao hoán**!

### Giải thích: Vì sao $$\pi_n(X)$$ mạnh hơn $$H_n(X)$$ nhưng lại khó tính hơn rất nhiều?

#### Bước 1: Định nghĩa trực giác bằng khối lập phương $$I^n$$
Đồng nhất biên $$\partial I^n$$ về một điểm biến $$I^n/\partial I^n \cong S^n$$. Phép cộng $$f + g$$ đơn giản là đặt $$f$$ ở nửa trái $$t_1 \in [0, 1/2]$$ và $$g$$ ở nửa phải $$t_1 \in [1/2, 1]$$. Khi $$n \ge 2$$, tọa độ thứ hai $$t_2$$ cho phép trượt $$f$$ và $$g$$ vòng qua nhau, sinh ra tính giao hoán.

#### Bước 2: Sức mạnh tuyệt đối của $$\pi_n$$ (Định lý Whitehead)
Đồng điều $$H_n$$ đôi khi bị "mù" trước những xoắn tinh tế (như phân thớ Hopf bị $$H_3(S^2) = 0$$ bỏ qua). Ngược lại, **Định lý Whitehead** bảo đảm rằng giữa hai phức CW, chỉ cần một ánh xạ cảm sinh đẳng cấu trên mọi $$\pi_n$$ thì hai không gian đó chắc chắn tương đương đồng luân!

#### Bước 3: Cái giá phải trả — mất tính cắt bỏ
Đồng điều dễ tính vì có Định lý cắt bỏ (Excision) và dãy Mayer–Vietoris: xẻ không gian thành hai mảnh đơn giản rồi cộng ghép lại. Nhóm đồng luân **không** thỏa mãn cắt bỏ; ngay cả $$\pi_k(S^n)$$ với $$k > n$$ cũng chứa đầy các nhóm xoắn kỳ bí (như $$\pi_4(S^2) \cong \mathbb{Z}/2\mathbb{Z}$$, $$\pi_5(S^2) \cong \mathbb{Z}/2\mathbb{Z}$$...).

#### Bước 4: Chiến lược tính toán thực chiến
Để chinh phục $$\pi_n(X)$$, nhà tô-pô phối hợp ba vũ khí: (1) nâng lên không gian phủ phổ dụng $$\tilde{X}$$ (bảo toàn mọi $$\pi_n$$ với $$n \ge 2$$!), (2) kẹp vào **dãy khớp dài phân thớ** (như phân thớ Hopf ở trên), và (3) dùng **Định lý Hurewicz** để đọc nhóm $$\pi_n$$ đầu tiên khác không trực tiếp từ $$H_n$$!

$$
\text{Phân thớ }F \to E \to B
\;\xrightarrow{\;\text{Dãy khớp dài}\;}\;
\cdots \to \pi_n(F) \to \pi_n(E) \to \pi_n(B) \to \pi_{n-1}(F) \to \cdots
\;\xrightarrow{\;\text{Hurewicz \& Whitehead}\;}\;
\text{Phân loại kiểu đồng luân}.
$$

---

## 🎯 Định nghĩa và Tính chất cơ bản

### 1. Định nghĩa và trực giác hình học

Trong khi $\pi_1(X, x_0)$ xét các ánh xạ từ $S^1$ vào $X$ giữ cố định điểm cơ sở, nhóm đồng luân bậc $n$ tổng quát hóa ý tưởng này bằng cách dùng mặt cầu $n$-chiều $S^n = \{x \in \mathbb{R}^{n+1} : \|x\| = 1\}$ với điểm cơ sở $s_0 = (1, 0, \ldots, 0)$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Nhóm đồng luân bậc $n$):**  
Cho $X$ là không gian tô-pô với điểm cơ sở $x_0 \in X$. Một **ánh xạ có điểm cơ sở** (based map) là ánh xạ liên tục $f: (S^n, s_0) \to (X, x_0)$ thỏa mãn $f(s_0) = x_0$. Hai ánh xạ $f, g$ gọi là **đồng luân bảo toàn điểm cơ sở** nếu tồn tại phép đồng luân $H: S^n \times [0,1] \to X$ nối $f$ với $g$ sao cho $H(s_0, t) = x_0$ với mọi $t \in [0,1]$. Tập hợp tất cả các lớp đồng luân $[f]$ như vậy được ký hiệu là $\pi_n(X, x_0)$.
</div>

Một cách định nghĩa tương đương và thuận tiện hơn trong chứng minh là dùng khối lập phương đơn vị $I^n = [0,1]^n$. Do không gian thương $I^n / \partial I^n$ đồng phôi với $S^n$, mỗi ánh xạ $(S^n, s_0) \to (X, x_0)$ tương ứng một-một với một ánh xạ liên tục $(I^n, \partial I^n) \to (X, x_0)$ đưa toàn bộ biên $\partial I^n$ về $x_0$:

$$
\pi_n(X, x_0) = [(I^n, \partial I^n), (X, x_0)]
$$

---

### 2. Cấu trúc nhóm và phép cộng

Để trang bị cấu trúc nhóm trên $\pi_n(X, x_0)$, ta sử dụng mô tả qua khối lập phương $I^n$ (tương đương với ánh xạ bóp — pinch map — trên $S^n$). Chia $I^n$ thành hai nửa dọc theo tọa độ thứ nhất $t_1 \in [0, 1/2]$ và $t_1 \in [1/2, 1]$, rồi định nghĩa tổng $f + g: (I^n, \partial I^n) \to (X, x_0)$ bằng cách co giãn $f$ lên nửa đầu và $g$ lên nửa sau:

$$(f + g)(t_1, t_2, \ldots, t_n) = \begin{cases} f(2t_1, t_2, \ldots, t_n) & \text{nếu } 0 \leq t_1 \leq \tfrac{1}{2} \\ g(2t_1 - 1, t_2, \ldots, t_n) & \text{nếu } \tfrac{1}{2} \leq t_1 \leq 1 \end{cases}$$

Tại siêu phẳng chung $t_1 = 1/2$, cả hai vế đều nhận giá trị $x_0$ nên $f + g$ liên tục. Phép toán $[f] + [g] = [f + g]$ xác định tốt trên các lớp đồng luân và thỏa mãn các tiên đề nhóm:

![Group operation](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Sum_in_homotopy_groups.svg/400px-Sum_in_homotopy_groups.svg.png)  
*Phép cộng trong $\pi_n$ xây dựng bằng cách chia miền thành hai phần cho $f$ và $g$ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Sum_in_homotopy_groups.svg)*

- **Phần tử đơn vị:** Lớp $[c]$ của ánh xạ hằng $c(I^n) = \{x_0\}$. Trong $f + c$, ta có thể co giãn liên tục miền của $f$ ra toàn bộ $[0,1]$ nên $[f] + [c] = [f]$.
- **Phần tử nghịch đảo:** Lớp $[-f]$, với $(-f)(t_1, t_2, \ldots, t_n) = f(1 - t_1, t_2, \ldots, t_n)$ (phản xạ theo tọa độ thứ nhất). Ta có thể biến dạng liên tục $f + (-f)$ về ánh xạ hằng, nên $[f] + [-f] = 0$.
- **Tính kết hợp:** Cả $(f + g) + h$ và $f + (g + h)$ đều đồng luân với ánh xạ chia $I^n$ thành ba phần bằng nhau ứng với $f, g, h$.

Khi $n = 1$, cấu trúc này trùng khớp hoàn toàn với nhóm cơ bản $\pi_1(X, x_0)$.

---

### 3. Tính giao hoán và Lý luận Eckmann–Hilton

Khác với nhóm cơ bản $\pi_1$ có thể không giao hoán (chẳng hạn với hình số tám $S^1 \vee S^1$ hoặc mặt đóng có giống $g \geq 2$), các nhóm đồng luân bậc cao từ $n = 2$ trở lên luôn giao hoán.

<div class="textbook-theorem" markdown="1">
**Định lý (Eckmann–Hilton):**  
Với mọi $n \geq 2$, nhóm đồng luân $\pi_n(X, x_0)$ là **nhóm Abel**: $[f] + [g] = [g] + [f]$ với mọi $[f], [g] \in \pi_n(X, x_0)$.
</div>

**Ý tưởng chứng minh:** Vì $n \geq 2$, trong khối lập phương $I^n$ ta có ít nhất hai tọa độ tự do. Xuất phát từ cấu hình của $f + g$ (miền của $f$ ở nửa trái, miền của $g$ ở nửa phải), ta thu nhỏ miền tác động của $f$ và $g$ thành hai hình vuông con rời nhau nằm trong $I^n$ (phần còn lại ánh xạ vào $x_0$), sau đó trượt hai hình vuông con này vòng qua nhau trong mặt phẳng hai tọa độ $(t_1, t_2)$ rồi phóng lớn trở lại thành cấu hình của $g + f$.

![Eckmann-Hilton argument visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Sum_in_homotopy_groups.svg/400px-Sum_in_homotopy_groups.svg.png)  
*Minh họa phép trượt hai miền ánh xạ trong lý luận Eckmann–Hilton - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Sum_in_homotopy_groups.svg)*

Cách làm này không thực hiện được khi $n = 1$ vì trên đoạn thẳng $[0,1]$ hai đoạn con không thể trượt vượt qua nhau mà không cắt nhau. Theo cách phát biểu đại số của lý luận Eckmann–Hilton, với $n \geq 2$ ta có thể định nghĩa phép cộng dọc theo tọa độ thứ nhất hoặc tọa độ thứ hai; hai phép toán này tương thích với nhau và có cùng phần tử đơn vị, suy ra chúng trùng nhau và giao hoán.

<div class="textbook-theorem" markdown="1">
**Hệ quả:** Với mọi $n \geq 2$, $\pi_n(X, x_0)$ là một **nhóm Abel**, nên thường được viết bằng ký hiệu cộng và có thể áp dụng các công cụ của lý thuyết nhóm Abel.
</div>

---

### 4. Sự độc lập với điểm cơ sở

<div class="textbook-theorem" markdown="1">
**Định lý:** Nếu $X$ liên thông đường thì với mọi hai điểm cơ sở $x_0, x_1 \in X$, hai nhóm $\pi_n(X, x_0)$ và $\pi_n(X, x_1)$ đẳng cấu với nhau.
</div>

Tương tự như với nhóm cơ bản, mỗi đường đi $\gamma$ nối $x_0$ với $x_1$ cảm sinh một đẳng cấu $\beta_\gamma: \pi_n(X, x_1) \xrightarrow{\cong} \pi_n(X, x_0)$ bằng cách kéo dần điểm cơ sở của $S^n$ dọc theo $\gamma$. Vì vậy, đối với không gian liên thông đường, ta thường viết gọn $\pi_n(X)$ khi chỉ xét đến sai khác một đẳng cấu. Tuy nhiên, đẳng cấu này phụ thuộc vào lớp đồng luân của đường đi $\gamma$: các vòng đóng tại $x_0$ tạo ra một tác động của $\pi_1(X, x_0)$ lên $\pi_n(X, x_0)$.

---

## 📊 Ví dụ và Tính toán

### Ví dụ 1: Không gian một điểm

Với $X = \{\text{pt}\}$, mọi ánh xạ $S^n \to \{\text{pt}\}$ đều là ánh xạ hằng, do đó **$\pi_n(\text{pt}) = 0$** với mọi $n \geq 1$.

---

### Ví dụ 2: Không gian co rút được

Các nhóm đồng luân là bất biến đồng luân: nếu $X \simeq Y$ thì $\pi_n(X) \cong \pi_n(Y)$. Do đó, mọi không gian co rút được (như $\mathbb{R}^n$, đĩa $D^n$, hình nón $CX$) đều có $\pi_n(X) \cong \pi_n(\text{pt}) = 0$ với mọi $n \geq 1$.

---

### Ví dụ 3: $\pi_n(S^n) \cong \mathbb{Z}$

Đối với mặt cầu $n$-chiều $S^n$ ($n \geq 1$), ta có kết quả cơ bản **$\pi_n(S^n) \cong \mathbb{Z}$**. Đẳng cấu được cho bởi **bậc (degree)** của ánh xạ liên tục $f: S^n \to S^n$: hai ánh xạ $S^n \to S^n$ đồng luân với nhau nếu và chỉ nếu chúng có cùng bậc, và phép cộng trong $\pi_n(S^n)$ tương ứng với phép cộng các bậc $\deg(f + g) = \deg(f) + \deg(g)$. Phần tử sinh của $\pi_n(S^n)$ là lớp đồng luân của ánh xạ đồng nhất $\text{id}_{S^n}$ (bậc $1$). Kết quả này mở rộng trực tiếp đẳng cấu $\pi_1(S^1) \cong \mathbb{Z}$.

---

### Ví dụ 4: $\pi_k(S^n) = 0$ khi $k < n$

Nếu $k < n$ thì **$\pi_k(S^n) = 0$**. Lý do cốt lõi là mọi ánh xạ liên tục $f: S^k \to S^n$ đều đồng luân với một ánh xạ trơn (hoặc ánh xạ tế bào) không toàn ánh, tức là ảnh của nó bỏ sót ít nhất một điểm $p \in S^n$. Vì $S^n \setminus \{p\} \cong \mathbb{R}^n$ co rút được, ánh xạ này đồng luân với ánh xạ hằng. Về trực giác, một mặt cầu chiều thấp hơn không thể "bọc" không tầm thường quanh một mặt cầu chiều cao hơn.

---

### Ví dụ 5: $\pi_k(S^n)$ khi $k > n$

Trái với đồng điều (nơi $H_k(S^n) = 0$ với mọi $k > n$), các nhóm đồng luân $\pi_k(S^n)$ khi $k > n$ nói chung **không tầm thường** và rất phức tạp.

Ví dụ kinh điển đầu tiên là **$\pi_3(S^2) \cong \mathbb{Z}$**, sinh bởi **phân thớ Hopf** (Hopf fibration) $S^1 \to S^3 \to S^2$. Ở các bậc tiếp theo ta còn gặp các nhóm xoắn như **$\pi_4(S^3) \cong \mathbb{Z}/2\mathbb{Z}$** và **$\pi_5(S^3) \cong \mathbb{Z}/2\mathbb{Z}$**.

![Hopf fibration](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/Hopf_Fibration_showing_Hopf_coordinate_system.png/500px-Hopf_Fibration_showing_Hopf_coordinate_system.png)  
*Phân thớ Hopf ánh xạ $S^3$ lên $S^2$ với các thớ là đường tròn $S^1$ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hopf_Fibration_showing_Hopf_coordinate_system.png)*

Một quy luật quan trọng được cho bởi **Định lý treo Freudenthal** (Freudenthal Suspension Theorem): với mỗi $k \geq 0$ cố định, khi $k \leq n - 2$ (tức $n + k \leq 2n - 2$), dãy nhóm đồng luân ổn định:

$$
\pi_{n+k}(S^n) \cong \pi_{n+k+1}(S^{n+1})
$$

Giá trị giới hạn này gọi là **nhóm đồng luân ổn định của mặt cầu**, ký hiệu $\pi_k^s$. Dù có cấu trúc đại số phong phú và liên hệ mật thiết với lý thuyết cobordism và $K$-theory, việc tính $\pi_k^s$ cho các $k$ lớn vẫn là một bài toán mở lớn của tô-pô đại số.

---

### Ví dụ 6: $\pi_n(S^1)$

Đường tròn $S^1$ có không gian phủ phổ dụng là $\mathbb{R}$ (co rút được). Vì mọi ánh xạ $S^n \to S^1$ với $n \geq 2$ đều nâng được lên $\mathbb{R}$ (do $S^n$ đơn liên khi $n \geq 2$), mọi ánh xạ như vậy đều đồng luân với ánh xạ hằng. Do đó:
- $\pi_1(S^1) = \mathbb{Z}$,
- $\pi_n(S^1) = 0$ với mọi $n \geq 2$.

Theo thuật ngữ tô-pô đại số, $S^1$ là một không gian Eilenberg–MacLane kiểu $K(\mathbb{Z}, 1)$.

---

## 🔗 Các Định lý Cơ bản

### 1. Định lý Whitehead

<div class="textbook-theorem" markdown="1">
**Định lý (J.H.C. Whitehead):**  
Cho $f: X \to Y$ là một ánh xạ liên tục giữa hai phức CW. Nếu $f$ cảm sinh các đẳng cấu:

$$
f_* : \pi_n(X) \xrightarrow{\cong} \pi_n(Y) \quad \forall n \geq 0
$$

(tại mọi điểm cơ sở) thì **$f$ là một tương đương đồng luân**.
</div>

Định lý Whitehead cho thấy trên phạm trù các phức CW, một ánh xạ bảo toàn mọi nhóm đồng luân (tương đương đồng luân yếu) chính là một tương đương đồng luân thực sự. Lưu ý hai điều kiện quan trọng: thứ nhất, các đẳng cấu phải được cảm sinh bởi *cùng một ánh xạ* $f: X \to Y$ (chỉ biết $\pi_n(X) \cong \pi_n(Y)$ một cách trừu tượng là chưa đủ); thứ hai, giả thiết $X, Y$ là phức CW là cần thiết cho kết luận tổng quát.

---

### 2. Định lý Hurewicz

Định lý Hurewicz liên hệ trực tiếp các nhóm đồng luân với các nhóm đồng điều (vốn thường dễ tính hơn).

<div class="textbook-theorem" markdown="1">
**Định lý (Hurewicz):**  
Cho $X$ là một không gian liên thông đường.

- **Phần 1 ($n = 1$):** Tồn tại đồng cấu tự nhiên toàn ánh $h: \pi_1(X, x_0) \to H_1(X)$ gửi lớp đồng luân của một vòng về lớp đồng điều của nó, với hạt nhân là nhóm con giao hoán tử $[\pi_1(X, x_0), \pi_1(X, x_0)]$. Do đó $H_1(X)$ đẳng cấu với Abel hóa (abelianization) của $\pi_1(X, x_0)$.
- **Phần 2 ($n \geq 2$):** Xét đồng cấu Hurewicz $h_n: \pi_n(X, x_0) \to H_n(X)$ xác định bởi $h_n([f]) = f_*([S^n])$, trong đó $[S^n]$ là phần tử sinh của $H_n(S^n) \cong \mathbb{Z}$. Nếu $\pi_k(X, x_0) = 0$ với mọi $1 \leq k < n$, thì:

$$
h_n : \pi_n(X) \xrightarrow{\cong} H_n(X)
$$

là một **đẳng cấu**.
</div>

Nói gọn lại, đối với một không gian đơn liên, nhóm đồng luân đầu tiên khác không luôn trùng với nhóm đồng điều ở cùng bậc đó. Chẳng hạn, $S^2$ đơn liên nên $\pi_2(S^2) \cong H_2(S^2) \cong \mathbb{Z}$. Tuy nhiên, ở các bậc cao hơn, đồng luân và đồng điều tách rời nhau: $\pi_3(S^2) = \mathbb{Z}$ trong khi $H_3(S^2) = 0$.

---

### 3. Dãy khớp dài của phân thớ (Fibration)

Một **phân thớ theo nghĩa Hurewicz/Serre** (fibration) $p: E \to B$ với thớ $F = p^{-1}(b_0)$ (ký hiệu $F \to E \to B$) là ánh xạ thỏa mãn tính chất nâng đồng luân; mọi bó thớ cục bộ tầm thường trên không gian cơ sở paracompact đều là một fibration.

<div class="textbook-theorem" markdown="1">
**Định lý:** Mọi fibration $F \to E \to B$ cảm sinh một dãy khớp dài các nhóm đồng luân:

$$
\cdots \to \pi_n(F) \to \pi_n(E) \to \pi_n(B) \xrightarrow{\partial} \pi_{n-1}(F) \to \cdots
$$
</div>

**Ví dụ (Phân thớ Hopf):** Áp dụng dãy khớp dài cho phân thớ Hopf $S^1 \to S^3 \to S^2$:

$$
\pi_3(S^1) \to \pi_3(S^3) \to \pi_3(S^2) \xrightarrow{\partial} \pi_2(S^1)
$$

Vì $\pi_3(S^1) = \pi_2(S^1) = 0$ và $\pi_3(S^3) \cong \mathbb{Z}$, đoạn dãy trở thành:

$$
0 \to \mathbb{Z} \to \pi_3(S^2) \to 0
$$

Tính khớp cho ngay **$\pi_3(S^2) \cong \mathbb{Z}$**.

---

## 🧮 Thách thức Tính toán

### Vì sao $\pi_n(S^m)$ khó tính?

1. **Không có định lý van Kampen hay dãy Mayer–Vietoris:** Không có phương pháp đơn giản nào để ghép các nhóm đồng luân bậc cao của $A \cup B$ từ các nhóm đồng luân của $A$, $B$ và $A \cap B$.
2. **Sự phụ thuộc tích lũy:** Trong lý thuyết chướng ngại, việc phân tích bậc $n$ đòi hỏi thông tin từ tất cả các bậc thấp hơn $\pi_k$ ($k < n$).
3. **Thiếu công thức đóng ở miền không ổn định:** $\pi_n(S^m)$ biến thiên phức tạp theo cả $n$ và $m$, chỉ bắt đầu thể hiện quy luật khi đi vào miền ổn định.

### Một số giá trị đã biết

| $n \setminus m$ | $S^1$ | $S^2$ | $S^3$ | $S^4$ |
|---|---|---|---|---|
| 1 | $\mathbb{Z}$ | $0$ | $0$ | $0$ |
| 2 | $0$ | $\mathbb{Z}$ | $0$ | $0$ |
| 3 | $0$ | $\mathbb{Z}$ | $\mathbb{Z}$ | $0$ |
| 4 | $0$ | $\mathbb{Z}/2$ | $\mathbb{Z}/2$ | $\mathbb{Z}$ |
| 5 | $0$ | $\mathbb{Z}/2$ | $\mathbb{Z}/2$ | $\mathbb{Z}/2$ |

### Nhóm đồng luân ổn định

Theo Định lý treo Freudenthal, với mỗi $k \geq 0$ cố định, nhóm ổn định được xác định bởi:

$$
\pi_k^s = \lim_{n \to \infty} \pi_{n+k}(S^n)
$$

Một vài giá trị đầu tiên:
- $\pi_0^s = \mathbb{Z}$,
- $\pi_1^s = \mathbb{Z}/2\mathbb{Z}$,
- $\pi_2^s = \mathbb{Z}/2\mathbb{Z}$,
- $\pi_3^s = \mathbb{Z}/24\mathbb{Z}$.

---

## 🌉 Định lý Hurewicz, Định lý Whitehead và Phê chuẩn Đồng luân

Theo Chương 9 của [*Algebraic Topology* (L. Maxim)](https://people.math.wisc.edu/~lmaxim/topbookf.pdf), hai định lý trụ cột nối liền thế giới đồng luân $\pi_n$ và thế giới đồng điều $H_n$ là:

1. **Định lý Hurewicz:** Nếu $X$ là không gian $(n-1)$-liên thông ($\pi_k(X) = 0$ với mọi $k < n$, $n \ge 2$), thì đồng cấu Hurewicz $h: \pi_n(X) \xrightarrow{\sim} H_n(X; \mathbb{Z})$ là một **đẳng cấu** (và khi $n=1$, $H_1(X) \cong \pi_1(X)_{\mathrm{ab}}$ là Abel hoá của $\pi_1$).
   - Hệ quả tức thì: với $S^n$ ($n \ge 2$), $\pi_n(S^n) \cong H_n(S^n) \cong \mathbb{Z}$, nhưng $\pi_{n+1}(S^n)$ không thể tính bằng đồng điều mà cần đến **phân thớ Hopf** và **dãy phổ Serre**!
2. **Định lý Whitehead:** Một ánh xạ liên tục $f: X \to Y$ giữa các **phức CW liên thông** là một tương đương đồng luân khi và chỉ khi $f_*: \pi_n(X) \to \pi_n(Y)$ là đẳng cấu với mọi $n \ge 1$ (tức là các nhóm đồng luân phát hiện trọn vẹn kiểu đồng luân của phức CW — điều mà đồng điều không làm được!).

## 🧠 Tài liệu kinh điển & Tham khảo

### Công trình kinh điển

1. **Heinz Hopf** - *"Über die Abbildungen der dreidimensionalen Sphäre"* (1931)  
   *Phân thớ Hopf, $\pi_3(S^2) = \mathbb{Z}$*

2. **Witold Hurewicz** - *"Beiträge zur Topologie der Deformationen"* (1935-36)  
   *Định lý Hurewicz*

3. **Hans Freudenthal** - *"Über die Klassen der Sphärenabbildungen"* (1937)  
   *Định lý treo và đồng luân ổn định*

4. **J.H.C. Whitehead** - *"Combinatorial homotopy"* (1949)  
   *Định lý Whitehead*

5. **Jean-Pierre Serre** - *"Groupes d'homotopie et classes de groupes abéliens"* (1953)  
   *Kỹ thuật tính toán và dãy phổ*

### Giáo trình

6. **Allen Hatcher** - *Algebraic Topology*, **§4.1: Higher Homotopy Groups**

7. **Edwin H. Spanier** - *Algebraic Topology*, **Chapter 7**

8. **Robert M. Switzer** - *Algebraic Topology - Homotopy and Homology*

9. **George W. Whitehead** - *Elements of Homotopy Theory*

---

## 🔗 Ứng dụng và Liên kết

### Lý thuyết chướng ngại (Obstruction Theory)
Nhóm $\pi_n(Y)$ kiểm soát các chướng ngại khi mở rộng ánh xạ $f: X^{(n)} \to Y$ lên khung $X^{(n+1)}$; nếu $\pi_n(Y) = 0$ thì không có chướng ngại ở bước đó.

### Bó vectơ (Vector Bundles)
Các nhóm đồng luân của các không gian Grassmann (và các nhóm Lie) dùng để phân loại bó vectơ trên mặt cầu và các phức CW.

### Lý thuyết Cobordism
Thông qua không gian Thom, các nhóm đồng luân ổn định cho phép tính các vành cobordism của đa tạp trơn.

### Lý thuyết dây (String Theory)
Các ánh xạ $S^n \to M$ vào không gian đích mô tả các cấu hình brane, trong đó các nhóm đồng luân phân loại các số quấn (wrapping numbers) tô-pô.

### Robot học
Trong không gian cấu hình, $\pi_n$ phát hiện các chướng ngại tô-pô bậc cao liên quan đến lập kế hoạch chuyển động.

---

## Video tham khảo

- **xem trước** [A Sphere is a Loop of Loops (Visualizing Homotopy Groups)](https://www.youtube.com/watch?v=CxGtAuJdjYI) — Dennis Sweeney, tiếng Anh. Hình cầu như một vòng của các vòng, giúp hình dung $\pi_n$ trước định nghĩa hình thức.
- [The fundamental group and higher homotopy groups](https://www.youtube.com/watch?v=7RYu7uvomUs) — DanielChanMaths, tiếng Anh. Daniel Chan nối $\pi_1$ với các nhóm đồng luân bậc cao, sát phần tính toán của bài.

## 🧩 Bài tập

### Định nghĩa

1. **Kiểm chứng cấu trúc nhóm:** Kiểm tra tường minh các tiên đề nhóm của $\pi_n(X)$ trong trường hợp $n = 1$ với $X = S^1$.

2. **Tính Abel:** Giải thích trực quan vì sao $\pi_2(X)$ là nhóm giao hoán bằng ý tưởng trượt các hình vuông con.

### Ví dụ

3. **Một điểm:** Tính $\pi_n(\text{point})$ với mọi $n \geq 1$.

4. **Không gian co rút được:** Từ tính co rút được của $\mathbb{R}^3$, suy ra $\pi_n(\mathbb{R}^3)$.

5. **Đường tròn $S^1$:** Kiểm chứng $\pi_n(S^1) = 0$ với mọi $n \geq 2$ bằng không gian phủ $\mathbb{R} \to S^1$.

### Định lý Whitehead

6. **Áp dụng:** Cho $f: X \to Y$ là ánh xạ liên tục giữa hai phức CW cảm sinh đẳng cấu $f_*: \pi_n(X) \cong \pi_n(Y)$ với mọi $n \geq 0$. Ta có thể kết luận gì về $f$?

7. **Phản ví dụ:** Tìm một ví dụ hai không gian có các nhóm đồng điều đẳng cấu nhưng không tương đương đồng luân.

### Định lý Hurewicz

8. **Mặt cầu $S^2$:** Áp dụng Định lý Hurewicz để suy ra $\pi_2(S^2) \cong H_2(S^2) = \mathbb{Z}$.

9. **Giới hạn của Hurewicz:** Vì sao Định lý Hurewicz không cho phép tính $\pi_3(S^2)$ từ $H_3(S^2) = 0$?

### Phân thớ Hopf

10. **Tìm hiểu:** Đọc về phân thớ Hopf $S^3 \to S^2$ và giải thích vì sao nó là phần tử sinh của $\pi_3(S^2)$.

11. **Hình dung hình học:** Tìm hiểu cấu trúc các thớ tròn $S^1$ trong phân thớ Hopf và cách chúng móc nối với nhau trong $S^3$.

### Dãy khớp dài

12. **Áp dụng:** Sử dụng dãy khớp dài của phân thớ Hopf $S^1 \to S^3 \to S^2$ để tính $\pi_3(S^2)$ từ $\pi_*(S^1)$ và $\pi_*(S^3)$.

13. **Trường hợp tổng quát:** Với fibration $F \to E \to B$, mô tả cách hoạt động của đồng cấu nối $\partial: \pi_n(B) \to \pi_{n-1}(F)$.

### Nâng cao

14. **Nhóm $\pi_4(S^3)$:** Tìm hiểu cách chứng minh $\pi_4(S^3) = \mathbb{Z}/2\mathbb{Z}$.

15. **Đồng luân ổn định:** Xác định nhóm đồng luân ổn định $\pi_1^s$ ($\mathbb{Z}/2\mathbb{Z}$, sinh bởi ánh xạ Hopf).

16. **Tháp Postnikov:** Tìm hiểu khái niệm tháp Postnikov dùng để triệt tiêu lần lượt các nhóm đồng luân.

### Câu hỏi suy ngẫm

17. **Độ khó tính toán:** Liệt kê các nguyên nhân khiến việc tính $\pi_n(S^m)$ khó hơn nhiều so với $H_n(S^m)$.

18. **So sánh:** So sánh $\pi_n$ và $H_n$ về khả năng tính toán và lượng thông tin tô-pô mang lại.

19. **Ứng dụng:** Nêu các lĩnh vực mà nhóm đồng luân bậc cao đóng vai trò quan trọng.

20. **Bài toán mở:** Tìm hiểu một số bài toán mở hiện nay trong lý thuyết đồng luân.

---

## 📚 Đọc thêm

- **Hatcher, §4:** Nhóm đồng luân bậc cao và phân thớ.
- **Whitehead:** *Elements of Homotopy Theory* (tài liệu hệ thống).
- **Spanier, Chapter 7:** Trình bày lý thuyết chi tiết.
- **Switzer:** *Algebraic Topology* (đồng luân ổn định).
- **Ravenel:** *Complex Cobordism and Stable Homotopy Groups* (nâng cao).

---

## 🎓 Tóm tắt

Các nhóm đồng luân bậc cao $\pi_n(X, x_0)$ mở rộng nhóm cơ bản lên mọi chiều thông qua các lớp đồng luân của ánh xạ $(S^n, s_0) \to (X, x_0)$ (hay $(I^n, \partial I^n) \to (X, x_0)$). Với $n \geq 2$, $\pi_n(X)$ luôn là nhóm Abel theo lý luận Eckmann–Hilton. Ta có các kết quả cơ bản $\pi_n(S^n) \cong \mathbb{Z}$, $\pi_k(S^n) = 0$ khi $k < n$, và $\pi_n(S^1) = 0$ khi $n \geq 2$, trong khi trường hợp $k > n$ rất phức tạp và chỉ ổn định thành $\pi_k^s$ trong miền Freudenthal ($k \leq n - 2$).

Ba công cụ lý thuyết chủ đạo là Định lý Whitehead (ánh xạ cảm sinh đẳng cấu trên mọi $\pi_n$ giữa các phức CW là tương đương đồng luân), Định lý Hurewicz (nhóm đồng luân khác không đầu tiên của không gian đơn liên đẳng cấu với nhóm đồng điều tương ứng), và dãy khớp dài của fibration (cho phép tính các kết quả như $\pi_3(S^2) \cong \mathbb{Z}$).

**Tiếp theo:** Bó thớ (Fiber Bundles) — cấu trúc hình học tầm thường địa phương nhưng có thể xoắn toàn cục.

---

*"Homotopy groups: where spheres become mysteries, and topology meets the unknown."*

---

**Previous Chapter:** [Chapter 07: Homology Theory](/contents/vi/topology-chapter07/)  
**Next:** [Lecture 08.01: Fiber Bundles](/contents/vi/topology-chapter08/08_01_Fiber_Bundles/)
