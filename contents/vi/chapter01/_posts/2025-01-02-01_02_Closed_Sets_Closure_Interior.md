---
layout: post
title: "Lecture 01.02: Closed Sets, Closure, and Interior"
lang: vi
lang-ref: lecture-01-02
chapter: 1
lecture: 2
categories: [chapter01]
tags: [closed-sets, closure, interior, boundary, limit-points]
description: "Tập đóng, closure operator, interior, boundary, và limit points"
---

**Closed Sets, Closure, and Interior**

---

## 📖 Tổng quan

Trong hai bài trước, chúng ta tập trung vào **open sets**—khái niệm primitive của topology. Nhưng toán học thường có tính **duality** (đối ngẫu): với mỗi khái niệm, có một "dual concept" equally important.

**Open sets** have natural dual: **closed sets**. From this duality emerge powerful **operators** transforming sets: **Interior (int)** captures "completely inside" part, **Closure (cl)** adds "boundary" to set, và **Boundary (∂)** marks "border" between inside and outside.

These operators are **most important tools** trong entire topology! They appear everywhere. **Density** gets defined via closure: A dense exactly when cl(A) = X, meaning A's closure fills entire space. **Continuity** has elegant characterization: f continuous if and only if preimages of closed sets are closed. **Point classification** (interior points, boundary points, limit points) relies completely on these operators, providing vocabulary for discussing "position" in abstract spaces.

**Trong bài này** we systematically develop dual theory. **Closed sets** với their axioms mirror open set axioms beautifully. **Closure operator** cl(·) emerges with rich properties and geometric intuition—it "completes" a set by adding limit points. **Interior operator** int(·) reveals itself as perfect dual của closure, stripping away boundary. **Boundary** ∂ precisely captures "border" between inside và outside. **Limit points** versus **isolated points** dichotomy classifies how points relate to their sets. **Dense sets** concept (like ℚ trong ℝ) captures "everywhere presence" through closure.

**Tại sao absolutely essential?** Closure and interior provide language for **approximation**—fundamental idea threading through analysis and topology. **Limit points** form foundation for convergence theory, enabling us to discuss "approaching" without explicit sequences. **Dense sets** are key (ℚ dense trong ℝ means rationals approximate any real), appearing trong separability, Baire category theorem, và Stone-Weierstrass. These operators **define** many topological properties: regularity, normality, separability all formulated using closure and interior.

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Ranh giới

Hãy tưởng tượng một **vùng đất** trên bản đồ. Vùng này có:
- **Interior** (phần trong): Tất cả điểm "hoàn toàn bên trong"—đi một chút mọi hướng vẫn ở trong vùng
- **Boundary** (biên giới): Đường viền—một bước ra ngoài, một bước vào trong
- **Exterior** (phần ngoài): Tất cả điểm hoàn toàn bên ngoài
- **Closure** (bao đóng): Interior + Boundary = "vùng đất cộng với biên"

![Interior, Boundary, Exterior](https://upload.wikimedia.org/wikipedia/commons/thumb/0/04/Interior_Boundary_Exterior.svg/500px-Interior_Boundary_Exterior.svg.png)  
*Interior (xanh), Boundary (đỏ), Exterior (trắng) - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Interior_Boundary_Exterior.svg)*

**Ví dụ cụ thể trong ℝ:**

Xét A = [0, 1) (nửa khoảng)

- **Interior:** int(A) = (0, 1)  
  *Lý do:* Mọi điểm trong (0, 1) có một khoảng nhỏ xung quanh vẫn trong A.  
  Nhưng 0 không (mọi khoảng chứa 0 đều có điểm âm ∉ A).

- **Boundary:** ∂A = {0, 1}  
  *Lý do:* 0 và 1 là "điểm biên"—mọi neighborhood chứa cả điểm trong và ngoài A.

- **Closure:** cl(A) = [0, 1]  
  *Lý do:* Thêm điểm biên 1 vào A.

**Observation quan trọng:** Notice beautiful inclusion chain: int(A) ⊆ A ⊆ cl(A). Interior is "largest open set inside A", A itself sits in middle, và closure is "smallest closed set containing A".
- A open ⟺ A = int(A)
- A closed ⟺ A = cl(A)
- ∂A = cl(A) \ int(A)

---

## 📐 Định nghĩa Hình thức

