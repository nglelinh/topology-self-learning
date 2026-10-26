---
layout: post
title: "Lecture 02.00: Connected Spaces"
lang: vi
lang-ref: lecture-02-00
chapter: 2
lecture: 0
categories: [chapter02]
tags: [connected-spaces, path-connected, components, disconnected]
description: "Không gian liên thông, path-connectedness, và connected components"
---

**Connected Spaces**

---

## 📖 Tổng quan

Chào mừng đến Chapter 02! Chúng ta đã học **định nghĩa** topology và **morphisms** (continuous functions). Giờ đây chúng ta nghiên cứu **properties** của topological spaces.

Hai tính chất quan trọng nhất:
1. **Connectedness** (tính liên thông) — Chapter này
2. **Compactness** (tính compact) — Lecture tiếp theo

**Câu hỏi trực quan:** Khi nào một không gian là "one piece" (một mảnh)?

**Ví dụ:**
- Interval [0,1]: **connected** (không thể chia thành hai phần rời nhau)
- [0,1] ∪ [2,3]: **disconnected** (hai mảnh riêng biệt)
- Circle S¹: **connected** (một đường cong liền)
- Two circles: **disconnected**

![Connected vs Disconnected](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Connected_and_disconnected_spaces.svg/500px-Connected_and_disconnected_spaces.svg.png)  
*Connected (trái) vs Disconnected (phải) - Nguồn concept*

**Connectedness = không thể "chia nhỏ"**

**Trong bài này:**
- Định nghĩa chính thức của **connected**
- Các đặc trưng tương đương (via separation)
- **Path-connectedness**: Connected qua "đường đi"
- **Connected components**: Phân hoạch space thành "mảnh"
- Ứng dụng: Intermediate Value Theorem

**Tại sao quan trọng?**
- Connected spaces = "cannot be separated"
- Nhiều theorems cần connectedness (IVT, Fixed Point, etc.)
- Path-connectedness = stronger notion, dễ work hơn
- Components = topological invariants

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Chia cắt

Tưởng tượng bạn có một **piece of rope** (dây thừng). Rope này "connected" vì nó là một mảnh duy nhất.

**Làm sao "disconnect" rope?**  
→ **Cut** (cắt) nó! Sau khi cắt → hai pieces riêng biệt.

**Trong topology:**  
"Cutting" = tìm hai open sets U, V sao cho:
- U ∪ V = X (cover toàn bộ)
- U ∩ V = ∅ (disjoint)
- U, V ≠ ∅ (cả hai non-empty)

Nếu tìm được → **disconnected**.  
Nếu không tìm được → **connected**!

**Ví dụ trong ℝ:**

[0,1] ∪ [2,3]:
- U = (-1, 1.5) ∩ X = [0,1]
- V = (1.5, 4) ∩ X = [2,3]
- U, V open (trong subspace topology), disjoint, non-empty
- → Disconnected!

[0,2]:
- Không thể tìm được separation như vậy
- → Connected!

---

## 📐 Định nghĩa Hình thức

### 1. Connected Spaces

**Định nghĩa (Disconnected):**  
Topological space X là **disconnected** nếu tồn tại U, V ∈ 𝜏 (open) sao cho:
1. U, V ≠ ∅ (non-empty)
2. U ∩ V = ∅ (disjoint)
3. U ∪ V = X (cover space)

Khi đó, {U, V} gọi là **separation** (phân ly) của X.

**Định nghĩa (Connected):**  
X là **connected** nếu X **không** disconnected.

**Nói bằng lời:** Không tồn tại separation.

**Ví dụ 1: Interval**

[0,1] connected trong ℝ.

**Proof (sketch):** Giả sử (phản chứng) ∃ separation {U, V}.  
Không mất tổng quát, giả sử 0 ∈ U.  
Xét s = sup(U ∩ [0,1]) ∈ [0,1].

Nếu s ∈ U: U open → ∃ε: (s-ε, s+ε) ⊆ U → s không phải sup, mâu thuẫn.  
Nếu s ∈ V: V open → ∃ε: (s-ε, s+ε) ⊆ V → contradiction với s = sup(U).  
Nếu s ∉ U ∪ V: contradiction với U ∪ V = X. ∎

**Ví dụ 2: ℚ (rationals)**

ℚ **disconnected** trong ℝ!

**Proof:**  
U = ℚ ∩ (-∞, √2), V = ℚ ∩ (√2, ∞).  
U, V open trong subspace topology, disjoint, non-empty, U ∪ V = ℚ. ✓

**Ví dụ 3: Discrete Topology**

Mọi space > 1 điểm với discrete topology **disconnected**.

**Proof:** Cho x ≠ y. U = {x}, V = X \ {x} là separation. ✓

