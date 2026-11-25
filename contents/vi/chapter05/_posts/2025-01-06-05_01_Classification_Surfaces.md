---
layout: post
title: "Lecture 05.01: Classification of Compact Surfaces"
lang: vi
lang-ref: lecture-05-01
chapter: 5
lecture: 1
categories: [chapter05]
tags: [surfaces, classification, euler-characteristic, orientability, genus]
description: "Classification theorem cho compact surfaces: genus, orientability, và Euler characteristic"
---

**Phân loại các mặt compact**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Nếu ai đó đưa cho bạn một mặt 2 chiều đóng bất kỳ — có thể méo mó như củ gừng, có thể tự cắt xuyên qua nhau trong $$\mathbb{R}^3$$ như chai Klein hay mặt Boy — liệu có cách nào sắp xếp **tất cả vô hạn các bề mặt đóng có thể tồn tại trong vũ trụ** vào một danh sách gọn gàng duy nhất không? Câu trả lời là một trong những chiến thắng trọn vẹn nhất của toàn bộ lịch sử tô-pô học: **Định lý Phân loại Mặt đóng**! Mọi mặt đóng liên thông đều chỉ thuộc đúng **hai gia đình**: tổng liên thông của $$g$$ hình xuyến (định hướng được) hoặc tổng liên thông của $$k$$ mặt phẳng xạ ảnh (không định hướng được) — được nhận diện hoàn toàn chỉ bởi **tính định hướng** và **đặc trưng Euler $$\chi$$**!

Một trong những kết quả kinh điển của tô-pô học là **Định lý phân loại các mặt compact (không biên)**:

> **Mọi mặt compact liên thông (không biên) đều đồng phôi với đúng một mặt trong một danh sách chuẩn tắc đếm được.**

Kết quả này cho một phân loại đầy đủ theo phép đồng phôi — điều rất hiếm gặp trong tô-pô chiều cao (từ chiều $3$ trở lên, việc phân loại hoàn chỉnh các đa tạp tổng quát phức tạp hơn nhiều, và ở chiều $4$ bài toán nhận diện đồng phôi là không giải được bằng thuật toán).

![Surface examples](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Spot_the_cow_topology.gif/400px-Spot_the_cow_topology.gif)  
*Minh họa sự tương đương tô-pô của các mặt – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Spot_the_cow_topology.gif)*

Danh sách chuẩn tắc gồm hai họ:
- **Các mặt định hướng được:** mặt cầu $S^2$ (giống $g = 0$), hình xuyến $T^2$ ($g = 1$), và tổng quát là mặt giống $g$ ($\Sigma_g$) với mọi số nguyên $g \geq 0$.
- **Các mặt không định hướng được:** mặt phẳng xạ ảnh thực $\mathbb{R}P^2$ ($k = 1$), chai Klein $K = \mathbb{R}P^2 \# \mathbb{R}P^2$ ($k = 2$), và tổng liên thông của $k$ mặt phẳng xạ ảnh thực với mọi số nguyên $k \geq 1$.

Trong bài học này, chúng ta sẽ định nghĩa chính xác mặt (2-đa tạp), khảo sát các ví dụ cơ bản, phép tổng liên thông, tính định hướng được (orientability), đặc trưng Euler $\chi$, giống (genus) $g$, phát biểu Định lý phân loại và phác thảo ý tưởng chứng minh qua đa giác cơ bản.

Các bất biến $\chi$ và tính định hướng được xác định duy nhất một mặt đóng liên thông sai khác phép đồng phôi; đồng thời, chúng kết nối trực tiếp với đồng điều (trong tô-pô đại số), định lý Gauss–Bonnet (trong hình học vi phân), vật lý lý thuyết (mặt thế giới trong lý thuyết dây) và đồ họa máy tính (phân tích lưới bề mặt 3D).

---

## 🗺️ Kiến thức cần nhớ: Phân loại Mặt đóng là gì và dùng công cụ nào?

### 1. Mặt (2-Đa tạp) & Tổng liên thông (Connected Sum $$\#$$)
- **Bản chất:** Một **mặt đóng** là đa tạp 2 chiều, compact, liên thông và không có biên. Phép **tổng liên thông $$M_1 \# M_2$$** khoét một đĩa nhỏ trên mỗi mặt rồi dán hai đường biên tròn lại với nhau — giống như "phép cộng" các bề mặt (trong đó mặt cầu $$S^2$$ đóng vai trò số $$0$$: $$M \# S^2 \cong M$$!).

