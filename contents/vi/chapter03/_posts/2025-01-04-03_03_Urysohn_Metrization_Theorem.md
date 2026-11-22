---
layout: post
title: "Lecture 03.03: Urysohn Metrization Theorem"
lang: vi
lang-ref: lecture-03-03
chapter: 3
lecture: 3
categories: [chapter03]
tags: [metrization, urysohn-metrization, nagata-smirnov, metric-spaces]
description: "Urysohn Metrization Theorem và characterization của metrizable spaces"
---

**Định lý Mê-tric hóa Urysohn**

---

## 📖 Tổng quan

Không gian mê-tric có nhiều tính chất thuận lợi như khái niệm khoảng cách tường minh, đặc trưng bằng dãy và tính đầy đủ. Điều này đặt ra một câu hỏi trung tâm của tô-pô đại cương: **khi nào một không gian tô-pô $(X, \tau)$ là mê-tric hóa được (*metrizable*)**, nghĩa là tồn tại một mê-tric $d$ trên $X$ cảm sinh đúng tô-pô $\tau$?

Câu trả lời kinh điển đầu tiên là **Định lý Mê-tric hóa Urysohn**:

$$
\boxed{T_3 + \text{second countable} \implies \text{metrizable}}
$$

![Metrization concept](https://upload.wikimedia.org/wikipedia/commons/thumb/9/90/Metric_space.svg/400px-Metric_space.svg.png)  
*Cấu trúc không gian mê-tric - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Metric_space.svg)*

Bài giảng này trình bày định nghĩa không gian mê-tric hóa được, các điều kiện cần, chứng minh **Định lý Mê-tric hóa Urysohn** bằng cách nhúng vào không gian tích đếm được, và giới thiệu hai đặc trưng điều kiện cần và đủ tổng quát hơn là **Định lý Nagata–Smirnov** và **Định lý Bing**.

---

## 📐 Định nghĩa và các điều kiện cần

### 1. Không gian mê-tric hóa được (Metrizable Spaces)

<div class="textbook-definition" markdown="1">
**Định nghĩa (Mê-tric hóa được):**  
Không gian tô-pô $(X, \tau)$ được gọi là **mê-tric hóa được** (*metrizable*) nếu tồn tại ít nhất một mê-tric $d$ trên $X$ sao cho tô-pô $\tau_d$ cảm sinh bởi $d$ trùng với $\tau$:

$$
\exists d: X \times X \to \mathbb{R}: \tau = \tau_d
$$
</div>

**Ví dụ mê-tric hóa được:** $\mathbb{R}^n$ với tô-pô Euclid, các đa tạp compact, mọi không gian con của không gian mê-tric hóa được và mọi tích đếm được của các không gian mê-tric hóa được.

**Ví dụ không mê-tric hóa được:** Tô-pô đồng hữu hạn trên tập vô hạn, tô-pô đồng đếm được trên tập không đếm được, tô-pô tầm thường (có ít nhất $2$ điểm) và mặt phẳng Sorgenfrey $\mathbb{R}_\ell \times \mathbb{R}_\ell$.

---

### 2. Các điều kiện cần

<div class="textbook-theorem" markdown="1">
**Định lý:**  
Nếu $X$ mê-tric hóa được, thì $X$ đồng thời là:
1. Không gian Hausdorff ($T_2$);
2. Không gian chính quy ($T_3$);
3. Không gian chuẩn tắc ($T_4$);
4. Không gian đếm được thứ nhất.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Các tính chất này đều đã được chứng minh cho mọi không gian mê-tric ở các bài trước.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả:**  
Nếu một không gian vi phạm bất kỳ tính chất nào ở trên thì nó **không** mê-tric hóa được.
</div>

Ví dụ: tô-pô tầm thường ($\ge 2$ điểm) và tô-pô đồng hữu hạn trên tập vô hạn không Hausdorff nên không mê-tric hóa được; tô-pô đồng đếm được trên tập không đếm được không đếm được thứ nhất nên không mê-tric hóa được.

Tuy nhiên, bốn điều kiện cần trên **chưa đủ**. Phản ví dụ kinh điển là **Đường thẳng dài (*Long Line*)**: nó là không gian Hausdorff, chính quy, chuẩn tắc và đếm được thứ nhất, nhưng không mê-tric hóa được (vì không paracompact; nó compact dãy nhưng không compact, điều không thể xảy ra trong không gian mê-tric).

