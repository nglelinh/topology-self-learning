---
layout: post
title: "Lecture 06.02: Computing π₁ - Examples and Techniques"
lang: vi
lang-ref: lecture-06-02
chapter: 6
lecture: 2
categories: [chapter06]
tags: [π1-computations, circle, sphere, torus, simply-connected]
description: "Computing fundamental groups: S¹, S^n, T², surfaces, techniques và detailed proofs"
---

**Tính toán nhóm cơ bản $\pi_1$ – Ví dụ và Kỹ thuật**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nhìn vào một sợi dây quấn 3 vòng quanh đường tròn $$S^1$$, trực giác bảo ngay rằng nó **không thể** tháo thành 0 vòng — nhưng để *chứng minh toán học chặt chẽ* rằng $$\pi_1(S^1) \cong \mathbb{Z}$$, bạn cần một mẹo đẹp đến ngỡ ngàng: **trải đường tròn $$S^1$$ thành chiếc lò xo xoắn ốc vô hạn $$\mathbb{R}$$**! Mỗi khi sợi dây đi hết 1 vòng trên $$S^1$$, đầu nâng của nó trên lò xo $$\mathbb{R}$$ leo lên đúng **1 tầng** — và số nguyên ghi tầng cuối cùng chính là **số quấn (winding number)**! Từ một phép tính tưởng chừng giản dị đó, hàng loạt định lý vĩ đại như **Điểm bất động Brouwer**, **Định lý cơ bản Đại số** và **Borsuk–Ulam** lập tức rơi rụng như quân cờ domino!

Sau khi định nghĩa nhóm cơ bản $\pi_1(X, x_0)$ ở bài trước, câu hỏi tự nhiên tiếp theo là:

> **Làm thế nào để tính tường minh $\pi_1(X)$ cho các không gian cụ thể?**

Việc tính toán nhóm cơ bản thường kết hợp trực giác hình học với các công cụ có hệ thống: không gian phủ, tương đương đồng luân (và co rút biến dạng), định lý tích và định lý Seifert–van Kampen.

Trong bài học này, chúng ta trình bày chi tiết chứng minh $\pi_1(S^1) \cong \mathbb{Z}$ bằng không gian phủ $\mathbb{R} \to S^1$, chứng minh $\pi_1(S^n) = 0$ với $n \geq 2$, thiết lập định lý tích để suy ra $\pi_1(T^2) \cong \mathbb{Z}^2$, giới thiệu biểu diễn nhóm cơ bản của các mặt đóng ($\Sigma_g$, $\mathbb{R}P^2$, chai Klein $K$), và tổng kết các kỹ thuật tính toán chính.

![Fundamental group computations](https://upload.wikimedia.org/wikipedia/commons/thumb/9/97/Torus_cycles.svg/400px-Torus_cycles.svg.png)  
*Hai vòng sinh của nhóm cơ bản trên hình xuyến – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus_cycles.svg)*

---

## 🗺️ Bản đồ kiến thức nền: Cách tính $$\pi_1(S^1)$$ và Sức mạnh của các Hệ quả kinh điển

### 1. Kỹ thuật Nâng Đường đi (Path Lifting) qua Ánh xạ Phủ $$p: \mathbb{R} \to S^1$$
- **Bản chất:** Ánh xạ $$p(t) = e^{2\pi i t} = (\cos 2\pi t, \sin 2\pi t)$$ cuộn đường thẳng $$\mathbb{R}$$ vô số vòng lên đường tròn $$S^1$$. Nhờ hai bổ đề vàng (**Nâng đường đi** và **Nâng đồng luân**), mọi vòng $$\gamma$$ trên $$S^1$$ xuất phát từ $$(1,0)$$ đều có duy nhất một đường nâng $$\tilde{\gamma}: [0,1] \to \mathbb{R}$$ bắt đầu tại $$0$$, và điểm kết thúc $$\tilde{\gamma}(1) \in \mathbb{Z}$$ chính là **số quấn** (bất biến dưới đồng luân)!

