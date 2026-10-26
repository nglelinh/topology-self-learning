---
layout: post
title: "Lecture 02.02: Local Compactness and Compactification"
lang: vi
lang-ref: lecture-02-02
chapter: 2
lecture: 2
categories: [chapter02]
tags: [locally-compact, compactification, one-point-compactification, stone-cech]
description: "Locally compact spaces, one-point compactification, và Stone-Čech compactification"
---

**Local Compactness and Compactification**

---

## 📖 Tổng quan

Trong bài trước, chúng ta học về **compact spaces**—spaces "finite in disguise". Nhưng nhiều spaces quan trọng **không compact**: ℝ, ℝⁿ, open manifolds...

**Câu hỏi tự nhiên:**
1. Có property "weaker" than compactness nhưng vẫn useful không?  
   → **Locally compact**: mọi điểm có compact neighborhood

2. Có thể "compactify" non-compact space không?  
   → **Compactification**: add points để làm compact!

**Ví dụ trực quan:**
- **ℝ** không compact, nhưng **locally compact** (mỗi x có compact neighborhood [x-1, x+1])
- **ℝ + {∞}** = S¹ (circle) = compact! (one-point compactification)
- **ℝⁿ + {∞}** = Sⁿ (sphere)

![One-point compactification of R](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Compactification.svg/400px-Compactification.svg.png)  
*One-point compactification: ℝ → S¹ - Nguồn concept*

**Trong bài này:**
- **Locally compact spaces**: định nghĩa và examples
- **One-point compactification**: thêm "point at infinity"
- **Stone-Čech compactification**: universal compactification
- **Applications**: analysis, algebraic topology

**Tại sao quan trọng?**
- Locally compact = property của ℝⁿ, manifolds
- Compactification = tool để apply compact theorems
- Stone-Čech = categorical perspective
- Geometry at infinity (in algebraic topology)

---

## 📐 Locally Compact Spaces

### 1. Định nghĩa

**Định nghĩa (Locally Compact):**  
X là **locally compact** nếu mọi x ∈ X có **compact neighborhood**.

$$
\forall x \in X: \exists K \text{ compact}, \exists U \in \tau: x \in U \subseteq K
$$

**Phiên bản mạnh hơn:** Mọi x và mọi neighborhood V của x, tồn tại compact K với x ∈ int(K) ⊆ K ⊆ V.

**Ví dụ 1: ℝⁿ**

ℝⁿ locally compact: mọi x ∈ ℝⁿ, closed ball B̄(x, 1) compact (Heine-Borel).

**Ví dụ 2: Manifolds**

Mọi n-dimensional manifold locally compact (locally homeomorphic với ℝⁿ).

**Ví dụ 3: Discrete Space**

Mọi discrete space locally compact: {x} là compact neighborhood của x.

**Non-example 1: ℚ**

ℚ (với topology từ ℝ) **không** locally compact!

**Proof:** Mọi compact subset của ℚ là finite union của points (no intervals).  
Nhưng mọi neighborhood của x ∈ ℚ chứa infinitely many rationals.  
→ Không có compact neighborhood. ✗

**Non-example 2: Infinite-Dimensional Spaces**