---

## 📐 Định lý Mê-tric hóa Urysohn

### 1. Phát biểu

**Định lý Mê-tric hóa Urysohn:**

> **Mọi không gian tô-pô $T_3$ (chính quy + $T_1$) và thỏa mãn tiên đề đếm được thứ hai đều mê-tric hóa được.**

$$
(X \text{ regular} \land X \text{ second countable}) \implies X \text{ metrizable}
$$

*(Lưu ý: ở công thức trên quy ước "regular" đi kèm $T_1$, tức $T_3$.)*

Đây là một điều kiện đủ rất thuận tiện trong thực hành, chẳng hạn suy ra ngay mọi đa tạp Hausdorff đếm được thứ hai (và đặc biệt mọi đa tạp compact) đều mê-tric hóa được.

---

### 2. Chiến lược và phác thảo chứng minh

Ý tưởng chứng minh là nhúng $X$ vào khối lập phương Hilbert $[0, 1]^{\mathbb{N}}$ (vốn là không gian mê-tric hóa được) bằng một họ đếm được các hàm Urysohn $\{f_n: X \to [0, 1]\}$, rồi kéo ngược mê-tric về $X$:

$$
d(x, y) = \sum_{n=1}^\infty \frac{1}{2^n} |f_n(x) - f_n(y)|
$$

**Phác thảo chứng minh:**
1. **Suy ra tính chuẩn tắc:** Vì $X$ đếm được thứ hai nên $X$ là không gian Lindelöf; kết hợp với giả thiết $T_3$ suy ra $X$ là không gian chuẩn tắc ($T_4$), cho phép áp dụng Bổ đề Urysohn.
2. **Xây dựng họ đếm được $\{f_n\}$:** Cho $\{B_k\}$ là một cơ sở đếm được của $X$. Xét tất cả các cặp $(B_i, B_j)$ sao cho $\text{cl}(B_i) \subseteq B_j$ (có tối đa đếm được cặp như vậy). Với mỗi cặp $(B_i, B_j)$, hai tập đóng $\text{cl}(B_i)$ và $X \setminus B_j$ rời nhau, nên theo Bổ đề Urysohn tồn tại hàm liên tục $f_{ij}: X \to [0, 1]$ thỏa $f_{ij}(\text{cl}(B_i)) = \{0\}$ và $f_{ij}(X \setminus B_j) = \{1\}$. Đánh số lại toàn bộ các hàm này thành dãy $\{f_n\}_{n=1}^{\infty}$.
3. **Định nghĩa mê-tric:** Từ dãy $\{f_n\}$, ta có thể định nghĩa mê-tric bằng chuỗi hội tụ đều ở trên hoặc bằng công thức tương đương:
$$
d(x,y) = \sup_{n} \min\left\{|f_n(x) - f_n(y)|, \frac{1}{n}\right\}
$$
Vì $X$ là $T_3$, với mọi $x \neq y$ tồn tại $B_i, B_j$ với $x \in B_i, \text{cl}(B_i) \subseteq B_j \subseteq X \setminus \{y\}$, do đó $f_{ij}(x) = 0 \neq 1 = f_{ij}(y)$, bảo đảm $d(x, y) > 0$ khi $x \neq y$.
4. **Kiểm tra $\tau_d = \tau$:**
   - **($\tau_d \subseteq \tau$):** Vì mỗi $f_n$ liên tục đối với $\tau$ và chuỗi hội tụ đều, hàm khoảng cách $y \mapsto d(x, y)$ liên tục đối với $\tau$, nên mọi hình cầu mở theo $d$ đều mở trong $\tau$.
   - **($\tau \subseteq \tau_d$):** Với mọi $U \in \tau$ và $x \in U$, nhờ tính $T_3$ và cơ sở $\{B_k\}$, tồn tại cặp $(B_i, B_j)$ sao cho $x \in B_i \subseteq \text{cl}(B_i) \subseteq B_j \subseteq U$. Khi đó hàm $f_n = f_{ij}$ tương ứng thỏa $f_n(x) = 0$ và $f_n(X \setminus U) = \{1\}$, suy ra hình cầu mở $B_d(x, 1/2^n)$ (với mê-tric tổng) nằm trọn trong $U$.

