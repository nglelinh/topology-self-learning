---
layout: post
title: "Lecture 03.03: Urysohn Metrization Theorem"
lang: vi
lang-ref: lecture-03-03
chapter: 3
lecture: 3
categories: [chapter03]
tags: [metrization, urysohn-metrization, nagata-smirnov, metric-spaces]
description: "Urysohn Metrization Theorem và characterization của metrizable spaces"
---

**Urysohn Metrization Theorem**

---

## 📖 Tổng quan

Chúng ta đã học nhiều về topological spaces—một abstraction mạnh mẽ. Nhưng **metric spaces** có many nice properties:
- Có khái niệm "distance"
- Sequences sufficient (không cần nets)
- Completeness có ý nghĩa
- Intuitive và geometric

**Câu hỏi tự nhiên:**  
> **Khi nào một topological space có thể "metrizable"?**  
> (Tồn tại metric inducing topology đó)

**Preview của câu trả lời:**

**Urysohn Metrization Theorem:**
$$
\boxed{T_3 + \text{second countable} \implies \text{metrizable}}
$$

**Đây là một trong những định lý đẹp nhất trong topology!**

![Metrization concept](https://upload.wikimedia.org/wikipedia/commons/thumb/9/90/Metric_space.svg/400px-Metric_space.svg.png)  
*Metric space structure - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Metric_space.svg)*

**Trong bài này:**
- **Metrizable spaces:** Định nghĩa và necessary conditions
- **Urysohn Metrization Theorem:** Sufficient conditions (T₃ + 2nd countable)
- **Nagata-Smirnov Metrization:** More general characterization
- **Examples và applications**

**Tại sao quan trọng?**
- Characterize exactly khi nào có metric!
- ℝⁿ, compact manifolds metrizable
- Metric tools available trong metrizable spaces
- Bridge between point-set và metric topology

---

## 📐 Định nghĩa và Necessary Conditions

### 1. Metrizable Spaces

**Định nghĩa (Metrizable):**  
Topological space (X, τ) là **metrizable** nếu tồn tại metric d trên X sao cho τ = topology induced bởi d.

$$
\exists d: X \times X \to \mathbb{R}: \tau = \tau_d
$$

**Nói bằng lời:** Topology "comes from" một metric.

**Ví dụ Metrizable:**
- ℝⁿ với Euclidean topology
- Compact manifolds
- Subspaces của metrizable spaces
- Countable products của metrizable spaces

**Non-metrizable Examples:**
- Cofinite topology (infinite set)
- Cocountable topology (uncountable set)
- Trivial topology (> 1 point)
- Sorgenfrey plane ℝ_ℓ × ℝ_ℓ

---

### 2. Necessary Conditions

**Định lý (Metric ⇒ Properties):**  
Nếu X metrizable, thì:
1. X là **Hausdorff (T₂)**
2. X là **Regular (T₃)**
3. X là **Normal (T₄)**
4. X là **first countable**

**Chứng minh:**  
Đã chứng minh trong các bài trước: mọi metric space có các properties này. ✓

**Hệ quả:**  
Nếu space vi phạm bất kỳ property nào trên → **không metrizable**.

**Ví dụ:**
- Trivial topology không Hausdorff → không metrizable ✗
- Cofinite (infinite) không first countable → không metrizable ✗

---

**Câu hỏi:** Các conditions trên có **sufficient** không?

**Trả lời:** **KHÔNG!** Cần thêm countability condition.

**Counterexample (Long Line):**  
"Long line" L là space:
- Hausdorff ✓
- Regular ✓
- Normal ✓
- First countable ✓
- Nhưng **không metrizable** ✗ (không second countable)

---

## 📐 Urysohn Metrization Theorem

### 1. Statement

**Định lý Urysohn (Urysohn Metrization Theorem):**

> **Nếu X là T₃ (regular + T₁) và second countable, thì X metrizable.**

$$
(X \text{ regular} \land X \text{ second countable}) \implies X \text{ metrizable}
$$

**Đây là sufficient condition!**

**Ý nghĩa:**
- T₃: đủ separation (không cần T₄)
- Second countable: countability key!
- Conditions dễ verify trong practice

**Ví dụ:**
- ℝⁿ: regular + second countable → metrizable ✓
- Subspace của ℝⁿ: kế thừa properties → metrizable ✓
- Compact manifolds: locally Euclidean + second countable → metrizable ✓

---

### 2. Proof Strategy

**Ý tưởng chứng minh:** Construct metric explicitly!

**Step 1: Embedding into ℝ^∞**

Sử dụng Urysohn's Lemma và second countability để construct countably many continuous functions fₙ: X → [0,1] "separating" points và closed sets.

**Step 2: Define Metric**

$$
d(x, y) = \sum_{n=1}^\infty \frac{1}{2^n} |f_n(x) - f_n(y)|
$$

**Step 3: Verify**
- d is metric ✓
- Topology induced = original topology ✓

**Full Proof (Sketch):**

**Construction của {fₙ}:**

