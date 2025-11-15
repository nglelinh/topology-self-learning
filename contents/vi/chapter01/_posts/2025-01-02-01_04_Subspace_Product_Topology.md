---
layout: post
title: "Lecture 01.04: Subspace and Product Topology"
lang: vi
lang-ref: lecture-01-04
chapter: 1
lecture: 4
categories: [chapter01]
tags: [subspace-topology, product-topology, projections, tychonoff]
description: "Subspace topology, product topology, và Tychonoff's theorem (statement)"
---

**Subspace and Product Topology**

---

## 📖 Tổng quan

Trong toán học, một pattern mạnh mẽ là: xây dựng objects phức tạp từ objects đơn giản. Topology không ngoại lệ!

Hai constructions quan trọng nhất:
1. **Subspace topology**: Lấy một "piece" của space
2. **Product topology**: "Nhân" hai spaces lại với nhau

**Ví dụ trực quan:** **Subspace** topology appears when circle S¹ sits naturally inside plane ℝ² inheriting topology. **Product** constructions build complexity: plane ℝ² emerges as ℝ × ℝ (line times line), torus T² as S¹ × S¹ (circle times circle), cylinder as S¹ × [0,1] (circle times interval).

These constructions không phải mere "technical definitions"—they're deeply **natural** và pervade mathematics. Surfaces embedded trong ℝ³ carry subspace topology making them topological spaces. Spacetime trong relativity is ℝ × ℝ³ (time dimension times 3D space). Configuration spaces trong physics and robotics are product spaces tracking multiple parameters simultaneously. Function spaces reveal themselves as infinite products, enabling functional analysis.

**Trong bài này** we systematically develop two fundamental constructions. **Subspace topology** defines induced topology on subsets—most natural way to make subset inherit topological structure. **Product topology** on X × Y emerges as weakest topology making projections continuous. **Basis for product** consists of "open rectangles" U × V, providing intuitive geometric picture. **Projections** π₁, π₂ satisfy beautiful universal property characterizing product categorically. **Infinite products** ∏ᵢXᵢ extend construction, với Tychonoff's theorem as crown jewel. **Box topology** appears as alternative (stronger, but pathological—not standard).

**Tại sao absolutely fundamental?** Mọi smooth manifold is **locally homeomorphic to products** (ℝⁿ), making product topology essential for differential geometry. Many **surfaces emerge as quotients** of products (torus from square, Klein bottle from rectangle). **Tychonoff's Theorem**—arbitrary product của compact spaces is compact—is one of most important results trong topology, equivalent to Axiom of Choice! **Universal properties** provide category-theoretic perspective revealing deeper structure, connecting topology với abstract algebra and functional analysis.

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Inheritance

**Subspace topology** giống như **inheritance** trong biology:

Con mèo **kế thừa** DNA từ cha mẹ. Tương tự, khi A ⊆ X, ta muốn A "kế thừa" topology từ X.

**Ví dụ:** [0,1] ⊂ ℝ

Trong ℝ, (0, 0.5) là open. Trong [0,1], ta muốn (0, 0.5) vẫn "open".  
Nhưng (0, 0.5) không phải khoảng mở trong ℝ (chỉ là một phần).  
Solution: (0, 0.5) = (−∞, 0.5) ∩ [0,1] → "open trong [0,1]"!

**Nguyên tắc chung:**  
> **U open trong A ⟺ U = V ∩ A với V open trong X**

![Subspace topology illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Subspace_topology.svg/400px-Subspace_topology.svg.png)  
*Subspace topology: U open trong A khi U = V ∩ A - Nguồn concept*

---

### Câu chuyện về Coordinates

**Product topology** giống như **coordinate systems**:

Trong ℝ², mỗi điểm có **hai tọa độ** (x, y). Topology trên ℝ² phải "respect" topology trên mỗi coordinate axis!

**Ví dụ:** Open rectangle (a,b) × (c,d) trong ℝ²

- Projection lên x-axis: (a,b) — open trong ℝ
- Projection lên y-axis: (c,d) — open trong ℝ
- Product: (a,b) × (c,d) — open trong ℝ²

**Nguyên tắc:** Product topology là **smallest** topology làm cho projections continuous!

![Product topology visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Cartesian-coordinate-system.svg/400px-Cartesian-coordinate-system.svg.png)  
*Product space với coordinate projections - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cartesian-coordinate-system.svg)*

---