---

### 3. Một số hệ quả

<div class="textbook-theorem" markdown="1">
**Hệ quả 1 (Không gian con):**  
Mọi không gian con của không gian mê-tric hóa được đều mê-tric hóa được.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Thu hẹp mê-tric của không gian bao lên tập con cho đúng tô-pô con.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả 2 (Tích đếm được):**  
Tích đếm được của các không gian mê-tric hóa được (với tô-pô tích) là mê-tric hóa được.
</div>

<div class="textbook-proof" markdown="1">
**Chứng minh:** Nếu $d_n$ là mê-tric trên $X_n$, thay $d_n$ bởi mê-tric bị chặn tương đương $\bar{d}_n = \min\{d_n, 1\}$ và đặt $d((x_n), (y_n)) = \sum_{n=1}^{\infty} \frac{1}{2^n}\bar{d}_n(x_n, y_n)$. Mê-tric này cảm sinh đúng tô-pô tích trên $\prod_{n=1}^{\infty} X_n$.
</div>

<div class="textbook-theorem" markdown="1">
**Hệ quả 3:**  
Mọi không gian compact Hausdorff đếm được thứ hai đều mê-tric hóa được.
</div>

---

## 📐 Định lý Nagata–Smirnov và Định lý Bing

Định lý Urysohn đòi hỏi giả thiết đếm được thứ hai nên không bao quát được các không gian mê-tric không khả ly (như tập không đếm được với mê-tric rời rạc). Hai định lý sau đưa ra **điều kiện cần và đủ** cho mọi không gian mê-tric hóa được.

### 1. Định lý Mê-tric hóa Nagata–Smirnov

**Định lý Nagata–Smirnov:**

> **Không gian $X$ mê-tric hóa được $\iff X$ là $T_3$ (chính quy + $T_1$) và có một cơ sở hữu hạn địa phương đếm được (*countably locally finite / $\sigma$-locally finite basis*).**

<div class="textbook-definition" markdown="1">
**Định nghĩa (Hữu hạn địa phương — Locally Finite):**  
Một họ tập hợp $\{U_\alpha\}$ là **hữu hạn địa phương** nếu mỗi điểm $x \in X$ đều có một lân cận chỉ giao với hữu hạn tập trong họ. Một họ là *hữu hạn địa phương đếm được* nếu nó là hợp đếm được của các họ hữu hạn địa phương.
</div>

### 2. Định lý Mê-tric hóa Bing

**Định lý Bing:**

> **Không gian $X$ mê-tric hóa được $\iff X$ là $T_3$ và có một cơ sở $\sigma$-rời rạc (*$\sigma$-discrete basis*).**

<div class="textbook-definition" markdown="1">
**Định nghĩa ($\sigma$-rời rạc):**  
Một cơ sở là **$\sigma$-rời rạc** nếu nó là hợp đếm được của các họ rời rạc (trong đó mỗi điểm của $X$ có một lân cận giao với tối đa một tập trong họ).
</div>

---

## 📐 Bảng ví dụ và phản ví dụ

### Không gian mê-tric hóa được

| Không gian | Lý do mê-tric hóa được |
|-------|----------------|
| $\mathbb{R}^n$ | $T_3$ + đếm được thứ hai (hoặc mê-tric Euclid trực tiếp) |
| Đa tạp compact (Hausdorff) | $T_3$ + đếm được thứ hai |
| Không gian con của không gian mê-tric hóa được | Thu hẹp mê-tric |
| Không gian Hilbert $\ell^2$ | Mê-tric sinh bởi chuẩn |
| Không gian rời rạc (bất kỳ lực lượng) | Mê-tric rời rạc |

### Không gian không mê-tric hóa được

| Không gian | Điều kiện bị vi phạm |
|-------|----------------|
| Tô-pô đồng hữu hạn (tập vô hạn) | Không Hausdorff ($T_2$) |
| Tô-pô đồng đếm được (tập không đếm được) | Không Hausdorff và không đếm được thứ nhất |
| Tô-pô tầm thường ($\ge 2$ điểm) | Không Hausdorff |
| Đường thẳng dài (Long line) | Không paracompact (compact dãy nhưng không compact) |
| Mặt phẳng Sorgenfrey $\mathbb{R}_\ell \times \mathbb{R}_\ell$ | Không chuẩn tắc ($T_4$) |
| $[0, 1]^{\mathbb{R}}$ (tô-pô tích) | Không đếm được thứ nhất |

