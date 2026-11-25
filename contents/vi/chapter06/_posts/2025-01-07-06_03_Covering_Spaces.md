---
layout: post
title: "Lecture 06.03: Covering Spaces Theory"
lang: vi
lang-ref: lecture-06-03
chapter: 6
lecture: 3
categories: [chapter06]
tags: [covering-spaces, universal-cover, deck-transformations, lifting]
description: "Covering spaces: định nghĩa, lifting properties, universal cover, deck transformations, và classification theorem"
---

**Lý thuyết không gian phủ ($p: \tilde{X} \to X$)**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu bạn từng học lý thuyết Galois trong đại số đại cương, chắc hẳn bạn nhớ mối tương ứng kỳ diệu giữa các *trường trung gian* và các *nhóm con của nhóm Galois*. Thật đáng kinh ngạc: trong tô-pô học cũng tồn tại một **đối xứng gương hoàn hảo hệt như vậy**! Mọi **không gian phủ liên thông** $$\tilde{X} \to X$$ của một không gian đẹp $$X$$ tương ứng **một-một** với các **nhóm con** của nhóm cơ bản $$\pi_1(X)$$ — trong đó **không gian phủ phổ dụng** (đơn liên) đứng trên đỉnh cao nhất ứng với nhóm con tầm thường $$\{1\}$$!

Lý thuyết **không gian phủ** (covering spaces) mô tả cấu trúc toàn cục của một không gian tô-pô thông qua một không gian khác đơn giản hơn nhưng có cấu trúc địa phương giống hệt nó: không gian $\tilde{X}$ "phủ" lên $X$ sao cho trên mỗi lân cận đủ nhỏ của $X$, $\tilde{X}$ trông như nhiều bản sao rời nhau (các "lá") xếp chồng lên nhau.

Trong bài học này, chúng ta xây dựng có hệ thống các nội dung chính: định nghĩa không gian phủ qua lân cận phủ đều, các ví dụ tiêu chuẩn ($\mathbb{R} \to S^1$, $z \mapsto z^n$, $S^n \to \mathbb{R}P^n$, $\mathbb{R}^2 \to T^2$, cây vô hạn phủ hình số $8$), các định lý nâng (nâng đường đi, nâng đồng luân và tiêu chuẩn nâng), không gian phủ phổ dụng (universal cover), nhóm các phép biến đổi phủ (deck transformations) và Định lý phân loại không gian phủ — tương ứng song ánh giữa các không gian phủ liên thông của $X$ với các lớp liên hợp của nhóm con của $\pi_1(X)$.

![Covering space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Covering_space.svg/500px-Covering_space.svg.png)  
*Minh họa không gian phủ với nhiều lá xếp chồng lên không gian đáy*

Lý thuyết này là công cụ quan trọng để tính nhóm cơ bản, nghiên cứu mặt Riemann trong giải tích phức, và tạo ra sự tương đồng cấu trúc nổi tiếng với lý thuyết Galois trong đại số.

---

## 🗺️ Kiến thức cần nhớ: Lý thuyết Không gian Phủ là gì và nghiên cứu những gì?

### 1. Ánh xạ Phủ (Covering Map) & Lân cận Được phủ đều
- **Bản chất:** Ánh xạ toàn ánh liên tục $$p: \tilde{X} \to X$$ gọi là **ánh xạ phủ** nếu quanh mọi điểm $$x \in X$$ đều có lân cận mở $$U$$ sao cho nghịch ảnh $$p^{-1}(U)$$ tách thành một chồng các "tờ bánh kếp" mở rời nhau $$\bigsqcup V_\alpha$$, mỗi tờ đồng phôi hoàn hảo với $$U$$ qua $$p$$! Số lượng tờ gọi là **số lá (bậc)** của phủ.

### 2. Hai Tính chất Nâng (Lifting Properties) & Tiêu chuẩn Nâng
- **Nâng đường đi & đồng luân:** Mọi đường đi trên $$X$$ đều nâng lên duy nhất một đường đi trên $$\tilde{X}$$ khi chọn trước điểm xuất phát.
- **Tiêu chuẩn nâng tổng quát:** Ánh xạ $$f: (Y, y_0) \to (X, x_0)$$ nâng lên được thành $$\tilde{f}: (Y, y_0) \to (\tilde{X}, \tilde{x}_0)$$ khi và chỉ khi $$f_*(\pi_1(Y, y_0)) \subseteq p_*(\pi_1(\tilde{X}, \tilde{x}_0))$$!

