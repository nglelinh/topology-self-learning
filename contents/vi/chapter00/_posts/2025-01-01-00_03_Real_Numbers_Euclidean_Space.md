---
layout: post
title: "Lecture 00.03: Real Numbers and Euclidean Space"
lang: vi
lang-ref: lecture-00-03
chapter: 0
lecture: 3
categories: [chapter00]
tags: [real-numbers, euclidean-space, metric, completeness]
description: "Số thực, không gian Euclid, metric topology, và các tính chất nền tảng"
---

**Real Numbers and Euclidean Space**

---

## 📖 Tổng quan

Sau khi xây dựng nền tảng logic và lý thuyết tập hợp, chúng ta cuối cùng đến với **ví dụ cụ thể đầu tiên**: các số thực ℝ và không gian Euclid ℝⁿ. Đây không chỉ là ví dụ—chúng là **động lực** (motivation) cho toàn bộ topology!

Hãy nghĩ lại: Topology ra đời từ câu hỏi "Liên tục là gì?" trong giải tích. Calculus định nghĩa liên tục qua ε và δ. Nhưng các nhà toán học nhận ra rằng bản chất của "liên tục" không phụ thuộc vào số—mà phụ thuộc vào **cấu trúc của không gian**.

Trong bài này, chúng ta sẽ:
- Xây dựng **ℝ** từ ℚ (phác thảo)
- Hiểu **completeness** (tính đầy đủ) của ℝ
- Định nghĩa **metric** và **metric space**
- Khám phá **Euclidean topology** trên ℝⁿ
- Thấy rằng topology là sự trừu tượng hóa của các khái niệm metric

**Tại sao bài này quan trọng?**
- ℝⁿ là không gian tô-pô quan trọng nhất trong thực hành
- Metric space là cầu nối giữa giải tích và topology
- Mọi khái niệm topology (open, closed, continuous) đều có nguồn gốc từ ℝ
- Completeness là tính chất quyết định sự "nice" của không gian

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Số Thực

Hãy bắt đầu từ những gì bạn biết:
- **ℕ = {1, 2, 3, ...}**: Số tự nhiên, đủ để đếm
- **ℤ = {..., -2, -1, 0, 1, 2, ...}**: Số nguyên, đủ để trừ
- **ℚ = {p/q : p,q ∈ ℤ, q ≠ 0}**: Số hữu tỉ, đủ để chia

**Nhưng:** ℚ không đủ! Chúng ta đã biết √2 ∉ ℚ.

**Vấn đề sâu xa hơn:** ℚ có "lỗ hổng" (gaps).

Xét tập A = {x ∈ ℚ : x² < 2}. Tập này không có **supremum** (cận trên nhỏ nhất) trong ℚ!
- Nếu x² < 2, ta có thể tìm y ∈ ℚ với x < y và y² < 2
- Không có "số hữu tỉ lớn nhất" trong A

**Giải pháp:** Cần một hệ số "đầy đủ" hơn—đó là **ℝ**.

![Number line with gaps](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d7/Real_number_line.svg/500px-Real_number_line.svg.png)  
*Trục số thực - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Real_number_line.svg)*

---

## 📐 Định nghĩa Hình thức

### 1. Construction of ℝ (Xây dựng Số thực)

Có nhiều cách xây dựng ℝ từ ℚ. Hai cách phổ biến:

#### Cách 1: Dedekind Cuts

**Định nghĩa (Dedekind Cut):**  
Một **Dedekind cut** là một cặp (A, B) với A, B ⊆ ℚ sao cho:
1. A ∪ B = ℚ, A ∩ B = ∅, A ≠ ∅, B ≠ ∅
2. ∀a ∈ A, ∀b ∈ B: a < b
3. A không có phần tử lớn nhất

**Trực giác:** Một "cắt" chia ℚ thành hai nửa: "nhỏ hơn" và "lớn hơn" một số thực.

