---
layout: post
title: "Lecture 01.03: Continuous Functions and Homeomorphisms"
lang: vi
lang-ref: lecture-01-03
chapter: 1
lecture: 3
categories: [chapter01]
tags: [continuous-functions, homeomorphisms, topological-equivalence]
description: "Hàm liên tục trong topology, các đặc trưng tương đương, và homeomorphisms"
---

**Continuous Functions and Homeomorphisms**

---

## 📖 Tổng quan

Chúng ta đã học cách định nghĩa **không gian tô-pô** (topological spaces). Bây giờ đến câu hỏi quan trọng: **Làm sao so sánh hai không gian?**

Trong đại số tuyến tính, chúng ta so sánh vector spaces qua **linear maps**.  
Trong lý thuyết nhóm, chúng ta so sánh groups qua **homomorphisms**.  
Trong topology, chúng ta so sánh spaces qua **continuous functions**!

Nhưng định nghĩa nào của "continuous"? Trong calculus, bạn học định nghĩa ε-δ. Nhưng định nghĩa đó **phụ thuộc vào metric**—không thể dùng cho general topological spaces!

**Khám phá vĩ đại:** Có một định nghĩa **thuần tô-pô** của continuity chỉ dùng open sets!

$$
f: X \to Y \text{ continuous} \iff \text{preimage của mọi open set là open}
$$

Định nghĩa này:
- Không cần metric
- Tương đương với ε-δ khi có metric
- Elegant và powerful
- Nền tảng của **toàn bộ** topology

**Trong bài này:**
- Định nghĩa continuity qua open sets
- Các đặc trưng tương đương (closed sets, closure, basis)
- **Homeomorphisms**: "isomorphisms" của topology
- Topological properties và invariants
- Ví dụ kinh điển: coffee cup ≅ doughnut

**Tại sao quan trọng?**
- Continuous functions = "morphisms" trong category của topological spaces
- Homeomorphism = topological equivalence
- Mọi topological property phải invariant under homeomorphisms
- Đây là ngôn ngữ để nói về "deformations" và "shapes"

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Rubber Sheet Geometry

Topology thường được gọi là **"rubber sheet geometry"** (hình học tấm cao su). Tưởng tượng shapes được làm từ cao su—bạn có thể:
- **Stretch** (kéo dài)
- **Bend** (uốn cong)
- **Twist** (vặn xoắn)

Nhưng KHÔNG được:
- **Tear** (xé rách)
- **Glue** (dán)
- **Cut** (cắt)

Nếu hai shapes có thể biến đổi từ cái này sang cái kia qua các phép "continuous deformation", chúng **topologically equivalent** (homeomorphic)!

![Mug to Torus](https://upload.wikimedia.org/wikipedia/commons/2/26/Mug_and_Torus_morph.gif)  
*Coffee mug ≅ Torus (homeomorphic) - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Mug_and_Torus_morph.gif)*

**Ví dụ kinh điển:**
- **Coffee mug ≅ Doughnut (torus)**: Cả hai có một "hole"
- **Sphere ≠ Torus**: Không thể biến sphere thành torus không cắt/dán
- **Line segment [0,1] ≅ [2,5]**: Chỉ khác "scale", cùng topology
- **[0,1] ≠ (0,1)**: Một có endpoints, một không—topologically khác nhau!

**Câu hỏi:** Làm sao formalize "continuous deformation"?  
**Trả lời:** Homeomorphisms—bijective continuous functions với continuous inverse!

---

## 📐 Định nghĩa Hình thức

### 1. Continuous Functions

**Định nghĩa (Continuity - Open Sets):**  
Cho (X, 𝜏_X) và (Y, 𝜏_Y) là topological spaces. Hàm f: X → Y là **continuous** nếu:

$$
\forall V \in \tau_Y: f^{-1}(V) \in \tau_X
$$

**Nói bằng lời:** Preimage (nghịch ảnh) của mọi open set trong Y là open trong X.

**Ký hiệu:** f⁻¹(V) = {x ∈ X : f(x) ∈ V} (preimage, không phải inverse!)

**Ví dụ 1: Identity map**

f: ℝ → ℝ, f(x) = x (Euclidean topology trên cả hai)

Với mọi open V ⊆ ℝ: f⁻¹(V) = V (open) ✓  
→ f continuous

**Ví dụ 2: Constant map**

f: X → Y, f(x) = y₀ với mọi x (y₀ ∈ Y fixed)

