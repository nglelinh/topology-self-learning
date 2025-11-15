---
layout: post
title: "Lecture 01.01: Basis and Subbasis for a Topology"
lang: vi
lang-ref: lecture-01-01
chapter: 1
lecture: 1
categories: [chapter01]
tags: [basis, subbasis, generated-topology, standard-basis]
description: "Basis và subbasis cho topology, cách sinh topology từ họ tập hợp đơn giản"
---

**Basis and Subbasis for a Topology**

---

## 📖 Tổng quan

Trong bài trước, chúng ta đã định nghĩa topology như một họ các open sets thỏa mãn ba axioms. Nhưng việc **kiểm tra** tất cả axioms cho một họ lớn các tập hợp có thể rất phức tạp.

Hãy tưởng tượng: Trong ℝ với Euclidean topology, có **vô số** open sets (mọi hợp của các khoảng mở). Làm sao chúng ta mô tả topology này một cách compact?

**Ý tưởng:** Giống như trong đại số tuyến tính, một không gian vector được sinh bởi một **basis**, một topology cũng có thể được sinh bởi một họ nhỏ hơn gọi là **basis**.

**Ví dụ:** Trong ℝ, thay vì liệt kê tất cả open sets, ta chỉ cần nói: "Tất cả các khoảng mở (a, b) là basis". Mọi open set khác đều là hợp của các khoảng này!

**Trong bài này:**
- **Basis for a topology**: Định nghĩa và tiêu chuẩn
- **Standard basis** cho ℝⁿ
- **Subbasis**: Họ nhỏ hơn nữa sinh ra topology
- **Generated topology**: Cách tạo topology từ basis/subbasis
- **Comparing bases**: Khi nào hai bases sinh cùng topology?

**Tại sao quan trọng?**
- Basis đơn giản hóa việc work với topology
- Nhiều topologies được định nghĩa qua basis
- Continuity dễ check hơn với basis
- Product topology được định nghĩa qua basis

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Building Blocks

Hãy nghĩ về **LEGO**. Bạn không cần vô số mảnh LEGO độc nhất để xây mọi thứ. Bạn chỉ cần một số "basic pieces" (cơ bản), và ghép chúng lại theo nhiều cách khác nhau để tạo ra structures phức tạp.

**Topology hoạt động tương tự!**

- **Basic pieces** = Basis elements (ví dụ: khoảng mở (a,b) trong ℝ)
- **Complex structures** = Arbitrary open sets (hợp của basis elements)
- **Construction rule** = "Take unions"

**Ví dụ cụ thể trong ℝ:**

Muốn mô tả open set U = (0, 1) ∪ (2, 5) ∪ (7, 10)?
- Không cần định nghĩa U riêng!
- Chỉ cần: U là **hợp** của ba basis elements: (0,1), (2,5), (7,10)

![LEGO analogy for basis](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Lego_Color_Bricks.jpg/400px-Lego_Color_Bricks.jpg)  
*LEGO blocks như basis elements - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Lego_Color_Bricks.jpg)*

---

## 📐 Định nghĩa Hình thức

### 1. Basis for a Topology

**Định nghĩa (Basis):**  
Cho (X, 𝜏) là topological space. Một họ ℬ ⊆ 𝜏 là **basis** cho 𝜏 nếu:

$$
\forall U \in \tau: U = \bigcup_{\alpha \in I} B_\alpha \quad \text{với } B_\alpha \in \mathcal{B}
$$

**Nói cách khác:** Mọi open set đều là hợp của các basis elements.

**Phát biểu tương đương:**  
ℬ là basis nếu với mọi x ∈ U ∈ 𝜏, tồn tại B ∈ ℬ sao cho x ∈ B ⊆ U.

**Trực giác:** Mọi điểm trong mọi open set đều có một basis element "bao quanh" nó.

**Ví dụ 1: Standard basis cho ℝ**

$$
\mathcal{B} = \{(a, b) : a, b \in \mathbb{R}, a < b\}
$$

(Tất cả các khoảng mở)

**Kiểm tra:** Mọi open set trong ℝ (Euclidean topology) đều là hợp của các khoảng mở ✓

**Ví dụ 2: Alternative basis cho ℝ**

$$
\mathcal{B}' = \{(a, b) : a, b \in \mathbb{Q}, a < b\}
$$

(Các khoảng mở với endpoints hữu tỉ)

**Surprise!** ℬ' cũng là basis cho Euclidean topology trên ℝ!

**Tại sao?** Vì ℚ dense trong ℝ: mọi khoảng (a,b) (a,b ∈ ℝ) đều là hợp của các khoảng (r,s) với r,s ∈ ℚ.

