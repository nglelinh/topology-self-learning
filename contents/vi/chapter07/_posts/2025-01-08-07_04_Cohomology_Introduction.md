---
layout: post
title: "Lecture 07.04: Cohomology - Introduction"
lang: vi
lang-ref: lecture-07-04
chapter: 7
lecture: 4
categories: [chapter07]
tags: [cohomology, cup-product, ring-structure, poincare-duality]
description: "Cohomology Hⁿ(X): dual của homology, cup product ∪, ring structure, Universal Coefficient Theorem"
---

**H^n(X) - Dual Theory with Rich Algebraic Structure**

---

## 📖 Tổng quan

Chúng ta đã thành thạo **homology $H_n(X)$**—các bất biến abelian group mạnh mẽ. Homology cho chúng ta một cách đo lường các lỗ trong không gian và là một công cụ mạnh mẽ trong topology đại số.

**Nhưng có gì thêm?**

> **Cohomology $H^n(X)$ = "dual" của homology**

**Tại sao "dual" không đủ?**

Cohomology có **cấu trúc bổ sung** mà homology không có:

✅ **Cup product $\cup$:** Phép nhân trong cohomology! Đây là một cấu trúc đại số quan trọng cho phép chúng ta nhân các cohomology classes với nhau.

✅ **Ring structure:** $H^*(X)$ = graded ring—tổng trực tiếp của tất cả các cohomology groups tạo thành một graded ring, một cấu trúc đại số phong phú hơn nhiều so với chỉ các groups.

✅ **Contravariant:** $f: X \to Y$ cảm ứng $f^*: H^n(Y) \to H^n(X)$ (reverse direction!)—cohomology là contravariant, nghĩa là các maps đi theo hướng ngược lại so với homology.

✅ **More refined:** Phân biệt các không gian mà homology không thể—cohomology có thể phân biệt các không gian mà homology không thể phân biệt được.

✅ **Geometric:** Poincaré duality liên kết $H^k \leftrightarrow H_{n-k}$—đây là một kết quả hình học sâu sắc cho phép chúng ta liên kết cohomology và homology trên các manifolds.  

![Cohomology cup product](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Cup_product.svg/400px-Cup_product.svg.png)  
*Cup product visualization - Nguồn concept*

Trong bài học này, chúng ta sẽ khám phá cohomology một cách có hệ thống. Chúng ta sẽ nghiên cứu **Cochain complex**—cấu trúc dual của chain complex. Chúng ta sẽ học về **Cohomology groups $H^n(X)$**—định nghĩa và các tính chất cơ bản. Chúng ta sẽ tìm hiểu **Cup product $\cup$**—cấu trúc phép nhân quan trọng trong cohomology. Chúng ta sẽ xem xét **Ring $H^*(X)$**—graded ring invariant mạnh mẽ. Chúng ta sẽ học về **Universal Coefficient Theorem**—liên kết $H^n$ với $H_n$. Chúng ta sẽ khám phá **Poincaré Duality**—duality trên các manifolds. Chúng ta sẽ xem xét các **ví dụ** cụ thể như spheres, torus, projective spaces—những ví dụ này cho thấy sức mạnh của cohomology. Cuối cùng, chúng ta sẽ xem xét các **ứng dụng** trong obstruction theory và characteristic classes—những ứng dụng quan trọng trong topology và geometry.

**Tại sao đây là kiến thức quan trọng?** **Ring structure** = bất biến mạnh mẽ hơn nhiều so với chỉ các groups—cấu trúc ring cho phép chúng ta nhân các cohomology classes và tạo ra các bất biến mạnh mẽ hơn. Đây là **nền tảng** cho modern geometry (vector bundles, characteristic classes)—cohomology là công cụ cơ bản trong nghiên cứu các vector bundles và characteristic classes. Nó **cần thiết** trong algebraic geometry và differential topology—cohomology xuất hiện khắp nơi trong các lĩnh vực này. Cuối cùng, **Cup product** phát hiện các intersections hình học—đây là một cách mạnh mẽ để nghiên cứu các intersections trong không gian.

---

## 🔗 Cochains and Coboundary

### 1. Cochain Groups

**Ôn tập (Homology):**  
Chain complex: $C_n(X)$ với boundary $\partial: C_n \to C_{n-1}$.

**Dualize:**

