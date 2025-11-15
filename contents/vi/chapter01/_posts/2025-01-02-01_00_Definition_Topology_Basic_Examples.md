---
layout: post
title: "Lecture 01.00: Definition of Topology and Basic Examples"
lang: vi
lang-ref: lecture-01-00
chapter: 1
lecture: 0
categories: [chapter01]
tags: [topology-definition, examples, trivial-topology, discrete-topology]
description: "Định nghĩa chính thức của topology, các axioms, và các ví dụ cơ bản"
---

**Definition of Topology and Basic Examples**

---

## 📖 Tổng quan

Chào mừng bạn đến với **bài giảng quan trọng nhất** trong toàn bộ khóa học! Đây là lúc chúng ta cuối cùng định nghĩa chính thức: **Topology là gì?**

Sau khi đã chuẩn bị qua lý thuyết tập hợp, metric spaces, và Euclidean space, giờ đây chúng ta sẵn sàng để thực hiện một bước **trừu tượng hóa mạnh mẽ**. Chúng ta sẽ bỏ qua tất cả "khoảng cách" (distance) và chỉ giữ lại **cấu trúc** (structure) về "gần" và "xa".

**Ý tưởng cốt lõi:**  
Trong metric space, chúng ta định nghĩa "open set" thông qua open balls. Nhưng nếu bỏ metric đi và **chỉ giữ lại tập hợp các open sets**, thì ta vẫn có thể nói về continuity, convergence, và nhiều khái niệm khác!

**Đây chính là topology**: Một cách để nói về "cấu trúc" của không gian mà không cần metric.

**Trong bài này** we lay absolute foundation. First, precise **topological space** definition emerges—deceptively simple yet profoundly powerful. Understanding ba **topology axioms** reveals why they're not arbitrary rules but natural requirements ensuring consistency. Exploring **basic examples** (trivial, discrete, cofinite topologies) shows extreme cases và builds intuition. Learning to **compare topologies** (coarser vs finer) introduces partial ordering on topology space itself. Finally, **closed sets, interior, closure** get defined purely via open sets, demonstrating how much geometry lives in abstract structure.

**Tại sao absolutely foundational?** Đây là bedrock của **entire topology edifice**! Every concept following—continuous functions, compactness, connectedness, separation axioms—builds exclusively on this definition. Nothing else! Topology liberates us to study "shape" và "structure" independent of "size" or "distance", enabling geometric reasoning trong spaces where distance makes no sense (function spaces, quotient spaces, infinite-dimensional spaces). This abstraction proved revolutionary, unifying previously disparate branches of mathematics.

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Abstraction

Hãy nhớ lại: Trong ℝ với Euclidean metric, open set là tập U sao cho mọi điểm x ∈ U có một "vùng xung quanh" còn nằm trong U.

**Tính chất của open sets trong ℝ:**
1. **∅ và ℝ đều open**
2. **Hợp tùy ý** các open sets là open  
   Ví dụ: (0,1) ∪ (2,3) ∪ (4,5) ∪ ... đều open
3. **Giao hữu hạn** các open sets là open  
   Ví dụ: (0,2) ∩ (1,3) = (1,2) open

**Quan sát kỳ diệu:**  
Những tính chất này không phụ thuộc vào "công thức" của metric! Chúng chỉ phụ thuộc vào **cấu trúc** của họ open sets.

**Ý tưởng của Hausdorff (1914):**  
> "Thay vì định nghĩa open sets từ metric, tại sao không **chọn** một họ tập hợp làm 'open sets' ngay từ đầu, chỉ cần chúng thỏa mãn ba tính chất trên?"

Và thế là **topology** ra đời!

![Felix Hausdorff](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Hausdorff_1913.jpg/300px-Hausdorff_1913.jpg)  
*Felix Hausdorff (1868–1942) - Cha đẻ của topology hiện đại - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hausdorff_1913.jpg)*

---

## 📐 Định nghĩa Hình thức

### 1. Topological Space (Không gian Tô-pô)

**Định nghĩa (Topology):**  
Cho X là một tập hợp. Một **topology** trên X là một họ 𝜏 các tập con của X (gọi là **open sets**) thỏa mãn ba điều kiện:

**(T1) Empty set và whole space:**
$$
\emptyset \in \tau \quad \text{và} \quad X \in \tau
$$

**(T2) Arbitrary unions:**
$$
\{U_\alpha\}_{\alpha \in I} \subseteq \tau \implies \bigcup_{\alpha \in I} U_\alpha \in \tau
$$

(Hợp của **bất kỳ** họ nào các open sets là open)

