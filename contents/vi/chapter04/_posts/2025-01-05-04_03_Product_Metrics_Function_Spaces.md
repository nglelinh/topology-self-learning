---
layout: post
title: "Lecture 04.03: Product Metrics and Function Spaces"
lang: vi
lang-ref: lecture-04-03
chapter: 4
lecture: 3
categories: [chapter04]
tags: [product-metrics, function-spaces, uniform-convergence, pointwise-convergence, banach-spaces]
description: "Product metrics, function spaces, uniform vs pointwise convergence, và Banach spaces"
---

**Product Metrics and Function Spaces**

---

## 📖 Tổng quan

Đến giờ chúng ta đã học về các không gian metric hữu hạn chiều như $\mathbb{R}^n$. Nhưng trong toán học, chúng ta thường xuyên làm việc với các **không gian vô hạn chiều**—đặc biệt là các **function spaces** (không gian hàm).

Function spaces là các không gian mà các điểm là các hàm số! Các ví dụ quan trọng bao gồm $C([0,1])$ = các hàm liên tục trên $[0,1]$, $L^p([0,1])$ = các hàm khả tích bậc $p$, và $\ell^p$ = các dãy số có tổng hữu hạn. Đây là những không gian vô hạn chiều—chúng ta không thể mô tả chúng bằng các tọa độ hữu hạn như trong $\mathbb{R}^n$.

Metrics trên function spaces là cực kỳ quan trọng để định nghĩa sự hội tụ của các dãy hàm số, nghiên cứu các phương trình vi phân, phát triển functional analysis, và trong cơ học lượng tử (Hilbert spaces). Không có metric, chúng ta không thể nói về sự hội tụ của các dãy hàm, và điều này là cần thiết cho hầu hết các ứng dụng trong giải tích và vật lý.

![Function space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Uniform_convergence.gif/400px-Uniform_convergence.gif)  
*Hoạt hình về uniform convergence - Nguồn concept*

Trong bài học này, chúng ta sẽ khám phá các khái niệm cơ bản của product metrics và function spaces. Chúng ta bắt đầu với product metrics—các metrics trên $X \times Y$ và các tích vô hạn. Chúng ta sẽ nghiên cứu các metrics trên function spaces—uniform metric, pointwise convergence, và $L^p$ metrics. Chúng ta sẽ khám phá sự khác biệt quan trọng giữa uniform convergence và pointwise convergence—hai khái niệm này rất khác nhau và có các tính chất khác nhau. Chúng ta sẽ nghiên cứu Banach spaces—các không gian vector định chuẩn đầy đủ, và các ví dụ quan trọng như $C([0,1])$, $\ell^p$, và $L^p$.

Tại sao những khái niệm này lại quan trọng đến vậy? Thứ nhất, chúng tạo thành nền tảng của functional analysis—Banach spaces và Hilbert spaces là xương sống của giải tích hàm hiện đại. Thứ hai, trong các phương trình vi phân đạo hàm riêng (PDEs), các nghiệm sống trong function spaces—chúng ta cần các không gian này để nghiên cứu các nghiệm của PDEs. Thứ ba, trong cơ học lượng tử, các wave functions sống trong $L^2$—không gian Hilbert với inner product cho phép chúng ta tính toán các xác suất. Cuối cùng, trong xử lý tín hiệu, không gian $L^2$ là cơ bản cho Fourier analysis và các kỹ thuật xử lý tín hiệu khác.

---

## 🔢 Product Metrics

### 1. Finite Products

**Setup:** (X₁, d₁), (X₂, d₂) metric spaces.

**Goal:** Define metric trên X₁ × X₂.

**Natural options:**

**(1) Maximum metric:**
$$
d_\infty((x_1, x_2), (y_1, y_2)) = \max\{d_1(x_1, y_1), d_2(x_2, y_2)\}
$$

**(2) Sum metric:**
$$
d_1((x_1, x_2), (y_1, y_2)) = d_1(x_1, y_1) + d_2(x_2, y_2)
$$

**(3) Euclidean metric:**
$$
d_2((x_1, x_2), (y_1, y_2)) = \sqrt{d_1(x_1, y_1)^2 + d_2(x_2, y_2)^2}
$$

**Theorem:**  
Cả ba đều metrics trên X₁ × X₂.