**Ví dụ:**
- **√2:** A = {x ∈ ℚ : x < 0 hoặc x² < 2}, B = {x ∈ ℚ : x > 0 và x² ≥ 2}
- **π:** A = {x ∈ ℚ : x < π}, B = {x ∈ ℚ : x ≥ π}

**Định nghĩa:** ℝ = {tất cả Dedekind cuts}

#### Cách 2: Cauchy Sequences

**Định nghĩa (Cauchy Sequence):**  
Dãy (xₙ) trong ℚ là **Cauchy** nếu:
$$
\forall \varepsilon > 0 \; \exists N \in \mathbb{N} \; \forall m,n \geq N: |x_m - x_n| < \varepsilon
$$

**Trực giác:** Các phần tử của dãy "tụ lại gần nhau" khi n → ∞.

**Vấn đề:** Một Cauchy sequence trong ℚ có thể không hội tụ đến số hữu tỉ!

**Ví dụ:**  
Dãy xₙ = 1 + 1/2 + 1/6 + ... + 1/n! là Cauchy, nhưng hội tụ đến e ≈ 2.718... ∉ ℚ.

**Giải pháp:** Định nghĩa ℝ là tập các lớp tương đương của Cauchy sequences trong ℚ (hai dãy tương đương nếu hiệu chúng → 0).

---

### 2. Completeness Axiom (Tiên đề Đầy đủ)

Thay vì xây dựng, ta thường **tiên đề hóa** ℝ qua tính chất quan trọng nhất:

**Least Upper Bound Property (LUB):**

> **Mọi tập con không rỗng, bị chặn trên của ℝ đều có supremum (cận trên nhỏ nhất) trong ℝ.**

$$
\forall A \subseteq \mathbb{R}: (A \neq \emptyset \land A \text{ bounded above}) \implies \exists \sup A \in \mathbb{R}
$$

**Định nghĩa (Supremum):**  
Số s = sup A nếu:
1. s là cận trên của A: ∀a ∈ A: a ≤ s
2. s là nhỏ nhất: nếu t là cận trên khác, thì s ≤ t

**Tương tự:** Greatest Lower Bound (GLB) = Infimum (inf A)

**Ví dụ:**
- A = (0, 1): sup A = 1 (nhưng 1 ∉ A!)
- B = {1 - 1/n : n ∈ ℕ}: sup B = 1
- C = ℚ ∩ [0, √2]: sup C = √2 (trong ℝ, không tồn tại trong ℚ!)

**Hệ quả quan trọng:**

**Archimedean Property:**  
∀x, y ∈ ℝ với y > 0: ∃n ∈ ℕ: ny > x

**Trực giác:** Không có "infinitesimal" (vô cùng nhỏ) thực sự trong ℝ.

**Density of ℚ:**  
Giữa hai số thực bất kỳ luôn có một số hữu tỉ.

$$
\forall x, y \in \mathbb{R}: (x < y) \implies \exists r \in \mathbb{Q}: x < r < y
$$

---

### 3. Metric Spaces (Không gian Metric)

**Động lực:** Để nói về "liên tục", ta cần khái niệm "khoảng cách". Đó chính là **metric**.

**Định nghĩa (Metric):**  
Một **metric** trên tập X là hàm d: X × X → ℝ thỏa mãn:

1. **Non-negativity:** d(x, y) ≥ 0, và d(x, y) = 0 ⟺ x = y
2. **Symmetry:** d(x, y) = d(y, x)
3. **Triangle Inequality:** d(x, z) ≤ d(x, y) + d(y, z)

**Trực giác:** d(x, y) là "khoảng cách" từ x đến y.

![Triangle inequality visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/Triangle_inequality.svg/400px-Triangle_inequality.svg.png)  
*Bất đẳng thức tam giác - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Triangle_inequality.svg)*

**Ví dụ:**

**1. Euclidean metric trên ℝ:**
$$
d(x, y) = |x - y|
$$

