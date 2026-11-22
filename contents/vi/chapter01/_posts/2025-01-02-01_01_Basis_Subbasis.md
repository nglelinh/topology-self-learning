---
layout: post
title: "Lecture 01.01: Basis and Subbasis for a Topology"
lang: vi
lang-ref: lecture-01-01
chapter: 1
lecture: 1
categories: [chapter01]
tags: [basis, subbasis, generated-topology, standard-basis]
description: "Basis và subbasis cho topology, cách sinh topology từ họ tập hợp đơn giản"
---

**Cơ sở và Tiền cơ sở của một Tô-pô**

---

## 📖 Tổng quan

Ở bài trước, ta định nghĩa tô-pô là một họ các tập mở thỏa mãn ba tiên đề. Tuy nhiên, trên các không gian lớn như $\mathbb{R}$, việc liệt kê toàn bộ các tập mở hay kiểm tra trực tiếp ba tiên đề thường rất cồng kềnh.

Tương tự như trong đại số tuyến tính — nơi một không gian vector được sinh bởi một cơ sở — một tô-pô cũng có thể được xác định gọn gàng bằng một họ nhỏ hơn gọi là **cơ sở** (*basis*). Chẳng hạn, trên $\mathbb{R}$ với tô-pô Euclid, thay vì mô tả mọi tập mở, ta chỉ cần xét họ các khoảng mở $(a, b)$: mọi tập mở khác đều là hợp của các khoảng mở như vậy.

Bài giảng này trình bày các nội dung chính: định nghĩa và tiêu chuẩn nhận biết **cơ sở**, **cơ sở chuẩn** của $\mathbb{R}^n$, cách **so sánh hai cơ sở**, khái niệm **tiền cơ sở** (*subbasis*) và **tô-pô sinh bởi một họ tập hợp**, cùng **cơ sở lân cận** tại một điểm.

**Tại sao bài này quan trọng?** Cơ sở giúp định nghĩa tô-pô, so sánh hai tô-pô và kiểm tra tính liên tục của ánh xạ đơn giản hơn nhiều; ngoài ra, tô-pô tích và tô-pô thứ tự đều được xây dựng trực tiếp qua cơ sở hoặc tiền cơ sở.

---

## 🎯 Từ trực giác đến hình thức

### Ý tưởng các khối ghép cơ bản

Có thể hình dung cơ sở của một tô-pô giống như các mảnh ghép LEGO cơ bản: ta không cần chuẩn bị sẵn mọi mô hình phức tạp, mà chỉ cần một tập hợp mảnh ghép chuẩn rồi ghép chúng lại với nhau. Trong tô-pô, các phần tử cơ sở (như các khoảng mở $(a, b)$ trong $\mathbb{R}$) là những mảnh ghép cơ bản, còn mọi tập mở bất kỳ đều thu được bằng phép lấy hợp. Chẳng hạn, tập mở $U = (0, 1) \cup (2, 5) \cup (7, 10)$ đơn giản là hợp của ba phần tử cơ sở $(0, 1)$, $(2, 5)$ và $(7, 10)$.

![LEGO analogy for basis](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Lego_Color_Bricks.jpg/400px-Lego_Color_Bricks.jpg)  
*Các mảnh ghép LEGO minh họa cho phần tử cơ sở - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Lego_Color_Bricks.jpg)*

---

## 📐 Định nghĩa hình thức

### 1. Cơ sở của một tô-pô (Basis for a Topology)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Cơ sở — Basis):**  
Cho $(X, \tau)$ là một không gian tô-pô. Một họ $\mathcal{B} \subseteq \tau$ được gọi là **cơ sở** (*basis*) cho $\tau$ nếu mọi tập mở đều viết được dưới dạng hợp các phần tử của $\mathcal{B}$:

$$
\forall U \in \tau: U = \bigcup_{\alpha \in I} B_\alpha \quad \text{với } B_\alpha \in \mathcal{B}
$$
</div>

*(Quy ước hợp của họ rỗng là $\emptyset$.)*

**Phát biểu tương đương:** Họ $\mathcal{B} \subseteq \tau$ là cơ sở cho $\tau$ khi và chỉ khi với mọi $U \in \tau$ và mọi $x \in U$, tồn tại $B \in \mathcal{B}$ sao cho $x \in B \subseteq U$.

