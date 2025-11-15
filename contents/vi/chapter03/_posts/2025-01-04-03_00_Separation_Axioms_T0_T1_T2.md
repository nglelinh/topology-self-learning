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

**Separation Axioms - T₀, T₁, T₂ (Hausdorff)**

---

## 📖 Tổng quan

Chúng ta đã học về compact và connected spaces—hai tính chất "global" quan trọng. Giờ đây chúng ta nghiên cứu **separation axioms**—các điều kiện về cách mà các điểm hoặc tập hợp có thể được "tách rời" bởi open sets.

**Câu hỏi động lực:**  
Trong một topological space, làm sao để "distinguish" (phân biệt) hai điểm khác nhau?

**Ví dụ trực quan:**
- **Trivial topology** trên {a, b}: Chỉ có ∅ và {a,b} là open  
  → **Không thể** tách a và b bởi open sets!
  
- **Discrete topology**: Mọi subset open  
  → Có thể tách hoàn toàn: {a} và {b} là open disjoint sets

- **Euclidean ℝ**: Với x ≠ y, luôn có open balls B(x,ε), B(y,δ) disjoint  
  → Có thể tách rời hoàn toàn

**Separation axioms** formalize mức độ "separability" này qua hierarchy:

$$
T_0 \subset T_1 \subset T_2 \subset T_3 \subset T_{3.5} \subset T_4
$$

![Separation axioms hierarchy](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Separation_axioms.svg/500px-Separation_axioms.svg.png)  
*Hierarchy của separation axioms - Nguồn concept*

**Trong bài này:**
- **T₀ (Kolmogorov)**: Điểm có thể distinguish topologically
- **T₁ (Fréchet)**: Singletons closed
- **T₂ (Hausdorff)**: Điểm có disjoint neighborhoods
- Examples và counterexamples
- Importance trong topology

**Tại sao quan trọng?**
- Hausdorff = "standard" assumption trong topology
- Limits unique trong Hausdorff spaces
- Compact subsets closed (trong Hausdorff)
- Metrizable spaces luôn Hausdorff

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Tách biệt

Tưởng tượng bạn có hai người: **Alice** và **Bob**.

**Level 0 (Trivial):** Không có cách nào distinguish Alice và Bob  
→ Giống như trivial topology

**Level 1 (T₀ - Kolmogorov):** Có ít nhất một neighborhood của Alice không chứa Bob, hoặc ngược lại  
→ "Asymmetric" separation

**Level 2 (T₁ - Fréchet):** Alice có neighborhood không chứa Bob **VÀ** Bob có neighborhood không chứa Alice  
→ "Symmetric" nhưng neighborhoods có thể overlap

**Level 3 (T₂ - Hausdorff):** Alice và Bob có **completely disjoint** neighborhoods  
→ "Complete separation"

![T0 T1 T2 illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/T0-T2_spaces.svg/600px-T0-T2_spaces.svg.png)  
*T₀, T₁, T₂ spaces minh họa - Nguồn concept*

---

## 📐 Định nghĩa Hình thức

### 1. T₀ Spaces (Kolmogorov)

**Định nghĩa (T₀ Space):**  
X là **T₀** (Kolmogorov) nếu với mọi x ≠ y ∈ X, tồn tại open set U chứa một điểm nhưng không chứa điểm kia.

$$
\forall x \neq y: \exists U \in \tau: (x \in U \land y \notin U) \lor (y \in U \land x \notin U)
$$

**Trực giác:** Topology có thể "distinguish" hai điểm khác nhau.

**Ví dụ 1: Sierpiński Space**

X = {0, 1}, τ = {∅, {0}, {0,1}}

- U = {0} chứa 0 nhưng không chứa 1
- → T₀ space ✓
- Nhưng không có open set chứa 1 mà không chứa 0
- → Không symmetric!

**Ví dụ 2: Discrete Topology**

Mọi space với discrete topology là T₀ (thực ra là T₂!).

**Non-example: Trivial Topology**

X = {a, b}, τ = {∅, X}

- Mọi open set chứa a cũng chứa b
- → Không T₀ ✗

**Ví dụ 3: Cofinite Topology trên Infinite Set**

X infinite, τ = cofinite topology

- Với x ≠ y: U = X \ {y} open, chứa x, không chứa y
- → T₀ ✓

---

