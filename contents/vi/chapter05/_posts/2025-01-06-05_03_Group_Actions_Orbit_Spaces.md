---
layout: post
title: "Lecture 05.03: Group Actions and Orbit Spaces"
lang: vi
lang-ref: lecture-05-03
chapter: 5
lecture: 3
categories: [chapter05]
tags: [group-actions, orbit-spaces, quotient-by-group, covering-spaces, symmetry]
description: "Group actions trên topological spaces, orbit spaces, và applications: covering spaces, symmetry"
---

**Tác động nhóm và Không gian quỹ đạo**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Hầu hết những không gian đẹp nhất của toán học và vật lý đều được sinh ra từ một công thức duy nhất: **lấy một không gian đơn giản, cho một nhóm đối xứng $$G$$ tác động lên nó, rồi gộp mọi điểm cùng quỹ đạo thành một điểm!** Lấy đường thẳng $$\mathbb{R}$$ chia cho nhóm tịnh tiến $$\mathbb{Z}$$ ra đường tròn $$S^1$$; lấy mặt cầu $$S^2$$ chia cho phép đối tâm $$\mathbb{Z}/2\mathbb{Z}$$ ra mặt phẳng xạ ảnh $$\mathbb{R}P^2$$; lấy nửa mặt phẳng hyperbolic $$\mathbb{H}$$ chia cho nhóm ma trận $$\mathrm{SL}_2(\mathbb{Z})$$ ra không gian moduli các đường cong elliptic! Bài học này đặt nền móng cho **tác động nhóm** và **không gian quỹ đạo $$X/G$$**.

Đối xứng là một cấu trúc phổ biến trong toán học và vật lý, và **tác động nhóm** (group action) là ngôn ngữ chính thức để mô tả đối xứng của các không gian tô-pô.

Một tác động của nhóm $G$ lên không gian $X$ gán cho mỗi phần tử $g \in G$ một phép biến đổi (đồng phôi) của $X$, tương thích với phép toán nhóm. **Không gian quỹ đạo** (orbit space) $X/G$ là không gian thương thu được bằng cách đồng nhất các điểm nằm trên cùng một quỹ đạo của tác động.

![Group action visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Hexagonal_tiling_3-color.svg/400px-Hexagonal_tiling_3-color.svg.png)  
*Minh họa tác động của nhóm đối xứng trên lát gạch lục giác – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hexagonal_tiling_3-color.svg)*

Nhiều không gian quen thuộc xuất hiện tự nhiên dưới dạng không gian quỹ đạo $X/G$:
- $\mathbb{Z}$ tác động lên $\mathbb{R}$ bằng phép tịnh tiến cho $\mathbb{R}/\mathbb{Z} \cong S^1$,
- $\mathbb{Z}/2\mathbb{Z}$ tác động lên $S^n$ bằng phép đối cực cho $S^n/(\mathbb{Z}/2\mathbb{Z}) \cong \mathbb{R}P^n$,
- $S^1$ tác động lên $\mathbb{C}$ bằng phép quay quanh gốc tọa độ cho $\mathbb{C}/S^1 \cong [0, \infty)$ (mỗi quỹ đạo là một đường tròn bán kính $r \ge 0$),
- Nhóm các phép biến đổi phủ (deck transformations) tác động trên không gian phủ phổ dụng $\tilde{X}$ cho thương $\tilde{X}/\pi_1(X) \cong X$.

Trong bài học này, chúng ta sẽ tìm hiểu định nghĩa tác động nhóm, quỹ đạo (orbit), nhóm ổn định hóa (stabilizer), định lý Quỹ đạo – Ổn định hóa, tác động tự do (free action), tác động gián đoạn thực sự (properly discontinuous action), miền cơ bản (fundamental domain) cùng các ứng dụng trong không gian phủ và nhóm Lie.

---

## 🗺️ Bản đồ kiến thức nền: Tác động Nhóm & Không gian Quỹ đạo là gì?

### 1. Tác động Liên tục của Nhóm $$G$$ lên Không gian $$X$$
- **Bản chất:** Một tác động trái $$G \times X \to X,\; (g, x) \mapsto g\cdot x$$ gán cho mỗi phần tử $$g \in G$$ một phép đồng phôi của $$X$$ tuân theo luật kết hợp $$(gh)\cdot x = g\cdot(h\cdot x)$$ và $$e\cdot x = x$$.

