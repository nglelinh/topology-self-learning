---
layout: post
title: "Lecture 04.01: Completeness and Baire Category Theorem"
lang: vi
lang-ref: lecture-04-01
chapter: 4
lecture: 1
categories: [chapter04]
tags: [completeness, baire-category, nowhere-dense, residual, complete-spaces]
description: "Completeness trong metric spaces, Baire Category Theorem, và applications"
---

**Tính đầy đủ và Định lý phạm trù Baire**

---

## 📖 Tổng quan

> **Câu chuyện mở đầu:** Hãy tưởng tượng bạn đang tiến dần từng bước theo một chuỗi chỉ dẫn cực kỳ chính xác về một kho báu: $$1,\; 1.4,\; 1.41,\; 1.414,\; 1.4142\dots$$ Các bước chân của bạn ngày càng sát nhau đến mức sai số nhỏ hơn $$10^{-100}$$ — đó là một **dãy Cauchy**. Thế nhưng nếu bản đồ của bạn chỉ gồm các **số hữu tỉ $$\mathbb{Q}$$**, thì đúng tại vị trí kho báu $$\sqrt{2}$$ lại là một **cái hố trống rỗng** không tồn tại trong bản đồ! **Tính đầy đủ (Completeness)** chính là lời cam kết rằng không gian của bạn **không có bất kỳ lỗ thủng vi mô nào** — và từ đó nảy sinh hai định lý quyền lực bậc nhất của giải tích hiện đại: **Điểm bất động Banach** và **Định lý Phạm trù Baire**!

Tính đầy đủ (completeness) là một trong những khái niệm trung tâm của giải tích và tô-pô. Về mặt trực quan, một không gian metric là đầy đủ nếu nó không có "điểm khuyết": mọi dãy Cauchy (dãy có các phần tử tiến gần nhau tùy ý khi chỉ số tăng) đều hội tụ đến một điểm nằm ngay trong không gian đó.

Định lý phạm trù Baire (Baire Category Theorem) phát biểu rằng một không gian metric đầy đủ khác rỗng không thể biểu diễn thành hợp đếm được của các tập không đâu trù mật (nowhere dense). Phát biểu này cho thấy các không gian metric đầy đủ là "lớn" theo nghĩa phạm trù Baire — chúng không thể bị phân rã thành đếm được các phần "mỏng".

![Complete vs incomplete space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Cauchy_sequence_illustration.svg/500px-Cauchy_sequence_illustration.svg.png)  
*Minh họa dãy Cauchy hội tụ trong không gian đầy đủ – Nguồn: Wikimedia Commons*

Tính đầy đủ và định lý Baire giữ vai trò nền tảng vì nhiều lý do. Thứ nhất, định lý điểm bất động Banach cần tính đầy đủ để đảm bảo dãy lặp từ một ánh xạ co hội tụ đến điểm bất động duy nhất. Thứ hai, không gian Banach — đối tượng cơ bản của giải tích hàm — được định nghĩa chính là không gian vector định chuẩn đầy đủ. Thứ ba, định lý Baire thường được dùng để chứng minh sự tồn tại của các đối tượng có tính chất "điển hình" (generic), chẳng hạn hàm liên tục nhưng không đâu khả vi. Cuối cùng, định lý Baire cho thấy sự khác biệt giữa các cách hiểu về "độ lớn" của một tập hợp: một tập có thể trù mật (dense) nhưng vẫn gầy (meager), như trường hợp của $\mathbb{Q}$ trong $\mathbb{R}$.

Trong bài học này, chúng ta sẽ tìm hiểu định nghĩa và các ví dụ về không gian metric đầy đủ ($\mathbb{R}^n$, đoạn đóng, không gian hàm $C([0,1])$, không gian dãy $\ell^p$), các tính chất cơ bản (như mối liên hệ với tập con đóng và dãy tập đóng lồng nhau), phép đầy đủ hóa (completion), các khái niệm tập không đâu trù mật, tập gầy, tập phần dư (residual), cùng chứng minh và một số ứng dụng của Định lý phạm trù Baire.

---

## 🗺️ Bản đồ kiến thức nền: Tính đầy đủ và Phạm trù Baire là gì?

### 1. Dãy Cauchy & Không gian Metric Đầy đủ (Complete Metric Space)
- **Bản chất:** Một dãy $$(x_n)$$ là **dãy Cauchy** nếu các phần tử tiến sát lại gần *nhau* ($$d(x_m, x_n) \to 0$$) mà không cần biết trước giới hạn là ai. Không gian gọi là **đầy đủ** nếu **mọi dãy Cauchy đều hội tụ** về một điểm *nằm trong* không gian đó.
- **Lưu ý tô-pô quan trọng:** Tính đầy đủ là tính chất **metric**, KHÔNG phải bất biến tô-pô! (Khoảng mở $$(0, 1)$$ đồng phôi với $$\mathbb{R}$$, nhưng $$\mathbb{R}$$ đầy đủ còn $$(0, 1)$$ bị thủng hai đầu mút nên không đầy đủ!)