### 2. T₁ Spaces (Fréchet)

**Định nghĩa (T₁ Space):**  
X là **T₁** (Fréchet) nếu với mọi x ≠ y, mỗi điểm có neighborhood không chứa điểm kia.

$$
\forall x \neq y: \exists U, V \in \tau: (x \in U, y \notin U) \land (y \in V, x \notin V)
$$

**Phát biểu tương đương:**  
X là T₁ ⟺ Mọi singleton {x} là **closed**.

**Chứng minh:**

**(⇒)** Giả sử X là T₁, cần chứng minh {x} closed.  
Tương đương: X \ {x} open.  
Với mọi y ∈ X \ {x}, tồn tại Uᵧ ∋ y với x ∉ Uᵧ (T₁ property).  
X \ {x} = ⋃_{y≠x} Uᵧ open. ✓

**(⇐)** Giả sử mọi {x} closed.  
X \ {x} open ∋ y với mọi y ≠ x.  
Tương tự X \ {y} open ∋ x.  
→ T₁. ✓

**Ví dụ 1: Euclidean ℝ**

ℝ là T₁: {x} closed với mọi x.

**Ví dụ 2: Cofinite Topology**

X infinite, cofinite topology là T₁:
- {x} finite → X \ {x} cofinite → open
- → {x} closed ✓

**Non-example: Sierpiński Space**

{0,1} với τ = {∅, {0}, {0,1}}
- {1} không closed (X \ {1} = {0} không open)
- → Không T₁ ✗

**Định lý (T₁ ⇒ T₀):**  
Mọi T₁ space là T₀.

**Chứng minh:** Trivial từ definitions. ∎

---

### 3. T₂ Spaces (Hausdorff)

**Định nghĩa (Hausdorff Space):**  
X là **T₂** (Hausdorff) nếu với mọi x ≠ y, tồn tại **disjoint** open neighborhoods.

$$
\forall x \neq y: \exists U, V \in \tau: x \in U, y \in V, U \cap V = \emptyset
$$

**Trực giác:** Hai điểm khác nhau có thể "completely separated" bởi open sets.

![Hausdorff property](https://upload.wikimedia.org/wikipedia/commons/thumb/9/97/Hausdorff_space.svg/400px-Hausdorff_space.svg.png)  
*Hausdorff property: disjoint neighborhoods - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_space.svg)*

**Ví dụ 1: Metric Spaces**

**Định lý:** Mọi metric space là Hausdorff.

**Chứng minh:**  
Cho x ≠ y trong (X, d).  
Đặt ε = d(x,y)/2 > 0.  
U = B(x, ε), V = B(y, ε).  
U ∩ V = ∅ (triangle inequality). ✓

**Hệ quả:** ℝⁿ với Euclidean metric là Hausdorff.

**Ví dụ 2: Discrete Topology**

Discrete topology trên bất kỳ set nào là Hausdorff.  
U = {x}, V = {y} disjoint.

**Non-example 1: Cofinite Topology (Infinite)**

X infinite, cofinite topology **không** Hausdorff!

**Proof:**  
Cho x ≠ y, U, V open chứa x, y.  
U = X \ A, V = X \ B với A, B finite.  
U ∩ V = X \ (A ∪ B) còn lại infinite ≠ ∅. ✗

**Non-example 2: Trivial Topology**

Trivial topology không Hausdorff (chỉ có X là open set chứa bất kỳ điểm nào).

**Định lý (T₂ ⇒ T₁):**  
Mọi Hausdorff space là T₁.

**Chứng minh:**  
Cho x ≠ y. Hausdorff → ∃U ∋ x, V ∋ y disjoint.  
U không chứa y, V không chứa x.  
→ T₁. ✓

**Hierarchy:**
$$
\text{Hausdorff (T₂)} \implies \text{Fréchet (T₁)} \implies \text{Kolmogorov (T₀)}
$$

---

### 4. Properties of Hausdorff Spaces

**Định lý (Limits Unique):**  
Trong Hausdorff space, nếu sequence hội tụ, limit là **unique**.

**Chứng minh:**  
Giả sử xₙ → x và xₙ → y với x ≠ y.  
Hausdorff → ∃U ∋ x, V ∋ y disjoint.  
xₙ → x → ∃N₁: ∀n ≥ N₁: xₙ ∈ U.  
xₙ → y → ∃N₂: ∀n ≥ N₂: xₙ ∈ V.  
Cho n ≥ max{N₁, N₂}: xₙ ∈ U ∩ V = ∅. Mâu thuẫn! ∎