### 3. Tương ứng Galois của Không gian Phủ & Nhóm Biến đổi Phủ (Deck Transformations)
- **Định lý Phân loại:** Mọi phủ liên thông của $$X$$ (liên thông đường, liên thông đường địa phương và bán đơn liên địa phương) tương ứng 1–1 với các lớp liên hợp của nhóm con $$H \le \pi_1(X)$$, với số lá đúng bằng chỉ số $$[\pi_1(X) : H]$$!
- **Phủ chuẩn tắc (Regular covering):** Khi $$H \trianglelefteq \pi_1(X)$$ là nhóm con chuẩn tắc, nhóm các phép tự đồng phôi bảo toàn thớ (**Deck transformations**) thỏa mãn $$\operatorname{Deck}(\tilde{X}/X) \cong \pi_1(X)/H$$!

---

## 🧮 Ví dụ tính tay làm từng bước: Khảo sát trọn vẹn Phủ 3 lá $$p_3(z) = z^3: S^1 \to S^1$$

Xem đường tròn là $$S^1 = \{z \in \mathbb{C} : \lvert z\rvert = 1\}$$ và xét ánh xạ $$p_3: S^1 \to S^1,\; p_3(z) = z^3$$:

1. **Đếm số lá tại điểm gốc $$1 \in S^1$$:** Giải $$z^3 = 1$$ ta được đúng **3 điểm** (3 căn bậc ba của đơn vị):
   $$
   p_3^{-1}(1) = \left\{1,\; \omega = e^{2\pi i/3},\; \omega^2 = e^{4\pi i/3}\right\} \quad (\text{phủ 3 lá!}).
   $$
2. **Kiểm tra nhóm con ảnh $$(p_3)_*(\pi_1(S^1)) \le \pi_1(S^1)$$:**
   Lấy vòng sinh chuẩn $$\gamma(s) = e^{2\pi i s}$$ (ứng với $$1 \in \mathbb{Z}$$). Ảnh của nó qua $$p_3$$ là:
   $$
   (p_3 \circ \gamma)(s) = (e^{2\pi i s})^3 = e^{6\pi i s} \quad (\text{quấn 3 vòng} \implies 3 \in \mathbb{Z}!).
   $$
   Vậy nhóm con tương ứng là **$$H = 3\mathbb{Z} \le \mathbb{Z}$$**! Kiểm tra chỉ số: $$[\mathbb{Z} : 3\mathbb{Z}] = 3$$ — khớp chính xác số lá của phủ!
3. **Tính Nhóm Biến đổi Phủ $$\operatorname{Deck}(p_3)$$:**
   Ta cần tìm các phép đồng phôi $$\tau: S^1 \to S^1$$ sao cho $$p_3(\tau(z)) = p_3(z)$$, tức $$(\tau(z))^3 = z^3$$. Có đúng **3 phép quay**:
   $$
   \tau_0(z) = z, \qquad \tau_1(z) = \omega z \;(\text{quay } 120^\circ), \qquad \tau_2(z) = \omega^2 z \;(\text{quay } 240^\circ).
   $$
   Nhóm này đẳng cấu với **$$\mathbb{Z}/3\mathbb{Z} \cong \mathbb{Z}/3\mathbb{Z} = \pi_1(S^1)/H$$** — xác nhận hoàn hảo Tương ứng Galois!

### Giải thích: Đọc bản đồ Tương ứng Galois của Không gian Phủ

#### Bước 1: Hình dung "tháp các không gian phủ" của $$X$$
Đứng trên đỉnh cao nhất là **phủ phổ dụng $$\tilde{X}$$** (đơn liên, ứng với nhóm con nhỏ nhất $$\{1\}$$); nằm dưới đáy là chính $$X$$ (ứng với toàn bộ $$\pi_1(X)$$); ở giữa là mọi phủ trung gian ứng với từng nhóm con $$H \le \pi_1(X)$$.

#### Bước 2: Dùng ánh xạ phủ để tính $$\pi_1$$ của không gian khó
Ví dụ muốn tính $$\pi_1(\mathbb{R}P^2)$$: ta đã có phủ 2 lá $$S^2 \to \mathbb{R}P^2$$ với $$S^2$$ đơn liên (phủ phổ dụng!) và nhóm biến đổi phủ $$\{\pm 1\} \cong \mathbb{Z}/2\mathbb{Z}$$ $$\implies$$ đọc thẳng **$$\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$$**!

