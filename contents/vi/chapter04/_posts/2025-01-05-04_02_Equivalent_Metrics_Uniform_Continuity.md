---
layout: post
title: "Lecture 04.02: Equivalent Metrics and Uniform Continuity"
lang: vi
lang-ref: lecture-04-02
chapter: 4
lecture: 2
categories: [chapter04]
tags: [equivalent-metrics, uniform-continuity, lipschitz, contraction]
description: "Equivalent metrics, uniform continuity, Lipschitz maps, và contraction mappings"
---

**Equivalent Metrics and Uniform Continuity**

---

## 📖 Tổng quan

Một không gian có thể có nhiều metrics khác nhau, nhưng chúng có thể tạo ra cùng một topology. Đây là khái niệm về các metric tương đương—các metric khác nhau nhưng cùng một topology. Điều này có nghĩa là mặc dù cách đo khoảng cách có thể khác nhau, cấu trúc tô-pô cơ bản vẫn giữ nguyên—các tập mở, các dãy hội tụ, và các hàm liên tục đều giống nhau.

Uniform continuity là một sự tăng cường của tính liên tục: $\delta$ không phụ thuộc vào điểm $x$. Điều này có những hệ quả sâu sắc—nó cho phép chúng ta kiểm soát sự biến thiên của hàm một cách đồng đều trên toàn bộ miền, không chỉ tại từng điểm riêng lẻ. Điều này đặc biệt quan trọng khi làm việc với các hàm trên các không gian compact hoặc khi cần mở rộng các hàm từ một tập dày đặc.

![Uniform continuity visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Nonuniform_continuity.svg/500px-Nonuniform_continuity.svg.png)  
*Liên tục nhưng không liên tục đều - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Nonuniform_continuity.svg)*

Các contraction mappings là trường hợp đặc biệt của uniform continuity, dẫn đến định lý điểm bất động mạnh mẽ của Banach. Một contraction mapping là một ánh xạ làm giảm khoảng cách giữa các điểm—nó "co lại" không gian. Định lý Banach cho chúng ta biết rằng mọi contraction mapping trên một không gian metric complete đều có một điểm bất động duy nhất, và chúng ta có thể tìm điểm này bằng cách lặp lại ánh xạ từ một điểm bất kỳ.

Trong bài học này, chúng ta sẽ khám phá các khái niệm về equivalent metrics và uniform continuity. Chúng ta bắt đầu với định nghĩa của equivalent metrics và các cách đặc trưng chúng—bằng cách sử dụng ánh xạ đồng nhất, sự hội tụ của dãy, hoặc các quả cầu mở. Chúng ta sẽ nghiên cứu các ví dụ quan trọng như các metric trên $\mathbb{R}^n$ và các ví dụ về các metric không tương đương. Chúng ta sẽ định nghĩa uniform continuity và khám phá mối quan hệ của nó với tính liên tục thông thường. Chúng ta sẽ nghiên cứu định lý Heine-Cantor, cho chúng ta biết rằng mọi hàm liên tục trên một không gian compact đều liên tục đều. Chúng ta sẽ khám phá Lipschitz continuity—một dạng continuity định lượng mạnh hơn uniform continuity. Cuối cùng, chúng ta sẽ nghiên cứu contraction mappings và định lý điểm bất động Banach, cùng với các ứng dụng của chúng trong việc giải phương trình và các phương trình vi phân.

Tại sao những khái niệm này lại quan trọng? Thứ nhất, việc chọn metric là quan trọng—các metric khác nhau có thể dẫn đến các tính chất khác nhau, ngay cả khi chúng tương đương về mặt tô-pô. Thứ hai, các định lý điểm bất động là cơ bản trong giải tích—chúng cho phép chúng ta chứng minh sự tồn tại và tính duy nhất của nghiệm cho nhiều loại phương trình. Thứ ba, các định lý này có ứng dụng quan trọng trong các phương trình vi phân thường và đạo hàm riêng—chúng đảm bảo sự tồn tại và tính duy nhất của nghiệm. Cuối cùng, trong giải tích số, các phương pháp lặp hội tụ nhờ các tính chất contraction—đây là cơ sở cho nhiều thuật toán số học.

---

## 🎯 Equivalent Metrics

### 1. Definition và Characterizations

**Định nghĩa (Equivalent Metrics):**  
Hai metrics d₁, d₂ trên X **equivalent** (hay **topologically equivalent**) nếu chúng induce cùng topology:

$$
\tau_{d_1} = \tau_{d_2}
$$