---

## 🧠 Bài báo nền tảng và tài liệu tham khảo

### Công trình kinh điển

1. **Pavel Urysohn** - *"Über die Mächtigkeit der zusammenhängenden Mengen"* (1925)  
   *Định lý Mê-tric hóa Urysohn.*

2. **Jun-iti Nagata** - *"On a necessary and sufficient condition of metrizability"* (1950)  
   *Định lý Nagata–Smirnov.*

3. **Yuri Smirnov** - *"A necessary and sufficient condition for metrizability"* (1951)  
   *Phát hiện độc lập định lý Nagata–Smirnov.*

4. **R.H. Bing** - *"Metrization of topological spaces"* (1951)  
   *Định lý Mê-tric hóa Bing.*

### Giáo trình

5. **James R. Munkres** - *Topology*, 2nd Ed., **§34: Urysohn Metrization**  
   *Trình bày chứng minh đầy đủ.*

6. **Stephen Willard** - *General Topology*, **Chapter 6**  
   *Trình bày đầy đủ về bài toán mê-tric hóa.*

7. **Ryszard Engelking** - *General Topology*, **Chapter 4**  
   *Góc nhìn chuyên sâu.*

---

## 🔗 Ứng dụng và liên hệ

- **Lý thuyết đa tạp:** Mọi đa tạp Hausdorff đếm được thứ hai (và tổng quát hơn, đa tạp Hausdorff paracompact) đều mê-tric hóa được, là nền tảng để xây dựng mê-tric Riemann.
- **Giải tích hàm:** Mọi không gian Banach đều mê-tric hóa được bởi chuẩn $d(x, y) = \|x - y\|$; ngoài ra, tô-pô yếu* trên hình cầu đơn vị đối ngẫu của không gian Banach khả ly cũng mê-tric hóa được (suy từ Định lý Urysohn).
- **Tô-pô đại số:** Nhiều lớp phức CW (chẳng hạn phức CW hữu hạn địa phương) là mê-tric hóa được.

---

## Video tham khảo

