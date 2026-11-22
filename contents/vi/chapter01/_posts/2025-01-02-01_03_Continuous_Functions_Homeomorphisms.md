---
layout: post
title: "Lecture 01.03: Continuous Functions and Homeomorphisms"
lang: vi
lang-ref: lecture-01-03
chapter: 1
lecture: 3
categories: [chapter01]
tags: [continuous-functions, homeomorphisms, topological-equivalence]
description: "Hàm liên tục trong topology, các đặc trưng tương đương, và homeomorphisms"
---

**Ánh xạ liên tục và Phép đồng phôi**

---

## 📖 Tổng quan

Sau khi định nghĩa không gian tô-pô, câu hỏi tự nhiên tiếp theo là: **làm thế nào để so sánh hai không gian tô-pô với nhau?** Trong đại số tuyến tính ta dùng ánh xạ tuyến tính, trong lý thuyết nhóm ta dùng đồng cấu nhóm; tương tự, trong tô-pô công cụ bảo toàn cấu trúc là **ánh xạ liên tục** (*continuous function*).

Định nghĩa $\varepsilon$-$\delta$ quen thuộc trong giải tích phụ thuộc vào khoảng cách mê-tric nên không áp dụng trực tiếp được cho không gian tô-pô tổng quát. Tuy nhiên, tính liên tục có thể phát biểu hoàn toàn bằng ngôn ngữ tập mở:

$$
f: X \to Y \text{ continuous} \iff \text{preimage của mọi open set là open}
$$

Định nghĩa này không cần mê-tric, khớp hoàn toàn với định nghĩa $\varepsilon$-$\delta$ trong trường hợp không gian mê-tric, và là nền tảng cho mọi phần tiếp theo của môn học. Trong bài giảng này, ta sẽ trình bày định nghĩa ánh xạ liên tục, các đặc trưng tương đương (qua tập đóng, bao đóng, cơ sở), **phép đồng phôi** (*homeomorphism*), **tính chất tô-pô** (bất biến tô-pô), cùng hai khái niệm bổ trợ là phép nhúng và ánh xạ thương.

---

## 🎯 Từ trực giác đến hình thức

### Hình học tấm cao su

Tô-pô học thường được ví là "hình học tấm cao su" (*rubber sheet geometry*). Nếu hình dung các vật thể làm bằng cao su đàn hồi, ta được phép kéo giãn, uốn cong hoặc vặn xoắn, nhưng **không được** xé rách, cắt đứt hay dán các điểm tách rời lại với nhau. Hai hình biến đổi được cho nhau qua những phép biến dạng liên tục hai chiều như vậy được gọi là **đồng phôi** (*homeomorphic*).

![Mug to Torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)  
*Chiếc cốc có quai đồng phôi với hình xuyến (torus) - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif)*

Một số ví dụ kinh điển:
- Chiếc cốc có quai và hình xuyến (bánh donut) đồng phôi nhau vì đều có một lỗ xuyên qua.
- Mặt cầu $S^2$ không đồng phôi với hình xuyến $T^2$ vì không thể biến đổi qua lại mà không cắt hoặc dán.
- Hai đoạn đóng $[0, 1]$ và $[2, 5]$ đồng phôi nhau (chỉ khác tỉ lệ và vị trí).
- Đoạn đóng $[0, 1]$ không đồng phôi với khoảng mở $(0, 1)$.

Công cụ hình thức hóa trực giác này chính là **phép đồng phôi** — một song ánh liên tục có ánh xạ ngược cũng liên tục.

---

## 📐 Định nghĩa hình thức

### 1. Ánh xạ liên tục (Continuous Functions)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tính liên tục qua tập mở):**  
Cho $(X, \tau_X)$ và $(Y, \tau_Y)$ là hai không gian tô-pô. Ánh xạ $f: X \to Y$ được gọi là **liên tục** (*continuous*) nếu nghịch ảnh của mọi tập mở trong $Y$ là tập mở trong $X$:

$$
\forall V \in \tau_Y: f^{-1}(V) \in \tau_X
$$
</div>

Lưu ý rằng $f^{-1}(V) = \{x \in X : f(x) \in V\}$ là **nghịch ảnh** (*preimage*) của tập $V$, luôn xác định ngay cả khi $f$ không có ánh xạ ngược.