- f⁻¹(V) = X nếu y₀ ∈ V
- f⁻¹(V) = ∅ nếu y₀ ∉ V

Cả hai đều open → f continuous (luôn!)

**Ví dụ 3: Inclusion map**

A ⊆ X với subspace topology. i: A → X, i(a) = a

Với V ∈ 𝜏_X: i⁻¹(V) = V ∩ A ∈ 𝜏_A (theo định nghĩa subspace topology!) ✓

**Ví dụ 4: Projection maps**

π₁: X × Y → X, π₁(x,y) = x (product topology)

π₁ continuous! (Chứng minh: exercise với basis)

---

### 2. Equivalent Characterizations

**Định lý (Equivalent Definitions of Continuity):**  
Các phát biểu sau **tương đương**:

1. **f continuous** (định nghĩa)
2. **Preimage của closed sets là closed:**  
   ∀F ⊆ Y closed: f⁻¹(F) closed
3. **Closure condition:**  
   ∀A ⊆ X: f(cl_X(A)) ⊆ cl_Y(f(A))
4. **Interior condition:**  
   ∀B ⊆ Y: f⁻¹(int_Y(B)) ⊆ int_X(f⁻¹(B))
5. **Basis condition:**  
   Nếu ℬ là basis cho 𝜏_Y, thì ∀B ∈ ℬ: f⁻¹(B) ∈ 𝜏_X

**Chứng minh:**

**(1 ⇒ 2):**  
Cho F ⊆ Y closed. Khi đó Y \ F open.  
f⁻¹(Y \ F) = X \ f⁻¹(F) open (theo (1)).  
→ f⁻¹(F) closed ✓

**(2 ⇒ 1):**  
Cho V ⊆ Y open. Khi đó Y \ V closed.  
f⁻¹(Y \ V) = X \ f⁻¹(V) closed (theo (2)).  
→ f⁻¹(V) open ✓

**(1 ⇒ 3):**  
Cho A ⊆ X. Cần chứng minh: f(cl(A)) ⊆ cl(f(A)).  
Tương đương: cl(A) ⊆ f⁻¹(cl(f(A))).

f(A) ⊆ cl(f(A)) → A ⊆ f⁻¹(cl(f(A))).  
cl(f(A)) closed → f⁻¹(cl(f(A))) closed (theo (2)).  
→ cl(A) ⊆ f⁻¹(cl(f(A))) ✓

**(5):** Exercise (sử dụng: mọi open set là hợp của basis elements).

**Ứng dụng practical:**

**Basis condition (5)** rất hữu ích! Để check continuity:
- Không cần check **tất cả** open sets trong Y
- Chỉ cần check **basis elements**!

**Ví dụ:** f: ℝ → ℝ continuous ⟺ f⁻¹((a,b)) open với mọi (a,b).

---

### 3. Continuity at a Point

**Định nghĩa (Continuity at a Point):**  
f: X → Y continuous **tại x₀** nếu:

$$
\forall V \in \tau_Y, f(x_0) \in V: \exists U \in \tau_X, x_0 \in U: f(U) \subseteq V
$$

**Nói bằng lời:** Với mọi neighborhood V của f(x₀), tồn tại neighborhood U của x₀ sao cho f(U) ⊆ V.

**Định lý:**  
f continuous (trên toàn X) ⟺ f continuous tại mọi x ∈ X.

**Connection với ε-δ:**

Trong metric spaces (X,d_X), (Y,d_Y):

**Topology definition:** f continuous tại x₀ ⟺  
∀ε > 0: ∃δ > 0: d_X(x,x₀) < δ ⇒ d_Y(f(x),f(x₀)) < ε

**Đây chính là định nghĩa ε-δ từ calculus!**

**Kết luận:** Topological continuity **generalizes** ε-δ continuity.

---

### 4. Properties of Continuous Functions

**Định lý (Composition):**  
Nếu f: X → Y và g: Y → Z đều continuous, thì g ∘ f: X → Z continuous.

**Chứng minh:**  
Cho W ∈ 𝜏_Z open.  
(g ∘ f)⁻¹(W) = f⁻¹(g⁻¹(W)).  
g⁻¹(W) ∈ 𝜏_Y (g continuous).  
f⁻¹(g⁻¹(W)) ∈ 𝜏_X (f continuous). ∎

**Ý nghĩa:** Continuous functions form a **category**!