### 2. Nguyên lý Ánh xạ co Banach (Banach Fixed-Point Theorem)
- **Bản chất:** Nếu $$T: X \to X$$ co mọi khoảng cách lại theo tỉ lệ $$k < 1$$ ($$d(Tx, Ty) \le k\,d(x, y)$$) trên một không gian **đầy đủ**, thì lặp lại $$x_{n+1} = T(x_n)$$ tạo ra một dãy Cauchy — và tính đầy đủ bảo đảm tồn tại **duy nhất một điểm bất động $$x^* = T(x^*)$$**! Đây là động cơ đứng sau định lý tồn tại nghiệm phương trình vi phân Picard–Lindelöf và thuật toán giải hệ phương trình số.

### 3. Định lý Phạm trù Baire (Baire Category Theorem)
- **Bản chất:** Một không gian metric đầy đủ **không bao giờ** là hợp đếm được của các tập "mỏng manh" (tập đóng có phần trong rỗng — *nowhere dense*). Nói cách khác, giao đếm được của các tập mở trù mật vẫn **trù mật**! Định lý này sinh ra vô số chứng minh tồn tại kỳ diệu (như chứng minh hầu hết các hàm liên tục trên $$[0,1]$$ đều **không khả vi tại bất kỳ điểm nào**!).

---

## 🧮 Ví dụ tính tay cầm tay chỉ việc

### Ví dụ 1: Dãy Cauchy trong $$\mathbb{Q}$$ hội tụ vào "lỗ thủng" $$\sqrt{2}$$
Xét dãy lặp Newton–Babylon bắt đầu từ $$x_0 = 1 \in \mathbb{Q}$$:
$$
x_{n+1} = \frac{1}{2}\left(x_n + \frac{2}{x_n}\right).
$$
Tính tay 4 số hạng đầu tiên:
- $$x_0 = 1$$.
- $$x_1 = \frac{1}{2}(1 + 2) = \frac{3}{2} = 1.5$$.
- $$x_2 = \frac{1}{2}\left(\frac{3}{2} + \frac{4}{3}\right) = \frac{17}{12} \approx 1.41667$$.
- $$x_3 = \frac{1}{2}\left(\frac{17}{12} + \frac{24}{17}\right) = \frac{577}{408} \approx 1.4142157$$.

Mọi $$x_n$$ đều là **phân số hữu tỉ**, sai số giảm bình phương cực nhanh ($$\lvert x_3 - x_2\rvert < 0.0025$$) nên $$(x_n)$$ là một **dãy Cauchy trong $$\mathbb{Q}$$**. Nhưng nếu giới hạn $$L$$ tồn tại thì $$L = \frac{1}{2}(L + 2/L) \implies L^2 = 2 \implies L = \sqrt{2} \notin \mathbb{Q}$$! Do đó $$\mathbb{Q}$$ **không đầy đủ** — và $$\mathbb{R}$$ chính là **sự làm đầy đủ** (completion) của $$\mathbb{Q}$$!

### Ví dụ 2: Chứng minh $$\mathbb{R}$$ không đếm được trong 3 dòng bằng Định lý Baire
Giả sử phản chứng $$\mathbb{R}$$ đếm được, tức viết được dưới dạng hợp đếm được của từng điểm đơn lẻ:
$$
\mathbb{R} = \bigcup_{n=1}^\infty \{x_n\}.
$$
- Mỗi tập đơn điểm $$F_n = \{x_n\}$$ là tập **đóng** và có **phần trong rỗng** (không chứa bất kỳ khoảng mở $$(a, b)$$ nào), nên $$F_n$$ **không đâu trù mật**.
- Nhưng $$\mathbb{R}$$ là một không gian metric đầy đủ khác rỗng! Theo **Định lý Phạm trù Baire**, $$\mathbb{R}$$ **không thể** là hợp đếm được của các tập không đâu trù mật $$\implies$$ mâu thuẫn! Vậy $$\mathbb{R}$$ bắt buộc **không đếm được**!

### Khung giải thích: Ba bước khóa chặt sức mạnh của Tính đầy đủ (nên đọc chậm)

#### Bước 1: Dãy Cauchy giúp kiểm tra hội tụ mà KHÔNG cần biết trước giới hạn
Khi giải một phương trình vi phân hay tích phân phức tạp, bạn chưa biết nghiệm trông như thế nào. Bạn chỉ dựng được một dãy xấp xỉ $$(x_n)$$ mà $$d(x_{n+1}, x_n) \le k^n d(x_1, x_0)$$. Tổng cấp số nhân hữu hạn chứng tỏ $$(x_n)$$ là dãy Cauchy.

#### Bước 2: Tính đầy đủ biến "dãy Cauchy" thành "nghiệm thật sự tồn tại"
Trong không gian đầy đủ (như $$\mathbb{R}^n$$, $$C[a,b]$$ với chuẩn đều, không gian Banach/Hilbert), dãy Cauchy lập tức có giới hạn $$x^* \in X$$! Nếu không gian chưa đầy đủ, ta luôn có thể "trám kín mọi lỗ thủng" bằng phép làm đầy đủ duy nhất (như $$\mathbb{Q} \hookrightarrow \mathbb{R}$$).

#### Bước 3: Giao các hình cầu lồng nhau (Cantor) $$\implies$$ Phạm trù Baire
Trên không gian đầy đủ, bất kỳ dãy tập đóng khác rỗng lồng nhau $$F_1 \supseteq F_2 \supseteq \cdots$$ có đường kính $$\operatorname{diam}(F_n) \to 0$$ đều có giao khác rỗng (Định lý Cantor). Dùng đúng bổ đề này để né lần lượt từng tập đóng không đâu trù mật $$E_1, E_2, \dots$$ ta chứng minh được Định lý Baire!