Hilbert space ℓ² **không** locally compact (Riesz's theorem).

---

### 2. Properties

**Định lý (Closed Subspace):**  
Nếu X locally compact Hausdorff và F ⊆ X closed, thì F locally compact.

**Định lý (Open Subspace):**  
Nếu X locally compact Hausdorff và U ⊆ X open, thì U locally compact.

**Chứng minh:** Exercise (sử dụng compact neighborhoods).

**Định lý (Product):**  
Nếu X, Y locally compact, thì X × Y locally compact.

**Chú ý:** Infinite products của locally compact spaces **không** locally compact (nói chung).

---

## 📐 One-Point Compactification

### 1. Construction

**Động lực:** Làm sao "compactify" non-compact space bằng cách thêm **one point**?

**Idea:** Add "point at infinity" ∞.

**Construction (Alexandroff Compactification):**

Cho X locally compact Hausdorff, **không compact**.  
Define:
$$
X^* = X \cup \{\infty\}
$$

**Topology trên X^*:**
- Open sets in X remain open
- Neighborhoods của ∞: {∞} ∪ (X \ K) với K ⊆ X compact

Formally:
$$
\tau^* = \tau \cup \{X^* \setminus K : K \subseteq X \text{ compact closed}\}
$$

**Định lý:**  
X^* là compact Hausdorff space.

**Chứng minh (sketch):**

**Hausdorff:** Nếu x, y ∈ X: dùng Hausdorff của X.  
Nếu x ∈ X, y = ∞: x có compact neighborhood K, nên U = int(K), V = X^* \ K separate chúng.

**Compact:** Cho {Uα} open cover của X^*.  
Nếu ∞ ∈ Uα₀, thì Uα₀ = X^* \ K với K compact.  
K ⊆ ⋃_{α≠α₀} Uα → finite subcover cho K.  
→ Finite subcover cho X^*. ∎

---

### 2. Examples

**Example 1: ℝ**

ℝ^* = ℝ ∪ {∞} homeomorphic với **S¹** (circle)!

**Homeomorphism:** Stereographic projection  
f: ℝ → S¹ \ {north pole}, extend với f(∞) = north pole.

![Stereographic projection](https://upload.wikimedia.org/wikipedia/commons/thumb/6/69/Stereoprojzero.svg/400px-Stereoprojzero.svg.png)  
*Stereographic projection: ℝ ∪ {∞} ≅ S¹ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Stereoprojzero.svg)*

**Example 2: ℝⁿ**

(ℝⁿ)^* ≅ **Sⁿ** (n-sphere)

**Example 3: ℂ (Complex Plane)**

ℂ^* = ℂ ∪ {∞} = **Riemann sphere** ≅ S²

**Applications:** Complex analysis, meromorphic functions.

**Example 4: Open Disk**

D² (open unit disk) → D²^* ≅ S² (2-sphere)

---

### 3. Uniqueness

**Định lý (Uniqueness):**  
Nếu X locally compact Hausdorff không compact, one-point compactification **unique** (up to homeomorphism).

**Chứng minh:** Universal property (xem sau).

---

## 📐 Stone-Čech Compactification

### 1. Universal Property

**Vấn đề:** One-point compactification **không** universal!

**Ví dụ:** Continuous f: ℝ → [0,1] không extend được lên ℝ^* = S¹ (nói chung).

**Giải pháp:** **Stone-Čech compactification** βX—largest possible compactification!

**Định lý (Stone-Čech):**  
Với mọi Tychonoff space X (T₃.₅), tồn tại compact Hausdorff βX và embedding i: X → βX sao cho:

**Universal Property:**  
Với mọi compact Hausdorff K và continuous f: X → K, tồn tại **duy nhất** continuous extension f̄: βX → K.

```
X ---f---> K
|          
i|         
v          
βX --f̄--> K
```

**Trực giác:** βX = "largest" compactification—mọi continuous map extend được!

---

### 2. Construction (Sketch)

**Construction via C(X, [0,1]):**

Xét tất cả bounded continuous functions f: X → [0,1].  
Embed X vào [0,1]^{C(X,[0,1])} bởi:
$$
x \mapsto (\ldots, f(x), \ldots)
$$

Take closure → βX!

**Tính chất:**
- |βℕ| = 2^{2^{ℵ₀}} (extremely large!)
- β(ℝ) \ ℝ gọi là "space of ultrafilters"
- Very non-constructive (cần Axiom of Choice)

---

### 3. Examples

**Example 1: Compact Space**

Nếu X đã compact, βX = X.

**Example 2: ℕ**

βℕ = Stone-Čech compactification của ℕ (discrete).  
|βℕ| = 2^{2^{ℵ₀}} >> |ℕ^*| = ℵ₀ + 1.

βℕ có cấu trúc algebraic phức tạp (semigroup operations).

**Example 3: (0,1)**

β(0,1) = [0,1] (vì (0,1) dense trong [0,1] compact).

**Example 4: ℝ**

βℝ ≠ ℝ^* = S¹ (βℝ much larger!)

---

## 🔗 Applications

### Algebraic Topology - Ends

**Ends of Space:** βX \ X mô tả "geometry at infinity".  
- ℝ: 2 ends (±∞)
- ℝⁿ (n ≥ 2): 1 end
- Infinite graph: số ends = topological invariant

### Complex Analysis - Riemann Sphere

**Meromorphic Functions:** Functions ℂ → ℂ^* = Riemann sphere.  
Poles = values at ∞.

### Functional Analysis - Banach Algebras

**Maximal Ideals:** Maximal ideal space của C_b(X) ≅ βX.  
Gelfand transform uses Stone-Čech!

### Set Theory - Ultrafilters

**βℕ \ ℕ** = space của non-principal ultrafilters trên ℕ.  
Applications trong logic, combinatorics.

---

## Video tham khảo

- **xem trước** [Basic Topology 8 | Locally Compact Hausdorff Spaces](https://www.youtube.com/watch?v=UN86A94iz6I) — The Bright Side of Mathematics, tiếng Anh. Compact địa phương Hausdorff: mỗi điểm có một lân cận compact, đúng nửa đầu bài.
- [one point compactification -- Topology Video 18](https://www.youtube.com/watch?v=5tdsgjHlMtA) — MathMajor, tiếng Anh. Compact hóa một điểm, phép thêm một điểm ở vô cực mà bài xây ở nửa sau.
- [Lecture 31: One point compactification](https://www.youtube.com/watch?v=os9m6Q4gAzM) — NPTEL IIT Bombay, tiếng Anh. Cùng phép compact hóa một điểm, trong một bài giảng đại học đủ chậm để đối chiếu chứng minh.

## 🧩 Exercises

### Locally Compact

1. **Verify:** ℝⁿ locally compact.

2. **ℚ Not Locally Compact:**  
   Chứng minh chi tiết ℚ không locally compact.

3. **Product:**  
   X, Y locally compact → X × Y locally compact?

### One-Point Compactification

4. **ℝ^*:**  
   Mô tả topology trên ℝ^* = ℝ ∪ {∞}.  
   Chứng minh ℝ^* ≅ S¹.

5. **ℝⁿ^*:**  
   (ℝⁿ)^* ≅ Sⁿ. Construct homeomorphism tường minh.

6. **Not Locally Compact:**  
   Tại sao ℚ không có one-point compactification?

### Stone-Čech

7. **Universal Property:**  
   f: ℕ → [0,1], f(n) = 1/n.  
   f extend lên βℕ như thế nào?

8. **Size:**  
   Tại sao |βℕ| = 2^{2^{ℵ₀}}?  
   (*Hint:* Ultrafilters)

### Advanced

9. **Alexandroff vs Stone-Čech:**  
   So sánh ℝ^* và βℝ. Tại sao khác nhau?

10. **Ends:**  
    Số ends của ℝ, ℝ², ℝ³?

---

## 📚 Further Reading

- **Munkres, Topology:** §29 (Local Compactness), §38 (Stone-Čech)
- **Willard, General Topology:** Chapter 6
- **Engelking, General Topology:** Chapter 3.5–3.6

---

## 🎓 Summary

✅ **Locally Compact:** Mọi điểm có compact neighborhood  
✅ **One-Point Compactification:** X^* = X ∪ {∞}  
✅ **ℝⁿ^* ≅ Sⁿ:** Stereographic projection  
✅ **Stone-Čech βX:** Universal compactification  
✅ **Universal Property:** Mọi continuous map extend  

**Điểm chính:**
- Locally compact = ℝⁿ, manifolds
- One-point: simple, geometric
- Stone-Čech: universal, abstract
- Compactification = tool để apply compact theorems

**Tiếp theo:** Chapter 03 về **Separation Axioms**!

---

🎯 **Visualize compactifications! Vẽ ℝ → S¹, ℝ² → S².** 🎯

---

**Previous:** [Lecture 02.01: Compact Spaces](/contents/vi/topology-chapter02/02_01_Compact_Spaces/)  
**Next Chapter:** [Chapter 03: Separation Axioms](/contents/vi/topology-chapter03/)