### 2. Tại sao $$\pi_1(S^n) = 0$$ với mọi $$n \ge 2$$?
- **Bản chất:** Trên mặt cầu 2 chiều $$S^2$$ (hay $$S^n$$ với $$n \ge 2$$), bất kỳ vòng 1 chiều nào cũng có thể né một điểm (ví dụ cực Bắc $$N$$); mà $$S^n \setminus \{N\} \cong \mathbb{R}^n$$ co rút được về 1 điểm! (Chú ý: cần lập luận kỹ thuật chia nhỏ vòng để tránh trường hợp đường cong Peano phủ kín mặt cầu!)

### 3. Bốn Hệ quả Kinh điển từ duy nhất $$\pi_1(S^1) \cong \mathbb{Z}$$
- **Định lý Điểm bất động Brouwer 2D:** Mọi ánh xạ liên tục $$f: D^2 \to D^2$$ đều có ít nhất 1 điểm $$f(x^*) = x^*$$!
- **Định lý Cơ bản của Đại số:** Mọi đa thức phức bậc $$n \ge 1$$ đều có ít nhất 1 nghiệm phức!
- **Định lý Borsuk–Ulam 2D:** Tại mọi thời điểm trên Trái Đất, luôn có 2 điểm đối tâm có *cùng nhiệt độ và cùng áp suất*!
- **Định lý Bánh mì kẹp thịt (Ham Sandwich):** Luôn có 1 nhát cắt phẳng chia đôi đồng thời 3 vật thể bất kỳ trong không gian!

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc

### Ví dụ 1: Tính trực tiếp Số quấn bằng Đường nâng $$\tilde{\gamma}$$
Xét ánh xạ phủ $$p(t) = e^{2\pi i t}: \mathbb{R} \to S^1$$ và hai vòng khép kín tại $$z_0 = 1 \in S^1$$:
1. **Vòng $$\gamma_3(s) = e^{6\pi i s}$$** ($$s \in [0, 1]$$):
   - Đường nâng duy nhất bắt đầu tại $$\tilde{\gamma}_3(0) = 0$$ là **$$\tilde{\gamma}_3(s) = 3s$$** (kiểm tra: $$p(3s) = e^{2\pi i (3s)} = e^{6\pi i s} = \gamma_3(s)$$!).
   - Điểm cuối: $$\tilde{\gamma}_3(1) = +3 \implies$$ lớp $$[\gamma_3]$$ ứng với số nguyên **$$+3 \in \mathbb{Z}$$**!
2. **Vòng $$\gamma_{-2}(s) = e^{-4\pi i s}$$:**
   - Đường nâng bắt đầu tại $$0$$ là $$\tilde{\gamma}_{-2}(s) = -2s \implies \tilde{\gamma}_{-2}(1) = -2 \in \mathbb{Z}$$!
3. **Kiểm tra đồng cấu tích $$\gamma_3 * \gamma_{-2}$$:** Nửa đầu nâng từ $$0$$ lên $$+3$$, nửa sau nâng tiếp từ $$+3$$ lùi $$2$$ đơn vị về $$3 + (-2) = +1$$! Tức $$\deg([\gamma_3] \cdot [\gamma_{-2}]) = 3 + (-2) = 1$$ — biến phép nối vòng thành **phép cộng số nguyên**!

### Ví dụ 2: Chứng minh trọn vẹn Định lý Điểm bất động Brouwer 2D trong 4 dòng
Giả sử phản chứng tồn tại ánh xạ liên tục $$f: D^2 \to D^2$$ **không có điểm bất động** (tức $$f(x) \neq x$$ với mọi $$x \in D^2$$):
1. Với mỗi $$x \in D^2$$, kẻ tia thẳng xuất phát từ $$f(x)$$ đi qua $$x$$ và cắt đường biên tròn $$S^1 = \partial D^2$$ tại một điểm duy nhất gọi là $$r(x)$$.
2. Ta kiểm tra ngay: $$r: D^2 \to S^1$$ liên tục, và nếu $$x \in S^1$$ thì tia từ $$f(x)$$ qua $$x$$ cắt biên tại chính $$x$$ nên $$r(x) = x$$ (tức $$r \circ i = \operatorname{id}_{S^1}$$ — $$r$$ là một **phép co rút** từ đĩa $$D^2$$ lên biên $$S^1$$!).
3. Áp dụng hàm tử $$\pi_1$$ lên $$S^1 \xrightarrow{i} D^2 \xrightarrow{r} S^1$$:
   $$
   \mathbb{Z} = \pi_1(S^1) \xrightarrow{\;i_*\;} \pi_1(D^2) = \{0\} \xrightarrow{\;r_*\;} \pi_1(S^1) = \mathbb{Z}.
   $$
