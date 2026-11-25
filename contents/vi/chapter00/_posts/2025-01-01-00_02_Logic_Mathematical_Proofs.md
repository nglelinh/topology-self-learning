---
layout: post
title: "Lecture 00.02: Logic and Mathematical Proofs"
lang: vi
lang-ref: lecture-00-02
chapter: 0
lecture: 2
categories: [chapter00]
tags: [logic, proof-techniques, induction, contradiction]
description: "Logic toán học, các kỹ thuật chứng minh: trực tiếp, phản chứng, quy nạp"
---

**Logic và Chứng minh Toán học**

---

## 📖 Tổng quan

Trong giải tích năm nhất, đôi khi chỉ cần đảo vị trí hai chữ ký hiệu $$\forall$$ và $$\exists$$ là cả một định lý đổi nghĩa hoàn toàn: *"với mọi $$\varepsilon > 0$$, tại mỗi $$x$$ tồn tại $$\delta$$"* chỉ là liên tục từng điểm, còn *"với mọi $$\varepsilon > 0$$, tồn tại một $$\delta$$ dùng chung cho mọi $$x$$"* lại là liên tục đều mạnh hơn hẳn! Khi bước vào Tô-pô học — nơi ta không còn công thức đạo hàm hay tích phân để bấm máy tính, mà phải chứng minh những khẳng định trừu tượng như *"mọi không gian compact và Hausdorff đều chuẩn tắc"* — kỹ năng đọc, phủ định và thao tác trên cấu trúc logic chính là la bàn duy nhất giúp bạn không lạc đường.

Bài giảng này hệ thống hóa bốn trụ cột của tư duy chứng minh toán học: **logic mệnh đề**, **lượng từ ($$\forall, \exists$$)**, **các chiến lược chứng minh** (trực tiếp, phản đảo, phản chứng, quy nạp) và **bản đồ các lỗi logic kinh điển** mà người mới học tô-pô hay vấp phải.

**Mạch bài học:** Kiến thức cần nhớ (logic mệnh đề–phản đảo, thứ tự lượng từ & các kỹ thuật chứng minh trong tô-pô) → Giải thích: cầm tay đảo lượng từ và viết phủ định để chứng minh hàm bước nhảy gián đoạn → Trực giác & Định nghĩa hình thức → Lỗi logic phổ biến → Bài tập & Tóm tắt.

---

## Kiến thức cần nhớ: Logic toán học và Kỹ thuật chứng minh đóng vai trò gì trong Tô-pô?

### 1. Phép kéo theo $$P \Rightarrow Q$$ và sức mạnh của phản đảo $$\neg Q \Rightarrow \neg P$$

Phần lớn định lý tô-pô có dạng *"Nếu không gian $$X$$ có tính chất $$P$$ thì nó có tính chất $$Q$$"*. Rất nhiều khi đi thẳng từ $$P$$ sang $$Q$$ rất khó, nhưng đi theo mệnh đề tương đương logic là **phản đảo** ($$\neg Q \Rightarrow \neg P$$) lại ngắn gọn bất ngờ — chẳng hạn để chứng minh tập đóng nằm trong không gian compact là compact, hay chứng minh một ánh xạ là đơn ánh.

### 2. Lượng từ lồng nhau ($$\forall, \exists$$) và quy tắc phủ định cơ học

Định nghĩa không gian Hausdorff (*"$$\forall x \neq y,\; \exists U, V$$ mở sao cho $$x \in U, y \in V, U \cap V = \emptyset$$"*) hay tính compact (*"$$\forall$$ phủ mở, $$\exists$$ phủ con hữu hạn"*) đều là chuỗi lượng từ lồng nhau. Nắm vững quy tắc đổi $$\neg(\forall x, P(x)) \equiv \exists x, \neg P(x)$$ và $$\neg(\exists x, P(x)) \equiv \forall x, \neg P(x)$$ giúp bạn viết ra **chính xác điều kiện để tìm phản ví dụ** mà không bao giờ đoán mò.

### 3. Bốn công cụ chứng minh chủ lực

- **Chứng minh trực tiếp:** đi từ định nghĩa đến kết luận theo chuỗi suy diễn thuận.
- **Chứng minh phản chứng:** giả sử $$P \land \neg Q$$ rồi suy ra mâu thuẫn (cực mạnh khi chứng minh tính duy nhất của giới hạn trong không gian Hausdorff hoặc tính liên thông).
- **Quy nạp toán học:** chứng minh cho mọi bước hữu hạn $$n \in \mathbb{N}$$ (ví dụ: giao của $$n$$ tập mở là mở, tích hữu hạn của không gian Hausdorff là Hausdorff).