**Proof:** Verify axioms (exercise). ✓

---

**Theorem (Equivalence):**  
d₁, d₂, d∞ equivalent trên X₁ × X₂ (finite product).

**Proof:**  
d∞ ≤ d₂ ≤ d₁ ≤ 2·d∞. ✓

**Consequence:** Topology của product well-defined.

---

**Theorem (Relation với Product Topology):**  
Mọi product metric (d₁, d₂, d∞) induces **product topology** τ_{X₁} × τ_{X₂}.

**Proof:**  
Basis cho product topology: U₁ × U₂, Uᵢ open.  
Open balls trong product metric contain products of balls. ✓

---

**Example: ℝⁿ = ℝ × ℝ × ... × ℝ**

Product metrics trên ℝⁿ = d₁, d₂, d∞ (đã học trước).  
All equivalent, induce standard topology. ✓

---

### 2. Infinite Products

**Setup:** (Xₙ, dₙ) metric spaces, n = 1, 2, 3, ...

**Goal:** Metric trên ∏ Xₙ = X₁ × X₂ × X₃ × ...

**Problem:** Naive generalizations fail!
- Σdₙ có thể diverge
- sup dₙ có thể = ∞

**Solution:** Normalize!

---

**Định nghĩa (Uniform Metric trên Infinite Product):**  
Assume dₙ ≤ 1 (bounded). Define:

$$
d((x_n), (y_n)) = \sup_n d_n(x_n, y_n)
$$

**Theorem:** Nếu dₙ ≤ 1, d là metric.

**Proof:** Verify axioms (straightforward). ✓

---

**Alternative (Weighted Metric):**

$$
d((x_n), (y_n)) = \sum_{n=1}^\infty \frac{1}{2^n} d_n(x_n, y_n)
$$

(Assume dₙ ≤ 1 để series converge.)

**Theorem:** d metric, induces product topology.

**Proof:** Technical. See Munkres §20. ✓

---

**Remark:** Different metrics trên infinite products có thể **not equivalent**!  
Sup metric và weighted metric induce same topology (product topology), nhưng convergence properties differ.

---

### 3. Completeness của Products

**Theorem (Finite Products):**  
(X₁, d₁), (X₂, d₂) complete ⇒ (X₁ × X₂, d) complete.

**Proof:**  
(xₙ) = ((x₁ⁿ, x₂ⁿ)) Cauchy trong X₁ × X₂.  
⇒ (x₁ⁿ) Cauchy trong X₁, (x₂ⁿ) Cauchy trong X₂.  
X₁, X₂ complete ⇒ x₁ⁿ → x₁, x₂ⁿ → x₂.  
⇒ (x₁ⁿ, x₂ⁿ) → (x₁, x₂). ✓

---

**Theorem (Infinite Products - Weighted Metric):**  
(Xₙ, dₙ) complete ∀n ⇒ (∏Xₙ, d_weighted) complete.

**Proof:** Tychonoff-style argument (technical). ✓

**Corollary:** ℝ^∞ = ℝ × ℝ × ... complete với weighted metric.

---

## 📊 Function Spaces

### 1. Space of Continuous Functions: C([0,1])

**Definition:**  
C([0,1]) = {f: [0,1] → ℝ : f continuous}

**This is vector space:** (f + g)(x) = f(x) + g(x), (λf)(x) = λf(x).

**Goal:** Define metric.

---

**Metric 1: Uniform (Supremum) Metric**

$$
d_\infty(f, g) = \sup_{x \in [0,1]} |f(x) - g(x)|
$$

**Also called:** Supremum norm, uniform norm.

**Notation:** ||f - g||∞ = d∞(f,g).

**Theorem:** d∞ is metric.

**Proof:**
- (M1): sup |f - g| ≥ 0, = 0 ⟺ f = g ✓
- (M2): Symmetric ✓
- (M3): sup |f - h| ≤ sup |f - g| + sup |g - h| ✓

---

**Theorem (Completeness):**  
(C([0,1]), d∞) complete.

**Proof:**  
(fₙ) Cauchy trong d∞ ⇒ uniformly Cauchy.  
∀x: (fₙ(x)) Cauchy trong ℝ ⇒ f(x) = lim fₙ(x) exists.  
Uniform convergence ⇒ f continuous (standard analysis theorem).  
fₙ → f uniformly ⇒ fₙ → f trong d∞. ✓