### 2. Đa giác Dán cạnh (Polygonal Presentation) & Từ Biên
- **Bản chất:** Mọi mặt đóng đều có thể cắt mở thành một đa giác phẳng với các cạnh được gán nhãn chữ cái có hướng (như $$aba^{-1}b^{-1}$$ cho hình xuyến $$T^2$$, hay $$aa$$ cho $$\mathbb{R}P^2$$). Các phép cắt–dán tổ hợp trên đa giác rút gọn mọi mặt phức tạp về đúng dạng chuẩn!

### 3. Hai Bất biến Đầy đủ: Tính Định hướng & Đặc trưng Euler $$\chi$$
- **Gia đình định hướng được:** $$S^2$$ ($$\chi=2$$) và $$\Sigma_g = T^2 \# \cdots \# T^2$$ ($$g$$ lần), với $$\chi(\Sigma_g) = 2 - 2g$$.
- **Gia đình không định hướng được:** $$N_k = \mathbb{R}P^2 \# \cdots \# \mathbb{R}P^2$$ ($$k$$ lần), với $$\chi(N_k) = 2 - k$$ (chú ý quy tắc vàng của Dyck: $$T^2 \# \mathbb{R}P^2 \cong \mathbb{R}P^2 \# \mathbb{R}P^2 \# \mathbb{R}P^2 = N_3$$!).

---

## 🧮 Ví dụ tính tay làm từng bước: Đếm $$V - E + F$$ từ Từ biên của 3 mặt kinh điển

Hãy tự tay tính đặc trưng Euler $$\chi = V - E + F$$ trực tiếp từ đa giác dán cạnh của 3 bề mặt quan trọng nhất:

1. **Hình xuyến $$T^2$$ — Hình vuông với từ biên $$a b a^{-1} b^{-1}$$:**
   - Mặt: $$F = 1$$ (lòng hình vuông).
   - Cạnh: 4 cạnh dán thành 2 cặp $$a, b \implies E = 2$$.
   - Đỉnh: đi vòng quanh một góc ta thấy cả 4 góc của hình vuông đều bị dán vào nhau thành đúng **1 đỉnh duy nhất** $$\implies V = 1$$.
   - Vậy $$\chi(T^2) = 1 - 2 + 1 = 0$$ (định hướng được $$\implies g = 1$$!).

2. **Mặt phẳng xạ ảnh thực $$\mathbb{R}P^2$$ — Nhị giác với từ biên $$a a$$:**
   - Mặt: $$F = 1$$ (đĩa tròn).
   - Cạnh: 2 nửa viền dán cùng chiều thành 1 cạnh $$a \implies E = 1$$.
   - Đỉnh: hai đầu của $$a$$ dán trùng nhau thành đúng **1 đỉnh** $$\implies V = 1$$.
   - Vậy $$\chi(\mathbb{R}P^2) = 1 - 1 + 1 = 1$$ (không định hướng được $$\implies k = 1$$!).

3. **Chai Klein $$K$$ — Hình vuông với từ biên $$a b a^{-1} b$$:**
   - Giống hình xuyến, $$F = 1,\; E = 2,\; V = 1 \implies \chi(K) = 1 - 2 + 1 = 0$$!
   - Nhưng khác hình xuyến ở chỗ hai cạnh $$b$$ dán **cùng chiều** (chứa dải Möbius bên trong $$\implies$$ **không định hướng được**!).
   - Tra ngay bảng phân loại: mặt không định hướng có $$\chi = 2 - k = 0 \implies k = 2$$, tức **$$K \cong \mathbb{R}P^2 \# \mathbb{R}P^2$$** (hai mặt phẳng xạ ảnh ghép lại, hay hai dải Möbius dán biên vào nhau!).

### Giải thích: Con đường 4 bước dẫn tới Định lý Phân loại Mặt đóng

#### Bước 1: Tam giác hóa và trải phẳng thành một đa giác duy nhất
Mọi mặt đóng đều có thể chia thành hữu hạn tam giác (Định lý Radó). Dán lần lượt các tam giác dọc theo một cây khung sẽ trải toàn bộ mặt ra thành **một đa giác phẳng duy nhất** có các cạnh ghép cặp.