---

### Giải thích: Cầm tay đảo thứ tự lượng từ và phủ định định nghĩa liên tục

Hãy tự tay kiểm tra hai bài tập "nhỏ mà có võ" sau để thấy sức mạnh của lượng từ:

1. **Đảo vị trí $$\forall$$ và $$\exists$$ làm đổi chân trị hoàn toàn:**
   - Mệnh đề A: $$\forall x \in \mathbb{R},\; \exists y \in \mathbb{R} : y > x$$. **Đúng!** (Cho trước bất kỳ $$x$$ nào, ta chọn $$y = x + 1$$ phụ thuộc vào $$x$$, hiển nhiên $$x + 1 > x$$.)
   - Mệnh đề B: $$\exists y \in \mathbb{R},\; \forall x \in \mathbb{R} : y > x$$. **Sai!** (Mệnh đề này đòi hỏi một số $$y$$ *cố định* lớn hơn *mọi* số thực — vô lý vì chỉ cần chọn $$x = y$$ thì $$y > y$$ sai!)
2. **Phủ định cơ học định nghĩa liên tục $$\varepsilon$$–$$\delta$$ để bắt lỗi gián đoạn:**
   - Liên tục tại $$x_0$$: $$\forall \varepsilon > 0,\; \exists \delta > 0,\; \forall x : \lvert x - x_0 \rvert < \delta \Rightarrow \lvert f(x) - f(x_0) \rvert < \varepsilon$$.
   - Đẩy dấu phủ định $$\neg$$ đi qua từng lượng từ (và nhớ $$\neg(P \Rightarrow Q) \equiv P \land \neg Q$$):
     $$
     \exists \varepsilon_0 > 0,\; \forall \delta > 0,\; \exists x : \lvert x - x_0 \rvert < \delta \;\land\; \lvert f(x) - f(x_0) \rvert \ge \varepsilon_0.
     $$
   - **Áp dụng ngay cho hàm bước nhảy** $$f(x) = 0$$ khi $$x < 0$$ và $$f(x) = 1$$ khi $$x \ge 0$$ tại $$x_0 = 0$$: chọn $$\varepsilon_0 = \frac{1}{2}$$. Với mọi $$\delta > 0$$ bất kỳ, chọn điểm $$x = -\frac{\delta}{2}$$. Ta kiểm tra bằng tay hai điều kiện: $$\lvert x - 0 \rvert = \frac{\delta}{2} < \delta$$ (thỏa!) nhưng $$\lvert f(x) - f(0) \rvert = \lvert 0 - 1 \rvert = 1 \ge \frac{1}{2} = \varepsilon_0$$ (thỏa!). Chứng minh hoàn tất không một kẽ hở!

---

## 🎯 Từ trực giác đến hình thức

### Bản chất của một chứng minh

Có thể ví việc chứng minh toán học với suy luận của một thám tử khi kiểm tra giả thuyết "Người $A$ là thủ phạm". **Chứng minh trực tiếp** chỉ ra bằng chứng cụ thể nối từ các dữ kiện đã biết đến kết luận. **Chứng minh phản chứng** bắt đầu bằng việc giả sử điều ngược lại ($A$ không phải thủ phạm), rồi suy ra một mâu thuẫn với chứng cứ đã xác nhận. **Chứng minh phản đảo** lập luận rằng nếu một người không có mặt tại hiện trường thì người đó không thể là thủ phạm — tức chứng minh mệnh đề phản đảo của "là thủ phạm $\Rightarrow$ có mặt tại hiện trường".

Chứng minh toán học hoạt động theo nguyên tắc tương tự: đó là một chuỗi các bước suy luận hợp lệ xuất phát từ **giả thiết** (tiên đề, định nghĩa, định lý đã chứng minh) và dẫn đến **kết luận**. Mỗi bước đều phải suy ra từ các bước trước theo đúng quy tắc logic.

**Ví dụ đơn giản:**