### 1. Closed Sets (Tập Đóng)

**Định nghĩa (Closed Set):**  
Trong topological space (X, 𝜏), tập F ⊆ X là **closed** nếu complement của nó open:

$$
F \text{ closed} \iff X \setminus F \in \tau
$$

**Ví dụ trong ℝ (Euclidean topology):**
- **[a, b]** closed (complement = (-∞,a) ∪ (b,∞) open)
- **{x}** (singleton) closed (complement = ℝ \ {x} open)
- **ℕ** closed
- **Cantor set** closed

**Dual Axioms for Closed Sets:**

**Định lý:** Họ tất cả closed sets thỏa mãn:

**(C1)** ∅ và X closed

**(C2)** **Giao tùy ý** closed sets là closed:
$$
\{F_\alpha\}_{\alpha \in I} \text{ closed} \implies \bigcap_{\alpha \in I} F_\alpha \text{ closed}
$$

**(C3)** **Hợp hữu hạn** closed sets là closed:
$$
F_1, \ldots, F_n \text{ closed} \implies F_1 \cup \cdots \cup F_n \text{ closed}
$$

**Chứng minh:** Dùng De Morgan's laws:
- X \ (⋂Fα) = ⋃(X \ Fα) ∈ 𝜏 (arbitrary unions of open sets)
- X \ (F₁ ∪ ... ∪ Fₙ) = (X\F₁) ∩ ... ∩ (X\Fₙ) ∈ 𝜏 (finite intersections) ∎

**Comparison với Open Sets:**

| Open Sets | Closed Sets |
|-----------|-------------|
| ∅, X open | ∅, X closed |
| Arbitrary unions | Arbitrary **intersections** |
| Finite intersections | Finite **unions** |

**Chú ý quan trọng:**
- "Not open" ≠ "closed"
- "Not closed" ≠ "open"
- Một tập có thể vừa open vừa closed: **clopen**
- Một tập có thể không open không closed: ví dụ [0,1) trong ℝ

---

### 2. Closure Operator (Toán tử Bao đóng)

**Định nghĩa (Closure):**  
Cho A ⊆ X. **Closure** của A là giao của tất cả closed sets chứa A:

$$
\overline{A} = \text{cl}(A) = \bigcap \{F : F \text{ closed}, A \subseteq F\}
$$

**Trực giác:** cl(A) là **smallest closed set** containing A.

**Ví dụ trong ℝ:**
- cl((0,1)) = [0,1]
- cl([0,1]) = [0,1] (đã closed)
- cl(ℚ) = ℝ (vì ℚ dense)
- cl({1/n : n ∈ ℕ}) = {1/n} ∪ {0}

**Định lý (Properties of Closure):**

Closure operator thỏa mãn bốn **Kuratowski closure axioms**:

**(K1) Extensivity:** 
$$
A \subseteq \overline{A}
$$

**(K2) Idempotence:**
$$
\overline{\overline{A}} = \overline{A}
$$

**(K3) Preservation of unions:**
$$
\overline{A \cup B} = \overline{A} \cup \overline{B}
$$

**(K4) Normality:**
$$
\overline{\emptyset} = \emptyset
$$

**Chứng minh:**

**(K1):** cl(A) là closed set chứa A, nên A ⊆ cl(A) ✓

**(K2):** cl(A) closed, nên cl(cl(A)) = cl(A) ✓

**(K3):**  
- cl(A) ∪ cl(B) closed (finite union of closed sets)
- A ∪ B ⊆ cl(A) ∪ cl(B)
- cl(A ∪ B) ⊆ cl(A) ∪ cl(B) (minimality)
- Ngược lại: A ⊆ A ∪ B ⇒ cl(A) ⊆ cl(A ∪ B), tương tự cl(B) ⊆ cl(A ∪ B)
- ⇒ cl(A) ∪ cl(B) ⊆ cl(A ∪ B) ✓

**(K4):** Trivial: ∅ closed, nên cl(∅) = ∅ ✓

**Fact kỳ diệu (Kuratowski):**  
Có thể **định nghĩa topology** bằng một operator cl: 𝒫(X) → 𝒫(X) thỏa mãn (K1)–(K4)!

Sau đó: F closed ⟺ F = cl(F).

---

### 3. Limit Points (Điểm Tụ)

