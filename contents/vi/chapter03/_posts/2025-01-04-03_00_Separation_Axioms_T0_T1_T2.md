---
layout: post
title: "Lecture 03.00: Separation Axioms - T₀, T₁, T₂ (Hausdorff)"
lang: vi
lang-ref: lecture-03-00
chapter: 3
lecture: 0
categories: [chapter03]
tags: [kolmogorov, frechet, hausdorff, separation, T0, T1, T2]
description: "Các tiên đề phân ly T₀, T₁, T₂: Kolmogorov, Fréchet, và Hausdorff spaces"
---

**Các Tiên đề tách — $T_0$, $T_1$, $T_2$ (Hausdorff)**

---

## 📖 Tổng quan

Trong giải tích năm nhất, ta mặc nhiên tin một điều hiển nhiên đến mức chẳng bao giờ nghi ngờ: *một dãy số hội tụ thì chỉ có **duy nhất một** giới hạn.* Nhưng hãy thử đặt mình vào một không gian tô-pô tầm thường $$X = \{a, b\}$$ với $$\tau = \{\emptyset, \{a, b\}\}$$: xét dãy hằng $$x_n = a, a, a, \dots$$ — vì tập mở duy nhất chứa $$b$$ là cả $$X$$ (chứa mọi $$x_n$$), dãy hằng toàn chữ $$a$$ đó **vừa hội tụ về $$a$$, vừa hội tụ về $$b$$**!

Để loại trừ những không gian "mờ nhòe" nơi các điểm dính bết vào nhau như thế, Chương 03 giới thiệu **các tiên đề tách (separation axioms)** — một chiếc thang đo độ phân giải của tập mở từ yếu đến mạnh:

$$
T_4 \subset T_{3.5} \subset T_3 \subset T_2 \subset T_1 \subset T_0
$$

![Separation axioms hierarchy](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Separation_axioms.svg/500px-Separation_axioms.svg.png)  
*Hệ phân tầng các tiên đề tách - Nguồn minh họa khái niệm*

Bài giảng này khai mở ba nấc thang đầu tiên — **$$T_0$$ (Kolmogorov)**, **$$T_1$$ (Fréchet)** và đặc biệt là **$$T_2$$ (Hausdorff)**, điều kiện vàng bảo đảm giới hạn là duy nhất và mọi tập con compact đều đóng.

**Mạch bài học:** Bản đồ kiến thức nền (ý nghĩa chiếc thang $$T_0 \to T_1 \to T_2$$ & vai trò đặc biệt của Hausdorff) → Khung giải thích chậm: cầm tay phân loại 3 không gian mẫu để chứng minh bao hàm ngặt $$T_2 \subsetneq T_1 \subsetneq T_0$$ → Trực giác & Định nghĩa hình thức → Tính chất không gian Hausdorff → Bài tập & Tóm tắt.

---

## Bản đồ kiến thức nền: Các Tiên đề tách $$T_0, T_1, T_2$$ đo lường điều gì?

### 1. $$T_0$$ (Kolmogorov) và $$T_1$$ (Fréchet): phân biệt một chiều vs. hai chiều

- **$$T_0$$:** Với mọi $$x \neq y$$, có *ít nhất một* tập mở chứa điểm này mà không chứa điểm kia (phân biệt một chiều — hai điểm không thể có hệ lân cận giống hệt nhau).
- **$$T_1$$:** Với mọi $$x \neq y$$, có tập mở chứa $$x$$ không chứa $$y$$ **VÀ** có tập mở chứa $$y$$ không chứa $$x$$. Đặc trưng tương đương cực gọn: **$$X$$ là $$T_1 \iff$$ mọi tập đơn điểm $$\{x\}$$ đều là tập đóng!**

### 2. $$T_2$$ (Hausdorff): hai "bong bóng mở" không chạm nhau

Một không gian $$T_1$$ vẫn có thể rất kỳ dị (như đường thẳng có hai gốc tọa độ, hoặc tô-pô đồng hữu hạn). **Tiên đề Hausdorff ($$T_2$$)** đòi hỏi mạnh hơn hẳn: với mọi $$x \neq y$$, hai lân cận mở $$U \ni x$$ và $$V \ni y$$ phải **rời nhau hoàn toàn** ($$U \cap V = \emptyset$$).

