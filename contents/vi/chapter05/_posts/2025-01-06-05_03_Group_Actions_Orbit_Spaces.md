---
layout: post
title: "Lecture 05.03: Group Actions and Orbit Spaces"
lang: vi
lang-ref: lecture-05-03
chapter: 5
lecture: 3
categories: [chapter05]
tags: [group-actions, orbit-spaces, quotient-by-group, covering-spaces, symmetry]
description: "Group actions trên topological spaces, orbit spaces, và applications: covering spaces, symmetry"
---

**Group Actions and Orbit Spaces**

---

## 📖 Tổng quan

Đối xứng xuất hiện ở khắp nơi trong toán học và vật lý. **Group actions** chính thức hóa đối xứng một cách toán học, cho phép chúng ta nghiên cứu các đối xứng của các không gian tô-pô một cách có hệ thống.

Một **group action** là một cách mà một nhóm $G$ "tác động" lên một không gian $X$—mỗi phần tử của nhóm tương ứng với một đối xứng của $X$. Điều này có nghĩa là mỗi phần tử $g \in G$ cho chúng ta một cách biến đổi không gian $X$ mà bảo toàn một số tính chất nhất định. **Orbit space** $X/G$ là không gian của các orbits—các điểm được đồng nhất nếu chúng liên quan với nhau bởi group action. Đây là một cách tự nhiên để tạo ra các không gian mới từ các không gian đã biết bằng cách "mod out" các đối xứng.

![Group action visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Hexagonal_tiling_3-color.svg/400px-Hexagonal_tiling_3-color.svg.png)  
*Tác động của nhóm đối xứng trên tiling - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hexagonal_tiling_3-color.svg)*

Tại sao group actions lại quan trọng đến vậy? Thứ nhất, chúng nắm bắt các đối xứng hình học—rotations, reflections, translations đều có thể được mô hình hóa như các group actions. Thứ hai, nhiều không gian quan trọng xuất hiện như các orbit spaces $X/G$—ví dụ, hình tròn $S^1$ có thể được xem như $\mathbb{R}/\mathbb{Z}$ nơi $\mathbb{Z}$ tác động bằng translation. Thứ ba, trong lý thuyết covering spaces, universal cover có thể được hiểu như một quotient bởi fundamental group—đây là một kết nối sâu sắc giữa group actions và covering spaces. Cuối cùng, trong vật lý, gauge theory, particle physics, và general relativity đều sử dụng group actions để mô hình hóa các đối xứng và các không gian cấu hình.

Các ví dụ quan trọng bao gồm: $S^1$ tác động lên $\mathbb{C}$ bằng rotation dẫn đến quotient là một điểm (nếu chúng ta đồng nhất tất cả các điểm trên cùng một quỹ đạo), $\mathbb{Z}$ tác động lên $\mathbb{R}$ bằng translation dẫn đến $\mathbb{R}/\mathbb{Z} \cong S^1$, $\mathbb{Z}/2\mathbb{Z}$ tác động lên $S^n$ bằng antipodal map dẫn đến $S^n/(\mathbb{Z}/2\mathbb{Z}) = \mathbb{R}P^n$, và các deck transformations của covering spaces là các ví dụ tự nhiên của group actions.

Trong bài học này, chúng ta sẽ khám phá các khái niệm cơ bản của group actions và orbit spaces. Chúng ta bắt đầu với định nghĩa của group actions và các ví dụ quan trọng. Chúng ta sẽ nghiên cứu orbits và stabilizers—các khái niệm cơ bản cho phép chúng ta hiểu cách group action phân chia không gian. Chúng ta sẽ định nghĩa orbit space $X/G$ với quotient topology và khám phá các tính chất của nó. Chúng ta sẽ nghiên cứu free actions—các actions không có điểm cố định, và properly discontinuous actions—các actions tạo ra các quotient tốt. Cuối cùng, chúng ta sẽ khám phá các ứng dụng trong covering spaces và Lie groups.

---

## 🔄 Group Actions: Definition

### 1. Basic Definition

**Định nghĩa (Group Action):**  
Cho G group, X topological space.  
**Left action** của G trên X là map:

$$
G \times X \to X, \quad (g, x) \mapsto g \cdot x
$$

satisfying:

**(GA1) Identity:** e · x = x ∀x (e = identity của G)

**(GA2) Compatibility:** g · (h · x) = (gh) · x ∀g, h ∈ G, x ∈ X

**Continuous action:** Map G × X → X continuous (với product topology trên G × X).

---

**Right action:** x · g satisfying xe = x, x(gh) = (xg)h.

**Convention:** Chúng ta dùng left actions.

---

**Alternative notation:**  
Action = group homomorphism φ: G → Homeo(X).

**φ(g) = permutation của X induced by g.**

**Equivalent definitions.**

---

### 2. Examples

**Example 1: Rotation Action**

G = S¹ = {e^(iθ) : θ ∈ [0, 2π)}.  
X = ℂ.  
Action: e^(iθ) · z = e^(iθ) z (multiply).

**Geometric:** Rotate plane by angle θ.

**Continuous:** ✓

---

**Example 2: Translation Action**

G = ℤ.  
X = ℝ.  
Action: n · x = x + n.

**Geometric:** Translate by integer.

**Quotient:** ℝ/ℤ ≅ S¹ (circle). ✓

---

**Example 3: Antipodal Action**

G = ℤ/2ℤ = {0, 1}.  
X = S^n.  
Action: 0 · x = x, 1 · x = -x (antipodal).

**Quotient:** S^n / (ℤ/2ℤ) = ℝP^n (projective space). ✓

---

**Example 4: Matrix Action**

G = GL_n(ℝ) (invertible matrices).  
X = ℝⁿ.  
Action: A · x = Ax (matrix multiplication).

**Linear action.**

---

**Example 5: Covering Space Deck Transformations**

X̃ → X covering space.  
G = group của deck transformations (covering automorphisms).

**Action:** G acts trên X̃.

**Quotient:** X̃/G = X (often). ✓

---

## 🎯 Orbits và Stabilizers

### 1. Orbits

**Định nghĩa (Orbit):**  
Orbit của x ∈ X:

$$
G \cdot x = \{g \cdot x : g \in G\} \subseteq X
$$

**Trực giác:** All points reachable từ x by group action.

---

**Proposition:**  
Orbits partition X:
- X = ⋃ orbits (cover)
- Orbits disjoint or identical

**Proof:** Define equivalence relation x ~ y ⟺ ∃g: y = g · x. ✓

---

**Định nghĩa (Orbit Space):**  
**Orbit space** (hay **quotient by group action**):

$$
X/G = \{G \cdot x : x \in X\} = \text{set of orbits}
$$

**Quotient topology:** U ⊆ X/G open ⟺ π^(-1)(U) open trong X.

**Projection:** π: X → X/G, π(x) = G · x.

---

**Examples:**

**Example 1:** ℝ/ℤ = S¹.  
Orbits: {x + n : n ∈ ℤ}.

**Example 2:** S^n / (ℤ/2ℤ) = ℝP^n.  
Orbits: {x, -x}.

---

### 2. Stabilizers

**Định nghĩa (Stabilizer):**  
**Stabilizer** (hay **isotropy group**) của x:

$$
G_x = \{g \in G : g \cdot x = x\} \subseteq G
$$

**Trực giác:** Subgroup của G fixing x.

---

**Proposition:** G_x subgroup của G.

**Proof:** Verify closed under multiplication, inverses. ✓

---

**Orbit-Stabilizer Theorem:**

**Theorem:**  
Bijection:

$$
G/G_x \leftrightarrow G \cdot x
$$

(G/G_x = left cosets của G_x.)

**Formula:** |G · x| = |G| / |G_x| (if finite).

**Proof:** gG_x ↔ g · x well-defined bijection. ✓

---

**Examples:**

**Example 1:** S¹ acts trên ℂ by rotation.  
Stabilizer của 0: entire S¹ (all rotations fix origin).  
Stabilizer của z ≠ 0: {e} (only identity).

**Example 2:** SO(3) acts trên S² (sphere).  
Stabilizer của north pole: SO(2) (rotations around axis).

---

## 🌀 Free Actions và Properly Discontinuous

### 1. Free Actions

**Định nghĩa (Free Action):**  
Action **free** nếu G_x = {e} ∀x ∈ X.

**Nói bằng lời:** No non-identity element fixes any point.