**(T3) Finite intersections:**
$$
U_1, U_2, \ldots, U_n \in \tau \implies U_1 \cap U_2 \cap \cdots \cap U_n \in \tau
$$

(Giao của **hữu hạn** open sets là open)

**Ký hiệu:** Cặp (X, 𝜏) được gọi là **topological space** (không gian tô-pô).

**Trực giác:**
- **(T1):** "Không có gì" và "toàn bộ" đều "open"
- **(T2):** Ghép nhiều vùng open lại vẫn open
- **(T3):** Giao một số hữu hạn vùng open vẫn open

**Chú ý quan trọng:**  
- Unions có thể **tùy ý** (vô hạn, uncountable!)
- Intersections chỉ **hữu hạn**!

**Tại sao không cho phép giao vô hạn?**  
Xét trong ℝ: ⋂ₙ₌₁^∞ (-1/n, 1/n) = {0}, nhưng {0} **không open** trong ℝ!

---

### 2. Basic Examples (Ví dụ Cơ bản)

#### Example 1: Trivial Topology (Indiscrete Topology)

**Định nghĩa:**  
Topology **thô nhất** (coarsest) trên X:
$$
\tau_{\text{trivial}} = \{\emptyset, X\}
$$

**Chỉ có** ∅ và X là open!

**Kiểm tra axioms:**
- (T1): ∅, X ∈ 𝜏 ✓
- (T2): ∅ ∪ X = X ∈ 𝜏 ✓
- (T3): ∅ ∩ X = ∅ ∈ 𝜏 ✓

**Trực giác:** Topology này "không phân biệt" gì cả—mọi thứ "dính" vào nhau.

**Ví dụ cụ thể:** X = {a, b, c}, 𝜏 = {∅, {a,b,c}}

---

#### Example 2: Discrete Topology

**Định nghĩa:**  
Topology **mịn nhất** (finest) trên X:
$$
\tau_{\text{discrete}} = \mathcal{P}(X) = \text{tất cả tập con của } X
$$

**Mọi** tập con đều open!

**Kiểm tra axioms:**
- (T1): Rõ ràng ✓
- (T2): Hợp tùy ý các tập con vẫn là tập con ✓
- (T3): Giao hữu hạn các tập con vẫn là tập con ✓

**Trực giác:** Topology này "phân biệt hoàn toàn"—mọi điểm "cô lập".

**Ví dụ cụ thể:** X = {a, b}, 𝜏 = {∅, {a}, {b}, {a,b}}

**Kết nối với metric:** Discrete topology = topology induced bởi discrete metric!

![Discrete vs Trivial topology](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Topological_structures.svg/500px-Topological_structures.svg.png)  
*So sánh các cấu trúc tô-pô - Nguồn concept illustration*

---

#### Example 3: Euclidean Topology on ℝ

**Định nghĩa:**  
𝜏 = {U ⊆ ℝ : U là hợp của các khoảng mở}

**Ví dụ open sets:**
- (a, b): khoảng mở
- (0, 1) ∪ (2, 3): hợp hai khoảng
- ℝ \ {0, 1, 2, ...}: bù của tập rời rạc
- ℚ: KHÔNG open trong ℝ!

**Đây chính là** topology thông thường trên ℝ—induced từ Euclidean metric.

---

#### Example 4: Cofinite Topology

**Định nghĩa:**  
Trên tập X, cofinite topology là:
$$
\tau_{\text{cofinite}} = \{U \subseteq X : X \setminus U \text{ hữu hạn hoặc } U = \emptyset\}
$$

**Nói cách khác:** U open ⟺ bù của U hữu hạn (hoặc U = ∅).

**Kiểm tra axioms:**

**(T1):**
- ∅: bù của ∅ là X (có thể vô hạn) → ∅ open by definition ✓
- X: bù của X là ∅ (hữu hạn: 0 phần tử) → X open ✓

**(T2) Unions:**  
Cho {Uα} là họ open sets.  
Bù của ⋃Uα là ⋂(X \ Uα).  
Mỗi X \ Uα hữu hạn → giao của chúng ⊆ từng cái → hữu hạn ✓

**(T3) Finite intersections:**  
Cho U₁, ..., Uₙ open.  
Bù của U₁ ∩ ... ∩ Uₙ là (X \ U₁) ∪ ... ∪ (X \ Uₙ).  
Mỗi X \ Uᵢ hữu hạn → hợp hữu hạn các tập hữu hạn = hữu hạn ✓

**Ví dụ cụ thể:** X = ℤ
- Open sets: ∅, ℤ, ℤ \ {0}, ℤ \ {1, 2}, ℤ \ {-5}, ...
- Closed sets (bù của open): tập hữu hạn, ℤ