#### Bước 2: Gom đỉnh và ghép cặp các cạnh cùng chiều / ngược chiều
Bằng các nhát cắt chéo rồi dán lại trên đa giác (biến đổi cắt–dán không đổi tô-pô!), ta dồn tất cả các đỉnh về chung 1 đỉnh, đồng thời gom mọi cặp cạnh cùng chiều thành khối $$c_i c_i$$ (mũ chéo — crosscap $$\mathbb{R}P^2$$) và cặp ngược chiều đan xen thành khối $$a_j b_j a_j^{-1} b_j^{-1}$$ (quai cầm — handle $$T^2$$).

#### Bước 3: Áp dụng Định lý Dyck để "nuốt" quai cầm vào mũ chéo
Nếu mặt đã có ít nhất một mũ chéo (không định hướng được), mỗi quai cầm $$T^2$$ chạm vào mũ chéo $$\mathbb{R}P^2$$ sẽ biến thành 2 mũ chéo mới: $$T^2 \# \mathbb{R}P^2 \cong \mathbb{R}P^2 \# \mathbb{R}P^2 \# \mathbb{R}P^2$$! Nhờ đó ta không bao giờ có mặt "lai" giữa $$T^2$$ và $$\mathbb{R}P^2$$!

#### Bước 4: Nhận diện tức thì mọi mặt đóng chỉ bằng 2 bước kiểm tra
Gặp bất kỳ mặt đóng liên thông nào, chỉ cần kiểm tra đúng 2 điều: (1) nó có chứa dải Möbius (không định hướng) hay không? và (2) tính $$\chi = V - E + F$$. Bạn lập tức gọi tên chính xác mặt đó sai khác đồng phôi!

$$
\text{Mặt đóng }M
\;\xrightarrow{\;\text{Cắt–dán đa giác}\;}\;
\begin{cases}
\text{Định hướng được: } \Sigma_g = \#^g T^2 \;(\chi = 2 - 2g) \\
\text{Không định hướng: } N_k = \#^k \mathbb{R}P^2 \;(\chi = 2 - k)
\end{cases}
$$

---

## 🌍 Mặt (Surfaces): Định nghĩa và ví dụ

### 1. Định nghĩa

Về trực quan, một **mặt** (surface) là không gian tô-pô mà xung quanh mỗi điểm trông cục bộ giống mặt phẳng $\mathbb{R}^2$.

**Định nghĩa chính thức:**  
Một **mặt** (hay **2-đa tạp tô-pô không biên**) là không gian tô-pô $X$ thỏa mãn:
1. **Hausdorff**,
2. **Thỏa mãn tiên đề đếm được thứ hai** (second countable),
3. **Euclid địa phương chiều 2:** với mọi $x \in X$, tồn tại lân cận mở $U$ của $x$ đồng phôi với một tập con mở của $\mathbb{R}^2$.

Trong bài học này, chúng ta tập trung vào các **mặt đóng liên thông**, tức các mặt compact, liên thông và không có biên.

---

### 2. Các ví dụ tiêu chuẩn

**Ví dụ 1: Mặt cầu $S^2$**

$$
S^2 = \{(x,y,z) \in \mathbb{R}^3 : x^2 + y^2 + z^2 = 1\}
$$

$S^2$ là mặt compact (đóng và bị chặn trong $\mathbb{R}^3$), liên thông, định hướng được, có giống $g = 0$ và đặc trưng Euler $\chi = 2$.

![Sphere](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Sphere_wireframe_10deg_6r.svg/400px-Sphere_wireframe_10deg_6r.svg.png)  
*Mặt cầu $S^2$ – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Sphere_wireframe_10deg_6r.svg)*

---

**Ví dụ 2: Hình xuyến $T^2$**

**Cách dựng:** Lấy thương của hình vuông $[0,1]^2$ bằng cách dán hai cặp cạnh đối diện cùng chiều: $(0, t) \sim (1, t)$ và $(s, 0) \sim (s, 1)$.

**Tính chất:** $T^2$ nhúng được vào $\mathbb{R}^3$ như một mặt tròn xoay, là mặt compact, liên thông, định hướng được, có giống $g = 1$ và đặc trưng Euler $\chi = 0$.

![Torus](https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Torus.png/400px-Torus.png)  
*Hình xuyến $T^2$ – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus.png)*

---

**Ví dụ 3: Mặt giống $g$ ($\Sigma_g$)**