### 3. Vì sao hầu hết hình học và giải tích đều giả thiết không gian là Hausdorff?

Nhờ hai bong bóng rời nhau $$U \cap V = \emptyset$$, ta lập tức khôi phục hai tính chất sống còn của giải tích: (1) **giới hạn của mọi dãy (hoặc lưới) nếu có là duy nhất**, và (2) **mọi tập con compact của không gian Hausdorff đều đóng**.

---

### Khung giải thích (nên đọc chậm): Cầm tay kiểm chứng ranh giới chặt $$T_2 \subsetneq T_1 \subsetneq T_0$$ trên 3 không gian mẫu

Hãy tự tay kiểm tra ba không gian cụ thể để thấy rõ mỗi nấc thang thực sự loại bỏ được những "quái vật" nào:

1. **Ví dụ đạt $$T_0$$ nhưng KHÔNG đạt $$T_1$$ — Không gian Sierpiński:**
   Xét $$X = \{0, 1\}$$ với tô-pô $$\tau = \bigl\{\emptyset,\; \{1\},\; \{0, 1\}\bigr\}$$.
   - Kiểm tra $$T_0$$: Với cặp điểm duy nhất $$0 \neq 1$$, tập mở $$U = \{1\}$$ chứa $$1$$ mà không chứa $$0$$ → **Đạt $$T_0$$!**
   - Kiểm tra $$T_1$$: Có tập mở nào chứa $$0$$ mà không chứa $$1$$ không? Tập mở duy nhất chứa $$0$$ là $$\{0, 1\}$$, lại chứa luôn $$1$$! (Hoặc kiểm tra nhanh: phần bù của $$\{1\}$$ là $$\{0\}$$ không mở nên $$\{1\}$$ không đóng!) → **KHÔNG đạt $$T_1$$!**
2. **Ví dụ đạt $$T_1$$ nhưng KHÔNG đạt $$T_2$$ — Tô-pô đồng hữu hạn trên $$\mathbb{R}$$:**
   Trên $$\mathbb{R}$$, gọi $$U$$ là mở nếu $$U = \emptyset$$ hoặc $$\mathbb{R} \setminus U$$ là tập hữu hạn.
   - Kiểm tra $$T_1$$: Với mọi $$x \in \mathbb{R}$$, phần bù $$\mathbb{R} \setminus \{x\}$$ có phần bù là $$\{x\}$$ (hữu hạn!) nên mở → $$\{x\}$$ đóng → **Đạt $$T_1$$!**
   - Kiểm tra $$T_2$$: Chọn hai điểm bất kỳ $$0 \neq 1$$ và hai tập mở khác rỗng bất kỳ $$U \ni 0, V \ni 1$$. Ta có $$U = \mathbb{R} \setminus F_1$$ và $$V = \mathbb{R} \setminus F_2$$ với $$F_1, F_2$$ hữu hạn. Khi đó:
     $$
     U \cap V = \mathbb{R} \setminus (F_1 \cup F_2) \neq \emptyset
     $$
     vì $$\mathbb{R}$$ vô hạn còn $$F_1 \cup F_2$$ hữu hạn! Không bao giờ tìm được hai tập mở rời nhau → **KHÔNG đạt $$T_2$$!** (Và mọi dãy gồm các phần tử phân biệt như $$x_n = n$$ đều hội tụ tới *mọi* số thực trên $$\mathbb{R}$$!)
3. **Ví dụ đạt $$T_2$$ — $$\mathbb{R}$$ với tô-pô Euclid:**
   Với $$x \neq y$$, đặt $$r = \frac{\lvert x - y \rvert}{2} > 0$$. Hai khoảng mở $$(x - r, x + r)$$ và $$(y - r, y + r)$$ rời nhau hoàn toàn → **Đạt $$T_2$$!**

---

## 🎯 Từ trực giác đến hình thức

### Các mức độ phân biệt hai điểm

Xét hai điểm phân biệt $x$ và $y$:
- **Không thỏa $T_0$:** Mọi tập mở chứa $x$ đều chứa $y$ và ngược lại (như tô-pô tầm thường).
- **$T_0$ (Kolmogorov):** Có ít nhất một tập mở chứa điểm này mà không chứa điểm kia (phân biệt bất đối xứng).
- **$T_1$ (Fréchet):** $x$ có lân cận mở không chứa $y$, **và** $y$ có lân cận mở không chứa $x$ (phân biệt đối xứng, nhưng hai lân cận vẫn có thể giao nhau).
- **$T_2$ (Hausdorff):** $x$ và $y$ có hai lân cận mở **hoàn toàn rời nhau**.