**2. Euclidean metric trên ℝⁿ:**
$$
d(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^n (x_i - y_i)²}
$$

**3. Manhattan metric (Taxicab) trên ℝ²:**
$$
d_1((x_1, y_1), (x_2, y_2)) = |x_1 - x_2| + |y_1 - y_2|
$$

**Tên gọi:** Khoảng cách đi "theo lưới đường phố" ở Manhattan.

**4. Max metric (Chebyshev) trên ℝⁿ:**
$$
d_\infty(\mathbf{x}, \mathbf{y}) = \max_{i=1,\ldots,n} |x_i - y_i|
$$

**5. Discrete metric trên bất kỳ tập X:**
$$
d(x, y) = \begin{cases} 0 & \text{if } x = y \\ 1 & \text{if } x \neq y \end{cases}
$$

![Different metrics on R2](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Manhattan_distance.svg/400px-Manhattan_distance.svg.png)  
*So sánh Euclidean và Manhattan distance - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Manhattan_distance.svg)*

---

### 4. Metric Topology (Tô-pô Metric)

**Định nghĩa (Open Ball - Hình cầu mở):**  
Với x ∈ X và r > 0, **open ball** tâm x bán kính r là:
$$
B(x, r) = \{y \in X : d(x, y) < r\}
$$

**Trong ℝ:** B(a, r) = (a - r, a + r) (khoảng mở)  
**Trong ℝ²:** B(p, r) = đĩa tròn mở tâm p bán kính r  
**Trong ℝ³:** B(p, r) = quả bóng mở tâm p bán kính r

**Định nghĩa (Open Set in Metric Space):**  
Tập U ⊆ X là **open** (mở) nếu:
$$
\forall x \in U: \exists r > 0: B(x, r) \subseteq U
$$

**Trực giác:** Mọi điểm trong U có "không gian xung quanh" vẫn nằm trong U.

![Open set visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Open_set_-_example.svg/400px-Open_set_-_example.svg.png)  
*Tập mở trong mặt phẳng - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Open_set_-_example.svg)*

**Ví dụ trong ℝ:**
- **(a, b)** là mở (khoảng mở)
- **[a, b]** KHÔNG mở (điểm a không có ball xung quanh nằm trong [a, b])
- **ℝ** là mở
- **∅** là mở (vacuously true!)

**Định lý:**  
Họ tất cả các tập mở trong metric space (X, d) tạo thành một **topology** trên X.

**Chứng minh (sketch):**  
Cần kiểm tra:
1. ∅ và X mở ✓
2. Hợp tùy ý các tập mở là mở ✓
3. Giao hữu hạn các tập mở là mở ✓

**Ý nghĩa:** Mọi metric space tự động là topological space!

---

### 5. Euclidean Space ℝⁿ

**Định nghĩa:**  
**Không gian Euclid n-chiều** là ℝⁿ = ℝ × ℝ × ... × ℝ (n lần) với Euclidean metric:
$$
d(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^n (x_i - y_i)²}
$$

**Các trường hợp đặc biệt:**
- **ℝ¹ = ℝ:** Đường thẳng
- **ℝ²:** Mặt phẳng
- **ℝ³:** Không gian 3 chiều (thế giới vật lý)
- **ℝ⁴:** Không-thời gian (relativity)

**Standard Basis:** ℝⁿ có topology induced bởi tất cả các open balls. Nhưng ta có thể dùng **basis** đơn giản hơn:

**Định lý (Standard Basis for ℝⁿ):**  
Họ tất cả các "open rectangles" (tích Cartesian của các khoảng mở) tạo thành basis cho topology của ℝⁿ:
$$
\mathcal{B} = \{(a_1, b_1) \times (a_2, b_2) \times \cdots \times (a_n, b_n)\}
$$

**Ví dụ trong ℝ²:**  
Một open rectangle: (1, 3) × (2, 5) = {(x, y) : 1 < x < 3, 2 < y < 5}