**Ví dụ 1: Cơ sở chuẩn trên $\mathbb{R}$**
$$
\mathcal{B} = \{(a, b) : a, b \in \mathbb{R}, a < b\}
$$
Mọi tập mở trong tô-pô Euclid trên $\mathbb{R}$ đều là hợp của các khoảng mở dạng này.

**Ví dụ 2: Cơ sở với đầu mút hữu tỉ trên $\mathbb{R}$**
$$
\mathcal{B}' = \{(a, b) : a, b \in \mathbb{Q}, a < b\}
$$
Họ $\mathcal{B}'$ cũng là một cơ sở cho tô-pô Euclid trên $\mathbb{R}$, vì nhờ tính trù mật của $\mathbb{Q}$ trong $\mathbb{R}$, mọi khoảng mở $(a, b)$ đều là hợp của các khoảng mở $(r, s)$ với $r, s \in \mathbb{Q}$. Điều này cho thấy một tô-pô có thể có nhiều cơ sở khác nhau.

---

### 2. Tiêu chuẩn cơ sở (Basis Criterion)

Khi nào một họ tập con $\mathcal{B}$ của $X$ có thể làm cơ sở cho một tô-pô nào đó trên $X$?

<div class="textbook-theorem" markdown="1">
**Định lý (Tiêu chuẩn cơ sở):**  
Một họ $\mathcal{B}$ các tập con của $X$ là cơ sở cho một tô-pô trên $X$ khi và chỉ khi nó thỏa mãn hai điều kiện:
</div>

**(B1) Phủ toàn bộ $X$:**
$$
X = \bigcup_{B \in \mathcal{B}} B
$$

**(B2) Tính chất giao:**
$$
\forall B_1, B_2 \in \mathcal{B}, \forall x \in B_1 \cap B_2: \exists B_3 \in \mathcal{B}: x \in B_3 \subseteq B_1 \cap B_2
$$

Về trực giác, (B2) bảo đảm rằng quanh mỗi điểm nằm trong phần giao của hai phần tử cơ sở luôn có một phần tử cơ sở nhỏ hơn nằm trọn trong phần giao đó.

![Basis intersection property](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Basis_for_a_Topology_%28Illustration%29.svg/500px-Basis_for_a_Topology_%28Illustration%29.svg.png)  
*Tính chất giao của cơ sở - Nguồn minh họa khái niệm*

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:**
</div>

**Chiều thuận ($\Rightarrow$):** Nếu $\mathcal{B}$ là cơ sở cho $\tau$, thì vì $X \in \tau$ nên $X$ là hợp các phần tử của $\mathcal{B}$ (suy ra B1); hơn nữa với mọi $B_1, B_2 \in \mathcal{B}$, ta có $B_1 \cap B_2 \in \tau$, nên $B_1 \cap B_2$ là hợp của các phần tử thuộc $\mathcal{B}$ (suy ra B2).

**Chiều đảo ($\Leftarrow$):** Giả sử $\mathcal{B}$ thỏa (B1) và (B2). Ta định nghĩa:
$$
\tau = \left\{U \subseteq X : U = \bigcup_{\alpha} B_\alpha, B_\alpha \in \mathcal{B}\right\}
$$
(bao gồm $\emptyset$ như hợp rỗng). Việc kiểm tra $\tau$ thỏa mãn ba tiên đề tô-pô là bài tập cơ bản.

**Ví dụ áp dụng:** Xét họ $\mathcal{B} = \{[a, b) : a < b\}$ trên $\mathbb{R}$.
- (B1): $\mathbb{R} = \bigcup_{n \in \mathbb{Z}} [n, n+1)$, thỏa mãn.
- (B2): $[a, b) \cap [c, d) = [\max(a, c), \min(b, d))$; nếu giao khác rỗng thì chính nó thuộc $\mathcal{B}$.

Do đó $\mathcal{B}$ sinh ra một tô-pô trên $\mathbb{R}$, gọi là **tô-pô giới hạn dưới** (*lower limit topology* hay *tô-pô Sorgenfrey*), khác với tô-pô Euclid.

---