**Kết luận quan trọng:** Một topology có thể có **nhiều bases khác nhau**!

---

### 2. Basis Criterion (Tiêu chuẩn Basis)

**Làm sao biết** một họ tập hợp ℬ có thể là basis cho một topology nào đó?

**Định lý (Basis Criterion):**  
Họ ℬ các tập con của X là basis cho một topology trên X nếu và chỉ nếu:

**(B1)** ℬ phủ X:
$$
X = \bigcup_{B \in \mathcal{B}} B
$$

**(B2)** "Intersection property":
$$
\forall B_1, B_2 \in \mathcal{B}, \forall x \in B_1 \cap B_2: \exists B_3 \in \mathcal{B}: x \in B_3 \subseteq B_1 \cap B_2
$$

**Trực giác (B2):** Nếu hai basis elements giao nhau, giao đó phải chứa basis elements nhỏ hơn.

![Basis intersection property](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Basis_for_a_Topology_%28Illustration%29.svg/500px-Basis_for_a_Topology_%28Illustration%29.svg.png)  
*Intersection property của basis - Nguồn concept*

**Chứng minh (sketch):**

**Necessity (⇒):** Nếu ℬ là basis cho 𝜏:
- (B1): X ∈ 𝜏, nên X là hợp của các B ∈ ℬ ✓
- (B2): B₁ ∩ B₂ ∈ 𝜏 (vì 𝜏 closed under finite intersections), nên B₁ ∩ B₂ là hợp của các B₃ ∈ ℬ ✓

**Sufficiency (⇐):** Cho ℬ thỏa mãn (B1), (B2). Định nghĩa:
$$
\tau = \left\{U \subseteq X : U = \bigcup_{\alpha} B_\alpha, B_\alpha \in \mathcal{B}\right\}
$$

Cần chứng minh 𝜏 là topology. (Exercise!)

**Ví dụ ứng dụng:**

**Claim:** ℬ = {[a, b) : a < b} là basis cho một topology trên ℝ.

**Kiểm tra:**
- (B1): ℝ = ⋃ₙ [n, n+1) ✓
- (B2): [a, b) ∩ [c, d) = [max(a,c), min(b,d))  
  Nếu không rỗng, đây lại là một [e, f) ∈ ℬ ✓

**Kết luận:** ℬ sinh ra một topology (gọi là **lower limit topology** trên ℝ).

**Chú ý:** Đây là topology **khác** với Euclidean topology!

---

### 3. Comparing Bases

**Câu hỏi:** Khi nào hai bases sinh ra **cùng** topology?

**Định lý:**  
ℬ và ℬ' sinh cùng topology trên X ⟺ 
- ∀B ∈ ℬ, ∀x ∈ B: ∃B' ∈ ℬ': x ∈ B' ⊆ B
- ∀B' ∈ ℬ', ∀x ∈ B': ∃B ∈ ℬ: x ∈ B ⊆ B'

**Trực giác:** Mỗi basis element của ℬ "chứa" basis elements của ℬ', và ngược lại.

**Ví dụ:**

ℬ = {(a, b) : a,b ∈ ℝ}  
ℬ' = {(a, b) : a,b ∈ ℚ}

Chúng sinh cùng Euclidean topology trên ℝ!

**Ứng dụng quan trọng:**  
ℬ' **countable**, nên Euclidean topology trên ℝ có countable basis → ℝ là **second countable**!

---

### 4. Standard Basis for ℝⁿ

**Định nghĩa (Standard Basis for ℝⁿ):**

$$
\mathcal{B} = \{(a_1, b_1) \times (a_2, b_2) \times \cdots \times (a_n, b_n) : a_i < b_i\}
$$

(Tất cả các "open rectangles" / "open boxes")

**Trong ℝ²:**  
B = (a₁, b₁) × (a₂, b₂) = {(x, y) : a₁ < x < b₁, a₂ < y < b₂}

Đây là **hình chữ nhật** (không chứa biên)!

![Open rectangle in R2](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2d/Open_rectangle.svg/300px-Open_rectangle.svg.png)  
*Open rectangle là basis element trong ℝ² - Nguồn concept*

**Ví dụ open set trong ℝ²:**

Open disk B((0,0), 1) = {(x,y) : x² + y² < 1}

Đây **không phải** open rectangle! Nhưng nó là **hợp** của vô số open rectangles:

$$
B((0,0), 1) = \bigcup_{\text{rectangles } R \subseteq B((0,0),1)} R
$$

**Alternative basis cho ℝⁿ:**