**Định nghĩa (Cochain Groups):**  
Cố định coefficient group $G$ (thường là $\mathbb{Z}$).

$$
C^n(X; G) = \text{Hom}(C_n(X), G)
$$

**Group của các homomorphisms từ $C_n(X)$ đến $G$.** Trực giác hình học là cochain group là không gian của các "functions" trên chain group—mỗi cochain là một cách gán giá trị cho mỗi chain.

**Elements:** Cochains $\phi: C_n(X) \to G$. Mỗi cochain là một homomorphism từ chain group đến coefficient group.

---

**Trực giác:**

- **Chains:** "Geometric" objects (simplices)—các đối tượng hình học như simplices
- **Cochains:** "Functions" trên chains (assign values)—các hàm số trên chains, gán giá trị cho mỗi chain

**Ví dụ:** 1-chain = formal sum của các edges.  
1-cochain = function gán số cho mỗi edge. Đây là một cách hiểu trực quan—chains là các đối tượng hình học, còn cochains là các hàm số trên các đối tượng này.

---

### 2. Coboundary Operator

**Định nghĩa (Coboundary):**  
Boundary $\partial: C_{n+1} \to C_n$ cảm ứng **coboundary** $\delta: C^n \to C^{n+1}$.

**Công thức:** $\phi \in C^n$, định nghĩa $\delta\phi \in C^{n+1}$ bởi:

$$
(\delta \phi)(c) = \phi(\partial c), \quad c \in C_{n+1}
$$

**"Precompose với boundary."** Trực giác hình học là coboundary operator được định nghĩa bằng cách "precompose" với boundary operator—chúng ta áp dụng cochain vào boundary của chain. Điều này tạo ra một cochain ở chiều cao hơn.

---

**Diagram:**

```
C_{n+1} --∂--> C_n
   |           |
   ↓           ↓
   G <--δφ--- G
```

δφ = φ ∘ ∂.

---

### 3. Key Property: δ² = 0

**Theorem:** δ^{n+1} ∘ δ^n = 0.

**Proof:**  
(δ²φ)(c) = (δφ)(∂c) = φ(∂²c) = φ(0) = 0.

Uses ∂² = 0! ✓

**Same as homology, but "dual."**

---

### 4. Cochain Complex

**Cochain complex:**

$$
0 \to C^0(X) \xrightarrow{\delta^0} C^1(X) \xrightarrow{\delta^1} C^2(X) \to \cdots
$$

**Arrows go UP in dimension** (opposite of chains).

**Cocycles:** Z^n = ker(δ^n) (cochains với δφ = 0)

**Coboundaries:** B^n = im(δ^{n-1}) (cochains = δψ)

**Lemma:** B^n ⊆ Z^n (follows from δ² = 0).

---

## 📊 Cohomology Groups

### 1. Definition

**Định nghĩa (Cohomology Groups):**

$$
H^n(X; G) = \frac{Z^n(X; G)}{B^n(X; G)} = \frac{\ker(\delta^n)}{\text{im}(\delta^{n-1})}
$$

**Quotient: cocycles modulo coboundaries.**

**Same algebraic structure as homology!**

---

### 2. Properties

**Abelian groups:** H^n(X) always abelian.

**Functorial (contravariant):**  
f: X → Y induces:

$$
f^* : H^n(Y) \to H^n(X) \quad \text{(reverse direction!)}
$$

**Construction:**  
φ: C_n(Y) → G cochain.  
Define f^*(φ) = φ ∘ f_# (precompose with chain map).

**Contravariance:**
- (f ∘ g)^* = g^* ∘ f^*
- id^* = id

**Opposite category behavior dari homology!**

---

### 3. Homotopy Invariance

**Theorem:** X ≃ Y ⇒ H^n(X) ≅ H^n(Y).

**Proof:** Same as homology (dual argument). ✓

**Cohomology = homotopy invariant.**

---

## ⭐ Cup Product

### 1. Definition

**Revolutionary feature:** Cohomology có **multiplication**!

**Định nghĩa (Cup Product):**

$$
\cup : H^p(X) \times H^q(X) \to H^{p+q}(X)
$$

**Bilinear, associative operation.**

---

**Construction (Sketch):**  
φ ∈ C^p, ψ ∈ C^q. Define φ ∪ ψ ∈ C^{p+q} by:

$$
(\phi \cup \psi)(\sigma) = \phi(\sigma|_{[v_0, \ldots, v_p]}) \cdot \psi(\sigma|_{[v_p, \ldots, v_{p+q}]})
$$

**Evaluate φ on "front" of simplex, ψ on "back", multiply.**

**Extends to cohomology:**  
If φ, ψ cocycles, then φ ∪ ψ cocycle.  
If φ coboundary, then φ ∪ ψ coboundary.

**Induces well-defined:**  
[φ] ∪ [ψ] = [φ ∪ ψ] ∈ H^{p+q}(X).

---

### 2. Properties

**Bilinearity:** (α₁ + α₂) ∪ β = α₁ ∪ β + α₂ ∪ β.

**Associativity:** (α ∪ β) ∪ γ = α ∪ (β ∪ γ).

**Unity:** 1 ∈ H^0(X) is identity: 1 ∪ α = α ∪ 1 = α.

**Graded commutativity:**

$$
\alpha \cup \beta = (-1)^{pq} \beta \cup \alpha
$$

(α ∈ H^p, β ∈ H^q)

**Signs matter!**

---

### 3. Ring Structure

**Định nghĩa (Cohomology Ring):**

$$
H^*(X) = \bigoplus_{n=0}^\infty H^n(X)
$$

with cup product ∪.

**H^*(X) = graded commutative ring!**

**Much richer structure than homology groups.**

---

**Example:**

For S², we'll see:  
H^*(S²) = ℤ[α]/(α²) where α ∈ H²(S²).

**Polynomial ring truncated!**

---

## 🔄 Universal Coefficient Theorem

### 1. Statement

**Theorem (Universal Coefficient - Cohomology):**

$$
H^n(X; G) \cong \text{Hom}(H_n(X), G) \oplus \text{Ext}(H_{n-1}(X), G)
$$

**Relates cohomology to homology!**

---

**Terms:**
- **Hom(A, G):** Homomorphisms A → G
- **Ext(A, G):** Extension group (measures "twisting")

**Special case:** If H_n(X) free (no torsion), then:

$$
H^n(X; G) \cong \text{Hom}(H_n(X), G) \cong H_n(X) \otimes G
$$

**(When G = ℤ, just H^n ≅ H_n)**

---

### 2. Example

**X = S²:**  
H₂(S²) = ℤ (free).

$$
H^2(S^2; \mathbb{Z}) \cong \text{Hom}(\mathbb{Z}, \mathbb{Z}) \oplus \text{Ext}(0, \mathbb{Z}) \cong \mathbb{Z}
$$

**H^2(S²) ≅ H₂(S²) ≅ ℤ.** ✓

---

**X = ℝP²:**  
H₁(ℝP²) = ℤ/2ℤ (torsion!).

$$
H^1(\mathbb{RP}^2; \mathbb{Z}) \cong \text{Hom}(\mathbb{Z}/2\mathbb{Z}, \mathbb{Z}) \oplus \text{Ext}(H_0, \mathbb{Z})
$$

$$
\cong 0 \oplus 0 = 0
$$

**But H₁(ℝP²) = ℤ/2ℤ ≠ 0!**

**Torsion causes H^n ≠ H_n!**

---

## 🧮 Examples and Computations

### Example 1: Point

X = {pt}.

**H_n(pt) = ℤ (n=0), 0 (n>0).**

**Universal Coefficient:**

$$
H^n(\text{pt}) \cong H_n(\text{pt}) \cong \begin{cases}
\mathbb{Z} & n = 0 \\
0 & n > 0
\end{cases}
$$

**Ring:** H^*(pt) = ℤ (trivial multiplication).

---

### Example 2: Sphere S^n

**H_k(S^n) = ℤ (k=0,n), 0 else.**

**Universal Coefficient:**

$$
H^k(S^n) \cong \begin{cases}
\mathbb{Z} & k = 0, n \\
0 & \text{otherwise}
\end{cases}
$$

**Cohomology ring:**

$$
H^*(S^n) \cong \mathbb{Z}[x]/(x^2), \quad x \in H^n(S^n)
$$

**(Generator x với x² = 0.)**

**For n odd:** Actually x² automatically 0 (graded commutativity).

**For n even:** x² = 0 by dimension (no H^{2n}(S^n)).

---

### Example 3: Torus T²