#### Bước 4: Khám phá thế giới "điển hình" của giải tích hàm
Định lý Baire là nền móng của bộ ba trụ cột Giải tích Hàm: Nguyên lý bị chặn đều (Banach–Steinhaus), Định lý ánh xạ mở và Định lý đồ thị đóng — những công cụ cốt lõi của bậc cao học toán và vật lý lý thuyết.

$$
\text{Dãy Cauchy}
\;\xrightarrow{\;\text{Tính đầy đủ}\;}\;
\begin{cases}
\text{Ánh xạ co Banach} \implies \text{Nghiệm duy nhất }x^* = T(x^*) \\
\text{Định lý Cantor} \implies \text{Phạm trù Baire} \implies \text{Giải tích Hàm}
\end{cases}
$$

---

## 🔍 Không gian metric đầy đủ

### 1. Định nghĩa và các tính chất đầu tiên

Trước hết, ta nhắc lại khái niệm dãy Cauchy. Một dãy $(x_n)$ trong không gian metric $(X, d)$ được gọi là **dãy Cauchy** nếu các phần tử của nó tiến gần nhau tùy ý khi chỉ số đủ lớn:

$$
\forall \varepsilon > 0: \exists N \in \mathbb{N}: \forall m,n \geq N: d(x_m, x_n) < \varepsilon
$$

Một dãy Cauchy có xu hướng hội tụ, nhưng giới hạn của nó có thể không thuộc không gian $X$ đang xét.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không gian metric đầy đủ):**  
Không gian metric $(X, d)$ được gọi là **đầy đủ** (complete) nếu mọi dãy Cauchy trong $X$ đều hội tụ đến một điểm thuộc $X$.
</div>

Một tính chất cơ bản là mọi dãy hội tụ đều là dãy Cauchy. Thật vậy, nếu $x_n \to x$, thì với mọi $\varepsilon > 0$, tồn tại $N$ sao cho $d(x_n, x) < \varepsilon/2$ với mọi $n \geq N$. Khi đó, với mọi $m, n \geq N$:

$$
d(x_m, x_n) \leq d(x_m, x) + d(x, x_n) < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
$$

Do đó $(x_n)$ là dãy Cauchy. Chiều ngược lại không đúng nói chung, và chính việc đòi hỏi chiều ngược lại đúng định nghĩa nên lớp không gian metric đầy đủ.

---

### 2. Các ví dụ về không gian đầy đủ

Ví dụ cơ bản nhất là không gian Euclid $\mathbb{R}^n$ với metric $d_2$. Nếu $(\mathbf{x}^{(k)})$ là một dãy Cauchy trong $\mathbb{R}^n$, thì từng tọa độ $(x_i^{(k)})$ ($i = 1, \ldots, n$) là một dãy Cauchy trong $\mathbb{R}$. Vì $\mathbb{R}$ đầy đủ, mỗi dãy tọa độ hội tụ đến một giá trị $x_i \in \mathbb{R}$, suy ra $\mathbf{x}^{(k)} \to (x_1, \ldots, x_n) \in \mathbb{R}^n$.

Một ví dụ quen thuộc khác là đoạn đóng $[a,b] \subset \mathbb{R}$. Nếu $(x_n)$ là dãy Cauchy trong $[a,b]$, thì vì $\mathbb{R}$ đầy đủ nên $x_n \to x \in \mathbb{R}$; lại vì $[a,b]$ đóng trong $\mathbb{R}$ nên $x \in [a,b]$. Tổng quát hơn, mọi tập con đóng của một không gian đầy đủ đều đầy đủ.

Ngược lại, khoảng mở $(0,1)$ không đầy đủ: dãy $x_n = 1/n$ là dãy Cauchy trong $(0,1)$ nhưng giới hạn $0 \notin (0,1)$. Tương tự, tập số hữu tỉ $\mathbb{Q}$ với metric Euclid cũng không đầy đủ vì tồn tại dãy số hữu tỉ hội tụ đến $\sqrt{2} \notin \mathbb{Q}$. Đây cũng là động lực lịch sử dẫn đến việc xây dựng tập số thực $\mathbb{R}$ từ $\mathbb{Q}$.

Trong giải tích hàm, không gian các hàm liên tục $C([0,1], \mathbb{R})$ với metric đều (chuẩn supremum):

$$
d_\infty(f,g) = \sup_{x \in [0,1]} |f(x) - g(x)|
$$

là một không gian metric đầy đủ. Nếu $(f_n)$ là dãy Cauchy theo $d_\infty$, thì với mỗi $x \in [0,1]$, dãy số thực $(f_n(x))$ là Cauchy nên hội tụ đến một giá trị $f(x)$. Hơn nữa, tính chất Cauchy đều kéo theo $f_n \to f$ đều trên $[0,1]$, và giới hạn đều của một dãy hàm liên tục là hàm liên tục, nên $f \in C([0,1])$.

Cuối cùng, với mọi $p \geq 1$, không gian dãy $\ell^p$ gồm các dãy số $(x_n)$ thỏa mãn $\sum_{n=1}^\infty |x_n|^p < \infty$, trang bị metric:

$$
d((x_n), (y_n)) = \left(\sum_{n=1}^\infty |x_n - y_n|^p\right)^{1/p}
$$

là không gian metric đầy đủ. Chứng minh sử dụng bất đẳng thức Minkowski và tính đầy đủ của $\mathbb{R}$.

---

### 3. Tính chất của không gian đầy đủ

<div class="textbook-theorem" markdown="1">
**Định lý 1 (Không gian con đóng):**  
Nếu $X$ đầy đủ và $Y \subseteq X$ là tập con đóng, thì $Y$ (với metric cảm sinh) cũng đầy đủ.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Giả sử $(y_n)$ là dãy Cauchy trong $Y$. Khi đó $(y_n)$ cũng là dãy Cauchy trong $X$, nên $y_n \to x \in X$ do $X$ đầy đủ. Vì $Y$ đóng trong $X$, ta suy ra $x \in Y$.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:** Đoạn $[a,b]$ đầy đủ vì nó là tập con đóng của $\mathbb{R}$.
</div>

---

<div class="textbook-theorem" markdown="1">
**Định lý 2 (Chiều ngược lại):**  
Nếu $Y$ là không gian con đầy đủ của một không gian metric $X$ bất kỳ, thì $Y$ đóng trong $X$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Lấy $x \in \operatorname{cl}(Y)$. Tồn tại dãy $(y_n)$ trong $Y$ sao cho $y_n \to x$ trong $X$. Vì $(y_n)$ hội tụ nên nó là dãy Cauchy trong $Y$. Do $Y$ đầy đủ, tồn tại $y \in Y$ sao cho $y_n \to y$. Bởi tính duy nhất của giới hạn, $x = y \in Y$, suy ra $\operatorname{cl}(Y) = Y$.
</div>

Như vậy, trong một không gian metric đầy đủ $X$, một tập con $Y \subseteq X$ là đầy đủ khi và chỉ khi $Y$ đóng trong $X$.

---

<div class="textbook-theorem" markdown="1">
**Định lý 3 (Định lý Cantor về dãy tập đóng lồng nhau):**  
Cho $X$ là không gian metric đầy đủ và $F_1 \supseteq F_2 \supseteq F_3 \supseteq \cdots$ là một dãy giảm các tập con đóng, khác rỗng với $\operatorname{diam}(F_n) \to 0$. Khi đó giao $\bigcap_{n=1}^\infty F_n$ gồm đúng một điểm.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
Chọn $x_n \in F_n$ với mỗi $n$. Với $m \ge n$, cả $x_m$ và $x_n$ đều thuộc $F_n$, nên $d(x_m, x_n) \le \operatorname{diam}(F_n) \to 0$. Do đó $(x_n)$ là dãy Cauchy, và vì $X$ đầy đủ nên $x_n \to x \in X$. Với mọi $n$, phần đuôi $\{x_n, x_{n+1}, \ldots\}$ nằm trong tập đóng $F_n$, suy ra $x \in F_n$, tức $x \in \bigcap_{n=1}^\infty F_n$. Nếu có điểm $y \in \bigcap_{n=1}^\infty F_n$, thì $d(x, y) \le \operatorname{diam}(F_n) \to 0$, nên $x = y$.
</div>

Định lý này được dùng phổ biến trong các chứng minh sự tồn tại và các định lý điểm bất động.

---

### 4. Phép đầy đủ hóa không gian metric (Completion)

Mọi không gian metric chưa đầy đủ đều có thể được mở rộng một cách duy nhất thành một không gian đầy đủ chứa nó như một tập con trù mật — gọi là **phép đầy đủ hóa** (completion). Ví dụ quen thuộc nhất là $\mathbb{R}$ là đầy đủ hóa của $\mathbb{Q}$.

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý đầy đủ hóa):**  
Mọi không gian metric $(X, d)$ đều có một **đầy đủ hóa** $(\overline{X}, \overline{d})$, duy nhất sai khác một phép đẳng cự cố định trên $X$, thỏa mãn:
- $(\overline{X}, \overline{d})$ là không gian metric đầy đủ,
- $X$ nhúng đẳng cự vào $\overline{X}$,
- Ảnh của $X$ trù mật trong $\overline{X}$.
</div>

**Ý tưởng xây dựng:**  
Xét tập các lớp tương đương của các dãy Cauchy trong $X$, trong đó hai dãy Cauchy $(x_n)$ và $(y_n)$ tương đương nếu $d(x_n, y_n) \to 0$. Khoảng cách giữa hai lớp được định nghĩa bởi $\lim_{n \to \infty} d(x_n, y_n)$.

<div class="textbook-proof" markdown="1">
**Chứng minh:** Các bước kiểm tra mang tính kỹ thuật nhưng trực tiếp; xem chi tiết trong Munkres, §43.
</div>

**Ví dụ:**
- Đầy đủ hóa của $\mathbb{Q}$ là $\mathbb{R}$.
- Đầy đủ hóa của $(0,1)$ là $[0,1]$.
- Đầy đủ hóa của $C([0,1])$ với metric $L^1$ là không gian $L^1([0,1])$.

---

## 🎯 Tập không đâu trù mật và phạm trù Baire

