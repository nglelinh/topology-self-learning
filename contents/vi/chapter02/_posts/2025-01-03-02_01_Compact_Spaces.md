---
layout: post
title: "Lecture 02.01: Compact Spaces"
lang: vi
lang-ref: lecture-02-01
chapter: 2
lecture: 1
categories: [chapter02]
tags: [compact-spaces, heine-borel, sequential-compactness, limit-point-compactness]
description: "Không gian compact, Heine-Borel theorem, và các characterizations"
---

**Compact Spaces**

---

## 📖 Tổng quan

Nếu **connectedness** là về "one piece", thì **compactness** là về "finiteness in disguise" (finite ẩn trong vô hạn).

**Câu hỏi trực quan:** Khi nào một không gian là "small" theo nghĩa topology?

Trong metric spaces, "bounded and closed" thường là câu trả lời (**Heine-Borel Theorem**). Nhưng trong general topology, chúng ta cần định nghĩa trừu tượng hơn!

**Ý tưởng cốt lõi:**  
> **Compact = "Mọi open cover có finite subcover"**

Nghe phức tạp? Hãy nghĩ như sau:
- Bạn có một space X
- Bạn "phủ" X bằng **vô số** open sets
- Compactness nói: "Chỉ cần **hữu hạn** trong số chúng là đủ!"

![Open cover illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Compact_space.svg/400px-Compact_space.svg.png)  
*Compact space: mọi open cover có finite subcover - Nguồn concept*

**Trong bài này:**
- Định nghĩa **compactness** qua open covers
- **Heine-Borel Theorem**: [a,b] compact trong ℝ
- **Closed subsets** của compact spaces
- **Continuous images** của compact spaces
- **Sequential compactness** trong metric spaces
- **Extreme Value Theorem**: ứng dụng trong analysis

**Tại sao quan trọng?**
- Compact spaces = "nice" spaces (nhiều theorems work!)
- Heine-Borel: characterize compact subsets của ℝⁿ
- EVT: continuous functions trên compact spaces đạt max/min
- Tychonoff: products của compact spaces là compact

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Hotel

Tưởng tượng bạn quản lý một **infinite hotel** (khách sạn vô hạn) với rooms đánh số 1, 2, 3, ...

**Open cover analogy:**  
Mỗi open set = một "service area" (khu vực phục vụ). Bạn muốn:
- **Cover toàn bộ hotel** (mọi room được serve)
- Sử dụng **ít service areas nhất có thể** (economic!)

**Compact hotel:**  
Dù có vô số service areas available, luôn có thể chọn **hữu hạn** areas để cover toàn bộ!

**Non-compact hotel (ví dụ: ℕ):**  
Xét cover: Uₙ = {n, n+1, n+2, ...}  
Mỗi Uₙ open, ⋃Uₙ = ℕ.  
Nhưng **không thể** chọn hữu hạn Uₙ để cover ℕ!  
→ ℕ không compact.

**Compact space [0,1]:**  
Bất kỳ open cover nào của [0,1], luôn có thể extract finite subcover.  
→ [0,1] compact!

---

## 📐 Định nghĩa Hình thức

### 1. Compact Spaces

**Định nghĩa (Open Cover):**  
Họ {Uα}α∈I ⊆ 𝜏 là **open cover** của X nếu:

$$
X = \bigcup_{\alpha \in I} U_\alpha
$$

**Định nghĩa (Subcover):**  
{Uβ}β∈J ⊆ {Uα}α∈I là **subcover** nếu vẫn cover X:

$$
X = \bigcup_{\beta \in J} U_\beta, \quad J \subseteq I
$$

**Định nghĩa (Compact Space):**  
X là **compact** nếu mọi open cover có **finite subcover**.

$$
\forall \{U_\alpha\}_{\alpha \in I} \text{ open cover}: \exists \text{ finite } J \subseteq I: X = \bigcup_{\alpha \in J} U_\alpha
$$

**Ví dụ 1: Finite Space**

X = {1, 2, 3} với bất kỳ topology nào → **compact**!

**Proof:** Mọi open cover là finite (vì X finite) → tự động có finite subcover. ✓