### 3. So sánh hai cơ sở (Comparing Bases)

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Hai cơ sở $\mathcal{B}$ và $\mathcal{B}'$ sinh ra cùng một tô-pô trên $X$ khi và chỉ khi:
- $\forall B \in \mathcal{B}, \forall x \in B: \exists B' \in \mathcal{B}': x \in B' \subseteq B$; và
- $\forall B' \in \mathcal{B}', \forall x \in B': \exists B \in \mathcal{B}: x \in B \subseteq B'$.
</div>

Áp dụng định lý này cho $\mathcal{B} = \{(a, b) : a, b \in \mathbb{R}\}$ và $\mathcal{B}' = \{(a, b) : a, b \in \mathbb{Q}\}$, ta thấy hai cơ sở này sinh cùng tô-pô Euclid trên $\mathbb{R}$. Vì $\mathcal{B}'$ đếm được, ta suy ra $\mathbb{R}$ thỏa mãn **tiên đề đếm được thứ hai** (*second countable*).

---

### 4. Cơ sở chuẩn cho $\mathbb{R}^n$

<div class="textbook-definition" markdown="1">
**Định nghĩa (Cơ sở chuẩn cho $\mathbb{R}^n$):**

$$
\mathcal{B} = \{(a_1, b_1) \times (a_2, b_2) \times \cdots \times (a_n, b_n) : a_i < b_i\}
$$
</div>

Đây là họ tất cả các hình hộp mở (*open boxes*). Chẳng hạn trong $\mathbb{R}^2$, mỗi phần tử cơ sở là một hình chữ nhật mở $(a_1, b_1) \times (a_2, b_2) = \{(x, y) : a_1 < x < b_1, \; a_2 < y < b_2\}$.

![Open rectangle in R2](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2d/Open_rectangle.svg/300px-Open_rectangle.svg.png)  
*Hình chữ nhật mở là phần tử cơ sở trong $\mathbb{R}^2$ - Nguồn minh họa khái niệm*

Đĩa mở $B((0, 0), 1) = \{(x, y) : x^2 + y^2 < 1\}$ trong $\mathbb{R}^2$ không phải là hình chữ nhật mở, nhưng vẫn là tập mở vì nó là hợp của tất cả các hình chữ nhật mở nằm bên trong nó:
$$
B((0,0), 1) = \bigcup_{\text{rectangles } R \subseteq B((0,0),1)} R
$$

Ta cũng có thể dùng họ tất cả các hình cầu mở làm cơ sở thay thế:
$$
\mathcal{B}_{\text{balls}} = \{B(\mathbf{x}, r) : \mathbf{x} \in \mathbb{R}^n, r > 0\}
$$

<div class="textbook-theorem" markdown="1">
**Định lý:** $\mathcal{B}$ (các hình hộp mở) và $\mathcal{B}_{\text{balls}}$ (các hình cầu mở) sinh ra cùng một tô-pô trên $\mathbb{R}^n$ (tô-pô Euclid).
</div>

<div class="textbook-proof" markdown="1">
**Phác thảo chứng minh:**
- Quanh mỗi điểm thuộc một hình hộp mở đều có một hình cầu mở chứa trong hình hộp đó.
- Quanh mỗi điểm thuộc một hình cầu mở đều có một hình hộp mở chứa trong hình cầu đó.
- Áp dụng định lý so sánh hai cơ sở, suy ra hai tô-pô trùng nhau.
</div>

---

### 5. Tiền cơ sở (Subbasis)

Đôi khi ta muốn sinh một tô-pô từ một họ tập hợp còn nhỏ hơn cả cơ sở.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tiền cơ sở — Subbasis):**  
Một họ $\mathcal{S}$ các tập con của $X$ (thường yêu cầu $\bigcup_{S \in \mathcal{S}} S = X$, hoặc quy ước giao của họ rỗng là $X$) là **tiền cơ sở** (*subbasis*) cho tô-pô $\tau$ nếu họ tất cả các giao hữu hạn phần tử của $\mathcal{S}$:

$$
\mathcal{B} = \left\{\bigcap_{i=1}^n S_i : S_i \in \mathcal{S}, n \in \mathbb{N}\right\}
$$
</div>
(cùng với $X$ theo quy ước giao rỗng nếu cần) tạo thành một cơ sở cho $\tau$.