$$
\mathcal{B}_{\text{balls}} = \{B(\mathbf{x}, r) : \mathbf{x} \in \mathbb{R}^n, r > 0\}
$$

(Tất cả các open balls)

**Định lý:** ℬ (rectangles) và ℬ_balls sinh **cùng** topology trên ℝⁿ (Euclidean topology)!

**Chứng minh (sketch):**
- Mỗi rectangle chứa một ball
- Mỗi ball chứa rectangles
- Apply comparison theorem ✓

---

### 5. Subbasis (Cơ sở Con)

**Đôi khi** basis vẫn còn "lớn". Ta muốn something nhỏ hơn nữa!

**Định nghĩa (Subbasis):**  
Một họ 𝒮 các tập con của X là **subbasis** cho topology 𝜏 nếu:

$$
\mathcal{B} = \left\{\bigcap_{i=1}^n S_i : S_i \in \mathcal{S}, n \in \mathbb{N}\right\}
$$

(Tất cả **giao hữu hạn** của các subbasis elements) là basis cho 𝜏.

**Nói cách khác:**  
- **Subbasis** → (take finite intersections) → **Basis** → (take arbitrary unions) → **Topology**

**Ví dụ 1: Standard subbasis cho ℝ**

$$
\mathcal{S} = \{(a, \infty) : a \in \mathbb{R}\} \cup \{(-\infty, b) : b \in \mathbb{R}\}
$$

(Tất cả "rays": tia phải và tia trái)

**Giao hữu hạn:**
- (a, ∞) ∩ (-∞, b) = (a, b) nếu a < b
- (a₁, ∞) ∩ (a₂, ∞) = (max(a₁, a₂), ∞)

**Kết quả:** Basis sinh ra = {tất cả khoảng mở} = Standard basis cho ℝ!

**Ví dụ 2: Product topology (preview)**

Cho (X, 𝜏_X) và (Y, 𝜏_Y). Trên X × Y, xét:

$$
\mathcal{S} = \{U \times Y : U \in \tau_X\} \cup \{X \times V : V \in \tau_Y\}
$$

Subbasis này sinh ra **product topology** trên X × Y!

**Tại sao dùng subbasis?**
- Đơn giản hơn basis trong một số constructions
- Order topology, product topology thường định nghĩa qua subbasis
- Elegance: compact description

---

### 6. Generated Topology

**Định lý (Existence of Generated Topology):**  
Cho 𝒮 là họ tùy ý các tập con của X. Tồn tại **duy nhất** topology 𝜏 trên X sao cho:
1. 𝒮 ⊆ 𝜏 (mọi S ∈ 𝒮 đều open)
2. 𝜏 là **coarsest** (thô nhất) topology thỏa mãn (1)

**Ký hiệu:** 𝜏 = ⟨𝒮⟩ (topology generated by 𝒮)

**Construction:**

$$
\tau = \left\{U \subseteq X : U = \bigcup_{\alpha} \left(\bigcap_{i=1}^{n_\alpha} S_{\alpha,i}\right), S_{\alpha,i} \in \mathcal{S}\right\}
$$

**Nói bằng lời:**
1. Take finite intersections of subbasis elements → basis
2. Take arbitrary unions of basis elements → topology

**Ví dụ:**

𝒮 = {(0, 1), (0.5, 1.5)} trên ℝ.

Generated topology chứa:
- (0, 1), (0.5, 1.5) (subbasis)
- (0, 1) ∩ (0.5, 1.5) = (0.5, 1) (basis)
- Mọi hợp của các tập trên
- ...

**Chú ý:** Generated topology thường **không bằng** Euclidean topology!

---

### 7. Neighborhood Basis

**Định nghĩa (Neighborhood):**  
Tập N ⊆ X là **neighborhood** của điểm x nếu tồn tại U ∈ 𝜏 với x ∈ U ⊆ N.

**Trực giác:** N chứa một open set xung quanh x.

**Định nghĩa (Neighborhood Basis):**  
Họ ℬₓ các neighborhoods của x là **neighborhood basis** tại x nếu:

$$
\forall N \text{ neighborhood của } x: \exists B \in \mathcal{B}_x: B \subseteq N
$$

**Ví dụ trong ℝ:**

$$
\mathcal{B}_x = \{(x - 1/n, x + 1/n) : n \in \mathbb{N}\}
$$

là neighborhood basis tại x.

**Ứng dụng:**  
- **Convergence:** xₙ → x ⟺ với mọi B ∈ ℬₓ, tồn tại N sao cho ∀n ≥ N: xₙ ∈ B
- **Continuity:** f continuous tại x ⟺ với mọi neighborhood của f(x), preimage chứa neighborhood của x

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Định nghĩa neighborhood bases*