Cho {Bₙ} countable basis cho X.  
Với mỗi cặp (Bᵢ, Bⱼ) với cl(Bᵢ) ⊆ Bⱼ:
- X regular + Urysohn → ∃fᵢⱼ: X → [0,1] với fᵢⱼ(cl(Bᵢ)) = 0, fᵢⱼ(X \ Bⱼ) = 1

Enumerate tất cả such pairs → countable collection {fₙ}.

**Properties của {fₙ}:**
- Với x ≠ y: ∃ basis elements Bᵢ, Bⱼ separating them
- → ∃fₙ: fₙ(x) ≠ fₙ(y)
- → {fₙ} "separates points"

**Define metric:**
$$
d(x,y) = \sup_{n} \min\left\{|f_n(x) - f_n(y)|, \frac{1}{n}\right\}
$$

(Hoặc dùng formula với ∑ phía trên)

**Verify d induces original topology:**

**(⇒) τ_d ⊆ τ:**  
Mỗi fₙ continuous trong τ → d continuous → τ_d ⊆ τ. ✓

**(⇐) τ ⊆ τ_d:**  
Với U ∈ τ, x ∈ U: ∃Bᵢ, Bⱼ: x ∈ Bᵢ, cl(Bᵢ) ⊆ Bⱼ ⊆ U.  
fᵢⱼ(x) = 0, fᵢⱼ(X \ Bⱼ) = 1.  
Ball centered at x (trong metric d) contained trong U. ✓

---

### 3. Corollaries

**Hệ quả 1 (Subspaces):**  
Mọi subspace của metrizable space là metrizable.

**Proof:** Kế thừa metric và properties. ✓

**Hệ quả 2 (Countable Products):**  
Countable product của metrizable spaces là metrizable.

**Proof:** Second countability preserved, regularity preserved. ✓

**Hệ quả 3 (ℝⁿ):**  
ℝⁿ metrizable (obvious, nhưng now có proof!)

---

## 📐 Nagata-Smirnov Metrization Theorem

### 1. More General Characterization

Urysohn yêu cầu **second countable**—restrictive!  
Nagata-Smirnov generalize:

**Định lý Nagata-Smirnov:**

> **X metrizable ⟺ X regular + có countably locally finite basis.**

**Định nghĩa (Locally Finite):**  
Họ {Uα} là **locally finite** nếu mọi x ∈ X có neighborhood intersecting chỉ finitely many Uα.

**Ý nghĩa:** Weaker than second countable—cho phép more spaces metrizable.

**Ví dụ:**  
Manifolds thường có countably locally finite basis (even if not second countable).

---

### 2. Bing Metrization Theorem

**Định lý Bing:**

> **X metrizable ⟺ X regular + có σ-discrete basis.**

**Định nghĩa (σ-discrete):**  
Basis là countable union của discrete families.

**Discrete family:** Mọi điểm có neighborhood intersecting at most one member.

**Ý nghĩa:** Another characterization, useful trong certain contexts.

---

## 📐 Examples và Non-Examples

### Metrizable Spaces

| Space | Why Metrizable |
|-------|----------------|
| ℝⁿ | Regular + second countable |
| Compact manifolds | Locally Euclidean + second countable |
| Subspaces của metrizable | Inherit properties |
| Hilbert space ℓ² | Separable + complete |
| Discrete (countable) | Second countable |

### Non-Metrizable Spaces

| Space | Violates What? |
|-------|----------------|
| Cofinite (infinite) | Not first countable |
| Cocountable (uncount.) | Not first countable |
| Trivial (>1 pt) | Not Hausdorff |
| Long line | Not second countable |
| Sorgenfrey plane | Not normal (product issue) |
| [0,1]^ℝ (product) | Not first countable |

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Pavel Urysohn** - *"Über die Mächtigkeit der zusammenhängenden Mengen"* (1925)  
   *Urysohn Metrization Theorem*

2. **Jun-iti Nagata** - *"On a necessary and sufficient condition of metrizability"* (1950)  
   *Nagata-Smirnov Theorem*

3. **Yuri Smirnov** - *"A necessary and sufficient condition for metrizability"* (1951)  
   *Independent discovery*

4. **R.H. Bing** - *"Metrization of topological spaces"* (1951)  
   *Bing's characterization*

### Textbooks

5. **James R. Munkres** - *Topology*, 2nd Ed., **§34: Urysohn Metrization**  
   *Complete proof*

6. **Stephen Willard** - *General Topology*, **Chapter 6**  
   *Comprehensive treatment*

7. **Ryszard Engelking** - *General Topology*, **Chapter 4**  
   *Advanced perspective*

---

## 🔗 Applications and Connections

### Manifold Theory
**Smooth Manifolds:** Paracompact + Hausdorff manifolds metrizable. Metric useful cho Riemannian geometry.

### Functional Analysis
**Banach Spaces:** Separable Banach spaces metrizable. Metric structure essential cho convergence theory.

### Algebraic Topology
**CW Complexes:** Often metrizable (locally finite structure). Allows metric tools trong homotopy theory.

### Computer Science
**Topology in CS:** Metrizable spaces easier to implement computationally (discrete approximations).