**Ví dụ 2: [0,1] compact**

Chứng minh cần Heine-Borel theorem (xem sau).

**Ví dụ 3: ℕ KHÔNG compact**

Cover: Uₙ = {n} (discrete topology).  
{Uₙ}ₙ∈ℕ là open cover.  
Không thể extract finite subcover (mỗi element cần một set riêng). ✗

**Ví dụ 4: (0,1) KHÔNG compact**

Cover: Uₙ = (1/n, 1) với n ≥ 2.  
⋃ₙ≥₂ Uₙ = (0,1) (mọi x ∈ (0,1): x > 1/n với n đủ lớn).  
Nếu chọn finite subcover: U_{n₁}, ..., U_{nₖ}, let N = max{nᵢ}.  
⋃ᵢ U_{nᵢ} = U_N = (1/N, 1) ≠ (0,1). ✗

→ (0,1) không compact.

---

### 2. Properties of Compact Spaces

**Định lý (Closed Subspace):**  
Nếu K ⊆ X với K compact và X Hausdorff, thì K **closed**.

**Chứng minh (sketch):**  
Cho x ∉ K. Với mọi y ∈ K, Hausdorff → ∃ Uᵧ ∋ x, Vᵧ ∋ y disjoint.  
{Vᵧ}ᵧ∈K là open cover của K → có finite subcover V_{y₁}, ..., V_{yₙ}.  
U = U_{y₁} ∩ ... ∩ U_{yₙ} là neighborhood của x disjoint với K.  
→ X \ K open → K closed. ∎

**Chú ý:** Hausdorff essential! Trong trivial topology, mọi subset compact nhưng không nhất thiết closed.

---

**Định lý (Closed Subset of Compact):**  
Nếu X compact và F ⊆ X closed, thì F **compact** (subspace topology).

**Chứng minh:**  
Cho {Uα} open cover của F trong X.  
Thêm X \ F (open) → {Uα} ∪ {X \ F} là open cover của X.  
X compact → có finite subcover.  
Bỏ X \ F đi → finite subcover của F. ∎

**Hệ quả:** Trong Hausdorff space, compact ⟺ closed bounded (trong metric spaces).

---

**Định lý (Continuous Image):**  
Nếu f: X → Y continuous và X compact, thì **f(X) compact**.

**Chứng minh:**  
Cho {Vα} open cover của f(X) trong Y.  
{f⁻¹(Vα)} là open cover của X (f continuous).  
X compact → có finite subcover f⁻¹(V_{α₁}), ..., f⁻¹(V_{αₙ}).  
→ f(X) ⊆ V_{α₁} ∪ ... ∪ V_{αₙ}. ∎

**Hệ quả quan trọng:**  
**Compactness là topological invariant!**

X ≅ Y và X compact → Y compact.

---

**Định lý (Extreme Value Theorem - EVT):**  
Nếu X compact, f: X → ℝ continuous, thì f **đạt maximum và minimum**.

$$
\exists x_{\max}, x_{\min} \in X: \forall x \in X: f(x_{\min}) \leq f(x) \leq f(x_{\max})
$$

**Chứng minh:**  
f(X) ⊆ ℝ compact (continuous image).  
f(X) ⊆ ℝ closed and bounded (Heine-Borel).  
f(X) bounded → sup f(X), inf f(X) tồn tại.  
f(X) closed → sup, inf ∈ f(X). ✓

![Extreme Value Theorem](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Extreme_value_theorem.svg/400px-Extreme_value_theorem.svg.png)  
*EVT: continuous function trên compact đạt max/min - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Extreme_value_theorem.svg)*

**Ứng dụng:** Optimization problems!

---

### 3. Heine-Borel Theorem

**Định lý Heine-Borel:**  
Trong **ℝⁿ** (Euclidean topology), tập K compact ⟺ K **closed và bounded**.

**Chứng minh (sketch cho ℝ):**

**(⇒) Compact ⇒ Closed và Bounded:**

**Bounded:** Cover ℝ bởi {(-n, n)}ₙ∈ℕ.  
K compact → ∃ finite subcover → K ⊆ (-N, N) bounded. ✓

