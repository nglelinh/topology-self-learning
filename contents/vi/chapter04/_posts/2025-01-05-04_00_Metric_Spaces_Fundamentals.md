---
layout: post
title: "Lecture 04.00: Metric Spaces - Fundamentals"
lang: vi
lang-ref: lecture-04-00
chapter: 4
lecture: 0
categories: [chapter04]
tags: [metric-spaces, distance, isometry, completeness, cauchy-sequences]
description: "Không gian metric: định nghĩa, ví dụ, isometries, và tính chất cơ bản"
---

**Metric Spaces - Fundamentals**

---

## 📖 Tổng quan

Chúng ta đã học về các không gian tô-pô—một sự trừu tượng hóa rất tổng quát. Giờ đây, chúng ta quay lại một lớp đặc biệt quan trọng: các không gian metric—những không gian có khái niệm "khoảng cách" (distance).

Tại sao các không gian metric lại đặc biệt? Chúng có nhiều tính chất tốt mà các không gian tô-pô tổng quát không có. Khoảng cách trở nên có thể định lượng được—chúng ta có thể đo lường "xa bao nhiêu" giữa hai điểm, không chỉ đơn giản là chúng có "gần nhau" hay không. Các dãy là đủ để mô tả tô-pô—không cần các nets hoặc filters trừu tượng như trong các không gian tổng quát. Completeness có ý nghĩa rõ ràng: các dãy Cauchy hội tụ, cho phép các kỹ thuật giải tích mạnh mẽ. Chúng rất trực quan, cung cấp hiểu biết hình học và trực quan. Quan trọng nhất, chúng có mặt ở khắp nơi: $\mathbb{R}^n$, các không gian hàm $C([0,1])$, các không gian xác suất—hầu hết các không gian trong giải tích đều là metric.

![Metric space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Metric_space_illustration.svg/500px-Metric_space_illustration.svg.png)  
*Không gian metric với hàm khoảng cách - Nguồn: Wikimedia Commons*

Mối liên hệ với tô-pô học là sâu sắc nhưng tinh tế. Mọi metric đều tạo ra một tô-pô tự nhiên thông qua các quả cầu mở, làm cho các không gian metric trở thành trường hợp đặc biệt của các không gian tô-pô. Tuy nhiên, điều ngược lại không đúng: không phải mọi tô-pô đều đến từ một metric (các không gian metrizable tạo thành một lớp con nghiêm ngặt). Định lý Metrization của Urysohn mô tả chính xác những tô-pô nào là metrizable—một kết quả phân loại đẹp đẽ mà chúng ta sẽ nghiên cứu sau.

Trong bài học này, chúng ta sẽ phát triển một cách có hệ thống lý thuyết về không gian metric. Định nghĩa metric bắt đầu với ba tiên đề cơ bản đặc trưng cho khái niệm khoảng cách. Các ví dụ trải dài từ quen thuộc (Euclidean $d_2$, Manhattan $d_1$, metric max $d_\infty$) đến bất ngờ (discrete metric, các metric không gian hàm). Metric topology xuất hiện một cách tự nhiên: các quả cầu mở định nghĩa cơ sở, tạo ra tô-pô làm cho metric trở thành hàm liên tục. Các isometry bảo toàn khoảng cách một cách hoàn hảo, đại diện cho các "chuyển động cứng" trong bối cảnh trừu tượng. Completeness phân biệt các không gian mà các dãy Cauchy hội tụ (complete) với những không gian có "lỗ hổng" (incomplete).

Tại sao các không gian metric lại là nền tảng? Chúng tạo thành nền tảng cho giải tích thực—giới hạn, tính liên tục, đạo hàm đều được xây dựng trên cấu trúc metric. Chúng kết nối tô-pô học và hình học, cung cấp trực giác hình học cho các khái niệm tô-pô trừu tượng. Các ứng dụng lan tỏa khắp toán học: giải tích hàm nghiên cứu các không gian metric vô hạn chiều, hình học vi phân sử dụng các metric Riemannian, lý thuyết xác suất dựa vào các không gian xác suất metric. Trong khoa học dữ liệu và machine learning, các metric khoảng cách là hoàn toàn cần thiết—clustering, classification, giảm chiều đều phụ thuộc quan trọng vào việc chọn các metric phù hợp.