**Ví dụ cơ bản:**
1. **Ánh xạ đồng nhất:** $f: \mathbb{R} \to \mathbb{R}$, $f(x) = x$ (với cùng tô-pô Euclid) liên tục vì $f^{-1}(V) = V$.
2. **Ánh xạ hằng:** $f: X \to Y$, $f(x) = y_0$ luôn liên tục với mọi tô-pô trên $X$ và $Y$, vì $f^{-1}(V)$ bằng $X$ (nếu $y_0 \in V$) hoặc $\emptyset$ (nếu $y_0 \notin V$), và cả hai đều mở trong $X$.
3. **Ánh xạ bao hàm:** Với $A \subseteq X$ mang tô-pô con, ánh xạ $i: A \to X$, $i(a) = a$ liên tục vì $i^{-1}(V) = V \cap A \in \tau_A$.
4. **Ánh xạ chiếu:** $\pi_1: X \times Y \to X$, $\pi_1(x, y) = x$ liên tục đối với tô-pô tích.

---

### 2. Các đặc trưng tương đương của tính liên tục

<div class="textbook-theorem" markdown="1">
**Định lý (Các đặc trưng tương đương):**  
Với ánh xạ $f: X \to Y$, năm mệnh đề sau **tương đương**:

1. $f$ liên tục (nghịch ảnh của mọi tập mở là tập mở).
2. **Qua tập đóng:** Với mọi tập đóng $F \subseteq Y$, $f^{-1}(F)$ đóng trong $X$.
3. **Qua bao đóng:** Với mọi $A \subseteq X$, $f(\text{cl}_X(A)) \subseteq \text{cl}_Y(f(A))$.
4. **Qua phần trong:** Với mọi $B \subseteq Y$, $f^{-1}(\text{int}_Y(B)) \subseteq \text{int}_X(f^{-1}(B))$.
5. **Qua cơ sở:** Nếu $\mathcal{B}$ là một cơ sở của $\tau_Y$, thì $\forall B \in \mathcal{B}: f^{-1}(B) \in \tau_X$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh (các chiều chính):**
</div>

- **(1 $\Rightarrow$ 2):** Nếu $F \subseteq Y$ đóng thì $Y \setminus F$ mở, nên $f^{-1}(Y \setminus F) = X \setminus f^{-1}(F)$ mở, suy ra $f^{-1}(F)$ đóng.
- **(2 $\Rightarrow$ 1):** Lập luận tương tự bằng cách lấy phần bù của tập mở $V \subseteq Y$.
- **(1 $\Rightarrow$ 3):** Với $A \subseteq X$, ta có $f(A) \subseteq \text{cl}_Y(f(A))$, nên $A \subseteq f^{-1}(\text{cl}_Y(f(A)))$. Vì $\text{cl}_Y(f(A))$ đóng, theo (2) tập $f^{-1}(\text{cl}_Y(f(A)))$ cũng đóng và chứa $A$, do đó $\text{cl}_X(A) \subseteq f^{-1}(\text{cl}_Y(f(A)))$, tức $f(\text{cl}_X(A)) \subseteq \text{cl}_Y(f(A))$.
- **(5):** Suy từ tính chất nghịch ảnh bảo toàn phép hợp tùy ý (dành làm bài tập).

Trong thực hành, tiêu chuẩn (5) rất tiện lợi: để kiểm tra $f: \mathbb{R} \to \mathbb{R}$ liên tục, chỉ cần kiểm tra $f^{-1}((a, b))$ mở với mọi khoảng mở $(a, b)$.

---

### 3. Tính liên tục tại một điểm

<div class="textbook-definition" markdown="1">
**Định nghĩa (Liên tục tại điểm $x_0$):**  
Ánh xạ $f: X \to Y$ **liên tục tại $x_0 \in X$** nếu với mọi tập mở $V$ chứa $f(x_0)$, tồn tại tập mở $U$ chứa $x_0$ sao cho $f(U) \subseteq V$:

$$
\forall V \in \tau_Y, f(x_0) \in V: \exists U \in \tau_X, x_0 \in U: f(U) \subseteq V
$$
</div>

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Ánh xạ $f: X \to Y$ liên tục trên $X$ khi và chỉ khi $f$ liên tục tại mọi điểm $x \in X$.
</div>

Trong hai không gian mê-tric $(X, d_X)$ và $(Y, d_Y)$, điều kiện trên trùng khớp chính xác với định nghĩa $\varepsilon$-$\delta$ trong giải tích: $\forall \varepsilon > 0, \exists \delta > 0: d_X(x, x_0) < \delta \Rightarrow d_Y(f(x), f(x_0)) < \varepsilon$. Như vậy, tính liên tục tô-pô là sự tổng quát hóa tự nhiên của tính liên tục mê-tric.