**Trực giác:** "Hầu hết" các điểm phải thuộc open set—chỉ có thể loại bỏ hữu hạn điểm.

**Kết nối:**  
- Nếu X hữu hạn: cofinite = discrete
- Nếu X vô hạn: cofinite ≠ discrete (thô hơn)

---

#### Example 5: Cocountable Topology

**Định nghĩa:**  
Trên tập X (uncountable), cocountable topology là:
$$
\tau_{\text{cocountable}} = \{U \subseteq X : X \setminus U \text{ đếm được hoặc } U = \emptyset\}
$$

**Ví dụ:** Trên ℝ
- Open sets: ∅, ℝ, ℝ \ ℚ, ℝ \ {x₁, x₂, ...}, ...
- Closed sets: tập đếm được, ℝ

**Trực giác:** Chỉ có thể loại bỏ "countably many" điểm.

---

### 3. Comparing Topologies (So sánh Topology)

**Định nghĩa (Coarser/Finer):**  
Cho 𝜏₁, 𝜏₂ là hai topologies trên X.

- 𝜏₁ **coarser** (thô hơn) than 𝜏₂ nếu 𝜏₁ ⊆ 𝜏₂  
- 𝜏₂ **finer** (mịn hơn) than 𝜏₁ nếu 𝜏₂ ⊇ 𝜏₁

**Trực giác:**
- **Coarser:** Ít open sets hơn → "phân biệt" ít hơn
- **Finer:** Nhiều open sets hơn → "phân biệt" nhiều hơn

**Ví dụ trên X = {a, b, c}:**

1. 𝜏₁ = {∅, X} (trivial)
2. 𝜏₂ = {∅, {a}, X}
3. 𝜏₃ = {∅, {a}, {b}, {a,b}, X}
4. 𝜏₄ = 𝒫(X) (discrete)

Thứ tự: 𝜏₁ ⊆ 𝜏₂ ⊆ 𝜏₃ ⊆ 𝜏₄

**Mối quan hệ:**
- **Trivial** là coarsest possible
- **Discrete** là finest possible
- Giữa chúng có vô số topologies khác!

**Comparison trên ℝ:**
$$
\tau_{\text{trivial}} \subseteq \tau_{\text{cofinite}} \subseteq \tau_{\text{cocountable}} \subseteq \tau_{\text{Euclidean}} \subseteq \tau_{\text{discrete}}
$$

---

### 4. Closed Sets (Tập Đóng)

**Định nghĩa:**  
Trong topological space (X, 𝜏), tập F ⊆ X là **closed** nếu:
$$
X \setminus F \in \tau
$$

**Nói cách khác:** F closed ⟺ bù của F open.

**Ví dụ trong ℝ (Euclidean topology):**
- **[a, b]** closed (vì ℝ \ [a,b] = (-∞,a) ∪ (b,∞) open)
- **{x}** closed (singleton)
- **ℕ** closed
- **ℚ** KHÔNG closed (vì ℝ \ ℚ không open)

**Tính chất của closed sets:**

**Dual Axioms:**
1. **∅ và X closed**
2. **Giao tùy ý** các closed sets là closed
3. **Hợp hữu hạn** các closed sets là closed

**Chứng minh (sketch):** Dùng De Morgan's laws và axioms của open sets.

**Chú ý:**  
- Một tập có thể vừa open vừa closed! (Ví dụ: ∅, X)
- Một tập có thể không open không closed! (Ví dụ: [0,1) trong ℝ)

![Open vs Closed sets](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Open_closed_sets.svg/500px-Open_closed_sets.svg.png)  
*Phân biệt open và closed sets - Nguồn concept*

---

### 5. Interior, Closure, Boundary

**Định nghĩa (Interior - Phần trong):**  
**Interior** của A ⊆ X là hợp của tất cả open sets chứa trong A:
$$
\text{int}(A) = A° = \bigcup \{U \in \tau : U \subseteq A\}
$$

**Trực giác:** Phần "hoàn toàn bên trong" A—các điểm có "không gian xung quanh" trong A.

**Ví dụ trong ℝ:**
- int([0,1]) = (0,1)
- int(ℚ) = ∅ (không có open interval nào trong ℚ)
- int((0,1)) = (0,1)

**Định nghĩa (Closure - Bao đóng):**  
**Closure** của A ⊆ X là giao của tất cả closed sets chứa A:
$$
\overline{A} = \text{cl}(A) = \bigcap \{F : F \text{ closed}, A \subseteq F\}
$$

