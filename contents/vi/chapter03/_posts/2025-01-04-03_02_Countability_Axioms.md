---
layout: post
title: "Lecture 03.02: Countability Axioms"
lang: vi
lang-ref: lecture-03-02
chapter: 3
lecture: 2
categories: [chapter03]
tags: [first-countable, second-countable, separable, lindelof, countability]
description: "First countable, second countable, separable, và Lindelöf spaces"
---

**Countability Axioms**

---

## 📖 Tổng quan

Sau khi học về separation (cách tách các điểm và tập hợp), chúng ta chuyển sang **countability**—khái niệm về "size" của topology.

**Câu hỏi động lực:** Khi nào một topological space "không quá lớn" theo nghĩa có countable structure?

**Các khái niệm chính:**
1. **First Countable:** Mỗi điểm có countable neighborhood basis
2. **Second Countable:** Toàn bộ topology có countable basis  
3. **Separable:** Có countable dense subset
4. **Lindelöf:** Mọi open cover có countable subcover

**Ví dụ trực quan:**
- **ℝ** (Euclidean): First countable, second countable, separable, Lindelöf ✓✓✓✓
- **Discrete topology trên ℝ:** First countable, không second countable ✓✗
- **Uncountable space với cofinite:** Không first countable ✗

![Countability hierarchy](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/Separation_and_countability.svg/500px-Separation_and_countability.svg.png)  
*Relationships giữa countability properties - Nguồn concept*

**Tại sao quan trọng?**
- **Metrization:** Second countable + T₃ ⇒ metrizable
- **Sequences:** First countable cho phép dùng sequences thay vì nets
- **Separable:** ℚ dense trong ℝ—foundation cho analysis
- **Lindelöf + Hausdorff + paracompact ⇒ normal**

---

## 📐 Định nghĩa Hình thức

### 1. First Countable Spaces

**Định nghĩa (Neighborhood Basis):**  
**Neighborhood basis** tại x là họ {Bₙ} các neighborhoods của x sao cho mọi neighborhood N của x, tồn tại Bₙ ⊆ N.

**Định nghĩa (First Countable):**  
X là **first countable** nếu mọi điểm có **countable neighborhood basis**.

$$
\forall x \in X: \exists \{B_n\}_{n=1}^\infty \text{ neighborhoods of } x: \forall N \ni x: \exists n: B_n \subseteq N
$$

**Trực giác:** "Local" property—mỗi điểm có countable "local structure".

**Ví dụ 1: Metric Spaces**

**Định lý:** Mọi metric space là first countable.

**Chứng minh:**  
Với x ∈ X, neighborhood basis: {B(x, 1/n)}_{n=1}^∞.  
Với mọi neighborhood N của x, ∃ε: B(x,ε) ⊆ N.  
Chọn n > 1/ε → B(x, 1/n) ⊆ N. ✓

**Hệ quả:** ℝⁿ first countable.

**Ví dụ 2: Discrete Topology**

Mọi space với discrete topology first countable: {{x}} là countable neighborhood basis.

**Non-example: Cocountable Topology (Uncountable Set)**

X uncountable với cocountable topology **không** first countable!

**Proof:**  
Neighborhood của x = sets chứa x với countable complement.  
Giả sử {Bₙ} countable neighborhood basis tại x.  
Mỗi Bₙ có countable complement Cₙ.  
C = ⋃Cₙ countable (countable union of countable sets).  
N = X \ C là neighborhood của x.  
Nhưng không có Bₙ ⊆ N (vì mỗi Bₙ intersects C). Mâu thuẫn! ✗

---

**Định lý (Sequential Characterization):**  
Trong first countable space, A̅ = {x : ∃ sequence trong A converging to x}.

**Nói bằng lời:** Closure có thể described hoàn toàn bằng sequences!

**Chứng minh:**  
(⊆) Luôn đúng.  
(⊇) Cho x ∈ A̅. {Bₙ} countable neighborhood basis tại x.  
Vₙ = B₁ ∩ ... ∩ Bₙ cũng là neighborhood basis.  
Mỗi Vₙ ∩ A ≠ ∅ → chọn xₙ ∈ Vₙ ∩ A.  
Sequence {xₙ} → x. ✓