4. Hợp thành $$r_* \circ i_*$$ phải là đồng nhất trên $$\mathbb{Z}$$ (gửi $$1 \mapsto 1$$), nhưng nó đi ngang qua nhóm tầm thường $$\{0\}$$ nên bắt buộc gửi $$1 \mapsto 0 \mapsto 0$$ — **mâu thuẫn $$1 = 0$$**! Vậy $$f$$ chắc chắn phải có ít nhất một điểm bất động!

### Khung giải thích: Nhịp cầu 4 bước từ $$\pi_1(S^1) \cong \mathbb{Z}$$ sang các định lý lớn (nên đọc chậm)

#### Bước 1: Dùng lò xo phủ $$\mathbb{R} \to S^1$$ để gán mỗi vòng một số nguyên duy nhất
Chính tính chất "nhìn cục bộ giống hệt nhau" của ánh xạ phủ giúp ta mở cuộn mọi vòng trên $$S^1$$ thành đường đi trên $$\mathbb{R}$$, và đồng luân trên $$S^1$$ mở cuộn thành đồng luân cố định hai đầu mút trên $$\mathbb{R}$$.

#### Bước 2: Dùng $$\pi_1(S^1) \neq 0$$ để bác bỏ sự tồn tại của phép co rút $$D^2 \to S^1$$
Một đĩa đặc không bao giờ bóp liên tục ra viền tròn của chính nó mà không đục thủng ở giữa — bởi làm vậy sẽ đẩy nhóm $$\mathbb{Z}$$ xuyên qua nhóm $$\{0\}$$.

#### Bước 3: Biến "không có nghiệm / không có điểm bất động" thành một phép co rút giả định
Cả Brouwer (không có $$f(x)=x$$) lẫn Định lý cơ bản Đại số (đa thức $$p(z)$$ không có nghiệm trên $$\mathbb{C}$$) đều cho phép ta xây dựng một ánh xạ liên tục từ đĩa vào $$S^1$$ có số quấn $$n \neq 0$$ trên biên nhưng lại co rút được qua lòng đĩa (số quấn $$0$$) — lập tức dẫn tới mâu thuẫn $$n = 0$$!

#### Bước 4: Tổng quát hóa lên chiều cao bằng Đồng điều $$H_n(S^n) \cong \mathbb{Z}$$
Ở chiều $$n \ge 3$$, $$\pi_1(S^{n-1}) = 0$$ không đủ phân biệt $$D^n$$ với $$S^{n-1}$$ nữa — đó là lý do Chương 07 xây dựng **nhóm đồng điều $$H_{n-1}(S^{n-1}) \cong \mathbb{Z}$$** để chứng minh Brouwer cho mọi chiều $$n$$!

$$
p: \mathbb{R} \to S^1
\;\xrightarrow{\;\text{Nâng đường đi}\;}\;
\pi_1(S^1) \cong \mathbb{Z}
\;\xrightarrow{\;\nexists\text{ co rút }D^2\to S^1\;}\;
\text{Brouwer, Đại số cơ bản \& Borsuk–Ulam}.
$$

---

## 🔵 $\pi_1(S^1) \cong \mathbb{Z}$: Đường tròn

### 1. Phát biểu và trực giác

<div class="textbook-theorem" markdown="1">
**Định lý:** $\pi_1(S^1, 1) \cong \mathbb{Z}$.
</div>

Mỗi vòng khép kín trên đường tròn $S^1$ được đặc trưng duy nhất sai khác đồng luân đường bởi **chỉ số vòng** (winding number) $n \in \mathbb{Z}$ — số lần vòng quấn quanh $S^1$ (có dấu theo chiều quay). Phép nối hai vòng có chỉ số $n$ và $m$ cho vòng có chỉ số $n + m$, tương ứng với phép cộng trong $\mathbb{Z}$.

![Winding number illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Winding_number.svg/500px-Winding_number.svg.png)  
*Các vòng có chỉ số vòng khác nhau quanh đường tròn – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Winding_number.svg)*