**Trực giác:** Tập nhỏ nhất chứa A và "ranh giới" của A.

**Ví dụ trong ℝ:**
- cl((0,1)) = [0,1]
- cl(ℚ) = ℝ (ℚ "dense" trong ℝ)
- cl({1/n : n ∈ ℕ}) = {1/n : n ∈ ℕ} ∪ {0}

**Định nghĩa (Boundary - Biên):**  
**Boundary** của A là:
$$
\partial A = \overline{A} \setminus A°
$$

**Ví dụ trong ℝ:**
- ∂((0,1)) = {0, 1}
- ∂([0,1]) = {0, 1}
- ∂(ℚ) = ℝ (mọi số thực là boundary point của ℚ!)

**Tính chất quan trọng:**
1. int(A) ⊆ A ⊆ cl(A)
2. A open ⟺ A = int(A)
3. A closed ⟺ A = cl(A)
4. cl(A) = A ∪ ∂A

---

## 🧠 Fundamental Papers & References

### Historic Papers

1. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Định nghĩa đầu tiên của topological space (Hausdorff space)*

2. **Kazimierz Kuratowski** - *"Sur l'opération A̅ de l'Analysis Situs"* (1922)  
   *Định nghĩa topology qua closure operator*

3. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Intuitive foundations—trước khi formal topology ra đời*

4. **Pavel Alexandroff** - *"Über stetige Abbildungen kompakter Räume"* (1927)  
   *Đóng góp cho general topology theory*

### Textbooks

5. **James R. Munkres** - *Topology*, 2nd Ed., **§12–13: Topological Spaces**  
   *Standard reference, clear exposition*

6. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 2**  
   *Gentle introduction với nhiều examples*

7. **John L. Kelley** - *General Topology* (1955)  
   *Classic graduate text, comprehensive*

8. **Ryszard Engelking** - *General Topology* (1989)  
   *Encyclopedia của general topology*

---

## 🔗 Applications and Connections

### Computer Science - Digital Topology
**Image Processing:** Pixels trong ảnh digital có thể xem như discrete space. Định nghĩa "connectivity" và "boundary" của objects cần topology concepts!

**Ví dụ:** Trong ảnh 2D, hai pixels "adjacent" nếu chúng share edge (4-connectivity) hoặc corner (8-connectivity). Đây là các topologies khác nhau!

### Physics - Manifolds
**General Relativity:** Spacetime là 4-dimensional manifold—locally giống ℝ⁴ nhưng globally có thể "curved". Topology quyết định "shape" tổng thể của universe!

### Data Science - Topological Data Analysis (TDA)
**Persistent Homology:** Phân tích "shape" của data trong high-dimensional space. Topology giúp detect "holes", "clusters", và "structures" mà không cần metric cụ thể.

### Mathematics - Continuity
**Calculus Generalization:** Định nghĩa ε-δ của continuity chỉ là special case. Topological definition (preimage của open set là open) áp dụng cho mọi space!

### Real-World Example
**GPS Maps:** Khi zoom in/out trong bản đồ, "topology" của đường và khu vực không thay đổi (vẫn connected, vẫn có boundary), dù "metric" (scale) thay đổi. Đây là topological thinking!

---

## 🧩 Exercises

### Basic Understanding

1. **Verify Topology:**  
   Cho X = {a, b, c}. Các họ sau có phải là topology không? Tại sao?
   - a) 𝜏 = {∅, {a}, {a,b}, X}
   - b) 𝜏 = {∅, {a}, {b}, {a,b}, X}
   - c) 𝜏 = {∅, {a}, {b}, {c}, X}

2. **List Open Sets:**  
   X = {1, 2, 3, 4}, 𝜏 = cofinite topology.  
   Liệt kê tất cả open sets và closed sets.

3. **Topology on ℕ:**  
   Trên ℕ với cofinite topology, các tập sau open hay closed?
   - a) {1, 2, 3, 4, 5}
   - b) {n ∈ ℕ : n > 100}
   - c) {2, 4, 6, 8, ...} (số chẵn)

### Interior, Closure, Boundary

4. **Compute Interior:**  
   Trong ℝ với Euclidean topology, tìm int(A):
   - a) A = [0, 1] ∪ {2}
   - b) A = ℚ ∩ [0, 1]
   - c) A = {1/n : n ∈ ℕ}

5. **Compute Closure:**  
   Trong ℝ, tìm cl(A):
   - a) A = (0, 1) ∪ (2, 3)
   - b) A = {1/n : n ∈ ℕ}
   - c) A = ℤ