## 📐 Định nghĩa Hình thức

### 1. Subspace Topology

**Định nghĩa (Subspace Topology):**  
Cho (X, 𝜏) topological space và A ⊆ X. **Subspace topology** trên A là:

$$
\tau_A = \{U \cap A : U \in \tau\}
$$

**Nói bằng lời:** Open sets trong A = intersections của open sets trong X với A.

**Ký hiệu:** (A, 𝜏_A) gọi là **subspace** của X.

**Ví dụ 1: Interval trong ℝ**

A = [0, 2] ⊂ ℝ (Euclidean topology)

Open sets trong A:
- [0, 1) = (−1, 1) ∩ [0,2]
- (1, 2] = (1, 3) ∩ [0,2]
- (0.5, 1.5) = (0.5, 1.5) ∩ [0,2]
- [0, 2] = ℝ ∩ [0,2]
- ∅ = ∅ ∩ [0,2]

**Chú ý:** [0, 1) open trong [0,2] nhưng **không** open trong ℝ!

**Ví dụ 2: Circle trong ℝ²**

S¹ = {(x,y) : x² + y² = 1} ⊂ ℝ²

"Open arc" trong S¹ = intersection của open disk với S¹.

**Định lý (Subspace is Topology):**  
𝜏_A thỏa mãn ba topology axioms.

**Chứng minh:**

**(T1):** ∅ = ∅ ∩ A ∈ 𝜏_A, A = X ∩ A ∈ 𝜏_A ✓

**(T2) Unions:**  
{Uα ∩ A} với Uα ∈ 𝜏.  
⋃(Uα ∩ A) = (⋃Uα) ∩ A ∈ 𝜏_A ✓

**(T3) Finite intersections:**  
(U₁ ∩ A) ∩ (U₂ ∩ A) = (U₁ ∩ U₂) ∩ A ∈ 𝜏_A ✓

**Định lý (Inclusion Continuous):**  
Inclusion map i: A → X, i(a) = a **always continuous**.

**Chứng minh:**  
Cho U ∈ 𝜏. i⁻¹(U) = U ∩ A ∈ 𝜏_A (by definition!) ✓

---

### 2. Basis for Subspace

**Định lý:**  
Nếu ℬ là basis cho 𝜏 trên X, thì:

$$
\mathcal{B}_A = \{B \cap A : B \in \mathcal{B}\}
$$

là basis cho 𝜏_A trên A.

**Ứng dụng:** Để mô tả subspace topology, chỉ cần basis của ambient space!

**Ví dụ:**  
Basis cho ℝ: {(a,b)}  
Basis cho [0,1]: {(a,b) ∩ [0,1]} = các khoảng mở trong [0,1]

---

### 3. Properties of Subspaces

**Định lý (Relative Closure):**  
Cho A ⊆ X, B ⊆ A. Closure của B trong A:

$$
\text{cl}_A(B) = \text{cl}_X(B) \cap A
$$

**Chứng minh:** Exercise (sử dụng definition của closure).

**Định lý (Subspace của Subspace):**  
Nếu A ⊆ B ⊆ X, thì subspace topology trên A từ B **bằng** subspace topology trên A từ X.

**Trực giác:** Không quan trọng "intermediate space"—chỉ quan trọng ambient space.

---

### 4. Product Topology (Finite)

**Định nghĩa (Product Topology - 2 spaces):**  
Cho (X, 𝜏_X) và (Y, 𝜏_Y). Trên X × Y, **product topology** là topology sinh bởi basis:

$$
\mathcal{B} = \{U \times V : U \in \tau_X, V \in \tau_Y\}
$$

**Nói bằng lời:** Basis elements = "open rectangles" U × V.

**Ký hiệu:** (X × Y, 𝜏_X×Y) gọi là product space.

**Ví dụ 1: ℝ × ℝ = ℝ²**

Basis: {(a,b) × (c,d)} = open rectangles

Open sets: arbitrary unions của rectangles (mọi open set trong ℝ²!)

**Ví dụ 2: S¹ × [0,1] = Cylinder**

Basis: {open arc × open interval}

![Cylinder as product](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Cylinder_geometry.svg/300px-Cylinder_geometry.svg.png)  
*Cylinder = S¹ × [0,1] - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cylinder_geometry.svg)*

**Ví dụ 3: S¹ × S¹ = Torus**

Basis: {open arc₁ × open arc₂}