<div class="textbook-theorem" markdown="1">
**Mệnh đề:** Nếu $n$ là số chẵn, thì $n^2$ là số chẵn.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Giả sử $n$ chẵn. Theo định nghĩa, tồn tại $k \in \mathbb{Z}$ sao cho $n = 2k$.  
Khi đó: $n^2 = (2k)^2 = 4k^2 = 2(2k^2)$.  
Vì $2k^2 \in \mathbb{Z}$, nên $n^2$ là số chẵn. ∎
</div>

Cấu trúc suy luận đơn giản này chính là khuôn mẫu cơ bản cho mọi chứng minh tô-pô phức tạp hơn.

---

## 📐 Định nghĩa hình thức

### 1. Logic mệnh đề (Propositional Logic)

<div class="textbook-theorem" markdown="1">
**Mệnh đề (Proposition):** Một phát biểu khẳng định có giá trị chân lý xác định: hoặc đúng (T), hoặc sai (F).
</div>

**Ví dụ:**
- "$2 + 2 = 4$" $\to$ Đúng (T).
- "Paris là thủ đô của Đức" $\to$ Sai (F).
- "$x > 5$" $\to$ Không phải mệnh đề (vì tính đúng/sai phụ thuộc vào giá trị của $x$).

#### Các phép toán (liên từ) logic

| Ký hiệu | Tên | Định nghĩa | Ví dụ |
|---------|-----|------------|-------|
| $\neg P$ | Phủ định (NOT) | Đảo giá trị chân lý của $P$ | Nếu $P$: "$n$ chẵn", $\neg P$: "$n$ lẻ" |
| $P \land Q$ | Hội (AND) | Đúng khi cả $P$ và $Q$ cùng đúng | "$n$ chẵn VÀ $n > 10$" |
| $P \lor Q$ | Tuyển (OR) | Đúng khi ít nhất một trong $P, Q$ đúng | "$n$ chẵn HOẶC $n > 10$" |
| $P \Rightarrow Q$ | Kéo theo (Implication) | "Nếu $P$ thì $Q$" | "Nếu $n$ chẵn thì $n^2$ chẵn" |
| $P \Leftrightarrow Q$ | Tương đương (Biconditional) | $P \Rightarrow Q$ và $Q \Rightarrow P$ | "$n$ chẵn $\Leftrightarrow n = 2k$" |

**Bảng chân trị của phép kéo theo:**

| $P$ | $Q$ | $P \Rightarrow Q$ |
|---|---|-------|
| T | T | T |
| T | F | F |
| F | T | T |
| F | F | T |

**Lưu ý quan trọng:** Phép kéo theo $P \Rightarrow Q$ luôn đúng khi giả thiết $P$ sai (gọi là *đúng một cách hiển nhiên / chân lý rỗng*, tiếng Anh: *vacuous truth*).

**Ví dụ:** Mệnh đề "Nếu $1 + 1 = 3$ thì tôi là Napoleon" là mệnh đề ĐÚNG theo bảng chân trị vì giả thiết "$1 + 1 = 3$" sai.

![Logic gates visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9f/Venn_diagram_for_OR.svg/300px-Venn_diagram_for_OR.svg.png)  
*Biểu đồ Venn cho phép tuyển (OR) - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Venn_diagram_for_OR.svg)*

---

### 2. Lượng từ (Quantifiers)

#### Lượng từ phổ quát ($\forall$)

**$\forall x \in S: P(x)$** đọc là "Với mọi $x$ thuộc $S$, $P(x)$ đúng".

**Ví dụ:**
- $\forall n \in \mathbb{N}: n^2 \ge 0$
- $\forall x \in \mathbb{R}: x^2 - 1 = (x - 1)(x + 1)$

**Phủ định:**
$$
\neg(\forall x: P(x)) \equiv \exists x: \neg P(x)
$$

"Không phải mọi $x$ đều thỏa $P$" $\iff$ "Tồn tại ít nhất một $x$ không thỏa $P$".

#### Lượng từ tồn tại ($\exists$)

**$\exists x \in S: P(x)$** đọc là "Tồn tại $x$ thuộc $S$ sao cho $P(x)$ đúng".

**Ví dụ:**
- $\exists n \in \mathbb{N}: n^2 = 16$ (Đúng, với $n = 4$)
- $\exists x \in \mathbb{R}: x^2 = -1$ (Sai trong $\mathbb{R}$, đúng trong $\mathbb{C}$)

**Phủ định:**
$$
\neg(\exists x: P(x)) \equiv \forall x: \neg P(x)
$$