#### Bước 3: Dùng không gian phủ để chứng minh định lý thuần túy của Lý thuyết Nhóm!
Một phép màu ngược chiều (Định lý Nielsen–Schreier): *mọi nhóm con của một nhóm tự do đều là nhóm tự do!* Chứng minh thuần đại số rất dài, nhưng bằng không gian phủ chỉ mất 3 dòng: nhóm tự do là $$\pi_1$$ của một đồ thị (bó đường tròn); mọi không gian phủ của một đồ thị lại là **một đồ thị**; mà $$\pi_1$$ của đồ thị bất kỳ luôn là nhóm tự do!

#### Bước 4: Kiểm tra điều kiện tồn tại phủ phổ dụng
Không gian như "bông tai Hawaii" (vô hạn đường tròn bán kính $$1/n$$ chạm tại gốc) có các vòng nhỏ tùy ý không co rút được quanh gốc — vi phạm tính *bán đơn liên địa phương* nên **không** có phủ phổ dụng!

$$
\{\text{Phủ liên thông }\tilde{X} \to X\}
\;\xleftrightarrow{\;\text{Tương ứng Galois (1–1)}\;}\;
\{\text{Nhóm con }H \le \pi_1(X)\},
\qquad
\text{số lá} = [\pi_1(X) : H].
$$

---

## 🎯 Định nghĩa không gian phủ

### 1. Lân cận phủ đều (Evenly Covered Neighborhoods)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian phủ):**  
Ánh xạ liên tục toàn ánh $p: \tilde{X} \to X$ được gọi là một **ánh xạ phủ** (covering map), và $\tilde{X}$ là **không gian phủ** (covering space) của $X$, nếu với mọi $x \in X$ tồn tại một lân cận mở $U$ của $x$ (**lân cận phủ đều** – evenly covered neighborhood) sao cho:

$$
p^{-1}(U) = \bigsqcup_{\alpha \in A} V_\alpha
$$
</div>

là hợp rời khác rỗng của các tập mở $V_\alpha \subseteq \tilde{X}$, và với mỗi $\alpha \in A$, hạn chế $p|_{V_\alpha}: V_\alpha \to U$ là một phép đồng phôi.

**Thuật ngữ:** $\tilde{X}$ là không gian phủ (không gian toàn phần), $X$ là không gian đáy (base space), $p$ là ánh xạ phủ, và các tập $V_\alpha$ là các **lá** (sheets) phía trên $U$.

![Evenly covered neighborhood](https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/Covering_map.svg/400px-Covering_map.svg.png)  
*Minh họa lân cận phủ đều – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Covering_map.svg)*

---

### 2. Các tính chất cơ bản

<div class="textbook-theorem" markdown="1">
**Định lý:** Mọi ánh xạ phủ $p: \tilde{X} \to X$ đều có các tính chất sau:
1. Liên tục và toàn ánh,
2. Là ánh xạ mở (ảnh của tập mở là tập mở),
3. Là đồng phôi địa phương (mọi điểm trong $\tilde{X}$ đều có một lân cận mở được $p$ ánh xạ đồng phôi lên một tập mở trong $X$).
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Suy trực tiếp từ tính chất lân cận phủ đều (xem phần bài tập).
</div>

Lưu ý rằng một ánh xạ phủ không nhất thiết là đồng phôi toàn cục (chẳng hạn $p: \mathbb{R} \to S^1$ không phải đơn ánh), và ngược lại không phải mọi đồng phôi địa phương toàn ánh đều là ánh xạ phủ.

---

## 📊 Các ví dụ tiêu chuẩn

### Ví dụ 1: $\mathbb{R} \to S^1$ (Phủ phổ dụng của đường tròn)

<div class="textbook-definition" markdown="1">
**Định nghĩa:** $p: \mathbb{R} \to S^1$, $p(t) = e^{2\pi it}$.
</div>