### 1. Tập không đâu trù mật (Nowhere Dense Sets)

Khái niệm không đâu trù mật cung cấp một cách đo "độ nhỏ" của tập hợp theo nghĩa tô-pô: một tập là không đâu trù mật nếu bao đóng của nó không chứa bất kỳ tập mở khác rỗng nào.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Không đâu trù mật):**  
Tập con $A \subseteq X$ được gọi là **không đâu trù mật** (nowhere dense) nếu $\operatorname{int}(\operatorname{cl}(A)) = \emptyset$.
</div>

Điều này có nghĩa là $\operatorname{cl}(A)$ không có điểm trong nào — không tồn tại quả cầu mở nào nằm trọn trong $\operatorname{cl}(A)$.

---

**Ví dụ:**
- **Ví dụ 1:** $\{0\}$ không đâu trù mật trong $\mathbb{R}$, vì $\operatorname{cl}(\{0\}) = \{0\}$ và $\operatorname{int}(\{0\}) = \emptyset$.
- **Ví dụ 2:** $\mathbb{N}$ không đâu trù mật trong $\mathbb{R}$, vì $\operatorname{cl}(\mathbb{N}) = \mathbb{N}$ và $\operatorname{int}(\mathbb{N}) = \emptyset$.
- **Ví dụ 3:** Tập Cantor $C$ không đâu trù mật trong $[0,1]$: $C$ compact, hoàn toàn bất liên thông, hoàn hảo, có độ đo $0$, với $\operatorname{cl}(C) = C$ và $\operatorname{int}(C) = \emptyset$.
- **Ví dụ 4:** $[0,1]$ **không** phải là tập không đâu trù mật trong $\mathbb{R}$, vì $\operatorname{int}(\operatorname{cl}([0,1])) = (0,1) \neq \emptyset$.
- **Ví dụ 5:** $\mathbb{Q}$ **không** phải là tập không đâu trù mật trong $\mathbb{R}$, vì $\operatorname{cl}(\mathbb{Q}) = \mathbb{R}$ và $\operatorname{int}(\mathbb{R}) = \mathbb{R} \neq \emptyset$.

---

<div class="textbook-theorem" markdown="1">
**Mệnh đề:**  
$A$ không đâu trù mật trong $X$ khi và chỉ khi $X \setminus \operatorname{cl}(A)$ trù mật trong $X$.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**  
$A$ không đâu trù mật $\iff \operatorname{int}(\operatorname{cl}(A)) = \emptyset \iff \operatorname{cl}(A)$ không chứa quả cầu mở nào $\iff$ mọi quả cầu mở đều cắt $X \setminus \operatorname{cl}(A) \iff X \setminus \operatorname{cl}(A)$ trù mật trong $X$.
</div>

---

### 2. Phạm trù Baire và tập gầy (Meager Sets)

Khái niệm phạm trù Baire phân loại các tập con của không gian tô-pô thành các tập "nhỏ" (tập gầy / phạm trù thứ nhất) và "lớn" (tập phạm trù thứ hai / tập phần dư). Lưu ý rằng thuật ngữ *category* ở đây là cách gọi lịch sử từ công trình của Baire, không liên quan đến lý thuyết phạm trù (category theory) trong đại số.

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập gầy / Phạm trù thứ nhất):**  
Tập con $A \subseteq X$ được gọi là **tập gầy** (meager hay first category) nếu $A = \bigcup_{n=1}^\infty A_n$, trong đó mỗi $A_n$ là tập không đâu trù mật.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập không gầy / Phạm trù thứ hai):**  
Tập con $A \subseteq X$ được gọi là **không gầy** (nonmeager hay second category) nếu $A$ không phải là tập gầy.
</div>

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tập phần dư – Residual/Comeager):**  
Tập con $A \subseteq X$ được gọi là **tập phần dư** (residual hay comeager) nếu phần bù $X \setminus A$ là tập gầy.
</div>

---

**Ví dụ:**
- **Ví dụ 1:** Mọi tập đếm được trong $\mathbb{R}$ đều là tập gầy. Đặc biệt, $\mathbb{Q} = \bigcup_{n} \{r_n\}$ là hợp đếm được của các tập đơn điểm không đâu trù mật, nên $\mathbb{Q}$ là tập gầy.
- **Ví dụ 2:** Tập Cantor $C$ không đâu trù mật trong $[0,1]$, nên cũng là tập gầy.
- **Ví dụ 3:** $\mathbb{R} \setminus \mathbb{Q}$ là tập phần dư trong $\mathbb{R}$ vì phần bù của nó là $\mathbb{Q}$ (tập gầy).

Ví dụ của $\mathbb{Q}$ cho thấy tính trù mật, tính phần dư và độ đo đầy đủ là những khái niệm khác nhau về "độ lớn": $\mathbb{Q}$ trù mật trong $\mathbb{R}$ nhưng lại là tập gầy và có độ đo $0$, còn $\mathbb{R} \setminus \mathbb{Q}$ vừa có độ đo đầy đủ vừa là tập phần dư.

---

### 3. Định lý phạm trù Baire

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý phạm trù Baire – Dạng 1):**  
Cho $(X, d)$ là một không gian metric đầy đủ. Nếu $U_1, U_2, U_3, \ldots$ là một dãy các tập mở và trù mật trong $X$, thì