**Cách dựng:** Tổng liên thông của $g$ hình xuyến ($T^2 \# \cdots \# T^2$, $g$ lần), trực quan là mặt cầu gắn thêm $g$ tay cầm (handles).
- $g = 0$: mặt cầu $S^2$,
- $g = 1$: hình xuyến $T^2$,
- $g = 2$: hình xuyến hai lỗ $\Sigma_2$.

Các mặt $\Sigma_g$ đều compact, liên thông, định hướng được và có đặc trưng Euler $\chi = 2 - 2g$.

![Genus 2 surface](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/Double_torus_illustration.png/400px-Double_torus_illustration.png)  
*Mặt giống $2$ – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Double_torus_illustration.png)*

---

**Ví dụ 4: Mặt phẳng xạ ảnh thực $\mathbb{R}P^2$**

**Cách dựng:** Lấy thương mặt cầu $S^2$ theo quan hệ đối cực $x \sim -x$ (hoặc tương đương, lấy đĩa đóng $D^2$ và đồng nhất các cặp điểm đối cực trên đường tròn biên).

**Tính chất:** $\mathbb{R}P^2$ compact, liên thông, **không định hướng được**, có đặc trưng Euler $\chi = 1$. Mặt này không thể nhúng vào $\mathbb{R}^3$ mà không tự cắt (nhưng có thể dìm vào $\mathbb{R}^3$, ví dụ mặt Boy hay cross-cap).

---

**Ví dụ 5: Chai Klein $K$**

**Cách dựng:** Lấy thương của hình vuông $[0,1]^2$ theo quan hệ $(0, t) \sim (1, t)$ (dán trái–phải cùng chiều) và $(s, 0) \sim (1-s, 1)$ (dán dưới–trên ngược chiều).

**Tính chất:** $K$ compact, liên thông, có $\chi = 0$ giống hình xuyến nhưng **không định hướng được**. Giống $\mathbb{R}P^2$, chai Klein không nhúng được vào $\mathbb{R}^3$ mà cần không gian $\mathbb{R}^4$; mọi hình vẽ trong $\mathbb{R}^3$ đều là phép dìm có tự cắt.

![Klein bottle](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5c/Klein_bottle.svg/400px-Klein_bottle.svg.png)  
*Phép dìm chai Klein trong $\mathbb{R}^3$ – Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Klein_bottle.svg)*

---

### 3. Phép tổng liên thông (Connected Sum)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tổng liên thông):**  
Cho hai mặt $S_1, S_2$. **Tổng liên thông** $S_1 \# S_2$ được xây dựng bằng cách:
1. Khoét bỏ một đĩa mở nhỏ trên mỗi mặt,
2. Dán hai đường tròn biên vừa tạo ra với nhau bằng một phép đồng phôi.
</div>

**Ví dụ:**
- $T^2 \# T^2 \cong \Sigma_2$ (mặt giống $2$),
- $\mathbb{R}P^2 \# \mathbb{R}P^2 \cong K$ (chai Klein),
- $S^2 \# S \cong S$ với mọi mặt $S$ (mặt cầu đóng vai trò phần tử đơn vị).

---

## 🔄 Tính định hướng được (Orientability)

### 1. Ý tưởng trực quan

Một mặt được gọi là **định hướng được** nếu ta có thể chọn một quy ước nhất quán về chiều quay ("thuận chiều kim đồng hồ") trên toàn bộ mặt. Tương đương, một mặt là định hướng được khi và chỉ khi nó **không** chứa tập con nào đồng phôi với dải Möbius.

Nếu một người đi dọc theo một vòng khép kín trên mặt mang theo một khung định hướng (chẳng hạn mũi tên chỉ hướng), khi quay về điểm xuất phát:
- Khung luôn giữ nguyên hướng trên mặt định hướng được ($S^2$, $T^2$, $\Sigma_g$).
- Có thể bị lật ngược hướng trên mặt không định hướng được ($\mathbb{R}P^2$, chai Klein, dải Möbius).

---

### 2. Mô tả hình thức (sơ lược)

- **Qua phép phân tam giác:** Mặt định hướng được khi và chỉ khi có thể định hướng tất cả các tam giác sao cho trên mỗi cạnh chung, hai tam giác kề nhau cảm sinh hai hướng ngược nhau.
- **Qua trường vector (cho mặt trơn trong $\mathbb{R}^3$):** Một mặt trơn nhúng trong $\mathbb{R}^3$ định hướng được khi và chỉ khi tồn tại trường vector pháp tuyến đơn vị liên tục trên toàn mặt.

---

### 3. Các tính chất cơ bản