**Notation:** d₁ ~ d₂.

**Trực giác:** Same open sets, same convergent sequences, same continuous functions.

---

**Proposition (Characterization bằng Identity Map):**  
d₁ ~ d₂ ⟺ id: (X, d₁) → (X, d₂) homeomorphism.

**Proof:**  
id homeomorphism ⟺ id, id⁻¹ continuous ⟺ τd₁ = τd₂. ✓

---

**Proposition (Characterization bằng Convergence):**  
d₁ ~ d₂ ⟺ mọi sequence:

$$
x_n \xrightarrow{d_1} x \iff x_n \xrightarrow{d_2} x
$$

**Proof (⇒):**  
τd₁ = τd₂ ⇒ same closed sets ⇒ same convergent sequences. ✓

**Proof (⇐):**  
Convergence characterizes closed sets (first countable) ⇒ same closed sets ⇒ same topology. ✓

---

**Proposition (Characterization bằng Open Balls):**  
d₁ ~ d₂ ⟺ ∀x, r₁ > 0: ∃r₂ > 0: Bd₂(x, r₂) ⊆ Bd₁(x, r₁)  
và ngược lại.

**Proof:** Basis cho topology. ✓

**Practical:** Check balls contain each other.

---

### 2. Examples trên ℝⁿ

**Theorem (Equivalence trên ℝⁿ):**  
Trên ℝⁿ, các metrics sau **equivalent**:

**(1) Euclidean:** d₂(x,y) = (Σ(xᵢ - yᵢ)²)^(1/2)

**(2) Manhattan:** d₁(x,y) = Σ|xᵢ - yᵢ|

**(3) Maximum:** d∞(x,y) = maxᵢ |xᵢ - yᵢ|

**Proof:**  
Chứng minh d∞ ≤ d₂ ≤ d₁ ≤ n·d∞.

**Step 1:** d∞ ≤ d₂.  
maxᵢ |xᵢ - yᵢ| ≤ (Σ(xᵢ - yᵢ)²)^(1/2). ✓

**Step 2:** d₂ ≤ d₁.  
(Σ(xᵢ - yᵢ)²)^(1/2) ≤ Σ|xᵢ - yᵢ| (drop squares). ✓

**Step 3:** d₁ ≤ n·d∞.  
Σ|xᵢ - yᵢ| ≤ n · maxᵢ |xᵢ - yᵢ|. ✓

**Conclusion:** d∞ ≤ d₂ ≤ d₁ ≤ n·d∞ ⇒ equivalent. ✓

**Remark:** Constants depend on n, nhưng equivalence holds.

---

**Corollary:**  
Mọi Lᵖ metric trên ℝⁿ (p ≥ 1) equivalent.

**Proof:** Similar inequalities.

**Consequence:** Topology của ℝⁿ well-defined (independent của choice metric).

---

### 3. Examples NOT Equivalent

**Example 1: Discrete vs Euclidean trên ℝ**

**Discrete metric:**
$$
d_{\text{disc}}(x,y) = \begin{cases}
0 & x = y \\
1 & x \neq y
\end{cases}
$$

**Claim:** d_disc ≁ d_Euclidean trên ℝ.

**Proof:**  
{x} open trong (ℝ, d_disc) nhưng không open trong (ℝ, d_Euclidean). ✓

**Lesson:** Discrete metric induces discrete topology, very different!

---

**Example 2: Different Function Space Metrics**

**Trên C([0,1]):**

**(1) Uniform metric:** d∞(f,g) = sup|f(x) - g(x)|

**(2) L¹ metric:** d₁(f,g) = ∫|f(x) - g(x)|dx

**Claim:** d∞ ≁ d₁.

**Proof:**  
Sequence fₙ(x) = xⁿ:
- d₁(fₙ, 0) = ∫₀¹ xⁿ dx = 1/(n+1) → 0 (converge trong L¹)
- d∞(fₙ, 0) = 1 ∀n (không converge uniformly)

Vậy convergence khác ⇒ topology khác. ✓

**Lesson:** Metrics trên function spaces very sensitive!

---

### 4. Strongly Equivalent Metrics

**Định nghĩa (Strongly Equivalent):**  
d₁, d₂ **strongly equivalent** (hay **uniformly equivalent**) nếu ∃c₁, c₂ > 0:

$$
c_1 d_1(x,y) \leq d_2(x,y) \leq c_2 d_1(x,y) \quad \forall x,y
$$