### 2. Quỹ đạo (Orbit) & Nhóm Ổn định hóa (Stabilizer)
- **Quỹ đạo $$G\cdot x = \{g\cdot x : g \in G\}$$:** Tập tất cả các vị trí mà điểm $$x$$ có thể bị đẩy tới dưới tác động của nhóm $$G$$.
- **Nhóm ổn định hóa $$G_x = \{g \in G : g\cdot x = x\}$$:** Tập các phép đối xứng giữ nguyên điểm $$x$$. (Liên hệ đại số kinh điển: $$G/G_x \leftrightarrow G\cdot x$$!)
- **Tác động tự do (Free action):** Mọi điểm đều có $$G_x = \{e\}$$ (không có điểm bất động nào ngoài phần tử đơn vị).

### 3. Không gian Quỹ đạo $$X/G$$ & Tác động Dừng Đúng (Properly Discontinuous)
- **Bản chất:** Dán mọi điểm trong cùng một quỹ đạo thành một điểm tạo ra không gian thương $$X/G$$. Đặc biệt, khi tác động rời rạc là **tự do và dừng đúng** (mỗi điểm có lân cận $$U$$ sao cho $$gU \cap U = \emptyset$$ với mọi $$g \neq e$$), ánh xạ chiếu $$X \to X/G$$ trở thành một **ánh xạ phủ** tuyệt đẹp (cửa ngõ sang Chương 06!).

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc: So sánh Quỹ đạo & Stabilizer trên 3 tác động kinh điển

1. **Nhóm $$G = \mathbb{Z}$$ tịnh tiến trên $$X = \mathbb{R}$$ bởi $$n \cdot x = x + n$$:**
   - **Quỹ đạo của $$x = 0.3$$:** $$\{\dots, -1.7, -0.7, 0.3, 1.3, 2.3, \dots\}$$.
   - **Stabilizer:** $$x + n = x \iff n = 0 \implies G_x = \{0\}$$ với mọi $$x$$ (**tác động tự do**!).
   - **Dừng đúng:** Chọn lân cận $$U = (x - \tfrac{1}{3}, x + \tfrac{1}{3})$$; với mọi $$n \neq 0$$, $$U + n$$ rời hẳn $$U$$!
   - **Không gian quỹ đạo:** $$\mathbb{R}/\mathbb{Z} \cong S^1$$ (và $$\mathbb{R} \to S^1$$ là ánh xạ phủ!).

2. **Nhóm $$G = \mathbb{Z}/2\mathbb{Z} = \{+1, -1\}$$ tác động đối tâm trên $$X = S^2$$ bởi $$(\pm 1)\cdot x = \pm x$$:**
   - **Quỹ đạo:** Mỗi cặp điểm đối tâm $$\{x, -x\}$$ (đúng 2 điểm).
   - **Stabilizer:** Vì $$x \in S^2$$ nên $$x \neq -x \implies G_x = \{+1\}$$ (**tự do**!).
   - **Không gian quỹ đạo:** $$S^2 / (\mathbb{Z}/2\mathbb{Z}) = \mathbb{R}P^2$$ (mặt phẳng xạ ảnh thực!).

3. **Nhóm quay $$G = SO(2)$$ xoay quanh trục $$Oz$$ trên $$X = S^2$$:**
   - **Điểm trên vĩ tuyến $$z \in (-1, 1)$$:** Quỹ đạo là cả đường tròn vĩ tuyến $$S^1$$; stabilizer là $$\{I\}$$.
   - **Cực Bắc $$(0,0,1)$$ và Cực Nam $$(0,0,-1)$$:** Bị giữ bất động bởi mọi phép quay! Quỹ đạo chỉ có 1 điểm; stabilizer là **toàn bộ $$SO(2)$$** (tác động **không tự do**!).
   - **Không gian quỹ đạo:** Mỗi vĩ tuyến (và hai cực) được xác định duy nhất bởi cao độ $$z \in [-1, 1] \implies S^2 / SO(2) \cong [-1, 1]$$ (xuất hiện 2 điểm biên tương ứng với 2 điểm bất động!).

### Khung giải thích: Quy trình 4 bước phân tích một không gian quỹ đạo $$X/G$$ (nên đọc chậm)