"Không tồn tại $x$ thỏa $P$" $\iff$ "Mọi $x$ đều không thỏa $P$".

#### Lượng từ lồng nhau (Nested Quantifiers)

Thứ tự của các lượng từ khác loại không thể tùy ý đổi chỗ:

- **$\forall x \, \exists y: P(x, y)$** nói chung khác với **$\exists y \, \forall x: P(x, y)$**.

**Ví dụ:**
1. **$\forall x \in \mathbb{R} \, \exists y \in \mathbb{R}: y > x$**  
   "Với mọi $x$, tồn tại $y$ lớn hơn $x$" $\to$ ĐÚNG (chọn $y = x + 1$).

2. **$\exists y \in \mathbb{R} \, \forall x \in \mathbb{R}: y > x$**  
   "Tồn tại một số $y$ lớn hơn mọi $x$" $\to$ SAI (tập số thực không có phần tử lớn nhất).

**Trong giải tích và tô-pô:**

<div class="textbook-definition" markdown="1">
**Định nghĩa (Tính liên tục tại $a$):**
$$
\forall \varepsilon > 0 \; \exists \delta > 0 \; \forall x: (|x - a| < \delta \implies |f(x) - f(a)| < \varepsilon)
$$
</div>

Chính thứ tự các lượng từ xác định bản chất của tính liên tục ($\delta$ được phép phụ thuộc vào $\varepsilon$).

---

### 3. Các kỹ thuật chứng minh (Proof Techniques)

#### A. Chứng minh trực tiếp (Direct Proof)

**Cấu trúc:** Giả sử $P$ đúng $\to$ suy luận từng bước hợp lệ $\to$ kết luận $Q$ đúng.

**Ví dụ:**

<div class="textbook-theorem" markdown="1">
**Mệnh đề:** Nếu $a, b$ là các số lẻ, thì $a + b$ là số chẵn.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh:**  
Giả sử $a, b$ lẻ. Theo định nghĩa:
- $a = 2k + 1$ với $k \in \mathbb{Z}$
- $b = 2m + 1$ với $m \in \mathbb{Z}$

Do đó:
$$
a + b = (2k + 1) + (2m + 1) = 2(k + m + 1)
$$

Vì $k + m + 1 \in \mathbb{Z}$, nên $a + b$ là số chẵn. ∎
</div>

**Khi nào dùng:** Khi có đường suy luận thẳng từ giả thiết sang kết luận.

---

#### B. Chứng minh bằng mệnh đề phản đảo (Proof by Contrapositive)

**Nguyên tắc:** Để chứng minh $P \Rightarrow Q$, ta chứng minh mệnh đề tương đương logic $\neg Q \Rightarrow \neg P$ (mệnh đề phản đảo).

**Ví dụ:**

<div class="textbook-theorem" markdown="1">
**Mệnh đề:** Nếu $n^2$ chẵn, thì $n$ chẵn.
</div>

<div class="textbook-proof textbook-proof-marked" markdown="1">
**Chứng minh (bằng mệnh đề phản đảo):**  
Ta chứng minh: nếu $n$ lẻ, thì $n^2$ lẻ.

Giả sử $n$ lẻ, tức $n = 2k + 1$ với $k \in \mathbb{Z}$.  
Khi đó:
$$
n² = (2k + 1)² = 4k² + 4k + 1 = 2(2k² + 2k) + 1
$$

Vì $2k^2 + 2k \in \mathbb{Z}$, nên $n^2$ lẻ. ∎
</div>

**Khi nào dùng:** Khi giả thiết $\neg Q$ dễ khai thác hơn $P$ (chẳng hạn khi $P$ hoặc $Q$ ở dạng phủ định).

---

#### C. Chứng minh bằng phản chứng (Proof by Contradiction)

**Cấu trúc:** Giả sử kết luận cần chứng minh là SAI $\to$ suy luận hợp lệ $\to$ dẫn tới một mâu thuẫn với giả thiết hoặc sự thật đã biết $\to$ suy ra kết luận ban đầu ĐÚNG.

**Ví dụ kinh điển:**

<div class="textbook-theorem" markdown="1">
**Mệnh đề:** $\sqrt{2}$ là số vô tỉ.
</div>