---

### 2. Chứng minh qua không gian phủ $\mathbb{R} \to S^1$

Xét ánh xạ phủ $p: \mathbb{R} \to S^1$ xác định bởi $p(t) = e^{2\pi it}$. Ánh xạ này liên tục, toàn ánh, là đồng phôi địa phương, và mỗi điểm $e^{i\theta} \in S^1$ có nghịch ảnh $p^{-1}(e^{i\theta}) = \{\theta/(2\pi) + n : n \in \mathbb{Z}\}$.

**Bước 1: Nâng đường đi (Path Lifting)**

<div class="textbook-lemma" markdown="1">
**Bổ đề (Nâng đường đi):** Với mọi vòng $\gamma: [0,1] \to S^1$ thỏa $\gamma(0) = 1$, tồn tại duy nhất một đường nâng (lift) liên tục $\tilde{\gamma}: [0,1] \to \mathbb{R}$ sao cho $\tilde{\gamma}(0) = 0$ và $p \circ \tilde{\gamma} = \gamma$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Chia $[0,1]$ thành hữu hạn đoạn nhỏ sao cho ảnh của mỗi đoạn nằm trong một lân cận phủ đều của $p$, sau đó nâng lần lượt từng đoạn bằng nghịch đảo địa phương của $p$ và dán lại (sẽ trình bày tổng quát trong bài 06.03).
</div>

Vì $\gamma(1) = 1$ và $p(\tilde{\gamma}(1)) = \gamma(1) = 1$, ta có $\tilde{\gamma}(1) \in p^{-1}(1) = \mathbb{Z}$.

---

**Bước 2: Định nghĩa ánh xạ chỉ số vòng**

Định nghĩa $\phi: \pi_1(S^1, 1) \to \mathbb{Z}$ bởi:

$$
\phi([\gamma]) = \tilde{\gamma}(1)
$$

trong đó $\tilde{\gamma}$ là đường nâng duy nhất của $\gamma$ xuất phát tại $0$. Theo định lý nâng đồng luân (bài 06.03), nếu $\gamma \simeq_p \delta$ thì đường nâng của phép đồng luân giữ nguyên điểm cuối $\tilde{\gamma}(1) = \tilde{\delta}(1)$, nên $\phi$ xác định tốt.

---

**Bước 3: Kiểm tra tính đồng cấu**

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Đặt $n = \tilde{\gamma}(1)$ và $m = \tilde{\delta}(1)$. Đường nâng của $\gamma \cdot \delta$ xuất phát tại $0$ sẽ đi theo $\tilde{\gamma}$ trên $[0, 1/2]$ (đến $n$), rồi đi theo đường tịnh tiến $t \mapsto n + \tilde{\delta}(2t-1)$ trên $[1/2, 1]$ (đến $n + m$). Do đó $\phi([\gamma][\delta]) = n + m = \phi([\gamma]) + \phi([\delta])$.
</div>

---

**Bước 4: Kiểm tra song ánh**

- **Đơn ánh:** Nếu $\phi([\gamma]) = 0$, thì $\tilde{\gamma}(0) = \tilde{\gamma}(1) = 0$. Vì $\mathbb{R}$ lồi nên $\tilde{\gamma}$ đồng luân đường với đường hằng $0$ trong $\mathbb{R}$ qua $H(s,t) = (1-t)\tilde{\gamma}(s)$; chiếu xuống bởi $p$ cho $p \circ H: \gamma \simeq_p e_1$, tức $[\gamma] = [e_1]$.
- **Toàn ánh:** Với mọi $n \in \mathbb{Z}$, vòng $\gamma_n(t) = e^{2\pi int}$ có đường nâng $\tilde{\gamma}_n(t) = nt$, nên $\phi([\gamma_n]) = n$.

Vậy $\phi: \pi_1(S^1, 1) \to \mathbb{Z}$ là một đẳng cấu nhóm, với phần tử sinh $[\gamma_1]$ ứng với $\gamma_1(t) = e^{2\pi it}$.

---

### 3. Ý nghĩa và ứng dụng