**H_*(T²) = ℤ, ℤ², ℤ** (n = 0,1,2).

**H^*(T²) = ℤ, ℤ², ℤ** (same by Universal Coefficient, no torsion).

**Ring structure:**

Generators: 1 ∈ H^0, a, b ∈ H^1, (a∪b) ∈ H^2.

$$
H^*(T^2) \cong \mathbb{Z}[a, b]/(a^2, b^2)
$$

**Exterior algebra on two generators!**

**Key:** a ∪ a = 0, b ∪ b = 0 (graded commutativity, odd degree).  
But a ∪ b ≠ 0 (generates H²).

---

### Example 4: ℝP²

**H_*(ℝP²) = ℤ, ℤ/2ℤ, 0.**

**Cohomology (ℤ coefficients):**

$$
H^0(\mathbb{RP}^2) = \mathbb{Z}, \quad H^1 = 0, \quad H^2 = 0
$$

**Torsion disappears!**

**Different picture:** Use ℤ/2ℤ coefficients:

$$
H^*(\mathbb{RP}^2; \mathbb{Z}/2\mathbb{Z}) = (\mathbb{Z}/2\mathbb{Z})[x]/(x^3), \quad x \in H^1
$$

**Polynomial ring mod x³!**

**Cup product:** x ∪ x = x² ≠ 0 ∈ H²(ℝP²; ℤ/2ℤ) ≅ ℤ/2ℤ.

**Detects non-orientability!**

---

## 🧠 Poincaré Duality

### 1. Statement

**Theorem (Poincaré Duality):**  
M compact, oriented, n-manifold without boundary.

$$
H^k(M; \mathbb{Z}) \cong H_{n-k}(M; \mathbb{Z})
$$

**Isomorphism:**

$$
PD : H^k(M) \xrightarrow{\cong} H_{n-k}(M)
$$

**"Top homology ↔ bottom cohomology."**

---

**Geometric intuition:**  
k-dimensional cycle α in M.  
Dual (n-k)-dimensional cycle β = "orthogonal complement."

**Intersection pairing ↔ cup product!**

---

### 2. Example: S^n

**H^k(S^n) ≅ H_{n-k}(S^n):**

- k=0: H^0 = ℤ ↔ H_n = ℤ ✓
- k=n: H^n = ℤ ↔ H_0 = ℤ ✓
- else: 0 ↔ 0 ✓

**Perfect duality!**

---

### 3. Example: T²

**n=2:**

- H^0(T²) = ℤ ↔ H₂(T²) = ℤ ✓
- H^1(T²) = ℤ² ↔ H₁(T²) = ℤ² ✓ (self-dual!)
- H^2(T²) = ℤ ↔ H₀(T²) = ℤ ✓

---

### 4. Non-orientable

**ℝP²:** Not orientable ⇒ Poincaré Duality fails với ℤ coefficients.

**Use ℤ/2ℤ coefficients:** Duality holds.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Henri Poincaré** - *"Analysis Situs"* (1895)  
   *Introduced duality, Betti numbers*

2. **Eduard Čech** - *"Théorie générale de l'homologie"* (1932)  
   *Cohomology theory*

3. **Samuel Eilenberg, Norman Steenrod** - *"Foundations"* (1952)  
   *Axiomatic cohomology*

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§3.1: Cohomology**

5. **Glen E. Bredon** - *Topology and Geometry*, **Chapter V**

6. **Raoul Bott, Loring W. Tu** - *Differential Forms in Algebraic Topology*

7. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapter 5**

---

## 🔗 Applications and Connections

### Characteristic Classes
**Chern, Stiefel-Whitney, Pontryagin Classes:** Cohomology classes of vector bundles. Classify bundles, detect obstructions.

### Obstruction Theory
**Cup Product:** Detects obstructions to extending maps, sections. Essential in bundle theory.

### Algebraic Geometry
**Sheaf Cohomology:** Cohomology of sheaves = foundation. Computes geometric invariants.

### String Theory
**Cohomology Classes:** Background fields (B-fields, RR-fields) = cohomology classes. Topology affects physics.

### De Rham Cohomology
**Differential Forms:** For manifolds, H^n_{dR}(M) ≅ H^n(M; ℝ). Bridge topology ↔ analysis.

---

## 🧩 Exercises

### Cochains

1. **Dual:** If C_n = ℤ³, what is C^n?

