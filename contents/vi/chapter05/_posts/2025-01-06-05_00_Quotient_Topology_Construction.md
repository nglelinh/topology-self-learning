---
layout: post
title: "Lecture 05.00: Quotient Topology and Construction"
lang: vi
lang-ref: lecture-05-00
chapter: 5
lecture: 0
categories: [chapter05]
tags: [quotient-topology, equivalence-relations, quotient-map, identification]
description: "Quotient topology: định nghĩa, construction, equivalence relations, và quotient maps"
---

**Tô-pô thương và Phép xây dựng không gian thương**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu bạn từng chơi trò chơi điện tử cổ điển như *Pac-Man* hay *Asteroids*, bạn đã sống trong một **không gian thương** mà không hay biết! Khi phi thuyền bay chạm mép phải màn hình, nó lập tức xuất hiện trở lại ở mép trái; bay chạm mép trên, nó trồi lên từ mép dưới. Về mặt toán học, lập trình viên đã lấy hình chữ nhật phẳng $$[0,1]^2$$ và **dán đồng nhất** các cặp điểm đối diện nhau — biến màn hình phẳng thành một **hình xuyến $$T^2$$**! **Tô-pô thương (Quotient Topology)** chính là nghệ thuật "cắt và dán" chặt chẽ nhất của toán học, dùng để chế tạo hầu như mọi không gian thú vị từ đường tròn, mặt cầu, dải Möbius đến mặt phẳng xạ ảnh!

Trong các chương trước, chúng ta đã tìm hiểu những cách cơ bản để xây dựng không gian tô-pô mới: không gian con, không gian tích và tô-pô sinh bởi metric. Bài học này giới thiệu một phương pháp tổng quát khác: **tô-pô thương** (quotient topology) — kỹ thuật "dán" hay "đồng nhất" các điểm của một không gian cho trước.

Không gian thương cho phép tạo ra nhiều đối tượng hình học quan trọng từ các không gian đơn giản: dán các cạnh của hình vuông để thu được hình xuyến (torus), chai Klein (Klein bottle) hay dải Möbius; co một tập con về một điểm duy nhất; đồng nhất các điểm đối cực trên mặt cầu để xây dựng không gian xạ ảnh thực $\mathbb{R}P^n$; hay mô hình hóa phép lấy thương đại số như $\mathbb{Z}/n\mathbb{Z}$.

![Quotient space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Quotient_group_diagram.svg/400px-Quotient_group_diagram.svg.png)  
*Minh họa khái niệm phép lấy thương – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Quotient_group_diagram.svg)*

Ý tưởng cốt lõi rất trực quan: xuất phát từ một không gian tô-pô $X$ và một quan hệ tương đương $\sim$ chỉ rõ những điểm nào cần đồng nhất với nhau, ta lập tập hợp các lớp tương đương $X/{\sim}$ và trang bị cho nó tô-pô mịn nhất sao cho ánh xạ chiếu $\pi: X \to X/{\sim}$ liên tục.

Trong bài học này, chúng ta sẽ ôn lại quan hệ tương đương, định nghĩa tô-pô thương và tính chất phổ dụng (universal property) của nó, khảo sát ánh xạ thương (quotient map), phân tích các ví dụ tiêu chuẩn ($S^1$, $T^2$, hình trụ, dải Möbius, $\mathbb{R}P^n$, hình nón và phép treo), cũng như các điều kiện để không gian thương có tính chất Hausdorff.

Tô-pô thương xuất hiện xuyên suốt nhiều nhánh toán học và vật lý: định lý phân loại các mặt compact, xây dựng phức CW trong tô-pô đại số, lý thuyết đa tạp trong hình học vi phân và các không gian pha hay không gian cấu hình trong vật lý lý thuyết.

---

## 🗺️ Kiến thức cần nhớ: Tô-pô Thương là gì và nghiên cứu những gì?

### 1. Phép dán Toán học: Quan hệ tương đương $$X / {\sim}$$
- **Bản chất:** Bắt đầu từ một không gian quen thuộc $$X$$ (như đoạn thẳng $$[0,1]$$ hay hình vuông $$[0,1]^2$$), ta tuyên bố các điểm nào sẽ bị "dán dính thành một" qua một quan hệ tương đương $$\sim$$. Tập các lớp tương đương $$X/{\sim}$$ đi kèm ánh xạ chiếu tự nhiên $$q: X \to X/{\sim}$$.