Với mỗi $z = e^{i\theta} \in S^1$, tập mở $U = S^1 \setminus \{-z\}$ có nghịch ảnh $p^{-1}(U) = \bigsqcup_{n \in \mathbb{Z}} \left(\frac{\theta}{2\pi} - \frac{1}{2} + n,\; \frac{\theta}{2\pi} + \frac{1}{2} + n\right)$, là hợp rời đếm được của các khoảng mở mà mỗi khoảng đồng phôi với $U$ qua $p$. Vì $\mathbb{R}$ đơn liên, đây là **phủ phổ dụng** của $S^1$.

---

### Ví dụ 2: $z \mapsto z^n$ trên $S^1$

<div class="textbook-definition" markdown="1">
**Định nghĩa:** $p: S^1 \to S^1$, $p(z) = z^n$ ($n \geq 2$).
</div>

Với $U = S^1 \setminus \{-z_0\}$, nghịch ảnh $p^{-1}(U)$ gồm $n$ cung mở rời nhau, mỗi cung đồng phôi với $U$ qua $p$. Đây là phủ $n$ lá; các phép biến đổi phủ là các phép quay góc $2\pi k/n$ ($k = 0, \ldots, n-1$).

---

### Ví dụ 3: $S^n \to \mathbb{R}P^n$ (Phủ đối cực hai lá)

<div class="textbook-definition" markdown="1">
**Định nghĩa:** $p: S^n \to \mathbb{R}P^n$ là ánh xạ thương đồng nhất $x \sim -x$.
</div>

Mỗi điểm của $\mathbb{R}P^n$ có đúng $2$ nghịch ảnh đối cực trên $S^n$, và mọi lân cận đủ nhỏ tránh các cặp đối cực đều được phủ đều bởi $2$ lá. Với $n \geq 2$, vì $\pi_1(S^n) = 0$, $S^n$ là **phủ phổ dụng** của $\mathbb{R}P^n$ (còn khi $n = 1$, $S^1 \to \mathbb{R}P^1 \cong S^1$ là phủ hai lá nhưng không phải phủ phổ dụng).

---

### Ví dụ 4: $\mathbb{R}^2 \to T^2$ (Phủ phổ dụng của hình xuyến)

<div class="textbook-definition" markdown="1">
**Định nghĩa:** $p: \mathbb{R}^2 \to T^2$, $p(x,y) = (e^{2\pi ix}, e^{2\pi iy})$.
</div>

Đây là ánh xạ thương theo tác động tịnh tiến của mạng $\mathbb{Z}^2$ trên $\mathbb{R}^2$, có đếm được vô hạn lá và là phủ phổ dụng của $T^2$.

---

### Ví dụ 5: Phủ phổ dụng của hình số $8$ ($S^1 \vee S^1$)

Phủ phổ dụng của hình số $8$ là **cây vô hạn bậc $4$** (đồ thị Cayley của nhóm tự do $\mathbb{Z} * \mathbb{Z}$), trong đó mỗi đỉnh có $4$ cạnh nối (hai cạnh ứng với vòng thứ nhất theo hai chiều và hai cạnh ứng với vòng thứ hai). Vì mọi cây đều co rút được nên đơn liên, ví dụ này cho thấy hình dạng toàn cục của phủ phổ dụng có thể khác hẳn không gian đáy.

---

## 🔼 Các định lý nâng (Lifting Properties)

### 1. Định lý nâng đường đi (Path Lifting Theorem)

<div class="textbook-theorem" markdown="1">
**Định lý (Nâng đường đi):**  
Cho ánh xạ phủ $p: \tilde{X} \to X$, một đường đi $\gamma: [0,1] \to X$ và một điểm $\tilde{x}_0 \in p^{-1}(\gamma(0))$. Khi đó tồn tại duy nhất một đường nâng liên tục $\tilde{\gamma}: [0,1] \to \tilde{X}$ sao cho $p \circ \tilde{\gamma} = \gamma$ và $\tilde{\gamma}(0) = \tilde{x}_0$.
</div>

**Phác thảo chứng minh:** Bằng bổ đề số Lebesgue, chia $[0,1]$ thành hữu hạn đoạn nhỏ sao cho ảnh của mỗi đoạn nằm trong một lân cận phủ đều; nâng duy nhất từng đoạn qua nghịch đảo địa phương của $p$ và dán liên tiếp. Tính duy nhất trên toàn $[0,1]$ suy từ tính liên thông của $[0,1]$.

![Path lifting](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e1/Covering_space_path_lifting.svg/400px-Covering_space_path_lifting.svg.png)  
*Minh họa nâng đường đi duy nhất lên không gian phủ*