2. **Coboundary:** Verify δ² = 0 using ∂² = 0.

### Cohomology Groups

3. **Point:** Verify H^n(pt) = ℤ (n=0), 0 (n>0).

4. **Contractible:** X contractible ⇒ H^n(X) = ?

### Contravariance

5. **Induced Map:** f: S¹ → S¹ degree 2. What is f^*: H^1(S¹) → H^1(S¹)?

6. **Composition:** Verify (f ∘ g)^* = g^* ∘ f^*.

### Cup Product

7. **Torus:** Verify a ∪ b ≠ 0 but a ∪ a = 0 trong H^*(T²).

8. **Commutativity:** α ∈ H^1, β ∈ H^2. Compute α ∪ β vs β ∪ α.

### Ring Structure

9. **Sphere:** Verify H^*(S²) ≅ ℤ[x]/(x²).

10. **Product:** Compute H^*(S¹ × S¹) as ring.

### Universal Coefficient

11. **Apply:** X với H₁(X) = ℤ/3ℤ. Compute H^1(X; ℤ).

12. **Torsion:** Why H^1(ℝP²; ℤ) = 0 even though H₁ = ℤ/2ℤ?

### Poincaré Duality

13. **Verify:** Poincaré Duality for S³ explicitly.

14. **Surface:** Σ_g genus g. Verify H^1(Σ_g) ≅ H₁(Σ_g) via duality.

### Advanced

15. **ℝP² Coefficients:** Compute H^*(ℝP²; ℤ/2ℤ) và verify ring structure.

16. **ℂP²:** Research H^*(ℂP²). (Answer: ℤ[x]/(x³), x ∈ H².)

### Reflection

17. **Why Cohomology?:** List advantages over homology.

18. **Ring Power:** Give example where ring structure distinguishes spaces homology groups can't.

19. **Contravariance:** Explain intuition for reverse direction của cohomology maps.

20. **Cup Product Geometry:** Research how cup product relates to intersection theory.

---

## 📚 Further Reading

- **Hatcher, §3:** Comprehensive cohomology theory
- **Bott & Tu:** Differential forms perspective
- **Bredon, Chapter V:** Advanced topics
- **Milnor & Stasheff:** *Characteristic Classes*

---

## 🎓 Summary

**Cohomology = dual theory with rich structure:**

✅ **Cochains C^n:** Hom(C_n, G) (dual)  
✅ **Coboundary δ:** C^n → C^{n+1} (δ² = 0)  
✅ **Cohomology H^n:** ker(δ) / im(δ)  
✅ **Contravariant:** f induces f^* (reverse direction)  
✅ **Cup Product ∪:** Multiplication H^p ⊗ H^q → H^{p+q}  
✅ **Ring H^*(X):** Graded ring invariant  
✅ **Universal Coefficient:** Relates H^n to H_n (Ext appears!)  
✅ **Poincaré Duality:** H^k(M) ≅ H_{n-k}(M) (manifolds)  

**Điểm chính:**
- Cohomology = more refined than homology
- Cup product = powerful geometric invariant
- Ring structure detects subtle topology
- Contravariance = natural for duality
- Foundation for characteristic classes

**Geometric intuition:**
- Cochains = "measurements" on chains
- Cup product = intersection of cycles
- Ring structure = multiplicative invariant
- Poincaré Duality = orthogonal complement

**Practical wisdom:**
- Use ℤ/2ℤ coefficients for non-orientable spaces
- Cup product often easiest to compute via duality
- Ring structure more powerful than groups alone
- Essential for bundles, obstruction theory

**Chapter 07 Complete!** Chúng ta mastered:
- Simplicial homology (triangulation)
- Singular homology (universal)
- Computational methods (cellular, Mayer-Vietoris)
- Cohomology (dual, ring structure)

**Tiếp theo:** Chapter 08 về **Advanced Topics**—higher homotopy, bundles, manifolds!

---

*"Cohomology: where duality becomes multiplication, and topology becomes algebra."*

🎯 **Master cohomology! The ring structure is revolutionary.** 🎯

---

**Previous:** [Lecture 07.03: Mayer-Vietoris](/contents/vi/topology-chapter07/07_03_Mayer_Vietoris/)  
**Next Chapter:** [Chapter 08: Advanced Topics](/contents/vi/topology-chapter08/)
