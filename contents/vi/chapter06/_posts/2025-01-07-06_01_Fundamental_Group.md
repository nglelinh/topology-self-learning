---
layout: post
title: "Lecture 06.01: The Fundamental Group"
lang: vi
lang-ref: lecture-06-01
chapter: 6
lecture: 1
categories: [chapter06]
tags: [fundamental-group, π1, group-structure, basepoint, path-connected]
description: "Fundamental group π₁(X,x₀): định nghĩa, group structure, invariance, và ý nghĩa hình học"
---

**Nhóm cơ bản $\pi_1(X, x_0)$ – Bất biến đại số đầu tiên**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Hãy tưởng tượng bạn buộc một sợi dây thun vào một chiếc cọc cố định $$x_0$$ trên mặt đất, cầm đầu dây đi dạo một vòng khắp không gian $$X$$ rồi buộc lại vào đúng chiếc cọc $$x_0$$. Nếu không gian phẳng phiu không có vật cản, bạn luôn thu gọn sợi dây về sát chiếc cọc. Nhưng nếu có một cái cột (lỗ thủng) ở giữa, sợi dây có thể quấn quanh cột 1 vòng, 2 vòng, hay ngược chiều $$-1$$ vòng mà không thể tháo ra được! Năm 1895, Henri Poincaré đã biến trò thả dây ấy thành một **nhóm đại số** thực thụ mang tên **Nhóm cơ bản $$\pi_1(X, x_0)$$** — chiếc cầu vàng đầu tiên dịch tô-pô sang lý thuyết nhóm!

Từ khái niệm đồng luân đường ở bài học trước, chúng ta xây dựng bất biến đại số đầu tiên của tô-pô học: **nhóm cơ bản** (fundamental group).

> **Với mỗi không gian có điểm cơ sở $(X, x_0)$, ta gán một nhóm $\pi_1(X, x_0)$ có các phần tử là các lớp đồng luân đường của các vòng khép kín tại $x_0$.**

Cách tiếp cận do Henri Poincaré khởi xướng năm 1895 chuyển câu hỏi hình học về không gian thành câu hỏi đại số về nhóm. Nhóm cơ bản có thể tính toán được cho nhiều lớp không gian, cho phép phân biệt các không gian không đồng phôi, chứng minh các định lý như định lý điểm bất động Brouwer và định lý đường cong Jordan, đồng thời mở đường cho lý thuyết không gian phủ, đồng điều và các nhóm đồng luân bậc cao.

![Fundamental group visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Fundamental_group.svg/500px-Fundamental_group.svg.png)  
*Minh họa các vòng khép kín và cấu trúc nhóm cơ bản*

Trong bài học này, chúng ta sẽ xây dựng tường minh $\pi_1(X, x_0)$, kiểm chứng các tiên đề nhóm với phép nối đường đi, phân tích một số ví dụ cơ bản ($\mathbb{R}^n$, $S^1$, $S^n$ với $n \ge 2$, $T^2$), chứng minh tính độc lập (sai khác đẳng cấu) đối với điểm cơ sở trên không gian liên thông đường, đồng thời thiết lập tính hàm tử (functoriality) và tính bất biến đồng luân của $\pi_1$.

---

## 🗺️ Kiến thức cần nhớ: Nhóm cơ bản $$\pi_1(X, x_0)$$ là gì và hoạt động như thế nào?

### 1. Hàm tử từ Tô-pô sang Lý thuyết Nhóm ($$\mathbf{Top}_* \to \mathbf{Grp}$$)
- **Bản chất:** Nhóm cơ bản gán cho mỗi không gian có điểm gốc $$(X, x_0)$$ một nhóm $$\pi_1(X, x_0)$$ (tập các lớp đồng luân của vòng khép kín tại $$x_0$$ với phép nối vòng $$[\alpha]\cdot[\beta] = [\alpha * \beta]$$), và gán cho mỗi ánh xạ liên tục $$f: (X, x_0) \to (Y, y_0)$$ một **đồng cấu nhóm** $$f_*: \pi_1(X, x_0) \to \pi_1(Y, y_0)$$.
- **Hệ quả vàng:** Nếu $$X \simeq Y$$ (đặc biệt nếu $$X \cong Y$$), thì **$$\pi_1(X) \cong \pi_1(Y)$$**! Muốn chứng minh hai không gian không đồng phôi, chỉ cần chứng minh nhóm cơ bản của chúng không đẳng cấu!

### 2. Tính Đơn liên (Simply Connected)
- **Bản chất:** Không gian liên thông đường có $$\pi_1(X) = \{1\}$$ (mọi vòng đều co về một điểm) gọi là **đơn liên** — ví dụ $$\mathbb{R}^n$$, đĩa $$D^n$$, và mặt cầu $$S^n$$ (với $$n \ge 2$$!).

### 3. Tính Giao hoán vs. Không Giao hoán của $$\pi_1$$
- **Điểm cực kỳ thú vị:** Khác với đồng điều $$H_1$$ luôn giao hoán, **$$\pi_1$$ có thể KHÔNG giao hoán**! Trên hình số 8 ($$S^1 \vee S^1$$), đi vòng trái $$a$$ rồi vòng phải $$b$$ khác hẳn đi vòng phải $$b$$ rồi vòng trái $$a$$ ($$ab \neq ba$$)! Chính vì vậy $$\pi_1$$ nhạy hơn $$H_1$$ trong việc phân biệt các không gian có nhiều lỗ nối chung.