---

## Video tham khảo

- **xem trước** [Lecture 40: Urysohn’s Metrization Theorem](https://www.youtube.com/watch?v=8QrZhsErCT4) — NPTEL IIT Bombay, tiếng Anh. Định lý metric hóa Urysohn trong một bài giảng đại học trọn vẹn.
- [The most important Theorem in Topology | Urysohn Metrisation theorem](https://www.youtube.com/watch?v=4pKQgFI3nF8) — Problemathic, tiếng Anh. Cùng định lý, nói ngắn hơn, để giữ phát biểu trước khi đi vào chứng minh dài.

## 🧩 Exercises

### Understanding Metrizable

1. **Necessary Conditions:**  
   Liệt kê tất cả necessary conditions cho metrizable.

2. **ℝⁿ Metrizable:**  
   Verify ℝⁿ satisfies Urysohn's conditions.

3. **Subspace:**  
   Chứng minh: subspace của metrizable space là metrizable.

### Urysohn Theorem

4. **Apply Urysohn:**  
   Compact Hausdorff space + second countable → metrizable.  
   Chứng minh statement này.

5. **Metric Construction:**  
   Với countable collection {fₙ: X → [0,1]} separating points:  
   $$d(x,y) = \sum \frac{1}{2^n} |f_n(x) - f_n(y)|$$  
   Verify đây là metric.

6. **Topology Match:**  
   Chứng minh metric trên induces original topology.

### Non-Metrizable

7. **Cofinite:**  
   Chứng minh cofinite topology (infinite set) không metrizable.

8. **Long Line:**  
   Tìm hiểu "long line".  
   - Properties nào satisfied?
   - Tại sao không metrizable?

9. **Sorgenfrey Plane:**  
   ℝ_ℓ × ℝ_ℓ không metrizable (không normal).  
   Giải thích.

### Advanced

10. **Nagata-Smirnov:**  
    Phát biểu Nagata-Smirnov theorem.  
    So sánh với Urysohn.

11. **Paracompact:**  
    Tìm hiểu: paracompact + Hausdorff ⟹ metrizable?  
    (Cần thêm conditions gì?)

12. **Products:**  
    Countable product của metrizable metrizable.  
    Uncountable product có metrizable không?

### Applications

13. **Manifolds:**  
    Compact manifolds second countable.  
    → Compact manifolds metrizable.

14. **Hilbert Space:**  
    ℓ² separable.  
    → ℓ² (với weak topology?) metrizable?

15. **Completeness:**  
    Metrizable space X: có thể choose metric making X complete không?

### Reflection

16. **Why Second Countable?:**  
    Giải thích tại sao second countability key trong Urysohn theorem.

17. **Metric Uniqueness:**  
    Nếu X metrizable, metric có unique không?  
    Equivalence của metrics?

18. **Historical:**  
    Tìm hiểu lịch sử metrization problem (1920s-1950s).

---

## 📚 Further Reading

- **Munkres, Topology:** §34 (Urysohn Metrization)
- **Willard, General Topology:** Chapter 6 (Metrization)
- **Engelking, General Topology:** Chapter 4
- **Nagata:** *Modern General Topology* (Advanced treatment)

---

## 🎓 Summary

Trong bài này, chúng ta học về **metrization**—khi nào topology "comes from" metric:

✅ **Metrizable:** ∃ metric inducing topology  
✅ **Necessary:** Hausdorff, regular, first countable  
✅ **Urysohn Metrization:** T₃ + second countable ⟹ metrizable  
✅ **Construction:** Explicit metric từ Urysohn functions  
✅ **Nagata-Smirnov:** More general (locally finite basis)  
✅ **Examples:** ℝⁿ, compact manifolds, subspaces  
✅ **Non-examples:** Cofinite, long line, Sorgenfrey plane  

**Điểm chính:**
- Second countability key trong Urysohn
- T₃ sufficient (không cần T₄!)
- Metrizable spaces = "nice" spaces với distance
- Construction explicit—không chỉ existence
- Applications: manifolds, analysis, algebraic topology

**Practical wisdom:**
- Check T₃ + second countable để verify metrizable
- ℝⁿ và subspaces automatically metrizable
- Metric tools available trong metrizable spaces
- Completeness separate issue (topology vs metric)

**Chapter 03 Complete!** Chúng ta đã học:
- T₀, T₁, T₂ (Hausdorff)
- T₃ (Regular), T₄ (Normal), Urysohn's Lemma
- Countability axioms
- Metrization theorems

**Tiếp theo:** Chapter 04 về **Metric Spaces** chi tiết—completeness, Baire category, function spaces!

---

*"Metrization: when topology becomes geometry."* — Topological wisdom

🎯 **Master the conditions: T₃ + second countable = metrizable!** 🎯

---

**Previous:** [Lecture 03.02: Countability Axioms](/contents/vi/topology-chapter03/03_02_Countability_Axioms/)  
**Next Chapter:** [Chapter 04: Metric Spaces and Metrization](/contents/vi/topology-chapter04/)