**Ví dụ 4: Trivial Topology**

Mọi space với trivial topology **connected**.

**Proof:** Chỉ có ∅, X là open → không thể tìm separation. ✓

---

### 2. Equivalent Characterizations

**Định lý (Equivalent Definitions):**  
Các phát biểu sau **tương đương**:

**(1)** X connected

**(2)** Chỉ có ∅ và X vừa open vừa closed (clopen)

**(3)** Không tồn tại continuous surjection f: X → {0,1} (discrete topology)

**(4)** Mọi continuous f: X → {0,1} là constant

**Chứng minh:**

**(1 ⇒ 2):**  
Giả sử A ⊆ X clopen, A ≠ ∅, X.  
Khi đó U = A open, V = X \ A open (vì A closed).  
U ∩ V = ∅, U ∪ V = X, U,V ≠ ∅ → separation, mâu thuẫn với (1)!

**(2 ⇒ 3):**  
Giả sử ∃f: X → {0,1} continuous surjection.  
f⁻¹({0}) clopen (vì {0} clopen trong {0,1}).  
f surjective → f⁻¹({0}) ≠ ∅, X.  
Mâu thuẫn với (2)!

**(3 ⇒ 4):** Trivial.

**(4 ⇒ 1):**  
Giả sử {U, V} separation của X.  
Define f: X → {0,1}: f(U) = 0, f(V) = 1.  
f continuous (vì f⁻¹({0}) = U open, f⁻¹({1}) = V open).  
f không constant, mâu thuẫn với (4)! ∎

**Ứng dụng practical:**  
Để chứng minh X connected, dùng characterization (2): tìm tất cả clopen sets.

---

### 3. Properties of Connected Spaces

**Định lý (Continuous Image):**  
Nếu f: X → Y continuous và X connected, thì f(X) connected.

**Trực giác:** Continuity preserves connectedness.

**Chứng minh:**  
Giả sử (phản chứng) f(X) disconnected với separation {U, V}.  
f⁻¹(U), f⁻¹(V) open (f continuous), disjoint, non-empty (f surjection lên f(X)).  
f⁻¹(U) ∪ f⁻¹(V) = X → separation của X, mâu thuẫn! ∎

**Hệ quả quan trọng:**  
**Connectedness là topological property!**

X ≅ Y và X connected → Y connected.

**Ứng dụng:** Để chứng minh Y connected, tìm X connected với continuous surjection f: X → Y.

---

**Định lý (Union of Connected Spaces):**  
Cho {Aα}α∈I họ connected subspaces của X.  
Nếu ⋂α Aα ≠ ∅ (có điểm chung), thì ⋃α Aα connected.

**Trực giác:** Các connected pieces "overlap" → union connected.

![Union of connected spaces](https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Connected_union.svg/400px-Connected_union.svg.png)  
*Union của connected spaces qua intersection - Nguồn concept*

**Chứng minh:**  
Cho A = ⋃Aα, x₀ ∈ ⋂Aα.  
Giả sử (phản chứng) f: A → {0,1} continuous non-constant.  
Không mất tổng quát, f(x₀) = 0.  
Mỗi fα = f|_{Aα} continuous, fα(x₀) = 0.  
Aα connected → fα constant → fα ≡ 0.  
→ f ≡ 0 trên A, mâu thuẫn! ∎

**Hệ quả:**  
Nếu A connected và A ⊆ B ⊆ cl(A), thì B connected.

**Chứng minh:** A và cl(A) cùng intersect A → A ∪ cl(A) = cl(A) connected. ∎

---

**Định lý (Product of Connected Spaces):**  
Nếu X, Y connected, thì X × Y connected (product topology).

**Chứng minh (sketch):**  
Fix x₀ ∈ X, y₀ ∈ Y.  
- Slice {x₀} × Y ≅ Y connected
- Slice X × {y} ≅ X connected với mọi y
- Tất cả slices X × {y} intersect tại (x₀, y)
- → ⋃_y (X × {y}) = X × Y connected ✓

---

### 4. Connected Subspaces of ℝ

**Định lý (Characterization on ℝ):**  
A ⊆ ℝ connected ⟺ A là **interval** (có thể unbounded).

**Intervals:**
- Bounded: [a,b], (a,b), [a,b), (a,b]
- Unbounded: [a,∞), (a,∞), (-∞,b], (-∞,b), ℝ

**Chứng minh (⇐):**  
Đã chứng minh [0,1] connected.  
Mọi interval homeomorphic với [0,1], (-∞,∞), [0,∞), hoặc (-∞,0] → connected. ✓

**Chứng minh (⇒):**  
Giả sử A connected, không phải interval.  
Tồn tại a < c < b với a,b ∈ A nhưng c ∉ A.  
U = A ∩ (-∞,c), V = A ∩ (c,∞) → separation → mâu thuẫn! ∎