$$
\bigcap_{n=1}^\infty U_n \text{ trù mật trong } X.
$$
</div>

Nói cách khác, giao đếm được của các tập mở trù mật trong một không gian metric đầy đủ vẫn là tập trù mật.

---

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý phạm trù Baire – Dạng 2):**  
Một không gian metric đầy đủ khác rỗng $X$ không thể biểu diễn thành hợp đếm được của các tập không đâu trù mật.
</div>

Tương đương: mọi không gian metric đầy đủ khác rỗng đều thuộc phạm trù thứ hai (không gầy).

**Chứng minh Dạng 1 $\Rightarrow$ Dạng 2:**  
Giả sử phản chứng $X = \bigcup_{n=1}^\infty A_n$ với mỗi $A_n$ không đâu trù mật. Khi đó $U_n = X \setminus \operatorname{cl}(A_n)$ là tập mở và trù mật trong $X$ theo mệnh đề trên. Theo Dạng 1, $\bigcap_{n=1}^\infty U_n$ trù mật trong $X$, nên khác rỗng (do $X \neq \emptyset$). Tuy nhiên:
$\bigcap_{n=1}^\infty U_n = X \setminus \bigcup_{n=1}^\infty \operatorname{cl}(A_n) \subseteq X \setminus \bigcup_{n=1}^\infty A_n = \emptyset$, mâu thuẫn.

---

**Chứng minh Định lý phạm trù Baire (Dạng 1):**

Cho $X$ đầy đủ và $U_1, U_2, \ldots$ là các tập mở trù mật. Ta cần chứng minh $\left(\bigcap_{n=1}^\infty U_n\right) \cap V \neq \emptyset$ với mọi tập mở khác rỗng $V \subseteq X$.

- **Bước 1:** Vì $U_1$ trù mật nên $U_1 \cap V$ là tập mở khác rỗng. Chọn quả cầu mở $B_1 = B(x_1, r_1)$ với $0 < r_1 < 1$ sao cho quả cầu đóng $\overline{B}(x_1, r_1) \subseteq U_1 \cap V$.
- **Bước 2:** Vì $U_2$ trù mật nên $U_2 \cap B_1$ là tập mở khác rỗng. Chọn $B_2 = B(x_2, r_2)$ với $0 < r_2 < 1/2$ sao cho $\overline{B}(x_2, r_2) \subseteq U_2 \cap B_1$.
- **Quy nạp:** Với mỗi $n \ge 2$, chọn $B_n = B(x_n, r_n)$ với $0 < r_n < 1/n$ sao cho $\overline{B}(x_n, r_n) \subseteq U_n \cap B_{n-1}$.

Với mọi $m > n$, ta có $x_m, x_n \in B_n$, suy ra $d(x_n, x_m) < 2r_n < 2/n \to 0$. Vậy $(x_n)$ là dãy Cauchy. Vì $X$ đầy đủ, tồn tại $x \in X$ sao cho $x_n \to x$.

Với mọi $n \ge 1$, phần đuôi $\{x_n, x_{n+1}, \ldots\}$ nằm trong $\overline{B}(x_n, r_n)$. Vì $\overline{B}(x_n, r_n)$ là tập đóng, giới hạn $x$ thuộc $\overline{B}(x_n, r_n) \subseteq U_n \cap V$ (với $n=1$ ta có $\overline{B}(x_1, r_1) \subseteq U_1 \cap V$, và với $n \ge 2$ ta có $\overline{B}(x_n, r_n) \subseteq U_n \cap B_{n-1} \subseteq U_n \cap V$). Do đó $x \in \left(\bigcap_{n=1}^\infty U_n\right) \cap V$. Vậy $\bigcap_{n=1}^\infty U_n$ trù mật trong $X$.

Lưu ý rằng chứng minh trên mang tính kiến thiết ở chỗ chỉ ra trực tiếp cách tìm một điểm trong giao thông qua dãy quả cầu lồng nhau.

---

### 4. Một số ứng dụng của Định lý phạm trù Baire

**Ứng dụng 1: Sự tồn tại hàm liên tục không đâu khả vi**

<div class="textbook-theorem" markdown="1">
**Định lý (Banach):**  
Tập hợp các hàm liên tục trên $[0,1]$ không khả vi tại bất kỳ điểm nào là một tập phần dư trong $C([0,1])$.
</div>

Chứng minh kết hợp Định lý phạm trù Baire với tính đầy đủ của $(C([0,1]), d_\infty)$. Kết quả này cho thấy theo nghĩa phạm trù Baire, một hàm liên tục "điển hình" không khả vi ở bất kỳ đâu.

---

**Ứng dụng 2: Tính "điển hình" của số vô tỉ**

Tập $\mathbb{R} \setminus \mathbb{Q}$ là tập phần dư trong $\mathbb{R}$, nên theo nghĩa Baire, hầu hết các số thực là số vô tỉ (tương đồng với kết quả theo nghĩa độ đo Lebesgue khi $\mathbb{Q}$ có độ đo $0$).

---

**Ứng dụng 3: Định lý ánh xạ mở (Open Mapping Theorem)**