### 2. Định nghĩa Tô-pô Thương & Tập Bão hòa (Saturated Sets)
- **Bản chất:** Ta muốn ánh xạ dán $$q$$ liên tục và giữ lại nhiều tập mở nhất có thể (tô-pô mịn nhất làm $$q$$ liên tục):
  $$
  U \subseteq X/{\sim} \text{ mở} \quad\Longleftrightarrow\quad q^{-1}(U) \text{ mở trong } X.
  $$
  Tập con $$A \subseteq X$$ có dạng $$q^{-1}(U)$$ (chứa trọn mọi lớp tương đương mà nó chạm vào) gọi là **tập bão hòa**.

### 3. Tính chất Phổ dụng (Universal Property) — Vũ khí tối thượng
- **Bản chất:** Muốn xây dựng một ánh xạ liên tục từ không gian thương phức tạp $$X/{\sim}$$ sang $$Y$$, bạn **không cần** làm việc trực tiếp trên các lớp tương đương rối rắm — chỉ cần xây dựng một ánh xạ liên tục $$f: X \to Y$$ nhận **cùng giá trị trên các điểm bị dán với nhau**, nó sẽ tự động "hạ xuống" thành ánh xạ liên tục duy nhất $$\bar{f}: X/{\sim} \to Y$$!

---

## 🧮 Ví dụ tính tay làm từng bước: Dán đoạn thẳng $$[0, 1]$$ thành Đường tròn $$S^1$$

Xét $$X = [0, 1]$$ với quan hệ dán hai đầu mút $$0 \sim 1$$ (mọi điểm $$x \in (0,1)$$ chỉ tương đương với chính nó), và ánh xạ chiếu $$q: [0, 1] \to X/{\sim}$$.

1. **Kiểm tra tập mở quanh điểm dán $$p = q(0) = q(1)$$:**
   - Xét tập $$V_1 = [0, 0.2)$$ trong $$[0, 1]$$: $$V_1$$ mở trong $$[0, 1]$$, nhưng $$q^{-1}(q(V_1)) = [0, 0.2) \cup \{1\}$$ **KHÔNG mở** trong $$[0, 1]$$ (vì quanh điểm $$1$$ thiếu hẳn một khoảng $$(1-\varepsilon, 1]$$!). Do đó $$q(V_1)$$ **không mở** trong $$X/{\sim}$$!
   - Xét tập $$V_2 = [0, 0.2) \cup (0.8, 1]$$: nó chứa cả $$0$$ lẫn $$1$$ nên **bão hòa** ($$q^{-1}(q(V_2)) = V_2$$) và **mở** trong $$[0, 1]$$! Vì vậy $$q(V_2)$$ là một cung mở đích thực bao quanh điểm dán $$p$$ trên đường tròn!

2. **Chứng minh chặt chẽ $$[0, 1]/\{0 \sim 1\} \cong S^1$$ trong 3 dòng bằng Tính chất Phổ dụng:**
   - Xét ánh xạ liên tục toàn ánh $$f: [0, 1] \to S^1,\; f(t) = (\cos 2\pi t,\; \sin 2\pi t)$$.
   - Kiểm tra điều kiện tương thích phép dán: $$f(0) = (1, 0) = f(1)$$, và trên $$(0, 1)$$ hàm $$f$$ là đơn ánh!
   - Theo Tính chất Phổ dụng, $$f$$ hạ xuống thành song ánh liên tục $$\bar{f}: [0,1]/\{0\sim 1\} \to S^1$$. Vì $$[0,1]$$ compact nên thương của nó compact, còn $$S^1$$ là Hausdorff $$\implies \bar{f}$$ tự động là một **phép đồng phôi**!

### Giải thích: Quy trình 4 bước làm chủ Tô-pô Thương

#### Bước 1: Hình dung phép dán trước khi viết công thức
Muốn chế tạo $$S^1$$: dán 2 đầu đoạn $$[0,1]$$. Muốn chế tạo $$S^2$$: bóp toàn bộ viền tròn $$\partial D^2$$ của đĩa $$D^2$$ về đúng 1 điểm (cực Bắc)! Muốn chế tạo $$\mathbb{R}P^2$$: dán từng cặp điểm đối tâm $$x \sim -x$$ trên mặt cầu $$S^2$$!

#### Bước 2: Cẩn thận cái bẫy "Tập mở nhưng không bão hòa"
Ánh xạ thương $$q$$ luôn liên tục và toàn ánh, nhưng **không nhất thiết là ánh xạ mở**! Muốn kiểm tra $$U$$ mở trong $$X/{\sim}$$, luôn luôn kéo ngược $$q^{-1}(U)$$ về $$X$$ và kiểm tra xem $$q^{-1}(U)$$ có mở trong $$X$$ hay không.