Kết quả $\pi_1(S^1) \cong \mathbb{Z}$ xuất hiện trong giải tích phức ($\int_\gamma \frac{dz}{z} = 2\pi i \cdot \operatorname{Ind}_\gamma(0)$), vật lý (lượng tử hóa từ thông) và robotics (phân loại cách dây cáp quấn quanh chướng ngại vật).

---

## 🌐 $\pi_1(S^n) = 0$ với $n \geq 2$

<div class="textbook-theorem" markdown="1">
**Định lý:** Mặt cầu $S^n$ đơn liên với mọi $n \geq 2$:

$$
\pi_1(S^n, *) = \{e\} \quad \forall n \geq 2
$$
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh (Ý tưởng chính):**  
Cho vòng $\gamma: [0,1] \to S^n$. Nếu $\gamma$ không toàn ánh (bỏ sót ít nhất một điểm $p \in S^n$), thì ảnh của $\gamma$ nằm trong $S^n \setminus \{p\} \cong \mathbb{R}^n$ (qua phép chiếu lập thể), vốn co rút được, nên $\gamma$ đồng luân với vòng hằng.

Trong trường hợp tổng quát (khi $\gamma$ có thể là đường cong phủ đầy $S^n$), ta chọn hai điểm đối cực $p, q \in S^n$ sao cho điểm cơ sở khác $p$ và $q$, rồi áp dụng bổ đề số Lebesgue để chia $[0,1]$ thành hữu hạn đoạn nhỏ sao cho mỗi đoạn chỉ rơi vào $S^n \setminus \{p\}$ hoặc $S^n \setminus \{q\}$, từ đó biến dạng đồng luân $\gamma$ (hoặc dùng trực tiếp định lý Seifert–van Kampen cho phủ mở $S^n = (S^n \setminus \{p\}) \cup (S^n \setminus \{q\})$ vì giao của chúng liên thông đường khi $n \ge 2$). Kết quả là mọi vòng trên $S^n$ ($n \ge 2$) đều co rút được về điểm cơ sở.
</div>

Sự tương phản $\pi_1(S^1) \cong \mathbb{Z}$ và $\pi_1(S^2) = 0$ cho thấy nhóm cơ bản phân biệt được $S^1$ và $S^2$. Lưu ý rằng các nhóm đồng luân bậc cao của $S^n$ ($n \ge 2$) vẫn rất phong phú (chẳng hạn $\pi_3(S^2) \cong \mathbb{Z}$ gắn với phân thớ Hopf).

---

## 🍩 $\pi_1(T^2) \cong \mathbb{Z} \times \mathbb{Z}$: Hình xuyến

### 1. Định lý tích

<div class="textbook-theorem" markdown="1">
**Định lý (Nhóm cơ bản của không gian tích):**  
Với hai không gian có điểm cơ sở $(X, x_0)$ và $(Y, y_0)$:

$$
\pi_1(X \times Y, (x_0, y_0)) \cong \pi_1(X, x_0) \times \pi_1(Y, y_0)
$$
</div>

**Ý tưởng chứng minh:** Mỗi vòng $\gamma: [0,1] \to X \times Y$ tương ứng duy nhất với cặp vòng thành phần $(\gamma_1, \gamma_2)$ qua hai phép chiếu $p_1: X \times Y \to X$ và $p_2: X \times Y \to Y$. Ánh xạ $\Phi([\gamma]) = ((p_1)_*[\gamma], (p_2)_*[\gamma])$ là một đẳng cấu nhóm vì đồng luân đường và phép nối vòng đều tác động độc lập trên từng tọa độ.

---

### 2. Áp dụng cho hình xuyến $T^2$ và $T^n$

Vì $T^2 = S^1 \times S^1$, áp dụng định lý tích ta thu được:

$$
\pi_1(T^2) = \pi_1(S^1 \times S^1) \cong \pi_1(S^1) \times \pi_1(S^1) \cong \mathbb{Z} \times \mathbb{Z}
$$

Hai phần tử sinh là $\alpha$ (vòng kinh tuyến) và $\beta$ (vòng vĩ tuyến), giao hoán với nhau, nên mọi phần tử đều có dạng $\alpha^m \beta^n$ ($m, n \in \mathbb{Z}$). Tổng quát, hình xuyến $n$ chiều $T^n = (S^1)^n$ có $\pi_1(T^n) \cong \mathbb{Z}^n$.