**Hệ quả quan trọng:** ℝ connected, ℚ disconnected.

---

### 5. Intermediate Value Theorem

**Định lý (Intermediate Value Theorem - IVT):**  
Cho X connected, f: X → ℝ continuous.  
Nếu x, y ∈ X với f(x) < f(y), thì:

$$
\forall r \in (f(x), f(y)): \exists z \in X: f(z) = r
$$

**Nói bằng lời:** f đạt mọi giá trị trung gian.

**Chứng minh:**  
f(X) connected (continuous image).  
f(x), f(y) ∈ f(X) → (f(x), f(y)) ⊆ f(X) (vì f(X) là interval connected).  
→ ∀r ∈ (f(x), f(y)): ∃z: f(z) = r. ∎

![Intermediate Value Theorem](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/Intermediate_value_theorem.svg/400px-Intermediate_value_theorem.svg.png)  
*IVT illustration - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Intermediate_value_theorem.svg)*

**Ứng dụng:**  
Chứng minh phương trình có nghiệm!

**Ví dụ:** x³ - x + 1 = 0 có nghiệm trong (-2, 0).

f(-2) = -5 < 0, f(0) = 1 > 0 → ∃c ∈ (-2,0): f(c) = 0 by IVT. ✓

---

### 6. Path-Connectedness

**Định nghĩa (Path):**  
**Path** trong X từ x đến y là continuous map:

$$
\gamma: [0,1] \to X \quad \text{với } \gamma(0) = x, \gamma(1) = y
$$

**Định nghĩa (Path-Connected):**  
X là **path-connected** nếu với mọi x, y ∈ X, tồn tại path từ x đến y.

**Trực giác:** Có thể "đi" từ bất kỳ điểm nào đến điểm nào qua đường liên tục.

![Path connected space](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Path-connectedness.svg/400px-Path-connectedness.svg.png)  
*Path-connected: có path giữa mọi hai điểm - Nguồn concept*

**Ví dụ:**
- **ℝⁿ** path-connected: γ(t) = (1-t)x + ty (straight line)
- **S¹** path-connected: arc on circle
- **[0,1] ∪ [2,3]** KHÔNG path-connected: không có path từ [0,1] → [2,3]

**Định lý (Path-Connected ⇒ Connected):**  
Nếu X path-connected, thì X connected.

**Chứng minh:**  
Fix x₀ ∈ X. Với mọi x ∈ X, ∃ path γ: [0,1] → X từ x₀ → x.  
[0,1] connected → γ([0,1]) connected (continuous image).  
{γ([0,1])}_{x ∈ X} họ connected spaces, tất cả contain x₀.  
→ ⋃_x γ([0,1]) = X connected. ∎

**Ngược lại KHÔNG đúng!**