Tóm lại, quy trình sinh tô-pô từ tiền cơ sở gồm hai bước:
- **Tiền cơ sở** $\xrightarrow{\text{lấy giao hữu hạn}}$ **Cơ sở** $\xrightarrow{\text{lấy hợp tùy ý}}$ **Tô-pô**.

**Ví dụ 1: Tiền cơ sở chuẩn trên $\mathbb{R}$**
$$
\mathcal{S} = \{(a, \infty) : a \in \mathbb{R}\} \cup \{(-\infty, b) : b \in \mathbb{R}\}
$$
Giao của một tia phải và một tia trái cho $(a, \infty) \cap (-\infty, b) = (a, b)$ (khi $a < b$), còn giao của hai tia cùng chiều vẫn là một tia. Do đó cơ sở sinh ra chứa mọi khoảng mở $(a, b)$ và sinh đúng tô-pô Euclid trên $\mathbb{R}$.

**Ví dụ 2: Tô-pô tích (gợi mở)**  
Cho $(X, \tau_X)$ và $(Y, \tau_Y)$. Trên $X \times Y$, họ
$$
\mathcal{S} = \{U \times Y : U \in \tau_X\} \cup \{X \times V : V \in \tau_Y\}
$$
là một tiền cơ sở sinh ra **tô-pô tích** trên $X \times Y$ (vì $(U \times Y) \cap (X \times V) = U \times V$). Tiền cơ sở đặc biệt gọn gàng khi xây dựng tô-pô thứ tự và tô-pô tích vô hạn.

---

### 6. Tô-pô sinh bởi một họ tập hợp (Generated Topology)

<div class="textbook-theorem" markdown="1">
**Định lý (Sự tồn tại của tô-pô sinh):**  
Cho $\mathcal{S}$ là một họ tùy ý các tập con của $X$. Tồn tại **duy nhất** một tô-pô $\tau$ trên $X$ sao cho:
1. $\mathcal{S} \subseteq \tau$ (mọi phần tử của $\mathcal{S}$ đều mở).
2. $\tau$ là tô-pô **thô nhất** thỏa mãn (1).
</div>

Ký hiệu: $\tau = \langle \mathcal{S} \rangle$. Tô-pô này có thể mô tả tường minh (với quy ước giao rỗng bằng $X$ và hợp rỗng bằng $\emptyset$):
$$
\tau = \left\{U \subseteq X : U = \bigcup_{\alpha} \left(\bigcap_{i=1}^{n_\alpha} S_{\alpha,i}\right), S_{\alpha,i} \in \mathcal{S}\right\}
$$

**Ví dụ:** Trên $\mathbb{R}$, xét $\mathcal{S} = \{(0, 1), (0{,}5, 1{,}5)\}$. Tô-pô sinh bởi $\mathcal{S}$ gồm $\emptyset$, $\mathbb{R}$, hai tập trong $\mathcal{S}$, phần giao $(0{,}5, 1)$ và hợp $(0, 1{,}5)$ — nhỏ hơn rất nhiều so với tô-pô Euclid.

---

### 7. Cơ sở lân cận (Neighborhood Basis)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Lân cận — Neighborhood):**  
Tập $N \subseteq X$ là một **lân cận** của điểm $x$ nếu tồn tại tập mở $U \in \tau$ sao cho $x \in U \subseteq N$.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Cơ sở lân cận — Neighborhood Basis):**  
Họ $\mathcal{B}_x$ gồm các lân cận của $x$ là một **cơ sở lân cận** tại $x$ nếu:

$$
\forall N \text{ neighborhood của } x: \exists B \in \mathcal{B}_x: B \subseteq N
$$
</div>

**Ví dụ trong $\mathbb{R}$:** Họ các khoảng mở thu nhỏ quanh $x$:
$$
\mathcal{B}_x = \{(x - 1/n, x + 1/n) : n \in \mathbb{N}\}
$$
là một cơ sở lân cận đếm được tại $x$.

**Ứng dụng:** Cơ sở lân cận giúp phát biểu gọn các tính chất cục bộ:
- Dãy $x_n \to x$ khi và chỉ khi với mọi $B \in \mathcal{B}_x$, tồn tại $N$ sao cho $\forall n \ge N: x_n \in B$.
- Ánh xạ $f$ liên tục tại $x$ khi và chỉ khi với mọi lân cận của $f(x)$, nghịch ảnh của nó chứa một phần tử thuộc $\mathcal{B}_x$.

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Đưa ra định nghĩa cơ sở lân cận.*