**Ý nghĩa:** Hausdorff condition đảm bảo uniqueness của limits—essential cho analysis!

**Định lý (Compact Subsets Closed):**  
Trong Hausdorff space, mọi compact subset là closed.

**Chứng minh:**  
Cho K ⊆ X compact, cần chứng minh X \ K open.  
Cho x ∈ X \ K. Với mọi y ∈ K:  
- Hausdorff → ∃Uᵧ ∋ x, Vᵧ ∋ y disjoint.  
{Vᵧ}ᵧ∈K open cover của K.  
K compact → ∃ finite subcover V_{y₁}, ..., V_{yₙ}.  
U = U_{y₁} ∩ ... ∩ U_{yₙ} neighborhood của x.  
U ∩ K = ∅ (vì U ∩ Vᵧᵢ = ∅).  
→ X \ K open. ✓

**Chú ý:** Điều này **sai** trong non-Hausdorff spaces!

**Định lý (Diagonal Closed):**  
X Hausdorff ⟺ Diagonal Δ = {(x,x) : x ∈ X} closed trong X × X.

**Chứng minh:** Exercise (sử dụng product topology).

---

### 5. Examples và Counterexamples

**Summary Table:**

| Space | T₀ | T₁ | T₂ (Hausdorff) |
|-------|----|----|----------------|
| Discrete | ✓ | ✓ | ✓ |
| Trivial (≥2 pts) | ✗ | ✗ | ✗ |
| Cofinite (infinite) | ✓ | ✓ | ✗ |
| Sierpiński {0,1} | ✓ | ✗ | ✗ |
| ℝⁿ (Euclidean) | ✓ | ✓ | ✓ |
| Metric spaces | ✓ | ✓ | ✓ |

**Pathological Example:**

**Zariski Topology trên ℂⁿ:**  
Closed sets = algebraic varieties (zero sets của polynomials).  
- T₀: ✓
- T₁: ✓ (points are varieties)
- T₂: ✗ (open sets "too large"—any two non-empty open sets intersect!)

**Importance:** Algebraic geometry uses non-Hausdorff topology!

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Định nghĩa Hausdorff spaces (original T₂ axiom)*

2. **Andrey Kolmogorov** - *"Zur Begründung der projektiven Geometrie"* (1932)  
   *T₀ axiom trong projective geometry*

3. **Maurice Fréchet** - *"Sur quelques points du calcul fonctionnel"* (1906)  
   *Early work liên quan đến T₁ condition*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§31–32: Separation Axioms**  
   *Clear systematic treatment*

5. **Stephen Willard** - *General Topology*, **Chapter 4**  
   *Comprehensive coverage*

6. **John L. Kelley** - *General Topology*, **Chapter 3**  
   *Advanced perspective*

7. **Ryszard Engelking** - *General Topology*, **Chapter 1**  
   *Encyclopedia-level detail*

---

## 🔗 Applications and Connections

### Analysis - Uniqueness of Limits
**Convergence:** Trong metric spaces (Hausdorff), limits unique. Foundation cho calculus, functional analysis.

### Algebraic Geometry - Non-Hausdorff Topology
**Zariski Topology:** Schemes trong algebraic geometry often non-Hausdorff. Generic points không có disjoint neighborhoods.

### Physics - Quantum Mechanics
**State Space:** Hilbert space với weak topology (not Hausdorff). Physical observables correspond to closed operators.

### Computer Science - Domain Theory
**Scott Topology:** Trên partially ordered sets, often T₀ but not T₁. Used trong semantics của programming languages.

---

## 🧩 Exercises

### T₀ Spaces

1. **Verify T₀:**  
   Các spaces sau có T₀ không?
   - a) {a,b,c} với τ = {∅, {a}, {a,b}, X}
   - b) ℕ với cofinite topology
   - c) {0,1} với τ = {∅, {0}, X}

2. **Sierpiński:**  
   Chứng minh Sierpiński space {0,1} với τ = {∅, {0}, X} là T₀ nhưng không T₁.

### T₁ Spaces

3. **Singleton Closed:**  
   Chứng minh: X là T₁ ⟺ mọi singleton closed.