![Open rectangle in R2](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Open_rectangle.svg/300px-Open_rectangle.svg.png)  
*Open rectangle làm basis element - Nguồn: Minh họa concept*

**Tính chất quan trọng của ℝⁿ:**
- **Separable:** Có countable dense subset (ℚⁿ)
- **Second countable:** Có countable basis
- **Hausdorff:** Hai điểm khác nhau có neighborhoods disjoint
- **Complete:** Mọi Cauchy sequence hội tụ (trong ℝⁿ)
- **Locally compact:** Mọi điểm có compact neighborhood
- **Connected:** Không thể chia thành hai open sets rời nhau

---

### 6. Convergence in Metric Spaces

**Định nghĩa (Convergence - Hội tụ):**  
Dãy (xₙ) trong metric space (X, d) **hội tụ** đến x ∈ X nếu:
$$
\forall \varepsilon > 0 \; \exists N \in \mathbb{N} \; \forall n \geq N: d(x_n, x) < \varepsilon
$$

**Ký hiệu:** xₙ → x hoặc lim_{n→∞} xₙ = x

**Trực giác:** Khoảng cách từ xₙ đến x → 0 khi n → ∞.

**Định nghĩa (Cauchy Sequence trong Metric Space):**  
Dãy (xₙ) là **Cauchy** nếu:
$$
\forall \varepsilon > 0 \; \exists N \in \mathbb{N} \; \forall m,n \geq N: d(x_m, x_n) < \varepsilon
$$

**Định lý:**  
Mọi convergent sequence là Cauchy.

**Chứng minh:** Nếu xₙ → x, cho ε > 0, chọn N sao cho ∀n ≥ N: d(xₙ, x) < ε/2.  
Khi đó với m, n ≥ N:
$$
d(x_m, x_n) \leq d(x_m, x) + d(x, x_n) < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
$$
∎

**Ngược lại KHÔNG đúng tổng quát!** (Trừ khi space "complete")

**Định nghĩa (Complete Metric Space):**  
Metric space (X, d) là **complete** nếu mọi Cauchy sequence hội tụ trong X.

**Ví dụ:**
- **ℝ** complete ✓ (theo completeness axiom)
- **ℚ** KHÔNG complete ✗ (√2 = lim 1.4, 1.41, 1.414, ... ∉ ℚ)
- **(0, 1)** KHÔNG complete ✗ (dãy 1/n → 0 ∉ (0, 1))
- **[0, 1]** complete ✓

**Định lý quan trọng:**  
**ℝⁿ** là complete metric space.

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Richard Dedekind** - *Stetigkeit und irrationale Zahlen* (1872)  
   *Xây dựng ℝ bằng Dedekind cuts*

2. **Georg Cantor** - *Grundlagen einer allgemeinen Mannigfaltigkeitslehre* (1883)  
   *Xây dựng ℝ bằng Cauchy sequences*

3. **Maurice Fréchet** - *Sur quelques points du calcul fonctionnel* (1906)  
   *Giới thiệu khái niệm metric space*

4. **Felix Hausdorff** - *Grundzüge der Mengenlehre* (1914)  
   *Nền tảng của topology hiện đại, metric spaces*

### Textbooks

5. **Walter Rudin** - *Principles of Mathematical Analysis*, 3rd Ed., **Chapter 1**  
   *Construction và properties của ℝ*

6. **James R. Munkres** - *Topology*, 2nd Ed., **§20: Metric Topology**  
   *Metric spaces trong context của topology*

7. **Kenneth A. Ross** - *Elementary Analysis: The Theory of Calculus* (2013)  
   *Undergraduate-friendly approach đến ℝ*

8. **Charles C. Pugh** - *Real Mathematical Analysis* (2002)  
   *Modern treatment với geometric intuition*

---

## 🔗 Applications and Connections

### Physics - Relativity
**Minkowski Space:** Trong special relativity, không-thời gian là ℝ⁴ với metric không phải Euclidean:
$$
ds² = -c²dt² + dx² + dy² + dz²
$$