**Định lý (Restriction):**  
Nếu f: X → Y continuous và A ⊆ X (subspace topology), thì f|_A: A → Y continuous.

**Chứng minh:** Exercise.

**Định lý (Pasting Lemma):**  
Cho X = A ∪ B với A, B closed. Nếu f: A → Y và g: B → Y đều continuous và f|_{A∩B} = g|_{A∩B}, thì:

$$
h: X \to Y, \quad h(x) = \begin{cases} f(x) & x \in A \\ g(x) & x \in B \end{cases}
$$

continuous.

**Ứng dụng:** "Glue" các continuous functions lại!

---

### 5. Homeomorphisms

**Định nghĩa (Homeomorphism):**  
f: X → Y là **homeomorphism** nếu:
1. f **bijective** (1-1 và onto)
2. f **continuous**
3. f⁻¹: Y → X **continuous**

**Ký hiệu:** X ≅ Y (hoặc X ≃ Y) nếu tồn tại homeomorphism giữa chúng.

**Trực giác:** Homeomorphism = "topological isomorphism". X và Y có "same topology" (sau khi relabeling points).

![Homeomorphism examples](https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/Homeomorphism-cont-bis.svg/400px-Homeomorphism-cont-bis.svg.png)  
*Homeomorphism giữa intervals - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Homeomorphism-cont-bis.svg)*

**Ví dụ 1: Linear stretch**

f: [0,1] → [2,5], f(x) = 3x + 2

- Bijective ✓
- Continuous (linear!) ✓
- f⁻¹(y) = (y-2)/3 continuous ✓

→ [0,1] ≅ [2,5]

**Ví dụ 2: Open vs Closed interval**

**Claim:** [0,1] ≇ (0,1) (không homeomorphic!)

**Chứng minh (sketch):**  
Giả sử f: [0,1] → (0,1) homeomorphism.  
Xét g = f|_{(0,1)}: (0,1) → (0,1) \ {f(0), f(1)} homeomorphism.  
Nhưng remove 1 point từ (0,1) → disconnected.  
Remove 2 points từ [0,1] → still connected (middle part).  
Contradiction! ∎

**Ví dụ 3: Circle vs Line**

**S¹ ≇ ℝ:** Circle compact, ℝ not compact.

**Ví dụ 4: Stereographic Projection**

f: S² \ {north pole} → ℝ² là homeomorphism!

**Construction:** Project từ north pole xuống equatorial plane.

---

### 6. Topological Properties

**Định nghĩa (Topological Property):**  
Một property P là **topological property** (hoặc **topological invariant**) nếu:

$$
X \text{ has } P \land (X \cong Y) \implies Y \text{ has } P
$$

**Nói bằng lời:** Property được bảo toàn qua homeomorphisms.

**Ví dụ Topological Properties:**
- **Compactness**: X compact → f(X) compact
- **Connectedness**: X connected → f(X) connected
- **Hausdorff**: X Hausdorff → Y Hausdorff (nếu X ≅ Y)
- **Cardinality**: |X| = |Y| nếu X ≅ Y (bijection!)

**Ví dụ NON-Topological Properties:**
- **Boundedness** (trong metric sense): [0,1] bounded, nhưng [0,1] ≅ ℝ unbounded (sử dụng f(x) = tan(πx - π/2))
- **Metric completeness**: ℝ complete, (0,1) không complete, nhưng homeomorphic qua bijection

**Cách dùng:**  
Để chứng minh X ≇ Y, tìm một topological property mà X có nhưng Y không!

---

### 7. Embedding và Quotient Maps

**Định nghĩa (Embedding):**  
f: X → Y là **embedding** nếu f homeomorphism giữa X và f(X) (với subspace topology).

**Trực giác:** X "embeds" vào Y—có thể xem X như một subspace của Y.

**Ví dụ:**
- (0,1) ↪ ℝ: inclusion map là embedding
- S¹ ↪ ℝ²: circle embeds trong plane
- Graph(f) = {(x,f(x))} ↪ ℝ²: graph của continuous f embeds trong ℝ²

**Định nghĩa (Quotient Map - Preview):**  
p: X → Y là **quotient map** nếu:
1. p surjective
2. U ⊆ Y open ⟺ p⁻¹(U) open trong X

**Trực giác:** Y có topology "induced" từ X via p.

**Ví dụ:** [0,1] → S¹ bằng cách "glue" endpoints → quotient map.

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Intuitive foundation của continuous deformations*