#### Bước 1: Tìm một "miền cơ bản" (Fundamental Domain)
Chọn một mảnh con $$D \subseteq X$$ chứa ít nhất một đại diện của mỗi quỹ đạo (ví dụ $$[0,1]$$ cho $$\mathbb{R}/\mathbb{Z}$$, hay bán cầu Bắc cho $$S^2/(\mathbb{Z}/2\mathbb{Z})$$).

#### Bước 2: Xem nhóm $$G$$ dán phần biên của miền cơ bản như thế nào
Mọi điểm bên trong $$D$$ là duy nhất; chỉ các điểm trên biên $$\partial D$$ mới bị dán với nhau bởi các phần tử sinh của $$G$$ (ví dụ $$0 \sim 1$$ trên $$[0,1]$$, hay biên xích đạo $$x \sim -x$$ trên bán cầu Bắc).

#### Bước 3: Kiểm tra điểm bất động (Stabilizer khác tầm thường)
Nếu tác động **tự do + dừng đúng** trên một đa tạp $$X$$, thương $$X/G$$ chắc chắn vẫn là một **đa tạp trơn** (như $$S^1, T^2, \mathbb{R}P^2$$). Nếu có điểm bất động (như phép quay $$180^\circ$$ trên $$\mathbb{R}^2$$), thương xuất hiện đỉnh nhọn (orbifold / hình nón!).

#### Bước 4: Đọc ngay nhóm cơ bản của thương
Nếu $$X$$ đơn liên (như $$\mathbb{R}$$ hay $$S^2$$) và $$G$$ tác động tự do, dừng đúng, thì **$$\pi_1(X/G) \cong G$$**! Ta đọc ra ngay $$\pi_1(S^1) \cong \mathbb{Z}$$ và $$\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$$ mà hầu như không phải tính gì thêm!

$$
\text{Không gian }X \text{ + Tác động nhóm }G
\;\xrightarrow{\;\text{Miền cơ bản + Dán biên}\;}\;
\text{Không gian quỹ đạo }X/G
\;\xrightarrow{\;\text{Tự do + Dừng đúng}\;}\;
\pi_1(X/G) \cong G.
$$

---

## 🔄 Định nghĩa tác động nhóm

### 1. Định nghĩa cơ bản

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tác động nhóm):**  
Cho $G$ là một nhóm (nhóm tô-pô hoặc nhóm rời rạc) và $X$ là không gian tô-pô. Một **tác động trái** (left action) của $G$ lên $X$ là một ánh xạ:

$$
G \times X \to X, \quad (g, x) \mapsto g \cdot x
$$
</div>

thỏa mãn hai tiên đề:
- **(GA1) Phần tử đơn vị:** $e \cdot x = x$ với mọi $x \in X$ ($e$ là phần tử đơn vị của $G$).
- **(GA2) Tính kết hợp:** $g \cdot (h \cdot x) = (gh) \cdot x$ với mọi $g, h \in G$ và $x \in X$.

Tác động được gọi là **liên tục** nếu ánh xạ $G \times X \to X$ liên tục (với tô-pô tích trên $G \times X$).

Tương tự có thể định nghĩa tác động phải $x \cdot g$ thỏa mãn $x \cdot e = x$ và $x \cdot (gh) = (x \cdot g) \cdot h$; trong bài này ta quy ước dùng tác động trái.

**Cách nhìn tương đương (khi $G$ rời rạc):** Một tác động liên tục của $G$ lên $X$ tương ứng với một đồng cấu nhóm $\varphi: G \to \operatorname{Homeo}(X)$, trong đó $\varphi(g)(x) = g \cdot x$.

---

### 2. Các ví dụ

- **Ví dụ 1 (Phép quay):** $G = S^1 = \{e^{i\theta} : \theta \in [0, 2\pi)\}$ tác động lên $X = \mathbb{C}$ bởi $e^{i\theta} \cdot z = e^{i\theta} z$. Đây là tác động liên tục quay mặt phẳng phức một góc $\theta$.
- **Ví dụ 2 (Phép tịnh tiến):** $G = \mathbb{Z}$ tác động lên $X = \mathbb{R}$ bởi $n \cdot x = x + n$. Không gian quỹ đạo là $\mathbb{R}/\mathbb{Z} \cong S^1$.
- **Ví dụ 3 (Phép đối cực):** $G = \mathbb{Z}/2\mathbb{Z} = \{0, 1\}$ tác động lên $X = S^n$ bởi $0 \cdot x = x$ và $1 \cdot x = -x$. Không gian quỹ đạo là $S^n/(\mathbb{Z}/2\mathbb{Z}) \cong \mathbb{R}P^n$.
- **Ví dụ 4 (Tác động tuyến tính):** $G = GL_n(\mathbb{R})$ tác động lên $X = \mathbb{R}^n$ bởi phép nhân ma trận $A \cdot x = Ax$.
- **Ví dụ 5 (Phép biến đổi phủ – Deck Transformations):** Với không gian phủ $p: \tilde{X} \to X$, nhóm các tự đồng phôi phủ $G = \operatorname{Aut}(\tilde{X}/X)$ tác động tự nhiên lên $\tilde{X}$.