6. **Boundary Examples:**  
   Tìm ∂A trong ℝ:
   - a) A = (0, 1]
   - b) A = ℚ
   - c) A = Cantor set

### Comparing Topologies

7. **Order Topologies:**  
   Trên X = {a, b, c, d}, cho:
   - 𝜏₁ = {∅, X}
   - 𝜏₂ = {∅, {a}, X}
   - 𝜏₃ = {∅, {a}, {b,c}, {a,b,c}, X}
   
   Sắp xếp theo thứ tự coarser → finer.

8. **Euclidean vs Discrete:**  
   Chứng minh rằng Euclidean topology trên ℝ coarser than discrete topology.  
   Có tồn tại topology giữa chúng không?

### Advanced

9. **Construct Topology:**  
   Trên ℝ, định nghĩa: U open ⟺ U là hợp của các khoảng [a, b).  
   Chứng minh đây là topology. Nó có bằng Euclidean topology không?

10. **Indiscrete Continuity:**  
    Cho (X, 𝜏ₜᵣᵢᵥᵢₐₗ) và (Y, 𝜏) bất kỳ.  
    Chứng minh: Mọi hàm f: X → Y đều continuous.  
    (*Preview continuous functions*)

11. **Cofinite on ℝ:**  
    Trong ℝ với cofinite topology:
    - a) (0, 1) có open không?
    - b) ℝ \ ℕ có open không?
    - c) So sánh với Euclidean topology.

12. **Closure Properties:**  
    Chứng minh trong bất kỳ topological space:
    - a) cl(∅) = ∅
    - b) cl(A ∪ B) = cl(A) ∪ cl(B)
    - c) cl(cl(A)) = cl(A)

### Reflection

13. **Why Three Axioms?:**  
    Giải thích tại sao ba axioms (T1), (T2), (T3) là "tự nhiên" nếu muốn generalize khái niệm "open" từ metric spaces.

14. **Finite vs Infinite:**  
    Tại sao (T2) cho phép unions vô hạn nhưng (T3) chỉ intersections hữu hạn?  
    Cho ví dụ minh họa điều gì xảy ra nếu cho phép intersections vô hạn.

15. **Open vs Closed:**  
    Tại sao "closed" được định nghĩa qua "open" (không ngược lại)?  
    Có thể xây dựng topology bằng cách chọn "closed sets" trước không?

---

## 📚 Further Reading

- **Munkres, Topology:** §12–13 (Topological Spaces, Basis)
- **Morris, Topology Without Tears:** Chapter 2 (Topological Spaces)
- **Willard, General Topology:** Chapter 1 (Topological Spaces)
- **Armstrong, Basic Topology:** Chapter 2 (Topological Spaces)

---

## 🎓 Summary

Trong bài giảng này, chúng ta đã định nghĩa **topology**—khái niệm cốt lõi của toàn bộ môn học:

✅ **Topological Space:** (X, 𝜏) với 𝜏 thỏa mãn ba axioms  
✅ **Three Axioms:**
   - (T1): ∅, X ∈ 𝜏
   - (T2): Arbitrary unions of open sets are open
   - (T3): Finite intersections of open sets are open  
✅ **Basic Examples:** Trivial, discrete, Euclidean, cofinite, cocountable  
✅ **Comparing Topologies:** Coarser vs finer  
✅ **Closed Sets:** Dual concept, defined via complement  
✅ **Interior, Closure, Boundary:** Derived concepts từ open sets  

**Điểm chính:**
- Topology = cách nói về "structure" không cần metric
- Open sets là primitive concept—mọi thứ khác derived từ chúng
- Axioms đơn giản nhưng powerful: cho phép reasoning về continuity, convergence, etc.
- Có vô số topologies trên cùng một tập X!

**Philosophical insight:**  
Topology cho phép ta nói: "Cái cốc cà phê và cái bánh donut giống nhau" vì chúng có cùng **topological structure** (đều có một "hole"), dù metric khác nhau!

**Tiếp theo:** Trong Lecture 01.01, chúng ta sẽ học về **Basis và Subbasis**—cách xây dựng topology từ các "building blocks" đơn giản hơn, và cách so sánh các topologies hiệu quả.

---

*"Topology is the study of continuity in its most general form."* — Anonymous

🎯 **Hãy làm nhiều bài tập! Chỉ qua practice bạn mới "get used to" abstraction của topology.** 🎯

---

**Previous Chapter:** [Chapter 00: Foundations](/contents/vi/topology-chapter00/)  
**Next:** [Lecture 01.01: Basis and Subbasis for a Topology](/contents/vi/topology-chapter01/01_01_Basis_Subbasis/)