- **xem trước** [Lecture 40: Urysohn’s Metrization Theorem](https://www.youtube.com/watch?v=8QrZhsErCT4) — NPTEL IIT Bombay, tiếng Anh. Định lý metric hóa Urysohn trong một bài giảng đại học trọn vẹn.
- [The most important Theorem in Topology | Urysohn Metrisation theorem](https://www.youtube.com/watch?v=4pKQgFI3nF8) — Problemathic, tiếng Anh. Cùng định lý, nói ngắn hơn, để giữ phát biểu trước khi đi vào chứng minh dài.

## 🧩 Bài tập

### Hiểu về tính mê-tric hóa được

1. **Điều kiện cần:** Liệt kê các điều kiện cần của một không gian mê-tric hóa được.
2. **Kiểm tra cho $\mathbb{R}^n$:** Kiểm tra $\mathbb{R}^n$ thỏa mãn các giả thiết của Định lý Mê-tric hóa Urysohn.
3. **Không gian con:** Chứng minh mọi không gian con của không gian mê-tric hóa được đều mê-tric hóa được.

### Định lý Urysohn

4. **Không gian compact Hausdorff:** Chứng minh mọi không gian compact Hausdorff đếm được thứ hai đều mê-tric hóa được.
5. **Kiểm tra mê-tric:** Cho họ đếm được $\{f_n: X \to [0, 1]\}$ tách điểm trên $X$. Chứng minh
   $$d(x,y) = \sum \frac{1}{2^n} |f_n(x) - f_n(y)|$$
   là một mê-tric trên $X$.
6. **Sự trùng khớp tô-pô:** Hoàn thiện chi tiết bước chứng minh $\tau_d = \tau$ trong chứng minh Định lý Urysohn.

### Phản ví dụ không mê-tric hóa được

7. **Tô-pô đồng hữu hạn:** Chứng minh tô-pô đồng hữu hạn trên tập vô hạn không mê-tric hóa được.
8. **Đường thẳng dài:** Tìm hiểu định nghĩa Đường thẳng dài, các tiên đề tách/đếm được mà nó thỏa mãn và lý do nó không mê-tric hóa được.
9. **Mặt phẳng Sorgenfrey:** Giải thích vì sao $\mathbb{R}_\ell \times \mathbb{R}_\ell$ không mê-tric hóa được.

### Nâng cao

10. **Nagata–Smirnov:** So sánh giả thiết cơ sở của Định lý Nagata–Smirnov với Định lý Urysohn.
11. **Tính paracompact:** Tìm hiểu xem giả thiết "paracompact + Hausdorff" có đủ kéo theo mê-tric hóa được không, và cần bổ sung điều kiện nào.
12. **Tích không đếm được:** Tích đếm được của các không gian mê-tric hóa được là mê-tric hóa được; vì sao tích không đếm được $[0, 1]^{\mathbb{R}}$ không mê-tric hóa được?

### Ứng dụng

13. **Đa tạp compact:** Giải thích vì sao mọi đa tạp Hausdorff compact đều đếm được thứ hai và do đó mê-tric hóa được.
14. **Không gian Hilbert:** $\ell^2$ với tô-pô chuẩn là mê-tric hóa được; liệu $\ell^2$ với tô-pô yếu có mê-tric hóa được không?
15. **Tính đầy đủ:** Nếu $X$ mê-tric hóa được, liệu luôn có thể chọn một mê-tric tương đương làm cho $X$ đầy đủ không? (Gợi ý: xét $X = \mathbb{Q}$.)

### Câu hỏi suy ngẫm

16. **Vai trò của tiên đề đếm được thứ hai:** Giải thích vì sao giả thiết đếm được thứ hai đóng vai trò quyết định trong chứng minh của Urysohn.
17. **Tính không duy nhất của mê-tric:** Nếu $(X, \tau)$ mê-tric hóa được, có bao nhiêu mê-tric khác nhau cùng cảm sinh tô-pô $\tau$?
18. **Lịch sử:** Tìm hiểu tiến trình giải bài toán mê-tric hóa từ Urysohn (1925) đến Nagata, Smirnov và Bing (1950–1951).

---

## 📚 Đọc thêm

- **Munkres, Topology:** §34 (Urysohn Metrization)
- **Willard, General Topology:** Chapter 6 (Metrization)
- **Engelking, General Topology:** Chapter 4
- **Nagata:** *Modern General Topology*

---

## 🎓 Tóm tắt

✅ **Mê-tric hóa được:** Tồn tại mê-tric cảm sinh đúng tô-pô ban đầu.  
✅ **Điều kiện cần:** Phải là $T_2, T_3, T_4$ và đếm được thứ nhất.  
✅ **Định lý Mê-tric hóa Urysohn:** $T_3$ + đếm được thứ hai $\Rightarrow$ mê-tric hóa được (chứng minh bằng cách nhúng vào $[0, 1]^{\mathbb{N}}$ qua họ đếm được các hàm Urysohn).  
✅ **Điều kiện cần và đủ tổng quát:** Định lý Nagata–Smirnov (cơ sở hữu hạn địa phương đếm được) và Định lý Bing (cơ sở $\sigma$-rời rạc).

**Kết thúc Chương 03:** Ta đã hoàn thiện hệ thống các tiên đề tách ($T_0$–$T_4$), Bổ đề Urysohn, Định lý Tietze, các tiên đề đếm được và bài toán mê-tric hóa.

**Tiếp theo:** Chương 04 sẽ đi sâu vào **Không gian Mê-tric** — tính đầy đủ, Định lý phạm trù Baire và không gian hàm số.

---

*"Metrization: when topology becomes geometry."* — Topological wisdom

🎯 **Hãy ghi nhớ cấu trúc cốt lõi: $T_3$ + đếm được thứ hai $\Rightarrow$ $T_4$ $\Rightarrow$ nhúng vào $[0, 1]^{\mathbb{N}}$ $\Rightarrow$ mê-tric hóa được.** 🎯

---

**Previous:** [Lecture 03.02: Countability Axioms](/contents/vi/topology-chapter03/03_02_Countability_Axioms/)  
**Next Chapter:** [Chapter 04: Metric Spaces and Metrization](/contents/vi/topology-chapter04/)