**Remark:** Uniform convergence preserves continuity—key property!

---

**Metric 2: L¹ Metric (Integral Metric)**

$$
d_1(f,g) = \int_0^1 |f(x) - g(x)| \, dx
$$

**Theorem:** d₁ is metric trên C([0,1]).

**Proof:** Verify axioms (use integral properties). ✓

**Theorem:** d₁ ≁ d∞ (not equivalent).

**Proof (Counterexample):**  
fₙ(x) = xⁿ.
- d₁(fₙ, 0) = ∫₀¹ xⁿ dx = 1/(n+1) → 0
- d∞(fₙ, 0) = sup xⁿ = 1 ≠ 0

Vậy convergence trong d₁ ≠ convergence trong d∞. ✓

---

**Theorem (NOT Complete):**  
(C([0,1]), d₁) **không complete**.

**Proof sketch:**  
Construct sequence fₙ continuous converging trong d₁ to discontinuous function.

**Example:**  
fₙ(x) = piecewise linear approximation của step function.  
fₙ Cauchy trong d₁, nhưng limit = step function ∉ C([0,1]). ✗

**Lesson:** Completeness depends on metric!

---

### 2. Uniform vs Pointwise Convergence

**Định nghĩa (Uniform Convergence):**  
fₙ **uniformly converges** to f nếu:

$$
\sup_x |f_n(x) - f(x)| \to 0
$$

**Notation:** fₙ ⇉ f.

**Trong metric language:** fₙ → f trong (C([0,1]), d∞).

---

**Định nghĩa (Pointwise Convergence):**  
fₙ **pointwise converges** to f nếu:

$$
\forall x: f_n(x) \to f(x)
$$

**Notation:** fₙ → f pointwise.

---

**Theorem:**  
Uniform convergence ⇒ pointwise convergence.

**Proof:** Trivial. ✓

**Converse sai:**

**Example:** fₙ(x) = xⁿ trên [0,1].
- Pointwise: fₙ(x) → f(x) = {0 if x < 1; 1 if x = 1}
- Không uniform: sup|fₙ(x) - f(x)| = 1 ≠ 0 ✗

---

**Theorem (Preservation của Continuity):**
- Uniform convergence của continuous functions ⇒ limit continuous ✓
- Pointwise convergence ⇒ limit có thể discontinuous ✗

**Example:** fₙ(x) = xⁿ above—limit discontinuous.

**Moral:** Uniform convergence = "good" convergence (preserves properties).

---

### 3. Sequence Spaces: ℓ^p

**Definition:**  
ℓ^p = {sequences (xₙ) : Σ|xₙ|^p < ∞}, 1 ≤ p < ∞.

**Metric:**
$$
d_p((x_n), (y_n)) = \left(\sum_{n=1}^\infty |x_n - y_n|^p\right)^{1/p}
$$

**Theorem:** d_p is metric (use Minkowski inequality).

**Theorem:** ℓ^p complete ∀p ≥ 1.

**Proof:** Technical (dominated convergence). ✓

---

**Special case: ℓ²**

ℓ² = {(xₙ) : Σxₙ² < ∞} = **Hilbert space** (với inner product).

**Inner product:**
$$
\langle (x_n), (y_n) \rangle = \sum_{n=1}^\infty x_n y_n
$$

**Norm:** ||x|| = √⟨x,x⟩.

**Metric:** d(x,y) = ||x - y||.

**Applications:**
- Quantum mechanics (wave functions)
- Signal processing (Fourier series)
- Statistics (L² random variables)

---

**ℓ^∞:**

ℓ^∞ = {bounded sequences (xₙ)} với metric:
$$
d_\infty((x_n), (y_n)) = \sup_n |x_n - y_n|
$$

**Theorem:** ℓ^∞ complete.

---

### 4. L^p Spaces

**Definition (Informal):**  
L^p([0,1]) = {measurable functions f : ∫|f|^p < ∞} / equivalence a.e.

**Metric:**
$$
d_p(f,g) = \left(\int_0^1 |f(x) - g(x)|^p \, dx\right)^{1/p}
$$

**Theorem:** L^p complete (Riesz-Fischer Theorem).