---

## 🎯 Quỹ đạo và Nhóm ổn định hóa

### 1. Quỹ đạo (Orbits)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Quỹ đạo):**  
Quỹ đạo của điểm $x \in X$ dưới tác động của $G$ là tập con:

$$
G \cdot x = \{g \cdot x : g \in G\} \subseteq X
$$
</div>

Quỹ đạo $G \cdot x$ gồm tất cả các điểm mà $x$ có thể đi tới dưới tác động của các phần tử trong $G$.

---

<div class="textbook-theorem" markdown="1">
**Mệnh đề:**  
Các quỹ đạo tạo thành một phân hoạch của $X$: mọi điểm thuộc một quỹ đạo, và hai quỹ đạo bất kỳ hoặc trùng nhau hoặc rời nhau.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Xác định quan hệ tương đương $x \sim y \iff \exists g \in G: y = g \cdot x$; các lớp tương đương chính là các quỹ đạo.
</div>

---

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian quỹ đạo):**  
**Không gian quỹ đạo** (hay thương theo tác động nhóm) là tập các quỹ đạo:

$$
X/G = \{G \cdot x : x \in X\} = \text{set of orbits}
$$
</div>

Không gian $X/G$ được trang bị tô-pô thương cảm sinh bởi ánh xạ chiếu $\pi: X \to X/G$, $\pi(x) = G \cdot x$ (tức $U \subseteq X/G$ mở $\iff \pi^{-1}(U)$ mở trong $X$). Lưu ý rằng ánh xạ chiếu $\pi: X \to X/G$ luôn là **ánh xạ mở**, vì với mọi tập mở $V \subseteq X$, $\pi^{-1}(\pi(V)) = \bigcup_{g \in G} g \cdot V$ là hợp của các tập mở nên mở trong $X$.

**Ví dụ:**
- Trong $\mathbb{R}/\mathbb{Z} \cong S^1$, mỗi quỹ đạo có dạng $\{x + n : n \in \mathbb{Z}\}$.
- Trong $S^n/(\mathbb{Z}/2\mathbb{Z}) \cong \mathbb{R}P^n$, mỗi quỹ đạo là một cặp điểm đối cực $\{x, -x\}$.

---

### 2. Nhóm ổn định hóa (Stabilizers)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Nhóm ổn định hóa):**  
**Nhóm ổn định hóa** (stabilizer hay isotropy group) của điểm $x \in X$ là tập hợp:

$$
G_x = \{g \in G : g \cdot x = x\} \subseteq G
$$
</div>

Đây là tập các phần tử của $G$ giữ cố định điểm $x$.

---

<div class="textbook-theorem" markdown="1">
**Mệnh đề:** $G_x$ là một nhóm con của $G$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Kiểm tra trực tiếp $e \in G_x$, và $G_x$ đóng dưới phép nhân cũng như lấy nghịch đảo.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý Quỹ đạo – Ổn định hóa):**  
Tồn tại một song ánh tự nhiên giữa tập các lớp ghép trái $G/G_x$ và quỹ đạo $G \cdot x$:

$$
G/G_x \leftrightarrow G \cdot x
$$
</div>

Nếu $G$ hữu hạn, ta có công thức $|G \cdot x| = |G| / |G_x|$.

<div class="textbook-proof" markdown="1">
**Chứng minh:** Ánh xạ $gG_x \mapsto g \cdot x$ xác định tốt và là một song ánh.
</div>

**Ví dụ:**
- $S^1$ tác động lên $\mathbb{C}$ bằng phép quay: $G_0 = S^1$ (mọi phép quay đều giữ cố định gốc tọa độ), còn với $z \neq 0$ thì $G_z = \{1\}$.
- $SO(3)$ tác động lên $S^2$: nhóm ổn định hóa của cực bắc là $SO(2)$ (các phép quay quanh trục $Oz$).