---

### 2. Định lý nâng đồng luân (Homotopy Lifting Theorem)

<div class="textbook-theorem" markdown="1">
**Định lý (Nâng đồng luân):**  
Cho ánh xạ phủ $p: \tilde{X} \to X$, một phép đồng luân $F: [0,1] \times [0,1] \to X$ và một đường nâng $\tilde{F}_0: [0,1] \to \tilde{X}$ của $F(\cdot, 0)$. Khi đó tồn tại duy nhất một phép đồng luân nâng $\tilde{F}: [0,1] \times [0,1] \to \tilde{X}$ sao cho $p \circ \tilde{F} = F$ và $\tilde{F}(s, 0) = \tilde{F}_0(s)$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Chia hình vuông $[0,1]^2$ thành lưới hình vuông con đủ nhỏ sao cho ảnh của từng ô nằm trong một lân cận phủ đều, rồi nâng tuần tự từng ô.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả (Bất biến điểm cuối theo đồng luân đường):**  
Nếu $\gamma \simeq_p \delta$ là hai đường đi đồng luân đường từ $x_0$ đến $x_1$, thì các đường nâng $\tilde{\gamma}, \tilde{\delta}$ xuất phát từ cùng một điểm $\tilde{x}_0 \in p^{-1}(x_0)$ có **cùng điểm cuối** và đồng luân đường với nhau trong $\tilde{X}$.
</div>

Đây là tính chất then chốt giúp dùng không gian phủ để tính $\pi_1(S^1) \cong \mathbb{Z}$.

---

### 3. Tiêu chuẩn nâng tổng quát (Lifting Criterion)

<div class="textbook-theorem" markdown="1">
**Định lý (Tiêu chuẩn nâng):**  
Cho ánh xạ phủ $p: (\tilde{X}, \tilde{x}_0) \to (X, x_0)$ và ánh xạ liên tục $f: (Y, y_0) \to (X, x_0)$, trong đó $Y$ **liên thông đường và liên thông đường địa phương**. Khi đó tồn tại ánh xạ nâng liên tục $\tilde{f}: (Y, y_0) \to (\tilde{X}, \tilde{x}_0)$ ($p \circ \tilde{f} = f$) khi và chỉ khi:

$$
f_*(\pi_1(Y, y_0)) \subseteq p_*(\pi_1(\tilde{X}, \tilde{x}_0))
$$
</div>

Tiêu chuẩn này đưa bài toán tô-pô về sự tồn tại ánh xạ nâng về một điều kiện bao hàm nhóm con thuần túy đại số.

---

## 🌟 Không gian phủ phổ dụng (Universal Covering Space)

### 1. Định nghĩa

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phủ phổ dụng):**  
Không gian phủ $p: \tilde{X} \to X$ được gọi là **không gian phủ phổ dụng** của $X$ nếu $\tilde{X}$ đơn liên ($\pi_1(\tilde{X}) = \{e\}$) và liên thông đường.
</div>

Thuật ngữ "phổ dụng" phản ánh việc $\tilde{X}$ phủ lên mọi không gian phủ liên thông khác của $X$.

---

### 2. Sự tồn tại và tính duy nhất

<div class="textbook-theorem" markdown="1">
**Định lý (Tồn tại phủ phổ dụng):**  
Không gian $X$ có phủ phổ dụng nếu $X$:
1. Liên thông đường,
2. Liên thông đường địa phương,
3. Nửa đơn liên địa phương (semilocally simply connected): mọi điểm $x \in X$ có lân cận $U$ sao cho mọi vòng trong $U$ đều co rút được trong $X$.
</div>

Mọi đa tạp liên thông và mọi phức CW liên thông đều thỏa mãn ba điều kiện này. Một phản ví dụ không có phủ phổ dụng là **hoa tai Hawaii** (hợp đếm được các đường tròn tiếp xúc tại một điểm có bán kính tiến về $0$), vì nó không nửa đơn liên địa phương tại điểm chung.

<div class="textbook-theorem" markdown="1">
**Định lý (Tính duy nhất):**  
Nếu $X$ có phủ phổ dụng, thì phủ phổ dụng đó là duy nhất sai khác một đẳng cấu không gian phủ.
</div>

---

## 🔄 Nhóm các phép biến đổi phủ (Deck Transformations)