#### Bước 3: Dùng Tính chất Phổ dụng + Compact-sang-Hausdorff để chứng minh Đồng phôi
Thay vì tự tay đi chứng minh $$\bar{f}^{-1}$$ liên tục (rất vất vả!), ta chỉ cần dùng định lý vàng: *song ánh liên tục từ không gian compact vào không gian Hausdorff luôn là đồng phôi!*

#### Bước 4: Cảnh giác tính Hausdorff có thể bị mất khi lấy thương
Dù $$X$$ rất đẹp (như $$\mathbb{R}$$), nếu bạn dán một cách bất cẩn (như dán hai đường thẳng trừ gốc tọa độ, hoặc dán $$x \sim y \iff x - y \in \mathbb{Q}$$ trên $$\mathbb{R}$$), không gian thương có thể đánh mất tính Hausdorff hoàn toàn!

$$
\text{Không gian }X \text{ + Phép dán }\sim
\;\xrightarrow{\;q^{-1}(U)\text{ mở}\;}\;
\text{Không gian thương }X/{\sim}
\;\xrightarrow{\;\text{Phổ dụng + Compact}\to\text{Hausdorff}\;}\;
S^1,\; S^n,\; T^2,\; \mathbb{R}P^n.
$$

---

## 🔗 Quan hệ tương đương (Equivalence Relations)

### 1. Các khái niệm cơ bản

<div class="textbook-definition" markdown="1">
**Định nghĩa (Quan hệ tương đương):**  
Quan hệ $\sim$ trên tập hợp $X$ được gọi là một **quan hệ tương đương** nếu thỏa mãn ba tính chất sau với mọi $x, y, z \in X$:
</div>

- **(ER1) Phản xạ (Reflexive):** $x \sim x$.
- **(ER2) Đối xứng (Symmetric):** $x \sim y \Rightarrow y \sim x$.
- **(ER3) Bắc cầu (Transitive):** $x \sim y$ và $y \sim z \Rightarrow x \sim z$.

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Lớp tương đương):**  
**Lớp tương đương** của $x \in X$ là tập hợp:

$$
[x] = \{y \in X : y \sim x\}
$$
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập thương):**

$$
X/{\sim} = \{[x] : x \in X\} = \text{set of equivalence classes}
$$
</div>

**Ánh xạ chiếu chính tắc (Projection map):**

$$
\pi: X \to X/{\sim}, \quad \pi(x) = [x]
$$

---

<div class="textbook-theorem" markdown="1">
**Định lý (Phân hoạch):**  
Một quan hệ tương đương $\sim$ sinh ra một **phân hoạch** của $X$:
- $X = \bigcup_{x \in X} [x]$ (phủ toàn bộ $X$),
- Với mọi $x, y \in X$, hoặc $[x] = [y]$ hoặc $[x] \cap [y] = \emptyset$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Kiểm tra trực tiếp từ ba tính chất phản xạ, đối xứng và bắc cầu.
</div>

Ngược lại, mọi phân hoạch của $X$ đều xác định duy nhất một quan hệ tương đương trên $X$.

---

### 2. Các ví dụ

**Ví dụ 1: Đồng dư modulo $n$**  
Trên $X = \mathbb{Z}$, định nghĩa $x \sim y \iff x \equiv y \pmod n$. Các lớp tương đương là $[0], [1], \ldots, [n-1]$, và tập thương là $\mathbb{Z}/n\mathbb{Z}$.

---

**Ví dụ 2: Dán hai đầu mút đoạn thẳng**  
Trên $X = [0,1]$, xét quan hệ tương đương sinh bởi $0 \sim 1$. Các lớp tương đương gồm $[0] = [1] = \{0, 1\}$ và $[x] = \{x\}$ với mọi $x \in (0,1)$. Không gian thương $[0,1]/{\sim}$ đồng phôi với đường tròn $S^1$.

---

**Ví dụ 3: Co một không gian con về một điểm**  
Cho không gian $X$ và tập con khác rỗng $A \subseteq X$. Định nghĩa $x \sim y$ nếu $x = y$ hoặc $x, y \in A$. Các lớp tương đương gồm một lớp $[A] = A$ và các lớp đơn điểm $[x] = \{x\}$ với mọi $x \notin A$. Không gian thương được ký hiệu là $X/A$.

---

**Ví dụ 4: Đồng nhất các điểm đối cực trên mặt cầu**  
Trên $X = S^n$, định nghĩa $x \sim -x$ (đồng nhất mỗi điểm với điểm đối cực của nó). Không gian thương $S^n/{\sim} = \mathbb{R}P^n$ là **không gian xạ ảnh thực** chiều $n$, có thể hiểu hình học là tập hợp các đường thẳng đi qua gốc tọa độ trong $\mathbb{R}^{n+1}$.