---

## 🧮 Ví dụ tính tay làm từng bước: So sánh $$\pi_1(T^2)$$ (giao hoán) vs. $$\pi_1(S^1 \vee S^1)$$ (không giao hoán)

1. **Kiểm tra công thức phép nối vòng và phần tử nghịch đảo:**
   Cho hai vòng $$\alpha, \beta: [0,1] \to X$$ tại $$x_0$$. Phép nối $$(\alpha * \beta)(s)$$ chạy gấp đôi tốc độ trên $$\alpha$$ ở nửa đầu $$[0, \tfrac{1}{2}]$$ và chạy trên $$\beta$$ ở nửa sau $$[\tfrac{1}{2}, 1]$$. Vòng ngược là $$\bar{\alpha}(s) = \alpha(1 - s)$$.
   Để chứng minh $$[\alpha * \bar{\alpha}] = [c_{x_0}]$$ bằng tay, ta chỉ cần kéo tụt điểm quay đầu lùi dần về $$0$$ qua công thức đồng luân tường minh:
   $$
   H(s, t) = \begin{cases} \alpha(2s) & \text{nếu } 0 \le s \le \frac{1-t}{2}, \\ \alpha(1-t) & \text{nếu } \frac{1-t}{2} \le s \le \frac{1+t}{2}, \\ \alpha(2 - 2s) & \text{nếu } \frac{1+t}{2} \le s \le 1. \end{cases}
   $$
   Kiểm tra: tại $$t=0$$ ta thu đúng $$\alpha * \bar{\alpha}$$; tại $$t=1$$ toàn bộ vòng dừng im tại $$\alpha(0) = x_0$$! ✓

2. **Tại sao trên Hình xuyến $$T^2 = S^1 \times S^1$$ ta có $$ab = ba$$, còn trên Hình số 8 $$S^1 \vee S^1$$ thì $$ab \neq ba$$?**
   - **Trên hình xuyến $$T^2$$:** Do định lý tích $$\pi_1(X \times Y) \cong \pi_1(X) \times \pi_1(Y)$$, ta có ngay:
     $$
     \pi_1(T^2) \cong \pi_1(S^1) \times \pi_1(S^1) \cong \mathbb{Z} \times \mathbb{Z}.
     $$
     Trực quan hình học: khi cắt hình xuyến ra thành hình vuông $$[0,1]^2$$, đường biên là đúng vòng $$a * b * a^{-1} * b^{-1}$$. Vì **có mặt vuông đặc lấp kín bên trong**, ta kéo trượt đường biên co rút gọn về 1 điểm $$\implies a b a^{-1} b^{-1} = 1 \implies ab = ba$$!
   - **Trên hình số 8 ($$S^1 \vee S^1$$):** Hãy tưởng tượng bạn **đục thủng** toàn bộ mặt vuông của hình xuyến, chỉ giữ lại đúng 2 vòng biên $$a$$ và $$b$$ chạm nhau tại 1 điểm! Không còn mặt vuông nào để kéo trượt $$ab$$ sang $$ba$$ nữa $$\implies \pi_1(S^1 \vee S^1) \cong F_2 = \langle a, b \rangle$$ (nhóm tự do 2 phần tử sinh, **không giao hoán**!).

### Giải thích: 4 bước làm chủ tư duy Hàm tử của Nhóm cơ bản

#### Bước 1: Kiểm tra tính độc lập với điểm gốc $$x_0$$
Nếu $$X$$ liên thông đường, mọi đường đi $$\gamma$$ nối $$x_0$$ tới $$x_1$$ cho phép dịch chuyển vòng tại $$x_1$$ về $$x_0$$ bằng cách "đi theo $$\gamma$$, chạy vòng, rồi quay về theo $$\bar{\gamma}$$" — sinh ra đẳng cấu $$\pi_1(X, x_0) \cong \pi_1(X, x_1)$$.

#### Bước 2: Dùng phép đồng cấu cảm sinh $$f_*$$ để chứng minh KHÔNG tồn tại ánh xạ co rút
Nếu $$A \subseteq X$$ có phép co rút $$r: X \to A$$ ($$r \circ i = \operatorname{id}_A$$), thì $$r_* \circ i_* = \operatorname{id}_{\pi_1(A)}$$ ép $$i_*$$ phải đơn ánh và $$r_*$$ phải toàn ánh! Nếu $$\pi_1(X) = 0$$ còn $$\pi_1(A) \neq 0$$, điều đó là **bất khả thi** (chìa khóa của Định lý điểm bất động Brouwer!).

#### Bước 3: Khai thác Định lý Tích
Không gian tích biến thành nhóm tích trực tiếp: $$\pi_1(X \times Y) \cong \pi_1(X) \times \pi_1(Y)$$ — cho ngay $$\pi_1(T^n) \cong \mathbb{Z}^n$$ và $$\pi_1(S^1 \times S^2) \cong \mathbb{Z} \times 0 \cong \mathbb{Z}$$!