<div class="textbook-theorem" markdown="1">
**Định lý:**
1. $S^2$, $T^2$ và mọi mặt $\Sigma_g$ đều định hướng được.
2. $\mathbb{R}P^2$ và chai Klein $K$ không định hướng được.
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Tính định hướng của tổng liên thông):**
- Định hướng được $\#$ Định hướng được $=$ Định hướng được.
- Định hướng được $\#$ Không định hướng được $=$ Không định hướng được.
- Không định hướng được $\#$ Không định hướng được $=$ Không định hướng được.
</div>

Chỉ cần một thành phần không định hướng được thì tổng liên thông sẽ không định hướng được (vì nó chứa dải Möbius của thành phần đó).

---

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Mọi mặt đóng định hướng được đều nhúng được vào $\mathbb{R}^3$. Ngược lại, không có mặt đóng không định hướng được nào nhúng được vào $\mathbb{R}^3$ (chúng chỉ có thể dìm vào $\mathbb{R}^3$ hoặc nhúng vào $\mathbb{R}^4$).
</div>

---

## 🔢 Đặc trưng Euler (Euler Characteristic)

### 1. Định nghĩa qua phép phân tam giác

Phân chia một mặt compact thành hữu hạn các tam giác (đơn hình 2 chiều) gọi là một **phép phân tam giác** (triangulation). Ký hiệu $V$ là số đỉnh, $E$ là số cạnh và $F$ là số mặt tam giác.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Đặc trưng Euler):**

$$
\chi = V - E + F
$$
</div>

Một kết quả cơ bản của tô-pô tổ hợp và lý thuyết đồng điều là $\chi$ **không phụ thuộc vào cách chọn phép phân tam giác**, và là một bất biến tô-pô (hai mặt đồng phôi có cùng đặc trưng Euler).

<div class="textbook-proof" markdown="1">
**Chứng minh:** Sử dụng tô-pô tổ hợp hoặc lý thuyết đồng điều (trong đó $\chi = \sum_i (-1)^i \operatorname{rank} H_i(S)$).
</div>

---

### 2. Các ví dụ tính toán

- **Mặt cầu $S^2$:** Phân tam giác bởi biên của một tứ diện có $V = 4, E = 6, F = 4$, suy ra $\chi(S^2) = 4 - 6 + 4 = 2$.
- **Hình xuyến $T^2$:** Với một phép phân tam giác tiêu chuẩn có $V = 9, E = 27, F = 18$, ta được $\chi(T^2) = 9 - 27 + 18 = 0$.
- **Mặt phẳng xạ ảnh $\mathbb{R}P^2$:** $\chi(\mathbb{R}P^2) = 1$.
- **Chai Klein $K$:** $\chi(K) = 0$ (cùng đặc trưng Euler với $T^2$, nhưng khác nhau về tính định hướng được).

---

### 3. Công thức cho mặt định hướng được giống $g$

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Với mặt đóng định hướng được giống $g$ ($\Sigma_g$):

$$
\chi = 2 - 2g
$$
</div>

Cụ thể: $g = 0 \Rightarrow \chi = 2$ ($S^2$); $g = 1 \Rightarrow \chi = 0$ ($T^2$); $g = 2 \Rightarrow \chi = -2$; mỗi tay cầm thêm vào làm giảm $\chi$ đi $2$.

---

### 4. Công thức cho mặt không định hướng được

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Với mặt đóng không định hướng được là tổng liên thông của $k$ mặt phẳng xạ ảnh thực ($k \ge 1$):

$$
\chi = 2 - k
$$
</div>

Cụ thể: $k = 1 \Rightarrow \chi = 1$ ($\mathbb{R}P^2$); $k = 2 \Rightarrow \chi = 0$ (chai Klein $K$); $k = 3 \Rightarrow \chi = -1$.

---

## 🏆 Định lý phân loại các mặt compact

### 1. Phát biểu

<div class="textbook-theorem" markdown="1">
**Định lý (Phân loại các mặt compact liên thông không biên):**  
Mọi mặt compact liên thông không biên đều đồng phôi với **đúng một** mặt trong hai họ sau:
</div>

**Họ định hướng được:**
1. Mặt cầu $S^2$ ($g = 0$),
2. Hình xuyến $T^2$ ($g = 1$),
3. Mặt giống $g$: $\Sigma_g = T^2 \# \cdots \# T^2$ ($g$ lần, với $g \geq 2$).