### 1. Định nghĩa và cấu trúc nhóm

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phép biến đổi phủ):**  
Với ánh xạ phủ $p: \tilde{X} \to X$, một **phép biến đổi phủ** (deck transformation hay covering automorphism) là một phép đồng phôi $f: \tilde{X} \to \tilde{X}$ thỏa mãn:

$$
p \circ f = p
$$
</div>

Tập hợp tất cả các phép biến đổi phủ ký hiệu là $\operatorname{Aut}(\tilde{X}/X)$ (hoặc $G(\tilde{X})$).

<div class="textbook-theorem" markdown="1">
**Định lý:** $\operatorname{Aut}(\tilde{X}/X)$ là một nhóm dưới phép hợp ánh xạ.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** $\operatorname{id}_{\tilde{X}} \in \operatorname{Aut}(\tilde{X}/X)$, và nếu $f, g$ bảo toàn $p$ thì $f \circ g$ và $f^{-1}$ cũng bảo toàn $p$.
</div>

---

### 2. Trường hợp phủ phổ dụng

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Nếu $\tilde{X}$ là phủ phổ dụng của không gian liên thông đường và liên thông đường địa phương $X$, thì:

$$
\text{Aut}(\tilde{X}/X) \cong \pi_1(X)
$$
</div>

Hệ quả là $X$ đồng phôi với không gian quỹ đạo của phủ phổ dụng dưới tác động của $\pi_1(X)$:

$$
X = \tilde{X} / \pi_1(X)
$$

**Ví dụ:**
- $\mathbb{R} \to S^1$: các phép biến đổi phủ là $f_n(t) = t + n$ ($n \in \mathbb{Z}$), nên $\operatorname{Aut}(\mathbb{R}/S^1) \cong \mathbb{Z} \cong \pi_1(S^1)$.
- $S^2 \to \mathbb{R}P^2$: các phép biến đổi phủ là $\{\operatorname{id}, x \mapsto -x\} \cong \mathbb{Z}/2\mathbb{Z} \cong \pi_1(\mathbb{R}P^2)$.

---

## 📋 Định lý phân loại không gian phủ

### 1. Định lý tương ứng

<div class="textbook-theorem" markdown="1">
**Định lý (Phân loại không gian phủ):**  
Cho $X$ liên thông đường, liên thông đường địa phương và nửa đơn liên địa phương. Khi đó có một song ánh giữa các lớp đẳng cấu của không gian phủ liên thông của $X$ và các lớp liên hợp của nhóm con của $\pi_1(X)$:

$$
\{\text{Coverings of } X\} / \text{isomorphism} \leftrightarrow \{\text{Subgroups of } \pi_1(X)\} / \text{conjugacy}
$$
</div>

Cụ thể, mỗi không gian phủ liên thông $p: (\tilde{X}, \tilde{x}_0) \to (X, x_0)$ tương ứng với nhóm con $p_*(\pi_1(\tilde{X}, \tilde{x}_0)) \leq \pi_1(X, x_0)$. Phủ phổ dụng ứng với nhóm con tầm thường $\{e\}$.

---

### 2. Phủ chuẩn tắc (Normal / Regular Coverings)

<div class="textbook-definition" markdown="1">
**Định nghĩa:** Không gian phủ liên thông $p: \tilde{X} \to X$ được gọi là **phủ chuẩn tắc** (normal hay regular) nếu $p_*(\pi_1(\tilde{X}, \tilde{x}_0))$ là một nhóm con chuẩn tắc của $\pi_1(X, x_0)$.
</div>

<div class="textbook-theorem" markdown="1">
**Định lý:** Phủ liên thông $p: \tilde{X} \to X$ là phủ chuẩn tắc khi và chỉ khi $\operatorname{Aut}(\tilde{X}/X)$ tác động bắc cầu trên mỗi sợi $p^{-1}(x)$. Khi đó $\operatorname{Aut}(\tilde{X}/X) \cong \pi_1(X)/p_*(\pi_1(\tilde{X}))$.
</div>

Đặc biệt, phủ phổ dụng luôn là phủ chuẩn tắc vì $\{e\}$ là nhóm con chuẩn tắc.

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Henri Poincaré** – *"Analysis Situs"* (1895)

2. **Hermann Weyl** – *"Die Idee der Riemannschen Fläche"* (1913)

3. **Heinz Hopf** – *"Fundamentalgruppe und zweite Bettische Gruppe"* (1941)