**Chứng minh:**  
Giả sử phản chứng rằng $\sqrt{2}$ là số hữu tỉ. Khi đó tồn tại $p, q \in \mathbb{Z}$ ($q \neq 0$) với $\gcd(p, q) = 1$ (phân số tối giản) sao cho:
$$
\sqrt{2} = \frac{p}{q}
$$

Bình phương hai vế:
$$
2 = \frac{p²}{q²} \implies p² = 2q²
$$

Do đó $p^2$ chẵn $\Rightarrow p$ chẵn (theo ví dụ ở mục B), nên viết được $p = 2k$ với $k \in \mathbb{Z}$. Thay vào đẳng thức trên:
$$
(2k)² = 2q² \implies 4k² = 2q² \implies q² = 2k²
$$

Do đó $q^2$ chẵn $\Rightarrow q$ chẵn.

Điều này dẫn đến mâu thuẫn: cả $p$ và $q$ đều chẵn nên $\gcd(p, q) \ge 2$, trái với giả thiết phân số tối giản $\gcd(p, q) = 1$.

Vậy $\sqrt{2}$ là số vô tỉ. ∎

![Proof by contradiction flowchart](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Proof_by_Contradiction_Diagram.svg/400px-Proof_by_Contradiction_Diagram.svg.png)  
*Sơ đồ chứng minh phản chứng - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Proof_by_Contradiction_Diagram.svg)*

**Khi nào dùng:** Khi khó chứng minh trực tiếp, đặc biệt với các mệnh đề khẳng định tính duy nhất hoặc sự "không tồn tại".

---

#### D. Quy nạp toán học (Mathematical Induction)

**Nguyên tắc:** Để chứng minh $P(n)$ đúng với mọi số nguyên dương $n \ge 1$:
1. **Bước cơ sở (Base case):** Chứng minh $P(1)$ đúng (hoặc $P(0)$ nếu xét từ $0$).
2. **Bước quy nạp (Inductive step):** Giả sử $P(k)$ đúng (giả thiết quy nạp), chứng minh $P(k + 1)$ cũng đúng.

**Ví dụ:**

<div class="textbook-theorem" markdown="1">
**Mệnh đề:** Với mọi số nguyên $n \ge 1$:
$$
1 + 2 + 3 + \cdots + n = \frac{n(n+1)}{2}
$$
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:**
</div>

**Bước cơ sở ($n = 1$):**
$$
1 = \frac{1 \cdot 2}{2} = 1 \quad \checkmark
$$

**Bước quy nạp:**  
Giả sử công thức đúng với $n = k$:
$$
1 + 2 + \cdots + k = \frac{k(k+1)}{2}
$$

Ta cần chứng minh công thức cũng đúng với $n = k + 1$:
$$
1 + 2 + \cdots + k + (k+1) = \frac{(k+1)(k+2)}{2}
$$

Áp dụng giả thiết quy nạp:
$$
1 + 2 + \cdots + k + (k+1) = \frac{k(k+1)}{2} + (k+1)
$$
$$
= \frac{k(k+1) + 2(k+1)}{2} = \frac{(k+1)(k+2)}{2} \quad \checkmark
$$

Vậy công thức đúng với mọi số nguyên $n \ge 1$. ∎

![Mathematical induction dominoes](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Dominoeffect.png/400px-Dominoeffect.png)  
*Hiệu ứng domino minh họa quy nạp - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Dominoeffect.png)*

**Các biến thể thường gặp:**
- **Quy nạp mạnh (Strong induction):** Giả sử $P(1), \dots, P(k)$ đều đúng để chứng minh $P(k + 1)$.
- **Nguyên lý thứ tự tốt (Well-ordering principle):** Tương đương với nguyên lý quy nạp trên $\mathbb{N}$.

**Khi nào dùng:** Khi chứng minh các công thức hoặc tính chất phụ thuộc vào chỉ số $n \in \mathbb{N}$.

---

### 4. Các lỗi logic phổ biến (Common Logical Mistakes)

#### Lỗi 1: Nhầm lẫn mệnh đề kéo theo với mệnh đề đảo (Converse Error)

**Sai lầm:** $P \Rightarrow Q$ đúng KHÔNG kéo theo mệnh đề đảo $Q \Rightarrow P$ đúng.

**Ví dụ đời thường:**
- **Đúng:** "Nếu trời mưa thì đường ướt" ($P \Rightarrow Q$).
- **Sai:** "Nếu đường ướt thì trời mưa" ($Q \Rightarrow P$) — đường có thể ướt do xe tưới nước.