<div class="textbook-theorem" markdown="1">
**Định lý (Định lý ánh xạ mở – Giải tích hàm):**  
Nếu $T: X \to Y$ là một toán tử tuyến tính liên tục toàn ánh giữa hai không gian Banach, thì $T$ là ánh xạ mở.
</div>

Ý tưởng chứng minh sử dụng trực tiếp Định lý phạm trù Baire: viết $Y = \bigcup_{n=1}^\infty T(B_n(0))$, suy ra tồn tại $n$ sao cho bao đóng của $T(B_n(0))$ có điểm trong, từ đó chứng minh $T$ mở tại gốc tọa độ và mở trên toàn không gian.

---

**Ứng dụng 4: Nguyên lý bị chặn đều (Banach–Steinhaus)**

<div class="textbook-theorem" markdown="1">
**Định lý (Banach–Steinhaus):**  
Một họ các toán tử tuyến tính liên tục $\{T_\alpha\}$ từ không gian Banach $X$ vào không gian định chuẩn $Y$ bị chặn từng điểm thì bị chặn đều theo chuẩn toán tử.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Áp dụng Định lý phạm trù Baire cho dãy tập đóng $F_n = \{x \in X : \sup_\alpha \|T_\alpha x\| \le n\}$.
</div>

---

## 🧠 Tài liệu kinh điển và tham khảo

### Các công trình kinh điển

1. **René Baire** – *"Sur les fonctions de variables réelles"* (1899)  
   *Giới thiệu khái niệm phạm trù và chứng minh Định lý phạm trù Baire.*

2. **Stefan Banach** – *"Sur les opérations dans les ensembles abstraits"* (1922)  
   *Xây dựng lý thuyết không gian Banach và tính đầy đủ.*

3. **Maurice Fréchet** – *"Sur quelques points du calcul fonctionnel"* (1906)  
   *Nghiên cứu không gian metric.*

### Giáo trình

4. **James R. Munkres** – *Topology*, 2nd Ed., **§27, §48: Baire Category**

5. **Walter Rudin** – *Principles of Mathematical Analysis*, **Chapter 3**  
   *Không gian đầy đủ.*

6. **John C. Oxtoby** – *Measure and Category*, 1971  
   *So sánh chi tiết giữa độ đo và phạm trù Baire.*

7. **Michael Reed & Barry Simon** – *Functional Analysis*, **Chapter 1**  
   *Các ứng dụng của định lý Baire trong giải tích hàm.*

---

## 🔗 Ứng dụng và liên kết

### Giải tích hàm
**Không gian Banach:** Không gian vector định chuẩn đầy đủ. Định lý Baire dẫn đến ba kết quả trụ cột: Định lý ánh xạ mở, Định lý đồ thị đóng và Nguyên lý bị chặn đều.

### Giải tích thực
**Chứng minh tồn tại:** Định lý Baire cho phép chứng minh sự tồn tại của các đối tượng có tính chất điển hình (như hàm liên tục không đâu khả vi) mà không cần xây dựng tường minh từng công thức.

### Lý thuyết tập mô tả (Descriptive Set Theory)
**Không gian Ba Lan (Polish Spaces):** Các không gian metric đầy đủ và khả ly, nơi Định lý phạm trù Baire là công cụ cơ bản.

### Phương trình vi phân
**Định lý điểm bất động:** Định lý điểm bất động Banach dựa trên tính đầy đủ để giải các phương trình vi phân thường (ODE) và đạo hàm riêng (PDE).

### Lý thuyết xác suất
**Đầy đủ hóa không gian đo:** Bổ sung các tập con của tập có độ đo $0$ giúp đảm bảo tính đo được ổn định.

---

## Video tham khảo