#### Bước 4: Chuẩn bị hai công cụ tính mạnh ở bài sau
Khi không gian không phải là tích đơn giản, ta dùng hai vũ khí hạng nặng của Chương 06: **Không gian phủ** (tính $$\pi_1(S^1), \pi_1(\mathbb{R}P^n)$$) và **Định lý Seifert–van Kampen** (tính $$\pi_1$$ bằng cách ghép 2 mảnh mở!).

$$
(X, x_0) \xrightarrow{\;f\;} (Y, y_0)
\;\xRightarrow{\;\text{Hàm tử }\pi_1\;}\;
\pi_1(X, x_0) \xrightarrow{\;f_*\;} \pi_1(Y, y_0)
\;\Longrightarrow\;
\text{Không đồng phôi \& Điểm bất động Brouwer}.
$$

---

## 🔄 Xây dựng nhóm cơ bản

### 1. Vòng khép kín và Đồng luân đường (Nhắc lại)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Vòng khép kín – Loop):**  
Một **vòng khép kín** (loop) tại điểm cơ sở $x_0 \in X$ là một ánh xạ liên tục:

$$
\gamma: [0,1] \to X, \quad \gamma(0) = \gamma(1) = x_0
$$
</div>

Tập hợp tất cả các vòng khép kín tại $x_0$ được ký hiệu là:

$$
\Omega(X, x_0) = \{\gamma: [0,1] \to X : \gamma(0) = \gamma(1) = x_0\}
$$

Hai vòng $\gamma, \delta \in \Omega(X, x_0)$ được gọi là **đồng luân đường** ($\gamma \simeq_p \delta$) nếu tồn tại ánh xạ liên tục $F: [0,1] \times [0,1] \to X$ sao cho $F(s,0) = \gamma(s)$, $F(s,1) = \delta(s)$ và $F(0,t) = F(1,t) = x_0$ với mọi $s, t \in [0,1]$.

![Path homotopy loops](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Homotopy_of_loops.svg/400px-Homotopy_of_loops.svg.png)  
*Đồng luân đường giữa hai vòng khép kín – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Homotopy_of_loops.svg)*

Ký hiệu $[\gamma]$ là lớp đồng luân đường của $\gamma$. Tập thương:

$$
\pi_1(X, x_0) = \Omega(X, x_0) / {\sim_p}
$$

gồm toàn bộ các lớp đồng luân đường của các vòng tại $x_0$.

---

### 2. Phép toán nhóm: Nối đường đi (Path Concatenation)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phép nối vòng):**  
Cho hai vòng $\gamma, \delta \in \Omega(X, x_0)$. Vòng tích $\gamma \cdot \delta$ được định nghĩa bằng cách đi qua $\gamma$ trên $[0, 1/2]$ rồi đi qua $\delta$ trên $[1/2, 1]$:

$$
(\gamma \cdot \delta)(t) = \begin{cases}
\gamma(2t) & 0 \leq t \leq 1/2 \\
\delta(2t - 1) & 1/2 \leq t \leq 1
\end{cases}
$$
</div>

<div class="textbook-theorem" markdown="1">
**Định lý:** Nếu $\gamma \simeq_p \gamma'$ và $\delta \simeq_p \delta'$, thì $\gamma \cdot \delta \simeq_p \gamma' \cdot \delta'$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Nếu $F_\gamma: \gamma \simeq_p \gamma'$ và $F_\delta: \delta \simeq_p \delta'$, thì ánh xạ $F(s,t) = F_\gamma(2s, t)$ với $0 \le s \le 1/2$ và $F(s,t) = F_\delta(2s-1, t)$ với $1/2 \le s \le 1$ liên tục (theo bổ đề dán) và là một đồng luân đường từ $\gamma \cdot \delta$ đến $\gamma' \cdot \delta'$.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** Phép nhân trên các lớp đồng luân được định nghĩa tốt bởi:

$$
[\gamma] \cdot [\delta] = [\gamma \cdot \delta]
$$
</div>

---

### 3. Kiểm chứng các tiên đề nhóm

<div class="textbook-theorem" markdown="1">
**Định lý:** $(\pi_1(X, x_0), \cdot)$ là một nhóm.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Ta lần lượt kiểm tra phần tử đơn vị, phần tử nghịch đảo và tính kết hợp.
</div>

**Phần tử đơn vị:**  
Định nghĩa vòng hằng $e_{x_0}(t) = x_0$ với mọi $t \in [0,1]$. Ta kiểm tra $[\gamma] \cdot [e_{x_0}] = [\gamma]$ qua phép đồng luân tường minh:
$$
F(s,t) = \begin{cases}
\gamma(2s/(1+t)) & 0 \leq s \leq (1+t)/2 \\
x_0 & (1+t)/2 \leq s \leq 1
\end{cases}
$$
Tại $t = 0$, $F(s,0) = (\gamma \cdot e_{x_0})(s)$; tại $t = 1$, $F(s,1) = \gamma(s)$; và hai đầu mút $s=0, s=1$ luôn giữ tại $x_0$. Tương tự chứng minh $[e_{x_0}] \cdot [\gamma] = [\gamma]$.