**Notation:** d₁ ≈ d₂.

**Trực giác:** Metrics differ by constants only.

---

**Theorem:**  
Strongly equivalent ⇒ equivalent.

**Proof:** Inequalities ⇒ open balls contain each other. ✓

**Converse sai:** Equivalent ≠ strongly equivalent.

**Example:** d(x,y) = |x - y| và d'(x,y) = min(|x - y|, 1) trên ℝ equivalent nhưng không strongly equivalent.

---

**Theorem:**  
d₁ ≈ d₂ ⇒ same Cauchy sequences, same completeness.

**Proof:** Inequalities preserve Cauchy property. ✓

**Contrast:** Equivalent metrics có thể have different completeness!

**Example:** d và d' = min(d, 1):
- d ~ d' (same topology)
- d unbounded, d' bounded
- Completeness có thể differ

---

## 🔄 Uniform Continuity

### 1. Definition và Motivation

**Nhắc lại (Continuity):**  
f: (X, d_X) → (Y, d_Y) continuous tại x:

$$
\forall \varepsilon > 0: \exists \delta > 0: d_X(x, x') < \delta \Rightarrow d_Y(f(x), f(x')) < \varepsilon
$$

**Chú ý:** δ phụ thuộc x và ε.

---

**Định nghĩa (Uniform Continuity):**  
f **uniformly continuous** nếu:

$$
\forall \varepsilon > 0: \exists \delta > 0: \forall x, x' \in X: d_X(x, x') < \delta \Rightarrow d_Y(f(x), f(x')) < \varepsilon
$$

**Khác biệt:** δ chỉ phụ thuộc ε, **không phụ thuộc x**.

**Trực giác:** "Uniform control"—same δ works everywhere.

---

**Theorem:**  
Uniformly continuous ⇒ continuous.

**Proof:** Trivial (take δ uniform). ✓

**Converse sai:** Continuous ⇏ uniformly continuous.

---

**Example 1: f(x) = x² trên ℝ**

**Claim:** f continuous nhưng không uniformly continuous.

**Proof:**  
Cho ε = 1.  
Suppose ∃δ works uniformly.  
Chọn x = 1/δ, x' = x + δ/2.  
Then |x - x'| = δ/2 < δ, nhưng:
$$
|f(x') - f(x)| = |(x + \delta/2)^2 - x^2| = |x\delta + (\delta/2)^2| \approx x\delta = 1/\delta \cdot \delta = 1
$$
(Với x lớn, expression > 1.) Contradiction! ✓

**Lesson:** Unbounded derivative ⇒ không uniformly continuous.

---

**Example 2: f(x) = 1/x trên (0,1)**

**Claim:** f continuous nhưng không uniformly continuous.

**Proof:**  
xₙ = 1/n, x'ₙ = 1/(n+1).  
|xₙ - x'ₙ| = 1/n - 1/(n+1) = 1/(n(n+1)) → 0.  
Nhưng |f(xₙ) - f(x'ₙ)| = |n - (n+1)| = 1 ≠ 0.  
Vậy không uniformly continuous. ✓

**Lesson:** Unbounded function trên bounded domain có thể fail.

---

### 2. Uniform Continuity trên Compact Spaces

**Theorem (Heine-Cantor):**  
f: K → Y continuous, K compact ⇒ f uniformly continuous.

**Proof:**  
Cho ε > 0.  
∀x ∈ K: ∃δₓ: B(x, δₓ) ⊆ f⁻¹(B(f(x), ε/2)).  
Cover K = ⋃ B(x, δₓ/2).  
K compact ⇒ finite subcover: x₁, ..., xₙ.  
Chọn δ = min{δₓᵢ/2}.  
∀x, x' với d(x, x') < δ:  
x ∈ B(xᵢ, δₓᵢ/2) cho some i.  
x' ∈ B(xᵢ, δₓᵢ) (triangle inequality).  
Both f(x), f(x') ∈ B(f(xᵢ), ε/2) ⇒ d(f(x), f(x')) < ε. ✓

**Consequence:** Continuous functions trên [a,b] uniformly continuous.

**Remark:** Compactness crucial!

---

### 3. Extension Theorem

**Theorem (Extension of Uniform Continuous Functions):**  
f: A → Y uniformly continuous, Y complete, A dense trong X ⇒ f extends uniquely đến continuous f̄: X → Y.

**Proof sketch:**  
Cho x ∈ X. A dense ⇒ ∃ sequence aₙ ∈ A: aₙ → x.  
f uniformly continuous ⇒ f(aₙ) Cauchy.  
Y complete ⇒ f(aₙ) converges.  
Define f̄(x) = lim f(aₙ). (Independent của choice sequence.)  
f̄ continuous, extends f. ✓

**Application:** Extend functions from ℚ to ℝ.

---

## 📏 Lipschitz Continuity

### 1. Definition

**Định nghĩa (Lipschitz Continuous):**  
f: X → Y **Lipschitz continuous** với **Lipschitz constant** L nếu:

$$
d_Y(f(x), f(y)) \leq L \cdot d_X(x,y) \quad \forall x, y \in X
$$

**Trực giác:** Distance không increase quá L lần.

**Notation:** f is L-Lipschitz.

---

**Theorem:**  
Lipschitz ⇒ uniformly continuous ⇒ continuous.

**Proof:**  
Cho ε > 0. Chọn δ = ε/L.  
d_X(x,y) < δ ⇒ d_Y(f(x), f(y)) ≤ L·d_X(x,y) < L·δ = ε. ✓

**Converse sai:** Uniformly continuous ⇏ Lipschitz.

**Example:** f(x) = √x trên [0,1] uniformly continuous (compact), nhưng không Lipschitz (derivative unbounded tại 0).

---

### 2. Examples

**Example 1:** f(x) = 3x + 5 trên ℝ.  
|f(x) - f(y)| = 3|x - y|. Lipschitz với L = 3. ✓

**Example 2:** f(x) = sin(x) trên ℝ.  
|sin(x) - sin(y)| ≤ |x - y| (mean value theorem). Lipschitz với L = 1. ✓

**Example 3:** f(x) = x² trên [0, M].  
|f(x) - f(y)| = |x - y| · |x + y| ≤ 2M |x - y|. Lipschitz với L = 2M. ✓  
(Nhưng trên ℝ unbounded, không Lipschitz.)

---

### 3. Contraction Mappings

**Định nghĩa (Contraction):**  
f: X → X là **contraction** (hay **contraction mapping**) nếu ∃ k < 1:

$$
d(f(x), f(y)) \leq k \cdot d(x,y) \quad \forall x,y
$$

**Nói bằng lời:** Lipschitz với constant k < 1.

**Trực giác:** f "contracts" distances—điểm closer sau apply f.

---

**Theorem (Banach Fixed Point Theorem):**  
Cho (X, d) complete metric space, f: X → X contraction.  
Thì ∃! x* ∈ X: f(x*) = x* (**fixed point**).

**Moreover:** ∀x₀ ∈ X, sequence xₙ₊₁ = f(xₙ) converges to x*.

**Proof:**

**Step 1 (Construct sequence):**  
Chọn x₀ arbitrary. Define xₙ₊₁ = f(xₙ).

**Step 2 (Cauchy):**  
d(xₙ₊₁, xₙ) = d(f(xₙ), f(xₙ₋₁)) ≤ k·d(xₙ, xₙ₋₁) ≤ ... ≤ kⁿ·d(x₁, x₀).

Với m > n:
$$
d(x_m, x_n) \leq d(x_m, x_{m-1}) + \cdots + d(x_{n+1}, x_n) \leq (k^{m-1} + \cdots + k^n) d(x_1, x_0)
$$
$$
\leq k^n \frac{1}{1-k} d(x_1, x_0) \to 0
$$
Vậy (xₙ) Cauchy. ✓

**Step 3 (Converge):**  
X complete ⇒ xₙ → x* ∈ X.

**Step 4 (Fixed point):**  
f(x*) = f(lim xₙ) = lim f(xₙ) = lim xₙ₊₁ = x*. ✓

**Step 5 (Uniqueness):**  
Suppose f(y) = y.  
d(x*, y) = d(f(x*), f(y)) ≤ k·d(x*, y).  
k < 1 ⇒ d(x*, y) = 0 ⇒ x* = y. ✓ QED

---

**Corollary (Rate of Convergence):**

$$
d(x_n, x^*) \leq \frac{k^n}{1-k} d(x_1, x_0)
$$

**Remark:** Exponential convergence!

---

**Application: Solving Equations**

**Problem:** Solve g(x) = 0.

**Rewrite:** x = x - g(x) = f(x).

**If f contraction trên complete space, ∃! solution.**

**Example:** Solve x = cos(x).  
f(x) = cos(x) contraction trên [0,1]?  
|f'(x)| = |sin(x)| ≤ sin(1) < 1 ✓  
Vậy unique fixed point x* ≈ 0.739. ✓

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Stefan Banach** - *"Sur les opérations dans les ensembles abstraits"* (1922)  
   *Banach Fixed Point Theorem*

2. **Eduard Heine** & **Georg Cantor** - *On uniform continuity* (1870s)  
   *Heine-Cantor theorem*

### Textbooks

3. **James R. Munkres** - *Topology*, 2nd Ed., **§20, §43**

4. **Walter Rudin** - *Principles of Mathematical Analysis*, **Chapter 4**  
   *Uniform continuity*

5. **Serge Lang** - *Real and Functional Analysis*, **Chapter 1**  
   *Banach Fixed Point Theorem*

6. **Michael Reed & Barry Simon** - *Functional Analysis*, **Chapter 1**

---

## 🔗 Applications and Connections

### Differential Equations
**Picard-Lindelöf Theorem:** Existence và uniqueness của ODEs via Banach Fixed Point Theorem.

### Numerical Analysis
**Iterative Methods:** Newton's method, gradient descent converge khi local contraction.

### Economics
**Nash Equilibrium:** Kakutani's Fixed Point Theorem (generalization) proves existence.

### Image Processing
**Fractal Compression:** Uses contraction mappings để encode images.

### Machine Learning
**Training Algorithms:** Convergence analysis uses contraction properties.

---

## Video tham khảo

- **xem trước** [Topology #11 Metric Equivalences](https://www.youtube.com/watch?v=odCnlzlpKZ0) — Daniel Firth, tiếng Anh. Hai metric tương đương khi chúng mở cùng một họ tập, đúng nửa đầu bài.
- [Uniform Continuity Explained | Real Analysis](https://www.youtube.com/watch?v=MmxtJwr3Kws) — Wrath of Math, tiếng Anh. Liên tục đều: epsilon không còn phụ thuộc điểm, đúng nửa sau.
- [Math 441 - 4.4 Uniform Continuity](https://www.youtube.com/watch?v=dQktXveD5bc) — Marc Renault, tiếng Anh. Một buổi học thật về liên tục đều, để thấy chứng minh kiểu ε–δ.

## 🧩 Exercises

### Equivalent Metrics

1. **Verify Equivalence:**  
   Chứng minh chi tiết d₁, d₂, d∞ equivalent trên ℝ².

2. **Not Equivalent:**  
   d_disc và d_Euclidean không equivalent trên ℝ. Chứng minh bằng explicit open set.

3. **Strongly Equivalent:**  
   d(x,y) và 2d(x,y) strongly equivalent? Verify.

### Uniform Continuity

4. **Compute:**  
   f(x) = x³ uniformly continuous trên [-1, 1]? Trên ℝ?

5. **Heine-Cantor:**  
   Áp dụng Heine-Cantor: f(x) = 1/x continuous trên [1,2] ⇒ uniformly continuous.

6. **Counterexample:**  
   Tìm f continuous trên (0,1) nhưng không uniformly continuous.

### Lipschitz

7. **Verify Lipschitz:**  
   f(x) = |x| Lipschitz trên ℝ với L = 1.

8. **Not Lipschitz:**  
   f(x) = x² không Lipschitz trên ℝ. Prove.

9. **Bounded Derivative:**  
   f: [a,b] → ℝ differentiable, |f'| ≤ M ⇒ f Lipschitz với L = M.

### Banach Fixed Point

10. **Apply Banach:**  
    f(x) = (x + 2)/3 contraction trên ℝ. Find fixed point.

11. **Solve Equation:**  
    x = e^(-x) has unique solution. Use Banach Fixed Point.

12. **Rate of Convergence:**  
    Trong bài 11, x₀ = 0. Compute x₁, x₂, x₃. Estimate x*.

### Applications

13. **ODE:**  
    dy/dx = f(x,y), y(0) = y₀. Picard iteration: yₙ₊₁(x) = y₀ + ∫₀ˣ f(t, yₙ(t))dt.  
    Sketch proof convergence using Banach.

14. **Newton's Method:**  
    xₙ₊₁ = xₙ - f(xₙ)/f'(xₙ). When contraction?

15. **Fractal:**  
    Sierpinski triangle defined by contraction mappings. Describe.

### Advanced

16. **Extension Theorem:**  
    f: ℚ ∩ [0,1] → ℝ, f(x) = x². Extend to [0,1].

17. **Kakutani:**  
    Research Kakutani Fixed Point Theorem (set-valued maps).

18. **Brouwer:**  
    Brouwer Fixed Point Theorem (continuous f: Dⁿ → Dⁿ has fixed point).  
    Relation với Banach?

### Reflection

19. **Why Completeness?:**  
    Banach Fixed Point requires completeness. Example contraction trên incomplete space without fixed point?

20. **Applications:**  
    List 3 applications của Banach Fixed Point Theorem trong different fields.

---

## 📚 Further Reading

- **Munkres, Topology:** §20, §43
- **Rudin, PMA:** Chapter 4
- **Kreyszig:** *Introductory Functional Analysis* (Banach spaces)
- **Granas & Dugundji:** *Fixed Point Theory*

---

## 🎓 Summary

Trong bài học này, chúng ta đã khám phá các khái niệm về equivalent metrics và uniform continuity. Các metric tương đương là những metric khác nhau nhưng tạo ra cùng một topology—chúng có cùng các tập mở, cùng các dãy hội tụ, và cùng các hàm liên tục. Trên $\mathbb{R}^n$, các metric $d_1$, $d_2$, và $d_\infty$ đều tương đương—đây là một kết quả quan trọng đảm bảo rằng topology của $\mathbb{R}^n$ được xác định rõ ràng, độc lập với việc chọn metric cụ thể. Các metric strongly equivalent là những metric khác nhau chỉ bởi các hằng số—chúng không chỉ tương đương về mặt tô-pô mà còn có cùng các dãy Cauchy và cùng tính completeness.

Uniform continuity là một sự tăng cường của tính liên tục: $\delta$ không phụ thuộc vào điểm $x$, cho phép chúng ta kiểm soát sự biến thiên của hàm một cách đồng đều trên toàn bộ miền. Định lý Heine-Cantor cho chúng ta biết rằng mọi hàm liên tục trên một không gian compact đều liên tục đều—đây là một kết quả mạnh mẽ cho thấy tầm quan trọng của tính compact. Lipschitz continuity là một dạng continuity định lượng mạnh hơn uniform continuity—nó đảm bảo rằng khoảng cách giữa các ảnh không tăng quá $L$ lần khoảng cách giữa các điểm gốc. Một contraction mapping là một ánh xạ Lipschitz với hằng số $k < 1$—nó "co lại" không gian. Định lý điểm bất động Banach phát biểu rằng mọi contraction mapping trên một không gian metric complete đều có một điểm bất động duy nhất, và chúng ta có thể tìm điểm này bằng cách lặp lại ánh xạ từ một điểm bất kỳ.

Điểm chính của bài học là equivalent metrics tương đương với cùng topology—chúng có cùng cấu trúc tô-pô mặc dù cách đo khoảng cách khác nhau. Uniform continuity mạnh hơn continuity—nó đảm bảo kiểm soát đồng đều trên toàn bộ miền. Lipschitz continuity là mạnh nhất trong ba khái niệm—nó cung cấp một đánh giá định lượng về sự biến thiên của hàm. Định lý Banach rất mạnh mẽ—nó giải quyết các phương trình và phương trình vi phân bằng cách đảm bảo sự tồn tại và tính duy nhất của nghiệm. Completeness là quan trọng—định lý Banach yêu cầu không gian phải complete để đảm bảo sự hội tụ của dãy lặp.

Trong thực tế, chúng ta kiểm tra tính compact để đảm bảo uniform continuity—định lý Heine-Cantor cho chúng ta biết rằng mọi hàm liên tục trên compact đều liên tục đều. Để áp dụng định lý Banach, chúng ta chọn một điểm ban đầu $x_0$, lặp lại ánh xạ, và dãy sẽ hội tụ theo cấp số nhân đến điểm bất động. Các ứng dụng của các khái niệm này có mặt ở khắp nơi: giải tích, giải tích số, và machine learning—chúng là công cụ cơ bản trong nhiều lĩnh vực toán học và khoa học.

**Tiếp theo:** Lecture 04.03 về **Product Metrics và Function Spaces**—các metric trên các không gian vô hạn chiều!

---

*"Fixed points are where iteration comes to rest."* — Banach's wisdom

🎯 **Master the contractions! They solve equations.** 🎯

---

**Previous:** [Lecture 04.01: Completeness and Baire Category](/contents/vi/topology-chapter04/04_01_Completeness_Baire_Category/)  
**Next:** [Lecture 04.03: Product Metrics and Function Spaces](/contents/vi/topology-chapter04/04_03_Product_Metrics_Function_Spaces/)