**Closed:** ℝ Hausdorff → compact subsets closed. ✓

**(⇐) Closed và Bounded ⇒ Compact:**

Đủ chứng minh [a, b] compact.  
**Proof bằng phản chứng:** (Bisection method)

Giả sử [a, b] không compact. Tồn tại open cover {Uα} không có finite subcover.  
Chia [a, b] thành [a, m], [m, b] với m = (a+b)/2.  
Ít nhất một trong hai không có finite subcover (nếu cả hai có → [a,b] có).  
Gọi [a₁, b₁] là interval đó.  
Lặp lại: có nested sequence [a, b] ⊇ [a₁, b₁] ⊇ [a₂, b₂] ⊇ ...  
với bₙ - aₙ = (b - a)/2ⁿ → 0.

Completeness của ℝ → ∃ x ∈ ⋂ₙ [aₙ, bₙ].  
x ∈ [a, b] → x ∈ Uα₀ với α₀ nào đó.  
Uα₀ open → ∃ε: (x - ε, x + ε) ⊆ Uα₀.  
Chọn n lớn: bₙ - aₙ < ε → [aₙ, bₙ] ⊆ Uα₀.  
Mâu thuẫn với [aₙ, bₙ] không có finite subcover! ∎

**Hệ quả:** [a, b], [a, b), (a, b], {closed ball trong ℝⁿ} compact.

**Non-examples:** (a, b), ℝ, ℕ không compact (không closed hoặc không bounded).

---

### 4. Sequential Compactness

**Trong metric spaces**, có characterization khác của compactness!

**Định nghĩa (Sequentially Compact):**  
X là **sequentially compact** nếu mọi sequence có **convergent subsequence**.

$$
\forall (x_n) \text{ sequence}: \exists \text{ subsequence } (x_{n_k}), \exists x \in X: x_{n_k} \to x
$$

**Định lý (Metric Spaces):**  
Trong metric space, các khái niệm sau **tương đương**:
1. Compact
2. Sequentially compact
3. Limit point compact (mọi infinite subset có limit point)

**Chứng minh:** Advanced (cần Lebesgue number lemma).

**Ví dụ:** [0,1] sequentially compact = Bolzano-Weierstrass theorem!

**Chú ý:** Trong general topological spaces, equivalence **sai**!

---

### 5. Locally Compact Spaces

**Định nghĩa (Locally Compact):**  
X là **locally compact** nếu mọi x ∈ X có compact neighborhood.

**Ví dụ:**
- **ℝⁿ** locally compact (mọi x có compact neighborhood [x-1, x+1]ⁿ)
- **Infinite-dimensional Hilbert space** KHÔNG locally compact
- **ℚ** KHÔNG locally compact (không có compact intervals trong ℚ)

**Định lý:**  
Locally compact Hausdorff spaces có **one-point compactification**.

**Ví dụ:** ℝⁿ → Sⁿ (add "point at infinity").

---

### 6. Compact Metric Spaces

**Định lý (Totally Bounded):**  
Metric space (X, d) compact ⟺ **complete và totally bounded**.

**Định nghĩa (Totally Bounded):**  
∀ε > 0: X có thể cover bởi **finite** balls radius ε.

**Ví dụ:**
- [0,1] totally bounded và complete → compact ✓
- ℝ không totally bounded (cần infinite balls) → không compact ✓
- (0,1) totally bounded nhưng không complete → không compact ✓

**Lebesgue Number Lemma:**  
Nếu (X, d) compact metric space, {Uα} open cover, thì ∃δ > 0 (Lebesgue number):

$$
\forall A \subseteq X: \text{diam}(A) < \delta \implies \exists \alpha: A \subseteq U_\alpha
$$

**Trực giác:** Cover "uniform" — không có "holes" nhỏ hơn δ.

---

### 7. Tychonoff's Theorem (Statement)

**Định lý Tychonoff:**

> **Tích tùy ý các không gian compact là compact** (trong product topology).

$$
\forall i \in I: X_i \text{ compact} \implies \prod_{i \in I} X_i \text{ compact}
$$

**Đây là một trong những định lý mạnh nhất và quan trọng nhất trong topology!**