2. **Pavel Alexandroff & Heinz Hopf** - *"Topologie I"* (1935)  
   *Systematic treatment of bases and subbases*

3. **Nicolas Bourbaki** - *"Éléments de mathématique: Topologie générale"* (1940)  
   *Modern axiomatic approach, bases and filters*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§13: Basis for a Topology**  
   *Clear exposition với nhiều examples*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 2, §2.2**  
   *Gentle introduction to bases*

6. **Stephen Willard** - *General Topology*, **Chapter 2**  
   *Comprehensive treatment*

7. **John L. Kelley** - *General Topology*, **Chapter 2**  
   *Nets và filters approach*

---

## 🔗 Applications and Connections

### Computer Science - Data Structures
**Spatial Indexing:** Trong databases, "R-trees" sử dụng "bounding rectangles" (tương tự basis elements trong ℝⁿ) để organize spatial data hiệu quả.

**Ví dụ:** Google Maps sử dụng spatial indexing với basis-like structures để quickly find nearby locations.

### Analysis - Topological Vector Spaces
**Normed Spaces:** Trong functional analysis, topology thường defined qua basis của open balls. Convergence, continuity đều check qua basis elements.

### Differential Geometry - Charts and Atlases
**Manifolds:** Được định nghĩa locally giống ℝⁿ. "Charts" act như basis elements—cover space và có "overlap conditions" (tương tự intersection property).

### Physics - Phase Space
**Classical Mechanics:** Phase space có topology natural. Basis elements = "small regions" trong position-momentum space. Evolution preserves topology.

### Real-World Example
**Weather Maps:** Các vùng "high pressure", "low pressure" có thể xem như basis elements. Union của chúng mô tả entire weather pattern (topology của atmospheric conditions).

---

## 🧩 Exercises

### Understanding Bases

1. **Verify Basis:**  
   Cho X = {a, b, c, d}. Các họ sau có phải là basis cho một topology không?
   - a) ℬ = {% raw %}{{a}, {b}, {c,d}, X}{% endraw %}
   - b) ℬ = {% raw %}{{a,b}, {b,c}, {c,d}}{% endraw %}
   - c) ℬ = {% raw %}{{a}, {a,b}, {a,b,c}, X}{% endraw %}

2. **Generate Topology:**  
   X = {1, 2, 3}, ℬ = {% raw %}{{1}, {2,3}}{% endraw %}.  
   Liệt kê tất cả open sets trong topology sinh bởi ℬ.

3. **Standard Basis:**  
   Chứng minh rằng ℬ = {(a, b) : a,b ∈ ℝ} thỏa mãn basis criterion (B1) và (B2).

### Comparing Bases

4. **Same Topology?**  
   Trên ℝ, xét hai bases:
   - ℬ₁ = {(a, b) : a < b}
   - ℬ₂ = {[a, b) : a < b}
   
   Chúng có sinh cùng topology không? Tại sao?

5. **Rational Endpoints:**  
   Chứng minh rằng ℬ = {(r, s) : r,s ∈ ℚ, r < s} là basis cho Euclidean topology trên ℝ.  
   (*Hint:* Sử dụng density của ℚ)

6. **Countable Basis:**  
   Chứng minh rằng ℝ với Euclidean topology có countable basis.  
   Điều này gợi ý gì về "size" của topology?

### ℝⁿ and Products

7. **Open Rectangles:**  
   Trong ℝ², vẽ các basis elements:
   - a) (0, 1) × (0, 1)
   - b) (-1, 2) × (0, 3)
   - c) Giao của (a) và (b)
   
   Giao có phải là basis element không?

8. **Open Disk:**  
   Open disk B((0,0), 1) trong ℝ² **không phải** open rectangle.  
   Chứng minh rằng nó **là** open set bằng cách biểu diễn như hợp của open rectangles.

9. **Different Metrics:**  
   Trong ℝ² với Manhattan metric d₁(x,y) = |x₁-y₁| + |x₂-y₂|:
   - a) Vẽ "open ball" B((0,0), 1) trong metric này
   - b) Nó có phải là open rectangle không?
   - c) Topology induced có bằng Euclidean topology không?

### Subbases

10. **Ray Subbasis:**  
    Trên ℝ, cho 𝒮 = {(a, ∞) : a ∈ ℝ} ∪ {(-∞, b) : b ∈ ℝ}.  
    - a) Chứng minh 𝒮 là subbasis
    - b) Mô tả basis sinh từ 𝒮
    - c) So sánh với standard basis

