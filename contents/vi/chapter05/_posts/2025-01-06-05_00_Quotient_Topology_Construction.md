---
layout: post
title: "Lecture 05.00: Quotient Topology and Construction"
lang: vi
lang-ref: lecture-05-00
chapter: 5
lecture: 0
categories: [chapter05]
tags: [quotient-topology, equivalence-relations, quotient-map, identification]
description: "Quotient topology: định nghĩa, construction, equivalence relations, và quotient maps"
---

**Quotient Topology and Construction**

---

## 📖 Tổng quan

Đến giờ chúng ta đã học nhiều cách xây dựng các không gian tô-pô: không gian con, tích, và metric topology. Giờ đây, chúng ta sẽ học một trong những cách mạnh mẽ nhất: **quotient topology**—cách "dán các điểm lại với nhau" hay "đồng nhất các điểm". Đây là một công cụ cơ bản cho phép chúng ta tạo ra các không gian mới từ các không gian đã biết bằng cách xác định các điểm nào đó là "giống nhau".

Các không gian quotient cho phép chúng ta làm nhiều điều đẹp đẽ và quan trọng. Chúng ta có thể dán các cạnh của các hình lại với nhau để tạo ra các bề mặt phức tạp như torus, Klein bottle, và không gian projective. Chúng ta có thể "co lại" các tập con thành các điểm—một kỹ thuật quan trọng trong nhiều ứng dụng. Chúng ta có thể mô hình hóa các phép đồng nhất như số học modular ($\mathbb{Z}/n\mathbb{Z}$). Và quan trọng nhất, chúng ta có thể nghiên cứu các bề mặt và manifolds—những đối tượng cơ bản trong hình học và tô-pô học.

![Quotient space visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Quotient_group_diagram.svg/400px-Quotient_group_diagram.svg.png)  
*Khái niệm về quotient construction - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Quotient_group_diagram.svg)*

Trực giác đằng sau quotient topology là đơn giản nhưng sâu sắc: bắt đầu với một không gian $X$. Xác định hoặc dán một số điểm lại với nhau theo một quan hệ tương đương. Kết quả là không gian quotient $X/\sim$. Điều này cho phép chúng ta "gấp" hoặc "dán" không gian theo những cách cụ thể để tạo ra các hình dạng mới.

Các ví dụ quan trọng bao gồm hình tròn $S^1 = [0,1]$ với $0 \sim 1$ (dán hai đầu mút lại với nhau), torus được tạo ra từ một hình vuông bằng cách dán các cạnh đối diện lại với nhau, không gian projective $\mathbb{R}P^n = S^n$ với các điểm đối cực được đồng nhất, và các bề mặt như cylinder và Möbius strip.

Trong bài học này, chúng ta sẽ khám phá các khái niệm cơ bản của quotient topology. Chúng ta bắt đầu với các quan hệ tương đương—nền tảng cho việc xây dựng quotient spaces. Chúng ta sẽ định nghĩa quotient topology thông qua universal property—một cách tiếp cận mạnh mẽ cho thấy quotient topology là "tốt nhất có thể" theo một nghĩa nhất định. Chúng ta sẽ nghiên cứu các quotient maps—các ánh xạ liên tục toàn ánh tạo ra quotient topology. Chúng ta sẽ xem xét các ví dụ quan trọng như hình tròn, torus, và không gian projective. Cuối cùng, chúng ta sẽ khám phá các tính chất của quotient spaces—khi nào chúng có các tính chất tốt như Hausdorff, và khi nào các quotient maps là open hoặc closed.

Tại sao quotient topology lại quan trọng đến vậy? Thứ nhất, trong lý thuyết bề mặt, định lý phân loại sử dụng quotient construction để phân loại tất cả các bề mặt compact. Thứ hai, trong hình học vi phân, các manifolds được định nghĩa thông qua các charts và atlases, và nhiều manifolds quan trọng được xây dựng như các quotient spaces. Thứ ba, trong tô-pô học đại số, các CW complexes được xây dựng bằng cách dán các cells lại với nhau—một quá trình quotient. Cuối cùng, trong vật lý, các phase spaces và gauge theory sử dụng quotient spaces để mô hình hóa các đối xứng và các không gian cấu hình.

---

## 🔗 Equivalence Relations

### 1. Basics

**Định nghĩa (Equivalence Relation):**  
Relation ~ trên X là **equivalence relation** nếu:

**(ER1) Reflexive:** x ~ x ∀x

**(ER2) Symmetric:** x ~ y ⇒ y ~ x

**(ER3) Transitive:** x ~ y, y ~ z ⇒ x ~ z