**Ý nghĩa:** Trong first countable spaces, có thể dùng sequences thay vì general nets!

---

### 2. Second Countable Spaces

**Định nghĩa (Second Countable):**  
X là **second countable** nếu topology có **countable basis**.

$$
\exists \{B_n\}_{n=1}^\infty \text{ basis}: \forall U \in \tau: U = \bigcup_{n \in I} B_n, I \subseteq \mathbb{N}
$$

**Trực giác:** "Global" property—toàn bộ topology có countable structure.

**Ví dụ 1: ℝ với Euclidean Topology**

**Định lý:** ℝ second countable.

**Chứng minh:**  
Basis ℬ = {(a,b) : a,b ∈ ℚ} countable.  
Mọi open U là union của intervals với rational endpoints. ✓

**Tổng quát:** ℝⁿ second countable (basis = open rectangles với rational corners).

**Ví dụ 2: Countable Sets**

Mọi countable set với bất kỳ topology nào có countable basis (vì 𝒫(X) countable).

**Non-example: Discrete Topology (Uncountable)**

Discrete topology trên uncountable set X **không** second countable.

**Proof:**  
Trong discrete topology, mọi singleton {x} open.  
Basis phải chứa {x} với mọi x.  
→ Basis uncountable. ✗

**Non-example: Lower Limit Topology ℝ_ℓ**

ℝ với lower limit topology (basis {[a,b)}) **không** second countable!

**Proof (sketch):** Counting argument—không thể cover tất cả [a,b) bằng countable basis.

---

**Định lý (Second ⇒ First):**  
Second countable ⇒ first countable.

**Chứng minh:**  
Cho {Bₙ} countable basis cho X.  
Với x ∈ X, neighborhood basis tại x = {Bₙ : x ∈ Bₙ} (countable subset). ✓

**Chú ý:** Ngược lại **sai**! (Discrete topology trên uncountable set)

---

### 3. Separable Spaces

**Định nghĩa (Dense Set):**  
D ⊆ X là **dense** nếu D̅ = X.

**Định nghĩa (Separable):**  
X là **separable** nếu có **countable dense subset**.

$$
\exists D \subseteq X: |D| \leq \aleph_0 \land \overline{D} = X
$$

**Trực giác:** "Approximation" property—countable subset "fill" entire space.

**Ví dụ 1: ℝ**

ℚ dense trong ℝ → ℝ separable.

**Ví dụ 2: ℝⁿ**

ℚⁿ dense trong ℝⁿ → ℝⁿ separable.

**Ví dụ 3: Hilbert Space ℓ²**

{sequences với finitely many rational entries} dense → ℓ² separable.

**Non-example: Discrete Topology (Uncountable)**

Uncountable set X với discrete topology **không** separable.

**Proof:**  
D dense → D̅ = X → D = X (mọi point closed trong discrete).  
Nhưng D countable, X uncountable. Mâu thuẫn! ✗

---

**Định lý (Second Countable ⇒ Separable):**  
Second countable ⇒ separable.

**Chứng minh:**  
Cho {Bₙ} countable basis.  
Chọn xₙ ∈ Bₙ (mỗi Bₙ non-empty).  
D = {xₙ} countable.  
Mọi open U ≠ ∅ chứa Bₙ nào đó → chứa xₙ.  
→ U ∩ D ≠ ∅ → D dense. ✓

**Chú ý:** Ngược lại **sai** trong general!  
Separable không implies second countable.

**Counterexample:** Có separable spaces không second countable (e.g., uncountable products).

---

### 4. Lindelöf Spaces

**Định nghĩa (Lindelöf):**  
X là **Lindelöf** nếu mọi open cover có **countable subcover**.

$$
\forall \{U_\alpha\}_{\alpha \in I} \text{ open cover}: \exists \text{ countable } J \subseteq I: X = \bigcup_{\alpha \in J} U_\alpha
$$

**Trực giác:** "Compactness-like" nhưng yêu cầu countable subcover thay vì finite.

**Ví dụ 1: Compact Spaces**

Mọi compact space là Lindelöf (finite ⊆ countable).

**Ví dụ 2: Second Countable**

**Định lý:** Second countable ⇒ Lindelöf.