---

## 🏗️ Tô-pô thương (Quotient Topology)

### 1. Định nghĩa

Cho $X$ là không gian tô-pô, $\sim$ là một quan hệ tương đương trên $X$ và $\pi: X \to X/{\sim}$ là ánh xạ chiếu. Ta muốn trang bị trên $X/{\sim}$ một tô-pô sao cho $\pi$ liên tục và giữ lại nhiều tập mở nhất có thể.

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tô-pô thương):**  
**Tô-pô thương** trên $X/{\sim}$ là họ tập hợp:

$$
\tau_{X/\sim} = \{U \subseteq X/{\sim} : \pi^{-1}(U) \text{ open in } X\}
$$
</div>

Nói cách khác, $U \subseteq X/{\sim}$ mở trong $X/{\sim}$ khi và chỉ khi nghịch ảnh $\pi^{-1}(U)$ mở trong $X$. Cặp $(X/{\sim}, \tau_{X/\sim})$ gọi là **không gian thương** (quotient space).

---

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Họ $\tau_{X/\sim}$ là một tô-pô trên $X/{\sim}$.
</div>

**Chứng minh:**
- $\pi^{-1}(\emptyset) = \emptyset$ và $\pi^{-1}(X/{\sim}) = X$ đều mở trong $X$, nên $\emptyset, X/{\sim} \in \tau_{X/\sim}$.
- Với mọi họ $\{U_i\} \subseteq \tau_{X/\sim}$, $\pi^{-1}\left(\bigcup_i U_i\right) = \bigcup_i \pi^{-1}(U_i)$ mở trong $X$.
- Với mọi họ hữu hạn $U_1, \ldots, U_k \in \tau_{X/\sim}$, $\pi^{-1}\left(\bigcap_{i=1}^k U_i\right) = \bigcap_{i=1}^k \pi^{-1}(U_i)$ mở trong $X$.

Vậy $\tau_{X/\sim}$ là một tô-pô.

---

<div class="textbook-theorem" markdown="1">
**Mệnh đề:** Ánh xạ chiếu $\pi: X \to X/{\sim}$ là ánh xạ liên tục.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Suy trực tiếp từ định nghĩa: nếu $U$ mở trong $X/{\sim}$ thì $\pi^{-1}(U)$ mở trong $X$.
</div>

---

### 2. Tính chất phổ dụng (Universal Property)

<div class="textbook-theorem" markdown="1">
**Định lý (Tính chất phổ dụng của tô-pô thương):**  
Ánh xạ $f: X/{\sim} \to Y$ liên tục khi và chỉ khi ánh xạ hợp $f \circ \pi: X \to Y$ liên tục.
</div>

**Biểu đồ giao hoán:**
```
X ---π---> X/~
 \         /
  f∘π     f
   \     /
    \   /
     ⌄ ⌄
      Y
```

<div class="textbook-proof" markdown="1">
**Chứng minh ($\Rightarrow$):**  
Nếu $f$ liên tục và $\pi$ liên tục thì hợp $f \circ \pi$ liên tục.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh ($\Leftarrow$):**  
Giả sử $f \circ \pi$ liên tục. Với mọi tập mở $V \subseteq Y$, ta có $(f \circ \pi)^{-1}(V) = \pi^{-1}(f^{-1}(V))$ mở trong $X$. Theo định nghĩa tô-pô thương, $f^{-1}(V)$ mở trong $X/{\sim}$. Do đó $f$ liên tục.
</div>

**Hệ quả:** Tô-pô thương là tô-pô **mịn nhất** (chứa nhiều tập mở nhất) trên $X/{\sim}$ làm cho $\pi$ liên tục.

---

### 3. Ánh xạ thương (Quotient Maps)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Ánh xạ thương):**  
Một toàn ánh liên tục $f: X \to Y$ được gọi là **ánh xạ thương** (quotient map) nếu với mọi $U \subseteq Y$:

$$
U \text{ open in } Y \iff f^{-1}(U) \text{ open in } X
$$
</div>

Điều này có nghĩa là tô-pô trên $Y$ chính là tô-pô thương cảm sinh bởi $f$.

---

<div class="textbook-theorem" markdown="1">
**Mệnh đề:**  
Ánh xạ chiếu $\pi: X \to X/{\sim}$ luôn là ánh xạ thương theo định nghĩa.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý:** Nếu $f: X \to Y$ là toàn ánh liên tục và là **ánh xạ mở** (hoặc **ánh xạ đóng**), thì $f$ là ánh xạ thương.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh (trường hợp ánh xạ mở):**  
Chiều $(\Rightarrow)$ suy từ tính liên tục của $f$. Với chiều $(\Leftarrow)$, giả sử $V \subseteq Y$ thỏa mãn $f^{-1}(V)$ mở trong $X$. Vì $f$ là toàn ánh nên $V = f(f^{-1}(V))$; do $f$ là ánh xạ mở nên $V$ mở trong $Y$. Trường hợp ánh xạ đóng chứng minh tương tự bằng cách lấy phần bù.
</div>