**Họ không định hướng được:**
1. Mặt phẳng xạ ảnh thực $\mathbb{R}P^2$ ($k = 1$),
2. Chai Klein $K = \mathbb{R}P^2 \# \mathbb{R}P^2$ ($k = 2$),
3. Tổng liên thông $(\mathbb{R}P^2)^{\#k} = \mathbb{R}P^2 \# \cdots \# \mathbb{R}P^2$ ($k$ lần, với $k \geq 3$).

---

### 2. Tính duy nhất qua bất biến

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Hai mặt đóng liên thông đồng phôi với nhau khi và chỉ khi chúng có cùng đặc trưng Euler $\chi$ và cùng tính định hướng được.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Suy trực tiếp từ Định lý phân loại và việc cặp bất biến $(\chi, \text{tính định hướng được})$ nhận các giá trị phân biệt trên toàn bộ danh sách chuẩn tắc.
</div>

Nhờ định lý này, để nhận diện một mặt đóng liên thông bất kỳ, ta chỉ cần tính đặc trưng Euler $\chi$ (chẳng hạn qua phép phân tam giác) và kiểm tra xem mặt có định hướng được hay không.

---

### 3. Bảng tổng hợp các mặt

| Mặt | Định hướng được | Giống $g$ | $\chi$ | Ký hiệu |
|-----|-----------------|-----------|--------|---------|
| Mặt cầu | Có | $0$ | $2$ | $S^2$ |
| Hình xuyến | Có | $1$ | $0$ | $T^2$ |
| Hình xuyến hai lỗ | Có | $2$ | $-2$ | $\Sigma_2$ |
| Mặt giống $g$ | Có | $g$ | $2 - 2g$ | $\Sigma_g$ |
| Mặt phẳng xạ ảnh | Không | – | $1$ | $\mathbb{R}P^2$ |
| Chai Klein | Không | – | $0$ | $K$ |
| Tổng liên thông $k$ mặt $\mathbb{R}P^2$ | Không | – | $2 - k$ | $(\mathbb{R}P^2)^{\#k}$ |

---

### 4. Phác thảo chứng minh

1. **Phân tam giác (Định lý Radó):** Mọi mặt compact đều thừa nhận một phép phân tam giác hữu hạn.
2. **Đa giác cơ bản:** Dán dần các tam giác kề nhau thành một đa giác đơn duy nhất có các cạnh được ghép cặp để dán lại.
3. **Đưa về dạng chuẩn:** Thực hiện dãy hữu hạn phép cắt–dán trên đa giác để đưa từ biên về một trong hai dạng chuẩn tắc:
   - Định hướng được: $a_1 b_1 a_1^{-1} b_1^{-1} \cdots a_g b_g a_g^{-1} b_g^{-1}$ (hoặc $a a^{-1}$ cho $S^2$).
   - Không định hướng được: $c_1 c_1 c_2 c_2 \cdots c_k c_k$.
4. **Nhận diện:** Mỗi dạng chuẩn tương ứng chính xác với một mặt trong danh sách $S^2$, $\Sigma_g$, $(\mathbb{R}P^2)^{\#k}$.
5. **Phân biệt:** Đặc trưng Euler $\chi$ và tính định hướng được chứng tỏ không có hai mặt nào trong danh sách đồng phôi với nhau.

Chứng minh đầy đủ có thể tham khảo trong các giáo trình của Armstrong, Massey hoặc Hatcher.

---

## 🎨 Trực quan hình học

### 1. Đa giác cơ bản (Fundamental Polygons)

- **Mặt cầu $S^2$:** Đĩa đóng co biên thành một điểm (hoặc hai bán cầu dán dọc xích đạo).
- **Hình xuyến $T^2$:** Hình vuông dán các cạnh đối diện cùng chiều ($a b a^{-1} b^{-1}$).
- **Mặt giống $2$ ($\Sigma_2$):** Hình bát giác với từ biên $a b a^{-1} b^{-1} c d c^{-1} d^{-1}$.
- **Mặt phẳng xạ ảnh $\mathbb{R}P^2$:** Đĩa đóng đồng nhất các điểm đối cực trên biên (hoặc đa giác có từ biên $a a$).
- **Chai Klein $K$:** Hình vuông với $(0,t) \sim (1,t)$ và $(s,0) \sim (1-s,1)$ (từ biên $a b a^{-1} b$, tương đương dạng chuẩn $c_1 c_1 c_2 c_2$).

### 2. Quy tắc ghi nhớ

- Gắn thêm một **tay cầm** (tổng liên thông với $T^2$) giữ nguyên tính định hướng được, tăng giống $g$ thêm $1$ và giảm $\chi$ đi $2$.
- Gắn thêm một **cross-cap** (tổng liên thông với $\mathbb{R}P^2$) làm mặt trở nên không định hướng được và giảm $\chi$ đi $1$.
- Mặt cầu $S^2$ có $\chi = 2$ là giá trị lớn nhất có thể của đặc trưng Euler trên các mặt đóng liên thông.

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **Leonhard Euler** – *"Solutio problematis ad geometriam situs pertinentis"* (1736)  
   *Bài toán bảy cây cầu Königsberg và khởi nguồn tô-pô tổ hợp.*

2. **August Möbius** – Phát hiện dải Möbius (1858)

3. **Felix Klein** – Chai Klein (1882)

4. **Max Dehn & Poul Heegaard** – Chứng minh Định lý phân loại mặt (1907)

### Giáo trình

5. **James R. Munkres** – *Topology*, 2nd Ed., **§76: Surfaces (Appendix)**

6. **William Massey** – *A Basic Course in Algebraic Topology*, **Chapter 1**

7. **Allen Hatcher** – *Algebraic Topology*, **§2.2: Surfaces**

8. **M. A. Armstrong** – *Basic Topology*, **Chapter 6**

9. **John M. Lee** – *Introduction to Topological Manifolds*, **Chapter 6**

---

## 🔗 Ứng dụng và liên kết

### Hình học vi phân – Định lý Gauss–Bonnet
Với mặt trơn đóng $S$ và độ cong Gauss $K$, ta có $\iint_S K\,dA = 2\pi \chi(S)$, liên kết trực tiếp đại lượng hình học địa phương ($K$) với bất biến tô-pô toàn cục ($\chi$).

### Tô-pô đại số – Đồng điều
Với mặt đóng định hướng được giống $g$: $H_0(S) \cong \mathbb{Z}$, $H_1(S) \cong \mathbb{Z}^{2g}$, $H_2(S) \cong \mathbb{Z}$; tổng đan dấu các số Betti cho lại $\chi(S) = 1 - 2g + 1 = 2 - 2g$.

### Vật lý – Lý thuyết dây
Mặt thế giới (worldsheet) do dây quét ra trong không-thời gian là các mặt Riemann được phân loại theo giống $g$, tương ứng với các bậc nhiễu loạn.

### Sinh học – Cuộn gập protein
Các bất biến tô-pô mặt và nút được dùng để phân tích cấu trúc cuộn gập phức tạp của chuỗi polypeptide.

### Đồ họa máy tính
Giống $g$ và đặc trưng Euler $\chi$ là các thông số cơ bản để kiểm tra tính hợp lệ và phân tích tô-pô của lưới bề mặt 3D.

---

## Video tham khảo

- **xem trước** [What is...the classification of surfaces?](https://www.youtube.com/watch?v=p1hyQpDk3lw) — VisualMath, tiếng Anh. Phát biểu trực quan định lý phân loại mặt: mặt cầu, tổng liên thông các hình xuyến và mặt phẳng xạ ảnh.
- [Classification Theorem 04 Torus & Klein Bottle](https://www.youtube.com/watch?v=OAILb52PkN0) — Sarah Brewer (mathémartiste), tiếng Anh. Phân tích hình xuyến và chai Klein trong chuỗi bài về phân loại mặt.
- [Klein Bottles - Numberphile](https://www.youtube.com/watch?v=AAsICMPwGPY) — Numberphile, tiếng Anh. Minh họa trực quan chai Klein trước khi quay lại đặc trưng Euler và tính định hướng.

## 🧩 Bài tập

### Mặt

1. **Kiểm tra định nghĩa mặt:**  
   Kiểm tra $S^2$ là không gian Euclid địa phương chiều $2$ tại cực bắc.

2. **Bản đồ địa phương trên hình xuyến:**  
   Mô tả một bản đồ tọa độ địa phương tại một điểm bất kỳ của $T^2$.

3. **Tổng liên thông:**  
   Mô tả tường minh cách dựng $T^2 \# T^2$ và giải thích vì sao kết quả là mặt compact.

### Tính định hướng được

4. **Kiểm tra tính định hướng của $S^2$:**  
   Giải thích trực quan vì sao $S^2$ định hướng được bằng hình ảnh dịch chuyển khung định hướng.

5. **Dải Möbius:**  
   Theo dõi một khung định hướng đi một vòng quanh dải Möbius để thấy hướng bị đảo ngược.

6. **Chai Klein:**  
   Chỉ ra một dải Möbius nằm bên trong chai Klein $K$ để kết luận $K$ không định hướng được.

### Đặc trưng Euler

7. **Tính $\chi$ của hình lập phương:**  
   Với bề mặt hình lập phương ($V = 8, E = 12, F = 6$), tính $\chi$.

8. **Phân tam giác hình xuyến:**  
   Xây dựng một phép phân tam giác của $T^2$ với $V = 9, E = 27, F = 18$ và kiểm tra $\chi = 0$.

9. **Mặt giống $2$:**  
   Kiểm tra $\chi(\Sigma_2) = -2$ từ công thức $\chi = 2 - 2g$.

### Phân loại mặt

10. **Nhận diện mặt:**  
    Một mặt đóng liên thông định hướng được có $\chi = 0$ là mặt nào?

11. **Mặt không định hướng được:**  
    Một mặt đóng liên thông không định hướng được có $\chi = 1$ là mặt nào?

12. **Tìm giống $g$:**  
    Một mặt đóng liên thông định hướng được có $\chi = -4$ thì giống $g$ bằng bao nhiêu?

### Đa giác cơ bản

13. **Hình vuông thành hình xuyến:**  
    Vẽ hình vuông với nhãn cạnh $a, b, a^{-1}, b^{-1}$ và minh họa các bước dán thành $T^2$.

14. **Mặt phẳng xạ ảnh:**  
    Vẽ miền cơ bản của $\mathbb{R}P^2$ từ đĩa đóng có biên đồng nhất đối cực.

15. **Đa giác của chai Klein:**  
    Vẽ hình vuông kèm nhãn dán cạnh tương ứng với chai Klein.

### Định lý Gauss–Bonnet

16. **Độ cong mặt cầu:**  
    Mặt cầu đơn vị $S^2$ có độ cong Gauss không đổi $K = 1$. Tính $\iint_{S^2} K\,dA$ và kiểm tra giá trị này bằng $2\pi\chi(S^2) = 4\pi$.

17. **Hình xuyến phẳng:**  
    Hình xuyến phẳng (trong $\mathbb{R}^4$) có $K = 0$ tại mọi điểm. Kiểm tra $\iint_{T^2} K\,dA = 0 = 2\pi\chi(T^2)$.

18. **Mặt hyperbolic:**  
    Mặt giống $2$ có $\chi = -2 < 0$, phù hợp với việc nó thừa nhận metric có độ cong hằng âm $K = -1$.

### Nâng cao

19. **Phủ hai lá định hướng được:**  
    Mọi mặt không định hướng được đều có một phủ hai lá định hướng được. Lấy ví dụ ánh xạ phủ $S^2 \to \mathbb{R}P^2$.

20. **Chứng minh Định lý phân loại:**  
    Tìm hiểu và tóm tắt các bước chính trong chứng minh Định lý phân loại các mặt compact.

---

## 📚 Đọc thêm

- **Hatcher, Algebraic Topology:** §2.2 (Phân loại mặt)
- **Massey, Basic Course:** Chapter 1 (Chứng minh chi tiết)
- **Armstrong, Basic Topology:** Chapter 6 (Phác thảo chứng minh)
- **Stillwell:** *Classical Topology and Combinatorial Group Theory* (Góc nhìn lịch sử)

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu Định lý phân loại các mặt đóng liên thông. Mỗi mặt là một 2-đa tạp Hausdorff, thỏa mãn tiên đề đếm được thứ hai. Hai bất biến tô-pô — đặc trưng Euler $\chi = V - E + F$ và tính định hướng được — hoàn toàn phân biệt mọi mặt đóng liên thông sai khác phép đồng phôi: họ định hướng được gồm $S^2$ và các mặt $\Sigma_g$ ($\chi = 2 - 2g$, $g \ge 0$), còn họ không định hướng được gồm $(\mathbb{R}P^2)^{\#k}$ ($\chi = 2 - k$, $k \ge 1$).

**Tiếp theo:** Lecture 05.02 về **Phức CW (CW Complexes)** — khung xây dựng không gian tô-pô tổng quát cho mọi số chiều.

---

*"The classification of surfaces: topology's perfect jewel."*

---

**Previous:** [Lecture 05.00: Quotient Topology](/contents/vi/topology-chapter05/05_00_Quotient_Topology_Construction/)  
**Next:** [Lecture 05.02: CW Complexes](/contents/vi/topology-chapter05/05_02_CW_Complexes/)