**Ví dụ trong tô-pô:**
- **Đúng:** "Nếu một không gian tô-pô là compact và Hausdorff, thì nó là không gian chuẩn tắc."
- **Sai:** "Nếu một không gian là chuẩn tắc, thì nó compact" (phản ví dụ: đường thẳng thực $\mathbb{R}$ là chuẩn tắc nhưng không compact).

#### Lỗi 2: Đảo thứ tự lượng từ (Quantifier Order)

**Sai lầm:** Tự ý đổi vị trí $\forall$ và $\exists$.

**Ví dụ:**
- **$\forall \varepsilon > 0 \, \exists \delta > 0 \dots$:** "Với mỗi $\varepsilon > 0$, tồn tại $\delta > 0$ phụ thuộc vào $\varepsilon$" $\to$ định nghĩa liên tục.
- **$\exists \delta > 0 \, \forall \varepsilon > 0 \dots$:** "Tồn tại một $\delta > 0$ duy nhất dùng chung cho mọi $\varepsilon > 0$" $\to$ kéo theo $f$ là hàm hằng trên lân cận $a$, hoàn toàn khác với tính liên tục.

#### Lỗi 3: Hiểu nhầm chân lý rỗng (Vacuous Truth)

**Sai lầm:** Quên rằng $P \Rightarrow Q$ luôn đúng khi $P$ sai.

**Ví dụ:** Mệnh đề "Mọi số nguyên vừa chẵn vừa lẻ đều chia hết cho $7$" là ĐÚNG, vì không tồn tại số nguyên nào vừa chẵn vừa lẻ để làm phản ví dụ.

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Tác phẩm kinh điển về logic

1. **Aristotle** - *Organon* (~350 BCE)  
   *Nền tảng của logic hình thức phương Tây.*

2. **Gottlob Frege** - *Begriffsschrift* (1879)  
   *Đưa ra ký hiệu logic hiện đại và hệ thống lượng từ.*

3. **Bertrand Russell & Alfred N. Whitehead** - *Principia Mathematica* (1910–1913)  
   *Nỗ lực xây dựng toàn bộ toán học từ nền tảng logic.*

4. **Kurt Gödel** - *Incompleteness Theorems* (1931)  
   *Chứng minh những giới hạn căn bản của các hệ thống hình thức.*

### Giáo trình tham khảo cho tô-pô

5. **James R. Munkres** - *Topology*, 2nd Ed., **§2: Logical Implications**  
   *Ngắn gọn, tập trung vào các phép suy luận dùng trong tô-pô.*

6. **Daniel J. Velleman** - *How to Prove It* (2006)  
   *Giáo trình hướng dẫn kỹ năng viết chứng minh rất rõ ràng cho người mới học.*

7. **Richard Hammack** - *Book of Proof* (2013)  
   *Tài liệu miễn phí trực tuyến, dễ tiếp cận.*

8. **Patrick Suppes** - *Introduction to Logic* (1957)  
   *Giáo trình kinh điển theo hướng trình bày hình thức.*

---

## 🔗 Ứng dụng và liên hệ

### Khoa học máy tính — Kiểm chứng hình thức
Các **trợ lý chứng minh** (*proof assistants*) như Coq, Lean và Isabelle sử dụng logic hình thức để kiểm tra tính đúng đắn của phần mềm cũng như các chứng minh toán học phức tạp. Ví dụ, Định lý Bốn màu (*Four Color Theorem*) đã được hình thức hóa và kiểm chứng hoàn toàn trên máy tính bằng Coq.

### Toán học — Các định lý bất toàn của Gödel
Trong bất kỳ hệ hình thức nhất quán nào đủ mạnh để chứa số học cơ bản, luôn tồn tại những mệnh đề đúng nhưng không thể chứng minh hay bác bỏ bên trong hệ đó. Kết quả này cho thấy giới hạn nội tại của khái niệm "chứng minh hình thức".

### Triết học và nền móng toán học
**Logic trực giác (Intuitionistic Logic):** Một trường phái toán học không chấp nhận Luật bài trung ($P \lor \neg P$ luôn đúng) và do đó hạn chế phép chứng minh phản chứng. Trong toán học kiến thiết (*constructive mathematics*), để chứng minh $\exists x: P(x)$, ta cần chỉ ra thuật toán hoặc cách xây dựng tường minh đối tượng $x$.