**Trực giác:** ~ captures "sameness" in some sense.

---

**Định nghĩa (Equivalence Class):**  
**Equivalence class** của x:

$$
[x] = \{y \in X : y \sim x\}
$$

**Định nghĩa (Quotient Set):**

$$
X/{\sim} = \{[x] : x \in X\} = \text{set of equivalence classes}
$$

**Projection map:**

$$
\pi: X \to X/{\sim}, \quad \pi(x) = [x]
$$

---

**Theorem (Partition):**  
Equivalence relation ~ induces **partition** của X:
- X = ⋃[x] (cover)
- [x] = [y] hay [x] ∩ [y] = ∅ (disjoint)

**Proof:** Straightforward từ axioms. ✓

**Converse:** Mọi partition induces equivalence relation.

---

### 2. Examples

**Example 1: Congruence Modulo n**

X = ℤ, x ~ y ⟺ x ≡ y (mod n).

Equivalence classes: [0], [1], ..., [n-1].  
Quotient: ℤ/nℤ.

---

**Example 2: Gluing Endpoints**

X = [0,1], 0 ~ 1 (plus reflexivity, transitivity).

Equivalence classes:
- [0] = [1] = {0, 1}
- [x] = {x} ∀x ∈ (0,1)

Quotient: [0,1]/~ ≅ S¹ (circle).

---

**Example 3: Identify Subspace to Point**

X space, A ⊆ X. Define:
- x ~ y ⟺ x, y ∈ A
- x ~ x (reflexive)

Equivalence classes:
- [A] = A (one big class)
- [x] = {x} ∀x ∉ A

Quotient: X/A (collapse A to point).

**Notation:** X/A means X với A identified to point.

---

**Example 4: Antipodal Points trên Sphere**

X = S^n, x ~ -x (antipodal).

Quotient: S^n/~ = ℝP^n (**real projective space**).

**Geometric:** Lines through origin trong ℝ^(n+1).

---

## 🏗️ Quotient Topology

### 1. Definition

**Setup:** X topological space, ~ equivalence relation.  
Quotient set X/~ với projection π: X → X/~.

**Goal:** Topology trên X/~ making π continuous và "best possible".

---

**Định nghĩa (Quotient Topology):**  
**Quotient topology** trên X/~ là topology:

$$
\tau_{X/\sim} = \{U \subseteq X/{\sim} : \pi^{-1}(U) \text{ open in } X\}
$$

**Nói bằng lời:** U open trong X/~ ⟺ π^(-1)(U) open trong X.

**Notation:** (X/~, τ) gọi là **quotient space**.

---

**Verification:**

**Theorem:** τ_X/~ thật sự là topology.

**Proof:**
- ∅, X/~ trong τ: π^(-1)(∅) = ∅, π^(-1)(X/~) = X open ✓
- Unions: π^(-1)(⋃Uᵢ) = ⋃π^(-1)(Uᵢ) open ✓
- Finite intersections: π^(-1)(⋂Uᵢ) = ⋂π^(-1)(Uᵢ) open ✓

Vậy τ topology. ✓

---

**Proposition:** π: X → X/~ continuous.

**Proof:** By definition: U open in X/~ ⇒ π^(-1)(U) open in X. ✓

---

### 2. Universal Property

**Universal Property của Quotient Topology:**

**Theorem:**  
f: X/~ → Y continuous ⟺ f ∘ π: X → Y continuous.

**Diagram:**
```
X ---π---> X/~
 \         /
  f∘π     f
   \     /
    \   /
     ⌄ ⌄
      Y
```

**Proof (⇒):**  
f continuous, π continuous ⇒ f ∘ π continuous. ✓

**Proof (⇐):**  
Suppose f ∘ π continuous. Need: f continuous.  
V open in Y.  
(f ∘ π)^(-1)(V) = π^(-1)(f^(-1)(V)) open in X.  
By definition quotient topology: f^(-1)(V) open in X/~.  
Vậy f continuous. ✓

---

**Consequence (Uniqueness):**  
Quotient topology là **finest** (largest) topology trên X/~ making π continuous.

**Trực giác:** Most open sets possible while keeping π continuous.

---

### 3. Quotient Maps

**Định nghĩa (Quotient Map):**  
f: X → Y continuous surjection là **quotient map** nếu:

$$
U \text{ open in } Y \iff f^{-1}(U) \text{ open in } X
$$

**Nói bằng lời:** Y có quotient topology induced by f.

---

**Proposition:**  
Projection π: X → X/~ luôn là quotient map (by definition).

---