---

### 4. Kiểm tra tập mở và tập đóng trên không gian thương

Để kiểm tra một tập $U \subseteq X/{\sim}$ có mở hay không, ta kiểm tra xem $\pi^{-1}(U)$ có mở trong $X$ hay không. Trong nhiều tình huống, việc kiểm tra tập đóng thuận tiện hơn:

<div class="textbook-theorem" markdown="1">
**Định lý (Tập đóng trong không gian thương):**  
$F \subseteq X/{\sim}$ đóng trong $X/{\sim}$ khi và chỉ khi $\pi^{-1}(F)$ đóng trong $X$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Lấy phần bù vì $\pi^{-1}((X/{\sim}) \setminus F) = X \setminus \pi^{-1}(F)$.
</div>

---

## 🌀 Các ví dụ về không gian thương

### 1. Đường tròn $S^1$ từ đoạn $[0,1]$

Xét $X = [0,1]$ với quan hệ $0 \sim 1$ và ánh xạ $\pi: [0,1] \to S^1 \subseteq \mathbb{C}$ cho bởi $\pi(t) = e^{2\pi it}$.

Ta kiểm tra:
- $\pi$ liên tục, toàn ánh, và $\pi(0) = \pi(1) = 1$.
- $\pi$ **không phải** ánh xạ mở: tập $[0, \varepsilon)$ mở trong tô-pô không gian con của $[0,1]$, nhưng ảnh $\pi([0, \varepsilon))$ là cung nửa mở bắt đầu tại $1 \in S^1$, không mở trong $S^1$.
- Tuy nhiên, vì $[0,1]$ compact và $S^1$ Hausdorff, $\pi$ là ánh xạ đóng, do đó $\pi$ là ánh xạ thương.

Kết luận: $[0,1]/{\sim} \cong S^1$.

---

### 2. Hình xuyến $T^2$ từ hình vuông

Xét hình vuông $X = [0,1] \times [0,1]$ với hai phép dán cạnh đối diện:
- $(0, t) \sim (1, t)$ (dán cạnh trái với cạnh phải),
- $(s, 0) \sim (s, 1)$ (dán cạnh dưới với cạnh trên).

Kết quả thu được là hình xuyến $T^2$.

![Torus from square](https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Torus_from_rectangle.gif/400px-Torus_from_rectangle.gif)  
*Dán các cạnh hình vuông để tạo hình xuyến – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus_from_rectangle.gif)*

Hình xuyến có thể nhúng vào $\mathbb{R}^3$ dưới dạng mặt tròn xoay với tham số hóa ($R > r > 0$):
$\pi(s,t) = \bigl((R + r \cos(2\pi t))\cos(2\pi s),\; (R + r \cos(2\pi t))\sin(2\pi s),\; r \sin(2\pi t)\bigr)$.

---

### 3. Hình trụ (Cylinder)

Trên $X = [0,1] \times [0,1]$, nếu chỉ đồng nhất $(0, t) \sim (1, t)$ (dán cạnh trái với cạnh phải mà không dán trên–dưới), ta thu được hình trụ $S^1 \times [0,1]$.

---

### 4. Dải Möbius (Möbius Strip)

Trên $X = [0,1] \times [0,1]$, đồng nhất $(0, t) \sim (1, 1-t)$ (dán cạnh trái với cạnh phải sau khi xoắn ngược chiều). Kết quả là một mặt không định hướng được (chỉ có một phía duy nhất).

![Möbius strip](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/M%C3%B6bius_strip.jpg/400px-M%C3%B6bius_strip.jpg)  
*Dải Möbius – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:M%C3%B6bius_strip.jpg)*

---

### 5. Không gian xạ ảnh thực $\mathbb{R}P^n$

Trên $X = S^n \subseteq \mathbb{R}^{n+1}$, đồng nhất các cặp điểm đối cực $x \sim -x$. Ta thu được $\mathbb{R}P^n = S^n/{\sim}$, biểu diễn tập hợp các đường thẳng qua gốc tọa độ trong $\mathbb{R}^{n+1}$.
- $\mathbb{R}P^1 \cong S^1$.
- $\mathbb{R}P^2$ là mặt phẳng xạ ảnh thực (không định hướng được và không nhúng được vào $\mathbb{R}^3$).