**Phần tử nghịch đảo:**  
Với vòng $\gamma$, xét vòng ngược $\gamma^{-1}(t) = \gamma(1-t)$. Phép đồng luân $G(s,t)$ đi dọc $\gamma$ đến thời điểm $1-t$ rồi quay ngược lại dọc $\gamma^{-1}$ co dần vòng $\gamma \cdot \gamma^{-1}$ (tại $t=0$) về vòng hằng $e_{x_0}$ (tại $t=1$). Do đó $[\gamma] \cdot [\gamma^{-1}] = [e_{x_0}]$, và tương tự $[\gamma^{-1}] \cdot [\gamma] = [e_{x_0}]$.

**Tính kết hợp:**  
Hai vòng $(\gamma \cdot \delta) \cdot \varepsilon$ và $\gamma \cdot (\delta \cdot \varepsilon)$ cùng đi qua ba vòng $\gamma, \delta, \varepsilon$ theo cùng thứ tự, chỉ khác cách phân chia tham số trên $[0,1]$ (lần lượt là $[0,1/4], [1/4,1/2], [1/2,1]$ và $[0,1/2], [1/2,3/4], [3/4,1]$). Biến đổi tuyến tính các điểm chia theo $t \in [0,1]$ cho một đồng luân đường giữa chúng, suy ra $([\gamma] \cdot [\delta]) \cdot [\varepsilon] = [\gamma] \cdot ([\delta] \cdot [\varepsilon])$.

Vậy $\pi_1(X, x_0)$ là một nhóm.

---

## 📊 Các ví dụ đầu tiên

### 1. $\pi_1(\mathbb{R}^n) = 0$ (Nhóm tầm thường)

<div class="textbook-theorem" markdown="1">
**Định lý:** $\mathbb{R}^n$ là không gian đơn liên (simply connected): $\pi_1(\mathbb{R}^n, x_0) = \{[e]\}$.
</div>

**Chứng minh:** Mọi vòng $\gamma$ tại $x_0$ trong $\mathbb{R}^n$ đều đồng luân đường với vòng hằng $e_{x_0}$ qua đồng luân đoạn thẳng:

$$
F(s,t) = (1-t)\gamma(s) + t x_0
$$

Tính lồi của $\mathbb{R}^n$ đảm bảo $F(s,t) \in \mathbb{R}^n$ với mọi $s, t \in [0,1]$.

---

### 2. $\pi_1(S^1) \cong \mathbb{Z}$

<div class="textbook-theorem" markdown="1">
**Định lý:** $\pi_1(S^1, 1) \cong \mathbb{Z}$.
</div>

Các lớp đồng luân của vòng trên $S^1$ được phân loại duy nhất bởi **chỉ số vòng** (winding number) $n \in \mathbb{Z}$ — số vòng quấn quanh $S^1$ (dương nếu ngược chiều kim đồng hồ, âm nếu thuận chiều kim đồng hồ).

**Ý tưởng chứng minh:** Dùng ánh xạ phủ $p: \mathbb{R} \to S^1$, $p(t) = e^{2\pi it}$. Mỗi vòng $\gamma$ tại $1 \in S^1$ được nâng duy nhất lên một đường đi $\tilde{\gamma}: [0,1] \to \mathbb{R}$ xuất phát tại $\tilde{\gamma}(0) = 0$; điểm cuối $\tilde{\gamma}(1) \in \mathbb{Z}$ chỉ phụ thuộc vào lớp $[\gamma]$ và cảm sinh đẳng cấu nhóm $\pi_1(S^1, 1) \to \mathbb{Z}$. Phần tử sinh của nhóm là lớp của vòng $\gamma_1(t) = e^{2\pi it}$.

![S1 fundamental group](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Winding_number.svg/400px-Winding_number.svg.png)  
*Minh họa chỉ số vòng quanh đường tròn – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Winding_number.svg)*

---

### 3. $\pi_1(S^n) = 0$ với $n \geq 2$

<div class="textbook-theorem" markdown="1">
**Định lý:** Các mặt cầu $S^n$ với $n \geq 2$ đều đơn liên.
</div>

**Ý tưởng chứng minh:** Nếu một vòng $\gamma$ trên $S^n$ bỏ sót ít nhất một điểm $p \in S^n$, thì ảnh của nó nằm trong $S^n \setminus \{p\} \cong \mathbb{R}^n$ (co rút được), nên $\gamma$ đồng luân với vòng hằng. Lưu ý rằng một vòng liên tục tổng quát có thể phủ kín $S^n$ (đường cong Peano), nên để chứng minh chặt chẽ ta cần xấp xỉ $\gamma$ bằng một vòng đồng luân trơn (hoặc tuyến tính từng khúc) bỏ sót một điểm, hoặc áp dụng trực tiếp định lý Seifert–van Kampen cho phủ $S^n = (S^n \setminus \{N\}) \cup (S^n \setminus \{S\})$.

Kết quả này cho thấy $\pi_1$ phân biệt được $S^1$ ($\pi_1 \cong \mathbb{Z}$) với $S^2$ ($\pi_1 = 0$).