2. **Pavel Alexandroff & Heinz Hopf** - *"Topologie I"* (1935)  
   *Trình bày có hệ thống về cơ sở và tiền cơ sở.*

3. **Nicolas Bourbaki** - *"Éléments de mathématique: Topologie générale"* (1940)  
   *Cách tiếp cận tiên đề hóa hiện đại qua cơ sở và bộ lọc.*

### Giáo trình

4. **James R. Munkres** - *Topology*, 2nd Ed., **§13: Basis for a Topology**  
   *Trình bày rõ ràng kèm nhiều ví dụ.*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 2, §2.2**  
   *Nhập môn dễ theo dõi về cơ sở.*

6. **Stephen Willard** - *General Topology*, **Chapter 2**  
   *Trình bày đầy đủ, chặt chẽ.*

7. **John L. Kelley** - *General Topology*, **Chapter 2**  
   *Cách tiếp cận qua lưới và bộ lọc.*

---

## 🔗 Ứng dụng và liên hệ

### Khoa học máy tính — Cấu trúc dữ liệu không gian
Trong cơ sở dữ liệu địa lý, cây R-tree dùng các hình chữ nhật bao (*bounding rectangles*) — tương tự các phần tử cơ sở dạng hình hộp trong $\mathbb{R}^n$ — để lập chỉ mục và truy vấn nhanh các đối tượng lân cận (chẳng hạn trong hệ thống bản đồ số).

### Giải tích — Không gian vector định chuẩn
Trong giải tích hàm, tô-pô của không gian định chuẩn được xác định từ cơ sở các hình cầu mở; các kiểm tra về hội tụ và liên tục đều quy về cơ sở này.

### Hình học vi phân — Bản đồ tọa độ và át-lát
Một đa tạp được mô tả bởi họ các bản đồ tọa độ (*charts*) phủ toàn không gian cùng điều kiện tương thích trên phần giao — cấu trúc rất gần với hai điều kiện cơ sở.

### Vật lý — Không gian pha
Trong cơ học cổ điển, các vùng nhỏ trong không gian vị trí–động lượng đóng vai trò phần tử cơ sở cho tô-pô tự nhiên của không gian pha.

---

## Video tham khảo

- **xem trước** [[TÔPÔ ĐẠI CƯƠNG] Bài 2. Cơ sở của một tô pô (phần 1)](https://www.youtube.com/watch?v=j4qUKcuf-uA) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Cơ sở của một tô-pô, phần 1, sát định nghĩa bài đang xây.
- [[TÔ PÔ ĐẠI CƯƠNG] Bài 2. Cơ sở của một tô pô (phần 2)](https://www.youtube.com/watch?v=y_Eqq1QKyXM) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Phần 2 của cùng bài giảng, dùng khi cơ sở đã có và ta sinh ra tô-pô.
- [Topology Lecture 08: Basis for a Topology](https://www.youtube.com/watch?v=dUfNktEkwPo) — Marius Furter, tiếng Anh. Một lối tiếng Anh chậm, có ví dụ, cho hai điều kiện của cơ sở.

## 🧩 Bài tập

### Hiểu về cơ sở

1. **Kiểm tra tiêu chuẩn cơ sở:**  
   Cho $X = \{a, b, c, d\}$. Các họ sau có phải là cơ sở cho một tô-pô trên $X$ không?
   - a) $\mathcal{B} =$ {% raw %}{{a}, {b}, {c,d}, X}{% endraw %}
   - b) $\mathcal{B} =$ {% raw %}{{a,b}, {b,c}, {c,d}}{% endraw %}
   - c) $\mathcal{B} =$ {% raw %}{{a}, {a,b}, {a,b,c}, X}{% endraw %}

2. **Sinh tô-pô từ cơ sở:**  
   Với $X = \{1, 2, 3\}$ và $\mathcal{B} =$ {% raw %}{{1}, {2,3}}{% endraw %}, hãy liệt kê tất cả các tập mở trong tô-pô sinh bởi $\mathcal{B}$.