---

## 🌀 Tác động tự do và Tác động gián đoạn thực sự

### 1. Tác động tự do (Free Actions)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tác động tự do):**  
Tác động của $G$ lên $X$ được gọi là **tự do** (free) nếu $G_x = \{e\}$ với mọi $x \in X$.
</div>

Nói cách khác, không có phần tử nào khác $e$ cố định bất kỳ điểm nào của $X$: nếu $g \cdot x = x$ với một điểm $x$ nào đó thì $g = e$.

**Ví dụ tự do:**
- $\mathbb{Z}$ tác động lên $\mathbb{R}$ bằng phép tịnh tiến,
- $\mathbb{Z}/2\mathbb{Z}$ tác động lên toàn bộ $S^n$ bằng phép đối cực $x \mapsto -x$ (vì $-x \neq x$ với mọi $x \in S^n$).

**Ví dụ không tự do:**
- $S^1$ tác động lên $\mathbb{C}$ (gốc $0$ là điểm cố định),
- $SO(3)$ tác động lên $\mathbb{R}^3$ (gốc $0$ là điểm cố định).

---

### 2. Tác động không gian phủ / Gián đoạn thực sự

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tác động không gian phủ / Properly Discontinuous theo nghĩa Hatcher):**  
Tác động của nhóm rời rạc $G$ lên $X$ thỏa mãn điều kiện **tác động không gian phủ** (thường gọi là *properly discontinuous* trong một số giáo trình) nếu với mọi $x \in X$, tồn tại lân cận mở $U$ của $x$ sao cho:

$$
g \cdot U \cap U \neq \emptyset \implies g = e
$$
</div>

Lưu ý rằng điều kiện trên tự động kéo theo tác động là tự do. Trong ngữ cảnh không gian Hausdorff compact địa phương, một khái niệm liên quan là tác động **thực sự** (proper): với mọi cặp tập compact $K, L \subseteq X$, tập $\{g \in G : gK \cap L \neq \emptyset\}$ là hữu hạn.

**Ví dụ thỏa mãn:**
- $\mathbb{Z}$ tác động lên $\mathbb{R}$ bằng phép tịnh tiến,
- $\mathbb{Z}/2\mathbb{Z}$ tác động lên $S^n$ bằng phép đối cực,
- $\mathbb{Z}^2$ tác động lên $\mathbb{R}^2$ bằng phép tịnh tiến theo mạng nguyên.

**Ví dụ không thỏa mãn:**
- $\mathbb{Q}$ tác động lên $\mathbb{R}$ bằng phép cộng (các quỹ đạo trù mật),
- $S^1$ tác động lên $\mathbb{C}$ (quỹ đạo là đường tròn liên tục, không rời rạc).

---

<div class="textbook-theorem" markdown="1">
**Định lý (Phép chiếu phủ):**  
Nếu nhóm rời rạc $G$ tác động lên $X$ thỏa mãn điều kiện tác động không gian phủ ($gU \cap U = \emptyset$ với mọi $g \neq e$), thì ánh xạ chiếu $\pi: X \to X/G$ là một **ánh xạ phủ** (covering map). Đặc biệt, nếu $X$ đơn liên và liên thông đường địa phương thì $X$ là không gian phủ phổ dụng của $X/G$ và $\pi_1(X/G) \cong G$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Với lân cận $U$ như định nghĩa, $\pi(U)$ mở trong $X/G$ và $\pi^{-1}(\pi(U)) = \bigsqcup_{g \in G} g \cdot U$ là hợp rời các tập mở, mỗi tập được $\pi$ ánh xạ đồng phôi lên $\pi(U)$.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý (Không gian quỹ đạo Hausdorff):**  
Nếu $G$ tác động thực sự (proper) lên không gian Hausdorff compact địa phương $X$ (chẳng hạn $G$ hữu hạn hoặc tác động tịnh tiến của mạng rời rạc $\mathbb{Z}^n$ trên $\mathbb{R}^n$), thì không gian quỹ đạo $X/G$ là không gian Hausdorff.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Tính thực sự của tác động đảm bảo đồ thị quan hệ tương đương đóng trong $X \times X$, kết hợp với việc $\pi$ là ánh xạ mở suy ra $X/G$ Hausdorff.
</div>