**Equivalent:** g · x = x ⇒ g = e.

---

**Examples:**

**Free:**
- ℤ acts trên ℝ by translation ✓
- ℤ/2ℤ acts trên S^n \ {poles} (antipodal, excluding fixed points) ✓

**NOT Free:**
- S¹ acts trên ℂ (origin fixed by all) ✗
- SO(3) acts trên ℝ³ (origin fixed) ✗

---

**Theorem (Free ⇒ Covering):**  
G discrete, acts freely và properly discontinuously trên X simply connected, Hausdorff ⇒ π: X → X/G covering map.

**Proof:** See covering space theory. ✓

**Application:** ℝ → S¹ covering (ℤ acts freely).

---

### 2. Properly Discontinuous Actions

**Định nghĩa (Properly Discontinuous):**  
Action **properly discontinuous** nếu ∀x ∈ X: ∃ neighborhood U của x:

$$
g \cdot U \cap U \neq \emptyset \implies g = e
$$

**Trực giác:** Orbits "spread out"—locally finite.

**Equivalent (for locally compact Hausdorff):** ∀ compact K, L: {g : gK ∩ L ≠ ∅} finite.

---

**Examples:**

**Properly discontinuous:**
- ℤ acts trên ℝ ✓ (translates disjoint locally)
- ℤ/2ℤ acts trên S^n (antipodal) ✓
- ℤ² acts trên ℝ² (lattice) ✓

**NOT Properly discontinuous:**
- ℚ acts trên ℝ (dense orbits) ✗
- S¹ acts trên ℂ (orbits circles, not discrete) ✗

---

**Theorem (Nice Quotients):**  
G acts properly discontinuously trên Hausdorff X ⇒ X/G Hausdorff.

**Proof:** Properly discontinuous ⇒ can separate orbits. ✓

**Corollary:** ℝ/ℤ, S^n/(ℤ/2ℤ) Hausdorff. ✓

---

## 🎭 Applications

### 1. Covering Spaces

**Connection:** Covering space theory = special case group actions.

**Setup:** p: X̃ → X covering space.  
**Deck transformation group:** Aut(X̃/X) = {f: X̃ → X̃ homeomorphism : p ∘ f = p}.

**G = Aut(X̃/X) acts trên X̃.**

**Theorem:**  
X̃ path-connected, locally path-connected, X path-connected ⇒ X̃/G ≅ X.

**Special case:** X̃ universal cover, G = π₁(X) ⇒ X̃/π₁(X) = X. ✓

**Example:** ℝ universal cover S¹, ℤ = π₁(S¹) acts by translation, ℝ/ℤ = S¹. ✓

---

### 2. Fundamental Domain

**Định nghĩa (Fundamental Domain):**  
**Fundamental domain** F ⊆ X cho action:
- ⋃_{g∈G} g · F = X (cover)
- g · int(F) ∩ int(F) = ∅ ∀g ≠ e (disjoint interiors)

**Trực giác:** "Representative piece"—mỗi orbit intersects F đúng một lần (roughly).

---

**Example 1: ℤ acts trên ℝ**

Fundamental domain: [0, 1).  
ℝ = ⋃_n [n, n+1).  
Quotient ℝ/ℤ ≅ [0,1)/(0~1) = S¹. ✓

---

**Example 2: ℤ² acts trên ℝ²**

Fundamental domain: [0,1) × [0,1) (unit square).  
Quotient: T² (torus). ✓

---

**Example 3: Wallpaper Groups**

17 wallpaper groups = symmetries of plane tilings.  
Each has fundamental domain (tessellates plane).

![Wallpaper group](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Wallpaper_group-p4m-2.jpg/400px-Wallpaper_group-p4m-2.jpg)  
*Wallpaper group p4m - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Wallpaper_group-p4m-2.jpg)*

---

### 3. Lie Group Actions

**Lie groups:** Smooth groups (SO(n), U(n), SU(n), ...).

**Actions trên manifolds:** Smooth actions.

**Orbit space:** Often stratified space (not manifold).

**Example:** SO(3) acts trên ℝ³.  
Orbits: {0}, spheres S²_r.  
Orbit space: [0, ∞) (radius).

---

**Homogeneous Spaces:**

**Định nghĩa:** M = G/H (quotient Lie group by closed subgroup).