**Ý nghĩa:**
- Cần **Axiom of Choice** để chứng minh
- Thực tế: Tychonoff ⟺ AC
- Không đúng trong box topology!

**Ví dụ:** [0,1]^ℕ = Hilbert cube compact.

**Ứng dụng:**
- Alaoglu's theorem (functional analysis)
- Existence theorems (PDE, optimization)
- Compactifications

**Chứng minh:** Requires Alexander subbase theorem hoặc ultrafilters. (Very advanced!)

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Eduard Heine** - *"Über trigonometrische Reihen"* (1872)  
   *Uniform continuity trên closed bounded intervals*

2. **Émile Borel** - *"Sur quelques points de la théorie des fonctions"* (1895)  
   *Finite subcover property*

3. **Andrey Tychonoff** - *"Über die topologische Erweiterung von Räumen"* (1930)  
   *Tychonoff's theorem*

4. **Pavel Alexandroff & Pavel Urysohn** - *"Mémoire sur les espaces topologiques compacts"* (1929)  
   *Systematic study của compactness*

### Textbooks

5. **James R. Munkres** - *Topology*, 2nd Ed., **§26–27: Compact Spaces**  
   *Clear exposition*

6. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 10**  
   *Accessible treatment*

7. **Stephen Willard** - *General Topology*, **Chapter 5**  
   *Comprehensive*

8. **John L. Kelley** - *General Topology*, **Chapter 5**  
   *Advanced, nets approach*

---

## 🔗 Applications and Connections

### Analysis - Extreme Value Theorem
**Optimization:** EVT guarantees global max/min tồn tại trên compact domains. Foundation cho calculus of variations.

### Functional Analysis - Alaoglu's Theorem
**Weak-* Compactness:** Unit ball trong dual space weak-* compact (dùng Tychonoff). Key tool trong PDE theory.

### Differential Equations - Existence Theorems
**Peano's Theorem:** ODEs có solution nếu RHS continuous (dùng compactness để extract convergent subsequence).

### Economics - Equilibrium Existence
**Nash Equilibrium:** Exists trong finite games vì strategy space compact (sử dụng fixed point theorems cần compactness).

### Real-World Example
**GPS Triangulation:** Finding closest point trên compact surface của Earth. EVT guarantees minimum distance exists.

---

## Video tham khảo

- **xem trước** [The Concept So Much of Modern Math is Built On | Compactness](https://www.youtube.com/watch?v=td7Nz9ATyWY) — Morphocular, tiếng Anh. Vì sao phủ mở và phủ con hữu hạn là cách đúng để nói một tập không bị loãng ra vô hạn.
- [Basic Topology 4 | Compact Sets](https://www.youtube.com/watch?v=pYli4-0hzSs) — The Bright Side of Mathematics, tiếng Anh. Định nghĩa compact và các tính chất đầu tiên, trong chuỗi Basic Topology.
- [Không gian tô-pô compact](https://www.youtube.com/watch?v=_o4E8YTaDk4) — Cuong Nguyen, tiếng Việt. Không gian compact nói bằng tiếng Việt, để nghe lại định nghĩa trong ngôn ngữ của bài.

## 🧩 Exercises

### Compactness Definition

1. **Verify Compact:**  
   Các spaces sau compact không?
   - a) {1, 2, 3} với discrete topology
   - b) ℕ với discrete topology
   - c) [0, 1]
   - d) (0, 1)

2. **Find Cover:**  
   (0, 1) ⊂ ℝ. Tìm open cover không có finite subcover.

3. **Finite Space:**  
   Chứng minh: Mọi finite space với bất kỳ topology nào đều compact.

### Heine-Borel

4. **Closed và Bounded:**  
   Trong ℝ, tập sau compact không?
   - a) [0, 1] ∪ [2, 3]
   - b) {1/n : n ∈ ℕ} ∪ {0}
   - c) [0, ∞)
   - d) Cantor set

5. **ℝ² Examples:**  
   Trong ℝ², tập sau compact không?
   - a) Closed unit disk {(x,y) : x² + y² ≤ 1}
   - b) Open unit disk {(x,y) : x² + y² < 1}
   - c) Unit circle S¹