**Hệ quả:** $\mathbb{R}/\mathbb{Z} \cong S^1$ và $S^n/(\mathbb{Z}/2\mathbb{Z}) \cong \mathbb{R}P^n$ đều là không gian Hausdorff.

---

## 🎭 Các ứng dụng chính

### 1. Không gian phủ (Covering Spaces)

Cho không gian phủ $p: \tilde{X} \to X$. Nhóm các **phép biến đổi phủ** (deck transformations) là:
$G = \operatorname{Aut}(\tilde{X}/X) = \{f: \tilde{X} \to \tilde{X} \text{ đồng phôi} : p \circ f = p\}$.

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Nếu $p: \tilde{X} \to X$ là một không gian phủ **chuẩn tắc** (normal/regular, chẳng hạn phủ phổ dụng với $\tilde{X}$ đơn liên), trong đó $\tilde{X}$ liên thông đường và liên thông đường địa phương, thì $\tilde{X}/G \cong X$.
</div>

Đặc biệt, khi $\tilde{X}$ là phủ phổ dụng của $X$, ta có $G \cong \pi_1(X)$ và $\tilde{X}/\pi_1(X) \cong X$. Chẳng hạn $\mathbb{R}$ là phủ phổ dụng của $S^1$, $G = \mathbb{Z} = \pi_1(S^1)$ tác động bằng phép tịnh tiến và $\mathbb{R}/\mathbb{Z} \cong S^1$.

---

### 2. Miền cơ bản (Fundamental Domain)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Miền cơ bản):**  
Tập con $F \subseteq X$ được gọi là một **miền cơ bản** cho tác động của $G$ trên $X$ nếu:
- $\bigcup_{g \in G} g \cdot F = X$ (các ảnh của $F$ phủ toàn bộ $X$),
- $g \cdot \operatorname{int}(F) \cap \operatorname{int}(F) = \emptyset$ với mọi $g \neq e$ (phần trong rời nhau).
</div>

Về trực quan, $F$ là một "mảnh đại diện" cắt mỗi quỹ đạo đúng một lần (trừ có thể ở biên).

- **$\mathbb{Z}$ tác động lên $\mathbb{R}$:** Miền cơ bản đóng là $[0,1]$ (hoặc nửa mở $[0,1)$); thương $\mathbb{R}/\mathbb{Z} \cong [0,1]/(0 \sim 1) \cong S^1$.
- **$\mathbb{Z}^2$ tác động lên $\mathbb{R}^2$:** Miền cơ bản là hình vuông đơn vị $[0,1]^2$; thương là hình xuyến $T^2$.
- **Các nhóm giấy dán tường (Wallpaper Groups):** Có đúng $17$ nhóm đối xứng lát mặt phẳng Euclid; mỗi nhóm có một miền cơ bản lát kín mặt phẳng.

![Wallpaper group](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Wallpaper_group-p4m-2.jpg/400px-Wallpaper_group-p4m-2.jpg)  
*Nhóm giấy dán tường p4m – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Wallpaper_group-p4m-2.jpg)*

---

### 3. Tác động nhóm Lie và Không gian thuần nhất

Các **nhóm Lie** ($SO(n), U(n), SU(n), \ldots$) là những nhóm mang cấu trúc đa tạp trơn. Khi một nhóm Lie tác động trơn lên một đa tạp, không gian quỹ đạo thường là một không gian phân tầng (stratified space). Chẳng hạn, $SO(3)$ tác động lên $\mathbb{R}^3$ có quỹ đạo là gốc $\{0\}$ và các mặt cầu $S^2_r$ ($r > 0$), cho không gian quỹ đạo $[0, \infty)$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian thuần nhất – Homogeneous Space):**  
Không gian thương $M = G/H$ của một nhóm Lie $G$ theo một nhóm con đóng $H \subseteq G$.
</div>

**Ví dụ:**
- $S^n \cong SO(n+1) / SO(n)$,
- $\mathbb{R}P^n \cong O(n+1) / (O(n) \times O(1))$,
- Đa tạp Grassmann $G_k(\mathbb{R}^n) \cong O(n) / (O(k) \times O(n-k))$.

---