---

## 🎭 Nhóm cơ bản của các mặt đóng

### 1. Mặt định hướng được giống $g$ ($\Sigma_g$)

<div class="textbook-theorem" markdown="1">
**Định lý:**

$$
\pi_1(\Sigma_g) = \langle a_1, b_1, \ldots, a_g, b_g \mid [a_1,b_1] \cdots [a_g,b_g] = 1 \rangle
$$
</div>

Nhóm có $2g$ phần tử sinh và một quan hệ duy nhất (với hoán tử $[a_i, b_i] = a_i b_i a_i^{-1} b_i^{-1}$).
- Khi $g = 1$ ($T^2$): $\langle a, b \mid aba^{-1}b^{-1} = 1 \rangle \cong \mathbb{Z}^2$ (giao hoán).
- Khi $g \geq 2$: nhóm **không giao hoán**.

---

### 2. Mặt không định hướng được

**Mặt phẳng xạ ảnh thực $\mathbb{R}P^2$:**

<div class="textbook-theorem" markdown="1">
**Định lý:** $\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$.
</div>

**Ý tưởng chứng minh:** Ánh xạ thương đối cực $p: S^2 \to \mathbb{R}P^2$ là ánh xạ phủ hai lá với không gian phủ đơn liên $S^2$, nên $\pi_1(\mathbb{R}P^2)$ đẳng cấu với nhóm phép biến đổi phủ $\mathbb{Z}/2\mathbb{Z}$. Phần tử sinh tương ứng với ảnh của một đường nối hai điểm đối cực trên $S^2$ (đi qua hai lần tạo thành vòng khép kín trên $S^2$, vốn co rút được).

**Chai Klein $K$:**

<div class="textbook-theorem" markdown="1">
**Định lý:** $\pi_1(K) = \langle a, b \mid aba^{-1}b = 1 \rangle$.
</div>

Quan hệ $aba^{-1}b = 1$ (tức $aba^{-1} = b^{-1}$) cho thấy $\pi_1(K)$ là nhóm **không giao hoán**, khác hẳn với $\pi_1(T^2) \cong \mathbb{Z}^2$.

---

## 🛠️ Tổng hợp các kỹ thuật tính $\pi_1$

1. **Phương pháp không gian phủ:** Tìm một không gian phủ đơn liên (phủ phổ dụng) $p: \tilde{X} \to X$ rồi tính nhóm phép biến đổi phủ (như $\mathbb{R} \to S^1$ hay $S^2 \to \mathbb{R}P^2$).
2. **Tương đương đồng luân và co rút biến dạng:** Rút gọn không gian về một không gian con đơn giản hơn có cùng kiểu đồng luân. Chẳng hạn:
   - $\mathbb{R}^2 \setminus \{0\} \simeq S^1 \Rightarrow \pi_1(\mathbb{R}^2 \setminus \{0\}) \cong \mathbb{Z}$.
   - $\mathbb{R}^3 \setminus \{0\} \simeq S^2 \Rightarrow \pi_1(\mathbb{R}^3 \setminus \{0\}) = 0$.
3. **Định lý tích:** Dùng $\pi_1(X \times Y) \cong \pi_1(X) \times \pi_1(Y)$.
4. **Định lý Seifert–van Kampen (bài 06.04):** Phân tách $X = A \cup B$ thành các tập mở liên thông đường để tính $\pi_1(X)$ từ $\pi_1(A)$, $\pi_1(B)$ và $\pi_1(A \cap B)$ (ví dụ hình số $8$ có $\pi_1(S^1 \vee S^1) \cong \mathbb{Z} * \mathbb{Z}$).

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Henri Poincaré** – *"Analysis Situs"* (1895)

2. **Max Dehn & Poul Heegaard** – *Phân loại mặt* (1907)

3. **Herbert Seifert** – *"Topologie dreidimensionaler gefaserter Räume"* (1932)

### Giáo trình

4. **Allen Hatcher** – *Algebraic Topology*, **§1.1: Examples**

5. **James R. Munkres** – *Topology*, **§53–54: Computing $\pi_1$**

6. **William S. Massey** – *Algebraic Topology*, **Chapters 4–5**