2. **L.E.J. Brouwer** - *"Zur Analysis Situs"* (1910)  
   *Topological invariants, fixed point theorems*

3. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Formalization của continuous functions*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§18–19: Continuous Functions**  
   *Clear exposition*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 5**  
   *Nhiều examples*

6. **M.A. Armstrong** - *Basic Topology*, **Chapter 2**  
   *Geometric intuition*

7. **Allen Hatcher** - *Algebraic Topology*, **§0**  
   *Homotopy perspective*

---

## 🔗 Applications and Connections

### Computer Graphics - Morphing
**Animation:** Morphing giữa hai shapes = continuous deformation. Homeomorphisms guarantee topology preserved (số holes không đổi).

### Physics - Phase Transitions
**Thermodynamics:** Phase space topology changes tại critical points. Continuity của physical quantities = continuous maps between phase spaces.

### Data Science - Manifold Learning
**Dimensionality Reduction:** t-SNE, UMAP cố gắng preserve topological structure (neighborhoods) khi project high-dim data → low-dim. Ideally homeomorphic embeddings!

### Neuroscience - Brain Mapping
**Cortical Surface:** Brain surface topologically sphere (with handles). Flattening for visualization = continuous map (not homeomorphism—distortion unavoidable!).

### Real-World Example
**Subway Maps:** Topologically correct (connections preserved) nhưng không preserve metric (distances distorted). Continuous deformation of actual geography!

---

## Video tham khảo

- **xem trước** [Ánh xạ liên tục và phép đồng phôi](https://www.youtube.com/watch?v=rEZoSe0HjOs) — Cuong Nguyen, tiếng Việt. Liên tục rồi đồng phôi, đúng hai tầng của bài, nói bằng tiếng Việt.
- [[Tôpô đại cương] Bài 22. Ánh xạ liên tục: định nghĩa và Ví dụ](https://www.youtube.com/watch?v=cU8HZcRSpFM) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Định nghĩa ánh xạ liên tục qua nghịch ảnh tập mở, kèm ví dụ.
- [Basic Topology 19 | Homeomorphic Spaces](https://www.youtube.com/watch?v=1FFwuZbzbjE) — The Bright Side of Mathematics, tiếng Anh. Khi nào một song ánh liên tục thực sự là đồng phôi, và vì sao hai không gian khi đó là một.

## 🧩 Exercises

### Continuity

1. **Verify Continuous:**  
   Cho f: ℝ → ℝ. Kiểm tra continuity (topology sense):
   - a) f(x) = 2x + 3
   - b) f(x) = x²
   - c) f(x) = ⌊x⌋ (floor function)

2. **Constant Map:**  
   Chứng minh: Mọi constant map f: X → Y continuous (với topologies bất kỳ).

3. **Discrete to Any:**  
   Cho X có discrete topology, Y bất kỳ.  
   Chứng minh: Mọi f: X → Y continuous.

4. **Trivial from Any:**  
   Cho Y có trivial topology, X bất kỳ.  
   Chứng minh: Mọi f: X → Y continuous.

5. **Composition:**  
   f: X → Y, g: Y → Z continuous.  
   Chứng minh g ∘ f continuous bằng định nghĩa (preimage của open sets).

### Characterizations

6. **Closed Sets:**  
   Chứng minh: f continuous ⟺ preimage của mọi closed set là closed.

7. **Basis Check:**  
   f: ℝ → ℝ, f(x) = x² (Euclidean topology).  
   Sử dụng basis ℬ = {(a,b)} để check continuity.  
   f⁻¹((a,b)) có dạng gì?

8. **Closure Condition:**  
   Cho f: X → Y continuous, A ⊆ X.  
   Chứng minh: f(cl(A)) ⊆ cl(f(A)).  
   Có thể strict inequality không? Cho ví dụ.

### Homeomorphisms

9. **Verify Homeomorphism:**  
   f: (0,1) → ℝ, f(x) = tan(π(x - 1/2)).  
   - a) Chứng minh f bijective
   - b) Chứng minh f continuous
   - c) Chứng minh f⁻¹ continuous
   - d) Kết luận: (0,1) ≅ ℝ

10. **Not Homeomorphic:**  
    Chứng minh [0,1] ≇ (0,1) bằng cách:
    - a) Remove một điểm từ (0,1) → disconnected
    - b) Remove một điểm từ [0,1] → still connected (nếu không phải endpoint)
    - c) Connectedness là topological property