**Example (Open Map):**

**Theorem:** f: X → Y continuous surjection, **open** (or **closed**) ⇒ f quotient map.

**Proof (open case):**  
V ⊆ Y. Suppose f^(-1)(V) open.  
V = f(f^(-1)(V)) (surjective).  
f open ⇒ V open. ✓  
Converse (V open ⇒ f^(-1)(V) open) = continuity. ✓

**Remark:** Open/closed maps automatically quotient.

---

### 4. Checking Topology trên Quotient

**Problem:** How to verify U ⊆ X/~ open?

**Answer:** Check π^(-1)(U) open trong X.

**Practical:** Often easier check closed sets: F closed ⟺ π^(-1)(F) closed.

---

**Theorem (Closed Sets):**  
F ⊆ X/~ closed ⟺ π^(-1)(F) closed trong X.

**Proof:** Complement. ✓

---

**Corollary:**  
Quotient space có nice properties if π open or closed map.

---

## 🌀 Examples của Quotient Spaces

### 1. Circle S¹ từ [0,1]

**Construction:**  
X = [0,1], 0 ~ 1.  
X/~ = S¹ (circle).

**Verification:**  
π: [0,1] → S¹ ⊆ ℂ, π(t) = e^(2πit).

**Check quotient map:**  
- π continuous ✓
- π surjective ✓  
- π(0) = π(1) = 1 ✓
- Need: π open or closed?

**π NOT open:** (0, ε) open, nhưng π((0, ε)) = arc, not open in S¹ if ε small. ✗

**π closed?** Yes! [0,1] compact, S¹ Hausdorff ⇒ π closed. ✓

**Conclusion:** [0,1]/~ ≅ S¹ với quotient topology.

---

### 2. Torus T² từ Square

**Construction:**  
X = [0,1] × [0,1] (square).

**Identifications:**
- (0, t) ~ (1, t) (glue left-right)
- (s, 0) ~ (s, 1) (glue top-bottom)

**Result:** T² = torus (doughnut shape).

![Torus from square](https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Torus_from_rectangle.gif/400px-Torus_from_rectangle.gif)  
*Gluing square to form torus - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Torus_from_rectangle.gif)*

**Topology:** Quotient topology induced by π: [0,1]² → T².

**Embedding:** T² ⊆ ℝ³ as surface of revolution.

**Parametrization:**  
π(s,t) = ((R + r cos(2πt))cos(2πs), (R + r cos(2πt))sin(2πs), r sin(2πt))  
với R > r > 0.

---

### 3. Cylinder

**Construction:**  
X = [0,1] × [0,1].  
Identify (0, t) ~ (1, t) (glue left-right only).

**Result:** S¹ × [0,1] = cylinder.

**Note:** Different từ torus—không glue top-bottom.

---

### 4. Möbius Strip

**Construction:**  
X = [0,1] × [0,1].  
Identify (0, t) ~ (1, 1-t) (glue với twist).

**Result:** Non-orientable surface!

![Möbius strip](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/M%C3%B6bius_strip.jpg/400px-M%C3%B6bius_strip.jpg)  
*Möbius strip - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:M%C3%B6bius_strip.jpg)*

**Property:** Single-sided surface (bug can walk từ "inside" to "outside" without crossing edge).

---

### 5. Real Projective Space ℝP^n

**Construction:**  
X = S^n ⊆ ℝ^(n+1).  
x ~ -x (antipodal points).

**Result:** ℝP^n = S^n/~.

**Interpretation:** Lines through origin trong ℝ^(n+1).