![T0 T1 T2 illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/T0-T2_spaces.svg/600px-T0-T2_spaces.svg.png)  
*Minh họa các không gian $T_0$, $T_1$, $T_2$ - Nguồn minh họa khái niệm*

---

## 📐 Định nghĩa hình thức

### 1. Không gian $T_0$ (Kolmogorov)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian $T_0$):**  
Không gian $X$ là **$T_0$** (*Kolmogorov*) nếu với mọi $x \neq y \in X$, tồn tại tập mở $U$ chứa đúng một trong hai điểm đó:

$$
\forall x \neq y: \exists U \in \tau: (x \in U \land y \notin U) \lor (y \in U \land x \notin U)
$$
</div>

**Ví dụ 1: Không gian Sierpiński**  
$X = \{0, 1\}$, $\tau = \{\emptyset, \{0\}, \{0, 1\}\}$. Tập mở $U = \{0\}$ chứa $0$ nhưng không chứa $1$, nên $X$ là không gian $T_0$ (dù không có tập mở nào chứa $1$ mà không chứa $0$).

**Ví dụ 2:** Mọi không gian rời rạc và mọi không gian có tô-pô đồng hữu hạn đều là $T_0$.

**Phản ví dụ:** Không gian có ít nhất $2$ điểm với tô-pô tầm thường không phải $T_0$.

---

### 2. Không gian $T_1$ (Fréchet)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian $T_1$):**  
Không gian $X$ là **$T_1$** (*Fréchet*) nếu với mọi $x \neq y$, mỗi điểm đều có một lân cận mở không chứa điểm kia:

$$
\forall x \neq y: \exists U, V \in \tau: (x \in U, y \notin U) \land (y \in V, x \notin V)
$$
</div>

**Đặc trưng tương đương:** $X$ là không gian $T_1 \iff$ mọi tập đơn điểm $\{x\}$ đều là **tập đóng**.

<div class="textbook-proof" markdown="1">
**Chứng minh:**
</div>

- **($\Rightarrow$):** Nếu $X$ là $T_1$, với mỗi $y \in X \setminus \{x\}$ tồn tại tập mở $U_y \ni y$ sao cho $x \notin U_y$. Khi đó $X \setminus \{x\} = \bigcup_{y \neq x} U_y$ mở, nên $\{x\}$ đóng.
- **($\Leftarrow$):** Nếu mọi tập đơn điểm đều đóng, thì với $x \neq y$, hai tập $U = X \setminus \{y\}$ và $V = X \setminus \{x\}$ là các tập mở thỏa $x \in U, y \notin U$ và $y \in V, x \notin V$.

**Ví dụ:** $\mathbb{R}$ (tô-pô Euclid) và mọi tập vô hạn với tô-pô đồng hữu hạn đều là không gian $T_1$. Ngược lại, không gian Sierpiński $\{0, 1\}$ với $\tau = \{\emptyset, \{0\}, \{0, 1\}\}$ không phải $T_1$ vì $\{0\}$ không đóng (phần bù $X \setminus \{0\} = \{1\}$ không mở).

<div class="textbook-theorem" markdown="1">
**Định lý ($T_1 \Rightarrow T_0$):**  
Mọi không gian $T_1$ đều là không gian $T_0$.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:** Suy trực tiếp từ định nghĩa. ∎
</div>

---

### 3. Không gian $T_2$ (Hausdorff)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian Hausdorff):**  
Không gian $X$ là **$T_2$** (*Hausdorff*) nếu với mọi $x \neq y$, tồn tại hai lân cận mở **rời nhau** tách $x$ và $y$:

$$
\forall x \neq y: \exists U, V \in \tau: x \in U, y \in V, U \cap V = \emptyset
$$
</div>

![Hausdorff property](https://upload.wikimedia.org/wikipedia/commons/thumb/9/97/Hausdorff_space.svg/400px-Hausdorff_space.svg.png)  
*Tính chất Hausdorff: hai lân cận mở rời nhau - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_space.svg)*

**Ví dụ 1: Không gian mê-tric**