Không gian xạ ảnh được dùng trong hình học xạ ảnh, thị giác máy tính (tọa độ thuần nhất) và cơ học lượng tử (không gian trạng thái lượng tử).

---

### 6. Co một không gian con về một điểm

Cho tập con khác rỗng $A \subseteq X$, không gian $X/A$ thu được bằng cách co toàn bộ $A$ thành một điểm.

**Ví dụ:** Đĩa đóng $D^2$ co biên $S^1$ thành một điểm cho ta mặt cầu: $D^2/S^1 \cong S^2$.

<div class="textbook-proof" markdown="1">
**Chứng minh:** Dùng phép chiếu lập thể (hoặc ánh xạ liên tục từ $D^2$ lên $S^2$ đưa biên $S^1$ về cực bắc; vì $D^2$ compact và $S^2$ Hausdorff nên đó là ánh xạ thương).
</div>

---

### 7. Hình nón (Cone) và Phép treo (Suspension)

- **Hình nón trên $X$:** $CX = (X \times [0,1]) / (X \times \{0\})$, thu được bằng cách co đáy $X \times \{0\}$ của hình trụ $X \times [0,1]$ thành một điểm đỉnh.
- **Phép treo của $X$:** $\Sigma X = (X \times [0,1]) / {\sim}$, trong đó $X \times \{0\}$ được co thành một điểm cực nam và $X \times \{1\}$ được co thành một điểm cực bắc riêng biệt.
- **Ví dụ:** $\Sigma S^n \cong S^{n+1}$.

---

## 🔍 Tính chất của ánh xạ thương và không gian thương

### 1. Khi nào một toàn ánh liên tục là ánh xạ thương?

Không phải mọi toàn ánh liên tục hay ánh xạ chiếu $\pi: X \to X/{\sim}$ đều là ánh xạ mở hoặc đóng. Chẳng hạn, với $X = \mathbb{R}^2$ và $A$ là trục hoành, ánh xạ chiếu $\pi: \mathbb{R}^2 \to \mathbb{R}^2/A$ không phải là ánh xạ mở (một tập mở trong $\mathbb{R}^2$ cắt trục hoành có ảnh không nhất thiết chứa toàn bộ lân cận của điểm $[A]$).

<div class="textbook-theorem" markdown="1">
**Định lý (Điều kiện đủ):**  
Nếu $X$ compact, $Y$ Hausdorff và $f: X \to Y$ là toàn ánh liên tục, thì $f$ là ánh xạ đóng và do đó là ánh xạ thương.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Mọi ánh xạ liên tục từ không gian compact vào không gian Hausdorff đều là ánh xạ đóng.
</div>

---

### 2. Tính Hausdorff của không gian thương

Ngay cả khi $X$ là không gian Hausdorff, không gian thương $X/{\sim}$ **không nhất thiết** Hausdorff.

**Ví dụ:** Xét $X = \mathbb{R}$ và co khoảng mở $A = (0,1)$ thành một điểm (tức không gian thương $\mathbb{R}/(0,1)$). Trong $\mathbb{R}/(0,1)$, không thể tách điểm $[A]$ khỏi điểm $[0]$ (hoặc $[1]$) bằng hai tập mở rời nhau, nên $\mathbb{R}/(0,1)$ không Hausdorff.

---

<div class="textbook-theorem" markdown="1">
**Định lý (Điều kiện đủ để không gian thương là Hausdorff):**  
Đặt $R = \{(x,y) \in X \times X : x \sim y\}$. Nếu $R$ đóng trong $X \times X$ và ánh xạ thương $\pi: X \to X/{\sim}$ là ánh xạ mở (hoặc $X$ là không gian compact Hausdorff), thì $X/{\sim}$ là không gian Hausdorff.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Nếu $[x] \neq [y]$ thì $(x,y) \notin R$. Vì $R$ đóng trong $X \times X$, tồn tại các lân cận mở $U$ của $x$ và $V$ của $y$ sao cho $(U \times V) \cap R = \emptyset$. Khi $\pi$ là ánh xạ mở, $\pi(U)$ và $\pi(V)$ là hai lân cận mở rời nhau tách $[x]$ và $[y]$ (xem thêm Munkres, §22).
</div>

**Ví dụ:** Quan hệ đối cực trên mặt cầu compact $S^n$ là tập đóng trong $S^n \times S^n$ (và $\pi$ là ánh xạ mở), nên $\mathbb{R}P^n$ là không gian Hausdorff.

---