**Chứng minh:**  
Cho {Bₙ} countable basis, {Uα} open cover.  
Mỗi x ∈ X: x ∈ Uα(x) nào đó → ∃Bₙ(x): x ∈ Bₙ(x) ⊆ Uα(x).  
{Bₙ(x)} countable subcover bởi basis elements.  
Với mỗi Bₙ(x), chọn Uα chứa nó → countable subcover. ✓

**Ví dụ 3: ℝ**

ℝ Lindelöf (vì second countable).

**Non-example: Discrete Topology (Uncountable)**

Uncountable discrete space **không** Lindelöf.

**Proof:**  
Cover {{x}}_{x∈X} không có countable subcover. ✗

---

**Định lý (Lindelöf + Hausdorff ⇒ Normal):**  
Trong Hausdorff space, Lindelöf + paracompact ⇒ normal.

(Paracompact = every open cover has locally finite refinement—advanced topic)

---

### 5. Relationships

**Summary of Implications:**

```
Second Countable ⟹ Lindelöf
        ↓
First Countable    Separable
        ↘         ↙
     (no direct implication)
```

**Key Facts:**
1. Second countable ⇒ first countable
2. Second countable ⇒ separable
3. Second countable ⇒ Lindelöf
4. Separable **⇏** second countable
5. First countable **⇏** second countable
6. Lindelöf **⇏** second countable

**Theorem (Metrizable):**  
Trong metrizable spaces: separable ⟺ second countable.

**Proof:** Exercise (sử dụng properties của metric topology).

---

**Table of Examples:**

| Space | 1st Count | 2nd Count | Separable | Lindelöf |
|-------|-----------|-----------|-----------|----------|
| ℝⁿ (Euclidean) | ✓ | ✓ | ✓ | ✓ |
| Discrete (countable) | ✓ | ✓ | ✓ | ✓ |
| Discrete (uncountable) | ✓ | ✗ | ✗ | ✗ |
| Cocountable (uncountable) | ✗ | ✗ | ✓ | ✓ |
| ℝ_ℓ (Lower limit) | ✓ | ✗ | ✓ | ✓ |
| [0,1]^ℝ (product) | ✓ | ✗ | ✗ | ✗ |

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Early work on countability axioms*

2. **Ernst Lindelöf** - *"Sur quelques points de la théorie des ensembles"* (1903)  
   *Lindelöf covering property*

3. **René-Maurice Fréchet** - *"Sur quelques points du calcul fonctionnel"* (1906)  
   *First countable spaces (sequential spaces)*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§30: Countability Axioms**  
   *Clear systematic treatment*

5. **Stephen Willard** - *General Topology*, **Chapter 4**  
   *Comprehensive coverage*

6. **Ryszard Engelking** - *General Topology*, **Chapter 1.2**  
   *Detailed technical treatment*

---

## 🔗 Applications and Connections

### Analysis - Approximation Theory
**Weierstrass Approximation:** ℝ separable (ℚ dense) → polynomials dense trong C[0,1].

### Functional Analysis - Hilbert Spaces
**Separable Hilbert Spaces:** Most "useful" Hilbert spaces separable (ℓ², L²).

### Metrization Theory
**Urysohn Metrization:** T₃ + second countable ⟹ metrizable (next lecture!).

### Topology - Stone-Čech
**βℕ:** Stone-Čech compactification của ℕ không first countable tại points trong βℕ \ ℕ.

---

## Video tham khảo