**Relation với C([0,1]):**
- C([0,1]) ⊊ L^p (continuous ⊆ integrable)
- C([0,1]) dense trong L^p
- Completion của (C([0,1]), d_p) = L^p

---

**L²:**

L²([0,1]) = Hilbert space với inner product:
$$
\langle f, g \rangle = \int_0^1 f(x)g(x) \, dx
$$

**Applications:**
- Fourier series
- PDEs (weak solutions)
- Quantum mechanics

---

## 🎓 Banach Spaces

### 1. Normed Vector Spaces

**Định nghĩa (Norm):**  
V vector space. **Norm** là hàm ||·|| : V → ℝ thỏa:

**(N1) Positive definite:** ||x|| ≥ 0, ||x|| = 0 ⟺ x = 0

**(N2) Homogeneity:** ||λx|| = |λ| · ||x||

**(N3) Triangle inequality:** ||x + y|| ≤ ||x|| + ||y||

**Định nghĩa (Normed Space):** (V, ||·||) = normed vector space.

---

**Theorem:**  
Mọi norm induces metric: d(x,y) = ||x - y||.

**Proof:** Verify metric axioms từ norm axioms. ✓

---

**Examples:**

**Example 1: ℝⁿ**
- ||x||₁ = Σ|xᵢ|
- ||x||₂ = (Σxᵢ²)^(1/2)
- ||x||∞ = maxᵢ |xᵢ|

**Example 2: C([0,1])**
- ||f||∞ = sup|f(x)|

**Example 3: ℓ^p**
- ||(xₙ)||_p = (Σ|xₙ|^p)^(1/p)

**Example 4: L^p**
- ||f||_p = (∫|f|^p)^(1/p)

---

### 2. Banach Spaces

**Định nghĩa (Banach Space):**  
Normed vector space (V, ||·||) **complete** (as metric space) gọi là **Banach space**.

**Trực giác:** Banach space = complete normed vector space.

---

**Examples của Banach Spaces:**

✅ ℝⁿ (finite-dimensional, mọi norm)  
✅ C([0,1]) với ||·||∞  
✅ ℓ^p với 1 ≤ p ≤ ∞  
✅ L^p([0,1]) với 1 ≤ p ≤ ∞  

**Non-example:**

✗ C([0,1]) với ||·||₁ (không complete)

---

**Theorem (Finite-Dimensional):**  
Mọi finite-dimensional normed vector space là Banach space.

**Proof:** Equivalent với ℝⁿ, which complete. ✓

**Corollary:** ℝⁿ với bất kỳ norm nào = Banach space.

---

### 3. Hilbert Spaces

**Định nghĩa (Inner Product Space):**  
V vector space với **inner product** ⟨·,·⟩ thỏa:

**(IP1) Linearity:** ⟨ax + by, z⟩ = a⟨x,z⟩ + b⟨y,z⟩  
**(IP2) Symmetry:** ⟨x,y⟩ = ⟨y,x⟩ (or conjugate in ℂ)  
**(IP3) Positive definite:** ⟨x,x⟩ ≥ 0, ⟨x,x⟩ = 0 ⟺ x = 0

**Theorem:**  
Inner product induces norm: ||x|| = √⟨x,x⟩.

**Proof:** Verify norm axioms (use Cauchy-Schwarz). ✓

---

**Định nghĩa (Hilbert Space):**  
Inner product space **complete** (as metric space) gọi là **Hilbert space**.

**Trực giác:** Hilbert space = complete inner product space = Banach space với inner product.

---

**Examples của Hilbert Spaces:**

✅ ℝⁿ với standard inner product  
✅ ℓ²  
✅ L²([0,1])  

**Remark:** ℓ¹, L¹ Banach nhưng không Hilbert (norm không từ inner product).

---

**Theorem (Parallelogram Law):**  
Norm từ inner product ⟺ satisfies:

$$
||x + y||^2 + ||x - y||^2 = 2(||x||^2 + ||y||^2)
$$

**Application:** Test if norm từ inner product.

**Example:** ||·||₁ trên ℝ² không satisfy ⇒ không từ inner product. ✓

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Stefan Banach** - *"Théorie des opérations linéaires"* (1932)  
   *Foundation của Banach spaces*

2. **David Hilbert** - *"Grundzüge einer allgemeinen Theorie der linearen Integralgleichungen"* (1912)  
   *Hilbert spaces*