### Ví dụ thực tế
**Lập luận pháp lý:** Tư duy pháp luật cũng sử dụng cấu trúc kéo theo ("Nếu hành vi $X$ thỏa điều kiện $Y$, thì áp dụng chế tài $Z$") và phép lập luận phản chứng khi bác bỏ một giả thuyết dựa trên mâu thuẫn với chứng cứ.

---

## Video tham khảo

- **xem trước** [How To Write Your First Math Proof](https://www.youtube.com/watch?v=nISrZ80Oa50) — BriTheMathGuy, tiếng Anh. Một chứng minh viết tay đầu tiên: giả thiết, kết luận, và từng bước ở giữa.
- [An Introduction to Mathematical Proofs](https://www.youtube.com/watch?v=YYgepDY3rHw) — zeropercent, tiếng Anh. Khung rộng hơn về cách đọc và viết chứng minh, dùng kèm phần logic của bài.

## 🧩 Bài tập

### Logic cơ bản

1. **Bảng chân trị:**  
   Lập bảng chân trị cho $(P \lor Q) \Rightarrow (P \land Q)$. Mệnh đề này đúng trong những trường hợp nào?

2. **Viết phủ định:**  
   Viết mệnh đề phủ định của các phát biểu sau:
   - a) $\forall x \in \mathbb{R}: x^2 \ge 0$
   - b) $\exists n \in \mathbb{N}: n^2 < n$
   - c) $\forall \varepsilon > 0 \, \exists \delta > 0 \, \forall x: |x - a| < \delta \Rightarrow |f(x) - f(a)| < \varepsilon$

3. **Thứ tự lượng từ:**  
   Diễn đạt bằng lời và xác định tính đúng/sai của từng mệnh đề:
   - a) $\forall x \in \mathbb{R} \, \exists y \in \mathbb{R}: x + y = 0$
   - b) $\exists y \in \mathbb{R} \, \forall x \in \mathbb{R}: x + y = 0$
   - c) $\forall x \in \mathbb{R} \, \forall y \in \mathbb{R}: (x < y \Rightarrow x^2 < y^2)$

### Thực hành chứng minh

4. **Chứng minh trực tiếp:**  
   Chứng minh rằng nếu $n$ chia hết cho $6$, thì $n$ chia hết cho $2$ và $3$.

5. **Chứng minh phản đảo:**  
   Chứng minh rằng nếu $n^2$ không chia hết cho $3$, thì $n$ không chia hết cho $3$.

6. **Chứng minh phản chứng:**  
   Chứng minh rằng không tồn tại số hữu tỉ $r$ sao cho $r^2 = 3$.

7. **Quy nạp toán học:**  
   Chứng minh rằng với mọi $n \ge 1$:
   $$
   1² + 2² + 3² + \cdots + n² = \frac{n(n+1)(2n+1)}{6}
   $$

### Liên hệ với tô-pô

8. **Cấu trúc logic của định nghĩa tô-pô:**  
   Một họ $\tau$ các tập con của $X$ là một tô-pô trên $X$ nếu:
   - (i) $\emptyset, X \in \tau$
   - (ii) Hợp tùy ý của các tập trong $\tau$ thuộc $\tau$
   - (iii) Giao hữu hạn của các tập trong $\tau$ thuộc $\tau$
   
   Hãy viết lại điều kiện (ii) và (iii) bằng ký hiệu logic có sử dụng lượng từ.

9. **Tính liên tục:**  
   Cho định nghĩa $\varepsilon$-$\delta$ của tính liên tục tại $a$:
   $$
   \forall \varepsilon > 0 \; \exists \delta > 0 \; \forall x: (|x - a| < \delta \implies |f(x) - f(a)| < \varepsilon)
   $$
   
   Hãy viết phủ định để thu được định nghĩa "$f$ không liên tục tại $a$".

10. **Phân tích chứng minh:**  
    Đọc chứng minh sau và xác định kỹ thuật chứng minh được sử dụng:
    
    **Mệnh đề:** Tập hợp các số nguyên tố là vô hạn.
    
    **Chứng minh:** Giả sử phản chứng chỉ có hữu hạn số nguyên tố $p_1, p_2, \dots, p_n$.  
    Xét số $N = p_1 p_2 \cdots p_n + 1$.  
    Số $N$ không chia hết cho bất kỳ $p_i$ nào (luôn dư $1$).  
    Do đó $N$ hoặc là số nguyên tố mới, hoặc có một ước nguyên tố không nằm trong danh sách trên — mâu thuẫn. ∎