**Định nghĩa (Limit Point):**  
Điểm x ∈ X là **limit point** (accumulation point) của A ⊆ X nếu:

$$
\forall U \in \tau, x \in U: (U \cap A) \setminus \{x\} \neq \emptyset
$$

**Nói bằng lời:** Mọi neighborhood của x chứa ít nhất một điểm của A **khác x**.

**Trực giác:** x là "điểm tụ" của A = điểm có các điểm của A "tụ lại gần" nó.

**Ví dụ trong ℝ:**

1. **A = (0, 1)**  
   - Mọi x ∈ [0, 1] là limit points của A
   - Ví dụ: 0 là limit point (vì mọi (0-ε, 0+ε) chứa điểm của (0,1))
   - Điểm ngoài [0,1] không phải limit points

2. **A = {1/n : n ∈ ℕ}**  
   - 0 là limit point (unique!)
   - Mọi 1/n **không phải** limit points (có neighborhood chỉ chứa chính nó)

![Limit points visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7a/Limit_point_illustration.svg/400px-Limit_point_illustration.svg.png)  
*Limit points của một tập - Nguồn concept*

**Định nghĩa (Isolated Point):**  
Điểm x ∈ A là **isolated point** nếu nó **không phải** limit point của A.

Tương đương: ∃ neighborhood U của x sao cho U ∩ A = {x}.

**Ví dụ:**
- Trong A = {1/n : n ∈ ℕ}, mỗi 1/n là isolated
- Trong A = (0,1), không có isolated points
- Trong A = {0} ∪ (1,2), điểm 0 isolated

**Ký hiệu:** A' = tập tất cả limit points của A (derived set)

**Định lý (Closure via Limit Points):**
$$
\overline{A} = A \cup A'
$$

**Trực giác:** Closure = điểm gốc + điểm tụ.

**Chứng minh (sketch):**

**(⊆):** Cho x ∈ cl(A). Nếu x ∉ A, cần chứng minh x ∈ A'.  
Giả sử (phản chứng) x không phải limit point.  
Tồn tại U ∋ x với U ∩ A = ∅ hoặc {x}.  
Nếu U ∩ A = ∅: A ⊆ X \ U (closed), nên cl(A) ⊆ X \ U ⇒ x ∉ cl(A), mâu thuẫn.

**(⊇):** A ⊆ cl(A) rõ ràng. Cần A' ⊆ cl(A).  
Cho x ∈ A'. Mọi closed F ⊇ A phải chứa x (vì nếu x ∉ F, thì U = X \ F là neighborhood của x với U ∩ A = ∅, mâu thuẫn với x ∈ A'). ∎

---

### 4. Interior Operator (Toán tử Phần trong)

**Định nghĩa (Interior):**  
**Interior** của A là hợp của tất cả open sets chứa trong A:

$$
A° = \text{int}(A) = \bigcup \{U \in \tau : U \subseteq A\}
$$

**Trực giác:** int(A) là **largest open set** contained in A.

**Ví dụ trong ℝ:**
- int([0,1]) = (0,1)
- int((0,1)) = (0,1) (đã open)
- int(ℚ) = ∅ (không có open interval trong ℚ)
- int({x}) = ∅ (singleton không chứa open set nào)

**Định lý (Properties of Interior):**

**(I1) Restrictivity:**
$$
\text{int}(A) \subseteq A
$$

**(I2) Idempotence:**
$$
\text{int}(\text{int}(A)) = \text{int}(A)
$$

**(I3) Preservation of intersections:**
$$
\text{int}(A \cap B) = \text{int}(A) \cap \text{int}(B)
$$

**(I4) Normality:**
$$
\text{int}(X) = X
$$

**Dual Relationship với Closure:**

**Định lý:**
$$
\text{int}(A) = X \setminus \overline{X \setminus A}
$$

$$
\overline{A} = X \setminus \text{int}(X \setminus A)
$$

**Chứng minh:**  
int(A) = largest open ⊆ A  
     = X \ (smallest closed ⊇ (X \ A))  
     = X \ cl(X \ A) ✓

**Trực giác:** Interior và closure là **dual operators**.

---

### 5. Boundary (Biên)

**Định nghĩa (Boundary):**  
**Boundary** (frontier) của A là:

$$
\partial A = \overline{A} \setminus \text{int}(A)
$$