![Torus as product](https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Torus.png/300px-Torus.png)  
*Torus = S¹ × S¹ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus.png)*

**Định lý (Product is Topology):**  
𝜏_X×Y thỏa mãn topology axioms.

**Chứng minh:**  
ℬ = {U × V} thỏa mãn basis criterion:
- (B1): X × Y = X × Y ∈ ℬ ✓
- (B2): (U₁ × V₁) ∩ (U₂ × V₂) = (U₁ ∩ U₂) × (V₁ ∩ V₂) ∈ ℬ ✓

---

### 5. Projections

**Định nghĩa (Projection Maps):**

$$
\pi_X: X \times Y \to X, \quad \pi_X(x,y) = x
$$
$$
\pi_Y: X \times Y \to Y, \quad \pi_Y(x,y) = y
$$

**Định lý (Projections Continuous):**  
π_X và π_Y **luôn continuous** trong product topology.

**Chứng minh:**  
Cho U ∈ 𝜏_X open.  
π_X⁻¹(U) = U × Y = U × Y (basis element!) ∈ 𝜏_X×Y ✓

**Universal Property (Characterization):**  
Product topology là **coarsest** topology trên X × Y làm cho π_X, π_Y continuous.

**Nói bằng lời:** Đây là topology **nhỏ nhất** với projections continuous.

**Định lý (Product Continuity):**  
f: Z → X × Y continuous ⟺ π_X ∘ f và π_Y ∘ f continuous.

**Chứng minh (⇐):**  
Đủ check trên basis. Cho U × V basis element.  
f⁻¹(U × V) = f⁻¹(π_X⁻¹(U) ∩ π_Y⁻¹(V))  
          = (π_X ∘ f)⁻¹(U) ∩ (π_Y ∘ f)⁻¹(V) ∈ 𝜏_Z ✓

**Ứng dụng:** Để check f: Z → X × Y continuous, chỉ cần check coordinates!

---

### 6. Finite Products

**Định lý (Associativity):**  
(X × Y) × Z ≅ X × (Y × Z) ≅ X × Y × Z

**Trực giác:** Products "associate" naturally.

**Định nghĩa (n-fold Product):**  
$$
X_1 \times X_2 \times \cdots \times X_n
$$

Basis: $B_1 \times B_2 \times \cdots \times B_n$ với $B_i$ basis element trong $X_i$.

**Ví dụ:** ℝⁿ = ℝ × ℝ × ··· × ℝ (n lần)

Basis: Open rectangles (a₁,b₁) × ··· × (aₙ,bₙ)

---

### 7. Infinite Products

**Vấn đề:** Làm sao định nghĩa ∏ᵢ∈I Xᵢ với I **infinite**?

**Attempt 1 (Naïve - Box Topology):**  
Basis = {∏ᵢ Uᵢ : Uᵢ open trong Xᵢ}

**Vấn đề:** Projections **không continuous** nếu I infinite! Box topology "too fine".

**Solution (Product Topology):**  
Basis = {∏ᵢ Uᵢ : Uᵢ open, Uᵢ = Xᵢ **trừ hữu hạn** indices}

**Nói bằng lời:** Chỉ "finitely many coordinates" non-trivial.

**Định nghĩa (Infinite Product Topology):**

$$
\mathcal{B} = \left\{\prod_{i \in I} U_i : U_i \in \tau_i, U_i = X_i \text{ for all but finitely many } i\right\}
$$

**Ví dụ:**  
ℝ^∞ = ℝ × ℝ × ℝ × ···

Basis element: (a₁,b₁) × ··· × (aₙ,bₙ) × ℝ × ℝ × ···

**Định lý (Projections Continuous):**  
Mọi projection πᵢ: ∏ⱼXⱼ → Xᵢ continuous trong product topology.

**Universal Property:**  
Product topology là **coarsest** làm cho **all projections** continuous.

---

### 8. Tychonoff's Theorem