### Nâng cao

11. **Chứng minh kiến thiết và phi kiến thiết:**  
    Chứng minh rằng tồn tại hai số vô tỉ $a, b$ sao cho $a^b$ là số hữu tỉ.
    
    **Gợi ý:** Xét số $\sqrt{2}^{\sqrt{2}}$. Nếu nó là số hữu tỉ thì chọn $a = b = \sqrt{2}$. Nếu nó là số vô tỉ, xét $(\sqrt{2}^{\sqrt{2}})^{\sqrt{2}} = \sqrt{2}^2 = 2$.
    
    Chứng minh này có mang tính kiến thiết (*constructive*) không? Nó có chỉ ra cụ thể cặp $(a, b)$ nào thỏa mãn hay không?

12. **Siêu toán học:**  
    Tìm hiểu về Luật bài trung (*Law of Excluded Middle*): $P \lor \neg P$ luôn đúng.  
    - Vì sao logic trực giác không chấp nhận tiên đề này?
    - Logic trực giác có liên hệ như thế nào với tô-pô (chẳng hạn mô hình tô-pô của đại số Heyting)?

---

## 📚 Đọc thêm

- **Velleman, How to Prove It:** Chapters 1–3 (Propositional and Quantificational Logic)
- **Hammack, Book of Proof:** Chapters 4–6 (Direct Proof, Contrapositive, Contradiction)
- **Munkres, Topology:** §2 (Logical implications in set theory)
- **Eccles, An Introduction to Mathematical Reasoning:** Comprehensive proof techniques

---

## 🎓 Tóm tắt

Trong bài giảng này, ta đã hệ thống lại các công cụ suy luận cơ bản:

✅ **Logic mệnh đề:** Các phép toán logic ($\neg, \land, \lor, \Rightarrow, \Leftrightarrow$) và bảng chân trị.  
✅ **Lượng từ:** $\forall$ (với mọi), $\exists$ (tồn tại), quy tắc phủ định và vai trò của thứ tự lượng từ.  
✅ **Kỹ thuật chứng minh:**
   - Chứng minh trực tiếp: $P \to \dots \to Q$.
   - Chứng minh phản đảo: $\neg Q \to \dots \to \neg P$.
   - Chứng minh phản chứng: giả sử $\neg Q \to \dots \to$ mâu thuẫn.
   - Quy nạp toán học: $P(1) \land [P(k) \Rightarrow P(k+1)] \to \forall n \ge 1: P(n)$.  
✅ **Lỗi thường gặp:** Nhầm với mệnh đề đảo, đảo thứ tự lượng từ và hiểu nhầm chân lý rỗng.

**Điểm chính:**
- Logic là ngôn ngữ lập luận của toán học; nắm chắc cấu trúc logic giúp đọc và viết chứng minh chính xác.
- Mỗi kỹ thuật chứng minh thích hợp với những dạng mệnh đề khác nhau.
- Thứ tự lượng từ quyết định hoàn toàn ý nghĩa của định nghĩa.

**Liên hệ với tô-pô:**
- Nhiều định nghĩa cốt lõi trong tô-pô chứa các lượng từ lồng nhau.
- Chứng minh phản chứng xuất hiện thường xuyên khi nghiên cứu tính compact và tính liên thông.
- Quy nạp được dùng trong các phép xây dựng từng bước (chẳng hạn phức CW).

**Tiếp theo:** Trong Bài 00.03, ta sẽ tìm hiểu **Số thực và Không gian Euclid** — ví dụ cụ thể đầu tiên dẫn dắt sang định nghĩa không gian tô-pô.

---

*"A mathematician is a device for turning coffee into theorems." — Paul Erdős*

🎯 **Hãy rèn luyện kỹ năng viết chứng minh qua bài tập mỗi ngày.** 🎯

---

**Previous:** [Lecture 00.01: Cartesian Products and Zorn's Lemma](/contents/vi/topology-chapter00/00_01_Cartesian_Products_Zorns_Lemma/)  
**Next:** [Lecture 00.03: Real Numbers and Euclidean Space](/contents/vi/topology-chapter00/00_03_Real_Numbers_Euclidean_Space/)