11. **Circle Examples:**  
    - a) Chứng minh: S¹ (circle) ≇ ℝ (line)
    - b) Chứng minh: S¹ compact, ℝ không
    - c) Compactness là topological property

### Topological Properties

12. **Cardinality:**  
    Nếu X ≅ Y, thì |X| = |Y|. Tại sao?  
    Ngược lại có đúng không? (|X| = |Y| ⇒ X ≅ Y?)

13. **Finite Spaces:**  
    Có bao nhiêu topological spaces (up to homeomorphism) trên tập 2 phần tử?  
    3 phần tử?

14. **Invariant Hunt:**  
    Liệt kê 5 topological properties (sẽ học sau):
    - Compactness
    - Connectedness
    - Hausdorff
    - Second countable
    - ...

### Advanced

15. **Stereographic Projection:**  
    f: S² \ {N} → ℝ² (project từ north pole).  
    Formula:
    $$
    f(x,y,z) = \left(\frac{x}{1-z}, \frac{y}{1-z}\right)
    $$
    Chứng minh f homeomorphism.

16. **Topologist's Sine Curve:**  
    A = {(x, sin(1/x)) : 0 < x ≤ 1} ∪ {(0,0)} trong ℝ².  
    - A có connected không?
    - Closure cl(A) có connected không?
    - A có homeomorphic với [0,1] không?

17. **Knot Theory Preview:**  
    Có thể embed S¹ vào ℝ³ theo vô số cách (knots).  
    Các embeddings khác nhau có homeomorphic không?  
    (Như subspaces của ℝ³)

18. **Homeomorphism Group:**  
    Cho X fixed. Họ tất cả homeomorphisms f: X → X tạo thành group (với composition)?  
    Chứng minh group axioms.

### Reflection

19. **Why Bijective + Continuous Not Enough:**  
    f: [0,2π) → S¹, f(t) = (cos t, sin t) bijective và continuous.  
    Tại sao f **không phải** homeomorphism?

20. **Topology vs Geometry:**  
    So sánh:
    - Topology: study properties preserved by homeomorphisms
    - Geometry: study properties preserved by isometries
    
    Geometric property nào **không** là topological?

---

## 📚 Further Reading

- **Munkres, Topology:** §18–22 (Continuous Functions, Homeomorphisms, Quotient Topology)
- **Armstrong, Basic Topology:** Chapter 2–3 (Continuity and Homeomorphisms)
- **Hatcher, Algebraic Topology:** §0 (Homotopy and Cell Complexes)
- **Morris, Topology Without Tears:** Chapter 5–6

---

## 🎓 Summary

Trong bài này, chúng ta học về **morphisms** trong category của topological spaces:

✅ **Continuous Functions:** f continuous ⟺ f⁻¹(open) = open  
✅ **Equivalent Characterizations:** Via closed sets, closure, basis  
✅ **Continuity at a Point:** Local version, generalizes ε-δ  
✅ **Composition:** Continuous ∘ continuous = continuous  
✅ **Homeomorphisms:** Bijective + continuous + continuous inverse  
✅ **Topological Properties:** Invariants under homeomorphisms  
✅ **Rubber Sheet Geometry:** Stretch, bend, twist—no tear or glue  

**Điểm chính:**
- Topological continuity **generalizes** metric continuity (ε-δ)
- Homeomorphism = "same topology" = rubber-sheet deformation
- Topological properties: compactness, connectedness, etc.
- Để prove X ≇ Y: tìm topological property khác nhau
- Coffee mug ≅ doughnut: cùng số holes!

**Philosophical insight:**  
Topology study **qualitative** properties (shape, connectivity) không phụ thuộc **quantitative** measures (distance, angle). This is powerful abstraction!

**Tiếp theo:** Trong Lecture 01.04, chúng ta sẽ học về **Subspace Topology và Product Topology**—hai cách quan trọng nhất để xây dựng topological spaces mới từ spaces cũ.

---

*"A topologist cannot distinguish a coffee mug from a doughnut."* — Popular joke

🎯 **Practice identifying homeomorphisms! Đây là core skill của topology.** 🎯

---

**Previous:** [Lecture 01.02: Closed Sets, Closure, Interior](/contents/vi/topology-chapter01/01_02_Closed_Sets_Closure_Interior/)  
**Next:** [Lecture 01.04: Subspace and Product Topology](/contents/vi/topology-chapter01/01_04_Subspace_Product_Topology/)