### Giáo trình

4. **Allen Hatcher** – *Algebraic Topology*, **§1.3: Covering Spaces**

5. **James R. Munkres** – *Topology*, **§53–54: Covering Spaces**

6. **William S. Massey** – *Algebraic Topology*, **Chapters 5–6**

7. **Edwin Spanier** – *Algebraic Topology*, **Chapter 2**

8. **Glen E. Bredon** – *Topology and Geometry*, **Chapter II**

---

## 🔗 Ứng dụng và liên kết

### Giải tích phức – Mặt Riemann
Các hàm đa trị như $\sqrt{z}, \log z$ trở thành đơn trị trên không gian phủ tương ứng, và đơn trị hóa (monodromy) tương ứng với các phép biến đổi phủ.

### Tương đồng với lý thuyết Galois
Không gian phủ tương ứng với mở rộng trường, phủ chuẩn tắc tương ứng với mở rộng Galois, nhóm phép biến đổi phủ tương ứng với nhóm Galois, và định lý phân loại không gian phủ tương đồng với định lý cơ bản của lý thuyết Galois.

### Hình học vi phân – Phủ Riemann
Một metric Riemann trên $X$ được nâng tự nhiên lên không gian phủ $\tilde{X}$, kéo theo đường trắc địa nâng thành đường trắc địa.

### Vật lý – Lý thuyết chuẩn
Phân thớ $U(1)$ và các phân loại cấu hình tô-pô trong lý thuyết trường chuẩn liên hệ chặt chẽ với lý thuyết phủ và phân thớ.

### Lý thuyết số – Đường cong modular
Đường cong modular $\mathbb{H}/SL_2(\mathbb{Z})$ là thương của nửa mặt phẳng trên $\mathbb{H}$ dưới tác động của nhóm modular.

---

## Video tham khảo