---

### 4. Các tính chất của ánh xạ liên tục

<div class="textbook-theorem" markdown="1">
**Định lý (Hợp thành):**  
Nếu $f: X \to Y$ và $g: Y \to Z$ đều liên tục, thì ánh xạ hợp $g \circ f: X \to Z$ cũng liên tục.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Với mọi tập mở $W \in \tau_Z$, ta có $(g \circ f)^{-1}(W) = f^{-1}(g^{-1}(W))$. Vì $g$ liên tục nên $g^{-1}(W) \in \tau_Y$, và vì $f$ liên tục nên $f^{-1}(g^{-1}(W)) \in \tau_X$. ∎
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Thu hẹp):**  
Nếu $f: X \to Y$ liên tục và $A \subseteq X$ mang tô-pô con, thì ánh xạ thu hẹp $f|_A: A \to Y$ cũng liên tục.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Dành làm bài tập (sử dụng $f|_A = f \circ i$).
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Bổ đề dán — Pasting Lemma):**  
Cho $X = A \cup B$ với $A, B$ đều là các tập đóng trong $X$. Nếu $f: A \to Y$ và $g: B \to Y$ đều liên tục và trùng nhau trên giao ($f|_{A \cap B} = g|_{A \cap B}$), thì ánh xạ:

$$
h: X \to Y, \quad h(x) = \begin{cases} f(x) & x \in A \\ g(x) & x \in B \end{cases}
$$
</div>
là ánh xạ liên tục. Bổ đề này cho phép ghép các ánh xạ liên tục trên các mảnh đóng lại với nhau (kết quả cũng đúng nếu $A, B$ đều mở).

---

### 5. Phép đồng phôi (Homeomorphisms)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phép đồng phôi):**  
Ánh xạ $f: X \to Y$ là một **phép đồng phôi** (*homeomorphism*) nếu:
1. $f$ là song ánh;
2. $f$ liên tục;
3. Ánh xạ ngược $f^{-1}: Y \to X$ cũng liên tục.
</div>

Ký hiệu $X \cong Y$ (hoặc $X \simeq Y$) nếu tồn tại phép đồng phôi giữa $X$ và $Y$. Phép đồng phôi đóng vai trò như đẳng cấu trong tô-pô: hai không gian đồng phôi có cùng hoàn toàn cấu trúc tập mở.

![Homeomorphism examples](https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/Homeomorphism-cont-bis.svg/400px-Homeomorphism-cont-bis.svg.png)  
*Minh họa phép đồng phôi giữa các khoảng - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Homeomorphism-cont-bis.svg)*

**Ví dụ 1: Phép co giãn tuyến tính**  
Ánh xạ $f: [0, 1] \to [2, 5]$, $f(x) = 3x + 2$ là song ánh liên tục có ánh xạ ngược $f^{-1}(y) = (y - 2)/3$ cũng liên tục, nên $[0, 1] \cong [2, 5]$.

**Ví dụ 2: Đoạn đóng và khoảng mở không đồng phôi**  
Ta có $[0, 1] \not\cong (0, 1)$.

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Phác thảo chứng minh:**  
Giả sử tồn tại phép đồng phôi $f: [0, 1] \to (0, 1)$. Khi bỏ đi điểm đầu mút $0$, ánh xạ thu hẹp $f|_{(0, 1]}: (0, 1] \to (0, 1) \setminus \{f(0)\}$ vẫn là một phép đồng phôi. Tuy nhiên, $(0, 1]$ là tập liên thông, trong khi bỏ bất kỳ một điểm nào khỏi khoảng mở $(0, 1)$ đều tách nó thành hai khoảng mở rời nhau nên không liên thông — mâu thuẫn. ∎
</div>

**Ví dụ 3: Đường tròn và đường thẳng**  
$S^1 \not\cong \mathbb{R}$, vì $S^1$ compact còn $\mathbb{R}$ không compact.

**Ví dụ 4: Phép chiếu nổi (Stereographic Projection)**  
Phép chiếu từ cực Bắc $N \in S^2$ xuống mặt phẳng xích đạo tạo nên một phép đồng phôi $f: S^2 \setminus \{N\} \to \mathbb{R}^2$.

---

### 6. Tính chất tô-pô (Topological Properties)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tính chất tô-pô / Bất biến tô-pô):**  
Một tính chất $P$ được gọi là **tính chất tô-pô** (*topological property* hay *topological invariant*) nếu nó được bảo toàn qua phép đồng phôi:

$$
X \text{ has } P \land (X \cong Y) \implies Y \text{ has } P
$$
</div>

**Ví dụ các tính chất tô-pô:** Tính compact, tính liên thông, tính Hausdorff và lực lượng tập hợp.

**Ví dụ các tính chất KHÔNG phải tính chất tô-pô:**
- **Tính bị chặn** (theo mê-tric): $(0, 1)$ bị chặn, nhưng $(0, 1) \cong \mathbb{R}$ không bị chặn thông qua phép đồng phôi $f(x) = \tan(\pi x - \pi/2)$.
- **Tính đầy đủ mê-tric:** $\mathbb{R}$ đầy đủ, còn $(0, 1)$ không đầy đủ với mê-tric Euclid, dù hai không gian này đồng phôi với nhau.

Để chứng minh $X \not\cong Y$, phương pháp chuẩn là chỉ ra một tính chất tô-pô mà $X$ có nhưng $Y$ không có.

---

### 7. Phép nhúng và ánh xạ thương

<div class="textbook-definition" markdown="1">
**Định nghĩa (Phép nhúng — Embedding):**  
Ánh xạ $f: X \to Y$ là một **phép nhúng** nếu $f$ là một phép đồng phôi từ $X$ lên ảnh $f(X)$ (trang bị tô-pô con cảm sinh từ $Y$).
</div>

Ví dụ: ánh xạ bao hàm $(0, 1) \hookrightarrow \mathbb{R}$, đường tròn $S^1 \hookrightarrow \mathbb{R}^2$, và đồ thị $\text{Graph}(f) = \{(x, f(x))\} \hookrightarrow \mathbb{R}^2$ của một hàm liên tục $f: \mathbb{R} \to \mathbb{R}$.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Ánh xạ thương — Quotient Map, gợi mở):**  
Ánh xạ $p: X \to Y$ là một **ánh xạ thương** nếu:
1. $p$ toàn ánh;
2. $U \subseteq Y$ mở trong $Y \iff p^{-1}(U)$ mở trong $X$.
</div>

Ví dụ: ánh xạ $[0, 1] \to S^1$, $t \mapsto (\cos 2\pi t, \sin 2\pi t)$ dán hai đầu mút $0$ và $1$ lại với nhau là một ánh xạ thương.

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Nền tảng trực giác cho khái niệm biến dạng liên tục.*

2. **L.E.J. Brouwer** - *"Zur Analysis Situs"* (1910)  
   *Các bất biến tô-pô và định lý điểm bất động.*

3. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Hình thức hóa ánh xạ liên tục trên không gian tô-pô.*

### Giáo trình

4. **James R. Munkres** - *Topology*, 2nd Ed., **§18–19: Continuous Functions**  
   *Trình bày rõ ràng, đầy đủ.*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 5**  
   *Giàu ví dụ minh họa.*

6. **M.A. Armstrong** - *Basic Topology*, **Chapter 2**  
   *Trực giác hình học rõ nét.*

7. **Allen Hatcher** - *Algebraic Topology*, **§0**  
   *Góc nhìn đồng luân và tô-pô đại số.*

---

## 🔗 Ứng dụng và liên hệ

### Đồ họa máy tính — Biến hình (Morphing)
Các phép biến hình mượt giữa hai mô hình 3D tương ứng với phép biến dạng liên tục bảo toàn cấu trúc tô-pô (chẳng hạn số lỗ của bề mặt).

### Vật lý — Chuyển pha
Trong nhiệt động lực học và vật lý thống kê, các đại lượng vật lý thường biến thiên liên tục trên không gian pha trừ tại các điểm tới hạn nơi cấu trúc pha thay đổi.

### Khoa học dữ liệu — Học đa tạp và giảm chiều
Các thuật toán giảm chiều phi tuyến như t-SNE và UMAP tìm cách xây dựng ánh xạ từ dữ liệu chiều cao xuống không gian chiều thấp sao cho bảo toàn càng nhiều càng tốt cấu trúc lân cận địa phương.

### Khoa học thần kinh — Bản đồ vỏ não
Bề mặt vỏ não có cấu trúc tô-pô tương đương mặt cầu (với nhiều nếp gấp); việc trải phẳng vỏ não để trực quan hóa đòi hỏi phép chiếu liên tục (có biến dạng khoảng cách không tránh khỏi).