---

### 4. $\pi_1(T^2) \cong \mathbb{Z} \times \mathbb{Z}$

<div class="textbook-theorem" markdown="1">
**Định lý:** $\pi_1(T^2) \cong \mathbb{Z} \times \mathbb{Z}$.
</div>

Hình xuyến $T^2 = S^1 \times S^1$ có hai vòng sinh độc lập $\alpha$ (kinh tuyến – meridian) và $\beta$ (vĩ tuyến – longitude), thỏa mãn quan hệ giao hoán $\alpha\beta = \beta\alpha$. Ta sẽ chứng minh chặt chẽ đẳng cấu này trong bài tiếp theo qua định lý tích của nhóm cơ bản và định lý Seifert–van Kampen.

---

## 🔗 Tính độc lập với điểm cơ sở

### 1. Đẳng cấu đổi điểm cơ sở

Cho $X$ liên thông đường và hai điểm $x_0, x_1 \in X$. Chọn một đường đi $\alpha: [0,1] \to X$ từ $x_0$ đến $x_1$, và định nghĩa ánh xạ $\beta_\alpha: \pi_1(X, x_0) \to \pi_1(X, x_1)$ bởi:

$$
\beta_\alpha([\gamma]) = [\alpha^{-1} \cdot \gamma \cdot \alpha]
$$

(phép liên hợp bởi đường đi $\alpha$: xuất phát từ $x_1$, đi ngược $\alpha$ về $x_0$, đi hết vòng $\gamma$, rồi quay lại $x_1$ theo $\alpha$).

<div class="textbook-theorem" markdown="1">
**Định lý:** $\beta_\alpha$ là một đẳng cấu nhóm.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Ta có $\beta_\alpha([\gamma][\delta]) = [\alpha^{-1} \cdot \gamma \cdot \delta \cdot \alpha] = [\alpha^{-1} \cdot \gamma \cdot \alpha \cdot \alpha^{-1} \cdot \delta \cdot \alpha] = \beta_\alpha([\gamma])\beta_\alpha([\delta])$, nên $\beta_\alpha$ là đồng cấu nhóm. Hơn nữa $\beta_{\alpha^{-1}}$ là ánh xạ ngược hai phía của $\beta_\alpha$, nên $\beta_\alpha$ là đẳng cấu.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** Với mọi $x_0, x_1$ thuộc cùng một thành phần liên thông đường của $X$, ta có $\pi_1(X, x_0) \cong \pi_1(X, x_1)$.
</div>