**Examples:**
- S^n = SO(n+1) / SO(n)
- ℝP^n = O(n+1) / (O(n) × O(1))
- Grassmannians = G_k(ℝⁿ) = O(n) / (O(k) × O(n-k))

**Applications:** Differential geometry, representation theory.

---

### 4. Orbit Types và Stratification

**Định nghĩa (Orbit Type):**  
Points x, y same **orbit type** if G_x, G_y conjugate subgroups.

**Stratification:** X decomposes into strata of same orbit type.

**Example:** SO(3) trên ℝ³:
- Stratum 1: {0} (stabilizer = SO(3))
- Stratum 2: ℝ³ \ {0} (stabilizer = SO(2))

**Applications:** Singularity theory, geometric analysis.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Felix Klein** - *"Erlanger Programm"* (1872)  
   *Geometry = study của group actions*

2. **Élie Cartan** - *Lie group theory* (early 20th century)

3. **Claude Chevalley** - *"Theory of Lie Groups"* (1946)

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§1.3: Covering Spaces**  
   *Deck transformations*

5. **John M. Lee** - *Introduction to Smooth Manifolds*, **Chapter 21**  
   *Lie group actions*

6. **Glen E. Bredon** - *Introduction to Compact Transformation Groups* (1972)  
   *Comprehensive theory*

7. **Tammo tom Dieck** - *Transformation Groups* (1987)

---

## 🔗 Applications and Connections

### Algebraic Topology - Covering Spaces
**Deck Transformations:** Universal cover X̃/π₁(X) = X.

### Differential Geometry - Homogeneous Spaces
**Lie Groups:** Spheres, projective spaces, Grassmannians = G/H.

### Physics - Gauge Theory
**Principal Bundles:** Quotient by gauge group. Yang-Mills theory.

### Crystallography
**Space Groups:** Symmetries of crystals. 230 types in 3D.

### Dynamics - Symmetry Reduction
**Hamiltonian Systems:** Quotient by symmetry group (symplectic reduction).

---

## 🧩 Exercises

### Group Actions

1. **Verify Action:**  
   ℤ acts trên ℝ by n · x = x + n. Verify axioms (GA1), (GA2).

2. **Rotation:**  
   S¹ acts trên ℂ by e^(iθ) · z = e^(iθ)z. Continuous?

3. **Matrix Action:**  
   GL₂(ℝ) acts trên ℝ². Verify action axioms.

### Orbits

4. **Compute Orbits:**  
   ℤ acts trên ℝ. Orbit của π = ?

5. **Antipodal:**  
   ℤ/2ℤ acts trên S². Orbits = ?

6. **Partition:**  
   Prove orbits partition space X.

### Stabilizers

7. **Compute Stabilizer:**  
   S¹ acts trên ℂ by rotation. Stabilizer của 0? Của 1?

8. **Orbit-Stabilizer:**  
   Verify |G · x| · |G_x| = |G| cho finite G.

9. **SO(3) Action:**  
   SO(3) acts trên S². Stabilizer của north pole = ?

### Free Actions

10. **Verify Free:**  
    ℤ acts trên ℝ freely. Prove.

11. **Not Free:**  
    S¹ acts trên ℂ không free. Fixed point?

12. **Covering:**  
    ℝ → S¹. ℤ acts freely, quotient = S¹. Verify covering map.

### Properly Discontinuous

13. **Verify PD:**  
    ℤ acts trên ℝ properly discontinuously. Check definition.

14. **ℤ² Lattice:**  
    ℤ² acts trên ℝ² by translation. Properly discontinuous? Quotient = ?

15. **Not PD:**  
    ℚ acts trên ℝ không properly discontinuous. Why?

### Fundamental Domain

16. **ℝ/ℤ:**  
    Fundamental domain [0,1) cho ℤ action. Verify covering, disjoint interiors.

17. **Torus:**  
    ℤ² acts trên ℝ². Fundamental domain = unit square. Quotient T².

18. **Wallpaper:**  
    Research one wallpaper group. Fundamental domain?

### Applications

19. **Covering Space:**  
    ℝ² → T² covering. Deck transformation group = ℤ². Verify.

20. **Homogeneous Space:**  
    S^n = SO(n+1)/SO(n). Explain construction.