<div class="textbook-theorem" markdown="1">
**Định lý:** Mọi không gian mê-tric đều là không gian Hausdorff.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Với $x \neq y$ trong $(X, d)$, đặt $\varepsilon = d(x, y)/2 > 0$. Hai hình cầu mở $U = B(x, \varepsilon)$ và $V = B(y, \varepsilon)$ rời nhau theo bất đẳng thức tam giác.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** $\mathbb{R}^n$ với mê-tric Euclid là không gian Hausdorff.
</div>

**Ví dụ 2:** Mọi không gian rời rạc đều là Hausdorff (chọn $U = \{x\}$ và $V = \{y\}$).

**Phản ví dụ:** Tập vô hạn $X$ với tô-pô đồng hữu hạn **không** Hausdorff, vì nếu $U = X \setminus A$ và $V = X \setminus B$ ($A, B$ hữu hạn) thì $U \cap V = X \setminus (A \cup B)$ vẫn vô hạn nên khác rỗng. Tô-pô tầm thường (trên tập có ít nhất $2$ điểm) cũng không Hausdorff.

<div class="textbook-theorem" markdown="1">
**Định lý ($T_2 \Rightarrow T_1$):**  
Mọi không gian Hausdorff đều là không gian $T_1$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Nếu $U \ni x$ và $V \ni y$ rời nhau thì hiển nhiên $y \notin U$ và $x \notin V$.
</div>

Tóm lại:
$$
\text{Hausdorff (T₂)} \implies \text{Fréchet (T₁)} \implies \text{Kolmogorov (T₀)}
$$

---

### 4. Các tính chất quan trọng của không gian Hausdorff

<div class="textbook-theorem" markdown="1">
**Định lý (Tính duy nhất của giới hạn):**  
Trong không gian Hausdorff, nếu một dãy hội tụ thì giới hạn của nó là **duy nhất**.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Giả sử $x_n \to x$ và $x_n \to y$ với $x \neq y$. Do $X$ Hausdorff, tồn tại hai tập mở rời nhau $U \ni x$ và $V \ni y$. Theo định nghĩa hội tụ, tồn tại $N_1, N_2$ sao cho $x_n \in U$ với mọi $n \ge N_1$ và $x_n \in V$ với mọi $n \ge N_2$. Với $n \ge \max\{N_1, N_2\}$, ta có $x_n \in U \cap V = \emptyset$ — mâu thuẫn. ∎
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Tập con compact là tập đóng):**  
Trong không gian Hausdorff, mọi tập con compact đều là tập đóng.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Cho $K \subseteq X$ compact và $x \in X \setminus K$. Với mỗi $y \in K$, chọn hai tập mở rời nhau $U_y \ni x$ và $V_y \ni y$. Vì $\{V_y\}_{y \in K}$ phủ $K$ nên có phủ con hữu hạn $V_{y_1}, \dots, V_{y_n}$. Khi đó $U = U_{y_1} \cap \dots \cap U_{y_n}$ là tập mở chứa $x$ và rời với $K$, chứng tỏ $X \setminus K$ mở.
</div>

<div class="textbook-theorem" markdown="1">
**Định lý (Đường chéo đóng):**  
$X$ là không gian Hausdorff $\iff$ đường chéo $\Delta = \{(x, x) : x \in X\}$ là tập đóng trong $X \times X$ (với tô-pô tích).
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Dành làm bài tập (kiểm tra phần bù $(X \times X) \setminus \Delta$ là tập mở).
</div>

---

### 5. Bảng tổng hợp các ví dụ

| Không gian | $T_0$ | $T_1$ | $T_2$ (Hausdorff) |
|-------|----|----|----------------|
| Rời rạc | ✓ | ✓ | ✓ |
| Tầm thường ($\ge 2$ điểm) | ✗ | ✗ | ✗ |
| Đồng hữu hạn (vô hạn) | ✓ | ✓ | ✗ |
| Sierpiński $\{0, 1\}$ | ✓ | ✗ | ✗ |
| $\mathbb{R}^n$ (Euclid) | ✓ | ✓ | ✓ |
| Không gian mê-tric | ✓ | ✓ | ✓ |