7. **M. A. Armstrong** – *Basic Topology*, **Chapters 5–6**

---

## 🔗 Ứng dụng và liên kết

### Giải tích phức – Công thức tích phân Cauchy
Với hàm chỉnh hình $f$, $\int_\gamma \frac{f(z)\,dz}{z-a} = 2\pi i \cdot f(a) \cdot \operatorname{Ind}_\gamma(a)$ (khi $f \equiv 1$ cho $\int_\gamma \frac{dz}{z-a} = 2\pi i \cdot \operatorname{Ind}_\gamma(a)$), gắn trực tiếp với $\pi_1(\mathbb{C} \setminus \{a\}) \cong \mathbb{Z}$.

### Robotics – Tránh chướng ngại vật
Không gian cấu hình của một điểm di chuyển trên mặt phẳng có một vật cản có kiểu đồng luân $\mathbb{R}^2 \setminus \{0\} \simeq S^1$, nên các đường đi được phân loại theo chỉ số vòng quanh vật cản.

### Vật lý – Hiệu ứng Aharonov–Bohm
Độ dịch pha của electron quay quanh ống từ thông tỷ lệ với chỉ số vòng của đường đi.

### Khoa học dữ liệu – Phân tích dữ liệu tô-pô
Nhóm cơ bản và đồng điều bậc $1$ giúp phát hiện các cấu trúc vòng $1$ chiều trong đám mây điểm.

### Lý thuyết nút (Knot Theory)
Với một nút $K \subseteq S^3$, nhóm nút $\pi_1(S^3 \setminus K)$ là bất biến mạnh để phân biệt các nút khác nhau.

---

## Video tham khảo