- **xem trước** [Algebraic Topology 7: Covering Spaces](https://www.youtube.com/watch?v=Y4MVNILPyxs) — Math at Andrews University, tiếng Anh. Trình bày định nghĩa không gian phủ trước khi đi vào các định lý nâng.
- [7. Covering Spaces; Lifting Criterion - Pierre Albin](https://www.youtube.com/watch?v=6C2egTGwJsU) — Mat Neth, tiếng Anh. Bài giảng về không gian phủ và tiêu chuẩn nâng.
- [9. Classification of Covering Spaces; Deck Transformations - Pierre Albin](https://www.youtube.com/watch?v=kNePsKDbpUM) — Mat Neth, tiếng Anh. Phân loại không gian phủ và nhóm phép biến đổi phủ.

## 🧩 Bài tập

### Định nghĩa và tính chất cơ bản

1. **Kiểm tra ánh xạ phủ:**  
   Chứng minh $p: \mathbb{R} \to S^1$, $p(t) = e^{2\pi it}$ là ánh xạ phủ bằng cách chỉ rõ các lân cận phủ đều.

2. **Không phải ánh xạ phủ:**  
   Xét $f: [0,1) \to S^1$, $f(t) = e^{2\pi it}$. Dù $f$ liên tục và song ánh, hãy giải thích vì sao $f$ không phải ánh xạ phủ (gợi ý: xét lân cận của $1 \in S^1$).

3. **Số lá:**  
   Ánh xạ phủ $p: S^1 \to S^1$, $p(z) = z^3$ có bao nhiêu lá? Mô tả sợi $p^{-1}(1)$.

### Định lý nâng

4. **Nâng đường đi:**  
   Với $p: \mathbb{R} \to S^1$ và $\gamma(t) = e^{4\pi it}$, tìm đường nâng $\tilde{\gamma}$ xuất phát tại $0$ và giá trị $\tilde{\gamma}(1)$.

5. **Nâng đồng luân:**  
   Giải thích cách nâng một phép đồng luân $F: [0,1]^2 \to S^1$ giữa hai vòng lên $\mathbb{R}$.

6. **Tiêu chuẩn nâng:**  
   Dùng tiêu chuẩn nâng chứng minh mọi ánh xạ liên tục $f: S^2 \to S^1$ đều nâng được lên $\mathbb{R}$ (vì $\pi_1(S^2) = 0$).

### Phủ phổ dụng

7. **$\mathbb{R}^2 \to T^2$:**  
   Kiểm tra $\mathbb{R}^2$ đơn liên và là phủ phổ dụng của $T^2$.

8. **$S^2 \to \mathbb{R}P^2$:**  
   Giải thích vì sao $S^2$ là phủ phổ dụng của $\mathbb{R}P^2$.

9. **Hình số $8$:**  
   Phác họa cấu trúc cây vô hạn phủ $S^1 \vee S^1$ và giải thích vì sao nó đơn liên.

### Phép biến đổi phủ

10. **$\mathbb{R} \to S^1$:**  
    Chứng minh $f_n(t) = t + n$ là các phép biến đổi phủ của $\mathbb{R} \to S^1$.

11. **Cấu trúc nhóm:**  
    Kiểm tra $\operatorname{Aut}(\mathbb{R}/S^1) \cong \mathbb{Z}$ và chỉ ra phần tử sinh.

12. **Phép đối cực:**  
    Với $S^n \to \mathbb{R}P^n$, kiểm tra $f(x) = -x$ thỏa $p \circ f = p$.

### Phân loại không gian phủ

13. **Phân loại các phủ của $S^1$:**  
    Liệt kê tất cả các nhóm con của $\pi_1(S^1) \cong \mathbb{Z}$ và chỉ ra không gian phủ liên thông tương ứng với từng nhóm con.

14. **Phủ $n$ lá:**  
    Ánh xạ phủ $p(z) = z^n$ trên $S^1$ tương ứng với nhóm con nào của $\mathbb{Z}$?

15. **Phủ chuẩn tắc:**  
    Giải thích vì sao phủ phổ dụng luôn là phủ chuẩn tắc.

### Nâng cao

16. **Tác động Monodromy:**  
    Tìm hiểu tác động của $\pi_1(X, x_0)$ lên sợi $p^{-1}(x_0)$ và mối liên hệ với các phép biến đổi phủ.

17. **Tương đồng Galois:**  
    Lập bảng so sánh các đối tượng tương ứng giữa lý thuyết không gian phủ và lý thuyết Galois.

18. **Hoa tai Hawaii:**  
    Giải thích vì sao hoa tai Hawaii không có phủ phổ dụng (không nửa đơn liên địa phương).

### Câu hỏi suy ngẫm

19. **Ý nghĩa của từ "phổ dụng":**  
    Vì sao phủ phổ dụng mang tên gọi này?

20. **Trực giác hình học:**  
    Mô tả ý tưởng không gian phủ bằng một ví dụ trực quan ngoài toán học (như bãi đỗ xe nhiều tầng dạng xoắn ốc).

21. **Ứng dụng:**  
    Nêu $3$ ứng dụng của lý thuyết không gian phủ trong các nhánh toán học hoặc vật lý.

---

## 📚 Đọc thêm

- **Hatcher, §1.3**
- **Munkres, §53–54**
- **Massey, Chapters 5–6**
- **Bredon, Chapter II**
- **Spanier, Chapter 2**

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã hệ thống hóa lý thuyết **không gian phủ**: định nghĩa qua lân cận phủ đều, các ví dụ tiêu biểu ($\mathbb{R} \to S^1$, $S^n \to \mathbb{R}P^n$, $\mathbb{R}^2 \to T^2$, cây vô hạn phủ $S^1 \vee S^1$), các định lý nâng đường đi, nâng đồng luân và tiêu chuẩn nâng. Dưới điều kiện liên thông đường, liên thông đường địa phương và nửa đơn liên địa phương, không gian $X$ có phủ phổ dụng $\tilde{X}$ duy nhất với $\operatorname{Aut}(\tilde{X}/X) \cong \pi_1(X)$ và $X \cong \tilde{X}/\pi_1(X)$, đồng thời các không gian phủ liên thông của $X$ tương ứng song ánh với các lớp liên hợp của nhóm con của $\pi_1(X)$.

**Tiếp theo:** Lecture 06.04 về **Định lý Seifert–van Kampen** — tính nhóm cơ bản bằng cách phân tách không gian thành các phần đơn giản hơn.

---

*"Covering spaces: where local meets global, and geometry becomes algebra."*

---

**Previous:** [Lecture 06.02: Computing π₁](/contents/vi/topology-chapter06/06_02_Computing_Fundamental_Group/)  
**Next:** [Lecture 06.04: Van Kampen's Theorem](/contents/vi/topology-chapter06/06_04_Van_Kampen_Theorem/)