11. **Minimal Subbasis:**  
    X = {a, b, c}, 𝒮 = {% raw %}{{a,b}, {b,c}}{% endraw %}.  
    - a) Tìm basis sinh từ 𝒮
    - b) Liệt kê tất cả open sets trong topology sinh ra
    - c) Topology này có tên gọi đặc biệt không?

12. **Product Preview:**  
    Trên ℝ × ℝ, xét subbasis:  
    𝒮 = {(a,b) × ℝ : a<b} ∪ {ℝ × (c,d) : c<d}
    
    Chứng minh rằng basis sinh ra = {(a,b) × (c,d)} = standard basis cho ℝ².

### Advanced

13. **Lower Limit Topology:**  
    Topology sinh bởi ℬ = {[a, b) : a<b} trên ℝ gọi là "lower limit topology" 𝜏_ℓ.
    - a) Chứng minh [0, 1) open trong 𝜏_ℓ
    - b) (0, 1) có open trong 𝜏_ℓ không?
    - c) So sánh 𝜏_ℓ với Euclidean topology 𝜏_E

14. **Finer Topology:**  
    Chứng minh: Nếu ℬ₁ ⊆ ℬ₂ (cả hai đều bases), thì topology sinh bởi ℬ₂ finer than topology sinh bởi ℬ₁.

15. **Neighborhood Basis:**  
    Trong metric space (X, d), chứng minh rằng:
    $$
    \mathcal{B}_x = \{B(x, 1/n) : n \in \mathbb{N}\}
    $$
    là neighborhood basis tại x.

16. **Characterize Topology:**  
    Chứng minh: Topology 𝜏 hoàn toàn determined bởi neighborhood bases tại mọi điểm.  
    (*Hint:* U open ⟺ U là neighborhood của mọi x ∈ U)

### Reflection

17. **Why Finite Intersections?**  
    Trong subbasis definition, tại sao chỉ lấy **finite** intersections?  
    Điều gì xảy ra nếu allow infinite intersections?

18. **Bases vs Spanning Sets:**  
    So sánh "basis" trong topology với "basis" trong linear algebra.  
    - Điểm giống: cả hai "span" entire structure
    - Điểm khác: linear independence có tương đương gì không?

19. **Minimal Basis:**  
    Có tồn tại "minimal basis" (basis nhỏ nhất) cho một topology không?  
    So sánh với linear algebra.

---

## 📚 Further Reading

- **Munkres, Topology:** §13 (Basis for a Topology), §15 (Product Topology)
- **Morris, Topology Without Tears:** Chapter 2.2–2.3 (Bases)
- **Willard, General Topology:** Chapter 2 (Bases and Subbases)
- **Dugundji, Topology:** Chapter II.2 (Bases and Subbases)

---

## 🎓 Summary

Trong bài giảng này, chúng ta học cách **simplify** việc work với topologies:

✅ **Basis:** Họ tập hợp mà mọi open set là hợp của chúng  
✅ **Basis Criterion:** (B1) phủ X, (B2) intersection property  
✅ **Standard Bases:** ℝⁿ có basis từ open rectangles hoặc open balls  
✅ **Comparing Bases:** Khi nào hai bases sinh cùng topology  
✅ **Subbasis:** Họ nhỏ hơn, sinh basis qua finite intersections  
✅ **Generated Topology:** Từ subbasis → basis → topology  
✅ **Neighborhood Basis:** Local version của basis concept  

**Điểm chính:**
- Basis = "building blocks" của topology
- Một topology có thể có nhiều bases khác nhau
- Basis giúp check continuity, convergence dễ hơn
- Subbasis cho elegant constructions (product, order topology)
- ℝⁿ có countable basis → second countable

**Practical wisdom:**
- Khi định nghĩa topology: dùng basis (đơn giản hơn liệt kê tất cả open sets)
- Khi so sánh topologies: so sánh bases
- Khi chứng minh continuous: đủ check trên basis elements

**Tiếp theo:** Trong Lecture 01.02, chúng ta sẽ học về **Closed Sets, Closure, and Interior**—các khái niệm dual của open sets, và các operators quan trọng nhất trong topology.

---

*"A basis is to topology what a basis is to a vector space—it spans the structure."* — Topology wisdom

🎯 **Practice với nhiều bases khác nhau! Đây là key để mastery.** 🎯

---

**Previous:** [Lecture 01.00: Definition of Topology](/contents/vi/topology-chapter01/01_00_Definition_Topology_Basic_Examples/)  
**Next:** [Lecture 01.02: Closed Sets, Closure, and Interior](/contents/vi/topology-chapter01/01_02_Closed_Sets_Closure_Interior/)