- **xem trước** [3. Fundamental Group of the Circle - Pierre Albin](https://www.youtube.com/watch?v=GnQ1GuXH5vw) — Mat Neth, tiếng Anh. Chứng minh $\pi_1(S^1) \cong \mathbb{Z}$, trọng tâm của bài học.
- [Algebraic topology: Calculating the fundamental group](https://www.youtube.com/watch?v=BDrKDk8PQ_A) — Richard E Borcherds, tiếng Anh. Tính nhóm cơ bản của một số không gian quen thuộc.
- [M-19. Fundamental group of circle and torus](https://www.youtube.com/watch?v=VxLnh4L5LcU) — e-Content-Science, tiếng Anh. Trình bày song song $\pi_1(S^1)$ và $\pi_1(T^2)$.

## 🧩 Bài tập

### Đường tròn $\pi_1(S^1)$

1. **Chỉ số vòng:**  
   Với $\gamma(t) = e^{4\pi it}$, tính chỉ số vòng và lớp $[\gamma]$ trong $\pi_1(S^1, 1)$.

2. **Đồng luân tường minh:**  
   Viết tường minh phép đồng luân giữa $\gamma_2(t) = e^{4\pi it}$ và $\gamma_1 \cdot \gamma_1$.

3. **Nâng đường đi:**  
   Nâng đường đi $\gamma(t) = e^{\pi it}$ ($t \in [0,1]$) lên $\mathbb{R}$ xuất phát tại $0$ và tìm $\tilde{\gamma}(1)$.

### Mặt cầu $\pi_1(S^n)$

4. **$S^2$ đơn liên:**  
   Trình bày chứng minh chi tiết rằng mọi vòng trong $S^2$ đều đồng luân với vòng hằng.

5. **Mặt cầu $S^3$:**  
   Chứng minh $\pi_1(S^3) = 0$.

6. **Mặt cầu khoét một điểm:**  
   Xác định kiểu đồng luân và tính $\pi_1(S^2 \setminus \{\text{cực bắc}\})$.

### Hình xuyến $\pi_1(T^2)$

7. **Định lý tích:**  
   Chứng minh chi tiết $\pi_1(X \times Y) \cong \pi_1(X) \times \pi_1(Y)$.

8. **Phần tử sinh:**  
   Viết công thức tường minh cho hai vòng sinh $\alpha$ (kinh tuyến) và $\beta$ (vĩ tuyến) trên $T^2 = S^1 \times S^1$.

9. **Tính giao hoán:**  
   Giải thích hình học vì sao $\alpha \cdot \beta \simeq_p \beta \cdot \alpha$ trên $T^2$.

### Các mặt

10. **Mặt giống $2$:**  
    Nhóm $\pi_1(\Sigma_2)$ có bao nhiêu phần tử sinh và quan hệ là gì?

11. **$\mathbb{R}P^2$:**  
    Mô tả hình học vòng sinh của $\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$.

12. **Chai Klein:**  
    Từ quan hệ $aba^{-1}b = 1$ (tức $aba^{-1} = b^{-1}$) trong $\pi_1(K)$, giải thích vì sao $a$ và $b$ không giao hoán.

### Kỹ thuật tính toán

13. **Tương đương đồng luân:**  
    Nêu lập luận trực quan cho thấy $\mathbb{R}^2 \setminus \{p, q\} \simeq S^1 \vee S^1$.

14. **Co rút biến dạng:**  
    Kiểm tra $r(x) = x/\|x\|$ là co rút biến dạng từ $\mathbb{R}^2 \setminus \{0\}$ về $S^1$.

15. **Không gian phủ:**  
    Tóm tắt vai trò của ánh xạ phủ $p: \mathbb{R} \to S^1$ trong chứng minh $\pi_1(S^1) \cong \mathbb{Z}$.

### Nâng cao

16. **Hình số $8$:**  
    Tìm hiểu cách dùng định lý Van Kampen để tính $\pi_1(S^1 \vee S^1) \cong \mathbb{Z} * \mathbb{Z}$.

17. **Mặt phẳng khoét $k$ điểm:**  
    Xác định $\pi_1(\mathbb{R}^2 \setminus \{p_1, \ldots, p_k\})$ (đáp số: nhóm tự do $F_k$).

18. **Nhóm nút:**  
    Tìm hiểu nhóm nút của nút ba lá (trefoil knot) $K \subseteq S^3$ và lý do $\pi_1(S^3 \setminus K) \not\cong \mathbb{Z}$.

### Câu hỏi suy ngẫm

19. **Tại sao là $\mathbb{Z}$?:**  
    Giải thích vì sao $\pi_1(S^1)$ là $\mathbb{Z}$ chứ không phải $\mathbb{Q}$ hay $\mathbb{R}$.

20. **Ảnh hưởng của số chiều:**  
    Vì sao $\pi_1(S^1) \cong \mathbb{Z}$ nhưng $\pi_1(S^2) = 0$?

21. **Ứng dụng thực tế:**  
    Nêu một bài toán ứng dụng cụ thể trong đó việc tính $\pi_1$ mang lại thông tin trực tiếp.

---

## 📚 Đọc thêm

- **Hatcher, §1.1**
- **Munkres, §53–54**
- **Massey, Chapters 4–5**
- **Armstrong, Chapters 5–6**
- **Stillwell, Classical Topology**

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã tính nhóm cơ bản cho các không gian cơ bản:
- $\pi_1(S^1) \cong \mathbb{Z}$ (chứng minh qua không gian phủ $\mathbb{R} \to S^1$ và chỉ số vòng),
- $\pi_1(S^n) = 0$ với mọi $n \ge 2$,
- $\pi_1(T^2) \cong \mathbb{Z}^2$ (từ định lý tích $\pi_1(X \times Y) \cong \pi_1(X) \times \pi_1(Y)$),
- $\pi_1(\Sigma_g) = \langle a_1, b_1, \ldots, a_g, b_g \mid [a_1,b_1]\cdots[a_g,b_g] = 1 \rangle$, $\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$, và $\pi_1(K) = \langle a, b \mid aba^{-1}b = 1 \rangle$.

**Tiếp theo:** Lecture 06.03 về **Lý thuyết không gian phủ** — xây dựng hệ thống các định lý nâng, phủ phổ dụng, phép biến đổi phủ và định lý phân loại không gian phủ.

---

*"To compute $\pi_1$, find the right tool: covering spaces, Van Kampen, or homotopy equivalence."*

---

**Previous:** [Lecture 06.01: Fundamental Group](/contents/vi/topology-chapter06/06_01_Fundamental_Group/)  
**Next:** [Lecture 06.03: Covering Spaces](/contents/vi/topology-chapter06/06_03_Covering_Spaces/)