**Examples:**
- ℝP¹ = S¹/~ ≅ S¹ (circle)
- ℝP² = projective plane (non-orientable, can't embed trong ℝ³)

**Applications:**  
- Geometry (projective geometry)
- Computer vision (homogeneous coordinates)
- Physics (quantum states = points trong projective space)

---

### 6. Collapsing Subspace

**Construction:**  
X space, A ⊆ X nonempty.  
X/A = quotient với A identified to single point.

**Example:** D²/S¹ (disk với boundary identified).  
Result = S² (sphere)!

**Proof:** Stereographic projection from sphere to disk. ✓

---

### 7. Cone và Suspension

**Cone:** X topological space.  
CX = (X × [0,1]) / (X × {0}).

**Trực giác:** Collapse one end to point—forms "cone" over X.

**Suspension:** ΣX = (X × [0,1]) / (X×{0} ∪ X×{1}).

**Trực giác:** Collapse both ends—"suspend" X between two points.

**Example:** ΣS^n = S^(n+1).

---

## 🔍 Properties của Quotient Maps

### 1. When is Quotient Map Open/Closed?

**Not automatic:** π: X → X/~ may not be open or closed.

**Example (Not Open):**  
X = ℝ², A = x-axis.  
π: ℝ² → ℝ²/A.  
Open set in ℝ² có thể have preimage not open. ✗

---

**Theorem (Sufficient Conditions):**

**If X compact, Y Hausdorff, f: X → Y continuous surjection ⇒ f quotient map.**

**Proof:** Compact → Hausdorff = closed map. ✓

**Application:** Many geometric quotients (sphere → projective space).

---

### 2. Hausdorff Quotients

**Problem:** X Hausdorff ≠ X/~ Hausdorff.

**Example:**  
X = ℝ với equivalence: 0 ~ 1, else reflexive.  
X/~ NOT Hausdorff (can't separate [0] từ nearby points). ✗

---

**Theorem (Sufficient Condition):**  
R = {(x,y) : x ~ y} ⊆ X × X.  
If R closed trong X × X, thì X/~ Hausdorff.

**Proof:** Technical. See Munkres §22. ✓

**Example:** Antipodal relation trên S^n closed ⇒ ℝP^n Hausdorff. ✓

---

### 3. First Isomorphism Theorem

**Theorem:**  
f: X → Y continuous surjection.  
Define ~ : x ~ y ⟺ f(x) = f(y).  
Thì X/~ ≅ Y (homeomorphic).

**Proof:**  
Induced map f̄: X/~ → Y, f̄([x]) = f(x).  
f̄ bijection, continuous (universal property).  
f̄ homeomorphism if quotient map. ✓

**Application:** Identify quotient spaces với concrete spaces.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Henri Poincaré** - *Analysis Situs* (1895)  
   *Foundational work on topology, surfaces*

2. **Felix Hausdorff** - *Grundzüge der Mengenlehre* (1914)  
   *Systematic treatment topology*

### Textbooks

3. **James R. Munkres** - *Topology*, 2nd Ed., **§22: Quotient Topology**

4. **John M. Lee** - *Introduction to Topological Manifolds*, **Chapter 3**  
   *Quotient spaces, surfaces*

5. **Allen Hatcher** - *Algebraic Topology*, **§0.2: Surfaces**  
   *Geometric perspective*

6. **Sidney A. Morris** - *Topology without Tears*, **Chapter 7**

---

## 🔗 Applications and Connections

### Geometry - Surfaces
**Classification:** Compact surfaces classified via quotient construction (sphere, torus, projective plane, Klein bottle).

### Differential Geometry - Manifolds
**Charts:** Local homeomorphisms with quotient structure define manifolds.

### Algebraic Topology
**CW Complexes:** Built by gluing cells—quotient construction.

### Physics - Gauge Theory
**Principal Bundles:** Quotient by group actions (gauge symmetries).

### Computer Graphics
**Texture Mapping:** Torus parametrized as quotient của square.

---

## 🧩 Exercises

### Equivalence Relations

1. **Verify:**  
   x ~ y ⟺ x - y ∈ ℤ trên ℝ. Verify equivalence relation axioms.

2. **Equivalence Classes:**  
   Trong bài 1, mô tả [0], [π], [1/2].

3. **Partition:**  
   Equivalence relation induces partition. Prove carefully.

### Quotient Topology

4. **Definition:**  
   Verify quotient topology thật sự là topology.

5. **π Continuous:**  
   π: X → X/~ continuous. Prove từ definition.

6. **Universal Property:**  
   f: X/~ → Y continuous ⟺ f ∘ π continuous. Verify both directions.

### Quotient Maps

7. **Open Map:**  
   f: X → Y continuous open surjection ⇒ quotient map. Prove.

8. **Closed Map:**  
   f compact → Hausdorff ⇒ closed map. Sketch proof.

9. **Counterexample:**  
   Continuous surjection không phải quotient map. Example?

### Examples

10. **Circle:**  
    [0,1] với 0 ~ 1. Verify X/~ ≅ S¹.

11. **Torus:**  
    Sketch gluing square to torus. Label identifications.

12. **Möbius Strip:**  
    Construct từ rectangle. Where's twist?

### ℝP^n

13. **ℝP¹:**  
    ℝP¹ = S¹/~. Show ℝP¹ ≅ S¹.

14. **ℝP²:**  
    ℝP² non-orientable. Research proof sketch.

15. **Homogeneous Coordinates:**  
    ℝP^n = (ℝ^(n+1) \ {0}) / ~, [x₀:...:xₙ]. Explain.

### Hausdorff

16. **Not Hausdorff:**  
    ℝ với 0 ~ 1. Show X/~ không Hausdorff.

17. **Sufficient Condition:**  
    R closed trong X × X ⇒ X/~ Hausdorff. Research proof.

18. **Antipodal:**  
    Antipodal relation trên S^n closed? Verify ⇒ ℝP^n Hausdorff.

### Advanced

19. **Cone:**  
    CX = (X × [0,1]) / (X × {0}). CS^n = ?

20. **Suspension:**  
    ΣS^n ≅ S^(n+1). Sketch geometric argument.

---

## 📚 Further Reading

- **Munkres, Topology:** §22 (Quotient Topology)
- **Lee, Topological Manifolds:** Chapter 3 (Quotient spaces)
- **Hatcher, Algebraic Topology:** §0.2 (Surfaces)
- **Armstrong:** *Basic Topology* (Geometric intuition)

---

## 🎓 Summary

Trong bài học này, chúng ta đã khám phá quotient topology—một công cụ mạnh mẽ để xây dựng các không gian mới. Các quan hệ tương đương là nền tảng cho việc xây dựng quotient spaces—chúng là các quan hệ phản xạ, đối xứng, và bắc cầu cho phép chúng ta xác định các điểm nào là "giống nhau". Tập quotient $X/\sim$ là tập hợp tất cả các lớp tương đương, và quotient topology được định nghĩa bởi điều kiện: $U$ mở trong $X/\sim$ nếu và chỉ nếu $\pi^{-1}(U)$ mở trong $X$. Universal property đặc trưng cho quotient topology: một hàm $f: X/\sim \to Y$ là liên tục nếu và chỉ nếu $f \circ \pi: X \to Y$ là liên tục. Các quotient maps là các ánh xạ liên tục toàn ánh tạo ra quotient topology, và các ví dụ quan trọng bao gồm $S^1$, torus, Möbius strip, $\mathbb{R}P^n$, và các không gian thu được bằng cách co lại các tập con.

Điểm chính của bài học là quotient topology tương đương với việc "dán" hoặc "đồng nhất" các điểm—chúng ta xác định các điểm nào đó là giống nhau và tạo ra một không gian mới từ không gian gốc. Ánh xạ chiếu $\pi: X \to X/\sim$ luôn liên tục theo định nghĩa—đây là một tính chất cơ bản của quotient topology. Universal property đặc trưng cho quotient topology—nó cho chúng ta biết cách xây dựng các ánh xạ từ quotient space. Một kết quả quan trọng là nếu $X$ compact và $Y$ Hausdorff, thì mọi ánh xạ liên tục toàn ánh $f: X \to Y$ đều là quotient map closed. Tuy nhiên, cần lưu ý rằng $X$ Hausdorff không đảm bảo $X/\sim$ Hausdorff—chúng ta cần điều kiện bổ sung về quan hệ tương đương.

Trực giác hình học đằng sau các ví dụ quan trọng là: hình tròn được tạo ra từ đoạn $[0,1]$ bằng cách dán hai đầu mút lại với nhau, torus được tạo ra từ một hình vuông bằng cách dán các cạnh đối diện lại với nhau, và không gian projective được tạo ra từ hình cầu bằng cách đồng nhất các điểm đối cực. Những ví dụ này minh họa cách quotient topology cho phép chúng ta tạo ra các hình dạng phức tạp từ các hình dạng đơn giản.

Trong thực tế, chúng ta kiểm tra xem một tập $U$ có mở trong quotient space hay không bằng cách kiểm tra $\pi^{-1}(U)$ có mở trong không gian gốc hay không. Chúng ta sử dụng universal property để xây dựng các ánh xạ từ quotient space—đây là một kỹ thuật mạnh mẽ và phổ biến. Để xác minh rằng một quotient space là Hausdorff, chúng ta kiểm tra xem quan hệ tương đương $R = \{(x,y) : x \sim y\}$ có đóng trong $X \times X$ hay không—đây là một điều kiện đủ quan trọng.

**Tiếp theo:** Lecture 05.01 về **Classification of Surfaces**—phân loại hoàn chỉnh các bề mặt compact thông qua quotient!

---

*"Quotient topology: the art of gluing things together."* — Topologist's wisdom

🎯 **Master quotients! They create surfaces and manifolds.** 🎯

---

**Previous Chapter:** [Chapter 04: Metric Spaces](/contents/vi/topology-chapter04/)  
**Next:** [Lecture 05.01: Classification of Surfaces](/contents/vi/topology-chapter05/05_01_Classification_Surfaces/)