- **xem trước** [Second Countable Spaces, and the relation to First Countable Spaces](https://www.youtube.com/watch?v=Y6AILGjDoVA) — Andrew McCrady, tiếng Anh. Đếm được thứ nhất và thứ hai, và quan hệ giữa chúng.
- [1st/2nd countable and Lindelöf spaces --Topology Video 21](https://www.youtube.com/watch?v=7ZIrSxNan8o) — MathMajor, tiếng Anh. Thêm Lindelöf vào cùng bức tranh, đúng cụm tiên đề đếm được của bài.
- [Countability axioms | Part 2 | Topology](https://www.youtube.com/watch?v=oL06FkGQttM) — Problemathic, tiếng Anh. Một lối thứ hai, chậm hơn, nếu hai video trên còn đặc.

## 🧩 Exercises

### First Countable

1. **Metric First Countable:**  
   Chứng minh chi tiết: mọi metric space first countable.

2. **Sequential:**  
   Trong first countable space, chứng minh:  
   A closed ⟺ A chứa limits của mọi convergent sequences trong A.

3. **Product:**  
   Nếu X, Y first countable, chứng minh X × Y first countable.

### Second Countable

4. **ℝ Second Countable:**  
   Chứng minh ℝ second countable bằng basis {(a,b) : a,b ∈ ℚ}.

5. **ℝⁿ Second Countable:**  
   Mở rộng sang ℝⁿ.

6. **Subspace:**  
   Nếu X second countable, A ⊆ X, chứng minh A second countable.

7. **Discrete Uncountable:**  
   Chứng minh: discrete topology trên uncountable set không second countable.

### Separable

8. **ℚ Dense:**  
   Chứng minh ℚ dense trong ℝ.

9. **ℓ² Separable:**  
   Hilbert space ℓ² = {(xₙ) : ∑xₙ² < ∞}.  
   Chứng minh ℓ² separable.  
   (*Hint:* Sequences với finitely many rational entries)

10. **Product:**  
    Nếu X, Y separable, X × Y có separable không?

### Lindelöf

11. **Second ⇒ Lindelöf:**  
    Chứng minh chi tiết: second countable ⇒ Lindelöf.

12. **ℝ Lindelöf:**  
    Verify ℝ là Lindelöf.

13. **Compact ⇒ Lindelöf:**  
    Trivial, nhưng giải thích tại sao.

### Relationships

14. **Separable ⇏ Second:**  
    Tìm ví dụ separable space không second countable.  
    (*Hint:* Lower limit topology)

15. **First ⇏ Second:**  
    Discrete topology trên uncountable set: first countable nhưng không second countable.

16. **Metrizable:**  
    Trong metric spaces, chứng minh:  
    Separable ⟺ second countable.

### Advanced

17. **Cocountable:**  
    X uncountable với cocountable topology:
    - First countable? ✗
    - Separable? ✓
    - Lindelöf? ✓

18. **[0,1]^ℝ:**  
    Product [0,1]^ℝ (uncountable product):
    - First countable? ✓
    - Second countable? ✗
    - Separable? ✗

19. **Tychonoff Product:**  
    Product của countably many second countable spaces có second countable không?

### Reflection

20. **Why Countability?**  
    Giải thích tại sao countability axioms quan trọng trong:
    - Metrization
    - Sequential characterizations
    - Analysis

---

## 📚 Further Reading

- **Munkres, Topology:** §30 (Countability Axioms)
- **Willard, General Topology:** Chapter 4
- **Engelking, General Topology:** Chapter 1.2
- **Kelley, General Topology:** Chapter 5

---

## 🎓 Summary

Trong bài này, chúng ta học về **countability properties**:

✅ **First Countable:** Mọi điểm có countable neighborhood basis  
✅ **Second Countable:** Topology có countable basis  
✅ **Separable:** Có countable dense subset  
✅ **Lindelöf:** Mọi open cover có countable subcover  
✅ **Implications:**
   - Second countable ⇒ first countable
   - Second countable ⇒ separable
   - Second countable ⇒ Lindelöf  
✅ **Metrizable:** Separable ⟺ second countable (trong metric spaces)  

**Điểm chính:**
- ℝⁿ satisfies tất cả countability properties
- Second countable = strongest condition
- First countable cho phép dùng sequences
- Separable = approximation property
- Countability key trong metrization

**Practical wisdom:**
- Check second countable để prove metrizable
- First countable → sequences sufficient
- Separable useful trong analysis

**Tiếp theo:** Lecture 03.03 về **Urysohn Metrization Theorem**—khi nào space metrizable? T₃ + second countable ⇒ metrizable!

---

*"Second countability: the topology is not too large to describe."* — Topological intuition

🎯 **Countability = tractability! Smaller = nicer.** 🎯

---

**Previous:** [Lecture 03.01: Regular and Normal Spaces](/contents/vi/topology-chapter03/03_01_Regular_Normal_Spaces_Urysohn/)  
**Next:** [Lecture 03.03: Urysohn Metrization Theorem](/contents/vi/topology-chapter03/03_03_Urysohn_Metrization_Theorem/)