3. **Frigyes Riesz & Ernst Fischer** - *Riesz-Fischer Theorem* (1907)  
   *Completeness của L^p*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§20, §21, §43**

5. **Walter Rudin** - *Real and Complex Analysis*, **Chapters 3-4**  
   *L^p spaces*

6. **Walter Rudin** - *Functional Analysis*, 2nd Ed.  
   *Comprehensive treatment*

7. **Elias Stein & Rami Shakarchi** - *Functional Analysis*, **Chapters 1-2**

---

## 🔗 Applications and Connections

### Functional Analysis
**Foundation:** Banach và Hilbert spaces = backbone của modern functional analysis.

### Quantum Mechanics
**Wave Functions:** Live trong L²(ℝ³). Inner product = probability amplitudes.

### PDEs
**Weak Solutions:** Formulated trong Sobolev spaces (completions của smooth functions).

### Signal Processing
**Fourier Analysis:** L² space với orthonormal basis {e^(inx)}.

### Machine Learning
**Reproducing Kernel Hilbert Spaces (RKHS):** Foundation cho kernel methods, SVMs.

---

## Video tham khảo

- **xem trước** [Product metrics (revised)](https://www.youtube.com/watch?v=jBe5jkrzsV4) — Andrew McCrady, tiếng Anh. Metric tích, đúng phép dựng ở nửa đầu bài.
- [MAST30026 Lecture 13: Metrics on function spaces (Part 2)](https://www.youtube.com/watch?v=t6B7UCHvz18) — metauni, tiếng Anh. Metric trên không gian hàm, nửa sau của bài, trong giáo trình MAST30026.
- [Metric Spaces | Lecture 15 | Example of Norm on set of Continuous Functions](https://www.youtube.com/watch?v=10geqkzytCA) — Ranjan Khatu, tiếng Anh. Chuẩn sup trên hàm liên tục, ví dụ cụ thể của metric hàm mà bài đang dùng.

## 🧩 Exercises

### Product Metrics

1. **Verify Metric:**  
   d∞((x₁,x₂), (y₁,y₂)) = max{d₁(x₁,y₁), d₂(x₂,y₂)} satisfies metric axioms.

2. **Equivalence:**  
   Chứng minh d₁, d₂, d∞ equivalent trên ℝ × ℝ.

3. **Completeness:**  
   X, Y complete ⇒ X × Y complete. Prove.

### Function Spaces

4. **Uniform Metric:**  
   Compute d∞(f,g) với f(x) = x, g(x) = x² trong C([0,1]).

5. **L¹ Metric:**  
   Compute d₁(f,g) với same f, g.

6. **Not Equivalent:**  
   fₙ(x) = xⁿ. Show d₁(fₙ, 0) → 0 nhưng d∞(fₙ, 0) ≠ 0.

### Convergence

7. **Pointwise:**  
   fₙ(x) = x/n pointwise converges to? Uniformly?

8. **Uniform:**  
   fₙ(x) = sin(x/n) uniformly converges to f(x) = 0. Verify bằng ε-N.

9. **Continuous Limit:**  
   fₙ continuous, fₙ ⇉ f ⇒ f continuous. Prove carefully.

### ℓ^p Spaces

10. **Verify:**  
    (1, 1/2, 1/3, ...) ∈ ℓ²? ℓ¹?

11. **Compute:**  
    ||(1, 1/2, 1/4, ...)||₂.

12. **Cauchy-Schwarz:**  
    ⟨x,y⟩ ≤ ||x||₂ · ||y||₂ trong ℓ². Verify với explicit x, y.

### Banach Spaces

13. **Verify Norm:**  
    ||f||∞ = sup|f(x)| satisfies norm axioms trên C([0,1]).

14. **Not from Inner Product:**  
    ||·||₁ trên ℝ² không satisfy parallelogram law. Verify.

15. **Completeness:**  
    ℓ² complete. Sketch proof.

### Advanced

16. **Sobolev Spaces:**  
    Research W^{1,2}([0,1]) = {f : f, f' ∈ L²}. Banach space?

17. **Dual Space:**  
    Dual của ℓ^p = ℓ^q với 1/p + 1/q = 1. Example: dual(ℓ²) = ℓ².

18. **Operator Norm:**  
    T: V → W linear continuous. ||T|| = sup{||Tx|| : ||x|| ≤ 1}. Verify norm axioms.

### Reflection

19. **Why Completeness?:**  
    Tại sao completeness crucial trong functional analysis?

20. **Applications:**  
    Explain vai trò của L² trong quantum mechanics hoặc signal processing.

---

## 📚 Further Reading

- **Rudin, Functional Analysis:** Comprehensive
- **Reed & Simon, Vol. 1:** Physics perspective
- **Brezis, Functional Analysis:** Modern approach
- **Munkres, Topology:** §20-21 (metric spaces)

---

## 🎓 Summary

Trong bài học này, chúng ta đã khám phá **product metrics** và **function spaces**—các công cụ cơ bản để nghiên cứu các không gian vô hạn chiều. Product metrics bao gồm $d_1$, $d_2$, và $d_\infty$ trên $X \times Y$—tất cả đều tương đương cho các tích hữu hạn và tạo ra cùng topology. Trong không gian các hàm liên tục $C([0,1])$, uniform metric $d_\infty$ là complete—đây là một tính chất quan trọng cho phép chúng ta chứng minh sự tồn tại của các nghiệm. Uniform convergence và pointwise convergence là hai khái niệm rất khác nhau—uniform convergence kéo theo pointwise convergence và bảo toàn tính liên tục, trong khi pointwise convergence không nhất thiết bảo toàn tính liên tục. Các không gian dãy $\ell^p$ là các không gian của các dãy số với metric $d_p$, và chúng đều complete. Các không gian hàm $L^p$ là các không gian của các hàm khả tích bậc $p$ với metric $d_p$, và chúng cũng complete nhờ định lý Riesz-Fischer. Banach spaces là các không gian vector định chuẩn đầy đủ—chúng là nền tảng của functional analysis. Hilbert spaces là các không gian inner product đầy đủ—chúng có cấu trúc hình học phong phú hơn nhờ inner product, và các ví dụ quan trọng bao gồm $\ell^2$ và $L^2$.

Điểm chính của bài học là function spaces là các không gian vô hạn chiều—chúng ta không thể mô tả chúng bằng các tọa độ hữu hạn như trong $\mathbb{R}^n$. Uniform convergence là "tốt"—nó bảo toàn các tính chất như tính liên tục và tính khả tích, trong khi pointwise convergence có thể không bảo toàn các tính chất này. Completeness phụ thuộc vào metric—cùng một không gian có thể complete với metric này nhưng không complete với metric khác. Banach spaces là nền tảng của functional analysis—chúng cho phép chúng ta nghiên cứu các toán tử tuyến tính và các phương trình vi phân. Hilbert spaces có cấu trúc hình học phong phú nhờ inner product—chúng cho phép chúng ta định nghĩa các khái niệm như góc và trực giao.

Trong thực tế, chúng ta kiểm tra completeness để chứng minh các định lý tồn tại—nhiều định lý trong functional analysis yêu cầu không gian phải complete. Chúng ta sử dụng uniform convergence trong các ứng dụng—nó đảm bảo rằng các tính chất được bảo toàn khi chúng ta lấy giới hạn. Không gian $L^2$ xuất hiện ở khắp nơi—trong cơ học lượng tử, xử lý tín hiệu, và Fourier analysis. Các không gian $\ell^p$ mô hình hóa các dãy số—chúng cho phép chúng ta nghiên cứu các dãy số một cách có hệ thống.

**Chapter 04 hoàn thành!** Chúng ta đã nắm vững metric spaces: định nghĩa, completeness, Baire, equivalence, function spaces, và Banach/Hilbert spaces.

**Tiếp theo:** Chapter 05 về **Quotient Spaces và Surfaces**—topology của gluing và manifolds!

---

*"Infinite-dimensional spaces are where analysis truly lives."* — Functional analyst's motto

🎯 **Master the function spaces! They're everywhere in modern mathematics.** 🎯

---

**Previous:** [Lecture 04.02: Equivalent Metrics and Uniform Continuity](/contents/vi/topology-chapter04/04_02_Equivalent_Metrics_Uniform_Continuity/)  
**Next Chapter:** [Chapter 05: Quotient Spaces and Surfaces](/contents/vi/topology-chapter05/)