Metric này không positive definite, nhưng vẫn định nghĩa topology.

### Computer Graphics
**3D Rendering:** Các objects trong 3D graphics được model trong ℝ³. Transformations (rotation, translation) là continuous maps preserving Euclidean metric.

### Data Science
**Euclidean Space:** Mỗi data point thường được represent như một vector trong ℝⁿ. Distance metrics (Euclidean, Manhattan, Cosine) được dùng để "so sánh" data points.

**Ví dụ:** K-nearest neighbors (KNN) algorithm dựa vào Euclidean metric trong ℝⁿ.

### Machine Learning
**Feature Spaces:** Neural networks hoạt động trong không gian Euclid high-dimensional (ℝⁿ với n rất lớn). Topology của ℝⁿ đảm bảo gradient descent "works".

### Real-World Example
**GPS Navigation:** Vị trí trên Trái đất được approximate bằng ℝ³ (latitude, longitude, altitude). Khoảng cách giữa hai điểm dùng metric gần Euclidean (thực tế là spherical geometry).

---

## 🧩 Exercises

### Understanding ℝ

1. **Supremum và Infimum:**  
   Tìm sup A và inf A (nếu tồn tại):
   - a) A = {1/n : n ∈ ℕ}
   - b) A = {x ∈ ℚ : x² < 3}
   - c) A = {x ∈ ℝ : sin(x) = 1}

2. **Density:**  
   Chứng minh rằng giữa hai số thực bất kỳ a < b luôn tồn tại:
   - a) Một số hữu tỉ
   - b) Một số vô tỉ

3. **Archimedean Property:**  
   Sử dụng Archimedean property để chứng minh: ∀ε > 0, ∃n ∈ ℕ: 1/n < ε.

### Metrics

4. **Verify Metric:**  
   Chứng minh Manhattan metric d₁ trên ℝ² thỏa mãn triangle inequality.

5. **Different Metrics:**  
   Trên ℝ², vẽ "unit ball" B(0, 1) trong ba metrics:
   - a) Euclidean: d₂(x, y) = √(Σ(xᵢ - yᵢ)²)
   - b) Manhattan: d₁(x, y) = Σ|xᵢ - yᵢ|
   - c) Max: d∞(x, y) = max|xᵢ - yᵢ|
   
   Hình dạng của chúng khác nhau như thế nào?

6. **Discrete Metric:**  
   Với discrete metric trên X, mô tả tất cả open balls. Tập nào là open?

### Open Sets

7. **Open or Not:**  
   Trong ℝ với Euclidean metric, các tập sau mở hay không? Tại sao?
   - a) (0, 1)
   - b) [0, 1]
   - c) (0, 1] ∪ (2, 3)
   - d) ℕ
   - e) ℚ

8. **Open Balls:**  
   Trong ℝ² với Euclidean metric, chứng minh rằng B((0,0), 1) là open set.

9. **Basis:**  
   Chứng minh rằng họ tất cả open intervals (a, b) tạo thành basis cho topology của ℝ.

### Convergence

10. **Convergence Examples:**  
    Xác định các dãy sau hội tụ hay không (trong ℝ):
    - a) xₙ = 1/n
    - b) xₙ = (-1)ⁿ
    - c) xₙ = (n² + 1) / (n² + 2)

11. **Cauchy but not Convergent:**  
    Tìm một Cauchy sequence trong (0, 1) (với Euclidean metric) không hội tụ trong (0, 1).  
    Điều này cho thấy gì về completeness của (0, 1)?

12. **Convergence in ℝ²:**  
    Trong ℝ², dãy (xₙ, yₙ) hội tụ đến (a, b) khi nào?  
    Chứng minh rằng: (xₙ, yₙ) → (a, b) ⟺ xₙ → a và yₙ → b.

### Advanced