**Phát biểu tương đương:**
$$
\partial A = \overline{A} \cap \overline{X \setminus A}
$$

**Trực giác:** Điểm x ∈ ∂A nếu:
- Mọi neighborhood của x chứa cả điểm trong A và điểm ngoài A

**Ví dụ trong ℝ:**
- ∂([0,1]) = {0, 1}
- ∂((0,1)) = {0, 1}
- ∂(ℚ) = ℝ (mọi số thực là boundary!)
- ∂(∅) = ∅

**Tính chất:**

**Định lý (Partition of Space):**  
Với mọi A ⊆ X:
$$
X = \text{int}(A) \sqcup \partial A \sqcup \text{int}(X \setminus A)
$$

(Disjoint union - phân hoạch không gian thành ba phần)

**Chứng minh:** Exercise sử dụng definitions.

**Định lý (Boundary Properties):**
1. ∂A = ∂(X \ A) (boundary đối xứng)
2. ∂A = ∅ ⟺ A vừa open vừa closed (clopen)
3. A closed ⟺ ∂A ⊆ A
4. A open ⟺ ∂A ⊆ (X \ A)

---

### 6. Dense Sets (Tập Trù mật)

**Định nghĩa (Dense):**  
Tập A ⊆ X là **dense** trong X nếu:

$$
\overline{A} = X
$$

**Phát biểu tương đương:**
- Mọi non-empty open set giao với A
- Mọi điểm x ∈ X là limit point của A hoặc thuộc A

**Ví dụ:**
- **ℚ dense trong ℝ:** Mọi khoảng mở chứa số hữu tỉ
- **ℝ \ ℚ (irrational) dense trong ℝ:** Mọi khoảng mở chứa số vô tỉ
- **(0,1) dense trong [0,1]:** cl((0,1)) = [0,1]
- **{0,1} không dense trong ℝ:** cl({0,1}) = {0,1} ≠ ℝ

![Dense set illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/Dense_set_rationals.svg/400px-Dense_set_rationals.svg.png)  
*ℚ dense trong ℝ - Nguồn concept*

**Định nghĩa (Nowhere Dense):**  
A là **nowhere dense** nếu int(cl(A)) = ∅.

**Trực giác:** A "thin" đến mức closure của nó cũng không chứa open set nào.

**Ví dụ:**
- **ℕ nowhere dense trong ℝ:** int(cl(ℕ)) = int(ℕ) = ∅
- **Cantor set nowhere dense:** int(Cantor) = ∅
- **{1/n : n ∈ ℕ} nowhere dense**

**Ứng dụng quan trọng:**

**Định lý Baire (Preview):**  
Trong complete metric space, hợp countable các nowhere dense sets có interior rỗng.

**Hệ quả:** ℝ không thể viết như hợp countable các nowhere dense sets.  
→ ℝ "large" theo nghĩa topology!

---

### 7. Characterizations of Closure

**Định lý (Equivalent Definitions):**  
Các phát biểu sau **tương đương**:

1. x ∈ cl(A)
2. Mọi neighborhood của x giao với A
3. Mọi open set chứa x giao với A
4. x ∈ A hoặc x là limit point của A

**Chứng minh:**

**(1 ⇒ 2):** Giả sử (phản chứng) ∃ neighborhood N của x với N ∩ A = ∅.  
Tồn tại U ∈ 𝜏 với x ∈ U ⊆ N.  
Khi đó X \ U closed, A ⊆ X \ U, nên cl(A) ⊆ X \ U.  
Nhưng x ∈ cl(A) và x ∈ U → mâu thuẫn!

**(2 ⇒ 3):** Trivial (mọi open set chứa x là neighborhood).

**(3 ⇒ 4):** Nếu x ∈ A, done. Nếu x ∉ A:  
Mọi U ∋ x có U ∩ A ≠ ∅.  
Vì x ∉ A, nên U ∩ A chứa điểm ≠ x.  
→ x là limit point.

**(4 ⇒ 1):** cl(A) = A ∪ A', nên x ∈ cl(A). ∎

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Kazimierz Kuratowski** - *"Sur l'opération Ā de l'Analysis Situs"* (1922)  
   *Định nghĩa topology qua closure operator (Kuratowski closure axioms)*

2. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Limit points và derived sets*