4. **Cofinite T₁:**  
   Chứng minh cofinite topology trên infinite set là T₁.

5. **Finite T₁:**  
   Nếu X finite và T₁, chứng minh X có discrete topology.

### Hausdorff Spaces

6. **Metric Hausdorff:**  
   Chứng minh chi tiết: mọi metric space là Hausdorff.

7. **Limits Unique:**  
   Cho ví dụ non-Hausdorff space với sequence hội tụ đến nhiều limits.

8. **Compact Closed:**  
   Trong ℝ với cofinite topology:
   - a) [0,1] có compact không?
   - b) [0,1] có closed không?
   - c) Có vi phạm "compact → closed" không?

### Properties

9. **Product:**  
   Nếu X, Y Hausdorff, chứng minh X × Y Hausdorff.

10. **Subspace:**  
    Nếu X Hausdorff, A ⊆ X, chứng minh A (subspace topology) Hausdorff.

11. **Continuous Image:**  
    Cho f: X → Y continuous surjection, X Hausdorff.  
    Y có nhất thiết Hausdorff không? Counterexample?

### Advanced

12. **Diagonal:**  
    Chứng minh: X Hausdorff ⟺ Δ = {(x,x)} closed trong X × X.

13. **Completely Hausdorff:**  
    X là **completely Hausdorff** nếu với x ≠ y, ∃f: X → [0,1] continuous với f(x) = 0, f(y) = 1.  
    - Chứng minh: completely Hausdorff ⇒ Hausdorff
    - ℝ có completely Hausdorff không?

14. **Zariski Topology:**  
    Tìm hiểu Zariski topology trên ℂ.  
    Tại sao nó T₁ nhưng không T₂?

### Reflection

15. **Why Hausdorff?**  
    Liệt kê 5 lý do tại sao Hausdorff condition "standard" trong topology.

16. **Non-Hausdorff Examples:**  
    Tìm 3 ví dụ "natural" non-Hausdorff spaces trong toán học.

17. **Hierarchy:**  
    Tại sao T₂ ⇒ T₁ ⇒ T₀ nhưng không ngược lại?  
    Cho examples chứng minh implications không reverse.

---

## 📚 Further Reading

- **Munkres, Topology:** §31–32 (Separation Axioms)
- **Willard, General Topology:** Chapter 4 (Separation Axioms)
- **Engelking, General Topology:** Chapter 1.5 (Separation Properties)
- **Steen & Seebach:** *Counterexamples in Topology* (Encyclopedia của examples!)

---

## 🎓 Summary

Trong bài này, chúng ta học về **separation axioms**—hierarchy của conditions về "separability":

✅ **T₀ (Kolmogorov):** Topology distinguish hai điểm khác nhau  
✅ **T₁ (Fréchet):** Singletons closed ⟺ symmetric separation  
✅ **T₂ (Hausdorff):** Disjoint neighborhoods ⟺ complete separation  
✅ **Hierarchy:** T₂ ⇒ T₁ ⇒ T₀ (không reverse!)  
✅ **Hausdorff Properties:**
   - Limits unique
   - Compact subsets closed
   - Diagonal closed  

**Điểm chính:**
- Hausdorff = "standard" assumption (metric spaces, manifolds)
- Non-Hausdorff có ứng dụng (algebraic geometry, domain theory)
- T₁ ⟺ points closed
- Separation về "distinguishing" points topologically

**Practical wisdom:**
- Nếu working với metric spaces → automatically Hausdorff
- Check Hausdorff để ensure limits unique
- Non-Hausdorff spaces = special, careful reasoning needed!

**Tiếp theo:** Lecture 03.01 về **T₃ (Regular) và T₄ (Normal) Spaces**—stronger separation conditions, Urysohn's Lemma, Tietze Extension Theorem!

---

*"Hausdorff spaces are to topology what metric spaces are to geometry."* — Standard analogy

🎯 **Distinguish the distinctions! Understand the hierarchy T₀ ⊂ T₁ ⊂ T₂.** 🎯

---

**Previous Chapter:** [Chapter 02: Connectedness and Compactness](/contents/vi/topology-chapter02/)  
**Next:** [Lecture 03.01: Regular and Normal Spaces](/contents/vi/topology-chapter03/03_01_Regular_Normal_Spaces/)