**Ví dụ đáng chú ý — Tô-pô Zariski trên $\mathbb{C}^n$:** Các tập đóng là các tập nghiệm chung của các họ đa thức (đa tạp đại số). Tô-pô này là $T_1$ (mỗi điểm là tập đóng) nhưng không phải $T_2$ (mọi cặp tập mở khác rỗng đều giao nhau) — cho thấy hình học đại số làm việc tự nhiên với các không gian không Hausdorff.

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Định nghĩa tiên đề $T_2$ (không gian Hausdorff).*

2. **Andrey Kolmogorov** - *"Zur Begründung der projektiven Geometrie"* (1932)  
   *Tiên đề $T_0$ trong hình học xạ ảnh.*

3. **Maurice Fréchet** - *"Sur quelques points du calcul fonctionnel"* (1906)  
   *Các khảo sát sớm liên quan đến điều kiện $T_1$.*

### Giáo trình

4. **James R. Munkres** - *Topology*, 2nd Ed., **§31–32: Separation Axioms**  
   *Trình bày hệ thống, rõ ràng.*

5. **Stephen Willard** - *General Topology*, **Chapter 4**  
   *Trình bày đầy đủ.*

6. **John L. Kelley** - *General Topology*, **Chapter 3**  
   *Trình bày nâng cao.*

7. **Ryszard Engelking** - *General Topology*, **Chapter 1**  
   *Tài liệu tra cứu chi tiết.*

---

## 🔗 Ứng dụng và liên hệ

- **Giải tích:** Tính Hausdorff bảo đảm tính duy nhất của giới hạn trong không gian mê-tric và không gian định chuẩn (kể cả dưới tô-pô yếu trên không gian Hilbert).
- **Hình học đại số:** Tô-pô Zariski trên các lược đồ (*schemes*) nói chung không Hausdorff.
- **Khoa học máy tính — Lý thuyết miền (*Domain Theory*):** Tô-pô Scott trên các tập sắp thứ tự bộ phận thường là $T_0$ nhưng không $T_1$, được dùng trong ngữ nghĩa học ngôn ngữ lập trình.

---

## Video tham khảo

- **xem trước** [[Tôpô đại cương] Bài 15. Không gian Hausdorff và Tiên đề tách T2: Định nghĩa và ví dụ](https://www.youtube.com/watch?v=Cddm3s5qzRo) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Hausdorff và tiên đề tách T2 bằng tiếng Việt, đích của thang T0–T1–T2 trong bài.
- [Basic Topology 6 | Hausdorff Spaces](https://www.youtube.com/watch?v=wHIu3Js30Uk) — The Bright Side of Mathematics, tiếng Anh. Hai điểm tách được bằng hai tập mở, định nghĩa Hausdorff trong Basic Topology.
- [Intuitive Topology 7: Hausdorff](https://www.youtube.com/watch?v=-wbRSq7ExdM) — Hausdorff, tiếng Anh. Cùng tính chất, vẽ chậm, để thấy T2 mạnh hơn T1 ở chỗ nào.

## 🧩 Bài tập

### Không gian $T_0$

1. **Kiểm tra $T_0$:**  
   Các không gian sau có phải $T_0$ không?
   - a) $\{a, b, c\}$ với $\tau = \{\emptyset, \{a\}, \{a, b\}, X\}$
   - b) $\mathbb{N}$ với tô-pô đồng hữu hạn
   - c) $\{0, 1\}$ với $\tau = \{\emptyset, \{0\}, X\}$

2. **Không gian Sierpiński:**  
   Chứng minh $\{0, 1\}$ với $\tau = \{\emptyset, \{0\}, X\}$ là $T_0$ nhưng không $T_1$.

### Không gian $T_1$

3. **Tập đơn điểm đóng:**  
   Chứng minh $X$ là $T_1 \iff$ mọi tập đơn điểm $\{x\}$ đều đóng.

4. **Tô-pô đồng hữu hạn:**  
   Chứng minh tô-pô đồng hữu hạn trên tập vô hạn là $T_1$.

5. **Không gian $T_1$ hữu hạn:**  
   Chứng minh nếu $X$ hữu hạn và là $T_1$, thì tô-pô trên $X$ bắt buộc là tô-pô rời rạc.

### Không gian Hausdorff

6. **Không gian mê-tric:**  
   Trình bày chứng minh chi tiết: mọi không gian mê-tric đều Hausdorff.