3. **René-Louis Baire** - *"Sur les fonctions de variables réelles"* (1899)  
   *Baire category theorem, nowhere dense sets*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§17: Closed Sets and Limit Points**  
   *Standard reference*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 3**  
   *Clear exposition với examples*

6. **John L. Kelley** - *General Topology*, **Chapter 2**  
   *Comprehensive treatment*

7. **Stephen Willard** - *General Topology*, **Chapter 2**  
   *Rigorous approach*

---

## 🔗 Applications and Connections

### Analysis - Completeness
**Cauchy Sequences:** Trong metric space, sequence hội tụ ⟺ limit point của {xₙ} exists và unique. Closure operations capture convergence behavior.

### Numerical Analysis - Approximation
**Rational Approximation:** ℚ dense trong ℝ có nghĩa: mọi số thực có thể xấp xỉ tùy ý gần bởi số hữu tỉ. Computers dùng floating-point (subset của ℚ) để approximate reals.

### Data Science - Clustering
**DBSCAN Algorithm:** Sử dụng khái niệm "density" (tương tự dense sets) để cluster data points. Core points = interior, border points = boundary.

### Computer Graphics - Edge Detection
**Boundary Detection:** Trong image processing, detecting edges = tìm ∂(region). Algorithms như Canny edge detector dựa trên topology concepts.

### Real-World Example
**Coastline Paradox:** Độ dài coastline phụ thuộc vào measurement resolution. Topologically, coastline = boundary between land và sea, nhưng "fractional dimension" (fractal geometry) enters!

---

## 🧩 Exercises

### Closed Sets

1. **Verify Closed:**  
   Trong ℝ (Euclidean topology), các tập sau closed không?
   - a) [0, 1]
   - b) {1/n : n ∈ ℕ}
   - c) ℚ
   - d) {x ∈ ℝ : sin(x) = 0}

2. **Clopen Sets:**  
   Tìm tất cả clopen sets (vừa open vừa closed) trong:
   - a) ℝ với Euclidean topology
   - b) Discrete topology
   - c) Trivial topology

3. **Arbitrary Intersections:**  
   Cho Fₙ = [1/n, 1] trong ℝ (n ∈ ℕ).  
   - a) Mỗi Fₙ có closed không?
   - b) Tính ⋂ₙ₌₁^∞ Fₙ
   - c) Giao này có closed không?

### Closure

4. **Compute Closure:**  
   Trong ℝ, tìm cl(A):
   - a) A = (0, 1) ∪ {2}
   - b) A = {1 + 1/n : n ∈ ℕ}
   - c) A = {x ∈ ℚ : 0 < x < √2}
   - d) A = ℤ

5. **Kuratowski Axioms:**  
   Chứng minh rằng cl(A ∩ B) ⊆ cl(A) ∩ cl(B).  
   Cho ví dụ khi bất đẳng thức nghiêm ngặt.

6. **Closure in Discrete:**  
   Trong discrete topology, tính cl(A) với A tùy ý.

### Interior

7. **Compute Interior:**  
   Trong ℝ, tìm int(A):
   - a) A = [0, 1]
   - b) A = ℚ
   - c) A = [0, 1] ∪ [2, 3]
   - d) A = {1/n : n ∈ ℕ}

8. **Interior vs Closure:**  
   Chứng minh: int(A) = X \ cl(X \ A).

9. **Open Iff Interior:**  
   Chứng minh: A open ⟺ A = int(A).

### Limit Points

10. **Find Limit Points:**  
    Trong ℝ, tìm tập limit points A' của:
    - a) A = (0, 1)
    - b) A = {1/n : n ∈ ℕ}
    - c) A = ℚ
    - d) A = Cantor set

11. **Isolated Points:**  
    Tập A ⊆ ℝ với mọi điểm là isolated (không có limit points).  
    - a) Cho ví dụ A infinite
    - b) A có thể uncountable không?

12. **Closure Formula:**  
    Chứng minh: cl(A) = A ∪ A' (A' = limit points).

### Boundary

13. **Compute Boundary:**  
    Trong ℝ, tìm ∂A:
    - a) A = [0, 1)
    - b) A = ℚ
    - c) A = {0} ∪ (1, 2)
    - d) A = Cantor set

14. **Boundary Properties:**  
    Chứng minh:
    - a) ∂A = ∂(X \ A)
    - b) ∂A closed
    - c) ∂(∂A) ⊆ ∂A