13. **Equivalent Metrics:**  
    Hai metrics d₁, d₂ trên X được gọi là **equivalent** nếu chúng induce cùng topology.  
    Chứng minh rằng trên ℝⁿ, ba metrics sau equivalent:
    - Euclidean d₂
    - Manhattan d₁
    - Max d∞
    
    (*Hint:* Chỉ ra rằng mọi d₁-open ball chứa d₂-open ball và ngược lại)

14. **Completeness:**  
    Chứng minh rằng [0, 1] ⊂ ℝ là complete (metric space với inherited metric).

15. **Product Metric:**  
    Trên ℝ² = ℝ × ℝ, định nghĩa:
    $$
    d((x_1, y_1), (x_2, y_2)) = \max\{|x_1 - x_2|, |y_1 - y_2|\}
    $$
    Chứng minh đây là metric. Mô tả open balls trong metric này.

### Reflection

16. **Completeness vs Compactness:**  
    (0, 1) không complete. [0, 1] complete.  
    Sự khác biệt nào giữa chúng gây ra điều này?  
    (*Preview:* [0, 1] còn có tính chất gì đặc biệt?)

17. **Topology from Metric:**  
    Tại sao "open balls" là concept tự nhiên để định nghĩa topology?  
    Liên hệ với intuition về "neighborhoods" và "closeness".

---

## 📚 Further Reading

- **Rudin, Principles of Mathematical Analysis:** Chapter 1 (The Real Number System)
- **Munkres, Topology:** §20 (Metric Topology), §27 (Compact Spaces in Metric Topology)
- **Kolmogorov & Fomin, Introductory Real Analysis:** Chapter 2 (Metric Spaces)
- **Sutherland, Introduction to Metric and Topological Spaces:** Chapters 1–3

---

## 🎓 Summary

Trong bài giảng này, chúng ta đã hoàn thiện nền móng:

✅ **Số thực ℝ:** Construction qua Dedekind cuts hoặc Cauchy sequences  
✅ **Completeness:** LUB property, Archimedean property, density  
✅ **Metric spaces:** Định nghĩa khoảng cách, nhiều ví dụ metrics  
✅ **Metric topology:** Open balls → open sets → topology  
✅ **Euclidean space ℝⁿ:** Ví dụ cụ thể quan trọng nhất  
✅ **Convergence:** Cauchy sequences, completeness  

**Điểm chính:**
- ℝ "đầy đủ" (complete) theo nghĩa mọi Cauchy sequence hội tụ
- Metric là cách formalize "khoảng cách"
- Mọi metric tự động induce topology qua open balls
- ℝⁿ là ví dụ prototype cho mọi khái niệm topology
- Completeness là tính chất quan trọng—nhiều theorems cần nó

**Connection đến topology:**
- Topology ra đời để trừu tượng hóa các properties của ℝ không phụ thuộc vào metric cụ thể
- Open sets trong topology = generalization của open balls
- Continuity trong topology = generalization của ε-δ definition

**Kết thúc Chapter 00!**  
Chúng ta đã xây dựng đầy đủ nền tảng:
- Set theory, functions, relations
- Axiom of Choice, Zorn's Lemma
- Logic, proof techniques
- Real numbers, metric spaces

**Tiếp theo:** Chapter 01 sẽ giới thiệu **TOPOLOGICAL SPACES**—định nghĩa chính thức của topology, basis, continuous functions, và các ví dụ beyond metric spaces!

---

*"In mathematics, you don't understand things. You just get used to them." — John von Neumann*

🎯 **Chúc mừng hoàn thành Chapter 00! Bây giờ bạn đã sẵn sàng cho Topology thực sự!** 🎯

---

**Previous:** [Lecture 00.02: Logic and Mathematical Proofs](/contents/vi/topology-chapter00/00_02_Logic_Mathematical_Proofs/)  
**Next Chapter:** [Chapter 01: Topological Spaces and Continuous Functions](/contents/vi/topology-chapter01/)