**Lưu ý:** Đẳng cấu $\beta_\alpha$ phụ thuộc vào lớp đồng luân của đường đi $\alpha$ (hai đường đi khác nhau $\alpha, \alpha'$ cho hai đẳng cấu sai khác nhau một tự đẳng cấu trong của nhóm). Khi chỉ xét sai khác đẳng cấu trên không gian liên thông đường, ta thường viết gọn là $\pi_1(X)$.

---

### 2. Không gian không liên thông đường

Nếu $X$ không liên thông đường, $\pi_1(X, x_0)$ chỉ phụ thuộc vào thành phần liên thông đường chứa $x_0$:

<div class="textbook-theorem" markdown="1">
**Định lý:** $\pi_1(X, x_0) = \pi_1(C, x_0)$, trong đó $C$ là thành phần liên thông đường của $x_0$.
</div>

---

## 🎯 Tính hàm tử và Tính bất biến đồng luân

### 1. Đồng cấu cảm sinh

Cho ánh xạ liên tục bảo toàn điểm cơ sở $f: (X, x_0) \to (Y, y_0)$ (tức $f(x_0) = y_0$). Định nghĩa ánh xạ $f_*: \pi_1(X, x_0) \to \pi_1(Y, y_0)$ bởi:

$$
f_*([\gamma]) = [f \circ \gamma]
$$

<div class="textbook-theorem" markdown="1">
**Định lý:** $f_*$ là một đồng cấu nhóm xác định tốt.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Nếu $F: \gamma \simeq_p \delta$ là đồng luân đường trong $X$ thì $f \circ F$ là đồng luân đường giữa $f \circ \gamma$ và $f \circ \delta$ trong $Y$, nên $f_*$ xác định tốt. Ngoài ra $f_*([\gamma][\delta]) = [f \circ (\gamma \cdot \delta)] = [(f \circ \gamma) \cdot (f \circ \delta)] = f_*([\gamma])f_*([\delta])$.
</div>

**Hai tính chất hàm tử:**
1. $(\operatorname{id}_X)_* = \operatorname{id}_{\pi_1(X, x_0)}$.
2. $(g \circ f)_* = g_* \circ f_*$.

<div class="textbook-theorem" markdown="1">
**Hệ quả:** $\pi_1$ là một **hàm tử hiệp biến** (covariant functor) từ phạm trù các không gian có điểm cơ sở đến phạm trù các nhóm.
</div>

---

### 2. Tính bất biến đồng luân

<div class="textbook-theorem" markdown="1">
**Định lý:** Nếu $f, g: (X, x_0) \to (Y, y_0)$ đồng luân (cố định điểm cơ sở), thì $f_* = g_*$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Nếu $F: X \times [0,1] \to Y$ là đồng luân giữa $f$ và $g$ cố định $x_0$, thì $(s,t) \mapsto F(\gamma(s), t)$ là đồng luân đường giữa $f \circ \gamma$ và $g \circ \gamma$, suy ra $f_*([\gamma]) = g_*([\gamma])$.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả (Tính bất biến đồng luân):**  
Nếu $X \simeq Y$ (với $X, Y$ liên thông đường), thì $\pi_1(X) \cong \pi_1(Y)$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Nếu $f: X \to Y$ là tương đương đồng luân với nghịch đảo đồng luân $g: Y \to X$, thì $g_* \circ f_*$ và $f_* \circ g_*$ là các đẳng cấu (sai khác phép đổi điểm cơ sở nếu đồng luân không cố định điểm cơ sở), suy ra $f_*$ là đẳng cấu.
</div>

---

## 🌿 Phản ví dụ từ Wild Topology và Ứng dụng Cổ điển

### 1. Khi trực giác phức CW sụp đổ: Khuyên tai Hawaii và Vòng tròn Warsaw

Trong [*Algebraic Topology*](https://people.math.wisc.edu/~lmaxim/topbookf.pdf) (Mục 4.1, Hình 4.1) và bộ sưu tập [Wild Topology Bestiary](https://wildtopology.com/bestiary/), **Khuyên tai Hawaii (Hawaiian Earring)** $\mathbb{E} = \bigcup_{n=1}^{\infty} C_n$ gồm vô hạn đường tròn bán kính $1/n$ tiếp xúc nhau tại gốc $p=(0,0)$:

![Khuyên tai Hawaii và Vòng tròn Warsaw trong Wild Topology]({{ site.imgurl }}/chapter_img/chapter06/06_01_wild_topology.png)

- Khác với bó vô hạn đường tròn $\bigvee_{n=1}^{\infty} S^1$ (có tôpô yếu của phức CW), $\mathbb{E}$ mang **tôpô không gian con** của $\mathbb{R}^2$. Mọi lân cận $U$ của gốc $p$ đều chứa trọn các đường tròn $C_n$ với $n$ đủ lớn, nên $\mathbb{E}$ **không nửa đơn liên địa phương (not semilocally simply connected)**.
- Hệ quả: $\mathbb{E}$ **không có không gian phủ phổ dụng**, và $\pi_1(\mathbb{E}, p)$ là một nhóm **không đếm được**, lớn hơn thực sự nhóm tự do $\ast_{n=1}^\infty \mathbb{Z}$ (vì ta có thể đi qua vô hạn vòng nhỏ dần trong thời gian hữu hạn $[0,1]$!).
- Tương tự, **Vòng tròn Warsaw (Warsaw Circle)** (đóng kín đồ thị $\sin(1/x)$ bằng một cung nối ngoài) là không gian liên thông đường với $\pi_1 = 0$, nhưng **không co rút được (non-contractible)** và không đồng luân tương đương với $S^1$.

### 2. Hai ứng dụng kinh điển từ $\pi_1(S^1) \cong \mathbb{Z}$

Theo [Laurentiu Maxim (Mục 2.7)](https://people.math.wisc.edu/~lmaxim/topbookf.pdf), chỉ riêng đẳng cấu $\pi_1(S^1) \cong \mathbb{Z}$ đã đủ chứng minh hai định lý nền tảng:
- **Định lý điểm bất động Brouwer (chiều 2):** Mọi ánh xạ liên tục $f: D^2 \to D^2$ đều có ít nhất một điểm bất động (nếu không, tia nối $f(x)$ qua $x$ cắt biên $S^1$ tạo thành một phép co rút $r: D^2 \to S^1$, kéo theo đơn cấu $\mathbb{Z} = \pi_1(S^1) \hookrightarrow \pi_1(D^2) = 0$ — vô lý!).
- **Định lý cơ bản của Đại số:** Mọi đa thức khác hằng $p(z) \in \mathbb{C}[z]$ bậc $n \ge 1$ đều có nghiệm trên $\mathbb{C}$ (nếu không có nghiệm, vòng tròn bán kính lớn $R$ tạo nên ánh xạ bậc $n$ trên $S^1$, nhưng lại đồng luân về hằng khi $R \to 0$, mâu thuẫn với $n \neq 0$ trong $\pi_1(S^1)$).

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Henri Poincaré** – *"Analysis Situs"* (1895)  
   *Giới thiệu khái niệm nhóm cơ bản.*

2. **Henri Poincaré** – *"Cinquième complément à l'Analysis Situs"* (1904)  
   *Phát triển sâu hơn lý thuyết nhóm cơ bản.*

3. **Max Dehn** – *"Über die Topologie des dreidimensionalen Raumes"* (1910)  
   *Ứng dụng nhóm cơ bản vào 3-đa tạp.*

4. **Emmy Noether** – Các công trình về ứng dụng lý thuyết nhóm vào tô-pô (thập niên 1920)

### Giáo trình

5. **James R. Munkres** – *Topology*, 2nd Ed., **§52: Fundamental Group**

6. **Allen Hatcher** – *Algebraic Topology*, **§1.1: Basic Constructions**

7. **William S. Massey** – *A Basic Course in Algebraic Topology*, **Chapters 2–3**

8. **Glen E. Bredon** – *Topology and Geometry*, **Chapters I–II**

9. **Joseph J. Rotman** – *An Introduction to Algebraic Topology*, **Chapter 7**

10. **Marvin J. Greenberg & John R. Harper** – *Algebraic Topology: A First Course*, **Chapter 3**

---

## 🔗 Ứng dụng và liên kết

### Tô-pô – Phân biệt không gian
Vì $\pi_1(S^1) \cong \mathbb{Z} \neq 0 = \pi_1(S^2)$, ta kết luận $S^1 \not\cong S^2$.

### Định lý điểm bất động Brouwer (chiều 2)
Nếu tồn tại ánh xạ liên tục $f: D^2 \to D^2$ không có điểm bất động, ta xây dựng được phép co rút $r: D^2 \to S^1$, suy ra $r_* \circ i_* = \operatorname{id}_{\pi_1(S^1)}$ — mâu thuẫn vì $\pi_1(D^2) = 0$ còn $\pi_1(S^1) \cong \mathbb{Z}$.

### Lý thuyết không gian phủ
Các không gian phủ liên thông của $X$ được phân loại bởi các nhóm con của $\pi_1(X)$, và phủ phổ dụng $\tilde{X}$ thỏa mãn $X \cong \tilde{X}/\pi_1(X)$.

### Giải tích phức – Đơn trị hóa (Monodromy)
Các hàm đa trị như $\sqrt{z}$ hay $\log z$ trở thành đơn trị trên không gian phủ, và sự thay đổi nhánh khi đi quanh điểm kỳ dị được mô tả qua tác động của $\pi_1$.

### Robotics – Không gian cấu hình
$\pi_1$ của không gian cấu hình mô tả các lớp đường đi không thể biến dạng liên tục sang nhau khi tránh chướng ngại vật.

### Vật lý – Hiệu ứng Aharonov–Bohm
Độ dịch pha lượng tử của electron đi quanh vùng có từ thông bị cô lập phụ thuộc vào lớp của đường đi trong $\pi_1$ của không gian cấu hình.

---

## Video tham khảo

- **xem trước** [Intro to the Fundamental Group //  Algebraic Topology with @TomRocksMaths](https://www.youtube.com/watch?v=IpkzNeS8G20) — Dr. Trefor Bazett, tiếng Anh. Giới thiệu nhóm cơ bản từ đường đi và phép nối đường.
- [Algebraic topology: Fundamental group](https://www.youtube.com/watch?v=WL9BFRyWMUI) — Richard E Borcherds, tiếng Anh. Trình bày chặt chẽ cách xây dựng $\pi_1$.
- [2. Path Homotopy; the Fundamental Group - Pierre Albin](https://www.youtube.com/watch?v=nq8QBdP_N_o) — Mat Neth, tiếng Anh. Bài giảng đầy đủ về đồng luân đường và nhóm cơ bản.

## 🧩 Bài tập

### Định nghĩa và tính chất cơ bản

1. **Kiểm tra phép nối vòng:**  
   Với $\gamma, \delta$ là hai vòng tại $x_0$, kiểm tra $\gamma \cdot \delta$ liên tục và là vòng tại $x_0$.

2. **Phần tử đơn vị:**  
   Kiểm tra tính liên tục và điều kiện cố định điểm cơ sở của đồng luân $F: \gamma \cdot e \simeq_p \gamma$.

3. **Phần tử nghịch đảo:**  
   Xây dựng tường minh đồng luân đường chứng minh $[\gamma] \cdot [\gamma^{-1}] = [e]$.

4. **Tính kết hợp:**  
   Mô tả tường minh phép đổi tham số chứng minh $(\gamma \cdot \delta) \cdot \varepsilon \simeq_p \gamma \cdot (\delta \cdot \varepsilon)$.

### Tính toán $\pi_1$

5. **$\mathbb{R}^n$ đơn liên:**  
   Chứng minh mọi vòng trong $\mathbb{R}^n$ đều đồng luân đường với vòng hằng bằng $F(s,t) = (1-t)\gamma(s) + tx_0$.

6. **Đĩa đóng $D^2$:**  
   Giải thích vì sao $\pi_1(D^2) = 0$.

7. **Hình vành khăn:**  
   Tính $\pi_1(A)$ với $A = \{z \in \mathbb{C} : 1 \leq |z| \leq 2\}$ (đáp số: $\mathbb{Z}$).

8. **$\mathbb{R}^2 \setminus \{0\}$:**  
   Từ $\mathbb{R}^2 \setminus \{0\} \simeq S^1$, suy ra $\pi_1(\mathbb{R}^2 \setminus \{0\}) \cong \mathbb{Z}$.

9. **$\mathbb{R}^2 \setminus \{p, q\}$:**  
   Nêu lập luận trực quan vì sao $\pi_1(\mathbb{R}^2 \setminus \{p,q\}) \cong \mathbb{Z} * \mathbb{Z}$ (sẽ chứng minh bằng Van Kampen).

### Độc lập với điểm cơ sở

10. **Đổi điểm cơ sở:**  
    Kiểm tra chi tiết $\beta_\alpha([\gamma]) = [\alpha^{-1} \cdot \gamma \cdot \alpha]$ là đồng cấu nhóm.

11. **Đẳng cấu ngược:**  
    Chứng minh $\beta_{\alpha^{-1}}$ là nghịch đảo của $\beta_\alpha$.

12. **Phụ thuộc vào đường đi:**  
    Nếu $\alpha, \alpha'$ là hai đường đi từ $x_0$ đến $x_1$, hãy chỉ ra mối liên hệ giữa $\beta_\alpha$ và $\beta_{\alpha'}$ (sai khác tự đẳng cấu trong sinh bởi vòng $\alpha' \cdot \alpha^{-1}$).

### Tính hàm tử

13. **Đồng cấu cảm sinh:**  
    Với $f: S^1 \to S^1$, $f(z) = z^2$, tính $f_*: \pi_1(S^1) \to \pi_1(S^1)$ (đáp số: $n \mapsto 2n$).

14. **Hợp thành:**  
    Kiểm tra chi tiết $(g \circ f)_* = g_* \circ f_*$.

15. **Ánh xạ đồng nhất:**  
    Kiểm tra $(\operatorname{id}_X)_* = \operatorname{id}_{\pi_1(X)}$.

### Tính bất biến đồng luân

16. **Phép co rút (Retraction):**  
    Nếu $r: X \to A$ là phép co rút ($r|_A = \operatorname{id}_A$), chứng minh $r_*: \pi_1(X) \to \pi_1(A)$ là toàn ánh.

17. **Co rút biến dạng:**  
    Nếu $A$ là co rút biến dạng của $X$, chứng minh $i_*: \pi_1(A) \to \pi_1(X)$ là đẳng cấu.

18. **Tương đương đồng luân:**  
    Dùng tính hàm tử chứng minh nếu $X \simeq Y$ thì $\pi_1(X) \cong \pi_1(Y)$.

### Nâng cao

19. **Nhóm cơ bản không giao hoán:**  
    Tìm hiểu ví dụ hình số $8$: $\pi_1(S^1 \vee S^1) \cong \mathbb{Z} * \mathbb{Z}$ là nhóm không giao hoán.

20. **Abel hóa:**  
    Tìm hiểu mối liên hệ giữa nhóm Abel hóa $\pi_1^{\text{ab}}(X) = \pi_1(X)/[\pi_1(X), \pi_1(X)]$ và nhóm đồng điều thứ nhất $H_1(X)$.

21. **Nhóm đồng luân bậc cao:**  
    Tìm hiểu sơ lược về $\pi_n(X)$ ($n \ge 2$) và tính chất giao hoán của chúng.

### Câu hỏi suy ngẫm

22. **Tại sao cần điểm cơ sở $x_0$?:**  
    Giải thích vai trò của điểm cơ sở trong việc định nghĩa phép nối vòng.

23. **Trực giác hình học:**  
    Giải thích kết quả $\pi_1(S^1) \cong \mathbb{Z}$ bằng hình ảnh quấn dây quanh một trụ tròn.

24. **Ứng dụng:**  
    Nêu $3$ ứng dụng của $\pi_1$ trong các lĩnh vực khác nhau.

25. **Lịch sử:**  
    Tìm hiểu động cơ của Poincaré khi đưa ra khái niệm nhóm cơ bản vào năm 1895.

---

## 📚 Đọc thêm

- **Hatcher, Algebraic Topology:** §1.1
- **Munkres, Topology:** §52
- **Massey, Basic Course:** Chapters 2–3
- **Armstrong, Basic Topology:** Chapter 5
- **Stillwell, Classical Topology:** Góc nhìn lịch sử

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã xây dựng **nhóm cơ bản $\pi_1(X, x_0)$** gồm các lớp đồng luân đường của các vòng tại $x_0$ cùng phép toán nối vòng. Nhóm này độc lập với điểm cơ sở (sai khác đẳng cấu) trên không gian liên thông đường, mang tính hàm tử ($f \mapsto f_*$) và là bất biến đồng luân ($X \simeq Y \Rightarrow \pi_1(X) \cong \pi_1(Y)$). Các ví dụ nền tảng gồm $\pi_1(\mathbb{R}^n) = 0$, $\pi_1(S^1) \cong \mathbb{Z}$, $\pi_1(S^n) = 0$ ($n \ge 2$) và $\pi_1(T^2) \cong \mathbb{Z}^2$.

**Tiếp theo:** Lecture 06.02 về **Tính toán nhóm cơ bản $\pi_1$** — các phương pháp và chứng minh chi tiết cho $S^1$, $S^n$, $T^2$ và các mặt.

---

*"The fundamental group is where algebra meets geometry."*

---

**Previous:** [Lecture 06.00: Homotopy](/contents/vi/topology-chapter06/06_00_Homotopy_Path_Homotopy/)  
**Next:** [Lecture 06.02: Computing π₁](/contents/vi/topology-chapter06/06_02_Computing_Fundamental_Group/)