**Định lý Tychonoff (Tychonoff's Theorem):**

> **Tích tùy ý các không gian compact là compact** (trong product topology).

$$
\forall i \in I: X_i \text{ compact} \implies \prod_{i \in I} X_i \text{ compact}
$$

**Đây là một trong những định lý quan trọng nhất trong topology!**

**Ý nghĩa:**
- Compactness **bảo toàn** qua products (ngay cả infinite!)
- Chứng minh **cần Axiom of Choice**
- Thực tế, Tychonoff ⟺ AC (tương đương!)

**Ví dụ:**  
[0,1] compact → [0,1]^ℕ = {sequences in [0,1]} compact.

**Ứng dụng:**
- Banach-Alaoglu theorem (functional analysis)
- Compactness của function spaces
- Existence proofs trong analysis

**Chứng minh:**  
Requires ultrafilter lemma hoặc Alexander subbase theorem. (Advanced!)

**Chú ý quan trọng:**  
Trong **box topology**, Tychonoff **sai**! [0,1]^ℕ with box topology **not compact**.

→ Product topology là "right" choice!

---

### 9. Examples và Non-Examples

**Example 1: Hilbert Cube**

$$
H = [0,1]^\mathbb{N} = \prod_{n=1}^\infty [0,1]
$$

- Compact (Tychonoff!)
- Metrizable
- Universal space: mọi separable metric space embeds vào H

**Example 2: Cantor Space**

$$
\mathcal{C} = \{0,1\}^\mathbb{N}
$$

- Totally disconnected
- Perfect (every point là limit point)
- Homeomorphic với Cantor set trong ℝ

**Example 3: Function Spaces**

$$
\mathbb{R}^X = \{f: X \to \mathbb{R}\}
$$

Product topology = **pointwise convergence** topology.

fₙ → f ⟺ fₙ(x) → f(x) với mọi x (pointwise).

**Non-Example: ℝ^ℕ trong Box Topology**

Box basis: ∏ᵢ (aᵢ, bᵢ) (all coordinates non-trivial)

Projections continuous, **but not compact**! Tychonoff fails.

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Andrey Tychonoff** - *"Über die topologische Erweiterung von Räumen"* (1930)  
   *Proof của Tychonoff's theorem*

2. **Marshall Stone** - *"Applications of Boolean Rings to Topology"* (1937)  
   *Stone-Čech compactification, uses Tychonoff*

3. **John Kelley** - *"The Tychonoff Product Theorem Implies the Axiom of Choice"* (1950)  
   *Tychonoff ⟺ AC*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§16–19, §37**  
   *Standard reference*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 7–8**  
   *Accessible treatment*

6. **Stephen Willard** - *General Topology*, **Chapter 8**  
   *Comprehensive*

7. **John L. Kelley** - *General Topology*, **Chapter 5**  
   *Advanced, filters approach*

---

## 🔗 Applications and Connections

### Physics - Configuration Spaces
**Classical Mechanics:** Configuration space của n particles trong ℝ³ = (ℝ³)ⁿ = product space. Topology determines possible motions.

### Functional Analysis - Weak Topologies
**Banach Spaces:** Weak-* topology là product topology induced từ evaluations. Tychonoff → Banach-Alaoglu theorem.

### Probability - Product Measures
**Infinite Coin Flips:** {H,T}^ℕ với product topology. Measure theory: product measure (Kolmogorov extension).

### Computer Science - Type Theory
**Product Types:** A × B trong programming languages. Projections = fst, snd. Product topology analogy trong domain theory.

### Real-World Example
**Video Streams:** Sequence của frames = ∏ₜ Frame_t (infinite product). Continuity in product topology = "smooth" video playback.

---

## 🧩 Exercises

### Subspace Topology

1. **Compute Subspace:**  
   X = ℝ, A = [0,1]. Liệt kê các open sets trong A:
   - a) (0, 0.5)
   - b) [0, 0.5)
   - c) {0.25}

2. **Relative Open:**  
   Trong ℝ, A = [0,2].  
   - a) [0,1) có open trong A không?
   - b) (0,1) có open trong A không?
   - c) (0,1) có open trong ℝ không?

3. **Circle Subspace:**  
   S¹ ⊂ ℝ² (subspace topology).  
   "Open arc" U ⊂ S¹ có dạng gì?  
   Vẽ hình minh họa.

### Product Topology

4. **Basis Elements:**  
   Trong ℝ × ℝ = ℝ², các tập sau có phải basis elements không?
   - a) (0,1) × (0,1)
   - b) Open disk B((0,0), 1)
   - c) {(x,y) : x² + y² < 1}

5. **Open in Product:**  
   Open disk trong ℝ² có open trong product topology không?  
   (*Hint:* Viết như union của rectangles)

6. **Product Continuity:**  
   f: ℝ → ℝ², f(t) = (cos t, sin t).  
   Chứng minh f continuous bằng cách check coordinates.

### Projections