### 3. Định lý đẳng cấu thứ nhất (tô-pô)

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Cho $f: X \to Y$ là một **ánh xạ thương**. Định nghĩa quan hệ tương đương $x \sim y \iff f(x) = f(y)$. Khi đó $X/{\sim} \cong Y$ (đồng phôi).
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Ánh xạ cảm sinh $\overline{f}: X/{\sim} \to Y$ xác định bởi $\overline{f}([x]) = f(x)$ là một song ánh liên tục theo tính chất phổ dụng. Vì $f$ là ánh xạ thương, với mọi $U \subseteq X/{\sim}$ mở thì $\pi^{-1}(U) = f^{-1}(\overline{f}(U))$ mở trong $X$, suy ra $\overline{f}(U)$ mở trong $Y$. Vậy $\overline{f}^{-1}$ cũng liên tục, nên $\overline{f}$ là một phép đồng phôi.
</div>

Định lý này là công cụ tiêu chuẩn để nhận diện một không gian thương $X/{\sim}$ với một không gian cụ thể $Y$.

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Henri Poincaré** – *Analysis Situs* (1895)  
   *Công trình đặt nền móng cho tô-pô học và lý thuyết mặt.*

2. **Felix Hausdorff** – *Grundzüge der Mengenlehre* (1914)  
   *Trình bày có hệ thống về tô-pô đại cương.*

### Giáo trình

3. **James R. Munkres** – *Topology*, 2nd Ed., **§22: Quotient Topology**

4. **John M. Lee** – *Introduction to Topological Manifolds*, **Chapter 3**  
   *Không gian thương và các mặt.*

5. **Allen Hatcher** – *Algebraic Topology*, **§0.2: Surfaces**  
   *Góc nhìn hình học.*

6. **Sidney A. Morris** – *Topology without Tears*, **Chapter 7**

---

## 🔗 Ứng dụng và liên kết

### Hình học – Các mặt
Phân loại các mặt compact (mặt cầu, hình xuyến, mặt phẳng xạ ảnh, chai Klein) được mô tả trực tiếp qua phép dán cạnh (không gian thương của đa giác).

### Hình học vi phân – Đa tạp
Nhiều đa tạp quan trọng (như không gian xạ ảnh, hình xuyến, không gian thấu kính) được xây dựng dưới dạng không gian thương.

### Tô-pô đại số
Phức CW được xây dựng quy nạp bằng cách dán các đĩa đóng dọc theo biên — một chuỗi phép lấy thương liên tiếp.

### Vật lý – Lý thuyết chuẩn (Gauge Theory)
Các phân thớ chính và không gian cấu hình vật lý xuất hiện dưới dạng thương theo tác động của nhóm đối xứng chuẩn.

### Đồ họa máy tính
Ánh xạ kết cấu (texture mapping) trên hình xuyến khai thác trực tiếp biểu diễn thương của hình vuông.

---

## Video tham khảo