### Properties

6. **Continuous Image:**  
   f: [0, 1] → ℝ, f(x) = 1/x nếu x > 0, f(0) = 0.  
   - f continuous không?
   - f([0,1]) compact không?
   - Tại sao không mâu thuẫn với theorem?

7. **Closed Subset:**  
   K ⊆ ℝ compact, F ⊆ K closed.  
   Chứng minh F compact.

8. **Extreme Value:**  
   Áp dụng EVT: Tìm max và min của f(x) = x² - 2x trên [0, 3].

### Sequential Compactness

9. **Bolzano-Weierstrass:**  
   [0, 1] sequentially compact.  
   Cho sequence xₙ = sin(n) trong [0,1].  
   Tìm convergent subsequence (không cần explicit formula).

10. **Counterexample:**  
    ℕ không sequentially compact. Tìm sequence không có convergent subsequence.

### Advanced

11. **Product:**  
    [0,1] × [0,1] compact? (Dùng Tychonoff hoặc Heine-Borel cho ℝ²)

12. **Hilbert Cube:**  
    H = [0,1]^ℕ compact? (Tychonoff!)

13. **Locally Compact:**  
    Chứng minh ℝ locally compact nhưng không compact.

14. **One-Point Compactification:**  
    ℝ + {∞} với topology thích hợp = S¹ (homeomorphic).  
    Mô tả topology này.

15. **Lebesgue Number:**  
    [0,1] với Euclidean topology, cover = {(0, 0.6), (0.4, 1)}.  
    Tìm Lebesgue number δ.

### Reflection

16. **Compact vs Closed:**  
    So sánh:
    - Trong ℝⁿ: compact ⟺ closed + bounded (Heine-Borel)
    - General topology: compact ⇏ closed (trừ khi Hausdorff)
    
    Tại sao Hausdorff quan trọng?

17. **Sequential vs General:**  
    Trong metric spaces, compact ⟺ sequentially compact.  
    Tại sao equivalence này fail trong general spaces?

18. **Applications:**  
    Liệt kê 5 theorems/applications sử dụng compactness:
    - EVT
    - ...

---

## 📚 Further Reading

- **Munkres, Topology:** §26–28 (Compact Spaces, Products)
- **Morris, Topology Without Tears:** Chapter 10
- **Willard, General Topology:** Chapter 5
- **Kelley, General Topology:** Chapter 5 (Nets and Compactness)

---

## 🎓 Summary

Trong bài này, chúng ta học về **compactness**—một trong hai tính chất quan trọng nhất:

✅ **Compact:** Mọi open cover có finite subcover  
✅ **Heine-Borel:** Trong ℝⁿ, compact ⟺ closed + bounded  
✅ **Closed Subset:** Closed subset của compact là compact  
✅ **Continuous Image:** f(compact) = compact  
✅ **EVT:** Continuous f: compact → ℝ đạt max/min  
✅ **Sequential Compactness:** Trong metric spaces, tương đương với compactness  
✅ **Tychonoff:** Products của compact spaces là compact (cần AC)  

**Điểm chính:**
- Compactness = "finiteness in disguise"
- Heine-Borel: characterization cụ thể cho ℝⁿ
- EVT: foundation cho optimization
- Compact spaces are "nice" — nhiều theorems work!
- Tychonoff cần Axiom of Choice

**Practical wisdom:**
- Trong ℝⁿ: check closed + bounded
- Sử dụng EVT để tìm extrema
- Continuous images preserve compactness
- Products preserve compactness (Tychonoff)

**Tiếp theo:** Lecture 02.02 về **Applications of Compactness** với Fixed Point Theorems, Uniform Continuity, và nhiều applications khác!

---

*"Compact spaces are to topology what finite sets are to set theory."* — Standard analogy

🎯 **Practice với Heine-Borel! Identify compact subsets của ℝⁿ.** 🎯

---

**Previous:** [Lecture 02.00: Connected Spaces](/contents/vi/topology-chapter02/02_00_Connected_Spaces/)  
**Next:** [Lecture 02.02: Applications of Compactness](/contents/vi/topology-chapter02/02_02_Applications_Compactness/)