---

## 📐 Định nghĩa và Axioms

### 1. Metric Spaces

**Định nghĩa (Metric):**  
Cho X là tập hợp. Một **metric** (hay **distance function**) trên X là hàm:

$$
d: X \times X \to \mathbb{R}
$$

thỏa mãn ba axioms:

**(M1) Positive Definiteness:**
$$
d(x,y) \geq 0, \quad d(x,y) = 0 \iff x = y
$$

**(M2) Symmetry:**
$$
d(x,y) = d(y,x)
$$

**(M3) Triangle Inequality:**
$$
d(x,z) \leq d(x,y) + d(y,z)
$$

**Định nghĩa (Metric Space):**  
Cặp (X, d) gọi là **metric space**.

**Trực giác về ba axioms:**
- **(M1):** Khoảng cách không âm, chỉ bằng 0 khi hai điểm trùng nhau
- **(M2):** Khoảng cách từ A đến B = từ B đến A
- **(M3):** Đi trực tiếp ngắn hơn đi vòng

![Triangle inequality](https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/Triangle_inequality.svg/400px-Triangle_inequality.svg.png)  
*Triangle inequality: d(x,z) ≤ d(x,y) + d(y,z) - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Triangle_inequality.svg)*

---

### 2. Standard Examples

**Example 1: Euclidean Metric on ℝⁿ**

$$
d_2(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}
$$

**Verify axioms:**
- (M1): Rõ ràng ✓
- (M2): Symmetry của |xᵢ - yᵢ| ✓  
- (M3): Minkowski inequality (from linear algebra) ✓

Đây là metric "thông thường" trên ℝⁿ.

---

**Example 2: Manhattan Metric (Taxicab)**

$$
d_1(\mathbf{x}, \mathbf{y}) = \sum_{i=1}^n |x_i - y_i|
$$

**Tên gọi:** Khoảng cách "đi theo lưới đường phố" như ở Manhattan.

**Example trong ℝ²:**  
d₁((0,0), (3,4)) = |3| + |4| = 7  
(So với Euclidean: d₂ = 5)

![Manhattan vs Euclidean](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Manhattan_distance.svg/400px-Manhattan_distance.svg.png)  
*Manhattan distance visualization - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Manhattan_distance.svg)*

---

**Example 3: Maximum Metric (Chebyshev)**

$$
d_\infty(\mathbf{x}, \mathbf{y}) = \max_{i=1,\ldots,n} |x_i - y_i|
$$

**Example:** d∞((0,0), (3,4)) = max{3, 4} = 4

**Geometric interpretation:** "Square" balls thay vì circles.

---

**Example 4: Discrete Metric**

Trên **bất kỳ** tập X:

$$
d(x,y) = \begin{cases}
0 & \text{if } x = y \\
1 & \text{if } x \neq y
\end{cases}
$$

**Verify axioms:**
- (M1): Trivial ✓
- (M2): Symmetric ✓
- (M3): d(x,z) ≤ 1 = d(x,y) + d(y,z) nếu x ≠ z ✓

**Property:** Topology induced = discrete topology!

---

**Example 5: Function Spaces**

**Uniform metric** trên $C([0,1], \mathbb{R})$ (các hàm liên tục):

$$
d_\infty(f,g) = \sup_{x \in [0,1]} |f(x) - g(x)|
$$

Đây là metric "supremum norm"—nó đo khoảng cách giữa hai hàm bằng giá trị lớn nhất của sự khác biệt giữa chúng trên toàn bộ miền.

**Example 6: L^p Metrics**

Trên $\mathbb{R}^n$ với $1 \leq p < \infty$:

$$
d_p(\mathbf{x}, \mathbf{y}) = \left(\sum_{i=1}^n |x_i - y_i|^p\right)^{1/p}
$$

Họ các metric này thống nhất nhiều ví dụ:
- $p = 1$: Manhattan metric
- $p = 2$: Euclidean metric  
- $p \to \infty$: Maximum metric

Họ các metric này thống nhất nhiều ví dụ quen thuộc trong một công thức tổng quát!

---

### 3. Metric Topology

**Định nghĩa (Open Ball):**  
**Open ball** tâm x, bán kính r > 0:

$$
B(x, r) = B_d(x, r) = \{y \in X : d(x,y) < r\}
$$

**Định nghĩa (Closed Ball):**

$$
\overline{B}(x, r) = \{y \in X : d(x,y) \leq r\}
$$

**Định nghĩa (Sphere):**

$$
S(x, r) = \{y \in X : d(x,y) = r\}
$$

**Định nghĩa (Induced Topology):**  
Topology **induced** bởi metric d:

$$
\tau_d = \{U \subseteq X : \forall x \in U: \exists r > 0: B(x,r) \subseteq U\}
$$

**Nói bằng lời:** U open ⟺ U là union của open balls.

**Định lý:**  
τ_d thỏa mãn topology axioms.

**Chứng minh:** Exercise (straightforward verification).

---

**Basis for Metric Topology:**

**Định lý:** ℬ = {B(x,r) : x ∈ X, r > 0} là basis cho τ_d.

**Proof:** Trivial từ definition.

**Corollary:** Metric topology second countable nếu X separable.

---

### 4. Convergence in Metric Spaces

**Định nghĩa (Convergence):**  
Sequence (xₙ) **converges** to x nếu:

$$
\forall \varepsilon > 0: \exists N: \forall n \geq N: d(x_n, x) < \varepsilon
$$

**Notation:** xₙ → x hay lim xₙ = x.

**Định lý (Uniqueness):**  
Trong metric space, limits **unique**.

**Proof:** Metric spaces Hausdorff (đã chứng minh trước). ✓

**Định lý (Sequential Characterization):**  
Trong metric space:
- x ∈ cl(A) ⟺ ∃ sequence trong A converging to x
- f continuous ⟺ xₙ → x ⇒ f(xₙ) → f(x)

**Proof:** Metric spaces first countable. ✓

---

### 5. Cauchy Sequences và Completeness

**Định nghĩa (Cauchy Sequence):**  
Sequence (xₙ) là **Cauchy** nếu:

$$
\forall \varepsilon > 0: \exists N: \forall m,n \geq N: d(x_m, x_n) < \varepsilon
$$

**Trực giác:** Terms "cluster together" khi n → ∞.

**Định lý:**  
Mọi convergent sequence là Cauchy.

**Proof:**  
xₙ → x. Cho ε > 0, ∃N: ∀n ≥ N: d(xₙ, x) < ε/2.  
Với m, n ≥ N:
$$
d(x_m, x_n) \leq d(x_m, x) + d(x, x_n) < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
$$
✓

**Converse KHÔNG đúng tổng quát!**

**Counterexample:** (0,1) với Euclidean metric.  
xₙ = 1/n Cauchy nhưng limit 0 ∉ (0,1).

---

**Định nghĩa (Complete Metric Space):**  
(X, d) là **complete** nếu mọi Cauchy sequence converges trong X.

**Examples Complete:**
- ℝⁿ complete (completeness axiom)
- [a, b] complete
- C([0,1]) với uniform metric complete
- ℓ^p complete (p ≥ 1)

**Examples NOT Complete:**
- (0, 1) không complete
- ℚ không complete  
- C([0,1]) với L¹ metric không complete

**Ý nghĩa:** Completeness = "no holes"—mọi Cauchy sequence "should" converge.

---

### 6. Isometries

**Định nghĩa (Isometry):**  
f: (X, d_X) → (Y, d_Y) là **isometry** nếu:

$$
d_Y(f(x), f(y)) = d_X(x, y) \quad \forall x, y \in X
$$

**Nói bằng lời:** f preserves distances exactly.

**Định lý:**  
Mọi isometry là injective và continuous.

**Proof:**
- **Injective:** f(x) = f(y) ⇒ d(x,y) = d(f(x), f(y)) = 0 ⇒ x = y ✓
- **Continuous:** ε-δ trivial với δ = ε ✓

**Định nghĩa (Isometric):**  
(X, d_X) và (Y, d_Y) **isometric** nếu ∃ isometry f: X → Y **surjective**.

**Notation:** X ≅ Y (as metric spaces).

**Ý nghĩa:** Isometric spaces = "same" as metric spaces (up to relabeling).

**Example:**  
[0, 1] và [2, 5] isometric qua f(x) = 3x + 2.