- **xem trước** [The Baire Category Theorem - Dr Joel Feinstein](https://www.youtube.com/watch?v=dvDo0RFAhqw) — University of Nottingham, tiếng Anh. Bài giảng của Joel Feinstein về Định lý phạm trù Baire, đúng trọng tâm của bài.
- [Chương 1: Không gian metric - Bài 5: Dãy Cauchy - Không gian metric đầy.](https://www.youtube.com/watch?v=V4BpOt3mXkc) — Cao Anh Hào-K49-SPTO-HPU2, tiếng Việt. Trình bày về dãy Cauchy và không gian metric đầy đủ bằng tiếng Việt.

## 🧩 Bài tập

### Tính đầy đủ

1. **Kiểm tra tính đầy đủ:**  
   Chứng minh chi tiết đoạn $[0,1]$ là không gian metric đầy đủ.

2. **Không gian không đầy đủ:**  
   Chứng minh $(0,1)$ không đầy đủ bằng cách chỉ ra một dãy Cauchy cụ thể.

3. **Không gian con đóng:**  
   Chứng minh nếu $Y$ đóng trong không gian đầy đủ $X$ thì $Y$ đầy đủ.

4. **Đầy đủ hóa:**  
   Tìm đầy đủ hóa của $\mathbb{Q} \cap [0,1]$.

### Dãy Cauchy

5. **Kiểm tra dãy Cauchy:**  
   Với $x_n = \sum_{i=1}^n \frac{1}{i!}$, chứng minh $(x_n)$ là dãy Cauchy trong $\mathbb{R}$.

6. **Dãy không Cauchy:**  
   Đưa ra một ví dụ về dãy số không phải dãy Cauchy.

7. **Tích của không gian đầy đủ:**  
   Nếu $X$ và $Y$ đầy đủ thì $X \times Y$ với metric tích có đầy đủ không? Chứng minh.

### Tập không đâu trù mật

8. **Kiểm tra tính không đâu trù mật:**  
   Chứng minh $\mathbb{N}$ không đâu trù mật trong $\mathbb{R}$.

9. **Tập Cantor:**  
   Phác thảo cách xây dựng tập Cantor $C$ và giải thích vì sao $C$ không đâu trù mật, có độ đo $0$, nhưng không đếm được và là tập hoàn hảo.

10. **Trù mật nhưng gầy:**  
    Giải thích vì sao $\mathbb{Q}$ vừa trù mật vừa là tập gầy trong $\mathbb{R}$.

### Định lý phạm trù Baire

11. **Ứng dụng định lý Baire:**  
    Dùng Định lý phạm trù Baire chứng minh $\mathbb{R}$ không thể biểu diễn thành hợp đếm được của các tập đếm được (từ đó suy ra $\mathbb{R}$ không đếm được).

12. **Tập số vô tỉ là tập phần dư:**  
    Trình bày chứng minh chi tiết rằng $\mathbb{R} \setminus \mathbb{Q}$ là tập phần dư trong $\mathbb{R}$.

13. **Hàm liên tục không đâu khả vi:**  
    Tìm hiểu phác thảo chứng minh định lý Banach về sự tồn tại của hàm liên tục không đâu khả vi.

### Ứng dụng

14. **Định lý điểm bất động Banach:**  
    Nếu $f: X \to X$ là ánh xạ co trên không gian metric đầy đủ $X$, thì $f$ có duy nhất một điểm bất động. Hãy phác thảo chứng minh.

15. **Dãy tập đóng lồng nhau:**  
    Áp dụng định lý Cantor về dãy tập đóng lồng nhau để giải phương trình bằng phương pháp xấp xỉ liên tiếp.

### Nâng cao

16. **Không gian compact địa phương:**  
    Một không gian Hausdorff compact địa phương cũng thỏa mãn Định lý phạm trù Baire (không cần cấu trúc metric đầy đủ). Lấy ví dụ với $\mathbb{R}^n$ và các đa tạp.

17. **Tập đếm được và tập gầy:**  
    Mọi tập đếm được trong $\mathbb{R}$ đều là tập gầy, nhưng tập gầy có thể không đếm được (ví dụ tập Cantor). Hãy so sánh hai khái niệm này.

18. **Định lý ánh xạ mở:**  
    Tìm hiểu phát biểu và phác thảo chứng minh Định lý ánh xạ mở sử dụng Định lý phạm trù Baire.

### Câu hỏi suy ngẫm

19. **Vai trò của tính đầy đủ:**  
    Giải thích vì sao tính đầy đủ đóng vai trò thiết yếu trong giải tích.

20. **Nghịch lý trực giác của Baire:**  
    Làm thế nào để dung hòa trực giác giữa việc $\mathbb{Q}$ trù mật trong $\mathbb{R}$ nhưng lại là tập "nhỏ" (tập gầy), trong khi $\mathbb{R} \setminus \mathbb{Q}$ là tập "lớn" (tập phần dư)?

---

## 📚 Đọc thêm

- **Munkres, Topology:** §48 (Baire Category)
- **Rudin, PMA:** Chapter 3 (Completeness)
- **Oxtoby:** *Measure and Category*
- **Kelley:** *General Topology* (Định lý Baire trong không gian tổng quát)

---

## 🎓 Tóm tắt

Trong bài học này, chúng ta đã tìm hiểu về tính đầy đủ và Định lý phạm trù Baire. Một không gian metric là đầy đủ nếu mọi dãy Cauchy đều hội tụ trong không gian đó; các ví dụ tiêu biểu gồm $\mathbb{R}^n$, đoạn đóng $[a,b]$, $C([0,1])$ với metric đều và các không gian $\ell^p$. Trong một không gian đầy đủ, tập con đầy đủ trùng khớp với tập con đóng, và mọi không gian metric đều có một đầy đủ hóa duy nhất sai khác một phép đẳng cự.

Một tập không đâu trù mật có bao đóng không chứa tập mở khác rỗng nào; tập gầy là hợp đếm được của các tập không đâu trù mật; tập phần dư là phần bù của một tập gầy. Định lý phạm trù Baire khẳng định giao đếm được của các tập mở trù mật trong không gian metric đầy đủ vẫn trù mật, hay tương đương, một không gian metric đầy đủ khác rỗng không thể là tập gầy. Đây là công cụ cơ bản trong giải tích hàm (Định lý ánh xạ mở, Nguyên lý bị chặn đều) và trong các chứng minh tồn tại các đối tượng điển hình.

**Tiếp theo:** Lecture 04.02 về **Các metric tương đương và Tính liên tục đều**.

---

*"The Baire Category Theorem is the soul of analysis."* — Anonymous

---

**Previous:** [Lecture 04.00: Metric Spaces Fundamentals](/contents/vi/topology-chapter04/04_00_Metric_Spaces_Fundamentals/)  
**Next:** [Lecture 04.02: Equivalent Metrics and Uniform Continuity](/contents/vi/topology-chapter04/04_02_Equivalent_Metrics_Uniform_Continuity/)