### Ví dụ thực tế
Sơ đồ tàu điện ngầm chỉ bảo toàn cấu trúc kết nối tô-pô (thứ tự các ga và điểm giao tuyến) mà bỏ qua khoảng cách địa lý thực tế.

---

## Video tham khảo

- **xem trước** [Ánh xạ liên tục và phép đồng phôi](https://www.youtube.com/watch?v=rEZoSe0HjOs) — Cuong Nguyen, tiếng Việt. Liên tục rồi đồng phôi, đúng hai tầng của bài, nói bằng tiếng Việt.
- [[Tôpô đại cương] Bài 22. Ánh xạ liên tục: định nghĩa và Ví dụ](https://www.youtube.com/watch?v=cU8HZcRSpFM) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Định nghĩa ánh xạ liên tục qua nghịch ảnh tập mở, kèm ví dụ.
- [Basic Topology 19 | Homeomorphic Spaces](https://www.youtube.com/watch?v=1FFwuZbzbjE) — The Bright Side of Mathematics, tiếng Anh. Khi nào một song ánh liên tục thực sự là đồng phôi, và vì sao hai không gian khi đó là một.

## 🧩 Bài tập

### Tính liên tục

1. **Kiểm tra liên tục:**  
   Xét $f: \mathbb{R} \to \mathbb{R}$ (với tô-pô Euclid). Kiểm tra tính liên tục theo định nghĩa tô-pô:
   - a) $f(x) = 2x + 3$
   - b) $f(x) = x^2$
   - c) $f(x) = \lfloor x \rfloor$ (hàm phần nguyên)

2. **Ánh xạ hằng:**  
   Chứng minh mọi ánh xạ hằng $f: X \to Y$ đều liên tục với mọi tô-pô trên $X$ và $Y$.

3. **Từ tô-pô rời rạc:**  
   Cho $X$ mang tô-pô rời rạc và $Y$ bất kỳ. Chứng minh mọi ánh xạ $f: X \to Y$ đều liên tục.

4. **Đến tô-pô tầm thường:**  
   Cho $Y$ mang tô-pô tầm thường và $X$ bất kỳ. Chứng minh mọi ánh xạ $f: X \to Y$ đều liên tục.

5. **Hợp thành:**  
   Cho $f: X \to Y$ và $g: Y \to Z$ liên tục. Chứng minh $g \circ f$ liên tục trực tiếp bằng định nghĩa nghịch ảnh tập mở.

### Các đặc trưng tương đương

6. **Tập đóng:**  
   Chứng minh $f$ liên tục $\iff$ nghịch ảnh của mọi tập đóng là tập đóng.

7. **Kiểm tra qua cơ sở:**  
   Với $f: \mathbb{R} \to \mathbb{R}$, $f(x) = x^2$, dùng cơ sở $\mathcal{B} = \{(a, b)\}$ để kiểm tra tính liên tục. Mô tả dạng của $f^{-1}((a, b))$ theo dấu của $a, b$.

8. **Điều kiện bao đóng:**  
   Cho $f: X \to Y$ liên tục và $A \subseteq X$. Chứng minh $f(\text{cl}(A)) \subseteq \text{cl}(f(A))$. Cho ví dụ khi bao hàm là nghiêm ngặt.

### Phép đồng phôi

9. **Kiểm tra phép đồng phôi:**  
   Xét $f: (0, 1) \to \mathbb{R}$, $f(x) = \tan(\pi(x - 1/2))$.
   - a) Chứng minh $f$ là song ánh.
   - b) Chứng minh $f$ liên tục.
   - c) Chứng minh $f^{-1}$ liên tục.
   - d) Kết luận $(0, 1) \cong \mathbb{R}$.

10. **Không đồng phôi:**  
    Chứng minh $[0, 1] \not\cong (0, 1)$ dựa trên các bước:
    - a) Bỏ bất kỳ một điểm nào khỏi $(0, 1)$ làm không gian mất tính liên thông.
    - b) Bỏ một đầu mút ($0$ hoặc $1$) khỏi $[0, 1]$ thì tập còn lại vẫn liên thông.
    - c) Tính liên thông là một bất biến tô-pô.

11. **Đường tròn và đường thẳng:**  
    Chứng minh $S^1 \not\cong \mathbb{R}$ dựa vào tính compact là một tính chất tô-pô ($S^1$ compact, còn $\mathbb{R}$ không compact).

### Tính chất tô-pô

12. **Lực lượng:**  
    Vì sao $X \cong Y$ kéo theo $|X| = |Y|$? Chiều ngược lại có đúng không?