---

## 📚 Further Reading

- **Lee, Smooth Manifolds:** Chapter 21 (Lie group actions)
- **Hatcher, Algebraic Topology:** §1.3 (Deck transformations)
- **Bredon, Transformation Groups:** Comprehensive theory
- **Armstrong:** *Groups and Symmetry* (Elementary introduction)

---

## 🎓 Summary

Trong bài học này, chúng ta đã khám phá **group actions** và **orbit spaces**—các công cụ mạnh mẽ để nghiên cứu đối xứng trong topology. Một group action là một ánh xạ $G \times X \to X$ thỏa mãn các điều kiện identity và compatibility—mỗi phần tử của nhóm tương ứng với một đối xứng của không gian. Các orbits $G \cdot x = \{g \cdot x : g \in G\}$ phân chia không gian $X$ thành các lớp tương đương, và orbit space $X/G$ là không gian của các orbits với quotient topology. Các stabilizers $G_x = \{g : g \cdot x = x\}$ là các nhóm con của $G$ cố định điểm $x$, và định lý Orbit-Stabilizer cho chúng ta biết về mối quan hệ giữa orbits và stabilizers. Free actions là các actions không có điểm cố định—không có phần tử nào khác identity cố định bất kỳ điểm nào. Properly discontinuous actions là các actions mà các orbits được "trải ra" một cách địa phương—chúng tạo ra các quotient tốt. Các ứng dụng quan trọng bao gồm covering spaces (nơi $\pi: \tilde{X} \to X$ và $G = \pi_1(X)$), và Lie groups (nơi các homogeneous spaces $G/H$ xuất hiện tự nhiên).

Điểm chính của bài học là group actions chính thức hóa đối xứng—chúng cho phép chúng ta nghiên cứu các đối xứng của các không gian một cách có hệ thống. Orbit space là quotient bởi action—chúng ta đồng nhất các điểm trong cùng một orbit. Free actions kết hợp với properly discontinuous actions dẫn đến covering spaces—đây là một kết nối sâu sắc giữa group actions và covering spaces. Fundamental domain là một "mảnh đại diện"—mỗi orbit giao với fundamental domain đúng một lần, cho phép chúng ta hình dung quotient một cách trực quan. Các ứng dụng rộng rãi bao gồm covering spaces, Lie groups, và crystallography—group actions xuất hiện ở khắp nơi trong toán học và vật lý.

Trực giác hình học đằng sau các ví dụ quan trọng là: $\mathbb{Z}$ tác động lên $\mathbb{R}$ bằng translation dẫn đến $\mathbb{R}/\mathbb{Z} = S^1$ (hình tròn), $\mathbb{Z}/2\mathbb{Z}$ tác động lên $S^n$ bằng antipodal map dẫn đến $\mathbb{R}P^n$ (không gian projective), các deck transformations của covering spaces là các ví dụ tự nhiên của group actions, và các homogeneous spaces $G/H$ xuất hiện trong nhiều bối cảnh hình học.

Trong thực tế, chúng ta tính toán orbits và stabilizers để hiểu cách group action phân chia không gian. Chúng ta kiểm tra tính free và properly discontinuous để đảm bảo các quotient tốt—các tính chất này đảm bảo rằng orbit space có các tính chất tô-pô tốt. Fundamental domain giúp chúng ta hình dung quotient một cách trực quan—nó cho chúng ta một cách để "nhìn thấy" orbit space. Covering spaces là trường hợp đặc biệt của group actions—chúng ta có thể hiểu covering spaces thông qua group actions của deck transformation group.

**Chapter 05 hoàn thành!** Quotient topology, surfaces, CW complexes, và group actions đã được nắm vững!

**Tiếp theo:** Chapter 06 về **Fundamental Group và Covering Spaces**—tô-pô học đại số bắt đầu!

---

*"Symmetry is the harmony of mathematics."* — Klein's vision

🎯 **Master group actions! They reveal hidden symmetries.** 🎯

---

**Previous:** [Lecture 05.02: CW Complexes](/contents/vi/topology-chapter05/05_02_CW_Complexes/)  
**Next Chapter:** [Chapter 06: Fundamental Group and Covering Spaces](/contents/vi/topology-chapter06/)