7. **Projection Maps:**  
   π₁: ℝ² → ℝ, π₁(x,y) = x.  
   - a) Chứng minh π₁ continuous
   - b) π₁ có open map không? (image của open set là open?)
   - c) π₁ có closed map không?

8. **Universal Property:**  
   f: Z → X × Y continuous ⟺ π_X ∘ f, π_Y ∘ f continuous.  
   Áp dụng: g: ℝ → ℝ², g(t) = (t², t³) continuous?

### Infinite Products

9. **Hilbert Cube:**  
   H = [0,1]^ℕ.  
   - a) Mô tả một basis element
   - b) H có compact không? (Tychonoff!)
   - c) H có countable basis không?

10. **Cantor Space:**  
    C = {0,1}^ℕ (product topology).  
    - a) |C| = ? (cardinality)
    - b) C có compact không?
    - c) C có connected không?

11. **Box vs Product:**  
    ℝ^ℕ với box topology vs product topology.  
    - a) Basis element trong box topology?
    - b) Basis element trong product topology?
    - c) Topology nào finer?

### Advanced

12. **Cylinder và Möbius Strip:**  
    - Cylinder = S¹ × [0,1]
    - Möbius strip ≠ S¹ × [0,1] (quotient!)
    
    Giải thích sự khác biệt topology.

13. **Torus:**  
    T² = S¹ × S¹.  
    - a) Vẽ hình minh họa
    - b) T² có homeomorphic với sphere S² không?
    - c) Tính Euler characteristic (preview!)

14. **Function Space:**  
    ℝ^ℝ với product topology.  
    fₙ → f có nghĩa gì? (pointwise convergence)  
    So sánh với uniform convergence.

15. **Tychonoff Application:**  
    Chứng minh: [0,1]^{[0,1]} (tất cả functions [0,1] → [0,1]) compact.  
    (*Hint:* Tychonoff + [0,1] compact)

### Reflection

16. **Why Product Topology?**  
    Tại sao product topology "better" than box topology?  
    Liệt kê reasons (projections, Tychonoff, etc.)

17. **Subspace vs Product:**  
    So sánh:
    - Subspace: "restrict" to subset
    - Product: "multiply" spaces
    
    Có construction "dual" không? (Quotient!)

18. **Categorical Perspective:**  
    Product topology satisfies universal property.  
    Tìm hiểu: product trong category theory.

---

## 📚 Further Reading

- **Munkres, Topology:** §16 (Subspace), §19 (Product), §37 (Tychonoff)
- **Morris, Topology Without Tears:** Chapters 7–8
- **Willard, General Topology:** Chapters 8–9
- **Bourbaki, General Topology:** Chapter I (Products)

---

## 🎓 Summary

Trong bài này, chúng ta học hai **constructions** quan trọng nhất:

✅ **Subspace Topology:** 𝜏_A = {U ∩ A : U ∈ 𝜏}  
✅ **Inclusion Continuous:** i: A ↪ X always continuous  
✅ **Product Topology (Finite):** Basis = {U × V}  
✅ **Projections Continuous:** π_X, π_Y continuous  
✅ **Universal Property:** Coarsest topology với projections continuous  
✅ **Infinite Products:** Basis elements có finitely many non-trivial coordinates  
✅ **Tychonoff's Theorem:** ∏ Xᵢ compact nếu mỗi Xᵢ compact  

**Điểm chính:**
- Subspace = "inheritance" của topology
- Product = "coordinate" structure
- Product topology ≠ box topology (infinite case!)
- Tychonoff cần Axiom of Choice
- Universal properties characterize constructions

**Ứng dụng:**
- ℝⁿ = product của n copies của ℝ
- Torus = S¹ × S¹
- Cylinder = S¹ × [0,1]
- Function spaces = infinite products

**Tiếp theo:** Chúng ta đã hoàn thành Chapter 01! Chapter 02 sẽ học về **Connectedness và Compactness**—hai tính chất tô-pô quan trọng nhất, foundation cho toàn bộ topology.

---

*"The product topology is the topology of coordinatewise convergence."* — Standard wisdom

🎯 **Visualize products! Vẽ cylinders, tori, và higher-dimensional products.** 🎯

---

**Previous:** [Lecture 01.03: Continuous Functions](/contents/vi/topology-chapter01/01_03_Continuous_Functions_Homeomorphisms/)  
**Next Chapter:** [Chapter 02: Connectedness and Compactness](/contents/vi/topology-chapter02/)