### 4. Kiểu quỹ đạo và Phân tầng (Stratification)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Kiểu quỹ đạo – Orbit Type):**  
Hai điểm $x, y \in X$ có cùng **kiểu quỹ đạo** nếu nhóm ổn định hóa $G_x$ và $G_y$ là hai nhóm con liên hợp trong $G$.
</div>

Không gian $X$ được phân chia thành các tầng (strata) gồm các điểm có cùng kiểu quỹ đạo. Ví dụ với $SO(3)$ tác động trên $\mathbb{R}^3$:
- Tầng 1: $\{0\}$ (ổn định hóa $SO(3)$),
- Tầng 2: $\mathbb{R}^3 \setminus \{0\}$ (ổn định hóa liên hợp với $SO(2)$).

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Felix Klein** – *"Erlanger Programm"* (1872)  
   *Quan điểm hình học là nghiên cứu các bất biến dưới tác động nhóm.*

2. **Élie Cartan** – *Lý thuyết nhóm Lie* (đầu thế kỷ 20)

3. **Claude Chevalley** – *"Theory of Lie Groups"* (1946)

### Giáo trình

4. **Allen Hatcher** – *Algebraic Topology*, **§1.3: Covering Spaces**

5. **John M. Lee** – *Introduction to Smooth Manifolds*, **Chapter 21**

6. **Glen E. Bredon** – *Introduction to Compact Transformation Groups* (1972)

7. **Tammo tom Dieck** – *Transformation Groups* (1987)

---

## 🔗 Ứng dụng và liên kết

### Tô-pô đại số – Không gian phủ
Phủ phổ dụng cho biểu diễn $X \cong \tilde{X}/\pi_1(X)$.

### Hình học vi phân – Không gian thuần nhất
Mặt cầu, không gian xạ ảnh và đa tạp Grassmann đều có dạng $G/H$.

### Vật lý – Lý thuyết chuẩn
Phân thớ chính và lý thuyết Yang–Mills mô tả các trường vật lý qua phép lấy thương theo nhóm chuẩn.

### Tinh thể học
Các nhóm không gian mô tả đối xứng tinh thể (gồm $230$ kiểu trong không gian $3$ chiều).

### Hệ động lực – Rút gọn đối xứng
Hệ Hamilton sử dụng phép lấy thương theo nhóm đối xứng (rút gọn symplectic).

---

## Video tham khảo