7. **Giới hạn không duy nhất:**  
   Nêu một ví dụ không gian không Hausdorff có một dãy hội tụ đồng thời về nhiều điểm khác nhau.

8. **Tập compact không đóng:**  
   Trong $\mathbb{R}$ với tô-pô đồng hữu hạn:
   - a) $[0, 1]$ có compact không?
   - b) $[0, 1]$ có đóng không?
   - c) Điều này có mâu thuẫn với định lý "tập con compact là đóng" không?

### Tính bảo toàn

9. **Tích:** Chứng minh nếu $X, Y$ Hausdorff thì $X \times Y$ Hausdorff.
10. **Không gian con:** Chứng minh nếu $X$ Hausdorff và $A \subseteq X$ thì không gian con $A$ cũng Hausdorff.
11. **Ảnh liên tục:** Cho $f: X \to Y$ là toàn ánh liên tục với $X$ Hausdorff. $Y$ có nhất thiết Hausdorff không? Nếu không, hãy nêu phản ví dụ.

### Nâng cao

12. **Đường chéo đóng:** Chứng minh $X$ Hausdorff $\iff \Delta = \{(x, x) : x \in X\}$ đóng trong $X \times X$.
13. **Hoàn toàn Hausdorff (*Urysohn / Completely Hausdorff*):** Không gian $X$ gọi là hoàn toàn Hausdorff nếu với mọi $x \neq y$, tồn tại hàm liên tục $f: X \to [0, 1]$ sao cho $f(x) = 0, f(y) = 1$. Chứng minh hoàn toàn Hausdorff $\Rightarrow$ Hausdorff và kiểm tra tính chất này trên $\mathbb{R}$.
14. **Tô-pô Zariski:** Tìm hiểu tô-pô Zariski trên $\mathbb{C}$ (trùng với tô-pô đồng hữu hạn) và giải thích vì sao nó $T_1$ nhưng không $T_2$.

### Câu hỏi suy ngẫm

15. **Vai trò của Hausdorff:** Liệt kê các lý do khiến giả thiết Hausdorff thường được mặc định trong giải tích và hình học.
16. **Không gian không Hausdorff:** Nêu ba ví dụ tự nhiên của không gian không Hausdorff trong toán học và khoa học máy tính.
17. **Tính một chiều của hệ phân tầng:** Nêu các ví dụ chứng tỏ $T_2 \Rightarrow T_1 \Rightarrow T_0$ không có chiều đảo.

---

## 📚 Đọc thêm

- **Munkres, Topology:** §31–32 (Separation Axioms)
- **Willard, General Topology:** Chapter 4 (Separation Axioms)
- **Engelking, General Topology:** Chapter 1.5 (Separation Properties)
- **Steen & Seebach:** *Counterexamples in Topology*

---

## 🎓 Tóm tắt

✅ **$T_0$ (Kolmogorov):** Phân biệt được hai điểm bất kỳ bằng ít nhất một tập mở.  
✅ **$T_1$ (Fréchet):** Phân biệt đối xứng $\iff$ mọi tập đơn điểm đều đóng.  
✅ **$T_2$ (Hausdorff):** Hai điểm phân biệt có hai lân cận mở rời nhau.  
✅ **Hệ phân tầng:** $T_2 \Rightarrow T_1 \Rightarrow T_0$ (các chiều đảo đều sai).  
✅ **Tính chất của không gian Hausdorff:** Giới hạn dãy là duy nhất, mọi tập con compact đều đóng và đường chéo $\Delta$ đóng trong $X \times X$.

**Tiếp theo:** Bài 03.01 sẽ mở rộng lên các bậc tách cao hơn là **Không gian chính quy ($T_3$), chuẩn tắc ($T_4$), Bổ đề Urysohn và Định lý mở rộng Tietze**.

---

*"Hausdorff spaces are to topology what metric spaces are to geometry."* — Standard analogy

🎯 **Hãy nắm chắc sự khác biệt giữa các bậc $T_2 \Rightarrow T_1 \Rightarrow T_0$ qua các ví dụ cụ thể.** 🎯

---

**Previous Chapter:** [Chapter 02: Connectedness and Compactness](/contents/vi/topology-chapter02/)  
**Next:** [Lecture 03.01: Regular and Normal Spaces](/contents/vi/topology-chapter03/03_01_Regular_Normal_Spaces/)