- **xem trước** [[Tôpô đại cương] Bài 38. Ánh xạ thương, tôpô thương và Ví dụ](https://www.youtube.com/watch?v=n8XSQwXw8Gc) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Trình bày ánh xạ thương, tô-pô thương và các ví dụ minh họa bằng tiếng Việt.
- [Quotient Topology for Equivalence Relations (Identification Spaces)](https://www.youtube.com/watch?v=s3LL3KQp7pQ) — Andrew McCrady, tiếng Anh. Giải thích phép dán qua quan hệ tương đương với nhịp độ chậm.
- [Topology Lecture 14: Quotient Spaces I](https://www.youtube.com/watch?v=P7mTDR8FRMc) — Marius Furter, tiếng Anh. Bài giảng đầy đủ về không gian thương kèm nhiều ví dụ đối chiếu.

## 🧩 Bài tập

### Quan hệ tương đương

1. **Kiểm tra quan hệ tương đương:**  
   Trên $\mathbb{R}$, định nghĩa $x \sim y \iff x - y \in \mathbb{Z}$. Kiểm tra ba tính chất của quan hệ tương đương.

2. **Lớp tương đương:**  
   Trong bài 1, mô tả các lớp tương đương $[0]$, $[\pi]$ và $[1/2]$.

3. **Phân hoạch:**  
   Chứng minh chi tiết rằng mọi quan hệ tương đương đều sinh ra một phân hoạch.

### Tô-pô thương

4. **Kiểm tra tô-pô:**  
   Chứng minh họ $\tau_{X/\sim}$ thỏa mãn các tiên đề tô-pô.

5. **Tính liên tục của $\pi$:**  
   Chứng minh $\pi: X \to X/{\sim}$ liên tục trực tiếp từ định nghĩa.

6. **Tính chất phổ dụng:**  
   Chứng minh cả hai chiều: $f: X/{\sim} \to Y$ liên tục $\iff f \circ \pi$ liên tục.

### Ánh xạ thương

7. **Ánh xạ mở:**  
   Chứng minh mọi toàn ánh liên tục mở $f: X \to Y$ đều là ánh xạ thương.

8. **Ánh xạ đóng:**  
   Phác thảo chứng minh: mọi ánh xạ liên tục từ không gian compact vào không gian Hausdorff đều là ánh xạ đóng.

9. **Phản ví dụ:**  
   Tìm một toàn ánh liên tục nhưng không phải là ánh xạ thương.

### Các ví dụ hình học

10. **Đường tròn:**  
    Với $[0,1]$ và $0 \sim 1$, chứng minh $[0,1]/{\sim} \cong S^1$.

11. **Hình xuyến:**  
    Vẽ sơ đồ dán hình vuông tạo thành hình xuyến $T^2$ và ghi rõ các cạnh được đồng nhất.

12. **Dải Möbius:**  
    Xây dựng dải Möbius từ hình chữ nhật và chỉ rõ chiều dán ngược.

### Không gian xạ ảnh $\mathbb{R}P^n$

13. **$\mathbb{R}P^1$:**  
    Chứng minh $\mathbb{R}P^1 = S^1/{\sim} \cong S^1$.

14. **$\mathbb{R}P^2$:**  
    Tìm hiểu phác thảo chứng minh mặt phẳng xạ ảnh $\mathbb{R}P^2$ không định hướng được.

15. **Tọa độ thuần nhất:**  
    Giải thích đồng phôi $\mathbb{R}P^n \cong (\mathbb{R}^{n+1} \setminus \{0\}) / {\sim}$ với tọa độ thuần nhất $[x_0 : \cdots : x_n]$.

### Tính Hausdorff

16. **Không gian thương không Hausdorff:**  
    Chứng minh không gian thương $\mathbb{R}/(0,1)$ (co khoảng mở $(0,1)$ thành một điểm) không phải là không gian Hausdorff.

17. **Điều kiện đủ:**  
    Tìm hiểu chứng minh: nếu $R$ đóng trong $X \times X$ và $\pi$ là ánh xạ mở thì $X/{\sim}$ là không gian Hausdorff.

18. **Quan hệ đối cực:**  
    Kiểm tra quan hệ đối cực trên $S^n$ là tập đóng trong $S^n \times S^n$, từ đó suy ra $\mathbb{R}P^n$ là không gian Hausdorff.

### Nâng cao

19. **Hình nón:**  
    Với $CX = (X \times [0,1]) / (X \times \{0\})$, hãy xác định không gian $CS^n$ đồng phôi với không gian quen thuộc nào.

20. **Phép treo:**  
    Phác thảo lập luận hình học cho thấy $\Sigma S^n \cong S^{n+1}$.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §22 (Quotient Topology)
- **Lee, Topological Manifolds:** Chapter 3 (Quotient spaces)
- **Hatcher, Algebraic Topology:** §0.2 (Surfaces)
- **Armstrong:** *Basic Topology* (Trực giác hình học)

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu tô-pô thương — kỹ thuật xây dựng không gian mới bằng cách đồng nhất các điểm theo một quan hệ tương đương $\sim$. Tô-pô thương trên $X/{\sim}$ được xác định bởi điều kiện $U$ mở trong $X/{\sim} \iff \pi^{-1}(U)$ mở trong $X$, là tô-pô mịn nhất làm cho ánh xạ chiếu $\pi$ liên tục và được đặc trưng bởi tính chất phổ dụng ($f$ liên tục $\iff f \circ \pi$ liên tục).

Nhiều đối tượng hình học quan trọng được xây dựng dưới dạng không gian thương: đường tròn $S^1$, hình xuyến $T^2$, dải Möbius, không gian xạ ảnh $\mathbb{R}P^n$, hình nón $CX$ và phép treo $\Sigma X$. Mọi toàn ánh liên tục từ không gian compact vào không gian Hausdorff đều là ánh xạ thương đóng, nhưng cần chú ý rằng không gian thương của một không gian Hausdorff không tự động là Hausdorff.

**Tiếp theo:** Lecture 05.01 về **Phân loại các mặt compact** — ứng dụng trực tiếp phép dán thương để phân loại các mặt đóng liên thông.

---

*"Quotient topology: the art of gluing things together."*

---

**Previous Chapter:** [Chapter 04: Metric Spaces](/contents/vi/topology-chapter04/)  
**Next:** [Lecture 05.01: Classification of Surfaces](/contents/vi/topology-chapter05/05_01_Classification_Surfaces/)