13. **Không gian hữu hạn:**  
    Có bao nhiêu không gian tô-pô đôi một không đồng phôi trên tập $2$ phần tử? Trên tập $3$ phần tử?

14. **Bất biến tô-pô:**  
    Liệt kê một số tính chất tô-pô sẽ học trong các chương tiếp theo (như tính compact, tính liên thông, tính Hausdorff, tiên đề đếm được thứ hai) và giải thích ngắn gọn ý nghĩa của chúng.

### Nâng cao

15. **Phép chiếu nổi (Stereographic Projection):**  
    Xét $f: S^2 \setminus \{N\} \to \mathbb{R}^2$ với $N = (0, 0, 1)$ xác định bởi:
    $$
    f(x,y,z) = \left(\frac{x}{1-z}, \frac{y}{1-z}\right)
    $$
    Chứng minh $f$ là một phép đồng phôi.

16. **Đường cong sin của nhà tô-pô (Topologist's Sine Curve):**  
    Xét $A = \{(x, \sin(1/x)) : 0 < x \le 1\} \cup \{(0, 0)\} \subset \mathbb{R}^2$.
    - $A$ có liên thông không?
    - Bao đóng $\text{cl}(A)$ có liên thông không?
    - $A$ có đồng phôi với $[0, 1]$ không?

17. **Gợi mở về lý thuyết nút (Knot Theory):**  
    Đường tròn $S^1$ có thể nhúng vào $\mathbb{R}^3$ theo nhiều cách khác nhau (tạo thành các nút thắt). Với tô-pô con kế thừa từ $\mathbb{R}^3$, các nút thắt khác nhau có đồng phôi với nhau không?

18. **Nhóm đồng phôi:**  
    Với một không gian tô-pô $X$ cố định, chứng minh tập tất cả các phép đồng phôi $f: X \to X$ cùng phép hợp thành tạo thành một nhóm.

### Câu hỏi suy ngẫm

19. **Vì sao song ánh liên tục chưa đủ để là phép đồng phôi?**  
    Xét $f: [0, 2\pi) \to S^1$, $f(t) = (\cos t, \sin t)$. Ánh xạ này là song ánh và liên tục, nhưng vì sao nó **không** phải phép đồng phôi?

20. **Tô-pô và hình học:**  
    So sánh tô-pô (nghiên cứu các bất biến qua phép đồng phôi) với hình học Euclid (nghiên cứu các bất biến qua phép đẳng cự). Nêu các tính chất hình học không phải là bất biến tô-pô.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §18–22 (Continuous Functions, Homeomorphisms, Quotient Topology)
- **Armstrong, Basic Topology:** Chapter 2–3 (Continuity and Homeomorphisms)
- **Hatcher, Algebraic Topology:** §0 (Homotopy and Cell Complexes)
- **Morris, Topology Without Tears:** Chapter 5–6

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã học về các ánh xạ bảo toàn cấu trúc tô-pô:

✅ **Ánh xạ liên tục:** Nghịch ảnh của mọi tập mở là tập mở.  
✅ **Các đặc trưng tương đương:** Qua tập đóng, bao đóng, phần trong và cơ sở.  
✅ **Liên tục tại điểm:** Phiên bản cục bộ, tổng quát hóa định nghĩa $\varepsilon$-$\delta$.  
✅ **Hợp thành và Bổ đề dán:** Xây dựng ánh xạ liên tục từ các ánh xạ đơn giản hơn.  
✅ **Phép đồng phôi:** Song ánh liên tục có ánh xạ ngược liên tục.  
✅ **Tính chất tô-pô:** Bất biến qua phép đồng phôi, dùng để phân biệt các không gian không đồng phôi.

**Tiếp theo:** Trong Bài 01.04, ta sẽ tìm hiểu **Tô-pô con và Tô-pô tích** — hai phương pháp cốt lõi để xây dựng không gian tô-pô mới từ các không gian đã biết.

---

*"A topologist cannot distinguish a coffee mug from a doughnut."* — Popular joke

🎯 **Hãy thực hành kiểm tra tính liên tục và nhận diện phép đồng phôi trên nhiều ví dụ cụ thể.** 🎯

---

**Previous:** [Lecture 01.02: Closed Sets, Closure, and Interior](/contents/vi/topology-chapter01/01_02_Closed_Sets_Closure_Interior/)  
**Next:** [Lecture 01.04: Subspace and Product Topology](/contents/vi/topology-chapter01/01_04_Subspace_Product_Topology/)