**反例 (Topologist's Sine Curve):**

$$
A = \{(x, \sin(1/x)) : 0 < x \leq 1\} \cup \{(0,0)\} \subseteq \mathbb{R}^2
$$

- A **connected** (closure của connected subspace)
- A **KHÔNG path-connected** (không có continuous path từ (0,0) đến any point trên curve)

![Topologist's sine curve](https://upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Topologist%27s_sine_curve.svg/400px-Topologist%27s_sine_curve.svg.png)  
*Topologist's sine curve - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Topologist%27s_sine_curve.svg)*

---

### 7. Connected Components

**Định nghĩa (Connected Component):**  
**Connected component** của x ∈ X là union của tất cả connected subspaces chứa x:

$$
C_x = \bigcup \{A \subseteq X : x \in A, A \text{ connected}\}
$$

**Định lý (Properties of Components):**
1. C_x connected (union theorem)
2. C_x closed
3. C_x ∩ C_y ≠ ∅ ⇒ C_x = C_y
4. X = ⋃_x C_x (disjoint union - partition)

**Trực giác:** Components = "maximal connected pieces" của X.

**Ví dụ:**

[0,1] ∪ [2,3]:
- C_x = [0,1] nếu x ∈ [0,1]
- C_x = [2,3] nếu x ∈ [2,3]
- Hai components

ℚ (rationals):
- Mỗi C_x = {x} (singleton)
- ℚ có countably many components (totally disconnected!)

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Bernard Bolzano** - *"Rein analytischer Beweis..."* (1817)  
   *Đầu tiên phát biểu IVT chặt chẽ*

2. **Camille Jordan** - *"Cours d'analyse"* (1893)  
   *Jordan curve theorem - connectedness*

3. **Felix Hausdorff** - *"Grundzüge der Mengenlehre"* (1914)  
   *Formalization của connectedness*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§23–24: Connected Spaces**  
   *Standard reference*

5. **Sidney A. Morris** - *Topology Without Tears*, **Chapter 9**  
   *Clear examples*

6. **Stephen Willard** - *General Topology*, **Chapter 6**  
   *Comprehensive treatment*

---

## 🔗 Applications and Connections

### Analysis - IVT và Fixed Points
**Brouwer Fixed Point:** Mọi continuous f: Dⁿ → Dⁿ có fixed point. Chứng minh dùng connectedness!

### Graph Theory - Connectivity
**Connected Graphs:** Graph connected ⟺ underlying space connected (với topology thích hợp).

### Neuroscience - Brain Networks
**Functional Connectivity:** Brain regions form connected networks. Disconnection = neurological disorders.

### Economics - Network Effects
**Market Networks:** Connected markets allow price discovery. Disconnection → arbitrage opportunities.

---

## Video tham khảo

- **xem trước** [Basic Topology 15 | Connected Spaces](https://www.youtube.com/watch?v=JEZ9Psscb18) — The Bright Side of Mathematics, tiếng Anh. Không gian liên thông qua tập vừa mở vừa đóng, đúng định nghĩa của bài.
- [[Tôpô đại cương] Bài 44. Không gian liên thông - Phần 1: Định nghĩa và Ví dụ](https://www.youtube.com/watch?v=d9E5MkJaQpg) — Nguyễn Thị Yến Nhi THPT Giồng Riềng, tiếng Việt. Cùng định nghĩa và ví dụ, bằng tiếng Việt.
- [Weird Topological Spaces  //  Connected vs Path Connected vs Simply Connected](https://www.youtube.com/watch?v=zzeADy0MSFA) — Dr. Trefor Bazett, tiếng Anh. Liên thông, liên thông đường, và đơn liên: ba mức mà bài cần tách bạch.

## 🧩 Exercises

### Connected Spaces

1. **Verify Connected:**  
   Các spaces sau connected không?
   - a) ℝ
   - b) ℚ
   - c) [0,1]
   - d) (0,1) ∪ (1,2)

2. **Clopen Sets:**  
   Tìm tất cả clopen sets trong:
   - a) ℝ
   - b) [0,1] ∪ [2,3]
   - c) Discrete topology trên {1,2,3}

3. **IVT Application:**  
   Chứng minh x⁵ + x = 1 có nghiệm trong (0,1).

### Path-Connected

4. **Verify Path-Connected:**  
   Các spaces sau path-connected không?
   - a) ℝⁿ
   - b) S¹ (circle)
   - c) [0,1] ∪ [2,3]

5. **Construct Path:**  
   X = ℝ² \ {origin}. Chứng minh X path-connected.

6. **Topologist's Sine Curve:**  
   A = {(x, sin(1/x)) : 0 < x ≤ 1} ∪ {(0,0)}.  
   Chứng minh A connected nhưng không path-connected.

### Components

7. **Find Components:**  
   Tìm connected components của:
   - a) ℚ
   - b) [0,1] ∪ [2,3] ∪ {5}
   - c) ℝ \ ℤ

8. **Components Properties:**  
   Chứng minh: Connected components luôn closed.

### Advanced

9. **Products:**  
   Chứng minh: Nếu X, Y connected thì X × Y connected.

10. **Continuous Image:**  
    Cho f: X → Y continuous, X connected.  
    Chứng minh f(X) connected.

---

## 📚 Further Reading

- **Munkres, Topology:** §23–25 (Connected Spaces, Components)
- **Morris, Topology Without Tears:** Chapter 9
- **Hatcher, Algebraic Topology:** §0 (Path-connectedness)

---

## 🎓 Summary

✅ **Connected:** Không thể chia thành hai open sets disjoint  
✅ **Characterizations:** Via clopen sets, continuous maps  
✅ **Continuous Image:** f(connected) = connected  
✅ **IVT:** Connected spaces → intermediate values  
✅ **Path-Connected:** Stronger notion, implies connected  
✅ **Components:** Maximal connected pieces  

**Điểm chính:**
- Connectedness = "one piece"
- IVT là hệ quả topology
- Path-connected ⇒ connected (ngược lại sai!)
- Components = partition X

**Tiếp theo:** Lecture 02.01 về **Applications of Connectedness** với nhiều theorems và examples hơn!

---

*"Connected spaces cannot be separated."* — Topology wisdom

🎯 **Visualize connectedness! Vẽ paths và separations.** 🎯

---

**Previous:** [Chapter 01: Topological Spaces](/contents/vi/topology-chapter01/)  
**Next:** [Lecture 02.01: Applications of Connectedness](/contents/vi/topology-chapter02/02_01_Applications_Connectedness/)