- **xem trước** [7.06 Group actions and covering spaces, 1](https://www.youtube.com/watch?v=slLVD9cXryo) — Jonathan Evans, tiếng Anh. Trình bày mối liên hệ giữa tác động nhóm, không gian quỹ đạo và không gian phủ.
- [Galois Coverings are precisely Quotients by Properly Discontinuous Free Actions](https://www.youtube.com/watch?v=RvooRyHHXAo) — nptelhrd, tiếng Anh. Phân tích mối liên hệ giữa phủ Galois và thương bởi tác động tự do, gián đoạn thực sự.
- [10. Covering Space Actions; the idea of Homology - Pierre Albin](https://www.youtube.com/watch?v=KudAvmWUx8s) — Mat Neth, tiếng Anh. Bài giảng của Pierre Albin về tác động không gian phủ và phép biến đổi phủ.

## 🧩 Bài tập

### Tác động nhóm

1. **Kiểm tra tác động:**  
   $\mathbb{Z}$ tác động lên $\mathbb{R}$ bởi $n \cdot x = x + n$. Kiểm tra hai tiên đề (GA1) và (GA2).

2. **Phép quay:**  
   $S^1$ tác động lên $\mathbb{C}$ bởi $e^{i\theta} \cdot z = e^{i\theta}z$. Kiểm tra tính liên tục của tác động này.

3. **Tác động ma trận:**  
   $GL_2(\mathbb{R})$ tác động lên $\mathbb{R}^2$. Kiểm tra các tiên đề tác động nhóm.

### Quỹ đạo

4. **Tính quỹ đạo:**  
   Với $\mathbb{Z}$ tác động lên $\mathbb{R}$ bằng phép tịnh tiến, quỹ đạo của $\pi$ là gì?

5. **Tác động đối cực:**  
   Với $\mathbb{Z}/2\mathbb{Z}$ tác động lên $S^2$ bằng phép đối cực, mô tả các quỹ đạo.

6. **Phân hoạch:**  
   Chứng minh các quỹ đạo phân hoạch không gian $X$.

### Nhóm ổn định hóa

7. **Tính nhóm ổn định hóa:**  
   Với $S^1$ tác động lên $\mathbb{C}$ bằng phép quay, tìm nhóm ổn định hóa của $0$ và của $1$.

8. **Định lý Quỹ đạo – Ổn định hóa:**  
   Kiểm chứng $|G \cdot x| \cdot |G_x| = |G|$ cho một nhóm hữu hạn $G$.

9. **Tác động của $SO(3)$:**  
   Với $SO(3)$ tác động lên $S^2$, tìm nhóm ổn định hóa của cực bắc.

### Tác động tự do

10. **Kiểm tra tự do:**  
    Chứng minh $\mathbb{Z}$ tác động tự do lên $\mathbb{R}$.

11. **Không tự do:**  
    Chứng minh $S^1$ tác động lên $\mathbb{C}$ không tự do và chỉ ra điểm cố định.

12. **Ánh xạ phủ:**  
    Kiểm tra ánh xạ thương $\mathbb{R} \to \mathbb{R}/\mathbb{Z} \cong S^1$ là một ánh xạ phủ.

### Tác động gián đoạn thực sự

13. **Kiểm tra điều kiện:**  
    Kiểm chứng $\mathbb{Z}$ tác động gián đoạn thực sự lên $\mathbb{R}$.

14. **Mạng $\mathbb{Z}^2$:**  
    $\mathbb{Z}^2$ tác động lên $\mathbb{R}^2$ bằng phép tịnh tiến có gián đoạn thực sự không? Không gian thương là gì?

15. **Không gián đoạn thực sự:**  
    Giải thích vì sao tác động cộng của $\mathbb{Q}$ lên $\mathbb{R}$ không gián đoạn thực sự.

### Miền cơ bản

16. **$\mathbb{R}/\mathbb{Z}$:**  
    Kiểm tra $[0,1]$ (hoặc $[0,1)$) là miền cơ bản cho tác động của $\mathbb{Z}$ lên $\mathbb{R}$.

17. **Hình xuyến:**  
    Với $\mathbb{Z}^2$ tác động lên $\mathbb{R}^2$, giải thích vì sao hình vuông đơn vị là miền cơ bản và thương là $T^2$.

18. **Nhóm giấy dán tường:**  
    Tìm hiểu một nhóm giấy dán tường và mô tả miền cơ bản của nó.

### Ứng dụng

19. **Không gian phủ của hình xuyến:**  
    Với ánh xạ phủ $\mathbb{R}^2 \to T^2$, kiểm chứng nhóm các phép biến đổi phủ là $\mathbb{Z}^2$.

20. **Không gian thuần nhất:**  
    Giải thích đồng phôi $S^n \cong SO(n+1)/SO(n)$.

---

## 📚 Đọc thêm

- **Lee, Smooth Manifolds:** Chapter 21 (Tác động nhóm Lie)
- **Hatcher, Algebraic Topology:** §1.3 (Phép biến đổi phủ)
- **Bredon, Transformation Groups**
- **Armstrong:** *Groups and Symmetry*

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu tác động nhóm và không gian quỹ đạo. Một tác động của nhóm $G$ lên $X$ phân hoạch $X$ thành các quỹ đạo $G \cdot x$, tạo nên không gian thương $X/G$ cùng nhóm ổn định hóa $G_x$ liên hệ qua định lý Quỹ đạo – Ổn định hóa. Tác động tự do và tác động không gian phủ (gián đoạn thực sự) sinh ra các ánh xạ phủ $\pi: X \to X/G$ và kết nối trực tiếp với nhóm phép biến đổi phủ, miền cơ bản, cũng như các không gian thuần nhất $G/H$ của nhóm Lie.

**Hoàn thành Chapter 05.** Chúng ta đã nắm được các công cụ xây dựng không gian qua phép lấy thương: tô-pô thương, phân loại mặt đóng, phức CW và không gian quỹ đạo.

**Tiếp theo:** Chapter 06 về **Nhóm cơ bản và Không gian phủ** — mở đầu cho tô-pô đại số.

---

*"Symmetry is the harmony of mathematics."*

---

**Previous:** [Lecture 05.02: CW Complexes](/contents/vi/topology-chapter05/05_02_CW_Complexes/)  
**Next Chapter:** [Chapter 06: Fundamental Group and Covering Spaces](/contents/vi/topology-chapter06/)