3. **Cơ sở chuẩn trên $\mathbb{R}$:**  
   Chứng minh họ $\mathcal{B} = \{(a, b) : a, b \in \mathbb{R}, a < b\}$ thỏa mãn tiêu chuẩn cơ sở (B1) và (B2).

### So sánh các cơ sở

4. **Có sinh cùng tô-pô không?**  
   Trên $\mathbb{R}$, xét hai cơ sở:
   - $\mathcal{B}_1 = \{(a, b) : a < b\}$
   - $\mathcal{B}_2 = \{[a, b) : a < b\}$
   
   Chúng có sinh cùng một tô-pô không? Giải thích lý do.

5. **Đầu mút hữu tỉ:**  
   Chứng minh $\mathcal{B} = \{(r, s) : r, s \in \mathbb{Q}, r < s\}$ là cơ sở cho tô-pô Euclid trên $\mathbb{R}$. (*Gợi ý:* Dùng tính trù mật của $\mathbb{Q}$.)

6. **Cơ sở đếm được:**  
   Chứng minh $\mathbb{R}$ với tô-pô Euclid có một cơ sở đếm được. Điều này nói lên điều gì về "độ lớn" của tô-pô này?

### Không gian $\mathbb{R}^n$ và không gian tích

7. **Hình chữ nhật mở:**  
   Trong $\mathbb{R}^2$, vẽ các tập sau:
   - a) $(0, 1) \times (0, 1)$
   - b) $(-1, 2) \times (0, 3)$
   - c) Phần giao của (a) và (b)
   
   Phần giao đó có phải là một phần tử cơ sở không?

8. **Đĩa mở trong $\mathbb{R}^2$:**  
   Đĩa mở $B((0, 0), 1)$ không phải là một hình chữ nhật mở. Chứng minh nó vẫn là tập mở bằng cách biểu diễn nó như hợp của các hình chữ nhật mở.

9. **Các mê-tric khác nhau:**  
   Trong $\mathbb{R}^2$ với mê-tric Manhattan $d_1(x, y) = |x_1 - y_1| + |x_2 - y_2|$:
   - a) Vẽ hình cầu mở $B((0, 0), 1)$ theo mê-tric này.
   - b) Nó có phải là hình chữ nhật mở có cạnh song song trục tọa độ không?
   - c) Tô-pô cảm sinh có trùng với tô-pô Euclid không?

### Tiền cơ sở

10. **Tiền cơ sở gồm các tia:**  
    Trên $\mathbb{R}$, xét $\mathcal{S} = \{(a, \infty) : a \in \mathbb{R}\} \cup \{(-\infty, b) : b \in \mathbb{R}\}$.
    - a) Chứng minh $\mathcal{S}$ là tiền cơ sở cho tô-pô Euclid.
    - b) Mô tả cơ sở sinh từ $\mathcal{S}$.
    - c) So sánh với cơ sở chuẩn của $\mathbb{R}$.

11. **Tiền cơ sở trên tập hữu hạn:**  
    Cho $X = \{a, b, c\}$ và $\mathcal{S} =$ {% raw %}{{a,b}, {b,c}}{% endraw %}.
    - a) Tìm cơ sở sinh từ $\mathcal{S}$.
    - b) Liệt kê tất cả các tập mở trong tô-pô sinh ra.
    - c) Nhận xét về tính chất tách của tô-pô này.

12. **Gợi mở về tô-pô tích:**  
    Trên $\mathbb{R} \times \mathbb{R}$, xét tiền cơ sở $\mathcal{S} = \{(a, b) \times \mathbb{R} : a < b\} \cup \{\mathbb{R} \times (c, d) : c < d\}$. Chứng minh cơ sở sinh ra cho cùng tô-pô với cơ sở chuẩn của $\mathbb{R}^2$.

### Nâng cao

13. **Tô-pô giới hạn dưới (Sorgenfrey):**  
    Gọi $\tau_\ell$ là tô-pô sinh bởi $\mathcal{B} = \{[a, b) : a < b\}$ trên $\mathbb{R}$.
    - a) Chứng minh $[0, 1)$ mở trong $\tau_\ell$.
    - b) $(0, 1)$ có mở trong $\tau_\ell$ không?
    - c) So sánh $\tau_\ell$ với tô-pô Euclid $\tau_E$.