**Chú ý:**  
- Isometry ⇒ homeomorphism
- Homeomorphism ⇏ isometry

**Example:** [0,1] homeomorphic với [0,2] nhưng không isometric (khác "size").

---

### 7. Bounded Sets và Diameter

**Định nghĩa (Bounded Set):**  
A ⊆ X **bounded** nếu ∃M: ∀x, y ∈ A: d(x,y) ≤ M.

**Định nghĩa (Diameter):**

$$
\text{diam}(A) = \sup\{d(x,y) : x, y \in A\}
$$

**Examples:**
- [0, 1] trong ℝ: diam = 1
- ℝ: diam = ∞ (unbounded)
- Finite set: bounded (obviously)

**Định lý:**  
A compact (trong metric space) ⇒ A bounded.

**Proof:** Cover by balls B(x₀, n) → finite subcover → bounded. ✓

**Converse sai:** (0,1) bounded nhưng không compact.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Maurice Fréchet** - *"Sur quelques points du calcul fonctionnel"* (1906)  
   *Introduced abstract metric spaces*

2. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Systematic treatment*

3. **Stefan Banach** - *"Sur les opérations dans les ensembles abstraits"* (1922)  
   *Complete metric spaces, Banach spaces*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§20: Metric Topology**  
   *Standard reference*

5. **Walter Rudin** - *Principles of Mathematical Analysis*, **Chapters 2-3**  
   *Analysis perspective*

6. **Seymour Lipschutz** - *General Topology* (Schaum's)  
   *Accessible với examples*

---

## 🔗 Applications and Connections

### Analysis - Completeness
**Fixed Point Theorems:** Banach Fixed Point Theorem requires complete metric spaces. Applications: solving differential equations.

### Computer Science - Algorithms
**Nearest Neighbor:** k-NN algorithm uses distance metrics (Euclidean, Manhattan) trong feature spaces.

### Data Science - Clustering
**k-Means:** Uses Euclidean distance để cluster data points. Choice của metric affects results!

### Physics - Special Relativity
**Minkowski Metric:** Spacetime với metric không positive-definite. Still satisfies modified axioms.

### Machine Learning - Embeddings
**Word Embeddings:** Words mapped to ℝⁿ với metric measuring semantic similarity.

---

## 🧩 Exercises

### Metric Definition

1. **Verify Axioms:**  
   Với d₁ Manhattan metric, verify chi tiết ba metric axioms.

2. **Discrete Metric:**  
   Chứng minh discrete metric thỏa mãn triangle inequality.

3. **Not a Metric:**  
   Cho d(x,y) = (x - y)². Điều này có phải metric trên ℝ không? Tại sao?

### Examples

4. **Compute Distances:**  
   Trong ℝ² với x = (1,2), y = (4,6):
   - a) d₂ (Euclidean)
   - b) d₁ (Manhattan)
   - c) d∞ (Max)

5. **Function Space:**  
   Trong C([0,1]), tính d∞(f,g) với:
   - f(x) = x, g(x) = x²

6. **L^p Norms:**  
   Với x = (1,2,3) ∈ ℝ³, tính ||x||_p với p = 1, 2, ∞.

### Topology

7. **Open Balls:**  
   Trong ℝ² với Manhattan metric, vẽ B((0,0), 1).  
   Hình dạng gì?

8. **Induced Topology:**  
   Discrete metric induces topology nào?

9. **Basis:**  
   Chứng minh {B(x,r) : x ∈ X, r > 0} là basis cho metric topology.

### Convergence

10. **Sequence:**  
    xₙ = 1/n trong ℝ. Chứng minh xₙ → 0 bằng ε-N definition.

11. **Cauchy:**  
    Chứng minh: convergent ⇒ Cauchy.

12. **Non-Complete:**  
    Trong (0,1), tìm Cauchy sequence không converge trong (0,1).

### Isometries

13. **Verify Isometry:**  
    f: ℝ → ℝ, f(x) = 2x có phải isometry không?

14. **Isometric:**  
    [0,1] và [a,b] isometric. Construct explicit isometry.

15. **Homeomorphism vs Isometry:**  
    Tìm homeomorphism f: [0,1] → [0,2] không phải isometry.