15. **Partition:**  
    Chứng minh: X = int(A) ⊔ ∂A ⊔ int(X \ A) (disjoint union).

### Dense Sets

16. **Verify Dense:**  
    Chứng minh ℚ dense trong ℝ.  
    (*Hint:* Mọi (a,b) chứa số hữu tỉ—Archimedean property)

17. **Irrationals Dense:**  
    Chứng minh ℝ \ ℚ (irrational) cũng dense trong ℝ.

18. **Nowhere Dense:**  
    Chứng minh ℕ nowhere dense trong ℝ.

### Advanced

19. **Cantor Set:**  
    Cantor set C có tính chất:
    - closed: ✓
    - nowhere dense: ✓
    - uncountable: ✓
    
    Chứng minh rằng ∂C = C (boundary = chính nó).

20. **Baire Category:**  
    ℝ = ℚ ∪ (ℝ \ ℚ).  
    - ℚ có dense
    - ℝ \ ℚ có dense
    
    Có thể viết ℝ = A ∪ B với A, B đều **không** dense không?

21. **Separation:**  
    Cho A, B ⊆ X disjoint với cl(A) ∩ B = ∅ và A ∩ cl(B) = ∅.  
    Chứng minh tồn tại U, V ∈ 𝜏 disjoint với A ⊆ U, B ⊆ V.  
    (*Preview:* Normal spaces)

### Reflection

22. **Dual Concepts:**  
    So sánh duality:
    - Open ⟷ Closed
    - Interior ⟷ Closure
    - Union ⟷ Intersection
    
    Giải thích tại sao duality này "natural".

23. **Topology from Closure:**  
    Nếu operator cl: 𝒫(X) → 𝒫(X) thỏa mãn Kuratowski axioms (K1)–(K4), có thể reconstruct topology không? Làm thế nào?

---

## 📚 Further Reading

- **Munkres, Topology:** §17 (Closed Sets and Limit Points), §18 (Continuous Functions)
- **Morris, Topology Without Tears:** Chapter 3 (Limit Points)
- **Willard, General Topology:** Chapter 2 (Convergence and Closure)
- **Kuratowski, Topology Vol. I:** Chapter I (Closure and Interior)

---

## 🎓 Summary

Trong bài giảng này, chúng ta học về các **operators** quan trọng nhất:

✅ **Closed Sets:** Dual của open sets, axioms (C1)–(C3)  
✅ **Closure cl(·):** Smallest closed set containing A  
✅ **Kuratowski Axioms:** (K1) Extensivity, (K2) Idempotence, (K3) Unions, (K4) Normality  
✅ **Limit Points:** Điểm có các điểm của A "tụ lại gần"  
✅ **Interior int(·):** Largest open set in A, dual của closure  
✅ **Boundary ∂:** cl(A) \ int(A), "ranh giới"  
✅ **Dense Sets:** cl(A) = X, "everywhere" trong space  

**Điểm chính:**
- Closure và interior là **dual operators**: int(A) = X \ cl(X \ A)
- Closure = original set + limit points: cl(A) = A ∪ A'
- Boundary = điểm mà mọi neighborhood intersects cả inside và outside
- Dense sets: ℚ và ℝ\ℚ đều dense trong ℝ
- Operators này satisfy nice axioms (Kuratowski, etc.)

**Practical wisdom:**
- Để chứng minh A closed: chứng minh A = cl(A) hoặc complement open
- Để chứng minh x ∈ cl(A): chứng minh mọi neighborhood của x giao A
- Dense sets key trong approximation theory

**Tiếp theo:** Trong Lecture 01.03, chúng ta học về **Continuous Functions và Homeomorphisms**—cách ánh xạ giữa các topological spaces, và định nghĩa "topological equivalence".

---

*"Closure is the smallest closed set; interior is the largest open set. Between them lies the boundary."* — Topology wisdom

🎯 **Làm nhiều bài tập tính closure, interior, boundary! Đây là skills cần thiết.** 🎯

---

**Previous:** [Lecture 01.01: Basis and Subbasis](/contents/vi/topology-chapter01/01_01_Basis_Subbasis/)  
**Next:** [Lecture 01.03: Continuous Functions and Homeomorphisms](/contents/vi/topology-chapter01/01_03_Continuous_Functions_Homeomorphisms/)