14. **So sánh tô-pô từ bao hàm cơ sở:**  
    Chứng minh: nếu $\mathcal{B}_1 \subseteq \mathcal{B}_2$ (cả hai đều là cơ sở trên $X$), thì tô-pô sinh bởi $\mathcal{B}_2$ mịn hơn tô-pô sinh bởi $\mathcal{B}_1$.

15. **Cơ sở lân cận trong không gian mê-tric:**  
    Trong không gian mê-tric $(X, d)$, chứng minh rằng:
    $$
    \mathcal{B}_x = \{B(x, 1/n) : n \in \mathbb{N}\}
    $$
    là một cơ sở lân cận tại $x$.

16. **Đặc trưng hóa tô-pô bằng cơ sở lân cận:**  
    Chứng minh tô-pô $\tau$ được xác định hoàn toàn bởi họ các cơ sở lân cận tại mọi điểm. (*Gợi ý:* $U$ mở $\iff U$ là lân cận của mọi $x \in U$.)

### Câu hỏi suy ngẫm

17. **Vì sao chỉ lấy giao hữu hạn?**  
    Trong định nghĩa tiền cơ sở, tại sao chỉ lấy giao **hữu hạn** các phần tử? Điều gì sẽ xảy ra nếu lấy giao vô hạn?

18. **Cơ sở tô-pô và cơ sở không gian vector:**  
    So sánh khái niệm "cơ sở" trong tô-pô với "cơ sở" trong đại số tuyến tính. Điểm giống nhau là cả hai đều sinh ra toàn bộ cấu trúc; vậy điều kiện độc lập tuyến tính có khái niệm tương đương trong tô-pô không?

19. **Cơ sở tối tiểu:**  
    Một tô-pô có nhất thiết tồn tại cơ sở nhỏ nhất (theo nghĩa bao hàm) không? Hãy liên hệ với trường hợp tô-pô Euclid trên $\mathbb{R}$.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §13 (Basis for a Topology), §15 (Product Topology)
- **Morris, Topology Without Tears:** Chapter 2.2–2.3 (Bases)
- **Willard, General Topology:** Chapter 2 (Bases and Subbases)
- **Dugundji, Topology:** Chapter II.2 (Bases and Subbases)

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã học các công cụ giúp làm việc với tô-pô gọn gàng hơn:

✅ **Cơ sở (Basis):** Họ tập mở mà mọi tập mở khác đều là hợp của chúng.  
✅ **Tiêu chuẩn cơ sở:** Điều kiện phủ (B1) và tính chất giao (B2).  
✅ **Cơ sở chuẩn của $\mathbb{R}^n$:** Các hình hộp mở (tương đương với các hình cầu mở).  
✅ **So sánh cơ sở:** Tiêu chuẩn để hai cơ sở sinh ra cùng một tô-pô.  
✅ **Tiền cơ sở (Subbasis):** Sinh ra cơ sở qua giao hữu hạn, rồi sinh tô-pô qua hợp tùy ý.  
✅ **Cơ sở lân cận:** Phiên bản cục bộ của cơ sở tại từng điểm.

**Điểm chính:**
- Một tô-pô có thể có nhiều cơ sở khác nhau.
- Khi định nghĩa tô-pô mới, so sánh hai tô-pô hoặc kiểm tra tính liên tục, làm việc trực tiếp trên cơ sở thường đơn giản hơn nhiều.
- $\mathbb{R}^n$ có cơ sở đếm được nên thỏa mãn tiên đề đếm được thứ hai.

**Tiếp theo:** Trong Bài 01.02, ta sẽ nghiên cứu **Tập đóng, Bao đóng và Phần trong** — các khái niệm đối ngẫu của tập mở và những toán tử cốt lõi trong tô-pô.

---

*"A basis is to topology what a basis is to a vector space—it spans the structure."* — Topology wisdom

🎯 **Hãy thực hành kiểm tra và so sánh nhiều cơ sở khác nhau để nắm chắc công cụ này.** 🎯

---

**Previous:** [Lecture 01.00: Definition of Topology](/contents/vi/topology-chapter01/01_00_Definition_Topology_Basic_Examples/)  
**Next:** [Lecture 01.02: Closed Sets, Closure, and Interior](/contents/vi/topology-chapter01/01_02_Closed_Sets_Closure_Interior/)