### Advanced

16. **Triangle Inequality:**  
    Chứng minh từ triangle inequality:  
    |d(x,z) - d(y,z)| ≤ d(x,y)

17. **Equivalent Metrics:**  
    d₁, d₂ **equivalent** nếu induce same topology.  
    Chứng minh d₁, d₂, d∞ trên ℝⁿ equivalent.

18. **Completion:**  
    Mọi metric space có "completion" (complete metric space chứa X dense).  
    Ví dụ: completion của ℚ = ℝ.

### Reflection

19. **Why Three Axioms?:**  
    Giải thích ý nghĩa geometric của từng axiom.

20. **Metric vs Topology:**  
    Topology chỉ cần "open sets". Metric thêm "distance".  
    Tradeoff gì giữa generality và structure?

---

## 📚 Further Reading

- **Munkres, Topology:** §20 (Metric Topology)
- **Rudin, PMA:** Chapters 2-3 (Metric Spaces)
- **Sutherland:** *Introduction to Metric and Topological Spaces*
- **Kolmogorov & Fomin:** *Introductory Real Analysis*

---

## 🎓 Summary

Trong bài học này, chúng ta đã khám phá các không gian metric—nền tảng của giải tích hiện đại. Một metric là một hàm $d: X \times X \to \mathbb{R}$ với ba tiên đề: tính xác định dương, tính đối xứng, và bất đẳng thức tam giác. Các ví dụ quan trọng bao gồm Euclidean metric, Manhattan metric, maximum metric, discrete metric, và các metric $L^p$. Metric topology được tạo ra một cách tự nhiên bởi các quả cầu mở—chúng định nghĩa một cơ sở cho tô-pô làm cho metric trở thành hàm liên tục. Sự hội tụ được định nghĩa bằng định nghĩa $\varepsilon$-$N$ cổ điển, và các giới hạn là duy nhất trong không gian metric. Các dãy Cauchy là những dãy mà các phần tử gần nhau tùy ý, và completeness đảm bảo rằng mọi dãy Cauchy đều hội tụ. Các isometry là các ánh xạ bảo toàn khoảng cách một cách hoàn hảo, đại diện cho các "chuyển động cứng" trong bối cảnh trừu tượng.

Điểm chính của bài học là metric = tô-pô + khoảng cách—chúng ta có cả cấu trúc tô-pô và khả năng đo lường khoảng cách. Mọi không gian metric tự động là Hausdorff, regular, normal, và first countable—các tính chất tốt mà các không gian tô-pô tổng quát không nhất thiết có. Completeness là một tính chất riêng biệt khỏi tô-pô—nó phụ thuộc vào metric cụ thể, không chỉ vào tô-pô. $\mathbb{R}^n$ với Euclidean metric là nguyên mẫu của không gian metric—nó là ví dụ quan trọng nhất và được nghiên cứu kỹ nhất. Các ứng dụng của metric spaces lan tỏa khắp toán học: giải tích, khoa học máy tính, khoa học dữ liệu, và vật lý.

Trong thực tế, các metric khác nhau tạo ra các hình học khác nhau—cùng một tập hợp có thể có các tính chất hình học rất khác nhau tùy thuộc vào metric mà chúng ta chọn. Chúng ta cần kiểm tra completeness khi làm việc với các định lý điểm bất động—chúng cần completeness để đảm bảo sự hội tụ. Các isometry bảo toàn các tính chất hình học—chúng là các ánh xạ "cứng" không làm thay đổi hình dạng. Việc chọn metric là quan trọng trong các ứng dụng—metric phù hợp có thể làm cho các bài toán trở nên dễ giải quyết hơn nhiều.

**Tiếp theo:** Lecture 04.01 về **Completeness và Baire Category Theorem**—nghiên cứu sâu hơn về các không gian complete và các ứng dụng!

---

*"A metric space is a topological space with a ruler."* — Geometric intuition

🎯 **Master the metrics! They're everywhere in mathematics.** 🎯

---

**Previous Chapter:** [Chapter 03: Separation Axioms](/contents/vi/topology-chapter03/)  
**Next:** [Lecture 04.01: Completeness and Baire Category](/contents/vi/topology-chapter04/04_01_Completeness_Baire_Category/)

